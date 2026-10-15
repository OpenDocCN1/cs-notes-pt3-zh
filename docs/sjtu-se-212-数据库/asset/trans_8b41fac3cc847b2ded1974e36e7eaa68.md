

## 参照完整性中的级联操作

```sql
create table course (
    course_id   char(5) primary key,
    title        varchar(20),
    dept_name    varchar(20) references department
)
```

```sql
create table course (
    ...
    dept_name varchar(20),
    foreign key (dept_name) references department
                         on delete cascade
                         on update cascade,
    ...
)
```

级联操作的替代方式：设置为空值、设置为默认值

## 复杂的检查子句

- check (time_slot_id in (select time_slot_id from time_slot))
  - 为什么不在这里使用外键？
- 每个课程班次至少有一名教师授课。
  - 应该如何编写？
- 遗憾的是：几乎所有数据库都不支持检查子句中的子查询
  - 替代方案：触发器（后面介绍）
- `create assertion <assertion-name> check <predicate>;`
  - 同样没有任何数据库支持

## 参照完整性中的违例及处理方式

## 触发器

- “事件—条件—动作规则”
  - 当事件发生时
  - 检查条件；如果条件为真，则执行动作

```text
Create Trigger name
Before|After|Instead Of events
[ referencing-variables ]
[ For Each Row ]
When ( condition )
action
```

在 section 和 time_slot 上使用触发器来强制执行完整性约束

```sql
Create Trigger timeslot_check1 after insert on section
referencing new row as nrow
for each row
when (nrow.time_slot_id not in (select time_slot_id from time_slot))
begin
    rollback
end;
```

```sql
create trigger timeslot_check2 after delete on time_slot
referencing old row as orow
for each row
when (orow.time_slot_id not in (
                         select time_slot_id
                         from time_slot)
     and orow.time_slot_id in (
                         select time_slot_id
                         from section))
begin
    rollback
end;
```

```sql
create trigger credits_earned after update of grade on takes
referencing new row as nrow
referencing old row as orow
for each row
when nrow.grade <> 'F' and nrow.grade is not null
    and (orow.grade = 'F' or orow.grade is null)
begin atomic
    update student
    set tot_cred = tot_cred +
    (select credits
        from course
        where course.course_id = nrow.course_id)
    where student.id = nrow.id;
end;
```

## 函数与存储过程

### 过程

- SQL 提供了一种模块语言
  - 允许在 SQL 中定义过程，并使用 if-then-else 语句、for 循环和 while 循环等
- 存储过程
  - 可以将过程存储在数据库中
  - 然后使用 call 语句执行这些过程
  - 允许外部应用程序在不了解数据库内部细节的情况下操作数据库
- SQL:1999 支持函数和过程
  - 函数和过程可以直接使用 SQL 编写，也可以使用外部编程语言编写。
  - 函数对于图像和几何对象等特殊数据类型尤其有用。
    - 示例：用于检查多边形是否重叠，或比较图像相似度的函数。
  - 某些数据库系统支持表值函数，这类函数可以返回一个关系作为结果。
- SQL:1999 还支持一组丰富的命令式结构，包括
  - 循环、if-then-else、赋值

### 函数

- 定义一个函数：给定系名称，返回该系教师人数。

```sql
Create Function dept_count(dept_name varchar(20))
returns integer
begin
    declare d_count integer;
    select count(*) into d_count
    from instructor
    where instructor.dept_name = dept_name;
    return d_count;
end
```

查找教师人数超过 12 人的所有系的系名和预算。

```sql
Select dept_name, budget
From   department
Where dept_count(dept_name) > 12
```

