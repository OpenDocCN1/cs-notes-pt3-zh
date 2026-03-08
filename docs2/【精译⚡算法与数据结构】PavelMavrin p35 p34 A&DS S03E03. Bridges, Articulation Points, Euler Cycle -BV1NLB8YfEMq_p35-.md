# 【精译⚡算法与数据结构】PavelMavrin p35 p34 A&DS S03E03. Bridges, Articulation Points, Euler Cycle -BV1NLB8YfEMq_p35-

🎼。

![](img/786bd129207248f2ea5db4607b964f63_1.png)

So today we continue to talk about Death research algorithm and its applications。

 and today we will move back to undirected graph。So like we discussed in the first lecture for undergraph。

 the structure of connectivity is very simple， so if you talk about connectivity in undergraph。

 it's very simple， you have these connectivity components and like all the vers inside the same component are connected and vers in different components are not connected。

 so it's very simple。So today we'll discuss something more interesting and we will discuss big connectivity。

So big connectivity is simply when you have two， two different paths from one node else， if you have。

Two notes。And you want to have two。Different paths one。

 And these paths shouldn't care shouldn't intersect。 So if you have one path。

 Yeah you have another sound method。 That's， that's， that's， that's ugly picture。 I I don't。

I all draw the bad one so that's main idea so we will talk about beeno cri。

 so we'll talk about the relation when you have two non intersecting paths between two nodes。呃呃，他说猪。

Two different kinds of big initiatives。First kind is when you allow these paths to have common nodes。

 but don't allow have common edges'sed。Hi， I believe the correct term is like age2 connectivity Doest matter。

 I will call B connected components， just for simplicity。

So there are two kind of big connectivity when you allow these edges of these paths to have common nodes。

Like here sorry if you go。You may have one breath like this and another bath like this。

So these two paths share a node， but they don't have any common edges yeah so this edge B connectivity or edge2 connectivity and another kind is when you allow when you don't allow these paths to have any common nodes。

Like these。So it's air connectivity and vertical connectivity。 It's kind of different。

 and we'll use slightly different algorithms for both it， But we will solve both problems。

 So we will， we will we will find the relation。 We will find will。Build the construction。

 which explains how this。Each TV works and how this work mechanic TV works。 It's slightly different。

 but we will solve them both today。嗯。Will add4 account on Friday。 What is all for， What is all。看说。告。

So first let's talk abouted connectivity activity。 So let's talk about this kind of basic connectivity activity。

 So let's say that's two nodes。아 미 액。Lecture 4 will be next Friday。 Yes， yes Oh no， no， no， no。

 it will not be on next Friday。 Yes， next Friday， yes。I'll announce it later。

 so next Friday you will be no lecture because we all moved Moscow to the world finals， yeah。

We'll skip the next lecture next Friday， but we'll get back on schedule in two weeks， yeah。嗯。

Or maybe， maybe we need to move to to Wednesday。 like well discuss it in then。

Back to be connectivity。 So let's say that two node are become connected。If we have two。

To two paths between these dons and these paths can have this cannot share any edge。

We have one pen here， let's put something like this。And another path here。

Let's say least to also are be connected。I claim that this relation is actually a transit。

What does it mean， It means that if you have two paths between some U and V。

And also you have two paths from V to W。Then you have two puffs from UW。Let's。

 that's the first thing we need to prove today。Yes， by looking on this picture。

 it looks like it easier to prove。 Yeah， so if you look on this picture and you may say that okay。

 I have。Two separate baths here。 Two separate baths here。 So I may have first bath。

Here and second path here。Looks like a nice proof， but it actually is， it's， it actually it's wrong。

 Can Can you spot the。Error in this proof。 So I want to prove that if I have。

2 non intersecting paths from U to V and two non intersecting paths from V to W。

 Then I have two non interecting paths from V from U to W。

What is the wrong way to prove this Just drop these two paths， these two paths。

 then construct this first path from U2W and this second pair from UW。Yeah。

 the error is that these two paths may actually intersect y because these two paths do not intersect。

And these two pairs are not just same， but these two paths actually may intersect。

Because because I don't know anything in relation between these two pairs。

 these two pairs and these two pairs may relate in any ways also。

 if I take a contiation of these two pairs in these two pairs， they actually may intersect。

So we need some more complicated proof。Let's prove this。 It's actually not not at hub。

 So how to prove this， let's build two paths from YouTube to。

 So let's take you take a V and construct these two paths。 So first path。Now we have a cycle。

 so we have a cycle which connects this U to V impact。Now let's take no double。

Let's contract two pes from W to V。These two paths at some point will intersect these cycle。

 so well at some point we'll have some node which belongs to this cycle。

 so let's have this so you have this path from W2 V。Let's app， like， coffee。At the first。Vics。

Which belongs to this cycle。And now let's do the same with the second path path。

 So we have another path from W to V。Again， let's copy it。At the first note。

 which belongs to this cycle。Now， in this picture， all the paths I do not intersect because these two paths don't interect。

 these two paths don't interect and these two paths do nott inter these paths because we can't tell it。

At the first point when， when they start to intersect， we cut them with anti position。

 So in this picture， nothing intersected nothing。And now we just build two paths。

 and the first path will be。This path and second path will be this path。

So we use one part of the cycle to build one path， another part of the cycle to build second one。

Little。So it's actually true if U and V are be connected and V andW are be connected。

 then U andW are be connected。一先都得。What does it mean， It means again that you have some relation。

 which is symmetrical。Reflective and transitive。 So it is some equience relation。

 So it will split all the notes into some equience classes。And in each of these equience classes。

 if you have two nodes from the same equience class， these two notes will be reconned。Thats the好。

And these classes are called B connectivity components and it's actually again。

 it's edge connectivity， so it's called two edge connectivity components that doesn't matter Ill call everything B connectivity。

Just for simplicity。So let's let's draw some。Let's have some rub。Let's say something like this。

 And then here。then more some。嗯。It's too simple， with me。Let's find all the components in this graph。

How to find good image coupon。 again， every cycle。Is a big activity component。

 So if you have a cycle， then all the nodes upon this cycle belong to the same big activity component。

 right， Because if you have cycle， you can move from any node to any nodes using just you have two perhapss。

 you can use one one part of the cycle and another part of the cycle。

 So every cycle belongs to the same big activity component。

 So here we have one big connectivity component。Here we have another connectivity Poland。

And these notes are become an activity component of single one。Like this。一从。Now。

 like in previous lecture， we can build the condensation of the graph。 Yeah。

 so we can replace every big connectivity component with a single node and build the graph of connectivity between these big connectivity components。

 Yeah， so let's say this a。B， C， D， E， and F。So we can build the pho graph， we can build graph from。

 so we have component B， component A。They're connecting using this edge here we have component C connected2 be component D。

Connected to B component E， connected to D component F。가네 또 쪽기。

So we can build a condensation like this again， every node in this condensation is some big connectivity component of the initial graph and they are connected if we have edge between these two connect components。

なおあ。Let's observe that this condensation is always acyclric。 Yeah， because if you have a cycle。

