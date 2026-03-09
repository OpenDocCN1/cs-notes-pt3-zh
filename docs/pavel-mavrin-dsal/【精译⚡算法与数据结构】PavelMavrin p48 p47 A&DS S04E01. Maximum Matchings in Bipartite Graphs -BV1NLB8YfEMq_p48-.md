# 【精译⚡算法与数据结构】PavelMavrin p48 p47 A&DS S04E01. Maximum Matchings in Bipartite Graphs -BV1NLB8YfEMq_p48-

🎼。

![](img/b2d058593121540843713b98cda4bf6e_1.png)

![](img/b2d058593121540843713b98cda4bf6e_2.png)

🎼So in this semester， we'll mostly talk about。Mas and never clothes。

And we start this semester talking about bipartite machine。



![](img/b2d058593121540843713b98cda4bf6e_4.png)

Mos。

![](img/b2d058593121540843713b98cda4bf6e_6.png)

M it chis。是的。

![](img/b2d058593121540843713b98cda4bf6e_8.png)

So what is it， The problem is very simple。 You have a graph。



![](img/b2d058593121540843713b98cda4bf6e_10.png)

![](img/b2d058593121540843713b98cda4bf6e_11.png)

Let's say something like， something like that。So you have some undirected glove。

And the matching is basically the set of edges such that no two edge share the same verex。

 so we need to mark some edges。

![](img/b2d058593121540843713b98cda4bf6e_13.png)

And all these edges must have different endpoint。For example， we can take， I don't know。我前对个。

Let's say。This age。 and this age。

![](img/b2d058593121540843713b98cda4bf6e_15.png)

![](img/b2d058593121540843713b98cda4bf6e_16.png)

So these two edges。For my machine。 again， we picked some edges and this edges must haves different end points。

And the problem we will solve in this。Lecture will be to find the maximum matching so the maximum matching is just the matching of the maximum number of edges。

 so we want to pick the maximum number of edges such as no to edge share the same endpoint。



![](img/b2d058593121540843713b98cda4bf6e_18.png)

Very simple。For example， this matching has size two， but we can make matching of size free。

 for example， if we remove this edge。And Mark， least with edge。



![](img/b2d058593121540843713b98cda4bf6e_20.png)

So this is the maximum mention。For this girl。Sometimes we have a matchingqui mar。

 which contain all the vers， so we have matchings of size and over2。Like in this case。

 if the machine contains all the nodes of the graphic， it recalls the perfect mention。

Not very important， but if you see the。啊。交了。Perfect matching。

 It means that it is a matching of size n overto， so it contains all the nodes of your graph。No。

There are two types of this problem， one problem is for bipartid graph and another problem is for known by background graph。

 for example， this graph is known bypartid。

![](img/b2d058593121540843713b98cda4bf6e_22.png)

And if you have bipartgraph， you can have the same problem。 So bipart。



![](img/b2d058593121540843713b98cda4bf6e_24.png)

![](img/b2d058593121540843713b98cda4bf6e_25.png)

You have。So you know this are split into two parts。 you have left part and right part。



![](img/b2d058593121540843713b98cda4bf6e_27.png)

And you only have edges between these two parts。

![](img/b2d058593121540843713b98cda4bf6e_29.png)

And in we photographgraph it's the same problem， we need to pick some number of edges。

 maxim number of edges such that all these edges do not sure the endpoints for example。

 we can pick this stage and this stage。

![](img/b2d058593121540843713b98cda4bf6e_31.png)

![](img/b2d058593121540843713b98cda4bf6e_32.png)

So I like it。One more。 so let's speak one more。

![](img/b2d058593121540843713b98cda4bf6e_34.png)

Mmhhum。That's all， Bi problem。啊。There is a big difference between bipartgraph and non bipartgraphs。

 This difference is actually quite fundamental。We will talk about this difference later and course。

 when we talk about linear programming and stuff。 So if you look at the linear program responding to this problem。

It's actually。Quite different for bipartgraph in and phenomenon bypartagraph。

 So the algorithm for solving this problem is very different。 Today。

 we' will talk only about bipartgraphs。So we'll only solve the problem of finding the maximum matching for bipartgraphs。

Do both the points need to be different。

![](img/b2d058593121540843713b98cda4bf6e_36.png)

For two different ends， yes， all all end points must be different。啊。Here is the important thing。

 I interesting。Okay， let's see one piece。That be since。Yeah， like this。H。

 and now we can pick this edge。

![](img/b2d058593121540843713b98cda4bf6e_38.png)

平常。哎，那 was。이거？So how the algorithms， how the basically all the algorithms will discuss in this course will look some。

 some like this。We will start from the empty matching。 So first， we'll pick no edges。

 empty matching is is correct matching， right， If you have no edges， then no edges shut the endpoint。



![](img/b2d058593121540843713b98cda4bf6e_40.png)

And after this， we will add edges one by one。We will add edges by finding there something which called ouring path。



![](img/b2d058593121540843713b98cda4bf6e_42.png)

嗯。Did they spill a tro？Nothing can sure。Yeah， I think so。So what is our making path？Yes。

 we'll talk about cool algorithm itemss in in in just。In just a minute。

So what is the argument in bed， it is a pair which looks like this。So we will find the path。

Such that first and last vers of this path are not used in the machine。 For example， in this graph。

 we have these two。These two notes。Are not used in the machine。In this graph， we use all the nodes。

 so let's change it these。すごす。Let's move back。といすか。Y。For example， in this graph。

 we have these two notes。 these two notes。free。So this。This nose doesn't belong to any age。

 which is in our current machine。So our mating path must have both ends in this free set。

 So both ends of this path must be free。In how much。Now。The edges of this path must alternate。

 so the first edge is not under matching the second path。I。In damaging。

 this edge is not used the imaging。 This edge is used in the， and so on。

