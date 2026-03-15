# 【剑桥大学-•-中英】分布式系统讲座-p14-P14-Distributed-Systems-5.1---Replication--BV1NwQhYeEyV_p14-

Welcome to Dis systems Le 5 Today we will be talking about replication So replication simply means having a copy of the same data on multiple nodes in the distributed system Replication is very widely used。

 so for example， many distributed databases use replication as part of their normal setup many distributed file systems allow you to have a copy of some files on multiple different nodes。

 many caching systems that are essentially forms of replication and we're going to be talking about algorithms that fit for all of those types of systems。



![](img/af4c1865f68e5468bf2814ab288e292a_1.png)

Now in a distributed system， any node has got a copy of the data is called a replica。

 and there are several reasons why you might want replication in a system。

 the most important one of which is that if some of the replicas are inaccessible for some reason。

 you've still got the other ones and the other copies of the data you can still use to serve user requests。

And so there are quite a few different reasons why a replica might be inaccessible for from time to time。

 there might be a software problem causing it to crash。

 There might be a hardware problem causing it to just stop working， there might be a network problem。

 which means you might have a network partition， so you might be able to communicate with some of the replicas。

 but not with others， especially if the replicas are distributed across different locations。

 you might be able to talk to your local replica， but not a replica that is somewhere remotely。



![](img/af4c1865f68e5468bf2814ab288e292a_3.png)

![](img/af4c1865f68e5468bf2814ab288e292a_4.png)

And another reason why you might want replication is you might deliberately make nodes inaccessible from time to time。

 For example， you might choose to reboot a node in order to install software updates and while that computer is rebooting。

 it can't be processing any user requests or any messages and so during that time that that node is unavailable and really what we want is that a service as a whole of a database。

 for example， it continues working even if some of the nodes are unavailable and replication is one of the mechanisms we have which allows us to provide that sort of full tolerance which is very useful。

 especially if you need to do maintenance of the system because it means you can reboot one node at a time。

 as long as you're not turning them all off at the same time。

 as long as you just reboot one at a time then the remaining nodes at any one time can continue processing requests。



![](img/af4c1865f68e5468bf2814ab288e292a_6.png)

![](img/af4c1865f68e5468bf2814ab288e292a_7.png)

Another reason why you might want replication is if there's very heavy load， for example。

 lots and lots of different users around the world all want the same piece of data。

 then that might be too much for a single node to handle and in which case having copies of that data on multiple nodes simply lets you handle more requests from more users。

 which is important in internet scale systems。

![](img/af4c1865f68e5468bf2814ab288e292a_9.png)

![](img/af4c1865f68e5468bf2814ab288e292a_10.png)

Now replication is really easy if the data that you're copying doesn't change。

 this is kind of obvious if you've got some data that is static。

 you can just make a copy of it a onetime copy across all of your nodes and jobs done so what we're all going to be focusing on in this lecture is data that changes because that's the bit that is hard the data changes are the bit that is hard and that requires the most care。



![](img/af4c1865f68e5468bf2814ab288e292a_12.png)

Now， one form of replication that you might have come across in the context of operating systems is called raid。

 And so this is if you have multiple hard disks attached to the same computer。

 you can use raid redundantly store data on more than one hard disk。 So for example。

 in the case of RA1。 you actually have two separate disks that are basically mirrors of each other。

 So any file that is written to one disk is also written to the other disk。

 which means if one of those disks experiences， a hardware failure。

 you've still got the data on the other disk， extremely useful if you don't like losing data。

 Now the replication that we talk about in distributed systems is somewhat similar to that except the techniques that are used to raid don't immediately apply in a distributed system because raid is designed for a single computer there's a single controller that manages all of the data in a distributed system as we've seen in the previous lectures we've got each node in acting independently。

 we've got the unreliable network in between the two nodes。



![](img/af4c1865f68e5468bf2814ab288e292a_14.png)

![](img/af4c1865f68e5468bf2814ab288e292a_15.png)

![](img/af4c1865f68e5468bf2814ab288e292a_16.png)

![](img/af4c1865f68e5468bf2814ab288e292a_17.png)

![](img/af4c1865f68e5468bf2814ab288e292a_18.png)

![](img/af4c1865f68e5468bf2814ab288e292a_19.png)

![](img/af4c1865f68e5468bf2814ab288e292a_20.png)

