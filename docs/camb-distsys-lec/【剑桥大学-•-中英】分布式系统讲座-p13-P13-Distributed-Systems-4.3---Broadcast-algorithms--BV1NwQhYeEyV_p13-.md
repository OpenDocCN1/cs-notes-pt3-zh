# 【剑桥大学-•-中英】分布式系统讲座-p13-P13-Distributed-Systems-4.3---Broadcast-algorithms--BV1NwQhYeEyV_p13-

Next， let's have a look at algorithms for actually implementing these different models of broadcast。

 So we're going to do that in two separate stages。 First of all。

 we'll show how to take best effort broadcast and make it reliable。

 And then once we've got reliable broadcast， we can layer on top of that modules for doing the delivery order。

 which allows us then to do either Pfo or causal or total order broadcast。

 So let's start with the reliability layer here。

![](img/9d588e5642b5f59258924d0c1c1b3c75_1.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_2.png)

The most obvious thing you might think about， like as。

 as a broadcast algorithm is you have the node that wants to broadcast a message just sends that message individually to every other node via point to point links and make those point point links reliable so that if the message gets dropped along the way。

 then the sender will resend it。 And so because then through retransmission。

 the message will eventually get through to every other node。 This， unfortunately。

 does not quite work。

![](img/9d588e5642b5f59258924d0c1c1b3c75_4.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_5.png)

Because what could happen is this here， A could try to broadcast message M1 to B and C。

 The message gets through to C， but the message gets dropped on its way to B。

 So A has to retransmit the message to B。 But then a crashes before a is able to complete this retransmission。

 And in this case， nobody is ever going to retry the sending of message M1 to B。 And so therefore。

 C will have delivered a message that B did not deliver B is never going to deliver this message and therefore we have an inconsistency。

 So we have to now design an algorithm which is robust so that even if the sender of a message crashes。

 all of the remaining nodes will still agree on which message was actually delivered。



![](img/9d588e5642b5f59258924d0c1c1b3c75_7.png)

And so one technique we can use is called eager reliable broadcast。

 and that relies on essentially just everybody sending messages everywhere。 So， first of all。

 A wants to broadcast M1 to B and C。 When B first receives M1。

 it rebroadcasts the same message again by a point to point links to every other node。

 And so this way， then even if A crashed， B will have further disseminated the message。

 And when C first receives the message， C will also rebroad the message to everyone else。😊。



![](img/9d588e5642b5f59258924d0c1c1b3c75_9.png)

And so this algorithm actually does ensure reliability。 it ensures that even if nodes crash。

 all of the non crashed nodes receive the message。However， it is quite expensive because。



![](img/9d588e5642b5f59258924d0c1c1b3c75_11.png)

Every node that receives a message will again send that message to n minus1 other nodes。

 and so in total we're going to end up with on the order of n squared message is being sent for every single message that a node wants to broadcast。



![](img/9d588e5642b5f59258924d0c1c1b3c75_13.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_14.png)

So we get reliability， but at the cost of fairly high network bandwidth。

Now lots of different algorithms have been designed to optimize this and one particular interesting group of algorithms is called gossip protocols。

 so they are modelled in the way how gossip and might spread through a network of people where one person hear is gossip from somebody and they then tell a few other people about this gossip and so eventually this information spreads through a group through a population of people they' are sometimes also called epidemic protocols because theyre somewhat similar to the way that an infectious disease might spread through a population。



![](img/9d588e5642b5f59258924d0c1c1b3c75_16.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_17.png)

And so in this example here each little blob is a node in the system。

 and I've just taken as the parameter for this algorithm that each node sends on the message to three other nodes and those three other nodes are picked at random And so here the red node is sending the message to three other nodes and then these three other nodes。

 each received a message and they each rebroad the message to three other randomly selected nodes and those recipients of those broadcasts。

 they again broadcast them further to others。 and you see that sometimes messages go to a node that has already received a message previously。

 sometimes messages even go back to a node that had the message sometime in the past but eventually over several rounds of this protocol with very high probability we reach a stage in which the message has received all of the nodes and now all of the nodes are black。



![](img/9d588e5642b5f59258924d0c1c1b3c75_19.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_20.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_21.png)

