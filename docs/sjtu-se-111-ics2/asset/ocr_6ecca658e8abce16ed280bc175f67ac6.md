# Prethreading

```
port = atoi(argv[0]);
sbuf_init(&sbuf, SBUFSIZE);
listenfd = open_listenfd(port);
/* Create worker threads */
for (i = 0; i < NTHREADS; i++)
    Pthread_create(&tid, NULL, thread, NULL);

while (1) {
    connfd = Accept (listenfd,
                     (SA *)&clientaddr, &clientlen);
    /* Insert connfd in buffer */
    sbuf_insert(&sbuf, connfd);
}
```