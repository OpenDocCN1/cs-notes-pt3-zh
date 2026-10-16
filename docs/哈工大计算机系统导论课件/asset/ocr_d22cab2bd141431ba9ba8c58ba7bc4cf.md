# 为何用无符号数？

+   - 一定要知道隐含的转换规则，否则不要用
+     - 常见错误
+       ```
+       unsigned i;
+       for (i = cnt-2; i >= 0; i--)
+       a[i] += a[i+1];
+       ```
+     - 不易察觉的问题
+       ```
+       #define DELTA sizeof(int)
+       int i;
+       for (i = CNT; i - DELTA >= 0; i -= DELTA)
+       ...
+       ```