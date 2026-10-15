
## Open Files

- An application announces its intention to access an I/O device
  - The application keeps track of only the descriptor
  - An application can set the current file position explicitly by performing a seek operation

## Open Files

```c
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

int open(char *filename, int flags, mode_t mode);
```

**Returns:** new file descriptor if OK, -1 on error

## flags

- O_RDONLY, O_WRONLY, O_RDWR (must have one)
- O_CREAT, O_TRUNC, O_APPEND (optional)

## mode

- S_IRUSR, S_IWUSR, S_IXUSR
- S_IRGRP, S_IWGRP, S_IXGRP
- S_IROTH, S_IWOTH, S_IXOTH

## Close Files

- close the file
  - Default actions when terminate
    - The kernel closes all open files
    - The kernel frees their memory resources

```
#include <unistd.h>
int close(int fd) ;
Returns: zero if OK, -1 on error
```

## Reading and Writing Files

- A read operation
  - Copies m > 0 bytes from the file to memory
    - starting at the current file position k
    - incrementing k by m
  - If the total bytes from k to the end of file is less than m, it triggers a condition known as end-of-file (EOF)
    - Can be detected by the application
    - There is no explicit "EOF character" at the end of a file

## Reading and Writing Files

```
#include <unistd.h>

ssize_t read(int fd, void *buf, size_t count);
    returns: number of bytes read if OK,
            0 on EOF, -1 on error

ssize_t write(int fd, const void *buf, size_t count);
    returns: number of bytes written if OK,
            -1 on error
```

## Reading File Metadata

```
#include <unistd.h>

#include <sys/stat.h>

int stat(const char *filename, struct stat *buf);

int fstat(int fd, struct stat *buf) ;

returns: 0 if OK, -1 on error
```

## Reading File Metadata

```
/* file info returned by the stat function */
struct stat {
    dev_t st_dev;               /* device */
    ino_t st_ino;               /* inode */
    mode_t st_mode;             /* protection and file type */
    nlink_t st_nlink;           /* number of hard links */
    uid_t st_uid;               /* user ID of owner */
    gid_t st_gid;               /* group ID of owner */
    dev_t st_rdev;              /* device type (if inode device) */
    off_t st_size;              /* total size, in bytes */
    unsigned long st_blksize;   /* blocksize for filesystem I/O */
    unsigned long st_blocks;    /* number of blocks allocated */
    time_t st_atime;            /* time of last access */
    time_t st_mtime;            /* time of last modification */
    time_t st_ctime;            /* time of last change */
};
```

```
int main(int argc, char **argv)
{
    struct stat stat ;
    char *type, *readok ;
    stat(argv[1], &stat) ;
    if (S_ISREG(stat.st_mode)) /* Determine file type */
        type = "regular" ;
    else if (S_ISDIR(stat.st_mode))
        type = "directory" ;
    else
        type = "other" ;

    if ((stat.st_mode & S_IRUSR)) /* check read access */
        readok = "yes";
    else
        readok = "no";

    printf("type: %s, read: %s\n", type, readok) ;
    exit(0) ;
}
```

S_ISREG() Is this a regular file?
S_ISDIR() Is this a directory file?

## V-Node table

- Shared by all processes
- Each entry contains most of the information in the stat structure, such as
  - st_mode
  - st_size

## Sharing Files

Descriptor table
(one table per process)

| Descriptor |
|---|
| fd0 |
| fd1 |
| fd2 |
| fd3 |
| fd4 |
| fd5 |
| fd6 |
| fd7 |

open file table
(shared by all process)
file A

| file A |
|---|
| file pos |
| refcnt = 1 |
| ... |

file B

| file B |
|---|
| file pos |
| refcnt = 1 |
| ... |

V-node table
(shared by all processes)

| file A |
|---|
| File access |
| File size |
| File type |
| ... |

| file B |
|---|
| File access |
| File size |
| File type |
| ... |
