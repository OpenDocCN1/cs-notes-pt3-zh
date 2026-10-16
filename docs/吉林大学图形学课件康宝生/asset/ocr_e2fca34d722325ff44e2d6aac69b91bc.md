Step3. 用 B 样条曲线计算的 deBoor-Cox 递推公式计算曲线 D(u)。

Step4. 以坐标原点为投影中心、超平面 ω = 1 为投影平面，对 D(u) 做投影变换，即得 NURBS 曲线 R(u)：

R(u) = \frac{\sum_{i=0}^{n} \omega_i d_i N_{i,k}(u)}{\sum_{i=0}^{n} \omega_i N_{i,k}(u)}