Nodes might be distributed around the world， so they might be not located in the same location。

 but they might be on different continents communicating over the internet。

 and so we have to deal with all of the challenges that this sort of distributed setup brings。



![](img/af4c1865f68e5468bf2814ab288e292a_22.png)

![](img/af4c1865f68e5468bf2814ab288e292a_23.png)

So let's look at one example just to get us started。😊。

Of cases where we've got a database that is storing some state and that state changes。

So here we have an example of a social network and some user posts an updates saying the moon is not actually made of cheese and you want to press the like button on that。

 Okay so the fact that you have pressed that like button needs to be stored somewhere and also the fact of how many people have clicked that like button needs to be stored somewhere and that somewhere is typically a database that is running somewhere on the servers of the social media provider。



![](img/af4c1865f68e5468bf2814ab288e292a_25.png)

And what could happen now is I'm just going to consider the count of likes for now。 So the client。

 just as you press the like button， the client needs to tell this counter that is stored somewhere that。

 oh， you need to increment the counter because one more person has liked this particular update now。

 But networks being what they are， of course， it could happen that either the request or the response is lost in the network。

 And so let's consider in this example that the request got through。

 but the acknowledgecknowment back to the client that okay， I I incremented the counter。

 The acknowment got lost in a network。 And so the client says， well。

 seems like the request didn't get through。 Let's try it again。

 Let's send a request to increment again。 The server receives that request again。

 And so it in ends up incrementing this counter twice。 And so we go from 12300 to 12302。

 Even though you actually only pressed that button once。



![](img/af4c1865f68e5468bf2814ab288e292a_27.png)

![](img/af4c1865f68e5468bf2814ab288e292a_28.png)

Now this might seem like a bit of a hypothetical example。

 but it really does occur Now the first thing we can do to try and prevent this kind of thing is to do deduplication and weve seen that in the context of the broadcast protocols for example。

 however with databases with a database generally we want to support a crash recovery type system model that means you know if a node crashes it doesn't stay offline forever it will come back which means that any data that needs to be not lost in the process of that crash and restart needs to be stored on disk in stable storage in some durable form and if you want to deuplicate requests to a database。

In a way that will work even across crashes and restarts。

 that means that all of the requests actually need to be stored in the database as well。

 I can end up being quite a lot of data。 Now， you might think that this sort of thing is just a hypothetical problem。

 but it really does occur。 This is an example。 this is a screenshot。

 a genuine screenshot that I made of Twitter a few years ago。

 And it shows a user account who is following -20 people。



![](img/af4c1865f68e5468bf2814ab288e292a_30.png)

So。This should be impossible because， of course， you can only follow a positive number of people in real life。

 There are no negative users。 And so I don't know exactly what happened in this in this scenario here。

 but I suspect that something happened was very similar to this example。

 So probably the user was following some number of people。

 Then they unfollowed those people in the process of unfollowing those people some counter of how many people this person is following had to get decremented。



![](img/af4c1865f68e5468bf2814ab288e292a_32.png)

![](img/af4c1865f68e5468bf2814ab288e292a_33.png)

And so there was some network failure somewhere。 And so that decrementing of the unfollow counter that sorry。

 the decrementing of that follow count got repeated。

 And so we end up decrementing more than there were actually followers。

 And so that's why we end up with a negative counter here。



![](img/af4c1865f68e5468bf2814ab288e292a_35.png)

So okay， I think Twitter has probably fixed that bug in the meantime。😊。



![](img/af4c1865f68e5468bf2814ab288e292a_37.png)

But let's look at how we would deal with this kind of problem in our systems and one tool that is very useful in the context of these kinds of retries is to make the operation idpot。

So idpotence is a concept from maths， which just means that if you apply a function once to some argument。

 it has the same effect as applying it twice or applying it three times or applying it any number of times and so an example of a function that is not idpotent is to increment a counter like we have just seen because if you increment a counter once。

 that's not the same as incrementing it twice， however。

 adding an element to a set is idpotent because if you add an element to a set and then add the same element to a set again。

 because the set doesn't count how many times an element is there it's either there or not there and so therefore doing the set union operator that is idpotent and so this means now if we represent this these likes or the user follows in the case of Twitter as a set rather than as a counter。

 then we can safely retry because even if the request gets lost or so we can just send that request to add an element to a。

Se we can do that again， and applying it twice does no harm because it just does the same as applying at once。

Which leads to a choice of different semantics that you get in in these types of distributed systems。

