```
```c
void fast_transpos(struct sparmatto a,b)
{
    b.m=a.n; b.n=a.m; b.t=a.t;
    if (b.t>0)
    {
        for(col=1;col<=a.n;col++)
            num[col]=0;       {num清零}
        for (t=1;t<=a.t;t++)              {对a.t个非零元素}
            num[a.data[t].j]=num[a.data[t].j]+1;  {按列写计数}

        cpot[1]=1;                                      {生成cpot}
        for (col=2; col<=a.n;col++)
            cpot[col]=cpot[col-1]+num[col-1];
        for (p=1; p<=a.t; p++)              {对a.t个非零元素转置}
        {
            col=a.data[p].j;  q=cpot[col];
            b.data[q].i=a.data[p].j;
            b.data[q].j=a.data[p].i;
            b.data[q].v=a.data[p].v;
            cpot[col]=cpot[col]+1;
        }
    }
}
```
```