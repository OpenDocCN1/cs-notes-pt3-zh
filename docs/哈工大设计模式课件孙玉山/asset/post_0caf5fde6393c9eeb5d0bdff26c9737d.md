
## 2. P2P Architecture with Directory Server - 1st Generation P2P

## One Example P2P Architecture

![](img/95717dc23f76db2057b9aa0c49790307_888_0.png)

## 2. P2P Architecture with Directory Server - 1st Generation P2P

The interaction between clients by referencing a Directory Server

- a) **Send request.** Client A issues **a request** to the Directory server
- b) **Find peers.** The Directory server then uses the lists it keep to find the peer that contains the content that Client A interests in and tells Client A
- c) **Interactions.** Client A can then directly interact with **that client**, in this case Client D which services his request.

![](img/95717dc23f76db2057b9aa0c49790307_890_0.png)

## 2. P2P Architecture with Directory Server - 1st Generation P2P

## Detailed description of How one peer interacts with another peer?

- **Step 1. 连接到目录服务器** When the user connects to the network, the peer first attempts to connect to a directory server
  - to locate each of the user’s buddies and
  - to register the location of the user that is now coming on-line

## 2. P2P Architecture with Directory Server - 1st Generation P2P

Once peers are located, they can provide information about their

- **capabilities** (e.g., memory: 3G; harddisk:1000g , CPU型号D2550,速度3.4GHz)
- **the services they provide** (provides movie: deepSea.mp3: 1.5g).

## 2. P2P Architecture with Directory Server - 1st Generation P2P

## Step 2. 开始通讯  Opening the lines of communication

- After it determines their locations, the peer then attempts to establish contact with all of the buddies that it has found.
  - The peer can use a user interface for contacts
    - The user interface provides information to the user about what other users are on-line.

![](img/95717dc23f76db2057b9aa0c49790307_893_0.png)

## Pure P2P Architecture –
2nd Generation P2P

## 3. Pure P2P Architecture – 2nd Generation P2P

![](img/95717dc23f76db2057b9aa0c49790307_895_0.png)

## Pure P2P architecture

## 3. Pure P2P Architecture – 2nd Generation P2P

## Characteristics of Pure P2P Architecture

- a) 节点既是客户端又是服务器 Peers can act as clients and servers and have the same capability as its neighbors.
- b) 没有中心服务器 It has no central servers. It has every node as a Peer and has no central router.
- c) There are two routing structures,
  1. 分布式目录 One is a distributed catalogue;
  2. 直接发送消息 The other direct messaging.

![](img/95717dc23f76db2057b9aa0c49790307_897_0.png)

Find

Process of sending a query message

![](img/95717dc23f76db2057b9aa0c49790307_898_0.png)

Find

Process of sending a query message

## 3. Pure P2P Architecture – 2nd Generation P2P

## Gnutella: Example of Pure P2P Architecture

- **What is Gnutella?**
- Gnutella, a Pure P2P Model, is a **file sharing** application and protocol:
  - the end hosts join Gnutella by connecting to existing end hosts already on the Gnutella.

## 3. Pure P2P Architecture-2nd Generation P2P

## Gnutella History

- Originally conceived of by **Justin Frankel**, then 21 year old, founder of Nullsoft
- Nullsoft posts Gnutella to the web on 2000/03,
- Nullsoft was later acquired by AOL, which has now stopped this project.
- However, the Gnutella application had already distributed as an open source application (with different versions).
- Gnutella has become a Protocol now.

![](img/95717dc23f76db2057b9aa0c49790307_900_0.png)

## 3. Pure P2P Architecture – 2nd Generation P2P

How Gnutella works?

To **facilitate** file sharing, messages are sent between end hosts.

- Queries for files are broadcasted on the overlay network (覆盖网络), and
- Replies are routed back to the host that originally generated the query through the overlay network.
