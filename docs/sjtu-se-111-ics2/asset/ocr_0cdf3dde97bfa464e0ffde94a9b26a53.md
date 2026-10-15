# The Tiny Web Server

```
```c
else { /* serve dynamic content */
    if (!(S_ISREG(sbuf.st_mode)) ||
        !(S_IXUSR & sbuf.st_mode)) {
        clienterror(fd, filename, "403", "Forbidden",
                    "Tiny couldn’t run the CGI program");
        return;
    }
    serve_dynamic(&rio, filename, cgiargs);
}
}
```
```