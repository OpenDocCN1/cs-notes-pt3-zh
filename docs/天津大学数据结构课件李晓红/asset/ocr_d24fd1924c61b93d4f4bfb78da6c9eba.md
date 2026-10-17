# 邻接表表示的图的定义（为算法）

```
typedef char VertexData; //顶点数据类型

typedef int EdgeData; //边上权值类型

typedef struct node { //边结点
    int dest; //目标顶点下标
    EdgeData cost; //边上的权值
    Struct node * link; //下一边链接指针
} EdgeNode;
```