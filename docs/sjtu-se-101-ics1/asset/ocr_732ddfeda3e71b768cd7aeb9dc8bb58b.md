# Conditional Move Operations

```
cmovle rA, rB 2 1 rArB
```

- Refer to generically as "cmovXX"

```
cmovl rA, rB 2 2 rArB
```

- Share the same "instruction code"

```
cmove rA, rB 2 3 rArB
```

with rrmovl

```
cmovne rA, rB 2 4 rArB
```

- Encodings differ only by "function code"

```
cmovge rA, rB 2 5 rArB
```

```
cmovg rA, rB 2 6 rArB
```

+   - Based on values of condition codes
+   - Same as IA32 counterparts