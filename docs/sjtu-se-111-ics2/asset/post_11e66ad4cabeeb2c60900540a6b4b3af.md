
## Echo server: open_listenfd (listen)

- listen() indicates that this socket will accept connection (connect) requests from clients.

```
int listenfd;                 /* listening socket */

/* make listenfd a server-side listening socket
ready to accept connection requests from clients */
Listen(listenfd, LISTENQ);
```

- We're finally ready to enter the main server loop that accepts and processes client connection requests.

## Echo server: main loop

- The server loops endlessly, waiting for connection requests, then reading input from the client, and echoing the input back to the client.

```
main() {
    /* create and configure the listening socket */

    while(1) {
        /* Accept(): wait for a connection request */
        /* echo(): read/echo input line from client */
        /* Close(): close the connection */
    }
}
```

## Echo server: accept()

- **accept()** returns a connected socket descriptor (`connfd`) with the same properties as the listening descriptor (`listenfd`)
  - Returns when connection between client and server is complete.
  - All I/O with the client will be done via the connected socket.
- **accept()** also fills in client’s address.

## Echo server: identifying the client

- The server can determine the domain name and IP address of the client.

```
struct hostent *hp; /* pointer to DNS host entry */
char *haddrp; /* pointer to dotted decimal string */

hp = Gethostbyaddr((const char *)
    &clientaddr.sin_addr.s_addr,
    sizeof(clientaddr.sin_addr.s_addr), AF_INET);
haddrp = inet_ntoa(clientaddr.sin_addr);
printf("server connected to %s (%s)\n",
    hp->h_name, haddrp);
```

## Echo server: echo ()

- The server uses Unix I/O to read and echo text lines until EOF (end-of-file) is encountered.
- EOF notification caused by client calling `close(clientfd)`.
- NOTE: EOF is a condition, not a data byte.

## Echo server: echo()

```
void echo(int connfd)
{
    size_t n;
    char buf[MAXLINE];
    rio_t rio;

    Rio_readinitb(&rio, connfd);
    while((n = Rio_readlineb(&rio, buf, MAXLINE)) !=0) {
        printf("server received %d bytes\n", n);
        Rio_writen(connfd, buf, n);
    }
}
```

## Networking Programming

## Outline

- Web servers
  - HTTP Protocol
  - Web Content
  - CGI
- The Tiny Web Server
- Suggested Reading:
  - 11.5~11.6

## Web servers

- Clients and servers communicate using the HyperText Transfer Protocol (HTTP)
  - Client and server establish TCP connection
  - Client requests content
  - Server responds with requested content
  - Client and server close connection (usually)
- Current version is HTTP/1.1
  - RFC 2616, June, 1999.

## Web servers

![](img/9bd5f6161cb6607b56d2fb964d1b8794_743_0.png)

|  |  |
|---|---|
| HTTP | Web content |
| TCP | Streams |
| IP | Datagrams |

## Web content

- Web servers return **content** to clients
  - content: a sequence of bytes with an associated MIME (Multipurpose Internet Mail Extensions) type

- Example MIME types
  - `text/html` — HTML page
  - `text/plain` — Unformatted text
  - `application/postscript` — Postscript document
  - `image/gif` — Binary image encoded in GIF format
  - `image/jpg` — Binary image encoded in JPG format

## Static and dynamic content

- The content returned in HTTP responses can be either static or dynamic
  - Static content:
    - Content stored in files and retrieved in response to an HTTP request
    - Examples: HTML files, images, audio clips.
  - Dynamic content:
    - Content produced on-the-fly in response to an HTTP request
    - Example: content produced by a program executed by the server on behalf of the client.

## URLs

- Each file managed by a server has a unique name called a **URL** (Universal Resource Locator)

- URLs for static content:
  - identifies a file called `index.html`, managed by a Web server at `ipads.se.sjtu.edu.cn` that is listening on port 80.

```
http://ipads.se.sjtu.edu.cn:80/courses/ics/index.html
http://ipads.se.sjtu.edu.cn:/courses/ics/index.html
http://ipads.se.sjtu.edu.cn/courses/ics/
```
