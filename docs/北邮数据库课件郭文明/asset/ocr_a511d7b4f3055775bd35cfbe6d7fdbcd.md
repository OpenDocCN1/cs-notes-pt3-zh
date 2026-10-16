# 4.4.3 ORACLE对象设计

+   - 对象设计举例：

```
create table emp
(empno number(5) primary key,ename varchar2(15) not null,
deptno number(3) not null constraint dept_fkey references dept)
pctfree 10 pctused 40 tablespace users
storage(initial 50K next 50K maxextents 10 pctincrease 25);
```

```
create or replace trigger inp_bill_detail_insert
after insert on inp_bill_detail for each row
begin
update pats_in_hospital set
total_costs=decode(total_costs,null,0,total_costs)+:new.costs,
total_charges=decode(total_charges,null,0,total_charges)+:new.charges
where patient_id=:new.patient_id and visit_id=:new.visit_id;
end; /
```

```
create view exam_item_dict as
select item_code,item_name from clinic_item_dict where
item_class= 'D' ;
```

```
grant select on exam_item_dict to public;
```