They are just terms that you might see， and so I wanted to mention them briefly。

 which are at most once at least once and exactly once。

 So at most once just means you send a request of the network once it may or may not get there。

 but you're not going to retry so it might arrive it might not arrive but you're not going to try and make this reliable in any way at least once means you're going to retry until you get an acknowledgecment which means the request may arrive multiple times。

 but really what we typically want is exactly once。

 which means the operation takes effect exactly once So the effect is as if the operation were received exactly one time。

 even though in practice due to retryries and due to message loss。

 it may actually be some different number of times and so if we retry and also have an operation that is item potent。

 then we can achieve exactly one semantics， So that means even。

If the operation is applied multiple times， the effect is as if it had been applied exactly once。

 or of course we can achieve exactly once through de duplication as well。

 as long as we're willing to store the requests that have really happened in some form。



![](img/af4c1865f68e5468bf2814ab288e292a_39.png)

So let's have another problem。 look at another problem， which。

Highlights the limitations of item pots。And that is。

 we've got two different clients this time and client one wants to add a like or add your user ID to the set of users who have liked a particular update。

 And as we've seen， this is an item potent operation。 This function F is item potent。Now。

 clientient 2 reads from the database。 It reads the current set of users who have liked it and decides to unlike this。

 And so what this means is to remove a particular user Id from the set of users who have liked a particular update。

And clientient 2 makes this request G and sends it to the server and the server acknowledges it。 Now。

 the first request the client1 made the acknowledgement got lost in a network。

 and so client1 is going to retry this request。 And so what the effect is now is the client1 sends this request to add the like back to the server again。

 And the server， though， has actually just removed the like from the set of user Is。

 And so it's going to add it back in again。 And so here， even though the function F is idpotent。

 So applying the like twice the same effect as applying it once。

In the context of also having this unlike operation， actually。

 the idpotents doesn't quite work anymore， because if we apply first f， then G then F。

Then this is not the same as just applying press F and G because the second application of F is going to add the element back into the set again。

 And so here， the user intention was that this item should not be liked because the user first liked it and then unliked it。

And this retry of adding the like still causally belongs to this first request here。

 so it's not a separate request to add it back in again。

 but the actual intention is that the end result is this update is not liked。

So let's have a look at an approach that we can use to solve this problem。



![](img/af4c1865f68e5468bf2814ab288e292a_41.png)

And I will illustrate this with another problem that can happen with replication and so in this case here what we have is a client that wants to add an element X to a set。

😊。

![](img/af4c1865f68e5468bf2814ab288e292a_43.png)

So I'm just going to treat it more abstractly not let's forget about status。

 updates and likes for now， just more abstractly we have some element X that needs to be added to a set on both replica A and replica B。

😊，And first， the user adds it and then the user wants to remove it again because people can change their minds。

 Okay， fine。 And so the first we have an ad request that goes to both replicas。

 Then we have a remove request。 Now， unfortunately。

 the remove request is lost in the network on its way from the client to replica B。

 So replica A receives both the ad and the remove。 but replica B only receives the ad and it doesn't receive the remove。

So the end result now is that the element X is in the set on replica B because it hasn't been removed。

 but X is not in the set on replica A because has been removed。Now， if you think about this。😊。

The state of the two replicas in this example here is exactly the same as in this example。

 So in the second example， the client wants to add X to the set。

 The addition goes through and reaches replica B。 but the addition is lost on its way to replica A。

 So， again， we have the same state that X is present on B， but absent on a。

And these two so that the final state of the two replicas is the same in these two examples。

 but actually we don't want it to be the same because the user intention was different in the case of the first scenario here。

 the user first added then removed so the user intention was that the final state should be that X is not in the set。

Whereas in the second scenario the user only added， the user didn't remove anything。

 so the user intention is that x is present in the set。

 so the user intention is actually different in these two。

 but from the point of view of the replicas these two outcomes look the same and so we have to distinguish these two outcomes。



![](img/af4c1865f68e5468bf2814ab288e292a_45.png)

And the way we can do that is by adding timestamps to things。

 so we're going to reuse what we've learned before about logical timestamps。

 and we're just going to have the client generate a logical timestamp when it makes the request to the two replicas。

