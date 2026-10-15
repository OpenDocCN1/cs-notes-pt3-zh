# Echo server: open_listenfd (listen)

+   - listen() indicates that this socket will accept connection (connect) requests from clients.

```
int listenfd;                 /* listening socket */

/* make listenf it a server-side listening socket
ready to accept connection requests from clients */
Listen(listenfd, LISTENQ);
```

+   - We're finally ready to enter the main server loop that accepts and processes client connection requests.