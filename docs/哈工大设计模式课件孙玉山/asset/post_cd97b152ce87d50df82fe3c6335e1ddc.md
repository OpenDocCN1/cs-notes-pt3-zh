
## 3. Pure P2P Architecture – 2nd Generation P2P

Query steps:

- 1. 【Connect to P2P Network】 Node A is first connected to the network.
- 2. 【Find New Nodes】 Ping Node A Pings to the other Nodes (B and C) to discover new nodes on the network.
- 3. 【New Node Replies】 Pong A pong message is sent as a reply to a ping and provides information on a network node, including
  - IP address,
  - port number (端口号), and
  - number of files shared.
- 4. 【Send query message to new node】 A query message is used to search for files shared by other nodes on the network. It contains a query string and a minimum requested link speed.
- 5. 【Get query reply】 A query reply message contains
  - a list of files which match a given query,
  - the size of each file, and
  - the link speed of the responding node.
- 6. 【Upload file】 A push message is used to upload file to clients behind a firewall who can not download files themselves.

How long will a specific request "live"?

- Time to live. TTL: "time to live". It determines how long a specific request will "live" on the network.
  - The number is how many "layers" each request will pass through

- 1) 发送给7个附近的client(第1层)
- 2) 每个第1层节点再发送给6个附近的节点（第2层）
- 3) 每个第2层节点再发送给5个附近的节点（第3层）
- ...

![](img/95717dc23f76db2057b9aa0c49790307_906_0.png)

没找到

Search is not guaranteed if object is outside the search range!

### Limitations/Difficulties

- 1) Unstable connectivity of the servants
  - performance management difficult
- 2) Scalability issues: e.g. when TTL=10, will produce huge networks
- 3) 搜索范围不够大，本应该存在的资源没有被覆盖

### Gnutella Protocol (cont)

- Gnutella is a distributed protocol such that the clients become servers and they become clients at the same time. A node
  - is a Client when it is looking for some data and
  - is a Server if it is servicing a request of another node.
- The communication between the nodes is done by the TCP/IP protocol.

### Properties of Gnutella

- a) Reliable: If one computer goes down, the network is unaffected, Hence more reliable.
- b) Gnutella permits swapping files of any type.
- c) Anonymous: Gnutella is anonymous-there is no need to provide a name or e-mail address to use Gnutella
- d) Share anything: Gnutella provides a mechanism of resource sharing: People can share anything, family photos, computer program, and home movies, etc.
- e) Pure P2P: Gnutella is Pure P2P and is completely decentralized.

## 4. Unstructured hierarchical P2P architecture– 3rd Generation P2P

- Problems in traditional pure P2P architecture Gnutella V0.4
- 网络搜索量大增。 Large scale P2P networks around the world caused the ever-increasing search traffic across different administrative domains.
- 对于大的网络，搜索应答率变得越来越低。 The search recall ratio ( the number of search results: the total number of available copies of the searched object) was significantly decreased as the network scale became larger
- 需要新设计，以便改善性能
- To tackle this problem, Gnutella v0.6 introduced two-layer hierarchy in its architecture as below

超级节点sn

叶子节点leaf

### Unstructured hierarchical P2P architecture– 3rd Generation P2P: Gnutella v0.6 network topology

![](img/95717dc23f76db2057b9aa0c49790307_913_0.png)

### Explanation of the architecture

- In this architecture, nodes are divided into leaf nodes and ultrapeer nodes.
- A leaf node (叶子节点): only maintains connection with its own ultrapeer,
- An ultrapeer (超级节点):
  - maintains connections to its own leaf nodes and acts as proxy for them
  - connects to the other ultrapeers from the overlay
