
## Bootstrap GDT
.p2align 2                         # force 4 byte alignment
gdt:
    SEG_NULLASM                    # null seg
    SEG_ASM(STA_X|STA_R, 0x0, 0xffffffff)  # code seg
    SEG_ASM(STA_W, 0x0, 0xffffffff)        # data seg

gdtdesc:
    .word   (gdtdesc - gdt - 1)             # sizeof(gdt) - 1
    .long   gdt                             # address gdt

![](img/53ee1e3b0eba43505c7d530851f32f6f_130_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_130_1.png)

http://wiki.osdev.org/Global_Descriptor_Table

```c
void
bootmain(void)
{
    struct elfhdr *elf;
    struct proghdr *ph, *eph;
    void (*entry)(void);
    uchar* pa;

    elf = (struct elfhdr*)0x10000;  // scratch space

    // Read 1st page off disk
    readseg((uchar*)elf, 4096, 0);

    // Is this an ELF executable?
    if(elf->magic != ELF_MAGIC)
        return;  // let bootasm.S handle error

    // Load each program segment (ignores ph flags).
    ph = (struct proghdr*)((uchar*)elf + elf->phoff);
    eph = ph + elf->phnum;
    for(; ph < eph; ph++){
        pa = (uchar*)ph->paddr;
        readseg(pa, ph->filesz, ph->off);
        if(ph->memsz > ph->filesz)
            stosb(pa + ph->filesz, 0, ph->memsz - ph->filesz);
    }

    // Call the entry point from the ELF header.
    // Does not return!
    entry = (void(*)(void))(elf->entry);
    entry();
}
```

```c
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

## ELF Header :

ELF header resides at the beginning and holds a road map describing the files organization

```
#define EI_NIDENT 16
typedef struct {
    unsigned char e_ident [EI_NIDENT];
    Elf32_Half e_type;
    Elf32_Half e_machine ;
    Elf32_Word e_version ;
    Elf32_Addr e_entry ;
    Elf32_Off e_phoff;
    Elf32_Off e_shoff;
    Elf32_Word e_flags ;
    Elf32_Half e_ehsize ;
    Elf32_Half e_phentsize ;
    Elf32_Half e_phnum ;
    Elf32_Half e_shentsize ;
    Elf32_Half e_shnum ;
    Elf32_Half e_shstrndx ;
}Elf32_Ehdr ;
```

e_machine : specifies the required architecture :0 = No machine ... 3 = Intel 80386 4 = Motorola 68000 ...8 = MIPS RS3000

e_entry : the virtual address to which the system first transfers control, when starting the process. If the file has no associated entry point, this member holds zero.

e_shoff : holds the section header table’s file offset in bytes. If the file has no section header table, this member holds zero.

| Name | Size | Alignment | Purpose |
|---|---|---|---|
| Elf32_Addr | 4 | 4 | Unsigned program address |
| Elf32_Half | 2 | 2 | Unsigned medium integer |
| Elf32_Off | 4 | 4 | Unsigned file offset |
| Elf32_Sword | 4 | 4 | Signed large integer |
| Elf32_Word | 4 | 4 | Unsigned large integer |
| Unsigned char | 1 | 1 | Unsigned small integer |

## Elf File Image

## Executable in Memory

text.offset text.filesz data.offset data.filesz

Elf Header Text (Code) Header Data Header Text (Code) Data

Text (Code) Data Stack (4096)

text.memsz data.memsz text.vaddr data.vaddr

Executable image and elf binary can being mapped onto each other

![](img/53ee1e3b0eba43505c7d530851f32f6f_134_0.png)
