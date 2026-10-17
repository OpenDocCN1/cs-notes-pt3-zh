# # Problem statements

Given n jobs and 1 processor, each job \( j_i \) has a 3-tuple \( (p_i; d_i; t_i) \) associated with it, where \( t_i \) is the number of units of processing time for job \( j_i \). \( p_i \) is a penalty if processing is not completed by deadline \( d_i \).

Aiming at selecting a subset J of n jobs such that all jobs in J can be completed by their deadline and minimizing 3.

\(\sum_{j \notin J} p_j \tag{3}\)

Representing solution space using fixed length tuple \( x[1..n] \), \( x_i = 1 \) if \( x_i \in J \), otherwise \( x_i = 0 \).