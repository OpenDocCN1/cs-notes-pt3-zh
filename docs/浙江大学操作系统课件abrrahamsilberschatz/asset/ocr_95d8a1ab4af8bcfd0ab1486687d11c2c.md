# # In-Memory File System Structures

+   The following figure illustrates the necessary file system structures provided by the operating systems. OS中的文件系统结构下面图例的功能

+   When a file is opened , the directory structure is searched for the given file name. Parts of the directory structure are usually cached in memory to speed directory operations. Once the file is found , the FCB is copied into a system- wide open-file table in memory. This table not only stores the FCB, but also has entries for a count of the number of processes that have the file open. Next , an entry is made in the per-process open-file table, with a pointer to the entry in the system- wide open-file table and some other fields.

+   Figure 12-3(a) refers to opening a file.

+   Figure 12-3(b) refers to reading a file.