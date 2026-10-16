

## 监视器的示意图

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_417_0.png)

## 条件变量

- 要允许进程在管程内等待，必须声明一个 **condition** 变量，如 **condition x, y;**
- 条件变量只能与操作 **wait** 和 **signal** 一起使用。
  - **x.wait()** 表示调用此操作的进程将被挂起，直到另一个进程调用 **x.signal();**
  - **x.signal()** 操作恢复恰好一个被挂起的进程。如果没有进程被挂起，则 **signal()** 操作无效。

## 带条件变量的管程

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_419_0.png)

### 条件信号

- 考虑被释放的进程和发出信号的进程
  - 有 **two** 个进程在管程中执行，互斥被违反了！
- 解决此问题的方法
  - 被释放的进程占用管程而发出信号的进程在某处等待。（唤醒并等待）
  - 被释放的进程在某处等待而发出信号的进程继续使用管程。（唤醒并继续）

## 信号量 vs. 条件

| Semaphores | Condition Variables |
|---|---|
| Can be used anywhere, but not in a monitor | Can only be used in monitors |
| `wait()` does not always block its caller | `wait()` **always** blocks its caller |
| `signal()` either releases a process, or increases the semaphore counter | `signal()` either releases a process, or the signal is **lost** as if it never occurs |
| If `signal()` releases a process, the caller and the released **both continue** | If `signal()` releases a process, either the caller or the released continues, but **not both** |

## Monitor vs. Process

- 管程定义的是公用数据结构，而进程定义的是私有数据结构
- 管程把共享变量上的同步操作集中起来，而临界区却分散在每个进程中
- 管程是为管理共享资源而建立的，进程主要是为占有系统资源和实现系统并发性而引入的
- 管程是被欲使用共享资源的进程所调用，管程和调用它的进程不能并发工作，而进程之间能并发工作
- 管程是语言或操作系统的成分，不必创建或撤销，而进程有生命周期，由创建而产生至撤销便消亡

## 哲学家进餐

```
void pickup(int i)
{
    state[i] = hungry;
    test[i];
    if (state[i] != eating)
        self[i].wait();
}
```

```
void putdown(int i)
{
    state[i] = thinking;
    // test left and right neighbors
    test((i+4) % 5);
    test((i+1) % 5);
}
```

### 哲学家进餐

```c
void test(int i)
{
    if ( (state[(i + 4) % 5] != eating) &&
         (state[i] == hungry) &&
         (state[(i + 1) % 5] != eating))
    {
        state[i] = eating;
        self[i].signal();
    }
}
```

## 哲学家进餐

- 每个哲学家 *i* 按以下顺序调用操作 **pickup()** 和 **putdown()**：
  - dp.pickup (i)
  - EAT
  - dp.putdown (i)

## 使用信号量实现的管程

- Variables

```
semaphore mutex; // (initially = 1)
semaphore next; // (initially = 0)
int next-count = 0;
```

- 每个外部过程 F 将被替换为

```
wait (mutex);
...
body of F;
...
if (next-count > 0)
  signal (next)
else signal (mutex);
```

- 管程内的互斥得到保证。

确保管程的互斥调用

管程内挂起进程的总数

防止执行 Signal操作后两个进程同时在管程中

## 管程实现

- 操作 x.signal 可以实现为

```
if (x-count > 0)
{
    next-count++;
    signal (x-sem);
    wait (next);
    next-count--;
}
```

## 管程实现

- **Conditional-wait** 构造：x.wait(c)
  - c – 在执行 wait 操作时求值的整数表达式。
  - c 的值（一个 *priority number*）与被挂起的进程的名称一起存储。
  - 当 x.signal() 执行时，关联优先级数字最小的进程将被接下来恢复。

## 管程实现

- 检查两个条件以建立  
  系统的  
  正确性
  - 用户进程必须始终以  
    正确的顺序在  
    管程上进行调用。
  - 必须确保不合作的进程不会忽略由  
    管程提供的互斥入口，  
    并尝试直接访问  
    共享资源，而不使用  
    访问协议。

