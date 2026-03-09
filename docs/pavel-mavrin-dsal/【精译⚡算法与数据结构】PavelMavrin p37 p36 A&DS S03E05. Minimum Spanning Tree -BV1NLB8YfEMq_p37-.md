# 【精译⚡算法与数据结构】PavelMavrin p37 p36 A&DS S03E05. Minimum Spanning Tree -BV1NLB8YfEMq_p37-

🎼The。🎼こ当。

![](img/8823a3d7b227166a10d39981ef2f4ca9_1.png)

🎼So today， we talk about minimal span trees and some similar problems like minimum options problem。



![](img/8823a3d7b227166a10d39981ef2f4ca9_3.png)

嗯。Let's go。 so minimal spliting tree。

![](img/8823a3d7b227166a10d39981ef2f4ca9_5.png)

![](img/8823a3d7b227166a10d39981ef2f4ca9_6.png)

Let's have some un drop。

![](img/8823a3d7b227166a10d39981ef2f4ca9_8.png)

Have some object。Let's say something like this。

![](img/8823a3d7b227166a10d39981ef2f4ca9_10.png)

But something like that。So the spinning tree is a tree which contains all the nodes of your graph。

So if your graph is connected it always contains some spinningning tree， for example。

 you can make something like you can make def search and take this depth search tree as a spinning tree So every tree which contains all the nodes of your graph is a spinning tree For example。

 let's put something like this on for example， if we take this edge。

 this edge and let's say this edge then go here and take this edge plus this edge。



![](img/8823a3d7b227166a10d39981ef2f4ca9_12.png)

![](img/8823a3d7b227166a10d39981ef2f4ca9_13.png)

And let's say something like these and these。

![](img/8823a3d7b227166a10d39981ef2f4ca9_15.png)

Okay。

![](img/8823a3d7b227166a10d39981ef2f4ca9_17.png)

So if you take these edges of your graph， you will have some spinning tree of your graph。It's simple。

So what is what are we trying to find， what trying to find the minimum spend train， Not is minimum。

 Imagineagining each edge has some weight。

![](img/8823a3d7b227166a10d39981ef2f4ca9_19.png)

For example， let's put some weight some old ages。

![](img/8823a3d7b227166a10d39981ef2f4ca9_21.png)

S then three， then four， and eight。It's 8。And five and say10 here and one here free here。

5 here and 6 here， and。2 and 7 and 10。6 again。And I don't know。



![](img/8823a3d7b227166a10d39981ef2f4ca9_23.png)

Quite when。So if you have a tree like this， the weight of the tree is just the sun of all weights of all ages。

 example for these tree， the sun will be5 plus phrase，8，9。



![](img/8823a3d7b227166a10d39981ef2f4ca9_25.png)

12。1621，23。W you I break。Soong。The weight of the tree is just sum of all ways， it is 29 for this。



![](img/8823a3d7b227166a10d39981ef2f4ca9_27.png)

Now， what we try to do is we try to build a spinning tree with minimum total cost of all ages。

 total weight of all ages， you can call them costs or rates。

 it doesn't matter have only one value so。Does't matter how we called it。

So that's the whole problem you have graph， each edge has some core or some weight。

 and we want to find some connected structure with minimal total sum。And it's quite useful。

 for example， if you have example， if you just want to connect all the nodes。

 you have some nodes of your graph and you want to somehow connect all of them。

 so the minimal connected structure of the graph is some spinning tree if you have a cycle you can always remove one edge from the cycle and the total total sum will be decreased。

if if all rates are non， non negative。So the minimal structure。

 which connects old node photograph is some spinning tree。



![](img/8823a3d7b227166a10d39981ef2f4ca9_29.png)

And we want to find the spa tree which have minimal total cost， mean minimal total weight。

 something like this。

![](img/8823a3d7b227166a10d39981ef2f4ca9_31.png)

That's the whole that's the whole problem。It's actually quite simple。



![](img/8823a3d7b227166a10d39981ef2f4ca9_33.png)

No。To solve this problem， there are many interesting algorithms。

Most of them are based on the same lema first before。Discuss all this our business。

 I will prove one simple le。

![](img/8823a3d7b227166a10d39981ef2f4ca9_35.png)

It looks like this。imaginemine you split the nodes of your graph into two groups。

 so you have all nodes of your graph， you're just split them into two not into two second sec。



![](img/8823a3d7b227166a10d39981ef2f4ca9_37.png)

First set will be 8， and the second set will be B。And now you look on all edges which connects A to B。

 so you look on all edges between these two sets。

![](img/8823a3d7b227166a10d39981ef2f4ca9_39.png)

Now， let's find the minimal edge among all edges in this group。

 So we find the minimal edge in the which connect connects A to B。 It's actually called a cut。

 So when we will discuss。Flows， it， it will make much more sense。 but but right now。

 it's not important。 So if you， if you know how the maximum flow work， it's kinda， kind of the same。

 but。AndIt's not not that important， so we just split all in notes into two groups。

And look on all edges which connects these groups。Now。

 let's take the minimum age and want all these edges。So we'll find the edge UVv。

Such that it has minimal。Wai。And U is in a， and V is in B。That's why this stage。

So this is the minimum edge。Yeah， it's nice shirt。 Yeah。 It's one of the cotton heroes around yeah。

I always participate in couple hero surround just because of the T shirts。

 so let's find this minimum edge。Now， the lemon is very simple。 If you have this edge。

 this edge should belong to some minimal span tree。ま呃。Sometimes there is not unique way success。

 I there may be multiple ways to construct minimal pain increase。

 so it belongs to sum of minimal pain increase， so if there are multiple pain trees。

 then it belongs to one of them。For example， if all postss are equal。

 then any spinningning tree is a minimal spinningning tree。

Sos sometimes there's no unique way to construct the mineral spry， but if。

If this this is the minimum edge on all these edges。

 then there is some minimal spinning tree which contains the edge you。Yes。

 if all the costs are distinct， then it is a unique way to construct minimum battery。

 We will prove it in in a moment。 We will prove it by right now， it's not。That's obvious。

 but it's actually wrong yeah。But if you have equal cost for some edges there may be different ways to construct mineral sptry。

In in that case， there is some minimal pantry， which contains the HV，Now let's prove this。Let's。

 So let's take some minimal spinning train。Let's look on this spec spec in this minimal span tree。

Notes UNV must be connected。It's literally written of the board here。

 So U V is the minimum H among all edges such that U belongs to A and V belongs to B。

 So we split all the nodes of graph into groups and take the minimal age between these groups。Now。

 let's take this minimal spinninging tree。In this minimal pin tree。

