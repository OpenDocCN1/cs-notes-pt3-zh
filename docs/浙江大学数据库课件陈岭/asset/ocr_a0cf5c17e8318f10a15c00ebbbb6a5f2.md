# # (4) Canonical Cover (正则覆盖)

DBMS should always check to ensure not violate any FD in F. If the F is too big, the check is costly. Then we need simplify the set of FDs.

Intuitively, a canonical cover of F (denoted Fc) is a “minimal” set of FDs equivalent to F :

+   1) Having no redundant FDs and no redundant parts of FDs, i.e. no functional dependency in Fc contains an extraneous attribute.

+   2) Each left side is unique.

E.g. α1→β1 , α1 →β2 , ⇒ α1→β1β2

![](bbox=[0.391, 0.766, 0.766, 0.859])