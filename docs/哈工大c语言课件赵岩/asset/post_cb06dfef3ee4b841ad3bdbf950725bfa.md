
## 通过宏来得到具体的取值范围2

```
#include <float.h>
```

| float | double | long double |
| --- | --- | --- |
| FLT_MAX | DBL_MAX | LDBL_MAX |
| FLT_MIN | DBL_MIN | LDBL_MIN |
| FLT_DIG | DBL_DIG | LDBL_DIG |
| FLT_EPSILON | DBL_EPSILON | LDBL_EPSILON |
| FLT_MAX_EXP | DBL_MAX_EXP | LDBL_MAX_EXP |
| FLT_MIN_EXP | DBL_MIN_EXP | LDBL_MIN_EXP |

## Demo 4: Overflow example

```
1  printf("%d\n", INT_MAX);
2  printf("%d\n", INT_MAX+1);
3  printf("%d\n", INT_MAX+INT_MAX);
4
5  printf("%d\n", INT_MIN);
6  printf("%d\n", INT_MIN+(-1));
7  printf("%d\n", INT_MIN+INT_MIN);
```

## 防止溢出

- 如果不需处理负数，则采用无符号类型。
- 预先估算运算结果的可能范围，采用取值范围更大的类型
- 可能溢出的地方，加入判断语句
- 用ANSI/ISO C定义的宏确定数据的表示范围，解决溢出问题

## 防止溢出

- 如果无需处理负数，则采用无符号类型。
- 预计估算运算结果的可能范围，采用取值范围更大的类型
- 可能溢出的地方，加入判断语句
- 用ANSI/ISO C定义的宏确定数据的表示范围，解决溢出问题

## 防止溢出

- 如果不需处理负数，则采用无符号类型。
- 预先估算运算结果的可能范围，采用取值范围更大的类型
- 可能溢出的地方，加入判断语句
- 用ANSI/ISO C定义的宏确定数据的表示范围，解决溢出问题

## 防止溢出

- 如果不需处理负数，则采用无符号类型。
- 预先估算运算结果的可能范围，采用取值范围更大的类型
- 可能溢出的地方，加入判断语句
- 用 ANSI/ISO C 定义的宏确定数据的表示范围，解决溢出问题

## 浮点型的有效位

Demo 5: A simple example of float

```
#include <stdio.h>
main(){
    float i = 1234567890;
    i += 20;
    printf("%f", i);
}
```

- 有位数是7位
- 从左到右的七个数是对的，与小数点无关
- 并不代表数据就只有7位，修改%.15f试试看。

## 浮点数相等判断

Demo 6: A simple example of float

```
#include <math.h>
#include <float.h>
main(){
    float f = 0.11f, int = i;
    for(i = 0; i<5; i++){
        f += 0.11f;
        if(f == 0.33f) /* wrong way */
        /* if(fabs(f-0.33f)<FLT_EPSILON) */
            printf("Equal");
    }
}
```

## 数据类型注意事项-口诀

- 297两头两头
- 29代表int的最大数是2后面接9个数
- 7代表浮点型有效位为7位
- 两头为：*_MAX和*_EPSILON
- 两头为：limits.h和float.h

## 字符型char

- 代表一个数
  - 有符号，代表 (-128-127)
  - 无符号，代表 (0-255)
- 保存一个字符
  - ASCII（美国标准信息交换码）编码，附录E
  - 可打印字符
  - 不可打印字符（控制字符）

## 字符型char

- 代表一个数
  - 有符号，代表 (-128-127)
  - 无符号，代表 (0-255)
- 保存一个字符
  - ASCII（美国标准信息交换码）编码，附录E
  - 可打印字符
  - 不可打印字符（控制字符）

## ASC码表

000 (nul) 016 ► (dle) 032 sp 048 0 064 @ 080 P 096 ` 112 p
001 ☺ (soh) 017 ‡ (dc1) 033 ! 049 1 065 A 081 Q 097 a 113 q
002 ☻ (stx) 018 ♥ (dc2) 034 " 050 2 066 B 082 R 098 b 114 r
003 ♥ (etx) 019 ♠ (dc3) 035 # 051 3 067 C 083 S 099 c 115 s
004 ♦ (eot) 020 ♣ (dc4) 036 $ 052 4 068 D 084 T 100 d 116 t
005 ♣ (enq) 021 ♠ (nak) 037 % 053 5 069 E 085 U 101 e 117 u
006 ♠ (ack) 022 ♣ (syn) 038 & 054 6 070 F 086 V 102 f 118 v
007 ♣ (bel) 023 ♥ (etb) 039 ' 055 7 071 G 087 W 103 g 119 w
008 ■ (bs) 024 ♠ (can) 040 ( 056 8 072 H 088 X 104 h 120 x
009 □ (ht) 025 ♣ (em) 041 ) 057 9 073 I 089 Y 105 i 121 y
010 (lf) 026 ♠ (sub) 042 * 058 : 074 J 090 Z 106 j 122 z
011 δ (vt) 027 ♣ (esc) 043 + 059 ; 075 K 091 [ 107 k 123 {
012 φ (np) 028 ♠ (fs) 044 , 060 < 076 L 092 \ 108 l 124 |
013 ♠ (cr) 029 ♣ (gs) 045 - 061 = 077 M 093 ] 109 m 125 }
014 ♣ (so) 030 ♥ (rs) 046 . 062 > 078 N 094 ^ 110 n 126 ~
015 ♠ (si) 031 ▼ (us) 047 / 063 ? 079 O 095 _ 111 o 127 ◊

## char型与int型的关系

Demo 6: A simple example about char

```
1  char ch = 'b';
2  printf("%c, %d\n", ch, ch);
3  ch = 'b'-('a'-'A');  /*ch = 'b' - 32;*/
4  printf("%c, %d\n", ch, ch);
```

Demo 7: char or integer

```
1  char c; /* unsigned char c, what happen? */
2  while((c=getchar())!=EOF){
3    putchar(c);
4  }
```

## 总结

数据类型

常量和变量

变量

常量

常数

基本符号

保留字

标识符

注意事项

溢出

存储长度

浮点型的有效位

基本数据类型

整形

浮点型

字符型

谢谢大家，欢迎提问！

## C语言
第2讲: 运算符和表达式

赵岩

哈尔滨工业大学软件学院

September 2, 2011

## 目录

- 变量和常量
  - 变量
  - 常量

## 目录

- 变量和常量
  - 变量
  - 常量
- 运算符
  - 算术运算符
  - 关系与逻辑运算符
  - 特殊运算符

## 目录

- 变量和常量
  - 变量
  - 常量
- 运算符
  - 算术运算符
  - 关系与逻辑运算符
  - 特征运算符
- 类型转换
  - 自动类型转换
  - 强制类型转换
- 运算符优先级与结合性

## 变量定义

- 变量定义语句：
  - <数据类型名> <变量名列表>;
  - 例1： int i, j, k;
  - 例2： long l1, l2;
  - 例3： int i=3, j=5, k=i+j;
- 变量名：其命名规则同标识符。
