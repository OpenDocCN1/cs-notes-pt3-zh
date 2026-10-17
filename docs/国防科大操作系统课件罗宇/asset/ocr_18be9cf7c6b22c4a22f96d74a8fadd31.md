# 一、 字符设备管理

+   • 字符设备管理的主要数据结构如下：

```
struct device_struct {
    const char * name;
    struct file_operations * fops;
};
static struct device_struct chrdevs[MAX_CHRDEV];
```

全局数组chrdevs[]记录了所有字符设备驱动程序的名称name及其对应的设备操作函数接口fops。数组的下标，则对应于设备的主设备号。