Then all the nodes on the cycle belong to the same big connectivity component。

 so you cant have cycle in this condensation。If you have undirected graph without cycles。

 it means you have a tree， right？So， every condensation。Of the graph when when you。

Condense all the begin activity components。 You will have some tree。

Tre is very good They structure trees with very good structure。 We in the previous century。

 we learned a lot of algorithms for the trees。 So if we have a tree， we can calculate。😊，Many。

 many useful things， just using the algorithm from the previous lecture。 we can use binary liftings。

 We can use link at trees， stuff like that。 We， we learned a lot of stuff about trees in the previous semester。

 So when you， when you want to learn something about。Close to big connectivity in a graph。

 What you going do， you you may find big connectivity components， make this condensation。

 And then in this condensation graph， use some algorithms for trees。

There are a lot of specific algorithms， specifically for trees。That's the plan。Now。These edge edges。

 which connects different， the connectivity components are called the bridges。So these edges。

And actually， the same edges you have here Yeah。 So for each edge。

 which connects different components， is actually transferred to this。跟能随。

So these edges are called the bridges。Bridge has every bridge has a very interesting property。

 so for every bridge， if you remove the bridge from the graph。

You will increase the number of connectivity components。No， let's prove this。So what So if。

 if I have a edge which connects to different connectivity components。Then if I remove this edge。

The number of of connected components will be increased。

No because these to nodes will not longer be connected。 No let's prove this it's easy。

 so let's have some edge from YouTube to。This U and V belong to different connectivityivity components。

 So I have some component here， some component here。So if I remove this edge。

I claim that U and V are no longer connected。Why they are no longer connected。

 Because if you and V are connected， then I have some pair。你。And if I have some path。

 it means that before I deleted this edge， I had two paths。 Yeah， so I have this edge plus this path。

 So I have two non intersecting paths。So以 it been main。So it means that if I remove this edge。

There will be no bread between U and V， it means that you and V are no longer connected。

That's kind of interesting property， so it means that it is actually means that this edge is the only edge which connects these two components If I remove this edge。

 these two components will no longer be connected。嗯哼。Again， I I just remind you that you。

 you need to say that everything is clear， at least every 50 seconds。

 or I will continue to say everything， okay。No。Do到 out过。

The plan for today is to build the algorithm which finds。

All the bridges and fines all their big connectivity components。This is again。

 one of the application of the the special bur and again， it was first found by。Byta John。

 I believe in this， in his first article about GFS and its implications。啊。Quite simple， I agreein。

Buty。It uses some specific magic roll discuss。Let's go。The algorithm， what we'll do？First。

 we'll run adept of social breathing。Which， so we'll take any note of the graph and run a GFS from this node。

Let's see。 So you'll take some。First note and run the rest from this note， you will have some。

3 of your D F S。So you start JS from here， you go here， here， here， then back， then go here。

 back and so on。It's too big。Okay， good。嗯。First observation， very simple。

 If I run the address algorithm。In the graph， that's where we'll use all the bridges。

So for every bridge。My IDs will use the bridge to go from here to here。

So all the bridges will be in this DFS tree。So if， if you have any bridge， yeah。

It will appear in this tree。Well， let's through this again， it's simple。

You start your D from in in one of the component， and you need to move to another component。

 You can't move from here to here without this in this edge。

 So this is the only edge which connects this component in this component。

 So if you if you start here and want to move here， you need to use this edge。

 So every bridge will appear in this tree。Great。Now。

 the only thing we need to find out is how how to find out if this for every edge in this tree。

 we will find out if this edge is bridge or not。So let's look at some age， let's look some。

So let's have some edge， so you have this edge， let's say from V。또トイツパラテ。

So let's take some node V and look at the edge from this V to its parent in this the DFS3。Yes。

 all the bridges will be included in in this day。Mhm。😊，너もこれ的。

Every spinning tree will contain all the bridges。 If you know what span trees。

 we will talk about spinning trees later in the score But all this。

 every spinning tree we must connect must contain all the bridges。Because you can can。

 you can connect these to componentss without having this edge。Yep。So what we'll do。

 we will look on this tree again， we know。我什。Many things about trees。

 so we'll just use the trees Al from the previous semester。

 very simplified just to look at this tree and and find out for each edge of the tree if this edge is bridge on。

这s the本。So let's see。 We have some edge in the tree from V to its parent。

How to find out if this H is a bridge or not。No， let's try to remove this edge。

 What will happen if we remove this edge。If we remove this edge。From the graph。

This tree will be split into the two parts。 So we have this top part of this tree and this bottom part of this。

 So we have this sub tree of V。Let's move some， some more note here。So if we remove this edge。

We have this sub tree， and it's separated from， from the remaining of the tree。We have these sub。

Sparate from。From the remaining of the tree。So if this edge is not a bridge。Then。

The when I remove this edge。This sub train must be connected to the remaining part of the tree somehow。

 So this sub train must have some another edge， not， not included into this stream。

Which connects this sub tree to the remaining part of the of the tree。How this edge may look like。

So you may have some edge which connects some node inside your sub with some node outside of your substrate。

You need to have some edge like this。嗯哼。What is the interesting part。

 The interesting part is this edge can never go like this because this is a tree of depth search。

In D FS3， you may not have。The edge between different branches of your DF S string。

So like we discussed on the first lecture in if you run DFS and look at the DFS stream。

 you may not have。But the edge between two different branches of the tree。

Because when you visit this left one， you will use this edge to go here。So you。

 you you cannot have this edge from different branches。 No， one of these branches was with first。

And when you visit the first branch， you will use this edge to go here。So you can go here。

 then go here because you have this age， yeah。So this edge always connects some。

Some node inside your subre with some of the ancestors of this node。

 So H is always connected to some of ancestors of this node。 So you have this path。응 not 또 또 희。有。그。

So you have this path from the rules of the trip to this node P。

And if you have any edge which connects you to this remainder of the tree。

 it must be connected to some of these nodes。1。Okay。And that's the only property we will use。

That's the only property we will use。嗯哼。Okay， that's the whole observation。

 Now we just build the algorithm which So what we need to do。

 we need to check for this node V if in this sub of V， there is a node which is connected to some。

Ancestor of this P。If I have this edge， then this edge is not a bridge。That's the plan。

 That's the whole plan。So how will find this edge its actually pretty simple， so let's look。Well so。

 so we have this。 So we have this be。And it's parent peak， and we have this section。

So we have this substrate of wheat and we have some antithrus here。Inside this up。

 we may have some up going some edges going up to some ances here。 So let's look on this edge。

 So we may have。H to here， and then H to here。 and then another H。Here。

So we need to check if we have edge。Which connects something here to some answers of this being。

We'll do the rolling from all the edges。Which goes from inside of this sub and going up to some ancestor。

 We need only one edge。 We need only edge， which goes maximum possible up。 So we'll hope that。然后。

How's called topmost。We need topmo node， which connect。

 which is connected to something inside this actually。 We need only not to know this node。

