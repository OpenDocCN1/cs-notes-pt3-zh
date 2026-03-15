# 【全集 2025 附课件】马萨诸塞大学 分布式系统 中英字幕 p17 Lecture 17 - 分布式系统中的复制 -BV19BSYBuE4Y_p17-

Okay so let's get started today we will continue the discussion on replication and consistency that we started last time last time we had all these different consistency module consistency guarantees and so on and we ended with epidemic protocols and eventual consistency we are done with that part we will come back to replication and today we'll talk about how can we actually implement replication and will talk about remote right and local right protocols well talk about quorum based protocol there is a part three because I think I did add some slides to the lecture which are going to be on fault tolerance we will start talking about fault tolerance and failure recovery which is related to replication so。

Let's start with。

![](img/643a99be646d86f3e09a360eacaf79d1_1.png)

Repplication， so we already mentioned when we talked about consistency that usually。



![](img/643a99be646d86f3e09a360eacaf79d1_3.png)

distributedistributed systems， you have to replicate data or code and when you replicate data。

 you have to ensure that they are consistent but then the question the other correlated question is how is replication actually handled how do you ensure when a read request comes in which replica handles it and so on so we'll talk about forget about consistency for today's class we know how to do it we'll start talking about replication itself and we'll start with primary base is fairly straightforward and then we'll end with red right protocols where you do not have a primary so when the primary base there is a coordinator that's coordinating every data item all the replication is handled by the coordinator in the red right there is no coordinator a decentralized approach for replication so those are the two techniques that we will talk about today so let's start with a simple simple。



![](img/643a99be646d86f3e09a360eacaf79d1_5.png)

![](img/643a99be646d86f3e09a360eacaf79d1_6.png)

![](img/643a99be646d86f3e09a360eacaf79d1_7.png)

![](img/643a99be646d86f3e09a360eacaf79d1_8.png)

![](img/643a99be646d86f3e09a360eacaf79d1_9.png)

Technique here， which is a primary based protocol。 Okay， so here is a picture that you can see。

 there is a there are several discs that are shown here。 but from the per perspective of our。



![](img/643a99be646d86f3e09a360eacaf79d1_11.png)

For discussion。The one that says single server for item X is the one that is actually the coordinator for data item X okay so we are only talking about single data item at this point the data item may be replicated at multiple of those disks that are shown here but there is one coordinator that's actually handling so the question is how a reads and writes handled so without replication it should be clear how you will handle this when the client sends reads or write requests there is no replication the system initially theres only one copy that' is going to be at that server thatss the primary so all the reads and write are forwarded so you'll see that write comes in then it sent to the coordinator coordinator performs the right send but the result read comes in since the coordinator coordinator performs it sends this back okay so this is the simple no replication case but now let's assume that you have replication which means that there is a primary or a coordinator。



![](img/643a99be646d86f3e09a360eacaf79d1_13.png)

![](img/643a99be646d86f3e09a360eacaf79d1_14.png)

![](img/643a99be646d86f3e09a360eacaf79d1_15.png)

![](img/643a99be646d86f3e09a360eacaf79d1_16.png)

![](img/643a99be646d86f3e09a360eacaf79d1_17.png)

![](img/643a99be646d86f3e09a360eacaf79d1_18.png)

![](img/643a99be646d86f3e09a360eacaf79d1_19.png)

And there is a backup server which is storing an extra copy of the data item so now what is going to happen is every time there is a right it is going to come to the coordinator the coordinator has to forward the right to all the replicas so that all the replicas are consistent with one another right so that's what you will see here lots of arrows but what you will see is that when the client sends the right。



![](img/643a99be646d86f3e09a360eacaf79d1_21.png)

![](img/643a99be646d86f3e09a360eacaf79d1_22.png)

Here right that right W2 it goes to the primary， the primary is going to broadcast the right to all the copies。

So you will see W3， there are three arrows right so it went out to three of the。Other there it is。

 excuse me。And then you get back acknowledgements once you hear back from all the replicas you are going to return a result back to the prime so this is called primary base right so you will essentially have a coordinator right so I'm going to show you this is your coordinator let's say the coordinator right comes to the coordinator the coordinator is going to send it to all the three replicas which are shown here R1 or2 or3 and then you will wait for all the responses to come back right and then you send back the response to the client so so essentially you get the right at the coordator rate does the replication and then it sends back a response。

This is called a very simple remote right protocol。



![](img/643a99be646d86f3e09a360eacaf79d1_24.png)

Now question is， what do you do？

![](img/643a99be646d86f3e09a360eacaf79d1_26.png)

When there is a sorry excuse me we should also talk about reads in this case so when the client is not going to make a read it can go to any of the replicas because they have been kept consistent with one another so this client will simply send a read to its local replica get back a response so there's no other need to go to the coordinator so reads are going to be local the rightss are essentially send to all the replic。



![](img/643a99be646d86f3e09a360eacaf79d1_28.png)

对。Simple technique。 Okay， here is a。Technique where the primary or the coordinator for the data item keeps changing based on where the reads and write are happening。

 right？Excuse me。So， we still have that server that is shown as the master for item X and now suppose this client that is shown in this picture starts accessing data item X so in the previous case you have to send the rights to the primary。



![](img/643a99be646d86f3e09a360eacaf79d1_30.png)

But another optimization that you could perform is because this client is actually sending all of its request to its local machine。

 the local disk that's shown there that's a server。

 you can move the primary from the current primary to the local one so the primary or the coordinator changes so this becomes the coordinator and then that can start handling all of that request now if you are only performing reads that's easy or just going to go to the local data item but even if you're performing rights。

 you can just send it to a local replica which is then going to broadcast it all the others sorry local coordinator is going to broadcast it other and get back acknowledge so so in this case the coordinator for the data item will shift back and forth depending on which clients are accessing that data item when we talk about network file the distributed file system the network file system we are going to come back to this concept will see that the quote unqu server for a file。



![](img/643a99be646d86f3e09a360eacaf79d1_32.png)

![](img/643a99be646d86f3e09a360eacaf79d1_33.png)

![](img/643a99be646d86f3e09a360eacaf79d1_34.png)

Actually shift depending on where the reads and writes are happening。

 typicallyy the server doesn't change。 It one machine。

 but you can actually move the primary from one server to the other depending on what optimization you want to perform Okay but still still。



![](img/643a99be646d86f3e09a360eacaf79d1_36.png)

![](img/643a99be646d86f3e09a360eacaf79d1_37.png)

Fairly straightforward， this is local right， so here is essentially what is going on。

With all of these arrows， So you will see now the client send the right to its local machine。

 that's W1。 You will see that。The primary old primary is now moved to that other machine that now become the new primary and then all further rights are going to be broadcast so you will see that W4 is a subsequent right that' is actually broadcast to all of the machines so you move the primary but is still doing the task of the old primary by broadcasting all the rights to other machines。

Yes， for question。当时他证。不是。It on the first。好的。Yes， so the question yes。

 that's a good question question is how do you decide when to move the primary to that server so so as you can see W1 actually arrived to the local machine local machine will actually send。

