# Wait_pid Function

```
15  while ((retpid = waitpid(pid[i++], &status, 0)) > 0) {
16      if (WIFEXITED(status))
18          printf("child %d terminated normally with exit
19              status=%d\n", retpid, WEXITSTATUS(status));
20      else
21          printf("child %d terminated abnormally\n", retpid);
22  }
23
24  /* The only normal term. is if there are no more chds. */
25  if (errno != ECHILD)
26      unix_error("waitpid error");
27
28  exit(0);
29}
```