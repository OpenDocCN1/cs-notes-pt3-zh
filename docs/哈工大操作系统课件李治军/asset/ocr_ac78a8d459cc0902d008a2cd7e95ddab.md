# get_dir完成真正的目录解析

```
static struct m_inode *get_dir(const char *pathname)
{ if((c=get_fs_byte(pathname))=='/')
    {inode=current->root; pathname++;}
else if(c) inode=current->pwd;
while(1){if(!c) return inode; //函数的正确出口
bh=find_entry(&inode,thisname,namelen,&de);
int inr=de->inode; int idev=inode->i_dev;
inode=iget(idev,inr); //根据目录项读取下一层inode}}
```

解析从此处开始！

+   ■ 核心的四句话正好对应目录树的四个
+   重点：(1)root: 找到根目录；
+   (2)find_entry: 从目录中读取目录项；
+   (3)inr: 是目录项中的索引节点号；
+   (4)iget: 再读下一层目录

![](bbox=[0.45, 0.55, 0.85, 0.88])