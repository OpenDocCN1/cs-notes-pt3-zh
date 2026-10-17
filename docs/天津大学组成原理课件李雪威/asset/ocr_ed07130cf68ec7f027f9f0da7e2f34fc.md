# # Counting Down with Unsigned

+   - Proper way to use unsigned as loop index
+   
+     ```c
+     unsigned i;
+     for (i = cnt-2; i < cnt; i--)
+         a[i] += a[i+1];
+     ```

+   - See Robert Seacord, *Secure Coding in C and C++*
+   
+     - C Standard guarantees that unsigned addition will behave like modular arithmetic
+   
+       - 0 − 1 → UMax

+   - Even better
+   
+     ```c
+     size_t i;
+     for (i = cnt-2; i < cnt; i--)
+         a[i] += a[i+1];
+     ```
+   
+     - Data type `size_t` defined as unsigned value with length = word size
+     - Code will work even if `cnt = UMax`
+     - What if `cnt` is signed and < 0?