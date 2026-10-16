
## 例7

- 每个有理数都是实数
- 某些实数是有理数
- 不是每一个实数都是有理数

## 例

并非每个实数都是有理数

$R(x)$: $x$ 是实数

$Q(x)$: $x$ 是有理数

$\neg\forall x(R(x) \rightarrow Q(x))$

$\exists x(R(x) \land \neg Q(x))$

## 例8

- 对平面上任意两点，有且仅有一条直线通过这两点
- 令
  - $P(x)$: $x$ 是一个点
  - $L(x)$: $x$ 是一条直线
  - $R(x, y, z)$: $z$ 通过 $x$ 和 $y$
  - $E(x, y)$: $x$ 等于 $y$
- $\forall x \forall y\ (P(x) \land P(y) \rightarrow \exists z\ (L(z) \land R(x,\ y,\ z) \land \forall u\ (L(u) \land R(x,\ y,\ u) \rightarrow E(z,\ u))))$

## 例9

- 在实数集中，任给一正实数，都存在大于该实数的实数

## 例10：函数序列收敛

- 设 $f_1(x), \dots, f_n(x), \dots$ 是函数序列，$f(x)$ 是一个函数。
- “对任给 $\varepsilon>0$, $x_0 \in (a, b)$, 都存在 $N$, 使得当 $n>N$ 时，有 $|f(x_0)-f_n(x_0)| < \varepsilon$
- 则称函数序列 $\{f_n(x)\}$ 在 $(a, b)$ 区间内收敛于 $f(x)$”
- 令
  - $G(x, y)$: $x$ 大于 $y$
  - $B(x)$: $x$ 属于 $(a, b)$ 区间
  - $s(x, n)$: $f(x)$ 与 $f_n(x)$ 之差的绝对值
- 于是
  - $\forall x \forall \varepsilon\ (G(\varepsilon, 0) \land B(x) \rightarrow \exists N \forall n\ (G(n, N) \rightarrow G(\varepsilon, s(x, n))))$

## 例11：函数序列一致收敛

- 设 $f_1(x),\ldots,f_n(x),\ldots$ 是函数序列，$f(x)$ 是一个函数。
- “对任给 $\varepsilon>0$，都存在 $N$，使得当 $n>N$ 时，对所有 $x\in(a,b)$，都有
  $$|f(x)-f_n(x)|<\varepsilon$$
- 则称函数序列 $\{f_n(x)\}$ 在 $(a,b)$ 区间内一致收敛于 $f(x)$”

## 例

发光的不都是金子

$L(x)$: $x$ 发光

$G(x)$: $x$ 是金子

$\neg\forall x(L(x) \rightarrow G(x))$

$\exists x(L(x) \land \neg G(x))$

## 例

不是所有男人都比女人高

$M(x)$: $x$ 是男人，$W(x)$: $x$ 是女人

$H(x,y)$: $x$ 比 $y$ 高

```
∃x(M(x) ∧ ∃y(W(y) ∧ H(y, x)))
```

```
¬∀x(M(x) → ∀y(W(y) → H(x, y)))
```

## 例

有人喜欢吃糖

$M(x)$: $x$ 是人　$S(x)$: $x$ 是糖

$L(x,y)$: $x$ 喜欢 $y$

$\exists x(M(x) \land \exists y(S(y) \land L(x,y)))$

$\neg\forall x(M(x) \rightarrow \forall y(S(y) \rightarrow \neg L(x,y)))$

- Can predicate logic say “there exist exactly two objects with property P”?
- Yes:
- $\exists x \exists y (P(x) \land P(y) \land x \ne y \land \forall z (P(z) \rightarrow (z = x \lor z = y)))$

## What’s wrong with

- $\exists x \exists y (P(x) \land P(y) \land x \ne y) \land \forall z (P(z) \rightarrow (z = x \lor z = y))$ as a formalisation of `exactly two`?
- This is a conjunction of two separate propositions. As a result, $x$ and $y$ are not bound, so this is not even a proposition.

## EXAMPLE 16

- Express the statement "Everyone has exactly one best friend" as a logical expression.

```
∀ x ∃ y ∀ z (B(x, y) ∧ ((z ≠ y) → ¬B(x,z))).
```

## EXAMPLE 17

- Express the statement "If somebody is female and is a parent, then this person is someone's mother" as a logical expression.

```
∀ x ((F(x) ∧ P(x)) → ∃ y M(x, y)).
```

## EXAMPLE 18

- Use quantifiers to express the statement "There is a woman who has taken a flight on every airline in the world."
- $P(w, f)$: $w$ has taken a flight.
- $Q(f, a)$: $f$ is a flight on airline $a$.

```
∃ w ∀ a ∃ f(P(w, f) ∧ Q(f, a))
```

## EXAMPLE 19

- (Calculus required) Express the definition of a limit using quantifiers.

```
∀ε > 0 ∃δ > 0 ∀x (0 < |x-a| < δ → |f(x)-L| < ε)
```

- Consider the following statements. The first two are premises and the third is the conclusion. The entire set is an argument.
- "All lions are fierce."
- "Some lions do not drink coffee."
- "Some fierce creatures do not drink coffee."
- Let $P(x)$, $Q(x)$, and $R(x)$ be the statements "$x$ is a lion," "$x$ is fierce," and "$x$ drinks coffee," respectively. Assuming that the universe of discourse is the set of all creatures, express the statements in the argument using quantifiers and $P(x)$, $Q(x)$, and $R(x)$.

```
∀x(P(x)→Q(x)).
∃x(P(x)∧¬R(x)).
∃x(Q(x)∧¬R(x)).
```

- Consider the following statements, of which the first three are premises and the fourth is the conclusion.
- "All hummingbirds are richly colored."
- "No large birds live on honey."
- "Birds that do not live on honey are dull in color."
- "Hummingbirds are small."
- Let $P(x)$, $Q(x)$, $R(x)$, and $S(x)$ be the statements "$x$ is a hummingbird," "$x$ is large," "$x$ lives on honey," and "$x$ is richly colored," respectively. Assuming that the universe of discourse is the set of all birds, express the statements in the argument using quantifiers and $P(x)$, $Q(x)$, $R(x)$, and $S(x)$.

```
∀x(P(x)→S(x)).
¬∃x(Q(x)∧R(x)).
∀x(¬R(x)→¬S(x)).
∀x(P(x)→¬Q(x)).
```
