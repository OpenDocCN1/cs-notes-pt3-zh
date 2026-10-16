# # $n$元置换的乘法与求逆

两个 $n$ 元置换的**乘法**就是函数的复合运算
$n$ 元置换的求**逆**就是求反函数。

例 设
$$
\sigma=\begin{pmatrix}1&2&3&4&5\\5&3&2&1&4\end{pmatrix},\quad
\tau=\begin{pmatrix}1&2&3&4&5\\4&3&1&2&5\end{pmatrix}
$$

$$
\sigma\tau=\begin{pmatrix}1&2&3&4&5\\5&1&3&4&2\end{pmatrix},\quad
\tau\sigma=\begin{pmatrix}1&2&3&4&5\\1&2&5&3&4\end{pmatrix}
$$

$$
\sigma^{-1}=\begin{pmatrix}5&3&2&1&4\\1&2&3&4&5\end{pmatrix}
=\begin{pmatrix}1&2&3&4&5\\4&3&2&5&1\end{pmatrix}
$$

使用轮换表示是：

$$
\sigma\tau=(1\ 5\ 4)(2\ 3)(1\ 4\ 2\ 3)=(1\ 5\ 2)
$$
$$
\tau\sigma=(1\ 4\ 2\ 3)(1\ 5\ 4)(2\ 3)=(3\ 5\ 4)
$$
$$
\sigma^{-1}=(1\ 5\ 4)^{-1}(2\ 3)^{-1}=(4\ 5\ 1)(2\ 3)=(1\ 4\ 5)(2\ 3)
$$