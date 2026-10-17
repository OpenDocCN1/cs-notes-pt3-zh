# 例3：对共享变量count的互斥访问

```
Parbegin

Program A: begin
    N:=count;
    N:=N+$100;
    count:=N;
end;

Program B: begin
    M:=count;
    M:=M-$200;
    count:=M;
end;

Parend;
```

互斥执行