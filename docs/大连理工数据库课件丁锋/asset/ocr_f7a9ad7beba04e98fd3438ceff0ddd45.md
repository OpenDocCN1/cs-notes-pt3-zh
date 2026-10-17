# 数据权限控制

+   • 授权与回收

```
GRANT {obj_priv_1[,obj_priv_2]...}
ON {[schema.]object[(column1[,column2])],...}
TO {user_1[,user_2]...}
[WITH GRANT OPTION];
```

```
REVOKE {obj_priv_1[,obj_priv_2]...}
ON {[schema.]object[(column1[,column2])]} }
FROM {user_1[,user_2]...}
[CASCADE|RESTRICT];
```