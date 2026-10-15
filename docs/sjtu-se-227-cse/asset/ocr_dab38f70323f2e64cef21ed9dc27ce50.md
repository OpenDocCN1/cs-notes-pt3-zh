# Back to the Example

```
1   procedure MEASURE (func)
2     start ← GET_TIME (SECONDS)
3     func () // invoke the function
4     end ← GET_TIME (SECONDS)
5     return end − start

1   procedure GET_TIME (units)
2     time ← CLOCK
3     time ← CONVERT_TO_UNITS (time, units)
4     return time
```

+   - Implement MEASURE and GET_TIME with RPC
+     - On different computers
+     - Marshaling: big-endian & little-endian converting