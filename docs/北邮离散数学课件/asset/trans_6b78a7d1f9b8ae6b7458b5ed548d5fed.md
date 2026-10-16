

Word b ∈ B^m
待发送

e

Encoded word
x = e(b) ∈ B^n

传输信道

Word x_t ∈ B^n
接收

B^n

f_H(x) = x*H

B^r

f_R(x) = [x]_R = x ⊕ N

xRy 当且仅当 x^{-1} ⊕ y ∈ N

f_H(x) = f_H(y)

同构

F̄(xN) = f_H(x) = x*H

B^n/N

N是正规子群

{xN | x ∈ B^n} = {(x*H = y | y ∈ B^r)}

N = {x = e(b), b ∈ B^m} = {(x*H = 0) | x ∈ B^n}

## Decoding Function – 解码函数

考虑一个 (m, n) 编码函数
 e: B^m → B^n.

一旦编码字 x = e(b) ∈ B^n，对 b ∈ B^m，已被接收为字 x_t，我们面临的问题是识别原始消息为字 b。

## Decoding Function

考虑一个 (m, n) 编码函数
e: B^m → B^n.

一个满函数 d: B^n → B^m 被称为与 e 关联的 (n, m) 解码函数（与e关联的译码函数）如果 d(x_t) = b' ∈ B^m 满足当传输信道无噪声时，则 b' = b，即
d o e = 1_{B^m}

## Decoding Function

解码函数 $d$ 要求是满的，以便每个接收字都能被解码为 $B^m$ 中的一个字。

它能正确解码正确接收的字，但对错误接收字的解码可能正确也可能不正确。

## Example 1

考虑在第 11.1 节例 2 中定义的奇偶校验码

定义解码函数 \( d: B^{m+1} \rightarrow B^m \).

如果 \( y = y_1y_2\cdots y_my_{m+1} \in B^{m+1} \)，则 \( d(y) = y_1y_2\cdots y_m \)

注意到如果 \( b = b_1b_2\cdots b_m \in B^m \)，则

\( (d \circ e)(b) = d(e(b)) = b \)

所以 \( d \circ e = 1_{B^m} \)

举一个具体例子，设 \( m = 4 \).

则 \( d(10010) = 1001 \) 且 \( d(11001) = 1100 \)

### Decoding function

设 e 是一个 (m, n) 编码函数且
d 是一个与 e 关联的 (n, m) 解码函数
。

对 (e, d) 来说 **纠正 k 或更少错误**

如果当 x = e(b) 被正确传输或
有 k 或更少错误地传输且 x<sub>t</sub> 被接收时，则
d(x<sub>t</sub>) = b。于是 x<sub>t</sub> 被解码为正确的
消息 b。

### Example 2

考虑在第 11.1 节例 3 中定义的 \((m, 3m)\) 编码函数。定义解码函数 \(d: B^m \to B^{3m}\)。

设 \(y = Y_1Y_2 \cdots Y_m Y_{m+1} \cdots Y_{2m} Y_{2m+1} \cdots Y_{3m}\)，则

\(d(y) = z_1z_2 \cdots z_m\)

其中

\(z_i = \begin{cases} 1 & \text{if } \{y_i, y_{i+m}, y_{i+2m}\} \text{ has at least two 1's} \\ 0 & \text{if } \{y_i, y_{i+m}, y_{i+2m}\} \text{ has less than two 1's} \end{cases}\)

例如 \(x_t = 011011111\)，则 \(d(x_t) = 011\)

### Maximum likelihood technique
- 极大似然技术

由于 \( B^m \) 有 \( 2^m \) 个元素，\( B^n \) 中有 \( 2^m \) 个码字。将其列为

\( x^{(1)}, x^{(2)}, \dots, x^{(2^m)} \)

如果接收字是 \( x_t \)，我们计算 \( \delta(x^{(i)}, x_t) \) 对 \( 1 \leq i \leq 2^m \)，并选择第一个码字，假设它是 \( x^{(s)} \)，使得

\( \min_{1 \leq i \leq 2^m} \{ \delta(x^{(i)}, x_t) \} = \delta(x^{(s)}, x_t) \)

## Maximum likelihood decoding function

即，\(x^{(s)}\) 是最接近 \(x_t\) 的码字且在列表中排在第一位。
如果 \(x^{(s)} = e(b)\)，我们定义与 \(e\) 关联的 *最大似然解码函数* \(d\) 为
\(d(x_t) = b\)

## Theorem 1

假设 $e$ 是一个 $(m, n)$ 编码函数且 $d$ 是与 $e$ 关联的最大似然解码函数。则 $(e, d)$ 能纠正 $k$ 或更少错误当且仅当 $e$ 的最小距离至少为 $2k + 1$。

### Example 3

### How many errors can $(e, d)$ correct?

(3, 8) 编码函数 $e: B^3 \rightarrow B^8$

e(000) = 00000000
e(001) = 10011100
e(010) = 00101101
e(011) = 10010101
e(100) = 10100100
e(101) = 10001001
e(110) = 00011100
e(111) = 00110001

且设 $d$ 是与 $e$ 关联的 (8, 3) 最大似然解码函数。

## Constructing

最大似然解码函数
与给定群码关联

## Theorem 2

如果 K 是群 G 的有限子群，则
G 中 K 的每个左陪集都有与
K 相同数量的元素。

