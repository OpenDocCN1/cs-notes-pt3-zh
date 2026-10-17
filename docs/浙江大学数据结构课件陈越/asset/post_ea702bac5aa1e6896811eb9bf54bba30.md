
## 题意理解

输入样例：

```
4
13005711862 13588625832
13505711862 13088625832
13588625832 18087925832
15005713862 13588625832
```

```
13005711862    1
13588625832    3
13505711862    1
13088625832    1
18087925832    1
15005713862    1
```

输出样例：

```
13588625832 3
```

## 解法1－排序

1. **第1步：**读入最多2×10^5个电话号码，每个号码存为长度为11的字符串
2. **第2步：**按字符串非递减顺序排序
3. **第3步：**扫描有序数组，累计同号码出现的次数，并且更新最大次数

- 编程简单快捷
- 无法拓展解决动态插入的问题

## 解法3 – 带智商的散列

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_473_0.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_473_1.png)

## 程序框架搭建

```c
int main()
{
    创建散列表；
    读入号码插入表中；
    扫描表输出冠军；
    return 0;
}
```

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_474_0.png)

```c
int main()
{
    int N, i;
    ElementType Key;
    HashTable H;

    scanf("%d", &N);
    H = CreateTable(N*2); /* 创建一个散列表 */
    for (i=0; i<N; i++) {
        scanf("%s", Key); Insert( H, Key );
        scanf("%s", Key); Insert( H, Key );
    }
    ScanAndOutput( H );
    DestroyTable( H );
    return 0;
}
```

扫描整个散列表

更新最大通话次数；
更新最小号码 + 统计人数；

## 模块的引用与裁剪

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_476_0.png)

```c
#define KEYLENGTH 11 /* 关键词字符串的最大长度 */
/* 关键词类型用字符串 */
typedef char ElementType[KEYLENGTH+1];
typedef int Index; /* 散列地址类型 */
```

```c
typedef struct LNode *PtrToLNode;
struct LNode {
    ElementType Data;
    PtrToLNode Next;
    int Count;
};
typedef PtrToLNode Position;
typedef PtrToLNode List;
```

```c
typedef struct TblNode *HashTable;
struct TblNode { /* 散列表结点定义 */
    int TableSize; /* 表的最大长度 */
    List Heads; /* 指向链表头结点的数组 */
};
```

Copyright @ 2014, 浙江大学计算机科学与技术学院  
All Rights Reserved

## 模块的引用与裁剪

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_477_0.png)

```c
#define MAXTABLESIZE 100000
int NextPrime( int N )
{ /* 返回大于N且不超过MAXTABLESIZE的最小素数 */
    int i, p = (N%2)? N + 2 : N+1; /* 从大于N的下一个奇数开始 */
    while ( p <= MAXTABLESIZE ) {
        for( i=(int)sqrt( p ); i>2; i-- )
            if ( !(p%i) ) break; /* p不是素数 */
        if ( i==2 ) break; /* for正常结束，说明p是素数 */
        else p += 2; /* 否则试探下一个奇数 */
    }
    return p;
}

HashTable CreateTable( int TableSize )
{
    HashTable H;
    int i;
    H = (HashTable)malloc(sizeof(struct TblNode));
    H->TableSize = NextPrime(TableSize);
    H->Heads = (List)malloc(H->TableSize*sizeof(struct LNode));
    for( i=0; i<H->TableSize; i++ ) {
        H->Heads[i].Data[0] = '\0'; H->Heads[i].Next = NULL;
        H->Heads[i].Count = 0;
    }
    return H;
}
```

```c
int Hash ( int Key, int P )
{ /* 除留余数法散列函数 */
    return Key%P;
}
```

## 模块的引用与裁剪

```c
bool Insert( HashTable H, ElementType Key )
{
    Position P, NewCell;
    Index Pos;

    P = Find( H, Key );
    if ( !P ) { /* 关键词未找到，可以插入 */
        NewCell = (Position)malloc(sizeof(struct LNode));
        strcpy(NewCell->Data, Key);
        NewCell->Count = 1;
        Pos = Hash(atoi(Key+KEYLENGTH-MAX), H->TableSize);
        /* 将NewCell插入为H->Heads[Pos]链表的第1个结点 */
        NewCell->Next = H->Heads[Pos].Next;
        H->Heads[Pos].Next = NewCell;
        return true;
    }
    else { /* 关键词已存在 */
        P->Count++;
        return false;
    }
}
```

## 树之 习题选讲

浙江大学 陈 越

## Tree Traversals Again

Copyright @ 2014, 浙江大学计算机科学与技术学院  
All Rights Reserved

## 题意理解

### 非递归中序遍历

- Push的顺序为先序遍历
- Pop的顺序给出中序遍历

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_482_0.png)

Sample Input:
6
Push 1
Push 2
Push 3
Pop
Pop
Push 4
Pop
Pop
Push 5
Push 6
Pop
Pop

|   |   |   |   |   |   |
|---|---|---|---|---|---|
| pre | 1 | 2 | 3 | 4 | 5 | 6 |
| in | 3 | 2 | 4 | 1 | 6 | 5 |

## 核心算法

pre ① 2 3 4 5 6

in 3 2 4 ① 6 5

post 3 4 2 6 5 ①

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_483_0.png)

```c
void solve( int prel, int inl, int postL, int n )
{
    if (n==0) return;

    if (n==1) (post[postL] = pre[preL]; return;)

    root = pre[preL];
    post[postL+n-1] = root;

    for (i=0; i<n; i++)
    if (in[inL+i] == root) break;

    L = i; R = n-L-1;
    solve(preL+1, inL, postL, L);
    solve(preL+L+1, inL+L+1, postL+L, R);
}
```

Copyright @ 2014, 浙江大学计算机科学与技术学院
All Rights Reserved
