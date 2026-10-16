
## 子查询嵌套检索（5）

- 用 EXISTS 检索
  - EXISTS 表示存在量词“∃”。
  - 表达式 EXISTS（子查询）
    当且仅当子查询结果为非空时为真。

例5：检索选修C2课程的学生姓名。

```sql
SELECT SN
FROM S
WHERE EXISTS
      (SELECT * FROM SC
       WHERE S#=S.S# AND C#='C2');
```

- 用 NOT EXISTS 检索
  - 表示“不存在”。
  - 表达式 NOT EXISTS（子查询）在子查询结果为空时为真。

## 子查询嵌套检索（7）

S(S#,SN,SA,SD); C(C#,CN,PC#); SC(S#,C#,G)

- 用NOT EXISTS 表达蕴涵

¬ p→q ≡ ¬ p ∨ q

(∀y) p→q ≡ ¬ (∃y (¬ (p→q))) ≡ ¬ (∃y (¬ (¬ p ∨ q))) ≡ ¬ ∃y (p ∧ ¬ q)

例7：检索至少选修了学生S2选修的全部课程的学生学号。

本题用蕴含表达：

> “检索这样学生的学号，对于任意课程，只要S2选修，他就选修。”

本题等价于“检索这样学生的学号，不存在S2选修而他没有选修的课程”。

```sql
SELECT DISTINCT S#
FROM SC SCX
WHERE NOT EXISTS
(SELECT * FROM SC SCY
WHERE SCY.S#='S2' AND NOT EXISTS
(SELECT * FROM SC SCZ
WHERE S#=SCX.S# AND C#=SCY.C#));
```

检索S2选修而SCX.S#没有选修的课程

检索SCX.S#选修SCY.C#的记录

## 并、差、交检索（1）

- 并、差、交的SQL运算符：
  - 并： UNION
  - 差： MINUS
  - 交： INTERSECT
- 并、差、交检索的操作对象必须是相容的，即必须有相同数量的属性列，且相应属性列的域也必须相同。

## 并、差、交检索（2）

S(S#,SN,SA,SD);  
C(C#,CN,PC#);  
SC(S#,C#,G)

例1：检索选修了C1或C2课程的学生学号。

```sql
SELECT S#  FROM SC  WHERE C#='C1'
UNION
SELECT S#  FROM SC  WHERE C#='C2';
```

例2：检索无人选修的课程号和名称。

```sql
SELECT C#, CN  FROM C  WHERE C# IN
(SELECT C# FROM C
MINUS
SELECT DISTINCT C#  FROM SC);
```

## 库函数检索（1）

- 库（集）函数
  - COUNT() 按列值计个数，COUNT(*) 对行计数。
  - SUM() 对数值列求总和
  - AVG() 求数值列的平均值
  - MAX() 在列中找出最大值
  - MIN() 在列中找出最小值

## 库函数检索（2）

S(S#,SN,SA,SD);  
C(C#,CN,PC#);  
SC(S#,C#,G)

例1：检索学生总数。

```sql
SELECT COUNT (*) FROM S;
```

例2：检索选修了课程的学生人数。

```sql
SELECT COUNT (DISTINCT S#) FROM SC;
```

例3：求学号为S4的学生的总分和平均分。

```sql
SELECT SUM (G), AVG (G)
FROM SC
WHERE S#='S4';
```

例4：检索选修了C1课程的学生最高分。

```sql
SELECT MAX (G) FROM SC WHERE C#='C1';
```

## 分组检索（1）

- 按属性列（列组）将关系的元组分组，每组在这些分组属性列（列组）上具有相同值，对每一组可执行SELECT操作。
- 分组子句：
  - GROUP BY 列名
  - [ HAVING 条件表达式] ——分组条件
- WHERE子句与HAVING子句
  - WHERE 子句是针对“行”进行，用于去掉不符合条件的若干行；HAVING子句针对“分组”进行，必须和GROUP BY 连用，用于去掉不符合条件的若干分组。
  - 在查询块中出现的顺序：WHERE — GROUP BY — HAVING

## 分组检索（2）

S(S#,SN,SA,SD);  
C(C#,CN,PC#);  
SC(S#,C#,G)

例1：检索至少选修三门课程的学生学号和选课门数。

```sql
SELECT S#, COUNT (*)
FROM SC
GROUP BY S#
HAVING COUNT (*) >=3;
```

例2：求选修四门以上课程的学生学号和总成绩（不统计不及格的课程）。最后按降序列出总成绩排序名单。

```sql
SELECT S#, SUM (G)
FROM SC
WHERE G>=60
GROUP BY S#
HAVING COUNT (*) >=4
ORDER BY SUM(G) DESC;
```

## 算术表达式值的检索

- SELECT子句中，可包括由属性列、常数、库函数、算术运算符+-*/等组成的算术表达式。
- 检索结果数据项名可用表达式表示或用“别名”来表示。

例1：有职工表EMP (EMP#, EMPN, JOB, SALARY, BONUS, DEPT)，要求检索所有PROGRAMMER的奖金大于工资25%的职工姓名和一年的总收入，并按奖金与工资之比的降序排列。

```sql
SELECT EMPN, BONUS/SALARY  BS,
       12* (SALARY+BONUS)  TOTAL
FROM EMP
WHERE JOB='PROGRAMMER'
  AND BONUS>0.25*SALARY
ORDER BY BONUS/SALARY DESC ;
```

## 部分匹配查询

- 使用谓词LIKE 或NOT LIKE，一般形式：
  - `<列名> LIKE/NOT LIKE <字符串常量>`
- “列名” 必须为字符型或变长字符型。
- “字符串常量” 可包含两个特殊符号 % 与 _
  - %：代表任意序列的0个或多个字符；
  - _：代表任意单个字符

例1：检索所有姓刘的学生学号、姓名。

```sql
SELECT S#, SN
FROM S
WHERE SN LIKE '刘%';
```

## SQL数据定义功能

- 定义、删除、修改基本表
- 定义、删除索引
- 定义、删除视图

| 操作对象 | 创建 | 删除 | 修改 |
| --- | --- | --- | --- |
| 表 | Create Table | Drop Table | Alter Table |
| 视图 | Create View | Drop View | |
| 索引 | Create Index | Drop Index | |

## SQL92的数据类型

- char（n）：固定长度的字符串。
- varchar（n）：可变长字符串。
- int：整数。
- smallint：小整数类型。
- numeric（p，q）：定点数共p位，小数点右边q位。
- Real，double precision：浮点数与双精度浮点数，精度与机器有关。
- Float(n)：n位的精度浮点数。
- date：日期（年、月、日）。
- time：时间（小时、分、秒）。
- interval：两个date或time类型数据之间的差

## 示例

```sql
Create table S
(S# char(5) not null unique,
SN char(20) not null,
SA int,
SD char(15),
Primary key(S#),
Check (SA >=18 and SA <=45));

Create table SC
(S# char(5) not null,
C# char(5) not null,
G number(4,2),
Primary key (S#, C#),
Foreign key (S#) references S (S#),
Foreign key (C#) references C (C#));
```

## 修改、删除基本表定义

### 修改基本表

- 语法：`Alter Table <表名>`
  - [Add <新列名><数据类型>[<完整性约束>]]
  - [Drop <完整性约束名>]
  - [Modify <列名><数据类型>]
- 示例：
  - 例1：S表增加 “入学时间” 属性

    ```sql
    Alter Table S Add Scome Date ;
    ```
  - 例2：将SA的数据类型改为半字长整数

    ```sql
    Alter Table S Modify SA Smallint
    ```

### 删除基本表

- 语法：`Drop Table <表名>`
- 示例：`Drop Table S;`