Let me just go through that animation again because it's so beautiful。 So we have the node spreading。

 the message spreading here。 And so in this case。😊。



![](img/9d588e5642b5f59258924d0c1c1b3c75_23.png)

All 30 nodes in this example have received a message after about six rounds of communication。

So this is。😊，There are lots of details that you can tune about gossip protocols about how exactly they decide when to send messages and when to stop sending messages and so on。

 but the basic principle is this， they are a way of achieving reliable broadcasts and they are quite robust so that even if some of the nodes crash or some of the messages get lost in the network。

 we still very have very high probability that all of the messages get through to all of the nodes。

Okay， so that gives us the reliability Now next look let's look at the ordering。

 so if we want to achieve PIO broadcasts， for example。

 that means we have to ensure that all of the messages by the same sender are delivered in the right order。

 This is an algorithm of how we might achieve this so each node here maintain three variables。



![](img/9d588e5642b5f59258924d0c1c1b3c75_25.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_26.png)

Sender sequence number is just an integer that gets incremented node for every message broadcast by this particular node delivered is a vector of integers indicating how many messages from each particular sender we have delivered and buffer is a holdback queue of messages so that if a message is not yet ready to be delivered we put it in the buffer and then pick it out of the buffer sometime later。



![](img/9d588e5642b5f59258924d0c1c1b3c75_28.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_29.png)

So if we want to broadcast a message， pick we attach the node number of the sender I and send and the attach we attach the sequence number of the sender to the message and this triple gets disseminate it to all of the nodes by a reliable broadcast and then we increment a sequence number for next time we want to broadcast。

Also， when we receive a message via reliable broadcast at node and I， we， first of all。

 add the message to the buffer and then we look at the buffer trying to find any messages that are ready to be delivered。

 and here ready to be delivered means that for any given sender we have a message in the buffer where the sequence number is the next the next integer that we are expecting in the sequence of sequence number from that particular sender。

 And so if we have a message matching that， then we take that message delivered to the application and we increment our local vector of the number of message is we have delivered from a particular sender。

 and so this is it this achieveies50 broadcast。

![](img/9d588e5642b5f59258924d0c1c1b3c75_31.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_32.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_33.png)

Next， let's have a look at causal broadcast。 The algorithm。

 The structure of the algorithm is very similar。 We start with the same three variables。 So again。

 we have a sender sequence number。 We have a vector counting the number of delivered messages。

 and we have the holdback buffer。When we want to broadcast a message at NI， first of all。

 we create this new variable dependencies。 So that captures the causal dependencies of this message。

 So it's a way of determining which messages happen before this particular message and those will have to be done all of the messages that have to be delivered before this message being broadcast。

 So we take dependencies to be a copy of our delivered vector。

 and we update the sending the broadcasting nodes own entry to be equal to the sequence number。

And then we send the message via reliable broadcast again。 This time。

 we don't attach the sequence number， but we attach this dependencies vector， in addition to I。

 which is the index of the node。 And then we increment a send a sequence number as before。 Okay。

 so this time we've got messages that have a vector attached to them rather than a single integer。

When one of these messages gets delivered at a node， we， first of all。

 put a message in the buffer as usual。 and now we search for any messages that are ready to be delivered。

 And these are any messages whose causal dependencies have been satisfied。

 So any messages that were broadcast before the current message they have already been broadcast by they have already been delivered by the local node。

 if those have been delivered， then this message is ready to be delivered because it's causal dependencies have already been delivered。

 So here we search for any sender dependencies and message in the buffer such that the dependencies vector is less than or equal to the delivered vector。

 and this less than or equal operator is exactly the less than or equal operator that we defined on vector clocks a little while back。

 So even even though this algorithm is not exactly the same as the vector clocks algorithm。

 it's similar in the way that it does use these vectors of。



![](img/9d588e5642b5f59258924d0c1c1b3c75_35.png)

Numbers， and it uses this less than or equal comparison as a part of its algorithm for causal broadcast。



![](img/9d588e5642b5f59258924d0c1c1b3c75_37.png)

