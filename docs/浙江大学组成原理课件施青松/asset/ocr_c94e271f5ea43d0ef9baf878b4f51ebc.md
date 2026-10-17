# The datapath there are ......

| Name | Example | Comments |
|---|---|---|
| 32 register | `$s0-$s7, $t0-$t9, $zero, $a0-$a3, $v0-$v1` | **Fast locations for data.** In MIPS, data must be in registers to perform arithmetic. MIPS register `$zero` always equals 0. `$gp`(28) is the global pointer, `$sp`(29) is the stack pointer, `$fp`(30) is the frame pointer, and `$ra`(31) is the return address. |
| 30 Word Addresses signals line | Memory[0], Memory[4], Memory[4294967292] | Accessed only by data transfer instructions. MIPS uses byte addresses, so sequential word addresses differ by 4. Memory holds data structures, arrays, and spilled registers, such as those saved on procedure calls. |

| Name | Register no. | Usage | Preserved on call |
|---|---:|---|---|
| `$zero` | 0 | The constant value 0 | n.a. |
| `$v0-$v1` | 2-3 | Values for results and expression evaluation | no |
| `$a0-$a3` | 4-7 | Arguments | no |
| `$t0-$t7` | 8-15 | Temporaries | no |
| `$s0-$s7` | 16-23 | Saved | yes |
| `$t8-$t9` | 24-25 | More temporaries | no |
| `$gp` | 28 | Global pointer | yes |
| `$sp` | 29 | Stack pointer | yes |
| `$fp` | 30 | Framer pointer | yes |
| `$ra` | 31 | Return address | yes |