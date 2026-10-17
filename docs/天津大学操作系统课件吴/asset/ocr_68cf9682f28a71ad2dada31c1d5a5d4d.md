# Producer-Consumer Problem
with Message Passing (1)

```
```c
#define N 100                         /* number of slots in the buffer */

void producer(void)
{
        int item;
        message m;                     /* message buffer */

        while (TRUE) {
                item = produce_item(); /* generate something to put in buffer */
                receive(consumer, &m);  /* wait for an empty to arrive */
                build_message(&m, item);/* construct a message to send */
                send(consumer, &m);     /* send item to consumer */
        }
}
```
```

...

The producer-consumer problem with N messages.