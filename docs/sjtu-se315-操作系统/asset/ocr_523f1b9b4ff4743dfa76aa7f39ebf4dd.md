# How Valarind Detect it

```
Thread #1: lock order "0x7FEFFFAB0 before 0x7FEFFFA80" violated
    at 0x4C23C91: pthread_mutex_lock (hg_intercepts.c:388)
    by 0x40081F: main (tc13_laog1.c:24)
Required order was established by acquisition of lock at 0x7FEFFFAB0
    at 0x4C23C91: pthread_mutex_lock (hg_intercepts.c:388)
    by 0x400748: main (tc13_laog1.c:17)
followed by a later acquisition of lock at 0x7FEFFFA80
    at 0x4C23C91: pthread_mutex_lock (hg_intercepts.c:388)
    by 0x400773: main (tc13_laog1.c:18)
```