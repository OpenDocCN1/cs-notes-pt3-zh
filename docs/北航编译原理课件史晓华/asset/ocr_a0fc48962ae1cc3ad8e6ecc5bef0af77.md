# 5. 符号串集合的幂运算：有符号串集合A，定义

A⁰={ε},      A¹=A,      A²=AA,      A³=AAA,

…… …… Aⁿ=Aⁿ⁻¹A=AAⁿ⁻¹ ， n>0

# 6. 符号串集合的闭包运算：设A是符号串集合，定义

A⁺= A¹ ∪ A² ∪ A³ ∪……∪ Aⁿ ∪……

称为集合A的正闭包。

A*= A⁰ ∪ A⁺

称为集合A的闭包。

例：A={x,y}

A⁺={x,y, xx,xy,yx,yy, xxx,xxy,xyx,x yy,yxx,yxy,yyx,yyy, ……}

A*={ε, x,y, xx,xy,yx,yy, xxx,xxy,xyx,x yy,yxx,yxy,yyx,yyy, ……}