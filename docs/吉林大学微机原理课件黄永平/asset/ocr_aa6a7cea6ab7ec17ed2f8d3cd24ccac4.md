# 4)段间间接调用指令(远过程)

# CALL DWORD PTR d2

; SP ← SP − 2, Stack ← CS (CS入栈)

SP ← SP − 2 , Stack ← IP (IP入栈)

IP ← M[d2]

CS← M[d2+2]

d2=M1,2,3,4寻址， M中的连续4个单元中的内容送IP， CS

![](bbox=[0.62, 0.52, 0.92, 0.72])

CALL DWORD PTR[BX]

+   • 段间间接转移 JMP DWORD PTR d2的区别？