# Productive Function via a Partial Function

Proposition. A set A is productive iff there is a partial recursive function p such that

∀x. (W_x ⊆ A → (p(x)↓ ∧ p(x) ∈ A \ W_x)). (1)

Proof. Suppose p is a partial recursive function satisfying (1). Let s be a primitive recursive function such that

φ_{s(x)}(y) = { y, p(x)↓ ∧ y ∈ W_x; ↑, otherwise. }

A productive function q can be defined by running p(x) and p(s(x)) in parallel and stops when either terminates.