Not you and we are connected somehow， so there is a path。Which belongs to the MSD。

 which can connects you to this。 So there is some pe。This path is inside。Yeah。

So there must be some pathth from U2。Such that all edges on this bed belong to MST。Now。

 you belong to set A。And B， and we belongs to be。So on this path， at some point。

 we must switch from a to B。 So on this path， there must be some H。Let's say， H， X， white。

Such that X belongs to A and E Y belongs to B。So for this stage。嗯哼。Now， what can we do。

 We can take this minimal span tree。Remove this H X， Y and add this new H to。We will get again。

 a spinning tree。And the cost of this paintingtry will be not greater than the cost of this paintingtry because we have the minimal edge。

 so the cost of the H UVv。Or U V is not。Greater than the cost of H E， X， Y。So if we remove H， X。

 Y and L H。UV will have another spinning tree， and the cost of this tree will be not greater than the cost of that tree。

So now we have the minimum penaltyity， which contains the edge QV。Its all。 that's the whole proof。

Why does stay in Spain prove this。sLet's prove this is dream。うん。It's quite exactly on people。Okay。

 easiest way to prove this is just to prove that all the nodes are connected again。

 So we have the number of edges is the same。 If we prove that all nodes are connected。

 then we prove that we have a tree， right。No。How to prove all nodes are connected。

 Let's take any two notes。And look on the path within these notes。 If this path contains this H X， Y。

 then instead。 So let's take any two notes。A and B，This noise was connected in this graph。

 so we have we had some path now if this path contained。X， Y。Then we will remove this X。

 Y and add this edges test。 So instead of this X， Y， let's add all this。Path， can they know U。

And now we have pair from A to B。 So every pair of node disconnect。你。

That's one of the one of the way to prove is。 Another way。

 just to look what happened if you add if you， if you add edge to the tree， you will have some cycle。

 right。Now this cycle contains this H X， Y。So now you have just a a tree with one1 extra h。

 you have this tree and one extra h。 We have this cycle and something here。

So after you add this new H， Uv。You will have situation like this。

Now you remove one edge from this cycle， this edge。And now again， you have a tree。

There's just more visual way to prove this。Okay。Co。

Now that's the whole limit that's actually the only la we'll need in these algorithms。Now。

 let's build some algorithms from the Muslimle。We will learn three different options。

One of the most common algorithm is actually there。그러 거 아 그랬。How to spread it correctly。

 and let me check。嗯。Both k。So across the， I'll get into the venine bowl， let's take the graph， let's。

Just remove this right now。

![](img/8823a3d7b227166a10d39981ef2f4ca9_41.png)

Let's take the graph，s let's find the minimal edge。

 so let's find let's sort all the edges by the cost by the weight and take the minimal one so for example here we have this edge one。

Easy acceleration。 This edge1 should belong to some minimal pen tree。

Why this H1 should belong to some minimal spell tree。

 Because we can look on any cut which contains this edge。 for example。

 you can look on the cut from this node and everything else。Again， let's find this Min edge。

This minimal edge is a minimal edge in some parts。 For example， we can take cut。

 We can say this edge is A and everything else is B。So this edge will be minimal age in discard。

So minimal edge in this card should belong to some minimum span tree。

 So let's just add this edge to the minimum span tree。So just take this edge and the minimal spin。

That's all。 Now， let's take the next edge。 It will be this age 2。This age2。

Also should be in some minimal span tray。 wipe， let's take a cut。

From these two ages or from these two notes and everything else。

S with this H 2 is minimal edge in this cut。 So it must belong to this furniture。なそ。

So now each time we just look on the minimal edge and try to add it to our spinning training。嗯。

It's too boring， again。I don't know how contract will grasp for these algorithm。 So add this three。

 add this three， add this four， add this five， and this five。Now。At some point。

 we will try to add this a shot。This edge shouldn't belong to minimal pantry。

 because if we add this edge。We will have a cycle and we don't want to have cycles in our minimum in our spinning trees right。

 so if we take the next edge in a sorted order and try to add this edge to our spinning tree and we see that we will get a cycle if we add this edge to our spinning tree。

Then we just skip this edge and go to the next stage。What does it mean。

 it means actually that this edge is not minimal in any cards because these two nodes are connected。

 so we have this path。So in any cut， there will be this pair and all edges on this pair are less than this edge。

That actually what Disney mean。So if we have this edge and if we try to edit it。

 we'll have the cycle。Let me just keep this edge and take the next edge。

AndSo we just skip this edge and find next h this six if we add this six again， we will have a cycle。

 so we skip this six。Take B6， B6 will form cycle zone any zone。This's the hole，s the hope one。

So the plants like these shortages。So E is just a set of all edges， just for simplicity。

 now we iterate our all edges。Hi， just very stay your language today。

That's not usually how you write cycles and how you write loops in your programming language that's good on。

嗯。So its really this unique medium， yes， if this edge is unique minimum in the cut。

 it must belong to any mini spin trail source correctly。ItPro the exactly look face。Now。

 let's take some。 Let's let's， let's iterate all edges in the sorted water。 Let's try to if this。

You and we。I not。깐 날 이렇게지。Ian Car hostte。Let we end。嗯。Let the we end。This edge U V to M D。

That's the hope，'s the hopele， this code works。So we sort all the edges by， by， by the weight。

 and then iterate or all edges in this order。 And if these nodes are not yet connected by this min pantry。

 we add this edge and connect them。usingsing this age。That's the whole one。

Now what is the fastest way to check if two nodes are connected， Yes。

 like you mentioned origin check， the easiest the data structure which I answer these questions is the union find the structure from the previous semester so we can use union find the structure or just joins of union name obviously in the structure so we can use this union find the structure to check if two nodes are connected and to connect them。

So's let's modify it a little， so。我次一。If find。Of you is not equal to find。Of fee。

 then we just make a union。Of you and the。This is basically the whole crossco algorithm。

Pretty simple。 to work Pre fast。So now let's talk about10 complexity。What does the time up like this。

What's the products your funeral file？But's， let's start with with this， this。

So this line is executed M times。And these line is actually is huge 10 times。嗯。Yes。

 we can use all the as from from the union find structure。 It's just simple union final structure。

 you can you can use both the random characteristicss and path compression。 Why not。

So if we give both theuristics there。Complexity of the inspiration will be。I fair man。对。But yeah。

 unfortunately， we also have this sort。And this sort is actually the most slow part of this algorithm。

 So the slowest part of this algorithm is actually sorting all the edges by， by the way。

 this sorting costs M log。M loggan time so the total time complexity so this will be much less than this。

 so this is the slowest part， so total time complexity will be M loggan。Okay。や。

