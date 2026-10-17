

## File System Backups (2)

Figure 4-25. A file system to be dumped. Squares are directories, circles are files. Shaded items have been modified since last dump. Each directory and file is labeled by its i-node number.

## File System Backups (3)

Figure 4-26. Bitmaps used by the logical dumping algorithm.

## Incremental versus differential backup

**Day 1**

**Day 2**

**Day 3**

**Day 4**

## Incremental backup

## Differential backup

## Backup devices

- Tape drive
  - Large capacity, fast
  - Requires new tapes regularly
- CD-R, CD-RW, DVD
  - Cheap but relatively slow
- (Removable) Hard disk
  - Fast but expensive
- Diskette drive
  - Often available but cumbersome for large backups
- Network
  - Useful in large installations; usually requires commercial software (for instance, Tivoli Storage Manager)

## Default backup tools

- **tar**
  - Backs up individual files
  - Widely available
  - Excellent for transferring data between platforms
- **cpio**
  - Backs up individual files
  - Widely available
  - Difficulties with many symbolic links
- **dump**
  - Backs up whole filesystems
  - Can handle incremental backups (nine levels)
- **dd**
  - Useful for making bit-for-bit dumps of disks and filesystems

## File System Consistency

Figure 4-27. File system states. (a) Consistent. (b) Missing block. (c) Duplicate block in free list. (d) Duplicate data block.

## Caching (1)

Hash table

Front (LRU)

Rear (MRU)

Figure 4-28. The buffer cache data structures.

## Caching (2)

- Some blocks, such as i-node blocks, are rarely referenced two times within a short interval.
- Consider a modified LRU scheme, taking two factors into account:
  - Is the block likely to be needed again soon?
  - Is the block essential to the consistency of the file system?

## Reducing Disk Arm Motion

Figure 4-29. (a) I-nodes placed at the start of the disk. (b) Disk divided into cylinder groups, each with its own blocks and i-nodes.

## The ISO 9660 File System

Figure 4-30. The ISO 9660 directory entry.

## Rock Ridge Extensions

### Rock Ridge extension fields:

- PX - POSIX attributes.
- PN - Major and minor device numbers.
- SL - Symbolic link.
- NM - Alternative name.
- CL - Child location.
- PL - Parent location.
- RE - Relocation.
- TF - Time stamps.

## Joliet Extensions

Joliet extension fields:

- Long file names.
- Unicode character set.
- Directory nesting deeper than eight levels.
- Directory names with extensions

## The MS-DOS File System (1)

Figure 4-31. The MS-DOS directory entry.

## The MS-DOS File System (2)

| Block size | FAT-12 | FAT-16 | FAT-32 |
|---|---|---|---|
| 0.5 KB | 2 MB | | |
| 1 KB | 4 MB | | |
| 2 KB | 8 MB | 128 MB | |
| 4 KB | 16 MB | 256 MB | 1 TB |
| 8 KB | | 512 MB | 2 TB |
| 16 KB | | 1024 MB | 2 TB |
| 32 KB | | 2048 MB | 2 TB |

Figure 4-32. Maximum partition size for different block sizes. The empty boxes represent forbidden combinations.

## The UNIX V7 File System (1)

Figure 4-33. A UNIX V7 directory entry.

## The UNIX V7 File System (2)

Figure 4-34. A UNIX i-node.

## The UNIX V7 File System (3)

| Root directory |
|---|
| 1 . |
| 1 .. |
| 4 bin |
| 7 dev |
| 14 lib |
| 9 etc |
| 6 usr |
| 8 tmp |

Looking up /usr yields i-node 6

| I-node 6 is for /usr |
|---|
| Mode size times |
| 132 |

I-node 6 says that /usr is in block 132

| Block 132 is /usr directory |
|---|
| 6 . |
| 1 .. |
| 19 dick |
| 30 erik |
| 51 jim |
| 26 ast |
| 45 bal |

/usr/ast is i-node 26

| I-node 26 is for /usr/ast |
|---|
| Mode size times |
| 406 |

I-node 26 says that /usr/ast is in block 406

| Block 406 is /usr/ast directory |
|---|
| 26 . |
| 6 .. |
| 64 grants |
| 92 books |
| 60 mbox |
| 81 minix |
| 17 src |

/usr/ast/mbox is i-node 60

Figure 4-35. The steps in looking up /usr/ast/mbox.

