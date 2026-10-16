```
nrd=read(fd,buf,count)
```

fd: 文件描述符；

buf: 进程空间接收区地址；

count: 读字节数；

+   1. 由u_ofile[fd]，找到file表对应入口；

+   2. 检查访问权限(f_flag, READ);

+   3. 由f_inode找到内存inode入口；

+   4. 由f_offset, count和i_addr计算访问磁盘块号(可能多个块)(bmap函数);

+   5. 启动IO设备读取盘块到系统缓冲区中(如buffer无,切换进程);

+   6. 缓冲区信息复制到进程空间(iomove);

+   7. 返回实际传输字节数nrd。