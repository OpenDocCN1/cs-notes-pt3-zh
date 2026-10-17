# Logical operations

# skip

# Logical shift operations

+   - right (srl)
+   - left (sll)

**Filled with '0'**

The machine instruction for the instruction
sll $t2, $s0, 3 (sll rd, rt, i)

| Op | Rs | Rt | Rd | Shamt | Adr/funct |
|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 16 | 10 | 3 | 0 |

Example: sll $t2, $s0, 3

+   - $s0: 0000 0000 0000 0000 1100 1000 0000 1111
+   - $t2: 0000 0000 0000 0110 0100 0000 0111 1000