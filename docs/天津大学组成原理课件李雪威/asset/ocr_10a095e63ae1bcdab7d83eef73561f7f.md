# # x86-64 Linux Register Usage #2

+   - %rbx, %r12, %r13, %r14
+     - Callee-saved
+     - Callee must save & restore
+   - %rbp
+     - Callee-saved
+     - Callee must save & restore
+     - May be used as frame pointer
+     - Can mix & match
+   - %rsp
+     - Special form of callee save
+     - Restored to original value upon exit from procedure

![](bbox=[0.488, 0.191, 0.977, 0.609])