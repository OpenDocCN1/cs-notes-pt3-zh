# Transitive closure algorithm

What we did (or rather, could have done):

+   - Compute the next matrix M_R^{[i]}, where 1 ≤ i ≤ n
+   - Do a Boolean join with the previously computed matrix

For our example:

+   - Compute M_R^{[2]} = M_R ∘ M_R
+   - Join that with M_R to yield M_R ∨ M_R^{[2]}
+   - Compute M_R^{[3]} = M_R^{[2]} ∘ M_R
+   - Join that with M_R ∨ M_R^{[2]} from above