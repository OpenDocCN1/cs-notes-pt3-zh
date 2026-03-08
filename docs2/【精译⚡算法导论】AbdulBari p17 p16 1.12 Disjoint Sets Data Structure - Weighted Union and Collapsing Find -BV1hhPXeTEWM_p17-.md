# 【精译⚡算法导论】AbdulBari p17 p16 1.12 Disjoint Sets Data Structure - Weighted Union and Collapsing Find -BV1hhPXeTEWM_p17-

The topic is， disjoined sets。

![](img/c04b099741deaa52439c003d29cb9afa_1.png)

In this video， I will cover the following things。 First is。

 what are disjoint sets and the operations on them。



![](img/c04b099741deaa52439c003d29cb9afa_3.png)

Then detecting a cycle see disjoint sets are useful for detecting a cycle in nondirected graph or undirected graph。

 so we will take an example and learn how to detect the cycle in a nondirected graph then graphically how to represent these disjoint sets and how it can be represented using array and lastly the time efficient operations on disjoint sets are weighted union and collapsing find that are based on the ranks or weights we will see that。



![](img/c04b099741deaa52439c003d29cb9afa_5.png)

![](img/c04b099741deaa52439c003d29cb9afa_6.png)

![](img/c04b099741deaa52439c003d29cb9afa_7.png)

Djoint sets are similar to sets topic in mathematics， but not exactly。

 They are a little bit change for making them useful in algorithms。

 So the famous algorithm that uses disjoint sets as C algorithm， which detects a cycle in a graph。

 So let us see how these disjoint sets are different from normal sets of mathematics。

 Let us understand what are disjoint sets。 See here I have a non connected and non directed graph。

 There are two components。 It's not connected graph two components I have taken。

 and each component I have represented it as a set set as1 is having one，2，3，4。

 These are the vertices of this component。 and set to is having5，6，7，8。

 These are the vertices of second component。 So the two different components are representing two different sets。

 and what is a disjoint here。 So no vertex。

![](img/c04b099741deaa52439c003d29cb9afa_9.png)

![](img/c04b099741deaa52439c003d29cb9afa_10.png)

This common here。 The numbers are not common here。 So if you take intersection of these two。

 S1 and S2， then you will not get anything Phi empty set。 So that is disjoint。 disjoint segments。

 Two sets are not having anything common。Then how we use them， What are the operations on them。 See。

 we prefer performing only two operations that are find and union。

 I'll show what does it mean by these operations。 So first operation， find。

I want to know what X 5 belongs to which set。😡，It's not here。 Yeah， it's here。

 so it belongs to set 2。Find operation is to find out any element or a vertex belonging to which set。



![](img/c04b099741deaa52439c003d29cb9afa_12.png)

It's like a set membership operation also means that element is a member of which set。

 So like I want to find out 7，7 doesn't belong here。 Okay， here it belongs。 So it belongs to set2。

 then3， find 3， find3 where it is here。 So it is set  one。 So that set。

 find operation is very simple。 So you have to find out in which set it belongs to。

 So I am showing you just mathematically later we will come to the data structure。



![](img/c04b099741deaa52439c003d29cb9afa_14.png)

![](img/c04b099741deaa52439c003d29cb9afa_15.png)

![](img/c04b099741deaa52439c003d29cb9afa_16.png)

![](img/c04b099741deaa52439c003d29cb9afa_17.png)

Now， let us look at union operation。See， for showing a union operation。

 I'll try to connect these two with an edge。

![](img/c04b099741deaa52439c003d29cb9afa_19.png)

I have added this edge， this edge that is 4 to 8。 So when you add an edge。

 then what we do here is we perform union operation。 So we connected what。



![](img/c04b099741deaa52439c003d29cb9afa_21.png)

4 comma 8， we have connected。 Now， find 4，4。 Yeah， it belongs to set 1， find 8。8。A， here it belongs。

 So it isn't set to。 So find 4 and find 8。 They belong to two different sets。

 So perform union S 1 union S 2。 So now we get a set that is 1，2，3，4，5，6，7，8。This is union operation。

 See in mathematics， simply we perform union on two sets。

 but here there is a reason of performing union。 What is the reason if there is an edge you come a V find out you it to which set it belongs and find out V to which set it belongs。

 And if they belong to do different sets， then perform union of those two sets。

 This is the purpose of performing union。 Now why we are doing this。 Let us see next。

 I'll add one more edge 1 to 5。

