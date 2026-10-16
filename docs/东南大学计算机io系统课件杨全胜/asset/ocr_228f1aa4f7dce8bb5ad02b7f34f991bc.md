# 2.6.1 Data Movement Instructions

# Load-Effective Address Instructions

```
LDS  reg16/32, mem32/48
LES  reg16/32, mem32/48
LFS  reg16/32, mem32/48
LGS  reg16/32, mem32/48
LSS  reg16/32, mem32/48
```

+   - Load any 16- or 32-bit register with an offset address and DS, ES, FS, GS, or SS segment register with segment address.

+   - Use any of memory-addressing modes to access a 32- or 48-bit section of memory that contains segment and offset address.