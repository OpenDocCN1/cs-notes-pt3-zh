# 三、嵌套过程的静态作用域

+   - 过程定义允许嵌套
+   - 最近嵌套规则

```
Program sort(input,output);
  var a: array[0..10] of integer;
    x: integer;
  procedure readarray;
    var i: integer;
    begin ... a ... end;
  prcedure exchange(i,j:integer);
    begin
      x:=a[i]; a[i]:=a[j]; a[j]:=x
    end;
```

```
procedure quicksort(m,n:integer);
  var k,v: integer;
  function partition(y,z:integer):integer;
    var i,j: integer;
    begin ... a ...;
          ... v ...;
          exchange(i,j);
          ...
    end;
  begin ... end {quicksort};
begin .... ...end {sort}.
```