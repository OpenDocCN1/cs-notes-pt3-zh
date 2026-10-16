
## 4. Unstructured hierarchical P2P architecture– 3rd Generation P2P

- One ultrapeer can connect with multiple leaf nodes, depending on its capacity and capability.

- 在查找过程中，叶子节点的责任, Leaf nodes are only responsible for
  - initiating lookup requests,
  - receiving correlated lookup response, and
  - responding the requests that they can exactly answer,

- 在查找过程中，超级节点的责任。
- Ultrapeers are responsible for
  - 转发请求到其它超级节点 forwarding lookup requests to other ultrapeers or
  - 转发请求到自己的叶子节点 its own connected leaf nodes, if it knows exactly the leaf node is able to answer the request.
- Ultrapeers can also initiate requests and receive correlated responses.
- At the level of ultrapeer, similar flooding-based mechanism as Gnutella v0.4 is utilized to forward the lookup requests.

查找过程示意图

Return

![](img/95717dc23f76db2057b9aa0c49790307_917_0.png)

## Peer Node Architecture

每个节点都应该安装相同的软件

## 5. Peer Node Architecture

### 一个节点软件的功能

Each peer provides a **basic set of core services**:

- 1. 负责通讯 Handles communication with the network,
- 2. 管理信息 Manages information about the location, status, and privileges.
- 3. 提供扩展模块基础 Provides the foundation for extension modules

### 节点软件的架构

The architecture of a Peer implements the layered architectural Pattern. The functions are layered one on top of the other.

- 1. **Layer 1.** web server
- 2. **Layer 2.** Servlet engine
- 3. **Layer 3.** The request manager
- 4. **Layer 4.** The event service
- 5. **Layer 5.** Buddy manager
- 6. **Layer 6.** Access control

### Core components

Web Server foundation

Access Control

Buddy Manager (location, presence, grouping)

Event Service

Request Manager

Servlet Engine

Web Server

Module container

• Holds dynamically loaded modules

• provide access to servlet and the API

Extension modules

Outgoing events sent via HTTP

Incoming events from HTTP

Incoming HTTP servlet requests

the architecture of an individual peer

- • Base layer and its functionalities.

The system is based on top of a **Web server** and **servlet engine** that trigger functionality based on incoming HTTP requests.

- – The network infrastructure may vary by platform and provides the binding to the Web services available on that platform.

- – It provides simple parsing of the HTTP requests, passing the content on to the platform independent request manager.

### 5. Peer node Architecture

- **Request Manager**
  - receives the HTTP request from the server and, depending on the content,
  - invokes services within the peer to handle the request.

- **Module container**
  - loaded with modules, may register for requests based on the URL
  - When the request manager passes a request to a module, the module can provide the response to be returned, or pass the request along to another module for additional processing.

- **Event Service**
  Receive **events** that are passed over HTTP. The events carry the bulk (大多数) of communication between peers.
- **Functionalities of Event service**
  - receive the events
  - invoke the services that have registered interest in those events
  - allow components to send events to other peers

### Buddy Manager

### Functionalities

- **Buddy Manager** is a means of
  - identifying individual users and
  - controlling the access relationships between peers: who may access resources and about whom the user would like information

- Welcome or not?
  - Information in the incoming event or HTTP request serves to identify users as being welcome or not
  - It also defined levels of access, thus the user may permit or deny access to services.
