S(S#,SN,SA,SD);
C(C#,CN,PC#);
SC(S#,C#,G)

例2：检索选修C1或C2且成绩高于70分的学生学号、课程号和成绩。

```
SELECT S#, C#, G
FROM SC
WHERE (C#='C1' OR C#='C2') AND G>=70;
```

例3：检索成绩在70至85分之间的学生学号、课程号和成绩。

```
SELECT S#, C#, G
FROM SC
WHERE G BETWEEN 70 AND 85;
```