![](img/c04b099741deaa52439c003d29cb9afa_23.png)

![](img/c04b099741deaa52439c003d29cb9afa_24.png)

So this was one to five。Now， we don't have these sets that are union。 and we got a new set。

 Let us call this as set 3。 So we have a new set。 Those elements are gone。 This is the final set。

 Now， one comma 5，1， Yes， find one。 It is present here。 find 5。 Yes， it is present here。 Now。

 both these vertices or numbers are belonging to same set。

 And if they belong to same set means there is a cycle。That's it。

 This is the way we find out a cycle in a graph。 So what are the things we learn。

 what is find operation， What is union operation and what is the purpose of union operation。

 Then how we can know that there is a cycle in a graph。

 If you take an edge and both the vertices are belonging to same set。

 Then there is a cycle in a graph。 So this was a very simple example。

 I have shown you what does it mean by find and union。 Now we will take one example graph。

 and we will see from the beginning， how we can detect cycle in a graph。

 I will form all the sets right from the beginning。 I will add all the edges one by one。

Let us take an example and find out how we can find our cycle。

 how we can detect a cycle in a graph by with the help of thesejo sets here I have taken one example graph and in this I have labeled the vertic says So let us say these are some weights。

 So just like let us find a minimum course planning tree from this one otherwise you can also say that I have numbered them So first edge that I'll be taking is this one then this one second one and third and fourth in this way I will include all the edges of a graph。



![](img/c04b099741deaa52439c003d29cb9afa_26.png)

![](img/c04b099741deaa52439c003d29cb9afa_27.png)

Now how we can take the help of disjoin sets for finding a cycle。

 let us check see there are eight vertices I have taken a universal set with eight vertices。

Each element you consider it as a set。Now let' us start。

 what we'll be doing is we will be going on taking edges including edges and forming the sets for them one by one。

 So the first edges1 comma2， so the first edges1 comma2， so find one one is here。



![](img/c04b099741deaa52439c003d29cb9afa_29.png)

And find two， it is here。 So actually they are in universal set。 So form a set for them。

 take one and2。 So perform union on one and 2。 So from this universal set。

 they are removed and they are brought into set 1 as one。



![](img/c04b099741deaa52439c003d29cb9afa_31.png)

Now， next edge， next edge is3 comma 4。 So 3 comma 4。



![](img/c04b099741deaa52439c003d29cb9afa_33.png)

3 is in universal set。 Remove this。 Find4。 This is in this universal set。 Remove it。

 So form a set that is set2 with3 and 4。

![](img/c04b099741deaa52439c003d29cb9afa_35.png)

Then third edge 5，6。 So this is 5 comma 6， and they belong to universal set。

 remove them from there and form a set for them，5，6。



![](img/c04b099741deaa52439c003d29cb9afa_37.png)

![](img/c04b099741deaa52439c003d29cb9afa_38.png)

The next one is fourth edges 7，8。 So take 7 and 8 and find 7。 It is here。 find 8。 It is here。

 They are in universal set form a set for them that is 7 and 8。



![](img/c04b099741deaa52439c003d29cb9afa_40.png)

![](img/c04b099741deaa52439c003d29cb9afa_41.png)

![](img/c04b099741deaa52439c003d29cb9afa_42.png)

Now， the next edge after the fourth edge， this is the fifth edge I' am going to take。

 That is2 co of 4。 Now， I can see that all these vertices are removed。 Numbers are removed。

 They are in different sets now。 Now， find it2。 It's not there。 Just forget this one。 Find it too。

 It is here。

![](img/c04b099741deaa52439c003d29cb9afa_44.png)

Find4。 It is here。 So they are in two different sets。 a perform union。

 So I will form a new set that is set 5 by taking union of these 2，1，2，3，4。

 I have performed union on these two sets。 Now you can see that union is being performed。

 Let us go to our next edge。 after two comma 4。 This one，2 comma 4，6，1 is this one。 That is2 comma 5。

 So two comma 5。

