

- 则对任意整数 \(i\)，
- \(i^2-1=(i-1)(i+1)\)
- 恒成立。也就是说，该命题函数的真值无论用什么个体代入总是对应为 T。此类命题函数的真值描述通过一个称为全称量词的特殊符号来量化。

• 定义2 命题函数P(x)的全称量化（universal quantification）是一个按如下规则确定真值的命题：如果对每一个个体a代入得到的P(a)均为T。则该命题为T。记为∀xP(x)。这里∀是全称量词（universal quantifier），表示为“对任意的”、“所有的”、“对每一个”等等。

## DEFINITION 2.
- 命题函数 P(x) 的全称量化是命题
- “P(x) 对论域中 x 的所有取值都为真。”

## EXAMPLE 5
- 用全称量化表达命题
- “本班的每个学生都学过微积分”
- 。

可以写成
∀ x P(x) or ∀ x (S(x)→P(x))
P(x) = "x 学过微积分。"
S(x) = "x 在本班。"

## EXAMPLE 8
- 当 P(x) 为命题 “x² < 10”，且论域由不超过 4 的正整数组成时，∀ x P(x) 的真值为何？

∀ x P(x) = P(1) ∧ P(2) ∧ P(3) ∧ P(4) = F.

• 定义3 命题函数 $P(x)$ 的存在量化（existential quantification）是一个按如下规则确定真值的命题：如果个体域中存在一个个体 $a$ 代入后得到 $P(a)$ 为 T，则该命题为 T，否则为 F。记 $∃$ 或 ∃。这里 ∃ 称为存在量词（existential quantification）。表示为“有一个”、“某些”、“某个”等等。

## DEFINITION 3.
- 命题函数 P(x) 的存在量化是命题
- “论域中存在一个元素 x 使得 P(x) 为真。”

## EXAMPLE 9
- 设 P(x) 表示命题 “x > 3。” 当论域为实数集时，量化 $\exists x\,P(x)$ 的真值为何？

由于 “x > 3” 例如当 x = 4 时为真，P(x) 的存在量化，即 $\exists x\,P(x)$，为真。

## EXAMPLE 10
- 设 Q(x) 表示命题 “x = x + 1。”  
  当论域为实数集时，量化 ∃xQ(x) 的真值为何？

F.

## EXAMPLE 11
- 当 P(x) 为命题 “$x^2 > 10$”，且论域由不超过 4 的正整数组成时，$\exists x\,P(x)$ 的真值为何？

$\exists x\,P(x)$  
$=P(1) \lor P(2) \lor P(3) \lor P(4)$  
$= \mathrm{T.}$

## Table1

| TABLE 1 Quantifiers. | | |
|---|---|---|
| Statement | When True? | When False? |
| ∀ x P(x) | P(x) is true for every x. | There is an x for which P(x) is false. |
| ∃ x P(x) | There is an x for which P(x) is true. | P(x) is false for every x. |

- 定义4 谓词公式定义为
- （1）n元谓词是一个谓词公式；
- （2）若A是谓词公式，则（¬A）也是谓词公式；
- （3）若A，B是谓词公式，则（A∨B）、（A∧B）、（A→B）、（A↔B）也是谓词公式；
- （4）若A是谓词公式且含有未被量化的个体变量x，则
  - ∀xA(x)，∃xA(x)也是谓词公式。
- （5）有限次地使用（1）～（4）所得到的也是谓词公式。

∀ x ((F(x) ∧ P(x)) → ∃ y M(x, y)).

- 变量的约束（BINDING VARIABLES）
- 1,自由变量（Free Variable）
- 2,约束变量（Bound Variable）

## More to Know About Binding
- (∀x P(x)) ∧ Q(x) - 变量 x 在 ∀x 量词的作用域之外，因此是自由的。不是一个完整的命题！
- (∀x P(x)) ∧ (∃x Q(x)) – 一个完整的命题，且没有多余的量词

在作用域中 X 的一切出现，称为 X 在公式中的约束出现。

所有约束出现的变元叫做约束变元。

不受约束的变元为自由变元。

## 例

1) ∀x(P(x) → Q(x))

指导变元

辖域

约束变元

2) \(\forall x\,(P(x) \rightarrow \exists y\,R(x,y))\)

![](img/c25dfd82fc242c2db53bc942dcad6885_354_0.png)

3) \(\forall x\forall y\,(P(x,y)\land Q(x,y))\to \exists xP(x,y)\)

指导变元

辖域

约束变元

指导变元

辖域

自由变元

约束变元

指导变元

辖域

约束变元

自由变元

P(x₁,...xₙ) 是 n 元谓词，有 n 个独立的自由变元。若对其中 k 个变元进行约束，则成为 n-k 元谓词。若没有自由变量出现，则该式就成为有关命题。

为避免由变元的约束与自由变元同时出现，而引起概念上的混乱，可对约束变元进行换名。

换名（约束变元改变名称符号）

$$\forall x(P(x)\to R(x,y))\land Q(x,y)$$

$$\forall z(P(z)\to R(z,y))\land Q(x,y)$$

∀y(P(y) → R(y, y)) ∧ Q(x, y)
∀z(P(z) → R(x, y)) ∧ Q(x, y)

+ 1) 换名范围:量词中的指导变元和作用域中出现的该导变元.公式中其余部分不变.
+ 2) 要换成作用域中没有出现的变元名称.

## 代入（自由变元的更换）

$\exists x\,(P(y)\land R(x,y))$

$\exists x\,(P(z)\land R(x,z))$

+ 1. 对该自由变元每一处进行代入。
+ 2. 代入的变元与原公式中所有变元名称不能相同。

个体域为有限时,客体变元
的所有可能的取代是可枚举的.
设论域元素为 a₁....aₙ
∀x A x ⇔ A a ∧ ... ∧ A aₙ
∃x A x ⇔ A a ∨ ... ∨ A aₙ

