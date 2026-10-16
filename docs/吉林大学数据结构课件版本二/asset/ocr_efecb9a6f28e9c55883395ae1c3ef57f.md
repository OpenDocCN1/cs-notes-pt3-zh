# 顺序栈的类型表示：

```
#define STACK_INIT_SIZE 100;
#define STACKINCREMENT 10;
typedef struct
{
//顺序栈定义
SElemType *base; //栈底指针
SElemType *top; //栈顶指针
int stacksize; //当前已分配的存储空间
} SqStack;
```

空栈

![](bbox=[0.78, 0.01, 0.98, 0.28])