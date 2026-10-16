
## C 指针的使用: 来做个自测吧!

```
int *p
```

p is a pointer to int（P是指针）

```
int *p[13]
```

p is an array[13] of pointer to int（p是指针数组）

```
int *(p[13])
```

p is an array[13] of pointer to int（p是指针数组）

```
int **p
```

p is a pointer to a pointer to an int（p是指针的指针）

```
int (*p)[13]
```

p is a pointer to an array[13] of int（p是数组指针）

```
int *f()
```

f is a function returning a pointer to int（指针函数，返回一个指针）

```
int (*f)()
```

f is a pointer to a function returning int（函数指针）

## 间接引用坏指针

- 经典的scanf错误

```
int val;
...
scanf("%d", val);//应当&val
```

从stdin读一个整数到一个变量val
正确方法：传递变量的地址给scanf

## 读未初始化的内存

- 常见的错误是假设堆内存被初始化为零

```
/* return y = Ax */
int *matvec(int **A, int *x) {
    int *y = malloc(N*sizeof(int));
    int i, j;

    for (i=0; i<N; i++)
        for (j=0; j<N; j++)
            y[i] += A[i][j]*x[j];
    return y;
}
```

## 覆盖内存

- 分配（可能）错误大小的对象

```
int **p;

p = malloc(N*sizeof(int));//int*

for (i=0; i<N; i++) {
    p[i] = malloc(M*sizeof(int));
}
```

假设指向对象的指针和它们所指向的对象是相同大小的（这里p是个指针数组）

## 覆盖内存

- Off-by-one error 错位错误

```
int **p;

p = malloc(N*sizeof(int *));

for (i=0; i<=N; i++) {
    p[i] = malloc(M*sizeof(int));
}
```

这里指针数组大小为N

## 覆盖内存

- 不检查输入串的大小

```
char s[8];
int i;

gets(s);  /* reads "123456789" from stdin */
//复制任意长度的串到缓冲区
```

- 经典缓冲区溢出攻击的基础

## 覆盖内存

- 误解指针运算

```
int *search(int *p, int val) {
    //扫描整型数组p
    while (*p && *p != val)
        p += sizeof(int);

    return p;
}
```

指针的算术操作是以它们指向的对象大小为单位
P++: p指向下一个int元素（p+4）
P+4: p指向下4个int元素_(p+4*4)

## 覆盖内存

- 引用指针而不是它所指向的对象

```
int *BinheapDelete(int **binheap, int *size) {
    int *packet;
    packet = binheap[0];
    binheap[0] = binheap[*size - 1];
    *size--;  // 应当是 (*size)--
    Heapify(binheap, *size, 0);
    return (packet);
}
```

## 引用不存在的变量

- 忘记当函数返回时局部变量将消失

```
int *foo () {
    int val;

    return &val;
}
```

栈帧释放后，val变量已不存在，对函数所返回指针的赋值（*p）将存在风险

## 多次释放

- Nasty!很讨厌

```
x = malloc(N*sizeof(int));
<manipulate x>
free(x);

y = malloc(M*sizeof(int));
<manipulate y>
free(x);
```

运行会报错！空指针可以多次释放

若释放后
x = NULL
free(x)成立

## 引用空闲堆块中的数据

- Evil!很邪恶

```
x = malloc(N*sizeof(int));
<manipulate x>
free(x);
...
y = malloc(M*sizeof(int));
for (i=0; i<M; i++)
    y[i] = x[i]++;//x[i]已被释放，可能已是其他已分配的堆块的部分
```

## 释放失败（内存泄漏）

- Slow, long-term killer!

```
foo() {
    int *x = malloc(N*sizeof(int));
    ...
    return;
}
```

## 释放失败（内存泄漏）

- 释放部分数据

```
struct list {
    int val;
    struct list *next;
};

foo() {
    struct list *head = malloc(sizeof(struct list));
    head->val = 0;
    head->next = NULL;
    <create and manipulate the rest of the list>
    ...
    free(head);
    return;
}
```

## 第9章 虚拟内存:基本概念

计算机科学与技术学院
哈尔滨工业大学

## 主要内容

- 地址空间
- 虚拟内存作为缓存的工具
- 虚拟内存作为内存管理的工具
- 虚拟内存作为内存保护的工具
- 地址翻译

## Why Virtual Memory (VM)?
为什么要使用虚拟内存？

- 有效使用主存
  - 主存作为一个存储在磁盘上的地址空间的缓存（虚存建立在磁盘上，可以很大）
  - 主存中只保存活动区域
- 简化内存管理（一致性）
  - 每个进程都使用统一的线性地址空间
- 独立地址空间（私有的）
  - 一个进程不能影响其他进程的内存
  - 用户程序无法获取特权内核信息和代码

## 一个使用物理寻址的系统

![](img/7ab811dea080313a753fa0ae68528fa9_1548_0.png)

- 在数字信号处理器、嵌入式微控制器中使用物理寻址

## 一个使用虚拟寻址的系统

- 现在处理器使用虚拟寻址,比如笔记本、智能电话等应用
- 计算机科学的伟大思想之一

## 地址空间

- **地址空间:** 非负整数地址的有序集合
  {0, 1, 2, 3 ...}
  如果地址空间中的整数是连续的，称为*线性地址空间*
- **虚拟地址空间:** N = 2ⁿ 个虚拟地址的集合
  {0, 1, 2, 3, ..., N-1}
- **物理地址空间:** M = 2ᵐ 个物理内存地址的集合
  {0, 1, 2, 3, ..., M-1}

## 主要内容

- 地址空间
- 虚拟内存作为缓存的工具
- 虚拟内存作为内存管理的工具
- 虚拟内存作为内存保护的工具
- 地址翻译

## 虚拟内存作为缓存的工具

- 概念上而言，虚拟内存被组织为一个由存放在磁盘上的 **N个连续字节大小的单元组成的数组**.
- 磁盘上数组的内容被缓存在 **物理内存中** (*DRAM cache*)
  - 这些内存块被称为页(每个页面的大小为P = 2^p字节)

![](img/7ab811dea080313a753fa0ae68528fa9_1552_0.png)

## Enabling Data Structure: Page Table 页表

- 页表是一个页表条目 (Page Table Entry, PTE)的数组，将虚拟页地址映射到物理页地址。
  - 虚拟地址空间中的每个页（VP）在页表固定位置有一个PTE
  - PTE由一个有效位和一个n位地址字段组成，有效位表示虚拟页是否被缓存物理内存
  - 有效位为0，空地址（地址为空）表示虚拟页还未分配

![](img/7ab811dea080313a753fa0ae68528fa9_1554_0.png)
