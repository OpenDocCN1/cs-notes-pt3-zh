# 8.2 赋值语句的翻译

假设赋值语句出现的环境可用下面的文法描述：

+   - P→ M D; S
+   - M→ ε
+   - D→ D; D | D→ id: T | D→ proc id; N D; S
+   - N→ ε
+   - T→ integer | real | array [num] of T₁ | ↑T₁ | record D end
+   - S→ id:=E
+   - E→ E+E | E*E | -E | (E) | id