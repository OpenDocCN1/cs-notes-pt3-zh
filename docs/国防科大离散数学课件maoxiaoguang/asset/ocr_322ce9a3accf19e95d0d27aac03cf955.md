# Example

Show that (p ∧ q) → (p ∨ q) is a Tautology.

(Proof)

```
(p ∧ q) → (p ∨ q)
⇔ ¬(p ∧ q) ∨ (p ∨ q) Implication
⇔ (¬p ∨ ¬q) ∨ (p ∨ q) De Morgan
⇔ (¬p ∨ p) ∨ (¬q ∨ q) Commutative, Associative
⇔ T ∨ T Negation
⇔ T Identity
```