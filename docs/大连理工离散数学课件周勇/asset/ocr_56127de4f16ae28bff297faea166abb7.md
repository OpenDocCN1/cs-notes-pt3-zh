# # 量词

+   - 量词本身不是一个独立的逻辑概念，可以用 \(\wedge, \vee\) 联结词取代。
+   
+   - 设个体域 \( S: S = \{a_1, a_2, \cdots, a_n\} \)
+   谓词可以表示成以下形式：
+   
+     \((\forall x)A(x) \iff A(a_1) \wedge A(a_2) \wedge \cdots \wedge A(a_n)\)
+   
+     \((\exists x)A(x) \iff A(a_1) \vee A(a_2) \vee \cdots \vee A(a_n)\)
+   
+     \((\exists! x)A(x) \iff (\exists c)((\forall x)(A(x) \iff (x = c)))\)
+   
+   - 由量词确定的命题真值与个体域有关。
+   
+     - 令 \( P(x): x \) 是素数
+   
+     - 则 \(\forall x P(x)\)，如果取个体域为素数集，为真；
+       如果个体域为整数集，为假。