So we want to find the alternating path with both ends。Not used in the machine。嗯哼。😊。

That'est the plan。So now what we do when we find the path like this。

 how can we increase the size of our current machine。It was a question。 Yes。

 it's supposed to answer the questions。嗯。Yes， what we do is basically in reverse this path。

 so we remove all these edges from matching and add these edges to the matching so we move from this state。

Do this day。When we make the separation， the size of the machine will be increased by one。

So here we have two edges in the。 Here we have three edges in the machine。That's all。

 That's the whole algorithm。 The whole algorithm looks like this。 We start from the empty matching。

And then we try to increase the size of the machine。

 We increase the size of the machine by finding a weighting path。When we find theing path。

We invert all this state of all edges on this path。And get the mention of size， plus  one。

For example， let's see， for example， in this graph， let's find the augmenting path， for example。

 in this graph， the augmenting path will look like this。So we can take this path。



![](img/b2d058593121540843713b98cda4bf6e_44.png)

So this is the oring path。We can invert the state of these three edges and increase the size of the machine by one。

嗯哼。So how to start the algorithm， something is very simple， so when you start the algorithm。

 you have the empty matching， so in the beginning you have something like this。

So all nodes of the graph are free of dimension。So how to fast the first how to find the first augmenting be。

 The first augmenting be is simply one edge， so every edge is the augmenting be of itself right。

 So if you put any edge。It is the correct or path， so the ends of this path are free and all the edges are alternate so so so but it's only one edge。

 so it's free。So you state。Any inch。Inward this age。Like this。这哪个有牌子？Now， you have mention of size 1。

Now you have mention of size 1。 You want to have mention of size 2。 What you do。

 You try to find augmenting path。 So you find augmenting pair， for example， like this。

 So you find this again， augmenting path。 You invert all the edges on this pen。

So now you have this page。 You don't have this edge， and you have this age。Now。

 you have matching of size， too。And so on。 So each time you find an augmenting path。

 increase the size of the machine。What's interesting， had you？

The interesting idea is that if you don't have augmenting paths。

 it means your mention is the maximum one， let's prove this。So， we prove that。If it is no。

How make impact。Please is the maximum as much。The size the size of your is maximable possible。

Let's prove this。嗯。No， okay， let's put more。First， let's move from right to left。

So if your mention is maximum possible， then you have no augment in paths。

This is just the size of the matching Yeah I just so M is the matching。It's like the set of edges。

 so this is there。Like the size of this set。Oh， let's see。So if you mention is the maximum one。

Then you have no augmenting paths。Now whyhy is it true， Because if you have augmentm path。

 then you can increase the size of the machine。 It means your machine is not the maximum one。

So from right to left， it's actually pretty obvious。你。Clear enough。Again。

 if you mention is is the maximum one。It means you cannot increase it。But if you have a bath。

 you can increase it。Yeah， so if your， if your machine is maximum1， then there is no augment paths。

Now from left to right。LetThat's more interesting。啊。Let's prove that if we know。

 if we don't have any augmenting paths。Then our mention is maximal。 Again。

 let's prove it by by contradiction。 So let's say that。We have no admitting pads。By。

Our machine is not maximum。对。Let's see。 So we have our mention F and it is not much small。

Then there is some other matching， which is much。So there exists I M marks。Yeah。

 and the size of this maximumim is more than the size of the。Right。No。

Let's take a look on both these matchings in the same graph。

 So let's draw both these matchings in the ground。 So let's mark all the edges of。

Matching M withve red。And mark all the edges in a mark with blue。Now words。

 let's remove all the edges from the graph， except the edges which belongs to M or to M maxs。Mhm。😊。

What will happen。So again， what do what do we do。We' take the gr。Draw two machiness。

Draw matching M and matching Mbox。M with red and match with blue。And now remove all other edges。

 which doesn't belong to M or Mx。Yeah， we can also remove the edges which belong to both M and max and it's not that important。

 yes， let's remove the edges which belong to both M and maxs。Just for simplicity。そう。

We only left the edges which belongs to M， but not M maxs and edges to belong M marks， but not M。Now。

 what we have left， let's look at any。Note of algorithmgraph。For each note of our graph。

 we may have at most two edges connected to this country。 So we may have at at at most one。Blue edge。

 and at most one， red edge。So the degree of each node in our graph is at most。Right。

What you can tell about the graph which have degree of each node at most2。

 so the degree of each node is one or two， how does this graph looks like？到时。Yeah。

 it may contain only these cycles and chains。そう。So if you have cycle， So let's look at the cycle。So。

 let's have some cycle。If you have a cycle， then the colors of the edges must alternate yeah。

So you have these edges red and not this this edges red。And these edges bloom。Now。

 let's see if you have acycl， then the number of blue and red edges is the same。Yeah。

If you have the cycle。Yeah， so it the size of the cycle must be even。

And the number of blue and red edges is the same。嗯哼。

But we know that the size of this M mark is larger than the size M。

So the number of blue edges is actually larger than the the number of red edges。

So there must be some component， which has more blue nodes， blue edges than red edges。

How does this component looks like？No， it must look like this。 It must be a chain。Very good。

 like piece。Such that the first。And the last edge of this chain are blue。You once again。

 the size of M max。Is more than the size of this M。Yep。So there must。

 there must be at least one component which has more blue edges than red edges。

This component should like should look like this because we only have cycles and cycles and chains。

So for each cycle， the number of blue and red edges is the same， so that must be a path。

Such that the first and last edges of this pet a。那。Now。

 it's quite easy to see that this path is actually augmenting both path for the red。Mction。

