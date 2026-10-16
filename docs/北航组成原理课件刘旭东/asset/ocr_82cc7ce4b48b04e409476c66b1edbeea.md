# 1.1 CPU的功能与组成

# ❖ CPU内部的寄存器

+   - **通用寄存器（General Register）**：用户可见（汇编语言可使用）
+     - 数据寄存器、基址寄存器、变址寄存器、堆栈指针、标志寄存器等
+   - **控制与状态寄存器**：用户不可见，为系统控制专用。
+     - **MAR（Memory Address Register）**：存储器地址寄存器
+     - **MBR/MDR（Memory Buffer Register，Memory Data Register）**：存储器数据缓冲器
+     - **PC（Program Counter）**：程序计数器
+     - **IR（Instruction Register）**：指令寄存器
+   - **临时寄存器（Temporary Register）**：用户不可见