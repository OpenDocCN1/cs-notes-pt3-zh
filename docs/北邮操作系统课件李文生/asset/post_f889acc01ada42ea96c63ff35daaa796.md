
## Principle of Locality

- Program and data references within a process tend to cluster
- Only a few pieces of a process will be needed over a short period of time
- Possible to make intelligent guesses about which pieces will be needed in the future
- This suggests that virtual memory may work efficiently

## Working-Set Model

- Δ ≡ working-set window ≡ a fixed number of page references

  Example: 10,000 instruction
- WSSᵢ (working set size of Process Pᵢ) = total number of pages referenced in the most recent Δ (varies in time)
    - if Δ too small will not encompass entire locality.
    - if Δ too large will encompass several localities.
    - if Δ = ∞ ⇒ will encompass entire program.
- D = Σ WSSᵢ ≡ total demand frames
- if D > m ⇒ Thrashing
- Policy if D > m, then suspend one of the processes.

## Keeping Track of the Working Set

- Approximate with interval timer + a reference bit
- Example: Δ = 10,000 references
    - Timer interrupts after every 5000 time units.
    - Keep 2 in-memory bits for each page.
    - Whenever a timer interrupts, copy and set the values of all reference bits to 0.
    - If one of the bits in-memory = 1 ⇒ page in working set.
- Why is this not completely accurate?
- Improvement: 10 history in-memory bits and interrupt every 1000 time units.

## Page-Fault Frequency Scheme

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_665_0.png)

- Establish “acceptable” page-fault rate.
    - If actual rate too low, process loses frame.
    - If actual rate too high, process gains frame.

## Supplement: 缺段中断及处理

- 当CPU要访问的指令/数据不在内存中时，产生“缺段中断”。
- OS捕获中断，并调用相应的中断处理程序，进行处理。
- 缺段处理过程：

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_666_0.png)

## 9.7 Memory-Mapped Files

- Memory-mapped file I/O allows file I/O to be treated as routine memory access by **mapping** a disk block to a page in memory
- A file is initially read using demand paging. A page-sized portion of the file is read from the file system into a physical page. Subsequent reads/writes to/from the file are treated as ordinary memory accesses.
- Simplifies file access by treating file I/O through memory rather than **read()** and **write()** system calls
- Also allows several processes to map the same file allowing the pages in memory to be shared

## Memory Mapped Files

process A
virtual memory

process B
virtual memory

physical memory

disk file

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_668_0.png)

```c
// now obtain a mapping for it
hMapFile = CreateFileMapping(hFile, // file handle
        NULL,  // default security
        PAGE_READWRITE,  // read/write access to mapped pages
        0,       // map entire file
        0,
        TEXT("SharedObject"));          // named shared memory object
if (hMapFile == NULL) {
        fprintf(stderr, "Could not create mapping (%d).\n", GetLastError());
        return -1;
}

// now establish a mapped viewing of the file
lpmapAddress =
MapViewOfFile(hMapFile,FILE_MAP_ALL_ACCESS,0,0,0);
if(lpmapAddress == NULL) {
        printf("Could not map view of file (%d).\n", GetLastError());
        return -1;
}

// write to shared memory
sprintf(lpmapAddress,"%s","Shared memory message");

while (1);
// remove the file mapping
UnmapViewOfFile(lpmapAddress);

// close all handles
CloseHandle(hMapFile);
CloseHandle(hFile);
}

## memory-mapping files in Win32--consumer

```c
#include <stdio.h>
#include <windows.h>

int main(int argc, char *argv[]) {
HANDLE hMapFile;
LPVOID lpMapAddress;

hMapFile = OpenFileMapping(FILE_MAP_ALL_ACCESS,    // read/write permission
    FALSE,          // Do not inherit the name
    TEXT("SharedObject")); // name of the mapped file object

if (hMapFile == NULL)
{
    printf("Could not open file mapping object (%d).\n", GetLastError());
    return -1;
}
```