Or M log n actually does matter， so log of M of M and N is actually the same thing yeah。

Well because the m is about n square and logarithm of n square is about the same as logarithm n。

 just by constant factor。It's a good question。 If it is possible to solve a linear time。

 We will talk about it。In a， in the end， okay。嗯。The answer is actually， we don't know this spoilers。

 but we'll talk about it inland。啊。Now， this is the first very simple algorithm。

 which allows you to build the minimal spending tree in this time。Now the next algorithm。

 the next algorithm is called the Pri algorithm。嗯。I need to raise something。



![](img/8823a3d7b227166a10d39981ef2f4ca9_43.png)

不有。Its spring right。Just check。That's Prince。English is 있어하우스스？그래。English is difficult。嗯，O。Now。

 the algorithm。Let's use the same idea。 bars differently。 Let's use differently。 So again， again。

 let's let's look on this graph。Let's take the go。

![](img/8823a3d7b227166a10d39981ef2f4ca9_45.png)

Let's take any note of this graph and call is not a starting mode， for example， let's take。

I don't let's take these notes。And say， this note is a starting note。Of the algorithm。Now。

 each time we'll do the following， we'll find the minimal edge in the cut。

From this note to everything else。So now we have only this node。

So let's say this node belong to save a。Everything else bumps at be。

Let's find the minimal edge between A and B。 It will be one of these edges。 Which one you like most。

Let's take these old age， for example。So we find the minimal h between this A and everything else。



![](img/8823a3d7b227166a10d39981ef2f4ca9_47.png)

This will be this edge。 So we add this edge to this。그래서。And put this note in the set tape。Now， again。

 let's try to find the minimum age between a and everything else。

So we have this set A and everything else。Between this and everything else， this is the minimum edge。

 so we take this edge， add it to the result。Now， could these known in。And so on。

 each time we have some current set A and everything else。So we have some set a。And everything else。

We look on all edges。Here。Find the minimum edge。Again， I just。

Minimal H such that U belongs to A and V does belong to。And we add this edge to the spinning tree。

So we add this edge to the span tree and now move this V to set H。Like， what look？

Let me right write a code。 So first， the a contains only。oneの space。

So we start by putting one of the nodes of the graph into this cell。And now each time。

Let me write it in court in way again。Like this。So we just repeat n minus1 times the whole operation。

 we take the minimal edge between a and everything else。Let's take， I will just write a serial code。

 very serial code。 It will be the minimum edge。Such that U belongs to A and V does not。

And we just Ed。This U V。To MT。And add this。V2， set a。It's right if you have the court， okay。

Clear enough。Again， it's quite easy to prove that it is correct algorithm again。

 just by using the same lemma we proof in the beginning of lecture。

Just every time we just just apply the same la so we take some cut in this cut to find the minimum edge。

 add this edge to the result and so on then repeat this process until we have the tree。That's all。

Now， what is the tank of this order， No again。Thank ofing。Actually， it's very pseudo code。

 so to find that complexity， we need to find the appropriate data structure。

So we need to find the proper data structure， which allows us to find this minimum。

And make these modifications。So yeah， we need some data structure。Which is good to find minimums。

So we need to find these minimums。And we need to modify the set。い。😊，嗯。There are actually two ways。

So we will discuss two data structures we can use here。教し。No first idea。

 Let's just put all these edges into some priority secure。Let's use some binary he， for example。

 let's just use binary he to keep the track of all the edges between as。Just do it here。嗯。

So if we have a prioritygic queue and we'll just put all the edges we need into this prioritygic queue。

So first， we have this priorityic Q， it will contain。All the ages from S to V， yeah。嗯。啊。

All all edge just going from。Now， we get a is just as。Now， we just again really bit。It wouldn repeat。

And -1 times the whole in would take the minimum element from the Q。嗯。哎。

Let's say youre removing justice。It是시。And now we need to modify the set a。 So when we add。

When we add vertex v to set A， we actually need to modify the set。

 which is currently in our cube because since we move this V to the set A。

Some edges should be put inside the cube。 Some edges should be removed from so。

 So let's iterate all edges。Connected to this node。V。So we have some edges like this。

If this U is in set not in set a。哦。If this verx Q is not an a。

 then we need to put this edge into primary secure。 because again， before we have V not an A。

 you not an A。 And now we have V in A， you not an A。 So this edge should be put into the。不有。And。

 if not。Then we actually need to remove this edge because this edge is something like this。

 So if we have edge from V to something inside a， then now we need to remove this edge。Yes。예 모르나？

I think it actually should work just like this。Now， this will contain complexity。

 So what happens with time complexity。 We use some purely secure as here。 We use it here， and here。

How many times did you call this separation， This separation is called exactly n times n minus9 times。

 So we have nspirations like this。And what about these operationss。

 these operationss I actually called for every age of the effort so every time we take some no sorry every vertex will be moved to set a exactly ones。

So this V will be it for all nodes and graph and each vertex we will be here in exactly once。

 So here we trade all edges of this vertex v。 So we will it rate for all edges of the graph exactly once。

 So these separations will be called for each edge exactly once。 So we have ems like this。

It of course。 Yeah， we will modify the little。 Yes， we will modify the short them。 Yeah， yeah。

're right。 You're right。 Thiss just the first version。Yes。

I believe it's just more easy way to understand what's going on here and we will improve it later。

So now， if you use any parent queue basically。Like。Wry he。 Why not。

Then you can achieve a complexity log n for all the operations。

 so both these operations will work in log in  time so total time complexity again will be。

And look at。要。Now， let's try to improve it。How will improve this？Other thing。 no， let's see。

 We actually keep too many edges in our player。当。Let's see here。So what's going on now。

 we have this set day and we have everything else。And we just try to put all the edges。

Between these two sets in into operator secure， that's too many edges。 actually。

 we don't think that many edges。啊。Exle for each node in which is not an A。

 we need actually only one edge， the minimum edge， which connects it to set a。

So for if we have multiple edges for this node V。For all these edges。

 we only need to keep track of only one edge， which minimal edge。

If this edge is not a minimal among these edges， it will never be minimum among all edges here。

So for each verex fee， which is not in set A。We need only to take care about one edge。

 which is the minimum edge。Let's do， let's do it。嗯。不要速度。그러가 될 것。



![](img/8823a3d7b227166a10d39981ef2f4ca9_49.png)

It's a graph historian。O。So the plan， the blend， for each node， which is not in set A。

 we will remember the minimum age， which connects to us。What's the D of V。Is the minimum edge？呃。

 do set a。这民県民。Of all bas U V such that you is in。Now， let's modify this order。 So， again。

 we we do the same thing including and so on。A is the set as。For all。AndWe， we have。

