# Proof by induction

**Induction step:**
For each $k \ge 0$ assume that the formula is true for $t = k$ and show that it is true for $t = k + 1$.
we have $P_{k+1} = P_k M - Y = \left[ P M^k - Y \left( \frac{M^k - 1}{M - 1} \right) \right] M - Y$
$= P M^{k+1} - Y \left( \frac{M^{k+1} - M}{M - 1} \right) - Y \left( \frac{M - 1}{M - 1} \right)$
$= P M^{k+1} - Y \left( \frac{M^{k+1} - 1}{M - 1} \right)$

Thus the formula is correct for $t = k + 1$, which proves the theorem.