# 【加州大学】分布式系统-CSE138（Distributed-Systems）-p15-P15-L15---introduction-to-sharding-consistent-hashing--BV1eGdLYjETJ_p15-

All right， let's make sure the stream is up。Allright， it looks like we're live， good。

Welcome to Thursday。So today we're going to be continuing our discussion of Dynamo。

 I was just reminded a student stepped into office hours to。

Ask some questions about the Dynamo paper and I was just reminded of there's really so much in this paper that we aren't going to have time to cover because this paper kind of has the kitchen sink of distributed systems ideas。

And there's a lot in there that we honestly don't have time for we're trying to hit the big themes。

 but there's a lot of detail， so now don't think of what we're talking about in class as comprehensive。

 However， today we're going to try to talk about one of those big ideas。

That's in this paper that is not specific to Idamo， they weren't the people who invented it。

But it's one of the ideas that they really use to good effect。So first we're going to talk about。

Sharting。Also known as data partitioning。And then we're going to talk about the concept of consistent hashing。

Which is a。Which is used in dynamo， but not unique to dynamo。

 It's one of the ideas that comes up in this paper， but they didn't invent it。嗯。

I realized last time that。I didn't talk about。Some of the systems that have been inspired by Dynamo。

 I guess I briefly mentioned Cassandra when I was talking about quorum systems。

 but but Dynamo is you know it's not open source of course。

 but it has inspired some great open source work so one of the systems in particular。

That was inspired by Dynamo is the Re database。So react。Has some interesting history。

 was it was developed by a company called Basho and。In the。And of mid 2010s。Baashio was。Kind of。

At the forefront of distributed systems in industry， and they had a great blog。

 they ran great events， and I met some great people who were working for them。And that's。

Sort of how I entered into the distributed systems community was these folks at Basho who worked on Re。

RAC is an open source clone of dynamo。And one of the things that they did。

 I'm not actually not sure if this is still in the react documentation， but at the time。

They had a really interesting section in their documentation where they compared react with Dynamo by going section by section through the Dynamo paper。

And talking about how their product implemented every aspect of the paper。

So I'm checking actually looking at their documentation right now to see if that's still the case。

 I'm not sure if it is， in any case you can go look up。

 reactact on your own if you're interested all the documentation is still online。And。诶。

It's a cool system to check out if you're interested in。Open source。

Implementation of something that's a whole lot like dynamo。

They also have some pretty good kind of practitioner oriented explanations of the concepts in their documentation。

Something to check out。All right， so let's just jump in with。With today's topic。

So we've spent a lot of time talking about replication， right？And as you know。

 replication involves having multiple copies of the same data on different notes。

 so in the systems that we've talked about so far。Every replicas stores all the data。

So that involves something like。You might have some different machines。So if it's key value store。

Let's say that you have some key value pairs。Something like this。And you've got a bunch of clients。

Who may be talking to one or more of these machines， right？

So everybody stores all the data in the replication approaches that we've talked about so far。

 sometimes this is called fall replication。Do you see any problems with doing it this way？

So we've been talking all this time about how a replication is good。

And now I guess I'm asking you to think about。What might not be good about having everybody store all of the data？

Any thoughts on that？Great， good points。Storage cost， for sure。

If you have to store all the data on one machine， then that machine needs to have a lot of storage。

 right？And that costs money。AndYep， it sounds like a couple of people said exactly the same thing in chat and then there's the cost of keeping the copies consistent right so if you are storing the data everywhere。

 then every time any of these machines gets updated then that update needs to get broadcast to all of them as you're finding working on the assignments so。

I can think of a couple of issues with this approach。

What if you have more data than fits on one machine？That's one problem。

Then keeping them all consistent is another issue。If everyone stores the data。Consist is arguably。

More expensive to maintain。Okay。So there's some problems with doing it this way。And， furthermore。

What if it's primary backup， so what if it's a primary backup type approach， maybe this one here。

 maybe M1 is the primary。So if you have lots of clients making lots and lots of requests。

The primary has to do a lot of work， it has to field all those requests。

And the clients can't just talk to the other two machines because in that situation。

 you would lose strong consistency。Well。What if you did this instead？

Let's talk about pros and cons of something that looks like this。

Now you've split up your data set across three machines。

And they don't have to be kept consistent with each other because they're all storring totally disjoint parts of the data set。

So that's kind of nice right it means that if this client only needs X。

 then they can just talk to that machine， if this client only needs Z。

 then they can just talk to that machine and so on so in this kind of a situation。

We've saved the effort of keeping these consistent and we've distributed the load。

So that's kind of nice， but what's wrong with this？

What did I lose in going from that earlier design to this design？Okay。

 some servers might not receive a request。Yeah， okay。 But what's the bigger issue， What did I lose。

Between going from this approach。That we had before to this one up here。Exactly， fault tolerance。

 Yeah， our data isn't replicated anymore。We lost replication， so now we don't have fault tolerance。

 okay？So let's put it back。I'll give these different names。I'll call this M11 M21 and M31。

 and let's do some other machines across here。So I've split up the data now。Among multiple nodes。

 I've also put back the replication。So right now I'm doing both replication and sharding。

 so splitting up the data set among multiple nodes is known as sharding。

