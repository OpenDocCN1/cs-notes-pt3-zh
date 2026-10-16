# 4.3 Interrupt in x86 System

# Interrupt and Exception Classification

+   Software-Generated Interrupts
+   Common interrupt instruction

| Vector number | function | Vector number | function |
|---|---|---|---|
| 10H | Video service | 13H | Disk control |
| 14H | COM | 15H | IO Peripheral |
| 16H | keyboard | 17H | LPT |
| 20H | Return to DOS | 21H | DOS system calls |
| 23H | Ctrl+Break | 24H | DOS serious error |
| 33H | Mouse | 2FH | DOS Protected mode interface |
|  |  | 31H |  |