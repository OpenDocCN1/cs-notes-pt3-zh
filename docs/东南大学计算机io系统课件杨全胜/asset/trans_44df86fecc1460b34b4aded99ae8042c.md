

## 2.3 Directives

### Data define

### Declaring and Initializing Strings

```
char      BYTE 'a'                ; a
message   BYTE "That's good."      ; That's good.
warn      BYTE 'I don't know.'      ; I don't know.
string    BYTE "The ""key"" is found." ; The "key" is found.
str1      BYTE "This is a long string that does not ",
          "fit on one line."
```

STRING BYTE "HELLO"

| STRING1 | 'H' |
| +1 | 'E' |
| +2 | 'L' |
| +3 | 'L' |
| +4 | 'O' |

## 2.3 Directives

### OFFSET and SEG Operator

- 地址常量由偏移量或段值组成。
  - **OFFSET 操作符**
    - 返回内存位置的偏移量。
  - **SEG 操作符**
    - 返回内存位置的段地址

```
str  BYTE "Hello!", 13, 10, 0
...
mov ax, SEG str      ; Load segment address
mov es, ax
mov bx, OFFSET var ; Load offset address
```

## 2.3 Directives

### Arithmetic Operators

- expression1 + expression2
  - 返回 expression1 加上 expression2
- expression1 − expression2
  - 返回 expression1 减去 expression2
- expression1 * expression2
  - 返回 expression1 乘以 expression2
- expression1 / expression2
  - 返回 expression1 除以 expression2
- −expression
  - 反转 expression 的符号。
- expression1 MOD expression2
  - 返回 expression1 除以 expression2 时余数的整数值（模）

## 2.3 Directives

### Arithmetic Operators

- 算术运算符可用于数值表达式或地址表达式
- 对于地址表达式，结果必须是物理上有意义的。
  - 地址 + 常数 = 地址
  - 地址 - 常数 = 地址
  - 地址 − 地址 = 常数

Example1:
MOV DX, BLOCK+(6-1)*2 ;

```
example2:
ARRAYA DW 1, 2, 3, 4, 5, 6, 7
WENDA  DW ?
MOV CX, (WENDA-ARRAYA)/2 ;
```

## 2.3 Directives

### PTR Operator

```
[type|distance] PTR expression
```

- 强制 expression 被视为具有指定类型。
- type 为 BYTE, WORD, DWORD, FWORD, QWORD 或 TBYTE。

```
Mask BYTE 70H,80H,16H,55H
Task WORD 1234H,9ABCH
MOV DX, WORD PTR Mask ; (DX)← 8070H
MOV AL, BYTE PTR Task ; AL←34H
MOV BYTE PTR[BX], 10 ;
```

- distance 为 near 或 far

```
JMP FAR PTR begin
```

## 2.3 Directives

### SHORT Operator

```
SHORT label
```

- 将 *label* 的类型设为 short。所有跳转到 *short label* 必须为短跳转（从跳转指令到 *label* 的范围在 −128 到 +127 字节之间）。

### EQU and = Operator

```
name EQU expression
name = expression
```

- EQU 和 = 计算 <expression> 的数值并将 resulting 常量值赋给 <name>。
- 与 = 不同，EQU 不允许重新定义数值等式。
- 如果 <expression> 无法求值，EQU 将 <expression> 视为文本。

## 2.3 Directives

### EQU and = Operator

```
Example:
CONST EQU 100*2
ADDRS EQU [BX+10]
CHAR EQU 'COMPUTER'
COUNT = AX
...
MOV BX, CONST ; the same as MOV BX,100*2
MOV BX, COUNT ; the same as MOV BX, AX
MOV ADDRS, 20 ; the same as MOV[BX+10], 20
```

## 2.3 Directives

$ - 位置计数器的当前值

Example1
ARRAY WORD 1, 2, $+4, 3, 4, $+3

Example2
BUFFER DB 1, 2, 3, 4, 5
COUNT EQU $-BUFFER
COUNT = BUFFER 的长度

Example3
OUT 21H, AL
JMP $+2 ;jump to next statement
MOV AX, 0

| ARRAY | 01h | 0074H |
| | 00 |
| 02h | 0076H |
| | 00 |
| 7Ch | 0078H |
| | 00 |
| 03h | 007AH |
| | 00 |
| 04h | 007CH |
| | 00 |
| 81h | 007EH |
| | 00 |

## 2.4 Assembly Language Source Code

### Select Instruction Set

- .8086 使用 8086 指令集
- .286 使用 80286 指令集
- .286P 使用保护模式下的 80286 指令集
- .386 使用 80386 指令集
- .386P 使用保护模式下的 80386 指令集
- .486 使用 80486 指令集
- .486P 使用保护模式下的 80486 指令集
- .586 使用 Pentium 指令集
- .586P 使用 Pentium 指令集
- .MMX 使用 MMX 指令集
- .XMM 使用 SSE 指令集

