
## Note

Following three are equivalent

- a congruence relation R on G
- a normal subgroup H of G
- a homomorphism from G to G/R or G'

## Corollary 2

Let
f be a homomorphism from a group (G, *) onto a group (G', *)
the kernel(核) of f, ker(f), be defined by ker(f) = {a ∈ G| f(a) = e'}.

Then
ker(f) is a normal subgroup of G.
The quotient group G/ker(f) is isomorphic to G'.

## Homework

- 4 @353
- 18, 30@354

## Key ideas for review

Binary operation

Commutative, Associative

Semigroup, Monoid, Group

Subsemigroup, Submonoid, Subgroup

Isomorphism, Homomorphism

Congruence relation R on semigroup (S, *)

Quotient semigroup S/R,

Order of group, Sₙ, Zₙ,置换群, 循环群

Left and right coset, Normal subgroup

例 $G=\mathbb{R}\times\mathbb{R}_+$，+定义为

$\langle x_1,y_1\rangle+\langle x_2,y_2\rangle$

$=\langle x_1+x_2,y_1+y_2\rangle$

$\langle G,+\rangle$ 为有幺元 $\langle 0,0\rangle$ 的阿贝尔群.

H = {< x,y > | y = 2x }

< H,+ > 为 < G,+ > 的子群.

对 < x₀,y₀ > ∈ G, < x₀,y₀ > H

H 关于

< x₀,y₀ >

的左陪集.

![](img/c25dfd82fc242c2db53bc942dcad6885_1046_0.png)

< A, Δ >
A a b c aΔc Δ
f(A) ⊆ B
< B, * >
B
f(a)
f(c)
f(a) * f(c)
f(aΔc)

## Thanks for your attention!

*Coming up next …*

*Groups and Coding*

## Relations
关系

Rosen 7th ed., ch. 9

## 9 Relations

- 9.1 Relations and Their Properties
- 关系及关系性质
- 9.2 *n*-ary Relations and Their Applications
- n元关系及应用
- 9.3 Representing Relations 关系的表示
- 9.4 Closures of Relations 关系闭包
- 9.5 Equivalence Relations 等价关系
- 9.6 Partial Orderings 偏序关系

## 9.1 Relations and Their Properties

- Introduction
- Functions as relations
- Relations on Set
- Properties of Relations
- Combining Relations

## What are relations?

- Relations are a formal means to specify which elements from two or more sets are related to each other
- Examples
  - {students} who take {courses}
  - {businesses} and their {telephone numbers}
  - {integers} and their {divisors}
  - {program variables} and the {subroutines} they are used in

![](img/c25dfd82fc242c2db53bc942dcad6885_1054_0.png)

## 琅琊榜人物关系图

![](img/c25dfd82fc242c2db53bc942dcad6885_1055_0.png)

## 《人民的名义》人物关系图

![](img/c25dfd82fc242c2db53bc942dcad6885_1056_0.png)

## 解构薄式“江湖” - 庭审实录中的72个人物关系

点击头像和小图显示人物关系及案情关系

贪污罪

滥用职权罪

受贿罪

王正刚

唐肖林

王立军

薄熙来

谢某

遇舍开来

谷明

尼尔·伍德

![](img/c25dfd82fc242c2db53bc942dcad6885_1058_0.png)

## 仙剑奇侠传一代至四代人物关系图 1.1A 图文版

二元关系：二个对象之间相关的关系

多元关系：多个对象之间的关系

多元关系常化成二元关系来研究

无序的二元关系：方块k与梅花k，谁在前，谁在后都还是同点的

有序的二元关系：父子关系，不能交换父与子的次序

又如：

- (1) a + b = 偶数，a 与 b 是无序的
- 用 [a, b] 表示无序对

- (2) a ≤ b，a 与 b 是有序的二元关系，叫作 a 相关于 b，记成 a r b，用 (a, b) 表示有序对

- (3) 无序的二元关系可用有序的二元关系表示
- 即 (a, b) 与 (b, a) 都属于这种二元关系

## Definition of relations

- Let *A* and *B* be two sets. A *binary relation* *R* from *A* to *B* is a subset of *A* × *B*.
  - Note that the order of the two sets matters.
- More generally, let *A₁, A₂, ..., Aₙ* be *n* sets. An *n-ary relation* *R* on these sets is a subset of *A₁* × *A₂* × ... × *Aₙ*.
  - The sets *Aᵢ* are known as the *domains* of the relation, and *n* as its *degree*
  - Again, the order of the domains matters.

## Binary Relations

- Let $A, B$ be any sets. A *binary relation* $R$ from $A$ to $B$, written (with signature) $R:A\times B$, or $R:A,B$, is (can be identified with) a subset of the set $A\times B$.
  - E.g., let $\prec : \mathbb{N}\leftrightarrow\mathbb{N} := \{(n,m)\mid n<m\}$
- The notation $aRb$ or $aRb$ means that $(a,b)\in R$.
  - E.g., $a\prec b$ means $(a,b)\in\prec$
- If $aRb$ we may say “$a$ is related to $b$ (by relation $R$)”,
  - or just “$a$ relates to $b$ (under relation $R$)”.
- A binary relation $R$ corresponds to a predicate function $P_R:A\times B\to\{\mathrm{T},\mathrm{F}\}$ defined over the 2 sets $A,B$;
  - e.g., predicate “eats” $:= \{(a,b)\mid$ organism $a$ eats food $b\}$
