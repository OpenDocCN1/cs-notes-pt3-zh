# Using Inverses to Solve Congruences

+   - We can solve the congruence $ax \equiv b \pmod m$ by multiplying both sides by $\bar{a}$.

**Example:** What are the solutions of the congruence $3x \equiv 4 \pmod 7$?

**Solution:** We found that $-2$ is an inverse of $3$ modulo $7$ (two slides back). We multiply both sides of the congruence by $-2$ giving

$$-2 \cdot 3x \equiv -2 \cdot 4 \pmod 7.$$

Because $-6 \equiv 1 \pmod 7$ and $-8 \equiv 6 \pmod 7$, it follows that if $x$ is a solution, then $x \equiv -8 \equiv 6 \pmod 7$.

We need to determine if every $x$ with $x \equiv 6 \pmod 7$ is a solution. Assume that $x \equiv 6 \pmod 7$. By Theorem 5 of Section 4.1, it follows that $3x \equiv 3 \cdot 6 = 18 \equiv 4 \pmod 7$, which shows that all such $x$ satisfy the congruence.

The solutions are the integers $x$ such that $x \equiv 6 \pmod 7$, namely, $6, 13, 20, \ldots$ and $-1, -8, -15, \ldots$.