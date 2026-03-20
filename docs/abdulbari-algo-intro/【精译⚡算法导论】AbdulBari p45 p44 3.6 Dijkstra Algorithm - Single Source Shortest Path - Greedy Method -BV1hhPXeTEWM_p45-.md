# 【精译⚡算法导论】AbdulBari p45 p44 3.6 Dijkstra Algorithm - Single Source Shortest Path - Greedy Method -BV1hhPXeTEWM_p45-

Topic is the extra algorithm。This algorithm is of single source shortest part problem。

If a weighted graph is given， then we have to find our shortest path from some starting vertex to all other vertices。

 Let us say I am selecting starting vertex as 1， Then I have to find out shortest path to all the vertices。

 maybe a direct path or via other vertices。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_1.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_2.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_3.png)

And I can select any one of the vertex as a source vertex。As we have to find out the shortest part。

 so it's a minimization problem。And a minimization problem is an optimization problem。

So optimization problems can be solved using griding method。

Greedy method says that a problem should be solved in stages by taking one step at a time and considering one input at a time to get an optimal solution。

And greedy method， there are predefined procedures and we follow that procedure to get a optimal solution。

So thistri algorithm gives a procedure for getting a optimal solution that is minimum result that is shortest part In this video。

 I will show how dx algorithms works。 and the this can work on a directed as well as non directed graph。

And also I will show you the drawback of Dxtra algo。Let us see the approach of Dixtra Al for that。

 Ill show you the basic thing that is followed by Dixtra。 So for that， first of all。

 I'll take a very small example and show you。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_5.png)

To show the approach of the X gardenm， I have taken a very small graph here。From this。

 we will understand what is the approach of the X。If I say one is the starting vertex and I want to find the shortest path to2 as well as3。

 so if you see from this graph there is a direct path to vertex 2 so its cost us 2 and there is no direct path to3 so we don't know what is the path。

First of all， we consider a direct catch path， but now if we follow this algorithm。

 well be selecting first the shortest path vertex， so this is shortest because this is two that is infinity。

 so we will select this one。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_7.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_8.png)

And dixtra says that once you have selected one of the shortest path。

 then check via that vertex from that vertex， there is any shortest path to other vertexes。

 So let us check who is connected to 2。 So from 2， we can do 3。 This is 2 plus 4 that is 6。

 and right now it is infinity。 Yes， this infinity can be changed to 6。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_10.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_11.png)

This means that there is the shortest path from matrixx 1，2，3 of distance 6。

 No doubt it's not a direct path。 It's coming via 2， but there is a path。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_13.png)

That's how， the extra algorithm always select a vertex with the shortest path。

 Then it will update the shortest path to other vertexes， if possible。

And this adation is called as relaxation。Let me show you how this relaxation works for that I will call this vertex as U and this vertex as v。

 and this is distance of u and this is distance of v initially it was infinity nor is change to 6 and this is cost of an h from U to v。

 so here relaxation means if the distance of vertex U plus cost of an edge u comma v is less than distance of vertex v。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_15.png)

See here the distance of u was 2 and the cost of an edge was 4 and this was initially infinity so the2 plus4 is less than infinity Yes。

 so we have modified this to 6 so well modify this one that is distance of v is modified to distance of u plus cost of an edge U comma v。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_17.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_18.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_19.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_20.png)

This is what we followed and this is called as relaxation and we do relaxation for the vertices。

 When we select a shortest path， we will try to relax other vertices。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_22.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_23.png)

Now let us follow this procedure and solve this graph problem to find the shortest part。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_25.png)

Let me solve this graph problem for this I will select this vertex as the source vertex starting vertex as starting vertex Now I will give the distances for all the vertices by considering just single edge so I will level the distances above those verticexes only this distance is0。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_27.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_28.png)

And this distance is 2。 This distance is 4。From one to4。

 there is no direct edge infinity from one to five， there is no direct edge infinity。

 similarly6 is also infinity。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_30.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_31.png)

Except to entry3 all our infinity。 This is the initial thing that we should do for any graph。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_33.png)

Now。Let us start the repeating steps， Now steps will be repeating first step。

 select the shortest path out of2，4 infinity infinity infinity， this is smallest select this one。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_35.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_36.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_37.png)

Once we selected this， we should perform relaxation。 What is that check who are connected。

3 and4 are connected。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_39.png)

Just check the distance of U that is2 plus1 p， and this is4，3 is less than four， modify this。

Then this is also connected2 plus 7，7 is， this is 9， and this is infinity。 modify this9。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_41.png)

That's all some vertices are relaxed。 They may or may not relax， but we should check this one。Now。

 second step。 Now the step is repeating same thing I should do。 select the smallest1。

3 infinity 9 infinity， Which one is the smallest short as this one。 Select this one。

 Now check if any vertex gets relaxed。 So there is only one connected is 3 plus 3，6。

 This is infinity。 so change it。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_43.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_44.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_45.png)

