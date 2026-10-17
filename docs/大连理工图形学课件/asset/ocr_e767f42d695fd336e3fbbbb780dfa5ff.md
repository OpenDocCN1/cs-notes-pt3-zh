# # 相对任一参考点的二维几何变换

# ## 例1. 相对点\((x_F, y_F)\)的旋转变换

\(T_{RF} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ -x_F & -y_F & 1 \end{bmatrix} \cdot \begin{bmatrix} \cos\theta & \sin\theta & 0 \\ -\sin\theta & \cos\theta & 0 \\ 0 & 0 & 1 \end{bmatrix} \cdot \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ x_F & y_F & 1 \end{bmatrix}\)

\(= \begin{bmatrix} \cos\theta & \sin\theta & 0 \\ -\sin\theta & \cos\theta & 0 \\ x_F - x_F \cos\theta + y_F \sin\theta & y_F - y_F \cos\theta - x_F \sin\theta & 1 \end{bmatrix}\)