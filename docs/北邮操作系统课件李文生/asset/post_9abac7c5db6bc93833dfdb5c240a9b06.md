
## Communication Models (1/2)

- Communication may take place using either message passing or shared memory.

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_216_0.png)

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_216_1.png)

## Communication Models (2/2)

- **Message passing is**
  - useful when smaller numbers of data need to be exchanged, because no conflicts need to be avoided.
  - easier to implement for intercomputer communication.
- **Shared memory allows maximum speed and convenience of communication.**
  - It can be done at memory speeds when within a computer.

## 3.4.1 Shared-memory systems

### Producer-Consumer Problem

- A common paradigm for cooperating processes: *producer* process produces information that is consumed by a *consumer* process.
- We must have available a buffer of items that can be filled by the *producer* and emptied by the *consumer*.
  - A *producer* can produce one item while the *consumer* is consuming another item.
  - The *producer* and *consumer* must be **synchronized**.
- Two types of buffers are used
  - *unbounded-buffer* places no practical limit on the size of the buffer.
  - *bounded-buffer* assumes that there is a fixed buffer size.

## Shared-Memory Solution to Bounded-Buffer problem

### Shared data

```
#define BUFFER_SIZE 10
typedef struct {
...
} item;
item buffer[BUFFER_SIZE];
int in = 0;
int out = 0;
```

- **in** points to the next free position in the buffer;
- **out** points to the first full position in the buffer;
- The buffer is empty when **in == out**;
- The buffer is full when **((in + 1) % BUFFER_SIZE) == out**;
- The solution is correct, but can only use **BUFFER_SIZE-1** elements.

## Shared Buffer--Circular array

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_220_0.png)

- The buffer is empty when `in == out;`
- The buffer is full when `(in + 1) % BUFFER_SIZE == out.`

Solution is correct, but can only use BUFFER_SIZE-1 elements.

### Bounded-Buffer — *Producer Process*

```
item nextProduced;
while (1) {    /* produce an item in nextProduced */
              while (((in + 1) % BUFFER_SIZE) == out)
                    ; /* do nothing */
              buffer[in] = nextProduced;
              in = (in + 1) % BUFFER_SIZE;
            }
```

### Bounded-Buffer — *Consumer Process*

```
item nextConsumed;
while (1) {  while (in == out) ; /* do nothing */
              nextConsumed = buffer[out];
              out = (out + 1) % BUFFER_SIZE;
              /* consume the item in nextConsumed */
            }
```

## Implementation Questions

- Direct / indirect communication?
- Synchronous / asynchronous communication?
- Automatic / explicit buffering?
- How are links established?
- Can a link be associated with more than two processes?
- How many links can there be between every pair of communicating processes?
- What is the capacity of a link?
- Is the size of a message that the link can accommodate fixed or variable?
- Is a link unidirectional or bi-directional?

## Direct Communication--naming

- **Processes must name each other explicitly:**
  - `send(P, message)` – send a message to process P
  - `receive(Q, message)` – receive a message from process Q
- **Properties of communication link**
  - Links are established automatically.
  - A link is associated with exactly one pair of communicating processes.
  - Between each pair there exists exactly one link.
  - The link may be unidirectional, but is usually bi-directional.
- **Disadvantages**
  - Limited modularity of the resulting process definitions

## Indirect Communication(1/3)

- Messages are sent and received from mailboxes (also referred to as ports).
  - Each mailbox has a unique id.
  - Processes can communicate only if they share a mailbox.
- Primitives are defined as:
  - `send(A, message)` – send a message to mailbox A
  - `receive(A, message)` – receive a message from mailbox A
- Properties of communication link
  - A link is established only if processes share a common mailbox.
  - A link may be associated with many processes.
  - Each pair of processes may share several communication links.
  - A link may be unidirectional or bi-directional.
