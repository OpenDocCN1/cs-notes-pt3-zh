# 右递归：

+   1. E↑x → E↑q A↓q
+   2. A↓q → + T↑r @ADD↓q,r,↑p A↓q
+   2. E↑x → T↑p
+   3. T↑x → T↑q * F↑r @MULT↓y,z,p
+   4. T↑x → F↑p
+   5. F↑x → (E↑p)
+   6. F↑x → Id↑p