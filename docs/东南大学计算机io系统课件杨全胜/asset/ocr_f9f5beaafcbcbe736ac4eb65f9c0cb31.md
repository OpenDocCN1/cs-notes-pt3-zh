# 6.3 82C55 Operation Mode

# Mode 2 – Strobed Input/Output

+   INTR. A “high” on this output can be used to interrupt the CPU for Both input or output operations.

# Output Operations

+   OBF#. The OBF# output will go “low” to indicate that the CPU has written data out to Port A.

+   ACK#. A “low” on this input enables the tri-state output buffer of port A to send out the data. Otherwise, the output buffer will be in the high impedance state.

+   INTE 2. Controlled by bit set/reset of PC6

# Input Operations

+   STB#. A “low” on this input loads data into the input latch.

+   IBF. A “high” on this output indicates that data has been loaded into the input latch.