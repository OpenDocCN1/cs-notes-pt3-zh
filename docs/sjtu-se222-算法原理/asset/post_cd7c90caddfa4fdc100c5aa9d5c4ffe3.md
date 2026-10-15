
## Where are we?

- Closest pair
- Geometry sweeping
- Geometric preliminaries
- Some basics geometry algorithms
  - Convex hull problem
  - Diameter of a set of points
  - Intersection of line segments

## Maximal points problem

The point $p_2 = (x_2, y_2)$ **dominates** the point $p_1 = (x_1, y_1)$, denoted by $p_1 \square p_2$, if $x_1 \le x_2$ and $y_1 \le y_2$.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_970_0.png)

A point $p$ is **maximal point** if there does NOT exist a point $q$ such that $p \ne q$ and $p \square q$.

## Maximal points problem

Problem: MaximalPoints
Input: a set of points with their coordinates (x_i,y_i).
Output: All the maximal points in the set.

Event

Θ(nlogn)

Sweeping line

![](img/a8f1b433a70f1e5c410c8b43e41b650e_971_0.png)

## City Skyline

8
(1, 1)
(2, 2)
(3, 3)
(4, 2)
(5, 3)
(6, 2)
(7, 0)
(8, 1)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_973_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_973_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_973_2.png)

## Geometry preliminaries

- Point: p(x,y)
- Line segment: ((x1,y1),(x2,y2))
- **Convex** polygon: A polygon P is **convex** if the line segment connecting any two points in P lies ENTIRELY in P.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_975_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_975_1.png)

## Left turn and right turn

Area = ?

D = | x₁ y₁ 1 |
      | x₂ y₂ 1 |
      | x₃ y₃ 1 |

D > 0

D < 0

![](img/a8f1b433a70f1e5c410c8b43e41b650e_976_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_976_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_976_2.png)

## Left turn and right turn

- To determine whether a point is under or above a line segment.
- To determine if two line segments intersect.

## Where are we?

- Closest pair
- Geometry sweeping
- Geometric preliminaries
- Some basics geometry algorithms
  - Convex hull problem
  - Diameter of a set of points
  - Intersection of line segments

## Convex hull

Problem: ConvexHull
Input: a set S={p₁, p₂, ..., pₙ} of n points in the plane,
Output: CH(S)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_979_0.png)

- Graham scan
- Jarvis’ march (gift-wrapping algorithm)
- Quick-hull

## Jarvis’ march

- Start at some *extreme point*, which is guaranteed to be on the hull.
- At each step, test each of the points, and find the one *which makes the largest right-hand turn*. That point has to be the next one on the hull.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_980_0.png)

## Quick hull

- Given a chord $p_i p_j$ of the convex hull
- Find the farthest one $p_k$ from the chord
- The points inside the triangle $p_i p_j p_k$ cannot be on the hull. Put the points which lie outside edge $p_i p_k$ in set s1, and points outside edge $p_j p_k$ in set s2.
- Recursively solve the problem of s1 and s2.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_981_0.png)

## Graham Scan

![](img/a8f1b433a70f1e5c410c8b43e41b650e_982_0.png)

Ronald Graham
(source from Wikipedia)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_982_1.png)

## Graham scan

![](img/a8f1b433a70f1e5c410c8b43e41b650e_983_0.png)

## Where are we?

- Closest pair
- Geometry sweeping
- Geometric preliminaries
- Some basics geometry algorithms
  - Convex hull problem
  - Diameter of a set of points
  - Intersection of line segments

## The diameter of a set of points

![](img/a8f1b433a70f1e5c410c8b43e41b650e_987_0.png)

The diameter of a set *P* of points equals to the diameter of *CH(P)*.

Any two points that admit two parallel supporting lines are called *antipodal pair*.

Any pair of vertices realizing the diameter in a convex polygon is an *antipodal pair*.

How to find antipodal pairs?
