# 2.6.2 Arithmetic Instructions

# Multiplication and Division

# Unsigned Multiplication

```
MUL SRC
```

# Signed Multiplication

```
IMUL SRC
```

The product after a multiplication is always a double-width product.

This instruction have an affect on CF and OF

+   - CF=OF=1: indicates that the high order half of the product is not zero

+   - CF=OF=0: indicates that the high order half of the product is zero

+   - No meaning on changing other flags