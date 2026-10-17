

## Demand Paging Example

- Memory access time = 1 microsecond （存取内存的时间）
- 50% of the time the page that is being replaced has been modified and therefore needs to be swapped out. 50%的时间，所置换的页被修改，因此需要被换出
- Swap Page Time = 10 msec = 10,000 msec （交换页的时间）

EAT = (1 – p) x 1 + p (15000)
1 + 15000P   (in msec)

## Process Creation

- Virtual memory allows other benefits during process creation:
  在进程创建过程中虚存允许另外的好处:
  - Copy-on-Write
    写拷贝
  - Memory-Mapped Files
    内存映射文件

![](img/ba81f478b8c7b785e80053d010189a68_435_0.png)

![](img/ba81f478b8c7b785e80053d010189a68_435_1.png)

## Copy-on-Write

- Copy-on-Write (COW) allows both parent and child processes to initially *share* the same pages in memory.
  COW允许父子进程在内存中初始共享相同页。
  If either process modifies a shared page, only then is the page copied.
  如果任一进程修改分享页，仅仅是页被拷贝。

- COW allows more efficient process creation as only modified pages are copied.
  COW允许更多有效进程创建页，仅当修改页被拷贝时。

- Free pages are allocated from a *pool* of zeroed-out pages.
  空闲页从一个zeroed-out页池中被分配。

## Memory-Mapped Files

- **Memory-mapped file I/O** allows file I/O to be treated as routine memory access by *mapping a disk block to a page in memory*.
  内存映射文件 I/O 允许文件 I/O 被处理，通过映射磁盘块到内存中一页常规内存访问。

- **A file is initially read using demand paging.** A page-sized portion of the file is read from the file system into a physical page. Subsequent reads/writes to/from the file are treated as ordinary memory accesses.
  一个文件开始被读使用请求页。文件的一页大小从文件系统被读入一物理的页。随后文件读／写处理被当作普通存储器访问。

- **Simplifies file access** by treating file I/O through memory rather than read() write() system calls. 通过内存文件I/O的一般文件访问的处理要优于读、写系统调用。

- **Also allows several processes to map the same file** allowing the pages in memory to be shared.
  也允许若干进程映射允许被共享内存页的相同文件。

## Memory Mapped Files

![](img/ba81f478b8c7b785e80053d010189a68_438_0.png)

## Page Replacement

- Prevent over-allocation of memory by modifying page-fault service routine to include page replacement（通过修改缺页服务例程，来包含页置换，防止分配过多）。

- Use _modify (dirty) bit_ to reduce overhead of page transfers – only modified pages are written to disk（修改（脏）位来防止页面转移过多—只有被修改的页面才写入磁盘）。

- Page replacement completes separation between logical memory and physical memory – large virtual memory can be provided on a smaller physical memory（页置换完善了逻辑内存和物理内存的划分—在一个较小的物理内存基础之上可以提供一个大的虚拟内存）。

## Basic Page Replacement

1. Find the location of the desired page on disk.
   在磁盘上找到需要页的位置

2. Find a free frame找到空闲的页框:
   - If there is a free frame, use it. （如果有一个空闲页框，使用它）
   - If there is no free frame, use a page replacement algorithm to select a victim frame.
   如果没有空闲页框，使用页代替算法选择一个牺牲(淘汰)页框。

3. Read the desired page into the (newly) free frame. Update the page and frame tables.
   读入该页到（最新）空闲页框。更新页和页框表

4. Restart the process.
   重启进程

## Page Replacement

frame valid-invalid bit

page table

0 i

f v

② change to invalid

④ reset page table for new page

physical memory

f victim

① swap out victim page

③ swap desired page in

## Graph of Page Faults Versus The Number of Frames

![](img/ba81f478b8c7b785e80053d010189a68_444_0.png)

number of page faults

number of frames

## FIFO Page Replacement

![](img/ba81f478b8c7b785e80053d010189a68_446_0.png)

![](img/ba81f478b8c7b785e80053d010189a68_446_1.png)

reference string

7  0  1  2  0  3  0  4  2  3  0  3  2  1  2  0  1  7  0  1

| 7 | 7 | 7 | 2 |   | 2 | 2 | 4 | 4 | 4 | 0 |   | 0 | 0 |   | 7 | 7 | 7 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 7 | 0 | 0 | 0 |   | 3 | 3 | 3 | 2 | 2 | 2 |   | 1 | 1 |   | 1 | 0 | 0 |
|   | 1 | 1 | 1 |   | 1 | 0 | 0 | 0 | 3 | 3 |   | 3 | 2 |   | 2 | 2 | 1 |

page frames

