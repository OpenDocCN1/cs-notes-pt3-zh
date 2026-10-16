# 让我们想想那些数字

+   - 在命中和不命中之间差距巨大
+     - 如果只有L1和主存，那么可以差100倍

+   - 你会相信99%命中率要比97%好两倍？
+     - 思考：
+       缓存命中时间为1个周期
+       不命中处罚要100个周期
+     - 平均访问时间：
+       97% 命中率：1 周期 + 0.03 x 100 周期 = 4 周期
+       99% 命中率：1 周期 + 0.01 x 100 周期 = 2 周期

+   - 这就是为什么用“不命中率”而不是“命中率”

1) Improve the average access time
要提高平均访问速度，必须提高命中率！
α HIT RATIO: Fraction of refs found in CACHE.
(1-α) MISS RATIO: Remaining references.
t_avg = α t_c + (1-α)(t_c + t_m) = t_c + (1-α) t_m
2) Transparency (compatibility, programming ease)
Cache对程序员来说是透明的，以方便编程！