# Matrix Multiplication Algorithm

```
procedure matmul(matrices A: m×k, B: k×n)
for i := 1 to m
  for j := 1 to n begin
    c_ij := 0
    for q := 1 to k
      c_ij := c_ij + a_iq b_qj
end {C=[c_ij] is the product of A and B}
```

Θ(m)·

Θ(n)·

Θ(1)+

Θ(k)·

Θ(1))

What’s the Θ of its time complexity?

Answer:
Θ(mnk)