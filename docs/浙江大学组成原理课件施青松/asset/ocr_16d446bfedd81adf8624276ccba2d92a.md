# Combine the reads and writes

+   - In most write-through cache organizations, the read and write miss penalties are the same
+     - the time to fetch the block from memory.
+   - If we neglect the write buffer stalls, we get the following equation:

Memory-stall clock cycles = \frac{\text{Memory accesses}}{\text{Program}} \times \text{Miss rate} \times \text{Miss penalty}

We can also write this as:

Memory-stall clock cycles = \frac{\text{Instructions}}{\text{Program}} \times \frac{\text{Misses}}{\text{Instructions}} \times \text{Miss penalty}