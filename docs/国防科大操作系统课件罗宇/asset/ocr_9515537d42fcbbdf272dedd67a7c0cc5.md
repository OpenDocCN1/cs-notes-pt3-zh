# 分析这个程序

+   - 总体结构——五个函数
+     init_module （创建所有的proc文件）
+     cleanup_module （清除所有创建的内容）
+     proc_read_current （当需要读current文件的内容时，由内核调用这个函数）
+     proc_read_hello （和上面类似）
+     proc_write_hello （和上面类似）