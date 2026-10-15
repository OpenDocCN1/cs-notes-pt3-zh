
- FAT File System
  - FAT Architecture
  - FAT Physical Structure
  - FAT Processes and Interactions

## Startup Process

- **BIOS** and CPU initiate the power-on self test
- **BIOS** finds the boot device
- **BIOS** loads the first physical sector (**MBR**)
- Transfer CPU execution to MBR
- MBR scans the partition table
- Load a copy of the **Boot Sector** for active partition
- Transfers CPU execution to Boot Sector

## File Processing on FAT Clusters

- Store file information
  - Continues to store file info in the next available cluster
    - when the file requires space greater than the cluster’s size.
  - e.g.
    - Three Files: 1 with (2-3-6-8), 2 with (4-5), 3 with (7)

![](img/53ee1e3b0eba43505c7d530851f32f6f_577_0.png)

## File Naming (cont.)

e.g. file with "The quick brown.fox" and "Thequi~1.fox"

![](img/53ee1e3b0eba43505c7d530851f32f6f_579_0.png)

## FAT: The Good and the Bad

- The Good – FAT supports:
  - Hierarchical tree of directories and files
  - Variable length files
  - Basic file and directory meta-data
- The Bad
  - At most, FAT32 supports 2TB disks
  - Locating free chunks requires scanning the entire FAT
  - Prone to internal and external fragmentation
    - Large blocks → internal fragmentation
  - **Reads require a lot of random seeking**

## Lots of Seek

- Consider the following code:

```
int fd = open("my_file.txt", "r");
int r = read(fd, buffer, 1024 * 4 * 4); // 4 4KB blocks
```

> FAT may have very low spatial locality, thus a lot of random seeking

FAT

| 56 | 57 | 58 | 59 | 60 | 61 | 62 | 63 | 64 | 65 | 66 | 67 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 67 | 0xFFFF | 0 | 0xFFFF | 63 | 0 | 56 | 57 | 0 | 0 | 59 | 60 |

Blocks

![](img/53ee1e3b0eba43505c7d530851f32f6f_581_0.png)

## NTFS File System

- NTFS Architecture
- NTFS Physical Structure
- NTFS Processes and Interactions

- NTFS File System
  - NTFS Architecture
  - NTFS Physical Structure
  - NTFS Processes and Interactions

## NTFS Clusters

- Cluster: smallest allocated disk space to hold file
  - Sequentially logical cluster numbers from the beginning of the partition
  - Clusters start at sector ZERO (different to FAT)
  - Floppy disks don’t use NTFS
  - Different cluster sizes depending on volume size

| Volume Size | NTFS Cluster Size |
|---|---|
| 7MB ~ 512MB | 512 bytes |
| 513MB ~ 1GB | 1KB |
| 1GB ~ 2GB | 2KB |
| 2GB ~ 2TB | 4KB |

Default NTFS Cluster Sizes

## Organization of an NTFS Volume

| NTFS Boot Sector | Master File Table | File System Data | Master File Table Copy |
|---|---|---|---|

### NTFS Boot Sector

- Layout of the volume
- File system structure
- Boot code

### File System Data

- Data not contained within MFT

### Master File Table

- Attributes of files
- Attributes of folders

*(Most Important)*

### Master File Table Copy

- A copy of MFT

## NTFS Boot Sector

- NTFS Boot Sector
  - Located at the first logical sector of each partition
  - Created when you format a volume
  - Ends with a 2-byte sector marker (always 0x55AA)
- Components
  - An x86-b
  - Original Equipment Manufacturer Identification (OEM ID)
  - BIOS Parameter Block (BPB)
  - Extended BPB
  - Executable boot code

The same as FAT File System

## Boot Sector Components

| 0x00 | 0x03 | 0x0B | 0x24 | 0x54 | 0x01FE |
|---|---|---|---|---|---|
| Jump | OEM ID | BPB | Ex-BPB | Bootstrap Code | Marker |
| 3Bs | 8Bs | 25Bs | 48Bs | 426Bs | 2Bs |

- Jump: skip the next several non-executable bytes
- OEM ID: ...
  - the name of the operating system that formatted the volume
- BPB & Ex-BPB: information of volume
  - Bytes Per Sector, Sectors Per Cluster, Media Descriptor, Total Sectors, Logical Cluster Number of the “MFT”, ...
- Bootstrap Code: executable code to start the OS
- Marker: end of boot sector

![](img/53ee1e3b0eba43505c7d530851f32f6f_589_0.png)