So this path is augmenting。4 m。No really。 So the first and last notess of this path are not used in the red matchings。

R mention because we don't have any red edges。from here。So the first and last。Notes。

Are not used in red matching。And the state of these edges is actually alternating， so wind。

We use these two edges in the red machine， but we don't use these three edges in the red machine。

 So this path is actually a graing path in in the red matching。没 all。It means if， if。

 if our machine is not max maximum， then we must have an。O major bath。再爽。Okay。

 that's the whole theory behind this。So again， how we find the maximum machine。

 we make a empty matching and then we try to find our mating pathth if we found o mating pathth we increased the size of the。

 if we don't find any o path it means that our current matching is the maximum one down that's all。

Okay， now the tricky question， how I use that my graph is pipepartid in this proof？

I promise you the algorithm for byparttographs。Cycle is even because the colors are alternating。

So it' actually true not only for bypartgraph。 So in by paragraphgraph， all cycles are even。 yeah。

 but even if you have non by photographtograph， this cycle will。

Have even length because the colors of these edges must alternate so。The answer is I didn't use it。

So this proof is correct for non byparttagraph as well。So for none by paragraphgraphs。

 we will use basically the same algorithm， we will start from empty matching and then find try to find alternating pes one by one until we find the maximum matching。

傻的。This scheme results can be used for non by pathgraphs as well。

The only trick is how to find these augmenting path。 It， it turns out that in。Bypartse graphs。

 it's much easier to find out paths。If you have non bipartgraph。

 there is some problem how to find augmenting path， even if you have one。啊。

We discuss this problem in the next lecture， and today we'll talk only in Vira。So again。

 this algorithm is the same for non bibater rep than for bipartttergraphs。

The only difference is the algorithm which finds the augmenting path。It turns out for bipygraphs。

 it's much easier to find augmenting pass。Yes， we' will talk about max flows and few lectures。Not to。

You don't need to know network plug to actually solve matching problems。啊。Let's go。So， how to find。

Our be in bypartagraph。 Oh， let's see you know。 here we have a nice bi photographgraph。

So how the augmenting paths looks in bipartital graphs。 So if you have a bipartagraph。

Then augmenting path looks like this。So， you' start from。Some。AFree note in the left side。

 for example， of your graph。And now you need to take alternating jobs。 So you go to the right half。

Using。The edge， which is not in dimension。And now you go to the left part。

Using the edge from the machine。Now， this node may not be free note。

 right because we have this edge in dimension machine。No， again。

 this augmenting path or always have odd size。 so we cannot stop。 So if we start in the left part。

 we must end in the right part。So we go to the right using free edge， then go to the left。

Using some edge from the machine。那我。Again， we go to the right。Over to the left。こない。

AndPlease stage for。Until we finally find this。So the outbreaking path in the bibatter graph looks always like this。

How can we use this？Let's see， we。Go to the right。哦。Only when we have the mode。

 which is not in the machine。And we go to the left， only using the node from the matching。

So let's outient our。It just so， let's orient all the。

Ages north in the machine from left to right and all the edges from the machine from right to left。

Shes go。So we areient this edge from left to right， Arient this edge from right to left。

This stage here。This image here。 This stitch here。嗯。Okay。Now we'll have a director graph。

what's cool about this Now we don't need to care about if the edge is in the machine or not。

So the direction of the edge actually defines the state of the edge。So these edges go to live。ちくちく。

Now in this graph， we just need to find any path from one freerenn node to another freerenn。So again。

 we now we don't care about the state of the edges， if the edges in the machine or not。

 We just look at the direction of this edge。If the direction is right， then our path will be right。

 for example， let's find some。Do we have any。어 응。We don't have any augment person on this graph。

 right。Let's get something。 So let's add， for example， this edge。嗯哼。

So now we can find this path so we can go here， then here， then here。So this is the augmenting pad。

So again， what we did。We add this direction to each。 So each edge now has direction。

 If the edge is not in the machine， we pointient from left to right。 If it is in the machine。

 we drive from from right to left。And now we just need to find the path。

From one free node to another freen。We know how to find pets in graph。We just spent whole semester。

Talking about graphs。 So how to find a pair from here to here。

 you can use depth search or path search。Basically any paths for finding algorithm will work。

 so let's run， for example， DFS so we we take this free node of the left in the left part and run DFS algorithm if this DFS algorithm will find any node in the right free node in the right part of the graph。

Then we'll find the augmenting path because each path from one f node to another f node is augmenting。

Mh哼。😊，Now， what if we have several free notes？So what if what if you have several freenos here？

And several three notes here。Now we want to find a pair。

From one of these node to one of these notess。we can run simply we can simply run DFs from all these node so we can era all three nodes of the left part and rather DFs from each one of them individually。

 but it can be done even simple so we can what we can do， we can introduce one external node here。

Let's go with this。Connected to all three node of the left part。

And then introduce one node here and connect all the node here。And now in this graph。

 you just need to find any pair from S to T。 So if you if you take any pair from S to T。

 it will looks like this。 So it will go to some three node of the left part then。

It will go something like this。So you have this auto mattting path。

From this print node to this re node， And then we willll go to T。So in this graph。

 you just need to run DFFs from S。Find any path from S to T。 If you have a path from S to T。

 then here you will have the augmenting path。 Then you invert this augmenting path and continue again。

뭐 응。Yes， let's like multi source interface。Yeah， we discussed it in the previous semester shortly。

Re team。Yes， you can do。 Yes， you can use DFS or B FS Does matter。 It will not affect the complexity。

So let's talk about time complexity。What is the time of for this algorithm。

