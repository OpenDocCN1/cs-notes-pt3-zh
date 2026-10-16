实现时，将定义式 A.a:=f(X.x, Y.y, Z.z) (抽象)变成 val[ntop]:=f(val[top-2], val[top-1], val[top]) (具体可执行代码)。

在执行代码段之前执行：
    ntop:=top-r+1 ——r是句柄的长度
执行代码段后执行： top:=ntop;

![](bbox=[0.05, 0.08, 0.97, 0.48])