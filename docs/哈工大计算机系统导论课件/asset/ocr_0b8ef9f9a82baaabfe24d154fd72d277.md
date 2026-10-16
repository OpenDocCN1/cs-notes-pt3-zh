# C程序例子

```
int sum(int *a, int n);

int array[2] = {1, 2};

int main()
{
    int val = sum(array, 2);
    return val;
}

main.c
```

```
int sum(int *a, int n)
{
    int i, s = 0;

    for (i = 0; i < n; i++) {
        s += a[i];
    }
    return s;
}

sum.c
```

每个模块都有自己的代码、数据（初始化全局变量、未初始化全局变量、静态变量、局部变量）