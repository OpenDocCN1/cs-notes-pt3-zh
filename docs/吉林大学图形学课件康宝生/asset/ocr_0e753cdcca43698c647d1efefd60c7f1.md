$$E_{i+1}^T = A^{i+1}E_0^T = U[BU^{-1}UBU^{-1}\cdots UB]U^{-1}E_0^T = UB^{i+1}U^{-1}E_0^T = U\begin{bmatrix}\lambda_1^{i+1} & 0 \\ 0 & \lambda_2^{i+1}\end{bmatrix}U^{-1}E_0^T$$

由于 $||\lambda_1|| = ||\lambda_2|| = 1$，所以存在一个和 $i$ 无关的常数 $C$ 作为各元素模的上界。因而，由上式可得：

$$||E_{i+1}|| \le C||E_0||$$

其中，$||\cdot||$ 是任何一种向量范数，如 $||E_0|| = \max(|e_{0x}|,\ |e_{0y}|)$，或