We see each time you run a TFS， time complexity of TFS。E is the O of M When M is the number of edges。

 right。And how many times you need to run DFS algorithm， actually。

 you run DFS each time you either find the augmenting path。Or you don't find on mattting path。

 If you don't find on mattting path， it means that your mention is fine。 It is maximum。 So just stop。

If you find the augment parameter， you increase the size of your matching。

The size of the is at most n because you have n nodes here， right？

The number of ages in the machine can be more than n。So you run the F at most n times。

 so the total time complexity will be。And multiplied by M。嗯。That's all。It's called theこのア。呼和乐色 al。

We will actually improve it a little bit， but。The main idea is this， Very simple。Can we do it faster。

 actually we can。We will discuss all。 which find there。

Maxim matching in bypartgraph faster than end end time。 but not today。

 we need some more theory about network clothes and stuff。 So we'll。

 we'll discuss some network close algorithm。 And when we learn some first network close algorithm。

 we will go back。To matching problem end。Will find better algorithm for。Bypartite machine。

 but it will be in。In a month， I think。嗯。Yeah， yeah， there are a lot of goods。Eistics。

 which actually can improve this。 For example Yes， if you just randomly shuffle all the edges and just start in random order。

 try to find all the edges in random， then most of the time。

 you will add a lot of edges to your machine。Can actually prove that， if you have。

If you just greaizzily add edges  one by one， then you will add about half of the edges from the maximal matching。

 It's not that important。 but yeah， actually， there are some。Cool heuristics。

 which can make the salad faster， but again， in the worst case。

 it will still work on anM time so you can build a bad taste for each heuristics。

Which will make your object work on an time。Yeah， but。

 but there are there are a few improvements you're can make。Now， let's。

 let's actually write the code。So how to implement this algorithm。

 the easiest way to implement this algorithm is following so what I will do， I will run an DFS。

 so you can implement it like like just like we discussed so can you can extend your graph with this tool notes。

 build this direct graph around DFS， find this outing path。

Inverse all the edges in this augmenting path and so on。 you can do it just like that。

 time complex will be like。But it's just， just too complicated。 the right just。

Much easier way to implement this algorithm。 You can do it like this， so。What we'll do？

We will not build this graphics display claim。We will just take the initial graph。

 So we take this graph and try to use it。So how will run DFs？So imagine you you。

 you run D first from some note of your graph。 So let's take some note in the left part top No view。

So note v is some note in the left part。And you run， dear fresh from this note。

So what happens when you' on DFS are written from this note， youll try to it all outgoing edges。

 So let's take some outgoing edge like this book， it's a deal。Now， what happens next？Let's see。

 this not you。May be free or it may be used in the machine。 So if it not this free。Yeah。

Then you just stop your DF， right， then if you find this free now， you stop your D first。

 you find you found the augmenting path。If this note is not free。The van。

You must take the next edge you you will take is the edge which connected to this node。

There is only one edge connected to this audio。It is the edge from the machine。

 which connects to audio view。 There's only one such page。So。

We just take this edge because we have only one edge。嗯 哼。And go to this note。

Let's put it in some array。 Let's say for note you。The edge from the machine。

Which response to no you is actually connected to load C P of you。So P of U is the node。

 which is connected to node U in the machine。嗯哼哼嗯。Why is guarantee doing No， no， no。

 it's not guaranteed。 So we we will if the node is not free。

Then there is one edge from the machine connected to this now。And it's only one。

Because it the mention。So if we go to the node， which is in the machine。

 then the next step will be to this node。 So we have only one possible。

 we have only one outgoing edge from this node。So for each。

 for each node in the right part of the graph， you have only one outgoing edge。

I is the edge from dimension。So what we'll do， we will run DFS like two step DFS。

 so we will start in the left part。So we will start the first from this note。

Now we will go here and then immediately go here and run the FS from this node。

 So we only run the FS from the node from the left side。That's the whole idea。I also is from。D F。

 S of V。So we will iterate all edges， then go here。 And then if this node is occupied， then go here。

And Ram difference from here， rely。Thats the idea。Now， the second idea is actually。like this。

So what we need to do， we need to find our main path and then inver it。

We can do this in the same D F S。So when you're on D first？

What happens if you reach this free node part， it means that in this stack of your DFS。

 so there is a stack of DFS yes， so you go from here， now you go from here， you go from here。

 you go from here。So there was some starting note。So you start D from here。

And this is your current state。 So all these previous states are in in the stack of your DFS。

We can just in them when we go back from the recurs。 So if we find this。Free note。

 then we go back from the re。And in the path when we go back。It will again it。

 it will simplify the algorithm because we don't have these two steps。We can do it like this。

 We can find this path。Put this preference to some array。

 then each error edge in this array invert the state of all the edges， but it's too complicated。

 We can do it in in one thing。嗯哼。So again， what， what will this D F do。

 This D Fs will start from the node V。It will try to find the augmenting path starting from this note。

If it succeed， then it will invert。The path from this video to the free node。

 and then you go back and inverse the edges。On the way back。Sos like that。诶，cle呢。Let's see。

So how is difference function will look like so it will look on bored。

This bulloleion is true if this DFS actually succeeded。 So if it。

 if this DFS found the path to some some augmenting pass。

 or it's found some path to the free node in in the right part。呃， then兔胜出。

Oh I would see now we simply have should run the DFS。 So how to run the。 so say if。If it's smart。

Then return John falls。Lmark。This like the usual defense。Then we do this thing。

 So we iterate over edges。 Let's see you from。フロ。Let's say G of。F like this。

So these are edges going from Norway。Now， we take this note to you。 So if。This U is free。

 So if this U is not in the matching， how we' see not in the matching。

 we will say that P of U is actually empty。So if P of U is empty。

