# 4.2 8259A PIC

# Modes of Operation

# Priority Mode

# Fixed Priority

+   - The interrupt requests are ordered in priority from 0 through 7 (0 highest).

# Rotation Priority

(The IR0 ~ IR7 priority as a circular queue.)

+   - Automatic Rotation
+     - In this mode a device, after being serviced, receives the lowest priority.

+   - Specific Rotation
+     - The programmer can change priorities by programming the bottom priority and thus fixing all other priorities; i.e., if IR4 is programmed as the bottom priority device, then IR5 will have the highest