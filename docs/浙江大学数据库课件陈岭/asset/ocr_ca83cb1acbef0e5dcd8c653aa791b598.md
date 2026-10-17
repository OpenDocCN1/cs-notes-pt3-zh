# Main body of program (cont.)

```
```c
{
    if (error == SQL_SUCCESS) {
        SQLBindCol(stmt, 1, SQL_C_CHAR, branchname, 80, &lenOut1);
        SQLBindCol(stmt, 2, SQL_C_FLOAT, &balance, 0, &lenOut2);
        /*对stmt中的返回结果数据加以分离，并与相应变量绑定。第1项数据转换为C的
        字符类型,送变量branchname(最大长度为80)，lenOut1为实际字符串长度(若=-1
        代表null)，第2项数据转换为C的浮点类型送变量balance中 */
        while (SQLFetch (stmt) >= SQL_SUCCESS) {
            /*逐行从数据区stmt中取数据，放到绑定变量中*/
            printf ( “%s %d\n”, branchname, balance);
            /*对取出的数据进行处理*/
            ...
        }
    }
    SQLFreeStmt (stmt, SQL_DROP); /* 释放数据区 */
}
```
```