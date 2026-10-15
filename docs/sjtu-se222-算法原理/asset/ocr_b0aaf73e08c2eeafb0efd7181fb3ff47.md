# Ford-Fulkerson method

For integer capacities, $O(mf^*)$, where $f^*$ is the maximum flow.
Ford-Fulkerson may **NOT** halt if the capacities are irrational, or may not converge to a value that is maximum.

![](bbox=[0.23, 0.6, 0.53, 0.89])

$r = (\sqrt{5} - 1)/2$

$p0 = \{s,v2,v3,t\}$
$p1 = \{s,v4,v3,v2,v1,t\}$
$p2 = \{s,v2,v3,v4,t\}$
$p3 = \{s,v1,v2,v3,t\}$

$p0,p1,p2,p1,p3,p1,p2,\ldots$