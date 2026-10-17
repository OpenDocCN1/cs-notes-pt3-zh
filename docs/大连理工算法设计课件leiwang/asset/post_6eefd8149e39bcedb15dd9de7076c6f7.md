

## Asymptotic notation

We write f(n) = O(g(n)) if there exist constants c > 0, n₀ > 0 such that 0 ≤ f(n) ≤ c g(n) for all n ≥ n₀.

EXAMPLE: 2n² = O(n³) (c = 1, n₀ = 2)

functions, not values

funny, “one-way” equality

## Set definition of O-notation

O(g(n)) = { f(n) : there exist constants c > 0, n₀ > 0 such that 0 ≤ f(n) ≤ cg(n) for all n ≥ n₀ }

**EXAMPLE:** 2n² ∈ O(n³)

(Logicians: λn.2n² ∈ O(λn.n³), but it’s convenient to be sloppy, as long as we understand what’s *really* going on.)

## Macro substitution

**Convention:** A set in a formula represents an anonymous function in the set.

**EXAMPLE:** \( f(n) = n^3 + O(n^2) \) means \( f(n) = n^3 + h(n) \) for some \( h(n) \in O(n^2) \).

EXAMPLE: n² + O(n) = O(n²)
means
for any f(n) ∈ O(n):
n² + f(n) = h(n)
for some h(n) ∈ O(n²) .

## Ω-notation (lower bounds)

O-notation is an upper-bound notation. It makes no sense to say f(n) is at least O(n²).

Ω(g(n)) = {f(n) : there exist constants c > 0, n₀ > 0 such that 0 ≤ cg(n) ≤ f(n) for all n ≥ n₀}

## Θ-notation (tight bounds)

Θ(g(n)) = O(g(n)) ∩ Ω(g(n))

**EXAMPLE:** 1/2 n² - 2n = Θ(n²)

## o-notation and ω-notation

O-notation and Ω-notation are like ≤ and ≥. o-notation and ω-notation are like < and >.

o(g(n)) = { f(n) : for any constant c > 0,
there is a constant n₀ > 0
such that 0 ≤ f(n) < c g(n)
for all n ≥ n₀ }

EXAMPLE: 2n² = o(n³) (n₀ = 2/c)

ω(g(n)) = { f(n) : for any constant c > 0, there is a constant n₀ > 0 such that 0 ≤ cg(n) < f(n) for all n ≥ n₀ }

**EXAMPLE:** \(\sqrt{n} = \omega(\lg n)\quad (n_0 = 1+1/c)\)

## Solving recurrences

- The analysis of merge sort from **_Lecture 1_** required us to solve a recurrence.
- Recurrences are like solving integrals, differential equations, etc.
  - Learn a few tricks.
- **_Lecture 3_**: Applications of recurrences to divide-and-conquer algorithms.

## Substitution method

The most general method:

1. Guess the form of the solution.
2. Verify by induction.
3. Solve for constants.

## Example of substitution

T(n) = 4T(n/2) + n
≤ 4c(n/2)³ + n
= (c/2)n³ + n
= cn³ - ((c/2)n³ - n) ← desired − residual
≤ cn³ ← desired

whenever (c/2)n³ - n ≥ 0, for example,
if c ≥ 2 and n ≥ 1. residual

## Example (continued)

- We must also handle the initial conditions, that is, ground the induction with base cases.
- **Base:** $T(n)=\Theta(1)$ for all $n<n_0$, where $n_0$ is a suitable constant.
- For $1\le n<n_0$, we have “$\Theta(1)$” $\le cn^3$, if we pick $c$ big enough.

