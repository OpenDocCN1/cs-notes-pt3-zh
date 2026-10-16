# 调用链和动态链的示例

```
program P;
var a, x : integer;
procedure Q(b: integer);
  var i: integer;
  procedure R(u: integer; v: integer);
    var c, d: integer;
  begin
    if u=1 then R(u+1, v)
    v:=(a+c)*(b-d);
  end{R};
begin
  R(1,x);
  .....
end {Q}
```

主程序P ⇒ 过程 S
⇒ 过程 Q ⇒ 过程 R
⇒ 过程 R

```
procedure S;
  var c, i:integer;
begin
  a:=1;
  .....
end. {P}
```

调用链

主程序P (P)
主程序P 过程 S (P,S)
主程序P 过程 S 过程 Q
主程序P 过程 S 过程 Q
主程序P 过程 S 过程 Q

(P,S,Q)
(P,S,Q,R)
(P,S,Q,R,R)