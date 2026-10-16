
## Step 2: A recursive solution

+   The overlapping-subproblems property of LCS （重叠子问题）

X_{i-1} = < x_1, x_2, ..., x_{i-1} >
Y_j = < y_1, y_2, ..., y_j >

X_i = < x_1, x_2, ..., x_i >
Y_{j-1} = < y_1, y_2, ..., y_{j-1} >

X_{i-1} = < x_1, x_2, ..., x_{i-1} >
Y_{j-1} = < y_1, y_2, ..., y_{j-1} >

c[i, j] = { 0 if i = 0 or j = 0,
 c[i-1, j-1] + 1, if i, j > 0 and x_i = y_j, (15.14)
 max(c[i-1, j], c[i, j-1]), if i, j > 0 and x_i ≠ y_j. }

For example:
X_4, Y_3

![](img/09c68ab421cfce4995ddad1430ef2637_408_0.png)

## Step 3: Computing the length of an LCS

+   - Based on equation (15.14), we could easily write an **exponential-time recursive** algorithm.

```
$$c[i,j]=\begin{cases}0,&\text{if }i=0\text{ or }j=0,\\c[i-1,j-1]+1,&\text{if }i,j>0\text{ and }x_i=y_j,\\\max(c[i-1,j],c[i,j-1]),&\text{if }i,j>0\text{ and }x_i\ne y_j.\end{cases}\tag{15.14}$$
```

```
$X_m=\langle x_1,x_2,\ldots,x_m\rangle$  
$Y_n=\langle y_1,y_2,\ldots,y_n\rangle$
```

+   - Use **dynamic programming** to compute the solutions bottom up（使用动态规划按自底向上方法进行求解）

X_m = <x₁, x₂, ..., x_m>
Y_n = <y₁, y₂, ..., y_n>

c[i, j] = 
{ 0 (if i = 0 or j = 0),
  c[i-1, j-1] + 1,
    (if i, j > 0 and x_i = y_j),
  max(c[i-1, j], c[i, j-1]),
    (if i, j > 0 and x_i ≠ y_j). }

Use table b[1..m, 1..n]
to simplify construction
of an optimal solution.
(使用b表构造最优解)

```
LCS-LENGTH(X, Y)        // X and Y as inputs
1  m ← length[X]
2  n ← length[Y]
3  for i ← 1 to m        // Table c[0..m, 0..n] stores c[i,j],
4    do c[i, 0] ← 0      // computed in row-major order.
5  for j ← 0 to n
6    do c[0, j] ← 0
7  for i ← 1 to m
8    for j ← 1 to n
9      if x_i = y_j
10       c[i, j] ← c[i-1, j-1] + 1
11       b[i, j] ← "↖"
12     else if c[i-1, j] ≥ c[i, j-1]  //use X_{i-1}, Y_j
13       c[i, j] ← c[i-1, j]
14       b[i, j] ← "↑"
15     else  c[i, j] ← c[i, j-1]
16       b[i, j] ← "←"
17 return c and b
```

$X_i=\langle x_1,x_2,\ldots,x_i\rangle$  
$Y_j=\langle y_1,y_2,\ldots,y_j\rangle$

$c[i,j]=\begin{cases}0 & (i=0\text{ or }j=0),\\ c[i-1,j-1]+1 & (i,j>0\text{ and }x_i=y_j),\\ \max(c[i-1,j],c[i,j-1]) & (i,j>0\text{ and }x_i\ne y_j).\end{cases}$

LCS 动态规划表格，行标签为 $X$ 的前缀，列标签为 $Y$ 的前缀，单元格中包含长度值及回溯箭头。

```
LCS-LENGTH(X, Y)                       // X and Y as inputs
1  m ← length[X]
2  n ← length[Y]
3  for i ← 1 to m                         // Table c[0..m, 0..n] stores c[i,j],
4      do c[i, 0] ← 0                     // computed in row-major order.
5  for j ← 0 to n
6      do c[0, j] ← 0
7  for i ← 1 to m
8      for j ← 1 to n
9          if x_i = y_j
10             c[i, j] ← c[i−1, j−1] + 1
11             b[i, j] ← ↖
12         else if c[i−1, j] ≥ c[i, j−1]       // use X_{i−1}, Y_j
13             c[i, j] ← c[i−1, j]
14             b[i, j] ← ↑
15         else  c[i, j] ← c[i, j−1]           // X_i, Y_{j−1}
16             b[i, j] ← ←
17 return c and b
```

Running time?

+   - The running time of the procedure is $O(mn)$, since each table entry takes $O(1)$ time to compute.
+   - Use $b[i,j]$ to reconstruct the elements of an LCS, the path is shaded or linked. （使用b表来重构 an LCS 的元素，路径用阴影或连线标注）

![](img/09c68ab421cfce4995ddad1430ef2637_412_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_412_1.png)

## Step 4: Constructing an LCS

+   - Initial call is `PRINT-LCS(b, X, m, n)`.
+   - Whenever we encounter a “↖” in entry `b[i,j]`, it implies that `x_i=y_j` is an element of the LCS.
+   - Procedure takes time `O(m+n)`, since at least one of `i` and `j` is decremented in each stage of the recursion. （每次递归时，`i` 和 `j` 至少有一个减值，算法的运行时间为 `O(m+n)`）

![](img/09c68ab421cfce4995ddad1430ef2637_413_0.png)

```
```text
PRINT-LCS(b, X, i, j)
1  if i=0 or j=0
2      return
3  if b[i,j] = "↖"
4      PRINT-LCS(b, X, i-1, j-1)
5      print x_i
6  else if b[i,j] = "↑"
7      PRINT-LCS(b, X, i-1, j)
8  else PRINT-LCS(b, X, i, j-1)
```
```
