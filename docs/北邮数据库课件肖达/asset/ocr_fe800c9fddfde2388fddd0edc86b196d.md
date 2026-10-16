# 传播权限（续）

执行了［例1］到［例7］后，学生-课程数据库的用户权限定义表

| 授权用户名 | 被授权用户名 | 数据库对象名 | 操作类型 | 能否转授权 |
|---|---|---|---|---|
| DBA | U1 | 关系Student | SELECT | 不能 |
| DBA | U2 | 关系Student | ALL | 不能 |
| DBA | U2 | 关系Course | ALL | 不能 |
| DBA | U3 | 关系Student | ALL | 不能 |
| DBA | U3 | 关系Course | ALL | 不能 |
| DBA | PUBLIC | 关系SC | SELECT | 不能 |
| DBA | U4 | 关系Student | SELECT | 不能 |
| DBA | U4 | 属性列Student.Sno | UPDATE | 不能 |
| DBA | U5 | 关系SC | INSERT | 能 |
| U5 | U6 | 关系SC | INSERT | 能 |
| U6 | U7 | 关系SC | INSERT | 不能 |