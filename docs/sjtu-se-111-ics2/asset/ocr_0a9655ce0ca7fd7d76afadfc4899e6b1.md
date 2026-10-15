# Control Combinations

Load/use
M
E Load
D Use

Mispredict
M
E JXX
D

ret1
M
E
D ret

ret2
M
E ret
D bubble

ret3
M ret
E bubble
D bubble

Combination A

Combination B

+   - Special cases that can arise on same clock cycle

+   - Combination A
+     - Not-taken branch
+     - ret instruction at branch target

+   - Combination B
+     - Instruction that reads from memory to %esp
+     - Followed by ret instruction