# 4.2.1.1 ORACLE内存结构

+   - 共享池：

字典高速缓存含有RDBMS引擎分析SQL语句所使用的数据字典信息。在这个区域中含有段信息、安全性、访问权限和在可用的自由存储空间等信息。

共享池的大小取决于init.ora文件参数 SHARED_POOL_SIZE, 它是以字节为单位的。ORACLE 9i可以通过ALTER SYSTEM SET SHARED_POOL_SIZE动态设置。

共享区经过长期装卸和卸载数据对象会产生许多碎片，如果在共享池中没有足够的连续空间用来装载目标数据，会产生错误。这个问题可以通过运行SQL命令ALTER SYSTEM FLUSH SHARED_POOL解决。但是如果在数据库操作时，经常遇到共享池错误，就必须增大共享池。