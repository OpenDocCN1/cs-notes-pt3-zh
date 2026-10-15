# Echo server: open_listenfd() (cont)

```
/* listenfd will be an endpoint for all requests to port on any IP address for this host */
bzero((char *) &serveraddr, sizeof(serveraddr));
serveraddr.sin_family = AF_INET;
serveraddr.sin_addr.s_addr = htonl(INADDR_ANY);
serveraddr.sin_port =
    htons((unsigned short)port);
Bind(listenfd,
    (SA *)&serveraddr, sizeof(serveraddr));
/* make it a listening socket ready to accept connection requests */
Listen(listenfd, LISTENQ);
return listenfd;
}
```