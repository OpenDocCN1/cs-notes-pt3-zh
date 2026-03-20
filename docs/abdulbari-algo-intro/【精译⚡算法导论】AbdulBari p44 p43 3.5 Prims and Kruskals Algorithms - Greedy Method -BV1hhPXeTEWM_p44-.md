# 【精译⚡算法导论】AbdulBari p44 p43 3.5 Prims and Kruskals Algorithms - Greedy Method -BV1hhPXeTEWM_p44-

The topic is minimum cost a spanning tree。 So for that， first of all。

 we'll understand what does it mean by a spanning tree。Here I have an example graph。😡。

Graph is represented as G and V E V is the set of vertices。1，2，3，4，5，6。 and is the set of edges。

 The set of edges are from 1 to 2。And2 to3。Three to four and so on。

Graphs are represented as set of vertices and edges。 Now， what is this spanning tree。

 Spning tree is a sub graph of a graph。 Hence， I should take the subset of this。

 So subset of what vertic is an edges， both a subset or only one subset。

 So I should take the subset of edges。

![](img/a12d59fc36c41afd888ba8c151452456_1.png)

Vertices must be as it is。 So I just should take all vertices 6。



![](img/a12d59fc36c41afd888ba8c151452456_3.png)

Spanning agreements， I should take all vertices。 Then how many edges。

 how many vertices I have numberumb of verortices are n that is 6。

 So I should take number of verrtices， minus-1。 that is only five edges。



![](img/a12d59fc36c41afd888ba8c151452456_5.png)

![](img/a12d59fc36c41afd888ba8c151452456_6.png)

pantry is a subgraph of a graph having all vertices， but only n-1 edges。 So out of these。Adges。

 I should take only5。 So 1，2，3，4，5。

![](img/a12d59fc36c41afd888ba8c151452456_8.png)

![](img/a12d59fc36c41afd888ba8c151452456_9.png)

I did not take this one。 So there is spanning tree。



![](img/a12d59fc36c41afd888ba8c151452456_11.png)

See， a tree will not have a cycle。 So there is no cycle here， yes。



![](img/a12d59fc36c41afd888ba8c151452456_13.png)

Theres no cycle here。 If I this， you can say it's a cycle。 If you start from one vertex。

 you can again reach back to that vertex。But here， there is no cycle。

 Is it possible that I will take this one， but I will not take this。 Yes。

 there's also inspiring tree。

![](img/a12d59fc36c41afd888ba8c151452456_15.png)

![](img/a12d59fc36c41afd888ba8c151452456_16.png)

I will take this， but I will not take this。 Yes， this is also an spellning pay。

 so which add you to cell that is a choice。

![](img/a12d59fc36c41afd888ba8c151452456_18.png)

There's a choice for a spanning tree。 So I can say that。



![](img/a12d59fc36c41afd888ba8c151452456_20.png)

S is a subgraph of a graph where S is defined as set of vertices and set of edges。

 where set of vertices are same as the vertices of a graph。And edges are number of vertices， -1。

 So the number of edges are number of verrtices， -1。 This how formally we can divide in mathematics。

 we can define like this。 So next thing， For a given graph。

 how many different spanning trees can be generated。

 I want to know that how many different spanning trees are possible。



![](img/a12d59fc36c41afd888ba8c151452456_22.png)

![](img/a12d59fc36c41afd888ba8c151452456_23.png)

![](img/a12d59fc36c41afd888ba8c151452456_24.png)

So see， number of edges are harmmin。6，1，2，3，4，5，6。 I have an aspiring tree。 I should take only 5。



![](img/a12d59fc36c41afd888ba8c151452456_26.png)

I should take only five， so6， C，5。

![](img/a12d59fc36c41afd888ba8c151452456_28.png)

Out of 6 edge。 Out of 6 edges。I have to select 5。 How many ways I can do that。 So6，5 C ways。 So fix6。

5 Cs how much 6 only。

![](img/a12d59fc36c41afd888ba8c151452456_30.png)

