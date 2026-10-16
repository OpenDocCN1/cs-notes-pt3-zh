
## 第2章 线性表

### 2.2 线性表的存储结构——一元多项式

```c
p = p->link;
break;
case '<':
    d = Attch(q->coef, q->exp, d);
    q = q->link;
    break;
}
while (p != NULL)
{
    d = Attch(p->coef, p->exp, d);
    p = p->link;
}
while (q != NULL)
{
    d = Attch(q->coef, q->exp, d);
    q = q->link;
}
```

### 2.3 特殊的线性表——栈

- **栈：**限定仅在表尾进行插入和删除操作的线性表。
- **空栈：**不含任何数据元素的栈。
- **栈顶和栈底：**允许插入（入栈、进栈、压栈）和删除（出栈、弹栈）的一端称为栈顶，另一端称为栈底。

**栈的示意图**

![](img/ad2aee679abbcf477936d4ee2701e2d3_105_0.png)

**栈的操作**

- 1. `MakeNull(S)`
- 2. `Top(S)`
- 3. `Pop(S)`
- 4. `Push(x, S)`
- 5. `Empty(S)`

**栈的特性：**后进先出

#### 2.3.1 栈的数组实现——顺序栈

栈的顺序存储结构及实现

如何改造数组实现栈的顺序存储？

![](img/ad2aee679abbcf477936d4ee2701e2d3_106_0.png)

确定用数组的哪一端表示栈底。

附设指针 top 指示栈顶元素在数组中的位置。

- 进栈：top 加1
- 栈空：top = -1
- 出栈：top 减1
- 栈满：top = MAX_SIZE

![](img/ad2aee679abbcf477936d4ee2701e2d3_107_0.png)

**栈的顺序存储结构定义**

```c
typedef struct {
    ElemType elements[max];
    int top;
} STACK;

STACK S;
```

- 栈的容量：max - 1；
- 栈顶指针：S.top
- 栈顶元素：S.elements[S.top]；
- 栈空：S.top = -1；
- 栈满：S.top = max - 1；

![](img/ad2aee679abbcf477936d4ee2701e2d3_108_0.png)

**栈的操作的实现**

**① void MakeNull(STACK &S)**

```c
void MakeNull(STACK &S)
{
    S.top = -1;
}
```

**② Boolean Empty(STACK S)**

```c
Boolean Empty(STACK S)
{
    if (S.top < 0)
        return TRUE;
    else
        return FALSE;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_109_0.png)

**③ ElemType Top(STACK S)**

```c
ElemType Top(STACK S)
{
    if (Empty(S))
        return NULL;
    else
        return (S.elements[S.top]);
}
```

**④ void Pop(STACK &S)**

```c
void Pop(STACK &S)
{
    if (Empty(S))
        cout << "栈空";
    else
        S.top = S.top - 1;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_110_0.png)

top

max-1

**⑤ void Push(ElemType x, STACK &S)**

```c
void Push(ElemType x, STACK &S)
{
    if (S.top == max - 1)
        cout << "栈满";
    else
    {
        S.top = S.top + 1;
        S.elements[S.top] = x;
    }
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_111_0.png)

#### 2.3.2 栈的指针实现——链栈

栈的链接存储结构及实现

- 链栈：栈的链接存储结构

如何改造链表实现栈的链接存储？

![](img/ad2aee679abbcf477936d4ee2701e2d3_112_0.png)

将哪一端作为栈顶？将链表首端作为栈顶，方便操作。

链栈需要加头结点吗？表头结点的作用与链表相同。

**栈的链式存储结构定义**

```c
struct node {
    ElemType data;
    node *next;
}; // 结点的"型"
typedef node *STACK; // 栈的"型"
```

两种示意图在内存中对应同一种状态

![](img/ad2aee679abbcf477936d4ee2701e2d3_113_0.png)

![](img/ad2aee679abbcf477936d4ee2701e2d3_113_1.png)

**栈的操作的实现**

**① STACK MakeNull()**

```c
STACK MakeNull()
{
    STACK s;
    s = new node;
    /* s = (node *)malloc(sizeof(node)); */
    s->next = NULL;
    return s;
}
```

**② Boolean Empty(STACK stk)**

```c
Boolean Empty(STACK stk)
{
    if (stk->next)
        return FALSE;
    else
        return TRUE;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_114_0.png)

**④ void Pop(STACK stk)**

```c
void Pop(STACK stk)
{
    STACK s;
    if (stk->next) { /* stk->next != NULL */
        s = stk->next;
        stk->next = s->next;
        delete s;  /* free(s) */
    }
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_116_0.png)

#### 2.3.3 栈与递归调用

**递归调用的定义**

子程序（或函数）直接调用自己或通过一系列调用语句间接调用自己。是一种描述问题和解决问题的基本方法。

**递归的基本思想**

把一个不能或不好求解的大问题转化为一个或几个小问题，再把这些小问题进一步分解成更小的小问题，直至每个小问题都可以直接求解。

**递归的要素**

- 递归边界条件：确定递归到何时终止，也称为递归出口；
- 递归模式：大问题是如何分解为小问题的，也称为递归体

**递归调用举例**

**求阶乘的函数**

```text
n! = { 1 当 n=1 时
       n * (n - 1)! 当 n≥1 时 }
```

**递归算法**

```c
long fact(int n)
{
    if (n == 0) return 1;
    else return n * fact(n - 1);
}
```

**求解阶乘 n! 的过程**

```text
递归调用
计算 fact(4)
计算 4*fact(3)
计算 3*fact(2)
计算 2*fact(1)
计算 fact(1)

回求值
返回 24
返回 6
返回 2
返回 1
```

- 递归过程在实现时，需要自己直接或间接调用自己。
- 层层向下递归，返回次序正好相反：

![](img/ad2aee679abbcf477936d4ee2701e2d3_121_0.png)
