# C语言描述

```
Status InitStack(SqStack &S)
{
    if(!(S.base=(SElemType *)malloc(STACK_INIT_SIZE*sizeof(SElemType))))
        exit(OVERFLOW); // 存储分配失败
    S.top=S.base;
    S.stacksize=STACK_INIT_SIZE;
    return OK;
}
```