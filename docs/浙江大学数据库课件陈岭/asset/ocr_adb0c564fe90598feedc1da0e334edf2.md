# The combination of join type and join condition

| Join Types | Join Conditions |
|---|---|
| **inner join**<br>**left outer join**<br>**right outer join**<br>**full outer join** | **natural**<br>**on** `<predicate>`<br>**using** (A₁, A₂, ..., Aₙ) |

自然连接：R **natural** { inner join, left join, right join, full join } S

非自然连接：R { inner join, left join, right join, full join } S **on**（连接条件判断式）
**using**（同名的等值连接属性名）

★ **Key word** *Inner, outer* is optional