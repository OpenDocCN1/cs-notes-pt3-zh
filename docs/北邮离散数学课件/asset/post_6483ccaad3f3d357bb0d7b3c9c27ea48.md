
## Example 3
- The initial flow in all edges is zero

![](img/c25dfd82fc242c2db53bc942dcad6885_1738_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1738_1.png)

## Example 3: STEP 1
– Starting at the source, we can reach nodes 2 and 4 by edges having excess capacity, so $N_1 = \{2, 4\}$

![](img/c25dfd82fc242c2db53bc942dcad6885_1739_0.png)

## Example 3: step 2
– From node 2 we can reach nodes 5 and 3 using edges with positive excess capacity. Node 5 is labeled with [2, 2] since only two additional units of flow can pass through edge (2, 5). Node 3 is labeled with [3, 2] since only 3 additional units of flow can pass through edge (2, 3)

## Example 3: step 2
– We cannot travel from node 4 to any unlabeled node by one edge. Thus, N₂ = {3, 5}

![](img/c25dfd82fc242c2db53bc942dcad6885_1741_0.png)

## Example 3: step 3
– We repeat Step 2 using N₂. We can reach the sink from node 3 and 3 units through edge (3, 6). Thus the sink is labeled with [3, 3]

![](img/c25dfd82fc242c2db53bc942dcad6885_1742_0.png)

## Example 3
- We now return to Step I with the situation shown as

![](img/c25dfd82fc242c2db53bc942dcad6885_1744_0.png)

## Steps 1,2,3
![](img/c25dfd82fc242c2db53bc942dcad6885_1745_0.png)

## Step 5
- Work back along path 1,2,5,6, subtracting 2 from the excess capacities of these edges
- And return to Step 1.

![](img/c25dfd82fc242c2db53bc942dcad6885_1746_0.png)

## Step 1,2,3
![](img/c25dfd82fc242c2db53bc942dcad6885_1747_0.png)

## Step 5
- Work back along the path 1,4,5,6, adjusting excess capacities.
- Return to Step 1.

![](img/c25dfd82fc242c2db53bc942dcad6885_1748_0.png)

## Go further?
- Step 1,2,3

![](img/c25dfd82fc242c2db53bc942dcad6885_1749_0.png)

## step 4
- Terminated with the final overall flow 7.
– Q.E.D.

![](img/c25dfd82fc242c2db53bc942dcad6885_1750_0.png)

## Example 4
![](img/c25dfd82fc242c2db53bc942dcad6885_1751_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1751_1.png)

## Step 1,2,3
![](img/c25dfd82fc242c2db53bc942dcad6885_1752_0.png)

## Step 5
![](img/c25dfd82fc242c2db53bc942dcad6885_1753_0.png)

## Step 1,2,3
![](img/c25dfd82fc242c2db53bc942dcad6885_1754_0.png)

## Step 5
![](img/c25dfd82fc242c2db53bc942dcad6885_1755_0.png)

## Step 1,2,3
![](img/c25dfd82fc242c2db53bc942dcad6885_1756_0.png)

## Step 5
![](img/c25dfd82fc242c2db53bc942dcad6885_1757_0.png)

## Step 1,2,3
![](img/c25dfd82fc242c2db53bc942dcad6885_1758_0.png)

## Step 5
![](img/c25dfd82fc242c2db53bc942dcad6885_1759_0.png)

## Go further?
- Step 1,2,3

![](img/c25dfd82fc242c2db53bc942dcad6885_1760_0.png)

## Step 4
![](img/c25dfd82fc242c2db53bc942dcad6885_1761_0.png)

## Cut (割集)
• A cut in a network N is a set K of edges having the property that every path from the source to the sink contains at least one edge from K.

![](img/c25dfd82fc242c2db53bc942dcad6885_1762_0.png)

## Capacity of a cut \(K\)
- The *capacity* of a cut \(K\), \(c(K)\), is the sum of the capacities of all edges in \(K\).
- If \(F\) is any flow and \(K\) is any cut, then \(-\operatorname{value}(F) \le c(K)\).

## Example
![](img/c25dfd82fc242c2db53bc942dcad6885_1765_0.png)

## Basic concepts
- Transport Networks digraphs whose edges labeled with capacities.
- Source
- Sink
- Super source(超源)
- Super sink(超宿(汇))
- Flows conservation of flow (Cᵢⱼ,Fᵢⱼ)
- Maximum flows virtual flow

## Supersource supersink
![](img/c25dfd82fc242c2db53bc942dcad6885_1767_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1768_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1770_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1771_0.png)
