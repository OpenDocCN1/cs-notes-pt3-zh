# APIC, IO-APIC, LAPIC

+   - Advanced PIC (APIC) for SMP systems
+     - Used in all modern systems
+     - Interrupts “routed” to CPU over system bus
+     - IPI: inter-processor interrupt
+   - Local APIC (LAPIC) versus “frontend” IO-APIC
+     - Devices connect to front-end IO-APIC
+     - IO-APIC communicates (over bus) with Local APIC
+   - Interrupt routing
+     - Allows broadcast or selective routing of interrupts
+     - Ability to distribute interrupt handling load
+     - Routes to lowest priority process
+       - Special register: Task Priority Register (TPR), i.e., locking
+     - Arbitrates (round-robin) if equal priority