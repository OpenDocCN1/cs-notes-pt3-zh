# Y86 Processor State

+   - Program Registers
+     - Same 8 as with IA32. Each 32 bits
+   - Condition Codes
+     - Single-bit flags set by arithmetic or logical instructions
+       - OF: Overflow  ZF: Zero  SF: Negative
+   - Program Counter
+     - Indicates address of instruction
+   - Memory
+     - Byte-addressable storage array
+     - Words stored in little-endian byte order

# Program registers

| %eax | %esi |
| %ecx | %edi |
| %edx | %esp |
| %ebx | %ebp |

# Condition codes

| OF | ZF | SF |

# PC

![](bbox=[0.72, 0.68, 0.84, 0.72])

# Memory

![](bbox=[0.7, 0.79, 0.92, 0.95])