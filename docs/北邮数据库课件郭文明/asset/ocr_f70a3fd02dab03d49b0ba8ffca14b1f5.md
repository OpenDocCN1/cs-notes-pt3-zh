# 4. 1. 2. 1 初始化参数文件

+   - 初始化参数文件：

在Oracle RDBMS中，缺省的init.ora文件位于UNIX服务器上的$ORACLE_HOME/dbs目录下或NT服务器上的$ORACLE_HOME/database目录下。当创建新数据库和实例时，这个文件可被复制和重新命名。

通过查询V$PARAMETER视图，可以从数据库内部观察init.ora文件中的配置参数集。V$PARAMETER视图把所有的init.ora 参数和它们的值都列出来，并且每一个值都有一个标记符，用以指明参数值是否为服务器默认值。

通过调整初始化参数可以改善数据库系统的整体性能。

下表是init.ora参数的一些表述，详细的参数设置可参看使用手册。