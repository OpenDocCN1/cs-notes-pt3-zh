# Optimization of Disk-Block Access

+   - **Block – a contiguous sequence of sectors from a single track**
+     - data is transferred between disk and main memory in blocks
+     - **sizes range from 512 bytes to several kilobytes**
+       - Smaller blocks: more transfers from disk
+       - Larger blocks: more space wasted due to partially filled blocks
+       - Typical block sizes today range from 4 to 16 kilobytes
+   - Disk-arm-scheduling algorithms order pending accesses to tracks so that disk arm movement is minimized