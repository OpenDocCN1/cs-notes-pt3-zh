# 【精译⚡算法导论】AbdulBari p71 p70 7.3 Traveling Salesman Problem - Branch and Bound -BV1hhPXeTEWM_p71-

The topic is a traveling salesperson problem using branch and Bo strategy。

In this video I explain you about the problem then the approach of branch and bound。

 then I will solve a textbook problem using branch and bound。

 See the problem is a weighted graph is given Here is an example of5 verttices graph and we have to find out a shortest2 that is going through all the vertices1s and returning back to the starting vertex。

 So usually we take the starting vertex as1 so we have to go around all the vertices that is2，3，4。

5 and again we have to come back to verex1。 for that cause adjaency matrix is given here。

 Now let us understand how this problem is solved using branch and bound。

 So for that I'll take a small graph with just four vertices and I'll discuss the approach and we will solve this one See suppose there is a graph with just four vertices and suppose the salesman is starting from vertex 1 and he is going around all the vertices and returning back to vertex1。



![](img/ba5dbf1743e53021749806a7ad65c1b8_1.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_2.png)

And we want the two such that the cost is minimum， the cost of a tourist is minimum。

 So he may be going 1，2，3， then 4， then back to one， or he may be going 1，2，3， then 2，3 to 2。

 then2 to 4， then back one。 He can go in any order， such that the cost is minimize。

So for exploring this problem， we take the help of a state space  tree and we say that he is starting from vertex 1。

And we start from one， we are the vertices he can visit。

 he can visit to two also three also four also， so he can go to two also and3 as well as he can go on four。

 he can go on anyone one， but we want the one which is giving us minimum2 then if he has all reach or2 then what are the remaining vertices he can visit vertex 3 also or for either this or this and from3 he can go to two remaining vertices then from four remaining vertices are2 and three。

And when he have visited1，2 and 3， then he has to re visit remaining verex that is4 only and here is 3。

 and here is 4 and2。3 and 2。So this is a state space tree that is exploring the entire problem showing all the possibilities。

 all the possible tours。Now actually， backtracking and branch and bound， they are similar。

They both use state space Tra， but the approach is for solving a problem is different。

 so let me explain differences between backrack and branch mount here。Sa backting first of all。

 we will generate the state space tree， but this is a complete tree， how it is it generated。

Let me show you the nodes in which order they are first this node， then this one。

 then this next this one。Then go back and thisnor and thisn。Then this note， see。

 just you follow my marker in this order， they are generated。



![](img/ba5dbf1743e53021749806a7ad65c1b8_4.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_5.png)

So this is De for search or like preorder。And in back trackingracking。

 if suppose there are multiple solutions， so actually for every end node。

 it will give it as a solution。But we don't want all possible tools。 We want minimum cost to。😡。

So I'll give you an idea here。If suppose you want a minimum cost tour， find out this tour。

 find the cost， find this course also， this course also。

But if suppose this cost is smaller than these， then take this one。😡。



![](img/ba5dbf1743e53021749806a7ad65c1b8_7.png)

Next， find dis also suppose this is becoming larger。

 so discard this one because we have a shorter path already。



![](img/ba5dbf1743e53021749806a7ad65c1b8_9.png)

Then this is also larger discarded Sheos this is minimum。

 then take that sort of all possible answers， you can track them and find out which is better and you can take that form。



![](img/ba5dbf1743e53021749806a7ad65c1b8_11.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_12.png)

So you can use backting also for solving the problems。But backtracking is much time consuming。

That is the reason for solving optimization that is minimization or maximization problems。

 we avoid backtracking， we use it for permutation problems。



![](img/ba5dbf1743e53021749806a7ad65c1b8_14.png)

Now coming to branch and bound， see the same problem when it is solved using branch and bound。

 we used level order Watch here the order in which the nodes are generated this one second than this one then this one。

Then this， this。So in this order， the nodes are generated。

And while generating the node for every node， we find out the cost。



![](img/ba5dbf1743e53021749806a7ad65c1b8_16.png)

And if for any node， if you are getting the cost greater than some upper bound。

 then we will kill that node。

![](img/ba5dbf1743e53021749806a7ad65c1b8_18.png)

