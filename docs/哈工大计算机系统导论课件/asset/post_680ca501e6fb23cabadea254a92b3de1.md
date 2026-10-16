
## 编写高速缓存友好的代码

- 让常见的情况运行得快
  - 专注在核心函数和内循环上
- 尽量减少每个循环内部的缓存不命中数量
  - 反复引用局部变量是好的——缓存在寄存器文件中（时间局部性）
  - 步长为 1 的引用模式是好的——缓存在连续的块（空间局部性）

关键思想：通过我们对高速缓存存储器的理解来对局部性概念进行量化

## 今天

- 高速缓存的组织结构和运算
- 高速缓存对程序性能的影响
  - 存储器山
  - 重新排列以提升空间局部性

## 存储器山

- **读吞吐量**（读带宽）
  - 每秒从存储系统中读取的字节数（MB/s）
- **存储器山**：测量读带宽作为空间和时间局部性的函数
  - 一种紧凑方式来描述存储系统性能

## 存储器山测试函数

```c
long data[MAXELEMS]; /* Global array to traverse */

/* test - Iterate over first "elems" elements of
 *          array "data" with stride of "stride", using
 *          4x4 loop unrolling.
 */
int test(int elems, int stride) {
    long i, sx2=stride*2, sx3=stride*3, sx4=stride*4;
    long acc0 = 0, acc1 = 0, acc2 = 0, acc3 = 0;
    long length = elems, limit = length - sx4;

    /* Combine 4 elements at a time */
    for (i = 0; i < limit; i += sx4) {
        acc0 = acc0 + data[i];
        acc1 = acc1 + data[i+stride];
        acc2 = acc2 + data[i+sx2];
        acc3 = acc3 + data[i+sx3];
    }

    /* Finish any remaining elements */
    for (; i < length; i++) {
        acc0 = acc0 + data[i];
    }
    return ((acc0 + acc1) + (acc2 + acc3));
}
mountain/mountain.c
```

test() 函数有许多 `elems` 和 `stride` 组合。

对于每个 `elems` 和 `stride`：

1. test() 函数开始预热缓存。
2. 调用 test() 函数之后测量读吞吐量（MB/s）。

## 存储器山

- Core i7 Haswell
- 2.1 GHz
- 32 KB L1 高速缓存
- 256 KB L2 高速缓存
- 8 MB L3 高速缓存
- 64 B 块大小
- 积极预取
- 空间局部性的斜坡
- 时间局部性山脊
- 缓存吞吐量（MB/s）
- 步长（×8 字节）
- 大小（字节）

![](img/7ab811dea080313a753fa0ae68528fa9_1091_0.png)

## 今天

- 高速缓存的组织结构和运算
- 高速缓存对程序性能的影响
  - 存储器山
  - **重新排列以提升空间局部性**

## 矩阵乘法的例子

- 描述：
  - N × N 矩阵相乘
  - 矩阵元素类型是 doubles（8 字节）
  - 总共 O(N³) 个操作
  - A、B 中每个元素都要读 N 次
  - 每个目标元素中都要对 N 个值求和
    - 但也可以保持在寄存器中

```c
/* ijk */
for (i=0; i<n; i++)
    for (j=0; j<n; j++) {
        sum = 0.0;
        for (k=0; k<n; k++)
            sum += a[i][k] * b[k][j];
        c[i][j] = sum;
    }
matmul/mm.c
```

变量 `sum` 保持在寄存器中。

## 矩阵相乘不命中率分析

- 假设：
  - 块大小 = 32B（足够大 4 倍）
  - 矩阵的维数（N）是非常大的
    - 大约 1/N 为 0.0
  - 缓存不足以容纳一行
- 分析方法：
  - 看内循环的访问模式

![](img/7ab811dea080313a753fa0ae68528fa9_1094_0.png)

## 内存中 C 数组的布局（回顾）

- **C 数组分配按行顺序**
  - 每行在连续的内存位置
- **按行扫描：**
  - `for (i = 0; i < N; i++)`
    `sum += a[0][i];`
  - 访问连续的元素
  - 如果块大小（B）> sizeof(a_ij) 字节，利用空间局部性
    - 不命中率 = sizeof(a_ij) / B
- **按列扫描：**
  - `for (i = 0; i < n; i++)`
    `sum += a[i][0];`
  - 访问远隔的元素
  - 没有空间局部性！
    - 不命中率 = 1（即 100%）

## 矩阵乘法（ijk）

```c
/* ijk */
for (i=0; i<n; i++)
    for (j=0; j<n; j++) {
        sum = 0.0;
        for (k=0; k<n; k++)
            sum += a[i][k] * b[k][j];
        c[i][j] = sum;
    }
matmul/mm.c
```

内部循环：

![](img/7ab811dea080313a753fa0ae68528fa9_1096_0.png)

**每次内循环迭代不命中：**

| A | B | C |
| --- | --- | --- |
| 0.25 | 1.0 | 0.0 |

块大小 = 32B（4 doubles）

## 矩阵乘法（jik）

```c
/* jik */
for (j=0; j<n; j++) {
    for (i=0; i<n; i++) {
        sum = 0.0;
        for (k=0; k<n; k++)
            sum += a[i][k] * b[k][j];
        c[i][j] = sum;
    }
}
matmul/mm.c
```

内部循环：

![](img/7ab811dea080313a753fa0ae68528fa9_1097_0.png)

**每次内循环迭代不命中：**

| A | B | C |
| --- | --- | --- |
| 0.25 | 1.0 | 0.0 |

块大小 = 32B（4 doubles）

## 矩阵乘法（kij）

```c
/* kij */
for (k=0; k<n; k++) {
    for (i=0; i<n; i++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
matmul/mm.c
```

内部循环：

![](img/7ab811dea080313a753fa0ae68528fa9_1098_0.png)

**每次内循环迭代不命中：**

| A | B | C |
| --- | --- | --- |
| 0.0 | 0.25 | 0.25 |

块大小 = 32B（4 doubles）

## 矩阵乘法（ikj）

```c
/* ikj */
for (i=0; i<n; i++) {
    for (k=0; k<n; k++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
matmul/mm.c
```

内部循环：

![](img/7ab811dea080313a753fa0ae68528fa9_1099_0.png)

**每次内循环迭代不命中：**

| A | B | C |
| --- | --- | --- |
| 0.0 | 0.25 | 0.25 |

块大小 = 32B（4 doubles）

## 矩阵乘法（jki）

```c
/* jki */
for (j=0; j<n; j++) {
    for (k=0; k<n; k++) {
        r = b[k][j];
        for (i=0; i<n; i++)
            c[i][j] += a[i][k] * r;
    }
}
matmul/mm.c
```

内部循环：

![](img/7ab811dea080313a753fa0ae68528fa9_1100_0.png)

**每次内循环迭代不命中：**

| A | B | C |
| --- | --- | --- |
| 1.0 | 0.0 | 1.0 |

块大小 = 32B（4 doubles）
