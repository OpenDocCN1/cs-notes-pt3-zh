# 11.2.1 可利用空间表的结点结构

header
(块头)

llink

tag

size

rlink

space

uplink

tag

footer
(块尾)

size

标志位：
tag= 1 占用块
0 空闲块

块尾的作用：
简化回收算法