D of V is cost of S V。 That's just the initiation of distinction。

 Now we just repeat the same procedure。Yes， and then we put to them all in the queue，Now。

 what we'll do， we will take the minimum。D from all these elements here。 So again。

 we want to find the minimal edge， which connects set a and everything else for each node。

 we remember one minimal edge。And now for all these notess， we will take the minimum one。

We will take the minimum of all minimums。 It will be the minimum of all possible edges。嗯哼。Again。

 once again。For each node here， we remember the minimum edge from all the edges which connects a to this node。

And now we will take minimum of all these minimums。It will be the minimum of all ages。

We kind of split all the elements into all these edges into groups in each group we find the minimum and now we take minimum of all these minimums。

Right。So， here we' look at。Well take this load V。 It will be minimum in our Q。No what's through。そごね。

I just do it in one operation， I will find it and remove it。Again。This periodic Q。

 we have all the notess sorted by this D by this value D。嗯哼。

If I remove the minimum element from priorityic Q， I will find the minimal value of the。

So he the minimum。Well you did。In by itself， it's a minimum of all in edges。So for each node。

 I have minimum fogon edges and now I take minimum all this minimums。

It will be the minimum four ages。嗯。예？I will repeat again by Angel from。Again， what's going on here？

I want to implement this， I want to find minimal edge which connects something from you from sampling from a to something not from a。

To do this， I will keep track of minimum for H node V for each node V。

 I will take the minimum of all edges like this and put it here into D。

And now I take minimum of all possible D。And it will be the minimum for ages。Okay 커不 good。

Now I find this node V。 I need to move it to set a and modify data structure。

 So how to modify data structure again， if I move this node V to set a。Ok， this picture is right。あ。

fishally。So when I move this V to set a。I need talk on all again， on all ages。From this note here。

So it's very all。For all ages for you。啊，M。No， right now， here。

 I just put this edge into the pur secure。 but here is something different。 Yeah。 here。

 I just need to update the value of D。So， for this node。Now I have one more edge connectedors。

To this。 So I just need to update this for。 So I need to update G U as minimum。Of previous radio。

And the cost of this edge。If the graph is not connected。

 you can you can always add some extra edges to make it connected。

 This doesn't mention I will Ill I'll assume the graph is connected。

 if the graph is not connected and you want to buy it， you build not a tree。

 but a forest of trees for each country， you can just split it into connect components and build a tree inside each component separately。

一次点。嗯。That's that's all， so。 Now we have the value of D。Now。

 what we need to do is update date the priority here。Because in the priority Q。We kinda。

So we sort all the elements in the priority Q by these values of D。 So in the priority Q。

 we take this minimum D。 So so all the elements in the priority Q are sort by this value of D。

 So when we change the value of D， we can change the key in the priority Q and we need to update the priority Q。

So in the you。We need to update。This element to you。嗯哼。😊，For example， if if you。

 if you have a binary hip， you needs to si this element up。 So you change the key of the element。

 you need to sift it up to make the priority Q。Ready it again， Rick？That's horrible dealing。No。

 you apparently， you can just remove the element， update the value。

 and then put it back in in the periodQ。 That's one of the way to do it。Kown as in conferences，어지。

Not always。 I， I believe it's too late to make an announcement。

I believe everybody who wants to watch this lecture here。不知道。Thiss the。All the best viewers are here。

I believe。那。That's all。 Now， let's go time complexity， Again， time complexity。Let's see。

And let's look on all operations in on。 we have this operation， This operation is called end times。

And this it is called ample timess。Now， again， if you just use the basic。Bter he。

Then both operations will work in。Logan time。 So if you just use， if you use binary hip。あ。

So if you use binary he。And both operations will work in log on time。So we will have engan here。

 Mloggan here， so total time complexity， it will be Mloggan。But sometimes it's not。 it's not。

 It's not the best destruction， for example， if。If M is big， and n is small。

Then you kind of want to make this operation faster and this operation slower。And for example。

 you may use very efficient data structure， which is called an array， so if you just use an array。

And is actually efficient data structure。 if you want to find minimum。

And you want this is useful research one you want to make updates first yeah。

So if you use a right instead of binary he。Then。Here you will find minimum in linear 10。

 so it will be。And square for desper。But updates will be first。

 You just update the element and do nothing。 It'。 So these updates will work in constant time。

 So it will be L plus M。Wch one is where to this of？

What time complexity is better M log n or n square plus M。Yes。Yes。

 will use your nice chip in in in in in a moment。 but let's just stop here for a second。

So we have two possible implementations of this of this algorithm。

 One implementation works in M log N time， and now it works in n square plus and。Which one is better。

The answer is it actually depends。On this ratio ratio between N and M。For example， for example。

 if your graph is very passive， if you have very small number of edges， if M is about n。

Then here you have N log N and here we have N square。And if the graph is very dense。

 so if M is about n square， then here we have n square log， and here we have just n square。

So if you have a small number of edges。These algorithms is actually more efficient。

 If you have large number of pages， then these algorithms actually more efficient。

 It will it happens sometimes。 Sometimes you have different time。 You can actually combine them。

Make some combined algorithm， which looks on the value of M and N and combines them in some special way。

 So some if you see that the number M is big， you use this algorithm， It's number small。

 you use this algorithm。 And if you just fix some。some good good 그 some。How's called。No。

 you you need to make some water and this and this。

 So if you just can distinguish when you can use this and when you can use this。

 you will have something optimal。For both these cases。Yes。I don't not forget。

 Another way to think about it is instead of using binary hips or arrays。

 you can just use Fibonology hips here。T lamp， it's more efficient。if you that chicken。Then here。

 you need to remove minimum。 You can remove minimum from hip and in log and time。 Yeah。

 so it will be in log。But this operation is actually decreasing the key in the fibonage cube because this D is always decreasing Yeah。

 because it's minimum of previous value And So here in in this line。

 you always decrease the key D and you can decrease key in in Fibonic hip in constant time。

 So this actual operation works in constant plus L。This complex is better than both of this。 Yeah。

 so it's better than this， obviously and better than this。

 So this kind of kind of optimal small of this frame。给。

About it's theoretical for algorithm in theory in practice， magnetic hips actually have a very。

 very bad kinds factors also tank complexity tank complexity theoretical is quite good。

 but the actual time spending by your computer will be better。In most cases。

 you can you need to use one of these algorithm things。Mostly this。

 but sometimes sometimes this is efficient。 If your graph is very dense。

 then using a arrays if more efficient than just using binary hip。酷。Okay， third score results。

 what people know about time complexity of minimal span trees。嗯。Just just just。Just to keep in。

