# Virtual U/K Bit

+   - Implementing a virtual U/K bit:
+     - VMM stores the current state of guest's U/K bit (in some memory location)
+     - Privileged instructions in guest code will cause an exception (U mode)
+       - VMM exception handler's job will be to emulate these instructions
+     - "trap and emulate"
+       - E.g., if load PTP instruction runs in virtual K mode, load shadow PT. Otherwise, send an exception to the guest OS, so it can handle it