Now， select the shortest out of what6，9 infinity。 Which one is shortest， This one。

 Select this one and see who are connected and try to relax them。 So6 plus 2 is 8 and is 9。

 So this is more smaller， modified 6 plus 5 is 11。 This is infinity modified。😊。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_47.png)

So two vertices are modified， they are relaxed。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_49.png)

Now， who are remaining 4 and 6。 Who is minimum 8。 Select this one。And check if anything gets relaxed。

8 plus1 is 9， it's already 11 modify it。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_51.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_52.png)

So here I have taken an example。 most of the time the vertices are modifying their distances are modify。

 They may or may not modify。 Now， the last one is remaining as 6。

 So now we have the shortest parts from starting vertex 1 to all other vertices。

 So what are the other vertices，2，3，4，5 and 6。 What are the distances I got for2， it is 2 and 3。

 it is 3 and 4。 It is 8，5 is 6 and 6es 9。 These are the distances of all the vertices。

 and these are the set of vertices。 These are Dvs。 and these are vertices。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_54.png)

So that's how a test trail garden works on a graph to find in the shortest path。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_56.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_57.png)

Let us little bit analyze and find out the time complexity of this algorithmgar。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_59.png)

If you analyze what it is doing， it is finding shortest parts to all the vertices。

 How many vertices are there。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_61.png)

These are the vertices。 Or we can also say N number of vertices。

 So for all vertices is finding shortest path。 while doing so， what it is doing， it is relaxing。

 relaxing which vertticexes when it is on 3， It is relaxed。 It has relaxed only 5。 when it was on2。

 It has relaxed only 3 and 4。 So total how many vertices it may be relaxing。

 We don't know it depends on the graph。 Okay， at most how many vertices it may be relaxing。

 All N vertices suppose two is connecting to all。😊。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_63.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_64.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_65.png)

Then it may be relaxing all of them。 It may be checking all of them。 So again， it is V。

 So it means n into n n for vertices and n vertices are relaxed。

 So when it will happen that from two all are connected， then again， three all are connected。

 that will be a complete graph in case of complete graph， it will take n into n time。

 and this will be n square。😊。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_67.png)

So this is the worst case time of textx algorithm maximum time it may be order of n square。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_69.png)

I can write this tee off。V square or the off n square。 The merge is time。 and I can use theta there。

 Once I know that function that is n square， and it belongs to some class that is N square class quadratic class。

 So this is the of n square。 Here I have a weight directed graph commonly found in textbooks。

 on this， we will run the extra algorithm to solve single source shortest part problem。

 So I will not be updating the distances upon the vertices itself。

 but I will be writing them in the table。 So let us see how I can prepare this table。

 instead of writing there， I am writing here。 So initially。

 I should find the directors pass to all the vertices。 So for 2， it is 5，53， it is 45， likewise。

 all the parts are given。 And one thing to mention here， the starting vertex is 1。

 So in the graph you can see 1 to 2，50，1， to 3，45，1 to 4，10，1 to 5， No edge 1 to 6。 No edge。😊。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_71.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_72.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_73.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_74.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_75.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_76.png)

So 50， 45，10 in Indianfinity already given。A is solid。 the smallest vertex is 4。

 So is selected vertex 4。 So the selected vertex is 4。 Then once the vertex 4 is selected。

 see from 4，5 is connected。 So can we relax this one。 So 4 is a 10，10 plus 15，25 Yes。

5 can be modified， and we got a path that is infinity。 So it is 25 now， and this remains infinity。

 and this is 10， which is already selected 45 and 50， They remains as it is。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_78.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_79.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_80.png)

Now， select the next smallest one。 So this one。What x5 is selected。

 so what x 5 when that is selected there is an h to 3 and there is an h to2。

 so if I take 2 how much is 5，25 now， so I did not mention here 25 plus 2045 and this distance is already 50。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_82.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_83.png)

This is 50， but now we have a shorter path y 5 that is 45， so modified is 45。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_85.png)

And this is also 45， this 10 is selected， 25 is selected， this still remains infinity。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_87.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_88.png)

Now， I have to select the next shortest one， So I have 45，45 infinity， so I can pick up any one。

 so I'll select the second vertex 2。 Once vertex 2 is selected from there， the connected vertex is 3。

 So plus 10。😊。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_90.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_91.png)

45 plus 10，55。 But already， the distance to trees is 45。So 45 plus 10 will be 55。 so this is smaller。

 no change。 So this remains as it is。45 is already selected。 This remains 45 only10 is selected。

25 is selected and infinity。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_93.png)

Select next minimum， so three，3 selected。Now from3， there is an edge coming towards 5。

 but 5 is already in the selected vertex， dont check it。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_95.png)

If you check also， it's of no use。 see 30 is how3 is how much，45，45 plus 30 will be 75。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_97.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_98.png)

