# 例. 单一资源管理

```
Procedure release;
    Begin
        busy:=false;
        signal(q);
    End;
```

```
Begin busy:=false End;
```

```
Var lp,tape:single_resource;
```

lp: Busy q

Tape: Busy q

申请lp: lp.require

释放lp: lp.release

申请tape: tape.require;

释放tape: tape.release