# # Definition

a nondeterministic algorithm is an algorithm that, even for the same input, can exhibit different behaviors on different runs

There are several ways an algorithm may behave differently from run to run.

+   - A probabilistic algorithm's behaviors depends on a random number generator.

+   - A concurrent algorithm can perform differently on different runs due to a race condition(竞态条件).

```
```c
void random(String s) {
    String c=genCertif();
    boolean checkK=verify(s,c)
    if (checkK) output "yes" return; //SUCCESS
    FAILURE
```
```