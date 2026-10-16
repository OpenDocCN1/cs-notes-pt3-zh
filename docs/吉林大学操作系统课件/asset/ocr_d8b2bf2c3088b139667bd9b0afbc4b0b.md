# 作业 #2

```
Consider the following program:  begin
var blocked: array[0..1] of boolean;  blocked[0]:=false;
turn:0..1;                         blocked[1]:=false;
procedure P(id:integer);          turn:=0;
begin                             parbegin
  repeat                           P(0); P(1)
    blocked[id]:=true;             parend;
    while turn<>id do              end.
    begin
      while blocked[1-id] do
        {nothing}
      turn:=id
    end;
    <Critical section>
    blocked[id]:=false;
    <Remainder>
  until false
end;
```

This is a software solution to the mutual exclusion problem proposed by Hyman. Find a counter example to demonstrate that this solution is incorrect. It is interesting to note that even the Communication of the ACM was fooled on this one.