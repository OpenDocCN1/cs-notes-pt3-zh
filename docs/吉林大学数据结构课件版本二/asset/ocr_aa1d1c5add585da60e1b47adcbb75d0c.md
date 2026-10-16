# 初始化

```
status InitStack ( SqStack &S ) {  //置空栈
S.base =(SElemType *)malloc(STACK_INIT_SIZE * sizeof(SElemType));
If(!S.base)  exit(overflow);
S.top = S.base ;
S.stacksize= STACK_INIT_SIZE ;
Return ok;
}
```

![](bbox=[0.84, 0.48, 0.99, 0.71])

空栈

置空栈