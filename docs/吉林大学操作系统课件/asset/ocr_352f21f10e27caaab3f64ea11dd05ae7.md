# 管程实现SCAN算法

```
Procedure initialize;
    Var I: 0..199;
    Begin
        busy:=false;
        headpos:=0;
        direction:=up;
        For I:=0 To 199 Do
            count[I]:=0
    End
Begin initialize End;
```