So already5 is having its weight as distance S 25， so no use of checking it。

 so nothing is relaxed and this is selected。 Thats all so 45 selected 46 is also selected10 selected 25 selected infinity。

Now， who is remaining infinity is remaining。 So 6 is also selected。

 So the path to vertex 6 has remained infinitefin only because there is no incoming at John 6。

 so we cannot reach 6。The path verex existses infinity only with how the algorithm works。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_100.png)

This algorithm can work on non directed graph。 Also， suppose you have a graph。

 simple example I will take here。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_102.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_103.png)

Simple example I have taken here Now how it works on this one。

 So if you are not comfortable with non directed edges。

 you can convert them into directed by adding parallel edges so you can say this is3 and this is also three。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_105.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_106.png)

Now it becomes a directed graph， so you can convert a non directed graph to directed graph right so it can work on both directed id as non directed graph。

Now I will show you the drawback of Dxtra algorithmm。

 Let us see the drawback of Dx algorithm for that， I have taken a very simple graph and it is having a negative weighted edge。

The weight of this set is negative。So weight of an edge， how it can be negative。 See。

 it is not distance。 So distance is not not measured in pause negative， right。

 but any problem or any business problem， we can represent it using grass。Like usually。

 when we want to explain something to our friend then what we do。

 we just take a paper and draw something。 So what is that， It looks like a graph only。

 So most of the problems from real world are mapped in the form of a graph。

 So when you are representing something in the form of a graph。

 it may have positive and negative as also。So this is not exactly distance that is measured by tape。

 but this is some value。 So those values can be negative also。 So actually。

 the extra has not considered that if there are negative edge then what we should do。

 he has not considered。 Let us see what happens if you follow his procedures on this one。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_108.png)

Let us start。 if I say this is the starting vertex， then the distance is 0。

 that the direct edge path is 3 and the direct edge path is 5 and there is no direct edge path。

 so this is infinity。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_110.png)

This is the initial setup object Jtra。 Now， let us solve this one。

 Which1 I should select the smallest one。 The shortest part is to select this one。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_112.png)

Are there any connected vertices to this one so that I can relax。 No。

 there is no outgoing edge just front to leave it。Next， select the next is smallest。

 So 5 and infinity。 So5 is the smallest。 So select 4。 If we select this 4。

 then will it relax any vertex Yes the connected vertex is 3。 So what is that part，5 plus 2，7。

 So this is 7。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_114.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_115.png)

Now， both are selected。 Third one is remaining。 Select that one also。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_117.png)

Once this is selected， shall we relax that one。 No， no need。 already。

 we learn that when already vertex is already relaxed， no need to check it。 Let us check it once。

7-3 is 4。 No already is 3。 So that's there。😊。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_119.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_120.png)

So all the things are perfect。 The answer is perfect。 So this algorithm has workedd。

 even when there is a negative weight edge。Now I'll make a small change。 I'll restart again。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_122.png)

I'll start over again。 And now I will make this edge as -10。 Let see what happens now。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_124.png)

I am again finding the shortest part to all the vertic says。 This is the source verex So it is 0。

 and this is 3， and this is 5。 and there is no direct part infinity。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_126.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_127.png)

I'm performing disturbance again because I have changed an edge。Now， let us see。

 Select the minimum 1。 So two is minimum selected。 Anything get modified。 No。

 next minimum is this one。 Anything get modified。 There's 5 plus 2 is 7 Mo us。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_129.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_130.png)

Next minimum is this one。 and this is the last one。 Sheed flags that no it's already selected。

 but let us check it once 7-10。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_132.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_133.png)

-3。 Now， actually， the part we found was a3。 But now we realize that when we come along these vertices and reach here。

 it is -3。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_135.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_136.png)

So we were in a hurry to select the shortest path to vertex 2 when we select it as 3。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_138.png)

베버스！If we would have tried the other way， we would have got the。



![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_140.png)

Better answer。 So actual correct answer is -3， but thistra has given us the wrong answer and also ask us not to check those vertices。

 which are already as we should not。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_142.png)

Check them because no need to check。 You will not find any better answer。

 But here we are finding a better answer。 The reason is we have a negative edge。

 So this may work or may not work in case of negative edges。

There's all about singles for short part problem。 And the approach was greedy。 You can see。

 You can see the greediness here。 But see， it is not trying all possibilities and selecting the minimum 1。

 It found that this minimum selected。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_144.png)

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_145.png)

Right this is for the greedy approach， so greedy approach has failed here when there are negative vectors。

Allright， there is another solution for this single source shortest part problem that is Billman Ford's algorithm。

 we will see that in dynamic programming。Alright， so next video will be on dynamic programming。

 These are the topics I have covered from3 method。 Leave your a comment so that I can know how you are following the videos。

 right， If any suggestion， just give me。

![](img/69c7d679d3cb7b7d1ca06ec7d2dcd678_147.png)

I'll try to implement them in my next videos。