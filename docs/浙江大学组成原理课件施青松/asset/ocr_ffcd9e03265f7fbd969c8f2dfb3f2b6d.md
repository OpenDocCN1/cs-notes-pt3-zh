# Simple Questions

+   - How many cycles will it take to execute this code? (1–2)
+   
+     ```asm
+     lw $t2, 0($t3)
+     lw $t3, 4($t3)
+     beq $t2, $t3, Label     #assume not
+     add $t5, $t2, $t3
+     sw $t5, 8($t3)
+     ```
+   
+     Label1:  ...

+   - What is going on during the 8th cycle of execution?
+     - Answer: Calculating memory address

+   - In what cycle does the actual addition of $t2 and $t3 takes place?
+     - No. 16

![](bbox=[0.12, 0.823, 0.867, 0.863])