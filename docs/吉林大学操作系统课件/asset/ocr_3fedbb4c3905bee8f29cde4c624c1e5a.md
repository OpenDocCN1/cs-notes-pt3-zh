# Simultaneous V-operation

```
SV(S1,d1;...;Sn,dn)
{
    for(i=1; i<=n; i++)
        Si = Si+di;
        Remove all processes waiting in the
        queue associated with Si into ready queue;
}
```

其中Si为信号量，ti、di为大于0的整数。当ti、di均为1时，称为AND型信号量，是最常用的一种形式。