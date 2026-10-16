```
```cpp
double decas(int n,double P[],double t)
{
    int m,i;
    double *R, *Q, P0;
    R = new double[n +1];
    Q = new double[n +1];
    for(i=0;i<=n;i++)
        R[i]= P [i];  //将控制点坐标P保存于R中
```
```