It means this node is not in dimension right now。Who knows the steroid。No， we actually don't need to。

We don't need to remember about left notes。 actually， Are they dimension or not。

We only need to have pointers from right to left， because one use them in December。

We never use this point to go from here to here。 We always go from right to left。

 So we only need to have points from right to left。So if he is not used， then。

Then we found the augmenting P， so we go through here and we found the augment path now we need to inverse this edge to inverse this edge。

 we just need to add this edge to the。So again， we now we will go back and reverse this path。

 So we start from this edge。 We need to reverse this edge。 This edge must belong to the matching。

 So to put this edge to the matching， we just need to say that P of U equal to。And jump。No。

If it's not free， then we do this trick。 So we go to you and then go to P U and run theest here regard。

If this the returns true， it means that this the found。This pathth。

Already inverted this part of this path。And now we need to go back here and inverse these edges。

So we need to mark these edges not in the machine and this edge。But this edge must be in dimension。

 So we need to have。啊。best all we need to have is to change P of U。

 So we'll change P of U from this node to this node。

It will make this edge belong to them matching and this is the the dimension。

So we just begin see I will do the same thing。嗯。You may see that we have the same thing here so you can unite these two person into single E statement。

 right， so you can say if P of u equal to man or theFs of P。YouYou can simplify this。 I will not。Now。

 if we tried all edges and didn't find our mat in pair， we just returned falses。嗯哼。That's all。

 But that's the whole difference affair for finding the or paths。Thanks。Okay， now the final trick。

 the final trick is the following， so how to use this DFS， we can do it like this。

 we can what we need to do。In each generation， we need to run DFs from all。3 nodes of the left part。

 So we need to era all nodes of the left part。 try to run DFS from all these nodes。

 If at least one of these DFS is succeeded， then we increase the matching and continue again。

But we can do it even simple so what we can do。不지。What let's take some note。Its more work here。

Some space。Let's take some northern left button。그냥 보。Let's take some free note and left part。

And round differ from this node。D F S， yeah。What will happen？So if this difference succeeded。

 So if this difference friend find some augmenting path。Then。We will in this path。

And this note will no longer be free。嗯。So if we on first from some free note of the left part。

And these difference first found on our mattting path。Then it will invert this augment path。

This note will no longer be free。嗯哼。😊，And it will always the same。

 So if some node belongs to the matching， it will always belong to the matching。

Because the algorithm works like this So if。If you mark some node。

 So if some node is now in the machine， it will always be in the machine because in each duration。

 we just increase the set of the of the nodes in the machine。Great。So again， again， again。

 what is my idea， I is if youre on DFS。And this day first found the augment path。

Then you you no longer need this note。restaurant。Right。Because it will no longer be free。

And we run the effects only from the three notes of the left part。嗯哼。Second observation。

If you on the and this device didn't find any。Fre notes and electron or U V。 So you run D FS。

 and it fails。 It didn't find any augmenting paths。 It means you have some。Fre notes here。

But these free notes are not reachable from this node。

Now let's look look at the set of all reachable nodes from this。 So you start D from here。

 you will reach some node。 So you go here， then go here， then go here， then go here and so on。So。

 there is a set of。Rationable notes。So these notes are reachable from the starting note。嗯。

But all these free notes are not reachable。Yeah。Is the observation。

These notes will no longer be used in any ouring paths。Why is it true。Because from this note。

We cannot reach these free node of the right part。So again。

 if this free node was reachable from one of these nodes in this green set。

Then they also will be reachable from this starting node because all these nodes are reachable from starting nodes。

So if we can reach from here to here， we can reach from starting note to here。嗯哼。Now， if this node。

 from this node， we can reach the free node of the right party pin。

 we can't use these nodes in any augmenting PEs because in augmenting paths。

 all nodes of the augmenting PE from each node of augmenting path。Our main best looks like this。

And this is， and this is the preno。So you can reach。

The free note of the right part from any note of your augment path。

So if you can reach from these nodes any free node of the right part。

 it means they can't be using any augmenting beds。嗯。

What does mean it means you will never find any augment paths from this note。😡。

So if you run DFS from some free note of the left part and didn't find our mat path。

You no longer need to find。 You try to try to find our back from this note。

So if you run DFS and it fails。You no longer need to run the affair again。B quality year。

So this idea will simply fire that algorithm， how that algorithm will we will go from we will start for another from all nodes of the left part。

So， we'll just iterate。For all nodes from the left one。And try to right around this difference。

So to the de first， let's raise all the marks， let's feel。Marx。We false。And we' on difference。

Likeite piece。 That's all。Again got a very simple idea。 Again。

 we tried to run the first from all nodes of the left part， one by one。If we succeed。

 we increase the by one。 And this node is no longer free。 So we don't need to round the F again。

If we fail， it means we don't need this note。 This note will will never be in using any augmenting paths。

So we just keep it。So again， we take each node one by one。

 and we either find our meeting be or not if we don't find our meeting be。

 we just keep this note ends with the all。L is the left part of this so let's see this part is L。

This part。And yeah， yeah， true。It's actually a little bit more complicated。 The graph is changing。

 Yeah， so when you find augmenting path， you actually flip all the edges in this path and the graph is slightly changed。

 So maybe if you don't have augmenting path now， you will have it you will have it after some changes。

 You actually not because the graph only changes in the augmenting paths。

 Only augmenting path is changing Not not the whole graph is changing only there's。

Part of the graph in in our mat bath。But since these nodes can be used in augmenting paths。

 this part of the graph will never change。So you can reach from here to any free north flu part and this part will actually never change because you only change augment mating paths and this part will no never be in any augment path。

