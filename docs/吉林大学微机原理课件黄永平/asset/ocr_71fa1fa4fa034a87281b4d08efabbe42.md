# 2. 地址传送指令（LEA, LDS, LES）

HYPer

目的：把地址传送到指定寄存器。

```
(1)有效地址送寄存器

LEA d, s ; d← s有效地址

Rc16 ← M有效地址
```

Load Effective Address

+   - 该地址常用用来设置一个16位的寄存器作为地址指针；
+   - 该指令的执行效果与mov reg , offset src相同。

```
LEA bx, [bx][si]
```

| 执行前 | 执行后 |
|--------|--------|
| (bx)=1000h
(si)=2000h | bx=1000h+2000h=3000h |