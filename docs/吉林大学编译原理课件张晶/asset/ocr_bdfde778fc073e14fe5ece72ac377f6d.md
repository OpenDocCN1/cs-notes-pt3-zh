# 例子

例： (M, P, Q, R) 为R的声明链，假设有当前调用链是 ( M, P¹, P², Q¹, R¹, R², R³ )

则当前动态链为：

[AR(M), AR(P¹), AR(P²), AR(Q¹), AR(R¹), AR(R²), AR(R³)]

R的当前变量访问环境VarVisitEnv(LAR(R)) = [LAR(M), LAR(P), LAR(Q), LAR(R)] = [AR(M), AR(P²), AR(Q¹), AR(R³)]

Level(M)=0,Level(P)=1,Level(Q)=2,Level(R)=3,即层数为L的过函，其变量访问环境包含L+1项AR地址