```
```c
if (!builtin_command(argv)) {
    if ((pid = Fork()) == 0) { /* execute in child */
        if (execve(argv[0], argv, environ) < 0) {
            printf("%s: Command not found.\n", argv[0]);
            exit(0);
        }
    }
}

/* parent waits for foreground job to terminate */
if (!bg) { /* foreground */
    int status;
    if (waitpid(pid, &status, 0) < 0)
        unix_error("waitfg: waitpid error");
}
else
    printf("%d %s", pid, cmdline);
}
return;
}
```
```