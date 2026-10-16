
# “While” 的实现#2

- “Do-while” 转换
- 使用选项 -O1

```
while ( Test )
Body
```

```
if (! Test)
goto done;
do
Body
while(Test);
done:
```

```
if (! Test)
goto done;
loop:
Body
if ( Test)
goto loop;
done:
```

> Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

# While循环——例2

## C代码

```c
long pcount_while
  (unsigned long x) {
  long result = 0;
  while (x) {
    result += x & 0x1;
    x >>= 1;
  }
  return result;
}
```

## Do-While版本

```c
long pcount_goto_dw
  (unsigned long x) {
  long result = 0;
  if (!x) goto done;
loop:
  result += x & 0x1;
  x >>= 1;
  if(x) goto loop;
done:
  return result;
}
```

- 与do-while版本的函数对比
- 初始条件守护循环的入口

# "For" 循环形式

一般形式

```
for(Init, Test, Update)
Body
```

循环初始化(Init)

```
i = 0
```

循环条件测试(Test)

```
i < WSIZE
```

更新(Update)

```
i++
```

循环体(Body)

```
{
  unsigned bit =
    (x >> i) & 0x1;
  result += bit;
}
```

```
#define WSIZE 8*sizeof(int)
long pcount_for(unsigned long x){
size_t i;
long result = 0;
for (i = 0; i < WSIZE; i++) {
  unsigned bit =
    (x >> i) & 0x1;
  result += bit;
}
return result;
}
```

# “For” 循环→ While循环

For版本

```
for (Init; Test; Update)
    Body
```

While版本

```
Init;
while ( Test ) {
    Body
    Update;
}
```

# For-While 转换

循环初始化

```
i = 0
```

循环条件测试

```
i < WSIZE
```

更新

```
i++
```

循环体

```
{
unsigned bit =
(x >> i) & 0x1;
result += bit;
}
```

```
long pcount_for_while
(unsigned long x)
{
size_t i;
long result = 0;
i = 0;
while (i < WSIZE)
{
unsigned bit =
(x >> i) & 0x1;
result += bit;
i++;
}
return result;
}
```

# For 循环的Do-While实现

## goto版本

## C代码

```
long pcount_for(unsigned long x)
{
    size_t i;
    long result = 0;
    for (i = 0; i < WSIZE; i++)
    {
        unsigned bit =
            (x >> i) & 0x1;
        result += bit;
    }
    return result;
}
```

```
long pcount_for_goto_dw(unsigned long x) {
    size_t i;
    long result = 0;
    i = 0; Init
    if (!(i < WSIZE))
        goto done;
    loop:
    {
        unsigned bit = (x >> i) & 0x1; Body
        result += bit;
    }
    i++; Update
    if (i < WSIZE) Test
        goto loop;
    done:
    return result;
}
```

初始化测试被优化删除

# 主要内容

- 流程控制:条件码(状态标志位)
- 条件分支
- 循环结构的实现
- **Switch语句**

# Switch语句

- **多case标号**
  - 本例：5 & 6
- **下穿case语句**
  - 本例：2
- **缺失的case**
  - 本例：4

```
long switch_eg (long x, long y, long z){
    long w = 1;
    switch(x) {
    case 1:
        w = y*z;
        break;
    case 2:
        w = y/z;
        /* 下穿Fall Through */
    case 3:
        w += z;
        break;
    case 5:
    case 6:
        w -= z;
        break;
    default:
        w = 2;
    }
    return w;
}
```

# 跳转表结构

Switch语句

```
switch(x) {
case val_0:
  Block 0
case val_1:
  Block 1
  ...
case val_n-1:
  Block n-1
}
```

JTab:

跳转表

![](img/7ab811dea080313a753fa0ae68528fa9_539_0.png)

跳转目标

![](img/7ab811dea080313a753fa0ae68528fa9_539_1.png)

翻译 (Extended C)

```
goto *JTab[x];
```

# Switch语句示例

```
long switch_eg(long x, long y, long z)
{
    long w = 1;
    switch(x) {
    ...
    }
    return w;
}
```

| 寄存器 | 用途 |
| --- | --- |
| %rdi | 参数x |
| %rsi | 参数y |
| %rdx | 参数z |
| %rax | 返回值 |

汇编实现：

```
switch_eg:
    movq  %rdx, %rcx
    cmpq  $6, %rdi  # x:6
    ja    .L8
    jmp   *.L4(, %rdi, 8)
```

注意：此处没有w及初始化

属于default的数值范围？

# Switch语句示例

```
long switch_eg(long x, long y, long z)
{
    long w = 1;
    switch(x) {
        ...
    }
    return w;
}
```

# 跳转表

```
.section .rodata
.align 8
.L4:
    .quad .L8 # x = 0
    .quad .L3 # x = 1
    .quad .L5 # x = 2
    .quad .L9 # x = 3
    .quad .L8 # x = 4
    .quad .L7 # x = 5
    .quad .L7 # x = 6
```

汇编实现：

```
switch_eg:
    movq %rdx, %rcx
    cmpq $6, %rdi   # x:6
    ja  .L8         # Use default
    jmp *.L4(, %rdi, 8) # goto *JTab[x]
```

间接跳转

# 汇编实现的解释

- 表结构
  - 每个目标需8字节
  - 基地址为 .L4

- 跳转指令
  - 直接跳转：jmp .L8
    跳转到标号 .L8处
  - 间接跳转：jmp *.L4(, %rdi, 8)
    跳转表的起始地址：.L4
  - 必须以8为比例因子 (地址是8字节)
  - 0 ≤ x ≤ 6时，从有效地址 .L4 + x*8处获取目标地址

```
跳转表
.section .rodata
.align 8
.L4:
    .quad .L8 # x = 0
    .quad .L3 # x = 1
    .quad .L5 # x = 2
    .quad .L9 # x = 3
    .quad .L8 # x = 4
    .quad .L7 # x = 5
    .quad .L7 # x = 6
```
