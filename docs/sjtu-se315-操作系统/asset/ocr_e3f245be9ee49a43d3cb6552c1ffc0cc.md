# Example of atomicity violation

Thread 1

should be atomically executed

```
if (thd->proc_info) {
  ...
  fputs(thd->proc_info, ...)
  ...
}
```

Thread 2

```
thd->proc_info = NULL;
```

MySQL ha_innodb.hpp