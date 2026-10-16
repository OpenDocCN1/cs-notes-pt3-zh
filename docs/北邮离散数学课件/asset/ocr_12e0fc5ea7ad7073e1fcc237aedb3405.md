# if-then-else rule

(p ∧ cond){S₁}q
(p ∧ ¬cond){S₂}q
∴ p{if cond then S₁ else S₂}q

Example: Show that

T {if x<0 then abs:=-x else abs:=x} abs=|x|

+   - If x<0 then after the if body, abs will be |x|. If ¬(x<0), i.e., x≥0, then after the else body, abs=x, which is |x|. So the rule applies.