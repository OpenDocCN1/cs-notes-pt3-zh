# 程序举例：

```
```c
#define MAX(x,y) x>y?x:y
main()
{
int n1,n2;
float f1,f2;
scanf("%d%d%f%f",&n1,&n2,&f1,&f2);
printf("maxi=%dmaxf=%f",MAX(n1,n2),MAX(f1,f2));
}
```
```

# 经预编译宏替换后的printf语句如下：

```
```c
printf("maxi=%dmaxf=%f",n1>n2?n1:n2,f1>f2?f1:f2);
```
```