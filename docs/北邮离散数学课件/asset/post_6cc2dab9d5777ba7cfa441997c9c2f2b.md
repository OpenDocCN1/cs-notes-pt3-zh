
Word b ∈ B^m
to be sent

e

Encoded word
x = e(b) ∈ B^n

Transmission channel

Word x_t ∈ B^n
received

B^n

f_H(x) = x*H

B^r

f_R(x) = [x]_R = x ⊕ N

xRy if only if x^{-1} ⊕ y ∈ N

f_H(x) = f_H(y)

同构

F̄(xN) = f_H(x) = x*H

B^n/N

N是正规子群

{xN | x ∈ B^n} = {(x*H = y | y ∈ B^r)}

N = {x = e(b), b ∈ B^m} = {(x*H = 0) | x ∈ B^n}

## Decoding Function – 解码函数

Consider an (m, n) encoding function
 e: B^m → B^n.

Once the encoded word x = e(b) ∈ B^n, for b ∈ B^m, is received as the word x_t, we are faced with the problem of identifying the word b that was the original message.

## Decoding Function

Consider an (m, n) encoding function
e: B^m → B^n.

An onto function d: B^n → B^m is called an (n, m) decoding function associated with e(与e关联的译码函数) if d(x_t) = b' ∈ B^m is such that when the transmission channel has no noise, then b' = b, that is,
d o e = 1_{B^m}

## Decoding Function

The decoding function $d$ is required to be onto so that every received word can be decoded to give a word in $B^m$.

It decodes properly received words correctly, but the decoding of improperly received words may or may not be correct.

## Example 1

Consider the parity check code that is defined in Example 2 of Section 11.1

Define the decoding function \( d: B^{m+1} \rightarrow B^m \).

If \( y = y_1y_2\cdots y_my_{m+1} \in B^{m+1} \), then \( d(y) = y_1y_2\cdots y_m \)

Observe that if \( b = b_1b_2\cdots b_m \in B^m \), then

\( (d \circ e)(b) = d(e(b)) = b \)

so \( d \circ e = 1_{B^m} \)

For a concrete example, let \( m = 4 \).

Then \( d(10010) = 1001 \) and \( d(11001) = 1100 \)

### Decoding function

Let e be an (m, n) encoding function and let
d be an (n, m) decoding function
associated with e.

The pair (e, d) is said to **correct k or fewer errors**

if whenever x = e(b) is transmitted correctly or
with k or fewer errors and x<sub>t</sub> is received, then
d(x<sub>t</sub>) = b. Thus x<sub>t</sub> is decoded as the correct
message b.

### Example 2

Consider the \((m, 3m)\) encoding function defined in Example 3 of Section 11.1. Define the decoding function \(d: B^m \to B^{3m}\).

Let \(y = Y_1Y_2 \cdots Y_m Y_{m+1} \cdots Y_{2m} Y_{2m+1} \cdots Y_{3m}\), Then

\(d(y) = z_1z_2 \cdots z_m\)

where

\(z_i = \begin{cases} 1 & \text{if } \{y_i, y_{i+m}, y_{i+2m}\} \text{ has at least two 1's} \\ 0 & \text{if } \{y_i, y_{i+m}, y_{i+2m}\} \text{ has less than two 1's} \end{cases}\)

E.g. \(x_t = 011011111\), then \(d(x_t) = 011\)

### Maximum likelihood technique
- 极大似然技术

Since \( B^m \) has \( 2^m \) elements, there are \( 2^m \) code words in \( B^n \). List it as

\( x^{(1)}, x^{(2)}, \dots, x^{(2^m)} \)

If the received word is \( x_t \), we compute \( \delta(x^{(i)}, x_t) \) for \( 1 \leq i \leq 2^m \), and choose the first code word, say it is \( x^{(s)} \), such that

\( \min_{1 \leq i \leq 2^m} \{ \delta(x^{(i)}, x_t) \} = \delta(x^{(s)}, x_t) \)

## Maximum likelihood decoding function

That is, \(x^{(s)}\) is a code word that is closest to \(x_t\) and the first in the list.
If \(x^{(s)} = e(b)\), we define the *maximum likelihood decoding function* \(d\) associated with \(e\) by
\(d(x_t) = b\)

## Theorem 1

Suppose that $e$ is an $(m, n)$ encoding function and $d$ is a maximum likelihood decoding function associated with $e$. Then $(e, d)$ can correct $k$ or fewer errors if and only if the minimum distance of $e$ is at least $2k + 1$.

### Example 3

### How many errors can $(e, d)$ correct?

The (3, 8) encoding function $e: B^3 \rightarrow B^8$

e(000) = 00000000
e(001) = 10011100
e(010) = 00101101
e(011) = 10010101
e(100) = 10100100
e(101) = 10001001
e(110) = 00011100
e(111) = 00110001

and let $d$ be an (8, 3) maximum likelihood decoding function associated with $e$.

## Constructing

maximum likelihood decoding function
associated with a given group code

## Theorem 2

If K is a finite subgroup of a group G, then
every left coset of K in G has exactly as
many elements as K.