![](img/c04b099741deaa52439c003d29cb9afa_46.png)

![](img/c04b099741deaa52439c003d29cb9afa_47.png)

![](img/c04b099741deaa52439c003d29cb9afa_48.png)

Find two so two is in this set now is our union， remove them。



![](img/c04b099741deaa52439c003d29cb9afa_50.png)

This is in set 5， and 5 is in set 3 perform union of these two and former set 6。

 So what are those vertices，1，2，3，4， and these 2，5，6。 See the reason of performing unionists。

 we are including an edge， considering an edge。

![](img/c04b099741deaa52439c003d29cb9afa_52.png)

So this set is also gone。 We have a union。 This is also gone。 Now， we have only two sets now。



![](img/c04b099741deaa52439c003d29cb9afa_54.png)

Right。Now， after this edge，7 edges， this one，1， comma 3，1， comma 3。 and' remove these sets。

 And I'll just write two sets here。 Find one。 It belongs to set 6。 Find 3。 it belongs to same set。

 So when they both belong to same set， it means there is a cycle。 Yes。

 you can see that by taking this edge， I'll be forming cycle。

 I will highlight the edges that I have included so far。 See， I have included these edges。

 I have included these。😊。

![](img/c04b099741deaa52439c003d29cb9afa_56.png)

![](img/c04b099741deaa52439c003d29cb9afa_57.png)

I have included these edges。 right， now， if I include this edge， this will form a cycle。

 so don't include this。That how the edge， which is forming a cycle don't included。

 We have detected one cycle。 Let us continue After that7 edge， the next edge 81 is this one。

 So 8 is watch 6 and 8，6 and 8。Let us see。 find 6，5 6，6 belongs here。5，8，8 belongs to this one。

 So they are in different sets。 perform union。 Now， we'll get 7th a set。 And what is that 1，2，3，4，5。

6 from this set and 7，8 from this set，7 and 8 from this set。 So these two are gone。

So this is also included。Now， the last edge remaining is 9，1，5 comm 7。5 comma 7，5 and 5。

 It is in the set。 find 7。 This also in the set。 Both all are in same set only now。

 as they both belong to same set， there is a cycle。

So this is how crystal algorithm also uses it in the same way for finding a spanning tree like you may be knowing that in crystal cell always we select a minimum ca edge now shall we select it or not is it forming a cycle or not how we can know by checking into the sets so this was like a working off a crystal cell only。



![](img/c04b099741deaa52439c003d29cb9afa_59.png)

![](img/c04b099741deaa52439c003d29cb9afa_60.png)

Now， how it is done graphically and how it is represented using array that we have to see。

 So I'll take the same graph and show you。 Let us quickly look at how we can show the sets graphically。

 So I will do the same thing。 I have the same graph and the vertices these instead of universal set。

 I have shown them as vertices here。 that is I have taken notes Now I will go on including the edges。

 So the first edges1 comma 2。 If I include edge 1 comma 2。 you remember I was making a set as12。

 Now actually we don't need a set， we are not performing mathematical operations here。

 like intersection union difference we are not performing that one。



![](img/c04b099741deaa52439c003d29cb9afa_62.png)

So what we want is just we want to detect a cycle so we want to do it in an easy way。

 so instead of showing it like this graphically we will take one and two basically we don't need the name of a set we need just one representative of a set so we will make whatex one as a parent of set and two as a child if you like you can make two as a parent and one as a child also。



![](img/c04b099741deaa52439c003d29cb9afa_64.png)

![](img/c04b099741deaa52439c003d29cb9afa_65.png)

So let me show you other edges that is3 comma 4。 so if I take 3 commas 4 and make a set，3，4。

 so three as a parent and four as a child of it。

![](img/c04b099741deaa52439c003d29cb9afa_67.png)

![](img/c04b099741deaa52439c003d29cb9afa_68.png)

Now， third set that is 5，6 I。

![](img/c04b099741deaa52439c003d29cb9afa_70.png)

