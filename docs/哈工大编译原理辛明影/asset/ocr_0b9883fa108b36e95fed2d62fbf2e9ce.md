# 带有继承属性L.in的翻译方案

```
D→T { L·in:=T·type } L
T→int { T·type :=integer }
T→real { T·type :=real }
L→{L₁·in :=L·in}
    L₁,id{addtype(id·entry,L·in)}
L→id { addtype(id·entry,L·in) }
```

# 例5.3 变量说明的类型定义

int a, b, c