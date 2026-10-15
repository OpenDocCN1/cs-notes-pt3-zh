
## VFS Flowchart

Processes (usually) don’t need to know about low-level file system details

Relatively simple to add additional file system drivers

Process 1

Process 2

Process 3

Virtual File System Interface

Kernel

ext3 Driver

NTFS Driver

FAT32 Driver

ext3 Partition

NTFS Partition

FAT32 Partition

## Mount isn’t Just for Bootup

- When you plug storage devices into your running system, mount is executed in the background
- Example: plugging in a USB stick
- What does it mean to “safely eject” a device?
  - Flush cached writes to that device
  - Cleanly unmount the file system on that device

![](img/53ee1e3b0eba43505c7d530851f32f6f_612_0.png)

### Homework

- Please learn about **btrfs**, use your own words to describe its system architecture, and state its pros and cons (you can compare it with ext4/fat/ntfs)
- (optional) you can also check ReiserFS and ZFS, they also have very interesting features

## File System Durability & Crash Recovery

Yubin Xia & Rong Chen

Some of the materials are adopted from Frans’ 6.828 course

## Review: File Naming in FAT32

e.g. file with "The quick brown.fox" and "Thequi~1.fox"

![](img/53ee1e3b0eba43505c7d530851f32f6f_615_0.png)

2nd Long Entry (And Last)
Short Entry
1st Long Entry

long file name

short file name

## FAT32 Long File Name

- Using 0xF in directory entry
  - Means this entry is part of long file name
  - 0xF is not used in DOS/WIN32 (consider as invalid)
- Using unicode for storage
  - 2 bytes (16 bits)
- The short (8.3) file name is still there
  - The system cannot work without short name

## Bind Short Name and Long Name

```c
int i,j,chksum=0;

for (i=11; i>0; i--)
{
    chksum = ((chksum & 1) ? 0x80 : 0)
           + (chksum >> 1)
           + shortname[j++];
}
```

## Question

- What is the process of searching a file by its long name?

## File Name Search in ExFAT

- Search name by hash value first
  - Hash the upper case version of the file name
  - Each record in the directory is searched by comparing the hash value
  - When a match is found, the filenames are compared to ensure that the proper file was located in case of collisions
    - Only two characters have to be compared, why?

## FS DURABILITY & CRASH CONSISTENCY

## File System Durability

Topic: tension between fs perf. and crash recovery

Disk performance is often a #1 bottleneck

"how many seeks will that take?"

Durability != Crash consistency

“Here is all of my data. But some of the metadata is wrong.”

Crash recovery is much harder than performance

"what if a crash occurred at this point?"

## An Example: Append a File

- Inside of I[v1]:
  - owner : yubin
  - permissions : read-only
  - size : 1
  - pointer : 4
  - pointer : null
  - pointer : null
  - pointer : null

![](img/53ee1e3b0eba43505c7d530851f32f6f_623_0.png)

- Inside of I[v2]:
  - owner : yubin
  - permissions : read-only
  - size : 2
  - pointer : 4
  - pointer : 5
  - pointer : null
  - pointer : null

![](img/53ee1e3b0eba43505c7d530851f32f6f_624_0.png)

## Crash Scenarios: 1 Succeeds

- Imagine only a single write succeeds; there are thus three possible outcomes:
- 1. Just the data block (Db) is written to disk
  - What will happen?
- 2. Just the updated inode (I[v2]) is written to disk
  - What will happen?
- 3. Just the updated bitmap (B[v2]) is written to disk
  - What will happen?

## Crash Scenarios: 2 Succeed

- Two writes succeed and the last one fails:
- 1. The inode (I[v2]) and bitmap (B[v2]) are written to disk, but not data (Db)
- 2. The inode (I[v2]) and the data block (Db) are written, but not the bitmap (B[v2])
- 3. The bitmap (B[v2]) and data block (Db) are written, but not the inode (I[v2])
