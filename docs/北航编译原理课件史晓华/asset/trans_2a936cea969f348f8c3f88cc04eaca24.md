

```
program main();
var
  x, y : real;  i, k: integer;
  name: array [1..16] of char;
  :
procedure M1(ind:integer);
  var  x : integer
  procedure P2(j) : real);
  :
  procedure P3;
  var
    f : array [1..5] of integer
    test1: boolean;
    begin
    :
    end; {P3}
  begin
  :
  end;{P2}
procedure q2;
  var r1,r2 : real;
  begin
  :
  P2(r1+r2);
  :
  end; {q2}
begin
  :
  P2(x/y);
  :
end;{M1}
begin
  :
  M1(i+k);
  :
end {main}
```

main
M1
P2
P3
q2
0
1
2
3
2

## 栈式符号表结构

main

M1

P2

P3

q2

栈顶

主程序符号表main

M1符号表

P2符号表

main符号表

M1符号表

P2符号表

P3符号表

main符号表

M1符号表

P2符号表

main符号表

M1符号表

q2

main符号表

M1符号表

main符号表

释放符号表

## Compiler

## 符号表

|  | name | kind | type |
|---|---|---|---|
| 1 | x | var | real |
| 2 | y | var | real |
| 3 | i | var | int |
| 4 | k | var | int |
| 5 | name | var | array |
| 6 | M₁ | proc |  |
| 7 | ind | para | int |
| 8 | x | var | int |
| 9 | P₂ | proc |  |
| 10 | j | para | real |
| 11 | P₃ | proc |  |
| 12 | f | var | array |
| 13 | test1 | var | boolean |

```
program main(...);
var
x, y : real; i, k: integer;
name: array [1...16] of char;
:
procedure M1(ind:integer);
    var x : integer;
    procedure P2(j : real);
        :
        procedure P3;
            var
            f : array [1...5] of integer
            test1: boolean;
            begin
            :
            end; {P3}
        begin
        :
        end;{P2}
    procedure q2;
        var r1,r2 : real;
        begin
        :
        p2(r1+r2);
        :
        end; {q2}
    begin
    :
    P2(x/y);
    :
    end;{M1}
begin
:
M1(i+k);
:
end {main}
```

## 编译q₂说明部分后：

|  |  |  |  |  |  |
|---|---|---|---|---|---|
| 7 | ind | para | int | 1 |  |
| 8 | x | var | int | 1 |  |
| 9 | P₂ | proc |  | 1 | 参数信息 |
| 10 | q₂ | proc |  | 1 | 参数信息 |
| 11 | r₁ | var | real | 2 |  |
| 12 | r₂ | var | real | 2 |  |

```
program main(...);
var
x, y : real; i, k: integer;
name: array [1...16] of char;
:
procedure M1(ind:integer);
var x : integer;
procedure P2(j : real);
:
procedure P3;
var
f : array [1...5] of integer
test1: boolean;
begin
:
end; {P3}
begin
:
end;{P2}
procedure q2;
var r1,r2 : real;
begin
:
p2(r1+r2);
:
end; {q2}
begin
:
P2(x/y);
:
end;{M1}
begin
:
M1(i+k);
:
end {main}
```

编译完q₂过程体：

|  | ind | para | int |  |
|---|---|---|---|---|
| 7 | ind | para | int |  |
| 8 | x | var | int |  |
| 9 | P₂ | proc |  | 参数信息 |
| 10 | q₂ | proc |  | 参数信息 |

当过程和函数体编译完成后，应将与之相应的参数名和局部变量名以及后者的特性信息从符号表中删去。

要求：给出一段程序，会画出其栈式符号表

作业： P185:4, 6

## 第四章补充题

- • 补充题：有如下文法G[E]: 
- E→E+T|T
- T→E|(E)|i
- 1. 求每个非终结符的FIRSTVT和LASTVT集合
- 2. 构造算符优先关系矩阵
- 3. 判断该文法是否为算符优先文法。

## 第六章　运行时的存储组织及管理

- - 概述
- - 静态存储分配
- - 动态存储分配

## 6.1 概述

## (1) 运行时的存储组织与管理

目标程序运行时所需存储空间的组织与管理以及源程序中变量存储空间的分配。

```
例: real a, b, c;
...
a := b*c;
↓
取b
* c
送a
```

符号表
| a | 简单变量 | real |
| b | 简单变量 | real |
| c | 简单变量 | real |
| ..... |  |  |
数据区

## (2) 静态存储分配和动态存储分配

静态存储分配

在编译阶段由编译程序实现对存储空间的管理和为源程序中的变量分配存储的方法。

条 件

如果在编译时能够确定源程序中变量在运行时的 数据空间大小，且运行时不改变，那么 就可以采用静态存储分配方法。

但是并不是所有数据空间大小都能在编译过程中确定

## 动态存储分配

在目标程序运行阶段由目标程序实现对存储空间的组织与管理，和为源程序中的变量分配存储的方法。

## 特 点

- - 在目标程序运行时进行变量的存储分配。
- - 编译时要生成进行动态分配的目标指令。

## 6.2 静态存储分配

## (1) 分配策略

由于每个变量所需空间的大小在编译时已知，因此可以用简单的方法给变量分配目标地址。

- - 开辟一数据区。（首地址在加载时定）
- - 按编译顺序给每个模块分配存储空间。
- - 在模块内部按顺序给模块的变量分配存储，一般用相对地址，所占数据区的大小由变量类型决定。
- - 目标地址填入变量的符号表中。

例：有下列FORTRAN 程序段

```
real      MAXPRN, RATE
integer   IND1, IND2
real      PRINT(100), YPRINT(5,100), TOTINT
```

假设整数占4个字节大小，实数占8个字节大小，则符号表中各变量在数据区中所分配的地址为：

| 名字 | 类型 | 维数 | 地址 |
|---|---|---|---|
| MAXPRN | r | 0 | 264 |
| RATE | r | 0 | 272 |
| IND1 | i | 0 | 280 |
| IND2 | i | 0 | 284 |
| PRINT | r | 1 | 288 |
| YPRINT | r | 2 | 1088 |
| TOTINT | r | 0 | 5088 |

数据区

+8×100

+8×100×5

## （2）模块(FORTRAN子程序)的完整数据区

- - 变量
- - 返回地址
- - 形式参数
- - 临时变量

## FORTRAN子程序的典型数据区

模块n-1

模块n

模块n+1

隐式参数区

形式参数区

局部变量和临时变量区

隐式参数区:返回地址
函数返回值

形式参数区:存放相应实参信息(值或地址)

