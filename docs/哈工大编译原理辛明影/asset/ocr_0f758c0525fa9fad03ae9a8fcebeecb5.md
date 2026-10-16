# 9.5.3 动态作用域

```
program dynamic(input, output);
var r: real;
procedure show;
begin write(r: 5: 3) end;
procedure small;
var r: real;
begin r := 0.125; show end;
begin
r := 0.25;
show; small; writeln;
show; small; writeln
end.
```

dynamic
show small show
show small show

静态作用域

0.250 0.250
0.250 0.250