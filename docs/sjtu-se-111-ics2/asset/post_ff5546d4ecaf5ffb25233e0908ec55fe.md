
## The Tiny Web Server

```
1 /*
2 * tiny.c - A simple HTTP/1.0 Web server that uses the
3 * GET method to serve static and dynamic content.
4 */
5 #include "csapp.h"

void doit(int fd);
void read_requesthdrs(int fd);
int parse_uri(char *uri, char *fname, char *cgiargs);
void serve_static(rio_t *rio, char *fname, int fsize);
void get_filetype(char *fname, char *ftype);
void serve_dynamic(rio_t *rio,char *fname,char*cgiargs);
void clienterror(rio_t *rio, char *cause, char *errnum,
char *shortmsg, char *longmsg);
```

```
16 int main(int argc, char **argv)
17 {
    int listenfd, connfd, port, clientlen;
    struct sockaddr_in clientaddr;

    /* check command line args */
    if (argc != 2) {
        fprintf(stderr,"usage: %s <port>\n", argv [0]);
        exit(1);
    }
    port = atoi(argv[1]);
```

```
28  listenfd = open_listenfd(port);
  while (1) {
      clientlen = sizeof(clientaddr);
      connfd = Accept(listenfd,
                  (SA *)&clientaddr, &clientlen);
      doit(connfd);
      Close(connfd);
  }
}
```

## The Tiny Web Server

```
1 void doit(int fd)
2 {
    int is_static;
    struct stat sbuf;
    char buf[MAXLINE], method[MAXLINE];
    char uri[MAXLINE], version[MAXLINE];
    char filename[MAXLINE], cgiargs[MAXLINE];
    rio_t rio;
```

GET /courses/ics HTTP/1.1
method uri version

```
9   /* read request line and headers */
10  Rio_readinitb(&rio, fd)
11  Rio_readlineb(&rio, buf, MAXLINE);
12  sscanf(buf, "%s %s %s\n", method, uri, version);
13  if (strcasecmp(method, "GET")) {
      clienterror(fd, method, "501", "Not Implemented",
                  "Tiny does not implement this method");
      return;
  }
  read_requesthdrs(&rio);
```

```
/* parse URI from GET request */
is_static = parse_uri(uri, filename, cgiargs);
if (stat(filename, &sbuf) < 0) {
    clienterror(fd, filename, "404", "Not found",
                "Tiny couldn't find this file");
    return;
}

if (is_static) { /* serve static content */
    if ((!S_ISREG(sbuf.st_mode)) ||
        !(S_IRUSR & sbuf.st_mode)) {
            clienterror(fd, filename, "403",
            "Forbidden", "Tiny couldn't read the file");
            return;
    }
    serve_static(&rio, filename, sbuf.st_size);
}
```

```
else { /* serve dynamic content */
    if (!(S_ISREG(sbuf.st_mode)) ||
        !(S_IXUSR & sbuf.st_mode)) {
        clienterror(fd, filename, "403", "Forbidden",
                    "Tiny couldn't run the CGI program");
        return;
    }
    serve_dynamic(&rio, filename, cgiargs);
}
}
```

```
1 void clienterror(rio_t *fd, char *cause, char *errnum,
2                 char *shortmsg, char *longmsg)
3 {
    char buf[MAXLINE], body[MAXBUF];

    /* build the HTTP response body */
    sprintf(body, "<html><title>Tiny Error</title>");
    sprintf(body, "%s<body bgcolor=\"ffffff\">\r\n", body);
    sprintf(body, "%s%s: %s\r\n", body, errnum, shortmsg);
   sprintf(body, "%s<p>%s: %s\r\n", body, longmsg, cause);
   sprintf(body, "%s<hr><em>Tiny Web server</em>\r\n",body);

   /* print the HTTP response */
   sprintf(buf, "HTTP/1.0 %s %s\r\n", errnum, shortmsg);
   Rio_writen(fd, buf, strlen(buf));
   sprintf(buf, "Content-type: text/html\r\n");
   Rio_writen(fd, buf, strlen(buf));
   sprintf(buf, "Content-length: %d\r\n\r\n", strlen(body));
   Rio_writen(fd, buf, strlen(buf));
   Rio_writen(fd, body, strlen(body));
}
```

## The Tiny Web Server

```
1 void read_requesthdrs(rio_t *fd)
2 {
    char buf[MAXLINE];

    Readline(fd, buf, MAXLINE);
    while(strcmp(buf, "\r\n"))
        Rio_readlineb(fd, buf, MAXLINE);
    return;
}
```

```
1 int parse_uri(char *uri, char *filename, char *cgiargs)
2 {
    char *ptr;

    if (!strstr(uri, "cgi-bin")) { /* static content */
        strcpy(cgiargs, "");
        strcpy(filename, ".");
        strcat(filename, uri);
        if (uri[strlen(uri)-1] == '/')
           strcat(filename, "home.html");
        return 1;
    }
    else { /* dynamic content */
        ptr = index(uri, '?');
        if (ptr) {
            strcpy(cgiargs, ptr+1);
            *ptr = '\0';
        } else
            strcpy(cgiargs, "");
        strcpy(filename, ".");
        strcat(filename, uri);
        return 0;
    }
}
```
