

## 示例继续

- 设 3∈S，且若 x,y∈S 则 x+y∈S。设 A = {n∈Z⁺ | (3|n)}。
- **定理：** A=S。**证明：** 我们证明 A⊆S 且 S⊆A。
- 为证明 A⊆S，证明 [n∈Z⁺ ∧ (3|n)]→ n∈S。
- **归纳证明。** 设 P(n):≡ n∈S。对 3 的正倍数进行归纳。基础情形：n=3，因此 3∈S 由 S 的定义。归纳步骤：已知 P(n)，证明 P(n+3)。由归纳假设，n∈S，且 3∈S，所以由 S 的定义，n+3∈S。
- 为证明 S⊆A：设 n∈S，证明 n∈A。
- **结构归纳证明。** 设 P(n):≡n∈A。两种情况：n=3（基础情形），它在 A 中，或 n=x+y（递归步骤）。我们知道 x 和 y 是正数，因为没有任何规则会生成负数。所以，x<n 且 y<n，因此根据强归纳假设，我们知道 x 和 y 在 A 中。由于 3|x 且 3|y，我们有 3|(x+y)，因此 x+y ∈ A。

## 作业

- § 5.1 32, 44, 54
- § 5.2 4, 26
- § 5.3 20, 32, 38, 48

## 递归算法 (§ 5.4)

- 递归定义可用于描述 *算法* 以及函数和集合。
- 示例：计算 $a^n$ 的过程。

```
procedure power(a ≠ 0: real, n ∈ N)
if n = 0 then return 1
else return a · power(a, n-1)
```

## 递归算法的效率

- 递归算法的时间复杂度可能关键地取决于它所做的递归调用次数。
- **示例：** *模幂运算* 对 $n$ 次幂可在做对的情况下花费 log($n$) 时间，但若稍有不同则为线性时间。
  - 任务：计算 $b^n$ **mod** $m$，其中 $m\ge2$，$n\ge0$，且 $1\le b < m$。

## 模幂算法 #1

利用 $b^n = b \cdot b^{n-1}$ 以及 $x \cdot y \ \mathbf{mod}\ m = x \cdot (y \ \mathbf{mod}\ m) \ \mathbf{mod}\ m.$  
（在家证明后者定理。）

```
procedure mpower(b≥1, n≥0, m>b ∈ N)
{Returns $b^n$ mod $m$.}
if n=0 then return 1 else
return (b·mpower(b,n−1,m)) mod m
```

注意该算法花费 Θ(n) 步！

## 模幂算法 #2

- 利用 $b^{2k} = b^{k\cdot 2} = (b^{k})^{2}$。

```
procedure mpower(b,n,m) {same signature}
    if n=0 then return 1
    else if 2|n then
        return mpower(b,n/2,m)^2 mod m
    else return (mpower(b,n-1,m)·b) mod m
```

它的时间复杂度是多少？

Θ(log n) 步

## 一个轻微的变化

几乎相同但花费 Θ(n) 时间！

```
procedure mpower(b,n,m) {same signature}
    if n=0 then return 1
    else if 2|n then
        return (mpower(b,n/2,m)·mpower(b,n/2,m)) mod m
    else return (mpower(b,n−1,m)·b) mod m
```

所做的递归调用次数至关重要！

## 递归欧几里得算法

```
procedure gcd(a, b ∈ N)
  if a = 0 then return b
  else return gcd(b mod a, a)
```

- 注意递归算法通常比迭代算法更简单编码...
- 然而，如果你的编译器不够智能，它们可能会消耗更多栈空间。

## 递归线性搜索

- 注意这里使用递归而非简单地循环 *loc := i to j* 并没有真正的优势...

```
procedure search(a: series; i, j: integer; x: item to be found)
{Find x in series a at a location ≥i and <j}
if a_i = x return i {At the right item? Return it!}
if i = j return 0 {No locations in range? Failure!}
return search(i+1, j, x) {Try rest of range}
```

## 递归二分搜索

```
procedure binarySearch(a, x, i, j) {same sig}
{Find location of x in a, ≥i and <j}
m := ⌊(i + j)/2⌋        {Go to halfway point.}
if x = aₘ return m        {Did we luck out?}
if x<aₘ ∧ i<m return        {If it’s to the left,}
    binarySearch(a,x,i,m-1){Check that ½}
else if aₘ<x ∧ m<j return    {If it’s to right,}
    binarySearch(a,x,m+1,j){Check that ½}
else return 0        {No more items, failure.}
```

## 递归斐波那契算法

```
procedure fibonacci(n ∈ N)
  if n=0 return 0
  if n=1 return 1
  return fibonacci(n-1)+fibonacci(n-2)
```

- 这是一个高效的算法吗？
  - 它在 n 上是多项式时间的吗？
- 执行了多少次加法？

