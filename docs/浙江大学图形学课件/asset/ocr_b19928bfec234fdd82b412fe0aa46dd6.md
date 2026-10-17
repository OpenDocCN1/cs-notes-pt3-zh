# This set simultaneous of equations can be written in matrix form:

$$\begin{bmatrix}
1-R_1F_{11} & -R_1F_{12} & \cdots & -R_1F_{1n} \\
-R_2F_{21} & 1-R_2F_{22} & \cdots & -R_2F_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
-R_nF_{n1} & -R_nF_{n2} & \cdots & 1-R_nF_{nn}
\end{bmatrix}
\begin{bmatrix}B_1\\B_2\\\vdots\\B_n\end{bmatrix}
=
\begin{bmatrix}E_1\\E_2\\\vdots\\E_n\end{bmatrix}$$

$E_i$ is non-zero only for patches of light sources

$R_i$ is the reflectivity of the patch

$F_{ij}$ is the form factor which can be calculated

+   - The matrix equation is solved to calculate $B_i$'s