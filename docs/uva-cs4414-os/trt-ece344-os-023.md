# 023：加锁

![](img/0fe976fa7e86e2b43352fbbd3c36c612_1.png)

在本节课中，我们将要学习操作系统中的高级加锁概念，包括监视器、条件变量以及如何避免死锁。这些知识对于理解和编写多线程程序至关重要。

---

## 监视器：编程语言中的简化锁

上一节我们介绍了基本的互斥锁，本节中我们来看看编程语言如何简化锁的使用。

一些面向对象语言内置了名为“监视器”的概念。开发者认为直接使用互斥锁较为困难，因此希望有更简单的方法。其规则是：如果一个对象的方法被标记为“受监视的”，那么在该对象的**所有**受监视方法中，**同一时间只能有一个线程是活跃的**。

这本质上意味着每个对象实例会拥有一个互斥锁，编译器会自动在受监视方法的开始和结尾插入加锁和解锁调用。

在Java中，`synchronized`关键字就实现了这一功能。例如，我们有一个银行账户类：

```java
class BankAccount {
    private int balance;
    public synchronized void deposit(int amount) {
        balance += amount;
    }
    public synchronized void withdraw(int amount) {
        balance -= amount;
    }
}
```

编译器会在底层为`BankAccount`的每个实例创建一个互斥锁字段，并为每个`synchronized`方法在开头添加`lock()`，在结尾添加`unlock()`。这样，所有`synchronized`方法同一时间只能有一个线程执行，从而避免了数据竞争。

这是一种更简单的加锁方式。在下一讲中，我们将为实验五做准备，运行一个多线程银行系统，并探讨如何使其高效运行。

---

## 条件变量：更通用的同步原语

在深入银行系统之前，我们先介绍另一个同步原语：条件变量。

条件变量的行为与信号量类似，但更通用，用于控制执行顺序。它允许你更轻松地表达复杂的等待条件，而信号量本质上只是一个整数，遵循简单的增减和等待规则。

条件变量可以被看作是一个队列（Q），你管理这个队列，线程在其中等待某个条件变为真。

Pthreads库中，条件变量的类型是`pthread_cond_t`。它有以下基本操作：
*   `pthread_cond_init`: 初始化。
*   `pthread_cond_destroy`: 销毁。
*   `pthread_cond_wait`: 等待条件。
*   `pthread_cond_signal`: 唤醒队列中的一个线程。
*   `pthread_cond_broadcast`: 唤醒队列中的所有线程。

`pthread_cond_wait`函数至关重要。调用它时，**必须已经持有一个互斥锁**。它的工作流程如下：
1.  将当前线程原子性地添加到该条件变量的等待队列中。
2.  解锁传入的互斥锁。
3.  使当前线程进入阻塞（睡眠）状态。

当其他线程调用`signal`或`broadcast`唤醒此线程后：
1.  线程被标记为可运行。
2.  在从`wait`函数返回**之前**，它会尝试重新获取（锁定）之前传入的互斥锁。
3.  当`wait`返回时，线程再次持有了该互斥锁。

![](img/0fe976fa7e86e2b43352fbbd3c36c612_3.png)

一个互斥锁可以保护多个条件变量。我们主要关注`wait`和`signal`调用。

---

### 生产者-消费者示例：条件变量版

以下是如何使用条件变量重写生产者-消费者问题。

我们需要跟踪缓冲区中已填充槽位的数量（`filled`）。我们创建两个条件变量：
*   `cond_empty`: 生产者等待有空槽位。
*   `cond_filled`: 消费者等待有已填充的槽位。

```c
pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;
pthread_cond_t cond_empty = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond_filled = PTHREAD_COND_INITIALIZER;
int filled = 0;
const int N = BUFFER_SIZE;

// 生产者线程
void producer() {
    pthread_mutex_lock(&mutex);
    while (filled == N) { // 缓冲区已满
        pthread_cond_wait(&cond_empty, &mutex); // 等待空槽位
    }
    // 生产物品，放入缓冲区
    filled++;
    pthread_cond_signal(&cond_filled); // 通知消费者有物品了
    pthread_mutex_unlock(&mutex);
}

// 消费者线程
void consumer() {
    pthread_mutex_lock(&mutex);
    while (filled == 0) { // 缓冲区为空
        pthread_cond_wait(&cond_filled, &mutex); // 等待有物品
    }
    // 从缓冲区取出物品消费
    filled--;
    pthread_cond_signal(&cond_empty); // 通知生产者有空位了
    pthread_mutex_unlock(&mutex);
}
```

与使用两个信号量的版本相比，条件变量版本使用一个共享变量`filled`和两个队列来管理等待，对于复杂条件可能更清晰。

经验法则是：如果条件仅依赖于一个简单的整数计数器，使用信号量；如果条件更复杂，则使用条件变量。

---

## 条件变量的使用陷阱与“虚假唤醒”

使用条件变量时有一些需要注意的细节。

考虑以下代码，线程1等待一个布尔条件为真后才执行关键代码，线程2负责将条件设为真。

```c
bool condition = false;
pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;
pthread_cond_t cond = PTHREAD_COND_INITIALIZER;

// 线程1
pthread_mutex_lock(&mutex);
if (condition == false) { // 注意：这里用的是 if
    pthread_cond_wait(&cond, &mutex);
}
// 关键代码：此处要求 condition 必须为 true
pthread_mutex_unlock(&mutex);

// 线程2
pthread_mutex_lock(&mutex);
condition = true;
pthread_cond_signal(&cond);
pthread_mutex_unlock(&mutex);
```

