# # Graph reweighting

**Theorem.** Given a function $h: V \to \mathbb{R}$, **reweight** each edge $(u,v) \in E$ by $w_h(u,v)=w(u,v)+h(u)-h(v)$. Then, for any two vertices, all paths between them are reweighted by the same amount.

*Proof.* Let $p=v_1 \to v_2 \to \cdots \to v_k$ be a path in $G$. We have

$$w_h(p)=\sum_{i=1}^{k-1}w_h(v_i,v_{i+1})$$

$$=\sum_{i=1}^{k-1}\left(w(v_i,v_{i+1})+h(v_i)-h(v_{i+1})\right)$$

$$=\sum_{i=1}^{k-1}w(v_i,v_{i+1})+h(v_1)-h(v_k)$$

$$=w(p)+h(v_1)-h(v_k).$$

**Same amount!**

![](bbox=[0.041, 0.021, 0.145, 0.184])