# 库函数检索（2）

S(S#,SN,SA,SD);  
C(C#,CN,PC#);  
SC(S#,C#,G)

例1：检索学生总数。  

```sql
SELECT COUNT (*) FROM S；
```

例2：检索选修了课程的学生人数。  

```sql
SELECT COUNT (DISTINCT S#) FROM SC；
```

例3：求学号为S4的学生的总分和平均分。  

```sql
SELECT SUM (G)，AVG (G)
FROM SC
WHERE S#='S4'；
```

例4：检索选修了C1课程的学生最高分。  

```sql
SELECT MAX (G) FROM SC WHERE C#='C1'；
```