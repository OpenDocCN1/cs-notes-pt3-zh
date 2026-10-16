# 4.2 8259A PIC

# Modes of Operation

# Buffered Mode

+   - When the 8259A is used in a large system where bus driving buffers are required on the data bus, it will structure the 8259A to send an enable signal on SP#/EN# to enable the buffers.
+   - This modification forces the use of software programming to determine whether the 8259A is a master or a slave.

# Non-buffered Mode

+   - SP#/EN# = 1; 8259A is the master controller
+   - SP#/EN# = 0; 8259A is the slave controller