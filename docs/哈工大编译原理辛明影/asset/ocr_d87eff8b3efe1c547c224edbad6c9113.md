# 7.5.3 布尔表达式的控制流翻译

+   - 属性 (继承属性)
+     - B.true， B为真时控制到达的位置；
+     - B.false， B为假时控制到达的位置。

+   - a<b
+     - if a<b goto B.true
+     - goto B.false

+   - B→B₁ or B₂
+     - 如果B₁为真，则立即可知B为真，即B₁.true与B.true相同；
+     - 如果B₁为假，则必须计算B₂的值，令B₁.false为B₂的开始
+     - B₂的真假出口分别与B的真假出口相同