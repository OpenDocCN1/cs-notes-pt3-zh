# 4.3.3.1 ORACLE逻辑备份

+   - 指定表的逻辑备份

导出一组表的处理方法与用户导出的方法一样。用TABLES关键字列举表的名字，可以导出一个或一组表。

下面的例子把ABC表与XYZ表从BGE模式中导出到缺省输出文件中：

```
exp USERID=SYSTEM/MANAGER OWNER=BGE TABLES =XYZ, ABC
```

注意EXP缺乏一些主要的功能，EXP使你不能导出一条基于SQL WHERE子句的信息。Oracle的导出文件实际上是一种专有格式。市场上有很多第三方的工具提供了这些缺少的功能。

运行exp HELP=Y会显示EXP的所有关键字及其描述。

ORACLE逻辑备份工具EXP的对应恢复工具是IMP，其用法可以参照EXP。