![](bbox=[0.0, 0.05, 0.13, 0.62])

而当第一次mount一个fat分区时会调用fat_read_super()，该函数有一条语句sb->s_op = &fat_sops。 fat_sops变量的成员值如下：

```
static struct super_operations fat_sops = {
    write_inode:        fat_write_inode,
    delete_inode:       fat_delete_inode,
    put_super:          fat_put_super,
    .....
};
```

super_operations就是一个抽象类，它只提供接口但并没有实现这些接口，而ext2_sops、fat_sops则是具体类，实现相应的接口。其它几个接口与此类似。