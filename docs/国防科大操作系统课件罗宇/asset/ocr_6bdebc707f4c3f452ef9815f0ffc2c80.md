# Reader的一般结构为：

```
P(mutext);
readcount := readcount+1;
If readcount=1 then P(wrt);
V(mutext);
读数据A
P (mutext);
readcount := readcount-1;
If readcount=0 then V(wrt);
V(mutext);
```