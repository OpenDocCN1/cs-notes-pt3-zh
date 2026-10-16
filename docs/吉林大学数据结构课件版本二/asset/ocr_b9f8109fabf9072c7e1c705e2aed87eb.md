# 顺序栈的基本运算：

```
判栈满
int StackFull (SqStack S)
{
    if( S.top- S.base >= S.StackSize )
        return TRUE; //判栈满,满则返回TRUE
    else return  FALSE; //否则返回FALSE
}
```