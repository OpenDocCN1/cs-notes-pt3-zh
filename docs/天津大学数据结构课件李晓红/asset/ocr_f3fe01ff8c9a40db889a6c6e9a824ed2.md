# # 链式队列的定义

typedef int QueueData;

typedef struct node {
QueueData data; //队列结点数据
struct node *link; //结点链指针
} QueueNode;

typedef struct {
QueueNode *rear, *front;
} LinkQueue;