Message here and that will just transfer the so why W2 is actually coming back that will transfer the responsibility to the local to the new machine new machine will perform the right and then you will either reply to the client or send back knowledge right so so yes you have to communicate with the current primary in NFS as we will see in a couples lectures you will ask the server saying can I become the new primary the server may say yes or no if it' is no then you are back to the remote protocol where all the rights go to one server if it says yes then the server becomes the new primary。



![](img/643a99be646d86f3e09a360eacaf79d1_39.png)

![](img/643a99be646d86f3e09a360eacaf79d1_40.png)

成个呢度。Okay question is is this going to happen for single rights or multiple rights？

If there' is only one client accessing a data item you can move the primary to the local machine that where the rights are happening and that is going to be more efficient because the rights are hitting the local machine and that's faster。

 but if there are two clients let's say there are two clients in this example if both of these clients are performing rights。



![](img/643a99be646d86f3e09a360eacaf79d1_42.png)

You cannot have two primaries you still need one primary so either you keep the remote machine the primary you don't move it at all or one of these clients takes over the responsibility that the primary and the other one is still getting remote text right so when there are concurrent rights from multiple clients then you may not choose to move the primary at all it is better to keep the server that was already the primary as the current primary but this optimization will only work if there is one client writing others may read reads are fine but there should be only one writer when multiple writers you are not going to move things back in。



![](img/643a99be646d86f3e09a360eacaf79d1_44.png)

![](img/643a99be646d86f3e09a360eacaf79d1_45.png)

Okay all right so that's local rights， but now let's talk a little bit about replicated right protocols because we want to now say this notion of a primary is not something we want maybe the primary fails or something like that and that's not resilient so what can we do in this case by having no primary at all so you have set of replicas replicas can make updates and you still want to ensure consistency so there are two ways we are going to do replicated right protocols one is called synchronous the other is called asynchronous so its important to understand the difference between synchronous rights and asynchronous rights when your replication so first thing is you should know what synchronous and asynchronous mean synchronous as I have said multiple times you can whenever I say synchronous you should think blocking whenever I say asynchronous you should think nonblocking。



![](img/643a99be646d86f3e09a360eacaf79d1_47.png)

![](img/643a99be646d86f3e09a360eacaf79d1_48.png)

![](img/643a99be646d86f3e09a360eacaf79d1_49.png)

![](img/643a99be646d86f3e09a360eacaf79d1_50.png)

So when you do synchronous rights that essentially means a blocking right which means all the replicas have to have seen the right and responded before the right returns back to the client that is called synchronous right so if you have a client。

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_52.png)

![](img/643a99be646d86f3e09a360eacaf79d1_53.png)

My favor client C， and then there is a。This is your primary okay so in synchronous right the right comes here the primary has to send it to all the replicas say R1 r2 r3 okay and then have responses come back which say that acknowledgements come back and you the client is going to be blocked until that client will not get a return from the right and once the acknowledge comes back you will essentially the right will return saying it has completed。

So， in some sense， replicated rights sorry not replicated synchronous rights。😊。

Guarantee that all the replicas have been updated before the client is told the right has completed。

Okay so so that is good for consistency because you will when the client says the right is done you are guaranteed that every replica has been updated and has the most recent update of the data item but it is also from a performance standpoint is quite slow because a the client is blocked until all of these rights are broadcast and moreover the right proceeds at the speed of the slowest replica if one of these R1 r to r3 where a distant machine the time to send the right over a network will be much longer than the other replica so you are going to be the right throughput is going to be based on the slowest replica in the system。



![](img/643a99be646d86f3e09a360eacaf79d1_55.png)

![](img/643a99be646d86f3e09a360eacaf79d1_56.png)

![](img/643a99be646d86f3e09a360eacaf79d1_57.png)

That' is basically a fact of how these synchronous rights work， they are good for consistency。

 but they are not great from a performance standpoint。

 especially if some replicas are further away from other replic。😊，なイ。

In this replicated right protocol is the lead function from a different plan also go up。

Question is in a replicated right protocol is the read from a different client block that's your question right。



![](img/643a99be646d86f3e09a360eacaf79d1_59.png)

Unless there are additional locks at the application level from a file system level reads and writes are concurrent so if there is a write in progress some other client comes and reads it you will read the file the file system is not enforcing any higher level application semantics now if that is a shared file from an application standpoint maybe you should have put a lock when you did this but from our perspective we are just performing a reads and write we don't worry about as application of a lock or not so thats up to the application semantics of what it is trying to achieve so assume that if there's a read it will come and basically read the data item while the right is problem。



![](img/643a99be646d86f3e09a360eacaf79d1_61.png)

![](img/643a99be646d86f3e09a360eacaf79d1_62.png)

![](img/643a99be646d86f3e09a360eacaf79d1_63.png)

Because that's a file system，Asynchronous right okay so in asynchronous rights as I said is is non blocking right so the client will send the right request to the primary okay the primary can immediately say。



![](img/643a99be646d86f3e09a360eacaf79d1_65.png)

![](img/643a99be646d86f3e09a360eacaf79d1_66.png)

I received the right and the client can proceed and all of what Ive shown here can happen in the background and the client can have progressed and move ahead of this right so it's nonblocking so from a performance standpoint it's very good because the client has not blocked if there are remote replicas。

 all these messages don't have to be dealt with before the client can continue so from a performance standpoint it's very good from a consistency standpoint is not great because what can happen is the client will say okay update this file you immediately get back a reply because you are just sending a write request is like sending a print or a read request so you send a read request read request return。

 you as a developer assume that when the read returns。

 then the file has been updated that's what your assumption but clearly it does not been updated in a replicated scenario because all of these additional messages are going to go later client has already assume that the right is complete。



![](img/643a99be646d86f3e09a360eacaf79d1_68.png)

![](img/643a99be646d86f3e09a360eacaf79d1_69.png)

![](img/643a99be646d86f3e09a360eacaf79d1_70.png)

![](img/643a99be646d86f3e09a360eacaf79d1_71.png)

![](img/643a99be646d86f3e09a360eacaf79d1_72.png)

![](img/643a99be646d86f3e09a360eacaf79d1_73.png)

![](img/643a99be646d86f3e09a360eacaf79d1_74.png)

But in the system it is still in progress now if there is a crash lets say the primary crashes before it could send all of the replicas these messages and then you reboot the machines you will see that the right is actually not finished but the client assumes it has finished because the client got a reply saying the right was successful。

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_76.png)

![](img/643a99be646d86f3e09a360eacaf79d1_77.png)

So consistency is not going to be guaranteed in an asynchronous right protocol。

 but performance will be better。😊。

![](img/643a99be646d86f3e09a360eacaf79d1_79.png)

哎。Is that clear？So which one you pick actually depends on the scenario if you have critical systems where you cannot actually compromise consistency。

 let's say it is bank database or financial databases you will do you will do synchronous rights。

because you want to make sure that there is no problem from a consistency standpoint so you will pay that extra price performance might suffer but if you want high performance you are not as worried about consistency you can switch to as synchronous but by and large anything that you see that is more critical like bank databases or or anything like that they stick to synchronous right and because they don't want to take a performance hit these replicas cannot be really far away from another there is a performance will really suffer so you will see like banks will put a second replica maybe five miles or 10 miles away because that's the latency you can if you put them 100 miles away that latency starts showing up and all the performance of your applications that are working on on this file system or database will start suffering。

