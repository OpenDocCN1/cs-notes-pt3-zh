
## Handling Inconsistent Updates

- Dealing with inconsistent updates is hard in general. Manual intervention often required to merge the updates.
- Version vector schemes
  - were developed to deal with failures in a distributed file system, where inconsistencies are rare.
  - are used to maintain a unified file system between a fixed host and a mobile computer, where updates at the two hosts have to be merged periodically.
    - Also used for similar purposes in groupware systems.
  - are used in database systems where mobile users may need to perform transactions.
    - In this case, a “document” may be a single record.
- Inconsistencies must either be very rare, or fall in special cases that are easy to deal with in most cases

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1378_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1379_0.png)

## End of Chapter

## Figure 25.02

line segment

{(x1,y1), (x2,y2)}

triangle

{(x1,y1), (x2,y2), (x3,y3)}

polygon

{(x1,y1), (x2,y2), (x3,y3), (x4,y4), (x5,y5)}

polygon

{(x1,y1), (x3,y3), ID1}
{(x1,y1), (x4,y4), ID1}
{(x1,y1), (x4,y4), (x5,y5), ID1}

object

representation

## Figure 25.03

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1381_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1381_1.png)

(a) Difference of cylinders

(b) Union of cylinders

## Figure 25.04

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1382_0.png)

## Figure 25.05

## Figure 25.06

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1384_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1385_0.png)

## Chapter 26: Advanced Transaction Processing

## Chapter 26: Advanced Transaction Processing

- Transaction-Processing Monitors
- Transactional Workflows
- High-Performance Transaction Systems
  - Main memory databases
  - Real-Time Transaction Systems
- Long-Duration Transactions
- Transaction management in multidatabase systems

## Transaction Processing Monitors

- **TP monitors** initially developed as multithreaded servers to support large numbers of terminals from a single process.
- Provide infrastructure for building and administering complex transaction processing systems with a large number of clients and multiple servers.
- Provide services such as:
  - Presentation facilities to simplify creating user interfaces
  - Persistent queuing of client requests and server responses
  - Routing of client messages to servers
  - Coordination of two-phase commit when transactions access multiple servers.
- Some commercial TP monitors: CICS from IBM, Pathway from Tandem, Top End from NCR, and Encina from Transarc

## TP Monitor Architectures

(a) Process-per-client model

(b) Single-server model

(c) Many-server, single-router model

(d) Many-server, many-router model

remote clients
server
files

remote clients
server
files

remote clients
router
servers
files

remote clients
routers
servers
files

monitor

## TP Monitor Architectures (Cont.)

- **Process per client model** - instead of individual login session per terminal, server process communicates with the terminal, handles authentication, and executes actions.
  - Memory requirements are high
  - Multitasking- high CPU overhead for context switching between processes

- **Single process model** - all remote terminals connect to a single server process.
  - Used in client-server environments
  - Server process is multi-threaded; low cost for thread switching
  - No protection between applications
  - Not suited for parallel or distributed databases

## TP Monitor Architectures (Cont.)

- **Many-server single-router model** - multiple application server processes access a common database; clients communicate with the application through a single communication process that routes requests.
  - Independent server processes for multiple applications
  - Multithread server process
  - Run on parallel or distributed database

- **Many server many-router model** - multiple processes communicate with clients.
  - Client communication processes interact with router processes that route their requests to the appropriate server.
  - Controller process starts up and supervises other processes.
