# Example of atomicity violation

```
Thread 1                         Thread 2

if (thd->proc_info) {
    ...

    fputs(thd->proc_info, ...)

    ...
}
```

MySQL ha_innodb.hpp