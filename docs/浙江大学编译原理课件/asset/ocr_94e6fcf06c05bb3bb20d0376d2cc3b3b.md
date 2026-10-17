# 7.3.2 Stack-Based Environment with local Procedures

```
program nonlocalRef;

procedure p;
var n: integer;

    procedure q;
    begin
        (* a reference to n is
           now non-local and
           non-global *)
    end; (* q *)

    procedure r(n:integer);
    begin
        q;
    end; (* r *)
```

```
begin  (* p *)
    n :=1;
    r(2);
end;  (*p*)

begin (* main*)
    p;
end.
```

![](bbox=[0.778, 0.669, 0.999, 0.999])

![](bbox=[0.0, 0.909, 0.092, 0.999])