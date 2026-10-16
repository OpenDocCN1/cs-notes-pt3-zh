# 6.7 Monitors

+   - High-level synchronization construct that allows the safe sharing of an abstract data type among concurrent processes.
+   - Monitor is a software module
+   - Chief characteristics
+     - Local data variables are accessible only by the monitor
+     - Process enters monitor by invoking one of its procedures
+     - Only one process may be executing in the monitor at a time

```
monitor monitor-name
{
    shared variable declarations
    procedure body P1 (...)
    { ... }
    procedure body P2 (...)
    { ... }
    procedure body Pn (...)
    { ... }
    {
    initialization code
    }
}
```