So I can have six different spanning trees。Just now you can see it is a simple one that I have skipped this edge like this。

 I can leave 1，1 edge， right， And again， former spanry， right， I can take all accept this。 take all。

 accept this。 take all except this。60%。Suppose if I have the no edge now。Now I have seven edges。

 and I want to select 5。Now how many span trees are possible。See I have this as spelling tree also。



![](img/a12d59fc36c41afd888ba8c151452456_32.png)

Or I can have thisplan tree also。

![](img/a12d59fc36c41afd888ba8c151452456_34.png)

Now possibilities are more。 Now this is 7 C 5。7， c，5。 But this edge will form cycle。

 So how many cycles it is forming， This is one cycle， and this is another cycle。

 So this edge is forming two cycles of number of verrtices less than 6。

 So if it is forming number of vertices less than 6， then you sample be。



![](img/a12d59fc36c41afd888ba8c151452456_36.png)

7 c 5-2。

![](img/a12d59fc36c41afd888ba8c151452456_38.png)

So， that's it。So what is the formula to know how many different spanning trees are possible from a given graph。

 So whatever the number of edges you have， you should take all those and see of how many edges you need。

 you need 5。 So 5 is what number of vertices -1。 So this is number of verrtices -1 and number of。



![](img/a12d59fc36c41afd888ba8c151452456_40.png)

![](img/a12d59fc36c41afd888ba8c151452456_41.png)

![](img/a12d59fc36c41afd888ba8c151452456_42.png)

Sys。

![](img/a12d59fc36c41afd888ba8c151452456_44.png)

You have to subtract number of cycles。 I have a graph where the edges are having weights。

 So this is a weighted graph。This surveyted graph。I want to know what are the possible spanning trees possible。

 So I'll draw a few spanning trees。 Let us draw one spanning tree。

 This is vertex 1 and 2 and 3 and 4。 So four vertices are there。

 Then how many addresss I should take 4-1， only 3。 So I'll select this 1，1，2，3。

 So what is the weight of this one，5，3 and 6。 So what is the cost of this spanning tree cost of this spanning tray is 14。



![](img/a12d59fc36c41afd888ba8c151452456_46.png)

I'll take one more pentry，1，2，3，4， and I'll take these edges。 Let us see what is the cost of this，4。

6，3。 Then what is the cost of this fund。

![](img/a12d59fc36c41afd888ba8c151452456_48.png)

Tardine。

![](img/a12d59fc36c41afd888ba8c151452456_50.png)

I'll take one more span tree，1，2，3，4 and I'll take these edges， this one and this one and this one。4。

2， and 3。 So this is cost us how much 9。

![](img/a12d59fc36c41afd888ba8c151452456_52.png)

Now， from this example， some observation， we can understand something。

 If you have a weighted graph and you get different spanning trees。

 the cost of the spanning trees may be varying。 You can get a different cost of spanning trees。Now。

 the problem is。Can I find out the minimum causes spanning tree， Can I find out the minimum one。

 which gives me minimum， Yes， you can find out how you can try all possible spanning trees。

 And then from that， you can check whichever is minimum。 you can pick up that answer。

This is one method。Trying all possible spanning trees will be too lengthy。

Is there any gradienting method？Yes， the greedy methods are available for finding the minimum causes spanning tree。

 If a weighted graph is given， you can find out the minimum causes spanning tree by following the method without finding out all possible spanning trees。

 So what are those methods。 One method is。

![](img/a12d59fc36c41afd888ba8c151452456_54.png)

![](img/a12d59fc36c41afd888ba8c151452456_55.png)

![](img/a12d59fc36c41afd888ba8c151452456_56.png)

![](img/a12d59fc36c41afd888ba8c151452456_57.png)

Prim algorithm and the second methodist Cruscals algorithm。



![](img/a12d59fc36c41afd888ba8c151452456_59.png)

There are two algorithms for finding minimum course span injury。



![](img/a12d59fc36c41afd888ba8c151452456_61.png)

