# S-m-n Theorem

Proof

Given e, x₁, ..., xₘ, we can effectively construct the following program and its index

T(n, m + n)
:
T(1, m + 1)
Q(1, x₁)
:
Q(m, xₘ)
Pₑ

where Q(i, x) is the program Z(i), S(i), ..., S(i) x times

The injectivity is achieved by padding enough useless instructions.