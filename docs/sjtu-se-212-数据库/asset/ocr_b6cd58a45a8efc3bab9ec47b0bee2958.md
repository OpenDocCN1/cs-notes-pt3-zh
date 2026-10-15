# SubQuery

Select-from-where,可以出现在哪里？

+   - Where
+   - From

Find the average instructors' salaries of those departments where the average salary is greater than $42,000.

```
select dept_name, avg_salary from
(select dept_name, avg(salary) as avg_salary
from instructor
group by dept_name
) as dept_avg (dept_name, avg_salary)
where avg_salary > 42000;
```