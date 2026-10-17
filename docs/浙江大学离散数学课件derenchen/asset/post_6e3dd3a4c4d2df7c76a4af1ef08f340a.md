
注：

- 1. 在演算过程中，利用交换律，可使每个简单析取式或简单合取式中命题变项都按字典序出现。
- 2. 上述求析取范式的过程中，第二步和第三步结果都是析取范式。这说明命题公式的析取范式是不唯一的。同样，合取范式也是不唯一的。为了得到唯一的规范化形式的范式，需要定义主析取范式和主合取范式。为此，先引入如下极小项和极大项概念。

### 定义2.4

在含有n个命题变项的简单合取式（简单析取式）中，若每个命题变项和它的否定式不同时出现，但二者之一必出现且仅出现一次，并且第i个命题变项或其否定式出现在从左算起的第i位上(若命题变项无下标，则按字典序排列)，则称该简单合取式(简单析取式)为极小项（极大项）。

注：由于每个命题变项在极小项中以原形或否定式形式出现且仅出现一次，因而n个命题变项共可产生2^n个不同的极小项。每个极小项仅有一个成真赋值，若一个极小项的成真赋值对应的二进制数转化为十进制数为i，则将该极小项记为m_i。

类似地，n个命题变项可产生2^n个不同的极大项。每个极大项只有一个成假赋值。若一个极大项的成假赋值对应的十进制数为i，则将该极大项记为M_i。

### 定理2.4

设 $m_i$ 与 $M_i$ 是命题变项 $p_1$，$p_2$ …，$p_n$ 形成的极小项和极大项，则 $\lnot m_i \Leftrightarrow M_i$，$\lnot M_i \Leftrightarrow m_i$。

证明：略，可从以上两表验证该定理。

### 定义2.5

如果由$n$个命题变项构成的析取范式（合取范式）中所有的简单合取式（简单析取式）都是极小项（极大项），则称该析取范式（合取范式）为主析取范式（主合取范式）。

### 定理2.5

任何命题公式都存在着与之等值的主析取范式和主合取范式，并且是唯一的。

证明：见教材37页。

注：主析取范式和主合取范式的求法：

- (1) 先通过等值推演将所给的命题公式化为析取范式（合取范式）；
- (2) 若某个简单合取式（简单析取式）A中既不含变项p<sub>i</sub>，又不含变项¬p<sub>i</sub>，则通过：

  A⇔A∧1 ⇔ A∧(p<sub>i</sub>∨¬p<sub>i</sub>) ⇔ (A∧p<sub>i</sub>)∨(A∧¬p<sub>i</sub>)

  或： A⇔A∨0 ⇔ A∨(p<sub>i</sub>∧¬p<sub>i</sub>) ⇔ (A∨p<sub>i</sub>)∧(A∨¬p<sub>i</sub>)

  补齐变项。

- (3) 消去重复变项和矛盾式，如用p，m<sub>i</sub>,0 分别代替p∧p，m<sub>i</sub>∨m<sub>i</sub> 和矛盾式，等。

### 例2.8

求公式 (p→q)↔r的主析取范式和主合取范式。

解：(1)主析取范式

由例2.7 知，
\((p→q)↔r \Leftrightarrow (p∧¬q∧¬r)∨(¬p∧r)∨(q∧r)\)
其中
\((¬p∧r) \Leftrightarrow ¬p∧(¬q∨q)∧r\)
\(\Leftrightarrow (¬p∧¬q∧r)∨(¬p∧q∧r)\)
\(\Leftrightarrow m₁∨m₃\)

\((q∧r) \Leftrightarrow (¬p∨p)∧q∧r\)
\(\Leftrightarrow (¬p∧q∧r)∨(p∧q∧r)\)
\(\Leftrightarrow m₃∨m₇\)

\((p∧¬q∧¬r) \Leftrightarrow m₄\)

因此
\((p→q)↔r \Leftrightarrow m₁∨m₃∨m₄∨m₇\)

(2)主合取范式

由例2.7 知，
\((p→q)↔r \Leftrightarrow (p∨r)∧(¬q∨r)∧(¬p∨q∨¬r)\)
∵
\((p∨r) \Leftrightarrow p∨(q∧¬q)∨r\)
\(\Leftrightarrow (p∨q∨r)∧(p∨¬q∨r)\)
\(\Leftrightarrow M₀∧M₂\)

\((¬q∨r) \Leftrightarrow (p∧¬p)∨¬q∨r\)
\(\Leftrightarrow (p∨¬q∨r)∧(¬p∨¬q∨r)\)
\(\Leftrightarrow M₂∧M₆\)

\((¬p∨q∨¬r) \Leftrightarrow M₅\)

∴
\((p→q)↔r \Leftrightarrow M₀∧M₂∧M₅∧M₆\)

### 1. 求公式的成真与成假赋值

对含有n个变项的命题公式A，若其主析取范式含s（0≤s≤2<sup>n</sup>）个极小项，则A有s个成真赋值，它们是极小项下标的二进制表示，其余2<sup>n</sup> - s个赋值都是成假赋值。

例如，在例2.8中，(p→q)↔r⇔m<sub>1</sub>∨m<sub>3</sub>∨m<sub>4</sub>∨m<sub>7</sub>，因各极小项含三个文字，故各极小项下标的长为3的二进制数 001， 011， 100， 111为该公式的成真赋值，而其余赋值000， 010， 101， 110为成假赋值。

