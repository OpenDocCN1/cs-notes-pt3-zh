

```c
78 void
79 userinit(void)
80 {
81     struct proc *p;
82     extern char _binary_initcode_start[], _binary_initcode_size[];
83
84     p = allocproc();
85     initproc = p;
86     if((p->pgdir = setupkvm()) == 0)
87         panic("userinit: out of memory?");
88     inituvm(p->pgdir, _binary_initcode_start, (int)_binary_initcode_size);
89     p->sz = PGSIZE;
90     memset(p->tf, 0, sizeof(*p->tf));
91     p->tf->cs = (SEG_UCODE << 3) | DPL_USER;
92     p->tf->ds = (SEG_UDATA << 3) | DPL_USER;
93     p->tf->es = p->tf->ds;
94     p->tf->ss = p->tf->ds;
95     p->tf->eflags = FL_IF;
96     p->tf->esp = PGSIZE;
97     p->tf->eip = 0;  // beginning of initcode.S
98
99     safestrcpy(p->name, "initcode", sizeof(p->name));
100    p->cwd = namei("/");
101
102    p->state = RUNNABLE;
103 }
```

## 用户虚拟内存映射

### 创建进程

- `inituvm`: 初始化用户虚拟内存
- `loaduvm`: 加载程序段

### 上下文切换

- `switchuvm`

### 增长/缩小/释放虚拟内存

- `allocuvm`
- `deallocuvm`
- `freevm`

### Fork

- `copyuvm`

```c
179 // Load the initcode into address 0 of pgdir.
// sz must be less than a page.
180 void
181 inituvm(pde_t *pgdir, char *init, uint sz)
182 {
183     char *mem;
184
185     if(sz >= PGSIZE)
186         panic("inituvm: more than a page");
187     mem = kalloc();
188     memset(mem, 0, PGSIZE);
189     mappages(pgdir, 0, PGSIZE, v2p(mem), PTE_W|PTE_U);
190     memmove(mem, init, sz);
191 }
```

```c
// Switch TSS and h/w page table to correspond to process p.
void
switchuvm(struct proc *p)
{
    pushcli();
    cpu->gdt[SEG_TSS] = SEG16(STS_T32A, &cpu->ts, sizeof(cpu->ts)-1, 0);
    cpu->gdt[SEG_TSS].s = 0;
    cpu->ts.ss0 = SEG_KDATA << 3;
    cpu->ts.esp0 = (uint)p->kstack + KSTACKSIZE;
    ltr(SEG_TSS << 3);
    if(p->pgdir == 0)
        panic("switchuvm: no pgdir");
    lcr3(v2p(p->pgdir));  // switch to new address space
    popcli();
}
```

```c
// Load a program segment into pgdir. addr must be page-aligned
// and the pages from addr to addr+sz must already be mapped.
int
loaduvm(pde_t *pgdir, char *addr, struct inode *ip, uint offset, uint sz)
{
    uint i, pa, n;
    pte_t *pte;

    if((uint) addr % PGSIZE != 0)
        panic("loaduvm: addr must be page aligned");
    for(i = 0; i < sz; i += PGSIZE){
        if((pte = walkpgdir(pgdir, addr+i, 0)) == 0)
            panic("loaduvm: address should exist");
        pa = PTE_ADDR(*pte);
        if(sz - i < PGSIZE)
            n = sz - i;
        else
            n = PGSIZE;
        if(readi(ip, p2v(pa), offset+i, n) != n)
            return -1;
    }
    return 0;
}
```

```c
// Allocate page tables and physical memory to grow process from oldsz to
// newsz, which need not be page aligned.  Returns new size or 0 on error.
int
allocuvm(pde_t *pgdir, uint oldsz, uint newsz)
{
    char *mem;
    uint a;

    if(newsz >= KERNBASE)
        return 0;
    if(newsz < oldsz)
        return oldsz;

    a = PGROUNDUP(oldsz);
    for(; a < newsz; a += PGSIZE){
        mem = kalloc();
        if(mem == 0){
            cprintf("allocuvm out of memory\n");
            deallocuvm(pgdir, newsz, oldsz);
            return 0;
        }
        memset(mem, 0, PGSIZE);
        mappages(pgdir, (char*)a, PGSIZE, v2p(mem), PTE_W|PTE_U);
    }
    return newsz;
}
```

```c
// Deallocate user pages to bring the process size from oldsz to
// newsz. oldsz and newsz need not be page-aligned, nor does newsz
// need to be less than oldsz. oldsz can be larger than the actual
// process size. Returns the new process size.
int
deallocuvm(pde_t *pgdir, uint oldsz, uint newsz)
{
  pte_t *pte;
  uint a, pa;

  if(newsz >= oldsz)
    return oldsz;

  a = PGROUNDUP(newsz);
  for(; a < oldsz; a += PGSIZE){
    pte = walkpgdir(pgdir, (char*)a, 0);
    if(!pte)
      a += (NPTENTRIES - 1) * PGSIZE;
    else if((*pte & PTE_P) != 0){
      pa = PTE_ADDR(*pte);
      if(pa == 0)
        panic("kfree");
      char *v = P2V(pa);
      kfree(v);
      *pte = 0;
    }
  }
  return newsz;
}
```