So not so in asynchronous rightss， you can have the replicas as far away as you want。

 but consistency is not going to answer those questions and therelarious。

Okay question is what happens if a replica blocks in the synchronous right That's your question right yeah so if the replica blockss in a synchronous right the primary kick because it is waiting for responses from the replicas it could simply send a message to the client saying the right failed because remember you're just reading a writing you can always get an error message saying the right didn't succeed for some reason which happens even in normal file system maybe the disc is full so if you try to write a full disk you will get an error and then the application is to deal with it so so you could certainly send back a response saying the right fail and then the replicas it can be told not to can undo the right or something like that so you can add some logic to deal with failed rights in the system。



![](img/643a99be646d86f3e09a360eacaf79d1_81.png)

![](img/643a99be646d86f3e09a360eacaf79d1_82.png)

![](img/643a99be646d86f3e09a360eacaf79d1_83.png)

![](img/643a99be646d86f3e09a360eacaf79d1_84.png)

Allright so this is replicated right so I have the more complicated sequence diagram that shows that simple picture I showed you already this is synchronous you will see that the client sent a message write message to the leader the coordinator。

 the coordinator is sending that right to all the three replicas which are called follower all of them have to send an acknowledgement saying the right was successful okay ones that。



![](img/643a99be646d86f3e09a360eacaf79d1_86.png)

Acknowledgement comes you will send back a response to the client Okay so from the sending of the request to this the client has blocked it took all of that time for the right to complete So its from a client's perspective a slow right。



![](img/643a99be646d86f3e09a360eacaf79d1_88.png)

but it is consistent and here is essentially what happens in case of asynchronous so you will see。

That the client send a request to the leader， the leader has sent this right request to three followers。

这不。So at any point once those requests have been sent the leader can respond to the client saying right as finished in this case we are waiting for at least two of the copies to have said okay before you are sending back a response not the third one but you don't need to even wait that long you could have sent it right after the right was received or right after the right was sent to all of the client depending on what type of asynchronous replication is being implemented you will get an acknowledgement well before the entire operation has finished。

This will from a client's perspective it is faster but it is not going to give you consistency if there are crashes if there are no crashes everything is good you will still complete the right in the bag。

That clear。Yes， question。Thank。完了。So的。Okay question is what happens if the replication fails for one of the replica that is going to depend on the storage system or the file system clearly for consistency reason if the replication fails or let's say replica3 you have to retry and make sure that eventually it gets all the rights that have not reached it but that's an additional failure recovery logic that you implement this technique is simply saying from a client's perspective when do you get okay saying your right finished so all it's saying is you don't wait for the all the replicas to have finished the right but then orthogonal question is and the same is true for synchronous what happens when there are failures how do you deal with them so when the failed machine comes back it has to be reynchronized with the rest so that the states are again synchronized otherwise you will have some rights that are never reached that replica。

All right。

![](img/643a99be646d86f3e09a360eacaf79d1_90.png)

So that synchronous replication。But now we will actually talk about a different set of protocols which is no primary yes we will have no coordinator this is leader less replication so。

So any replica can be allowed to update and consistency here will be a little more complicated。

Excuse me。So this is called this class of techniques are called quorum based protocol because we will see that you need a quorum of replicas to agree。

 not every replica but you need a quorum because you are not going to wait for every replica to answer you can pick some subset of the replicas you can perform the right on that subset and so long as that subset agree we will say that the right has been successful and because now the rights are going to a subset of the replicas the read still have to be consistent you do not want your read to actually read from a machine that was not part of the most recent right subset and return some old data so how do you design a technique where the rights are not going to all of the machines until now you said rights are going to all of the machines now we will relax that assumption there is no leader we will send the right to only a subset。



![](img/643a99be646d86f3e09a360eacaf79d1_92.png)

![](img/643a99be646d86f3e09a360eacaf79d1_93.png)

![](img/643a99be646d86f3e09a360eacaf79d1_94.png)

And we will still guarantee that the read can never return outdated results。

How are we going to do this We are going to essentially use quorum and we are going to use voting so the you will ask some subset。

 well send the rights to some subset， we'll send the reach to some subset and well always assume that you vote on the results and the results match then we will say that that's the right results to return to the client so we need to now design a technique where you no longer send the rights to all of the machines in the system will send them to a subset any arbitrary subset based on some rules that we will decide but any arbitrary subset that the client chooses and yet we will ensure that you will never get old results so this will be called quorum based techniques there's a whole class of protocols but we see a simple one that's called Gford quorum based protocol and we will essentially use the following rules we have to essentially pick two quorums quos basically mean these are the number of machines you need to perform an operation so we have a right quorum。



![](img/643a99be646d86f3e09a360eacaf79d1_96.png)

![](img/643a99be646d86f3e09a360eacaf79d1_97.png)

![](img/643a99be646d86f3e09a360eacaf79d1_98.png)

![](img/643a99be646d86f3e09a360eacaf79d1_99.png)

So right quo is a number that says the right operation has to be performed on those many machines from the overall set and well have a read quo which says any read request has to be sent to all of those machines and the results that come from those machines how to match for the read to be successful that is called the read quo so you have to pick is assuming there are n servers you have to pick a number that represents the right quo you have to pick a number that represents the read quo and here are the rules of how we are going to do this here the sum of the read and the right quo has to be greater than n。



![](img/643a99be646d86f3e09a360eacaf79d1_101.png)

![](img/643a99be646d86f3e09a360eacaf79d1_102.png)

You have n is let us say10 okay you can say right quo is 7 that means you perform the rights on  seven out of 10 machines and then the red quo has to be at least  four okay so that 4 plus 7 has to be greater than 10 the right quo has to be always strict majority。

You cannot pick a right quorum that's smaller than half the machines in the system， that's our root。

 so， these are our two rules and implicit in these two rules is also that the right quo is always bigger than the read quo。

Yeah because we always you say n r plus nw is greater than n and is strictly greater than half of course you could up read quo other ways but we will assume that the right quo is always bigger than the read quo so I will show you some examples okay but lets just understand how the protocol will work first you are going to pick this read and write quo and then when you want to make a right you are simply going to contact any arbitrary NW servers out of n。

Pick that chosen at random and you are going to perform the rights on those machines。

When you want to perform a read you are going to pick Nr servers at random from N and you are going to do a read on the data item and then you are going to check did they all return the same result maybe youre reading a file you compare the file they all return the same file if there is any mismatch you are to repeat because you read failed but if all of them match if all NR servers return a result that match then you can you are guaranteed that that is the most recent right you can never get a read quo where the machines agree and you are getting an old result that is going to be guaranteed by the protocol will see why。



![](img/643a99be646d86f3e09a360eacaf79d1_104.png)

![](img/643a99be646d86f3e09a360eacaf79d1_105.png)

![](img/643a99be646d86f3e09a360eacaf79d1_106.png)

Is that clear what I said？So here are some examples that help us understand this， right？



![](img/643a99be646d86f3e09a360eacaf79d1_108.png)

12 machines a through L。

![](img/643a99be646d86f3e09a360eacaf79d1_110.png)

three different examples of choosing read and write Co。

