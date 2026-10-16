
4. Select the red parts at station B (there are 10), then query station A for each tuple to see whether a supplier in Beijing supplies this part.

![](img/0e3bdb3629a6dd1eaa4c29e30bfd2664_479_0.png)

| Relation | Number of tuples |
|---|---:|
| S(S#,CITY) | 10^4 tuples |
| P(P#,COLOR) | 10^5 tuples |
| SP(S#,P#) | 10^6 tuples |

Number of red parts = 10;  
number of supply orders from Beijing suppliers = 10^5

Transmission time T = 2t * 10 = 20ts

## 5. Select the shipment orders of Beijing suppliers at station A (10^5), transmit them to station B, and complete the query at station B.

![](img/0e3bdb3629a6dd1eaa4c29e30bfd2664_480_0.png)

| S(S#,CITY) | 10^4 tuples |
| P(P#,COLOR) | 10^5 tuples |
| SP(S#,P#) | 10^6 tuples |

Number of red parts = 10;  
number of shipment orders from Beijing suppliers = 10^5

Transmission time T = 1t + 10^5 * 100 / 10^7 = (t+1)s

6. Select the red parts at station B (10), transmit the results to station A, and complete the query at station A.

![](img/0e3bdb3629a6dd1eaa4c29e30bfd2664_481_0.png)

| Relation | Number of tuples |
|---|---:|
| S(S#,CITY) | 10^4 tuples |
| P(P#,COLOR) | 10^5 tuples |
| SP(S#,P#) | 10^6 tuples |

Number of red parts = 10;  
number of shipment orders from Beijing suppliers = 10^5

Transmission time T = 1t + 10 * 100 / 10^7 = 1t

| No. | Schematic diagram | T(1s,10kbps) | T(t,10Mbps)(t=10^-3s) |
|---|---|---|---|
| 1 | S, SP ↔ P | 10^3 s (16.7 min) | (t+1) (1s) |
| 2 | S, SP ↔ P S / SP | 10^4 s (28 h) | (2t+10) (10s) |
| 3 | S, SP ↔ P query/reply | 2 * 10^5 s (2.3 days) | 2t * 10^5 (200s) |
| 4 | S, SP ↔ P query/reply | 20s | 20t (0.02s) |
| 5 | S, SP → P transmit σ(S) ▷◁ SP | 10^3 s (16.7 min) | (t+1) (1s) |
| 6 | S, SP ← P transmit σ(P) | 1.1s | 1t (10^-3 s) |

- Different query strategies differ greatly in communication time, so optimization is necessary.
- In some strategies, both data transmission time and transmission delay must be considered, while in other strategies the main consideration is transmission delay (such as the query-reply approach), and in still other strategies the data transmission volume is large, so the main consideration is transmission time.

## Problems to be solved in query processing and optimization

- In a distributed database system, queries can be divided into three categories: local queries, remote queries, and global queries.
  - Local queries and remote queries involve data at a single node (local or remote) and can be handled using centralized database processing techniques;
  - Global queries involve data at multiple nodes and are very complex.

- To execute global queries and determine a good query strategy, many judgments and computations are needed.
  - Query decomposition
    - Decompose the global query into several subqueries, each involving data at only one node and processable by the local DBMS. It is necessary to select those nodes (physical fragments) with the lowest query cost.
  - Choosing the order of operation execution
    - Mainly determines the order of joins and union operations involving relations at different nodes.
  - Choosing the method of operation execution
    - Includes selecting access paths, the algorithm for a certain operation, and the execution method for joins.

## Goals of query optimization

- The choice of query processing strategy is based on the expected cost of executing the query.
  - Query execution cost: I/O cost + CPU cost + communication cost
  - Distributed queries can be divided into distributed optimization of access strategies and local optimization. Among them, distributed optimization of access strategies is more important.
- Communication cost is computable and is usually a function of data transmission volume:
  TC(X) = C0 + X*C1
  X is the data transmission volume, C0 is the overhead of initializing one transmission between two nodes, and C1 is the transmission rate, i.e., the time spent transmitting a unit of data.
- In distributed database query optimization, "communication cost" is studied as the primary factor. Therefore, the primary goal of query optimization is to minimize the communication cost during query execution.
- Join operations and union operations between different nodes are the main causes of data transmission, so the optimization of join queries is an important research topic in optimization.

## Optimization of join queries

- Semijoin: Use semijoins to reduce relations (or fragments) and thereby save transmission overhead.

- Definition of semijoin: R ⋉ₐ=ʙ S = R ⋈ₐ=ʙ (Πʙ (S))

Example:

### R1

| A | B |
| --- | --- |
| a1 | b1 |
| a2 | b1 |
| a2 | b3 |
| a2 | b4 |
| a3 | b3 |

⋈

### R2

| B | C |
| --- | --- |
| b1 | c1 |
| b2 | c2 |
| b5 | c1 |
| b5 | c2 |
| b6 | c4 |
| b7 | c2 |
| b8 | c3 |

=

### R1 ⋈ R2

| A | B |
| --- | --- |
| a1 | b1 |
| a2 | b1 |

- According to the definition of semijoin, we have
- R ⋈ₐ=ʙ S = (R ⋈ₐ=ʙ S) ⋈ₐ=ʙ S = (R ⋈ₐ=ʙ Π_B (S) ) ⋈ₐ=ʙ S

- Application of semijoins in query optimization

![](img/0e3bdb3629a6dd1eaa4c29e30bfd2664_487_0.png)

- Communication cost when using semijoin:
- C_SJ = 2C0 + C1 * (size(B) * card(Π_B(S)) + size(R) * card(R'))

- Communication cost when not using semijoin:
- C_JN = C0 + C1 * size(R) * card(R)

- When the number of tuples in R participating in the join is sufficiently small, using the semijoin strategy is advantageous. 41

## Distributed transaction processing

- Atomicity and serializability of distributed transactions
  - In a distributed database system, a global transaction is divided into subtransactions on many nodes. The atomicity of a distributed transaction means that all subtransactions composing the transaction must either all commit consistently or all roll back consistently.
  - In multi-user systems, the serializability of distributed transactions must also be guaranteed.
- Distributed transaction management mainly includes: transaction recovery and concurrency control.

## Recovery of distributed transactions

- Each site has a local transaction manager, responsible for managing the execution of local subtransactions. At the same time, all local transaction managers must coordinate with each other to ensure the atomicity of distributed transactions: all subtransactions must either commit or roll back.
- The most commonly used technique for coordinating local transaction managers to ensure the atomicity of distributed transactions is the two-phase commit protocol (2-Phase-Commitment Protocol).

## Two-Phase Commit Protocol (1)

- The two-phase commit protocol divides all local transaction managers of a distributed transaction into two categories: a coordinator (one) and participants.
  - Coordinator: responsible for making the final decision on whether the transaction commits or aborts.
  - Participants: responsible for managing the execution of the corresponding subtransactions and performing write operations on their respective local databases.

## Two-Phase Commit Protocol (2)

- Contents of the two-phase commit protocol
  - Phase 1: The coordinator solicits opinions and makes a decision
    - The coordinator sends a "prepare to commit" message to all participants and records it in the log; if a participant is ready to commit, it replies "ready", otherwise it replies "abort", and records it in the log.
    - If the coordinator receives "ready" messages from all participants within the specified time, it makes a "commit" decision; otherwise, it makes an "abort" decision.
  - Phase 2: Participants execute the decision
    - The coordinator writes the relevant decision to the log, then sends this decision to all participants.
    - After receiving the command, all participants first record the information "received commit/abort decision" in the log, then send a response message to the coordinator, and finally execute the corresponding decision.
    - After the coordinator receives the response messages from all participants, the execution of a transaction ends. The relevant log information can be saved offline.
- With the two-phase commit protocol, if the system fails, each site uses its relevant log for transaction recovery.

## Concurrency Control (2)

- Further strategies for concurrency control in distributed database systems:
  - Several feasible methods for handling multi-copy locking:
    - For write operations, X locks must be requested on all copies; for read operations, it is sufficient to request an S lock on one copy.
    - For both write and read operations, X locks or S locks must be requested on the majority of copies.
    - Designate the copy on a certain site as the primary copy, and all read and write operations request locking on the primary copy.
  - Solving global deadlock (deadlock occurring at two or more sites)
    - Deadlock detection and resolution methods
    - Deadlock prevention, such as sorting transactions according to a certain criterion and only allowing transactions to wait one-way in this order.

![](img/0e3bdb3629a6dd1eaa4c29e30bfd2664_493_0.png)
