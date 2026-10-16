# 实例源码

```
```c
#define CONST 1.42e8
int n;
double term, sum = 0;  /*求和变量赋初值*/
for (n=1; n<=64; n++){
    term = pow(2, n-1);
    sum += term;        /*作累加运算*/
}
printf("sum = %e\n", sum);   /*总考查数*/
printf("volum=%e\n", sum/CONST); /*体积数*/
```
```