# 4.2 8259A PIC

# ■ Operation and commands

# ◆ Operation Control Word 3 (OCW3)

# SMM operation

| A0 | D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
|---|---|---|---|---|---|---|---|---|
| 0 | × | ESMM | SMM | 0 | 1 | P | RR | RIS |

| ESMM | SMM | Function |
|---|---|---|
| 0 | × | No Action |
| 1 | 0 | Reset special mask |
| 1 | 1 | Set special mask |