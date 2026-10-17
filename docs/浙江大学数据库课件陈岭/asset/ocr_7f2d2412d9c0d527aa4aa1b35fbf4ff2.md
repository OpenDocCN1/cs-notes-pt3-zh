# # Example of triggers in Oracle

```
Create or replace trigger secure_student before insert or delete or update on student
Begin
    IF ( to_char(sysdate, 'DY') in ('星期六' , '星期日' ))
    OR (to_char(sysdate, 'HH24') NOT Between 8 and 17 )
    THEN raise_application_error (-20506, '你只能在上班时间修改数据');
    END IF;
END;
```

(退出插入状态)

注：运行该程序，实际是对其进行编译，若出错，可查看数据字典中user_errors的出错信息。User_triggers登记已建立了哪些触发器及定义内容。

删除触发器：drop trigger <触发器名>;