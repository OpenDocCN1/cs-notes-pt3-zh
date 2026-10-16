# 4.3 Interrupt in x86 System

# Interrupt and Exception Classification

# Software-Generated Interrupts

+   - Software, non-maskable, and Vector interrupt
+   - The INT n instruction permits interrupts to be generated from within software by supplying an interrupt vector number as an operand.
+   - interrupt vector number: Operand in INT n
+   - No need interrupt recognition.

+   - BIOS interrupt
+     - INT 10H, INT 13H, INT 16H, ...
+   - DOS interrupt
+     - INT 20H, INT 21H, INT 24H,...