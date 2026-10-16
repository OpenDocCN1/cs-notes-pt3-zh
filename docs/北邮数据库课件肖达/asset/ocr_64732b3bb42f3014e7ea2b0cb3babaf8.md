# 综合举例：学生-课程数据库

+   - Student(Sno, Sname, Ssex, Sage, Sdept)
+   - Course(Cno, Cname, Cpno, Ccredit)
+   - SC(Sno, Cno, Grade)

[例8] 查询选修了2号课程的学生学号。
π_Sno (σ_Cno='2' (SC)) = { 200215121, 200215122 }

[例9] 查询至少选修了一门其直接先行课为5号课程的学生姓名
π_Sname(σ_Cpno='5'(Course ▷◁ SC ▷◁ Student))
或 π_Sname(σ_Cpno='5'(Course) ▷◁ SC ▷◁ π_Sno, Sname(Student))
或 π_Sname (π_Sno (σ_Cpno='5' (Course) ▷◁ SC) ▷◁ π_Sno, Sname (Student))

[例10] 查询选修了全部课程的学生号码和姓名。
π_Sno, Cno (SC) ÷ π_Cno (Course) ▷◁ π_Sno, Sname (Student)