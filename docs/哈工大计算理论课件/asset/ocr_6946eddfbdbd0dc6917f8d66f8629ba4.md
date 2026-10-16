# Regular expressions

+   - If a language is described by a regular expression, then it is regular.
+   Proof: ( R → NFA → A )

1) R → NFA

We consider the six cases in the formal definition of regular expressions.

+   - R = a, Then L(R) = {a}. The following NFA recognizes L(R)

![](bbox=[0.32, 0.54, 0.7, 0.65])

+   - N=({q₁,q₂},Σ,ε,q₁,{q₂}), where

δ(q₁,a) = {q₂}
δ(r,b) = ∅      for r ≠ q₁ or b ≠ a