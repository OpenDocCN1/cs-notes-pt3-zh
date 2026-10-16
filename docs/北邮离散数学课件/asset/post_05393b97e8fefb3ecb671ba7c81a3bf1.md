
## (2) 构造 S_{i+1}

- a） b₁ = a₁， b₂ = a₂， ...， b_{m-1} = a_{m-1}
- b） b_m = a_m +1
- c） b_{m+1} = b_m +1， b_{m+2} = b_{m+1} + 1， ...， b_k = b_{k-1} + 1

注：

不用担心 b_k 会取到大于 n 的数

例：

n = 10，k = 7。若 m = 5，则
（a₁，a₂，a₃，a₄，a₅，a₆，a₇）
与（4，5，6，7，8，9，10）比较
由于 m = 5，据算法，a₅不会取到 8，只能小于 8，于是 bₘ = aₘ + 1 至多是 8，a₆，a₇至多是 9 和 10，不会取到大于 10 的数。

例 3：求 { 1，2，...，10 } 的 6 子集，共有 C₁₀⁶ = 210 个，当 Sᵢ = { 2，3，5，6，9，10 } 时，求 Sᵢ₊₁。

Sᵢ = { 2, 3, 5, 6, 9, 10 }
与 { 5, 6, 7, 8, 9, 10 } 比较
6 ≠ 8, aₘ = 6, m = 4,
于是 b₁ = a₁ = 2, b₂ = a₂ = 3, b₃ = a₃ = 5,
 b₄ = a₄ + 1 = 7, b₅ = 7 + 1 = 8,
 b₆ = 8 + 1 = 9
得 Sᵢ₊₁ = { 2, 3, 5, 7, 8, 9 }

继续求:
Sᵢ₊₂ = { 2, 3, 5, 7, 8, 10 }
Sᵢ₊₃ = { 2, 3, 5, 7, 9, 10 }
Sᵢ₊₄ = { 2, 3, 5, 8, 9, 10 }
Sᵢ₊₅ = { 2, 3, 6, 7, 8, 9 }
......

## 定理二：

对 n 个元素的 k 子集组合，用字典序组合法，可由 { 1，2，…，k } 开始，到 { n−k+1，n−k+2，…，n−1，n } 结束，共有 Cₙᵏ 个组合。

## 作业

- § 6.1 — 46, 48, 70
- § 6.2 — 12, 26, 46
- § 6.3 — 28, 40, 44
- § 6.5 — 14, 20, 34, 46
- § 6.6 — 12

## 作业

- § 6.1 46, 50
- § 6.2 12, 26, 46
- § 6.3 28, 44
- § 6.5 14, 20, 34, 46

How many solutions are there to the inequality

X1+X2+X3 ≤ 11

Where X1 ,X2 and X3 are nonnegative integers?

## Groups and Coding

## Groups and Coding （分组和编码）

Coding of Binary Information and Error Detection （检测）

Decoding and Error Correction

## Coding of Binary Information and Error Detection（错误检测）

- Encoding（编码） function
- Hamming distance（海明距离）
- Group Codes
- Parity check matrix（奇偶校验矩阵）

## Coding theory

In today’s modern world of communication, data items(项目) are constantly being transmitted (传输) from point to point. The basic problem in transmission of data is that of receiving the data as sent and not receiving a distorted (扭曲的) piece of data.

Coding theory has developed techniques for introducing redundant information(引入冗余信息) in transmitted data that help in detecting (检测), and sometimes in correcting, errors.

## Unit of information

*Message*(消息) is a finite sequence of characters from a finite alphabet *B* = {0, 1}

*Word*(字) is a sequence of *m* 0's and 1's.

## Groups

The set $B$ is a group under the binary operation + (mod 2 addition模2加 )

It follows that $B^m = B \times B \times ... \times B$ ($n$ factors) is a group under the operator $\oplus$ defined by

$(x_1, x_2, ..., x_m) \oplus (y_1, y_2, ..., y_m)$
$= (x_1 + y_1, x_2 + y_2, ..., x_m + y_m)$

An element in $B^m$ will be written as $(b_1,b_2,..., b_m)$ or more simply as $b_1b_2...b_m$

## Transmission（传输） channel and Noise

An element x ∈ B^m is sent through the transmission channel and is received as an element x_t ∈ B^m.

![](img/c25dfd82fc242c2db53bc942dcad6885_724_0.png)

## Transmission channel and Noise

Noise(噪声) in the transmission channel may cause a 0 to be received as a 1, or vice versa(反之亦然), lead x ≠ xₜ

![](img/c25dfd82fc242c2db53bc942dcad6885_725_0.png)

## Encoding function - 编码函数

Choose: an integer n>m and a one-to-one function e: B^m → B^n

e is called an (m, n) encoding function, representing every word in B^m as a word in B^n.
If b ∈ B^m, then e(b) is called the code word(码字) representing b.

![](img/c25dfd82fc242c2db53bc942dcad6885_726_0.png)

## Encoding function

If the transmission channel is noiseless, then $x_t = x$ for all $x$ in $B^n$.

In this case $x = e(b)$ is received for each $b \in B^m$, and since $e$ is a known function, $b$ may be identified.

![](img/c25dfd82fc242c2db53bc942dcad6885_727_0.png)

## Encoding function

In general, errors in transmission do occur.
We will say that the code word $x = e(b)$ has been transmitted with *k or fewer errors* if $x$ and $x_t$ differ in at least 1 but no more than $k$ positions.[k表示Bn里面码字之间的距离]

![](img/c25dfd82fc242c2db53bc942dcad6885_728_0.png)

## Error detect – 误差检测

Let e: B^m → B^n be an (m, n) encoding function.
e detects k or fewer errors if whenever x = e(b) is transmitted with k or fewer errors, then x_t is not a code word (thus x_t could not be x and therefore could not have been correctly transmitted).

For b ∈ B^n, the number of 1's in x is called the weight(权) of x and is denoted by |x|
