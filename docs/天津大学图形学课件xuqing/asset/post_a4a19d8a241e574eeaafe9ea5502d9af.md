
## B 样条曲线

- B样条曲线允许任意阶连续，可以通过任意数目点生成满足C₂或更高阶连续性的曲线，函数的一般形式为：

- 分类
  - 均匀B样条曲线。
  - 非均匀B样条曲线。
  - 非均匀有理B样条曲线。

$$P(u) = \sum_{k=0}^n p_k B_{k,d}(u)$$
$$u_{min} \leq u \leq u_{max}$$
$$2 \leq d \leq n+1 \text{ (阶数)}$$

$$B_{k,1}(u) = \begin{cases} 1 & u_k \leq u \leq u_{k+1} \\ 0 & otherwise \end{cases}$$

$$B_{k,d}(u) = \frac{u - u_k}{u_{k+d-1} - u_k} B_{k,d-1}(u) + \frac{u_{k+d} - u}{u_{k+d} - u_{k+1}} B_{k+1,d-1}(u)$$

## B-Spline Curves

- Continuity: C₂ or higher

- including
  - uniform
  - Non-uniform
  - NURBS

$$P(u) = \sum_{k=0}^n p_k B_{k,d}(u)$$
$$u_{min} \le u \le u_{max}$$
$$2 \le d \le n + 1$$

$$B_{k,1}(u) = \begin{cases} 1 & u_k \le u \le u_{k+1} \\ 0 & otherwise \end{cases}$$

$$B_{k,d}(u) = \frac{u - u_k}{u_{k+d-1} - u_k} B_{k,d-1}(u) + \frac{u_{k+d} - u}{u_{k+d} - u_{k+1}} B_{k+1,d-1}(u)$$

## 均匀B样条曲线

- 均匀线性B样条曲线(d=2)。
- 线性B样条曲线是通过2个一次多项式片断定义的。

$$B_{i,2}(t) = \begin{cases} u & i \leq t < i+1 \quad u = t - i \\ i - u & i+1 \leq t < i+2 \quad u = t - (i+1) \\ 0 & otherwise \end{cases}$$

$$P(u) = (i - u)p_i + u p_{i+1}$$

![](img/258e4144ed4b66c8fd4b0f298118df23_138_0.png)

## Uniform B-Spline Curves

- Uniform linearity B-Spline Curves(d=2)。

$$B_{i,2}(t) = \begin{cases} u & i \leq t < i+1 \quad u = t-i \\ i-u & i+1 \leq t < i+2 \quad u = t-(i+1) \\ 0 & otherwise \end{cases}$$

$$P(u) = (i-u)p_i + up_{i+1}$$

![](img/258e4144ed4b66c8fd4b0f298118df23_139_0.png)

## 均匀B样条曲线

- 均匀二次B样条曲线(d=3)。
- 线性B样条曲线是通过3个二次多项式片断定义的。

$$B_{i,3}(t)=\begin{cases}
\frac{1}{2}u^2, & i\le t<i+1,\quad u=t-i\\
-u^2+u+\frac{1}{2}, & i+1\le t<i+2,\quad u=t-(i+1)\\
\frac{1}{2}(i-u)^2, & i+2\le t<i+3,\quad u=t-(i+2)\\
0, & otherwise
\end{cases}$$

$$P(u)=\frac{1}{2}(i-u)^2p_i+(-u^2+u+\frac{1}{2})p_{i+1}+\frac{1}{2}u^2p_{i+2}$$

![](img/258e4144ed4b66c8fd4b0f298118df23_140_0.png)

## Uniform B-Spline Curves

- Uniform Quadratic B-Spline (d=3)。

$$B_{i,3}(t)=\begin{cases}
\frac{1}{2}u^2 & i\le t<i+1,\quad u=t-i\\
-u^2+u+\frac{1}{2} & i+1\le t<i+2,\quad u=t-(i+1)\\
\frac{1}{2}(i-u)^2 & i+2\le t<i+3,\quad u=t-(i+2)\\
0 & \text{otherwise}
\end{cases}$$

$$P(u)=\frac{1}{2}(i-u)^2p_i+\left(-u^2+u+\frac{1}{2}\right)p_{i+1}+\frac{1}{2}u^2p_{i+2}$$

![](img/258e4144ed4b66c8fd4b0f298118df23_141_0.png)

## 均匀B样条曲线

- 均匀三次B样条曲线(d=4)。
- 线性B样条曲线是通过4个三次多项式片断定义的。

$$B_{i,3}(t) = \left\{ \begin{array}{ll} \frac{1}{6}u^3 & \quad i \leq t < i+1 \quad u = t-i \\ \frac{1}{6}(-3u^3 + 3u^2 + 3u + 1) & \quad i+1 \leq t < i+2 \quad u = t-(i+1) \\ \frac{1}{6}(3u^3 - 6u^2 + 4) & \quad i+2 \leq t < i+3 \quad u = t-(i+2) \\ \frac{1}{6}(-u^3 + 3u^2 - 3u + 1) & \quad i+3 \leq t < i+4 \quad u = t-(i+3) \\ 0 & \quad otherwise \end{array} \right.$$

$$P(u) = \frac{1}{6}(-u^3 + 3u^2 - 3u + 1)p_i + \frac{1}{6}(3u^3 - 6u^2 + 4)p_{i+1} + \frac{1}{6}(-3u^3 + 3u^2 + 3u + 1)p_{i+2} + \frac{1}{6}u^3 p_{i+3}$$

![](img/258e4144ed4b66c8fd4b0f298118df23_142_0.png)

## Uniform B-Spline Curves

- Uniform Cubic B-Spline Curves (d=4)。

$$B_{i,4}(t) = \begin{cases} \frac{1}{6}u^3 & i \le t < i+1 \quad u=t-i \\ \frac{1}{6}(-3u^3 + 3u^2 + 3u + 1) & i+1 \le t < i+2 \quad u=t-(i+1) \\ \frac{1}{6}(3u^3 - 6u^2 + 4) & i+2 \le t < i+3 \quad u=t-(i+2) \\ \frac{1}{6}(-u^3 + 3u^2 - 3u + 1) & i+3 \le t < i+4 \quad u=t-(i+3) \\ 0 & otherwise \end{cases}$$

$$P(u) = \frac{1}{6}(-u^3 + 3u^2 - 3u + 1)p_i + \frac{1}{6}(3u^3 - 6u^2 + 4)p_{i+1} + \frac{1}{6}(-3u^3 + 3u^2 + 3u + 1)p_{i+2} + \frac{1}{6}u^3 p_{i+3}$$

![](img/258e4144ed4b66c8fd4b0f298118df23_143_0.png)

## 非均匀B样条曲线

- 非均匀B样条曲线通过在节点向量中取不同间距来实现。
- 使用类似于均匀B样条曲线中使用的方法，可以得到非均匀B样条曲线的混合函数。
- 实际中间距取0或1，以方便计算。

## 非均匀有理B样条曲线（NURBS）

- 虽然B样条曲线有很多优点，但是仍然有一些函数不能准确的用它们来表示。特别是B样条曲线不能表示圆锥的部分。
- 为了表示这样的曲线，采用了两个多项式的比例，用非均匀有理样条曲线表示分子和分母，最一般的形式是非均匀有理B样条曲线。
- 非均匀有理B样条把每一个控制点 $p_k$ 与一个权值 $h_k$ 相连，并对分子分母使用同样的B样条曲线。

$$P(u)=\frac{\sum_{k=1}^{n}h_k p_k B_{k,d}}{\sum_{k=1}^{n}h_k B_{k,d}}$$