上述代码存在严重问题。假设执行序列如下：
1.  线程1加锁，检查`condition`为false，进入`wait`。在`wait`中，它被放入队列并释放锁。
2.  线程2加锁，将`condition`设为true，调用`signal`（但此时队列中线程1尚未完全入队？实际上，`wait`的“原子性”保证了入队和释锁是原子的，但这里假设一种极端情况）。假设`signal`时队列为空，无事发生。线程2解锁。
3.  线程1从`wait`中继续执行（它之前已入队），被唤醒，重新加锁，然后**直接跳过`if`判断**，执行关键代码。然而，此时`condition`可能已经被其他线程（比如新增的线程3）改回了false！

这就导致了“虚假唤醒”：线程被唤醒了，但等待的条件并未成立。**因此，必须使用`while`循环来重新检查条件，而不是`if`。**

```c
// 正确的写法：使用 while
pthread_mutex_lock(&mutex);
while (condition == false) { // 总是用 while！
    pthread_cond_wait(&cond, &mutex);
}
// 关键代码
pthread_mutex_unlock(&mutex);
```

`while`循环确保了即使线程被意外唤醒（某些系统允许），或者在唤醒后、重新获得锁之前条件又被其他线程改变，它也会再次检查条件并可能重新进入等待。**这是一个必须遵守的规则。**

---

## 锁的粒度与性能考量

接下来我们讨论锁的使用策略。锁的粒度是指锁保护代码范围的大小。在锁之间的代码实际上是串行执行的。

我们需要用锁来防止数据竞争，但最粗暴的方式是用一个大锁保护所有东西，这会导致性能低下。因此，需要在正确性和性能之间取得平衡。

![](img/0fe976fa7e86e2b43352fbbd3c36c612_5.png)

例如，要并行化一个哈希表（这将是实验五的内容）：
*   **粗粒度锁**：用一个锁保护整个哈希表。简单，但并发性差。
*   **细粒度锁**：为每个桶（bucket）或链表配备一个锁。并发性高，但锁的数量增多，管理复杂，且锁操作本身有开销。

需要考虑的因素包括：
1.  **锁开销**：创建、销毁、加锁、解锁操作都需要时间和内存。锁数量过多会影响性能。
2.  **争用**：多个线程试图获取同一个锁的可能性。争用越高，串行化越严重，性能越差。
3.  **死锁**：这是最需要避免的问题，尤其在拥有多个锁时。

---

## 死锁及其预防

死锁是指一组线程彼此等待对方持有的资源，导致所有线程都无法继续执行的状态。

产生死锁需要同时满足四个必要条件：
1.  **互斥**：资源一次只能被一个线程持有。
2.  **持有并等待**：线程持有一个资源，同时等待获取另一个资源。
3.  **不可抢占**：资源不能被强制从持有线程中夺走。
4.  **循环等待**：存在一个线程资源的环形等待链（T1等T2的资源，T2等T1的资源）。

要预防死锁，只需破坏其中至少一个条件。本课程中，我们主要关注破坏条件2或条件4。

**示例死锁**：
```c
// 线程1
lock(L1);
lock(L2);
// ...
unlock(L2);
unlock(L1);

// 线程2
lock(L2); // 与线程1顺序相反！
lock(L1);
// ...
unlock(L1);
unlock(L2);
```
如果线程1持有L1，线程2持有L2，双方接下来都会因请求对方持有的锁而永久阻塞。

### 预防方法一：锁排序（破坏循环等待）
定义锁的全局获取顺序（例如，按内存地址排序），所有线程都必须按此顺序获取锁。
```c
// 正确的顺序：总是先锁 L1，再锁 L2
// 线程1
lock(L1); lock(L2); ... unlock(L2); unlock(L1);
// 线程2
lock(L1); lock(L2); ... unlock(L2); unlock(L1); // 顺序一致
```
这样就不可能形成循环等待。

### 预防方法二：尝试锁与回退（破坏持有并等待）
使用`pthread_mutex_trylock`进行非阻塞尝试。如果无法立即获得所有需要的锁，就释放已持有的锁，稍后再试。
```c
while (1) {
    lock(L1);
    if (trylock(L2) == 0) { // 成功获取 L2
        break; // 进入临界区
    } else { // 获取 L2 失败
        unlock(L1); // 释放 L1，破坏“持有并等待”
        // 可以 yield() 或短暂睡眠，让其他线程运行
        sched_yield();
    }
}
// 临界区代码
unlock(L2);
unlock(L1);
```
这种方法避免了线程在持有一个锁的同时无限等待另一个锁，从而破坏了死锁条件。

---

## 总结

本节课中我们一起学习了操作系统中的高级加锁机制。

我们首先了解了**监视器**，它是编程语言层面提供的简化锁机制，能自动管理互斥锁。接着，我们深入探讨了**条件变量**，它是一种更通用的同步原语，通过等待队列管理线程，用于实现复杂的等待条件。**必须记住，使用条件变量时，判断条件应使用`while`循环而非`if`语句，以防止虚假唤醒。**

然后，我们讨论了**锁的粒度**对程序性能的影响，需要在安全性和并发度之间做出权衡。最后，我们重点分析了**死锁**的成因及其四个必要条件，并学习了两种预防策略：通过**全局锁排序**来破坏循环等待，以及使用**尝试锁和回退**策略来破坏持有并等待条件。

![](img/0fe976fa7e86e2b43352fbbd3c36c612_7.png)

掌握这些概念对于编写正确、高效的多线程程序至关重要。在接下来的实验五中，你将有机会实践这些知识，并行化一个哈希表。