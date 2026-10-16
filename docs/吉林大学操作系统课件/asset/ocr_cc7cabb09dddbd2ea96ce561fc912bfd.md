# Level5 (块级分布式异或校验)

+   - 校验码计算：
+     - p4~7=block4 XOR block5 XOR block6 XOR block7
+   - 若block7发生故障，可通过下式恢复
+     - block7=p4~7 XOR block4 XOR block5 XOR block6