# Before-or-After Atomicity

+   - **volatile long long int in;**
+   - Works only on 64bit machines, not 32bit

```
mov in, %eax
mov in+4, %edx
add $0x1, %eax
adc $0x0, %edx
mov %eax, in
mov %edx, in+4
```