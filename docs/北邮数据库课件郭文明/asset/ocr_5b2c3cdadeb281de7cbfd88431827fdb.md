# 1.4.3.4 三种产品的对象关系特征

| | ORACLE | INFORMIX | DB2 UDB |
|---|---|---|---|
| 用户定义类型(UDT) | 有, 结构化的‘对象类型’ | 有, 结构化的‘行类型’ | 有, 结构化的 UDT |
| 继承 | 无 | 有 | 有 |
| UDT引用 | 有 | 无 | 有 |
| 集合类型 | 有, 嵌套表、VARRAY | 有, 集合, 多集合, 列表 | 无 |
| 用户定义函数(UDF) | 有, PL/SQL,C,Java | 有, SPL, C, Java | 有,C,Java |
| 封装的UDT | BLOB(Binary Large Object)对象 | BLOB对象 | BLOB对象 |
| 打包UDT | Cartridge | DataBlad | Extender |
| BLOB尺寸 | 4G-1 | 4T | 2G-1 |
| BLOB子串 | UDF访问 | UDF访问 | UDF访问 |