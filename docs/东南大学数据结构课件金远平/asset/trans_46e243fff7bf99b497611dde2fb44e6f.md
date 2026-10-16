

``` 
1 void MatrixDigraph::ShortestPath(const int n, const int v)
2 {//dist[j],0≤j<n, is set to the length of the shortest path(v-j)
3 //in a digraph G with n vertices and edge lengths in length[i][j]
4   for (int i=0; i<n; i++) { s[i]=false; dist[i]=length[v][i];}
5   s[v]=true;
6   dist[v]=0;
7   for (i=0; i<n-2; i++) { //determine n-1 paths from v
8     int u=choose(n); //choose returns a value u such that
9                     //dist[u]=minimum dist[w], where s[w]=false
10    s[u]= true;
11    for ( int w=0; w<n; w++)
12      if (!s[w] && dist[u]+length[u][w]<dist[w])
13        dist[w]=dist[u]+length[u][w];
14  }
}
```

## The running status of ShortestPath for the example:

| vertex | dist |  |  |  |  |  |
|---|---|---:|---:|---:|---:|---:|
|  | 0 | 1 | 2 | 3 | 4 | 5 |
| 0 | 0 | 50 | 45 | 10 | +∞ | +∞ |
| 3 | 0 | 50 | 45 | 10 | 25 | +∞ |
| 4 | 0 | 45 | 45 | 10 | 25 | +∞ |
| 1 | 0 | 45 | 45 | 10 | 25 | +∞ |
| 2 | 0 | 45 | 45 | 10 | 25 | +∞ |

![](img/15e8d7d94d8ddf02cb6839870195a31e_537_0.png)

## Analysis of ShortestPath:

The time for loop of line 4 is O(n). The for loop of line 7 is executed n-2 times, each requires O(n) at line 8 and at line 11 to 13. So the total time is (n²).

Even if adjacency lists are used, the overall time for line 11 to 13 can be brought down to O(e), but for line 8 remains O(n²).

Note the algorithm does not work when some edges may have negative length, as shown bellow:

![](img/15e8d7d94d8ddf02cb6839870195a31e_539_0.png)

Using the **dynamic programming** approach, we can obtain a conceptually simpler algorithm that has complexity of O(n³) and works even when G has edges with negative length so long as G has no cycles with negative length.

A^k[i][j] --- the length of shortest path from i to j going through no intermediate vertex of index greater than k.

A^{n-1}[i][j] --- the length of the shortest i--j path in G.

A^{-1}[i][j] --- length[i][j].

(2) The shortest path does go through k. The path consists of a subpath from i to k and another one from k to j. These must be the shortest paths from i to k and from k to j going through no vertex with index greater than k-1, so their lengths are A^{k-1}[i][k] and A^{k-1}[k][j].

Note the above is true only if G has no negative cycle containing k.

![](img/15e8d7d94d8ddf02cb6839870195a31e_544_0.png)

From (1) and (2), we have:
A^k[i][j]=min{A^{k-1}[i][j], A^{k-1}[i][k]+ A^{k-1}[k][j]}, k≥0.

# Assume:

- G is represented by length-adjacency matrix as for ShortestPath.
- double a[NMAX][NMAX] is data member of MatrixDigraph.

```
1 void MatrixDigraph::AllLengths (const int n)
2 { //length[n][n] is the adjacency matrix of G with n vertices.
3   //a[i][j] is the length of shortest path from i to j
4   for (int i=0; i<n; i++)
5     for (int j=0; j<n; j++)
6       a[i][j] = length[i][j]; // copy length into a
7   for ( int k=0; k<n; k++) // for a path with highest index k
8     for (i=0; i<n; i++)   //for all pairs
9       for (j=0; j<n; j++)
10        if (a[i][k]+a[k][j]<a[i][j]) a[i][j]=a[i][k]+a[k][j];
11 }
```

The computation is done in place using a, because A^k[i][k]= A^{k-1}[i][k] and A^k[k][j]= A^{k-1}[k][j].

# The time is obviously O(n³).

# Example 6.7:

![](img/15e8d7d94d8ddf02cb6839870195a31e_547_0.png)

| A⁻¹ | 0 | 1 | 2 |
|---|---|---|---|
| 0 | 0 | 4 | 11 |
| 1 | 6 | 0 | 2 |
| 2 | 3 | ∞ | 0 |

| A⁰ | 0 | 1 | 2 |
|---|---|---|---|
| 0 | 0 | 4 | 11 |
| 1 | 6 | 0 | 2 |
| 2 | 3 | 7 | 0 |

| A¹ | 0 | 1 | 2 |
|---|---|---|---|
| 0 | 0 | 4 | 6 |
| 1 | 6 | 0 | 2 |
| 2 | 3 | 7 | 0 |

| A² | 0 | 1 | 2 |
|---|---|---|---|
| 0 | 0 | 4 | 6 |
| 1 | 5 | 0 | 2 |
| 2 | 3 | 7 | 0 |

# Exercises: P372-1, P373-2, 5, P375-17

# 6.5 Activity Networks

# 6.5.1 Activity-on-Vertex (AOV) Networks

**Definition:** A directed graph G in which the vertices represent tasks or activities and the edges represent precedence relations between tasks is an **activity-on-vertex network** or AOV network.

In the following, we’ll see the AOV network corresponding to the courses of the next slide.

