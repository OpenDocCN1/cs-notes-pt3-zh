# # The values of the stack pointer and stack before, during and after procedure call in Example 2.15

![](bbox=[0.05, 0.145, 0.95, 0.735])

+   - Conflict over the use of register both
+   - Push all the registers to stack
+     - Caller: pushes $a0~$a3 or $t0~$t9
+     - Callee: pushes $ra (return address) and $s0~$s7