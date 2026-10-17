# Summary of MIPS architecture in Chapter 2

# MIPS instruction format

| Name | Fields | Comments |
|---|---|---|
| Field size | 6 bits \| 5 bits \| 5 bits \| 5 bits \| 5 bits \| 6 bits | All MIPS instructions 32 bits |
| R-format | op \| rs \| rt \| rd \| shamt \| funct | Arithmetic instruction format |
| I-format | op \| rs \| rt \| address/immediate | Transfer, branch, imm. format |
| J-format | op \| target address | Jump instruction format |

# MIPS operands

| Name | Example |
|---|---|
| 32 registers | $s0~$s7, $t0~$t9, $zero, $a0~$a3, $v0~$v1, $gp, $fp, $gp, $ra, $at |
| Mem words | Memory[0], Memory[4], …, Memory[4294967292] |

# MIPS assembly language

+   Arithmetic
+   
+   - add — `add $s1, $s2, $s3`
+   - subtract — `sub $s1, $s2, $s3`
+   - add immediate — `addi $s1, $s2, -3` (Note: subi does not exist)