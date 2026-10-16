# Direct Memory Access (Cont.)

+   - Takes control of the system from the CPU to transfer data to and from memory over the system bus
+   - Cycle stealing (周期挪用) is used to transfer data on the system bus
+   - The instruction cycle is suspended so data can be transferred
+   - The CPU pauses one bus cycle
+   - No interrupts occur
+     - Do not save context

![](bbox=[0.52, 0.78, 0.92, 0.92])