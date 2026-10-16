
## Availability

- Traditionally, availability of centralized server
- For distributed systems, availability of system to process requests
  - For large system, at almost any point in time there’s a good chance that
    - a node is down or even
    - Network partitioning
- Distributed consensus algorithms will block during partitions to ensure consistency
  - Many applications require continued operation even during a network partition
    - Even at cost of consistency

## Brewer’s CAP Theorem

- Three properties of a system
  - Consistency (all copies have same value)
  - Availability (system can run even if parts have failed)
    - Via replication
  - Partitions (network can break into two or more parts, each with active systems that can’t talk to other parts)
- Brewer’s CAP “Theorem”: You can have at most two of these three properties for any system
- Very large systems will partition at some point
  - Choose one of consistency or availability
  - Traditional database choose consistency
  - Most Web applications choose availability
    - Except for specific parts such as order processing

## Replication with Weak Consistency

- Many systems support replication of data with weak degrees of consistency (i.e., without a guarantee of serializability)
  - i.e. Q_R + Q_W <= S or 2*Q_W < S
  - Usually only when not enough sites are available to ensure quorum
    - But sometimes to allow fast local reads
  - Tradeoff of consistency versus availability or latency
- Key issues:
  - Reads may get old versions
  - Writes may occur in parallel, leading to inconsistent versions
    - Question: how to detect, and how to resolve
      - Version vector scheme, Section 25.5.4

## Eventual Consistency

- When no updates occur for a long period of time, eventually all updates will propagate through the system and all the nodes will be consistent
- For a given accepted update and a given node, eventually either the update reaches the node or the node is removed from service
- Known as **BASE** (Basically **A**vailable, **S**oft state, **E**ventual consistency), as opposed to ACID
  - **Soft state**: copies of a data item may be inconsistent
  - **Eventually Consistent** – copies becomes consistent at some later time if there are no more updates to that data item

## Availability vs Latency

- CAP theorem only matters when there is a partition
  - Even if partitions are rare, applications may trade off consistency for latency
    - E.g. PNUTS allows inconsistent reads to reduce latency
      - Critical for many applications
    - But update protocol (via master) ensures consistency over availability
  - Thus there are two questions :
    - If there is partitioning, how does system tradeoff *availability* for *consistency*
    - else how does system trade off *latency* for *consistency*

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1077_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1078_0.png)

## Distributed Query Processing

## Distributed Query Processing

- For centralized systems, the primary criterion for measuring the cost of a particular strategy is the number of disk accesses.
- In a distributed system, other issues must be taken into account:
  - The cost of a data transmission over the network.
  - The potential gain in performance from having several sites process parts of the query in parallel.

## Query Transformation

- Translating algebraic queries on fragments.

- It must be possible to construct relation r from its fragments

- Replace relation r by the expression to construct relation r from its fragments

Consider the horizontal fragmentation of the account relation into

```
account₁ = σ branch_name = "Hillside" (account)
```

```
account₂ = σ branch_name = "Valleyview" (account)
```

The query σ branch_name = "Hillside" (account) becomes

```
σ branch_name = "Hillside" (account₁ ∪ account₂)
```

which is optimized into

```
σ branch_name = "Hillside" (account₁) ∪ σ branch_name = "Hillside" (account₂)
```
