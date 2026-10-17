# Proof

If $r = 1$, then the sum is:

$$S = \sum_{j=0}^{n} a = (n+1)a$$

$$S = \sum_{j=0}^{n} ar^{j}$$  
$$rS = r\sum_{j=0}^{n} ar^{j}$$  
$$= \sum_{j=0}^{n} ar^{j+1}$$  
$$= \sum_{k=1}^{n+1} ar^{k}$$  
$$= \sum_{k=0}^{n} ar^{k} + \left(ar^{n+1} - a\right)$$  
$$rS = S + \left(ar^{n+1} - a\right)$$  
$$rS - S = \left(ar^{n+1} - a\right)$$  
$$S(r - 1) = \left(ar^{n+1} - a\right)$$  
$$S = \frac{\left(ar^{n+1} - a\right)}{r - 1}$$