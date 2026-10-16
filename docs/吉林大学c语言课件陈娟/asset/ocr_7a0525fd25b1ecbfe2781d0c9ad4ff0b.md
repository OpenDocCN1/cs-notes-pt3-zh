# 指针做参数总结

```
void h(int x, int *y){...}
void g(int m,int *n){
    int a, *b;
    h(a,b);
    h(*b,&a);
    h(m,n);
    h(*n,&m);
}
```