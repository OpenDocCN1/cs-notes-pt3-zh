# 例：过程声明的中间代码(不保存符号表)

```
procedure Q( x: real );
var u : real ;
function f( k: real ):real;
    begin
        f := k +k
    end;
begin
    u := f(50);
    y:= u * x
end;
```

```
(ENTRY, Label_f, Size_f, L_f)
(ADDF, k, k, t_0)
(ASSIG, t_0, -, f)
(ENDFUNC, _, _, _)
(ENTRY, Label_Q, Size_Q, L_Q)
(FLOAT, 50, _, t_1)
(VALACT, t_1, off_x, 2)
(CALL, Label_f, true, t_2)
(ASSIG, t_2, -, u)
(MULTF, u, x, t_3)
(ASSIG, t_3, -, y)
(ENDPROC, _, _, _)
```