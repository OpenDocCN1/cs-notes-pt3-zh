# # Assembled instructions and their addresses:

| add   | 80000 | 0   | 19   | 19   | 9   | 0   | 32   | Loop:   |
|-------|-------|-----|------|------|-----|-----|------|---------|
| add   | 80004 | 0   | 9    | 9    | 9   | 0   | 32   |         |
| add   | 80008 | 0   | 9    | 22   | 9   | 0   | 32   |         |
| Lw    | 80012 | 35  | 9    | 8    |     | 0   |      |         |
| bne   | 80016 | 5   | 8    | 21   |     | 2   | (8)  |         |
| add   | 80020 | 0   | 19   | 20   | 19  | 0   | 32   |         |
| j     | 80024 | 2   |      |      | 20000 |     | (80000) | Exit:   |
|       | 80028 | ... |      |      |     |     |      |         |

80028 - 80020 = 8

PC+4+offset=80028

# # Modification:

+   - All MIPS instructions are 4 bytes long

+   - PC-relative addressing refers to the number of words

+   - The address field at 80016 above should be 2 instead of 8

2.9 MIPS Addressing for 32-Bit Immediate and Addresses