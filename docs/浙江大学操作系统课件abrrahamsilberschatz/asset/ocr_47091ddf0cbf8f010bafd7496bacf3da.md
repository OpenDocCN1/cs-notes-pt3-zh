# # Dual-Mode Operation (Cont.-1)

2. Monitor mode (also kernel mode or system mode or supervisor) – All instructions can be issued, execution done on behalf of operating system.
管态（核心态或系统态）-所有指令能使用，为操作系统做的执行

+   - Mode bit added to computer hardware to indicate the current mode: monitor (0) or user (1). 计算机硬件中增加状态位，指示正确的状态：管态（0）或用户态（1）

+   - When an interrupt or fault occurs hardware switches to monitor mode. 当中断或错误出现，硬件切换至管态