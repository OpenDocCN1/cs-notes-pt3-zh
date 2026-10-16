# 顺序栈的基本运算：

# 4、取栈顶元素

```
Datatype gettop(sqstack *s)
{
    if(stackempty(s))
        error("stack is empty");
    return s->data[s->top];
}
```

![](bbox=[0.704, 0.699, 0.951, 0.927])