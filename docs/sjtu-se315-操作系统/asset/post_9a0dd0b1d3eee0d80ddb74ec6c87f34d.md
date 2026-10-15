
## Compression of Files and Folders

- Moving Files or Folders within an NTFS Volume
  - keeps its compression state regardless of the compression state of the folder it is moved
- Copying Files or Folders within an NTFS Volume
  - takes on the compression state of the folder it is copied to.
- Between FAT and NTFS Volumes
  - FAT -> NTFS: takes on the compression attribute of the target folder
  - NTFS -> FAT: uncompressed

## Hard Links

- Hard Links
  - Add a directory entry for the hard link without duplicating the original file
  - Application can modify a file by using any of its hard Links
  - Can’t give a file different security descriptors on a per-hard-link basis

## Sparse Files

- Sparse Files
  - Focus on the file contain large sections of data composed of zeros
  - Store
    - Allocates disk clusters only for the data explicitly specified by the application
    - Non-specified ranges of the file are represented by non-allocated space on the disk
  - Read
    - From allocated ranges, return the data stored
    - From non-allocated ranges, return ZERO

## Sparse Files (cont.)

### Without Sparse File Attribute Set

![](img/53ee1e3b0eba43505c7d530851f32f6f_603_0.png)

Sparse data (zeros)  
10 gigabytes

Disk space used  
17 gigabytes

Meaningful data  
7 gigabytes

### With Sparse File Attribute Set

![](img/53ee1e3b0eba43505c7d530851f32f6f_603_1.png)

Sparse data (zeros)  
10 gigabytes

Disk space used  
7 gigabytes

Meaningful data  
7 gigabytes

## File System Recoverability

- Recovering NTFS File Structures
  - View each operation as a transaction and manages each one as an integral unit
  - Each transaction
    - Records the metadata operations in a log file cached in memory
    - Records the actual metadata operations in memory
    - Marks the transaction in the cached log file as committed
    - Flushes the log file to disk
    - Flushes the actual metadata operations to disk

## MBR & MOUNT

## The Master Boot Record

| Address |  | Description | Size (Bytes) |
| Hex | Dec. |  |  |
| 0x000 | 0 | Bootstrap code area | 446 |
| 0x1BE | 446 | Partition Entry #1 | 16 |
| 0x1CE | 462 | Partition Entry #2 | 16 |
| 0x1DE | 478 | Partition Entry #3 | 16 |
| 0x1EE | 494 | Partition Entry #4 | 16 |
| 0x1FE | 510 | Magic Number | 2 |
|  |  | Total: 512 |  |

Includes the starting LBA and length of the partition

![](img/53ee1e3b0eba43505c7d530851f32f6f_606_0.png)

## Extended Partitions

- In some cases, you may want >4 partitions
- Modern OSes support extended partitions

![](img/53ee1e3b0eba43505c7d530851f32f6f_607_0.png)

- Extended partitions may use OS-specific partition table formats (meta-data)
  - Thus, other OSes may not be able to read the logical partitions

## Types of Root File Systems

- Windows exposes a multi-rooted system
  - Each device and partition is assigned a letter
  - Internally, a single root is maintained
- Linux has a single root
  - One partition is mounted as /
  - All other partitions are mounted somewhere under /
- Typically, the partition containing the kernel is mounted as / or C:

![](img/53ee1e3b0eba43505c7d530851f32f6f_608_0.png)

## Mounting a File System

- 1. Read the super block for the target file system
  - Contains meta-data about the file system
  - Version, size, locations of key structures on disk, etc.
- 1. Determine the mount point
  - On Windows: pick a drive letter
  - On Linux: mount the new file system under a specific directory

| Filesystem | Size | Used | Avail | Use% | Mounted on |
|---|---|---|---|---|---|
| /dev/sda5 | 127G | 86G | 42G | 68% | /media/cbw/Data |
| /dev/sda4 | 61G | 34G | 27G | 57% | /media/cbw/Windows |
| /dev/sdb1 | 1.9G | 352K | 1.9G | 1% | /media/cbw/NDSS-2013 |

## Virtual File System Interface

- Problem: the OS may mount several partitions containing different underlying file systems
  - It would be bad if processes had to use different APIs for different file systems
- Linux uses a Virtual File System interface (VFS)
  - Exposes POSIX APIs to processes
  - Forwards requests to lower-level file system specific drivers
- Windows uses a similar system
