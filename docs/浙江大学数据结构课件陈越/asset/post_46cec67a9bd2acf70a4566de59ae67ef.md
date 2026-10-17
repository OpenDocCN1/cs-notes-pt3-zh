

## （3）后序遍历

遍历过程为：

- ① 后序遍历其左子树；
- ② 后序遍历其右子树；
- ③ 访问根结点。

**（DFB）（HGIC）A**

**后序**遍历=> D E F B H G I C A

```c
void PostOrderTraversal( BinTree BT )
{
    if( BT ) {
        PostOrderTraversal( BT->Left );
        PostOrderTraversal( BT->Right );
        printf("%d", BT->Data);
    }
}
```

## 先序、中序和后序遍历过程

遍历过程中经过结点的路线一样，只是访问各结点的时机不同。

图中在从入口到出口的曲线上用⊗、☆ 和△三种符号分别标记出了先序、中序和后序访问各结点的时刻。

## 二叉树的非递归遍历

### 中序遍历非递归遍历算法

非递归算法实现的基本思路：**使用堆栈**

### 中序遍历非递归遍历算法

- 遇到一个结点，就把它压栈，并去遍历它的左子树；
- 当左子树遍历结束后，从栈顶弹出这个结点并访问它；
- 然后按其右指针再去中序遍历该结点的右子树。

```c
void InOrderTraversal( BinTree BT )
{
    BinTree T=BT;
    Stack S = CreatStack( MaxSize ); /*创建并初始化堆栈s*/
    while( T || !IsEmpty(S) ){
        while(T){ /*一直向左并将沿途结点压入堆栈*/
            Push(S,T);
            T = T->Left;
        }
        if(!IsEmpty(S)){
            T = Pop(S); /*结点弹出堆栈*/
            printf("%5d", T->Data); /*（访问）打印结点*/
            T = T->Right; /*转向右子树*/
        }
    }
}
```

### 先序遍历的非递归遍历算法

```c
void InOrderTraversal( BinTree BT )
{
    BinTree T = BT;
    Stack S = CreatStack( MaxSize ); /*创建并初始化堆栈s*/
    while ( T || !IsEmpty(S) ){
        while(T){ /*一直向左并将沿途结点压入堆栈*/
            Push(S,T);
            T = T->Left;
        }
        if(!IsEmpty(S)){
            T = Pop(S); /*结点弹出堆栈*/
            printf("%5d", T->Data); /*（访问）打印结点*/
            T = T->Right; /*转向右子树*/
        }
    }
}
```

### 后序遍历非递归遍历算法

## 层序遍历

二叉树遍历的核心问题：二维结构的线性化

- 从结点访问其左、右儿子结点
- 访问左儿子后，右儿子结点怎么办？
- 需要一个存储结构保存暂时不访问的结点
- 存储结构：堆栈、队列

### 层序遍历

❖ **队列实现：** 遍历从根结点开始，首先将根结点入队，然后开始执行循环：结点出队、访问该结点、其左右儿子入队

**层序遍历 =>** `A B C D F G I E H`

层序基本过程：先根结点入队，然后：

- ① 从队列中取出一个元素；
- ② 访问该元素所指结点；
- ③ 若该元素所指结点的左、右孩子结点非空，则将其左、右孩子的指针顺序入队。

```c
void LevelOrderTraversal ( BinTree BT )
{
    Queue Q;  BinTree T;
    if ( !BT ) return; /* 若是空树则直接返回 */
    Q = CreatQueue( MaxSize ); /*创建并初始化队列Q*/
    AddQ( Q, BT );
    while ( !IsEmpty( Q ) ) {
        T = DeleteQ( Q );
        printf("%d\n", T->Data); /*访问取出队列的结点*/
        if ( T->Left )  AddQ( Q, T->Left );
        if ( T->Right ) AddQ( Q, T->Right );
    }
}
```

## 【例】求二叉树的高度。

```c
int PostOrderGetHeight( BinTree BT )
{
    int HL, HR, MaxH;
    if( BT ) {
        HL = PostOrderGetHeight(BT->Left); /*求左子树的深度*/
        HR = PostOrderGetHeight(BT->Right); /*求右子树的深度*/
        MaxH = (HL > HR) ? HL : HR; /*取左右子树较大的深度*/
        return ( MaxH + 1 ); /*返回树的深度*/
    }
    else return 0; /* 空树深度为0 */
}
```

## 【例】由两种遍历序列确定二叉树

答案是：必须要有中序遍历序列和三种遍历中的任意两种遍历序列，能否唯一确定一棵二叉树呢？

没有中序的困扰：

- ➢ 先序遍历序列：A B
- ➢ 后序遍历序列：B A

### 【例】

先序序列：a b c d e f g h i j  
中序序列：c b e d a h g i j f

> 左子树（或右子树）序列不配套意味着什么？

类似地，后序和中序遍历序列也可以确定一棵二叉树。

## 小白专场：树的同构

### 题意理解

给定两棵树T1和T2。如果T1可以通过若干次左右孩子互换就变成T2，则我们称两棵树是“同构”的。现给定两棵树，请你判断它们是否是同构的。

### 求解思路

- 1. 二叉树表示
- 2. 建二叉树
- 3. 同构判别

### 二叉树表示

结构数组表示二叉树：静态链表

```c
#define MaxTree 10
#define ElementType char
#define Tree int
#define Null -1
struct TreeNode
{
    ElementType Element;
    Tree  Left;
    Tree  Right;
} T1[MaxTree], T2[MaxTree];
```

|   | A | B | C | D |   |
|---|---|---|---|---|---|
| Left | -1 | 2 | -1 | -1 |   |
| Right | 1 | 3 | -1 | -1 |   |
|   | 0 | 1 | 2 | 3 | 4 |