And I've got three shards here。So we could call this shard one。This shard too。And this one sh three。

And then we could think of these。As being our replicas。

So sharding and replication are orthogonal to each other。You can do sharding without the replication。

 that's kind of what we had a minute ago when we just had something like this。

Or we can put the replication back in。And now we have both sharding and replication。

So splitting up the data among multiple nodes like this。Is not to be confused with network partition。

Network partitions， as we talked about are something that you don't want this is also called partitioning。

 but this is partitioning on purpose。Not to be confused with something that you don't do on purpose。

 which is a network partition。Okay， so what are the reasons for doing this？One reason， of course。

 is so that you can store more data than can fit on one node in a hypothetical situation where you could only store one key value pair on a node。

Then you'd have to do this， right if you wanted to store more than one。

Now in this particular example I happened to have split up my data into three partitions in practice we would have a whole bunch of key value pairs on every partition。

 but a disjoint set of them on each， so this is just an illustration right in practice you would have many。

 many key value pairs per partition， but there would be a disjoint set on each。So。

Storing more data than can fit on OneNote is one reason to do this。Or capacity to put it。

More concisely。So increased capacity。And then another reason would be increased throughput。

So these clients now。If they are happening to talk to different parts of the data set。

 then they can both do so at once and those nodes don't have to coordinate with one another。

 so throughput means more throughput means you can serve more requests in a given amount of time。So。

Just to give you an idea of other possibilities。You could also imagine a different sort of partitioning setup。

And I don't want to confuse you too much because this something like this。Works， right。

 but you can also imagine something something different。Where you have your data partitioned。

But in this case， there's。Every node here corresponds to a particular every node belongs to one shard。

 right， but you can imagine a different sort of setup， so for example， we could have this。

You could imagine having。Say three machines。And let's say that I do it this way。So I could put。X。

On M1 and M2。I could put why。On M1。And M3。And I could put Z。On M2 and M3。So this is also sharding。

And then here's our clients over here。So this is kind of nice。Because。

I've managed to split up the request load， right？So if one person is making a request and they need an X。

 right， they have a choice of who to talk to， right， but maybe they can talk to this machine here。

Maybe somebody else needs Z so they can talk to one of these machines over here。

So we can still get some throughput that's better than if we were not doing sharding。

But something kind of interesting is going on here， so we have two copies of every。

Of every key value pair。You can imagine a sort of setup where。

Every machine is going to be acting like a primary for one part of the data set and is a backup for another。

 So maybe this right here is the primary。Copy of X， and then this is the backup copy of X。

Maybe this is the primary copy of Z， and this is the backup copy of Z。

And maybe this is the primary copy of Y， and this is the backup copy of Y。

So in that kind of a scenario， if you need X， you would talk to Ma one because machine one has the primary copy of X。

 then those updates would have to be synchronized with the backup copy。Which is over here。

 so those machines would talk。Likewise， if you need Z， then you would talk only to Ma two。

And then you would have to synchronize here。And so on。So this is an approach where there's。

More than one。Shard。Per note。And this is also a totally reasonable way to do sharding。

So sharding is really important， it's really important in railroad systems。

 it gives you better throughput， right， because you can serve different parts of your data set from different machines at the same time。

And it makes it possible to store a data set that's too big for any one node， so increased capacity。

 increased throughput。If you were not using a strongly consistent replication strategy。

 then you were already able to serve requests from different machines at the same time。

 Dynamo does this， for instance， but you definitely still need partitioning if you want to serve these bigger than can fit on OneNote data sets。

So real systems are going to do both replication and partitioning。And。

As you can kind of see from coming back to this picture。

The choice of the partitioning strategy is mostly orthogonal to the choice of the replication strategy so in our discussion today。

We're going to mostly forget about replication and focus on partitioning。 In other words。

 we're just going to be looking at this piece of the picture。

So it's not that replication doesn't matter anymore。

It's just that we're going to be focusing on this piece of the picture and you can assume that the data is replicated somehow。

So how it's replicated is not going to be our concern for the moment。

 instead for the moment we're just going to be concentrating on how do you split up your data set among the shards？

So we're going to leave aside replication for a little while and focus just on sharding for a while。

So let's get rid of the replicas from our picture and just focus on partitions。

And if it makes you nervous to see data only appearing in one place。

 then you can imagine that this is getting replicated somehow。

 but just imagine that that conversation is going to be orthogonal to what we're talking about here and everything that we're going to be talking about here is something that can take place in the presence of replication。

Okay。So let's say that we have a large amount of data and we want to partition it。

How do we decide which data to put on which notes？How do we decide how to split up our data among the shards or how do we decide to shard our data？

Let's keep it simple。And continue to imagine that the data is these key value pairs。

 so it's a simple data model。So。Which key value pairs go where？Well。

