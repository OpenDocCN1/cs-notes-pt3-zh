# 实体完整性定义(续)

[例2] 将SC表中的Sno, Cno属性组定义为码

```
CREATE TABLE SC
(Sno  CHAR(9) NOT NULL,
Cno  CHAR(4) NOT NULL,
Grade  SMALLINT,
PRIMARY KEY (Sno, Cno)  /*只能在表级定义主码*/
);
```