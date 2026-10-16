# 30.3.1 An iterative FFT implementation

```
RECURSIVE-FFT(a)
1  n = a.length
2  if n == 1
3      return a
4  ωₙ = e^(2πi/n)
5  ω = 1
6  a^[0] = (a₀, a₂, ..., aₙ₋₂)
7  a^[1] = (a₁, a₃, ..., aₙ₋₁)
8  y^[0] = RECURSIVE-FFT(a^[0])
9  y^[1] = RECURSIVE-FFT(a^[1])
10 for k = 0 to n/2 − 1
11     yₖ = yₖ^[0] + ω yₖ^[1]
12     yₖ₊(n/2) = yₖ^[0] − ω yₖ^[1]
13     ω = ω ωₙ
14 return y
```

![](bbox=[0.48, 0.27, 0.88, 0.48])

y_k^[0] → • → + → y_k^[0] + ω_n^k y_k^[1]  y_k  (k = 0,1,...,n/2 −1)
ω_n^k →
 y_k^[1] → • → − → y_k^[0] − ω_n^k y_k^[1]  y_{k+n/2}

butterfly operation
adding and subtracting t from y_k^[0]

```
for k = 0 to n/2 − 1
    t = ω y_k^[1]
    y_k = y_k^[0] + t
    y_{k+(n/2)} = y_k^[0] − t
    ω = ω ω_n
```