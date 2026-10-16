# bool gcd( int u, int v)

```
r=v
while r!=0:
    r=u%v
    u=v
    v=r
if u==1:
    return true
else:
    return false
```

结束