# 例. 单一资源管理

```
Type single_resource=MONITOR;
Var busy:boolean;
q:condition;
Define require,release;
Procedure require;
Begin
If busy Then
wait(q);
busy:=true
End;
```