I have a weighted graph here， and I have to find a minimum causes spanning tree by following Pri algorithm。

 Let's see how Pri algorithm works through an example。The As per Pri algorithm。

 he says that from a graph， first of all， you select a minimum cause edge。

 So the smallest edge in the entire graph is this one。Then。This is the initial one。 Now。

 for the rest of the procedure， always select a minimum cost edge from the graph。

 but make sure that it should be connected to already selected verortices。



![](img/a12d59fc36c41afd888ba8c151452456_63.png)

Now， the next minimum is which1，3 to 4。 Don't take that。 It will not be connected to one or 6。

 So take only those which are connected to one or 6 means what he is trying to do is always maintain a tree。



![](img/a12d59fc36c41afd888ba8c151452456_65.png)

Prince thinks that if some farther away edges selected， than it may not be forming a treefin。



![](img/a12d59fc36c41afd888ba8c151452456_67.png)

![](img/a12d59fc36c41afd888ba8c151452456_68.png)

So that is the reason he suggested that always select a minimum match which should be connected。



![](img/a12d59fc36c41afd888ba8c151452456_70.png)

So let us see what is the next one。 So for this connected one are this one and this one。

 So this 25 and 28，25 is minimum， so select this 25。



![](img/a12d59fc36c41afd888ba8c151452456_72.png)

![](img/a12d59fc36c41afd888ba8c151452456_73.png)

Then this 28 and 5 connected to 5 are 22 and 24 So of this 28，24 and 22。

 So from 1 and 6 and 5 I am checking so already6 is over。 So one and 5。

 So out of those this is the smallest one。 so4 is selected。



![](img/a12d59fc36c41afd888ba8c151452456_75.png)

![](img/a12d59fc36c41afd888ba8c151452456_76.png)

Now， from 1，6 and 5，4， who is smallest， the connected one。 So this is 24 and 18 and 12。

 So 12 is a smaller， so we will take 12。

![](img/a12d59fc36c41afd888ba8c151452456_78.png)

![](img/a12d59fc36c41afd888ba8c151452456_79.png)

Then not of all these， which connected as the smallest。 So here I have 24，18 and 16。

 So 16 is a smaller。 So take that 16。

![](img/a12d59fc36c41afd888ba8c151452456_81.png)

Then an out of all these who is next connected。 So from 2 to 7， there is an edge which is connected。

 So this is 7。

![](img/a12d59fc36c41afd888ba8c151452456_83.png)

That's it。There are 7 vertices， So 1，2，3，4，5，6，6 edges are selected。

 And this how we got a minimum gas cost spanning trail。And。

 and this is how we got a minimum cost span tree。 What is the cost of a tree， The cost of a tree is。

 if I add all these。If I add all these， it is 99。So the approach of premises initially select the smallest one。

 then always select the connected smallest one。Okayect。



![](img/a12d59fc36c41afd888ba8c151452456_85.png)

So this is the method of pre。Next。If I have a graph，1，2。three。4。5，6，7。



![](img/a12d59fc36c41afd888ba8c151452456_87.png)

If I have a graph like this， which is not connected， there are total  seven vertices。

 but there are two pieces in a graph。 Can prim find out the minimum course spanning tree for this one。

 No， no algorithm can find out because we cannot find a tree for this one spanning tree for this one in a spanning tree。

 it must be connected。 So for non connected graph， we cannot find spanning trees at all。

 But if I start prims on this one， starting from vertex1， if it is starting。

 then it may find the spanning tree for only one component， not the other component。

 Next method for finding minimum course spanning trees， Cruical method。

 This also follows a greedy approach。 Instead of trying out all possible spanning trees。

 It shows a procedure by following which we can get a minimum course spanning tree。

 It says that always select a minimum course h always select a minimum。



![](img/a12d59fc36c41afd888ba8c151452456_89.png)

![](img/a12d59fc36c41afd888ba8c151452456_90.png)

![](img/a12d59fc36c41afd888ba8c151452456_91.png)

![](img/a12d59fc36c41afd888ba8c151452456_92.png)

Edge， let us follow this one。 select smallest edge。



![](img/a12d59fc36c41afd888ba8c151452456_94.png)

