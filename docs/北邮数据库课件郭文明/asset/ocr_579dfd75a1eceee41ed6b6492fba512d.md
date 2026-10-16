# 1.2.3关系代数综合例子

**例1** 查询所有定购了至少一个价值为0.50的商品的顾客的名字。

$\pi_{\mathrm{cname}}\left((\pi_{\mathrm{pid}}(\sigma_{\mathrm{price}=0.50}(P))\bowtie O)\bowtie C\right)$

**例2** 找出全部没有在代理商a03处订购商品的顾客cid值。

$\pi_{\mathrm{cid}}(O)-\pi_{\mathrm{cid}}(\sigma_{\mathrm{aid}='a03'}(O))$

或　$\pi_{\mathrm{cid}}(C)-\pi_{\mathrm{cid}}(\sigma_{\mathrm{aid}='a03'}(O))$

**例3** 找出只在代理商a03处订购商品的顾客。

$\pi_{\mathrm{cid}}(O)-\pi_{\mathrm{cid}}(\sigma_{\mathrm{aid}\ne'a03'}(O))$