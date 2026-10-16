
## Safe, Unsafe , Deadlock State

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_462_0.png)

## Avoidance algorithms

- Single instance of a resource type
  - Use a resource-allocation-graph algorithm
- Multiple instances of a resource type
  - Use the banker’s algorithm

## Resource-Allocation-Graph Algorithm

- *Claim edge* $P_i \rightarrow R_j$ indicated that process $P_i$ may request resource $R_j$; represented by a dashed line.
- **Claim edge converts to request edge** when a process requests a resource.
- When a resource is released by a process, **assignment edge reconverts to a claim edge.**
- Resources must be claimed a priori in the system.

## Resource-Allocation Graph
For Deadlock Avoidance

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_465_0.png)

## Unsafe State In Resource-Allocation Graph

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_466_0.png)

## Banker’s Algorithm

- Multiple instances.
- Each process must a priori claim maximum use.
- When a process requests a resource it may have to wait.
- When a process gets all its resources it must return them in a finite amount of time.

## Data Structures for the Banker’s Algorithm

Let n = number of processes, and m = number of resources types.

- **Available**: Vector of length m. If available [j] = k, there are k instances of resource type Rj available.
- **Max**: n x m matrix. If Max [i,j] = k, then process Pi may request at most k instances of resource type Rj.
- **Allocation**: n x m matrix. If Allocation[i,j] = k then Pi is currently allocated k instances of Rj.
- **Need**: n x m matrix. If Need[i,j] = k, then Pi may need k more instances of Rj to complete its task.

## Safety Algorithm

1. Let *Work* and *Finish* be vectors of length *m* and *n*, respectively. Initialize:
   
   *Work* = Available;  *Finish* [i] = false for i = 0, 1, ..., n.

2. Find an *i* such that both:
   
   (a) *Finish* [i] = *false*
   
   (b) *Needᵢ* ≤ *Work*
   
   If no such *i* exists, go to step 4.

3. *Work* = *Work* + *Allocationᵢ*
   
   *Finish* [i] = *true*
   
   go to step 2.

4. If *Finish* [i] == true for all *i*, then **the system is in a safe state.**

## Resource-Request Algorithm for Process Pi

Let *Request*ᵢ be the request vector for process *P*ᵢ. If *Request*ᵢ[*j*] = *k* then process *P*ᵢ wants *k* instances of resource type *R*ⱼ.

1. If *Request*ᵢ ≤ *Need*ᵢ go to step 2. Otherwise, raise error condition, since process has exceeded its maximum claim.
2. If *Request*ᵢ ≤ *Available*, go to step 3. Otherwise *P*ᵢ must wait, since resources are not available.

## Resource-Request Algorithm for Process $P_i$

3. Pretend to allocate requested resources to $P_i$ by modifying the state as follows:

$$Available = Available - Request_i;$$

$$Allocation_i = Allocation_i + Request_i;$$

$$Need_i = Need_i - Request_i;$$

- **If safe** ⇒ the resources are allocated to $P_i$.
- **If unsafe** ⇒ $P_i$ must wait, and the old resource-allocation state is restored.

## Example of Banker’s Algorithm

- 5 processes $P_0$ through $P_4$; 3 resource types $A$ (10 instances), $B$ (5 instances), and $C$ (7 instances).
- Snapshot at time $T_0$:

| Allocation | Max | Available |
|---|---|---|
| A B C | A B C | A B C |
| $P_0$ 0 1 0 | 7 5 3 | 3 3 2 |
| $P_1$ 2 0 0 | 3 2 2 |  |
| $P_2$ 3 0 2 | 9 0 2 |  |
| $P_3$ 2 1 1 | 2 2 2 |  |
| $P_4$ 0 0 2 | 4 3 3 |  |

## Example of Banker’s Algorithm

The content of the matrix. Need is defined to be Max − Allocation.

**Need**

|  | A | B | C |
|---|---:|---:|---:|
| P₀ | 7 | 4 | 3 |
| P₁ | 1 | 2 | 2 |
| P₂ | 6 | 0 | 0 |
| P₃ | 0 | 1 | 1 |
| P₄ | 4 | 3 | 1 |

The system is in a safe state since the sequence < P₁, P₃, P₄, P₂, P₀ > satisfies safety criteria.

## Example P1 Request (1,0,2)

▪ Check that Request ≤ Available (that is, (1,0,2) ≤ (3,3,2) ⇒ **true**.)

|  | **Allocation** | **Need** | **Available** |
|---|---|---|---|
|  | A B C | A B C | A B C |
| $P_0$ | 0 1 0 | 7 4 3 | 2 3 0 |
| $P_1$ | 3 0 2 | 0 2 0 |  |
| $P_2$ | 3 0 1 | 6 0 0 |  |
| $P_3$ | 2 1 1 | 0 1 1 |  |
| $P_4$ | 0 0 2 | 4 3 1 |  |
