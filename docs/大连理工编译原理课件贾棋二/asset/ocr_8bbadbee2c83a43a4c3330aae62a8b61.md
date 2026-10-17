# # 例 题 4

假定使用(a)值调用；(b)引用调用；(c)复写—恢复调用；(d)换名调用。下面程序打印的结果是什么。

```
```pascal
program main(input,output);
var a,b: integer;
procedure p(x,y,z: integer);
begin
    y:=y+1 ;
    z:=z+x;
end;
begin
    a:=2;
    b:=3;
    p(a+b,a, a) ;
    print a;
end.
```
```