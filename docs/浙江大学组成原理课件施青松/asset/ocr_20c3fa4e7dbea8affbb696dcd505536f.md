# # Page faults

+   - When the OS  creates a process, it usually creates the space on disk for all the pages of a process.

+   - When a gage fault occurs, the OS will be given control through exception mechanism.

+   - The OS will find the page in the disk by the page table.

+   - Next, the OS will bring the requested page into main memory. If all the pages in main memory are in use, the OS will use LRU strategy to choose a page to replace

![](bbox=[0.418, 0.25, 0.957, 0.906])