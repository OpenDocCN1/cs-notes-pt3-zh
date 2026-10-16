# 例子3

+   a.c文件

```
1 int i=5; /* a.c */
2 foo();
3 main(){
4     printf("%d",foo());
5 }
```

+   b.c文件

```
1 int i; /*b.c*/
2 foo(){
3     i*=2;
4 };
```