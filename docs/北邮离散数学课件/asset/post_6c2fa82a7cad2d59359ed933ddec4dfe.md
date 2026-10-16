
## Recursively Defined Functions

- We use two steps to define a function with the set of nonnegative integers as its domain:
- BASIS STEP: Specify the value of the function at Zero.
- RECURSIVE STEP: Give a rule for finding its value at an integer from its values at smaller integers.

## Recursively Defined Functions

- Simplest case: One way to define a function $f:\mathbb{N}\to S$ (for any set $S$) or series $a_n = f(n)$ is to:
  - Define $f(0)$.
  - For $n>0$, define $f(n)$ in terms of $f(0),...,f(n-1)$.
- *E.g.*: Define the series $a_n := 2^n$ recursively:
  - Let $a_0 := 1$.
  - For $n>0$, let $a_n := 2a_{n-1}$.

## Another Example

- Suppose we define $f(n)$ for all $n \in \mathbf{N}$ recursively by:
  - Let $f(0)=3$
  - For all $n \in \mathbf{N}$, let $f(n+1)=2f(n)+3$
- What are the values of the following?
  - $f(1)=$ 9 $f(2)=$ 21 $f(3)=$ 45 $f(4)=93$

## Recursive definition of Factorial

- Give an inductive (recursive) definition of the factorial function,
  $F(n) :\equiv n! :\equiv \prod_{1\le i\le n} i = 1\cdot 2\cdot \dots \cdot n.$
  - Base case: $F(0) :\equiv 1$
  - Recursive part: $F(n) :\equiv n \cdot F(n-1)$.
  - $F(1)=1$
  - $F(2)=2$
  - $F(3)=6$

## More Easy Examples

- Write down recursive definitions for:
  *i+n* (*i* integer, *n* natural) using only *s(i) = i+1*.
  *a·n* (*a* real, *n* natural) using only addition
  *a^n* (*a* real, *n* natural) using only multiplication
  *∑₀≤i≤n a_i* (for an arbitrary series of numbers {a_i})
  *∏₀≤i≤n a_i* (for an arbitrary series of numbers {a_i})
  *⋂₀≤i≤n S_i* (for an arbitrary series of sets {S_i})

## The Fibonacci Series

- The *Fibonacci series* $f_{n\ge0}$ is a famous series defined by:
  $f_0 := 0,\quad f_1 := 1,\quad f_{n\ge2} := f_{n-1} + f_{n-2}$

![](img/c25dfd82fc242c2db53bc942dcad6885_541_0.png)

## Inductive Proof about Fib. series

- **Theorem:** $f_n < 2^n$.
- **Proof:** By induction. Implicitly for all $n \in \mathbb{N}$

Base cases: $f_0 = 0 < 2^0 = 1$ $f_1 = 1 < 2^1 = 2$ Note use of base cases of recursive defn

Inductive step: Use 2nd principle of induction (strong induction). Assume $\forall k < n,\ f_k < 2^k$. Then $f_n = f_{n-1} + f_{n-2}$ is $< 2^{n-1} + 2^{n-2} < 2^{n-1} + 2^{n-1} = 2^n$.

## A lower bound on Fibonacci series

- **Theorem.** For all integers $n \ge 3$, $f_n > \alpha^{n-2}$, where $\alpha = (1+5^{1/2})/2 \approx 1.61803.$
- **Proof.** (Using strong induction.)
  - Let $P(n) = (f_n > \alpha^{n-2})$.
  - **Base cases:** For $n=3$, note that $\alpha < 2 = f_3$. For $n=4$, $\alpha^2 = (1+2\cdot5^{1/2}+5)/4 = (3+5^{1/2})/2 \approx 2.61803 < 3 = f_4$.
  - **Inductive step:** For $k\ge4$, assume $P(j)$ for $3\le j\le k$, prove $P(k+1)$. Note $\alpha^2 = \alpha+1$. Thus, $\alpha^{k-1} = (\alpha+1)\alpha^{k-3} = \alpha^{k-2} + \alpha^{k-3}$. By inductive hypothesis, $f_{k-1} > \alpha^{k-3}$ and $f_k > \alpha^{k-2}$. So, $f_{k+1} = f_k + f_{k-1} > \alpha^{k-2} + \alpha^{k-3} = \alpha^{k-1}$. Thus $P(k+1)$. ■

## Lamé’s Theorem

- **Theorem:** ∀a,b∈N, a≥b>0, the number of steps in Euclid’s algorithm to find gcd(a,b) is ≤5k, where k = ⌊log₁₀ b⌋+1 is the number of decimal digits in b.
  - Thus, Euclid’s algorithm is linear-time in the number of digits in b.
- **Proof:**
  - Uses the Fibonacci sequence!
  - See next 2 slides.

![](img/c25dfd82fc242c2db53bc942dcad6885_544_0.png)

## Proof of Lamé’s Theorem

- Consider the sequence of division-algorithm equations used in Euclid’s alg.:
  $r_0 = r_1 q_1 + r_2$ with $0 \le r_2 < r_1$
  $r_1 = r_2 q_2 + r_3$ with $0 \le r_3 < r_2$
  ...
  $r_{n-2} = r_{n-1} q_{n-1} + r_n$ with $0 \le r_n < r_{n-1}$
  $r_{n-1} = r_n q_n + r_{n+1}$ with $r_{n+1} = 0$ (terminate)
- The number of divisions (iterations) is $n$.

Where $a = r_0$, $b = r_1$, and $\gcd(a,b)=r_n$.

Continued on next slide...
