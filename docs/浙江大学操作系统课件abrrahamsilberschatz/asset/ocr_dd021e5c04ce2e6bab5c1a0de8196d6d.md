# # Linux内存的目录管理表-3

```
```c
#define DNAME_INLINE_LEN 16
struct dentry {
	atomic_t d_count;
	unsigned int
	d_flags;
	struct inode *d_inode; /* Where the name belongs to - NULL is negative */
	struct dentry *d_parent; /* parent directory */
	struct list_head d_vfsmnt;
	struct list_head d_hash; /* lookup hash list */
	struct list_head d_lru; /* d_count = 0 LRU list */
	struct list_head d_child; /* child of parent list */
	struct list_head d_subdirs; /* our children */
	struct list_head d_alias; /* inode alias list */	struct qstr d_name;
	unsigned long d_time; /* used by d_revalidate */
	struct dentry_operations *d_op;
	struct super_block *d_sb; /* The root of the dentry tree */
	unsigned long d_refitime; /* last time referenced */
	void *d_fsdata; /* fs-specific data */
	void *d_fsdata; /* TUX-specific data */
```
```