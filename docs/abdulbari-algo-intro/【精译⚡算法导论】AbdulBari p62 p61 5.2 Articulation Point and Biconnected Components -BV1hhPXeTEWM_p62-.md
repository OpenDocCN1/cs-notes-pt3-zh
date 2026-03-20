# 【精译⚡算法导论】AbdulBari p62 p61 5.2 Articulation Point and Biconnected Components -BV1hhPXeTEWM_p62-

Hi， the topic is articulation point and bi connected components。

 so let us know first what is an articulation point。



![](img/fb4998d581c01a1ea62c77f641d7ab39_1.png)

In a graph。

![](img/fb4998d581c01a1ea62c77f641d7ab39_3.png)

If there is any vertex whose removal will disconnect the graph into multiple components。

 then that vertex is called as articulation point in this graph I have taken an example。

 this3 is a vertex if you remove this3 then this one。

4 and 2 will form one piece that is one component 5 and6 will form another component if I remove this three。



![](img/fb4998d581c01a1ea62c77f641d7ab39_5.png)

That's how three is an articulation point。If a graph is representing some network。

 road network or computer networks， then we don't want any articulation point if that articulation point is having any problem then the network will break into multiple components。



![](img/fb4998d581c01a1ea62c77f641d7ab39_7.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_8.png)

Even if anything is failing in the network also， network should remain as intact as a one single component。

So that is the problem of articulation point so we prefer that articulation point should not be there in the graph if there is an articulation point we will like to remove that articulation point so the solution is if you know what are the components in this one like I can directly see that 14 and 2 and 56 are two different components just join an edge between them if you connect an edge now there is no articulation point in the graph。



![](img/fb4998d581c01a1ea62c77f641d7ab39_10.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_11.png)

If you remove3 also， this 5，6 will be connected via a4。



![](img/fb4998d581c01a1ea62c77f641d7ab39_13.png)

And if 4 is also removed， the probability that multiple nodes are failing is less。

RightSo anyway if3 is removed then the graph will not break into multiple pieces。

 so there is no articulation point， so how to remove articulation point connect the components with an edge。

Sos all what articulation point。 Now we want a procedure to find out articulation point just by looking at a graph we are able to see this one。

 but however our computers or machines can do that。

 So for that there should be a procedure or an algorithm。

 So now I will explain you the algorithm for finding articulation point。

 So the procedure is first step preparepa a defer search spanning tree for this graph。

 So first prepare as defer search spanning tree。 So I don't want re I want spanning tree。

 So if I start from vertex 1， then I can go on vertex 4， then from there I will go to vertex 3。

 then Ill go to vertex 5 from there I will go to vertex6 and from6， there is an edge to3。



![](img/fb4998d581c01a1ea62c77f641d7ab39_15.png)

Now there is no more connected vertices46， come back to5 and come back to3 from3。

 there is a vertex that is2 and from two， there is an edge to1。And two。

 there is no more vertices connected，3， Also， nothing is connected，4， Also nothing is adjacent to it。

 So4 is completely explored。 One is also explored。 So all are explored。 Now。

 this is the def search span tree I got。This is the first step。 We are finding articulation point。

 Now for this defer search tree mention discovery time or defer search number for each vertex in the order in which they are visited。

 So defer search number I'll write just D。 D is1。 Then discovery time is2。 Disc time was 3。

 Next this we have visited。 So discovery time is 4 and discovery time is 5 and discovery time of this one is 6。

 So this is the order in which the vertices are visited。 So if I write the vertices 1，2，3，4，5，6。

 then their discovery times R。

![](img/fb4998d581c01a1ea62c77f641d7ab39_17.png)

1，2 was 6， Then three was visited at 3， and 4 at 2。



![](img/fb4998d581c01a1ea62c77f641d7ab39_19.png)

5 at 4， and，6， and 5。

![](img/fb4998d581c01a1ea62c77f641d7ab39_21.png)

