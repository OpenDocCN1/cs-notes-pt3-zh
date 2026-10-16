# 1.3 Real-address mode memory model

# Alignment of Words, Doublewords, and Quadwords

+   - The natural boundaries for words, double words, and quadwords are even-numbered addresses, addresses evenly divisible by four, and addresses evenly divisible by eight, respectively.
+   - To improve the performance of programs, data structures (especially stacks) should be aligned on natural boundaries whenever possible.
+   - The reason for this is that the processor requires two memory accesses to make an unaligned memory access; aligned accesses require only one memory access.