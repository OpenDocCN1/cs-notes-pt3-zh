# 2-3 默认参数的函数

默认参数也称为缺省参量。

```
例： void delay(int loops);
    void delay(int loops)
{
    if (loops==0)
        return;
    for (int i=0;i<loops;i++);
}
```

将loops 定义成默认值为1000

```
void delay(int =1000);
```

调用时： delay();
            delay(2000);

允许函数默认参数值，是为了让编程简单，让编译器做更多的检查错误工作。

# 默认参数函数的声明

当又有声明又有定义时，定义中不允许默认参数。

若只有定义，则默认参数才可出现在函数定义中