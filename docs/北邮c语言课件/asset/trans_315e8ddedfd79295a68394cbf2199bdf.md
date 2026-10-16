

## 结构体类型数组

- 结构体数组的定义

三种形式：

形式一：

形式二：

形式三：

```
struct
{
  int num;
  char name[20];
  char sex;
  int age;
}stu[2];
```

![](img/609af85bac45577917bd36819bca122b_421_0.png)

## 结构体数组初始化与引用

- 结构体数组初始化
- 结构体数组引用

引用方式：结构体数组名[下标].成员名

```c
struct student
{
    int num;
    char name[20];
}str[3];
```

```c
struct student
{
    int num;
    char name[20];
    char sex;
    int age;
}str[3];
```

```c
str[0] = {1, "Wang Lin", 'M', 20};
str[1] = {2, "Li Gang", 'M', 19};
strcpy(str[0].name, "Zhao Da");
```

```c
stu[1].age++;
```

全部初始化时维数可省

## 例 统计候选人选票

```c
struct person
{
    char name[20];
    int count;
}leader[3]={"Li",0,"Zhang",0,"Wang",0};
main()
{
    int i,j; char leader_name[20];
    for(i=1;i<=10;i++)
    {
        scanf("%s",leader_name);
        for(j=0;j<3;j++)
            if(strcmp(leader_name,leader[j].name)==0)
                leader[j].count++;
    }
    for(i=0;i<3;i++)
        printf("%5s:%d\n",leader[i].name,leader[i].count);
}
```

| name | count |
|---|---:|
| Li | 0 |
| Zhang | 0 |
| Wang | 0 |

![](img/609af85bac45577917bd36819bca122b_423_0.png)

## 总结：结构体成员变量引用方式

- ①结构体变量.成员名
- ②(*p).成员名
- ③p->成员名

其中，->称为指向运算符

请分析下列几种运算：

- ①p->n
- ②p->n++
- ③++p->n

## 指向结构体数组元素的指针

例 指向结构体数组的指针

```c
struct student
{ int num;
char name[20];
char sex;
int age;
}stu[3]={{10101,"Li Lin",'M',18},
{10102,"Zhang Fun",'M',19},
{10104,"Wang Min",'F',20}};
main()
{ struct student *p;
for(p=stu;p<stu+3;p++)
printf("%d%s%c%d\n",p->num,p->name,p->sex,p->age);
}
```

## 结构体变量作为函数参数

- 用结构体变量的成员作参数——值传递
- 用指向结构体变量或数组的指针作参数——地址传递
- 用结构体变量作参数——多值传递，效率低

## 链表概述（1）

- 所谓链表是指若干个数据项按一定的原则连接起来。
- 每个数据项都包含有若干个数据和一个指向下一个数据项的指针，依靠这些指针将所有的数据项连接成一个链表。
- 每个数据项称为一个“结点”。

## 链表概述（2）

![](img/609af85bac45577917bd36819bca122b_429_0.png)

![](img/609af85bac45577917bd36819bca122b_429_1.png)

```c
struct student {
    long num;
    float score;
    struct student *next;
};
struct student *head;
```

## 一个简单链表示例：

![](img/609af85bac45577917bd36819bca122b_430_0.png)

## 链表的基本操作

- 链表的建立
  - 从链尾到链头：新节点插入到链头
  - 从链头到链尾：新节点插入到链尾
- 链表的插入操作
  - 根据一定的条件，把新节点插入到指定位置
- 链表的删除操作
  - 根据一定的条件，删除一个或多个结点
- 链表的输出操作
- 链表的查找操作

## 建立链表操作（从链尾到链头）

① for(i=0; i<n; i++)

head

a_{i+1}

a_i

```c
④ head = p;
```

```c
③ p->next = head;
```

p

```c
② p = malloc(sizeof(struct node));
p->data = a[i];
```

## 建立链表操作（从链头到链尾）

① for(i=0; i<n; i++)

```c
⑤ p = q;
```

```c
④ p->next = q;
```

```c
③ q->next = NULL;
```

```c
② q = malloc(sizeof(struct node));
q->data = a[i];
```

![](img/609af85bac45577917bd36819bca122b_433_0.png)

## 链表的插入操作

① if(p满足插入条件)

![](img/609af85bac45577917bd36819bca122b_434_0.png)

```c
② q = malloc(sizeof (struct node));
   q->data = x;
```

```c
③ q->next = p->next;
```

```c
④ p->next = q;
```

## 链表的删除操作

① if(p->next满足删除条件)

```c
② q = p->next;
```

```c
④ free(q);
```

```c
③ p->next = q->next;
```

![](img/609af85bac45577917bd36819bca122b_435_0.png)

## 链表的输出操作

① while(p)

```c
③ p = p->next;
```

```c
② printf("%d", p->data);
```

![](img/609af85bac45577917bd36819bca122b_436_0.png)

## 链表的查找操作

① while(num!=p1->num && p1!=NULL )

```c
③ p2=p1;p1=p1->next;
```

```c
② printf ("find: %ld %5.2f\n", num, p1->score);
```

![](img/609af85bac45577917bd36819bca122b_437_0.png)

![](img/609af85bac45577917bd36819bca122b_438_0.png)

(main)

| 变量 | 值 |
|---|---:|
| a | 27 |
| b | 3 |
| c | 30 |

arg

copy

(main)

| 变量 | 值 |
|---|---:|
| a | 27 |
| b | 3 |
| c | 30 |

(func)

| 参数 | 值 |
|---|---:|
| a | 27 |
| b | 3 |
| c | 30 |

arg

parm

(main)

| 变量 | 值 |
|---|---:|
| a | 27 |
| b | 3 |
| c | 30 |

(func)

| 参数 | 值 |
|---|---:|
| a | 18 |
| b | 5 |
| c | 90 |

arg

parm

(main)

| 变量 | 值 |
|---|---:|
| a | 27 |
| b | 3 |
| c | 30 |

arg

