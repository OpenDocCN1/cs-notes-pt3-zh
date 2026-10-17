# # 4.判定/条件覆盖(Decision/Condition Coverage)

![](bbox=[0.045, 0.293, 0.414, 0.828])

使用下面两组测试数据就可以达到上述覆盖标准：

A=2, B=0, X=4

（满足 A>1, B=0, A=2, X>1的条件，执行路径sacbed, a=T; b=T）

A=1, B=1, X=1

（满足 A<=1, B!=0, A!=2, X<=1的条件，执行路径sabd, a=F; b=F）