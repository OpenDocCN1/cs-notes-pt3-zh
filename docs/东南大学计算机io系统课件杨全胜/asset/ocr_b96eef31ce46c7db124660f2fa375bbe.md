# 3.1 I/O Module

# I/O module Function

+   Device communication

+   Control signals. Determine the function that the device will perform, such as:

+   - Send data to the peripheral.(OUTPUT)
+   - Accept data from the peripheral.(INPUT)
+   - Device report status, or I/O module perform some control function particular to the device.

+   Data transfer. In the form of a set of bits to be sent or received from the peripheral.

+   Status signals. Indicate the state of the device.

+   Data buffering

+   The data is buffered(by latch) in the I/O module and then send to device at its rate.

+   Error detection and reports error to the processor