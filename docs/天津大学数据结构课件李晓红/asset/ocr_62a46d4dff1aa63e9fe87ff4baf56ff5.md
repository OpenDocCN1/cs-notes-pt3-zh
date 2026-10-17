# ## 定义

const int MaxSize = 100;  //静态链表大小

typedef int ListData;

typedef struct node {   //静态链表结点
ListData data;
int link;
} SNode;

typedef struct {   //静态链表
SNode Nodes[MaxSize];
int newptr;   //当前可分配空间首地址
} SLinkList;