What are we trying to accomplish with our partitioning strategy。

 What do you think we want to aim for？Or another way to put that is what makes a sharding strategy good？

What do you think？Good， yeah。So。You want to avoid hot spots， right？

You'd like to get things reasonably， equally distributed or reasonably evenly distributed among the nodes。

 right？So okay， how would you accomplish that？What possibilities？You could try randomly assigning。

Records denote。What would happen if you did this well？If you have a， you know。

Assuming that you have a way to uniformly random assign the data to the nodes。

 then this will be pretty good at evenly spreading the data around。So this checks that check mark。

But what might not be good about randomly assigning the data？

So just to give you a hint about where I'm going。There's one good thing。

 and then what not so good thing about this approach。

 So what do you think the not so good thing about randomly assigning the data might be。

What if you're a client？What if you're a client and you want to know where Y is？Exactly。

 you won't know where to look for the data again later。

So randomly assigning will do really great in terms of evenly distributing the data。

 but it'll also make it hard to find what we want later on。Okay。

Kind of the opposite of this would be if you just decide to put everything on one partition， right？

So then it's easy to find what you want， it's trivial， right？I guess I'll use the same check marks。

Approach that I used before。Easy to find what we want。But it's。Absolutely。

 the worst you can possibly do in terms of。In terms of even distribution。Okay。

So those are kind of two straw man strategies that won't work。What can we do instead？Well。

 let me throw another slightly better strategy at you and tell me what you think about this。

You could have every partition store a particular range of the keys。Partition by key range。

So for instance， if my keys are alphabetical strings。

 then I could say that M1 is responsible for a certain range of the alphabet。

 and M2 is responsible for a certain range and M3 is responsible for a certain range。You know。

 maybe M1 is responsible for like Q's A through H。And maybe we have like B here。

Maybe M2 is responsible for I through R。We've got P here。嗯。And M3 gets S through z。Maybe we have。

Why here？Okay。So。This seems to work OK， and some systems do something like this。

 but what's the downside of doing it this way？Well finding what we need is not the problem in this case。

 if the client knows where to look， then。It's not hard to find what you need。But。What's the problem？

Any ideas why this might not be great？Yeah， so the point made in shot is some ranges might have more keys than other。

 what if the data starts coming in？What if the rights start coming in and they're all like， you know？

S。Why。Z。So you'd end up with an uneven distribution of data。

Because your keys weren't uniformly distributed across the space of。Of the alphabet， right。

 so then that means your data is now unevenly distributed across the servers。So。

Distribution of data might not be great。So key range partitioning probably isn't a good way to go unless you have some way of knowing in advance that your requests are going to be。

Adding a uniform distribution of keys but。There's hope。

We can actually solve this problem very easily。How do you take data that's not uniformly distributed and make it uniformly distributed。

 knows， who knows the answer？Good， great suggestion， suggestion is hashing。The keys。So。

A hash function。Is a way to take data that's not uniformly distributed and make it uniformly distributed。

 So a good hash function could take our possibly wildly uneven distribution of keys。

And we'll distribute them evenly across its output space。

 so let's take a look at what that might look like。So。Let's take it。Hash function。Let's say MD5。

 for example。So MD5 takes an input。And produces an output。So maybe the input is a string。

Let's say that this is a picture of the input space of MD5。

So let's say that we have a bunch of strings from like。A upp here down here。

And then we've got a bunch of other strings in here。And so on。What does the output space look like？

Well。With MD5， we get outputs that are somewhere in the range from zero。To。Two to the 128。Minus1。

So the hope。If we have a good hash function like M5 is that。Even if your strings are。No。

Unevenly spaced across this input space。 Like let's say that you have a bunch clustered here at the top。

 Let's say that you have like。Apple。Awkward。And so on。

So not really a nicely distributed set of strings。The hope is that these are all going to map onto more or less。

Even。Points。Somewhere in the output space。So this is great， right？

It'll give us a way to distribute the keys evenly across the nodes。

The trick is just that you have to hash them。Then you give every node some evenly sized piece of the output space。

So how would you do that， well， if we had our three nodes。M1， M2 and M3 that we talked about before。

Then one way to do this。Is take the output of the hash function。

And if you need to split this state over， say these three nodes。Do mod three of the hashed value。

So in other words， if something landed here at zero。Then that would go on to Ma one。

If it landed at one， that would if it two， that would go onto machine3。And so on。

So you would end up splitting up the data hopefully more or less evenly， so you know。

 maybe in this approach。I have no idea what the MBA5 hash of these strings are。

 but maybe hopefully you would end up with something more or less even。

 like maybe this would end up here。Maybe this would end up here。

Maybe Apple would end up here as well。And maybe。So maybe you'd get something like this。

It's not necessarily perfect， but the more data that you have。

 the more likely it's going to be that it's evenly spread out over this output space。

 and so even though it's a little bit uneven at this point。

 the hope is that you would end up with something that was more or less evenly distributed。

Furthermore， it's not going to be hard to figure out where things are because this is a really easy function to compute。

