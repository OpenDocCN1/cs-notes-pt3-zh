

## 2.6.1 数据传输指令

## MOV 指令

```
MOV DST , SRC
```

DST<--(SRC) ; Copy data from SRC to DST

| 符号 | 示例 |
|---|---|
| MOV reg8/16/32, imm8/16/32 | MOV EAX, 7327FAB2H |
| MOV reg8/16/32, reg8/16/32 | MOV AH, DL |
| MOV reg8/16/32, mem8/16/32 | MOV DX, WORD PTR[BX] |
| MOV mem8/16/32, reg8/16/32 | MOV BYTE PTR[DI], AL |
| MOV mem8/16/32, imm8/16/32 | MOV BYTE PTR[DI], 30 |
| MOV seg, reg16 | MOV DS, AX |
| MOV reg16, seg | MOV AX, DS |
| MOV seg, mem16 | MOV DS, WORD PTR[BX] |
| MOV mem16, seg | MOV WORD PTR[BX], DS |

- 源操作数和目的操作数不可用的组合
  - 源和目的都在内存中
  - 立即数源到段寄存器
  - 移动到或来自标志寄存器
  - 移动到指令指针寄存器
  - 移动到 CS
  - 从一个段寄存器移动到另一个段寄存器
  - 操作数大小不同
  - 移动多个对象

## MOV 指令

# 合法或非法？

```
val1 byte 100
val2 byte 200
number equ 100
```

```
mov val1 , val2
mov number , val2
mov val2, number
mov ds, offset val1
mov ax, offset val1
mov al, -40
```

```
mov al, ds
mov ds, ax
mov es, ds
mov ax, es
mov val, al
mov al, 0D8h
```

## PUSH 指令

```
PUSH SRC
```

- 将数据保存到 LIFO 栈
- 对于 16 位
  1. SP<--(SP)-2
  2. ((SP)+1,(SP))<--(SRC)
- 对于 32 位
  1. ESP←(ESP)-4
  2. ((ESP)+3,(ESP)+2,(ESP)+1,(ESP))←(SRC)

示例：

PUSH AX

执行前

AX
3125H

Lower addr.
SP →
52500H

执行后

AX
3125H

Lower addr.
SP →
25H 524FEH
31H 524FFH
52500H

## POP 指令

```
POP DST
```

- 从 LIFO 栈中检索数据
- 对于 16 位
  1. DST<--((SP)+1,(SP))
  2. SP<--(SP)+2
- 对于 32 位
  1. DST←((ESP)+3,(ESP)+2,(ESP)+1,(ESP))
  2. (ESP)←(ESP)+4

示例：

POP BX

执行前

BX

75C1H

执行后

BX

48h 6Bh

lower addr.

SP

6Bh

51000H

48h

1H

9Ah

2H

28h

3H

SP

6Bh

51000H

lower addr.

48h

1H

9Ah

2H

28h

3H

| 符号 | 示例 |
|---|---|
| `POP reg16/32` | `POP AX, POP EBX` |
| `POP mem16/32` | `POP WORD PTR[EBX+2] , POP VAR` |
| `POP seg` | `POP DS` |
| `POPA` | `POPA; pops di, si, bp, sp, bx, dx, cx, ax` |
| `POPAD` | `POPAD; pops edi, esi, ebp, esp, ebx, edx, ecx, eax` |
| `POPF` | `Pop flags` |
| `POPFD` | `Pop EFLAGS` |

> 注意：不能弹出 CS

## 加载有效地址指令

```
LEA reg16/32, mem8/16/32
```

将 16 或 32 位寄存器加载为操作数指定的数据的偏移地址。

![](img/d7c975450dfbe59120092c2721be78c6_154_0.png)

### LEA 指令

**LEA DI, BUFFER**  
; 将 BUFFER 的有效地址传输到 DI

DI `1234H`

BUFFER → 2000H:1234H

**MOV DI, BUFFER**  
; 将地址 BUFFER 的内容传输到 DI

DI `5678H`

|  | 值 |
|---|---|
| 5H | 56H |
|  | 78H |

# LEA 和 OFFSET 有什么不同？

```
LDS  reg16/32, mem32/48
LES  reg16/32, mem32/48
LFS  reg16/32, mem32/48
LGS  reg16/32, mem32/48
LSS  reg16/32, mem32/48
```

- 使用偏移地址加载任意 16 或 32 位寄存器，并使用段地址加载 DS、ES、FS、GS 或 SS 段寄存器。
- 使用任意内存寻址模式访问包含段和偏移地址的 32 或 48 位内存段。

## 杂项数据传输指令

### XCHG 指令

- 交换寄存器的内容与任何其他寄存器或内存位置的内容。
- 不能交换段寄存器或内存到内存数据

| 符号 | 示例 |
|---|---|
| XCHG *reg8/16/32*, *reg8/16/32* | XCHG AL,CL |
| XCHG *reg8/16/32*, *mem8/16/32* | XCHG AX,DATA1 |
| XCHG *mem8/16/32*, *reg8/16/32* | XCHG DATA2, EAX |

