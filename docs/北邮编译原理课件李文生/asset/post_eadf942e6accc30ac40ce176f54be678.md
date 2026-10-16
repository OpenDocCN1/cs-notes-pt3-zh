
## 扩充分析栈

目的：使之能够保存综合属性

做法：在分析栈中增加一个域，来存放综合属性值

例：带有综合属性域的分析栈

|  |  |
|---|---|
| Z | Z.z |
| Y | Y.y |
| X | X.x |
| --- | --- |
| state | val |

top →

- 栈由一对数组state和val实现
- state元素是指向LR(1)分析表中状态的指针（或索引）
- 如果state[i]对应的符号为A, val[i]中就存放分析树中与节点A对应的属性值。
- 假设综合属性刚好在每次归约前计算

A→XYZ对应的语义规则是A.a=f(X.x, Y.y, Z.z)

## 修改分析程序

- 对于终结符号
  - 其综合属性值由词法分析程序产生
  - 当分析程序执行移进操作时，其属性值随终结符号（或状态符号）一起入栈。
- 为每个语义规则编写一段代码，以计算属性值
- 对每一个产生式 A→XYZ
  - 把属性值的计算与归约动作联系起来 top →
  - 归约前，执行与产生式相关的代码段
  - 归约：右部符号及其属性出栈
    左部符号及其属性入栈

| state | val |
|---|---|
| Z | Z.z |
| Y | Y.y |
| X | X.x |
| … | … |

- LR分析程序中应增加计算属性值的代码段

## 例：用LR分析程序实现表达式求值

| 产生式 | 语义规则 | 代码段 |
|---|---|---|
| L→E | print(E.val) | print(val[top]) |
| E→E₁+T | E.val=E₁.val+T.val | val[ntop]=val[top-2]+val[top] |
| E→T | E.val=T.val |  |
| T→T₁*F | T.val=T₁.val*F.val | val[ntop]=val[top-2]*val[top] |
| T→F | T.val=F.val |  |
| F→(E) | F.val=E.val | val[ntop]=val[top-1] |
| F→digit | F.val=digit.lexval |  |

## 栈指针变量top和ntop的控制：

- 当用 A→β 归约时，若|β|=r，在执行相应的代码段之前， ntop=top-r+1。
- 在每一个代码段被执行之后， top=ntop

## 对 3*5+4 进行分析的动作序列 (见表4.8)

| 步骤 | 输入 | 分析栈 | 分析动作 |
|---|---|---|---|
| (1) | 3*5+4$ | state: 0<br>val: - | 移进 5 |
| (2) | *5+4$ | state: 0 5<br>val: - 3 | 归约，用F→digit goto[0,F]=3 |
| (3) | *5+4$ | state: 0 3<br>val: - 3 | 归约，用T→F goto[0,T]=2 |
| (4) | *5+4$ | state: 0 2<br>val: - 3 | 移进 7 |
| (5) | 5+4$ | state: 0 2 7<br>val: - 3 - | 移进 5 |
| (6) | +4$ | state: 0 2 7 5<br>val: - 3 - 5 | 归约，用F→digit goto[7,F]=10 |
| (7) | +4$ | state: 0 2 7 10<br>val: - 3 - 5 | 归约，用T→T*F goto[0,T]=2 |

| 步骤 | 输入 | 分析栈 | 分析动作 |
|---|---|---|---|
| (8) | +4$ | state: 0 2<br>val: - 15 | 归约，用E→T goto[0,E]= |
| (9) | +4$ | state: 0 1<br>val: - 15 | 移进 6 |
| (10) | 4$ | state: 0 1 6<br>val: - 15 - | 移进 5 |
| (11) | $ | state: 0 1 6 5<br>val: - 15 - 4 | 归约，用F→digit goto[6,F]=3 |
| (12) | $ | state: 0 1 6 3<br>val: - 15 - 4 | 归约，用T→F goto[6,T]=9 |
| (13) | $ | state: 0 1 6 9<br>val: - 15 - 4 | 归约，用E→E+T goto[0,E]=1 |
| (14) | $ | state: 0 1<br>val: - 19 | 接受 |