So this is the only interesting note for us。So if this topmost node is above this P。

Then I have some edge， which is connected to something above this be。That's the one。

So for this node V。I will find only this topmost node， and I will call it。四。啊不啊不。So again。

 it's actually pretty simple。 So what I want to do， I want to look。Inside this sub。

 find all the edges， which goes from this sub， sour up and from all this。And just。

 I need to find the top post。And I will remember this topmost edge in this node V。

 So for this node V in this sub， the topmost edge is visited inside from from inside this of this sub。

 is this upper of。That's the hope one。응  응。Now， let's make a pause。 just。

 you're not saying everything is clear soon。I will continue to to say the same thing。嗯。

What is the interesting， What is the interesting thing， So how to check。呃呃一不说。So all these notess。

 what is been， All， All these nodes belong to the same path。 Yeah。

 so all these notesbs are on the path from the roots to this peak。It means you can compare the notes。

You have like linear relationship these two between all these nodes。So。

 so that's what what what mean when you have top more nodes。 Yeah。

 So all these nodes are on the same line。 so you can select the top more node。

So these are notes of the tree not of the line， but they all belong to the same path， yeah。

So if all knows belong to the same pair view can take the topmost one。Yes。

 we will calculate these up in in in a single day first in a minute。아。How to compare to node。

 So what I will what I will try to do now， I will find these edges and try to find the topmost node I can visit from from from this subject。

 So how to how to compare to node。 So if I want to compare which node is above and which node is below。

There are two different schools for this。Fco is little bit more。 if usual。

 so what you can do is for each node。 you can remember its depth in tree。 So。

 So you can say that the root has the 1，0。 This is the1 here，2，3， for in。

So you can just inside your DFS ple clay for each node。

 it's a depth in a threshold distance from the route to this node。

And then when you compare to two different edges， you just compare these depths of this now。

This is one of the way to will solve this problem。Another way is to use a。

How it's called entry time of of node。So if you compare entry times of these nodes。

You have the same thing。 So nodes which are closer to the route。

 will have less entry time than notes which are below。Because you first enter this node。

 then you enter this node， then you enter this one and so on。 So instead of using these depths。

 you may use entry times。It's slightly more universal because entry time is different for all notess。

So you can， you you can basically enumerate all the notes by increasing of the entry time。

So it's slightly more useful technique。 So I will use this technique， but it's not important。So。

 so I need something。I need to need to calculate something which will allow me to compare to notes and say which note is above。

 which notes is below。You may use depths of this nose。Or you may use entertainment。

Both works perfectly fine。I will use entry time， because I am used to。But。It's up to you。So again。

So let's。Let's write the definition so。Up of three will be minimum。Entry time。T in。Of node W。

Such that I have edge from you to W。And you belongs to sub。O the。응 哼。Let the hope。No。

Let's try the property。 So if I calculated this。Us for all the notes。If we will do it in a minute。

Then how to check if this edge is actually a bridge。 so this edge is not a bridge。

 if I have this edge which connects something here to something above P or22 P or something above P。

 So this edge Vp is not a bridge。Redgege。응 네。If I have this edge connected to something here。

 so if up。Of three。Is less or equal。Then。Time of note， A P。응  응。Again， you stop。

Just at the time though。嗯。Okay。You assume V also， Yes， V is also inside this substreamme。 That's。

 that's there is one。One small detail here， because I order， I also have this edge PV。

 So here I look on all edges except this one edge because this edge actually is the edge I'm actually examining。

 So so I want to look on all edges， except edges。From the tree。そう、エニト選手もノートユュ。Not front trip。嗯哼。

So I need to find some edge。 We does me to the stream。

And which connects something from here to something above。

So if I precalculated these values for all the nodes。Then I just look on this note。

 find the value for this sub。 If this value is above this note P。

It connects something from here to something from here。There this edge is not a bridge。

Because if I remove this edge， I still have this edge， which connects leads to this。Yeah。응 응。Okay。

 hope it's good enough。 Hope it's good enough。Now， what we need to do。E to calculate this very。

So how to calculate these values， we will calculate these values using dynamic programming。

So what we'll do， we'll look at node fee。And look on its children in this tree。For this no。

 we have some suitable。So we have a few children。And each child has some subjects。

So have some sub here， some sub here， some sub here。And we have this baby trip。So。那。

If I have this green edge going from somewhere here to somewhere up， this green edge must。

Stuff inside of one of these subies。Or from this node visa。So I just， again。

 I split this sub into single node V plus these small subies。If the sample human one no。

 then the edge product will be。No， no， no， no。 if the if the sub contains only one node。

 still may be maybe not。We you have some edge。都三蚊之上。So。

So that I need to find all the green edges inside this sub。

 These green edges may go from this node V itself， so I may have some note from here。

Or it may be from some of these subies。So from each of the sub， I may have something。

And now what I need to do is just to take minimum。amAmong all these。PossPossible edges。So。For。

 for edges going from this node V。I will just iterate all edges from node V。

 And if I have edge from V to something。Then I will add these to this minimum。Just simply。

 it's red for all ages。Actually， my dear， face will do it。And if I have this sub， then from this sub。

 I only need the topmost edge here。 So from each of these small sub， let's see sub you。

From each of these sub， I only need one edge， which is the topmost edge。

 and this topmost edge will be precalculated in this audio。So from this node view。

 I take this topmost h。 It will start in this up of you。So here is the up of you。

So I will use this edge from every of the from every subject。

And then I will look on all edges going directly from this node view。嗯哼。

So while look on all these subies， take the topmost edge from each of the sub。

 look on all edges from this node V， and now take minimum of all the things。嗯哼。Let's practice this。

 So up of V will be minimum。Of what。Of all node， let's call it W of all W， such that。I have H， E W。

And not， no， not， not double Let see T double。And for each of these subaries。

 I need to take up and up of you。For all you， which are children。嗯。Of。That's all。

 That's the whole one。嗯哼。Now， let's write the code。 The code will be pretty simple。Again the one。No。

Inter thing in this scroll is I need to integrate all edges except this edge。

 I need to skip this edge when I enter all edges going from nodeV。嗯。I will do it like this。

 so I will simply， I will pass this P into my DFS and then check if I have H from V2 P。

Then I will just keep this edge。Let's not hold。So round D refreshs from node V with parent P。

So I started off no node V。 First， I will in initialize the value of。Enter time。

So I will say that entry time of node V is t plus plus。Just set the enter for this note。

Now I need to initialize this up， there are two possible ways to do it。

You can again up is minimum of something。 You can initialize up with plus and finishing。

It's perfectly normal。That's one way to do it。 Another way is to initial age is 5 in because。

That's also possibility， because this。You，You need to check here。 here。

 You want to check the app is no more than an enter time of P。

So you need to initialize this value with something which is great than。Entry time of P。Basically。

 any value， which is greater than En time P will work。That's so if you， if you don't have。

 if you don't want to have plus infinities in your code， you may initialize this up with T of V。

 It actually kinda makes sense because this V is kinda。Kind accessible from this sub。

