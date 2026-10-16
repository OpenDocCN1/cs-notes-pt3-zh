
## 习题

- § 1.1　　　2, 14, 26, 30, 38
- § 1.2　　　2, 4, 32, 40
- § 1.3－8, 28, 30, 36, 40, 48, 54, 58

- 求下列公式的析取范式和合取范式
  - (¬A ∨ ¬B) → (A ↔ C) → B

- 通过求主合取范式的方法，判断下列各对公式是否等价
  - ¬A ∨ (A ∧ B) ∨ C
  - (¬A ∨ B) ∧ (B ∨ C)

- 通过求主析取范式，求出所有使下列公式为真的赋值
  - (A ∨ B) ∧ (A → C) ∧ (B → C)

- P，Q，R，S四个字母，从中取两个字母，但要满足下述三个条件，问有几种取法，如何取？
  - 如果取P，则R和S要取一个
  - Q，R不能同时取
  - 取R则不能取S

## 可选习题

A ∧ B ∧ ¬ C ∧ ¬ D ∧ E

- 张先生手中有代号为A、B、C、D、E的五种股票，根据当前股市情况及张先生本人的经济需求，需要有若干个股票抛出，但又必须满足如下复杂的要求：
- （1）若A抛出，则B也抛出；
- （2）B和C要留一种股票且只能留一种；
- （3）C和D要么全抛，要么都不抛；
- （4）D和E两种股票中必然有一种或两种要抛出；
- （5）若E抛出，则A、B也抛出。

上述五种条件全部满足，问有几种合理的方案供张先生选择。

## Summary

- Predicate Logic (First-Order Logic (FOL), Predicate Calculus)
- The Language of Quantifiers
- Logical Equivalences
- Nested Quantifiers
- Translation from Predicate Logic to English
- Translation from English to Predicate Logic

## Predicates and Quantifiers

Section 1.4

## Section Summary

- Predicates
- Variables
- Quantifiers
  - Universal Quantifier
  - Existential Quantifier
- Negating Quantifiers
  - De Morgan’s Laws for Quantifiers
- Translating English to Logic
- Logic Programming (optional)

## Propositional Logic Not Enough

If we have:

“All men are mortal.”
“Socrates is a man.”

Does it follow that “Socrates is mortal?”

Can’t be represented in propositional logic. Need a language that talks about objects, their properties, and their relations.

Later we’ll see how to draw inferences.

## Introducing Predicate Logic

- Predicate logic uses the following new features:
  - Variables: x, y, z
  - Predicates: P(x), M(x)
  - Quantifiers (to be covered in a few slides):
- Propositional functions are a generalization of propositions.
  - They contain variables and a predicate, e.g., P(x)
  - Variables can be replaced by elements from their domain.

## Propositional Functions

Propositional functions become propositions (and have truth values) when their variables are each replaced by a value from the *domain* (or *bound* by a quantifier, as we will see later).

The statement $P(x)$ is said to be the value of the propositional function $P$ at $x$.

For example, let $P(x)$ denote “$x > 0$” and the domain be the integers. Then:
P(-3)  is false.
P(0)  is false.
P(3)  is true.

Often the domain is denoted by $U$. So in this example $U$ is the integers.

## Examples of Propositional Functions

Let “x + y = z” be denoted by R(x, y, z) and U (for all three variables) be the integers. Find these truth values:
R(2,-1,5)
Solution: F
R(3,4,7)
Solution: T
R(x, 3, z)
Solution: Not a Proposition

Now let “x - y = z” be denoted by Q(x, y, z), with U as the integers. Find these truth values:
Q(2,-1,3)
Solution: T
Q(3,4,7)
Solution: F
Q(x, 3, z)
Solution: Not a Proposition

## Compound Expressions

- Connectives from propositional logic carry over to predicate logic.
- If $P(x)$ denotes “$x > 0$,” find these truth values:

| Expression | Solution |
|---|---|
| $P(3) \lor P(-1)$ | T |
| $P(3) \land P(-1)$ | F |
| $P(3) \to P(-1)$ | F |
| $P(3) \to P(-1)$ | T |

- Expressions with variables are not propositions and therefore do not have truth values. For example,

  $P(3) \land P(y)$

  $P(x) \to P(y)$

- When used with quantifiers (to be introduced next), these expressions (propositional functions) become propositions.

## Quantifiers

![](img/c25dfd82fc242c2db53bc942dcad6885_303_0.png)

Charles Peirce (1839-1914)

- We need *quantifiers* to express the meaning of English words including *all* and *some*:
  - “All men are Mortal.”
  - “Some cats do not have fur.”
- The two most important quantifiers are:
  - *Universal Quantifier*, “For all,” symbol: ∀
  - *Existential Quantifier*, “There exists,” symbol: ∃
- We write as in ∀x P(x) and ∃x P(x).
- ∀x P(x) asserts P(x) is true for *every* x in the *domain*.
- ∃x P(x) asserts P(x) is true for *some* x in the *domain*.
- The quantifiers are said to bind the variable x in these expressions.
