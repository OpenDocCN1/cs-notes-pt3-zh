# Unix内核如何表示打开文件

两个运算符引用两个不同的打开文件。
描述符 1 (stdout) 指向终端, 描述符 4 指向打开磁盘文件

描述符表
[每个进程一张表]

打开文件表
[所有进程共享]

v-node 表
[所有进程共享]

stdin fd 0
stdout fd 1
stderr fd 2
fd 3
fd 4

File A (terminal)
文件位置
refcnt=1
：

文件访问
文件大小
文件类型
：

Info in stat struct

File B (disk)
文件位置
refcnt=1
：

文件访问
文件大小
文件类型
：