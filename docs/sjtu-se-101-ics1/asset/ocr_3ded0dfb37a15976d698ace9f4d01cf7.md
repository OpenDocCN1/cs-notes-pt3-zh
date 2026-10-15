# Example (Relocation) (Hw 7.14)

| 行 | 地址 | 机器码 | 汇编指令 |
|---:|:---|:---|:---|
| 8 | e: | ff 24 95 00 00 00 00 | jmp *0x0(,%edx,4) |
| 9 | 15: | 40 | inc %eax |
| 10 | 16: | eb 10 | jmp 28 <relo3+0x28> |
| 11 | 18: | 83 c0 03 | add $0x3,%eax |
| 12 | 1b: | eb 0b | jmp 28 <relo3+0x28> |
| 13 | 1d: | 8d 76 00 | lea 0x0(%esi),%esi |
| 14 | 20: | 83 c0 05 | add $0x5,%eax |
| 15 | 23: | eb 03 | jmp 28 <relo3+0x28> |
| 16 | 25: | 83 c0 06 | add $0x6,%eax |
| 17 | 28: | 89 ec | mov %ebp,%esp |
| 18 | 2a: | 5d | pop %ebp |
| 19 | 2b: | c3 | ret |