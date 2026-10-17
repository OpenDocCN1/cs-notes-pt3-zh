# # Proof of claim

d_{ij}^{(m)} = min_k \{ d_{ik}^{(m-1)} + a_{kj} \}

![](bbox=[0.367, 0.122, 0.967, 0.778])

**Relaxation!**
for \( k \leftarrow 1 \text{ to } n \)
do if \( d_{ij} > d_{ik} + a_{kj} \)
then \( d_{ij} \leftarrow d_{ik} + a_{kj} \)