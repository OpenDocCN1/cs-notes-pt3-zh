# # 解决项目集中冲突的方法

解决方法： 向前搜索一个输入符号a

+   - FOLLOW(S) = {#}
+   - FOLLOW(A) = {0,b}
+   - FOLLOW(B) = {0,a}
+   - 对于I2而言，若a=1，则应该执行S5；
+   - 若a ∈ FOLLOW(S)，则应用S→a.归约；
+   - 若a ∈ FOLLOW(A)，则应用A→. ε归约