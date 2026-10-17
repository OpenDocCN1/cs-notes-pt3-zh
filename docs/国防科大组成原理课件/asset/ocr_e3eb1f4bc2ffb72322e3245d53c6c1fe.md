# 瑞士军刀 - LMbench

+   - HP以色列海法实验室开发的一套强大的微测试程序集，可测量许多和系统性能相关的重要因素
+   - 衡量两个关键特征：延迟和带宽
+   - 带宽就是系统中搬运数据的能力
+     - 各级cache的带宽、内存的带宽、缓存的I/O带宽等
+   - 延迟是系统的反馈时间或者开销
+     - 各级cache的访问延迟、内存访问的延迟和操作系统中某一项功能的开销

| Name | Measures |
|---|---|
| lat_connect | Latency
TCP connection |
| lat_ctx | context switch via pipe-based 'hot-potato' token passing |
| lat_dram.page | DRAM page open |
| lat_fcntl | fcntl file locking 'hot-potato' token passing |
| lat_fifo | FIFO 'hot-potato' token passing |
| lat_fs | file creation and deletion |
| lat_http | http GET request latency |
| lat_mem_rd | memory read |
| lat_mmap | mmap operation |
| lat_ops | basic operations (xor, add, mul, div, mod) on (relevant) basic data types (int, int64, float,double) |
| lat_pagefault | page fault handler |
| lat_pipe | pipe 'hot-potato' token passing |
| lat_pmake | time to complete N parallel jobs that each do usecs-worth of work |
| lat_proc | procedure call overhead and process creation using fork, fork and execve, and fork and sh |
| lat_rand | random number generator |
| lat_rpc | SUN RPC procedure call |
| lat_select | select operation |
| lat_sem | semaphore 'hot-potato' token passing |
| lat_sig | signal handle installation and handling |
| lat_syscall | open, close, getpid, write, stat, fsstat |
| lat_tcp | TCP 'hot-potato' token passing |
| lat_udp | UDP 'hot-potato' token passing |
| lat_unix | UNIX 'hot-potato' token passing |
| lat_unix.connect | UNIX socket connection |
| lat_usleep | usleep, select, pselect, nanosleep, settimer timer resolution |
| bw_file_rd | Bandwidth
read and then load into processor |
| bw_mem | read, write, and copy data to/from memory |
| bw_mmap.rd | read from mmap'ed memory |
| bw_pipe | pipe inter-process data copy |
| bw_tcp | TCP inter-process data copy |
| bw_unix | UNIX inter-process |
| disk | Other
zone bandwidths and seek times |
| line | cache line size |
| linda | dl close |
| mhz | CPU clock speed |
| par_mem | memory subsystem ILP |
| par_ops | basic operation ILP |
| stream | STREAM clones [2] |
| tlb | TLB size |