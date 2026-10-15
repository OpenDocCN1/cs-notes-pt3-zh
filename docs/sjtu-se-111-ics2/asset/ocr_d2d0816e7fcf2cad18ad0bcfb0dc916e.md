# Echo server: `open_listenfd()` (setsockopt)

+   - The socket can be given some attributes.

```
/* eliminates "Address already in use" error
   from bind. */
optval = 1;
Setsockopt(listenfd, SOL_SOCKET, SO_REUSEADDR,
           (const void *)&optval, sizeof(int));
```