So this actually kind of makes sense。What's up to you。AndNow you iterate your all ages。

You mark this issue。Mark little。Now you turn for all ages for you。let's see out of you。

So it's ready for all edges from this node wing。If this u is already sorry L。 So see if u equal to B。

 then continue。Just was in。That actually doesn't work when you have parallel edges。

 if you if you allow to have parallel edges like this， this code will not work。 So be accurate here。

 So if if you allow to have parallel edges in your graph。

You need to do it a little bit more problems， buts see。Let's come with the exercise for you。

So how to modify this code if you allow to have multiple edges connected in same notes。

Just think about it in the next thing。I will say I will not have any multiple edges in my graph。

 So this golden。那。Let's see if this view is already marked。

It means I have a edge from here to some of my ancestors。嗯。If I have edge to some of my answers。

 it actually it may also be one of my processors you also may have edge like this。

 but it doesn't matter。So， if， if， if this ver system is marked。

 it means I have this edge or all this edge。I will count these edges as well because they does matter。

 So this edge， all the nodes here have greater entry time than this edge。

 So it it will not affect anything。So if this two is marked， then I will update my app。

Of we will be minimum。Of off。Of we and the and enter time of this you。Right。Great。응 어 어 어 어。表钱。说完了。S。

Check， please。And now if it is not part。The make one of these。

 I will recursively call the FS from this note。어 이게 무슨。And then when I return from the recurs。

 I will update my video。The up of V will be minimum。Of up of V and up of you。I believe that all。Yeah。

 that's the whole code。Now， in the end， in the end， when you finish all this。

 you calculated the value of up for foral V。 So in end。

 you can check that this edge is actually bridge so so if。Up of V。 So if it's not bridge。

 And so it is bridge， if up is。Great than time of PM。 So if great than time。Of逼。Then it is a bridge。

 then the VP is a bridge。That's home。Works fine。 So that's the whole code which finds all the bridges in your graph。

 Again， how it school works， all the bridges belongs to this stream because it is some tree which some spinning tree。

 So every Spain tree must contain all the bridges。So we will look on every edge in the stream。

 how to check if this edge is a bridge。 This edge is a bridge。

 if there is nothing which connects this sub to something above。 So how to check this。

 I will find the topmost edge going inside from inside of this sub。 if I have this edge。

 then it is not a bridge。 So I will calculate this up。

 this up will be the topmost edge from means from inside this from from this sub。

 So if how I calculate this up， I look on all the edges。

 If I have edge to something which is already marked。 then I have edge like this。

 I will update my up like this。 And if I have something not marked。

 it means I have some of my one of my children。 So I run DFS。For this node you。

 And when I return from this D F， I already calculate this value here。

 So I update my value of this value。H文。야 여 여や。不's错。No。Oh， spent a lot of time at here。

Actually spends a lot of time， okay。Now， how to find all the big activity components。

We found all the bridges。And now that we need to find actually your decomposition sorry we need to find all these sets of nodes which are be connected to them。

 So how to find big connectivity components if you know all the bridges。

One of the solution is to simply remove all the bridges from your graph and then find all the connected components。

So if you。tro again somer。嗯。Something here。So when you detect all the bridges。

You can remove these bridges from the ground。And then find all the connect components。

 you can use union find destruction or you can use GFS。 It doesn't matter。嗯。So you can run again。

 you can run the second the DFS just to find all the connect components and now each connect component will be a big connected component because it just removed all the bridges。

So youll find these kind components， every connect components will be。やて。

That's one way to solve this problem。 Unfortunately。

 it's not very useful when we will talk about relative spec connectivity， but。Here。

 it's totally working。Another way to solve this problem is to do。

 to do it at the same time when we detect the bridges。 So what will， what we can do is。To find this。

We connect components in the same depth of search when we find the bridges。

How to remove the edges efficiently。You can just mark all the edges。

Just mark them then they are bridges and then run D FS and just don't use the bridges， for example。

So good。You can make objects for each edge and in each object， make another boion。

 which says that this edge is a bridge here。 and then in the second they effects。

 just skip the edges， which are bridges。It's up to you。 So your programme is here， you can do her。

I believe not。 I believe there are various ways to do it。嗯。저 막。Yeah。

 so how to find these B connect components inside the same depth search。It can be done like this。

 What you can do is to。Maintain the stack。You maintain the stack of the notes you visited inside your DFS。

 sorted by the entry time。So you visit all the notes。

And just put all the notes you visit into some stack。Let's call into buffer。Let's make a pitch。

So here we will add the note into some buffer。嗯哼。那。If this edge is actually a bridge。

 so we didn't find any。Any ages going？From this sub。

So we just detected that this edge is actually a bridge。How to find。

All the notes in this be connect component notes in this be connect component。A actually， that knows。

Which we visited。After this node V。 So we need to take node V and all the node we visited after the node V。

😊，So， in this buffer。We visited something。 So we visited all all these。

 all these ancestors and maybe some another node。 So we， we may go here。

 visit these nodes with this notes。 So we put all these notes before we put this note in。😊。

At some point， we put this node V into this bathroom。

And then we put in this stack everything below this fee。So you put something here。

And now all these node after the node three。 So these notes。Will be the nodes。

 which belongs to the B connect component of the node V。That's the whole one。

So after we find out that this edge is a is a bridge。

We will pop everything up to this node V from this stack。

And all these notes will be belong to the bigger component of this node fee。😊，So we can do it here。

So here we just。Let's say like this， so we have this new connect component。

 new component will be just。Empty array， and then we just。Let's look like this， lets say wild true。

We push some pop something from this， from this buffer。Push it into components。And if it。

 if it takes， if it is V， then break。야 묻어 묻 못。So that's how you find be connected components inside the same definition。

 Again， what are you doing。Put all the notes you visit into stacker。So in this sec。

 this node will be sorted by the entry time of this node。嗯哼。So what you need to find here。

 So if this note。Or if this edge is the bridge。Then the connect component of this node fee。

Will be will connect this V and everything visit after this node V。

 So you need to find all the node which will visit after this node V。😊。

That's exactly all the nodes in this stack which goes to which we put into stack after this node V。

 So we pop everything up to this node V and all these nodes will be a bi connect component of this node V。

嗯哼。So this is the component。오 분 너무 우리。So this is come forward。No no。

That's all that's the whole algorithm， how to find big connectivity connectivity components when you have edge connectivity。

Good， good。Okay， listening next。啊。Now， let's talk about。We got a bit thanks to you。

So what happens if you have not。Hpic activity， but first expect connectivity activity。

 So you want to check if two nodes are connected with two paths。 We doesn't have common vertices。

Unfortunately， it's a little bit more complicated， so。

First complication is that this relation is actually not transit。So， if you have。住呃。Like here。

Let's say this u this V this W。I this girl， you help。杜呃。The word isn't perhaps from you to me。

And another two pers from V2 W。But you don't have two perhapsps from U to W。

 because these two perhapsps actually intersect at this point。

So if you think about it as a relation between advertisementes， it， it is not translation。

