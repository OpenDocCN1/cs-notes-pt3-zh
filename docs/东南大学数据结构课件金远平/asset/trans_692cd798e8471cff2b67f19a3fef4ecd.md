

请注意当 `currentNode == root` 时，`Next()` 返回中序遍历的第 1 个节点，因此我们可以使用以下函数对线索二叉树进行中序遍历：

```
template <class T>
void ThreadedTree<T>::Inorder()
{
    ThreadedInorderIterator ti;
    for (T* p = ti.Next(); p; p = ti.Next())
        Visit(*p);
}
```

由于每个节点最多被访问 2 次，计算时间很容易看出对于 n 个节点的树为 O(n)，并且遍历是在不使用栈的情况下完成的。

## 5.5.3 向线索二叉树中插入节点

向线索树中插入提供生长线索树的功能。

我们仅研究将 r 插入为 s 的右孩子的情况。左孩子的情况类似。

### (1) 若 s→rightThread==true，如：

![](img/15e8d7d94d8ddf02cb6839870195a31e_345_0.png)

### (2) 若 s→rightThread==false，如：

![](img/15e8d7d94d8ddf02cb6839870195a31e_346_0.png)

在 (1) 和 (2) 两种情况下，操作 ①、②、③ 相同，④ 仅用于 (2)。

```
```cpp
template <class T>
void ThreadedTree<T>::InsertRight(ThreadedNode<T>* s,
                                  ThreadedNode<T>* r)
{ // insert r as the right child of s
    r→rightChild=s→rightChild;        // ①
    r→rightThread=s→rightThread;      // ① note s!=t.root,
    r→leftChild=s;                    // ②
    r→leftThread=true;                // ②
    s→rightChild=r;                   // ③
    s→rightThread=false;              // ③
    if (! r→rightThread) {    // case (2)
        ThreadedNode<T>* temp=InorderSucc(r); // ④
        temp→leftChild=r;                      // ④
    }
}
```
```

## 练习：P277-1, P278-4

![](img/15e8d7d94d8ddf02cb6839870195a31e_353_0.png)

图 5.24 最大堆

由于最大堆是完全二叉树，我们使用数组 heap 来表示它。

因此我们有模板 **MaxHeap** 类，它派生自 MaxPQ<T>，如下一页所示：

```
template <class T>
MaxHeap<T>::MaxHeap (int theCapacity=10)
{ //constructor
    if (theCapacity < 1) throw "Capacity must be >= 1";
    capacity = theCapacity;
    heapSize = 0;
    heap = new T[capacity+1]; //heap[0] not used
}
```

```
template <class T>
Inline T& MaxHeap<T>::Top()
{
    if (IsEmpty()) throw "The heap is empty";
    return heap[1];
}
```

## Push 的分析：

具有 n 个节点的完全二叉树的高度为 ⌈log₂(n+1)⌉，while 循环迭代 O(log n) 次，每次花费 O(1) 时间，因此复杂度为 O(log n)。

```
template <class T>
void MaxHeap<T>::Pop()
{ // delete the max element.
    if (IsEmpty()) throw "Heap is empty. Cannot delete.";
    heap[1].~T(); // delete the max

    // remove the last element from heap
    T lastE = heap[heapSize--];

    // trickle down
    int currentNode = 1; // root
    int child = 2;   // left child of currentNode
```

```
```java
while (child <= heapSize)
{
    // set child to the larger child of currentNode
    if (child<heapSize && heap[child]<heap[child+1]) child++;

    // can we put lastE in currentNode?
    if (lastE>=heap[child]) break; // yes

    // no
    heap[currentNode]=heap[child]; // move child up
    currentNode=child; child *=2; // move down a level
}
heap[currentNode]=lastE;
```
```

## Pop 的分析：

具有 n 个节点的堆的高度为 ⌈log₂(n+1)⌉，while 循环迭代 O(log n) 次，每次花费 O(1) 时间，因此复杂度为 O(log n)。

## 练习：P287-2, 3

## 5.7 二叉搜索树

### 5.7.1 定义

当需要搜索或删除任意元素时，堆是不合适的。

字典是一组对，每对有一个键和一个相关联的元素。

尽管自然字典可能有多个具有相同键的对，但我们在此假设没有两个对具有相同的键。

字典的规范如 ADT 5.3 所示。

