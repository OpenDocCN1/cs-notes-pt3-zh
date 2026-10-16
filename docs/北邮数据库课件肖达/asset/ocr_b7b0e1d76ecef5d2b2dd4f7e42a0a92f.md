# 自主存取控制方法（续）

■ 关系数据库系统中存取控制对象

| 对象类型 | 对象 | 操作类型 |
|---|---|---|
| 数据库模式 | 模式 | CREATE SCHEMA |
|  | 基本表 | CREATE TABLE，ALTER TABLE |
|  | 视图 | CREATE VIEW |
|  | 索引 | CREATE INDEX |
| 数据 | 基本表和视图 | SELECT，INSERT，UPDATE，DELETE，REFERENCES，ALL PRIVILEGES |