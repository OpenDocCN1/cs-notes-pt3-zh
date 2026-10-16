

## 4.4.1 主定理

### 定理 4.1

设 a≥1 且 b>1 为常数，设 f(n) 为一个函数，且 T(n) 在非负整数上由递推式 T(n)=aT(n/b)+f(n) 定义，其中我们把 n/b 解释为 ⌊n/b⌋ 或 ⌈n/b⌉。则 T(n) 可作如下渐近界定。

- 1. 若 f(n)=O(n^(log_b a)-ε) 对某个常数 ε>0 成立，则 T(n)=Θ(n^(log_b a))。
- 2. 若 f(n)=Θ(n^(log_b a))，则 T(n)=Θ(n^(log_b a) lg n)。
- 3. 若 f(n)=Ω(n^(log_b a)+ε) 对某个常数 ε>0 成立，且若 af(n/b) ≤ c f(n) 对某个常数 c<1 及所有充分大的 n 成立，则 T(n)=Θ(f(n))。

?: 设 T(n)=d.f(n)，则 T(n)=a.T(n/b)+f(n) ⇒ d.f(n)=a.d.f(n/b)+f(n) 若 a.f(n/b)>f(n)，则 d.f(n)=a.d.f(n/b)+f(n)>d.f(n)+f(n)=(d+1).f(n) ⇒ d>d+1

## 4.4.1 主定理：特殊情况

$T(n)=aT(n/b)+f(n),$

$$
T(n)=
\begin{cases}
\Theta\left(n^{\log_b a}\right), & f(n)=O\left(n^{\log_b a-\varepsilon}\right)\\
\Theta\left(n^{\log_b a}\lg n\right), & f(n)=\Theta\left(n^{\log_b a}\right)\\
\Theta(f(n)), & f(n)=\Omega\left(n^{\log_b a+\varepsilon}\right)\text{ and }af(n/b)\le cf(n)\text{ for large }n
\end{cases}
$$

其中 $\varepsilon>0$ 且 $c<1$。

- **多项式**
  - **情况 1**，$f(n)$ 必须比 $n^{\log_b a}$ 多项式地更小。
  - **情况 3**，$f(n)$ 必须比 $n^{\log_b a}$ 多项式地更大。

**示例：** $f(n)=n\lg n$,   $n^{\log_b a}=n$

- **间隙**
  - 当 $f(n)$ 比 $n^{\log_b a}$ 更小时但不是多项式地更小时，情况 1 和情况 2 之间存在间隙。
  - 同样，当 $f(n)$ 比 $n^{\log_b a}$ 更大时但不是多项式地更大时，情况 2 和情况 3 之间存在间隙。

## 4.4.2 使用主方法：一些例子

T(n) = aT(n/b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{log_b a - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{log_b a + ε}) and a f(n/b) ≤ c f(n) for large n } ∃ε > 0 , c < 1

- **T(n)=9T(n/3)+n**
  a = 9, b = 3, f(n) = n ⇒ n^{log_b a} = n^{log_3 9} = n^2 = Θ(n^2)
  ⇒ f(n) = O(n^{log_3 9 - ε}), where ε = 1 ⇒ T(n) = Θ(n^2)

- **T(n)=T(2n/3)+1**
  a = 1, b = 3/2, f(n) = 1 ⇒ n^{log_b a} = n^{log_{3/2} 1} = n^0 = 1
  ⇒ f(n) = Θ(n^{log_3 a}) = Θ(1) ⇒ T(n) = Θ(lg n)

## 4.4.2 使用主方法：一些例子

T(n) = a T(n / b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{(log_b a) - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{(log_b a)+ε}) and a f(n / b) ≤ c f(n) for large n } , ∃ ε > 0 , c < 1

- T(n) = 3 T(n/4) + n lg n

a = 3, b = 4, f(n) = n lg n ⇒ n^{log_b a} = n^{log_4 3} = O(n^{0.793})

⇒ f(n) = Ω(n^{(log_4 3)+ε}), where ε ≈ 0.2, and for sufficiently large n, a f(n / b) = 3 (n / 4) lg(n / 4) ≤ (3 / 4) n lg n = c f(n) for c = 3 / 4

⇒ T(n) = Θ(n lg n)

## 4.4.2 使用主方法：一些例子

T(n) = a T(n / b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{log_b a - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{log_b a + ε}) and a f(n / b) ≤ c f(n) for large n } ε > 0 c < 1

- T(n)=2T(n/2)+n lg n

a = 2, b = 2, f(n) = n lg n ⇒ n^{log_b a} = n,

但 f(n) / n = lg n，其渐近小于任意正常数 c 的 n^ε，即 f(n) 并不是多项式地大于 n。因此该递推式落入情况 2 和情况 3 之间的间隙。

## 练习与问题

### 使用主方法给出以下递推式的紧渐近界。

T(n) = 4T(n/2) + n .

T(n) = 4T(n/2) + n² .

T(n) = 4T(n/2) + n³ .

## 第1章至第4章复习

- 描述算法的框架
- 算法的正确性
- 算法的效率
- 分治法
- 函数的渐近分析 (渐近分析)
- 递推式

## 第1章至第4章复习

### 示例：

- 归并排序
- 两个整数的乘法
- 两个矩阵的乘法
- 寻找最小值和最大值
- 多数问题 (多数问题)

