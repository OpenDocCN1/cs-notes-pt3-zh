# 例子：

```
smount(“/dev/disk1”，“/usr/d1”，0)
```

# 安装之前：

disk1只能作为特殊文件(块序列文件)访问(raw IO);

# 安装之后：

d1成为disk1文件卷的根目录。

disk1的super block读入内存缓冲区中，按filesys格式解释，根目录inode读入内存inode区中；

内存中inode区是所有安装文件卷共用的，因而，在内存inode中有i_dev指定inode对应的卷，用于回写。