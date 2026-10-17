+   - While branch target is far away
+     - Inserts an unconditional jump to target
+     - Invert the condition so that the branch decides whether to skip the jump

# Example 2.21  **Branching far away**

+   - Given a branch:
+   
+     `beq  $s0, $s1, L1`
+   
+   - Rewrite it to offer a much greater branching distance:
+   
+     `bne  $s0, $s1, L2`
+   
+     `j    L1`
+   
+     `L2:`