So you will not have this beautiful decomposition into equivalent classes。

So to make it more beautiful and to make it look more nice。

 we will talk about the verticex spec connectivity and relation not on vertices， but on edges。

So let's say that two edges。So if I have one edge and another edge。

Let's say that two edges are be connected。If I have。Two pers， one Perf connect one。

Of the ends of the elephant。1 end of one air。Ege to10 and another pair can take additional to this。

So if I have these two paths connected both ends of one edge to both ends of another。

 they may be like this or or the they will be crossed like this， it it doesn't matter。

So then I say that these two edges are being connected。And this relation is transitive。OhLet's see。

 So if I have。Two edges be connected， and they have another third edge。

And these edges be connected to this edge。 So again， lien。Previous proofs。

 So let's look on the these two paths。 So I have two paths from these ends to these ends。

 Let's stop these paths when they interector this cycle。 So I have this， and I have this。Again。

 these are the parts of the paths connecting these two ends with these two ends。Yeah。

 I have these two two non intersecting paths， and I just stop these paths when when we run into some node of this cycle。

No now now it's simple。 So when I have these paths and thisips。

 now I have these pair and these pair and these two pairs connect these two nodes with these two node and these path not inter。

So this is a nice transtulation。😊，Again， its strategy of symmetrical ref， it is equi。

 so all the edges will be split into some equi classes。😊，So for all the ages。

 we have good equivalentulation。 That's fine。そ。嗯。I don't want to era this。

Ill have to raise this part。That's kind of said， okay。Hello at this picture。

I will actually meet this definition。 So I just。C月份福福利动。

I just want to draw an example and then don't have enough space。 Okay， so let's draw some examples。

 So we have something like again。Like this。And here's something。Please。And let's move。

Do something here。And。上皮。Good的 enough。哦。不。So we' have this graph。Let's again， for each H。

 let's find its equi cost。let's welcome on the message。

This edge can be connected to anything because I don't have any edges from this point here。

 So this edge is not be connected to any other edge， So it is be connected component of its own。

 So let's say big component one。Now， these three edges。Form a big connected component。

Because for any age， I can have two paths to any other age。For for this path。

 for this edge and this edge， I have first path containing only single node and second path containing this edge。

 so you have this path， this edge and this edge。 So you have this small path of single node and you have this path of one edge so all pairs of these edges I actually be connected。

So they form a second we component，2，2， and 2。I will use all the colors in here。 Okay。

 so this edge is be connected content on itself。 So this edge is not be connected to any other edge。

 If you look at this edge or， for example， this edge， I， I don't have any path from here to here。

 except this path。So this edge is not connected to anything。 So it's， again。

 it's fairly big connected。No。This whole con g is one big big connected component。

Now you can check that you can。 if you take any two edges from this component。

 you can make two paths connecting their ends。So all these edge belong to the same。

Be connected component。系冇かし。OhNow here we have another big component。And here we have the file。

I'm not sure if you can't see the colors， but。异议。I used different cars for all disconnect components。

That's all， that's all that that thats theconect， be connect components in this graph。Now。

 let's look on the notes。What happened to the notes？啊。That I create two types of vertices。

There are two types of veres in graph。First type of note of vertices like vertices like this。

If all the edges。Connected to this node up will belong to the same beconn component。 if all the node。

 if all the ages belong to the same becon component。

 we can say this node also belonged to the same becon component。

So if I have this age and this age belong to second disconnect component。

 I say that these don't also belong to the same disconnect component。

But there are other types of nodes， there are types of notess like this。

Which belonged to to222 several different bigconect components。

 So I have this edge belong to component3 and this edge block component2。

 These are very special nodes。 Let's mark all of them。 So I have this node， this node， this node。

 this and this node。So these nodes are called articulation points of the graph。Again。

 aulation point is a vertex， which have two edges connected to it。

 belonging to two different be connected components。If I have two edges like this。

 then this is an ascicalation point of the graph。啊， now。Articulation points very special property。

 like bridges。 If you remove articulation points from the graph。

 the number of connected components will be increased。Let's prove this。

So let's take any obstacleulation points of the graph。So， you have。Two different edges belong to two。

2 different connect components。 So these edges belong to different B connect components。

 So what happen if I remove this if I remove this。Vertex， if I remove this vertex。

 these two nodes will no longer be connected。Because if this。Two node are connected。

Then I have these two edges be connected。 Yeah， so for these two edges， I have this。

Pth of single node connecting these ends。 and this path connecting this ends。そう。嗯哼。😊。

So if these two nodes belong to two different beconn components。

 then if I remove this subsation point， these two nodes will no longer be connected。What is the。

 I just explained。 So articulation point is a vertex， which has two different。

Two edges belong to different be connect components。

 So if I have two edges belong to different be connect components。

 then this vertex is articulation point。And again， this， again， all these topics usually used to to。

When you need to。Just。For example， you need to find some weak spots of your graph。

 something like this。So you want to find edge or the vertex， which is very important to your graph。

 So you bridge is very important for the connectivity of your graph Yeah。 if you remove the edge。

 you will not longer this ver will not be connected and articulation points for the same。

 So art collection points is something some important note for the connectivity of your graph。

For example， if you look on some。Or roads may something like this。Have some some and you want。Yeah。

 so， so， so so if this is the like scheme of the all the roads in your country and you have artulation points。

 So if you have some traffic jam here， then these parts of your graph will know when we can edit something like this。

 So its so all this theory usually used in problems like this。ね、そうでしょ。Okay。我不。Okay。

 I will just not rush it， I will do this small。五。Now， what is the plan about about condensation。

 Yeah， similar， like in the previous case， we can build the condensation， the condensation in the。

In this case， is constructed slightly different。 so how to build a condensation of this graph。

 condensation of graphs like this looks slightly different。Okay， let's do it first。

 let's do it in the wrong way。 Let's build a graph， which contains all your。Be connected components。

 Let's say 4，5。 here。 we have 6。Free。2 and1。And then just connect all these connect components if they are connected by some articulation point。

 So these6 and 4 are connected。 These4 and 5 are connected。

4 and3 connected3 and two is and2 and one is connected。Looks pretty fine。よ。負けて。Yeah。

But if you try to build a tree like this。😡，It it actually may may not work。

 Can you spot what what may the problem。So， if I try to build。This condensation。

 So I will try to to condense every big component into a single node and then build a tree。

In this tree， I have H if。Two components are connected， with some articulation point。

Can us spot the problem。What my go wrong。Time complex will be high。

We didn't talk about en complexityplexia。Next products will be the same。

Well just use basically the same algorithm to to find their articulation points。

yes problem is it it may not be a tree if you just build gars， because if you have artulation points。

 which connects not two be connected components， but more than two disconnect connected components。

 if you have something like this， you have another edge here。So would's say it is component 7。

Then these search points connect these free， we connect components， so four is connected to three。

 free is connected to seven， seven connect to four， so you have something like this。

So it's not a tree anymore。And it's bad。We，ll have trees， right， So we want this graph to be a tree。

