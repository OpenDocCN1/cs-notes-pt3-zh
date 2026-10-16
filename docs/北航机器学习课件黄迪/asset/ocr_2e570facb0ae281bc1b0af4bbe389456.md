# 核主成分分析

# Kernel PCA

将主成分分析的线性假设一般化使之适应非线性数据

传统PCA： D维样本 {x_n}, n = 1,2,...,N, Σ_n x_n = 0

S u_i = λ_i u_i   S = 1/N Σ_{n=1}^N x_n x_n^T   u_i^T u_i = 1

核PCA： 非线性映射 φ(x), x_n ⟼ φ(x_n), Σ_n φ(x_n) = 0

C v_i = λ_i v_i   C = 1/N Σ_{n=1}^N φ(x_n) φ(x_n)^T

1/N Σ_{n=1}^N φ(x_n) { φ(x_n)^T v_i } = λ_i v_i

v_i = Σ_{n=1}^N a_{in} φ(x_n)