So the client， when they need to look up a particular key， like if they need to look up this key。

 for example。They can just take the hash of it and then they know which machine is going to store。

And rather they're going to take the hash of it， in this case， hashmon three。

 and that will tell them where to look for that data。So。

If I want to know where to put a key value pair， know whose key is Apple？Then。

First I hash it to get this 128 bit hash value。And then I do mod three of that。

 and that'll give me no some machine ID。So the output here is going to be。

 in this case it's going to be0，1 or two， and that'll tell me one of these three machines。

And if I want to look up a key and I need to know where to find it。I just do the same thing。

 I calculate that key's hash， which is an easy quick computation。

 and then I do mod3 or mod to n for whatever number。Of nodes I have。

And that can be done either on the client side or it can be done on the data store side。

So that all sounds great。So。Carteitioning。By hash of key。Moud in。Where N is the number of partitions。

Okay， it seems pretty good。Unfortunately， there's a catch。You knew there was going to be a catch。

What's the catch with this approach？You a partition can get full， yeah。

 but I think you have that issue with any approach， right？So if a partition is starting to get full。

 but however， that that question kind of points to。The issue。

What happens if a partition is starting to get full， what should you do then？

What if you started to notice that machine three is getting pretty full， what would you do？Yeah。

 okay， key collision， so the worry is that different inputs could hash to the same thing。

 but I don't think that's too big of an issue， the output space of MD5 is pretty big。

 it would be fairly unlikely。And even if it did happen， it wouldn't be the end of the world， right？

So I'm not really too worried about that。Great， yeah。

 So the question I just asked was what do you do when when a partition starts to get too big and somebody correctly said in chat well。

 you could add a node， but then the hashes won't be correct。 Yeah， yeah。

What happens if I try to add another machine？A partition is getting full or more than one partition is getting full。

 Maybe they're all getting full。 And so I try to add another machine。Oh， no。Nowow what？

The trouble with doing this hash of key mod n thing is that if n changes。Now。

 most of the data has to has to somewhere else， right。

 most of the data or doesn't has to somewhere else， but gets ma into somewhere else。

 right Most of the data has to move around。So let's say that n changes from three to four like this。

 so we had three machines and now we have four。Let's say before we were doing， no， MD5。诶。Ardva。

And we got one， right， and let's say that that put us on M2。Say these are indexed from zero。

Or I should say MD5 of ourbarrc modd 3。Maybe that gave us one before。

Now let's say I do a MD5 of ourberg。Moud 4。诶。And now let's say that I get three。 So now that key。

 which I already stored， now needs to move from this machine to this machine。 So our our。

So that seems kind of messed up， right， you know， actually let me give a different example。

 let's say it changed from one to two。This is what seems messed up to me。 We've added a new machine。

And now I'm saying that Avarc has to move from here to here。That seems kind of messed up。

 doesn't it because？If you add a new machine。Then it would make sense if you have to move things onto the new machine。

 right？Now I'm saying that because we've added a new machine。

 now I have to move something from an old machine to another old machine。

Instead of moving data to the new machine， I've just shifted around the data on the old machines and could that might have to happen with all of these。

 maybe some of them would move to the new machine sure。

 but maybe some of them would have to move from one of the old machines to the other old machine。

 so that seems bad right we really don't want to have to do that。So the drawback here。

Too much data movement。When N changes。In an ideal world。

 we would do the minimum amount of data movement necessary。So that raises another question。

 what is the minimum amount of data movement necessary if we want the data to be evenly split among the node？

So let's say that we have。Six keys like this， we have yeah， one， two， three， four， five， six。

So we have six keys。On three nodes， it's about two per node。

 Maybe they weren't perfectly evenly distributed before， but， you know， let's。

 let's suppose that they're more or less evenly distributed。

 So before we had six keys on three nodes， about two per node。

And say that we add one more node like this， say that we add M4。

 So now there's six keys and four nodes。So if we have six keys in four nodes。

How many keys per node do we have now on average？Or should we have。All right， let's think about it。

Four nodes， six keys。If you had the same number on each right， then well six divided by four is 1。

5 right so you can't have one and a half but。It would have to be either one or two。

 so we'd hope for either one or two。On every one of the four notes。So。On average， right？

You would want to move about that many。To this new node， you'd want to move about 1。

5 keys to this new node， you know， one or two， let's say one。So that's the minimum movement possible。

To achieve an even split。So to write this out。Let's say that we had something like this。

So we have our strings like。And this might not exactly match the sharding that I had before。

But that's okay。Okay， so those are our three nodes。Let's say that we add one node to the system。

So here's our brand new。Sparkling new node。With no data on it yet。

We want to move the minimum amount of data to it。To be rebalanced， right。

 So because we now have six keys。And four nodes。呃。We want to have about。1。5 cus per node。Okay。

So that means we should move one or two keys here。So let's say that we move this one。

That's about as good as a split as any other。 So that's the minimum movement possible to achieve and even split。

 So that was this particular example where we had six keys and four nodes， but in general。

