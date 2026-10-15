

```c
void serve_static(int fd, char *filename, int filesize)
{
    int srcfd;
    char *srcp, ftype[MAXLINE], buf[MAXBUF];

    /* send response headers to client */
    get_filetype(filename, ftype);
    sprintf(buf, "HTTP/1.0 200 OK\r\n");
    sprintf(buf, "%sServer: Tiny Web Server\r\n", buf);
    sprintf(buf, "%sContent-length: %d\n", buf, filesize);
    sprintf(buf, "%sContent-type: %s\r\n\r\n", buf, ftype);
    Rio_writen(fd, buf, strlen(buf));

    /* send response body to client */
    srcfd = Open(filename, O_RDONLY, 0);
    srcp = Mmap(0, filesize, PROT_READ, MAP_PRIVATE, srcfd, 0);
    Close(srcfd);
    Rio_writen(fd, srcp, filesize);
    Munmap(srcp, filesize);
}
```

## The Tiny Web Server

```c
/*
 * get_filetype - derive file type from file name
 */
void get_filetype(char *filename, char *filetype)
{
    if (strstr(filename, ".html"))
        strcpy(filetype, "text/html");
    else if (strstr(filename, ".gif"))
        strcpy(filetype, "image/gif");
    else if (strstr(filename, ".jpg"))
        strcpy(filetype, "image/jpg");
    else
        strcpy(filetype, "text/plain");
}
```

```c
void serve_dynamic(int fd, char *filename, char *cgiargs)
{
    char buf[MAXLINE];

    /* return first part of HTTP response */
    sprintf(buf, "HTTP/1.0 200 OK\r\n");
    Rio_writen(fd, buf, strlen(buf));
    sprintf(buf, "Server: Tiny Web Server\r\n");
    Rio_writen(fd, buf, strlen(buf));

    if (Fork() == 0) { /* child */
        /* real server would set all CGI vars here */
        setenv("QUERY_STRING", cgiargs, 1);
        Dup2(fd, STDOUT_FILENO); /* redirect output to client */
        Execve(filename, NULL, environ); /* run CGI program */
    }
    Wait(NULL); /* parent reaps child */
}
```

## Proxies

- A **proxy** is an intermediary between a client and an **origin server**.
  - To the client, the proxy acts like a server.
  - To the server, the proxy acts like a client.

![](img/9bd5f6161cb6607b56d2fb964d1b8794_787_0.png)

## Why Proxies?

- Can perform useful functions as requests and responses pass by.
  - Examples: Caching, logging, anonymization, filtering, transcoding.

![](img/9bd5f6161cb6607b56d2fb964d1b8794_788_0.png)

Slower, more expensive global network

Fast, inexpensive local network

## Concurrent Programming

## Outline

- Topics:
  - Concurrent programming with processes
  - Concurrent programming with threads
  - Concurrent programming with I/O multiplexing
- Suggested reading:
  - 12.1–12.3

## Concurrency

- Concurrency is a general phenomenon.
  - Hardware exception handlers
  - Processes
  - Unix signal handlers

## Concurrency

- Application-level concurrency is useful.
  - Responding to asynchronous events
  - Computing in parallel on multiprocessor
  - Accessing slow I/O devices
  - Interacting with humans
  - Reducing latency by deferring work
  - Servicing multiple network clients

## Concurrency

- Concurrent programming:
  - Applications that use application-level concurrency
- Three basic approaches for concurrent programming:
  - Processes
  - Threads
  - I/O multiplexing

## Concurrency

- Concurrent programming is hard.
  - The human mind tends to be sequential.
  - Thinking about all possible sequences of events in a computer system is at least error-prone and frequently impossible.
  - Classical problem classes of concurrent programs:
    - Data races, deadlock, and livelock/starvation

## Iterative Echo Server

Client

Server

open_clientfd

open_listenfd

Connection request

Client / Server Session

Await connection request from next client

socket

socket

bind

listen

accept

connect

rio_writen

rio_readlineb

rio_readlineb

rio_writen

close

EOF

rio_readlineb

close

## Review: Iterative Echo Server

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

- Accept a connection request
- Handle echo requests until client terminates

