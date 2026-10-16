# 1) 软中断

# INT n

机器码
CD n

;SP ← SP − 2 ; Stack ← FR (Flag入栈);

IF← 0; TF←0 (清I---关中断，清T);

1.处理Flag

SP ← SP − 2 ; Stack ← CS (CS入栈);

SP ← SP − 2 ; Stack ← IP (IP入栈);

2.断点入栈

IP← [n x 4];

CS← [n x 4 + 2]

3.跳转到中断服务子程序

中断向量表(中断服务子程序入口地址表)
中断类型码n(上表中每项的编号0~255)

PC机:
n=0~4 系统专用
08H ~ 0FH ——硬件中断
10h~1Fh BIOS用
20H ~ 3FH —— DOS 用
40H ~ FFH ——用户用

+   - Push to stack:
+     flags register
+     CS
+     IP
+   - IF = 0 TF=0
+   - Transfer control to interrupt procedure