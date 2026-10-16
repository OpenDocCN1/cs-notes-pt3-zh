# 4.标志寄存器传送指令

(1) 读取标志指令 LAHF ;AH← Flags 的低字节

![](bbox=[0.15, 0.28, 0.85, 0.45])

Load AH from 8 low bits of Flags register

(2) 设置标志指令 SAHF ;Flags 的低位字节← AH

![](bbox=[0.15, 0.58, 0.85, 0.75])

Store AH register in low 8 bits of Flags register

注：该指令影响标志位 Z、A、P、C