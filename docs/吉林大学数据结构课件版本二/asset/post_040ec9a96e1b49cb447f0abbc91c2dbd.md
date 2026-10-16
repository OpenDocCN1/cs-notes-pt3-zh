
```
typedef struct node{
char data[10];
struct node *next;
}qtype;

typedef struct qp{
qtype *front,*rear;
}queue;

void seedoctor()
{
flag=1;
q=(queue*)malloc(sizeof(queue));
q->front=(qtype*)malloc(sizeof(qtype));
q->front->next=null;
q->rear=q->front;
```

```
while(flag==1)
{
printf("\n\n\n1:queue 2:seedoctor 3:seequeue 0:stopwork please select:");
scanf("%d",&sel);
switch(sel)
{
case 0:if(q->front!=q->rear)
printf("\nplease see doctor tomorrow!");
flag=0;
break;
```

```
case 1: printf("\nplease input the patient's name:");
    s=(qtype*)malloc(sizeof(qtype));
    s->next=null;
    scanf("%s",s->data);
    q->rear->next=s;
    q->rear=s;
    break;

case 2: if(q->front==q->rear)
    printf("\n no patient!");
else
    { s=q->front->next;
    if(q->rear==s) q->rear=q->front;
    printf("\npatient: '%s' see doctor!",s->data);
    q->front->next=s->next;
    free(s);
    }
    break;
```

```
case 3: if(q->front == q->rear)
printf("\n no patient!");
else{
s=q->front->next;
printf("\n the queue of the patients is:\n");
while(s!=null)
printf(" %s",s->data);
s=s->next;
}
break;
default: printf("\n please input the correct data:");
break;
}
}
```

## 思考题

假设您是一个金融家，在一月、四月和九月分别购入X公司的100股股票，并且在六月和十一月分别卖出100股。这几个月股票的价格分别为：

| 一月 | 四月 | 六月 | 九月 | 十一月 |
| --- | --- | --- | --- | --- |
| ¥10 | ¥30 | ¥20 | ¥50 | ¥30 |

+   - 在如下情况下判断您的投资是盈利还是亏损：
+   - A) FIFO财务处理
+   - B) LIFO财务处理

（也就是说，假设以队列方式或堆栈方式保留您的股票凭证），另外，在年底您仍然拥有的100股不计算在内。

## 思考题

+   - 在火车站的调度中,假设有一列软席和硬席混合的火车箱,现希望将软席车厢都调度到前面,硬席车厢都放在后面,试编写一算法。

## 产生溢出
称为上溢

设有顺序栈A，将元素a、b、c、d、e、f入栈

Top5

有数组A[5]

A[4]
A[3]
A[2]
A[1]
A[0]

e
d
c
b
a

Top=-1表示栈空

Top=0
表示栈中有一个元素

Top=MAXQSIZ
E-1

表示栈满

## 第四章 串

+   - 4.1 串类型的定义
+   - 4.2 串的表示和实现
+     - 4.2.1 定长顺序存储表示
+     - 4.2.2 堆分配存储表示
+     - 4.2.3 串的块链存储表示

## 第四章 串

## 4.1 串类型的定义

一、串的基本概念

定义：字符串是 n（≥0）个字符的有限序列
记作 S = "c₁c₂c₃...cₙ"

+   - 其中：
+     - S 是串名字
+     - "c₁c₂c₃...cₙ"是串值
+     - cᵢ 是串中字符
+     - n 是串的长度

例如，S = "Tsinghua University"

## 4.1 串类型的定义

# 一、串的基本概念

+   通常将仅由一个或多个空格组成的串称为空白串(Blank String)

+   长度为零的串称为空串(Empty String)，它不包含任何字符。

> 注意：空串和空白串的不同，例如 “ ” 和 “” 分别表示长度为1的空白串和长度为0的空串。

## 4.1 字符串的定义

# 一、串的基本概念

串中任意个连续字符组成的子序列称为该串的子串，包含子串的串相应地称为主串。

子串在主串中首次出现时的该子串的首字符对应的主串中的序号，定义为子串在主串中的序号 (或位置)

例如，设A和B分别为

```
A= “This is a string”
B= “is”
```

## 4.1 串类型的定义

# 一、串的基本概念

注意：空串是任意串的子串，任意串是其自身的子串。

# 串相等的判断

当且仅当两个串的值相等。

例如，设A和B分别为

A= “This is a string”      B= “is”

B= “string”      D= “This is

## 4.1 字符串的定义

# 一、串的基本概念

串的抽象数据类型定义

# 例2、串的定位 index(S, T, pos)

在主串 S 中取从第 i (i 的初值为 pos) 个字符起、长度和串 T 相等的子串和 T 比较，若相等，则求得函数值为 i，否则值增 1，直至 S 中不存在和串 T 相等的子串为止。

```
int index(string S,string T,int pos)
{
    if(pos>0){
        n=strlen(s);  m=strlen(t);  i=pos;
        while(i<=n-m+1){
            substr(sub,S,i,m);
            if(strcmp(sub,T)!=0)++i;
            else return(i);
        }
    }
    return(0);
}
```

## 4.2 串的表现和实现

+   - 4.2.1 定长顺序存储表示
+   - 4.2.2 堆分配存储表示
+   - 4.2.3 串的链式存储结构

## 4.2 串的表现和实现

## 4.2.1 定长顺序存储表示

```
#define maxstrlen 255

typedef char sstring[maxstrlen+1];

sstring s; // s是一个可容纳255个字符的顺序串。
```

## 4.2.1 定长顺序存储表示下的相关操作

# 一、串的链接 concat(&T,S1,S2)

例：串 s1 = “beijing ”
s2 = “university”

使用示例 T=s1 + s2;

连接结果 T= “beijing university”

## 4.2.1 定长顺序存储表示下的相关操作

# 1、串的连接 concat(&T,S1,S2) 的基本思想

将串 S1 和串 S2 连接在一起生成一个新串 T，可能有如下三种情况：

+   串 S1 和串 S2 连接在一起的长度小于等于新串 T 的长度，产生正确结果
+   串 S1 和串 S2 连接在一起的长度大于新串 T 的长度，并且 S1 的长度小于 T 的长度，此时，S2 产生截断。
+   串 S1 的长度等于 T 的长度，此时，串 S2 整个被舍弃并设置一个标志 uncut 来标明是否产生截断

## 1、串的联接concat(&T,S1,S2)

Status concat(SSString&T,SSString S1,SSString S2)

```
{
if(S1[0]+S2[0]<=MAXSTRLEN)
{
T[1...S1[0]]=S1[1...S1[0]];
T[S1[0]+1...S1[0]+S2[0]]=S2 [1...S2[0]];
T[0]= S1[0]+S2[0];
uncut=true;
}
}
```

## 1、串的联接concat(&T,S1,S2)

```
else if (S1[0] < MAXSTRLEN)
{
    T[1...S1[0]] = S1[1..S1[0]];
    T[S1[0]+1...MAXSTRLEN] = S2[1.. .MAXSTRLEN-S1[0]]
    T[0] = MAXSTRLEN;
    uncut = false;
}
else{
    T[0... MAXSTRLEN] = S1[0... MAXSTRLEN];
    uncut = false;
}
return uncut;
}
```