Then， set for。7 comma 8， I have included4。Edges， I got four set graphically they are shown like this。

 Now， let me include the next one from here。 you can get the clear picture。



![](img/c04b099741deaa52439c003d29cb9afa_72.png)

Edgege 2， comma 4，5，1，2 comma 4。 So where is 2。2 is here。 Who is a parent of 2，1。 The next is 4。



![](img/c04b099741deaa52439c003d29cb9afa_74.png)

![](img/c04b099741deaa52439c003d29cb9afa_75.png)

Find4。4 is here。 Who's a parent of4，3。 So these are in two different sets。

 So you remember we perform union， how to perform union。

 So we'll select one as a parent and two as a child here。 And it's a child is a3 and 4。

So we made the parent of one set as a child of the parent of another set。So you may be asking that。

 why didn' you select a three other parent if you want to select that one also it makes no difference。

It makes no difference whether you take three as a parent and one you make it as a child of three。

 it makes no difference。

![](img/c04b099741deaa52439c003d29cb9afa_77.png)

Then next one after fifth， sixth one is a two co a five。



![](img/c04b099741deaa52439c003d29cb9afa_79.png)

2 is here。 Who is the parent of this one，1， then5 is here。 So they are in two different sets。

 These are in two different sets。 So well include that 5。 we will bring it here and6 here。Actually。

 these are gone。 I'll remove them。Now， again， one more thing。Here also， you can ask a question。

 Why didn' you select 5 as a parent。 See here I have a strong answer that before including this。

 see how many nodes are there， Four nodes are there。 So weight of this is set as more。

 and this weight is less。 So we will make this as a parent and this as child。 earlier。

 although both the sets were having the same number of elements。 But now this is set 1，2，3。

4 is having more number of elements，5，6 is having just two elements。

 So this is representing this set， you see，1，2，3，4，5，6， This is。5th， sixth set。 If you remember。

 already we have done this。 So now this is gone。

![](img/c04b099741deaa52439c003d29cb9afa_81.png)

Now， next is7，1，1 comma 3。

![](img/c04b099741deaa52439c003d29cb9afa_83.png)

1 comma 3，1 is the parent itself， and three is parent is one。

 so both of their parent is one only it is one only so they belong to set one。

 so both belong to same set so its a cycle。That's enough。 Ill not go further。

 So this is how we detect whether there is a cycle or not graphically I have shown you now let us see the same thing again with the help of an array。

 how it is done using array。 Now I'll show you the graphical representation as well as array representation see for representing a set we don't need the name of a set。

 we are not performing actual union intersection or set difference operations of mathematics we just want to perform find an union。

 Our objective is to detect a cycle。 So for that。

![](img/c04b099741deaa52439c003d29cb9afa_85.png)

![](img/c04b099741deaa52439c003d29cb9afa_86.png)

For all eight vertics， we will take a single array called parent。

And the indices are representing these eight verrtices and each is having value minus1 means each vertex is in its own set next to show you graphically how it looks like I have even taken these eight nodes。



![](img/c04b099741deaa52439c003d29cb9afa_88.png)

Now let us perform the same thing on this graph and see how we will represent sets in an array and also I'll show it graphically。



![](img/c04b099741deaa52439c003d29cb9afa_90.png)

![](img/c04b099741deaa52439c003d29cb9afa_91.png)

So fars edge 1， comma 2。1， comma 2，1， who is a parent of 1 -1 itself。



![](img/c04b099741deaa52439c003d29cb9afa_93.png)

2， find 2。 go to index 2 and see what is there-1。 So who is a parent of2 itself。

 So how much time it has taken for finding one and finding two Find 1 is -1， find2 is -1。

 So constant a time。 So they belong to two different sets the perform union。 how we perform union。

 So graphically， I will show， I will select one as a parent and two as a child。

 So two is a child of one。 So here we will write1。 So who is a parent of two now，1。

 And what is one-1。 So there is a parent。So if there is -1 or negative value， then its parent。

 Now I'll do one more thing。 total how many nodes are there。 Two nodes are there。

 So instead of writing just -1， I'll write negative only。 So -2。 So there are two things。

 shows that it's apparent and2 shows that there are two nodes here。That's it。 Let us continue。

 repeat the same thing for all of them。 Next edges 3 comma 4，3 comma 4。



