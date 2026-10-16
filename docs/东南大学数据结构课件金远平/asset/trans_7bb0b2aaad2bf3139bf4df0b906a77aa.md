

# 示例 1.5 **排列生成器**

**问题：** 对于一个包含 n ≥ 1 个元素的集合，打印它的所有可能排列。

# 解决方案：

观察 (a,b,c)，答案是通过打印以下内容得到：

+   1. a 后跟 (b,c) 的所有排列
+   2. b 后跟 (a,c) 的所有排列
+   3. c 后跟 (b,a) 的所有排列

```
else {  // a[k:m] has more than one permutation.
    // generate recursively
    for (i=k; i<=m; i++) {
        swap(a[k], a[i]); // interchange a[k] and a[i]
        Permutations(a,k+1,m); // all permutations of a[k+1:m]
        swap(a[k], a[i]); // to return to the original configuration
        // important
    }
}
```

调用方式：Permutation(a,0,n-1)

# 使用 n=3 且 a[0:2]=(a,b,c) 进行尝试

((a,b,c),0,2)

((a,b,c),1,2)

((b,a,c),1,2)

((c,b,a),1,2)

((a,b,c),2,2) → a b c

((a,c,b),2,2) → a c b

((b,a,c),2,2) → b a c

((b,c,a),2,2) → b c a

((c,b,a),2,2) → c b a

((c,a,b),2,2) → c a b

# 如果没有恢复原始配置，

((a,b,c),0,2)
((a,b,c),1,2) → ((a,b,c),2,2) → a b c
((a,c,b),2,2) → a c b
((c,a,b),1,2) → ((c,a,b),2,2) → c a b
((c,b,a),2,2) → c b a
((a,b,c),1,2) 重复！
并且 b x x 的排列将会丢失。

# 练习：P32-2, P33-14

# 1.7 性能分析与
测量

**定义：** 程序的 **空间复杂度** 是其运行完成所需的内存量。程序的 **时间复杂度** 是其运行完成所需计算机时间的量。

+   1. 事前估计 --- 性能分析
+   2. 事后测试--- 性能测量

# 1.7.1 性能分析

# 1.7.1.1 空间复杂度

程序 P 的空间需求：
S(P)=c+Sₚ(instance characteristics)
我们仅关注 Sₚ。

# 示例 1.10

```
float Rsum (float *a, const int n) //compute ∑_{i=0}^{n-1} a[i] recursively
{
    if (n <=0) return 0;
    else return (Rsum(a,n-1)+a[n-1]);
}
```

实例由 n 刻画，每次调用需要 4 个字（n, a, 返回值, 返回地址），递归深度为 n+1，所以

$S_{rsum}(n)=4(n+1)$

# 1.7.1.2 时间复杂度

程序 P 的运行时间：
 tₚ(instance characteristics)

程序步被宽松地定义为程序中在语法或语义上有意义的片段，其执行时间与实例特征无关。

在教科书的 P41-43 中，对 C++ 中语句的步数有详细的分配。

我们主要关心的是程序解决特定问题实例需要多少步？

2 种方法：

+   (1) 计数
+   (2) 表格

# 示例 1.12

```
count=0;
float Rsum (float *a, const int n)
{
    count++; // for if
    if (n <=0) {
        count++; // for return
        return 0;
    }
    else {
        count++; // for return
        return (Rsum(a,n-1)+a[n-1]);
    }
}
```

t<sub>Rsum</sub>(0) = 2,
 t<sub>Rsum</sub>(n) = 2+ t<sub>Rsum</sub>(n-1)
    = 2+2+ t<sub>Rsum</sub>(n-2)
    .
    .
    .
    = 2n+ t<sub>Rsum</sub>(0)=2n+2

# 示例 1.14 斐波那契数

```
1 void Fibonnaci (int n)
2 { // compute the Fibonnaci number Fₙ
3   if (n <=1) cout << n<< endl; { // F₀=0 and F₁ =1
4 else { // compute Fₙ
5   int fn; int fnm2=0; int fnm1=1;
6   for (int i=2; i<=n; i++)
7   {
8     fn=fnm1+fnm2;
9     fnm2=fnm1;
10    fnm1=fn;
11  } //end of for
```

```
12    cout <<fn<<endl;
13 } //end of else
14 }
```

让我们使用表格来计算其总步数。

| 行 | s/e | 频率 | 总步数 |
|------|-----|-----------|-------------|
| 1 | 0 | 1 | 0 |
| 2 | 0 | 1 | 0 |
| 3 | 1 (n >1) | 1 | 1 |
| 4 | 0 | 1 | 0 |
| 5 | 2 | 1 | 2 |
| 6 | 1 | n | n |
| 7 | 0 | n-1 | 0 |
| 8 | 1 | n-1 | n-1 |
| 9 | 1 | n-1 | n-1 |
| 10 | 1 | n-1 | n-1 |
| 11 | 0 | n-1 | 0 |
| 12 | 1 | 1 | 1 |
| 13 | 0 | 1 | 0 |
| 14 | 0 | 1 | 0 |

所以
对于 n>1, t_Fibonnci(n)=4n+1,
对于 n=0 或 1, t_Fibonnci(n) =2

有时，实例特征与输入数据集的内容相关。

例如，*BinarySearch*。

因此：

+   - 最佳情况
+   - 最坏情况,
+   - 平均情况。

