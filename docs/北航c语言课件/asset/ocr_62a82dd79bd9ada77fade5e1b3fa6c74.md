```
```c
void main()
{
    int i=1;
    long int sigma=1;
    while (i<=10)
    {
        sigma=sigma*i;
        i++;
    }
    printf("10!=%ld\n", sigma);
}
```
```

![](bbox=[0.515, 0.145, 1.0, 0.546])

![](bbox=[0.593, 0.591, 0.914, 0.734])

> 思考：如果不使用long int，还可以使用什么变量类型定义sigma