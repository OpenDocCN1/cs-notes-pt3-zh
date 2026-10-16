# Chapter 7 Runtime Environments

# Section 2 Storage allocation strategies

4. Stack allocation

3) Stack allocation for non-nested procedure

```
int f(int n)
{
    if (n<=1) return 1;
else {
    int t1,t2,t;
    t1=f(n-1);
    t2=f(n-2);
    t=t1+t2;
    return t} }
```