If you have K keys and end nodes。Then that number， K divided by n。Is the minimum movement possible。

To get an even split。So we ought to be looking。For approaches that let us get that minimum possible movement。

At the point when N changes。We accomplish this using something called consistent hashing。

Gives us this minimum movement。So there's a lot of terminology overlap in distributed systems。

 unfortunately， so we're using this word consistent yet again。

We've already used this word in the context of consistency models。

And now we're using it to mean something entirely different。

 I'm sorry to say this is just an unfortunate terminology overlap in distributed systems literature。

It's a different concept， so this has to do with how you shard data。And how you move data。

When the number of nodes that you're sharding over changes。

So consistent hashing is an approach to sharding that will give you this really nice property。

 unlike what we saw before where you are partitioning by the hash of a key and taking mod in。

Consistent hashing gives us this nice minimum data movement。

So let's pause right here and do our quiz。And then when we come back。

 we'll talk about how consistent hashing works。

![](img/14bb71176e4ceef55264489b835a0d4d_1.png)

Right， so I will see you at 421。

![](img/14bb71176e4ceef55264489b835a0d4d_3.png)

Yes， that's right， I have a document camera， so the document camera is pointed at the paper and my laptop camera is pointed at me。

It I can share a link， the brand is IPvo。It's the IPvoVZR。And I like it a lot。嗯。

Let me find a link and share it。No， it's not very big。 It fits pretty nicely on the desk here。

 It's it's intended for。Home use。I don't remember where I got it。It could have been from Amazon。

I p Evo。Yeah， I just put a link on Zul here。It's a really nice thing。Yeah， it plugs in via USB。

 so it plugs into my laptop and。The USB powers it and also sends data。Yeah， it works pretty nicely。

 it's also got a light。嗯。I didn't have the light on before I should have had the light on。

 so it's got a light building。It's got some kind of cool settings， maybe I can show off later。嗯。Yeah。

 I love this thing， it's easy to use。I do go through a lot of paper， though。Yeah。

 I was thinking about getting， you can get like a。嗯。Sort of like a wipe and rewrite notebook。

 a wipebook， which I was thinking about getting。But if I'm back in the physical classroom in fall。

 then maybe I won't bother。Yeah。No， it's not very expensive。What is it about like 200 yeah？Okay。

Right， two minute warning。Oh， with the two cameras。 Yeah， so I'm I'm。诶。

For Zoom I'm just using my laptop camera and then I'm sharing my screen and I have。

 so I don't have it plugged into Zoom as a camera I'm using the software that comes with the dotcam。

 which is called visualizer， which puts up whatever is the current。

Whatever the camera is currently showing。And then I have I'm tabbing between that in a browser window here。

It's some。Yeah， I mean， I'd be happy to meet with you if you're interested in a little demo。Okay。

 it's 421， so let's resume。

![](img/14bb71176e4ceef55264489b835a0d4d_5.png)

Okay， so let's talk about consistent hashing and how that works。And once again。

 consistent hashing is rather confusingly named。I didn't pick the names of these things。ok。

So the idea with consistent hashing。Is that we can think of all of our nodes。

As being arranged in a ring。And you might recall this from the Dynamo paper。

And the points around this ring。Are going to correspond to the output space of our hash function。

So let's say that we have our nodes。Like this， let's say that this is M1。M to。M3。And4。

And so if this is zero up here。Maybe this is one。And so on around the ring。

And then coming if we're again saying that our hash function is MD5。It's got a 128 bit output right。

 so this would be like。All the way to。All the way to this very large number。So。

That's what we would have if we were using M5， but that's too big a number to think about。

 so let's pick something a little bit more manageable。Like two to the six。Which is 64。

So the ring will go from zero to。Two to the six minus1。Which is 63。

 I'll just write 63 that might be a little easier to think about。So maybe this is like 16 right here。

Maybe this here is 32。And this is 48。Yes。And every node is going to correspond to a particular point。

On the ring， so maybe M1 is it8。And maybe M2 is at 20。M3， I have it 32。And maybe M4 is at 47。

So each of our nodes is going to belong to a particular point on the ring。

I don't really care what point。And how do you decide which point it belongs to？

Maybe you could hash the name of the node using our hash function or hash the IP address of the node。

And if you do that， then the nodes will be more or less evenly spaced around the ring。

 at least you hope so。Okay， so now let's， let's say somebody wants to store some data。

 we've got all these nodes。 it's time to start using our key value store。

 So let's say that I want to store。A key， let's say that the key is Apple。

 or let's say that they want to write to the key apple。

I'll just worry about the key right now and not the value。

So how do I figure out which of these notes to put it on？I'll hash it just like before。

 so I'll take the hash。Of that key。And I'll get something that's in the output space of the hash function。

 so let's say that it's 14。We look at 0。14 on the ring， there's not a node there。

So what we do is we walk around the ring clockwise until we hit the first node， in this case it's M2。

So the key apple。And its value。Were going to get stored there。