作业:
5.1
5.2
5.3
5.4

## 5.3 L-属性定义的自顶向下翻译

- 在自顶向下的分析过程中实现L属性定义的翻译
- 预测分析方法对文法的要求
  - 不含左递归
  - A→α | β
  - FIRST(α)∩FIRST(β)=∅

### 一、消除翻译方案中的左递归

### 二、预测翻译程序的设计

### 一、消除翻译方案中的左递归

例：考虑对简单表达式求值的语法制导定义

| 产生式 | 语义规则 |
|---|---|
| L→E | print(E.val) |
| E→E₁+T | E.val=E₁.val+T.val |
| E→T | E.val=T.val |
| T→T₁*F | T.val=T₁.val*F.val |
| T→F | T.val=F.val |
| F→(E) | F.val=E.val |
| F→digit | F.val=digit.val |

翻译方案：

(1) L→E { print(E.val) }

(2) E→E₁+T { E.val=E₁.val+T.val }

(3) E→T { E.val=T.val }

(4) T→T₁*F { T.val=T₁.val*F.val }

(5) T→F { T.val=F.val }

(6) F→(E) { F.val=E.val }

(7) F→digit { F.val=digit.val }

消除左递归的方法：

A→Aα | β

替换为：A→βR

R→αR | ε

由(2)和(3)有：

(2′) E→T {E.val=T.val} M

(3′) M→+T {E.val=E₁.val+T.val} M₁

(3″) M→ε

继承属性 M.i：表示在M之前已经推导出的子表达式的值

综合属性 M.s：表示在M完全展开之后得到的表达式的值

为（3″）设置把M.i传递给M.s的语义动作，得到：

（3″） M→ε {M.s=M.i}

对于（2′）， E→T {E.val=T.val} M 通过M的属性M.s和M.i完成E和T的综合属性的传递E.val=T.val，得到：

（2′） E→T {M.i=T.val}
M {E.val=M.s}

对于（3′） M→+T {E.val=E₁.val+T.val} M₁

M₁.i的语义规则为： M₁.i=M.i+T.val

M.s的语义规则为： M.s=M₁.s

于是得到：

（3′） M→+T {M₁.i=M.i+T.val}
M₁ {M.s=M₁.s}

同样，通过引入非终结符号N，可以得到（4）和（5）的变换结果

![](img/12b57169bd1d5004c5e7193ff0d478d5_359_0.png)

![](img/12b57169bd1d5004c5e7193ff0d478d5_359_1.png)

## 翻译方案

# 表达式3*5+4的翻译过程

L→ E {print(E.val)}
E→ T {M.i=T.val}
  M {E.val=M.s}
M→ +
  T {M₁.i=M.i+T.val}
  M₁ {M.s=M₁.s}
M→ ε {M.s=M.i}
T→F {N.i=F.val}
  N {T.val=N.s}
N→ *
  F {N₁.i=N.i*F.val}
  N₁ {N.s=N1.s}
N→ ε {N.s=N.i}
F→(
  E
) {F.val=E.val}
F→digit {F.val=digit.lexval}

![](img/12b57169bd1d5004c5e7193ff0d478d5_360_0.png)

## 消除翻译方案中左递归的一般方法

翻译方案：

A→A₁Y  {A. a=g (A₁. a, Y. y)}

A→X  {A. a=f (X. x)}

消除基本文法中的左递归：

A→XR

R→YR | ε

为R设置继承属性R.i和综合属性R.s

R.i：表示在R之前已经扫描过的符号串的属性值

R.s：表示在R完全展开为终结符号之后得到的符号串的属性值。

翻译方案转换为：

A→X  {R.i=f (X. x)}

R  {A. a=R. s}

R→Y  {R₁. i=g (R. i, Y. y)}

R₁  {R. s=R₁. s}

R→ε  {R. s=R. i}

![](img/12b57169bd1d5004c5e7193ff0d478d5_361_0.png)
