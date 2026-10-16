```
(12) procedure quicksort(m, n:integer);
(13) var i:integer;
(14) begin
(15) if (n>m) then begin
(16) i:=partition(m, n);
(17) quicksort(m, i-1);
(18) quicksort(i+1, n)
(19) end;
(20) end;
(21) begin
(22) a[0]:=-9999; a[10]:=9999;
(23) readarray;
(24) quicksort(1, 9)
(25) end.
```

program sort
procedure readarray
function partition(y
procedure quicksort