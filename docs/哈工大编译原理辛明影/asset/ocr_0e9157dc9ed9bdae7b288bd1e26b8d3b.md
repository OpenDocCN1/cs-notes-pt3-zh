# 四、存贮管理

把源程序中的名字映射成运行时数据对象的地址是由前端和代码生成器共同完成的

![](bbox=[0.65, 0.01, 0.99, 0.35])

```
PROCEDURE sub(x, y:real);
VAR
    i , j:integer;
    a:ARRAY[1..5] OF real;
    e, f : real;
BEGIN
    ...
    f :=e+i*j;
    ...
END;
```