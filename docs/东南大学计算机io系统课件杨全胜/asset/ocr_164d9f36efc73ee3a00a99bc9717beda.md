# 7.4 16550 UART

# 16550 UART Pins

# Serial data I/O

+   - SIN: Serial Input
+   - SOUT: Serial Output
+   - XIN: External Crystal Input
+   - XOUT: External Crystal Output
+   - RCLK: Receiver Clock
+   - BAUDOUT#: Baud Out

+   - $f_{Baud Out}=f_{XOUT} \div Divisor\ latch=Baud\ rate \times 16$
+   - The BAUDOUT may also be used for the receiver section by tying this output to the RCLK input of the chip.