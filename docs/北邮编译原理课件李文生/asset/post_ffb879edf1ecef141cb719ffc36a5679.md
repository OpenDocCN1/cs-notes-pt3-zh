
## 示例

```
int m;
int plusv( int n)
{ return m+n; }
int mulv( int n)
{ return m*n; }
void cproc( int pform( int n) )
{ cout << pform(2) << endl; }
void main() {
    m=0;
    cproc(plusv);
    cproc(mulv);
}
```

![](img/12b57169bd1d5004c5e7193ff0d478d5_525_0.png)

## 三、嵌套过程的静态作用域

- 过程定义允许嵌套
- 最近嵌套规则

```
Program sort(input,output);
  var a: array[0..10] of integer;
    x: integer;
  procedure readarray;
    var i: integer;
    begin ... a ... end;
  procedure exchange(i,j:integer);
    begin
      x:=a[i]; a[i]:=a[j]; a[j]:=x
    end;
```

```
procedure quicksort(m,n:integer);
  var k,v: integer;
  function partition(y,z:integer):integer;
    var i,j: integer;
    begin ... a ...;
          ... v ...;
          exchange(i,j);
          ...
    end;
  begin ... end {quicksort};
begin .... ...end {sort}.
```

## 过程及名字的嵌套关系

```
主程序 sort
var a, x

PROC readarray
param. i, j
ref. a, x

PROC exchange
param. i, j
ref. a, x

PROC quicksort
param. m, n
var k, v

FUN partition
param. y, z
var. i, j
ref. a, v
call exchange
```

- 嵌套深度
  - 主程序：1
  - 每进入一个过程，深度加1
- 名字的嵌套深度
  - 声明时所在过程的嵌套深度

## 访问链

- 实现嵌套过程的静态作用域规则
- 通过访问链可以实现对非局部名字的访问

被调用过程活动记录的访问链指向其直接外层过程的最新活动的活动记录

## 访问链的使用

- 过程p引用非局部名字a，嵌套深度分别为nₚ，nₐ
  - nₐ < nₚ
- 当控制处于p中时，p的活动记录在栈顶
- 访问链的使用
  - 从栈顶活动记录出发，沿访问链前进 nₚ - nₐ 步
  - 到达a的声明所在过程的最新活动记录
  - 在该活动记录中，相对于访问链的某个固定偏移处即a的存储位置
  - 该值在编译时可以计算出来
  - 该值在编译时可以计算出来
- 符号表中，变量名字的目标地址：
  - <嵌套深度，偏移量>
- p中非局部名字a的地址：
  - < nₚ - nₐ，a在活动记录中相对于访问链的偏移>

## 访问链的建立

- 在调用序列中由调用过程p创建被调用过程q的访问链
- 过程p和q的嵌套深度分别为nₚ和n_q
- q的活动记录中访问链的建立依赖于q与p的关系
  - q嵌套在p中
    - n_q > n_p
  - q不嵌套在p中
    - n_q = n_p
    - n_q < n_p

## q嵌套在p中——n_q > n_p

- 静态文本中q与p的关系：
- q活动记录中的访问链指向栈中刚好在其前面的p的活动记录的访问链
- 调用序列中，p把top-ep的值写入q的活动记录的访问链

![](img/12b57169bd1d5004c5e7193ff0d478d5_531_0.png)

![](img/12b57169bd1d5004c5e7193ff0d478d5_531_1.png)

## q不嵌套在p中——n_q < n_p

静态文本中q与p的关系：

![](img/12b57169bd1d5004c5e7193ff0d478d5_533_0.png)

- 从p的活动记录出发，沿访问链前进 n_p−n_q 步；
- 找到x₁的活动记录访问链；
- 把x₁的访问链的值复制到q的活动记录中访问链域

## 访问链举例

![](img/12b57169bd1d5004c5e7193ff0d478d5_534_0.png)

## display表

- 目的：为了提高访问非局部名字的速度
- display表：
  - 指针数组d
  - 每一个指针指向一个活动记录
  - d[i]指向嵌套深度为i的过程的最新活动的活动记录
  - 全程数组
  - 元素个数在编译时刻根据过程的最大嵌套深度确定
  - 静态存储分配
  - 控制栈中，具有相同嵌套深度j的各活动记录，从靠近栈顶的最新活动记录开始，通过访问链链成一个链表
  - d[j]是该链表的头指针

## d表应用举例

## 四、动态作用域

- 名字的作用域由程序执行过程中，过程之间的调用与被调用关系决定
- 如过程 p 调用 q，q 又调用 r

![](img/12b57169bd1d5004c5e7193ff0d478d5_537_0.png)

- 访问链的指向：从被调用过程指向调用过程
- 访问链与控制链的指向相同
- 为了访问非局部名字，可能会沿控制链/访问链进入栈的深处——深访问

## 举例

## 静态作用域情况

- 程序

```
program dy_area(input,output);
var r: real;
procedure out_val;
begin write(r:5:3) end;
procedure small;
var r: real;
begin r:=1.1; out_val end;
begin
r:=2.2;
out_val; small; writeln;
out_val; small; writeln;
end.
```

| dy_area |
| 访问链 |
| r 2.2 |
|  |
| small |
| 访问链 |
| r 1.1 |
|  |
| out_val |
| 访问链 |
|  |
|  |

2.2 2.2
2.2 2.2

## 动态作用域情况

- 程序

```
program dy_area(input,output);
var r: real;
procedure out_val;
  begin write(r:5:3) end;
procedure small;
  var r: real;
  begin r:=1.1; out_val end;
begin
  r:=2.2;
  out_val; small; writeln;
  out_val; small; writeln;
end.
```

![](img/12b57169bd1d5004c5e7193ff0d478d5_539_0.png)

2.2 1.1
2.2 1.1

## 浅访问方式

- 动态作用域下，名字可以采用“浅访问”方式进行存储分配
- 做法：
  - 为每个名字在静态分配的存储空间中保存它的值
  - 当控制进入过程p时，p的活动记录入栈，p中的局部名字a接管静态分配给该名字的存储单元，而将该名字的当前值保存在p的活动记录中。
  - 控制在活动p中时，对名字a的访问总是对静态分配给a的存储单元进行存取操作。
  - 当p的活动结束时，再用保存的值恢复a的存储单元。

## 7.4 参数传递机制

过程之间通信的方式：

- 文件
- 非局部名字
- 参数

- 一、传值调用
- 二、引用调用
- 三、复制恢复
- 四、传名调用

```
program reference(input,output);
var a, b : integer;
procedure swap(x, y : integer);
  var temp : integer;
  begin
    temp:=x;
    x:=y;
    y:=temp
  end;
begin
  a:=1; b:=2;
  swap(a, b);
  writeln('a=', a);
  writeln('b=', b)
end.
```
