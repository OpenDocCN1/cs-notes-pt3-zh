
## Correctness of Euclidean Algorithm

- Suppose that $a$ and $b$ are positive integers with $a \ge b$. Let $r_0 = a$ and $r_1 = b$. Successive applications of the division algorithm yield:

\[
\begin{aligned}
r_0 &= r_1 q_1 + r_2 & 0 &\le r_2 < r_1,\\
r_1 &= r_2 q_2 + r_3 & 0 &\le r_3 < r_2,\\
&\vdots\\
r_{n-2} &= r_{n-1} q_{n-1} + r_n & 0 &\le r_n < r_{n-1},\\
r_{n-1} &= r_n q_n.
\end{aligned}
\]

- Eventually, a remainder of zero occurs in the sequence of terms: $a = r_0 > r_1 > r_2 > \cdots \ge 0$. The sequence can’t contain more than $a$ terms.

- By Lemma 1,

\[
\gcd(a,b) = \gcd(r_0,r_1) = \cdots = \gcd(r_{n-1},r_n) = \gcd(r_n, 0) = r_n.
\]

- Hence the greatest common divisor is the last nonzero remainder in the sequence of divisions.

## gcds as Linear Combinations

**Bézout’s Theorem**: If $a$ and $b$ are positive integers, then there exist integers $s$ and $t$ such that $\gcd(a,b) = sa + tb$. *(proof in exercises of Section 5.2)*

**Definition**: If $a$ and $b$ are positive integers, then integers $s$ and $t$ such that $\gcd(a,b) = sa + tb$ are called *Bézout coefficients* of $a$ and $b$. The equation $\gcd(a,b) = sa + tb$ is called *Bézout’s identity*.

- By Bézout’s Theorem, the gcd of integers $a$ and $b$ can be expressed in the form $sa + tb$ where $s$ and $t$ are integers. This is a *linear combination* with integer coefficients of $a$ and $b$.
  - $\gcd(6,14) = (-2) \cdot 6 + 1 \cdot 14$

## Finding gcds as Linear Combinations

**Example:** Express $\gcd(252,198) = 18$ as a linear combination of 252 and 198.

**Solution:** First use the Euclidean algorithm to show $\gcd(252,198) = 18$.

- i. $252 = 1 \cdot 198 + 54$
- ii. $198 = 3 \cdot 54 + 36$
- iii. $54 = 1 \cdot 36 + 18$
- iv. $36 = 2 \cdot 18$

Now working backwards, from iii and ii above

- $18 = 54 - 1 \cdot 36$
- $36 = 198 - 3 \cdot 54$

Substituting the 2nd equation into the 1st yields:

- $18 = 54 - 1 \cdot (198 - 3 \cdot 54) = 4 \cdot 54 - 1 \cdot 198$

Substituting $54 = 252 - 1 \cdot 198$ (from i) yields:

- $18 = 4 \cdot (252 - 1 \cdot 198) - 1 \cdot 198 = 4 \cdot 252 - 5 \cdot 198$

This method illustrated above is a two-pass method. It first uses the Euclidean algorithm to find the gcd and then works backwards to express the gcd as a linear combination of the original two integers. A one-pass method, called the *extended Euclidean algorithm*, is developed in the exercises.

## Consequences of Bézout’s Theorem

**Lemma 2:** If $a$, $b$, and $c$ are positive integers such that $\gcd(a,b) = 1$ and $a \mid bc$, then $a \mid c$.

**Proof:** Assume $\gcd(a,b) = 1$ and $a \mid bc$.

- Since $\gcd(a,b) = 1$, by Bézout’s Theorem there are integers $s$ and $t$ such that $sa + tb = 1$.
- Multiplying both sides of the equation by $c$ yields $sac + tbc = c$.
- From Theorem 1 of Section 4.1:
  - $a \mid tbc$ (part ii) and $a$ divides $sac + tbc$ since $a \mid sac$ and $a \mid tbc$ (part i)
- We conclude $a \mid c$, since $sac + tbc = c$.

**Lemma 3:** If $p$ is prime and $p \mid a_1a_2\cdots a_n$, then $p \mid a_i$ for some $i$. *(proof uses mathematical induction; see Exercise 64 of Section 5.1)*

- Lemma 3 is crucial in the proof of the uniqueness of prime factorizations.

## Uniqueness of Prime Factorization

We will prove that a prime factorization of a positive integer where the primes are in nondecreasing order is unique. (This is part of the fundamental theorem of arithmetic. The other part, which asserts that every positive integer has a factorization into primes, will be proved in Section 5.2.)

**Proof:** *(by contradiction)* Suppose that the positive integer $n$ can be written as a product of primes in two distinct ways:

\[
n = p_1 p_2 \cdots p_s \quad \text{and} \quad n = q_1 q_2 \cdots q_t.
\]

Remove all common primes from the factorizations to get

\[
p_{i_1} p_{i_2} \cdots p_{i_u} = q_{j_1} q_{j_2} \cdots q_{j_v}.
\]

By Lemma 3, it follows that $p_{i_1}$ divides $q_{j_k}$, for some $k$, contradicting the assumption that $p_{i_1}$ and $q_{j_k}$ are distinct primes.

Hence, there can be at most one factorization of $n$ into primes in nondecreasing order.

## Solving Congruences

**Section 4.4**