一错。So this is the whole code of the cool algorithm。I believe you can implement just like this。

 And it whole work。 clear enough。What's here？I want to prove one theorem， just。

I don't know why it runs。It's quite a highly important theoretical， but it's one of them。

There's one important theorem in this theory is called the whole theorem。

 so the whole theorem sounds like this on。There is a simple。네 twelve。

The simple thermo which allows you to check if your graph actually contain the perfect machine。

稍微自一个害。We have a graph。 We have end notess here， and end notess here。

And we want to check if our graph has a perfect machine。

So I want to check if the size of the maximum matching is actually and。Okay。

 so the theorem is with them。You have the perfect machine， if and only if。The following concern。

 So you have。Let's take any subset of the notes in the left part，s。

Let's pick some subset of the notes in the left part of the。Sa a。Now。

 let's find all the notes in the right part connected to this set date。

So we have some edges to here and here。こ水ひ。And also。So let's say this set is n of a。

It's like the set of all neighbors of the notess in a set a。The theorem is very simple。

 you have the perfect mention， even on the if for each set a， the size of this set of neighbors。

Is at least the size of the third a。Then and on。Size of maximum mention。M。你食啊。4。H age。

So if for for each set in the left part， the size of this settles its neighbors is at least the size of this set。

Then we have the perfect mission。Yeah。嗯。Okay， let's go from right to lift。

So if we have a perfect measure。Then the size of this M must be at least the size of a。

Why is it true， Well it's pretty simple。 We have a graphic machine。 So we take the size。

 we take the set A。嗯。Yes， you can the question is you cant implement this。 Yeah。

 you can check it first。 That's， that's true。 Usually， you usually you， you。

 you use this film from other answer。 So you， you kind of。

You can use your perfect your maximum matching algorithm to solve something like this。

We will do it in the practice。So yes， you only can check。Let's stop here for a second。

 There are two cases you can use this here the first case is when you have some special graph。

 sometimes you have some very special graph。And in this special graph。You can check this。this the。

 but you。Cannot find the maximum matching first。 So sorry if you just run the k algorithm this is in this graph because because it's very special。

 it will run too too slow。 it's usually's it's not built explicitly。

 It's just just some implicit graph。 Yeah， with some special structure。

So you can run just simply run the cornerography。But you can check this。side of the the whole the。

And it will be faster than just to finding their perfect matching。Another way to。

 when you use the whole the is something that you， you need to solve。

Some problem which looks kind of like that， we will do it in practice。And to do this， you instead。

 you try to find the maximum matching。嗯。😊，And then from this maxim matching。

 go back to your problem and try to solve it。hold不起流浪。We need examples for this。

 but we' will do it in practice not today。Now again， let's my back to the proof。

 So if the maxim matching have size n， so if you have perfect matching。Then for each set A。

 the size of the neighbors must be at least a， Why is it true since you have perfect matching？

So for each node in the a。You have some edge from the machine。So， you have some。

You have some edges and these edges have different right ends。

So all these right ends form a set of size， at least size of a。

 so the size of the neighbors must be at least size of a。嗯。Oh。Nice， rate。こ。Welcome。

 everyone everyone。啊。那有什么问问。I claim that if this is satisfied， then we have a perfect machine。

 let's prove this。Bof is quite a symbol。We'll see that if this satisfied， then in this algorithm。

 the effects will always find the augment mating path。So just if again。

 this case constraints is is fine。Then every time in this loop， we will find our mating path。

 so each time we willll increase matching by one。 so in the end the size of the machine will be。

Why is it true？Make good listen。Soう。Let's imagine we run this DFS and it didn't find the augmenting path。

Then what happened？We run the first from here。And we'll find some notes here and some notes here。Now。

 I claim that number of nodes。wheel mark in the left part is more than the number of nodes in the right part。

Because let's see。 So we're on the from here。 Let's say we visited these two node in the right part。

 So for each note in the right part， we have a edge from the match。 So we have。Hdge here。

 and we have edge here。It means if our DFS visited these two node in the right part。

 it will also visit these two node in the left part。

So the number of visiting nodes in the left part will always be more than number of node visited in the right part。

嗯。Again。Yet here， if we visit K notes here， then here we visit K plus one notes。Now。

 since we have K plus one nodes here and K nodes here。There must be at least one edge。

Which is going from this set， not to this set。 So there must be some extra extra。

But because the size of the neighbors of this set is more than K cable is is at least K plus one。

 So we have K plus one node here。They must be， least keep us one neighbors in the right part。

We only visited care of them， so they must be they must be one more。

 So there is one age going to here。嗯哼。That's all。And basically。

 we prove our DFS can stop without finding a free note in the right part。Mmmm。Clear enough。Okay。

 hope's get that。That's all， list the whole theater。Now next。

The next thing I want to discuss is the minimal color problem。아 어。I need some specialistries。

I will be business。Another important problem in graph theory is the vertex color problem。

If vertical power pump looks like this， you have a graph。And again this for some growth。嗯。Yeah。

What you want to do is to take some notes of this graph size that for each edge。

At least one of the ends of this edge must be in this set。 So you want to mark on node。 for example。

 this node。And， and， and， and let's say this note。なでし。doesnt pick 쪽。啊。

So the problem is the following you want to take some notes such that each edge is covered with this set。

 So for each edge， at least one of the ends of this edge must be in your set。Yes。

 and problem want to find is find the set of the minimal size。

 so we find to take minimal number of nodes， which will cover all the edges of your graph。

And this problem isn't P complete， right， It's actually quite easy to prove for that。

 this problem isn't P complete。You can do it as an exercise。s actually it's easy。

 So this problem isn't be complete， but。If you take a bipartthegraph。

