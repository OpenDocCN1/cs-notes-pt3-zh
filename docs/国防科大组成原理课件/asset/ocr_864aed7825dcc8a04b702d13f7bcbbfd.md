# MIPS的TLB及相关控制寄存器

+   - 32位模式
+   - 全相联
+   - 32-64项

| 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| 0 | MASK | 0 |
| VPN2 | G | 0 | ASID |
| 0 | PFN | C | D | V | 0 |
| 0 | PFN | C | D | V | 0 |

| | 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| | 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| Pagemask | 0 | MASK | 0 |
| EntryHi | VPN2 | 0 | ASID |
| EntryLo0 | 0 | PFN | C | D | V | G |
| EntryLo1 | 0 | PFN | C | D | V | G |
| Index | P | 0 | Index |
| Random | 0 | Random |
| Wired | 0 | Wired |
| EPC | EPC |
| BadVAddr | Bad Virtual Address |
| Context | PTEBase | BadVPN2 | 0 |