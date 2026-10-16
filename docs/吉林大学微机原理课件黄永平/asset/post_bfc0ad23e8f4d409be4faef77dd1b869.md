
```
STACKO      MACRO A
```

```
STACK        SEGMENT      STACK
```

```
    DB      A
```

```
STACK        ENDS
```

```
    ENDM
```

现要从键盘输入一串字符到系统缓冲区，然后将字符按相反顺序打印，采用调用宏库的办法，其程序如下：

```
INCLUDE           MACRO.LIB
STACK0 <200        DUP (0) >        ; 定义堆栈段
DATA               SEGMENT
INFO1              DB  ‘INPUT STRING: $’
INFO2              DB  ‘OUTPUT STRING: $’
BUFA               DB  81
                   DB  ?
                   DB  80 DUP (0)
```

```
BUFB          DB 81 DUP (0)
DATA          ENDS
CODE          SEGMENT
              ASSUME DS: DATA, SS: STACK, CS: CODE
START:        MOV   AX, DATA
              MOV   DS, AX
              RETURN      ; 输出回车换行
              PRINT INFO1 ; 输出字符变量INFO1 代表的字符
字符串
              INPUT BUFA  ; 键盘输入字符中到缓冲区；
              LEA   SI, BUFA+1
              MOV   CH, 0
              MOV   CL, [SI]
              ADD   SI, CX
              LEA   DI, BUFB
```

```
NEXT:
MOV AL, [SI]
MOV [DI], AL
DEC SI
INC DI
LOOP NEXT
MOV BYTE PTR [DI], '$'
RETURN ; 输出回车换行
PRINT INFO2 ; 输出的字符串变量INFO2代表
PRINT BUFB ; 反向输出输入字符串
MOV AH, 4CH
INT 21H
CODE ENDS
END START
```

## 4.7.6 重复汇编

- 1. 给定次数的重复汇编伪指令
  
  语句格式：`REPT` 表达式
  
  重复块
  
  `ENDM`
  
  功能：宏汇编程序将重复块连续地汇编表达式给定的次数。

- 2. 不定次数的重复汇编伪指令，有 IRP 和 IRPC 两种伪指令。

## 【例4.22】

某一源程序需要多次将AX, BX, CX, DX寄存器的内容压入堆栈，则可定义如下宏指令。

```
PUSHR      MACRO
           IRP  REG,  <AX, BX, CX, DX>
           PUSH REG
           ENDM
           ENDM
```

调用上述宏定义后，将展开成下列语句：

```
+ PUSH  AX
+ PUSH  BX
```

+ PUSH CX
+ PUSH DX
又如：
IRP W, 〈1122H, 3344H, 5566H, 7788H〉
DW W
ENDM
汇编程序在汇编时将产生语句：
+ DW 1122H, 3344H, 5566H, 7788H。
（2）IRPC
语句格式：IRPC 形参, 字符串
重复块
ENDM

## 4.7.7 条件汇编

条件汇编指在汇编期间，宏汇编程序根据条件是否成立决定具体汇编哪一程序段。条件汇编用条件汇编伪指令来定义。如表4.1所示。

语句格式： IF ×× 表达式

```
条件块1
[ELSE
条件块2]
ENDIF
```

| 伪指令 | 汇编条件 |
|---|---|
| IF 表达式 | 表达式≠0，则条件为真 |
| IFE 表达式 | 表达式=0，则条件为真 |
| IF 1 | 是第一次扫描则为真 |
| IF 2 |  |
| IFDEF 符号 | 符号已定义或被说明为外部符号，条件为真 |
| IFNDEF 符号 | 符号未定义或没被说明为外部符号，条件为真 |
| IFB 变量 | 变量为空格，则条件为真 |
| IFNB 变量 | 变量不为空格，则条件为真 |
| IFIDN 变量1, 变量2 | 字符串变量1与字符串变量2相等，则条件为真 |
| IFNIDN 变量1, 变量2 | 字符串变量1与字符串变量2不相等，则条件为真 |

•表4.1 条件汇编伪指令

## 【例4.25】试用条件汇编编写一宏定义，能完成多种DOS系统功能调用。

源程序如下：

```
DOSYS        MACRO N, BUF
             IFE     N
             EXITM
             ENDIF
             IFDEF  BUF
             LEA     DX, BUF
             MOV     AH, N
             INT     21H
             ELSE
```

```
MOV AH, N
INT 21H
ENDIF
ENDM

; .......................
DATA SEGMENT
MSG DB 'INPUT STRING: $'
BUF DB 81, 0, 80 DUP (0)
DATA ENDS

STACK SEGMENT STACK
DB 200 DUP (0)
```

```
STACK      ENDS
CODE       SEGMENT
           ASSUME DS: DATA, CS: CODE, SS: STACK
BEGIN:     MOV   AX, DATA
           MOV   DS, AX
           DOSYS 9, MSG
           DOSYS 10 , BUF
           DOSYS 4CH
CODE ENDS
END  START
```

则以上三条宏指令展开后的语句为：

```
+ LEA    DX, MSG
+ MOV    AH, 9
+ INT    21H
+ LEA    DX, BUF
+ MOV    AH, 10
+ INT    21H
+ MOV    AH, 4CH
+ INT    21H
```

## 存储器及接口

主讲人：黄永平

## 目录

![](img/d63acdb9d192b1c4466c984c4275a5a3_524_0.png)

## 本章学习目标

- ■ 掌握半导体存储器的分类、组成及组成部件的作用及工作原理、读/写操作的基本过程。

- ■ 掌握SRAM、DRAM芯片的组成特点、工作过程、典型芯片的引脚信号、了解DRAM刷新的基本概念。

- ■ 掌握半导体存储器的主要技术指标、芯片的扩充、CPU与半导体存储器间的连接。

- ■ 了解Cache的基本概念、特点、在系统中的位置。

## 一、存储器的分类

存储器就是用来存储程序和数据的，程序和数据都是信息的表现形式。按照存取速度和用途可把存储器分为两大类：**内存存储器**（简称内存，又称主存储器）和**外存储器**。存储器的容量越大，记忆的信息也就越多，计算机的功能也就就越强。

### 1、存储器的分类

![](img/d63acdb9d192b1c4466c984c4275a5a3_527_0.png)

### 2、半导体存储器性能

- ■ 存储容量：
  存储容量=存储单元个数x存储字长(每单元位数)

- ■ 存储速度：用存取时间和存取周期表示。

  - ● 存取时间(访问时间)---包括读出时间，和写入时间。

  - ● 存取周期---连续两次读操作或写操作的时间。

### 2、半导体存储器结构

![](img/d63acdb9d192b1c4466c984c4275a5a3_529_0.png)

存储器基本原理

### 2、半导体存储器结构

![](img/d63acdb9d192b1c4466c984c4275a5a3_530_0.png)

### 3、静态RAM ----一位存储单元

![](img/d63acdb9d192b1c4466c984c4275a5a3_531_0.png)
