# LRU Approximation Algorithms Cont.

+   - **Second chance**（二次机会）
+     - **Need reference bit.**（需要访问位）
+     - **Clock replacement.**（时钟置换）
+     - If page to be replaced (in clock order) has reference bit = 1. Then（如果将要（以顺时针）交换的访问位是 1，则）：
+       - set reference bit 0（把访问位设位0）。
+       - leave page in memory（把页留在内存中）。
+       - replace next page (in clock order), subject to same rules（以同样的规则，替换下一个页）。