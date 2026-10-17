

## 单表查询

### 聚集函数

- 例：查询学生总人数。

```sql
SELECT COUNT(*) FROM Student;
```

- 例：查询选修了课程的学生人数。

```sql
SELECT COUNT(DISTINCT Sno) FROM SC;
```

> 注意：用DISTINCT以避免重复计算学生人数

### 聚集函数

- 例：计算1号课程的学生平均成绩。

```sql
SELECT AVG(Grade) FROM SC
WHERE Cno= '1';
```

- 例：查询选修1号课程的学生最高分数。

```sql
SELECT MAX(Grade) FROM SC
WHERE Cno= '1';
```

### 查询结果分组

```sql
SELECT
[ALL|DISTINCT]
<column|expression>[, <column|expression>]...
FROM
<table|view>[, <table|view>]...
[WHERE <condition(s)>]
[GROUP BY <column>[HAVING<condition(s)_1>]]
[ORDER BY <column2>[ASC|DESC]]
```

- 使用GROUP BY子句分组
  - 细化聚集函数的作用对象
    - 未对查询结果分组，聚集函数将作用于整个查询结果
    - 对查询结果分组后，聚集函数将分别作用于每个组
  - 只有满足HAVING短语指定条件的组才输出

### 查询结果分组

- 例：求各个课程号及相应的选课人数。

```sql
SELECT Cno, COUNT(Sno) FROM SC GROUP BY Cno;
```

例：查询选修了3门以上课程的学生学号。

```sql
SELECT Sno FROM SC
GROUP BY Sno HAVING COUNT(*) >3;
```

### 查询结果分组

- GROUP BY子句的作用对象是查询的中间结果表
- 分组方法：按指定的一列或多列值分组，值相等的为一组
- 使用GROUP BY子句后，SELECT子句的列名列表中只能出现分组属性和聚集函数

### 查询结果分组

练习：查询有3门以上课程是90分以上的学生的学号及（90分以上的）课程数

```sql
SELECT Sno, COUNT(*) FROM SC
WHERE Grade>=90
GROUP BY Sno HAVING COUNT(*)>=3;
```

### 查询结果分组

HAVING短语与WHERE子句的区别：作用对象不同

- WHERE子句作用于基表或视图，从中选择满足条件的元组。
- HAVING短语作用于组，从中选择满足条件的组。

## 连接查询

### 基本含义

同时涉及多个表的查询称为连接查询
- 用来连接两个表的条件称为连接条件或连接谓词
  一般格式：

```
［<表名1>．］<列名1>  <比较运算符>  ［<表名2>．］<列名2>
```

比较运算符：=、>、<、>=、<=、!=

```
［<表名1>．］<列名1> BETWEEN ［<表名2>．］<列名2>
                         AND ［<表名2>．］<列名3>
```

### 连接字段

连接谓词中的列名称为连接字段
连接条件中的各连接字段类型必须是可比的，但不必是相同的

### SQL中连接查询的主要类型

- 广义笛卡尔积
- 等值连接(含自然连接)
- 非等值连接查询
- 自身连接查询
- 外连接查询
- 复合条件连接查询

### 等值连接

连接运算符为 = 的连接操作

```
[<表名1>.]<列名1> = [<表名2>.]<列名2>
```

任何子句中引用表1和表2中同名属性时，都必须加表名前缀。引用唯一属性名时可以加也可以省略表名前缀。

例：查询每个学生及其选修课程的情况。

```sql
SELECT Student.*, SC.* FROM Student, SC
WHERE Student.Sno = SC.Sno;
```

### 自然连接

等值连接的一种特殊情况，把目标列中重复的属性列去掉。

例：查询每个学生及其选修课程的情况。

```sql
SELECT Student.Sno, Sname, Ssex, Sage,
       Sdept, Cno, Grade
FROM   Student, SC WHERE Student.Sno = SC.Sno;
```

### 非等值连接

连接运算符 不是 = 的连接操作

[<表名1>.]<列名1> <比较运算符> [<表名2>.]<列名2>

比较运算符： >、 <、 >=、 <=、 !=

[<表名1>.]<列名1> BETWEEN [<表名2>.]<列名2>  
AND [<表名2>.]<列名3>

### 外连接

外连接与普通连接的区别

- 普通连接操作只输出满足连接条件的元组
- 外连接操作以指定表为连接主体，将主体表中不满足连接条件的元组一并输出

例: 查询每个学生及其选修课程的情况，即使学生一门课也没有选也要输出学生信息。

```sql
SELECT Student.Sno,Sname,Ssex,Sage,Sdept,Cno,Grade
FROM Student LEFT JOIN SC
ON Student.Sno = SC.Sno;
```

### 复合条件连接

WHERE子句中含多个连接条件时，称为复合条件连接

例：查询选修2号课程且其成绩在90分以上的所有学生的学号、姓名

```sql
SELECT Student.Sno, student.SName
FROM Student, SC
WHERE Student.Sno = SC.Sno AND /* 连接谓词*/
SC.Cno= '2' AND /* 其他限定条件 */
SC.Grade > 90;
```

### 多表连接

例：查询每个选修了课程的学生的学号、姓名、选修的课程名及成绩。

```sql
SELECT Student.Sno, Sname, Cname, Grade
FROM Student, SC, Course
WHERE Student.Sno = SC.Sno AND SC.Cno = Course.Cno;
```

## 嵌套查询（子查询）

例：查询选修了2号课程的学生的姓名

```sql
SELECT Sname
FROM Student
WHERE Sno IN
( SELECT Sno
FROM SC
WHERE Cno= '2' );
```

子查询的限制：不能使用ORDER BY子句

注意：有些嵌套查询可以用连接运算替代

### 带有IN谓词的子查询

例：查询选修课程名为“信息系统”的学生学号和姓名

```sql
SELECT Sno, Sname
FROM Student
WHERE Sno IN(
SELECT Sno
FROM SC
WHERE Cno IN(
SELECT Cno
FROM Course
WHERE Cname = '信息系统'
) );
```

① 首先找出 Course 关系中“信息系统”的课程号 (3)
② 然后在 SC 关系中找出选修了3号课程的学生学号
③ 最后在 Student 关系中取出 Sno 和 Sname

### 例：查询选修课程名为“信息系统”的学生学号和姓名-使用连接方法

```sql
SELECT Sno, Sname
FROM Student, SC, Course
WHERE Student.Sno = SC.Sno  AND
      SC.Cno = Course.Cno AND
      Course.Cname='信息系统';
```