This problem is actually not in the complete。So if you try to do the same， with bipart。Yess。

Let's see something like this。诶。Let say this。So if you take by like off。And try to do the same thing。

 So I marked this note。 Let's say this note and this note。It turns out this in bipartgraphs。

 it is not going be complete and it can be solved in for an noal time。Let's do you。

But before we do it， let's talk a little。 Let's talk a little。嗯。

It turns out that matchings and vertex cover is the。A pair of two dual tasks。

So we'll talk about dual problems later and we'll talk about again。

 we'll talk about linear programming， we'll talk about what is a dual problem and so on， but I。

Find in the maximal matching and find the minimal vertex cover are two dual problems。

What does it mean。It means they basically describe the same set。

 but from two different points of view。そう。来。Let's say like this。If you。Take any matching。

 not not maximum matching， but any matching。So you have your bipa diagram graph。

And you have some matching in this graph。こちげ。Let's say that， please。

Ill just word like this for simplicity。So let's say you have biproduct drop and you have some matching of this organ。

 the size of this matching is M。Easy to see。That the size of and let's take that now。

 let's take some ver color。Let's take some garbage color。 So the garbage color will take some。

Notes like this。나르 장들。So these notes are theduct code。Now， that's easy to see。

That the size of the vertex tower must be at least the size of dimension dimension。嗯哼。

Because you have these M edges， you need to cover these M edges。They， don't share any endpoint。

So all these。Notdes are different。 So to cover this M edges， you need to pick at least M nodes。

 right in your water cover。So the size of your graphictx power。Hes always。

At least the size of the matching。Again， if you take any matching and any ver power。

The size of yourverters cover will be greater or equal in the size of your machine。Clear enough。

So because you have this matching， you need to cover the edge。

 the edges of this matching to cover all these edges you need at least M node。

 so the size of your cover must be at least M。那。What's the interesting part。

 the interesting part for dual problems， the situation works looks like this。

 you have something like this so you have this set of matchings。And the set of rot scs。

So if you take any of sc， it will be greater or equal than size of dimension。

The cool trick is that for dual problems， this。Opttial point is the same。Because actually。

 what what's happening that in one problem， you try to maximize this thing and in other problem。

 you try to minimize the。Border， which like。Hard to explain。

StSttorship kind of looks like these though。Its like in one problem you describe the inner bound of some figure and in other problem you describe the ultra bounds of this figure and here you try to minimize the point inside and here you maximize the point from outside。

So we will find the same point， kind it。If this happens， what does meaning。

 It means if we find any matching。Which have the same size， than some。Car Do7。

It will immediately tell us that this matching is maximumimal。And this co is minimum。や。

So you need you don't need to prove that this color is minimal。

 So if you just find any any vector power， which has the same size as you're mention。

 it will immediately prove that the size is minimal possible。Okay， this whole philosophy。

 Now let's go to algorithm。So our is very simple。We'll take the graph。

And we will build the maximal matching in this graph loop because we can we just learned how to find the max maximal matching。

 let's find the max matching in this graph。 for example。

 let's say this edge and this edge and this edge。Yeah。

So we take the graph and build the maximal machine in this graph。Now we do the home thing。

 we tried to run DFS。Again， the same D S we used to find out mat pairs。 So we take all the。

Free notes in the left part。And run GFs from these node。What we will find。 So we'll set from here。

 we'll mark this node。 now we go here， mark this node， Now we go here， mark this note。



![](img/b2d058593121540843713b98cda4bf6e_46.png)

Thats all。いや、そう。So then， we start from each。Free note of the left part and run the same D F S we used to find our meeting pair。

So we go to the left using edges not in the matching and go to the left using the edges from the matching。

We will have the following picture， let me show you。

So this is left part of your in the right part of your graph。So here you have some free notes。

So you start GFs from here。Mmhm。😊，Let's put so so so。

 So your DFS will mark some notes here and mark some notes here。So let's put marked notes here。

 So these node are marked in your defense， and these notes are marked in your difference。Okay。

 let's call this parts。 Let's call this part L plus L minus L plus and L minus。

So plus is the set of nodes visited by D FS and minus is the set of nodes not visited by D FS。嗯哼。

Clear了。So again， what we did we build the maxim margin。And then we're on the same TF again。

So we run DFS from all three nodes of the left part。

And mark all the all the notes which were visited in this。The D F。We have a picture like this。

 so these nodes were visited in this DFs， these node nodes where Bur visited in this D。じゃ。Okay。

 first easy question。If you take any free note。In the right park。And which said this node belong to。

So it's easy to see that free notes of the left part。Always belong to set L plus。你告是。

Free notess of the left part are the nodes， we start defing from yeah。

 So if we start di from this node， we immediately mark this node so。

3 node of the left part will always be visited by the DFS because we just start DFS from these node。

Yeah， if you look at the notes。Fre notes in the right part， they will be in the set Air miles。

 so all free notes will be here。Why is it true， Because the matching is maximum， Yeah。

 there is maximum matching。 We don't have any augmenting path。If we don't have any automaticing path。

 it means we can move from here to here。That's all。So all the freenos of the left part are here。

 All the freenos of right part are here。Now let's look at all the edges。

 So what happened over the edges？What edges can we have in our？We can have edges from L+ to L+。

 so we can have edges like this。Over this screen。 yeah， like here though。

We have age from El plus to Air。We can have edges back from that Western one。

We can have edges from L minus to minus， and back。No problem。

What about edges from between this plus section and this minus section。

 What edges can we have between this plus section and this minus section， Can we have edge from。

 for example， from L plus to R minus， Can we have edge like this。Okay， this is Gretesham。

