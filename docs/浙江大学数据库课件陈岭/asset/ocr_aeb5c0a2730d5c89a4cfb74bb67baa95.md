# Example 2: Find all customers who have an account at all branches located in Brooklyn city.

Πcustomer-name, branch-name (depositor ⋈ account) ÷ Πbranch-name (σbranch-city = “Brooklyn” (branch))

# example 3: 查询选修了全部课程的学生学号和姓名。

+   涉及表: 课程信息course(cno, cname,pre-cno,score), 选课信息sc(sno,cno,grade), 学生信息student(sno, sname, sex, age)

+   当涉及到求 “全部” 之类的查询， 常用 “除法”

+   找出全部课程号： Πcno (Course)

+   找出选修了全部课程的学生的学号：

ΠSno, Cno (SC) ÷ Πcno (Course)

+   与student表自然连接（连接条件Sno）获得学号、姓名

( ΠSno, Cno (SC) ÷ Πcno (Course)) ⋈ ΠSno,Sname(student)