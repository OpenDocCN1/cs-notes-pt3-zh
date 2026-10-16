# Test and Set Instruction

+   - Test and modify the content of a word atomically

```
boolean TestAndSet ( boolean *target ) {
    boolean rv = *target;
    *target = TRUE;

    return rv;
}
```