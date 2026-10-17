
## Properties of A-star

In practice, how to estimate h(x) to its real value h*(x) is a hard point

- Admissibility: the heuristic function h(x) is admissible, meaning that it never overestimates the actual minimal cost of reaching the goal.

- Monotonicity (Consistency): the heuristic function h(x) is monotonic, means that for any pair of adjacent nodes x and y, \( h(x) \leq h(y) + d(x, y) \)

**Theorem**
A-star is the optimal if h holds admissibility and monotonicity.

## An example: 8 puzzle problem

**Problems statements:** The 8 puzzle is a simple game which consists of eight sliding tiles, numbered by digits from 1 to 8, placed in a 3 × 3 squared board of nine cells.

- One of the cells is always empty
- Any adjacent (horizontally and vertically) tile can be moved into the empty cell
- The objective of the game is to start from an initial configuration and end up in a configuration which the tiles are placed in ascending number order.

| 2 | 8 | 3 |
|---|---|---|
| 1 | 6 | 4 |
| 7 |   | 5 |

⇒

| 1 | 2 | 3 |
|---|---|---|
| 8 |   | 4 |
| 7 | 6 | 5 |

## Design a heuristic cost function

![](img/4208ee4325ab94ec0c685a689680f88f_399_0.png)

For a given state x, we need a heuristic cost function

$\hat{f}(x)=\hat{g}(x)+\hat{h}(x)$　　　　　　　　　　　　　　　　　(6)

Where

- $\hat{g}(x)$: the number of moves from initial state to state x.
- $\hat{h}(x)$: the number of tiles out of place (compared with the goal state) (Hamming priority function)

## State space tree

![](img/4208ee4325ab94ec0c685a689680f88f_400_0.png)

## Pseudo code of A-star algorithm

```
function A*(start,goal)
    closedset := the empty set    // The set of nodes already evaluated.
    openset := {start}    // The set of tentative nodes to be evaluated, initially containing the start node
    came_from := the empty map    // The map of navigated nodes.
    g_score[start] := 0    // Cost from start along best known path.
    // Estimated total cost from start to goal through y.
    f_score[start] := g_score[start] + heuristic_cost_estimate(start, goal)
    while openset is not empty
        current := the node in openset having the lowest f_score[] value
        if current = goal
            return reconstruct_path(came_from, goal)
        remove current from openset
        add current to closedset
        for each neighbor in neighbor_nodes(current)
            if neighbor in closedset
                continue
            tentative_g_score := g_score[current] + dist_between(current,neighbor)
            if neighbor not in openset or tentative_g_score < g_score[neighbor]
                came_from[neighbor] := current
                g_score[neighbor] := tentative_g_score
                f_score[neighbor] := heuristic_cost_estimate(neighbor,
                    goal)
                if neighbor not in openset
                    add neighbor to openset
    return failure
function reconstruct_path(came_from, current_node)
    if current_node in came_from
        p := reconstruct_path(came_from,
            came_from[current_node])
        return (p + current_node)
    else
        return current_node
```

# Coming up: NP Complete Problems

# Chapter 07: Non-deterministic Polynomial Complete Problems

Design and Analysis of Computer Algorithms

GONG Xiu-Jun

School of Computer Science and Technology, Tianjin University

Email: gongxj@tjtu.edu.cn

May 26, 2019
