# 3) 利用栈模拟递归—通用方法

如果是递归函数，需改写为递归过程

例： 求n!

```
void fact(int n; int &f){

init_stack(s);
0: if (n==0) f=1;
else
{
1: fact(n-1,f);
2: f:=n*f;
}
}
```

```
top=top+1; s[top].rd=2;
s[top].n=n; s[top].f=f;
n=n-1; goto 0;
```

```
if (top!=0)
{ s[top].f=f; {还原本层变参值}
top=top-1; n=s[top+1].n;
f=s[top+1].f; goto s[top+1].rd }
```