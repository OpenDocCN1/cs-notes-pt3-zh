# 如何计算当前过程的变量访问环境

情况1

```
PROC P;
... ...
Begin
  P
End
```

情况2

```
PROC Q;
Begin
...
end
... ...
PROC P;
Begin
Q
End
```

情况3

```
PROC P;
... ...
PROC Q
Begin   End
... ...
Begin Q End
```

情况4

```
PROC Q;
... ...
PROC P;
Begin Q
End
Begin   End
```

情况3： P调用Q ,P层数(N-1)小于Q层数(N).（P是Q的直接外层才允许此种调用）
DeclaChain(P) = (M, P₁, P₂, …, Pₙ₋₂, P)
DeclaChain(Q) = (M, P₁, P₂, …, Pₙ₋₂, P , Q)