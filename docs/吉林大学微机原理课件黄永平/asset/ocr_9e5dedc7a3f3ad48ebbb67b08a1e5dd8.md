# 3) 中断返回

# IRET

; IP ← Stack , SP ← SP +2 (IP出栈)
CS ← Stack , SP ← SP +2 (CS出栈)
FR ← Stack , SP ← SP +2 (FR出栈)
从中断服务子程序返回

+   Pop from stack:
+   - IP
+   - CS
+   - flags register