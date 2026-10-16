# 3.4 8086/8088 Hardware

# Pin-outs and the Pin Function

# 8086 pin we will use

+   - RD̅ : O, When the read signal is a logic 0, the data bus is receptive to data from the memory or I/O device.
+   - WR̅ : O, When the write signal is a logic 0, the data bus contains valid data that 8086 outputting to the memory or I/O device.
+   - ALE : O, Address latch Enable shows that 8086 AD₀-15 contains address information.
+   - INTR : I, Interrupt request is used to request a hardware interrupt.
+   - INTA̅ : O, The interrupt acknowledge signal is a response to the INTR input pin.