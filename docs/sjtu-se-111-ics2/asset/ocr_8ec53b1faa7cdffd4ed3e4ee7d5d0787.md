# System Call Error Handling

```
1 if ((pid = fork()) < 0) {
    fprintf(stderr, "fork error: %s\n",
        strerror(errno));
3   exit(0);
4 }
```

```
1 void unix_error(char *msg) /* unix-style error */
2 {
    fprintf(stderr, "%s: %s\n", msg, strerror(errno));
4   exit(0);
5 }
```

```
1 if ((pid = fork()) < 0)
2   unix_error("fork error");
```