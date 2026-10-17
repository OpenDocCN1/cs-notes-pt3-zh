# Storage Structure (Cont.)

+   - Disk surface is logically divided into *tracks*, which are subdivided into *sectors*.
+   
+     磁盘表面逻辑划分了磁道、再划分为扇区

+   - The *disk controller* determines the logical interaction between the device and the computer.
+   
+     磁盘驱动器确定设备和计算机之间的相互作用

+   - **Positioning time** 定位时间（random-access time 随机存取时间）: consists of the time to move the disk arm to the desired cylinder (called the seek time 寻道时间), and the time for the desired sector to rotate to the disk head (called the rotational latency 旋转延迟时间).