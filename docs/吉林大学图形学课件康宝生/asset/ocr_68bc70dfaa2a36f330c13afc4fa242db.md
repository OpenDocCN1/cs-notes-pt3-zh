这样的节点矢量定义了分段 Bernstein 基函数，对应的 B 样条曲线称为 Bézier 曲线。选择该类型 B 样条曲线有一个限制：控制顶点个数减 1 必须等于曲线次数的整数值，即：

$$\frac{L+k-1}{k}=\text{正整数}$$

+   - 一般非均匀 B 样条曲线（General Non-Uniform B-spline Curve）

对于这种类型，任意分布的节点序列 $U:u_0\leq u_1\leq\cdots\leq u_{L+2k-1}\leq u_{L+2k}$，只要在数学上成立（节点序列非递减、