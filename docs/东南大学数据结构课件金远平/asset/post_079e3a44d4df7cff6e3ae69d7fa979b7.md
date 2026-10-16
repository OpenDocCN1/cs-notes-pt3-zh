
Note that when `currentNode == root`, `Next()` return the 1st node of inorder, thus we can use the following function to do an inorder traversal of a threaded binary tree:

```
template <class T>
void ThreadedTree<T>::Inorder()
{
    ThreadedInorderIterator ti;
    for (T* p = ti.Next(); p; p = ti.Next())
        Visit(*p);
}
```

Since each node is visited at most 2 times, the computing time is readily seen to be O(n) for n nodes tree, and the traversal has been done without using a stack.

## 5.5.3 Inserting a Node into a Threaded Binary Tree

Insertion into a threaded tree provides the function for growing threaded tree.

We shall study only the case of inserting r as the right child of s. The left child case is similar.

### (1) If s→rightThread==true, as:

![](img/15e8d7d94d8ddf02cb6839870195a31e_345_0.png)

### (2) If s→rightThread==false, as:

![](img/15e8d7d94d8ddf02cb6839870195a31e_346_0.png)

In both (1) and (2), actions ①,②,③ are the same, ④ is special for (2).

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

## Exercises: P277-1, P278-4

![](img/15e8d7d94d8ddf02cb6839870195a31e_353_0.png)

Fig. 5.24 Max heaps

Since max heap is a complete binary tree, we use array heap to represent it.

Thus we have the template **MaxHeap** class, which derives from MaxPQ<T>, as in the next slide:

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

## Analysis of Push:

A complete binary tree with n nodes has a height ⌈log₂(n+1)⌉, the while loop is iterated O(log n) times, each takes O(1) time, so the complexity is O(log n).

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

## Analysis of Pop:

The height of a heap with n nodes is ⌈log₂(n+1)⌉, the while loop is iterated O(log n) times, each takes O(1) time, so the complexity is O(log n).

## Exercises: P287-2, 3

## 5.7 Binary Search Trees

### 5.7.1 Definition

When arbitrary elements are to be searched or deleted, heap is not suitable.

A dictionary is a collection of pairs, each pair has a key and an associated element.

Although natural dictionaries may have several pairs with the same key, we assume here that no two pairs have the same key.

The specification of a dictionary is given as ADT 5.3.
