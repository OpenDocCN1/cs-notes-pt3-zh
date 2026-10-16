# Solution 30.1-2

$a_0 + a_1 x + \cdots + a_{n-1} x^{n-1} = \sum_{j=0}^{n-1} a_j x^j =$

$A(x) = q(x)(x - x_0) + r$

$= (q_0 + q_1 x + \cdots + q_{n-2} x^{n-2})(x - x_0) + r$

$= (r - q_0 x_0) + (q_0 - q_1 x_0) x + \cdots + (q_{n-3} - q_{n-2} x_0) x^{n-2} + q_{n-2} x^{n-1}$

$\begin{cases} r - q_0 x_0 = a_0 \\ q_0 - q_1 x_0 = a_1 \\ \cdots \\ q_{n-3} - q_{n-2} x_0 = a_{n-2} \\ q_{n-2} = a_{n-1} \end{cases} \implies \begin{cases} r = a_0 + q_0 x_0 \\ q_0 = a_1 + q_1 x_0 \\ \cdots \\ q_{n-3} = a_{n-2} + q_{n-2} x_0 \\ q_{n-2} = a_{n-1} \end{cases}$

Θ(1)
Θ(1)
Θ(1)
Θ(1)

Θ(n)