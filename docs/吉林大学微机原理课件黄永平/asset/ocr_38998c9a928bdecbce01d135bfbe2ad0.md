# (1)字节串传送指令 MOVSB

```
; ES:[DI] ← DS:[SI]
SI ← SI ± 1
DI ← DI ± 1
```

Copy byte at DS:[SI] to ES:[DI]
Update SI and DI

# M to M ?

# (2)字串传送指令 MOVSW

```
; ES:[DI] ← DS:[SI]
SI ← SI ± 2
DI ← DI ± 2
```

Copy word at DS:[SI] to ES:[DI]
Update SI and DI

*MOVS = MOVSB 或 MOVSW

常用于把某一内存缓冲区中内容复制到另一个缓冲区中