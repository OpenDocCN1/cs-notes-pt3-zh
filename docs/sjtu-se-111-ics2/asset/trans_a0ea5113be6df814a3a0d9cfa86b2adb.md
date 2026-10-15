

## 线程安全的库函数

- 标准 C 库（在你的 K&R 书籍末尾）中的所有函数都是线程安全的。
- 大多数 Unix 系统调用都是线程安全的，但有少数例外：

| 线程不安全函数 | 类别 | 可重入版本 |
|---|---:|---|
| rand | 2 | rand_r |
| strtok | 2 | strtok_r |
| asctime | 3 | asctime_r |
| ctime | 3 | ctime_r |
| gethostbyaddr | 3 | gethostbyaddr_r |
| gethostbyname | 3 | gethostbyname_r |
| inet_ntoa | 3 | (none) |
| localtime | 3 | localtime_r |

## 问题：竞争

- *程序的正确性取决于*
  - 一个线程在其控制流中先到达点 x
  - 另一个线程到达点 y

```
/*thread routine */
void *thread(void *var_gp)
{
    int myid = *((int *)var_gp) ;
    printf("Hello from th. %d\n", myid);
    return NULL ;
}
```

```
#define N 4
int main()
{
    pthread_t tid[N];
    int i ;
    for ( i=0 ; i<N ; i++ )
        pthread_create(&tid[i], NULL, thread, &i);
    for ( i=0 ; i<N ; i++ )
        pthread_join(tid[i], NULL) ;
    exit(0) ;
}
```

```
int main()
{
    pthread_t tid[N];
    int i, *ptr ;
    for ( i=0 ; i<N ; i++ ) {
        ptr = malloc(sizeof(int));
        *ptr = i ;
        pthread_create(&tid[i], NULL, thread, ptr);
    }
    for ( i=0 ; i<N ; i++ )
        pthread_join(tid[i], NULL) ;
    exit(0) ;
}
```

## 问题：死锁

```c
int main()
{
    pthread_t tid[2];
    Sem_init(&mutex[0], 0, 1);  /* mutex[0] = 1 */
    Sem_init(&mutex[1], 0, 1);  /* mutex[1] = 1 */
    Pthread_create(&tid[0], NULL, count, (void*)0);
    Pthread_create(&tid[1], NULL, count, (void*)1);
    Pthread_join(tid[0], NULL);
    Pthread_join(tid[1], NULL);
    printf("cnt=%d\n", cnt);
    exit(0);
}
```

```
void *count(void *var_gp)
{
    int i;
    int id = (int) var_gp;
    for (i = 0; i < NITERS; i++) {
        P(&mutex[id]); P(&mutex[1-id]);
        cnt++;
        V(&mutex[id]); V(&mutex[1-id]);
    }
    return NULL;
}
```

Thread0
Tid[0]:
P(s₀);
P(s₁);
cnt++;
V(s₀);
V(s₁);

Thread1
Tid[1]:
P(s₁);
P(s₀);
cnt++;
V(s₁);
V(s₀);

加锁引入了死锁的可能性：等待一个永远不会为真的条件。

任何进入死锁区域的轨迹最终都会到达死锁状态，等待 s 或 t 变为非零。

其他轨迹则幸运地避开了死锁区域。

初始时，s=t=1

![](img/9bd5f6161cb6607b56d2fb964d1b8794_910_0.png)

## 线程总结

- 线程为编写并发程序提供了另一种机制
- 线程越来越受欢迎
  - 比进程成本稍低
  - 线程间共享数据很容易
- 然而，共享的便利性是有代价的：
  - 很容易引入微妙的同步错误
  - 使用线程时要谨慎！
- 了解更多信息：
  - D. Butenhof, "Programming with Posix Threads", Addison-Wesley, 1997

## 虚拟内存 (I)

## 大纲

- 物理寻址和虚拟寻址
- 地址空间
- VM 作为缓存的工具
- VM 作为内存管理的工具
- VM 作为内存保护的工具
- 建议阅读：9.1~9.5

## 物理寻址

- **主存储器的属性**
  - 组织为 M 个连续字节大小单元的数组
  - 每个字节都有唯一的 **物理地址** (PA)，从 0 开始
- **物理寻址**
  - CPU 使用物理地址访问内存
- **示例**
  - 早期 PC、DSP、嵌入式微控制器和 Cray 超级计算机

![](img/9bd5f6161cb6607b56d2fb964d1b8794_915_0.png)

- 用于“简单”系统，如汽车、电梯和数码相框中的嵌入式微控制器

## 虚拟寻址

- 虚拟寻址
  - CPU 通过 **虚拟地址** (VA) 访问主存储器
    - 虚拟地址会被转换为适当的物理地址

