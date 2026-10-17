# MIPS operands

| Name | Example | Comments |
|---|---|---|
| **32 register** | `$s0,$s1……,$s7`<br>`$t0, $t1……,$t7` | Fast locations for data. In MIPS, data must be in registers to perform arithmetic. Registers `$s0-$s7` map to 16-23 and `$t0-$t7` map to 8-15. |
| **2³⁰ memory words** | `Memory[0]`<br>`Memory[4]`<br>……<br>`Memory[4294967292]` | Accessed only by data transfer instructions in MIPS. MIPS uses byte addr., so sequential word addr. Differ by 4. Memory holds data structures, arrays, and spilled registers. |

# MIPS assembly language

| Category | Instruction | Example | Meaning | Comments |
|---|---|---|---|---|
| **Arithmetic** | add | Add `$s1,$s2,$s3` | `$s1=$s2 + $s3` | Three register operands |
|  | subtract | Sub `$s1,$s2,$s3` | `$s1=$s2 - $s3` | Three register operands |
|  | **Add immediate** | addi `$s1,$s2,100` | **`$s1=$s2+100`** | +constants; overflow detected |
| **Data transfer** | load word | lw `$1, 100($s2)` | `$s1=Memory[$s2+100]` | Data from memory to register |
|  | store word | sw `$s1, 100($s2)` | `Memory[$s2+100]=$s1` | Data from register to memory |
| **logical** | and | and `$s1,$s2,$s3` | `$s1=$s2 & $s3` | **three reg. operands; bit-by-bit AND** |
|  | or | or `$s1,$s2,$s3` | `$s1=$s2 \| $s3` | **three reg. operands; bit-by-bit OR** |
|  | nor | nor `$s1,$s2,$s3` | `$s1=~($s2 \| $s3)` | **three reg. operands; bit-by-bit NOR** |
|  | and immediate | addi `$s1,$s2,100` | `$s1=$s2 & 100` | Bit-by-bit AND reg with constant |
|  | or immediate | ori `$s1,$s2,100` | `$s1=$s2 \| 100` | Bit-by-bit OR reg with constant |
|  | shift left logical | sll `$s1,$s2,10` | `$s1=$s2 << 10` | Shift left by constant |
|  | shift right logical | srl `$s1,$s2,10` | `$s1=$s2 >> 10` | Shift right by constant |