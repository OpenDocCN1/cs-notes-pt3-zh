# 2. 组描述符

每个组都有自己的描述符，内核用结构 ext2_group_desc描述。

```
struct ext2_group_desc
{
    __u32 bg_block_bitmap; /*本组数据块位图所在块号*/
    __u32 bg_inode_bitmap; /* 本组inode位图所在块号 */
    __u32 bg_inode_table; /* 本组inode表的起始块号 */
    __u16 bg_free_blocks_count; /* 组中空闲块的数目 */
    __u16 bg_free_inodes_count; /*组中空闲inode数目 */
    __u16 bg_used_dirs_count; /* 组中目录的数目 */
};
```