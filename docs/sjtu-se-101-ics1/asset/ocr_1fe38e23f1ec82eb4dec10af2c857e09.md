# Invoke Callee

+   - Instruction
+     - `call label` (direct)
+     - `call *operand` (indirect)
+   - Behavior description (by hardware)
+     - Save *return address* in the stack
+     - Jump to the *entry* of callee
+   
+   call = push + jmp

```
push retaddr
jmp callee
```