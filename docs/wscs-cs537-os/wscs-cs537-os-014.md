# 014：并发编程（读者-写者锁、死锁）🔒

![](img/19b27f59ecfbe3f6a774612de786eaf9_1.png)

在本节课中，我们将学习并发编程的最后几个核心概念。我们将深入探讨如何使用信号量实现**读者-写者锁**，并分析并发程序中常见的**原子性、顺序性和死锁**问题及其解决方案。课程内容将帮助你巩固对并发原语的理解，并为实际编程中的并发问题提供解决思路。

![](img/19b27f59ecfbe3f6a774612de786eaf9_3.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_5.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_6.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_7.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_8.png)

---

![](img/19b27f59ecfbe3f6a774612de786eaf9_10.png)

## 课程回顾与公告 📢

上一节我们介绍了信号量和条件变量的基本概念。本节中，我们来看看如何应用这些知识解决更复杂的问题。

![](img/19b27f59ecfbe3f6a774612de786eaf9_12.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_14.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_16.png)

首先是一些课程公告：
*   项目4已提交，整体进展顺利。
*   项目5现已发布。与最初计划相比，该项目已大幅简化，更直接明了。这是本学期全新的项目，将于下周一截止。
*   你可以选择新的项目伙伴。建议优先选择你熟悉且合作顺畅的人。
*   第二次期中考试即将到来，主要涵盖所有并发主题，并少量回顾虚拟化内容。
*   下次课程将花一些时间复习并发，然后开始进入下一个主题：I/O与持久化。

![](img/19b27f59ecfbe3f6a774612de786eaf9_18.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_20.png)

---

![](img/19b27f59ecfbe3f6a774612de786eaf9_21.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_22.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_23.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_24.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_25.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_27.png)

## 并发编程目标回顾 🔄

![](img/19b27f59ecfbe3f6a774612de786eaf9_29.png)

在并发编程中，我们通常追求两个核心属性：

![](img/19b27f59ecfbe3f6a774612de786eaf9_31.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_32.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_33.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_35.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_36.png)

1.  **互斥**：确保一次只有一个线程或进程进入临界区执行特定代码。这通常通过**锁**来实现。
    *   **公式/代码表示**：`lock_acquire(&mutex);` 和 `lock_release(&mutex);` 之间的代码区域即为临界区。

![](img/19b27f59ecfbe3f6a774612de786eaf9_38.png)

2.  **顺序**：确保代码B在代码A执行完毕后才运行。这可以通过**条件变量**或**信号量**来实现。
    *   **条件变量**：用于在某个条件满足时唤醒等待的线程。
    *   **信号量**：通过一个内部整数值来协调线程间的执行顺序。

![](img/19b27f59ecfbe3f6a774612de786eaf9_40.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_42.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_43.png)

---

![](img/19b27f59ecfbe3f6a774612de786eaf9_45.png)

## 条件变量与信号量的核心区别 ⚖️

上一节我们对比了条件变量和信号量。本节中，我们来明确它们的核心区别：

![](img/19b27f59ecfbe3f6a774612de786eaf9_47.png)

*   **条件变量**：本身不存储任何状态信息，仅作为一个等待队列。使用时必须与一个互斥锁关联。调用 `cond_wait()` 时必须持有该锁，此调用会释放锁并使线程进入睡眠，直到被 `cond_signal()` 唤醒。唤醒后，线程需要重新获取锁才能从 `wait` 返回。

![](img/19b27f59ecfbe3f6a774612de786eaf9_49.png)

*   **信号量**：内部维护一个整数值，该值决定了信号量的行为。
    *   用于**顺序控制**时，通常初始化为 `0`。调用 `sem_wait()` 的线程会等待，直到其他线程调用 `sem_post()` 将值增加到 `1` 或以上。
    *   用于**互斥**时，通常初始化为 `1`。这确保了只有一个线程能通过 `sem_wait()`，其行为类似于锁。

![](img/19b27f59ecfbe3f6a774612de786eaf9_51.png)

---

## 哲学家就餐问题与死锁 🍽️

为了理解死锁，我们回顾了经典的**哲学家就餐问题**。

![](img/19b27f59ecfbe3f6a774612de786eaf9_53.png)

**问题描述**：有N位哲学家围坐一桌，每人面前有一碗饭，每两人之间有一根筷子。哲学家需要同时拿到左右两边的筷子才能吃饭。

![](img/19b27f59ecfbe3f6a774612de786eaf9_55.png)

**初始实现**：每根筷子用一个初始值为 `1` 的信号量表示。哲学家先拿左边筷子，再拿右边筷子。

![](img/19b27f59ecfbe3f6a774612de786eaf9_57.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_59.png)

**问题**：当所有哲学家同时拿起左边的筷子时，每个人都会等待右边的筷子被放下，导致**死锁**——所有线程都持有部分资源并等待其他资源，系统无法推进。

![](img/19b27f59ecfbe3f6a774612de786eaf9_61.png)

**解决方案一：打破循环依赖**
让其中一位哲学家以相反的顺序获取筷子（先右后左）。这样就破坏了资源请求的循环等待条件，避免了死锁。

