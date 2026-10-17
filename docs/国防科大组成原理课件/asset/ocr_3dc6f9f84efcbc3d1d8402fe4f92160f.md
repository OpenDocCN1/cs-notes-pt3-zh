# 进位逻辑

+   - 串行进位延迟太长
+   - 分析进位的生成过程

c_{i+1} = a_i & b_i | a_i & c_i | b_i & c_i
= a_i & b_i | (a_i | b_i) & c_i
= g_i | p_i & c_i

记 g_i = a_i & b_i 进位生成因子 (g=1则c_{i+1}输出为1)
p_i = a_i | b_i 进位传递因子 (p=1则c_{i+1}输出为c_i输入)