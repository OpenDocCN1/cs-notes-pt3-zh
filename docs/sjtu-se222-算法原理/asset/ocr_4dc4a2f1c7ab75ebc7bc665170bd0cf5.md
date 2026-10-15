# 算术编码的压缩效率

and thus

$$B_S \le \frac{\sigma - \sum_{k=1}^{N} \log_2 p(s_k)}{N}\quad \text{bits/symbol.}\tag{1.23}$$ 

Defining $E\{\cdot\}$ as the expected value operator, the expected number of bits per symbol is

$$\bar{B}=E\{B_S\}\le \frac{\sigma - \sum_{k=1}^{N}E\{\log_2 p(s_k)\}}{N}=\frac{\sigma - \sum_{k=1}^{N}\sum_{m=0}^{M-1}p(m)\log_2 p(m)}{N}\tag{1.24}$$ 
$$\le H(\Omega)+\frac{\sigma}{N}$$ 

Since the average number of bits per symbol cannot be smaller than the entropy, we have

$$H(\Omega)\le \bar{B}\le H(\Omega)+\frac{\sigma}{N},\tag{1.25}$$ 

and it follows that

$$\lim_{N\to\infty}\{\bar{B}\}=H(\Omega),\tag{1.26}$$