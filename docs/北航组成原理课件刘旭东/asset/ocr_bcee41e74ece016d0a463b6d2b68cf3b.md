# 2.2 8086/8088指令系统·寄存器

# ❖ 指令指针IP（Instruction Pointer）

+   - IP（16 bits）指向代码段中下一条要执行的指令。
+   - CS:IP 形成下一次要执行的指令的内存地址。

# ❖ 标志寄存器FLAGS（Flags Register）

+   - 16位，记录当前CPU运行程序的各种状态
+   - 进位标志位 CF（Carry Flag）
+   - 奇偶标志位 PF（Parity Flag）
+   - 辅助进位标志位 AF（Auxiliary Flag）
+   - 零值标志位 ZF（Zero Flag）
+   - 符号标志位 SF（Sign Flag）
+   - 溢出标志位 OF（Overflow Flag）
+   - 单步跟踪标志位 TF（Trace Flag）
+   - 中断允许标志位 IF（Interrupt-enable Flag）
+   - 方向标志位 DF（Direction Flag）

![](bbox=[0.09, 0.846, 0.892, 0.958])