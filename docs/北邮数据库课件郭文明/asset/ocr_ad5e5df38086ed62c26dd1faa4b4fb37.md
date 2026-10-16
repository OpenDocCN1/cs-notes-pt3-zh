# 1.2.3关系代数综合例子

**例11** 列出通过以下代理商订购的商品的pid：代理商从以下的顾客处接受订单，而这些顾客从一个接受过顾客c001订单的代理商处订购了至少一个商品。

接受顾客c001订单的代理商：

$\pi_{aid}(\sigma_{cid='c001'}(O))$

从这些代理商处订购过商品的顾客：

$\pi_{cid}(\pi_{aid}(\sigma_{cid='c001'}(O)) \bowtie O)$

从这些顾客处接受过订单的代理商：

$\pi_{aid}(\pi_{cid}(\pi_{aid}(\sigma_{cid='c001'}(O)) \bowtie O) \bowtie O)$

通过上述代理商订购的商品pid：

$\pi_{pid}(\pi_{aid}(\pi_{cid}(\pi_{aid}(\sigma_{cid='c001'}(O)) \bowtie O) \bowtie O) \bowtie O)$