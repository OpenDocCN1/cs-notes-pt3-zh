# 4.4 谓词Horn逻辑中的自动推理

对两个表达式e₁， e₂作合一的算法如下

//算法返回一个合一置换或“无法合一”的信息

```
Unify(e₁, e₂)
{ θ=空集;
    if e₁是变量符号x then θ={ e₂/x};
    else if e₂是变量符号x then θ={ e₁/x};
    else if(e₁是常量而e₂不是，或e₂是常量而e₁不是，
            或 e₁， e₂是两个不同的常量)
        then return “无法合一”
    else //此时e₁， e₂形如f(t₁,…,tₙ)和
            g(s₁,…,sₘ)； f,g为函数符号。
```