# 可执行文件中的程序头表

```
typedef struct {
    Elf32_Word  p_type;
    Elf32_Off   p_offset;
    Elf32_Addr  p_vaddr;
    Elf32_Addr  p_paddr;
    Elf32_Word  p_filesz;
    Elf32_Word  p_memsz;
    Elf32_Word  p_flags;
    Elf32_Word  p_align;
} Elf32_Phdr;
```

程序头表描述可执行文件中的节与虚拟空间中的存储段之间的映射关系

+   - 一个表项（32B）说明虚拟地址空间中一个连续的段或一个特殊的节
+   - 以下是某可执行目标文件程序头表信息
+   - 有 8 个表项，其中两个为可装入段（即 Type=LOAD）

Program Headers:    $ readelf -l main

| Type | Offset | VirtAddr | PhysAddr | FileSiz | MemSiz | Flg | Align |
|---|---|---|---|---|---|---|---|
| PHDR | 0x000034 | 0x08048034 | 0x08048034 | 0x00100 | 0x00100 | R E | 0x4 |
| INTERP | 0x000134 | 0x08048134 | 0x08048134 | 0x00013 | 0x00013 | R | 0x1 |
|  |  |  |  |  |  |  | [Requesting program interpreter: /lib/ld-linux.so.2] |
| LOAD | 0x000000 | 0x08048000 | 0x08048000 | 0x004d4 | 0x004d4 | R E | 0x1000 |
| LOAD | 0x0004fc | 0x080494fc | 0x080494fc | 0x00018 | 0x00018 | RW | 0x1000 |
| DYNAMIC | 0x000f20 | 0x08049f20 | 0x08049f20 | 0x000d0 | 0x000d0 | RW | 0x4 |
| NOTE | 0x000148 | 0x08048148 | 0x08048148 | 0x00044 | 0x00044 | R | 0x4 |
| GNU_STACK | 0x000000 | 0x00000000 | 0x00000000 | 0x00000 | 0x00000 | RW | 0x4 |
| GNU_RELRO | 0x000f0c | 0x08049f0c | 0x08049f0c | 0x00014 | 0x00014 | R | 0x1 |