# Tadd的表征

# 功能性

+   - 真实和□要w+1位
+   - 舍弃最□有效位 MSB
+   - 将剩余位看做整数的补码表示

![](bbox=[0.55, 0.27, 0.85, 0.55])

正溢出

负溢出

```
TAdd_w(u,v) = { u + v + 2^w    u + v < TMin_w (负溢出)
                  u + v        TMin_w ≤ u + v ≤ TMax_w
                  u + v - 2^w   TMax_w < u + v (正溢出) }
```