So a key is going to belong on whichever server is the successor。

Of the point that that key hashes to。This means if somebody wants to look up the key。Same deal。

 you hash the key， you got a number。You walk around the circle， so here you would go to 14。

 let's say。You walk around the circle until you hit a node。

 and that's the place that you'll find the key that you wanted。And the circle wraps around。So。

Let's say that I hased the key artvarc， for instance。And one let's say that that hashes to 62。

So where will that key be stored？That's right， yep， it'll go on M1。So。In Dynamo。

They use consistent hashing in this way， but they also use this ring to decide where to replicate things。

So let's say everything has to be replicated three times， for example。

 then the way that they do it is for any key。It's going to have some node that is it home。

Which is whatever node that it hashes to using this approach of。Computing the hash of the key。

 finding a point on the ring and then walking around clockwise until you hit the first node。

 so this node M2 is going to be the home node of this key Apple。

So if every key had to be replicated three times， then you're going to store it there。

But you also store it at the note after that。And the note after that。And then AdVrc。

 this would be its home node， so it would go there。And here。You can spell hard bark。

So we're using the ring both。To figure out where to put things in the first place in terms of sharding and we're also using the ring to determine where to replicate things so in Dynamo they will replicate a key along with its value right so I've left the values that these keys mapped to out of the picture。

But values are there too， like the value of Apple might be something。

 the value of artwork work might be something and so on。

But the way that it works in Dynamo is that you store something at its home node。

 and then if the replication factor is 3， then you also store it at the node after that and the node after that until you've stored it in three places。

So it's slightly more complicated than that in Dynamo because。The paper calls it a preference list。

 so every node has what's called a preference list。

Which is the list of places where that node's data should be replicated to。And interestingly。

 theplication， the preference list is actually going to be longer than say three if three were the replication factor。

Does anybody remember why the preference list has to be longer？That's right， yeah。

 some replicas could be down so or unavailable for whatever reason， unreachable。

They still try to replicate in three places， even if one of the nodes where they're supposed to be replicating is down。

 and they just keep going down the preference list until they find three nodes that are actually up。

Okay， so why did we start talking about consistent hashing well we started talking about it in the first place because we wanted to solve this issue of data movement right we were trying to get some approach that would give us the minimum movement when we added or removed nodes。

And we wanted to make sure that we moved around as little data as necessary。

 and that magic number that I gave before， which was k over n。

 which is the number of keys divided by the number of nodes。

We figured out that that was the minimum movement that you would have to do to get an even split。

When you add a new node。So how does consistent hashing actually solve that？Well。

 let's add a new node to our ring， let's say that our nodes are getting pretty full。

 maybe maybe we're looking at our at what we have and we're looking at the data and things are like maybe I don't know。

 80% full so we're starting to think okay， we'll be better better add another node。So。

Let's call it M5。And let's say that it goes right here。

Let's say that it hashes to this position 60 right here。Now that we've added this new node。

Which keys？Do we have to move？What do you think？Yeah， okay。

 so I guess in this particular picture it might be none of them， but let's say in general。Let me say。

 for instance， that。The strings。Let's say that its hash value was。I don't know， 50。

So let's say that it hashed in right there。So what would have happened before M5 was present？

This string hashes to 50， and then we would have had to walk around the ring until we hit a note。

So what would have happened before is that。Everything that hash to anything in this whole。Range。

Would have landed on M1。That's what have happened before M5 entered the picture。

Now that M5 has entered the picture， though， now the range that M1 is responsible for is smaller。

 so now M5 is now only responsible for this。Or sorry， M1 is only responsible for this smaller range。

And M5 is going to be responsible for this。So anything that would have hashed to。嗯。To M1。

 because it fell in this space here。Between M5 and M4， anything that would have been on M1？

Now ought to be moved over to M5。So a chunk of the data that's on M1 now needs to go over here when。

When M5 gets added to the ring。Yes。But on average。It's only going to be。

About this much data that needs to move。On average。

 we'll only have to move k over and keys over where k is the total number of keys that are stored。

In this new system， and N is the new number of notes。And the really great thing about it is。

These notes。Aren't affected at all。So they don't have to do anything different， they can be， in fact。

 totally oblivious to all of this that's going on。So M4 doesn't have to care M3 doesn't have to care M2 doesn't have to care know maybe sooner or later M4 should update its preference list maybe to add M5 and so forth。

 that kind of thing and maybe some of the other ones have to update their preference list too。

 depending on the replication factor and that kind of thing。But they don't have to move any data。

Which is really great。So that's nice。Okay， what about if a node crashes？Suppose M2 goes away。

Suppose it crashes。Who is going to be affected by M2 crashing？Well， what was him too responsible for？

Well， it was responsible for this range， right？Remember how we talked about how Apple the hash of Apple was 14。

 and so we walked around the ring and then stored Apple here at M2。

So now anything that hash to a spot on the ring that was in this whole range here would have been stored on M2。

So。That's what 9 through 20。The 9 through20 range of the hash function so now。M2 is gone。So now。

