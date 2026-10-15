# Understanding Translation Example

| `addq $1, %rdx` | `addq $1, %rdx.0` → `%rdx.1` |
|---|---|

+   - Register `%rdx` changes on each iteration
+   - Renamed as `%rdx.0`, `%rdx.1`, `%rdx.2`, ...