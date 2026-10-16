

i = 0; //1次
mark1: if(!(i < n-1)) goto mark4; //n次
k = j; //n-1次
j=i+1; //n-1次
mark2: if (!(j<n)) goto mark3; //(n+2)(n-1)/2次
if (b[k] > b[j]) k =j; //n(n-1)/2次
j++; //n(n-1)/2次
goto mark2; //n(n-1)/2次
mark3: x = b[j]; //n-1次
b[i] = b[k]; //n-1次
b[k] = x; //n-1次
i++; //n-1次
goto mark1; //n-1次
mark4:
T(n) =2n²+7n-7

## 2. 算法复杂度分析

要分析的内容

站得高，看的远

## § 要分析的内容

- > 与机器和编译器相关的运行时间。
- > 时间和空间复杂度：与机器和编译器无关。
- • 假设：
- ① 指令按顺序执行
- ② 每个指令简单，且恰好花费一个时间单位
- ③ 整数大小固定且我们有无限内存
- • 通常分析以下两个函数：

T_avg(N) & T_worst(N) -- 分别作为输入规模 N 的函数，平均和最坏情况下的时间复杂度。

如果有多个输入，这些函数可能有多个参数。

## 【示例】矩阵加法

```
void add( int a[][ MAX_SIZE ],
            int b[][ MAX_SIZE ],
            int c[][ MAX_SIZE ],
            int rows, int cols )
{
    int i, j;
    for( i = 0; i < rows; i++ )  /* rows + 1 */
        for( j = 0; j < cols; j++ )  /* rows(cols+1) */
            c[i][j] = a[i][j] + b[i][j];  /* rows · cols */
}
```

A: 交换 rows 和 cols。

T(rows, cols) = 2 rows · cols + 2rows + 1

## 【示例】迭代求和列表数字的函数

$T_{sum}(n) = 2n + 3$

```
float sum ( float list[], int n )
{ /* add a list of numbers */
    float tempsum = 0;  /* count = 1 */
    int i;
    for ( i = 0; i < n; i++ )
        /* count ++ */
        tempsum += list[i]; /* count ++ */
    /* count ++ for last execution of for */
    return tempsum;  /* count ++ */
}
```

## 【示例】递归求和列表数字的函数

$T_{rsum}(n) = 2n + 2$

但计算每一步需要更多时间。

```
float rsum ( float list[], int n )
{ /* add a list of numbers */
    if ( n ) /* count ++ */
        return rsum(list, n-1) + list[n - 1];
        /* count ++ */
    return 0;  /* count ++ */
}
```

以迭代和递归求和列表的程序为例... 如果它是 3n+2 是

好问题！
让我们问问学生 ...

![](img/18fa867d493fcce0c8a4a563c309db0a_43_0.png)

## 2. 算法复杂度分析
渐进性复杂度分析

*渐近记号*

站得高，看的远

## §2 Asymptotic Notation ( O, Ω, Θ, o ) 渐进性原理及表示符号

![](img/18fa867d493fcce0c8a4a563c309db0a_45_0.png)

计数步骤的目的是预测随着 N 变化运行时间的增长，从而比较两个程序的时间复杂度。所以我们真正想知道的是 T_p 的渐近行为。

假设 T_p1(N) = c1 N² + c2 N 且 T_p2(N) = c3 N。哪个更快？

无论 c1、c2 和 c3 是什么，都会存在一个 n0，使得对于所有 N > n0，T_p1(N) > T_p2(N)。

![](img/18fa867d493fcce0c8a4a563c309db0a_45_1.png)

我明白了！所以只要我知道 T_p1 大约为 N² 而 T_p2 大约为 N，那么对于足够大的 N，P2 会更快！

## 算法渐近复杂性

- - 衡量算法复杂性的档次/规模——阶， Rate/Order of growth
- - 对时间复杂度函数T(n)，有可能， T(n)→∞， as n→∞；
- - 例如，
- T(n) = 2n² + 4n + 1，  t(n)= 2n²
- - (T(n) - t(n)) / T(n) →0， as n→∞；
- , t(n)是T(n)的渐近性态，为算法的渐近复杂性。
- - 在数学上， t(n)是T(n)的渐近表达式，是T(n)略去低阶项留下主项。它比T(n)简单。

## § 2 Asymptotic Notation

【Definition】 T(N) = O(f(N)) if there are positive constants c and n0 such that T(N) ≤ c f(N) for all N ≥ n0. -> 【定义】若存在正的常数 c 和 n0，使得对于所有 N ≥ n0，T(N) ≤ c f(N)，则 T(N) = O(f(N))。

【Definition】 T(N) = Ω(g(N)) if there are positive constants c and n0 such that T(N) ≥ c g(N) for all N ≥ n0. -> 【定义】若存在正的常数 c 和 n0，使得对于所有 N ≥ n0，T(N) ≥ c g(N)，则 T(N) = Ω(g(N))。

【Definition】 T(N) = Θ(h(N)) if and only if T(N) = O(h(N)) and T(N) = Ω(h(N)). -> 【定义】当且仅当 T(N) = O(h(N)) 且 T(N) = Ω(h(N)) 时，T(N) = Θ(h(N))。

【Definition】 T(N) = o(p(N)) if T(N) = O(p(N)) and T(N) ≠ Θ(p(N)). -> 【定义】若 T(N) = O(p(N)) 且 T(N) ≠ Θ(p(N))，则 T(N) = o(p(N))。

Note:

- > 2N + 3 = O(?)
- > 2^N + N^2 = Ω(?)

## 渐近上界记号O

![](img/18fa867d493fcce0c8a4a563c309db0a_48_0.png)

## 渐近下界记号Ω

T(n)

平行

g(n)

c=1

n₀

## 非紧上界记号。

p(n)

非平行

T(n)

c=1

n₀

## 非紧下界记号 ω

f(n)

非平行

T(n)

c=1

n₀

