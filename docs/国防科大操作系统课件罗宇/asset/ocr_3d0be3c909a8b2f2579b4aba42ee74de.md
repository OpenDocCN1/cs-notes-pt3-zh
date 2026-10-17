# 四、文件系统的注册与安装

# 1. 文件系统驱动的注册

每一 种文件系统使用前必须先注册一个 file_system_type 对象。这可以看成是文件系统 driver 的加载。

```
struct file_system_type {
    const char *name;  /*文件类型名*/
    struct super_block * (*read_super)
        (struct super_block *, void *, int);
    struct file_system_type * next;
    ......
};
```

file_systems