In the first example we pick the right quorum to be 10 that means that any time a client wants to make a right it has to pick any1 out of those 12 servers doesn't matter which 10 10 servers at random perform the rights on those servers and the servers have to say the right was successful there is no rep no other communication you just send the right to 10 servers 10 servers reply saying right is done client is done with the right。



![](img/643a99be646d86f3e09a360eacaf79d1_112.png)

哎。Is that clear what I said rear Q is 3 that means that a client can pick any three servers out of this 12 at random。

😊，And if those three servers and say you read a file and if those files match are guaranteed that that is the most recent right if the files don't match or repeat you pick another three servers at random。

 you do this until you file three servers that say yes， this is the file they all agree。



![](img/643a99be646d86f3e09a360eacaf79d1_114.png)

And you are guaranteed now that you will get the most recent so lets take this example and try to understand why is it that the real quorum can never give you bad results。



![](img/643a99be646d86f3e09a360eacaf79d1_116.png)

![](img/643a99be646d86f3e09a360eacaf79d1_117.png)

And so here is an example so so lets say the right quorum is see that the dotted circle there C D E F GH I JKL so you left out A and B from the right you pick all the other 10 servers and you perform a right。

Okay now when another client comes in， it wants to read the file， it has to pick three servers。

 okay it picks A， B and C。😊，so now you get three files from one from a one from B and one from C and it is clear that A and B have not seen the right based on what we just showed you because the most recent right went from C through L right so these three servers are not going to agree because C has seen the right。

Its version of the file will be different from A and B。That clear。

Right because the right right from c through l so you pick three servers and you pick ABC A and B will have an old version。

 C will have the new version so this right will actually not succeed because the three servers will not agree。

So you repeat and if you now pick three servers that are a subset of the right quorum then you will succeed by definition because all three servers will return the same version of the file they all saw the most recent right but so long as you keep picking one that is outside that quorum you will keep failing so you keep trying keep retrying until you pick those three servers that agree and then youre guarantee youve got the most recent so what this is telling you is that the protocol is designed in a way where if you hit a server that did not see the most recent update by definition it is guaranteed to disagree because you pick the red quorum such that you will never actually pick three servers that did not find the right because this is why NR plus NW has to be greater than n。



![](img/643a99be646d86f3e09a360eacaf79d1_119.png)

![](img/643a99be646d86f3e09a360eacaf79d1_120.png)

And you will see that in another example where what happens if you actually don't choose it。

There is this clear any questions on this？Yes， question。第个。Yes。

 question is what happens there is another right good question。

 so maybe you have another right coming in and now you pick a through J and you leave out K and L。😊。

so now the file gets updated there is a new version of the file a through J have seen it K and L have the older version okay now another read comes in you have to pick three servers that agree if you pick JkL they will not agree because K and L did not see that right but J did see it but if you picked ABC like in this example they will automatically agree because that right did it A B and C。

哎。Yeah the question is is missing one of the older rights is that okay so that depends on how the right is being performed so if the write is the entire file is being replaced every time then it's okay right if you're saying I'm going to append a character to the file A and B didn't see the previous right and now you append another character that's not right so the rights actually have to be performed in a way where the entire data item is always update so if these are let's say integers that you're updating in a database of course it's fine right because you didn't see the previous update but now you updated a record its okay but if you' are actually doing reads and write to a file then the right has to actually replace the entire file with the new file you can't just modify parts of the file so long as you do that it will be fine there was a question somewhere。

对。I can to take a PCN picture the same。Okay， question is， why cannot we use a times time to do this。

 That's your question， right， Okay， so you could use times timess to figure out C as a newer version than A and B。

 but now that has introduced an additional。Criiteria saying the machines have to be synchronized and the times timess have to be accurate right so so if and we have the same problem clock synchronization is never fully accurate I say np has 50 milliseconds error right so if there are two rights within 50 milliseconds and ABc some one of them andcc is the other one you cannot actually tell which is the most recent so so you can use clock synchronization here but you will always have the problem of what we had said clock synchronization is never absolute is always an error and two events that are within the error at all and you can't say which is the newer push。

That particular MP has in your rights。How do we make sure。One of I。

Yeah so question if you don't have timets what are we actually doing so you can add version numbers to files version numbers are simple integers every time you update the file you increment the version number and you write it that's one example so that you can get away that's like logical clock right you have an integer version numbers are the same as the Laer clock at some level so you could do other things to to make sure that you have the most recent right figured out without comparing timests。

Yes。啊。This opportunity get up。Yeah question is can we use this approach if you are appending content you are simply doing append and append only write the new part of the file this approach will not work because A and B for the previous right didn't see that right and then maybe another right came and A and B are part of it or you basically are now appending some content where you miss the previous append so that will not work right still work file for databases where you are updating records or updating integers for files the only way you are going to do this is each right has to replace that entire file with the new contents of the file then you are okay。

え？イス。For的那个。Okay how does the coordinator keep track of NW there is no coordinator this is leaderless but the client all the reads and write are being done by clients the clients are told what the choice of NW and NRS and the rule is when you are performing a read you are to pick any 10 of those servers and perform the rights when you are performing a read you pick any three servers you perform the read if they agree or done if they don't agree you repeat。

question is are the 10 right and synchronous yes they have to be performed synchronous you have to send that right to all of those c through L in this case wait for the response then the right system。

Okay。好的。嗯。Whereas this protocol used quorum based protocol there we will actually look at we aren't gotten to consensus yet but when we start talking about things like consensus and agreement we will see that these kinds of techniques are actually quite popular but yeah you can use it in any replicated replication technique but more to the point these days they are used when you want to essentially get replicas to agree you don't want a coordinator because coordinator can fail there are all kinds of reason。

Yes， question。Since one of these use N and。Select the random。H。

Because if we keep selecting the same thing。经理有。はも。

The question is is there a performance disadvantage unlike the leader based protocol there is a disadvantage which is that reads can take multiple attempts to succeed okay that is the price you pay for not having a accordingly it。

If youre had a coordinator coordinator is handling all of that for you。

 your reads will take longer rides may not。Oa will see a technique where reads might not take longer at all but we will get to that so let' us take the second example here where we picked still 12 servers right so we picked the read quo to be 7 the right quorum to be6。

So the dotted lines are the right quorum so DhL IjK is the right the most recent right you pick those six servers you perform the right now you go to performformer read so you will pick seven servers。

Okay， and you will see the first seven。Like your pet， are they going to agree。は。😮。

So they will not agree because。HS see the more recent right than the others， so they will fail right？

And you can。Retry， but it will still keep failing。 because there is no way to pick seven servers where they will all agree because a you will always pick one of the right quorum and no matter how at least one maybe be more and you will pick some of the other ones。

And they will always disagree。so the right in this case never succeeds。What's the problem here？Yes。

The first problem is we picked Nw to be 6 is not a strict majority。

Have we said it has to be strict majority okay second problem is you pick the read quo as was pointed out to be bigger than the right quo。

The read quo is bigger than the right quo， there is no way to pick。S worse， they all agree。

Because you will pick six plus at least one that will disagree by definition。

 which is why we need to follow these rules here。

![](img/643a99be646d86f3e09a360eacaf79d1_122.png)

