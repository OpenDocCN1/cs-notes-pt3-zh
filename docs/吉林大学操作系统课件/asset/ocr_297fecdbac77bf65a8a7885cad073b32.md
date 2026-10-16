# smount(special_pathname, directory_pathname, roflag)

special_pathname: 特殊文件名

directory_pathname: 目录文件名（安装节点）

roflag: 只读标志

+   1. 检查是否超级用户；
+   2. 找到special_pathname文件的inode(用mknode建立)；
+   3. 合法性检查（特殊块型文件）；
+   4. 找到directory_pathname节点的inode；
+   5. 如非目录或引用数大于1，错返；
+   6. 读入super block到buf，按filesys格式解释.
+   7. 安装节点inode的i_addr[0]=设备文件i_addr[0]; (dev)
+   8. 分配一个mount表项，填写（m_dev， m_bufp， m_inodep），
+   9 安装节点inode的i_flag =| IMOUNT.