So how to make this graph tree， we will build a tree of two types of nodes， so we well。

We'll make two types of nodes。 First type of nodes will be the becon components。

 and the second type of nodes will be the articulation points。

 so we'll add another type of nodes for every articulation points in our graph。

 we will add another vertex in this tree。So this four is connected to these6 using these artulation points point。

4 connected to find using this。 These  four，3 and 7 are connected using this circulation point。

Heres like this， and here' is like this。And now this is a tree。Again。

 that's easy to prove this tree if you have a cycle here then everything everything is be connected in this tree and in this cycle。

So you don't have cycles here。 you have or you have the tree and three is a good data structure。

 We know a lot of。Useful algorithms how to analyze the trees。 So again you， you can take your graph。

Condense every icon component into a single node and then build this tree。

Co of these big components and articulation points。And then then you have this compensation。O。

Now's time to find the articulation point。Again， let's do it in two in two steps。 First。

 let's find all the artation points。How to find the points syndrome。We willacy。あ。No， again。

 let's run the process briefly。 Yeah， let's find an overview view。

Let's try to find out if this V is a collection point or not。So if we remove this V from background。

The tree will be split， so you have this parent。So you have something here。And your cur subies。

So if you remove V from the graph。Your graph will be splited into this top top part and these saties。

으으으？そう。If this fee is not articulation point。Then when you remove this be。

There must be some other edges which connects these sub to this。不夺宝。Again， let's see。

 you kind of have edges between these substrate。😡，So。There are no edges like this。Again。

 because it's the tree of depth passage in in depth passage tree。

 you can't have edge between different branches。So if you remove this V。

And these subris are still connected。Then they must be connected to something about this piece of every sub train。

Must have。Some H， which connects this sub to something about this。From each factory， you。

 you need to have something like this。こ。Mmhm。嗯。You going I have no please。Let's write it here。

 So V is not a。Is not。Articulation point。啊啊。Then， for each sub you。For each。Like this。

 So for each child you。I need to have this edge from this substrate to something above。Yes。

 we want to to check this edge exist。 We need to look at the value of up for this old view。And check。

 it is less or equal in time of fee。Yes， all you going say is three to lesson time of V。

 it's the same thing， yeah。You may say Yes， I'll turnt you you may say that it's strictly less than time。

我不。Can you see it， You can。It's the bread mark。You we say this is strictly less than in of B。

 it's the same thing。嗯。That's so in now will just use the same algorithm to find these values of up and just in the end。

 we need to check differently。Here。でもです。So in the end， we need to check。

If all the children have this property。 So if I have this property， so let's check。

Now let's say like this。 So I'll setcal point。Let's see here。 our solution point equal to false。

Is P or？So it's it like push E up。Of you is what like this G in of me。And now， in the end， if。

A P then V is articulation point。That's almost correct。That's almost correct。

 We have one problem in this code， but。Stream recording will be available on YouTube， as always。嗯。

We have one problem in this code。Actually， in this proof。In this proof。

 we assume that this node V has apparent。But not all notess in the tree have parents。We have。

One special note。 We have one special note， which doesn't have any parent。 Yeah。

 it is the root of the train。So for root of the chip， we need to find some special proof。

 So how to check if the root is a。Artcticulation brand。So if you have a root。It doesn't have this。

 So if you have some children off the root。How can these children be connected to each other。y。

The answer is they can't be connected other So if you have several children off the route。

Then if you remove the road， these children will not be connected。So if you have more than one child。

Or of the root node， then the route is a artulation print。嗯。Or， let's see。Or where is the route。

And have more than one children。嗯。How to fix the code？What count the children， but saves。

Gown zero here we have C plus plus， let's say C or。嗯。WeHave no parents。And counters more than one。

 something like this。Just just add some small fixs。For the录。우。That's all。

 that's how you find aulation points in your graph。Now， what if you want to find not onlytic points。

 but also these big connectivity components usually want to by both。 So we want those for each edge。

Find the big connectivity component of this edge。Any ideas。So， this cold。

Finds all the all the articulation points of your graph。 So if you're on this code。

 it will find you all these nodes。Now， you know all the exploration points。

 how to find all the begin activity components。太屁搞会了。Up here。 so so the definition of up is here。

I just left it here。Yes， with bridges。 we can do it like this。

 We can remove the bridges and then find the connect components。

 The calculation point is just little bit。😊，Less on this， because if you just remove this。

About this is from your graph。You will。You will have something strange here。 For example。

 in this bigcon connectivity component， if you remove all these nodes。

 you will have something strange。Yeah， for， for that search， it's easy to ignore the edges。

 You can just mark the edges and then ignore the edges about how to ignore the。Vertices， for example。

 all the vertices of some compound may be articulation points。 You may have something like this。

For this component， all the vertices are articulation prints。So how to find this mechanic component。

So it's a little bit less obvious。What I will do， I will do the same trick like black we did with the edge B connectivity。

 so I will try to construct these big connectivity components at the same time when I find these articulation points。

How to do it again， I will use a sta。But now I will put in in the tech note the vertices， but edges。

So I will add all the edges I visit。Ian vi thick。No。When I find some articulation points。

 So if this note is articulation point。If this order is ocean point， it means I have some subre。

So I have this sub， which is not connected。Do something above。 So when I remove this。

When I remove this vertex， this sub will be a separate connect component。Now， in this sub。

I need to take all the edges。Which were added after this edge video。 Again。

 I will use the same buffer。So， I will use the buffer。In this buffer， I will add all the。

All the edges I see。And now， when I go here， I will add this edge V U into this bathroom。

And then when I go back。哎，那我问。Something here。Is the big connect component。

And something here is exactly all the edges I added after this view。

 So why I have this no edge view and some edges after this and all these edges。

Belong to be a component of this H V U。This is， this is component of edge view。Tster板。嗯h哼ん。😊。

Let's try， let's try to implement this。 Let's try to implement this。Look here。 When I enter this DFS。

I will。And these。Edge V U to the buffer。And also I need to add all the edges。

 I I need to add not only the edges of this tree， but also these green edges which connects to something。

 So here， here， here， here， when I see the edge which does move to the tree。

 I also will add it to the bathroom。And these thing goes， so we we find this child。

 which is not connected to here， so this child and everything here is a UB connectedn component。

So I'll say this is become a component and then move next。And here， so。 And again， here here we。

 you need to remove。Everything。I want not write the same code。フロ booth。嗯嗯。Yeah。안。Until age。还是有。No。

 no， no， no， not no。Here you need to it here。そつれです。一。It load here。So， here。If you find that up。

If up of you is greater Or than chill in of V。So then this component will be removed。 so I need to。

Let's do something。 Okay， and， okay， let's try this。So again， I make the new connect component。

