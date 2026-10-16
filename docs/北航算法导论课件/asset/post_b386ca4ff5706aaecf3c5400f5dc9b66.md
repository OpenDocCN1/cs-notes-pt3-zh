
## 3.1.3 Ω-notation: asymptotic lower bound

- Ω – notation: For a given function g(n), we denote by Ω(g(n)) the set of functions Ω(g(n)) = {f(n): there exist positive constants c and n₀ such that 0 ≤ c g(n) ≤ f(n) for all n ≥ n₀}.
- Example of functions in Ω(n²)
  - n²
  - n² + n
  - n² + 2000n
  - 500n² − 1000n
  - n³
  - n²·0000001
  - n² lg lg lg n

## 3.1.3 Ω-notation: asymptotic lower bound

### Theorem 3.1

For any two functions f(n) and g(n), we have f(n)=Θ(g(n)) if and only if f(n)=O(g(n)) and f(n)=Ω(g(n)).

Prove: ⇒: f(n)=Θ(g(n)), then ∃c₁>0, c₂>0, n₀>0, s.t. n≥n₀, 0≤c₁g(n)≤f(n)≤c₂g(n) then n≥n₀, 0≤f(n)≤c₂g(n) ⇒ f(n)=O(g(n)) then n≥n₀, 0≤c₁g(n)≤f(n) ⇒ f(n)=Ω(g(n))

⇐: f(n)=O(g(n)), then ∃c₂>0, n₂₀>0, s.t. n≥n₂₀, 0≤f(n)≤c₂₀g(n) f(n)=Ω(g(n)), then ∃c₁₀>0, n₁₀>0, s.t. n≥n₁₀, 0≤c₁₀g(n)≤f(n) let n₀=max{n₁₀, n₂₀}, then n≥n₀, 0≤c₁₀g(n)≤f(n)≤c₂₀g(n), that is f(n)=Θ(g(n)).

## 3.1.3 Ω-notation: asymptotic lower bound

### Theorem 3.1

For any two functions f(n) and g(n), we have f(n)=Θ(g(n)) if and only if f(n)=O(g(n)) and f(n)=Ω(g(n)).

- In practice, rather than using the theorem to obtain asymptotic upper and lower bounds from asymptotically tight bounds, we usually use it to prove asymptotically tight bounds from asymptotic upper and tower bounds.

（定理作用：实际中，通常根据渐近上界和渐近下界来证明渐近紧界，而不是根据渐近紧界来得到渐近上界和渐近下界。）

## 3.1.3 Ω-notation: asymptotic lower bound

- The running time of insertion sort falls between Ω(n) and O(n²), the bounds are asymptotically tight.
- The running time of insertion sort is not Ω(n²). Why?
- It is not contradictory to say that the **worst-case running time** of insertion sort is Ω(n²). Why?
- The running time of an algorithm is Ω(g(n)), we mean that no matter what particular input of size n is chosen for each value of n, the running time on that input is at least a constant times g(n), for large n.
- （算法的运行时间为Ω(g(n))意味着对足够大的n，对输入规模为n的任意输入,其运算时间至少是g(n)的一个常数倍。）

## 3.1.5 o-notation: upper bound but not asymptotically tight

- The bound provided by O-notation may or may not be asymptotically tight.
- The bound 2n²=O(n²) is asymptotically tight, but the bound 2n=O(n²) is not.
- The o-notation denotes an upper bound that is not asymptotically tight. Formally, define o(g(n)) as the set

（非渐近紧的上界）

o(g(n)) = {f(n): for any positive constants c>0, there exits a constant n₀>0 such that 0≤f(n)<c g(n) for all n≥n₀}.

For example, 2n=o(n²), but 2n²≠o(n²).

## 3.1.5 o-notation: upper bound but not asymptotically tight

o(g(n)) = {f(n): for any positive constants c>0, there exits a constant n₀>0 such that 0≤f(n)<c g(n) for all n≥n₀}.

- The definitions of O-notation and o-notation are similar.
- The main difference
  - In f(n)=O(g(n)), the bound 0≤f(n)≤c g(n) holds for some constant c>0
  - In f(n)=o(g(n)), the bound 0≤f(n)<c g(n) holds for all constant c>0
- Intuitively, in the o-notation, the function f(n) becomes insignificant relative to g(n) as n approaches infinity; that is

limₙ→∞ f(n)/g(n) = 0

## 3.1.6 ω-notation: lower bound but not asymptotically tight

- ω-notation is to Ω-notation as o-notation is to O-notation.
- The ω-notation denotes an lower bound that is not asymptotically tight. Formally, define ω(g(n)) as the set ω(g(n)) = {f(n): for any positive constants c>0, there exists a constant n₀>0 such that 0≤c g(n)<f(n) for all n≥n₀}.

One way to define it is by f(n) ∈ ω(g(n)) if and only if g(n) ∈ o(f(n))

For example, n²/2 = ω(n), but n²/2 ≠ ω(n²).

- The relation f(n)=ω(g(n)) implies that limₙ→∞ f(n)/g(n) = ∞, if the limit exists.

## 3.1.7 Comparison of functions

- Many of the relational properties of real number apply to asymptotic comparisons.
- For the following, Assume that f(n) and g(n) are asymptotically positive.
- Transitivity (传递性)

f(n) = Θ(g(n)) and g(n) = Θ(h(n)) imply f(n) = Θ(h(n)),
f(n) = O(g(n)) and g(n) = O(h(n)) imply f(n) = O(h(n)),
f(n) = Ω(g(n)) and g(n) = Ω(h(n)) imply f(n) = Ω(h(n)),
f(n) = o(g(n)) and g(n) = o(h(n)) imply f(n) = o(h(n)),
f(n) = ω(g(n)) and g(n) = ω(h(n)) imply f(n) = ω(h(n)).