the sum ofs to be greater than n。NWS to a strict majority in the real quorum。

Has to be smaller than the right group。

![](img/643a99be646d86f3e09a360eacaf79d1_124.png)

It's the only way you will succeed。Exact here。 Y， All right。 So last case is the。



![](img/643a99be646d86f3e09a360eacaf79d1_126.png)

Third example。The right quorum is the entire set always。Okay。

 so all the rights go to all the replicas。The read quorum is one。

You do never have to ask more than one server if all the servers have always seen the right。

so right here will be broadcast to all the machines， the reads are going to be local。Right。

This one is called。Read one writes， write all， because you will always write all okay and you will only read one。

 So this makes it。More efficient to not retry reads， rights are expensive。

 they have to go to all the servers。Because reads are cheap。

 you never actually have to check with any server because you know。That every server got the right。

Is that clear。Yes。Book。Okay， question is what happens if NW is 11？

N R is equal to one okay and you go to the server that didn read that not work will return bad results and the reason it returns bad result is。



![](img/643a99be646d86f3e09a360eacaf79d1_128.png)

We did not agree with that rule N R and plus nw has to be greater than n if it iss 11 and1 it is actually equal not that is why if you pick them incorrectly you will get bad results but then you are getting wrong results you got to go and say did I follow the rules if you follow these rules that should never happen by definition。



![](img/643a99be646d86f3e09a360eacaf79d1_130.png)

哎。But that's a good point， any other questions？

![](img/643a99be646d86f3e09a360eacaf79d1_132.png)

Yes。没没关。就是在那个。Be coordinated and appointment be broadcast。

The question is if you are doing multiple rights is that a vary coordinator so so the way you want to think about this is a client is doing all the right there is no coordinator the client knows all 12 machines think about let's say you write the Python code right so you are doing some right to a file your Python library actually has to send in this case 10 rights to 10 different servers。

It can pick those1 servers anyway at once， so it is going to send those 10 rights is going to wait for the response when all the10 rights return it tell the client the right is done。

The read is the same way you will try to read that file okay you will go and pick three servers at random read the file you will compare either the version number or the contents if the match the library will say here is the right if it doesn't match then you will read so there is no server that is acting as the coordinator the client through a library is doing all of this right okay from a user perspective you are still doing reads and write internally it might translate to multiple reads and write but but that is not an issue from a developer is not writing 10 rights in the code but you only write once and then the library is going do this。

I this clear。Okay， yes。是。好。You are saying if the rights are concurrent， should you write also。

 is that your question？Yeah。The question is if the rights are concurrent should we write to all the server some subset of it？



![](img/643a99be646d86f3e09a360eacaf79d1_134.png)

So when there are concurrent rights， you still need a way to order the right and make sure that rights at least get increasing and unique sequence numbers so let us say current version of the file is 10。



![](img/643a99be646d86f3e09a360eacaf79d1_136.png)

The if two clients read this file and says version 10 and each of them says now I' am going to write a new version called version 11 and then you are reoverwriting each other so that's bad you don't want that to happen so long as you have a way to deal with this maybe through locks or other higher level mechanism you can have concurrent rights but you need to make sure internally in the system they are ordered in some way you don't want to write to overwrite content like the example I just give。



![](img/643a99be646d86f3e09a360eacaf79d1_138.png)

![](img/643a99be646d86f3e09a360eacaf79d1_139.png)

还。Okay yes if the client from a client's perspective the request the rights are concurrent right so the client picked 10 servers in the right quorum and its written so the library sent 10 rights and concurrently and is waiting for the response same as what happened in the applicator yes those will be you are not sequentially writing to C and then D and all that will just take a very long time you just send 10 of these requests in parallel to 10 machines。

当。Okay question is in that case is right all expensive that depends on what cost you want to pay because you will have more rights going out but the reads are simplified right so this goes back to you have to look at your workload if the workload is read intensive rights are infrequent then it is better to actually go with that approach because you will write all 12 servers but your reads are very cheap you only read from one server but then if the opposite way true if it was。



![](img/643a99be646d86f3e09a360eacaf79d1_141.png)

Very read intensive sorry very right intensive then you may not want to pay that price you might want to pick smaller write quorums so you have cheaper rights。

 but then reads might have to retry， but they are not that frequent so you can pay that so that's going to depend So how you choose N R and NW is left the application developer right so long as you follow that rules there are many ways for this 12 to have picked so you could have picked NW is8 N R could before there could be many ways you pick this right so how you pick it is based on what you expect your read and write frequency to be。



![](img/643a99be646d86f3e09a360eacaf79d1_143.png)

That clear。ok。Allright so that's Gifford's quorum based protocol the first time we actually came to a protocol that involved voting an agreement right so we are actually voting on ABC in this case in that first example are voting on is the read going to succeed are these the same file version numbers and things like that we are going to come back to this and we talk about failure recovery and and consensus and things of that sort so theres a lot of this kind of voting based techniques that we are going to see this was the first time we encountered it but we will see it many more times。

Okay so I'm going to skip this because you already saw what happens but just to be clear in this case if you're doing the read the read has gone to maybe some not all the machines are shown here of course only three are shown that was a read quo you will ask them theyll all return the version numbers and you'll see the version number doesn't match which was the first example I showed you then you are going to essentially not look at it right so and then you are going to try to figure out what what you want and so yes。

Yes， in this case。You're right it is not coordinator so this is really the library of the client it iss not really a coordinator but the client library is dealing with right but that's a good point。



![](img/643a99be646d86f3e09a360eacaf79d1_145.png)

All right， so I'll skip this， but we will talk about replica management and then talk about failure recovery and other techniques up。



![](img/643a99be646d86f3e09a360eacaf79d1_147.png)

But we looked at remote right protocols， we looked at local right protocols。

 we looked at leaderless right protocols which are quorum based all of these。

Try to figure out how do you perform reads and write but replication involves many other things that you got to worry about not just consistency and how are you going to perform reads and writes are the synchronous asynchronous leader based leader less those are all good things to think about but there are other things you want to figure out how many replicas to have in the system that example I just showed you had 12 replicas。

for quorum basedtro Y to2 right why should it be5 should it be 10 should it be2 so somebody has to figure out what is the right number of replicas to have for any application just as when you had thread pools you decide how many threads to have threads gave you some notion of concurrency in replication you are to also figure out how much replicas to have because they are going to give us other techniques like scaling up or the ability to do to failure recovery and so on that's one thing the number of replicas the second is to do the replicas be at the same location or should they be distributed。



![](img/643a99be646d86f3e09a360eacaf79d1_149.png)

that also has some implications on what the cost of reads and writes could be right you could put all the replicas as machines in the same data center the same cloud or same location in this case communication between replicas is fairly cheap because they are actually in the same location but if that entire data center goes down。



![](img/643a99be646d86f3e09a360eacaf79d1_151.png)

![](img/643a99be646d86f3e09a360eacaf79d1_152.png)

You cant actually de do anything because you put the replicas right so the but they are at the same location so you can deal with server failures when you have replicas at the same location but you cannot deal with data center failure maybe the power went out。

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_154.png)

![](img/643a99be646d86f3e09a360eacaf79d1_155.png)

