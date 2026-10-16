# # Quorum Consensus Protocol

+   - A generalization of both majority and biased protocols

+   - Each site is assigned a weight.

+     - Let S be the total of all site weights

+   - Choose two values read quorum Q_r and write quorum Q_w

+     - Such that Q_r + Q_w > S and 2 * Q_w > S

+     - Quorums can be chosen (and S computed) separately for each item

+   - Each read must lock enough replicas that the sum of the site weights is >= Q_r

+   - Each write must lock enough replicas that the sum of the site weights is >= Q_w

+   - For now we assume all replicas are written

+     - Extensions to allow some sites to be unavailable described later