1，2，6。 That is 10。 This one is the smallest， and the next smallest test is 32 4。

 So the second edge I'm selecting is 3 to 4， and its cost is 2。 Next minimum is 2 to 7。 Select 2，2 7。

 and this is 14。 And the next minimum is 2 to 3。 That is 16。



![](img/a12d59fc36c41afd888ba8c151452456_96.png)

![](img/a12d59fc36c41afd888ba8c151452456_97.png)

![](img/a12d59fc36c41afd888ba8c151452456_98.png)

And after this， the next minimum edge is 7 to 4。 but that is 18。 If I select that。

 it will form a cycle。 Yes， crystal method says that always select a minimum cause edge。

 But if it is forming a cycle， don't include it in the solution。 discard that edge。

 don't include an edge。 So it means always select such that it is not forming a cycle。

 So if I include 4 to 7， it will form a cycle。 So next one， you check。 So the next one is 22。

 So this is from 5 to 4 or 4 to 5。 So this is 22。 Next minimum is 24。 So that is 7 and 5。

 If I include this also， it will form a cycle， don't include that one， then the next minimum 1 is 25。

 That is from 5 to 6。 So this is 25。

![](img/a12d59fc36c41afd888ba8c151452456_100.png)

![](img/a12d59fc36c41afd888ba8c151452456_101.png)

![](img/a12d59fc36c41afd888ba8c151452456_102.png)

![](img/a12d59fc36c41afd888ba8c151452456_103.png)

And the cost of this one is， if you add all these weights， it's 99。



![](img/a12d59fc36c41afd888ba8c151452456_105.png)

So here also got the same result just how I got in Pri algorithm。

 so the Pri algorithm and crucial algorithm has given the same result on this particular graph。



![](img/a12d59fc36c41afd888ba8c151452456_107.png)

Now， time taken by Ccals algorithm， how much time it takes。 See。

 it has to always select a minimum cause edges from the set of edges。

 So let us say there are E number of edges。 So out of these edges， it will find out the minimum1。

 and how many such edges it will be selecting it will be selecting v minus1 it is number of vertices minus1。

 like we know in a spanning tree， if there are seven vertices。

 we need six edges for forming a spanning tree So that 7 minus1。

 So as many vertices we have -1 number of edges we have to select So the total time will be theta of v into E there E v is number of vertices and E is number of edges。

 So it is n into E n is the number of vertices and E is the number of edges which can also be written as n square。

 if we say both are n then it is n square。 So the time taken by cross。



![](img/a12d59fc36c41afd888ba8c151452456_109.png)

![](img/a12d59fc36c41afd888ba8c151452456_110.png)

![](img/a12d59fc36c41afd888ba8c151452456_111.png)

![](img/a12d59fc36c41afd888ba8c151452456_112.png)

![](img/a12d59fc36c41afd888ba8c151452456_113.png)

![](img/a12d59fc36c41afd888ba8c151452456_114.png)

![](img/a12d59fc36c41afd888ba8c151452456_115.png)

![](img/a12d59fc36c41afd888ba8c151452456_116.png)

![](img/a12d59fc36c41afd888ba8c151452456_117.png)

Algo is N square。But。Crystcal algorithm can be improved when we have to always select a minimum course edge。

 Then there is one data structure， which will always give you minimum value。 That is min he。



![](img/a12d59fc36c41afd888ba8c151452456_119.png)

If min heap is used， then min heap will always give you a minimum value。 When you delete a value。

 you get a minimum value。 So if all these edges are kept in a minheap， whenever you delete。

 you will be getting a next minimum edges so you don't have to search So from minheap whenever you delete the time taken is log n。

 So how much time it will take for finding a minimum cause edge log n time。

 So how many times you have to do that that is n time number of vertices minus one time。 So n。

 So by using minheap， the time time complexity of crystal cell will be n log n。

 So that's how critical algorithm can be made faster。



![](img/a12d59fc36c41afd888ba8c151452456_121.png)

![](img/a12d59fc36c41afd888ba8c151452456_122.png)

![](img/a12d59fc36c41afd888ba8c151452456_123.png)

![](img/a12d59fc36c41afd888ba8c151452456_124.png)

