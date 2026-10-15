# ELF Header :

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