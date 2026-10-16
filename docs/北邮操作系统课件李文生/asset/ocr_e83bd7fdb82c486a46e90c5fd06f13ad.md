# I/O port

+   - **4 registers**
+     - Status: contains bits that can be read by the host. Idle, busy, ready, error
+     - Control: can be written by the host to start a command or to change the mode of a device.
+     - Data-in: read by the host to get input
+     - Data-out: written by the host to send output

Data registers are typically 1 to 4 bytes in size.

Some controllers have FIFO chips to expand the capacity of the controller beyond the size of the data register.
FIFO chips can hold several bytes of input or output data