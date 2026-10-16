```
P_j(t) = \sum_{i=0}^{2} b_{2j+i} B_{i,2}(t)
```

```
= \left[ t^2 \ t \ 1 \right] \left[ \begin{matrix} 1 & -2 & 1 \\ -2 & 2 & 0 \\ 1 & 0 & 0 \end{matrix} \right] \left[ \begin{matrix} b_{2j} \\ b_{2j+1} \\ b_{2j+2} \end{matrix} \right], \ 0 \leq t \leq 1, \ j=0,1,\cdots,n-2
```

因同一曲线段的两种不同表示形式可以相互转换，所以有以下关系：

```
\left[ t^2 \ t \ 1 \right] \frac{1}{2} \left[ \begin{matrix} 1 & -2 & 1 \\ -2 & 2 & 0 \\ 1 & 1 & 0 \end{matrix} \right] \left[ \begin{matrix} d_j \\ d_{j+1} \\ d_{j+2} \end{matrix} \right] = \left[ t^2 \ t \ 1 \right] \left[ \begin{matrix} 1 & -2 & 1 \\ -2 & 2 & 0 \\ 1 & 0 & 0 \end{matrix} \right] \left[ \begin{matrix} b_{2j} \\ b_{2j+1} \\ b_{2j+2} \end{matrix} \right]
```