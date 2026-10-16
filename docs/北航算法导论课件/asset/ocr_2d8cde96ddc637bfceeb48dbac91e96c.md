# 30.2.4 Interpolation at the complex roots of unity

# DFT

$$y=\begin{pmatrix}y_0\\y_1\\\vdots\\y_{n-1}\end{pmatrix}=\begin{pmatrix}1&1&1&\cdots&1\\1&\omega_n^1&\omega_n^2&\cdots&\omega_n^{n-1}\\\vdots&\vdots&\vdots&\ddots&\vdots\\1&\omega_n^{(n-1)\cdot1}&\omega_n^{(n-1)\cdot2}&\cdots&\omega_n^{(n-1)\cdot(n-1)}\end{pmatrix}\begin{pmatrix}a_0\\a_1\\\vdots\\a_{n-1}\end{pmatrix}=V_n a$$

# inverse DFT

$$a=\mathrm{DFT}_n^{-1}(y)=V_n^{-1}y$$

☐ **Theorem 30.7**

**For $j,k=0,1,\ldots,n-1$, the $(j,k)$ entry of $V_n^{-1}$ is $\omega_n^{-kj}/n$.**