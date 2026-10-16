
I6 → E → E or E ., $ | and | or 213
E → E . and E , $ | and | or
E → E . or E , $ | and | or

![](img/353f619caa6c5715591f2105bdfa2865_636_0.png)

I7 → I5 and
I7 → I6 or

I8 → E → (E) ., $ | and | or 214

I8 and → E → E and . E , ) | and | or 215
E → . E and E , ) | and | or
E → . E or E , ) | and | or
E → . not E , ) | and | or
E → . (E) , ) | and | or
E → . b , ) | and | or

I8 or → E → E or . E , ) | and | or 216
E → . E and E , ) | and | or
E → . E or E , ) | and | or
E → . not E , ) | and | or
E → . (E) , ) | and | or
E → . b , ) | and | or

![](img/353f619caa6c5715591f2105bdfa2865_638_0.png)

# 构造 LR(0) 分析表

(0) S' → E
(1) E → E and E
(2) E → E or E
(3) E → not E
(4) E → ( E )
(5) E → b

| States | ACTION |  |  |  |  |  |  | GOTO |
|---|---|---|---|---|---|---|---|---|
|  | and | or | not | ( | ) | b | $ | E |
| 0 |  |  | S2 | S3 |  | S4 |  | 1 |
| 1 | S5 | S6 |  |  |  |  | accept |  |
| 2 |  |  | S2 | S3 |  | S4 |  | 7 |
| 3 |  |  | S9 | S10 |  | S11 |  | 8 |
| 4 | r5 | r5 |  |  |  |  | r5 |  |
| 5 |  |  | S2 | S3 |  | S4 |  | 12 |
| 6 |  |  | S2 | S3 |  | S4 |  | 13 |
| 7 | S?Y3 | S?Y3 |  |  |  |  | r3 |  |
| 8 | S5 | S6 |  |  | S14 |  |  |  |
| 9 |  |  | S9 | S10 |  | S11 |  | 17 |
| 10 |  |  | S9 | S10 |  | S11 |  | 18 |
| 11 | r5 | r5 |  |  | r5 |  |  |  |
| 12 | r? | r? |  |  |  |  | r? |  |
| 13 | r5 r? | r5 r? |  |  |  |  | r? |  |
| 14 | r? | r? |  |  |  |  | r? |  |
| 15 |  |  | S9 | S10 |  | S11 |  | 19 |
| 16 |  |  | S9 | S10 |  | S11 |  | 20 |
| 17 | S?Y3 | S?Y3 |  |  | r3 |  |  |  |
| 18 | S15 | S16 |  |  | S21 |  |  |  |
| 19 | S?Y1 | S?Y1 |  |  | r1 |  |  |  |
| 20 | S?R? | S?R? |  |  | r2 |  |  |  |
| 21 | r4 | r4 |  |  | r4 |  |  |  |

# ③ 附加条件：not ← and

not > and，not > or，and > or；and、or：左结合；not：右结合

因此：S5 r3 not > and ⇒ r3，S6 r3 not > or ⇒ r3

S5 r1 and left ⇒ r1 S6 r1 and > or ⇒ r1

S5 r2 and > or ⇒ S5 S6 r2 or left ⇒ r2

S15 r3 not > and ⇒ r3 S16 r3 not > or ⇒ r3

S15 r1 and left ⇒ r1 S16 r1 and > or ⇒ r1

S15 r2 and > or ⇒ S15 S16 r2 or left ⇒ r2

# 复习

6. 重要知识点

+   - 第5章
+     - 属性
+     - 带注释的分析树
+       - 为表达式构造带注释的分析树（S-属性）
+     - 语法制导定义
+     - S-属性文法和S-属性的求值
+       - 为S-属性文法构造语义规则

请为输入串 111.0111 构造带注释的分析树，其中语法制导定义如下：

# 产生式

# 语义规则

S→L₁.L₂

{S.val=L₁.val+L₂.val/2^L2.len}

S→L

{S.val=L.val}

L→L₁B

{L.val=L₁.val*2+B.val, L.len=L₁.len+1}

L→B

{L.val=B.val,L.len=1}

B→0

{B.val=0}

B→1

{B.val=1}

1
↓
B.val=1
↓
L.val=1
L.len=1

1
↓
B.val=1

1
|
B.val=1

L.val=3
L.len=2

L.val=7
L.len=3

0
|
B.val=0
|
L.val=0
L.len=1

1
|
B.val=1

1
|
B.val=1

1
|
B.val=1

L.val=1
L.len=2

L.val=3
L.len=3

L.val=7
L.len=4

S.val=7 7/16 = 7.4375

# 复习

# 6. 重要知识点

+   - 第6章
+     - 类型
+     - 类型表达式
+   - 为声明构造类型表达式

# 复习

# 6. 重要知识点

+   - 第7章
+     - 基于栈的存储分配
+       - 活动记录形式
+       - C 语言程序
+         - 递归函数
+       - Pascal 语言程序
+         - 显示表（Display）
+       - 为 C 递归程序构造最大栈映射

我们假设 C 语言程序运行时栈存储分配所使用的存储组织和活动记录形式如上所述。请为下列 C 程序构造达到最大大小的时候的运行时栈映射。

C 程序如下：

```
#include <stdio.h>
int x,y,z;
int main()
{
x=35;
y=40;
z=f(x,y);
}
int f(int m, int n)
{
if (n>m) {
int t;
t=f(n,m);
return t }
else
if (n==0) return m;
else {
int t1,t2;
t1=m % n; //remainder of m/n
t2=f(n,t1);
return t2
}
}
```

注：1）这里我们假设 Main 函数的调用者的 sp 是全局变量数据区的起始地址，函数（包括 Main 函数）活动记录中的返回地址由操作系统自动填充，你可以不必关心它。

2）变量 X 和 Y 的初始值分别为 35 和 40，程序所用栈的起始地址为 K。
