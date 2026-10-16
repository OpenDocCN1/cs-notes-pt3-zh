例：有过程M, Q, R, S, 其中 level(M)=0; level(Q)=1; level(R)=1; level(S)=2, AR(S)的Display表如下：

AR(M)
Z单元
ar0
ar0
NULL

AR(Q)
ar1
ar0
ar1
ar0

AR(R)
Y单元
ar2
ar0
ar2
ar1

AR(S)
X单元
sp
ar2
ar0
ar2

Display
表
Off-Display

addr(X)=sp+off
addr(Y)=sp+D+(Ly-1)+off
addr(Z)=sp+D+(Lz-1)+off

sp