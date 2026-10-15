# Alternate view of a process

+   - Process = thread + code, data, and kernel context

Thread (main thread)

Code and Data

stack

SP

brk

PC

0

shared libraries

run-time heap

read/write data

read-only code/data

Thread context:
Data registers
Condition codes
Stack pointer (SP)
Program counter (PC)

Kernel context:
VM structures
Descriptor table
brk pointer