I know。キすオケー出す。I will not explain how it works， just explain that some algorithm there are some algorithms where you have this time complexity。

 okay， it's possible to make algorithm which works in this tank complexity。It uses not the designion。

 but another use some very strange hips。It's complicated。 So you may read about this， but it is。

 it is complicated。So it's possible to make a algorithm which works in almost linear time。

 so it's M multiplied by indoor second command function。

 it is the same function like we used in the like in union find。

 but it comes from different data structure。What else？It is possible to make a randomized algorithm。

 which works in in time。Maybe we'll talk about this algorithm。

 It's actually not not this algorithm is not that complicated。 We may， we may discuss this algorithm。

 It's actually quite simple。啊。Now。Whats interesting， What is interesting。

 We don't know if it's possible to solve the linear time without optimizationization。

 So there is there is nothing under which is known time complexity， non linear time complexity。

 which is completely determined， but。If it is possible， then there is an algorithm we to it。

 there is another algorithm which is proved to be optimal。

So we can prove that it's impossible to make this。 So if there is some optimal1 complexity for。

 for non randomized algorithm， which solve M T problem。

Then these algorithm have the same time complexity。It kinda uses these trees of how it's cold。응。

Decision trees。 Yeah， so it's kind to use if you look on the decision tree about building the minimal pan tree。

 like we discussed when we talk about sorting algorithms。 Yeah， maybe remember。

So basically what you do when you construct minimum span tree， you compare some edges。

 you need to compare these edges， compare these edges。

 you compare this edge and then you have this minimal span tree。

 so if you look on the possible number of this comparisons you need to make to build this minimum span tree。

 then there is an algorithm which have the same time complexity as the minimal height of possible decision tree for the minimum span tree。

But unfortunately， we don't know what is the minimum possible height of the decision tree。

So there is optimal algorithm， but no one knows it's in complexity。That's the constitution。

By randomizing， I mean that tank can tank complexityities is not M。

 but the expected1 complexity then。So the time is not fixed。

 the time of this algorithm itself is a random random random value。So， that。Like， like。

 like in quick sort。 Yeah， so in the timeex of quick sortgraph is analog loggan。

 but it's not the worst case runtime。 It's like average runtime。 Yeah。

 it's like expected value of the time。Is it's the same here。 So the expected。

Time complexity is linear。Y。Do嘟嘟嘟嘟嘟嘟嘟，嘟嘟嘟。Ft。Oh， we spend that the whole hour。 I。

 I hope one more algorithm。 One more algorithm is bar of algorithm。

 I I I just cannot skip the bar of algorithm。Let me explain one more algorithm everything for building memos pantry because it's cool。

 the final。For the mineral panries borrow code。Again， let and check the spelling。뭐 roof 그런 아니。

It's very cool algorithm because it was invented before the computers ored。

But of convert in in the early。in the beginning of the 20th century。

He just needed to build actually the minimum pantry to build something like electrical network in his town。

 something like this。 So he then this algorithm。Vtic simple polyography， let's， again。

 let's talk graph， let's graph， I love to talk graphs。Yes。Yes。And something here。

And let's put some weights。 Let's say 1，5。对。7。Free。嗯。嗯。2。7 here，6。And， let's see。36。7。8？D。

And something here。Let's say，4 and5。嗯。Mean for positive it works。嗯。No， no， no， no。

 the same algorithm we actually never used that the costss are not negative。

You can do the same algorithm hold with negative costs。 It doesn't matter。

If you just want to build the minimum po tray， and you want them。For example。

 if you want to find the max span in tree， you can just make a negative of all the values and build the min spin。

It also works。 No， no no。 We never used non negativity， so。

It it's actually useful for the only thing we use is the linear order elements。Yeah。Yeah。好始。So。

 we have this girl。Very simple idea。 Let's take any note。

And find the minimal edge connected to this note。Then just by using the same lema。

 we need to take this edge into minimal spending term。So let's take。Any note。

 to retro all edges connected to this node， find the minimal edge and add this minimal edge to the spinning tree。

So， we add this edge。this edge。Now for this vertex， we find the same edge， for this vertex。

 we find this edge for this vertex， we find this edge， for this vertex， we find this edge。Here。

 well find this 5。Here， we find this free。 Here， we find 7。Here， we find this four。 Here。

 we find four and so on on。Of course， I could Russian accent I Russian。



![](img/8823a3d7b227166a10d39981ef2f4ca9_51.png)

No。Now let's take all these notes and put them in into the mineral pantry。Okay， what we did。

 we we just use the same lemma， but use it not for single cut， but for fold cuts。

 So we take any note， look on the cut between this note and everything else and find the minimal edge in this cut。

M哼。Let's so。Now， let's see we can do it in linear time。 so for in linear time。

 we can iterate all edges for every node and find the minimum edge for every node。

So we can add all these edges into the minimum span three in linear time。Next。Now， it's not3。Yeah。

 so we add all these edges in into the me print about it back but right now， it's not tree。

By the way， what is the cost of this age。Let's see yeah。So what we do next。

 we just we need to compress every connect component into a single node like so let's look on the connect components in this minimum pen tree we and compress it into a single node。

So。Starting from here， we take all these notess， put them in a single component。

So we need to take this put in a single component。 this and single component， put this and this。

So we have four connect components。And you put these edges between them So these 10 and this 7 and these three and this。

7， right。And here we have 6，8 and 10。Here we have five and8。

So just compress every every component interesting single。Could be the composer to3， if you have。

If all the weights are different， then it's impossible to build a cycle。 You can easily prove this。

 If you have equal base， then sometimes， for example here。

You can take for this note take this edge for this note take this edge for this note take this edge and you will have a second。

 you can fix it easily just by having like the second satellite priorities。

 so if you have several if you have several edges with the minimum cost。

 you need to take some priorities for them。Just sort and by the index of the nos and like this。

So so if， if all rates are parallel as distant that it is impossible to build a cycle。

 you can easily prove this。嗯。Now you can press all the connect components into nodes and then repeat the same process so for this for this graph again you take each node and find the minimum action for this node you have this edge for this node you have this edge for this node you have six for this node you have five。

嗯，That's all。And now you just uncompress， uncompress， y。

 all these kind of compounds back here and add these edges into your original graph。

Use sum another mark。Because this test， you add these 6， you add this five。I am mystery。

And now you have an email penry。That's all。 That's the whole one。Now， what is that complexity？

