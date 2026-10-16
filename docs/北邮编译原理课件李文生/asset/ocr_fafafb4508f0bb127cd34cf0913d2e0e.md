# 举例

+   - **MOV R₀, R₁**
+     - 将寄存器R₀的内容复制到R₁中
+     - 开销： 1
+   - **MOV R₅, M**
+     - 将寄存器R₅的内容放到存储单元M中
+     - 开销： 2
+   - **ADD #1, R₃**
+     - 将寄存器R₃的内容增加1
+     - 开销： 2
+   - **SUB 4(R₀), *12(R₁)**
+     - 将地址为(contents(12+contents(R₁))的单元中的值减去contents(4+contents(R₀))，结果仍存放到地址为(contents(12+contents(R₁))的单元中。
+     - 开销： 3