And just remove everything。Again， X is a bomb bath。보プ。Add that tool。Just the centric。If X is V U。

 then break。Like this。嗯。Okay， a little bit ugly， but good enough。That's all。

 that's how we find big components in the graph。Cool， now。

 both these algorithms works in linear time。 obviously， yeah。

 So both these algorithms like the algorithm we used for finding the bridges and edge between connectivity components。

 and these algorithm fine articulation points and vertex between image components。

 they both work in linear time because we just have this one DFS。

 So the total time of this DFS is linear by the number of edges in your graph。 Yeah。

 that's quite obvious。😊，Cool，没错。I'm not sure if I want to do it today， but let's do it today。

 I need some more time。To discuss。The oil cycles。Because I will not have。

Any space in any other lecture。 So we will discuss today。Hope you're not doing her song。

Is any is anything clear right now。 I will just。I will arrange everything， and。

Talk about order cycles。We need extra case for the route。 actually we don't。

 So you need extra case if you want to check if the point is articulation point or not。

 but if you want to find these big connectivity components， you don't have a special case。

In the root， you will just。You will just run this if every time。 So for every child of the root。

 you will you will run this ifve。 So in the end， you will pop everything from the step。 Yeah。

 so if you have one child。 So you will run into this one chat。

 And when you return from this recursion， you will pop the last。Becon component。

And if you have several children off the route， you will just pop from this deck。

Every bi component you run this regressioncursion， then go back and then pop your next bi component。

You don't have any special cases here。Okay。Okay， now let's move to the next topic。Okay。

 little bit too much for one lecture， but。It will， it will be easier。will be easy。走。

So another algorithm which uses the depthest stretch kind of is the algorithm refined set order your。

Or maybe we need to move to another lecture。嗯。我算吃。Sleure will be too long。

So I need like 20 more minutes to discuss the other cycles。Okay， are you brave enough so。

Should we discuss order cycles today or move it to the next lecture。Let's walk。嗯。Okay。

We have one vote for today， one vote for next。I'm not hurry， but。Maybe you are too tired。

It's a little bit overwhelming for the single lecture。Okay， let's do it now Google。It will be。

 will be first。No very first explanation of the os。So in some graphs。You may have the order to order。

 It's the very simple thing。 So it's a cycle which contains every edge exactly once。嗯。嗯うん。

Let's have something like this。嗯呵呵。嗯。like this。So we can build a cycle which contains every age exactly once。

For example， here you may have something like you may go here， then go here。Then， for example。

 goes here。거 히 히。Then go here here。Or just visit all the edges exactly once。

These are special graphic autographs。嗯。It it is defined for both directed and undirected graphs in undirected graphs to just。

Can travel each edge in any direction in direct graph。

 You need to travel each edge in the direction of this edge。

So there is very simple property which which you can check if you want to check if your graph contains sellers like。

For direct graph， you just need to check that every node have a even degree。 So for every。

 for every ver of your graph， you must have even number。Of edges。And for direct graphing。

 just need to check that every age have the same number of ingoing edges and outgoing edges。

 So you have some number of ingoing edges， and you must have the same number of out edges。A special。

 very simple property is easy to see that it is sufficient so certain reduce。This is required。

It's easy to see that this property is required。 Yeah， because if you have some odd number of edges。

 then you can have a cycle which goes through this edge not because each time you go through this edge。

 you mark two edges of this node。 So you must have even number of edges and similar here。

 So if you have different number of outgoing and ingoing edges。

 you will not have a cycle because each cycle， we just with some ingo and edge and then visit some outgoing edge。

こ。And it turns out it's actually it's actually sufficient。 So this property is enough。

Pgraph to have a order cycle。Alrith， The algorithm was very simple， very simple algorithm。

So how to find order cycle。Okay。Ill just re。我去住。You run death for search like of Grithin。

Slightly different。So you need to modify your data search， so it mark not the nodes， but the edges。

 so you want to visit the same vertex multiple times， but you want to visit each nodes only once。

 each each edge only once。For no yes， you also need to check the connectivity。

 The simple connectivity is enough for both direct Androidgraph。

If you have oil on the graph and it is connected， it is strongly connected。It's easy to prove。

We will prove it just because you have for a recycle and this soil recycle。

 we will give you the strong connectivity， doesn't matter。Yes。

 you also need to check that your graph is connected。It's， it's obvious， okay。到。The algorithm。

 the algorithm is very simple。 you start your depth for search。

 but slightly different depth of search。 you want to mark not the vers， but the edges of your graph。

And you want， you may visit the same note multiple times， but you don't want to visit the same age。

 multiple terms。So we start from Samung。Take any edge。

And run the aggressively around the investment store。 For example， you take this edge。

then let's say take this edge。そ系啦系啦。Then。Well， let's go back just to make it interesting。

So we' go back and then let's say go here。Then go here。And go here。So at some point。

 you run out of edges。 So at some point， you go to some nodes and you。

 you don't have any outgoing edges which are not marked。 So every age of this。The verex is marked。

Then you go back from the recursion。And add this lastnob， a last edge to your motorcycle cycle。

So from here you go back and add this last。えしと your answer。Now again， from here， it's over to go。

 So you go back from the curtainsion， go here。And add this note to your answer。

 now your answer contains these two edges。Hello。Now we're sitting here。There are more edges。

 from this now。 So So you， again， you take any edge， which is not marked yet。

And use this edge for your deposit。 Yes， from here， you may go here， then go here， then go back here。

And here again， you have nowhere to go， so you stop the regression。

 return to the previous note and add this last edge to your answer。So youll go back from here。

And at this edge， to answer。算。ち。And add this edge here。And so now it's simple。 Now。

 every time you go back here at this edge， then go back at this edge and so on。 in then。

 you will have this cycle。That's whole， that's the hopeland。 Let's， let's let me。Des right the court。

So we are the first for this old。Yeah， what do we do， We take。Anyion edge， which is not marked。

Let say， while。Have have a mark。Will take any edge。嗯。えにあのマルト。We take any unmarked edge。

Were going from the this snow be。market。And then run the difference。お。

And when we return from this DFS。We add this edge。 V U do the answer。 So it is。Re select answer。

H this H P。This whole one。That's the home plan。That's错 all没事好我给。We need to specify some details here。

 but it's actually， it's actually quite。Simple。Now， first， before， before we specify these details。

 let's talk about why why this silicon algorithm actually works。Zu。Why this algorithm actually First。

 let's see that these algorithms actually visit all the edges of your graph。

 So if your graph is connected。Then here， I will visit every no every edge of my graph。

because I will visit each vertex at least once and for each vertex， I will visit all the edges。

 So when when the something finishes， all the edges are marked。 So I will add all。

 And if edges marked， then it will be added to the result。 So so this。

This path will contain all the edges of my graph。Exactly once， yeah。And。Now。

 we just need to prove that this。Answer is actually a path， because I added some。

Eges into this array。I need to prove that these edges are actually connected in a path in So if you take these edges in this order。

 you will have some path。It's actually easy to prove， let's see。What's Sky algorithm？

 So we just started thumb。So you start in some note。And then just use any note。Do for your D sorry。

 So you go somewhere。But then you go here， go here， go here， go here at some point。

 you stop into some， you stop in some node V。And in this note fee， you， you have no no almar edge。