Each duration takes linear time， not because you need to era all edges for every node。

 you can find minimum in the linear1。 Yeah， so for each node。

 you it all edges find the minimum edge added to your screen。 so you can do all this in linear time。

 And now when you compress all the connect components， the size of the graph will be decreased。

It will be dec at least twice。 So if you have end node here。

 then here you have no more than n or two nodes。Because each compound can contain at least two nodes。

So the number of nodes will be decreased at least twice。

So the number of durations will be at most loggan， so total income complexity will be at loggan。Okay。

Gu。그서까。Again，'s very simple， It's very efficient in in practice。 So So that's the。Again。

 this is the worst scale complexity， so in worst case。

 each connect component will contain only two edges in practice you will have big connect components like here you have connect components of four nodes and so on。

 so in practice you will have some big connect components so the number of offered nodes will be decreased even more price。

So it''s very efficient in practice。 and you can add some heeuristics to this process。

 So it's a very cool algorithm widely used in practice。故。We will have enough time。I believe we do。

We have one more problem to discuss。 One more problem to discuss。Any more questions by now。

 I will raise out ahead。Okay， we have 20 minutes。Will be enough not。Well train。

So I want to discuss one more problem， it's a little bit more complicated。It looks kind of the same。

But it's a little bit more complicated。Each look the maximum how cold。嗯。

Our our words I forgot the word again。A residents， yeah。Yes， our restaurants。Yeah。Yep， you're right。

I always forgot this word， this kind of strange word。We'll talk about Mimo about。

We will talk about being ourboosis problem。What is strange word。呃。What's problem about。



![](img/8823a3d7b227166a10d39981ef2f4ca9_53.png)

Let's have a go。But not undirectgraph， but direct graph。



![](img/8823a3d7b227166a10d39981ef2f4ca9_55.png)

And fix one node of graph。 Let I say this node is the source of this graph。



![](img/8823a3d7b227166a10d39981ef2f4ca9_57.png)

Like we did in theminators problem。 Yeah， So we have a directed graph and one single node。

 which is the source。응 응 응。Yeahs less。

![](img/8823a3d7b227166a10d39981ef2f4ca9_59.png)

And something here。やこな。And again， let's have every edge has a it。



![](img/8823a3d7b227166a10d39981ef2f4ca9_61.png)

So let's put some ways here， let's say。哎。かい。Just to make it more interesting。Let's see，5。6。

어리 왕 쪽 들어 와。Let's see，3。 and one。いや。So sorry。Let's say6 here。Here。ね、これの。So let's say4， six， that me。

Yeah。Let's see，37。诶。He，'s4 not。And let's say，2， and。4。



![](img/8823a3d7b227166a10d39981ef2f4ca9_63.png)

We' know and fight。Okay， now what is the problem。I want to find a again。

 I want to find something like a spinning tree。I want to find a tree。Which is rooted in node S。

And contains all the nodes of the graph， so I kind of want to find a like like in GFS3。

 so I want to find a directed tree with through and node S。

 which contains all the nodes of the graph。I don't want to provide this picture。

So I want to find something like this， I want to find a dream。

Which is directed in S and contains apaths。ほら。From node else to every other node。I want to。

 I want to build something like this。And I want the total cost of all edges in this 3 be as minimum as possible。

Again， the intuition is very simple， so imagine you want to have a path from node S to everything else。

So I want to have a back from S to all other notes。So， the minimal structure。

Which makes all the nodes accessible from node S。 Is a three rooted in the node S， yeah。

So if you have some node node in this screen， you can remove this node and the connectivity will stay the same yeah。

啊，他。So I want to be able to move from node S to every other node。😡。

And I want the total cost of all these H B as small as possible。That's problem。Okay。

 is the problem set camera， so I want to build three like this with minimal total cost of all edges in this tree。

So the problem looks kind of the same like minimal spending train， but unfortunately its it's quite。

 much more complicated。

![](img/8823a3d7b227166a10d39981ef2f4ca9_65.png)

Why it is more complicated。 No， because you kind of don't have this。Alemma like before。 So if you。

 if you try to apply the same lema like before。 So we have this。Again， you have this set A。

 you have this set B。And you， you try to， you find this edge U V。Direct edge again。

Here you have direct graphs。 you haveject H and you kind of want to say if I， if I have this tree。

 then in this tree， I have path from U to V， but you actually don't have this path。

 You have path from S to every upload node。 But if you take node U here and node V here。

 you don't have path from U to V so you can apply the same la here， because the path directed。

So it's a little bit more complicated。It's actually much more complicated。



![](img/8823a3d7b227166a10d39981ef2f4ca9_67.png)

And the cool thing that this is actually solvable in polynomial time。

 and we will discuss the algorithm。Right right now。 So it's it's its it's actually not that。Not the太。

Oh， let do lets just do it。呼。我是讲。So the algorithms Edmonund's algorithm。

We will talk about adunds invented some algorithms for these problems， and also for。

For for formation matchings。 So in in the next semester， we'll talk about non。How it's cold。嗯。

We'll talk about matching in the graph and we'll discuss another element algorithm。



![](img/8823a3d7b227166a10d39981ef2f4ca9_69.png)

It's actually looks kind of the same， but for a completely different problem。Let's go。So。那种。First。

Let's try to do something under all these weight。We can do the following operation。 We can take。三の？

Which is not the root。Let's take some note V。Let's look on all ingo edges。미 안 없어어。

All these interesting。Yes， we will talk about generalgraphs in the system， yeah。

Okay well totally do it。It's not that。 It's not that hard as it looks like。Will do it。 next semester。

So let's take any note of the girl。And look on all in ages。

Exactly one of this edge will be in this tree。 So for every edge except the root。

 there is exactly one edge growing in this node。So if you look on all ingo edges。

Exactly one of these edges will be in this final tree。So what you can do。

 you can add the same constants to all these results。 You can take all these edges， and add。

The same delta to all the weights of these edges。If you add data to， to the all to to each of these。

Edge， then the total cost of this trip will also be increased by Delta。Yeah。

But because you have this V somewhere here。So exactly one of these areas will be。Increased by de。

So again it's。This separation do not change the result。It do not change the final tree。

Because exactly one of these edges will be taken。If you increase them all by the same deelta。

The final tree will be increased by the same delta， so the minimum tree will stay the minimum tree。

Mmhm。😊，So it's the safe operation。 you can do it at any point。

 you can take any node and add them to all ingo edges。It will not change the final result。

That's the whole idea。 And I will try to apply this idea here。 So let's take any。Let's take any note。

 Let's take this note。This node has two avoid resource have three and six。

Let's just add-3 to all these edges。 So we'll just decrease all the edges by the minimum weight of all edges。

Let's take these two edges。And decrease the weight by free。So we take minus-3 here will will be 0。

