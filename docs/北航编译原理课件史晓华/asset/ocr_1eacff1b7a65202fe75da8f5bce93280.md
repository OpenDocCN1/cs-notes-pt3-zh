# 过程说明（定义）的ATG文法如下：

形参数计数，j初值为0

```
<proc defn>→<proc defn head> @initcnt↓j
<parameters>↓j↑k @emitstores↓k
<proc defn head>→procedure↓t <id>↑n @tblinsert↓t,n
<parameters>↓j↑k → @echo↓j↑k | (<parm list>↓j↑k)
<parm list>↓j↓l → <type>↑t : <id>↑n @tblinsert↓t,n
<parms>↓j↑l → @echo↓j↑l | , <type>↑t : <id>↑n @tblinsert↓t,n
@upcnt↓j↑k <parms>↓k↑l
```

形参名填表

K := j ++

K := j

l := j

# @tblinsert 是把过程名和它的形参名填入符号表中：

```
procedure tblinsert( t, n );
string t, n; integer hloc;
if lookup ( n ) > 0
then error(‘名字定义重复’, statno);
else begin
  hloc := hashfctn(n); /*求散列函数值*/
```

```
hashtbl[hloc] := s; /*s为符号表指针（下标），为全局量*/
symbtbl [s].name:= n;
symbtbl [s].type:= t;
s := s+1;
end;
```