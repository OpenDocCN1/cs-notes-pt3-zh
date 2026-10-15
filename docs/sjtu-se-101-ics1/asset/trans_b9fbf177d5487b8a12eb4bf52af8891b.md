

## 矩阵乘法 (jik)

```
/* jik */
for (j=0; j<n; j++) {
    for (i=0; i<n; i++) {
        sum = 0.0;
        for (k=0; k<n; k++)
            sum += a[i][k] * b[k][j];
        c[i][j] = sum;
    }
}
```

内部循环：

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1247_0.png)

- 每次内部循环迭代的未命中次数：
- A  B  C  2 次加载，0 次存储
- 0.25  1.0  0.0  misses/iter = 1.25

## 矩阵乘法 (kij)

```
/* kij */
for (k=0; k<n; k++) {
    for (i=0; i<n; i++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
```

内部循环：

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1248_0.png)

- 每次内部循环迭代的未命中次数：

| A | B | C |
|---|---|---|
| 0.0 | 0.25 | 0.25 |

2 次加载，1 次存储
misses/iter = 0.5

## 矩阵乘法 (ikj)

```
/* ikj */
for (i=0; i<n; i++) {
    for (k=0; k<n; k++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
```

内部循环：

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1249_0.png)

- 每次内部循环迭代的未命中次数：

| A | B | C |
|---|---|---|
| 0.0 | 0.25 | 0.25 |

2 次加载，1 次存储
misses/iter = 0.5

## 矩阵乘法 (ikj)

```
/* ikj */
for (i=0; i<n; i++) {
    for (k=0; k<n; k++) {
        r = a[i][k];
        for (j=0; j<n; j++)
            c[i][j] += r * b[k][j];
    }
}
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1250_0.png)

- 每次内部循环迭代的未命中次数：

A   B   C   2 次加载，1 次存储
0.0 0.25 0.25 misses/iter = 2.0

## 矩阵乘法 (jki)

```
/* jki */
for (j=0; j<n; j++) {
    for (k=0; k<n; k++) {
        r = b[k][j];
        for (i=0; i<n; i++)
            c[i][j] += a[i][k] * r;
    }
}
```

内部循环：

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1251_0.png)

# 每次内部循环迭代的未命中次数：

| A | B | C |
|---|---|---|
| 1.0 | 0.0 | 1.0 |

2 次加载，1 次存储
misses/iter = 2.0

## 矩阵乘法 (kji)

```c
/* kji */
for (k=0; k<n; k++) {
  for (j=0; j<n; j++) {
    r = b[k][j];
    for (i=0; i<n; i++)
      c[i][j] += a[i][k] * r;
  }
}
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1252_0.png)

# 每次内部循环迭代的未命中次数：

| A | B | C | Summary |
|---:|---:|---:|---|
| 1.0 | 0.0 | 1.0 | 2 loads, 1 store; misses/iter = 2.0 |

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1253_0.png)

## Pentium 矩阵乘法性能

- 性能差异为
  - 对于相同的应用程序几乎是 20 倍
- 版本对具有几乎相同的测量性能
  - 具有相同的内存引用次数和每次未命中次数
- 最差的内存行为版本运行明显更慢
  - 就每次迭代的访问次数和未命中次数而言

## Pentium 矩阵乘法性能

- 在这种情况下，未命中率是比总内存访问次数更好的性能预测指标。
- 最快的一对版本（kij 和 ikj）的性能是恒定的
  - 数组远大于任何缓存
- 预取硬件足够智能，可以识别步长为 1 的访问
  - 足够快，可以跟上紧密内部循环中的内存访问

## 内存山

## 大纲

- 内存山
- 建议阅读：6.6.1

读吞吐量 (MB/s)

步长 (x8 字节)

大小 (字节)

s1 s3 s5 s7 s9 s11 s13 s15 s32 64M 16M 4M 1M 256k 64k 16k 4k

L1

L2

L3

Mem

空间局部性的斜率

时间局部性的山脊

Core i7
2.67 GHz
32 KB L1 d-cache
256 KB L2 cache
8 MB L3 cache

## 内存山

- 读吞吐量（读带宽）
  - 程序从内存系统读取数据的速率
- 内存山
  - 读带宽相对于时间局部性和空间局部性的二维函数
  - 描述了每台计算机的内存系统能力

## 内存山主程序

```
/* mountain.c - Generate the memory mountain. */
#define MINBYTES (1 << 11)  /* Working set size ranges from 2 KB */
#define MAXBYTES (1 << 26) /* ... up to 64 MB */
#define MAXSTRIDE 64       /* Strides range from 1 to 64 */
#define MAXELEMS MAXBYTES/sizeof(data)
int data[MAXELEMS];      /* The array we'll be traversing */
```

