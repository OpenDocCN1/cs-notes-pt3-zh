# 2.6.3 Logic Instructions

# Shift and Rotate Instruction

# Rotate Instructions

Sent LSb of AL to the LSb of BL, keep the AL no changed.

```
ror bl,1
ror al,1
rcl bl,1
rol al,1
```

# Only affect OF and CF

+   - last bit shifted out goes to CF
+   - The OF flag is defined only for the 1-bit rotates; if the sign changed, OF=1