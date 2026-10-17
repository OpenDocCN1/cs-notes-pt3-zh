# dentry对象: dentry对象主要是描述文件名及其相关联的inode信息。

```
struct dentry {
    struct inode * d_inode; /* 该dentry对象所属的inode */
    struct dentry * d_parent; /* 父目录 */
    struct list_head d_hash; /* hash值相同的dentry链表*/
    struct list_head d_subdirs;/* 子目录链表*/
    struct qstr d_name;          /* 文件名及附属信息*/
    struct dentry_operations *d_op;
    .....
};
```

![](bbox=[0.0, 0.05, 0.15, 0.95])