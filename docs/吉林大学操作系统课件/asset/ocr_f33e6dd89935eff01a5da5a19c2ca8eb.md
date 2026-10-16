# 程序（Cont.）

```
begin
    read_count:=0;
    r_w_w.value:=1;
    mutex.value:=1;
    cobegin
        r1: reader; .....; rm: reader;
        w1: writer; ,,,,,; wn: writer
    coend
end.
```