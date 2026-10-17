# x86-64 Stack: Pop

+   - **popq Dest**
+     - Read value at address given by **%rsp**
+     - Increment **%rsp** by 8
+     - Store value at Dest (usually a register)

![](bbox=[0.59, 0.163, 0.98, 0.873])

(The memory doesn’t change, only the value of **%rsp**)