8 minus for here， Prily here。And now we' just apply the same procedure to old notess。

So we'll try to make as many zeros as possible， so we take this note we have two and all。

 so we'll just decrease these to zero。Here we have 5 and3。 We decrease by3， So we have 0 and 2。

Here we have one and 6 decreased by one。 So have 0 and 5。Here， we have 6 and three。

 So we have 0 and3。And here we have four don don many，4，4，5，7。 Okay， it will be 0，0。1 and3。

And here we have five。8。zero thing yeah。Looks fine。I don't like these2 zero。Maybe its fine。这れ。

Let's take this one。

![](img/8823a3d7b227166a10d39981ef2f4ca9_71.png)

I don't like I have two zeros， I don't know。That that happened when when I when you have the same cost for all's let's have all different costs just for simplicity。

No。Okay， let me go write the algorithm here， so we try all engine for all nodes。For all。

We take the date is the minimum。C。Or goinging in， no listen for， for all。U V。So， for each。

No we find the minimum in going page。And now， we take full。U V we just。YouVマ。That's the first step。



![](img/8823a3d7b227166a10d39981ef2f4ca9_73.png)

Now， now we have a lot of zeros。Let's mark all the zeros。From zero here， zeros here。



![](img/8823a3d7b227166a10d39981ef2f4ca9_75.png)

We have zeros here。So our graph contains a load of zeros。Case one。啊。If let's， let's look on on zero。

 So let's remove everything， but zeros。If every note is accessible from Sp using this only the zeros。

No reachable。From S by zeros。自よ。So if you can reach every node。From the dont S using only zeros。

Then I claim that the answer is actually 0。Why。Look， because you can build as a tree。From note S。

Which uses only these zero edges。 So the total cost of this tree is 0。

And you cannot have a tree with cost less than 0， because all the weight are not negative。

So if in this graph， you can access every node。From node S， using only zeros。

Then you can build a tree with total vertical to 0， and you can' make it less than 0。

So the0 is the optimal answer。嗯。Built。3。Of zeros。응 우리。Nice。But sometimes it's not the case。

 sometimes you have something like this， so you have some strain graph。And not every notice。

Accessible from reachable from node S。 for example， here， if to start from node S。

 you can only reach this node in this node and all these nodes are not reachable from node S。Then。

I claim that。If some note is not reachable from us。Then you have a cycle。For example。

 here we have two cycles， we have this。And we have this cycle。

So if some note is not reachable from S， then there is a cycle of zeros。Why this true。

Because let's find some note which is not reachable from S。Let's take some node V。

 It is not reachable from S。 So every node， every node has some ingoing edge， which is 0。

 So let's take you So let's take0 node going inside。 Now for this node， let's take another node。

 which is in going to this edge， which just has 0 and so on。 So each time we take some。

Im going H with zero cost。啊。Every node except S has at least one in going edge which has zero cost。

 so we always can take some0 edge in going to order and so at some point we will will go into loops because because we have fixed number of nodes so at some point we will find node which we visited before。

He。So at some point， we'll find something like this。And now we have this cycle。

So if not all nodes are reachable from S， then there is a cycle。 Let's find this cycle。

 It's precision。So cool。Zs。0s like this。So let's find this cycle zeros。

 If you have several different cycles， lets find any of them。So let's find any cycle of zeros。Now。

 let's see。Inside this group of nodes， every node is accessible from every other node。

Because you will have this cycle。So inside this group， every node is reachable。

So what we can do is we can compress this cycle into a single node。Yes， if you have multiple cycles。

 you can compress all of them。Let's do it here。Yeah。Let's compress all cycles just for simplicity。



![](img/8823a3d7b227166a10d39981ef2f4ca9_77.png)

Here we have these two nodes。 We can press them into this fat node。 We have these three nodes。

Let's one this。We have these three node compress them here。 We have this node， and we have here。

 we have yes。So this node is compressed， these were compressed and this note is these two node compressed。

So we have here。 We have one here。 We have three。I。 yes， I here。 We have 0。Free。3。0 and 2。嗯。Here。

 we have two one section。And for it。Yes。1，2，3，4，5，6，7，8，9，1，2，3，4，5，6，7，8，9，10。嗯。No that。

So we compress these three nodes into one node here and these two nodes into one node here。

And now just repeat the same， the same process。 We take this graph for each note。

 we decrease all the costs by the minimum of them。 So for this note， we minimum will be。

 So we have one，3，3。So minimum was one。 So we decrease everything by one。So， we have 0 and 0。

Here we have。2。えと？嗯。He， and for this note， we have 3 and 5 degrees with 0 and 2。And again。

 we look on all zeros。 We look at all the zero edges。 So we have these zero edge， this zero edge。

These zero h or any of them actually。And0。And now in this graph。

 everything is connected to every node is reachable from node S。So this is valid。T。

 so here we have a tree。Of zeros。And we can have less than 0。

 So this is the optimal three for this graph。Now what we need to do。

Is to move from this answer to answer to to， to this graph。How can we move this answer here。

We need to uncompress each of these fat nodes， so we take each of these fat nodes and uncompress them into these cycles。

어。I suspect back to use another color for this。So I need to add this edge here。

And I need to add this HQ。It's one of these interests。Thisかさ。

So I just take all edges from this graph and put them back to this graph。And now I don't have a tree。

 I have something with cycles。So I need get to get rid of the cycles。

 how to get rid of this of the cycles。 It's quite easy。 So for each cycle。

You have one in goingver this。So it this it is for this fat node， you have this in edge。

 So when you uncompress this fat node here。This edge will be going into one of the nodes of this cycle。

So what you for this note of the cycle， you have， you now have two ingo edges。

 You have this edge and this edge from the cycle。So to make it three again。

 you just remove this edge from the cycle， so you just remove this edge from the cycle。

And now you fix this and also you do do those thing here for for this node。

 So this node is going from here。 So you have this in goinging edge to move to this route。

 So it see this node。 So for this node now you have two in going edges。 you just remove the second。

Just least one。And now we have a tree。So this is a valid tree for this graph。That's home。

That's how you build the mineral。Our Brus， yeah。Yes thats your track。I think嗰啲。啊。

That's all list the whole algorithm， again， hows algorithm works？You take hold an old graph。

Find the minimal edge and reduce all the cost by this minimal age。Now， you。

 if all the nodes are reachable， then you just build three of zeros and you're done。 If not。

 then there are some cycles。 you just compress all the cycles and repeat it again。

