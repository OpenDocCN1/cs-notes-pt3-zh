# # Segmentation Architecture

+   - Logical address consists of a two tuple （一个逻辑地址是两个向量的集合）： <segment-number, offset>,

+   - Segment table – maps two-dimensional physical addresses; each table entry has （段表 - 映射二维物理地址，每个表项包括）： base – contains the starting physical address where the segments reside in memory. （基址 - 包括内存中段物理地址的起始地址） limit – specifies the length of the segment. （限长 - 指定段的长度）

+   - Segment-table base register (STBR) points to the segment table's location in memory. （段表基址寄存器 指向段表在内存中的地址）