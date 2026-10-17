```
struct file {
    struct list_head            f_list;
    struct dentry   *f_dentry; /*指向与文件对象关联的dentry对象*/
    struct vfsmount         *f_vfsmnt;
    struct file_operations  *f_op; /*文件对象的操作集合*/
    unsigned int            f_flags; /*使用open()时设定的标志*/
    mode_t                  f_mode;
    loff_t                  f_pos;  /*对文件读写操作的当前位置*/
    struct fown_struct      f_owner;
    ......
};
```