So we will try to produce or generate only those nodes which are fruitful。

 we will not generate all the nodes， we will try to follow the path which is taking us nearer to the minimize or maximize optimize solution note。



![](img/ba5dbf1743e53021749806a7ad65c1b8_20.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_21.png)

So that's how branch bound is different from backtracking。Now。

 let me solve this problem using branchn and Bo。

![](img/ba5dbf1743e53021749806a7ad65c1b8_23.png)

So the problem is solved by just using mattresses， let us start and see what we have to do first。



![](img/ba5dbf1743e53021749806a7ad65c1b8_25.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_26.png)

The very first thing what we have to do is take the given matrix that is cause a matrix for a given graph。

I have taken it here。 Red this matrix。 What does it mean by reducing a matrix， C。

What all the minimum values in a row write down them here。 So the minimum values are 10。



![](img/ba5dbf1743e53021749806a7ad65c1b8_28.png)

And the minimum value in this row is a 2。Minimum is the two here。 Minimum is a3。



![](img/ba5dbf1743e53021749806a7ad65c1b8_30.png)

And。Fearful。Now subtract that minimum values from all the rows， all the elements of a row。

 So reduce row。 So by that all the rows will be reduced。 Okay， so for reducing row。

 sub the minimum value。 I'll sub this 10 from all。 So 20 minus10， this becomes 10。

30 minus 10 becomes 20 and this becomes0 and this is 1。Subtract2 from all， this is 13。And this is 14。

Do。And this is 0。 Subtract 2 from all。 So this is 3-2 is 1， and this is 3。0。Do。Likewise。

 do it for these Also， I have reduced all the rows and the total cost of reduction of all the roses add all these。

 this is 21。

![](img/ba5dbf1743e53021749806a7ad65c1b8_32.png)

Rs are reduced。Now， reduce columns。 write the minimum value below each column。

 See the minimum value in this column is 1， and the minimum value in this column is 0。

 Minim value in this column is 3。Minimum value is 0。 Minimum value is 0。

 There are two values which are not 0。 So we should reduce this column with this value。

 So subtract one from all the elements in a column。 So this becomes。15， and this is one。

 and3 subtracts from all。 So this is 17 and 11。12 and 0。 So how much this is， If I add all these。

 this is  one plus 3，4 plus 21。 So 21 plus 4 is 25。



![](img/ba5dbf1743e53021749806a7ad65c1b8_34.png)

So this a reduce matrix。 reduce matrix is one in which every row and column is reduced。

 When you say a row column is reduced， it is having at least one element as0。

 So when zeros were not there so we have subtracted and made it 0。

 So this are reduce one and the cost of reduction is 25。

 So what does it mean What we have done actually we have found out the shortest distances from the matrix and we have subtracted and we have taken this 25。

 So the minimum cost of two maybe 25。

![](img/ba5dbf1743e53021749806a7ad65c1b8_36.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_37.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_38.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_39.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_40.png)

It is minimum 25。 It may be more than 25 Also。 So at least the cost of two will be 25。 Now。

 I have to continue solving the problem。 So for that， I will draw this reduced matrix here。



![](img/ba5dbf1743e53021749806a7ad65c1b8_42.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_43.png)

And I will use it so I have removed the original matrix and I have taken only a reduced matrix because that is the matrix we need now and the cost of reduction is 25 Now let us see how to solve it using branch and bound by with the help of a state page3 So first thing I will draw a states spacee3 So for this I will say I am starting from vertex 1 then what are the possible vertexes I can visit I can visit 2。

3，4，5 so I can visit2 or three。

![](img/ba5dbf1743e53021749806a7ad65c1b8_45.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_46.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_47.png)

Or four。Or5。For every vertex， we have to find out the cost。



![](img/ba5dbf1743e53021749806a7ad65c1b8_49.png)

How to find the cost I will show you for one matrix and the same thing will be followed for all the mattresses。

And what is the cost for the fast matrixs that is reduced cost。

 So the cost of the first matrix is 25。

![](img/ba5dbf1743e53021749806a7ad65c1b8_51.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_52.png)

And if you remember from zero naack problem that we are also maintaining an upper bound， so yes。

 we will maintain one upper， so upper will be initially infinity。



![](img/ba5dbf1743e53021749806a7ad65c1b8_54.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_55.png)

