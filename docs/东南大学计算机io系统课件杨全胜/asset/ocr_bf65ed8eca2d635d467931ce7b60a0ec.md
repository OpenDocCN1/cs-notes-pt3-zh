# 2.3 Directives

# Data define

# Declaring and Referencing Arrays

+   - Array elements occupy memory contiguously, so a program references each element relative to the start of the array.

+   - To declare an array, supply a label name, the element type, and a series of initializing values or ? placeholders.

```
warray WORD 1, 2, 3, 4
xarray DWORD 0FFFFFFFFh, 789ABCDEh
var1 BYTE 10, 20, 30
    BYTE 40, 50, 60
    BYTE 70, 80, 90
sarray WORD ?, 40, ?
```