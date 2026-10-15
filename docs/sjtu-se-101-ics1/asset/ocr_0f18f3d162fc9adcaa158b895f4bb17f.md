# Move Instruction Examples

| IA32 | Y86 |
|---|---|
| movl $0xabcd, %edx | irmovl $0xabcd, %edx |
| movl %esp, %ebx | rrmovl %esp, %ebx |
| movl -12(%ebp),%ecx | mrmovl -12(%ebp),%ecx |
| movl %esp,0x12345(%edx) | rmmovl %esp,0x12345c(%edx) |

| movl $0xabcd, (%eax) | — |
| movl %eax, 12(%eax,%edx) | — |
| movl (%ebp,%eax,4),%ecx | — |