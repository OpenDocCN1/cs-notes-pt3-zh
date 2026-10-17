# # 模块的引用与裁剪

![](bbox=[0.1, 0.218, 0.4, 0.611])

```
/* 边的定义 */
typedef struct ENode *PtrToENode;
struct ENode{
    Vertex V1, V2;      /* 有向边<V1, V2> */
    WeightType Weight;  /* 权重 */
};
typedef PtrToENode Edge;

/* 图结点的定义 */
typedef struct GNode *PtrToGNode;
struct GNode{
    int Nv;              /* 顶点数 */
    int Ne;              /* 边数 */
    WeightType G[MaxVertexNum][MaxVertexNum]; /* 邻接矩阵 */
    DataType Data[MaxVertexNum];              /* 顶点对应数据 */
};
typedef PtrToGNode MGraph; /* 以邻接矩阵存储的图类型 */
```

```
#define MaxVertexNum 100  /* 最大顶点数设为100 */
#define INFINITY 65535     /* ∞被认为是不带符号整数的最大值65535*/
typedef int Vertex;        /* 用顶点下标表示顶点, 为整型 */
typedef int WeightType;    /* 边的权值均为整型 */
typedef char DataType;     /* 顶点存储的数据类型为字符型 */
```