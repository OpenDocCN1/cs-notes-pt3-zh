

## Bentley-McIlroy 三路划分

之后，将相等键交换到中心。

- 从右到左扫描 j 和 p 并交换 a[j] 与 a[p]。
- 从左到右扫描 i 和 q 并交换 a[i] 与 a[q]。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_214_0.png)

exchange a[j] with a[p]

## Bentley-McIlroy 三路划分

之后，将相等键交换到中心。

- 从右到左扫描 j 和 p 并交换 a[j] 与 a[p]。
- 从左到右扫描 i 和 q 并交换 a[i] 与 a[q]。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_215_0.png)

exchange a[j] with a[p]

## Bentley-McIlroy 三路划分

之后，将相等键交换到中心。

- 从右到左扫描 j 和 p 并交换 a[j] 与 a[p]。
- 从左到右扫描 i 和 q 并交换 a[i] 与 a[q]。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_216_0.png)

exchange a[i] with a[q]

## Bentley-McIlroy 三路划分

之后，将相等键交换到中心。

- 从右到左扫描 j 和 p 并交换 a[j] 与 a[p]。
- 从左到右扫描 i 和 q 并交换 a[i] 与 a[q]。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_217_0.png)

exchange a[i] with a[q]

## Bentley-McIlroy 三路划分

之后，将相等键交换到中心。

- 从右到左扫描 j 和 p 并交换 a[j] 与 a[p]。
- 从左到右扫描 i 和 q 并交换 a[i] 与 a[q]。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_218_0.png)

## Lecture 5 Sort(III)

- 优先队列和堆排序
- 线性时间排序

## Priority queues

*priority queue* 是一种用于维护元素集合 S 的数据结构，每个元素都有一个相关联的值称为 *key*。
*max-priority queue* 支持以下操作：

- insert(S, x)
- max(S)
- delete-max(S)
- decrease-key(x, key)

## Array and sorted array

|  | Maximum | Insert | DeleteMax |
|---|---|---|---|
| Array | O(n) | O(1) | O(n) |
| Sorted array | O(1) | O(n) | O(1) |

Data structure matters.

## Binary tree

### Almost complete binary tree

### Array representation

complete tree with N = 16 nodes (height = 4)

Property. Height of an almost complete tree with N nodes is ⌊log N⌋.

Heap representations

![](img/a8f1b433a70f1e5c410c8b43e41b650e_223_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_223_1.png)

## Binary tree

![](img/a8f1b433a70f1e5c410c8b43e41b650e_224_0.png)

## Binary Heap

A *max-heap* (*min-heap*) is an *almost complete* *binary tree* with vertices satisfying the *max-heap* (*min-heap*) *property*:

*If v and p(v) are a vertex and its parent respectively, then p(v) ≥ v (p(v) ≤ v).*

![](img/a8f1b433a70f1e5c410c8b43e41b650e_225_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_225_1.png)

## Insert: SiftUp

![](img/a8f1b433a70f1e5c410c8b43e41b650e_226_0.png)

## Insert: SiftUp

![](img/a8f1b433a70f1e5c410c8b43e41b650e_227_0.png)

## Insert: SiftUp

![](img/a8f1b433a70f1e5c410c8b43e41b650e_228_0.png)

## Insert: SiftUp

![](img/a8f1b433a70f1e5c410c8b43e41b650e_229_0.png)

## Insert: SiftUp

![](img/a8f1b433a70f1e5c410c8b43e41b650e_230_0.png)

O(logn)

## Insert: SiftUp

![](img/a8f1b433a70f1e5c410c8b43e41b650e_231_0.png)

Algorithm 3.3 Insert

Input: A heap H[1..n] and a heap element x.

Output: A new heap H[1..n + 1] with x being one of its elements.

- 1. n ← n + 1
- 2. H[n] ← x
- 3. SiftUp(H, n)

SiftUp(H,i)

- 1. done ← false
- 2. if i = 1 then exit
- 3. repeat
- 4. if key(H[i]) > key(H[⌊i/2⌋])
- 5. then interchange H[i] and H[⌊i/2⌋]
- 6. else done ← true
- 7. i ← ⌊i/2⌋
- 8. until i = 1 or done

![](img/a8f1b433a70f1e5c410c8b43e41b650e_231_1.png)

## Decrease-key: SiftUp

![](img/a8f1b433a70f1e5c410c8b43e41b650e_232_0.png)

O(logn)

## Delete-maximum: SiftDown

![](img/a8f1b433a70f1e5c410c8b43e41b650e_234_0.png)

O(2 log n)

```
SiftDown(H,i)
1. done ← false
2. if 2i > n then exit
3. repeat
4.   i ← 2i
5.   if i + 1 ≤ n and key(H[i + 1]) > key(H[i])
6.   then i ← i + 1
7.   if key(H[⌊i/2⌋]) < key(H[i])
8.   then interchange H[i] and H[⌊i/2⌋]
9.   else done ← true
10. until 2i > n or done
```