The entire data center all the machines are down so the fact that your applicationplication didnt really help you in this case right but if you put the replicas in different locations。

😊，So now if one data center goes down some other replicas are still up。

So you can still go and get your data。But consistency becomes harder so this goes back to if you're doing synchronous rights your rights are now going to all kinds of locations right but that is actually going to increase latency for rights and so on and if you are doing quorum based reads your reads are also going to all kinds of locations you are actually getting the results voting and so on so you can do geographic repplication where you put the replicas in different places but that will actually come at a cost of consistency maintenance and reads and rights and so on when we talk about the web we will actually look at this problem we will see how do you put these replicas in different locations how do what happens if you put them in the same location how many two replicas to put should the number of replicas be varied dynamically。

😊，But just as in your thread pool dynamic thread pools the number of threads is changing based on load you can do the same thing for replication when the load is high you can create more replicas so that the load gets spread across all the replicas each replica is handling a fraction of the load and when the load goes down you can reduce the number of replicas so the size of the replica pool can also vary based on。

How much the demand you are seeing so you can do on demand replication and so on so there are all kinds of other techniques that we got to worry about in addition to consistency and reading and writing in a consistent manner which we are looked at but these things we are going to differ we are not going to talk about it necessarily now a lot of this will come back to and look at it from the context of the web。

Or the cloud so that is where I think it is better to see the techniques in the context of a specific application rather than thinking about it more generally。

Right， but。

![](img/643a99be646d86f3e09a360eacaf79d1_157.png)

As far as replication is concerned， that's all we are going to talk about now。

 but we will revisit this when we talk about the web。Instead， what I'll do for the rest of the class。



![](img/643a99be646d86f3e09a360eacaf79d1_159.png)

か。Is to talk about another facet of replication， which is fault tolerance。

What do you do when some of the machines go down？How are we going to deal with this in our distributed system and we have replica so we know some of the machines stay up so you can deal with that。

🤧。But first， I think what you should realize is if youre single machine systems。

No fault all and no ability to deal with fault machine goes down， applications is down。

That we talked about in our very first class， but now you have distributed system multiple nodes in the system okay so partial failures are possible where some subset of the nodes go down can the system continue to run。

Right just we just talked about the quorum based protocol we had 12 machines what if two failed can the system continue to run perhaps right you can if you pick the read and write quorum the proper way it should continue to run without any problem。



![](img/643a99be646d86f3e09a360eacaf79d1_161.png)

So there are many other techniques where we can think about locking or all these other things we talked about。



![](img/643a99be646d86f3e09a360eacaf79d1_163.png)

Where we need to see how to handle these failures what do we do right how do we automatically recover from them。

LetYeah。Now， the reason this is important is that when you have larger distributed systems。

 the probability of a failure keeps going up。

![](img/643a99be646d86f3e09a360eacaf79d1_165.png)

Okay， and。

![](img/643a99be646d86f3e09a360eacaf79d1_167.png)

And this is a simple equation， but it is something you ought to keep in mind。

 which is if you have n components in your system n machines in the system。

 the probability of a failure is the probability that any one machine fails。



![](img/643a99be646d86f3e09a360eacaf79d1_169.png)

![](img/643a99be646d86f3e09a360eacaf79d1_170.png)

， that is what a probability of failure when one or more machines fail is a probability of a failure and that is basically one minus probability of no failure。

😊，And as and you will see that as n goes up that number is actually going to trend to 1 and the reason is let us say p is the probability of a machine staying up okay so。

Probability of a failure is 1 minus p to the power n so is1 minus p to the power n so p means no failure so the p to the power n is none of the machines have failed one minus p to the power n is some machine as weight。

now， as n goes to infinity， which means that the system size is becoming larger and larger。

 what does this term become？iss going to trend to1 because P to the power n P is strictly less than one right theres some probability thatll stay up is not one。

 there's always a chance of failure So this is this is a number small as a fraction right fraction to the power n as m grosss that term will always go to zero so this term is going to go to one what does this tell you in any large scale system failure is actually a common case。

 not an uncommon case if you have one machine right you don't expect your laptop to be have to be a failed as the common case the common case is that you will essentially expect a machine to work and maybe something goes wrong once in a while it might fail but you may have a system with hundred machines chances of one machine failing is now actually not insignificant your 10000 machines the probability that some machines have failed is almost guaranteed at any time some fraction of the machine would have failed for any arbitrary reason you independent just because of that term if。



![](img/643a99be646d86f3e09a360eacaf79d1_172.png)

![](img/643a99be646d86f3e09a360eacaf79d1_173.png)

If those are independent failure as n grows a large number that that will train to one so what does this tell you for any large scale distributed system if you don't build failure recovery as part of your application application will fundamentally not work because half not shouldn half but some fraction of the machines would have gone down by definition and then if you havent dealt with that by designing these into your system then your application will not work。



![](img/643a99be646d86f3e09a360eacaf79d1_175.png)

![](img/643a99be646d86f3e09a360eacaf79d1_176.png)

So the larger the system more common will be the case a scenario where some machines are down for any reason this failed maybe the machine overheated and died or maybe the OS crashed anything could solve a problem hardware problem。

 anything can happen and a probability that something will go wrong just keeps going。

So fault tolerance for large system actually has to be built in it is not an option where you say let us assume thats a rare case and we don't worry about it。

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_178.png)

So you are to actually think about this more carefully。

Now think about with that what I just said think about how we are actually used to operating machines and systems right so almost every OS okay when it comes out it has bugs in it okay things software is never bug free especially large software is always bugs this is how software design works and。

There's some assumption that we always make that every once in a while that some bug might get triggered and the software might hang or something like that and if you're you know a Xi person you say okay I'll just reboot this machine or something like that and maybe things will come back to normal and you just move on but that's not how people actually are used to dealing with any system they they work with so let's now assume that distributed systems are become pervasive so almost anything you buy actually has piece of software and a computing device built it so let's say TVs are not smart TV that it is basically a computing device so if you tell somebody saying every three days your TV will hang you got to restart it they are not gonna to be happy let's now take a even more extreme case let's say all cars are also computing devices because they all have sensors in them they all do compute they can。



![](img/643a99be646d86f3e09a360eacaf79d1_180.png)

![](img/643a99be646d86f3e09a360eacaf79d1_181.png)

about all kinds of things like crash detection and automatic braking etca。

 so they run a lot of software if you tell somebody saying every four days you got to reboot your car that's not a thing that they understand what that even means or why you are to do that right so what we are used to in terms of laptops and PCs don't translate to the real world because that's not how people deal with。

Deices that are actually inherently unreliable because they are buggy right so so you don't want to build your systems in a way that requires the users to take these types of action you want higher levels of reliability in your system so you are not going to worry about how are you going to make your car or TV better but we will think about how are you going to make your distributed system better because that can be worse if your bank goes down you are not happy because you can't access your money right you go to the ATM and it says okay machine is rebooting come back after one hour thats not a thing that you really want to hear so you want your systems that we build to be very reliable so that's really the reason we want to think about fault or a distributed system。

Is that clear。

![](img/643a99be646d86f3e09a360eacaf79d1_183.png)

