
## 地址转换：PAE-4k

![](img/53ee1e3b0eba43505c7d530851f32f6f_226_0.png)

图 3-18：启用 PAE 时的线性地址转换（4KB 页）

## 地址转换：PAE-2M

![](img/53ee1e3b0eba43505c7d530851f32f6f_227_0.png)

图 3-19：启用 PAE 时的线性地址转换（2MB 页）

## 测验 #1

在 IA32 架构中，当 %cr4 寄存器中的 CR4_PSE 位被设置时，超级页模式被启用，操作系统可以使用 4KB 大小的页面或 4MB 大小的页面。小页面和大页面之间存在权衡。
考虑以下场景：

a) 将通过 mmap() 函数映射到 RAM 的一个数百 MB 的大文件内容转储到另一个位置：

```
memcpy(addr_of_new_location, addr_of_mapped_file, sizeof_file);
```

b) 执行以下计算，其中 A、B 是 int 指针：

```
for(i=0; i<0x40000; ++i){
    A[i] += B[i] & 0x3FFFFF;
}
```

在每种场景中，哪种大小（4KB 或 4MB）的页面表现更好？给出你的理由。

```
17 int
18 main(void)
19 {
20     kinit1(end, P2V(4*1024*1024)); // phys page allocator
21     kvmalloc();         // kernel page table
22     mpinit();           // collect info about this machine
23     lapicinit();
24     seginit();          // set up segments
25     cprintf("\ncpu%d: starting xv6\n\n", cpu->id);
26     picinit();          // interrupt controller
27     ioapicinit();       // another interrupt controller
28     consoleinit();      // I/O devices & their interrupts
29     uartinit();         // serial port
30     pinit();            // process table
31     tvinit();           // trap vectors
32     binit();            // buffer cache
33     fileinit();         // file table
34     iinit();            // inode cache
35     ideinit();          // disk
36     if (!ismp)
37         timerinit();    // uniprocessor timer
38     startothers();      // start other processors
39     kinit2(P2V(4*1024*1024), P2V(PHYSTOP)); // must come after startothers()
40     userinit();         // first user process
41     // Finish setting up this processor in mpmain.
42     mpmain();
43 }
```

```c
extern char data[];  // defined by kernel.ld
pde_t *kpgdir;       // for use in scheduler()
struct segdesc gdt[NSEGS];

// Set up CPU's kernel segment descriptors.
// Run once on entry on each CPU.
void
seginit(void)
{
  struct cpu *c;

  // Map "logical" addresses to virtual addresses using identity map.
  // Cannot share a CODE descriptor for both kernel and user
  // because it would have to have DPL_USER, but the CPU forbids
  // an interrupt from CPL=0 to DPL=3.
  c = &cpus[cpunum()];
  c->gdt[SEG_KCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, 0);
  c->gdt[SEG_KDATA] = SEG(STA_W,       0, 0xffffffff, 0);
  c->gdt[SEG_UCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, DPL_USER);
  c->gdt[SEG_UDATA] = SEG(STA_W,       0, 0xffffffff, DPL_USER);

  // Map cpu and cpu-local
  c->gdt[SEG_KCPU] = SEG(STA_W, (uint)&c->cpu, 8, 0);

  lgdt(c->gdt, sizeof(c->gdt));
  loadgs(SEG_KCPU << 3);

  // Initialize cpu-local storage.
  cpu = c;
  proc = 0;
}
```

![](img/53ee1e3b0eba43505c7d530851f32f6f_231_0.png)

## xv6 虚拟地址方案概览

0x00000000:0x80000000
KERNBASE 以下的用户地址

0x80000000:0x80100000
映射低 1MB 设备（供内核使用）

0x80100000:?
内核指令/数据

? :0x8E000000
此处映射 224 MB DRAM

0xFE000000:0x00000000
更多内存映射设备

## 4 KB 页面

entrypgdir 很简单：
由 1024 个 PDE 组成的数组，每个映射 4 MB，但 4 MB 的页面大小太大了！
如果进程很小，这会非常浪费；xv6 程序只有几十 KB。
4 MB 页面需要分配完整 4 MB 的物理内存。
解决方案：x86 MMU 支持 4 KB 页面。

kvmalloc

```
17 int
18 main(void)
19 {
20   kinit1(end, P2V(4*1024*1024)); // phys page allocator
21   kvmalloc();        // kernel page table
22   mpinit();          // collect info about this machine
```

```
// Allocate one page table for the machine for the kernel address
// space for scheduler processes.
void
kvmalloc(void)
{
  kpgdir = setupkvm();
  switchkvm();
}
```

```
// Switch h/w page table register to the kernel-only page table,
// for when no process is running.
void
switchkvm(void)
{
  lcr3(v2p(kpgdir));   // switch to the kernel page table
}
```

