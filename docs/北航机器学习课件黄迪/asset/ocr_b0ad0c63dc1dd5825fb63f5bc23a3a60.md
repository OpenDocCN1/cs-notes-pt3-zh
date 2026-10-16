# ID3算法

# 条件熵-推导

H(X|Y) = H(X,Y) - H(Y)
= -∑_{x,y} p(x,y) log₂ p(x,y) + ∑_{y} p(y) log₂ p(y)
= -∑_{x,y} p(x,y) log₂ p(x,y) + ∑_{y} (∑_{x} p(x,y)) log₂ p(y)
= -∑_{x,y} p(x,y) log₂ p(x,y) + ∑_{x,y} p(x,y) log₂ p(y)
= -∑_{x,y} p(x,y) log₂ [p(x,y)/p(y)]
= -∑_{x,y} p(x,y) log₂ p(x|y)