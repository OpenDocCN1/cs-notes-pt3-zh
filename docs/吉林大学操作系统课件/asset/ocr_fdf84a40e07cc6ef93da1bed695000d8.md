# 就餐条件测试

测试I号哲学家是否具备进食条件：

```
Procedure test(I:0..4)
    If (state[I]=hungry) and
        (state[(I-1)mod 5]<>eating) and
        (state[(I+1)mod 5]<>eating)
    Then state[I]:=eating; V(self[I])
```

Remark:

自测试不需要state[I]=hungry，但测试左邻右舍需要此条件。