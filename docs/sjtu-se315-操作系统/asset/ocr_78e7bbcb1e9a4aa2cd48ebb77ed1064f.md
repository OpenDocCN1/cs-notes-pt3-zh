# Assigning IRQs to Devices

+   - IRQ assignment is hardware-dependent
+     - Sometimes it’s hardwired, sometimes it’s set physically, sometimes it’s programmable
+     - PCI bus usually assigns IRQs at boot
+   - Some IRQs are fixed by the architecture
+     - IRQ0: Interval timer
+     - IRQ2: Cascade pin for 8259A
+   - Linux device drivers request IRQs when the device is opened
+     - Note: especially useful for dynamically-loaded drivers, such as for USB or PCMCIA devices
+     - Two devices that aren’t used at the same time can share an IRQ, even if the hardware doesn’t support simultaneous sharing