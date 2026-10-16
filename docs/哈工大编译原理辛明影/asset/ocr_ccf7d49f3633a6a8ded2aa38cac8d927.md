# 10.1.5 归纳变量删除

```
i := m - 1
j := n
t1 := 4*n
v := a[t1]
t2 := 4 * i
t4 := 4 * j
```

```
t2 := t2 + 4
t3 := a[t2]
if t3 < v goto B2
```

```
t4 := t4 - 4
t5 := a[t4]
if t5 > v goto B3
```

```
if t2 >= t4 goto B6
```

```
a[t2] := t5
a[t4] := t3
goto B2
```

```
t14 := a[t1]
a[t2] := t14
a[t1] := t3
```

图10.7 归纳变量删除后的流图