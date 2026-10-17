
## 线性结构之习题选讲

浙江大学 陈越

Copyright © 2014, 浙江大学计算机科学与技术学院  
All Rights Reserved

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_201_0.png)

## Reversing Linked List

## 什么是抽象的链表

- 有块地方存数据
- 有块地方存指针 —— 下一个结点的地址

Sample Input:

```text
00100 6 4
00000 4 99999
00100 1 12309
68237 6 -1
33218 3 00000
99999 5 68237
12309 2 33218
```

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_203_0.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_203_1.png)

Copyright © 2014, 浙江大学计算机科学与技术学院  
All Rights Reserved

## 单链表的逆转

取巧：用顺序表存储，先排序，再直接逆序输出。

在“内存”里多加几个没用的结点，让你偷懒！

```c
Ptr Reverse( Ptr head, int K )
{
    cnt = 1;
    new = head->next;
    old = new->next;
    while ( cnt < K )
    {
        tmp = old->next;
        old->next = new;
        new = old; old = tmp;
        cnt++;
    }
    head->next->next = old;
    return new;
}
```

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_204_0.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_204_1.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_204_2.png)

Copyright © 2014, 浙江大学计算机科学与技术学院  
All Rights Reserved

## 测试数据

- 有尾巴不反转
- 地址取到上下界
- 正好全反转
- K=N 全反转
- K=1 不用反转
- 最大（最后剩 K-1 不反转）、最小 N
- 有多余结点

## 边界测试

## 5.1 堆(heap)

## 若采用数组或链表实现优先队列

### 数组：

- 插入 — 元素总是插入尾部 ~ Θ(1)
- 删除 — 查找最大（或最小）关键字 ~ Θ(n)
  - 从数组中删去需要移动元素 ~ O(n)

### 链表：

- 插入 — 元素总是插入链表的头部 ~ Θ(1)
- 删除 — 查找最大（或最小）关键字 ~ Θ(n)
  - 删除结点 ~ Θ(1)

### 有序数组：

- 插入 — 找到合适的位置 ~ O(n) 或 O(log₂ n)
  - 移动元素并插入 ~ O(n)
- 删除 — 删去最后一个元素 ~ Θ(1)

### 有序链表：

- 插入 — 找到合适的位置 ~ O(n)
  - 插入元素 ~ Θ(1)
- 删除 — 删除首元素或最后元素 ~ Θ(1)

## 是否可以采用二叉树存储结构？

- 二叉搜索树？

- 如果采用二叉树结构，应更关注插入还是删除？

- 树结点顺序怎么安排？

- 树结构怎样？

## 优先队列的完全二叉树表示

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_210_0.png)

|   | a | b | c | d | e | f | g | h | i |   |   |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 |

### 堆的两个特性

- 结构性：用数组表示的完全二叉树；
- 有序性：任一结点的关键字是其子树所有结点的最大值（或最小值）
- “最大堆（MaxHeap）”，也称“大顶堆”：最大值
- “最小堆（MinHeap）”，也称“小顶堆”：最小值

## 【例】最大堆和最小堆

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_0.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_1.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_2.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_3.png)

> **注意：** 从根结点到任意结点路径上结点序列的有序性！

## 【例】不是堆

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_4.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_5.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_6.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_211_7.png)

## 堆的抽象数据类型描述

**类型名称：** 最大堆（MaxHeap）

**数据对象集：** 完全二叉树，每个结点的元素值不小于其子结点的元素值

**操作集：** 最大堆 H ∈ MaxHeap，元素 item ∈ ElementType，主要操作有：

- `MaxHeap Create( int MaxSize )`：创建一个空的最大堆。
- `Boolean IsFull( MaxHeap H )`：判断最大堆 H 是否已满。
- `insert( MaxHeap H, ElementType item )`：将元素 item 插入最大堆 H。
- `Boolean IsEmpty( MaxHeap H )`：判断最大堆 H 是否为空。
- `ElementType DeleteMax( MaxHeap H )`：返回 H 中最大元素（高优先级）。

## 最大堆的操作

### 最大堆的创建

```c
typedef struct HeapStruct *MaxHeap;
struct HeapStruct {
    ElementType *Elements; /* 存储堆元素的数组 */
    int Size; /* 堆的当前元素个数 */
    int Capacity; /* 堆的最大容量 */
};
```

```c
MaxHeap Create( int MaxSize )
{
    /* 创建容量为MaxSize的空的最大堆 */
    MaxHeap H = malloc( sizeof( struct HeapStruct ) );
    H->Elements = malloc( (MaxSize+1) * sizeof(ElementType) );
    H->Size = 0;
    H->Capacity = MaxSize;
    H->Elements[0] = MaxData;
    /* 定义“哨兵”为大于堆中所有可能元素的值，便于以后更快操作 */
    return H;
}
```

> 把 MaxData 换成小于堆中所有元素的 MinData，同样适用于创建最小堆。

## 最大堆的插入

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_214_0.png)

Case 1：new_item = 20，20 < 31 ✔

Case 2：new_item = 35，35 > 31，35 < 44 ✔

Case 3：new_item = 58，58 > 31，58 > 44，58 < MaxData ✔

### ❖ 算法：将新增加结点插入到从其父结点到根结点的有序序列中

```c
void insert( MaxHeap H, ElementType item )
{ /* 将元素item 插入最大堆，其中H->Elements[0]已经定义为哨兵 */
    int i;
    if ( IsFull(H) ) {
        printf("最大堆已满");
        return;
    }
    i = ++H->Size; /* i指向插入后堆中的最后一个元素的位置 */
    for ( ; H->Elements[i/2] < item; i/=2 )
        H->Elements[i] = H->Elements[i/2]; /* 向下过滤结点 */
    H->Elements[i] = item; /* 将item 插入 */
}
```

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_215_0.png)
