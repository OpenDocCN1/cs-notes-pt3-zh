# 按列序为主序存放

A[m][n]中a[i][j]位置：
k= j*m+i

Loc(aij)=Loc(a00)+(j*m+i)*l

a00

a10

......

a m-1 0

a01

a11

......

a m-1 1

......

a0n-1

a1n-1

......

a m-1 n-1

(m-1)*(n-1)