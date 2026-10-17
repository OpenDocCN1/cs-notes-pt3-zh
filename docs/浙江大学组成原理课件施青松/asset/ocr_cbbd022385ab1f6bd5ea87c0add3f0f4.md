# # Synchronous vs. Asynchronous

+   - Synchronous bus use a clock and a synchronous protocol, fast and small but every device must operate at same rate and clock skew requires the bus to be short
+   - Asynchronous bus don't use a clock and instead use handshaking

# # Handshaking protocol

+   - Our example ,which illustrates how asynchronous buses use handshaking, assumes there are three control lines.
+     - ReadReq: Used to indicate a read request for memory. The address is put on the data lines at the same time.
+     - DataRdy: Used to indicate that data word is now ready on the data lines.
+     - Ack: Used to acknowledge the ReadReq or the DataRdy signal of the other party.