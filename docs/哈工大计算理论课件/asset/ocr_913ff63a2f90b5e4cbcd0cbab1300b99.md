# Formal definition of a Turing Machines

+   So for the two ends of the tape

$q_i b v$ yields $q_j c v$  if $\delta(q_i,b)=(q_j,c,L)$

$u a q_i$ yields $u a \sqcup q_j$  if $\delta(q_i,b)=(q_j,c,R)$

note $u a q_i \sqcup$ is equivalent to $u a q_i$