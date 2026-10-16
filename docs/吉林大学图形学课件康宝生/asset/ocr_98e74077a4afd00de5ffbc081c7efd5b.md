$$\begin{bmatrix} x_{i+1} \\ y_{i+1} \end{bmatrix} = \begin{bmatrix} 1 - \dfrac{\alpha^2}{2} & -\alpha \\ \alpha & 1 - \dfrac{\alpha^2}{2} \end{bmatrix} \begin{bmatrix} x_i - x_c \\ y_i - y_c \end{bmatrix} + \begin{bmatrix} x_c \\ y_c \end{bmatrix}$$

当然，这种方法不能精确地求出圆内接多边形的顶点，取得越小，误差就越小。