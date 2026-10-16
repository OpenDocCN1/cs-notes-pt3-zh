```
begin
:
end;{P2}
procedure q2;
var r1,r2 : real;
begin
:
P2(r1+r2);
:
end; {q2}
begin
:
P2(x/y);
:
end;{M1}
begin
:
M1(i+k);
:
end {main}
```

```
program main(...);
var
x, y : real; i, k: integer;
name: array [1...16] of char;
:
procedure M1 (ind:integer);
var x : integer;
procedure P2 (j : real);
:
procedure P3;
var
f : array [1...5] of integer
test1: boolean;
begin
:
end; {P3}
begin
:
end;{P2}
procedure q2;
var r1,r2 : real;
begin
:
p2(r1+r2);
end; {q2}
begin
:
P2(x/y);
:
end;{M1}
begin
:
M1(i+k);
:
end {main}
```