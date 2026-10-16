# 用分支翻译一般条件表达式

C 代码

```
val = Test ? Then_Expr : Else_Expr;
```

```
val = x>y ? x-y : y-x;
```

使用goto的版本

```
ntest = !Test;
if (ntest) goto Else;
val = Then_Expr;
goto Done;
Else:
  val = Else_Expr;
Done:
...
```

+   - 为 then 表达式和 else 表达式生成独立的代码段
+   - 执行合适的代码段