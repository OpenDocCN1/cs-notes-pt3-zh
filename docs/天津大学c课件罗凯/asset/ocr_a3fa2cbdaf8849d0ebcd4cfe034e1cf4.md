# # Short Circuit Evaluation

+   - A boolean expression will quit as soon as it can make an accurate decision

+   - Examples:

```
if ( a < b && a > c ) // and
```

only if this is **true** will we check the other

```
if ( a < b || a > c ) // or
```

only if this is **false** will we check the other