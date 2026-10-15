
## Prethreading
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

## Prethreading
```
void *thread(void *vargp)
{
    Pthread_detach(pthread_self());
    while (1) {
        int connfd = sbuf_remove(&sbuf);
        /* Remove connfd from buffer */
        echo_cnt(connfd);
        /* Service client */
        Close(connfd);
    }
}
```

## Prethreading
```
#include "csapp.h"

static int byte_cnt;      /* byte counter */
static sem_t mutex;       /* and the mutex that protects it */

static void init_echo_cnt(void)
{
    Sem_init(&mutex, 0, 1);
    byte_cnt = 0;
}
```

## Prethreading
```
void echo_cnt(int connfd)
{
    int n; char buf[MAXLINE]; rio_t rio;
    static pthread_once_t once = PTHREAD_ONCE_INIT;

    Pthread_once(&once, init_echo_cnt);
    Rio_readinitb(&rio, connfd);
    while((n = Rio_readlineb(&rio, buf, MAXLINE)) != 0) {
        P(&mutex);
        byte_cnt += n;
        printf("thread %d rec. %d(%d) byte on fd %d\n",
               (int)pthread_self(),n,byte_cnt, connfd);
        V(&mutex);
        Rio_writen(connfd, buf, n);
    }
}
```

## Thread-safe functions
- Functions called from a thread must be thread-safe
- Definition: A function is thread-safe iff it will always produce correct results when called repeatedly from multiple concurrent threads.

## Thread-safe functions
- We identify four (non-disjoint) classes of thread-unsafe functions:
  - Class 1: Failing to protect shared variables.
  - Class 2: Relying on persistent state across invocations.
  - Class 3: Returning a pointer to a static variable.
  - Class 4: Calling thread-unsafe functions.

## Thread-unsafe functions (case 2)
- Class 2: Relying on persistent state across invocations
```
unsigned int next = 1;
/* rand - return pseudo-random int on 0..32767 */
int rand(void)
{
    next = next * 110351524 + 12345 ;
    return (unsigned int)((next/65536) % 32768);
}
/* srand - set seed for rand() */
void srand(unsigned int seed)
{
    next = seed;
}
```

## Thread-unsafe functions (case 2)
- Pass state as part of argument
  - and, thereby, eliminate static state
```
/* rand_r - return pseudo-random int on 0..32767 */
int rand_r(int *nextp)
{
    *nextp = *nextp * 110351524 + 12345 ;
    return (unsigned int)((*nextp/65536) % 32768);
}
```

## Thread-safe functions
- Class 3: Returning a pointer to a static variable
```
struct hostent *gethostbyname(char name)
{
    static struct hostent host;
    <contact DNS and fill in h>
    return &host;
}
```

## Thread-safe functions
```
hostp = Malloc(...);
gethostbyname_r(name, hostp);
```
- Class 3: (Fixes)
  - Rewrite so caller passes pointer to struct
    - Issue: Requires changes in caller and callee
  - "Lock-and-copy"
    - Issues: caller must free memory
```
struct hostent *gethostbyname_ts(char *name)
{
    struct hostent *p,*q = Malloc(...);
    P(&mutex);
    p = gethostbyname(name);
    *q = *p;
    V(&mutex);
    return q;
}
```

## Thread-safe functions
- Class 4: Calling thread-unsafe functions.
  - Calling one thread-unsafe function makes the entire function that calls it thread-unsafe
  - Fix: Modify the function so it calls only thread-safe functions ☺

## Reentrant functions
- A function is reentrant iff it accesses NO shared variables when called from multiple threads.
  - Reentrant functions are a important subset of thread-safe functions.
  - Require no synchronization operations.

## Reentrant functions
![](img/9bd5f6161cb6607b56d2fb964d1b8794_903_0.png)

NOTE: The fixes to Class 2 thread-unsafe functions require modifying the function to make it reentrant
