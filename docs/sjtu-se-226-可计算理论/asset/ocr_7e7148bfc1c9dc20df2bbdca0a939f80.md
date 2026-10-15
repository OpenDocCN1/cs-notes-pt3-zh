# Undecidability Result

# Theorem

Let c be any number. The followings are undecidable.

+   (a) Acceptance Problem: `c ∈ W_x`.
+   (b) Printing Problem: `c ∈ E_x`.

# Proof

Consider the function f defined by

```
f(x,y) = { y, if x ∈ W_x, undefined, if x ∉ W_x. }
```

By s-m-n theorem there is some total computable function k(x) such that θ_{k(x)}(y) ≃ f(x,y).

It is clear that c ∈ W_{k(x)} iff x ∈ W_x iff c ∈ E_{k(x)}.