

## Group Codes – 群码

An (*m*, *n*) encoding function *e*: *B*^m → *B*^n is called a *group code* if
*e*(*B*^m) = {*e*(*b*) | *e*(*b*) ∈ *B*^n } = Ran(*e*)
is a subgroup of *B*^n

## Subgroups

Recall from the definition of subgroup given in Section 9.4 that $N$ is a subgroup of $B^n$ if

+   (a) the identity of $B^n$ is in $N$,
+   (b) if $x$ and $y$ belong to $N$, then $x \oplus y \in N$, and
+   (c) if $x$ is in $N$, then its inverse is in $N$.

### Example 7: is e a group code?

Consider the (3, 6) encoding function e: B³ → B⁶ defined by

+   e(000) = 000000
+   e(001) = 001100
+   e(010) = 010011
+   e(011) = 011111
+   e(100) = 100101
+   e(101) = 101001
+   e(110) = 110110
+   e(111) = 111010

We must show that the set of all code words
N = {000000, 001100, 010011, 011111, 100101, 101001, 110110, 111010}
is a subgroup of $B^6$.

## Theorem 3

Let e: B^m → B^n be a group code. The minimum distance of e is the minimum weight of a nonzero code word.

### Proof of Theorem 3

Let δ be the minimum distance of the group code, and suppose that δ = δ(x, y), where x and y are distinct code words.

Also, let η be the minimum weight of a nonzero code word and suppose that η = |z| for a code word z.

Since e is a group code, x ⊕ y is a nonzero code word. Thus
δ = δ(x, y) = |x ⊕ y| ≥ η.

On the other hand, since 0 and z are distinct code words,
η = |z| = |z ⊕ 0| = δ(z, 0) ≥ δ

Hence η = δ.

Q.E.D.

### Example 8

The minimum distance of the group code in

```
e(000) = 000000
e(001) = 001100
e(010) = 010011
e(011) = 011111
e(100) = 100101
e(101) = 101001
e(110) = 110110
e(111) = 111010
```

is 2

To check this directly would require 28 different calculations.

## Constructing group code

## A review on Boolean matrices

mod-2 sum D ⊕ E

mod-2 Boolean product D * E

## Theorem 4

Let D and E be m × p Boolean matrices, and let F be a p × n Boolean matrix. Then (D ⊕ E) * F = (D * F) ⊕ (E * F).

That is, a distributive property holds for ⊕ and *.

### Example 5

Let $B = \{0, 1\}$, and let $+$ be the operation defined on $B$ as follows:

| + | 0 | 1 |
|---|---|---|
| 0 | 0 | 1 |
| 1 | 1 | 0 |

Then $B$ is a group.

Let D = [ d_ij ] be an m × p Boolean matrix, and let E = [ e_ij ] be a p × n Boolean matrix. We define the mod-2 Boolean product D * E as the m × n matrix F = [ f_ij ], where

f_ij = d_i1 · e_1j + d_i2 · e_2j + ⋯ + d_ip · e_pj,    1 ≤ i ≤ m,  1 ≤ j ≤ n.

This type of multiplication is illustrated in Figure 11.3. Compare this with similar figures in Section 1.5.

![](img/c25dfd82fc242c2db53bc942dcad6885_757_0.png)

### Figure 11.3

### EXAMPLE 10

We have
[1 1 0]   [1 0]   [1·1+1·1+0·0  1·0+1·1+0·1]
[0 1 1] * [1 1] = [0·1+1·1+1·0  0·0+1·1+1·1]
          [0 1]
= [0 1]
  [1 0].

## Boolean Products

Let **A**=[a_ij] be an m×k zero-one matrix,
& let **B**=[b_ij] be a k×n zero-one matrix,

The *boolean product* of **A** and **B** is like normal matrix ×, but using ∨ instead of + in the row-column “vector dot product”:

A ⊙ B = C = [c_ij] = [ ⋁_{ℓ=1}^k a_iℓ ∧ b_ℓj ]

### EXAMPLE 8 Find the Boolean product of A and B, where

A = [1 0; 0 1; 1 0], B = [1 1 0; 0 1 1].

Solution: The Boolean product A ⊙ B is given by

A ⊙ B = [(1 ∧ 1) ∨ (0 ∧ 0) (1 ∧ 1) ∨ (0 ∧ 1) (1 ∧ 0) ∨ (0 ∧ 1); (0 ∧ 1) ∨ (1 ∧ 0) (0 ∧ 1) ∨ (1 ∧ 1) (0 ∧ 0) ∨ (1 ∧ 1); (1 ∧ 1) ∨ (0 ∧ 0) (1 ∧ 1) ∨ (0 ∧ 1) (1 ∧ 0) ∨ (0 ∧ 1)]

= [1 ∨ 0 1 ∨ 0 0 ∨ 0; 0 ∨ 0 0 ∨ 1 0 ∨ 1; 1 ∨ 0 1 ∨ 0 0 ∨ 0]

= [1 1 0; 0 1 1; 1 1 0].

## Notation

We shall now consider the element
$x = x_1 x_2 ... x_n \in B^n$
as the $1 \times n$ matrix
$[x_1 x_2 ... x_n]$

## Theorem 5

Let $m$ and $n$ be nonnegative integers with $m < n$, $r = n - m$, and let $\mathbf{H}$ be an $n \times r$ Boolean matrix.

Then the function $f_H: B^n \to B^r$ defined by
$f_H(x) = x^* \mathbf{H}, \ x \in B^n$;
is a homomorphism from the group $B^n$ to the group $B^r$.