### 2. 判断公式的类型

设公式A中含n个变项，则

- (1) A为重言式当且仅当A的主析取范式含全部2ⁿ个极小项；
- (2) A为矛盾式当且仅当A的主析取范式不含任何极小项。（此时，记A的主析取范式为0）。
- (3) A为可满足式当且仅当A的主析取范式中至少含一个极小项。

### 例2.10

利用公式的主析取范式判断公式的类型：

- (1) ¬(p→q)∧q
- (2) p→(p∨q)
- (3) (p∨q)→r

解：

(1) ¬(p→q)∧q ⇔ ¬(¬p∨q)∧q ⇔ p∧¬q∧q ⇔ 0.

故 ¬(p→q)∧q 是矛盾式。

(2) p→(p∨q) ⇔ ¬p∨p∨q

⇔ (¬p∧(¬q∨q))∨(p∧(¬q∨q))∨((¬p∨p)∧q)

⇔ (¬p∧¬q)∨(¬p∧q)∨(p∧¬q)∨(p∧q)∨(¬p∧q)∨(p∧q)

⇔ (¬p∧¬q)∨(¬p∧q)∨(p∧¬q)∨(p∧q)

⇔ m₀∨m₁∨m₂∨m₃.

该主析取范式含全部2²个极小项，故p→(p∨q)是重言式。

注：另一种推演： p→(p∨q) ⇔ ¬p∨p∨q ⇔ 1∨q ⇔ 1 ⇔ m₀∨m₁∨m₂∨m₃

(3) \((p \vee q) \rightarrow r \Leftrightarrow \neg (p \vee q) \vee r\)

\(\Leftrightarrow (\neg p \wedge \neg q) \vee r\)

\(\Leftrightarrow (\neg p \wedge \neg q \wedge (\neg r \vee r)) \vee ((\neg p \vee p) \wedge (\neg q \vee q) \wedge r)\)

\(\Leftrightarrow (\neg p \wedge \neg q \wedge \neg r) \vee (\neg p \wedge \neg q \wedge r) \vee (\neg p \wedge \neg q \wedge r) \vee (\neg p \wedge q \wedge r) \vee (p \wedge \neg q \wedge r) \vee (p \wedge q \wedge r)\)

\(\Leftrightarrow m_0 \vee m_1 \vee m_3 \vee m_5 \vee m_7\)

故该公式是可满足式，但不是重言式。

### 3. 判断两公式是否等值

设公式A, B共有n个变项。按n个变项求出A, B的主析取范式。
若A与B有相同的主析取范式，则A⇔B；否则 A⇎B。

### 例2.11

判断下面两组公式是否等值：

- (1) p与(p∧q)∨(p∧¬q)
- (2) (p→q)→r 与 (p∧q)→r

解：

(1) p⇔p∧(¬q∨q)⇔(p∧¬q)∨(p∧q)⇔m2∨m3

而 (p∧q)∨(p∧¬q)⇔ m2∨m3，

故 p⇔ (p∧q) ∨ (p∧¬q)

(2) 因 (p→q) →r⇔m1∨m3∨m4∨m5∨m7

而 (p∧q) →r⇔m0∨m1∨m2∨m3∨m4∨m5∨m7

故 (p→q)→r⇎(p∧q)→r

### 4. 利用主析取范式和主合取范式解决应用问题

### 例2.12

某单位欲从三人A, B, C中挑选1～2人出国进修。由于工作需要选派时要满足以下条件：

- (1) 若A去，则C同去；
- (2) 若B去，则C不能去；
- (3) 若C不去，则A或B可以去。

问应如何选派？

解：设p：派A去；q：派B去；r：派C去

由条件得：(p→r)∧(q→ ¬r)∧( ¬r→(p∨q))

经演算得其主析取范式为：m₁∨m₂∨m₅

- m₁= ¬p∧ ¬q∧r；
- m₂= ¬p∧q∧ ¬r；
- m₅=p∧ ¬q∧r

由此可知，有3种选派方案：

- (1) C去，A, B都不去；
- (2) B去，A, C都不去；
- (3) A, C同去，B不去。

### 关于主合取范式的两点说明

- 1. 主合取范式可由主析取范式直接得到。

设公式 A 含有 n 个变项，A 的主析取范式为

$$A \Leftrightarrow m_{i_1} \lor m_{i_2} \lor \cdots \lor m_{i_l},\ (0 \leq i_r \leq 2^n-1,\ r=1,2,\cdots,l)$$

未在主析取范式中出现的极小项设为 $m_{j_1},m_{j_2},\cdots,m_{j_{2^n-l}}$，则 A 的主合取范式为：$A \Leftrightarrow M_{j_1}\land M_{j_2}\land\cdots\land M_{j_{2^n-l}}$

事实上，因 $\neg A \Leftrightarrow m_{j_1}\lor m_{j_2}\lor\cdots\lor m_{j_{2^n-l}}$，故

$$A \Leftrightarrow \neg(\neg A) \Leftrightarrow \neg(m_{j_1}\lor m_{j_2}\lor\cdots\lor m_{j_{2^n-l}}) \Leftrightarrow \neg m_{j_1}\land\neg m_{j_2}\land\cdots\land\neg m_{j_{2^n-l}}$$

$$\Leftrightarrow M_{j_1}\land M_{j_2}\land\cdots\land M_{j_{2^n-l}}$$