So you stop this discussion。How might happens this this node have no a marked edge。

 Well Let's see if all degrees of all。Well this is well even。

So if I have even degree for all nodes of my graph， then each time I mark two edges。

 so for each for each ver here， I mark this edge and this edge， so if degree was even before。

 then I mark two edges connected to this node， then degree is still even so。At any point。

For every note， the number of unmarked edge is even。Right。Right。For this node V。

I marked one edge here。So， the number of。Unmark age must be odd。0 is not not number。Obviously。嗯哼。😊。

So for this node V， there must be some another unmarked edge。So the degree of this view was even。

Then each time I visit this V， I I must， I may visit this V multiple times。

 So I may visit here and so on。 So every time I visit the V， I mark two edges of this movie。

 So the number of these edges is still even。And here， I marked another edge。

So the total number of edges unmarked unmarked edges connected to this V must be odd at this point。

But somehow it turns out I have no outgoing edges。Mhmm。😊，If the number is even if if。

 if the number is old， it can， it can't be 0。 Yeah， because0 is an even number。

So how could it happen so I stop in this node V and have nowhere to go。How could they cable it。Sorry。

How can it happen？嗯。Let's see， again， I carry the snow。What happened to this node。So I run this DFS。

 so every time I run through this node V， I mark to edges this edge and this edge。

 Then again I run here， I mark to edge this edge and this edge。And at some point， I run again。

 mark this edge， and I have nowhere to go。But I marked。Old number of edges。

 So there must be at least one edge。Iま。嗯。So how could it happen that I have nowhere to go from this node？

Start or end。what does exactly mean？But you obviously will stop something here？At some point。

 you will stop。So there must be some case when you actually have nowhere to go。How good 가。嗯。

Any it ideas？If all edges visit it， but I can't visit all the edges because each time I visit two edges and the total number of edges is even。

So if I have edge， which I use to go into this node V， then I have another edge。

 which I use to go out of this nodev。So if I somehow go in， then I have another edge。

 which I can use to go out this only。We actually have one special note in this。

 so in this picture we have one special note and this note is S。

 so this this note S is actually special。For this note S。Because I started here。

 I marked this first edge。 So now this degree of this S is odd。 So all other nodes have even degree。

 but this S has no odd degree。 odd number of unmarked edges。Mmhm。😊，And this is actually special。

If I am for this known S or E。So if I started in this note， S。Let's see what happened。

 So in this note S， I started my DFS。 So I run here， then I run here。And then I may stack here。

 so I run here， then go back， then run here， then go back。

 and now I stuck because I have no other edges to go。So for node S。

 it may happen an actually the only node。Which have this property。So， the only note， which。

May have no outgoing age。Is actually the node S。 So actually picture doesn't look like this。

 It looks like this。 So I， I start in note S， then go somewhere， you take any edge and go somewhere。

 And at some point， I will stack at the same node S。Because S is the only point。

 the only vertex which has all degree。Becauseuse I used one of the edges when I started the D S。

 All other all other words have even degree。Okay。That's all， so。

 so the first time I run out of these edges is when I standing in this node S。 and now I go back。

 So you go back， you add these edges to your result。And then at some point。

 you make branch from here， you make a branch go somewhere again。

Now let's find the second time when we start， so。When at one point can be stack in which real。

 we may again run out of unmarked ages。No， it turns out they only again。

 if you look at the picture is quite simple。 So the only node which has even degree。

 which has own degree。Again， all the nose happen。Even degree， except this one node。

 So this is the only node。Which has even which has all degree now。So if we stuck in some node。

 it may be only in this。Point。So the next time you will run out of these edges。

Is when you stuck into this stuck in this point， so you will do something and then again stop here。

嗯哼。And when you stop here， you go back from your recursion and add this edge to your result。

And this edge。Will be connected again to the end of your current web。 So this is。

 this is the current web。Your current results。So the end。

Of your current pair is the only note which has even degree， which has all degree green。

So if you run out of unmarked edges， it may happen only in this last note of your result。

So when you go back from the recurs。You add this edge to your result。

And this edge will always be connected to this part of your。Answer。嗯哼。And so again。

 now now you do the same thing。 so you go somewhere。 Then again， you make some branch。

Can go somewhere。 Again， this is the only point who have all degree。So， if you stock。

In this day fresh， it may be only here。That's all。So we just prove。

All we put all the edges into this answer and all the edges in this answer will be connected to one one to each other。

So， these edges will form some pathth。So it will be some breadth which contains all the edges of your graph。

 so it will be some orator。Okay， final， final thing。 how to implement it efficiently。

 So to implement this this efficiently。 We need some data structure。

We need some data structure which which will contain all the unmarked edges for4 for4 and node。

And we need for this data structure to have two operations。 We need to be able to find any。

Any edge from this set。And we need to mark the。So basically。

 what we need to have a set of all unmarked edges。And we need to have two operations。

 plus it's actually a single operation。So this separation takes any element from the set and removes it from the set。

Yes， you may use sets in C++， but it's actually over communication you don't need to find any specific element in your set。

 you must take any element of a set and remove it。So you may use for example， sticks。

YouUse uses the defect vector。 here。 So you uses the de vector for this。So for this node V， yeah。

 you have this。Least。Of all unmarked edges。In the beginning。

 you just put all the edges into this list。Now here you will just take the last element from this list。

 this element。And remove it from the list。It's a little bit。

It's little bit more complicated when you have Androiddirectgraphs。In undirect graphs。

 you need to actually remove this element from both lists。 So here you have this edge video yeah。

In the end of this list and for the old view。You may have no theory or。Edge Ua in this list。

So if you have undirected graph。It's a little bit more complicated。 So you need to remove。

 You need to mark this edge here and here。So here you just remove this element。From the least。

But now you need to remove this element。From the middle of the list。

 And it is a little bit more complicated。呃。There are various ways to solve it。

You may have a pointer from here to here and have linked list so you can remove element from the middle。

One possible solution。Another possible solution is to remember the position of this element here and then swap it with the last element and then remove it from the end of this。

At least。Also possible。 the easiest way to solve this is actually to mark。 actually。What we can do。

意ese。To have like object for each edge， you have some object which contains information about about this age。

 And so you have this。And so from both these positions， you just have a pointer to this object。

And now when you visit the first time here。You remove it from this stack， and mark。Market here。

 just have a Booleant value if this edge is marked a lot。And now it just don't remove it from here。

So you remove it from this stack。And넌들이 먹 here。And you will remove it from this stack when it will be the last element。

 So some at some point at some point。This element became the last element of this stack。

So you will try to use this element here。As a market， but you will see it。 it's already marked。

So well just keep this edge and remove from the stack。 So it just it ca it。 It's just like lazy。呃。

I don know， La removal of the elements。 So So you mark the elements that it must be removed。

 but you don't remove it Now。 You will remove it when it will be the last element。잘 될 때。

So we have various different solutions。 all of them work in constant time。

 So all this solution will give you the linear time complexity for this order。Oh， it was a， okay。

 it was a long lecture。Thank you， for Jamie today。🎼Yeah。🎼。

