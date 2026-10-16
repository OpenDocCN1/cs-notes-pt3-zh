# 构造每个文法符号X∈V_T ∪ V_N的FIRST(X)

+   若X∈V_T，则FIRST(X)={X};

+   若X∈V_N，且有产生式X→a...，其中 a∈V_T，则把a加入到FIRST(X)中;

+   若X→ε也是产生式，则 ε 也加入到FIRST(X)中。

+   若X→Y...是产生式，且Y∈V_N，则把FIRST(Y)中的所有非ε元素加入到FIRST(X)中;

若X→Y₁Y₂...Yₖ是产生式，如果对某个i，FIRST(Y₁)、FIRST(Y₂)、...、FIRST(Yᵢ₋₁)都含有ε，即Y₁Y₂...Yᵢ₋₁ ⇒* ε，则把FIRST(Yᵢ)中的所有非ε元素加入到FIRST(X)中;

若所有FIRST(Yᵢ)均含有ε，其中i=1、2、...、k，则把ε加入到FIRST(X)中。