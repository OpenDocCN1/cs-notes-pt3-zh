
## 2.4.3 队列的数组实现(Cont.)

队列的链接存储结构及实现

如何判断循环队列队空和队满？

队满时，front和rear的相对位置

![](img/ad2aee679abbcf477936d4ee2701e2d3_157_0.png)

队满： front==rear

## 2.4.3 队列的数组实现(Cont.)

队列的链接存储结构及实现

+ 如何区分队空、队满的判定条件？

+ 方法一：增设一个存储队列中元素个数的计数器count，当front==rear 且count==0时，队空；当且count==MaxSize时，队满；

+ 方法二：设置标志flag，当front==rear且flag==0时为队空；当front==rear且flag==1时为队满。

+ 方法三：保留队空的判定条件：front==rear；把队满判定条件修改为：((front+1)%MaxSize==rear)。

+ 代价：浪费一个元素空间，队满时数组中有一个空闲单元；

## 2.4.3 队列的数组实现(Cont.)

存储结构的定义

```
struct QUEUE {
	ElemType data [MaxSize ];
	int front ;
	int rear ;
};
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_159_0.png)

## 2.4.3 队列的数组实现(Cont.)

队列的链接存储结构及实现

+ 操作的实现---- ①队列初始化

```
void MakeNull ( QUEUE &Q)
{
    Q.front = MaxSize-1;
    Q.rear  = MaxSize-1;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_160_0.png)

## 2.4.3 队列的数组实现(Cont.)

队列的链接存储结构及实现

+ 操作的实现---- ②队列判空

```
bool Empty( QUEUE Q )
{   if ( Q.rear == Q.front )
    return TRUE ;
  else
    return FALSE;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_161_0.png)

## 2.4.3 队列的数组实现(Cont.)

队列的链接存储结构及实现

操作的实现---- ③返回队首元素

```
ElemType Front( QUEUE Q )
{ if ( Empty( Q ) ) return NULL ESE ;
else { Q.front=(Q.front+1)%MaxSize ;
return (Q.data[ Q. front ]);
}
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_162_0.png)

## 2.4.3 队列的数组实现(Cont.)

队列的链接存储结构及实现

操作的实现---- ④入队

```
void EnQueue ( ElemType x, QUEUE &Q )
{
    if ( (Q.rear+1)%MaxSize == Q.front )
        cout<< "队列满";
    else{    Q.rear=(Q.rear+1)%MaxSize ;
        Q.data[ Q.rear ] = x ;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_163_0.png)

## 2.4.3 队列的数组实现(Cont.)

队列的链接存储结构及实现

操作的实现---- ⑤ 出队

```
void DeQueue( QUEUE Q );
{
    if( Empty( Q ) )
        cout<< "空队列" <<endl;
    else
        Q.front = (Q.front+1)%MaxSize ;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_164_0.png)

## 2.4.4 队列的应用

+ - 队列使用的原则
+ - 凡是符合先进先出原则的
+ - 服务窗口和排号机、打印机的缓冲区、分时系统、树型结构的遍历、图的广度优先搜索等等

+ - 举例
+ - 约瑟夫出圈问题：n个人排成一圈，从第一个开始报数，报到m的人出圈，剩下的人继续开始从1报数，直到所有人都出圈为止。
+ - 舞伴问题：假设在周末舞会上，男士们和女士们进入舞厅时，各自排成一队。跳舞开始时，依次从男队和女队的队头上各出一人配成舞伴。若两队初始人数不相同，则较长的那一队中未配对者等待下一轮舞曲。现要求写算法模拟上述舞伴配对问题。

## 2.5.1 串的逻辑结构

## 串的操作

+ - string MakeNull();
+ - bool IsNull ( S );
+ - void In( S, a );
+ - int Len( S );
+ - void Concat( S1, S2 );
+ - string Substr( S, m, n );
+ - bool Index( S, S1 );

与其他线性结构相比，串的操作对象有什么特点？

+ - 串的操作通常以 串的整体 作为操作对象。

## 2.5.2 串的存储结构

## 顺序串：

用数组来存储串中的字符序列。

## 非压缩形式

![](img/ad2aee679abbcf477936d4ee2701e2d3_168_0.png)

## 压缩形式

![](img/ad2aee679abbcf477936d4ee2701e2d3_168_1.png)

## 2.5.2 串的存储结构(Cont.)

如何表示串的长度？

+ - 方法一： 用一个变量来表示串的实际长度， 同一般线性表
+ - 方法二： 在串尾存储一个不会在串中出现的特殊字符作为串的终结符，表示串的结尾。

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | ... ... | Max-1 |
|---|---|---|---|---|---|---|---|---|
| c | h | i | n | e | s | e | 空闲 | 7 |

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | ... ... | Max- |
|---|---|---|---|---|---|---|---|---|---|
| c | h | i | n | e | s | e | \0 | 空闲 |

## 2.5.2 串的存储结构(Cont.)

## 链接串：

用链接存储结构来存储串。

## 非压缩形式

## 压缩形式

假设地址值4四个字节，每个字符一个字节。

## 2.5.3 模式匹配

## 模式匹配：

给定主串 S="s₁s₂…sₙ" 和模式 T="t₁t₂…tₘ"，在 S 中寻找 T 的过程称为模式匹配。如果匹配成功，返回 T 在 S 中的位置 如果匹配失败，返回 0。

假设串采用顺序存储结构，串的长度存放在数组的 0 号单元，串值从 1 号单元开始存放。

## 朴素模式匹配算法(Brute-Force算法)：枚举法

## 基本思想

从主串 S 的第一个字符开始和模式 T 的第一个字符进行比较，若相等，则继续比较两者的后续字符；否则，从主串 S 的第二个字符开始和模式 T 的第一个字符进行比较，重复上述过程，直到 T 中的字符全部比较完毕，则说明本趟匹配成功；或 S 中字符全部比较完，则说明匹配失败。

## 2.5.3 模式匹配(Cont.)

设主串S= “abab cabcacbab”，模式串T= “abcac”

第1趟匹配 主串 ababcabcacbab i=3
模式串 abc j=3 匹配失败

第2趟匹配 主串 ababcabcacbab i=2
模式串 abc j=1 匹配失败

第3趟匹配 主串 ababcabcacbab i=7
模式串 abcac j=5 匹配失败

第4趟匹配 主串 ababcabcacbab i=4
模式串 abc j=1 匹配失败

第5趟匹配 主串 ababcabcacbab i=5
模式串 abc j=1 匹配失败

第6趟匹配 主串 ababcabcacbab i=6
模式串 abcac j=6 匹配成功

特点:主串指针需回溯，模式串指针需复位。

## 2.5.3 模式匹配(Cont.)

## BF算法实现的详细步骤：

+ 1. 在串S和串T中设比较的起始下标i和j;
+ 2. 循环直到S或T的所有字符均比较完;
+ 2.1 如果S[i]=T[j]，继续比较S和T的下一个字符;
+ 2.2 否则，将i和j回溯，准备下一趟比较;
+ 3. 如果T中所有字符均比较完，则匹配成功，返回匹配的起始比较下标；否则，匹配失败，返回0;
