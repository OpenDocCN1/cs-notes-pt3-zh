# Example: The do_brk() Bug

```
Asmlinkage unsigned long sys_brk(unsigned long brk) {
...
/* OK, looks good – let it rip. */
-if (do_mmap(NULL, oldbrk, newbrk-oldbrk,
-PRO T_READ|PROT_WRITE|PROT_EXEC,
-MAP_FIXED|MAP_PRIVATE, 0) != oldbrk)
+if (do_brk(oldbrk, newbrk-oldbrk) != oldbrk)
goto out;
```

+   - do_mmap() checked things properly, do_brk() removed almost all checking
+   - Purpose of do_brk() was to speed up anonymous mmap s from sys_brk()