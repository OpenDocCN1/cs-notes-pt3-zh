# Locality Example

```
sum = 0;
for (i = 0; i < n; i++)
    sum += a[i];
return sum;
```

+   - **Data references**
+     - Reference array elements in succession (stride-1 reference pattern).
+     - Reference variable `sum` each iteration.
+   - **Instruction references**
+     - Reference instructions in sequence.
+     - Cycle through loop repeatedly.

Spatial locality
Temporal locality
Spatial locality
Temporal locality