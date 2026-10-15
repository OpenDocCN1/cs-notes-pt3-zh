# Buffered I/O: Implementation

+   - For reading from file
+   - File has associated buffer to hold bytes that have been read from file but not yet read by user code

![](bbox=[0.08, 0.48, 0.92, 0.7])

```
typedef struct {
    int rio_fd;                 /* descriptor for this internal buf */
    int rio_cnt;                /* unread bytes in internal buf */
    char *rio_bufptr;           /* next unread byte in internal buf */
    char rio_buf[RIO_BUFSIZE];  /* internal buffer */
} rio_t;
```