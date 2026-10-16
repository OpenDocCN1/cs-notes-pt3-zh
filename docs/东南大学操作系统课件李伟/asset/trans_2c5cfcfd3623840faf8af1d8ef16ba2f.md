

## 使用 TestAndSet 满足三个条件

初始 Boolean waiting[i] = false; lock=false

### 进入临界区

```
waiting[i] = true;
key = true;
while (waiting[i] && key)
    key = TestAndSet(lock);
waiting[i] = false;
```

如果删除该语句，会产生什么后果？

### 离开临界区

```
j = (i+1)%n;
while ((j != i) && !waiting[j])
    j = (j+1)%n;
if (j == i)
    lock = false;
else
    waiting[j] = false;
```

## 信号量

- 同步工具
- 信号量 S – 整数变量
- 只能通过两种标准的原子操作访问
  - *wait(S): P()*
    - `while S ≤ 0;`
    - `S--;`
  - *signal(S): V()*
    - `S++;`

### 两种类型的信号量

- **计数信号量** – 整数值可以在无限制的域中取值。
- **二进制信号量** – 整数值只能在 0 和 1 之间取值；也称为 **互斥锁**。
- 可以将计数信号量 *S* 实现为二进制信号量。

### n 个进程的临界区

- **共享数据：**
  - semaphore mutex; //initially *mutex* = 1
- **进程 P_i:**
  ```
  do {
      wait(mutex);
          critical section
      signal(mutex);
          remainder section
  } while (1);
  ```

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_389_0.png)

### 信号量作为通用同步工具

- 仅在 *P_i* 中执行 *A* 之后，才在 *P_j* 中执行 *B*
- 使用初始化为 0 的信号量 *flag*
- 代码：

```
Pᵢ                         Pⱼ
⋮                          ⋮
A                    wait(flag)

signal(flag)               B
```

### 信号量实现

- 上述经典信号量定义的缺点是需要 **忙等待**。 *(当一个进程在其临界区内时，任何试图进入其临界区的其他进程都必须在入口代码中不断循环)*
- 这种类型的信号量也称为 **自旋锁** 因为进程在等待锁时会自旋。
- 为了克服忙等待的需要，进程可以 **阻塞自身** 而不是进行忙等待。

- 将信号量定义为记录

  ```
  typedef struct {
    int value;
    struct process *L; // waiting queue
  } semaphore;
  ```

- 假设有两个简单操作：
  - block() 挂起调用它的进程。
  - wakeup(P) 恢复被阻塞进程 P 的执行。

### 实现

信号量操作现在定义为

```
wait(S):
    S.value--;
    if (S.value < 0) {
        add this process to S.L;
        block();
    }

signal(S):
    S.value++;
    if (S.value <= 0) {
        remove a process P from S.L;
        wakeup(P);
    }
```

- 如果信号量的值是负数，其绝对值就是等待该信号量的进程数。
- 信号量的关键方面是它们必须被 **原子地** 执行。 (*临界区问题*)
- 忙等待 **并未** 完全消除。
  - 忙等待已从应用程序的临界区入口部分移除。
  - 此外，我们已将忙等待限制在 `wait()` 和 `signal()` 操作的临界区内。

## 练习

- 5个进程共享某一临界资源，则互斥信号量的取值范围是多少？
- 有4个进程共享一程序段，而每次最多允许2个进程进入该程序段，则信号量的初值是多少？

## 死锁和饥饿

- **死锁 – 两个或多个进程** 无限期地等待 **一个事件**，该事件只能由等待进程中的一个引起。
- 设 S 和 Q 为两个初始化为 1 的信号量

```
P₀                         P₁
wait(S);                    wait(Q);
wait(Q);                    wait(S);
⋮                           ⋮
signal(S);                  signal(Q);
signal(Q);                  signal(S);
```

- **饥饿** – 无限期阻塞。 **一个进程** 可能永远不会从其被挂起的信号量队列中移除。