![](img/c04b099741deaa52439c003d29cb9afa_95.png)

![](img/c04b099741deaa52439c003d29cb9afa_96.png)

Find 3-1。Itself is apparent。4-1 itself is a parent。 So form set。 So who is a parent of 4，3。

 And what is a3， It's parent。 But there are two nodes in this one，5 comma 6， third1。 So find 5。

 This is -1， find 6-1。 So 5 here and 6 here。 So this is 5， and this is -2。

 Now the next edge is this one，7 comma 8， find 7 itself is a parent。 find 8 itself is a parent。 Now。

 make 8 as a child of this7 or 7 as a parent。 So this is 7， and this is 2。



![](img/c04b099741deaa52439c003d29cb9afa_98.png)

![](img/c04b099741deaa52439c003d29cb9afa_99.png)

![](img/c04b099741deaa52439c003d29cb9afa_100.png)

De here we have finished。

![](img/c04b099741deaa52439c003d29cb9afa_102.png)

Next，5 edge，2 come a4，2 come4， find 2。1 is a parent。 find 4，3 is apparent。

 Let us do it in an array 2， go to 2，1， go to 1-2。 So who is the parent of this1，1。



![](img/c04b099741deaa52439c003d29cb9afa_104.png)

Find4， go to 4，3， go to 3，-2。 So who is the parent of this one，3。 And this was one。

 They are different parent。Perform union。So whom we should select as a parent， one。

 we will select it as parent。 So at a three， I will write one。Then total how manyy nodes now，4 nodes。

 So graphically，3 will come as a child of。1， and here is 4。That's it。 So that's how union is done。

 Now， let us take next one。

![](img/c04b099741deaa52439c003d29cb9afa_106.png)

Fifth， now this is sixth。都 ga five。

![](img/c04b099741deaa52439c003d29cb9afa_108.png)

2 and 5。Let us see who is a parent of 2，1。 Let us look at here，2。 It's 1。 go to 1。 It's -4。

 Just one step we are going， right， It's not any time。 We consider us constant time only。55，5。

 go to 5-2 itself is parent。 So for2， this is parent。 and for five itself is parent。 Now。

 who should become the parent for both。 We have to perform union now， unite these two。

 So who should become parent1 or 5。 See what is there at 1-4。 What is there at 5-2。

 whose weight is greater， rank is greater weight or rank， both are same only here。

 We call it as rank Also， whose rank is greater， one's rank is greater。

 So let 5 come as a child of one。So at 5 we write1 now two more movess are added to this。

 so4 and that minus2 is added， so it becomes soil。Two more nodes are added to it that 4 and  minus-2 it becomes 6。

 so total6 nodes are here。This is how union is performed。



![](img/c04b099741deaa52439c003d29cb9afa_110.png)

Let us go to next one after 6，7，7 this what，7， this one comma 3。 This will be interesting。 Find one。

1。 Okay， here in this one itself is a parent。 find 3，3。 Who is a parent 1。 Okay， here in an array 3。

1， go to one minus-1。 So the parent is same。 So for both one and three parent is same。

 Both our parent are same。 So it means they belong to same set and it's a cycle。

 If you include one comma 3， it will form a cycle。 See so far we included these edges， right。

 we have included these edges。 And if you include one comma 3， this will form a cycle。

 So don't include this one。 So that's our inclusion of any edge， will it form a cycle or not。

 we can know it with the help of this disjoint sets。😊。



![](img/c04b099741deaa52439c003d29cb9afa_112.png)

![](img/c04b099741deaa52439c003d29cb9afa_113.png)

![](img/c04b099741deaa52439c003d29cb9afa_114.png)

![](img/c04b099741deaa52439c003d29cb9afa_115.png)

![](img/c04b099741deaa52439c003d29cb9afa_116.png)

I can continue like this。 O， let me quickly finish the rest of them Also。 But here，5 comma 6 is gone。

 It is coming under this one。 Now， let us state next edge 6 8，6a 8， find6，6 parent is 5。

