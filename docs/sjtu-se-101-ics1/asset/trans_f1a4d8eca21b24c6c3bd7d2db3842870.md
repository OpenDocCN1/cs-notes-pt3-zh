

## 常用函数的打包

- 如何打包程序员常用的函数？
  - 数学、I/O、内存管理、字符串操作等。

## 常用函数的打包

- 鉴于目前的链接器框架，做法很尴尬：
  - 方案 1：将所有函数放在单个源文件中。
    - 程序员将一个大的目标文件链接到他们的程序中。
    - 空间和时间效率低下。
  - 方案 2：将每个函数放在单独的源文件中。
    - 程序员显式地将适当的二进制文件链接到他们的程序中。
    - 更高效，但对程序员负担较重。

## 常用函数的打包

- 解决方案：静态库（`.a` 归档文件）。
  - 将相关的可重定位目标文件连接成一个带索引的单个文件（称为归档）。
  - 增强链接器，使其尝试通过在一個或多个归档中查找符号来解析未解析的外部引用。
  - 如果归档成员文件解析了引用，则将其链接到可执行文件中。

## 使用静态库

- **E：**
  - 将被合并以形成可执行文件的可重定位目标文件。
- **U：**
  - 未解析的符号。
- **D：**
  - 在之前的输入文件中已定义的符号。
- 最初，所有都是空的。

## 使用静态库

- 按命令行顺序扫描 `.o` 文件和 `.a` 文件。
- 扫描对象文件 `f` 时：
  - 将 `f` 添加到 `E`。
  - 更新 `U` 和 `D`。
- 扫描归档文件 `f` 时：
  - 解析 `U`。
  - 如果 `m` 用于解析符号，则 `m` 被添加到 `E`。
  - 使用 `m` 更新 `U` 和 `D`。

## 使用静态库

- 如果扫描结束时未解析列表中仍有条目，则为错误。
- 问题：
  - 命令行顺序很重要！
  - 寓意：将库放在命令行末尾。

## 重定位

- 重定位：
  - 合并输入模块。
  - 为每个符号分配运行时地址。
- 两个步骤：
  - 重定位节和符号定义。
  - 重定位节内的符号引用。

## 重定位

- 对于对位置未知的对象的每个引用：
  - 汇编器生成一个重定位条目。
  - 代码的重定位条目放在 `.rel.text` 中。
  - 数据的重定位条目放在 `.rel.data` 中。

## 重定位

- 重定位条目

```c
typedef struct {
    int offset;
    int symbol:24,
         type:8;
} Elf32_Rel;
```

## 重定位

```asm
6  e8 fc ff ff ff    call  7<main+0x7>  swap();
```

`.rel.text` 中有一个重定位条目。

| offset | symbol | type |
|---:|---|---|
| 7 | swap | R_386_PC32 |

## 重定位

```c
int *bufp0 = &buf[0];
00000000 <bufp0>:
    0: 00 00 00 00
```

`.rel.data` 中有一个重定位条目。

| offset | symbol | type |
|---:|---|---|
| 0 | buf | R_386_32 |

## 重定位

```asm
6   e8 fc ff ff ff   call   7<main+0x7>  swap();
7: R_386_PC32 swap  relocation entry
```

```text
r.offset = 0x7
r.symbol = swap
r.type = R_386_PC32

ADDR(main) = ADDR(.text) = 0x80483b4
ADDR(swap) = 0x80483c8
refaddr = ADDR(main) + r.offset = 0x80483bb
ADDR(r.symbol) = ADDR(swap) = 0x80483c8
*refptr = (unsigned) (ADDR(r.symbol) + *refptr - refaddr)
         = (unsigned) (0x80483c8 + (-4) - 0x80483bb)
         = (unsigned) 0x9
```

## 重定位

```c
int *bufp0 = &buf[0];
```

```text
00000000 <bufp0>:
       0: 00 00 00 00
                 0: R_386_32  buf
```

`int *bufp0 = &buf[0];` 重定位条目：

```text
ADDR(r.symbol) = ADDR(buf) = 0x8049454
*refptr = (unsigned) (ADDR(r.symbol) + *refptr)
         = (unsigned) (0x8049454)
```

```text
0804945c <bufp0>:
0804945c:    54 94 04 08
```

## 重定位

```c
1  foreach section s {
2    foreach relocation entry r {
3      refptr = s + r.offset; /* ptr to reference to be relocated */
4
5      /* relocate a PC-relative reference */
6      if (r.type == R_386_PC32) {
7        refaddr = ADDR(s) + r.offset; /* ref's runtime address */
8        *refptr = (unsigned) (ADDR(r.symbol) + *refptr - refaddr);
9      }
10
11     /* relocate an absolute reference */
12     if (r.type == R_386_32)
13       *refptr = (unsigned) (ADDR(r.symbol) + *refptr);
14   }
15 }
```

