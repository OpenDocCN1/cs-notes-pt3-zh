

## An example of task scheduling

In a weighted staged directed graph \(G\), we want to search the shortest path from start node \(s\) to the terminal node \(e\).

The sub-path from a node in the Global Shortest Path (GSP) to the terminal node is also shortest path.

For example, if node \(i\) is in GSP, then its neighbor is in \(\{2,3,4,6\}\), if it is in GSP, then sub-path of GSP from \(i\) to \(e\) is also shortest.

Define that \(c(i)\) is the shortest distance from \(i\) to \(e\), then \(c(e) = 0\) and \(c(s)\) is the goal

\[
c(i) = \min_{j\in N(i)} \{c(j) + cost(i,j)\}
\]

where \(N(i)\) is the set of neighbors of \(i\)

We call this property as the Optimal Substructure of subproblems in the procedure problem decomposition

We also should noted that there are some overlapped subproblems in seeking the shortest paths.

Solve \(c(i)\) in reverse order

\(c(7) = 0\)

![](img/4208ee4325ab94ec0c685a689680f88f_11_0.png)

## An example of task scheduling

In a weighted staged directed graph \(G\), we want to search the shortest path from start node \(s\) to the terminal node \(e\).

The sub-path from a node in the Global Shortest Path (GSP) to the terminal node is also shortest path.

For example, if node \(j\) is a neighbor of \(i\) in \((2,3,4)\), if it is in GSP, then sub-path of GSP from \(i\) to \(e\) is the terminal node is also shortest.

Define that \(c(i)\) is the shortest distance from \(i\) to \(e\), then \(c(e) = 0\) and \(c(s)\) is the goal

\[
c(i) = \min_{j\in N(i)} (c(j) + cost(i,j))
\]

where \(N(i)\) is the set of neighbors of \(i\)

we call that property as the Optimal Substructures of subproblems in the procedure problem decomposition.

we also should noted that there are some overlapped subproblems in seeking the shortest paths.

Solve \(c(i)\) in reverse order

\(c(7) = 0\)

\(c(6) = 1, c(5) = 2\)

![](img/4208ee4325ab94ec0c685a689680f88f_12_0.png)

## An example of task scheduling

In a weighted staged directed graph \(G\), we want to search the shortest path from start node \(s\) to the terminal node \(e\).

The sub-path from a node in the Global Shortest Path (GSP) to the terminal node is also shortest. For the node 1, whichever of its neighbors is 2, 3, 4, 5 in GSP, the sub-path of GSP from it to the terminal is also shortest.

![](img/4208ee4325ab94ec0c685a689680f88f_13_0.png)

We call this property as the Optimal Substructure of subproblems in the procedure of problem decomposition. We also should noticed that there are some overlapped subproblems in seeking the shortest path.

Define that \(c(i)\) is the shortest distance from \(i\) to \(e\), then \(c(e)=0\) and \(c(s)\) is the goal

\[
c(i)=\min_{j\in N(i)}\{c(j)+\operatorname{cost}(i,j)\}
\]

where \(N(i)\) is the set of neighbors of \(i\).

Solve \(c(i)\) in reverse order

\(c(7)=0\)

\(c(6)=1,\ c(5)=2\)

\(c(4)=8+c(6)=9\)

## An example of task scheduling

In a weighted staged directed graph \(G\), we want to search the shortest path from start node \(s\) to the terminal node \(e\).

The sub-path from a node in the Global Shortest Path (GSP) to the terminal node is also shortest path.

Proof: If there is a shorter path from its neighbor is in \((2,3,4)\), if it is in GSP, then sub-path of GSP from \(i\) to \(e\) is the terminal path is also shortest.

We call this property as the **Optimal Substructure** of subproblems in the procedure of problem decomposition.

We also should noted that there are some overlapped subproblems in seeking the shortest paths.

Define that \(c(i)\) is the shortest distance from \(i\) to \(e\), then \(c(e) = 0\) and \(c(s)\) is the **goal**

\[
c(i) = \min \{c(j) + cost(i,j)\}
\]

where \(N(i)\) is the set of neighbors of \(i\)

Solve \(c(i)\) in reverse order

\(c(7) = 0\)

\(c(6) = 1, c(5) = 2\)

\(c(4) = 8+c(6)=9\)

\(c(3) = \min\{1 + c(5), 5 + c(6)\} = \min\{3,6\} = 3\)

![](img/4208ee4325ab94ec0c685a689680f88f_14_0.png)

## An example of task scheduling

In a weighted staged directed graph \(G\), we want to search the shortest path from start node \(s\) to the terminal node \(e\).

![](img/4208ee4325ab94ec0c685a689680f88f_15_0.png)

We call this property as the **Optimal Substructure** of subproblems in the procedure of problem decomposition.

We also should noted that there are some **overlapped subproblems** in solving the shortest paths.

The sub-path from a node in the middle of an STP (shortest path) to the terminal node is also shortest.

For the node 1, whichever its neighbor node is \(2, 3, 4\), if it is in SP, the sub-path of SP from it to the terminal is also shortest.

Define that \(c(i)\) is the shortest distance from \(i\) to \(e\), then \(c(e)=0\) and \(c(s)\) is the goal.

\[
c(i)=\min_{j\in N(i)}\{c(j)+cost(i,j)\}
\]

where \(N(i)\) is the set of neighbors of \(i\)

Solve \(c(i)\) in reverse order

\(c(7)=0\)

\(c(6)=1, c(5)=2\)

\(c(4)=8+c(6)=9\)

\(c(3)=\min\{1+c(5), 5+c(6)\}=\min\{3,6\}=3\)

\(c(2)=7, c(1)=7\)

