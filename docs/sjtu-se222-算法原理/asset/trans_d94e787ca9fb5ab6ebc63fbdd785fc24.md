

## 堆与数组

|  | 最大值 | 插入 | 删除最大值 |
|---|---|---|---|
| 数组 | O(n) | O(1) | O(n) |
| 有序数组 | O(1) | O(n) | O(1) |
| 堆 | O(1) | O(log n) | O(log n) |

## 如何建堆

![](img/a8f1b433a70f1e5c410c8b43e41b650e_236_0.png)

## 堆排序

- 用全部 N 个键创建最大堆。
- 重复移除最大键。

问题：如何建堆？

![](img/a8f1b433a70f1e5c410c8b43e41b650e_237_0.png)

## 如何建堆

```
Algorithm 3.6 MakeHeap
Input: An array A[1..n] of n elements.
Output: A[1..n] is transformed into a heap.
1. for i ← ⌊n/2⌋ downto 1
2. SiftDown(A, i)
3. end for
```

## 堆排序

![](img/a8f1b433a70f1e5c410c8b43e41b650e_239_0.png)

算法 3.7 堆排序
输入：包含 n 个元素的数组 A[1..n]。
输出：数组 A[1..n] 按非递减顺序排序。

- 1. MakeHeap(A)
- 2. for j ← n downto 2
- 3. interchange A[1] and A[j]
- 4. SiftDown(A[1..j − 1],1)
- 5. end for

## 测验

给出对以下 10 个键的数组执行建堆后得到的数组：
X U M V Y T A J I N

给出在上述构建的最大堆上连续执行 3 次删除最大值后得到的数组。

- A. Y X T V M U A N I J
- B. Y X T V U M A J I N
- C. U N T J I M A
- D. U N T I J M A

## 测验

建堆的时间复杂度是多少？
堆排序的时间复杂度是多少？

- A. Θ(n)
- B. Θ(n log n)
- C. Θ(n²)
- D. 以上都不是

## 应用

- 事件驱动模拟。[排队的顾客]
- 数据压缩。[哈夫曼编码]
- 图搜索。[迪杰斯特拉算法、普里姆算法]
- 统计。[维护序列中最大的 M 个值]
- 操作系统。[负载均衡、中断处理]
- 离散优化。[装箱、调度]
- ......

## 排序总结

|  | 原地？ | 稳定？ | 最坏 | 平均 | 最好 | 备注 |
|---|---|---|---|---|---|---|
| 选择排序 | x |  | N² / 2 | N² / 2 | N² / 2 | N 次交换 |
| 插入排序 | x | x | N² / 2 | N² / 4 | N | 适用于小 N 或部分有序 |
| 希尔排序 | x |  | ? | ? | N | 代码紧凑，亚二次复杂度 |
| 快速排序 | x |  | N² / 2 | 2 N ln N | N lg N | N log N 概率保证，实践中最快 |
| 三向快速排序 | x |  | N² / 2 | 2 N ln N | N | 存在重复键时改进快速排序 |
| 归并排序 |  | x | N lg N | N lg N | N lg N | N log N 保证，稳定 |
| 堆排序 | x |  | 2 N lg N | 2 N lg N | N lg N | N log N 保证，原地 |
| ??? | x | x | N lg N | N lg N | N lg N | 排序算法的圣杯 |

## 排序的复杂度

比较次数

树的高度 =
最坏情况下的
比较次数

每种可能的排列至少对应一个叶子节点

![](img/a8f1b433a70f1e5c410c8b43e41b650e_244_0.png)

## 排序的复杂度

![](img/a8f1b433a70f1e5c410c8b43e41b650e_245_0.png)

树的高度 = 最坏情况下的比较次数

> **命题。** *任何基于比较的排序算法在最坏情况下至少需要* `log (n!) ~ nlogn` *次比较。*

## 排序总结

|  | 原地？ | 稳定？ | 最坏 | 平均 | 最好 | 备注 |
|---|---|---|---|---|---|---|
| 选择排序 | x |  | N² / 2 | N² / 2 | N² / 2 | N 次交换 |
| 插入排序 | x | x | N² / 2 | N² / 4 | N | 适用于小 N 或部分有序 |
| 希尔排序 | x |  | ? | ? | N | 代码紧凑，亚二次复杂度 |
| 快速排序 | x |  | N² / 2 | 2 N ln N | N lg N | N log N 概率保证，实践中最快 |
| 三向快速排序 | x |  | N² / 2 | 2 N ln N | N | 存在重复键时改进快速排序 |
| 归并排序 |  | x | N lg N | N lg N | N lg N | N log N 保证，稳定 |
| 堆排序 | x |  | 2 N lg N | 2 N lg N | N lg N | N log N 保证，原地 |
| 基数排序 |  | x | kN | kN | kN | 适用于 k 位数字或字符串 |
| ??? | x | x | N lg N | N lg N | N lg N | 排序算法的圣杯 |

## 哪种排序算法？

| 原始 | ? | ? | ? | ? | 已排序 |
|---|---|---|---|---|---|
| l ifo | find | data | data | data | data |
| fifo | fifo | fifo | fifo | exch | exch |
| data | data | find | find | fifo | fifo |
| type | exch | hash | hash | find | find |
| hash | hash | heap | heap | hash | hash |
| heap | heap | l ifo | l ifo | heap | heap |
| sort | less | link | link | leaf | leaf |
| link | left | list | list | left | left |
| list | leaf | push | push | less | less |
| push | l ifo | root | root | l ifo | l ifo |
| find | push | sort | sort | link | link |
| root | root | type | type | list | list |
| leaf | list | leaf | leaf | sort | next |
| tree | tree | left | tree | tree | node |
| null | null | node | null | null | null |
| path | path | null | path | path | path |
| node | node | path | node | node | push |
| left | link | tree | left | type | root |
| less | sort | exch | less | root | sink |
| exch | type | less | exch | push | sort |
| sink | sink | next | sink | sink | swap |
| swim | swim | sink | swim | swim | swim |
| next | next | swap | next | next | tree |
| swap | swap | swim | swap | swap | type |