And so， the。Clients generates this timestamp T1 and it attaches T1 to the ad request that is sent to both A and B and now A and B both store this timestamp T1 and I'm also going to associate here X with a value true and true here just means that x is present in the set and we will see in a moment why we need this because what happens next is now that the client makes a remove request and because this is a new request it makes a new logical timestamp T2 attaches T2 to the request the request is sent to both A and B Now because this is a logical timestamp and the remove happened after the ad。

 this means that T1 will be less than T2 T2 will be greater than T1。

And so here we have replica A receives the request to remove it， remove X。

 and so instead of actually removing X from the database。



![](img/af4c1865f68e5468bf2814ab288e292a_47.png)

A leaves x in the database and says， actually， we're just going to attach this value false here to X。

 and false means treat the value X。 I'll treat the element X as if it were not present in the set。

 because the user asked that we remove it， but we're not actually going to remove it because otherwise we wouldn't know whether the user added or removed it。

 So we're going to leave this marker in the database marked as false。

 saying x is not actually in the set and the deletion happened with a times stampamp of T 2。



![](img/af4c1865f68e5468bf2814ab288e292a_49.png)

So here now we can distinguish on B， we have that x is present because it has a value of2 with with a timestamp of T1 on a replica a x is absent because it has a value of false and a timestamp of T2。

 So this construction where we don't actually delete something。But just mark something as deleted。

 It's called a tombstone。 and this appears in various different distributed algorithms。

 when we have to deal with deletion。 So tombstone just means something was supposed to be deleted。

 but for internal reasons， we have to actually keep it and maybe tombstones can get garbage collected at some later point in time。

 that's a separate question But But for now we just need to keep remembering this item。

 even though it has been deleted。 And of course， we attach this logical timestamp。

 So every time some object in the database is written。

 we attach the timestamp of the last operation that wrote it。

 And this allows us to tell which values are newer and which are older。

 So this means now that after this is happened， A and B are no longer in the same state。

 because A receive the request to delete X with the timestamp of T2 whereas B did not receive that request because it got lost in a network。

 And so according to B X is still present in the。

![](img/af4c1865f68e5468bf2814ab288e292a_51.png)

![](img/af4c1865f68e5468bf2814ab288e292a_52.png)

And it has a last modification times stampamp of T1。



![](img/af4c1865f68e5468bf2814ab288e292a_54.png)

And now the two replicas can run a protocol in which they compare what they have。

 They compare their data。 And this protocol is called an antienttropy protocol because I guess it's sort of。

 it's supposed to clear the entropy in the confusion and the uncertainty in the system and。



![](img/af4c1865f68e5468bf2814ab288e292a_56.png)

Bring all of the replicas back into the same state。

And so as A and B reconcile their state and perform this anti entropy protocol。

 they will compare their timestamps。 And since we have these logical timestamps attached to every data item。

 they can realize that Ot1 is less than T2。 So therefore this value that B has must be older。

 the value that a has must be newer and so therefore the object the record on B is going to get replaced with the one from a。

 So the one from a is the more recent one so that gets propagated to B。

 And so here the timestamps have helped us because they tell us about the recency and the relative ordering of these updates。

 So timestamps have been very useful。

![](img/af4c1865f68e5468bf2814ab288e292a_58.png)

And so typically we will probably have one timest for every given key or every object in the database because that's the granularity at which we're going to do that reconciliation。



![](img/af4c1865f68e5468bf2814ab288e292a_60.png)

Now what kind of logical timestamps do we use here so in our last lecture we saw the distinction between Lalor clocks and vector clocks and in fact we can use both in databases and we get slightly different behaviour so it really depends what behaviour we want。



![](img/af4c1865f68e5468bf2814ab288e292a_62.png)

![](img/af4c1865f68e5468bf2814ab288e292a_63.png)

And this becomes apparent if we consider two clients that are making rights to this replicated database concurrently。

 So here on client1， client1 wants to update the value that is associated with some key X。

 So x is the key V1 is the value that client1 wants to attach to X。

 and this operation is going to have a logical timestamp of T1。Concurrently， while this is happening。

 client2 also wants to set the value of x it wants to set it to a different value V2。

 So client1 also generates a logical timestamp T2， send an operation of the network attached attaches T2 to this operation。

 The operation is， I want to set the key X to the value V2。 Now。

 notice that replica A first receives the requests from client 2 second receives the request from client 1。

 whereas replica B receives them in the opposite order replica B first receives the request from client 1。

 then the request from client 2。 So this means the replicas can't just use the order in which they see the requests in order to determine whether V1 or V2 is the final value for X。

 because if they did just use the order in which the requests arrive。

 then they would end up in different state。 They would end up inconsistent at the end。

 And so what we want in a replicd system is that all of the replicas end up being in the same。



