# 8254 command

| CS# | RD# | WR# | A1 | A0 | operation | CHB D₇D₆ | 时序 |
|---|---|---|---|---|---|---|---|
| 0 | 1 | 0 | 0 | 0 | initial count → CNT0 | ** | 无 |
| 0 | 1 | 0 | 0 | 1 | initial count → CNT1 | ** | 无 |
| 0 | 1 | 0 | 1 | 0 | initial count → CNT2 | ** | 无 |
| 0 | 1 | 0 | 1 | 1 | Write control word | 00~10 | 无 |
|  |  |  |  |  | Write “read back” command | 11 | 无 |
| 0 | 0 | 1 | 0 | 0 | Read CNT0 current count | - | See the explanation behind |
|  |  |  |  |  | Read status of CNT0 | - |  |
| 0 | 0 | 1 | 0 | 1 | Read CNT1 current count | - |  |
|  |  |  |  |  | Read status of CNT1 | - |  |
| 0 | 0 | 1 | 1 | 0 | Read CNT1 current count | - |  |
|  |  |  |  |  | Read status of CNT1 | - |  |
| 0 | 0 | 1 | 1 | 1 | - |  |  |
| 1 | * | * | * | * | Prohibit access |  |  |
| 0 | 1 | 1 | * | * | - |  |  |