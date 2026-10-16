# (3)文件使用方式

+   • 基本方式字符（单独使用是对文本文件）：

r 只读文件(读), 如无文件，产生出错信息。
If the purpose is ‘reading’, and if it exists, then the file is opened with the current contents safe otherwise an error occurs.

w 建立新文件(写)，如有同名文件，删除之。
When the mode is ‘writing’, a file with the specified name is created if the file does not exist. The contents are deleted, if the file already exists.

a 写旧文件(添加)，如无旧文件，则生成该文件。
When the mode is ‘appending’, the file is opened in the current contents safe. A file with the specified name is created if the file does not exist.