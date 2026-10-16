
## 4.4.1 The master theorem

### Theorem 4.1

Let a≥1 and b>1 be constants, let f(n) be a function, and let T(n) be defined on the nonnegative integers by the recurrence T(n)=aT(n/b)+f(n), where we interpret n/b to mean either ⌊n/b⌋ or ⌈n/b⌉. Then T(n) can be bounded asymptotically as follows.

- 1. If f(n)=O(n^(log_b a)-ε) for some constant ε>0, then T(n)=Θ(n^(log_b a)).
- 2. If f(n)=Θ(n^(log_b a)), then T(n)=Θ(n^(log_b a) lg n).
- 3. If f(n)=Ω(n^(log_b a)+ε) for some constant ε>0, and if af(n/b) ≤ c f(n) for some constant c<1 and all sufficiently large n, then T(n)=Θ(f(n)).

?: Let T(n)=d.f(n), then T(n)=a.T(n/b)+f(n) ⇒ d.f(n)=a.d.f(n/b)+f(n) If a.f(n/b)>f(n), then d.f(n)=a.d.f(n/b)+f(n)>d.f(n)+f(n)=(d+1).f(n) ⇒ d>d+1

## 4.4.1 The master theorem: special cases

$T(n)=aT(n/b)+f(n),$

$$
T(n)=
\begin{cases}
\Theta\left(n^{\log_b a}\right), & f(n)=O\left(n^{\log_b a-\varepsilon}\right)\\
\Theta\left(n^{\log_b a}\lg n\right), & f(n)=\Theta\left(n^{\log_b a}\right)\\
\Theta(f(n)), & f(n)=\Omega\left(n^{\log_b a+\varepsilon}\right)\text{ and }af(n/b)\le cf(n)\text{ for large }n
\end{cases}
$$

where $\varepsilon>0$ and $c<1$.

- **Polynomially**
  - **Case 1**, $f(n)$ must be polynomially smaller than $n^{\log_b a}$.
  - **Case 3**, $f(n)$ must be polynomially larger than $n^{\log_b a}$.

**Example:** $f(n)=n\lg n$,   $n^{\log_b a}=n$

- **Gap**
  - There is a gap between cases 1 and 2 when $f(n)$ is smaller than $n^{\log_b a}$ but not polynomially smaller.
  - Similarly, there is a gap between cases 2 and 3 when $f(n)$ is larger than $n^{\log_b a}$ but not polynomially larger.

## 4.4.2 Using the master method: some examples

T(n) = aT(n/b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{log_b a - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{log_b a + ε}) and a f(n/b) ≤ c f(n) for large n } ∃ε > 0 , c < 1

- **T(n)=9T(n/3)+n**
  a = 9, b = 3, f(n) = n ⇒ n^{log_b a} = n^{log_3 9} = n^2 = Θ(n^2)
  ⇒ f(n) = O(n^{log_3 9 - ε}), where ε = 1 ⇒ T(n) = Θ(n^2)

- **T(n)=T(2n/3)+1**
  a = 1, b = 3/2, f(n) = 1 ⇒ n^{log_b a} = n^{log_{3/2} 1} = n^0 = 1
  ⇒ f(n) = Θ(n^{log_3 a}) = Θ(1) ⇒ T(n) = Θ(lg n)

## 4.4.2 Using the master method: some examples

T(n) = a T(n / b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{(log_b a) - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{(log_b a)+ε}) and a f(n / b) ≤ c f(n) for large n } , ∃ ε > 0 , c < 1

- T(n) = 3 T(n/4) + n lg n

a = 3, b = 4, f(n) = n lg n ⇒ n^{log_b a} = n^{log_4 3} = O(n^{0.793})

⇒ f(n) = Ω(n^{(log_4 3)+ε}), where ε ≈ 0.2, and for sufficiently large n, a f(n / b) = 3 (n / 4) lg(n / 4) ≤ (3 / 4) n lg n = c f(n) for c = 3 / 4

⇒ T(n) = Θ(n lg n)

## 4.4.2 Using the master method: some examples

T(n) = a T(n / b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{log_b a - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{log_b a + ε}) and a f(n / b) ≤ c f(n) for large n } ε > 0 c < 1

- T(n)=2T(n/2)+n lg n

a = 2, b = 2, f(n) = n lg n ⇒ n^{log_b a} = n,

but f(n) / n = lg n, which is asymptotically less than n^ε for any positive constant c, that is f(n) is not polynomially larger than n. Consequently, the recurrence falls into the gap between case 2 and case 3.

## Exercises and problems

### Use the master method to give tight asymptotic bounds for the following recurrences.

T(n) = 4T(n/2) + n .

T(n) = 4T(n/2) + n² .

T(n) = 4T(n/2) + n³ .

## Reviews from chap1 to chap4

- Framework for describing algorithms
- Correctness of algorithms
- Efficiency of algorithms
- Divide and Conquer
- Asymptotic analysis of function (渐近分析)
- Recurrences

## Reviews from chap1 to chap4

### Examples:

- Merge sort
- Multiplication of two integers
- Multiplication of two matrices
- Finding Minimum and Maximum
- Majority problem (多数问题)
