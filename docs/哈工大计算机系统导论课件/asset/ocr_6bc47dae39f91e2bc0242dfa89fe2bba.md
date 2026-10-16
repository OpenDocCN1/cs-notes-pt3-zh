# 非规格化数

v = (-1)^S M 2^E
E = 1 - Bias

+   - 条件: exp = 000...0
+     - 阶码(Exponent)值: E = 1 - Bias (instead of E = 0 - Bias)
+     - 尾数(Significand)编码隐含先导数值0: M = 0.xxx...x2
+       - xxx...x:是 frac 字段的数码

+   - 情况2: exp = 000...0, frac ≠ 000...0
+     - 最接近0.0的那些数
+     - 间隔均匀

![](bbox=[0.38, 0.47, 0.96, 0.88])

(-1)^S × 0.xx...x × 2^-126