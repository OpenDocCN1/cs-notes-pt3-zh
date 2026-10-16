
## 相关子查询

+   相关子查询和C语言中的常见循环嵌套类似：

```
for (i=0;i<9;i++)
    {for (j=0;j<99;j++)
        { j=f(i);
          ……
        }
    }
```

## 带有IN谓词的子查询（续）

[例40]查询选修了课程名为“信息系统”的学生学号和姓名

```
SELECT Sno, Sname
FROM Student
WHERE Sno IN
    ( SELECT Sno
      FROM SC
      WHERE Cno IN
          ( SELECT Cno
            FROM Course
            WHERE Cname = ‘信息系统’
          )
    );
```

+   ① 首先在Course关系中找出“信息系统”的课程号，为3号
+   ② 然后在SC关系中找出选修了3号课程的学生学号
+   ③ 最后在Student关系中取出Sno和Sname

## 带有比较运算符的子查询（续）

例：假设一个学生只可能在一个系学习，并且必须属于一个系，则在[例39]可以用 = 代替 IN：

```
SELECT Sno, Sname, Sdept
FROM   Student
WHERE Sdept =
       (SELECT Sdept
        FROM   Student
        WHERE Sname=‘刘晨’);
```

## 带有比较运算符的子查询（续）

【例41】找出每个学生超过他选修课程平均成绩的课程号。

```
SELECT Sno, Cno
FROM SC x
WHERE Grade >=( SELECT AVG(Grade)
                FROM SC y
                WHERE y.Sno=x.Sno );
```

此查询为相关子查询。

## 带有比较运算符的子查询（续）

### 可能的执行过程：

+   1. 从外层查询中取出SC的一个元组x，将元组x的Sno值（200215121）传送给内层查询。
+   
+      ```sql
+      SELECT AVG(Grade)
+      FROM SC y
+      WHERE y.Sno='200215121';
+      ```
+   
+   2. 执行内层查询，得到值88（近似值），用该值代替内层查询，得到外层查询：
+   
+      ```sql
+      SELECT Sno, Cno
+      FROM SC x
+      WHERE Grade >=88;
+      ```

## 三、带有 ANY（SOME）或 ALL 谓词的子查询

### 谓词语义

+   - **ANY**：任意一个值
+   - **ALL**：所有值

## 带有ANY（SOME）或ALL谓词的子查询（续）

![](img/ef3eda0c8c755c94cf60f8794999a1a7_423_0.png)

需要配合使用比较运算符

+   - `> ANY`：大于子查询结果中的某个值
+   - `> ALL`：大于子查询结果中的所有值
+   - `< ANY`：小于子查询结果中的某个值
+   - `< ALL`：小于子查询结果中的所有值
+   - `>= ANY`：大于等于子查询结果中的某个值
+   - `>= ALL`：大于等于子查询结果中的所有值
+   - `<= ANY`：小于等于子查询结果中的某个值
+   - `<= ALL`：小于等于子查询结果中的所有值
+   - `= ANY`：等于子查询结果中的某个值
+   - `= ALL`：等于子查询结果中的所有值（通常没有实际意义）
+   - `!=（或<>）ANY`：不等于子查询结果中的某个值
+   - `!=（或<>）ALL`：不等于子查询结果中的任何一个值

## 带有ANY（SOME）或ALL谓词的子查询（续）

【例42】查询其他系中比计算机科学某一学生年龄小的学生姓名和年龄

```
SELECT Sname, Sage
FROM   Student
WHERE Sage < ANY (SELECT Sage
                 FROM   Student
                 WHERE Sdept = 'CS')
  AND Sdept <> 'CS';    /*父查询块中的条件*/
```

## 带有 ANY（SOME）或 ALL 谓词的子查询（续）

结果：

| Sname | Sage |
|---|---:|
| 王敏 | 18 |
| 张立 | 19 |

执行过程：

+   1. RDBMS执行此查询时，首先处理子查询，找出CS系中所有学生的年龄，构成一个集合(20，19)
+   2. 处理父查询，找所有不是CS系且年龄小于20或19的学生

## 用聚集函数实现[例42]

```
SELECT Sname, Sage
FROM   Student
WHERE  Sage <
       (SELECT MAX(Sage)
        FROM Student
        WHERE Sdept = 'CS')
AND    Sdept <> 'CS';
```

## 带有EXISTS谓词的子查询(续)

+   - 用嵌套查询
+   
+     ```sql
+     SELECT Sname
+     FROM Student
+     WHERE EXISTS
+           (SELECT *
+            FROM SC
+            WHERE Sno=Student.Sno AND Cno='1');
+     ```

+   - 用连接运算
+   
+     ```sql
+     SELECT Sname
+     FROM Student, SC
+     WHERE Student.Sno=SC.Sno AND SC.Cno='1';
+     ```

## 带有EXISTS谓词的子查询(续)

例：[例39]查询与“刘晨”在同一个系学习的学生。

可以用带EXISTS谓词的子查询替换：

```
SELECT Sno, Sname, Sdept
FROM Student S1
WHERE EXISTS
    (SELECT *
     FROM Student S2
     WHERE S2.Sdept = S1.Sdept AND
           S2.Sname = ‘刘晨’);
```

用EXISTS谓词代替IN谓词

## 带有EXISTS谓词的子查询(续)

[例47]查询至少选修了学生200215122选修的全部课程的学生号码。

### 解题思路：

+   - 用逻辑蕴函数表达：查询学号为x的学生，对所有的课程y，只要200215122学生选修了课程y，则x也选修了y。
+   - 形式化表示：
+     - 用P表示谓词“学生200215122选修了课程y”
+     - 用q表示谓词“学生x选修了课程y”
+     - 则上述查询为：(∀y) p → q

## 带有EXISTS谓词的子查询(续)

+   - 等价变换：
+     \[(∀y)(p \to q) ≡ ¬(∃y(¬(p \to q)))\]
+     \[≡ ¬(∃y(¬(¬p ∨ q)))\]
+     \[≡ ¬∃y(p ∧ ¬q)\]

+   - 变换后语义：不存在这样的课程y，学生200215122选修了y，而学生x没有选。