5 at4 and 6 at5， these are the discovery types。Next step now we have to find out the lowest discoveryy number or defer search number reachable from any vertex by taking one package。

 so these are called as actually back。So。From one， I can go to descendants and descendants and take this two and come back here。

 so from one lowest number is one only。

![](img/fb4998d581c01a1ea62c77f641d7ab39_23.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_24.png)

Then from2 the lowest number that is reachable from2 is d1。Right from three from three。

 I can go to2 and then to one， so one， so this means that what we are trying to find out is there is some path that is going back to the parent right from three if I go downwards also there is a path to the parent。



![](img/fb4998d581c01a1ea62c77f641d7ab39_26.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_27.png)

Then。For four， from four， I can go to3 then two， then I can take a packet so the lowest number each able is1。



![](img/fb4998d581c01a1ea62c77f641d7ab39_29.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_30.png)

Then for  five， I can go to 6， and then。

![](img/fb4998d581c01a1ea62c77f641d7ab39_32.png)

I can come back to three， so this is three。And for six， the lowest deer search number is3， this is3。



![](img/fb4998d581c01a1ea62c77f641d7ab39_34.png)

So for 5 and 6， it is 3。 Now， the next step is to find out articulation point。 So for that。

 the condition is， if there are two vertices， U and V， where you is a parent。



![](img/fb4998d581c01a1ea62c77f641d7ab39_36.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_37.png)

And we is a child as per this def span。If there are two vertices， mince one is parent， one is child。

 So this is parent， this is child， this is parent。 this is child， this is parent。

 So there are many pair of vertices which are satisfying this relationship。

 Then the lowest number of V， if it is greater than or equal to D number of U。



![](img/fb4998d581c01a1ea62c77f641d7ab39_39.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_40.png)

If the lowest number of some vertex is greater or equal to the。

Der search your discovery number of its parent， then you is an articulation point。

 you will be an articulation point。So if this condition is true。

 then you is an articulation point and this condition is for all the vertices except root。Right。

 this will not work for root。 So leaving root， let us check other vertices 3 and 4。

 So what is the lowest number of three，3 is a child， right， lowest number of three is one。

 and what is the discovery number of four Defation number of four。 It is 2。 So this is one。



![](img/fb4998d581c01a1ea62c77f641d7ab39_42.png)

And this is two。 so no， this is not greater or equal。Then let us take next verortex。3 and 5。

 So let us say this is 3 and this is 5。 So L of 5 and D of U。 So D of 3， what is D of 3。

 D of3 is 3 and L of 5 lowest number of5 is3。 Oh， this is greater or equal。 So yes。

 So who is an articulation point here。3 is an articulation point。



![](img/fb4998d581c01a1ea62c77f641d7ab39_44.png)

T in our di。So this is an algorithm for finding articulation point。

 so you can write up algorithm for this one to perform defer search and also maintain defer search number if whenever you are getting any backage so maintain the lowest number also so this you can write on a program or an algorithm for this one。



![](img/fb4998d581c01a1ea62c77f641d7ab39_46.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_47.png)

Then after generating these two areass we can compare whether any condition is true here if any of such condition is true。

 then that vertex is an articulation point so our algorithm can find out articulation point our program can find out articulation point and if any articulation is point is found then we connect the an edge in between two components right from that articulation point the one side is one component the other side is another component we can add an edge between them。



![](img/fb4998d581c01a1ea62c77f641d7ab39_49.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_50.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_51.png)

![](img/fb4998d581c01a1ea62c77f641d7ab39_52.png)

So for making a graph stronger by removing an articulation point。

 we use this procedure we find out the articulation point and add an edge to remove articulation point。

Now last thing for the root， this condition will not be true right then if root is an articulation point because the traverse cell can start from anywhere。

 then how do you know if root is an articulation point see here root is having only one child if suppose root is having one more child someex is coming here than if root is having multiple children than root is an articulation point this is a different condition for root。

Right so that's all about bi connectedected components and articulation point。



![](img/fb4998d581c01a1ea62c77f641d7ab39_54.png)