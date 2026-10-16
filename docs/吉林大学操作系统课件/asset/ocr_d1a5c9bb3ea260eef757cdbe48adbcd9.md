# 有关文件的系统调用命令

+   - 写文件 n_wt=write(fd, buf, bytes)
+     - 由u_ofile[fd], 找到file表对应入口
+     - 检查访问权限(f_flag, WRITE)
+     - 由f_inode找到内存inode入口
+     - 由f_offset, count和i_addr计算磁盘地址块号(可能分配盘块)
+     - 申请系统缓冲区，将buf起始count数据送到缓冲区中(可多次)
+     - 缓冲区链到设备I/O链上,如设备空闲启动设备
+     - 修改inode中文件长度i_size
+     - 返回实际传输字节数nwt