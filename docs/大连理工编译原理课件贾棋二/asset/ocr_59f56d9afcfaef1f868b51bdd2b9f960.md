# 6.3 非局部名字的访问

program dynamic(input, output); dynamic
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

![](bbox=[0.494, 0.222, 0.966, 0.533])

动态作用域
0.250 0.125
0.250 0.125