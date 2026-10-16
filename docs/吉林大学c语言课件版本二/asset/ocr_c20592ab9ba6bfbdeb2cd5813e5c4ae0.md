# sort(int col,int row,int *p)

```
j=i
```

```
i=0;
i<col*row-1;
i++
```

```
k=i+1;
k<col*row;
k++
```

```
*(p+k)
<
*(p+j)
```

```
j=k
```

交换 *(p+i)、 *(p+j)

结束