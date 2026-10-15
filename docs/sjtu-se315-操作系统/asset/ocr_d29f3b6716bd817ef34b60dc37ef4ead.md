# Virtualizing the System ISA

+   - Hardware needed by monitor
+     - Ex: monitor must control real hardware interrupts
+   - Access to hardware would allow VM to compromise isolation boundaries
+     - Ex: access to MMU would allow VM to write any page
+   - So...
+     - All access to the virtual System ISA by the guest must be emulated by the monitor in software.
+     - System state kept in memory.
+     - System instructions are implemented as functions in the monitor.