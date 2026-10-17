# 6.4 参数传递

# 6.4.4 换名调用

用实参表达式对形参进行正文替换。

```
procedure swap(var x, y: integer);
  var temp: integer;
  begin
    temp := x;
    x := y;
    y := temp
  end
```

调用swap(i, a[i])