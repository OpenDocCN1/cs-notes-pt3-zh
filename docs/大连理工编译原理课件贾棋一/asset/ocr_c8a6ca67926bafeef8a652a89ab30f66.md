# 3.4 自下而上分析

# 3.4.4 移进-归约分析的冲突

# 1. 移进-归约冲突

# 例

```
stmt → if expr then stmt
     | if expr then stmt else stmt
     | other
```

如果移进-归约分析器处于格局

```
栈                         输入
... if expr then stmt       else ... $
```