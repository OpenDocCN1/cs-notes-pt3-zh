# 例：将下列表达式翻译成四元式序列。

X*2+A*(i+1)/(j+1)

其中i和j为整型变量，其它为实型变量。

+   1. (FLOAT, 2, _, t₁)
+   2. (MULTF, X, t₁, t₂)
+   3. (ADDI, i, 1, t₃)
+   4. (FLOAT, t₃, _, t₄)
+   5. (MULTF, A, t₄, t₅)
+   6. (ADDI, j, 1, t₆)
+   7. (FLOAT, t₆, _, t₇)
+   8. (DIVF, t₅, t₇, t₈)
+   9. (ADDF, t₂, t₈, t₉)