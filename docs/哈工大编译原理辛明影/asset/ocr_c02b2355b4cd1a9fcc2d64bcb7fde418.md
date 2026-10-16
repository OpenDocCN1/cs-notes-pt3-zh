# 8.4.4 嵌套过程的符号表

Pascal等允许在过程中嵌套定义其它过程

```
program sort(input, output);
procedure readarray;
    begin ... end{ readarray };
procedure exchange( i, j : integer );
    begin ... end{ exchange };
procedure quicksort( m, n : integer );
    function partition( x, y : integer );
        begin ... end{ partition };
    begin ... end{ quicksort };
begin ... end{ sort };
```