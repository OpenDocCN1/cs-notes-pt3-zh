

# Exam4 寻找最小值和最大值 (MaxMin)

## 最大元素

从 w[0, n-1] 中找出权重最大的元素 (重量)

```
maxElement=0
for (int i = 1; i < n; i++)
    if (w[maxElement] < w[i]) maxElement = i;
```

比较次数 (比较次数) 为 n−1。

- 明显的方法 (直接法)
  - 找出 n 个元素的最大值需要进行 n−1 次比较。
  - 找出剩余 n−1 个元素的最小值需要进行 n−2 次比较。
  - 比较总次数为 2n−3。

## 分治法

### 示例

- 找出 {3,5,6,2,4,9,3,1} 的最小值和最大值。
  - A = {3,5,6,2} 和 B = {4,9,3,1}。
  - min(A) = 2, min(B) = 1。
  - max(A) = 6, max(B) = 9。
  - min{min(A),min(B)} = 1。
  - max{max(A), max(B)} = 9。

- 选苹果；挑运动员；……

![](img/09c68ab421cfce4995ddad1430ef2637_180_0.png)

- 分治法
  - 示例
  - 划分成更小的问题

![](img/09c68ab421cfce4995ddad1430ef2637_181_0.png)

- 分治法
  - 示例
  - 解决小问题并合并

![](img/09c68ab421cfce4995ddad1430ef2637_182_0.png)

- **分治法**

```
MaxMin(L)
    if length(L)=1 or 2, we use at most one comparison.
    else
    {
        split (分裂) L into lists L1 and L2, each of n/2 elements
        (min1, max1) = MaxMin(L1)
        (min2, max2) = MaxMin(L2)
        return (Min(min1, min2), Max(max1, max2))
    }
```

**复杂度分析 (比较次数)：**

T(1)=0, T(2)=1,

T(n) = 2T(n/2)+2

= 4T(n/4)+2²+2 = 2³T(n/2³) + 2³+2²+2 = …

= 2ᵏ·T(n/2ᵏ)+2ᵏ+¹+…+2 = 2ᵏ+¹+2ᵏ+¹+…+2

= 2ᵏ⁻¹+2ᵏ−2 = **3n/2 − 2** （There, assume n=2ᵏ, Sₙ=a(1−qⁿ)/(1−q).）

- 明显方法 ($2n-3$) 与 分治法 ($3n/2-2$) 的比较

假设一次比较需要一秒。

| 时间 | $2n-3$ | $3n/2-2$ |
|---|---:|---:|
| 1 分钟 | $n=31$ | $n=41$ |
| 1 小时 | $n=1801$ | $n=2401$ |
| 1 天 | $n=43201$ | $n=57601$ |

# Exam5 多数问题 (多数问题)

- **问题**
  - 给定一个包含 n 个元素的数组 A，仅使用 “==” 测试来找出 A 中的多数元素 (出现次数超过 n/2 次)。
- **例如，给定 (2, 3, 2, 1, 3, 2, 2)，则 2 是多数元素因为 4>7/2。**
- **平凡解法：**
  - 计数 (计数) 为 O(n²)。

```
Majority(A[1, n])
for(i = 1 to n)
    M = 0
    for(j = 1 to n)
        if (i != j and A[i]==A[j]) M++
    end
    if (M>n/2) return “A[i] is the majority”
end
return “No majority”
```

分治法

```
Majority(A[1, n])
if n=1, then
    return A[1]
else
    m1=Majority(A[1, n/2])
    m2=Majority(A[n/2+1, n])
    test if m1 or m2 is the majority for A[1, n]
    return majority or no majority.
```

复杂度分析 (计数)：
T(n) = 2T(n/2)+O(n) = O(nlogn)

A=(2, 1, 3, 2, 1, 5, 4, 2, 5, 2)

f[1] = 2
f[2] = 4
f[3] = 1
f[4] = 1
f[5] = 2

然而，该问题存在线性时间算法。

```
for(i=1 to n) ++frequency[ A[i] ]
M = Max(frequency( A[j] ))
if (M > n/2)
    return "A[j] is the majority"
```

- 故事的寓意 (寓意)？

# 练习

使用一个可以比较 2 个元素重量的天平，求出 n 个元素中的第二重的一个。 （对于一个具有 n 个元素的数组，用一个天平，通过比较 2 个元素的重量，求出第二重的一个）

尝试给出一个算法，并分析其运行时间。如果使用分治法，如何描述该算法？以及其运行时间？

# 5 概率分析与随机算法

- 解释概率分析与随机算法的区别。
  （概率分析与随机算法）
- 介绍指示随机变量的技术。
  （用指示(器)随机变量来对算法进行概率分析）
- 给出另一个随机算法的例子。
  （一个随机算法实例）

![](img/09c68ab421cfce4995ddad1430ef2637_190_0.png)

