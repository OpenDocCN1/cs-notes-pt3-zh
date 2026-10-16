# A Faster Transitive Closure Alg.

```
procedure transClosure(M_R:rank-n 0-1 mat.)
  A := M_R;
  for i := 1 to ⌈log₂ n⌉ begin
    A := A ⊙ (A+I_n); {A represents ⋃_{j=1}^{2^{i+1}-1} R^i }
  end
  return A
  {Alg. takes only Θ(n³ log n) time!}
```

![](bbox=[0.78, 0.38, 0.86, 0.65])