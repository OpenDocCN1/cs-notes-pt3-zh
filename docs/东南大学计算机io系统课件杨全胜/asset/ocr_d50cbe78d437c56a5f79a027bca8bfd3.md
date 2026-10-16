# 4.2 8259A PIC

# Operation and commands

# Operation Control Word 2 (OCW2)

| R SL EOI 0 0 L2 L1 L0 | 功能 |
| 0 0 0 0 0 0 0 0 | AEOI; Fixed priority command |
| 0 0 1 0 0 0 0 0 | Non specific EOI; Fixed priority command |
| 0 1 1 0 0 L2 L1 L0 | Specific EOI; Fixed priority command |
| 1 0 0 0 0 0 0 0 | AEOI; Rotate in automatic priority command |
| 1 0 1 0 0 0 0 0 | Non specific EOI; Rotate in automatic priority command |
| 1 1 1 0 0 L2 L1 L0 | Specific EOI; Rotate on specific priority command |
| 1 1 0 0 0 L2 L1 L0 | AEOI; Rotate on specific priority command |

e.g. MOV AL, 20H
OUT 20H, AL ; in X86, What’s mean?