![](img/a12d59fc36c41afd888ba8c151452456_125.png)

Now， if there is a graph given that is not connected graph。 It is having two components。

4 vertices on this side，5 vertices on that side。 Can we find a spanning tree on a nonconected graph。

 No， spanning tree is not possible， but what happens if I run is crystals algorithm。

 So crystal algorithm will try to find out total number of edges that is 9-1。

 So it will try to select 8 edges。 And it will not be forming a spanning tree for entire graph。

 but it may be finding the spanning tree for each component。

 Let us say the first minimum the one it will select as this one。

 Then the next minimum it is having more than。One edge just let us say it selects next minimum and the next minimum it will select this next minimum it selects this and this is the next minimum。

 So in this way it is selecting the minimum ats from both the components or it will be selecting from all the components。

 so it may be finding spanning trees for all the components but not for the entire graph。

So critical algorithm may work for non connected graphs also。

 but it may give spanningry for those components。Let us take a problem here。

 A graph is given and the weights of the edges are also given。

 but here two edges are not having their weights。If I take only these edges which are having a weight they are forming a spanning tree of a graph。

 just hide these two edges， it becomes a spanning tree。

Now the question is what could be the minimum values of these two edges。

 what could be the minimum possible value， maximum can be anything。

 but at least what could be the value。See， as this is included in the spanning tree。

 this is included in a spanning tree， this is not included because it is forming a cycle。

So it is forming a cycle。 If it is included， this will form a cycle。

 So it may be considered after selecting these two， after selecting these two。

 So the weight of this could be for。Right first this is selected， then this is selected。

 then this is not selected means definitely is four if it is less than four then that would have been selected first。

Right， so it came later。 So it is forming a cycle。 so it is not taken， Then this four is taken。

 Then this4 is taken。 This 5 is taken。 So then what could be the minimum weight of this one。

 So it is not selected at last。 It is left over means minimum weight of this one could be 6。

 So this is 4， and that is 6。So if any missing edges are there you can find out these type of problems we find in examinations。

 so some missing edges you can find out so if you know spanning tree。

 you can answer this type of cushion， let us take this example and let us find out spanning tree for this one minimum cost is spanning tree。

So if I follow Cs methods。 so first， I will select the minimum cause edge this edge I have selected。

 then the next minimum is this three and that three so I can select anyone so I will select this one first。



![](img/a12d59fc36c41afd888ba8c151452456_127.png)

This is selected。 Next， I'll select this one。 So is it forming a cycle inclusion of this one， No。

 So I'll select that one。 Then which other the edges 4 and for these two are there so I can select anyone。

 So I'll select this one。 whether this will form any cycle no。

 So total how many edges are have selected 12，34。 and total how many vertices are there5 vertices are there。

 So four edges are selected。 That's I got a spanning tree。 So what is the cost of the spanning3。

2 plus 3 plus 3 plus4。 and this is2 and。

![](img/a12d59fc36c41afd888ba8c151452456_129.png)

![](img/a12d59fc36c41afd888ba8c151452456_130.png)

Spanning tree is a minimization result， so definitely there will be only one result。

 So for a problem there can be only one optimal solution。

 so we should have exactly one spanning tree only there cannot be more than one spanning tree。



![](img/a12d59fc36c41afd888ba8c151452456_132.png)

Right，But in this example， you can see instead of taking this four。



![](img/a12d59fc36c41afd888ba8c151452456_134.png)

This edge， I can take this four also。

![](img/a12d59fc36c41afd888ba8c151452456_136.png)

Now， also， it's for me a spanning tree。 Yes， so I can select one more。 but what is the cost。

 Cos is12， So cost is only one。 The optimal cost is 2 only。

 You will get definitely only one answer in the minimization or maxim problem。 But for that answer。

 the set of input may be changing。So either you can include this four or this four。

 So total how many spanning trees trees are possible two spanning trees are possible。

 but what is the minimum cost that is 2。

![](img/a12d59fc36c41afd888ba8c151452456_138.png)

![](img/a12d59fc36c41afd888ba8c151452456_139.png)