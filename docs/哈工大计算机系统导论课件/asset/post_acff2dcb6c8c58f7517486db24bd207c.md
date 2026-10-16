
## 主要内容: 位、字节 和 整型数

- 信息的位表示
- 位级运算
- 整型数
  - 表示：无符号数和有符号数
  - 无符号数和有符号数的转换
  - 扩展、截断
  - 整数运算：加、非、乘、移位
  - 总结
- 内存、指针、字符串表示

## 面向字节的内存组织管理

![](img/7ab811dea080313a753fa0ae68528fa9_111_0.png)

- **程序用地址来引用内存中的数据**
  - 内存可看做巨大的“字节数组”
    - 实际上不是这样，但不妨这样联想
  - 地址就像这个“字节数组”的索引
    - 指针变量可保存地址数值

- **注意：**
  - 操作系统为每个进程提供私有的地址空间
  - 每个进程可访问自己地址空间中的内存数据，彼此不干扰。

## 机器字

- 任何机器都有一个“字长"
  - 整型值数据的名义长度
  - 地址的名义长度
- 1985年intel 386 CPU开始,大多数机器使用32位 (4字节) 字长
  - 地址空间最大4GB (2³² bytes)
- 目前, 64位字长的机器是主流
  - 潜在地, 可以有16 EB (Exabytes) 的可寻址内存
  - 约18.4 X 10¹⁸字节
- 机器依然支持多种数据格式
  - 字长的一部分或几倍长度
  - 始终是整数个字节

## 面向字的内存组织管理

- **地址**：指定字节的位置
  - 字中第一个字节的地址
  - 相邻字的地址相差 4 (32-bit) 或 8 (64-bit)

![](img/7ab811dea080313a753fa0ae68528fa9_113_0.png)

## C数据类型的典型大小(字节数)

| C 数据类型 | 32位 | 64位 | x86-64 |
|---|---|---|---|
| char | 1 | 1 | 1 |
| short | 2 | 2 | 2 |
| int | 4 | 4 | 4 |
| long | 4 | 8 | 8 |
| float | 4 | 4 | 4 |
| double | 8 | 8 | 8 |
| long double | - | - | 10/16 |
| pointer | 4 | 8 | 8 |

## 字节序

- 有多个字节的 “字” (word)，其各个字节在内存中的排列
- 惯例
  - 大端序、大尾序（Big Endian）: Sun, PPC Mac, Internet
    - 最低有效位（LSB）字节的地址最高
  - 小端序、小尾序（Little Endian）: x86、运行Android 的ARM处理器、iOS和Windows
    - 最低有效位（LSB）字节的地址最低
- 双端序(Bi-Endian)
  - 机器可以配置成大端序或小端序
  - 很多新近的处理器均支持双端序

## 字节序示例

- 示例
- 变量x 有4字节数值0x01234567
- 假定x的地址为 0x100

Big Endian

![](img/7ab811dea080313a753fa0ae68528fa9_116_0.png)

Little Endian

![](img/7ab811dea080313a753fa0ae68528fa9_116_1.png)

## 整数型的表示

```
十进制: 15213
二进制: 0011 1011 0110 1101
16进制: 3 B 6 D
```

```
int A = 15213;
```

![](img/7ab811dea080313a753fa0ae68528fa9_117_0.png)

```
地址 long int C = 15213;
```

![](img/7ab811dea080313a753fa0ae68528fa9_117_1.png)

```
int B = -15213;
```

![](img/7ab811dea080313a753fa0ae68528fa9_117_2.png)

小

大

> 补码表示

> Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

## 验证数的表示

- 打印数据字节表示的程序代码

- 将指针转换成unsigned char * 类型，从而按字节数组处理

```
typedef unsigned char *pointer;

void show_bytes(pointer start, size_t len){
    size_t i;
    for(i = 0; i < len; i++)
        printf("%0xp\t %.2x\n",start+i, start[i]);
    printf("\n");
}
```

printf 指令:
%p: 打印指针
%x: 16进制格式打印

## show_bytes 的执行实例

```
int a = 15213;
printf("int a = 15213;\n");
show_bytes((pointer) &a, sizeof(int));
```

# Result (Linux x86-64):

```
int a = 15213;
0x7fffb7f71dbc    6d
0x7fffb7f71dbd    3b
0x7fffb7f71dbe    00
0x7fffb7f71dbf    00
```

## 大端/小端举例

假设小端方式机器中某条指令的地址为1000

该指令的汇编形式为：mov AX, 0x12345(BX)

其中操作码mov为40H，寄存器AX和BX的编号分别为0001B和0010B，立即数占32位，则存放顺序为：

若在大端机器上，则存放顺序如何？

只需要考虑指令中立即数的顺序！

## 大端/小端举例

以下是一个由反汇编器生成的一行针对IA-32处理器的机器级代码表示文本：

```
80483d2: 89 85 a0 fe ff ff  mov %eax, 0xfffffea0(%ebp)
```

- 其中，80483d2是十六进制表示的指令地址
- 89 85 a0 fe ff ff 是机器指令
- mov %eax, 0xfffffea0(%ebp) 是对应的汇编指令
- 0xfffffea0是立即数

请问：立即数0xfffffea0的值和所存放地址分别是多少？IA-32是大端还是小端方式？

- 立即数0xfffffea0所存放的地址为0x80483d4；
- 立即数0xfffffea0的值为-10110000B=-176；
- IA-32采用的是小端方式！

## 字符串的表示

- **C字符串**
  - 用字符数组表示
  - 每个字符都是ASCII格式编码
    - 字符集的标准7位编码
    - 字符‘0’的编码是 0x30
      - 数码 *i* 的编码是 0x30 + *i*
  - 字符串以null结尾
    - 最后的字符 = 0
  - 兼容性
    - 字节序不是个事！

```
char S[6] = "18213";
```

![](img/7ab811dea080313a753fa0ae68528fa9_123_0.png)

## C的整型数习题 (练习题2.44)

Initialization

```
int x = foo();
int y = bar();
unsigned ux = x;
unsigned uy = y;
```

- x < 0 || ((x*2) < 0)
- ux >= 0
- x & 7 == 7 || (x<<30) < 0
- ux > -1
- x > y || -x < -y
- x * x >= 0
- x > 0 && y > 0 || x + y > 0
- x >= 0 || -x <= 0
- x <= 0 || -x >= 0
- (x|-x)>>31 == -1
- ux >> 3 == ux/8
- x >> 3 == x/8
- x & (x-1) != 0

## 代码范例#2

SUN XDR 函数库

广泛用于机器间传输数据

```
void* copy_elements(void *ele_src[], int ele_cnt, size_t ele_size);
```

![](img/7ab811dea080313a753fa0ae68528fa9_125_0.png)

malloc(ele_cnt * ele_size)
