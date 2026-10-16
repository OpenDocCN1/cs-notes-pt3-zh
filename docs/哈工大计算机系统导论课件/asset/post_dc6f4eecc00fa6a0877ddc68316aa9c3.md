
## 1.2.4 ROL指令

ROL (rotate left) 指令向左移动，并将最高位同时拷贝到CF和最低位中；

![](img/7ab811dea080313a753fa0ae68528fa9_424_0.png)

```assembly
MOV $0x40, %AL
ROL $1, %AL
ROL $1, %AL
ROL $1, %AL

MOV $0x26, %AL
ROL $4, %AL
```

交换一个字节的高4位和低4位！

## 1.2.5 ROR指令

ROR（rotate right）指令向右移动，并将最低位同时拷贝到CF和最高位中；

![](img/7ab811dea080313a753fa0ae68528fa9_426_0.png)

```assembly
MOV $01, %AL
ROR $1, %AL
ROR $1, %AL
```

## 1.2.6 RCL和RCR指令

RCL（rotate carry left）指令按位左移，并将CF拷贝到最低有效位，然后将最高有效位拷贝至CF中；

![](img/7ab811dea080313a753fa0ae68528fa9_427_0.png)

```assembly
CLC
MOV $0x88, %BL
RCL $1, %BL
RCL $1, %BL
```

```assembly
.data
testval: .byte 0x6a

shrb $1, testval
jc quit
rclb $1, testval
```

RCR (rotate carry right) 指令按位右移，并将CF拷贝到最高有效位，然后将最低有效位拷贝至CF中；

![](img/7ab811dea080313a753fa0ae68528fa9_428_0.png)

```assembly
STC
MOV $0x10, %AH
RCR $1, %AH
shr/shl/sal/sar/rol/ror/rcl/rcr %rax #移动1位
```

## 1.2.7 SHLD/SHRD指令

- SHLD（shift left double）双精度左移

将目的操作数左移指定的位数；左移空出来的位用源操作数的高位来填充。

SHLD 移位位数，源操作数，目的操作数

![](img/7ab811dea080313a753fa0ae68528fa9_429_0.png)

- SHRD (shift right double) 双精度右移

将目的操作数右移指定的位数；右移空出来的位用源操作数的低位来填充。

SHRD 目的操作数，源操作数，移位位数

![](img/7ab811dea080313a753fa0ae68528fa9_430_0.png)

### 指令格式

SHLD/SHRD imm8/CL, reg16, reg16

SHLD/SHRD imm8/CL, reg32, reg32

SHLD/SHRD imm8/CL, reg64, reg64

SHLD/SHRD imm8/CL , reg16, mem16

SHLD/SHRD imm8/CL , reg32, mem32

SHLD/SHRD imm8/CL , reg64, mem64

注意：第二个操作数必须是寄存器，不能是mem

### SHLD/SHRD指令的例子

```assembly
varx: .int 0x12
mov $0x12345678, %eax # eax = 0x12345678
mov $0x98765432, %ecx

shld $4, %ecx, %eax # eax = 0x23456789
shrd $4, %ecx, %eax # eax = 0x22345678

mov $4, %cl
movl $0x01234567, varx # varx =0x01234567
shrd %cl, %eax, varx    # varx =0x80123456
```

### 移位指令汇总

| 移位类型 | 左移 | 右移 |
|---|---|---|
| 逻辑移位 | SHL CF | SHR 0 CF |
| 算术移位 | SAL CF | SAR CF |
| 循环移位 | ROL CF | ROR CF |
| 带有进位循环移位 | RCL CF | RCR CF |
| 双精度移位 | SHLD CF 目的操作数 源操作数 | SHRD 源操作数 目的操作数 CF |

所有指令都影响CF和OF

## 1.3 移位和循环移位的应用

- 多双字移位
- 二进制乘法
- 显示二进制位
- 分离位串

### 数组移位：右移1位(intel 格式)

```assembly
.data
  arraysize = 10
  array dword arraysize dup(76543210h)
.code
main PROC
  mov esi, (arraysize-1)*(type array)
  mov ecx, arraysize
  clc
  lahf

L:
  sahf
  rcr array[esi],1
  lahf
  sub esi,type array
  loop L
  exit
main ENDP
END main
```

将上述intel格式代码改写成ATT格式！

### 二进制乘法

- 为了应用SHL，将任意二进制乘数分解成2的幂的和：
  - X * 36 = X * 32 + X * 4 = X * 2^5 + X * 2^2
- X、Y是word或dword类型，分别如何实现 X*Y？

### 分离位串

![](img/7ab811dea080313a753fa0ae68528fa9_437_0.png)

- 将要提取的位移位到寄存器的最低部分
- 清除不相关的位。

## 1.4 乘法和除法指令

- 无符号乘法指令MUL
- 有符号乘法指令IMUL
- 无符号除法指令DIV
- 有符号整数除法指令IDIV
- 算术表达式的实现

### MUL指令

- MUL指令：无符号乘法指令、单操作数
- 指令格式：
  - MUL r/m8 ;AX = AL * r/m8
  - MUL r/m16 ;DX:AX = AX * r/m16
  - MUL r/m32 ;EDX:EAX = EAX * r/m32
  - MUL r/m64 ;RDX:RAX = RAX * r/m64

被乘数、积由乘数隐含指定：

| 乘数 | 被乘数 | 积 |
|---|---|---|
| r/m8 | AL | AX |
| r/m16 | AX | DX:AX |
| r/m32 | EAX | EDX:EAX |
| r/m64 | RAX | RDX:RAX |

操作数不可以是立即数！

如果积的高半部分不为0，则 CF=OF=1

```assembly
mov $0x5,%al
mov $0x20,%bl
mul %bl
```

> 被乘数是AL，乘积被放入AX中
> 根据乘积中高半部分是否为0，设置或清除CF位和OF位
> 处理无符号数，只关心CF标志位

AX= 0x00A0

CF = 0、OF=0

```assembly
.data
val1: .short 0x2000
val2: .short 0x0100
.text
mov val1, %ax
mulw val2
```

> 被乘数是AX，乘积被放入DX: AX中；
> 根据乘积中高半部分是否为0，设置或清除CF位和OF位；
> 处理无符号数，只关心CF标志位。

AX=0x0000
DX=0x0020
CF = 1、OF=1

```assembly
mov $0x12345, %eax
mov $0x1000, %ebx
mul %ebx
```

EAX = 0x12345000
EDX = 0x00000000
CF = 0 OF=0

1. 被乘数是EAX，乘积被放入EDX: EAX中；
2. 根据乘积中高半部分是否为0，设置或清除CF位和OF位；
3. 因为处理的是无符号数，所以只关心CF标志位；

### IMUL指令

IMUL指令：有符号乘法指令

#### IMUL指令的单操作数格式

IMUL r/m8 ;AX = AL*r/m8 byte

IMUL r/m16 ;DX:AX = AX*r/m16 word

IMUL r/m32 ;EDX:EAX=EAX* r/m32 double word

IMUL r/m64 ;RDX:RAX=RAX* r/m64 double word

操作数不可以是立即数！

有效位进位到结果的上半部分（低半部分全是数值位），CF 与 OF 标志设置为 1
