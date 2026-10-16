# 1.1 指令系统概述

# 机器指令的要素

+   - 操作码(Operation Code): 指明进行的何种操作（如 ADD, MOV, I/O）
+   - 源操作数地址(Source Operand Reference): 参加操作的操作数的地址，可能有多个。
+   - 目的操作数地址(Destination Operand Reference): 保存操作结果的地址。
+   - 下一条指令的地址(Next Instruction Reference): 指明下一条要运行的指令的位置，一般指令是按顺序依次执行的，所以绝大多数指令中并不显示的指明下一条指令的地址，也就是说，指令格式中并不包含这部分信息。只有少数指令需要显示指明下一条指令的地址。