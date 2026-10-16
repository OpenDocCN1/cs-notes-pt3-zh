# Lewis Carroll Example

![](bbox=[0.82, 0.02, 0.92, 0.16])

Charles Lutwidge Dodgson
(AKA Lewis Caroll)
(1832-1898)

The first two are called *premises* and the third is called the *conclusion*.

+   1. “All lions are fierce.”
+   2. “Some lions do not drink coffee.”
+   3. “Some fierce creatures do not drink coffee.”

Here is one way to translate these statements to predicate logic.
Let P(x), Q(x), and R(x) be the propositional functions “x is a lion,” “x is fierce,” and “x drinks coffee,” respectively.

+   1. ∀x (P(x) → Q(x))
+   2. ∃x (P(x) ∧ ¬R(x))
+   3. ∃x (Q(x) ∧ ¬R(x))

Later we will see how to prove that the conclusion follows from the premises.