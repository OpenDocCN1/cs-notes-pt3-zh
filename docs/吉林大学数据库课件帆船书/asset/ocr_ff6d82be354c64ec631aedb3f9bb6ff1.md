# Optimization of Updates

# Halloween problem

```
update R set A = 5 * A
where A > 10
```

+   If index on A is used to find tuples satisfying A > 10, and tuples updated immediately, same tuple may be found (and updated) multiple times

+   Solution 1: Always defer updates

+   collect the updates (old and new values of tuples) and update relation and indices in second pass

+   Drawback: extra overhead even if e.g. update is only on R.B, not on attributes in selection condition

+   Solution 2: Defer only if required

+   Perform immediate update if update does not affect attributes in where clause, and deferred updates otherwise.