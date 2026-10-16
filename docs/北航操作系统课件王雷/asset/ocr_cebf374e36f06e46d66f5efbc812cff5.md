# Booting sequence

+   1. Turn on
+   2. CPU jump to address of BIOS (0xFFFF0)
+   3. BIOS runs POST (Power-On Self Test)
+   4. Find bootable devices
+   5. Loads and execute boot sector form MBR
+   6. Load OS