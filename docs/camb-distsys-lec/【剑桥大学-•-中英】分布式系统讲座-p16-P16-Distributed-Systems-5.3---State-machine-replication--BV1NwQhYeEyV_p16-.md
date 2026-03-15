# 【剑桥大学-•-中英】分布式系统讲座-p16-P16-Distributed-Systems-5.3---State-machine-replication--BV1NwQhYeEyV_p16-

So we've been talking about replication。 and if you remember in the last lecture。

 we talked about broadcast protocols and the whole point of a broadcast protocol is for all of the nodes to receive some set of messages in some order and the point of replication is for all of the replicas to process some updates So you might be wondering shouldn't we be able to use a broadcast protocol to do replication and you would be right。

 indeed we can use broadcast protocols。 and we're going to look at that now。 So first of all。

 let's start with Ptoal order broadcast the strongest of the broadcast protocols。

 which we considered。 and if you remember the point of total order broadcast is that all of the nodes will deliver the same set of messages in the same order。

 which is exactly what we want for replication and this approach is called state machine replication So the algorithm is simple whenever a replica wants to make some update to its state It uses Ptoal order broadcast to broadcast that update。



![](img/9cc89e511f8fd9178c105c3c72450041_1.png)

![](img/9cc89e511f8fd9178c105c3c72450041_2.png)

![](img/9cc89e511f8fd9178c105c3c72450041_3.png)

All of the replicas。And whenever a replica delivers one of these updates。

 it processes that update applies to its own state。

 so it updates its own state as a function of this update that it received over the broadcast。



![](img/9cc89e511f8fd9178c105c3c72450041_5.png)

![](img/9cc89e511f8fd9178c105c3c72450041_6.png)

And the key thing that makes this work is that the logic for applying an update is deterministic and so。



![](img/9cc89e511f8fd9178c105c3c72450041_8.png)

You can think of each replica as a state machine， the state of the replica is all of the data that it has stored and every replica starts off in a fixed starting state which is usually an empty database containing no data and then the deterministic state update means that whenever two replicas are in the same state and we give them the same input then they will transition to the same next state and because50 total order broadcast ensures that each of the replicas receive delivers the same updates in the same order if we take these delivered updates to be the input to the state machine then on each replica the state machine is going to go through the same sequence of state transitions。



![](img/9cc89e511f8fd9178c105c3c72450041_10.png)

![](img/9cc89e511f8fd9178c105c3c72450041_11.png)

![](img/9cc89e511f8fd9178c105c3c72450041_12.png)

![](img/9cc89e511f8fd9178c105c3c72450041_13.png)

![](img/9cc89e511f8fd9178c105c3c72450041_14.png)

![](img/9cc89e511f8fd9178c105c3c72450041_15.png)

And they're both going to end up in the same state after they've processed the same sequence of messages。

 So this is exactly what we want of state machine replication。 and it's， it's a。

 it's very good way of performing replication just because if we have this total order broadcast。

 then the replication algorithm itself is really simple。 it's just。😊。



![](img/9cc89e511f8fd9178c105c3c72450041_17.png)

![](img/9cc89e511f8fd9178c105c3c72450041_18.png)

![](img/9cc89e511f8fd9178c105c3c72450041_19.png)

![](img/9cc89e511f8fd9178c105c3c72450041_20.png)

Whenever we have an update， we broadcast it by a total order broadcast。

 and whenever we deliver an update， we update the state accordingly。



![](img/9cc89e511f8fd9178c105c3c72450041_22.png)

And this idea is actually very widely used in a whole range of different replicated systems。

 so there are some databases， some distributed databases。

 for example which use this approach for replicating transactions so this logic here of the updating the state as long as it's deterministic it can be any arbitrarily complex logic so you can package a whole transaction including arbitrary business logic into this and make sure that the inputs to the transaction get delivered to all of the replicas through total order broadcast and then you can independently execute this transaction on each of the replicas and they will end up in the same state very nice very nice principle a very similar principle underlies blockchains and distributed ledgers and smart contracts and all of this area what you have in a blockchain is a chain of blocks and this chain of blocks is actually exactly the sequence of messages delivered by a total。



![](img/9cc89e511f8fd9178c105c3c72450041_24.png)

![](img/9cc89e511f8fd9178c105c3c72450041_25.png)

![](img/9cc89e511f8fd9178c105c3c72450041_26.png)

![](img/9cc89e511f8fd9178c105c3c72450041_27.png)

![](img/9cc89e511f8fd9178c105c3c72450041_28.png)

![](img/9cc89e511f8fd9178c105c3c72450041_29.png)

broadcast protocol so there's a consensus mechanism around performing implementing this total order broadcast。

 but once you've got it it's just a sequence of transactions or updates or jobs that need to be performed in a certain order and each replica will process those deterministic transactions in the same order and therefore they will end up in the same state and in this case the state constitutes a ledger saying who owns which coins for example。



![](img/9cc89e511f8fd9178c105c3c72450041_31.png)

![](img/9cc89e511f8fd9178c105c3c72450041_32.png)

![](img/9cc89e511f8fd9178c105c3c72450041_33.png)

![](img/9cc89e511f8fd9178c105c3c72450041_34.png)

Now the downside of state machine replication are the downsides of total order broadcast。

 so if you remember when we were looking at total order broadcast。

 we said that when a node wants to broadcast a message it cannot immediately deliver that message message to itself。

 it has to coordinate with the other nodes in order to decide the order in which the replic are going to deliver the messages and the same applies here with state machine replication。

 so that means the repa cannot immediately update its own state。

 it has to go through the total order broadcast process in order to node the order in which the states in which these updates are going to get applied。



