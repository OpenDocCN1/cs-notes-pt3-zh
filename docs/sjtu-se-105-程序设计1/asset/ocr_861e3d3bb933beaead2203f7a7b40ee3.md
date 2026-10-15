+   - 我们来跟踪计算2的阶乘的调用情况：
+     - 对比两个版本

新版本

旧版本

```
factorial(2)
→ fact_helper(2, 1)
→ fact_helper(1, 2)
→ fact_helper(0, 2)
← 2
← 2
← 2
```

```
factorial(2)
→ 2 * factorial(1)
→ 1 * factorial(0)
← 1
← 1*1 (==1)
← 2*1 (==2)
← 2
```