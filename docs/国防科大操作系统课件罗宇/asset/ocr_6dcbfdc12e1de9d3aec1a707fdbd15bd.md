# 6. struct dentry_operations

```
```c
struct dentry_operations {
    int (*d_revalidate)(struct dentry *, int);
    int (*d_hash)    (struct dentry *, struct qstr *);
    int (*d_compare) (struct dentry *,
                      struct qstr *, struct qstr *);
    ……
};
```
```

**d_revalidate**：检查dentry cache中的dentry是否是最新的。

**d_hash**：计算文件名的hash值。第一个参数是父目录，第二个参数包含了预设的文件名。

**d_compare**：比较一个目录下的两个文件名是否相等。如文件名是否区分大小写。