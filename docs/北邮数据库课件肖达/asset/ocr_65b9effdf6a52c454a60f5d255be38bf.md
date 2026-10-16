# 模式与表（续）

+   - DBA用户可以设置搜索路径，然后定义基本表

```
SET search_path TO “S-T”, PUBLIC;

Create table Student（……）;
```

结果建立了S-T.Student基本表。

RDBMS发现搜索路径中第一个模式名S-T存在，就把该模式作为基本表Student所属的模式。