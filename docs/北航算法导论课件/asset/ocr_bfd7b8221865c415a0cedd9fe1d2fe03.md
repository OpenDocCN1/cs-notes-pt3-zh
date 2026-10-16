# 30.1.3 Fast multiplication of polynomials

polynomial representation    $A(x)=\sum_{j=0}^{n-1} a_j x^j$

coefficient form
$a = (a_0, a_1, ..., a_{n-1})^T$

(DFT)
evaluation

interpolation
(inverse DFT)

point-value form
$\{(x_j, y_j)\}$

+   - We can use any points we want as evaluation points,
+   - but by choosing “complex roots of unity” as the evaluation points, we can convert between representations in only Θ(n lg n) time.〔选单位复数根作为求值点〕
+   - 30.2, FFT performs the DFT and inverse DFT operations in Θ(n lg n) time.