# 例：求200以内的最大的10个素数的和。

```
int sushu(long n)
{ long i;
for(i=2;i<=n-1;i++)
if(n%i==0) return 0;
return 1;
}
```

```
main()
{ long I,s=0,n=0;
int sushu(long n);
for(I=200;I--)
{ if(sushu(I))
{ s=s+I; n++;}
if(n==10)break;
}
printf("\n%ld",s);
}
```

C语言中允许在同一个程序的不同函数中定义相同名字的变量，这些变量在不同的函数中，作为完全不同的变量各自执行，互不干扰影响。

如此程序中，main函数与sushu函数中都分别定义了变量I与n，不同函数中的I与n独立执行，互不影响。

此程序的sushu函数中有两条return语句，函数将在第一次执行到某条return语句时结束，返回函数调用点，之后的语句将不再被执行。