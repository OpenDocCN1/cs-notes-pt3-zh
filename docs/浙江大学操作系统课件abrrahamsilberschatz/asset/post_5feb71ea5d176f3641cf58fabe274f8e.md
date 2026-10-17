

## Application Interface (Cont.)

- Since the OS does not provide file system services, the application must decide how to use the array of blocks.
  由于操作系统不提供文件系统服务，应用程序必须决定如何使用数据块的数组。

- Since every application makes up its own rules for how to organize a tape, a tape full of data can generally only be used by the program that created it.
  由于每个应用程序对于如何组织一个磁带都建立了自己的规则，一个装满数据的磁带通常只能由创建它的应用程序来使用。

- The basic operations for a tape drive differ from those of a disk drive.
  磁带驱动器的基本操作与磁盘驱动器是不同的。

## Tape Drives 磁带驱动器

- locate positions the tape to a specific logical block, not an entire track (corresponds to seek).
  定位操作指向磁带的一个特定逻辑块，而不是一个完整的磁道（与寻道操作对比）

- The read position operation returns the logical block number where the tape head is.
  读位置操作返回磁带头所在的逻辑块号。

- The space operation enables relative motion.
  间隔操作允许相关的运动。

- Tape drives are “append-only” devices; updating a block in the middle of the tape also effectively erases everything beyond that block.
  磁带驱动器是“只能附加”的设备；更新磁带中间的一个块，需要先清除那个块上的所有数据。

- An EOT mark is placed after a block that is written.
  写完的一块后面需要加上一个EOT标记。

## 14.8.2.2 File Naming 文件命名

- The issue of naming files on removable media is especially difficult when we want to write data on a removable cartridge on one computer, and then use the cartridge in another computer.
  当我们想向一台计算机的一个可移动盘碟写入数据、然后在另一台计算机中使用的时候，命名文件的问题在可移动媒介上更加困难。

- Contemporary OSs generally leave the name space problem unsolved for removable media, and depend on applications and users to figure out how to access and interpret the data.
  现代操作系统通常没有解决可移动媒介上的命名空间问题，而是依靠应用程序和用户来指出如何访问解释数据。

- Some kinds of removable media (e.g., CDs) are so well standardized that all computers use them the same way.
  一些可移动介质（比如CD）相当的规格化，所有的计算机都以同样的方式使用它们。

## 14.8.2.3 Hierarchical Storage Management (HSM) 层次存储管理

A hierarchical storage system extends the storage hierarchy beyond primary memory and secondary storage to incorporate tertiary storage — usually implemented as a jukebox of tapes or removable disks.
一个层次存储系统扩展了存储层次，从主存、二级存储到一体化的三级存储——通常是一个磁带的自动播放机或者可移动磁盘。

Usually incorporate tertiary storage by extending the file system.
通常通过扩展文件系统来一体化三级存储。

Small and frequently used files remain on disk.
经常使用的小文件仍然存在磁盘上。

Large, old, inactive files are archived to the jukebox.
不使用的大的旧文件存在自动播放机上。

HSM is usually found in supercomputing centers and other large installations that have enormous volumes of data.
HSM在超级计算中心和其他有庞大数据量的大设备中比较常见。

## 14.8.3 Performance Issues 有关性能的问题

## 14.8.3.1 Speed 速度

- Two aspects of speed in tertiary storage are bandwidth and latency.
  三级存储速度的两个方面是带宽和延迟。

- Bandwidth is measured in bytes per second.
  带宽用每秒字节数来衡量。

- Sustained bandwidth – average data rate during a large transfer; # of bytes/transfer time.
  Data rate when the data stream is actually flowing.
  持续的带宽——大量传输过程中的平均数据率；单位传输时间的字节数。数据流实际流动时的数据率。

## Speed

**Effective bandwidth** – average over the entire I/O time, including seek or locate, and cartridge switching. Drive’s overall data rate.
有效带宽——整个 I/O 时间的平均，包括寻道或者定位，以及盘碟选择。驱动器的全面数据率

- **Access latency** – amount of time needed to locate data.
  访问延迟——定位数据需要的时间。

- **Access time for a disk** – move the arm to the selected cylinder and wait for the rotational latency; < 35 milliseconds.
  磁盘的访问时间——移动磁臂来选择柱面，并且等待旋转延迟；<35毫秒。

- **Access on tape** requires winding the tape reels until the selected block reaches the tape head; tens or hundreds of seconds.
  访问磁带需要把所选的块倒到磁带头的位置；数十甚至数百秒。

![](img/ba81f478b8c7b785e80053d010189a68_645_0.png)

![](img/ba81f478b8c7b785e80053d010189a68_645_1.png)

## 14.8.3.3 Cost 成本

- Main memory is much more expensive than disk storage.
  主存比磁盘存储要贵很多。

- The cost per megabyte of hard disk storage is competitive with magnetic tape if only one tape is used per drive.
  硬盘存储的每兆字节成本与磁带不相上下，如果每个驱动器只用一条磁带。

- The cheapest tape drives and the cheapest disk drives have had about the same storage capacity over the years.
  近年来，最便宜的磁带驱动器和最便宜的磁盘驱动器的存储容量几乎一样。

- Tertiary storage gives a cost savings only when the number of cartridges is considerably larger than the number of drives.
  只有当磁碟的数量远大于驱动器数量的时候，三级存储才能节约成本。

