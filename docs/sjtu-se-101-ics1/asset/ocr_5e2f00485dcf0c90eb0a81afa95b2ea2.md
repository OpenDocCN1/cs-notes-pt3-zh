# Arithmetic and Logical Operations

Instruction Code
Function Code

# Add

```
addl rA, rB 6 0 rA rB
```

# Subtract (rA from rB)

```
subl rA, rB 6 1 rA rB
```

# And

```
andl rA, rB 6 2 rA rB
```

# Exclusive-Or

```
xorl rA, rB 6 3 rA rB
```

+   - Refer to generically as "OP1"
+   - Encodings differ only by "function code"
+     - Low-order 4 bites in first instruction word
+   - Set condition codes as side effect
+   - Notice: no multiply or divide operation