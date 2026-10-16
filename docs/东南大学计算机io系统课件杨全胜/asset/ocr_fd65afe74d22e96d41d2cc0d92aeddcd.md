# 1.3 Real-address mode memory model

# Real mode memory addressing

+   - All real mode physical memory address are 20 bits wide.
+   - All real mode logical memory addresses must consist of a segment address plus an offset address.

+   - **Segment address (16 bits):** located within one of segment register, defines the beginning address of any 64K-byte memory segment.
+   - **Offset address (16 bits):** selects any location within the 64K-byte memory segment.
+   - Writing as **Segment address : Offset address**