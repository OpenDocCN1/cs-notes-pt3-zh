# # External Sort-Merge (Cont.)

2. Merge the runs (N-way merge). We assume (for now) that N < M.

+   1. Use N blocks of memory to buffer input runs, and 1 block to buffer output. Read the first block of each run into its buffer page

+   2. repeat

+   1. Select the first record (in sort order) among all buffer pages

+   2. Write the record to the output buffer. If the output buffer is full write it to disk.

+   3. Delete the record from its input buffer page. If the buffer page becomes empty then read the next block (if any) of the run into the buffer.

+   3. until all input buffer pages are empty: