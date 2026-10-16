# 30.1.2 Point-value representation

• **polynomial representation**  
\(y=A(x)=\sum_{j=0}^{n-1}a_jx^j\)  
\(a=(a_0,a_1,\ldots,a_{n-1})^T\), column vectors  
\(\{(x_0,y_0),(x_1,y_1),\ldots,(x_{n-1},y_{n-1})\}\), a set of \(n\) point-value pairs

![](bbox=[0.158, 0.427, 0.901, 0.565])

# • Evaluation

+   - select \(n\) distinct points \(x_0,x_1,\ldots,x_{n-1}\),
+   - evaluate \(A(x_k)\) for \(k=0,1,\ldots,n-1\).
+   - the \(n\)-point evaluation takes time \(\Theta(n^2)\). (Horner method)
+   - if choose the \(x_k\) cleverly, the computation only needs \(\Theta(n\lg n)\).