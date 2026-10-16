```
```pascal
program P;
var a, x : integer;
procedure Q(b: integer);
var r: integer;
  procedure R(u: integer; var v: integer);
  var c, d: integer;
  begin
    if u=1 then R(u+1, v)
    ......
    v:=(a+c)*(b-d);
    ......
  end {R}
begin
  ......
  R(1,x);
  ......
end {Q}
```
```

![](bbox=[0.618, 0.008, 0.976, 0.264])

```
```pascal
procedure S;
  var c, i: integer;
  begin
    a:=1;
    Q(c);
    ......
  end {S}
begin
  a:=0;
  S;
  ......
end. {P}
```
```