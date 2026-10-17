# # Registers for procedure calling

+   - $a0 ~ $a3: four argument registers to pass parameters
+   - $v0 ~ $v1: two value registers to return values
+   - $ra: one return address register to return to origin point

# # Instruction for procedures: jal ( jump-and-link )

Caller jal ProcedureAddress
Callee jr $ra

# # Using more registers

+   - Stack: ideal data structure for spilling registers
+     - Push, pop
+     - Stack pointer ( $sp )

![](bbox=[0.788, 0.615, 0.962, 0.919])