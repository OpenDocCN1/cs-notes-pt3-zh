
## 5.3.3 依赖图_获得语义规则的计算顺序

依赖图就是一个有向图，用于描述分析树中节点的属性和属性间的相互依赖关系，称为分析树的依赖图

每个属性对应依赖图中的一个结点，如果属性b依赖与属性C，则从C的结点有一条有向边指向属性b的。

属性间的依赖关系是根据相应的语义规则确定的

## 依赖图的构造方法

for 分析树中的每个结点 n do
for 与结点 n 对应的文法符号的每个属性 a do
在依赖图中为 a 构造一个结点；
for 分析树的每个结点 n do
for 结点 n 所用产生式对应的每条
语义规则 b := f (c₁, c₂, ..., cₖ) do
for i := 1 to k do
从结点 cᵢ 到结点 b 构造一条有向边；

## 带有继承属性L.in的翻译方案

```
D→T { L·in:=T·type } L
T→int { T·type :=integer }
T→real { T·type :=real }
L→{L₁·in :=L·in}
    L₁,id{addtype(id·entry,L·in)}
L→id { addtype(id·entry,L·in) }
```

## 例5.3 变量说明的类型定义

int a, b, c

句子int a,b,c的带继承属性的分析树

## Int a, b, c的依赖图

![](img/46a88313606013b1cd4872a55f78bee2_500_0.png)

## 5.3.4 计算顺序

## 拓扑排序

一个无环有向图的拓扑排序是图中结点的任何顺序 m₁, m₂, ..., mₖ, 使得边必须是从序列中前面的结点指向后面的结点，也就是说，如果 mᵢ→mⱼ 是 mᵢ 到 mⱼ 的一条边,那么在序列中 mᵢ 必须出现在 mⱼ 的前面。

若依赖图中无环，则存在一个拓扑排序，它就是属性值的计算顺序。

## 5.3.4 计算顺序

- 无前驱的顶点优先拓扑排序法：
- 1。 寻找入度为0的点，输出
- 2。 删除其所有边
- 3。 再找入度为0的点，输出
- 4。 重复上述过程，直到全部输出

## Int a, b, c的依赖图的拓扑排序是：

```
1, 2, 3, 4, 5, 6, 7, 8, 9, 10
$a_4:=real;$
$a_5:=a_4;$
$addtype(id_3.entry, a_5);$
$a_7:=a_5;$
$addtype(id_2.entry, a_7);$
$a_9:=a_7;$
$addtype(id_1.entry, a_9);$
```

## 5.4 语法树（syntax tree）的构造

## ——语法制导定义中的属性计算示例

- 抽象语法（abstract syntax）

从具体语法中抽象出语言结构的本质性的东西，而不考虑语言的具体符号表示，从而可简化语义的形式描述。

在不同的语言中赋值语句有不同的写法：

`x=y;  x:=y;  y→x`

等等，可以用抽象形式

```
assignment (variable, expression)
```

把前面各种具体形式统一起来。

## 5.4.1 语法树

表示程序层次结构的树，它把分析树中对语义无关紧要的成分去掉，是分析树的抽象形式，也称作语法结构树，或结构树。

语法树是常用的一种中间表示形式。

## 5.4.1 语法树(续)

产生式S→if B then S₁ else S₂的语法树

if-then-else
/ | \
B S₁ S₂

赋值语句的语法树

assignment
/ \
variable expression

在语法树中，运算符符号和关键字都不在叶结点，而是内部结点中出现。

## 5.4.2 构造表达式的语法树

构造表达式的语法树使用的函数

- 1. **mknode(op, left, right)** 建立一个标记为op的运算符结点，两个域left和right是指向左右运算对象的指针。
- 2. **mkleaf(id, entry)** 建立一个标记为id的标识符结点，其域entry是指向该标识符在符号表中相应表项的指针。
- 3. **mkleaf(num, val)** 建立一个标记为num的数结点，域val用于保存该数的值。返回指向新建立结点的指针。

## 例 a-4+c的语法树

![](img/46a88313606013b1cd4872a55f78bee2_509_0.png)

## 5 4.3 构造语法树的语法制导定义

| 产生式 | 语义规则 |
|---|---|
| $E \rightarrow E_1 + T$ | $E.nptr := mknode('+', E_1.nptr, T.nptr)$ |
| $E \rightarrow E_1 - T$ | $E.nptr := mknode('-', E_1.nptr, T.nptr)$ |
| $E \rightarrow T$ | $E.nptr := T.nptr$ |
| $T \rightarrow (E)$ | $T.nptr := E.nptr$ |
| $T \rightarrow id$ | $T.nptr := mkleaf(id, id.entry)$ |
| $T \rightarrow num$ | $T.nptr := mkleaf(num, num.val)$ |

## 图 a-4+c的语法树的构造

![](img/46a88313606013b1cd4872a55f78bee2_511_0.png)

## 5.5 S-属性定义的自底向上计算

在分析栈中使用一个附加的域来存放综合属性值。下图为一个带有综合属性值域的分析栈：

| state | val |
| --- | --- |
| ... | ... |
| X | X.x |
| Y | Y.y |
| Z | Z.z |
| ... | ... |

![](img/46a88313606013b1cd4872a55f78bee2_512_0.png)

∀A→α    b:=f(c₁,c₂,...,cₖ)

b是A的综合属性，cᵢ(1≤i≤k)是α中符号的属性。综合属性的值是在自底向上的分析过程中，每次归约之前进行计算的。

A→XYZ    A·a:=f(X·x,Y·y,Z·z)

![](img/46a88313606013b1cd4872a55f78bee2_513_0.png)

实现时，将定义式 A.a:=f(X.x, Y.y, Z.z) (抽象)变成 val[ntop]:=f(val[top-2], val[top-1], val[top]) (具体可执行代码)。

在执行代码段之前执行：
    ntop:=top-r+1 ——r是句柄的长度
执行代码段后执行： top:=ntop;

![](img/46a88313606013b1cd4872a55f78bee2_514_0.png)

## 例5.1 台式计算器程序的语法制导定义（图5-2）

| 产生式 | 语义规则 |
|---|---|
| $L \rightarrow En$ | $print(E·val)$ (可看作是L的虚属性) |
| $E \rightarrow E_1 + T$ | $E·val := E_1·val + T·val$ |
| $E \rightarrow T$ | $E·val := T·val$ |
| $T \rightarrow T_1 * F$ | $T·val := T_1·val + F·val$ |
| $T \rightarrow F$ | $T·val := F·val$ |
| $F \rightarrow (E)$ | $F·val := E·val$ |
| $F \rightarrow digit$ | $F·val := digit·lexval$ |

## 翻译输入3*5+4n所做的移动

| 输入 | state | val | 使用的产生式 |
|---|---|---|---|
| 3*5+4n | - | - |  |
| *5+4n | 3 | 3 |  |
| *5+4n | F | 3 | F→digit |
| *5+4n | T | 3 | T→F |
| 5+4n | T* | 3- |  |
| +4n | T* 5 | 3-5 |  |
| +4n | T* F | 3-5 | F→digit |

|  |  |  |  |
|---|---|---|---|
| +4n | T | 15 | T→ T*F |
| +4n | E | 15 | E→ T |
| 4n | E+ | 15- |  |
| n | E+4 | 15-4 |  |
| n | E+F | 15-4 | F → digit |
| n | E+T | 15-4 | T→ F |
| n | E | 19 | E→ E+T |
|  | En | 19- |  |
|  | L | 19 | L→ En |