If you know about zero1 napsack problem， therefore every node we will find out the cost as well as the upper bound。

 but here we don't have upper bound， just we will have a cost。

So just we will take the cost and once we reach any leaf node， then we will update upper。

 we will not update or check for every node。

![](img/ba5dbf1743e53021749806a7ad65c1b8_57.png)

So I repeat it once again， we have to generate a state pasttry and for every node we have to find out the cost the cost of first node is 25 and we will have one value called upper that is infinity。

 this will not update every time this will update only once you have reached the leaf node so well be finding only cost I will show you how to find the cost for the first node so for that already I have taken that same reduced matrix here now let us see how to find the cost of this second node cost of this node see this node means that we are going from vertex 1 to2 so this is from one to2 right so one to two minutes what we have to do in this one is。



![](img/ba5dbf1743e53021749806a7ad65c1b8_59.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_60.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_61.png)

Make the first row and second column all values as infinity。



![](img/ba5dbf1743e53021749806a7ad65c1b8_63.png)

First row and second column has all infinity。 so first row is infinity。

And column second column as infinity。So first row and second column is made as infinity。

 then once we are coming from 1 to vertex 2 we should not go back to vertex 1 again。

 so2 to1 is also made as infinity。

![](img/ba5dbf1743e53021749806a7ad65c1b8_65.png)

After making first row and second column as infinity。

 check if the matrix is reduced or not so let us check for the row。 this is having10。

 This is also having0。 this row is also having 0 this row is also having0 yes。

 no problem then column is having0 this column youll leave it all are infinity only this column yes it' is having0。

0 is there zero is there so better you write on here。

 whatever the meaning value is here if you write on you'll come to know whether all are reduced or not so here all are reduced。

Then what is the cost So the cost is the cost of an edge from c of1 to1 to 2 plus the cost of that reduction and if any more reduction if you have done So cost of an edge1 to2 actually a made it as infinity here you can look at here that is one to 2 is it 10 So this is a 10 and the cost of that reduction actually it was 25。

 so this is reduced matrix from the original one so that 25 is already there then how much you have reduced this one nothing so it is total is 35。

 So cost of this is 35 So we have to consider three things。

 the cost of an edge from 1 to 2 and the actual reduced cost plus if there any reduction there is no reduction it is0 Now similarly we have to find out the cost for other vertices also that is from one to 3 and 1 to 4 and 1 to 5 I will find out those cost next for a cost。



![](img/ba5dbf1743e53021749806a7ad65c1b8_67.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_68.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_69.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_70.png)

Of third matrix， again， I have taken a reduced matrix here。 This is for finding for the third。

Vex that is from  one to 3。 So first of all， make first row as infinity。Third column as infinity。

First row and third column as made as infinity now we should not have any path going back from3 to1。

 so make3 to one also as infinity。

![](img/ba5dbf1743e53021749806a7ad65c1b8_72.png)

Next， check whether the matrix is reduced or not， if not， then reduce it。Check this row。

 It is having0。 This is having 0。 This is having0。 This is also having0。 The column。

 this is not having 0。 Then what is the minimum value 11。Then what is the minimum value here，0。

 minimum value。 This is infinity， So let it be 0 only， and the minimum value is 0。

 Min value is 0 here。 So this is not reduced。 So reduce this one。 So subtract 11。 So this will be。

For。4。And this will be one。 So now we have the reduced matrix。

 Then what is the cost of this vertex Now， the cost of this vertex is cost of an edge from 1 to 3 because we are going from1 to 3 plus cost of reduced matrix plus the cost of reduction of this matrix。

 So 1 to 3 is how much actually we have taken from here。 So 1 to 3 is 17。

 So this is 17 plus the cost of original matrix is 25， and the cost of this reduction is 11。

 So this is。

![](img/ba5dbf1743e53021749806a7ad65c1b8_74.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_75.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_76.png)

30，30，40，53。 So the cost of this vertex is 53。 So this is how we find the cost of each vertex。

 So I have finished with from vertex 1 to 2， then 1 to 3，1 to 4，1 to 5。 I will directly finish it。

 Hope you have understood how we get it， but I will draw those two mates here。

 right and I will directly write the answer for them then what happens after this。

 how we moved to the next level I will show you now。

 So here I have already prepared for fourth vertex and the fifth vertex。

 this is for second and third already I have shown you similarly I have committed for fourth and fifth vertex。



