# An improved heuristic

![](bbox=[0.08, 0.27, 0.42, 0.62])

Algorithm 15.1 ETSPAPPROX
Input: A set S of n points in the plane.
Output: An Eulerian tour τ of S.
1. Construct a minimum spanning tree T of S
2. Identify the set X of odd degree vertices in T
3. Find a minimum weight matching M on X
4. Find a Eulerian tour τₑ in T ∪ M
5. Traverse τₑ edge by edge and bypass every previously visited vertex.
6. Let τ be the resulting tour

Theorem R < 3/2.

OPT(I) > MST(I)
OPT(I) >= 2Matching(I)
MST(I) + Matching(I) > A(I)