5 parent is 1。 So go here in the NRA。 Let us see here。 Also，6 parent is 5。 and five parent is 1。

 and one' parent。 There's one itself is the parent。😊，So one is the parent of 6。

 Now we're about 8 find 8 in this graph。 you can see this graphically。 it is 7。 So go to 8 and 7。

 go to 7。 It's -2。 So this is the parent。 So perform union on one on 7。

 Now who is greater-8 is greater。 This is -2。 So make this7 parent as 1 and add two more nodes here and graphically show it like this7 and 8。

😊。

![](img/c04b099741deaa52439c003d29cb9afa_118.png)

![](img/c04b099741deaa52439c003d29cb9afa_119.png)

That's it。 Now， the last one is 91。 This is included。 Now，91， if I try to include5 and 7。

55 parent is 1， find 7 parent is 1。 Look at here，5，1 only 7，1 only。 So for both of them， parent is 1。

 So inclusion of 9 will form a cycle。

![](img/c04b099741deaa52439c003d29cb9afa_121.png)

![](img/c04b099741deaa52439c003d29cb9afa_122.png)

![](img/c04b099741deaa52439c003d29cb9afa_123.png)

![](img/c04b099741deaa52439c003d29cb9afa_124.png)

So this is how a simple array of values are sufficient for finding。

Whether there is a cycle or not with the help of find and union operation， That's all this。

 What just one thing is remaining here。 See， I， instead of taking just -1。

 I was taking ranks or weight and the union was performed based on whoever weight is higher。



![](img/c04b099741deaa52439c003d29cb9afa_126.png)

![](img/c04b099741deaa52439c003d29cb9afa_127.png)

![](img/c04b099741deaa52439c003d29cb9afa_128.png)

Right so this is weighted union。 Now one more term is used that is collapsing find。

 So let me tell you one thing here， see if I say find2 go to 211 is negative， just two steps。



![](img/c04b099741deaa52439c003d29cb9afa_130.png)

Find 3。 Go to 3，1 at 1-8。 So one is parent。 just two steps， constant steps。 Find 4， go to 4， go to 4。

 It will take you to 3。 go to 3。 It will take you to one than here。 So the time is more。

 time is more。 So here for some knows。 the time may be more。

 You have to go along the parent and parent and parent。 Then finally。

You will get the root or the main parent of a set。So what we do in this situation is when we find that parent of six is five and then its parent is one so finally parent of six is1。

 so for this we have to take multiple steps， but once we found out that the parent of six is one we don't have to keep it there only we can directly bring six under one。

So here， also in six。5 is the parent。5 parent is1。 So for6。 Also it is one。

 so we can directly modify this one。 Now， whenever we say find 6， go to index 6， what is find1。

 So at one it is negative。 So parent of6 is one。 directly in constant time。

 we can know parent of any element。 So this procedure of directly linking a node to the direct parent of a set。

Is the called as collapsing find？With collapsing find。

 we can reduce the time for finding the same value next time。 first time we spending some extra time。

 but next time in constant time， we can get the parent the same way suppose I find 8 from 8 go to 7 from 7。

 go to 1。 let us do it here。 go to 8，77 is1 go to1 parent。 So once you know that 8 is under one。

 So directly bring it under one。 So here also we can write 1。



![](img/c04b099741deaa52439c003d29cb9afa_132.png)

So whenever you find an element， you can collapse it to its Ta parent。



![](img/c04b099741deaa52439c003d29cb9afa_134.png)

So that's all how we can use array for representing disjoint sets and even link list can be used for doing this so for link list we can explore it I have shown about array in detail everything I have shown you when we use link list then we have to take nodes and in the node we have to write on these indexs of index we have to keep it as a value that is the node value and I point to the pair and point to the next node so you can explore that by yourself。



![](img/c04b099741deaa52439c003d29cb9afa_136.png)

![](img/c04b099741deaa52439c003d29cb9afa_137.png)

![](img/c04b099741deaa52439c003d29cb9afa_138.png)

![](img/c04b099741deaa52439c003d29cb9afa_139.png)

That's solved with a disjoint set。