![](img/ba5dbf1743e53021749806a7ad65c1b8_78.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_79.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_80.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_81.png)

And the cost we got is 25 and the cost of that one is 35。



![](img/ba5dbf1743e53021749806a7ad65c1b8_83.png)

Now we have to see what we should explore next。😡。

![](img/ba5dbf1743e53021749806a7ad65c1b8_85.png)

See， how many nodes are there。 So 2，3，4，5 total 4， what is that we have four nodes are there。

 I can expand this one， then this one， then this one and this one。 So first， I can expand this。

Now listen carefully。If I am exploring the next children of a node for this one。Then this one。

 then this one， then this one。 Then I'm following Fi four branch and bond， but。

If you see the cost of all these， this is having minimum cost then I should explore the children of only four then afterward I should see which one I should select So if I am selecting this one and exploring its children because of this least cost then this is least cost branch and bound LC branch bound。

 this is the difference Now let us explore the children of vertex 4 see this vertices are actually representing a root from one vertex 1 to vertex 2。

 then this from vertex 1 to vertex 3， vertex 1 to4， vertex 1 to 5。



![](img/ba5dbf1743e53021749806a7ad65c1b8_87.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_88.png)

exFrom vertex 4， I can go to vertex 2。And3。And vertex 5 Now the node numbers 2，3，4。

5 I have to console lets write the mass 6，7 and 8。Now I have to find the cost of these three nodes that is 67。

8 so that is representing the path from 4 to 24 to 3 and 4 to5。

 so which matrix I should use I should use this matrix and get the cost of these three nodes。



![](img/ba5dbf1743e53021749806a7ad65c1b8_90.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_91.png)

So let me show you how to do this。

![](img/ba5dbf1743e53021749806a7ad65c1b8_93.png)

I have taken this matrix。 that is the matrix that belong to node 4。 I have taken here。

 and I am going to find the cause for node 6。 Was this carefully the same thing has to be done for node 7 and node 8 that is verex 3 and verex 5。

 Also I am showing only one。😊。

![](img/ba5dbf1743e53021749806a7ad65c1b8_95.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_96.png)

Person。This is for4 to 2， verex 4 to 2 verex of a graph4 to 2， this is no numbers。

 but this is from vertex 4 to verex 2， so4 to two means4 through make it as infinity。

 so4 through is infinity and second column as infinity。



![](img/ba5dbf1743e53021749806a7ad65c1b8_98.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_99.png)

See till here， if you see the path from one to4，4 to2， we should not go back to one from2。

 so2 to1 also infinity， this is also infinity。

![](img/ba5dbf1743e53021749806a7ad65c1b8_101.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_102.png)

That's it。 So most of the values are infinity only here。Now， let us see whether it is reduced or not。

 This is infinity。 leave it in this0 is there。 and this 0 is there。 This is infinity leave it。

 This is 0 is there。 Then column minimum value is 0。 This is infinity column minimum value 0。

 this infinity column minimum value is 0。 So all are 0。 So this is already reduced。

 So I don't have to do anything。 Then no reduction cost。 So then what is the cost。 So first of all。

 cost of an edge from 4 to 24 to 2。

![](img/ba5dbf1743e53021749806a7ad65c1b8_104.png)

Plus， cost of4， vertex 4， cost of4。

![](img/ba5dbf1743e53021749806a7ad65c1b8_106.png)

Plus， cost of reduction。See that while that time we were taking the main cost of reduction。

 actually that was the cost of vertex 1。

![](img/ba5dbf1743e53021749806a7ad65c1b8_108.png)

Now cost of4 to2 is how much from this matrix 4 to 2 as it 3， so this is 3 plus cost of vertex 4。

 what was the cost 25？

![](img/ba5dbf1743e53021749806a7ad65c1b8_110.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_111.png)

25 only plus what is the cost of reduction， Nothing， So this is 28。 So this cost is 28。



![](img/ba5dbf1743e53021749806a7ad65c1b8_113.png)

