# Compiler

![](bbox=[0.014, 0.089, 0.982, 0.589])

$$ADR = LOC + \sum_{i=1}^{n}[V(i)-L(i)]\times P(i)\times E$$

其中

$$P(i)=\begin{cases}1,& 当\ i=n时\\[4pt]\displaystyle\prod_{j=i+1}^{n}[U(j)-L(j)+1],& 当\ 1\leq i<n\ 时\end{cases}$$

大小（字节数）