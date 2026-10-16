# 例：用递归法求n!

算法： f(n)= { 1          (n=1)
 f(n-1)*n   (n>1) }

```
main()
{long jx(int);
    int n;
    long f;
    printf("Input n :");
    scanf("%d",&n);
    f= jx(n);
    printf("\n n!=%d",f);
}
```

```
long jx(int n)
{
    long f;
    if(n==1) f=1;
    else f=n*jx(n-1);
    return f;
}
//n!=n*jx(n-1)
//jx(n1)= (n-1)*jx(n-2)
// ...
```