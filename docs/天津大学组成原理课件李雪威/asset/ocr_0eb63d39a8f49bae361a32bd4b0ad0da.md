# # Optimization Blocker: Procedure Calls

+   - **Why couldn't compiler move `strlen` out of inner loop?**
+     - Procedure may have side effects
+       - Alters global state each time called
+     - Function may not return same value for given arguments
+       - Depends on other parts of global state
+       - Procedure `lower` could interact with `strlen`

+   - **Warning:**
+     - Compiler treats procedure call as a black box
+     - Weak optimizations near them

+   - **Remedies:**
+     - Use of inline functions
+       - GCC does this with `-O1`
+         - Within single file
+     - Do your own code motion

```
```c
size_t lencnt = 0;
size_t strlen(const char *s)
{
    size_t length = 0;
    while (*s != '\0') {
        s++; length++;
    }
    lencnt += length;
    return length;
}
```
```

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

16