M2s neighbor， M3 is going to have to take those keys on， right。

 So an M3 here has to take on some more keys。 M3 is now responsible for this。Big。Chunk of the rain。

So this used to be M2s。And this part just here used to be M3s。

 now M3 is responsible for a bigger chunk of the ring。However。

 now M4 and M5 and M1 are unaffected by that， so it's business as usual for these nodes over here。

Meanwhile， M3 has to take on the data that。That was。That M2 can no longer store。

 but this actually works really nicely because in Dynamo in particular。

 remember how we said these keys are being stored on a node that's their home node。

 but they're also being replicated onto its successors around the ring。 Well， if this node crashes。

And its successor node has to take over its key range will hopefully it has the backup already。

So now it can just say， okay， these keys are mine， I'm the home of these keys now。

 these keys live here now， I'm their home now。And of course， at this point。

 whoever is operating this system will probably want to bring another node up to replace that lost node。

But until they do， this neighbor node is going to be picking up the slackck。

And that's consistent hashing。Questions about this。Us， the question is。Is the home？

For these now M3 and would they need to be propagated to the next nodes， Yes。

 so one thing that you might do at this point if M2 has crashed。

M3 can hopefully figure out that M2 has crashed， maybe M3 is constantly trying to gossip with all of its neighbors right。

 so if M3 finds it it can't talk to M2。嗯。Now M3 decides， okay， I'll be the home for those now。

And I'll start my own。Preference list for replicating those。And so then。

Maybe its preference list has many nodes， maybe like we said more than three。

 because it has to be careful of the fact that some of those might be down。

It's going to try to talk to this one and this one， you know。

 maybe this one over here didn't have Apple yet， so maybe it will try to replicate to that one。

On the other hand， maybe M2 is only intermittently down， so maybe it'll come back。And then it'll say。

 okay， I'll take over this chunk。Of the of the ring again。

Can you think of any ways that consistent hashing might go wrong？

Let's use our last bit of time to talk about that。How could this go wrong， What could go badly？H。

 cascading crash is because of increased load。So you're imagining a scenario where like a node dies and that its neighbor has to take on the load that it was carrying and then because of increased load it dies。

 yeah， okay， yeah， so there had better be a system administrator who's keeping an eye on this ring。

 right？If they're starting to see a lot of crashes。

 then they'd better start working on bringing up some nodes， right？

There's definitely some human involvement here。It's somebody's job to monitor this system。

Try to maintain a。A global view of what's going on that these machines lack。Keeping us all employed。

 right？Okay， what else？What else could go wrong？Sure， yeah， like if a couple of nodes crash。

Then their neighbor has to take on that huge range， right？So yeah， it could happen。

Something you have to watch out for。That's a little bit related to thing I was going to talk about。

 which is。What if the nodes aren't actually evenly spaced around the ring？

So in this picture I have them fairly evenly spaced， right。

 especially now that I headed M5 to the picture。But。

You could imagine a scenario in which the nodes aren't evenly spaced。So， we know that a good。

Hash function is going to map its inputs over its output range as evenly as possible。

 So that's what makes a hash function。That's one of the things that makes a hash function good。

 right， We're hoping that even if the。Inputs are。Cluuttered up in particular parts of the input space。

 we're hoping that they're going to be mapped out in a hopefully fairly even。Way in the output space。

 however。If you have not that many inputs。Then you can't necessarily expect that outputs face to be evenly covered。

 right， The more inputs that there are。The more likely that it is that you'll get an even distribution。

So these key value pairs， you know， presumably you have a whole lot of key value pairs。

 if you didn't have a whole lot of key value pairs。

 you probably wouldn't be building a distributed system。But you certainly wouldn't be sharding。

So hopefully the key value pairs are more or less evenly distributed over the output space。

 but what about the these machines， what about these machine identifiers or whatever it is that you're using to hash them to points on the ring There aren't that many of those in this picture I only had five。

So you can't necessarily expect that output space to be evenly covered。

The more inputs that there are， the more likely it is that you'll get an even distribution though。

 so here's a trick that you can play。You can actually have every one of these。

Every one of these machines。Be hash to many points on the ring。

So a node could pretend to be multiple nodes。So node could pretend to be。

 say four nodes or 30 nodes or 80 nodes。And everyone would have its own identifier。

Which would then get hash to some position on the ring。

And that would make an even distribution more likely。So there's still only one machine M one。

We're pretending。That that M1 gets hash to a whole bunch of different points on the ring。

 so I'll use a different color。So here's like a fake M1。Here's another fake M1。

Here's another fake M1。Here's another fake M1。Here's another one。

And similarly for all of the other ones。This will make it more likely that we've evenly distributed the nodes around the ring。

These。However， many fake machines that we have here。Are called virtual nodes。

So what's the purpose of virtual nodes？They make it so that you're more likely to have an even distribution of nodes around the ring。

And。That's nice， because。If you don't have an even distribution of nodes around the ring。

 then assuming your key values that your keys are getting more or less evenly hasshed around the ring。

