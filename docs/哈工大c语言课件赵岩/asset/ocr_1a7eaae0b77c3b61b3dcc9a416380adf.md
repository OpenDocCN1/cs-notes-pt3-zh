# 动态一维数组

```
1   int *p = NULL;
2   printf("Please enter array size:");
3   scanf("%d", &n);
4   p = (int *) malloc(n * sizeof (int));
5   p[i]   /*像一维数组一样使用*/
6   .....
7   free(p);
```