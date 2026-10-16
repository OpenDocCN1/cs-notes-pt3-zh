# [算法例] 求转置矩阵

# 算法1 { O(n*t) }

```
void trans_sparmat(struct sparmattp a,b)
{
    b.m=a.n; b.n=a.m; b.t=a.t;
    if (b.t > 0)
    {
        { q=1;        /* 指示b中存放数据的位置，初值为1 */
          for (col=1; col<=a.n; col++)    /* 对a扫描a.n趟 */
              for (p=1; p<=a.t; p++)     /* 对a.t个数据检查 */
                  if (a.data[p].j==col)   /* 满足当前扫描列号 */
                  {
                      b.data[q].i=a.data[p].j;  /* 向b赋值 */
                      b.data[q].j=a.data[p].i;
                      b.data[q].v=a.data[p].v;
                      q=q+1;                     /* 修正q值 */
                  }
        }
    }
}
```