Then some nodes are going to end up with a lot more than others。

So you want to make it more likely that your nodes are evenly distributed around the ring two and virtual nodes help with that by just having there be more nodes。

Now， these are all actually one machine。But。They're thought to be at different points on the ring so that here。

If I were to I were to， let's see that this M1 right here where it， I don't know， 24。嗯。

If I were to have。A key。Safu。That hashes to right here， so say it hashes to 23。

Then I would walk her around the ring to get to 24。

 and then it would then this key would actually get stored on machine  one。Of course。

 with this setup here where I have a bunch of M1s and only one each of the others。

 then that wouldn't be good， but the idea is that you would have virtual nodes set up for all of your machines。

You would be。Spreading the nodes out over the space around the ring in a way that would hopefully avoid huge gaps。

So virtual nodes are nice because they improve the distribution of nodes on the ring。

And there's actually another reason I can think of why they're nice。

 and this is something that's mentioned in the dynamo paper。

Does anybody know what else is nice about virtual nodes？Well。

 let's say that you have one of these machines。M1。And let's say that it has like a 10 terabyte drive。

And let's say that you have M2。E it only has a four。Terabyte drive。What can you do about that？

At that point， you don't want。The same number of Qs to be stored on M2 as M1 do you because then。

You'll run out of storage space on M2 more quickly。It turns out virtual notess can help with this。

If you're using virtual nodes， then you can give different numbers of virtual nodes to these machines。

Maybe this machine with the four terabyte drive。Only has 20 virtual notes。

And then this one with a 10 TV drive has 50 virtual notes， so the machines that have more capacity。

Can then be responsible for some larger slice of this space of keys。So those。

20 virtual nodes that map onto to M2 would then be scattered around the ring somehow。

 those 50 virtual nodes that correspond M1 would be scattered around the ring somehow and then。

Assuming that keys are more or less evenly distributed around the ring。

 then hopefully you would get about the right amount of data corresponding to the storage capacity on those machines。

Virtual nodes can let you。Have different numbers of virtual nodes per physical node。

So you can account for differences in storage capacity。So that's kind of cool。Allright。😊。

In the few minutes that we have left， do you see any downside to this idea of using virtual notes？

I can think of one thing that。You could maybe think of as a bug or maybe think of as a feature。

So one downside is that if you're using virtual node， let's say that M1 goes down。

 Let's say the physical M1 goes down then。Before it was kind of easy to think about what happened。

 if a node crashed， then its neighbor has to take over。For it's part of the key range。

 so it's pretty straightforward。But。If M1 goes down and you're using virtual nodes。

Then all the virtual nodes are going to be down too。

 so now there's lots of little places around the ring that are going to be affected。

If a physical node that's represented by many of these virtual nodes crashes。

 then lots of separate little areas on the ring are going to be affected。

And they're all going to have their own neighbors， right and then so lots of other nodes might have to step up to be responsible for those parts of the ring。

So in the Dynamo paper， they actually call this a feature。 they say if the node dies。

 then rather than just having its immediate neighbor take it on， then the load is spread out。

 So this sort of answers that one of the questions that we were talking about earlier right when we were saying。

 wouldnn't it be terrible if nodes right next to each other on their ring crashed and then then this whole space ends up having to go on the immediately neighboring physical node。

 Well， if you're using virtual nodes， then things are a little bit different then everybody can help kind of step in and pick up some of the。

Some of the work。So in the Dynamo paper they say this is good right。

 it's good to have this load spread out， and I can see why that would make sense。

The only thing I don't like about this is that it's a little bit less simple and obvious what's supposed to happen if a node dies and you don't get the nice situation we had before where the other nodes could just kind of go on you know doing their thing obliviously。

 but we still have this nice property there's still this minimal data movement。

 it's just that the data movement happens between more of the machines。

And then the only other downside I can think of of virtual nodes is that。

Replicationation might get a little more complicated。

 right because you want to make sure not to replicate to two virtual nodes that are actually the same physical node。

 so you have to think a little bit harder about who to replicate to。

Because that wouldn't give you any fault tolerance right， if you replicated to two virtual nodes。

 but they're actually the same machine， then if that one machine crashes， then you lose both copies。

So that's what virtual nodes are。And implementations of this kind of thing in practice typically do use virtual nodes。

 and this is discussed in a little bit more detail in the Dynamo paper if you're interested in taking a look。

 the questions of like how many virtual nodes you need。

 these are tunening questions that you might answer based on the characteristics of your system。

All right， in the one minute left， I want to remind you all that B B con is happening。

So I've talked about this before， but Bing Bang Con is the conference that some friends and I run。

 it's happening right now， In fact， our next session is starting in five minutes so and you can go to Bing B。

 co slash live stream to watch the talks it's free and I hope that some of you will take the time to check it out I know that a couple of you already have which is awesome So if you have an hour and you want to hear some cool talks about the joy excitementt and surprise of computing go take a look。

Otherwise， I'll see you next week， enjoy your weekend。

