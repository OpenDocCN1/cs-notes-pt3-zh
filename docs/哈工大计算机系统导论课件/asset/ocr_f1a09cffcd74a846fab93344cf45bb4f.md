# 循环展开 & 累加

+   **设想Idea**
+   - 能循环展开到任一程度 L吗？
+   - 能够并行累加K个结果吗？ Can accumulate K results in parallel
+   - L一定要乘以 K
+   
+   **限制**
+   - 效果/收益递减 Diminishing returns
+     - 不能超出执行单元的吞吐量限制
+   - 片段的大的经常开销 Large overhead for short lengths
+     - 顺序地完成循环