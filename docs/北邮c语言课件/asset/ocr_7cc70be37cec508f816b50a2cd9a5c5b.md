```
```c
double fsum(int n)
{
    int i; double s=0.0, y;
    for(i=~n; i<=n; i++)
    {y=f(1.0*i); s+=y;}
    return y;
}

main()
{
    clrscr();
    printf("%lf\n", fsum(30));
}
```
```