
# 使用信号量实现同步

- Dijkstra 对信号量的 P 和 V 操作
  - 信号量：非负整数同步变量。
  - P(s)：[ while (s == 0) wait(); s--; ]
    - 荷兰语 "Proberen"（测试）
  - V(s)：[ s++; ]
    - 荷兰语 "Verhogen"（增加）

- Dijkstra 对信号量的 P 和 V 操作
  - 操作系统保证括号 [ ] 之间的操作是不可分割地执行的。
    - 一次只能有一个 P 或 V 操作修改 s。
    - 当 P 中的 while 循环终止时，只有该 P 操作可以递减 s。
  - 信号量不变量：(s >= 0)

# POSIX 信号量

```
#include <semaphore.h>

int sem_init(sem_t *sem, 0, unsigned int value);
int sem_wait(sem_t *s);  /* P(s) */
int sem_post(sem_t *s);  /* V(s) */

#include "csapp.h"

void P(sem_t *s); /* Wrapper function for sem_wait */
void V(sem_t *s); /* Wrapper function for sem_wait */
```

# 使用 POSIX 信号量实现共享

```
#include "csapp.h"
#define NITERS 10000000
unsigned int cnt; /* counter */
sem_t sem;          /* semaphore */

int main() {
    pthread_t tid1, tid2;
    Sem_init(&sem, 0, 1);
    /* create 2 threads and wait */
    ...
    if (cnt != (unsigned)NITERS*2)
        printf("BOOM! cnt=%d\n", cnt);
    else
        printf("OK cnt=%d\n", cnt);
    exit(0);
}
```

```
/* thread routine */
void *count(void *arg)
{
    int i;

    for (i=0; i<NITERS; i++) {
        P(&sem);
        cnt++;
        V(&sem);
    }
    return NULL;
}
```

# 使用信号量实现安全共享

通过对共享变量周围的临界区使用信号量 s（初始设置为 1）的 P 和 V 操作，提供对共享变量的互斥访问。

信号量不变量创建了一个禁止区域，该区域包围了不安全区域，并且任何轨迹都不会触及它。

初始时
s = 1

![](img/9bd5f6161cb6607b56d2fb964d1b8794_870_0.png)

# 并发编程

# 大纲

- 主题：
  - 生产者-消费者问题
  - 读者-写者问题
  - 基于 Pthreading 的并发服务器
  - 并发问题
- 建议阅读：
  - 12.5~12.7

# 互斥锁

```
/* thread routine */
void *count(void *arg)
{
    int i;

    for (i=0; i<NITERS; i++) {
        P(&sem);
        cnt++;
        V(&sem);
    }
    return NULL;
}
```

# 使用信号量调度对共享资源的访问

- _基本思想_：线程使用信号量操作通知另一个线程某个条件已变为真
  - 使用计数信号量来跟踪资源状态。
  - 使用二进制信号量来通知其他线程。
- 两个经典示例：
  - 生产者-消费者问题
  - 读者-写者问题

# 使用信号量进行信号通知

![](img/9bd5f6161cb6607b56d2fb964d1b8794_875_0.png)

- 常见同步模式：
  - 生产者等待空槽位，将项目插入缓冲区，并通知消费者
  - 消费者等待项目，从缓冲区移除项目，并通知生产者

# 单元素缓冲区上的生产者-消费者问题

```
int main() {
    pthread_t tid_producer;
    pthread_t tid_consumer;

    /* Initialize the semaphores */
    Sem_init(&shared.empty, 0, 1);
    Sem_init(&shared.full, 0, 0);
    /* Create threads and wait */
    Pthread_create(&tid_producer, NULL, producer, NULL);
    Pthread_create(&tid_consumer, NULL, consumer, NULL);
    Pthread_join(tid_producer, NULL);
    Pthread_join(tid_consumer, NULL);

    exit(0);
}
```

```
#define NITERS 5

struct {
    int buf;
    sem_t full;
    sem_t empty;
} shared;
```

初始时：empty==1, full==0

## 生产者线程

```
void *producer(void *arg) {
    int i, item;

    for (i=0; i<NITERS; i++) {
        /* Produce item */
        item = i;
        printf("produced %d\n", item);

        /* Write item to buf */
        P(&shared.empty);
        shared.buf = item;
        V(&shared.full);
    }
    return NULL;
}
```

## 消费者线程

```
void *consumer(void *arg) {
    int i, item;

    for (i=0; i<NITERS; i++) {
        /* Read item from buf */
        P(&shared.full);
        item = shared.buf;
        V(&shared.empty);

        /* Consume item */
        printf("consumed %d\n", item);
    }
    return NULL;
}
```

