
## Finding Support

- Determine support of itemsets via a single pass on set of transactions
  - Large itemsets: sets with a high count at the end of the pass
- If memory not enough to hold all counts for all itemsets use multiple passes, considering only some itemsets in each pass.
- Optimization: Once an itemset is eliminated because its count (support) is too small none of its supersets needs to be considered.
- The **a priori** technique to find large itemsets:
  - Pass 1: count support of all sets with just 1 item. Eliminate those items with low support
  - Pass *i*: **candidates**: every set of *i* items such that all its *i-1* item subsets are large
    - Count support of all candidates
    - Stop if there are no candidates

## Other Types of Associations

- Basic association rules have several limitations
- Deviations from the expected probability are more interesting
  - E.g., if many people purchase bread, and many people purchase cereal, quite a few would be expected to purchase both
  - We are interested in **positive** as well as **negative correlations** between sets of items
    - Positive correlation: co-occurrence is higher than predicted
    - Negative correlation: co-occurrence is lower than predicted
- Sequence associations / correlations
  - E.g., whenever bonds go up, stock prices go down in 2 days
- Deviations from temporal patterns
  - E.g., deviation from a steady growth
  - E.g., sales of winter wear go down in summer
    - Not surprising, part of a known pattern.
    - Look for deviation from value predicted using past patterns

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1157_0.png)

## Clustering

Clustering: Intuitively, finding clusters of points in the given data such that similar points lie in the same cluster

Can be formalized using distance metrics in several ways

- Group points into k sets (for a given k) such that the average distance of points from the centroid of their assigned group is minimized

Centroid: point defined by taking average of coordinates in each dimension.

Another metric: minimize average distance between every pair of points in a cluster

Has been studied extensively in statistics, but on small data sets

Data mining systems aim at clustering techniques that can handle very large data sets

E.g., the Birch clustering algorithm (more shortly)

### Hierarchical Clustering

Example from biological classification

(the word classification here does not mean a prediction mechanism)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1158_0.png)

Other examples: Internet directory systems (e.g., Yahoo, more on this later)

- Build small clusters, then cluster small clusters into bigger clusters, and so on

- Start with all items in a single cluster, repeatedly refine (break) clusters into smaller ones

## Clustering Algorithms

- Clustering algorithms have been designed to handle very large datasets
- E.g., the **Birch algorithm**
  - Main idea: use an in-memory R-tree to store points that are being clustered
  - Insert points one at a time into the R-tree, merging a new point with an existing cluster if it is less than some δ distance away
  - If there are more leaf nodes than fit in memory, merge existing clusters that are close to each other
  - At the end of first pass we get a large number of clusters at the leaves of the R-tree
    - Merge clusters to reduce the number of clusters

## Collaborative Filtering

- Goal: predict what movies/books/... a person may be interested in, on the basis of
  - Past preferences of the person
  - Other people with similar past preferences
  - The preferences of such people for a new movie/book/...
- One approach based on repeated clustering
  - Cluster people on the basis of preferences for movies
  - Then cluster movies on the basis of being liked by the same clusters of people
  - Again cluster people based on their preferences for (the newly created clusters of) movies
  - Repeat above till equilibrium
- Above problem is an instance of **collaborative filtering**, where users collaborate in the task of filtering information to find information of interest
