# 图形化编程实例

+   - CalculatorGUI
+     - 负责从图形化界面接受用户的输出
+     - 将表达式字符串组装成Token-stream对象并传递给Calculator处理

+   - Calculator负责表达式计算
+     - 接受Token_stream对象
+     - 封装所有计算器的计算功能
+     - 通过对第6、7章程序改造而得到

+   - Token_stream需要改造
+     - 从CalculatorGUI接受一个字符串流
+     - 从该字符串流而不是cin读入Token对象