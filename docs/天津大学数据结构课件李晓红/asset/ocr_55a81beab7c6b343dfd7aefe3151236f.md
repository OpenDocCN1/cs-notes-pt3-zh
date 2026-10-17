# # 顺序栈的类型表示：

#define STACK_INIT_SIZE 100;
#define STACKINCREMENT 10;

typedef char StackData;

typedef struct {    //顺序栈定义
StackData *base; //栈底指针
StackData *top; //栈顶指针
int stacksize; //当前已分配的存储空间
} SeqStack;