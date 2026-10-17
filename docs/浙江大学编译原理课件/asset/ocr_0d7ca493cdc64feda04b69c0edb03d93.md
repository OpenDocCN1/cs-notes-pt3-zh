# 6.2.2 Synthesized and inherited attributes

Example 6.14

+   - **the attributes needed to express the corresponding semantic:**
+     - `isFloat`: boolean, indicates if any part of an expression has a floating-point value (**synthesized**)
+     - `etype`: gives the type of each subexpression and depends on `isFloat` (**inherited**), here is int or float
+     - `val`: gives the numeric value of each subexpression, depends on `etype`.

![](bbox=[0.78, 0.663, 1.0, 1.0])

![](bbox=[0.0, 0.912, 0.099, 1.0])