Now I have to do the same thing for node 7 and node 8 directly I will write down there mattresses and I will find out their cost。

 Here is the cost of node 7 and node 8 and these are the two mattresses for node 7 and 8。C。

 I have the cost of all nodes。 Now which node is minimum as per the least cost branch and bond。

 we have to select the least cost one minimum one。 so which one is minimum。😡，35，53，31，28，50，36。

 This is minimum。 So I should explore that node。 I should explore  6。



![](img/ba5dbf1743e53021749806a7ad65c1b8_115.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_116.png)

Then if you see the path we have came from vertex 1 to4 then 4 to 2 what are remaining now3 and 5 are remaining so I will expand this so the first one will be3 so this is for3 and one more is5 so three I will write on the node number as9 and 10。



![](img/ba5dbf1743e53021749806a7ad65c1b8_118.png)

![](img/ba5dbf1743e53021749806a7ad65c1b8_119.png)

So I have to prepare a matrix for node 9 and node 10 now for9。😡。

This matrix already I have taken this is coming from vertex 6 sorry。Noode 6。

 So I have taken the matrix of node 6 and I have cop it is as it is。

 Now let us see what are the things I have to do。 see we are going from vertex 2 to vertex 3。

 So second row and third column， I should make it as infinity。

 Second row is infinity and third column is infinity， this is also infinity。

 After making second row and third column infinity3 to1 also I should make it as infinity。

 So this is three to1 is also infinity。 Now check whether it is reduced or not。

 see there is only one row here， which is having value2。

 So subtract this one it is not reduce then this row， it is having level only。 So subtract this。

 So this level is subtracted from the row。 So two rows are reduced。 Now column wise if you see yes。

 rest of the values are infinity。 So if you see the number， this is0 this is0。

 So it is reduce matrix is reduced。 Then what is the cost cost of an edge from 2 to 3。 So 2 to3。

 then cost。😊。

![](img/ba5dbf1743e53021749806a7ad65c1b8_121.png)

Of its parent that is node 6 cost of node 6。Then plus 13。 So this 11 plus 2 is 13。

 Then cost of2 to 3 here，2 to three is 11，11 plus cost of disappear was how much 28。

28 plus 13 this is 52。 so the cost of node 9 is 52 same way we have to find out the cost of node 10 also I will draw this one so here I have the market for node 10 this is a 10 and the cost is 28。



![](img/ba5dbf1743e53021749806a7ad65c1b8_123.png)

See， this is for vertex 5 and the node number I have taken 10 here， so the cost is 28。



![](img/ba5dbf1743e53021749806a7ad65c1b8_125.png)

Now， which one I should select for exploration if you look at all the vertices and their cost。35，53。

31。50，36。52 and 28。 So the least one is 28。 That is vertex。5 and a node number 10。

So I should explore this one。😡，So what are the possible nodes that I can visit this is coming from one to4 from43 where possible so we selected two from two2 where possible from5 the last one remaining as vertex3 only so the node number 11 I will take so I have to find out the cost for this one so the cost of this node will come from this node so what is the matrix for this one here I have the matrix for that one。



![](img/ba5dbf1743e53021749806a7ad65c1b8_127.png)

If I find out the cost for this node number 11， then what I have to do。😡。

Fifth row third column infinity， fifth row infinity， third column infinity。

 then everything becomes infinity only， and the cost for that one will also be。



![](img/ba5dbf1743e53021749806a7ad65c1b8_129.png)

28。 So finally， we have the leaf 1。 that is from 1 to 4，4 to 2，2 to 5，5 to 3。 Now。

 nothing is remaining3 to1。 only we have to go back。

 So we have visited all the vertices of a graph and well be returning back to vertex 1。

 So the minimum cost we got is 28。😊，Then what to do next。See。

 as we have reached the leaf update upper to 28。 Once the upper is updated here， check the node。

 whose cost is greater than upper。 So all of them cost is greater than upper。

 So every node will get killed。 We don't have to explode them at all。 So every node will get killed。

 whose cost is greater than 28。 So which code node is remaining now。

 this node is remaining and that is leaf node。 So this is the answer。So the cost of a tour is 28。

 and the tour is from 1 to 4，4 to。2，2，2，5 and 5，2，3。 So1，2，4，4，2，2，2，2，5， and 5，2， 3， then 3，2，1。

 This is the shortest distance to minimum cost to。That's solved with the traveling salesperson problem using branch and time。

