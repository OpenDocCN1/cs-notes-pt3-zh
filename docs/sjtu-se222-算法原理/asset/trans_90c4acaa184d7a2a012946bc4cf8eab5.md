

## Bentley-McIlroy 3-way partitioning

重复直到 i 和 j 指针交叉。

- 从左到右扫描 i，只要 a[i] < a[lo]。
- 从右到左扫描 j，只要 a[j] > a[lo]。
- 交换 a[i] 与 a[j]。
- 如果 a[i] == a[lo]，交换 a[i] 与 a[p] 并递增 p。
- 如果 a[j] == a[lo]，交换 a[j] 与 a[q] 并递减 q。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_203_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_204_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_205_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_206_0.png)
exchange a[i] with a[j]
![](img/a8f1b433a70f1e5c410c8b43e41b650e_208_0.png)
exchange a[j] with a[q] and decrement q
![](img/a8f1b433a70f1e5c410c8b43e41b650e_209_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_210_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_211_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_212_0.png)
pointers cross

## Bentley-McIlroy 3-way partitioning

之后，将相等键交换到中心。

- 从右到左扫描 j 和 p 并交换 a[j] 与 a[p]。
- 从左到右扫描 i 和 q 并交换 a[i] 与 a[q]。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_213_0.png)
exchange a[j] with a[p]

