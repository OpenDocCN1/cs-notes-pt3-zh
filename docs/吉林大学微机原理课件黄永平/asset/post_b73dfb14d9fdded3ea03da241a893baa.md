
## 六、关于makefile

## MASM32下的makefile.bat

```
@ECHO OFF
: %1为输入的文件名
: 使用: makeit helloworld
: by hyper, http://www.cnblogs.com/hyper99

: 设置MASM32目录
if "%MASM32%"=="" set MASM32=E:\MASM32
path %MASM32%\bin
set AS=ML.exe
set LD=LINK16.exe

: 清除上次编译结果
if exist "%1.obj" del "%1.obj"
if exist "%1.map" del "%1.map"
if exist "%1.lst" del "%1.lst"
if exist "%1.dbg" del "%1.dbg"
if exist "%1.com" del "%1.com"
if exist "%1.exe" del "%1.exe"

: 编译和链接
%AS% /c /Fl /Zd /Zi %1.asm
%LD% /CODEVIEW %1.obj, %1.exe,,,nul.def
pause
```

## 几点注意（变量名，地址标号名，过程名，段名）

HYPer

- 1. 变量名，地址标号名，过程名 都是地址（相对所在段和偏移）

如用X_Name表示时：

```
! 取X_Name段地址
MOV BX, seg X_Name
取X_Name所在段的段值
```

```
! 取X_Name偏移地址
MOV BX, offset X_Name
LEA BX, X_Name
LEA BX, [X_Name]
三者等效
```

变量直接寻址

```
! 取X_Name变量值(DB类型时)
MOV AL, X_Name
MOV AL, [X_Name]
二者等效
```

## 几点注意（变量名，地址标号名，过程名，段名）
HYPer

2.段名，其值为段值（加载时重定位）
如用XSEG表示DSEG、CSEG、SSEG时：

```
;*****1.开始定义数据段**********
DSEG    SEGMENT 'DATA'
DSEG    ENDS

;*****2.开始定义堆栈段**********
SSEG    SEGMENT STACK 'STACK'
SSEG    ENDS

;*****3.开始定义代码段**********
CSEG    SEGMENT 'CODE'
CSEG    ENDS
END     Main ;开始进程是Main
```

! 取XSEG段地址
MOV BX, XSEG

参见MASM5.0生成的LST文件

## 几点注意（常量、变量名）

HYPer

## 3. 常量名 与 变量名

```
! 常量N
N EQU 200h
...
MOV AL, N    ;立即寻址
MOV AL, [N]  ;直接寻址
二者不同
```

```
! 取X变量值(DB类型时)
X DB 20h, 30h, 40h, 50h

MOV AL, X        ;直接寻址
MOV AL, [X]      ;直接寻址
二者等效

MOV AL, X+1      ;直接寻址
MOV AL, [X+1]    ;直接寻址
二者等效
```

![](img/d63acdb9d192b1c4466c984c4275a5a3_418_0.png)

X DB 20h, 30h, 40h, 50h
X只代表20h

## 几点注意（数据传送等宽原则）

HYPer

## 4. 数据传送等宽原则

数据传送等宽原则，也就是类型要正确

! 取X变量值(DB类型时)
X DB 20h, 30h, 40h, 50h

![](img/d63acdb9d192b1c4466c984c4275a5a3_419_0.png)

```
MOV AL, X      ;正确
MOV AL, [X]     ;正确
二者等效
```

```
MOV AX, X       ;! 错误
MOV AX, [X]     ;! 错误
```

```
MOV AX, WORD PTR X      ;正确
MOV AX, WORD PTR [X]    ;正确
```

## 几点注意 ($符)

## 5. $

# 指令中的$

| 段：偏移 | 机器指令 | 汇编指令 |
|---|---|---|
| 1671: 0215 | BB | MOV BX, $  ; $本指令开始位置地址偏移 |
| 1671: 0216 | 15 | |
| 1671: 0217 | 02 | |
|  | 等价于 MOV BX, 0215h | |

