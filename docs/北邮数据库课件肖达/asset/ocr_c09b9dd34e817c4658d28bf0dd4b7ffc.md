# 学生表Student

[例5] 建立“学生”表Student，学号是主码，姓名取值唯一。

```
CREATE TABLE Student
(Sno CHAR(9) PRIMARY KEY, /* 列级完整性约束条件 */
Sname CHAR(20) UNIQUE, /* Sname取唯一值 */
Ssex CHAR(2),
Sage SMALLINT,
Sdept CHAR(20)
);
```

主码