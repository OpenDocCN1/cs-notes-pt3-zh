# 有关文件的系统调用命令

+   建立文件链接 link(old_name,new_name)
+   查目录找到oldpathname(inode)
+   查目录找到newpathname的末级目录
+   检查操作合法性
+   Inode的i_nlink++
+   (name, i_number) 末级目录

+   断开文件链接 unlink(path_name)
+   查目录找到pathname(inode)
+   i_nlink--; 如结果为0, 释放所有磁盘块 (删除文件)
+   清除末级文件名在末级目录中的登记