![](img/19b27f59ecfbe3f6a774612de786eaf9_63.png)

**解决方案二：安全与活性检测（更优方案）**
不直接为每根筷子加锁，而是引入一个中央协调机制。哲学家在“拿筷子”前，先在一个互斥锁保护下检查其左右邻居是否正在吃饭。只有邻居都不在吃饭时，他才被允许“吃饭”。这个方案通过一个额外的信号量来通知哲学家可以开始吃饭，实现了更高的并发度。

---

![](img/19b27f59ecfbe3f6a774612de786eaf9_65.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_67.png)

## 读者-写者锁 📖✍️

![](img/19b27f59ecfbe3f6a774612de786eaf9_69.png)

传统锁对所有线程一视同仁，但某些场景下，我们可以区分**读者**和**写者**，以提升并发性能。

![](img/19b27f59ecfbe3f6a774612de786eaf9_71.png)

**读者-写者锁规则**：
*   多个**读者**可以同时持有锁（因为他们不修改数据）。
*   一次只能有一个**写者**持有锁。
*   **写者**持有锁时，不能有任何**读者**持有锁。

![](img/19b27f59ecfbe3f6a774612de786eaf9_73.png)

实现读者-写者锁时，需要权衡**读者优先**还是**写者优先**。

![](img/19b27f59ecfbe3f6a774612de786eaf9_75.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_76.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_78.png)

### 读者优先的实现

![](img/19b27f59ecfbe3f6a774612de786eaf9_80.png)

以下是使用信号量实现读者优先锁的核心逻辑：

```c
// 全局变量
sem_t lock;      // 保护读者计数的互斥信号量，初始化为1
sem_t writelock; // 写锁，初始化为1
int readers = 0; // 当前读者数量

![](img/19b27f59ecfbe3f6a774612de786eaf9_82.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_84.png)

void acquire_readlock() {
    sem_wait(&lock);
    readers++;
    if (readers == 1) { // 第一个读者需要获取写锁
        sem_wait(&writelock);
    }
    sem_post(&lock);
}

![](img/19b27f59ecfbe3f6a774612de786eaf9_86.png)

void release_readlock() {
    sem_wait(&lock);
    readers--;
    if (readers == 0) { // 最后一个读者释放写锁
        sem_post(&writelock);
    }
    sem_post(&lock);
}

![](img/19b27f59ecfbe3f6a774612de786eaf9_88.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_89.png)

void acquire_writelock() {
    sem_wait(&writelock); // 写者直接竞争写锁
}

void release_writelock() {
    sem_post(&writelock);
}
```

![](img/19b27f59ecfbe3f6a774612de786eaf9_91.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_92.png)

**工作流程**：
1.  第一个读者会获取 `writelock`，阻止写者。
2.  后续读者只需增加计数，可并发进入。
3.  写者必须等待 `writelock`。
4.  最后一个读者离开时释放 `writelock`，唤醒等待的写者。

**潜在问题**：如果读者持续到达，写者可能被**饿死**。

![](img/19b27f59ecfbe3f6a774612de786eaf9_94.png)

### 写者优先的实现

![](img/19b27f59ecfbe3f6a774612de786eaf9_96.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_98.png)

写者优先的实现更为复杂，它确保一旦有写者在等待，新到达的读者必须等待，直到所有等待的写者完成。

其核心思想是使用多个信号量（如 `okToRead`, `okToWrite`，初始化为0）和状态变量（`activeReaders`, `waitingWriters`等），在一个互斥锁保护下检查状态，并只在条件满足时对相应信号量调用 `sem_post()` 来唤醒等待的线程。释放锁时，会优先检查是否有等待的写者并唤醒他们。

**两种策略的对比**：
*   **读者优先**：可能饿死写者。
*   **写者优先**：可能饿死读者。
*   没有完美的策略，需根据具体应用场景（读多写少还是写多读少）进行选择。

---

## 现实中的并发BUG 🐛

![](img/19b27f59ecfbe3f6a774612de786eaf9_100.png)

编写正确的并发程序非常困难，现实中的大型软件（如MySQL、Apache）也存在并发漏洞。主要分为三类：

![](img/19b27f59ecfbe3f6a774612de786eaf9_102.png)

1.  **原子性违规**：本应原子执行的操作被打断。
2.  **顺序违规**：代码执行顺序不符合预期。
3.  **死锁**：多个线程相互等待对方持有的资源。

![](img/19b27f59ecfbe3f6a774612de786eaf9_104.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_106.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_107.png)

### 原子性违规示例与修复

![](img/19b27f59ecfbe3f6a774612de786eaf9_109.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_110.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_111.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_112.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_113.png)

**问题代码（MySQL中的一个真实Bug）**：
```c
// 线程1
if (thd->proc_info) {
    ... // 使用 thd->proc_info
}

![](img/19b27f59ecfbe3f6a774612de786eaf9_115.png)

// 线程2
thd->proc_info = NULL;
```
**问题**：线程1检查 `proc_info` 非空后，线程2将其置为 `NULL`，接着线程1继续使用它，导致空指针解引用。

![](img/19b27f59ecfbe3f6a774612de786eaf9_117.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_118.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_120.png)