Repeat the same process。 Repeat the same process。If you do it like this。

 like using this simple procedure。啊。But if， again， if， if you just do it in a simple way。

 just each time you do， do all this。Then the total complexity will be like this。

 so all these can be done in linear time。So I I can do this in panel。よさ最。

You can do this in later time， can check this in linear time。

And you can compress cycles in linear time。Because everything melt in linear time。

 so you can do all these operations in linear time。And when you compress cycles。

 you reduce reduced number of nodes in your graph， so you can reduce the number of nodes more than n times。

 So if you just apply it like this and complexity you will be N。そ。

SoSo just but very simple implementation of this will give you an economic complexity。

Can you dare do it first， you actually can。To do it first。

 one of the ways to think about is just to modify this algorithm。啊。What you need to do？

I basically remember the current state of your tree。Not， it's not a treat something strange here。

 So you need some way to detect the cycles， and you need some way to。

To compress the cycles in those single nodes。 because here in these separations。

 you only need to update update this for this new fat node for for all these single nodes。

 you don't need to update this minimum because for each of these node on the previous step。

 we had this operation already done。 So we need to make a separation only for this new fat nodes。

So it this this section not a problem after you compress the cycles。

 you need to apply this separation only to these new f node。 Yeah， so this sectional problem。

 this is actually kind of problem。 So here， you need to check if your current situation is actually a tree rooted in S。

 You can actually do it in some researches。 And here you need to for some fast way to detect the cycles and compress them。

 also do well， but it's kind of tricky。There is another way to think about this algorithm。

 which is kind of。Easier way to build first algorithm。啊。Do we really want to。 Okay。

 let me explain this if you， if you want to build faster algorithm。

 you need to do it in slightly different way。So what's the problem here problem here is that I'm trying to build a lot of things。

 so I'm trying to build all these structures， all these structures of function and then just compress the small cycle。

So I spend a lot of time just by remaking the whole graph and then just compress in the worst case。

 I just compress two nodes into one。 So in the worst case。

 I have a single cycle containing only two nodes。 So I just compress two nodes into one。

 that's not efficient。 What you want to do is do not create not to make all this picture。

 but only create a small part of this picture。 And if if it in this small part， you have a cycle。

 you compress the。 So I can do at least you start from some node takes take some node。Now。

 each time you take all ingo ages。apply the separation only to this single node。

 so you take all and going edges， take the minimum， decrease all the rate of the minimum。

 then you have a zero edge。Then again， for this， don' do the same trick， take all ongoing edges。

 take the minimum one and decrease everything by this。 so every time you take the zero edge。

 so you have this， you have this path of zeros， not the the whole graph of zeros。

 but only pathth of zeros。That at some point， you may have one of two two stores。

 you may reach the point S。 if you reach the point S， then this is the correct part of your final。

Yeah， this is correct part of your final。3。So you're just。

Left this as this take another node view and start from this point。Or you may have you may have look。

 so maybe at some point， you will have something like this。No。So maybe at some point you find 0 H。

 find 0 H， and then you have a loop。If服。If you have a look here。

 then you you need to find all the notes on the cycle and compress them into single ones。

But after you compress them to the single node， you have you again， you don't start from scratch。

 you don't start from this node V， but you start from here because you already have this state。

 a good state， so you have the node node V and then some path of zero edges to this node So you compress this cycle here is kind of stack you have this stack of nodes。

And if you have cycle here， you can press these top nodes into single node and put this new fat node in the top of the stack and stuff that continue from this point。

That's kindly how you get to fast the order。No else it's actually a bit more tricky because you need some good data structures which will allow you to find the minimum age among all in age and so you want some data structure。

Do remember all your ingoing ages。And this data structure should allow you to find the minimum。And。

Decrease everything by this minimum。So you need something like。Heip or。B the search tree。

 just to remember these in going edges。And when you compress this cycle into a single node。

You kinda need to take all these lists。So for each of these node， you have some ingoing edges yeah。

So when you compress these node into a cycle。You want to kind of concatenate all these lists into a single list of in edges。

So you need something like meable he。It's also possible there aremerable heaps。

So you can use mergeable heaps to to just to store the ingoing edges for all of these nodes。

 So when you combine these nodes into a single node， you just merge all this。

Mrggeable hes into one S heap。And then you're done。 And now in in this hip。

 you can do two operations。 You can find the minimum。

 and you can reduce all the values by the same minimum。That's also possible。

 And if you do it like this， you will have the time complexity here like M logm。So that's do well。

 that's actually quite it's not that hard implement。

So if you already have implemented some knowledgeable heaps。Its。It's actually no， it's not at heart。

 You you just do this。 You， you have this stack of notes each time you add try to add this extra h。

 If this node is already in your stack， then you have this cycle。

 you just remove all the nodes from the top the from top of the cycle。 compress them。

 merge all these hipaps and put this new f note in the top of this。 It's actually double。 It's do。

 interesting thing， you can， you can actually improve this to work and log and last same。

And the way you do this is actually by using Fibonacci hips。But。It's not as easy as it looks。

 So you you can just apply Fibonac hip and see it， because here you actually each time you need to remove a minimum edge。

And when you compress the cycle into a single node， you have a lot of loop edges。

 So when you when you have edges inside this component like here， you have some edges yeah。

When you compress press all these nodes into single node， you will have a note and some loops。

And these loops may have maybe be the minimums。 So when you remove this loops from this hip。

 each time you spend loggan time to remove this loops from this Fibonacche hip and removal from Fibonacche hip course to logan time。

 So if you just try to apply Fibonacche hip to this algorithm， you will have M loggan time again。

 because for each edge， you need to spend logan time to remove from from Fibonacci hip。

So it's a little bit more complicated。 You don't want to store all the edges in in this image hip。

 You kind want to select some edges。そ服 응。The ideas is。Like we use inpre algorithm。 So for each note。

 we remember some good edge， and we put only these good good edges in Fibonacci heap。

 and then we will do something in。 And then we need to modify Fibonacci heap because we kind of move。

Move elements from one hip to another and we can do the individual match hip。

 so we need to modify the hiacche hip and that's not。talkとき温多嘟就是ね。

The magic hip is complicated by itself。But for this other， you need to some5 image。

So let's pull everything， right？I quite， I highly recommend to。Read the paper about this order。

 If you are interested in this stock。That's complicated， so you can do this， but it's complicated。

I' am not sure if it is possible to make it faster than this time。

I believe there is no no longer professor than this。

 but I am not sure if there is a proof that is impossible。I think it's not。So maybe。

 maybe it's possible to do it first time。啊推动头。I didn't check。

 Maybe that was proof that this is not small reason。I'm not sure about this。

But that's the best of it my。Maybe it's actually optimal。Okay， I think this's all for today。

