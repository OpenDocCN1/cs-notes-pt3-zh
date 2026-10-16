# 程序执行的主要步骤

+   - 从键盘读入x的值

```
printf ("please input x: ");
scanf("%f",&x);
```

+   - 依次计算以x, x+5, x+2作为实参的函数p的值

```
y=(p(x)*p(x)+(5*x))/(p(x+5)-sqrt(x))*p(x+2)
```

+   - 输入输出函数y的值

```
printf ("y(x)=%8.4f\n",y)
```