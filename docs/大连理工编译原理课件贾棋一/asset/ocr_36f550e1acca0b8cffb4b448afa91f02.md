# 3.3 自上而下分析

# 3.3.3 递归下降的预测分析

+   - 为每一个非终结符写一个分析过程
+   - 这些过程可能是递归的

例：

```
type → simple
    | ↑ id
    | array [simple] of type
simple → integer
       | char
       | num dotdot num
```