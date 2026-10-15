

# 按惯例，_start 符号指定 ELF 入口点。
# 由于我们尚未设置虚拟内存，我们的入口点是
# 'entry' 的物理地址。
.globl _start
_start = V2P_WO(entry)

# 在引导处理器上进入 xv6，分页关闭。
.globl entry
entry:
    # 为 4M 字节页面打开页面大小扩展
    movl    %cr4, %eax
    orl     $(CR4_PSE), %eax
    movl    %eax, %cr4
    # 设置页目录
    movl    $(V2P_WO(entrypgdir)), %eax
    movl    %eax, %cr3
    # 打开分页。
    movl    %cr0, %eax
    orl     $(CR0_PG|CR0_WP), %eax
    movl    %eax, %cr0

# 设置栈指针。
movl $(stack + KSTACKSIZE), %esp

# 跳转到 main()，并切换到高地址执行。需要间接调用是因为
# 汇编器为直接跳转生成 PC 相对指令
mov $main, %eax
jmp *%eax

.comm stack, KSTACKSIZE

Page Size Extension (PSE): for 4M pages

entry.S

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

## PC PROGRAMMING

- PC Architecture
- Memory
- Execution
- PC Emulation

## Emulation of CPU

```
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

## Emulation of Memory

```
int32_t regs[8];
#define REG_EAX 1;
#define REG_EBX 2;
#define REG_ECX 3;
...
int32_t eip;
int16_t segregs[4];
...

char mem[256*1024*1024];
```

## Emulation of x86 Memory

```c
uint8_t read_byte(uint32_t phys_addr) {
    if (phys_addr < LOW_MEMORY)
        return low_mem[phys_addr];
    else if (phys_addr >= 960*KB && phys_addr < 1*MB)
        return rom_bios[phys_addr - 960*KB];
    else if (phys_addr >= 1*MB && phys_addr < 1*MB+EXT_MEMORY) {
        return ext_mem[phys_addr-1*MB];
    }
    else ...
}

void write_byte(uint32_t phys_addr, uint8_t val) {
    if (phys_addr < LOW_MEMORY)
        low_mem[phys_addr] = val;
    else if (phys_addr >= 960*KB && phys_addr < 1*MB)
        ; /* ignore attempted write to ROM! */
    else if (phys_addr >= 1*MB && phys_addr < 1*MB+EXT_MEMORY) {
        ext_mem[phys_addr-1*MB] = val;
    }
    else ...
}
```

![](img/53ee1e3b0eba43505c7d530851f32f6f_142_0.png)

## Emulation of Devices

- Hard disk: using a file of the host
- VGA display: draw in a host window
- Keyboard: host’s keyboard API
- Clock chip: host’s clock
- Etc.

