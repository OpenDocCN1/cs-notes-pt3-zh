

## Analysis of D&C algorithm

T(n) = 8T(n/2) + Θ(n²)

- # submatrices
- submatrix size
- work adding submatrices

n^log_ba = n^log_28 = n^3 ⇒ CASE 1 ⇒ T(n) = Θ(n^3).

**No better than the ordinary algorithm.**

## Strassen's idea

- Multiply 2×2 matrices with only 7 recursive mults.

P₁ = a · (f − h)
P₂ = (a + b) · h
P₃ = (c + d) · e
P₄ = d · (g − e)
P₅ = (a + d) · (e + h)
P₆ = (b − d) · (g + h)
P₇ = (a − c) · (e + f)

r = P₅ + P₄ − P₂ + P₆
s = P₁ + P₂
t = P₃ + P₄
u = P₅ + P₁ − P₃ − P₇

> 7 mults, 18 adds/subs.
> **Note:** No reliance on commutativity of mult!

r = P₅ + P₄ − P₂ + P₆
= (a + d)(e + h)
+ d(g − e) − (a + b)h
+ (b − d)(g + h)
= ae + ah + de + dh
+ dg − de − ah − bh
+ bg + bh − dg − dh
= ae + bg

## Strassen’s algorithm

1. **Divide**: Partition \( A \) and \( B \) into \( (n/2)\times(n/2) \) submatrices. Form terms to be multiplied using \( + \) and \( - \).
2. **Conquer**: Perform 7 multiplications of \( (n/2)\times(n/2) \) submatrices recursively.
3. **Combine**: Form \( C \) using \( + \) and \( - \) on \( (n/2)\times(n/2) \) submatrices.

\(T(n) = 7 T(n/2) + \Theta(n^2)\)

## Analysis of Strassen

T(n) = 7 T(n/2) + Θ(n²)

$T(n)=7T(n/2)+\Theta(n^2)$

$n^{\log_b a}=n^{\log_2 7}\approx n^{2.81}\Rightarrow \text{CASE 1}\Rightarrow T(n)=\Theta(n^{\lg 7})$.

n^{log_b a} = n^{log_2 7} ≈ n^{2.81} ⇒ CASE 1 ⇒ T(n) = Θ(n^{lg 7}).

The number 2.81 may not seem much smaller than 3, but because the difference is in the exponent, the impact on running time is significant. In fact, Strassen's algorithm beats the ordinary algorithm on today's machines for n ≥ 32 or so.

\( T(n) = 7 \, T(n/2) + \Theta(n^2) \)

\( n^{\log_b a} = n^{\log_2 7} \approx n^{2.81} \Rightarrow \text{CASE 1} \Rightarrow T(n) = \Theta(n^{\lg 7}) \).

The number 2.81 may not seem much smaller than 3, but because the difference is in the exponent, the impact on running time is significant. In fact, Strassen’s algorithm beats the ordinary algorithm on today’s machines for \( n \ge 32 \) or so.

**Best to date** (of theoretical interest only): \( \Theta(n^{2.376 \cdots}) \).

![](img/5e59105b951890406cf98b2a964cb2f9_270_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_271_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_273_0.png)

## VLSI layout

**Problem:** Embed a complete binary tree with *n* leaves in a grid using minimal area.

