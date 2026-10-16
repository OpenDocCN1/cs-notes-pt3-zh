# 翻译方案

# 布尔表达式的文法

+   - E→E₁ or M E₂
+   - E→E₁ and M E₂
+   - E→not E₁
+   - E→(E₁)
+   - E→id₁ relop id₂
+   - E→true
+   - E→false
+   - M→ε

# 标记非终结符号M

+   - 标识布尔表达式E₂的开始位置
+   - 用属性M.quad记录其所标识的布尔表达式的第一条三地址语句的地址
+   - 相应于产生式M→ε的动作：
+     M.quad=nextquad