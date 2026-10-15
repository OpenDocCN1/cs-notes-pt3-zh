

## 练习：最小生成树

应用 Kruskal 算法求最小生成树：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_714_0.png)

+   1: HOB → SOU
+   5: LOR → RAU
+   10: BRE → HOB
+   10: EDO → LOR
+   10: EDO → RAU
+   10: MOR → RIV
+   15: EDO → MIN
+   15: MIN → RAU
+   20: BLA → CIR
+   20: BLA → RAU
+   30: BRE → RIV
+   30: CAR → LOR
+   30: CAR → RIV
+   30: CIR → MIN
+   40: CIR → MOU
+   40: LOR → MOR
+   50: EDO → ISE
+   50: ISE → SOU
+   70: BLA → MOU

## Kruskal 算法的应用

- 假设你有一个看起来像这样的图：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_715_0.png)

- 如果你以随机顺序选择弧应用 Kruskal 算法来寻找最小生成树，会发生什么？

- 该算法有一个很好的演示，网址为
[http://cs.stanford.edu/~eroberts/jtf/demos/assignments/MazeMaker.html](http://cs.stanford.edu/~eroberts/jtf/demos/assignments/MazeMaker.html)

## 示例

- 给定有向图 G 及图中的节点 D 、 F ，求出到D的最短路径不经过F的节点集合。

## 结束

## 无锁数据结构

Zhengwei QI

Shanghai Jiao Tong University

## 线程安全

线程安全：在多线程环境中被调用时，能够正确地处理各个线程的局部变量，使程序功能正确完成。

要将非线程安全的函数改为线程安全的，则只需要修改函数的实现部分。一般通过加入同步机制以保护共享的资源，使之不会被几个线程同时访问。

```
void strcpy(char *dest, char *src)
{
    while (*dest++ = *src++) {
        ;
    }
    *dest = NUL;
}
```

```
int Temp;

void swap(int *x, int *y)
{
    Temp = *x;
    *x = *y;
    *y = Temp;
}
```

## 低优先级任务

## 高优先级任务

```
while (1) {
  x = 1;
  y = 2;
  swap(&x, &y);
  {
    Temp = *x;
    *x = *y;
    *y = Temp;
  }
  :
  OSTimeDly(1);
}
```

```
while (1) {
  z = 3;
  t = 4;
  swap(&z, &t);
  {
    Temp = *z;
    *z = *t;
    *t = Temp;
  }
  .
  OSTimeDly(1);
  .
}
```

Temp == 1

Temp == 3!

Temp == 3

![](img/af430dff16b82a0fe61ce7dee05dcf9c_721_0.png)

+   1. 把Temp定义为局部变量
+   2. 调用Swap()函数之前关中断，调动后再开中断
+   3. 用信号量禁止该函数在使用过程中被再次调用

```
#include <pthread.h>

int increment_counter ()
{
    static int counter = 0;
    static pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;

    pthread_mutex_lock(&mutex);

    // only allow one thread to increment at a time
    ++counter;
    // store value before any other threads increment it further
    int result = counter;

    pthread_mutex_unlock(&mutex);

    return result;
}
```

## 改进

- c++11中的atomics，可使此函数即线程安全又可重入。

```
#include <atomic>

int increment_counter ()
{
    static std::atomic<int> counter(0);

    // increment is guaranteed to be done atomically
    int result = ++counter;

    return result;
}
```

## Atomics 内部原理

- CAS: Compare and Set primitive
- boolean cas( int * valueToChange, int valueToSet To, int ValueToCompareTo)
  ```
  if( *valueToChange ==
  valueToCompareTo) {
      *valueToChange = valueToSetTo;
      return true;
  }
  else {
      return false;
  }
  ```

## 构建无锁数据结构

- **构建这些无锁数据结构需要什么？**
- **将更改的范围限制为单个原子变量**
  - Stack : head
  - Queue: head or tail depending on enque or deque

## 一个简单的无锁示例

- 一个无锁的 Stack
- 采用自 CMU 的 **Geoff Langdale**
  - 旨在说明无锁数据结构的设计以及无锁同步的问题
  - 我们需要一个原语操作：
    - Compare and Set (CAS)
    - 可在大多数现代机器上使用
      - X86 assembly: xchg
      - PowerPC assembly: LL(load linked), SC (Store Conditional)

## 用 C 实现的无锁整数栈

- 一个基于单链表的栈。设计并不特别好！
- 现在有了节点，让我们继续栈的主体部分

```
struct NodeEle {
    int data;
    Node *next;
};

typedef NodeEle Node;

Node* head; // The head of the list
```