**修复**：使用**同一个锁**保护检查和使用该指针的代码区域，确保其原子性。

### 顺序违规示例与修复

![](img/19b27f59ecfbe3f6a774612de786eaf9_122.png)

**问题代码**：
```c
// 线程1 (父线程)
void *mThread;
pthread_create(&mThread, NULL, worker, NULL);

![](img/19b27f59ecfbe3f6a774612de786eaf9_124.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_126.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_128.png)

// 线程2 (子线程)
void *worker(void *arg) {
    pthread_t myTid = mThread; // 可能读到未初始化的 mThread!
    ...
}
```
**问题**：`pthread_create` 返回并设置 `mThread` 之前，新创建的线程可能已经开始执行并读取 `mThread`。

![](img/19b27f59ecfbe3f6a774612de786eaf9_130.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_132.png)

**修复**：使用**条件变量**确保顺序。父线程在设置 `mThread` 后发出信号，子线程在读取前等待该信号。

### 死锁示例与修复

![](img/19b27f59ecfbe3f6a774612de786eaf9_134.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_136.png)

**死锁的四个必要条件**：
1.  **互斥**：资源不能共享。
2.  **持有并等待**：线程持有资源的同时等待其他资源。
3.  **不可抢占**：资源不能被强制剥夺。
4.  **循环等待**：存在一个线程资源的环形等待链。

![](img/19b27f59ecfbe3f6a774612de786eaf9_138.png)

**简单死锁示例**：
```c
// 线程1
lock(L1);
lock(L2);
...
// 线程2
lock(L2);
lock(L1);
...
```
**修复**：定义全局的**锁获取顺序**（例如，总是按内存地址从低到高获取），并遵循该顺序。

![](img/19b27f59ecfbe3f6a774612de786eaf9_140.png)

**隐蔽的死锁示例（库函数）**：
```c
void set_intersection(Set* s1, Set* s2) {
    lock(s1->lock);
    lock(s2->lock);
    // 计算交集...
    unlock(s2->lock);
    unlock(s1->lock);
}
```
**问题**：如果线程A调用 `set_intersection(A, B)`，同时线程B调用 `set_intersection(B, A)`，就可能形成 `A等B锁，B等A锁` 的死锁。

![](img/19b27f59ecfbe3f6a774612de786eaf9_142.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_143.png)

**修复**：同样，为所有 `Set` 的锁定义一个全局获取顺序（例如，比较锁对象的地址），并确保函数总是按此顺序加锁。

![](img/19b27f59ecfbe3f6a774612de786eaf9_145.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_147.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_149.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_151.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_153.png)

---

## 无锁编程：避免死锁的另一条路径 🛡️

![](img/19b27f59ecfbe3f6a774612de786eaf9_155.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_156.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_158.png)

消除“互斥”条件可以避免死锁。**无锁编程**利用硬件提供的原子原语（如 `Compare-and-Swap`, CAS）来构建并发操作，而无需使用传统的锁。

![](img/19b27f59ecfbe3f6a774612de786eaf9_160.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_162.png)

**CAS操作伪代码**：
```c
int CompareAndSwap(int *ptr, int expected, int new) {
    int actual = *ptr;
    if (actual == expected) {
        *ptr = new;
    }
    return actual; // 通常返回旧值，或一个表示是否交换成功的布尔值
}
```

![](img/19b27f59ecfbe3f6a774612de786eaf9_164.png)

**使用CAS实现原子加法**：
```c
void AtomicIncrement(int *value, int amount) {
    do {
        int old = *value;
        int new = old + amount;
    } while (CompareAndSwap(value, old, new) != old); // 如果value被其他线程修改，则重试
}
```
**优点**：避免了死锁。
**缺点**：可能出现**活锁**——线程不断重试却总失败。解决方案通常是引入**指数退避**等策略，在重试前等待一段时间。

![](img/19b27f59ecfbe3f6a774612de786eaf9_166.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_168.png)

无锁算法也被用于实现复杂数据结构，如无锁链表插入，这将在下次课程中详细讨论。

![](img/19b27f59ecfbe3f6a774612de786eaf9_170.png)

---

![](img/19b27f59ecfbe3f6a774612de786eaf9_172.png)

## 总结 📚

![](img/19b27f59ecfbe3f6a774612de786eaf9_174.png)

本节课中我们一起学习了：
1.  **读者-写者锁**的原理与两种优先策略的实现，理解了在并发控制中权衡读者与写者权限的重要性。
2.  现实并发程序中常见的**三类BUG**：原子性违规、顺序违规和死锁，并掌握了使用锁、条件变量和规定锁顺序等方法来修复它们。
3.  **无锁编程**的基本思想，通过硬件原子指令（如CAS）来避免使用锁，从而从根本上防止死锁，同时也认识了其可能带来的活锁挑战。

![](img/19b27f59ecfbe3f6a774612de786eaf9_176.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_178.png)

并发编程是复杂但强大的工具。理解这些核心概念和模式，是构建正确、高效并发系统的关键。下次课程我们将完成无锁链表的讨论，并开始为期中考试进行复习。