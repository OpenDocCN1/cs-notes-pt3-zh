# 步骤 1: 符号解析

目的：将每个模块中引用的符号与某个目标模块中的定义符号建立关联

```
int sum(int *a, int n);
int array[2] = {1, 2};
int main()
{
    int val = sum(array, 2);
    return val;
}
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
```

引用一个全局符号...

...它在这儿定义

定义一个全局符号

引用全局符号...

链接器不知道 val的任何信息

链接器不知道i和s的任何信息

它在这儿定义

main.c

sum.c