# 建立表达式 a*4+b 的语法树

```
p₁=makeleaf(id,entrya);  
p₂=makeleaf(num,4);  
p₃=makenode(`*`,p₁,p₂);  
p₄=makeleaf(id,entryb);  
p₅=makenode(`+`,p₃,p₄);
```

![](bbox=[0.382, 0.421, 0.981, 0.983])