Allect， so I's explain some more concepts and then we'll talk about some very simple techniques today we'll come back next time and talk about more sophisticated fault tolerance and taking but first thing is some terms that you need to understand and we'll talk about availability。

 reliability and safety and well also talk about maintain all of which seem like good things to have because maybe I won't define them but but they all look like good properties so let's see what they mean availability means that the system should be available for use at any given time so it just if I go to a system is it up or down what's the percentage or probability that it's up at any given time and I try to access system is always expressed as a percentage。



![](img/643a99be646d86f3e09a360eacaf79d1_185.png)

![](img/643a99be646d86f3e09a360eacaf79d1_186.png)

Right。So typically you want a system to have high ava never going to be 100% because there is always some chance the system will fit okay but the closer end the availability is 200% the more available your system is because the chances it are down are much smaller okay so usually。



![](img/643a99be646d86f3e09a360eacaf79d1_188.png)

Distributed systems that have high degree of fault tolerance built in will have high availability and this is usually expressed in what is called some number of nine of reliability so here is a number it is a 99。

999% reliable that is is called five nine of availability that if a system gives you that guarantee that means that the maximum downtime it can have is 6 minutes per year6 minutes per year translates to 99。

999% of the time in that year that takes up。That's a very high number to shoot for that basically some of the most reliable system give you five nines of availability so you could say I want less so you have four nines of availability 99。

99 will actually buy you more than six minutes you can be down few hours of the year still pretty reliable think about like you can only be down few hours every year a system has to run even if some components fail and so so you could do three nines of reliability there's 99。

9 that means that you can have some days where you can be down still pretty reliable even three nine of reliability is actually pretty high many system don't even get to the 99% maybe even less than that but the most reliable systems you bid you provide guarantees in terms of how reliability is and usually you think about some number of nines of reliability that so this is what availability means reliability here basically is related term to availability it simply says the system。



![](img/643a99be646d86f3e09a360eacaf79d1_190.png)

![](img/643a99be646d86f3e09a360eacaf79d1_191.png)

ho run continuously without failure now as I said you can have a distributed system not every component is going to be 1 hundred0 percent reliable because components will fail I just showed you even if there are independent failures n is large there will be some independent component failure the system as a whole should continue to run that is what reliability。

If you have a reliable system， it will automatically give you higher availability because even if some components fail it is continuing to run and by as a result users can access it and do their own。

😊，Safety。Essentially is a related term it says temporary failure should not cause catastrophic failures this means that there should be no single point of failure in the system。

 which means if that machine goes down the entire system is down。😊。

So that is not something you want in your system you want every component to be replicated so that any component that is not replicated in a large system is a single point of failure because if that machine goes down thats the only component in the entire system that deals with that task the system as a whole can actually fail but if you want to have safety properties that should not happen some small number of components failing should not bring down the entire system okay that's called a safety property。



![](img/643a99be646d86f3e09a360eacaf79d1_193.png)

![](img/643a99be646d86f3e09a360eacaf79d1_194.png)

![](img/643a99be646d86f3e09a360eacaf79d1_195.png)

And and you you need the safety properties when you have mission critical system like an airplane right in airplanes are built with very high levels of redundancy。

 even if an engine goes down the plane can fly。

![](img/643a99be646d86f3e09a360eacaf79d1_197.png)

Or if some loss component and the engine fails， sometimes there are three other components that can take over at0 four degrees of replication and so they have high degrees of。

Replication to ensure high amount of safety same with a nuclear reactor you don't want some computing software to fail and the nuclear reactor to have problem right so so when you build these kinds of systems。

 you really pay attention to how you build very reliable safe and available systems but when you build software systems for other things that's not the case you basically ship systems with lots of bugs in it and let the user deal with it It is not how it should be but so you want to make sure that you want your system to actually be fault and and have all of these properties question。

If。to sixth's not like a tree。The question is how is the availability guaranteed is it statistics or is it based on some analysis。

 so technically it's a combination of the two if you actually build some degree of replication in your system you assign some probabilities of failure to the system then you can actually do the math and say this is what actually can be guaranteed the problem with that analysis is that there should not be correlated failure right？

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_199.png)

So what I showed here， assume these are independent failures correlated failures means if I have0 replicas。

 they are all one location， the power goes out， the entire system is down right but so you you want to make sure that when you do this analysis that these are all independent failure so if you don't catch correlated failure that can cause cascading failures which means one component fails it basically causes other components fail system goes but if you do the analysis right you can come up with an availability guarantee but then that availability guarantees also measured because you build a system and you told your customer I'm giving you five nine of availability at the end of the year they may show me that you actually gave me that and then you have to measure it and say look you had three minutes of downtime so Im actually under the five nine of so it's both ways but yes it can't just be measured then you don't know what you build the system。



![](img/643a99be646d86f3e09a360eacaf79d1_201.png)

![](img/643a99be646d86f3e09a360eacaf79d1_202.png)

![](img/643a99be646d86f3e09a360eacaf79d1_203.png)

![](img/643a99be646d86f3e09a360eacaf79d1_204.png)

Yes。Can availability be 100%， typically not because you cannot assume a component will never fail and any hardware or software is prone to fail that machine might die for any arbitrary reason so you cannot guarantee 100 percent of this。

You always have some small failure probability built。Yes。N。

Okay question is higher availability is higher reliability or other way around so you start with reliability the more reliable your system is which means it runs continuously without failure even if some components fail you get higher availability。

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_206.png)

哎。Or to put another way， if you want higher availability。

 you want to ensure that your system is higher reliability。



![](img/643a99be646d86f3e09a360eacaf79d1_208.png)

That's the way you are going to get a。And the reliability is going to be through replication and Fair fault recovery and all of that we look at。

Maintainability is the last term there that just means that if there' is a failure。

 you should be able to recover from it so and fix the problem。



![](img/643a99be646d86f3e09a360eacaf79d1_210.png)

Allright so with that we will talk about some more terms and then Ill show you some very simple techniques to do some false tolerance whether three terms we will talk about a transient false。

 intermittent faults and permanent faults okay so。

![](img/643a99be646d86f3e09a360eacaf79d1_212.png)

The transient fault essentially means this failure as the name suggests is transient okay the failure just comes and goes so this could be like a bit flip in memory right if you have RA you will you will know that there are some arbitrary fault where one bit just flips automatically goes from zero to one so that whatever is stored word or integer is stored and that location memory is changed because the bit just flipped that's an error that can occur in in RA so but that is not a permanent fault that just happened once in a while so there are many kinds of transient faults where。



![](img/643a99be646d86f3e09a360eacaf79d1_214.png)

The fog just happens one time and it's gone after that。

So that's for a transient fault intermittent fault means this fault is not permanent but it is occurring every once in a while so maybe its your car when you are turning its ss or something like that right so thats kind of when you are driving normally it does not give you that problem so these are faults that recur from time to time but they are not there the whole time so thats why they are called intermittent and permanent fall means that the failure has occurred and some component is actually fail。

😊，So so basically in terms of time this means that component is dead right some part of the system actually fail。

 this means that maybe the component is failinging every once in a while it doesn' not work。

 but then it works for some period of time this means that the。If it was one type。

 it just happened once and it's not happening。So several different types of falls that we want to think about。

 we want to worry about all of them， but permanent falls clearly you need to really deal with。



