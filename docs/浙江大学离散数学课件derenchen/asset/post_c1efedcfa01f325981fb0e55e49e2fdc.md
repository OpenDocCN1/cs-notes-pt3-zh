

## Algorithms 算法

算法的概念与程序十分相似，但实际上有很大不同。程序并不都满足算法所要求的上述特征，例如有限性特征。算法代表了对特定问题的求解，而程序则是算法在计算机上的实现。因此算法也常常称为是一个能行过程。一个函数如果可以用一个算法来计算，那么我们称该函数是能行可计算的。

其中x, y为初始输入值，输出值在y中。由于x, y是正整数，所以算法在有限时间内结束。例如与x=90，y=924，算法的执行过程描述为：

924=10×90+24

90=3×24+18

24=1×18+6

18=3×6

所以，GCD（90, 924）=6。

从命题逻辑的角度来考虑，欧几里德算法也可称为一个判定过程。对于给定的x, y，该过程可以判定“x和y是互质的”（即除了1之外，x和y没有此因子）这样一个具有真假意义的命题的真值。

## 算法的计算量问题

例：f(x)=x²+2x+1

关于C和k的说明：

- 1、不唯一
- 2、是有序对作为元素的一个无限集
- 3、尽可能小

f(x)=x²+2x+1   g(x)= x²

f(x) is O(g(x)) and g(x) is O(f(x))

Example 2.

7 x²   is O(x³) ?

Example 3.

x³   is O(7 x²) ?

## Theorem 1

Theorem 1

If f(x)=a<sub>n</sub> x<sup>n</sup> +a<sub>n-1</sub> x<sup>n-1</sup>+...+a <sub>1</sub> x<sup>1</sup>+a<sub>0</sub>

where a<sub>i</sub> ∈ R, i=0,1,...,n

Then f(x) is O(x<sup>n</sup>)

## Theorem 2

Theorem 2

If f<sub>1</sub>(x) is O(g<sub>1</sub>(x)), f<sub>2</sub>(x) is O(g<sub>2</sub>(x)),

Then (f<sub>1</sub> + f<sub>2</sub>)(x) is O(max(g<sub>1</sub>(x), g<sub>2</sub>(x)) )

## Corollary 1

If $f_1(x)$ is $O(g(x))$, $f_2(x)$ is $O(g(x))$,

Then $(f_1+f_2)(x)$ is $O(g(x))$

## Theorem 3

Theorem 3

If f₁(x) is O(g₁(x)), f₂(x) is O(g₂(x)),

Then (f₁ f₂)(x) is O(g₁(x)g₂(x) )

## Definition 5

Let f and g be functions from the set of R or I to the set of R. Call that f(x) is Θ(g(x)) if f(x) is O(g(x)) and f(x) is Ω(g(x))

> Read as “f(x) is big-theta of g(x)”

> “f(x) is of order g(x)”

## Theorem 4

If \(f(x)=a_nx^n+a_{n-1}x^{n-1}+\cdots+a_1x^1+a_0\)

where \(a_i\in\mathbb{R}\), \(i=0,1,\ldots,n\)

with \(a_n\ne 0\)

Then \(f(x)\) is \(\Theta(x^n)\)

## 算法的计算复杂性

(computational complexity):

- 问题的规模 n
- 空间复杂度(space complexity): S(n)
- 时间复杂度(time complexity): T(n)

## 常用的算法复杂性分类：

- **O(1)**: constant complexity
- **O(log n)**: logarithmic complexity
- **O(n)**: linear complexity
- **O(n log n)**: n log n complexity
- **O(nᵇ)**: polynomial complexity
- **O(bⁿ)**: exponential complexity (b>1)
- **O(n!)**: factorial complexity

linear

polynomial

exponential

## 小结

### 一、算法的概念

Peano公理，递归，递推，可计算，特征

### 二、算法复杂性

表达形式，分类

## 练习题

pp90  2, 15,16

## 2.2 数论

# Number Theory

- 1、算术基本定理
- 2、同余关系
- 3、密码学基础

## 1、算术基本定理

以整数集为典型代数系统的数论知识一直被认为是既神秘又古老。虽然绝大多数人自小学生起就开始认识它，而一些数学家却一辈子踏着它在皇冠上攀。现在，计算机终于给数论这门再纯洁不过的数学分支扬起了应用的帆。我们这里介绍的虽然只是初等数论的基础知识，但它们在计算机的数据表示、数据传输以及电子商务应用中的数据保密等方面起着非常重要的作用。

## Definition 1

定义1 设a,b,c是任意的三个整数，若满足a=bc

则称b（或c）是a的因子/factor，a是b（或c）的倍数/multiple，b(或c)能整除（也称除尽/divides）a。

记为 b|a 和 c|a。

特别地，若b≠a且b≠1，则称b是a的真因子。

## Theorem 1

定理1. 设a、b、c 是任意三个整数，则下列各式成立

- (1) 若b | a，则下列各式成立 (b≠0)
- (−b) | a，b | (−a)，(−b) | (−a)，| b | | | a |
- (2) 若c | b且b | a (c≠0,b≠0)，则c | a
- (3) 若b | a (b≠0)，则b | ac
- (4) 若b | a且b | c (b≠0)，则b | (a±c)
- (5) 若a | b且b | a (a≠0,b≠0)，则a=±b

## 定理2

设 $a,b$ 是两个整数，$b\ne0$，则恰存在两个整数 $q、r$ 使满足

$a=bq+r$　　其中 $0\le r<|b|$

定理2中的等式 $a=bq+r$ 也可以用地板（下整）函数表示为

$a=b\lfloor a/b\rfloor+(a-b\lfloor a/b\rfloor)$

由此可知，定理2对于实数集 $R$ 也是成立的。

## EXAMPLE 2

定义2 设d,a₁,a₂,...,aₙ (n>=2)是任意整数，若有

d|a₁, d|a₂, ..., d|aₙ

则称d是a₁,a₂,...,aₙ的**公因子/common divisor**。

若d是a₁,a₂,...,aₙ的一个公因子，对a₁,a₂,...,aₙ的任一
个公因子c，存在c|d，则称d是a₁,a₂,...,aₙ的**最大公因子**
**/greatest common divisor**，记为(a₁,a₂,...,aₙ)。或 gcd

( a₁,a₂,...,aₙ ) 或GCD ( a₁,a₂,...,aₙ )

## theorem 3

定理3 设a、 b∈I 且满足

a=b*q+r

这里 a>b， 0<r<| b |， 则

gcd(a,b) = gcd(b,r)

## Theorem 4

## 定理4 任意两个整数都存在最大公因子。

求两个整数的最大公因子的欧几里德算法（Euclid，也称辗转相除法）。

设a、b是任意两个整数，a=q<sub>i</sub> b + r<sub>i</sub>i=0、1、2、...

## Example 1

## 例1：求133 和301 的最大公因子

| k   | 0   | 1   | 2   | 3   | 4   |
|-----|-----|-----|-----|-----|-----|
| q_k |     | 2   | 3   | 1   | 4   |
| r_k |     | 35  | 28  | 7   | 0   |

