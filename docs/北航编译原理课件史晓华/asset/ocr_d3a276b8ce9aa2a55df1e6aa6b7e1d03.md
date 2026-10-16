例:条件语句分析：

if <B> then <stmt> [else <stmt> ];

有如下分析程序：

```
procedure if_stmt;
begin
    nextsym;                         /*读下一个单词符号*/
    B;                               /*调用布尔表达式处理程序*/
    if not class='then' then
    begin
        cx := ‘缺then’              /*错误性质送cx*/
        error;                      /*调用出错处理程序*/
    end;
    else
    begin
        nextsym;
        statement
    end;
    if class=‘else’ then
    begin
        nextsym;
        statement;
    end
end if_stmt;
```