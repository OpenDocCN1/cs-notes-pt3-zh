# Monitor With Condition Variables

queue associated with x, y conditions

shared data

entry queue

Q:
suspended
associated
with x.
P: x.signal()
--- ???

Solution:

+   - Signal and wait
+   - Signal and continue

operations

initialization code

+   P waits
+   - until Q leaves the monitor,
+   - for another condition.
+   Q waits
+   - until P leaves the monitor
+   - for another condition