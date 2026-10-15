# # Review: Iterative Echo Server

```
```c
int main(int argc, char **argv)
{
    int listenfd, connfd, port = atoi(argv[1]);
    struct sockaddr_in clientaddr;
    int clientlen = sizeof(clientaddr);

    listenfd = Open_listenfd(port);
    while (1) {
        connfd = Accept(listenfd, (SA *)&clientaddr, &clientlen);
        echo(connfd);
        Close(connfd);
    }
    exit(0);
}
```
```

+   - Accept a connection request
+   - Handle echo requests until client terminates