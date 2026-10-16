# 7.5 COM in IA-32

# 16550 initialize

+   1. Write the divisor latch DL(port 0 and 1) to set baud rate.
+   2. Write the line control register LCR(port 3) to set the format of the asynchronous data communications exchange.
+   3. Write the MODEM control register MCR( port 4) to set the MODEM control word.
+   4. Write Interrupt enable register IER(port 1) to set the interrupt enable word.