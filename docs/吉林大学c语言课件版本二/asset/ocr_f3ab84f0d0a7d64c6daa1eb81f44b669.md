# 习题6.36

令整型指针p指向二维数组的第一个元素a[0][0]：

```
int *p=&a[0][0];
```

```
sort(int col,int row,int *p)
```

```
i=0;
i<col*row-1;
i++
```

在*(p+i)~(p+col*row-1) 之间, 找最小元素*(p+j)
交换 *(p+i)、*(p+j)

结束