![](img/9cc89e511f8fd9178c105c3c72450041_36.png)

And it does mean that we need a total order broadcast protocol。

 we will study that in the next lecture。

![](img/9cc89e511f8fd9178c105c3c72450041_38.png)

Another example of how this principle of total order broadcast is used for replication is in what is called passive replication for databases and so what happens here is that you have got a leader database and one or more follower databases and if you remember what we said about total order broadcast one way that you can implement total order broadcast is by designating one node as the leader and that leader is going to decide on an order of the messages and then all of the other nodes are going to deliver the messages in the order they were broadcast by the leader and this is exactly what happens in database replication so in database replication you've got one client which requests the leader to execute some transaction and maybe another client concurrently requests the leader to also execute some transaction and those transactions might execute concurrently on the leader。



![](img/9cc89e511f8fd9178c105c3c72450041_40.png)

![](img/9cc89e511f8fd9178c105c3c72450041_41.png)

We do have usually the requirement that only the leader can execute transactions if those transactions are going to modify the database state for any read only transactions could execute on the followers。

 but any rewrite transactions have to execute on the leader。 Now。

 transactions may execute concurrently， but they will commit in some total order。

 and this commit order is the crucial thing here， because when a transaction commits。

 then a record is appended to the commit log saying what were the changes that were data changes that were made by this transaction and this commit record is sent to all of the followers via total order broadcast。



![](img/9cc89e511f8fd9178c105c3c72450041_43.png)

![](img/9cc89e511f8fd9178c105c3c72450041_44.png)

So then all of the followers will apply the transaction commits and the data changes from each transaction in the commit order。

 and so again， we've got the same principle， all of the leader and all of the followers are applying the commits in the same order and so they go through the same sequence of state transactions again using the same principle as as a state machine replication。



![](img/9cc89e511f8fd9178c105c3c72450041_46.png)

So。That is using total order broadcast。 It's clearly a good way of implementing implementing replication。

We also discussed weaker forms of broadcasts。 So we discussed causal broadcast and PI0 broadcast reliable broadcast and best effort broadcast。

 So can we use those as well for implementing replication， And the answer is， yes， we can。

 It just requires a little bit more care。 So one concept we need for this is commutivity。

And so we're going to say that two updates are commutative if you can apply them in either order。

 So either you apply first F then G or you apply first G then F。

 and the end result is the same no matter in which order you apply these two updates。 Now。

 clearly not all updates are commutative only we have to specifically design the algorithm for updates to be commutative if we wanted to be commutative。

 but it is possible to design updates in such a way that they are commutative。



![](img/9cc89e511f8fd9178c105c3c72450041_48.png)

![](img/9cc89e511f8fd9178c105c3c72450041_49.png)

![](img/9cc89e511f8fd9178c105c3c72450041_50.png)

And if we do that， then for example， we can use causal broadcast so with causal broadcast。

 we also require that processing update is deterministic。

 that is' still a requirement of any of these broadcast based replication models。



![](img/9cc89e511f8fd9178c105c3c72450041_52.png)

![](img/9cc89e511f8fd9178c105c3c72450041_53.png)

But then remember that the order guaranteed provided by by causal broadcast is if one message happened before another。

 then those messages get delivered in there happens before order。

 but two concurrent messages might be delivered in either order。

 and so if we want to ensure that all of the replicas end up in the same state。

 then we must ensure that for any two updates that are concurrent。

 their state update functions must commute And so if we have that。

 then that means that any noncommutative state updates will be provided in the same in the right order by causal broadcast。

 and any any updates that might be reordered by causal broadcast are commutative and so therefore we can apply them in either order and will end up in the same state。



![](img/9cc89e511f8fd9178c105c3c72450041_55.png)

![](img/9cc89e511f8fd9178c105c3c72450041_56.png)

![](img/9cc89e511f8fd9178c105c3c72450041_57.png)

![](img/9cc89e511f8fd9178c105c3c72450041_58.png)

![](img/9cc89e511f8fd9178c105c3c72450041_59.png)

![](img/9cc89e511f8fd9178c105c3c72450041_60.png)

Now we can generalize this further and with reliable broadcast we have no ordering guarantees at all。

 we just have the guarantee that every message is delivered exactly at once。For in this case。

 we have to have all of the all of the updates that must commute because the broadcast protocol provides no ordering guarantees and we could go even weaker so we could even go to best effort broadcast in which case we're not even guaranteed any particular number of deliveries for a certain message or a message might be lost or it might be delivered multiple times。

 So in this case， a state update function will have to tolerate message loss and it will have to tolerate messages being delivered multiple times through itempots。

 but you can see that actually all these different models of broadcast。

 we can use in order to build replication systems。

![](img/9cc89e511f8fd9178c105c3c72450041_62.png)

![](img/9cc89e511f8fd9178c105c3c72450041_63.png)

![](img/9cc89e511f8fd9178c105c3c72450041_64.png)

![](img/9cc89e511f8fd9178c105c3c72450041_65.png)

![](img/9cc89e511f8fd9178c105c3c72450041_66.png)

So that's all for this lecture in the next lecture we're going to drill into some more detail on how actually we implement this total order broadcast in a way that is reliable。



![](img/9cc89e511f8fd9178c105c3c72450041_68.png)

![](img/9cc89e511f8fd9178c105c3c72450041_69.png)