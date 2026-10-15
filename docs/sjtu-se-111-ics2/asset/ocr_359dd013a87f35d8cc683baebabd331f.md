# Echo client: open_clientfd() (socket)

+   - The client creates a socket that will serve as the endpoint of an Internet (AF_INET) connection (SOCK_STREAM).
+     - socket() returns an integer socket descriptor.

```
int clientfd;  /* socket descriptor */
clientfd = Socket(AF_INET, SOCK_STREAM, 0);
```