# 数据中的$

|  |  |  |
|---|---|---|
| X DW 1234h, $, 5678h |  |  |
| 1671: 0215 | 34 |  |
| 1671: 0216 | 12 |  |
| 1671: 0217 | 17 | ; $所在位置的地址偏移 |
| 1671: 0218 | 02 |  |
| 1671: 0219 | 78 |  |
| 1671: 021A | 56 |  |

## 程序设计方法

主讲人：黄永平

## 目录

- - 概述
- - 顺序程序设计
- - 分支程序设计
- - 循环程序设计
- - 子程序设计
- - 模块化程序设计
- - 高级汇编语言技术

## 一.概述

- - 汇编语言程序设计的一般步骤
- - 流程图

## 汇编语言程序设计的一般步骤

- 1. 分析问题，确定算法
- 2. 绘制流程图
- 3. 分配存储空间和工作单元
- 4. 根据流程图编制程序
- 5. 调试程序

## 流程图

## 1. 流程图的概念

流程图是由特定的几何图形、指向线、文字说明来表示数据处理的步骤，形象描述逻辑控制结构以及数据流程的示意图。流程图具有简洁、明了、直观的特点。

## 2. 流程图符号表示

（1）起止框：表示程序的开始和结束。

![](img/d63acdb9d192b1c4466c984c4275a5a3_425_0.png)

• 起止框

（2）判断框

![](img/d63acdb9d192b1c4466c984c4275a5a3_426_0.png)

（3）处理框

![](img/d63acdb9d192b1c4466c984c4275a5a3_426_1.png)

（4）调用框

![](img/d63acdb9d192b1c4466c984c4275a5a3_426_2.png)

（5）指向线

（6）连接框

![](img/d63acdb9d192b1c4466c984c4275a5a3_427_0.png)

![](img/d63acdb9d192b1c4466c984c4275a5a3_427_1.png)

## 二.顺序程序设计

下面举例说明顺序程序的设计。

【例4.1】试编写一程序计算以下表达式的值。

w = (v - ( x * y + z -540 )) / x

式中x、y、z、v均为有符号字数据。

设x、y、z、v的值存放在字变量X、Y、Z、V中，结果存放在双字变量W之中，程序的流程图如下图所示。

开始

X*Y→(BX:CX)

将z扩展为双字→(DX:AX)

(BX:CX)+(DX:AX)→(BX:CX)

(BX:CX)-540→(BX:CX)

将V扩展成双字→(DX:AX)

(BX:AX)-(BX:CX)→(DX:AX)

(DX:AX)/X，其商→W，余数→W+2

结束

```
源程序如下：
DATA  SEGMENT
X  DW  200
Y  DW  100
Z  DW  3000
V  DW  10000
W  DW  2 DUP ( ? )
DATA  ENDS
STACK SEGMENT STACK
    DB  200 DUP (0)
STACK ENDS
CODE  SEGMENT
    ASSUME DS: DATA, CS: CODE, SS: STACK
```

```
START:      MOV  AX, DATA
MOV DS, AX; DATA→AX
MOV AX, X
IMULY       ; (X) * (Y) →DX: AX
MOV CX, AX
MOV BX, DX; (DX: AX) → (BX: CX)
MOV AX, Z
CWD; (Z) 符号扩展
ADD CX, AX
ADC BX, DX; (BX: CX) + (DX: AX) → (BX: CX)
SUB CX, 540
SBB BX, 0  ; (BX: CX) -540→ (BX: CX)
MOV AX, V
```

```
CWD   ; （V）符号扩展
    SUB AX, CX
    SBB DX, BX      ; （DX: AX）-（BX: CX）→（DX: AX）
    IDIV X          ; （DX: AX）/X
    MOV      W, AX ; 商→W
    MOV      W+2, DX     ; 余数DX→W+2
    MOV      AH, 4CH
    INT  21H
CODE ENDS ; 退出DOS 状态
    END START
```
