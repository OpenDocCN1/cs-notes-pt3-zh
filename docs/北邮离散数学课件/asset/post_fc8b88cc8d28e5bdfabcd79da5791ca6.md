
# 谓词公式的翻译
解释(interpret)

- 对一个合式公式的解释包括给出
- 个体域
- 谓词
- 函数
- 个体常项
- 的具体含义

# EXAMPLE 12

- Translate the statement
- ∀x (C(x) ∨ ∃y(C(y) ∧ F(x, y)))
- into English, where C(x) is "x has a

The statement says that for every student x in BUPT x has a computer or there is a student y such that y has a computer and x and y are friends. In other words, every student in BUPT has a computer or has a friend who has a computer.

# EXAMPLE 13

- Translate the statement
- ∃ x ∀ y ∀ z (((F(x,y) ∧ F(x,z) ∧ (y≠z)) → ¬F(y,z)))
- into English, where F(a,b) means a and b

This statement says that there is a student x such that for all students y and all students z other than y, if x and y are friends and x and z are friends, then y and z are not friends. In other words, there is a student none of whose friends are also friends with each other.

∀ x ∀ y(P(x,y) → Q(y))

- 个体域： 大于0的整数
- P(x,y): y>x
- Q(y): y>1

- 个体域： 整数
- P(x,y): y>x
- Q(y): y>1

# 语句形式化过程的三个关键点

- 准确地从语句中提取谓词，表示性质的谓语用一元谓词，表示关系的谓词用二元或更多元数的谓词来表示。
- 准确地使用量词和确定量词的辖域，当辖域中多于一个谓词时必须注意联结词与括号的使用。**全称蕴涵** **存在合取**
- 准确地使用多个重叠的量词，其排列次序应与原语句意义一致。

# Example 23

- Express the statement “ Every student in this class has studied calculus” using predicates and quantifiers.
- ∀x (S(x) → C(x))
- 区别:
- ∀x (S(x) ∨ E(x))

# EXAMPLE 24

- Express the statements "Some student in this class has visited Mexico" and "Every student in this class has visited either Canada or Mexico" using quantifiers.
- ∃x (S(x) ∧ M(x))
- 区别:
- ∃x (S(x) → M(x))

∀ x(C(x)∨M(x))

∀x (S(x) → (C(x)∨M(x)))

# Example 25

- Use predicates and quantifiers to express the system specifications “Every mail message larger than one megabyte will be compressed” and “If a user is active, at least one network link will be available.”
- Let S(m,y) be “Mail message *m* is larger than y megabytes” and let C(m) denote “Mail message *m* will be compressed.”
- ∀m (S(m,1) → C(m))
- A(u):User *u* is active  S(n,x): network link *n* is in state *x*
- ∃uA(u) → ∃nS(n, *available*)

# 例1： 每个人都爱她自己的孩子

- 令
  - P(x): x是人
  - C(x): x是孩子
  - I(x, y): x属于y
  - L(x, y): x爱y
- 一阶逻辑表示
  - ∀x∀y(P(y) ∧ C(x) ∧ I(x, y) → L(y, x))

# 例3

- 假设有一个人被每一个喜欢某些人的人所喜欢，又假设没有不喜欢人的人。证明有一个人被所有的人喜欢。
- 令
  - $L(x, y)$：x喜欢y
- 前提：
  - $P_1$：$\exists y\forall x\,(\exists z\,L(z,y)\rightarrow L(x,y))$
  - $P_2$：$\neg\exists x\forall y\,(\neg L(x,y))$
- 结论：
  - $C$：$\exists x\forall y\,L(y,x)$
- 于是，要证明：
  - $P_1\land P_2\rightarrow C$

# 例3

- 前提：
  - $P_1$: $\exists y \forall x (\exists z\, L(z,\ y) \to L(x,\ y))$
  - $P_2$: $\neg \exists x \forall y (\neg L(x,\ y))$
- 结论：
  - C: $\exists x \forall y\ L(y,\ x)$
- 于是，要证明：
  - $P_1 \land P_2 \to C$
  - $\exists y \forall x (\exists z\ L(z,\ y) \to L(x,\ y)) \land \neg \exists x \forall y (\neg L(x,\ y)) \to \exists x \forall y\ L(y,\ x)$
  - 是永真公式

# 例4

- 每一个人的外祖父都是他母亲的父亲
- 令
  - $P(x)$: $x$是人
  - $O(x, y)$: $x$是$y$的外祖父
  - $F(x, y)$: $x$是$y$的父亲
  - $M(x, y)$: $x$是$y$的母亲
- 命题表示
  - $\forall x \forall y\ (P(y) \land O(x, y) \rightarrow \exists z\ (F(x, z) \land M(z, y)))$

# 例5

- 不管黑猫白猫，抓住老鼠就是好猫
- 令
  - C(x): x是猫
  - B(x): x是黑的
  - W(x): x是白的
  - G(x): x是好的
  - M(x): x是老鼠
  - K(x, y): x抓住y
- 命题表示
  - ∀x∀y (C(x) ∧ M(y) ∧ (B(x) ∨ W(x)) ∧ K(x, y) → G(x))

# 例6

- 有些病人相信所有的医生，但病人都不相信一个骗子。证明：医生都不是骗子
- 令
  - $F(x)$：$x$是病人
  - $G(x)$：$x$是医生
  - $H(x)$：$x$是骗子
  - $L(x, y)$：$x$相信$y$

# 例6

- 前提：
  - $G_1$: $\exists x (F(x) \land \forall y (G(y) \to L(x, y)))$
  - $G_2$: $\forall x \forall y (F(x) \land H(y) \to \neg L(x, y))$
- 结论：
  - C: $\forall x (G(x) \to \neg H(x))$
- 于是，要证明：
  - $G_1 \land G_2 \to C$
  - 是永真公式
