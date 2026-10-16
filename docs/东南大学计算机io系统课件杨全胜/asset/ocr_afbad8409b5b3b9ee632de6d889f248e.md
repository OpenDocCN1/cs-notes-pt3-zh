# 5.2 Structure and pins of 8254

# Operation and Command

# Initial count

The initial count for different counter must be write to different address.

| A1A0 | Timer/counter |
| 0 0 | T/C0 |
| 0 1 | T/C1 |
| 1 0 | T/C2 |

+   Write one byte by each time

+   The range of initial count is:

+   Binary: 65536(0000H)、65535(FFFFH)~1(0001H)。

+   BCD: 10000(0000H)、9999(9999H)~1(0001H)。