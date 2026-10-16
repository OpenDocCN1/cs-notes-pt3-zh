P(t) = \sum_{i=0}^n P_i B_{i,n}(t)

二次 Bézier 曲线的表达形式为：

P(t) = (1-t)^2·P_0 + 2t(1-t)·P_1 + t^2·P_2, 0 ≤ t ≤ 1

写成矩阵形式，则为

P(t) = [t^2 t 1] \begin{bmatrix} 1 & -2 & 1 \ -2 & 2 & 0 \ 1 & 0 & 0 \end{bmatrix} \begin{bmatrix} P_0 \ P_1 \ P_2 \end{bmatrix}

当 t=1/2 时，二次 Bézier 曲线上的点为

P(1/2) = 1/4 P_0 + 1/2 P_1 + 1/4 P_2 = 1/2 [P_1 + 1/2 (P_0 + P_2)]