# Combining via relational composition

Similar to function composition

Let R be a relation from A to B, and S be a relation from B to C

+   - Let a ∈ A, b ∈ B, and c ∈ C
+   - Let (a,b) ∈ R, and (b,c) ∈ S
+   - Then the composite of R and S consists of the ordered pairs (a,c)

We denote the relation by S ∘ R

Note that S comes first when writing the composition!

(a, c) ∈ S ∘ R if ∃ b such that (a, b) ∈ R, and (b,c) ∈ S