# Graph Theorem

Graph Theorem. Let f(x) be a partial function. Then f(x) is computable iff the predicate ‘f(x) ≃ y’ is partially decidable iff {π(x,y) | f(x) ≃ y} is r.e.

Proof. If f(x) is computable by P(x), then

f(x) ≃ y ↔ ∃t.(P(x) ↓ y in t steps)

The predicate ‘P(x) ↓ y in t steps’ is primitive recursive.

Conversely let R(x,y,t) be such that

f(x) ≃ y ↔ ∃t.R(x,y,t).

Now f(x) = μy.R(x,y, μt.R(x,y,t)).