If we have a message that satisfies the dependencies， we deliver it。

 We remove the message from the buffer， and we increment the number of messages we have delivered from that particular sender。

 And this ensures causal broadcast。 You might have to think about the algorithm for a little bit to convince yourself that it really is correct。

 but I think it is correct。

![](img/9d588e5642b5f59258924d0c1c1b3c75_39.png)

So that is causal broadcast。😊，Finally， total order broadcast。



![](img/9d588e5642b5f59258924d0c1c1b3c75_41.png)

So total order broadcast is a bit harder。 So because remember。

 we have to somehow agree on what this total order is of of messages in which order the messages are going to get delivered。

Let's say one simple way of doing this。 We're going to pick one of the nodes as the leader。

 and this leader is going to be in charge of determining the order in which the messages get delivered。

 So that's why it's also sometimes known as a sequencer because it sequences the messages。

 And if one node wants to broadcast a message。 It doesn't directly broadcast it to the other nodes。

 Instead， the node sends it to the leader。

![](img/9d588e5642b5f59258924d0c1c1b3c75_43.png)

V a5I0 link probably， and the leader then broadcasted via 50 broadcast to the entire group。And so。

 because。All of the messages are going through the leader。

 simply the order in which the leader broadcasts the messages。

 then is the order in which all of the other nodes will deliver the messages since we're talking about Fi0 broadcast here。

And this works quite nicely。 It just has the problem that if our leader crashes。

 then no more messages can get delivered because we're requiring all of our messages to go through the leader。

 So really， we would need some kind of way of changing the leader from one node to another in case the leader crashes。

 But this is quite difficult to do safely， because， you know what。

 if you end up with two different leaders， then your' guarantee of total order is gone。

 So we will see ways of actually doing this kind of leader change safely in a later lecture when we'd come to talk about consensus。

 But for now， I'm just going to lead this as an open problem。



![](img/9d588e5642b5f59258924d0c1c1b3c75_45.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_46.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_47.png)

There's another way you could achieve total order broadcast， which does not rely on a leader。

 Instead， you could rely on lampport clocks。 So remember。

 Laport timests have an associated total order， and we can use that total order as the order in which we are going to deliver the messages。

 So we attach a lampport timestamp to every message。

 we create those lampport timestamps in the usual way like we have discussed。

 and then broadcast those messages via some kind of reliable broadcasts。

 and then each node needs to ensure that it delivers messages in increasing order of their lampport timestamps。



![](img/9d588e5642b5f59258924d0c1c1b3c75_49.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_50.png)

And this works， but it does rely on one particular piece of knowledge。

 which is a node needs to be sure at the time when a node delivers a message。



![](img/9d588e5642b5f59258924d0c1c1b3c75_52.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_53.png)

It needs to be sure that there will be no future messages with a lamp or timestamp less than this message that it's about to deliver。

Because if it did deliver the message now。 and then later a message with a lower time stampamp arrives。

 then it would have delivered them in the wrong order because it has to deliver them in the messages in strictly ascending order of Laor times stamp。

 So therefore， we need some way of knowing that there will not be any future messages with a times stamp less than some particular threshold。



![](img/9d588e5642b5f59258924d0c1c1b3c75_55.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_56.png)

And it is possible to know that because if we use FiO links between the nodes。

 then actually we know that each node will send messages in increasing order of Lalor timestamp and we receive those messages in increasing order。

 so therefore if we've heard from every other node。

 then we know that the minimum timestamp that we've seen across any of the other nodes is going to be the minimum we're ever going to see。

 so there will never be any later timestamps than this one。



![](img/9d588e5642b5f59258924d0c1c1b3c75_58.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_59.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_60.png)

![](img/9d588e5642b5f59258924d0c1c1b3c75_61.png)

And so based on that， it is now possible to again create total order broadcast again， unfortunately。

 this approach is not full tolerant because in this case， if just one of the nodes crashes。

 it will not be sending any more messages so the lamp or timestamps won't be moving forward anymore。

 and so node messages get delivered anymore。So these two algorithms do work。

 but neither of them is full tolerant， and later in a later lecture。

 we will see ways of achieving total order broadcast in a way that is full tolerant。



![](img/9d588e5642b5f59258924d0c1c1b3c75_63.png)