We can have edge like this because if we have edge like this。

 it means we have edge from visited node to non visited node。Yeah。

 it means our DFS did something wrong。 Yeah， if our did DFS visit， least not。

 why didn't didn't go here。So we don't have edges from plus to minus。Yeah。

 we only may have edges from minus to plus。Yeah。嗯。Now take your question， can we have edge like this？

This small drink cushion。WellIt turns out we can't have edge like this。

 we can't have edge from L minus to L plus。And why is it true， Because let's look， let's look。

 So we have this。Weex M N， N L plus。 So we have visited north in the left part。

 and we have this edge from here。 So with the this note， but we didn't visit this note。

How could happen how did we get into this note？No。We didn't install the F S here because this note is obviously not free。

 We have this edge。So this note is not free。 We didn't stop difference here。

 So we moved to this note from some other node here。But again。

 it can't happen because now we have two incoming edges to this note。

So both these nodes are in the machine。 and we we we may have only one load。 one edge in the machine。

Mm哼m。😊，So if the left node in the left part is visited。

Then we must go from some visited node from right。 So we only may have edge from some visited node in right part。

 we can't have edge from non visited node in the right。🤧咳。So， these edges are also。이 버스 막。

And the only edges something， which are possible is。The the H from L minus to a plus。

So these edge is actually possible。And here we may have something electrica from L minus to R plus。

Here， for example here， we have this edge from here to here。 So this L minus， this is R plus。

 and you have this。It's actually a quite cool picture。

 It's kind of this picture describe what's going on in the biography in all this matching theory。

So after you build your maximum matching。And run day first。

 the structure of of sugar looks like this。It's quite cool to keep this this picture in mind when you think about some problems about。

My drinks or something like that。Itsically about any problem about by bygraph。Oh。

 that's that's almost all。Now， let's try to find the minimum verex color。So which sets？

Should we take to cover all the edges of this graph？너 it 있지도。So to cover all the edges in graph。

 we just need to take set L minus and set up our plus。Let's take a minus and R plus。

So if we take all these notes。And on these notes。We will obviously cover all the edges of our graph。

 right？嗯 哼。Because all the eggs here on on the ends are plus or all mag。嗯。嗯。Are you here。

Why is it up small？Perfect question。By now I just claim that this is a a vertex cover。

 why is the optimalmal would prove just in a second。

W is optimalmo to prove this vx cover is minimal possible。

 I will just prove that the size of this cover is equal to the size of the matching。

So if if I prove the size of the of the color is the same as the size of the matching。

 I will prove that this it is minimal possible。Let's how to prove it again， let's go to this picture。

 let's go back to this picture。そ。So the structure of my office like this。

 I have some matching and some final here。 So I have。Free notes here and three notes here。嗯。Yeah。

 you can't prove it just by linear dual， but we didn't talk about linear goal changes also。

I will just prove it using very simple terms without any linear programming stuff。

 So let's go back here。So吃。I have my perfect cover。So this is my matching。

Let's say this is the maximum machine。So I have the maximal mention and some three notes here。

Lets see which products。We used in our D scan。First of all， these free notes。

I not used in the electric cover。So this vers column。don't contain any， does contain any node。

 any free notes from the right part and any free notes from the left part。M。😊，No。

Let's look at the mentioned so。Let's prove that for each edge in dimension。

 we only take one of the ends。Of this。Not of this age。そう。

So let's look on the maxim matching Where is it here in this graph So the maxim matching contains only the edges from right to left right。

 so maxim matching has edges like this and edges like this。but let's just mark。

So we have these edges and these edges。So。All the edges from the maximum matching。

Are the edges from L plus to L plus。Or from L minus to L minus。嗯哼。So for each edge from the mention。

 we may only take one of its ends。So if it is edge like this， we take the left end of this edge。

 if we have edge like this， we take the right end of this edge。That's the whole proof。Now， again。

 our graphic cover contain only。Nots from the maximum matching。

 it may contain any nodes from the any of the three nodes of Agraph。And from this maximum。

 we take only one and from each。From each age， so the size of this color will be the same as the size of the maximum matching。

어 어。Too much happening here，Over tip。한 번 좀。Yeah。That's the whole proof。Again。Again。

 the whole algorithm。To find the minimum objects power in bipartgraph。

You find the maxim matching in your car。Now you run the DFS from all three nodes of the left part and mark everything which is visited by your DFS。

And now you take all non visited edges or non visited nodes in left part and all visited nodes in the right one。

 for example， in this picture。Here。We take all non visited edge， non visited notes in the left part。

嗯。Not visit it。There's these notes and these notes。

And all visited node and the right course will take these knowledge。That doesn't look good。嗰是跟创者嘅。

So I ran different from this note and didn't mark。I also need to go here。凉梯啊。Yeah， that was better。

So now again， I mark I take all node visit node from the left part and all visit node from the right part。

 So I take this node from the left part and these two nodes。咁でな。Yeah， and now this is。

This is the minimum of cover。Again， why is minimal because it has the same size as as as the matching。

 if I have。If I have this matching and I have the vertex cover have the same size。

 it's obviously minimal。White has the same size because in this ver cover。

 I only take notes from this set。And from each of these edges， I only take one of its ends。

So I take one of the ends from each edge from the matching。

 So the number of the node I take is the same as the number of edges in the matching。不错。Yes。

 the dual is earliest uses。 the between verx cover and matching is only for bys。Yes， 전 좋아。有。Yes。

 for non by paragraphgraph， this problem is't be complete and matching problem is not in complete。

so we'll solve matching problem， but it will not happen。

 it will not help us to solve the minimum large problem。 That's true。Okay， I lift this off today。

