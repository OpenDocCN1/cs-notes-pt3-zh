# # MIPS assembly language

| Category | Instruction | Example | Meaning | Comments |
|---|---|---|---|---|
| Arithmetic | add | Add $s1,$s2,$s3 | $s1=$s2 + $s3 | Three register operands |
| | subtract | Sub $s1,$s2,$s3 | $s1=$s2 - $s3 | Three register operands |
| Data transfer | load word | lw $1, 100($s2) | $s1=Memory[$s2+100] | Data from memory to register |
| | store word | sw $s1, 100($s2) | Memory[$s2+100]=$s1 | Data from register to memory |
| logical | and | and $s1,$s2,$s3 | $s1=$s2 & $s3 | three reg. operands;bit-by-bit AND |
| | or | or $s1,$s2,$s3 | $s1=$s2 | $s3 | three reg. operands;bit-by-bit OR |
| | nor | nor $s1,$s2,$s3 | $s1=~($s2 | $s3) | three reg. operands;bit-by-bit NOR |
| | and immediate | addi $s1,$s2,100 | $s1=$s2 & 100 | Bit-by-bit AND reg with constant |
| | or immediate | ori $s1,$s2,100 | $s1=$s2 | 100 | Bit-by-bit OR reg with constant |
| | shift left logical | sll $s1,$s2,10 | $s1=$s2 << 10 | Shift left by constant |
| | shift right logical | srl $s1,$s2,10 | $s1=$s2 >> 10 | Shift right by constant |
| Conditional branch | branch on equal | beq $s1,$s2,L | If($s1==$s2) go to L | Equal test and branch |
| | branch not eqaal | bne $s1,$s2,L | If($s1!=$s2) go to L | Not equal test and branch |
| | set on less than | slt $s1,$s2,$s3 | If($s2<$s3) $s1=1 Else $s1=0 | Compare less than;used with beq, bne |
| | set on less than immediate | slt $s1,$s2100 | If($s2<100) $s1=1 Else $s1=0 | Compare less than immediate;used with beq, bne |
| Unconditional jump | jump | j L | go to L | Jump to target address |
| al jump | jump register | jr $ra | go to $ra | For procedure return |
| | jump and link | jal L | $ra=PC+4; go to L | For procedure call |