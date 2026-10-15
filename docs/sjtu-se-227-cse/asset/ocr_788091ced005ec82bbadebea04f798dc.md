# Before-or-After Atomicity

+   - **volatile int in;**
+   - Works on 32 and 64 bit machines
+     ```
+     mov in, %eax
+     add $0x1, %eax
+     mov %eax, in
+     ```