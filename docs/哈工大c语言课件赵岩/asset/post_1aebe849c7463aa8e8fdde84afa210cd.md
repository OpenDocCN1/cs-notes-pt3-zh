
## 结构体和函数

- 向函数传递结构体的单个成员
  - 单向值传递，函数内对结构内容的修改不影响原结构
- 向函数传递结构体的完整结构
  - 单向值传递，函数内对结构内容的修改不影响原结构，开销大
- 向函数传递结构体的首地址
  - 用结构体数组或者结构体指针做函数参数
  - 除提高效率外，还可以修改结构体指针所指向的结构体的内容

## 结构体做参数

```
1  typedef struct{
2    int x;
3    int y;}point;
4  point mid, begin={1,1}, end = {0, 0};
5    point MidPt(point pt1, point pt2){
6      point pt;
7      pt.x = (pt1.x+pt2.x)/2;
8      pt.y = (pt1.y+pt2.y)/2;
9      return pt; }
10     mid = MidPt(begin, end);
```

## 问题

整个过程中发生了几次结构体的拷贝？

## 结构体做参数和返回值

- 这样呢？

```
1 void MidPt(const point* pPt1,
2     const point* pPt2, point* pMid)
3 {
4     pMid->x = (pPt1->x + pPt2->x)/2;
5     pMid->y = (pPt1->y + pPt2->y)/2;
6 }
7 
8 MidPt(&begin , &end , &mid)
```

- 指针传递效率更高，内容传递更直观

## 洗牌和发牌模拟-1

```c
char *suit [] = {"Spades","Hearts",
"Clubs","Diamonds"};
char *face [] = {"A","2","3","4","5",
"6","7","8","9","10",
"jack","Queen","King"};
void FillCard(struct CARD wCard[],
char *wFace[], char *wSuit[]) {
int i;
for (i=0; i<52; i++) {
strcpy(wCard[i].suit, wSuit[i/13]);
strcpy(wCard[i].face, wFace[i%13]);
}
}
```

## 洗牌和发牌模拟-2

```
void Shuffle(struct CARD *wCard)
{
    int i,j;
    struct card temp;
    for (i=0; i<52; i++)
    {
        j = rand()%52;
        temp = wCard[i];
        wCard[i] = wCard[j];
        wCard[j] = temp; /* 洗牌过程 */
    }
}
```

## 洗牌和发牌模拟-3

```
void Deal(struct CARD *wCard)
{
    int i;
    for (i=0; i<52; i++) /*输出发牌结果*/
    {
        printf("%10s%10s\n", wCard[i].suit, wCard[i].face);
    }
}
```

## 结构体的嵌套

```
1 struct STUDENT{
2 int studentID;
3 char studentName[10];
4 char studentSex[4];
5 struct date timeOfEnter;
6 int scoreComputer;
7 int scoreEnglish;
8 int scoreMath;
9 int scoreMusic;
10 };
11 struct STUDENT stu[30] =
12 {{1,"令狐冲","男", {1999,12,20},90,83,72,82},
13  {2,"林平之","男", {1999,07,06},78,92,88,78}};
```

## 结构体嵌套

```
1 struct point
2 {
3     int x; int y;
4 };
5 
6 struct rect
7 {
8     struct point pt1;
9     struct point pt2;
10 };
```

## 结构体嵌套

- 下面的结构什么意思？

```
1 struct something
2 {
3     struct something obj1;
4     struct something obj2;
5 };
```

```
1 struct something
2 {
3     char name[10];
4     struct something* pOtherObj;
5 };
```

- 第一个结构无限制循环定义了，第二个没问题。

## 链表

- 链表：线性表的链式存储结构
- 其特点是用一组任意的存储单元存储线性表的数据元素；存储单元可以是连续的，也可以是不连续的
- 为表示每个元素与其后继元素之间的逻辑关系，除了存储元素本身的信息外，还要存储其直接后继的信息。两部分信息组成一个结点，每个结点包含：
  - 数据域：存储数据元素信息
  - 指针域：存储直接后继的存储位置信息
- n个结点链接成一个链表（因为只包含一个指针域，故又称线性链表或单链表）

## 数据结构-链表

- 结构体声明时不能包含自身，但可以包含指向本结构体类型的指针变量
- 链表（Linked table）

```
struct node
{
    int    data;
    struct node *next;
}
```

![](img/7afade9235e9e9d9b1d009051c946346_646_0.png)

## 链表节点删除

```
1 t = x->next;
2 x->next = t->next;
3 free(t);
```

![](img/7afade9235e9e9d9b1d009051c946346_647_0.png)

## 链表节点删除

```
1 t = x->next;
2 x->next = t->next;
3 free(t);
```

![](img/7afade9235e9e9d9b1d009051c946346_648_0.png)

## 链表节点删除

```
1 t = x->next;
2 x->next = t->next;
3 free(t);
```

![](img/7afade9235e9e9d9b1d009051c946346_649_0.png)

## 链表节点插入

```
1 t = malloc(sizeof(struct Node));
2 t->next = x->next;
3 x->next = t;
```

![](img/7afade9235e9e9d9b1d009051c946346_650_0.png)

## 链表节点插入

```
1 t = malloc(sizeof(struct Node));
2 t->next = x->next;
3 x->next = t;
```

![](img/7afade9235e9e9d9b1d009051c946346_651_0.png)

## 链表节点插入

```
1 t = malloc(sizeof(struct Node));
2 t->next = x->next;
3 x->next = t;
```

![](img/7afade9235e9e9d9b1d009051c946346_652_0.png)

## 结构体和共用体

- 结构体：
  - 把关系紧密且逻辑相关的多种不同类型的变量组织到统一的名字之下，也称复合数据类型
  - 这种类型的变量占用相邻的一段内存单元
- 共用体：
  - 把彼此互斥但又逻辑相关的多种不同类型的变量组织在一起
  - 这种类型的变量占用同一段内存单元，因此每一时刻只有一个数据起作用

## 共用体例子

```
1 union number{
2 char c;
3 short s;
4 int i;
5 };
```

![](img/7afade9235e9e9d9b1d009051c946346_654_0.png)

## 共用体的大小

- c、s 和 i 处于同样的地址
- sizeof(union number)
- 取决于占空间最多的那个成员变量

```
union number
{
    char c;
    short s;
    int i;
};
sizeof(number);
```
