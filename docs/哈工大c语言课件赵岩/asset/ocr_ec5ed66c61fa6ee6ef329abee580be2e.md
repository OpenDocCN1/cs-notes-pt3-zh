# 汉诺塔源码

# Demo 2: Hanoi source code

```
void hanoi(int n,char A,char B,char C)
{
if(n==1)
{
printf("Move disk %d from %c to %c\n",n,A,C);
}
else
{
hanoi(n-1,A,C,B);
printf("Move disk %d from %c to %c\n",n,A,C);
hanoi(n-1,B,A,C);
}
}
```