# # Complement & Increment Examples

x = 0

|    | Decimal | Hex   | Binary                        |
|---|---|---|---|
| 0  | 0       | 00 00 | 00000000 00000000             |
| ~0 | -1      | FF FF | 11111111 11111111             |
| ~0+1 | 0       | 00 00 | 00000000 00000000             |

x = TMin

|    | Decimal | Hex   | Binary                        |
|---|---|---|---|
| x  | -32768  | 80 00 | 10000000 00000000             |
| ~x | 32767   | 7F FF | 01111111 11111111             |
| ~x+1 | -32768  | 80 00 | 10000000 00000000             |

# # Canonical counter example