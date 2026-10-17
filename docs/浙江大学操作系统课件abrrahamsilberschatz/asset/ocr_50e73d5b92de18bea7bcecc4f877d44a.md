# # 9.4 Paging （分页）

+   Logical address space of a process can be noncontiguous; process is allocated physical memory whenever the latter is available. （进程的逻辑地址空间可能是不连续的，如果有可用的物理内存，它将分给进程。）

+   Divide physical memory into fixed-sized blocks called frames (size is power of 2, between 512 bytes and 8192 bytes). （把物理内存分成大小固定的块。）

+   Divide logical memory into blocks of same size called pages. （把逻辑内存也分位固定大小的块，叫做页。）

+   Keep track of all free frames. （保留一个页的记录。）

+   To run a program of size n pages, need to find n free frames and load program. （运行一个有N页大小的程序，需要找到N个空的页框读入程序。）

+   Set up a page table to translate logical to physical addresses. （建立一个页表，把逻辑地址转换为物理地址。）

+   Internal fragmentation. （内碎片。）