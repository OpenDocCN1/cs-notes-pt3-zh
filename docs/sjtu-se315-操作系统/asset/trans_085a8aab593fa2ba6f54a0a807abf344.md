

## Elf 文件映像

text.offset text.filesz data.offset data.filesz

Elf 头部 文本（代码） 头部 数据 文本（代码） 数据

## 内存中的可执行文件

text.memsz data.memsz text.vaddr data.vaddr

文本（代码） 数据 栈（4096）

可执行映像和 ELF 二进制文件可以相互映射

![](img/53ee1e3b0eba43505c7d530851f32f6f_112_0.png)

```
void
readsect(void *dst, uint offset)
{
    // Issue command.
    waitdisk();
    outb(0x1F2, 1);    // count = 1
    outb(0x1F3, offset);
    outb(0x1F4, offset >> 8);
    outb(0x1F5, offset >> 16);
    outb(0x1F6, (offset >> 24) | 0xE0);
    outb(0x1F7, 0x20);  // cmd 0x20 - read sectors

    // Read data.
    waitdisk();
    insl(0x1F0, dst, SECTSIZE/4);
}

// Read 'count' bytes at 'offset' from kernel into physical address 'pa'.
// Might copy more than asked.
void
readseg(uchar* pa, uint count, uint offset)
{
    uchar* epa;

    epa = pa + count;

    // Round down to sector boundary.
    pa -= offset % SECTSIZE;

    // Translate from bytes to sectors; kernel starts at sector 1.
    offset = (offset / SECTSIZE) + 1;

    // If this is too slow, we could read lots of sectors at a time.
    // We'd write more to memory than asked, but it doesn't matter --
    // we load in increasing order.
    for(; pa < epa; pa += SECTSIZE, offset++)
        readsect(pa, offset);
}
```

```
# By convention, the _start symbol specifies the ELF entry point.
# Since we haven't set up virtual memory yet, our entry point is
# the physical address of 'entry'.
.globl _start
_start = V2P_WO(entry)

# Entering xv6 on boot processor, with paging off.
.globl entry
entry:
    # Turn on page size extension for 4Mbyte pages
    movl    %cr4, %eax
    orl     $(CR4_PSE), %eax
    movl    %eax, %cr4
    # Set page directory
    movl    $(V2P_WO(entrypgdir)), %eax
    movl    %eax, %cr3
    # Turn on paging.
    movl    %cr0, %eax
    orl     $(CR0_PG|CR0_WP), %eax
    movl    %eax, %cr0

# Set up the stack pointer.
movl $(stack + KSTACKSIZE), %esp

# Jump to main(), and switch to executing at
# high addresses. The indirect call is needed because
# the assembler produces a PC-relative instruction
# for a direct jump.
mov $main, %eax
jmp *%eax

.comm stack, KSTACKSIZE
```

```
static void startothers(void);
static void mpmain(void) __attribute__((noreturn));
extern pde_t *kpgdir;
extern char end[]; // first address after kernel loaded from ELF file

// Bootstrap processor starts running C code here.
// Allocate a real stack and switch to it, first
// doing some setup required for memory allocator to work.
int
main(void)
{
    kinit1(end, P2V(4*1024*1024)); // phys page allocator
    kvmalloc();     // kernel page table
    mpinit();       // collect info about this machine
    lapicinit(mpcpu());
    seginit();      // set up segments
    cprintf("\ncpu%d: starting xv6\n\n", cpu->id);
    picinit();      // interrupt controller
    ioapicinit();   // another interrupt controller
    consoleinit();  // I/O devices & their interrupts
    uartinit();     // serial port
    pinit();        // process table
    tvinit();       // trap vectors
    binit();        // buffer cache
    fileinit();     // file table
    iinit();        // inode cache
    ideinit();      // disk
    if (!ismp)
        timerinit();    // uniprocessor timer
    startothers();  // start other processors
    kinit2(P2V(4*1024*1024), P2V(PHYSTOP)); // must come after startothers()
    userinit();     // first user process
    // Finish setting up this processor in mpmain.
    mpmain();
}
```

- PC 架构
- 内存
- 执行
- PC 仿真

## 使用 PC 仿真器进行开发

- Bochs PC 仿真器
  - **确实** 做了真实 PC **做** 的事情
  - 仅在软件中实现！

像普通程序一样在“宿主”操作系统上运行

![](img/53ee1e3b0eba43505c7d530851f32f6f_116_0.png)

## CPU 仿真

```c
for (;;) {
    read_instruction();
    switch (decode_instruction_opcode()) {
    case OPCODE_ADD:
        int src = decode_src_reg();
        int dst = decode_dst_reg();
        regs[dst] = regs[dst] + regs[src];
        break;
    case OPCODE_SUB:
        int src = decode_src_reg();
        int dst = decode_dst_reg();
        regs[dst] = regs[dst] - regs[src];
        break;
    ...
    }
    eip += instruction_length;
}
```

![](img/53ee1e3b0eba43505c7d530851f32f6f_117_0.png)

