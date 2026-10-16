# 源语言的说明

+   - 声明部分的文法
+     P→ D; S
+     D→ D; D
+     D→ id: T
+     D→ proc id; D; S
+     T→integer | real
+     | array [num] of T₁
+     | ↑T₁
+     | record D end

+   - 所有名字必须先声明后引用

+   - 变量声明、每个声明语句声明一个名字

+   - 过程声明、过程声明允许嵌套