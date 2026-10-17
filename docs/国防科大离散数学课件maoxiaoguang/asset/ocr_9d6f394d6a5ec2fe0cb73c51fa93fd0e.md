# Clausal form

+   The conjunctive normal form is called clausal form. Particular conjuncts (i.e., elementary disjunctions) are called clauses.

+   Example:

Transition of a formula into the clausal form:
¬[((p → q) ∧ (r ∨ ¬q) ∧ ¬r) → ¬p] ⇔
((p → q) ∧ (r ∨ ¬q) ∧ ¬r) ∧ p ⇔
(¬p ∨ q) ∧ (r ∨ ¬q) ∧ ¬r ∧ p

+   The formula consists of four clauses.

The proof of contradiction:

+   (¬p ∨ q) ∧ (r ∨ ¬q) ∧ (¬p ∨ r) ∧ ¬r ∧ ¬p ∧ p