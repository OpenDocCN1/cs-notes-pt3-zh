# 2.移位指令

HYPer

+   (1)逻辑左移指令 SHL d, count
+   (2)逻辑右移指令 SHR d, count
+   (3)算术左移指令 SAL d, count
+   (4)算术右移指令 SAR d, count

A-arithmetic
S,SH-shift
L-left
R-right

OF=0 if first operand keeps original sign

注：该指令影响标志位 CF, OF, SF, PF, ZF 视结果而定；最后一次移位后当最高有效位发生变化时(如1变0) OF=1，否则 OF=0。

![](bbox=[0.03, 0.62, 0.48, 0.82])

![](bbox=[0.52, 0.62, 0.97, 0.82])

![](bbox=[0.03, 0.82, 0.48, 1.0])

![](bbox=[0.52, 0.82, 0.97, 1.0])