```
fd=creat(pathname,mode)
```

pathname: 路径名；

mode: 共享说明；

+   1. 分配一个inode, 初始化(i_size=0, i_mode=mode, i_nlink=1,i_uid=u_uid, i_gid=u_gid)；
+   2. 填写目录项(name, i_number)；
+   3. 以写方式打开(填写inode表、file 表和u_ofile表)；
+   4. 返回文件描述符。

例子：

```
creat("d1/d2/f1", mode)
```

假设分配i_number=15, (f1,15)=>d2中(???????????????, -1)