![](img/643a99be646d86f3e09a360eacaf79d1_216.png)

Then the other kinds of fault is what type of fault it is， not whether it is permanent or transient。

 but what caused it right。One type of fault is a crash failure， okay software crash。

That's a type of a fault。 So server just start working This is called a crash failure and there is an omission failure。

 omission failure means that the server did not respond as you sent it a request a server is up it doesn't crash it did not send your response Its called an omission failure timing failure says the server is slow you sent it a request you would like a response within certain amount of time。

 let's say half a second or 100 millisecond the server is taking much longer to respond。

 it feels really slow its sluggish it's a type of a fault and because server is become very slow timing failure response failure is very similar to omission failure says that but it is giving an incorrect response it is responding。

 you ask it some question it sending a response but the response is wrong maybe you send it RRPC request it give an incorrect response an arbitrary failure which is the worst type that we will deal with also called Byzantine。

is saying that the server may produce arbitrary responses at arbitrary times okay sometimes the server looks like it' is working well giving you correct response other times its sending you garbage okay and you can't tell when it will do the right thing and we do the wrong thing it could be because there's a bug it could be because somebody is actually hacked into the system and they are doing malicious things and it could be any number of reasons why this type of failures occur these are the hardest ones to see that we have to deal with crash failures as we will see although it sounds like something bad has happened from a failure recurring perspective is the easiest one to deal。

So various kinds of failures。

![](img/643a99be646d86f3e09a360eacaf79d1_218.png)

Well come back to them next time but today I'm going to end with this this slide which just shows you how do you deal with this in hardware and we will use the same technique when we design software okay so here is a circuit there are two figures here one at the top and one at the bottom the circuit essentially has three components its a hardware circuit don't need to know anything about hardware to understand this but let's say there are a circuit has three components A B and C each input takes one bit as input and it produces one bit as output so each of these components is doing performing some operation and is taking an input is producing a1 bit output so there are three stages to this circuit。



![](img/643a99be646d86f3e09a360eacaf79d1_220.png)

![](img/643a99be646d86f3e09a360eacaf79d1_221.png)

so in this case， so if the circuit is designed this way， if any A， B and C fail。

 the circuit stops operating。😊，because there is no redundancy here let's say B just stops working permanent failure circuit doesnt work anymore you provided an input there going to be no output or there is an intermittent fault where let's say b is randomly producing bad results every once in a word okay circuit will still sometimes seem to work sometimes not work again you have problem so this clearly has no fault tolerance built in at all so now we have a different version of this circuit where we have replicated each of those components we have three replicas of a a 1 a to a3 where three replicas of B3 replicas of C。



![](img/643a99be646d86f3e09a360eacaf79d1_223.png)

So， we will take each input we will feed it to all three copies of a B and C。

 each of them will produce an output we will take a vote and we will take a majority vote even if one fails the other two will agree。

because if one of them fail the other too so if you just take a majority vote。

 so long as two of the three are agreeing， we willll say that is the output of that stage and we'll feed it to the next state。

So， we will put a water in the middle of each of these so you replicate a B and C three times every input is weigh through all the replicas you take the output and then you vote and then you feed the output of the word majority vote the next day。

So you put a water， but you can't have a single water。😊。

And you will see there are three voterss here， why can't I have a single vote？

Yes water can fail why would we assume that the water that's a single point of failure all circuits right so anything can go wrong so so you could have in theory just have one water and youll see that A1a to a3 go to v1 and you could have taken that output and fed it but if the water fails you have the same problem by replicating a B and C and having a single water you are not solve the problem which is why you have three of these as well so you will take the output of all three will feed it to each of the water each of them will take a majority vote it will feed it to the next stage and so on now in this so you will see thats happened at each of the stage so in this circuit this is called triple modular redundancy which means that there is t is called tmR so there is three copies of everything。



![](img/643a99be646d86f3e09a360eacaf79d1_225.png)

![](img/643a99be646d86f3e09a360eacaf79d1_226.png)

So instead of one copy or three copies of everything。

 each stage you will produce an output you will want， you will feed that to the next stage and so on。

Okay so now any component can fail in the system， the system will continue to run。

An operator without any problem because if A2 fails a1 and A3 will agree some water that is not taking a2 or even if it takes a2 the voterss will take the majority vote they will feed it to the next day everything runs as no problem。

In some cases， multiple stages can also have single failures and it will work not always。

 but at least it guarantee is one component failure and is still fine。😊。

Is that clear what I just said？So this is a way you can design a hardware circuit and actually handle you know hardware failures but what you will see is the cost has actually gone up by factor of three in fact more than a factor of three because it voters as well in this right so we got our failure recovery at a high cost you triple the cost of the system in this case。

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_228.png)

Yes， for question。And the system we call 100 percent reliable so if this system can handle single failure。

 what that means is so long as no more than one component fails， the system will continue to run。

Right so that's what you can actually call it yes。But if you are more than one failure you cannot actually guarantee if a1 and A2 fail at the same time then the system will stop working because they might both produce the wrong result and the water will think thats the right result and feed it right so you will always design the system to tolerate some types of failure the failure is actually not aligned with what you design for then all bits are off so so long as you have one failure yes it will work fine。



![](img/643a99be646d86f3e09a360eacaf79d1_230.png)

![](img/643a99be646d86f3e09a360eacaf79d1_231.png)

Thank yet， any other questions？Why do it is three copies okay the question is why do we need three copies so if you want to tolerate a single failure and this is if it is a crash failure then you only need two copies because one of them just stops responding the other one still produces the right result but if it is producing arbitrary result this state lets say a1 no matter what you feed it always output zero。

Because that' is what the circuit got stuck and it just producing zero no matter or what then you need the other two to outvert it。

Because you don't know what if if you had only two copies okay one produce 0 and one produce one you dont know what is the right result right so you want the other two to outward so you need three right so that one failure means the other two are working they will actually outward the failed one and produce the right this is only required if you have arbitrary failures。

If you have a crash failure where the circuit that part of the circuit just dies doesnt even produce an output then you only need two copies because one of them is crashed the other one is functioning it will produce the right result but if the arbitrary result you need three copies in this case plus a water。

😊。

![](img/643a99be646d86f3e09a360eacaf79d1_233.png)

And in fact， more than onevol。Is that clear。Okay so we this is a very simple example to show you how we are going to build our distributed system as you can imagine if there was a three tier application you would have to do something like this to actually produce a system that can deal with a single failure deal with arbitrary things happening at each machine and so on and so so I'm giving you this hardware example to tell you how we are going to build our software system there will be a high degree of replication in what to deal with different kinds of failures and we will use voting to understand what to do at each level right so this is basically going to be a very simple example of how we will design our distributed system which we'll talk about next time。



![](img/643a99be646d86f3e09a360eacaf79d1_235.png)

![](img/643a99be646d86f3e09a360eacaf79d1_236.png)

![](img/643a99be646d86f3e09a360eacaf79d1_237.png)

![](img/643a99be646d86f3e09a360eacaf79d1_238.png)

![](img/643a99be646d86f3e09a360eacaf79d1_239.png)

Okay， all right， so let's stop here。