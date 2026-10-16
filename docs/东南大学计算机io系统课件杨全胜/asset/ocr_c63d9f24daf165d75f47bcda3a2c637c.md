# 7.5 COM in IA-32

# Programming Communication with interrupt

Initialization

+   - Modify the interrupt vector, According to COM1 or COM2, set the correct interrupt vector.

+   - Determine the operation mode of 16550, set the IER and enable the interrupt ( set D3 in MCR = 1 at the same time).

+   - Set the baud rate and format of data (DL and LCR).

+   - Enable the interrupt, Set the OCW1 of 8259A, enable IRQ4 or IRQ3. Set IF =1 in EFLAGS