![](img/af4c1865f68e5468bf2814ab288e292a_65.png)

![](img/af4c1865f68e5468bf2814ab288e292a_66.png)

![](img/af4c1865f68e5468bf2814ab288e292a_67.png)

ateOtherwise， it's not a replication。And that's why we need to use the timestamps here because the timestamps provide a relative ordering of these two operations。



![](img/af4c1865f68e5468bf2814ab288e292a_69.png)

Now one option is that we use lampor clocks and if you remember what we have with lamp port clocks is they give us a total ordering so total ordering means that for any two timestamps that exist in the system we can always compare them and it will always be the case that one is less than the other and so in this case for example we can say that T1 is less than two than T2 but it might just as well be the other way round because in this case the two operations are concurrent and so the ordering that the lampport timests provide us is arbitrary essentially。



![](img/af4c1865f68e5468bf2814ab288e292a_71.png)

![](img/af4c1865f68e5468bf2814ab288e292a_72.png)

And so。What we can do here， for example， is that we compare T1 and T2 and we just keep the the version the value with the higher timet。



![](img/af4c1865f68e5468bf2814ab288e292a_74.png)

And this will work because then as the value gets overwritten。

 we know that the overrite happens after a previous operation and therefore it will always have a greater timestamp。

 So therefore overr a smaller times stampamp with a greater times stamp is is a fine thing。

 you can do that。

![](img/af4c1865f68e5468bf2814ab288e292a_76.png)

And this behavior is called last writer wins because we assume that the last one。

 the last writer is the one with the highest timestamp。

 and so the highest timestamp wins if they are several concurrent updates with different times stampamps。



![](img/af4c1865f68e5468bf2814ab288e292a_78.png)

Note， however， that this means that if say T2 is greater than T1。This means we keep V2。

 which was written by client2， and we simply discard V1。So value V V1 is simply gone。

 So we're not even storing that value anywhere。 it simply gets overwritten and forgotten。

 And this might be okay， depending on the application， there might be applications in which actually。

 if there are two concurrent rights。 It's fine to just keep one and throw away the others。

 If there are five concurrent rights， we're going to keep one and throw away four of them。

 But there might also be scenarios in which actually， if there are several concurrent rights。

 we want to keep all of them。 And we want to explicitly resolve this situation。 And if we want that。

 well， we use a vector clock instead of a lamp port clock。 if we use a vector clock。

 then if we generate two different times down to T1 and T2。 and these two operations are concurrent。

 then vector clocks will also be incomparable， we will end up with T1 and T 2 being incomparable and this allows us to detect the fact that these two operations are concurrent。

 And so。

![](img/af4c1865f68e5468bf2814ab288e292a_80.png)

![](img/af4c1865f68e5468bf2814ab288e292a_81.png)

![](img/af4c1865f68e5468bf2814ab288e292a_82.png)

In this case， now we will only overwrite one value with another value if their vector timestamps are the later ones strictly greater than the earlier one。



![](img/af4c1865f68e5468bf2814ab288e292a_84.png)

Under the strictly greater than relation that we've defined previously。

But if we have two concurrent updates， then we will keep both of them。

 And so in this case now there's not a single value attached to the key X。

 but there could be multiple values in this case， V1 and V2 and so in this case we can give those two values back to the application and the application can then resolve this that this is called a conflict and the application can have explicit logic for conflict resolution so that if these two updates happen concurrently and we have two different values written by different clients then we can avoid throwing away data。

 we can combine the information from these two values that were written concurrently into a single value write it back to the database again and that ensure then everyone is happy and no data was lost So we have this choice here using either the totally ordered lamp or timestamps or the partially ordered vector timestamps depending on which kind of behavior we actually want and different databases。



![](img/af4c1865f68e5468bf2814ab288e292a_86.png)

![](img/af4c1865f68e5468bf2814ab288e292a_87.png)

![](img/af4c1865f68e5468bf2814ab288e292a_88.png)

Stemms actually make different choices with regard to what sort of timests they want to use because for different applications。

 different methods are appropriate。

![](img/af4c1865f68e5468bf2814ab288e292a_90.png)

So far， that and。

![](img/af4c1865f68e5468bf2814ab288e292a_92.png)

Next， we will look at full tolerance in replication。

