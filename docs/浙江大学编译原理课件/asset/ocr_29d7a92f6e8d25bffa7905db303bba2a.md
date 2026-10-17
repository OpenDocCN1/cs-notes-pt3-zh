# 3.5 extended notations: EBNF and syntax diagrams

+   - **Example:**
+   
+     `stmt-Sequence → stmt ; stmt-Sequence | stmt`
+   
+     `stmt → s`

+   - **In EBNF this would appear as**
+   
+     `stmt-sequence → { stmt ; } stmt`
+   
+     *(right recursive form)*
+   
+     `stmt-sequence → stmt { ; stmt}`
+   
+     *(left recursive form)*

![](bbox=[0.78, 0.667, 1.0, 0.999])

![](bbox=[0.0, 0.913, 0.096, 0.999])