![](bbox=[0.0, 0.05, 0.125, 0.55])

```
A1 <= &Lock; （将Lock单元地址送A1寄存器。Lock单元初始值为0）
Loop: T&S  R1, A1;
    JRN R1, Loop;  (If (R1=1) then goto Loop )
```

# 临界段

```
A1  <= &Lock;
(A1) <=0; (0置Lock内存单元)
```

# 非临界段