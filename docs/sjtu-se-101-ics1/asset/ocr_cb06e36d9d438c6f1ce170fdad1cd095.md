# Conditional Move

**(c) Generated assembly code**

*(x at %ebp+8, y at %ebp+12)*

+   1. `movl 8(%ebp), %ecx`    *Get x*
+   2. `movl 12(%ebp), %edx`    *Get y*
+   3. `movl %edx, %ebx`    *Copy y*
+   4. `subl %ecx, %ebx`    *Compute y-x*
+   5. `movl %ecx, %eax`    *Copy x*
+   6. `subl %edx, %eax`    *Compute x-y and set as return value*
+   7. `cmpl %edx, %ecx`    *Compare x:y*
+   8. `cmovl %ebx, %eax`    *If <, replace return value with y-x*

| Register | Value |
|---|---|
| `%ecx` | x |
| `%edx` | y |
| `%ebx` | y-x |
| `%eax` | x-y |