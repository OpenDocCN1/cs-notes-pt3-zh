# 【精译⚡算法导论】AbdulBari p58 p57 4.7 -New- Traveling Salesman Problem - Dynamic Programming using Formula -BV1hhPXeTEWM_p58-

Hi the topic is traveling salesperson problem already I have one video on this problem already I have taken the same example and I have solved it。

 but now I am going to explain you in a different way by using the forum line each and every step。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_1.png)

So let us see about the problem quickly I will tell you see the problem is a directed weighted graph is given。

 so it means every edges having some weight see these are actually parallel edges， two edges。

122 also221 also。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_3.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_4.png)

But to show two edge， I have shown them as only one edge。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_6.png)

By directionional。 now， every edge is having weight。

 So this the cost adjac matrix for this directed graph。 Now， the problem is。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_8.png)

We have to start from some vertex and travel all the other vertices。

Once and we have to return back to the same starting vertex。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_10.png)

So start from any vertex and go through all the vertices once and return back to the starting vertex。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_12.png)

And the cost of traveling must be minimum。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_14.png)

This is the traveling salesperson problem。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_16.png)

For solving that。This is a formula given， this is a dynamic programming formula。

This is the general form of a formula。 Now， I will write on this formula。

 according to these four vertices graph。 Then I will discuss about it。

 The cost function is termed as G here。And our starting vertex is 1。

 and we have to visit remaining vertices， those are two，3 and4。And。Minimum of。What is this Let usacy。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_18.png)

See from any starting vert X i， I can go to any of the K vertices that belong to this set。

 it means from starting vert X 1， I can go to2 also， 3 also4 also。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_20.png)

So here C of12 k， what k can be， K can be anything from2，3 and4。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_22.png)

Plus。G of starting vertex K and from 2，3，4， subtract K。This is a general formula。

 but we have written a formula with respect to four vertices。

 The formula says that starting vertex is1， and you have to visit remaining vertices in any order you want。

 So you can go from 1 to 2， Also 1 to 3， Also 1 to 4。 Also。

 so that all possibilities we are trying here。 We will be going from 1 to 2 or 1 to 3，1 to 4。

 anything out of that， we have to take the minimum So whichever one we are going that vertex。

 we should subtract from the set of vertices。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_24.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_25.png)

See if you observe this the formula is recursive， its a recursive formula cost of a root is defined in terms of cost of a root again。

Here， the set of ver is to be visited at 2，3，4， and here it is one less。This is recursive formula。

 how we can find the result of any recursive function。 We generated recursive tree。

 So let us generate a recursive tree for this one。 See here I can go from 1 to 2。

 So the starting vertex is 1。 So if I go to vertex 2。 then as per the formula C of 1 k。

 What is the K we are considering2。 So C of 1，2 plus G of。2 to remaining。 So 2，2， C， K， K here。

 So remaining， remaining what K is2 here。 So two is removed。 So remaining will be 3 and 4。

 So this is 3 and  4。See again， we got a cast function next。I can go on vertex 3 Also。 So 1 to 3。

 if I go from 1 to 3。 So this is cost of an h from 1 to 3 plus cost of 3 to remaining。 So G of32。

 what is remaining 2 and 4。 So this is 2 and 4。And one more。I can go from one to 4 also。

 So this is for cost of an H from one to 4 from。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_27.png)

G of 4，2， remaining Portads 2 and 3。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_29.png)

See， this is just like I have substituted three different values of k What are those2 and 3 and 4。

2 and3 and 4 I have substituted so I get three different formulas now out of three different formulas。

 all these three I have to take the minimum so this expansion I have done here I have written them separately I am showing them in the form of a tree out of these three I have to take minimum this minimum。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_31.png)

Can I know minimum， I don't know this。 I don't know this。And this， I don't know the cost of this。

 So unless I know the cost of these functions， I cannot get the answer， and I cannot find minimum。

 So how to find out this one again， the same formula applies。 the same formula。 Now， here。

 the starting point is 2。 and here， the starting point is 3， and the starting point is 4。 So again。

 use the formula expand them。 But before going further， I can show you one thing。

 cost of an C of 1 to 2，1 to 3，1， to 4。 I can get it here they are given1 to 2，1 to 3，1 to 4。

 there is 10，15 and 20。 So I will write on1 to 2 is how much 10。 Okay， this value will be remaining。

 I have to find out this one。 This is how much 15。 This is remaining。 I have to find out this。

 This is 20。 This is remaining。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_33.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_34.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_35.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_36.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_37.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_38.png)

Now， let us expand these formulas and get the answer and add it to this one。

 then out of this take minimum。 So first， let us expand this。 Now， from here。

 what is the possibility starting vertex is 2。 I can go to 3 or 4， I can go to vertex 3。

 If I am going to vertex 3， This is from 2 to 3。 So cost of an H 2 to 3 plus G of3 to4。

 remaining vertex well before4， C 2 to 3。And then remaining is 4。 So 3，4 were there。

 So now three came out。 Only four is remaining R else from2， I can go to 3 also2， I can go to 4 also。

 So if I go on4， then C of2 to 4 plus G of4， then if I am going on 4， what will be remaining。

3 will be remaining。Now， in the same way， I will expand these formulas。 Also3 to 2， I can go。

 So C of3，2 plus G of。Do do4。Or。3 to 4 I can go。 So this is4。

 So c of3 comma4 plus g of 4 to remaining verex is 2。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_40.png)

Then here also， I will expand。 So this is， I can go from 4 to2 also and 3 also。

 So if I am going 4 to 2， this is C or 4 to 2。Plus G of 2 to remaining vertex will be 3 plus C of4 to 3。

 then G of 3 to remaining vertex will be 2。 Now， total 6 formulas we have now。

 I can fill up these C values， the cost of an H， so I will write on the values， see C of 2，3，2，4。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_42.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_43.png)

2，3 is 9，2，4 is 10。 So this becomes。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_45.png)

9， and this becomes 10。Then 3，2，3，4，3，2 is 13，3，4 is 12。 so this is 13， and this is 12。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_47.png)

Then， C 4，2 S。8。And 4，3 is 9。 This is 8。And this is 9，4，2 is 8，4，3 is 9。 Still。

 we don't know the value of these function。 So let us use the formula and expand them。

 If you observe here， this says that starting vertex is 3。

 and the remaining vertex that we have to visit it only 4。 So I'll go to vertex 4。

 So this will be from 3 to 4。 So C of 3，4 plus G of 42 remaining is nothing。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_49.png)

When 4 is also gone， we have visited4 all。 So then nothing is remaining。

 So same way here remaining is 3。 So say C of 4 to 3 plus G of 32， nothing to 3 plus G of 3，2。

 Nothing is remaining that this is 3 to 2。 So C of 3，2 plus G of2，2， nothing is remaining。

 So now it can realize。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_51.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_52.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_53.png)

If we are solving it， using a recursive tree， then the tree will expand like this。

 No doubt it will not execute like this。 The order of execution will be different。

 but the complete tree looks like this。 Now， these cost of edges I can write down here。 C of 3，4。

 C of 3，4 is how much3，4 is 12。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_55.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_56.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_57.png)

So let us take that to2。Plus， suanso function is there。 Then C of four trains，9。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_59.png)

C of 2，4，10。C of 4，2 is 8。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_61.png)

C of 2，3 as 9。C of 3，2 S 13。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_63.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_64.png)

Now， remaining still functions are there。 So I'll show here， see cost of a route from 2 to nothing。

 So you are on vertex 2 and no other vertex we have to visit， because if you see from this one。

 from 1 to 4。 we have gone from 4 to 3。 Then 3 to 2， and as per traveling salesperson problem。

 you must go back to the starting vertex again。 So from 2， we have to go back to vertex 1 again。

 So for 2 to nothing means we have to go back to vertex 1。 So 2 to 1 is how much 5。

 So we can replace this at 5。 So let us start from here。4 to nothing means 4 to 1，4 to 1 is how much。

 See you can see this column 4 to 1 is 8，3 to 1 is 6。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_66.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_67.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_68.png)

2 to1 is 5。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_70.png)

So here I have 4 to nothing，4 to 1，4 to 1 is how much 8， and 3 to nothing，3 to 1 is how much 6。

F to nothing， so。4 to1 is 8。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_72.png)

2， to，1， S 5。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_74.png)

3 to 1 is。6。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_76.png)

And 2，2，1， S 5。So the last level， we have the values now， just you look at the three ones。

 I am going to substitute the values and get back to the final answer。

Just you have a look at a tree one。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_78.png)

The tree has expanded so much。 If you try to use recursive tree， then this is how it will expand。

 So to avoid this， we don't follow this method for solving and getting the answer， but。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_80.png)

We will make it as a table， and we get the values for these last level first， then the upper level。

 then above level， then automatically we get the answer。

 So I will show you how actually this is solved。 This not the way I am just explaining this one。

 I was just explaining this。 Now， let us see what is the way of solving this。 I'll remove this one。

 Here I will write down。 So actually， we will find out the last level values。 What are those。😊。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_82.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_83.png)

G of。 We are on the second vertex is nothing is remaining。 G of。 We are on the third vertex。

 and nothing is remaining。 G of。 we are on fourth vertex。 Nothing is remaining。

 So we need to answer 2 to nothing，2 to nothing is how much5。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_85.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_86.png)

And 3 to nothing S 6。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_88.png)

4 to nothing， S 8。See， this is like a table will generate actually dynamic programming programming means tableular values。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_90.png)

It's not software。 It's not computer programming。 programming means table or values。

 dynamic programming， dynamically generated table。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_92.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_93.png)

Actually， we should solve it like a recursion， but we don't solve it like this we'll prepare a table。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_95.png)

W what values you find out， We find out the smaller values first。 Then we can know that this value。

 See， unless I know this value， I cannot get the answer for this。 That's why we follow these。 Now。

 in the next level， you will find out these values。 See what are these 3 to 4，4 to 3，2 to 4，4 to 2。

2 to 3，3 to 2。 So we need these values。 We are on vertex 2， and 3 is remaining。 We are on vertex 2。

 and 4 is remaining。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_97.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_98.png)

We are on vertex 3 and vertex 2 is remaining。 We are on vertex 3 and vertex 4 is remaining。

And we are on verex 4。2 is remaining to be visited。 vertex 4，3 is remaining to be visited。

 See here nothing remaining， So 2，5，3，5，4，5。 Now one vertex remaining。 So if you are on two。

 there are two possibilities，3 may be remaining or four may be remaining。

 So this way we have taken these functions and that are actually representing this second last level you see4。

2，2，3，3，2， all these are representing them。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_100.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_101.png)

Now， let us see what are these values。 See， this is 3，4，3， we are on  three and remaining is 4。

 so this is 20。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_103.png)

So three， here on3， remaining 4 is 20。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_105.png)

So we know this value now。 I will change it with 20。We are on four remaining what is3。 So this is 15。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_107.png)

We are on four remaining what is 3。 This is 15。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_109.png)

So I'll change this value to 15。I know the answer now。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_111.png)

We are on verex2 remaining value is 4。 so this is 18。2 and 4。 This is 18。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_113.png)

I'll replace this with 18。 We know the answer now here。We are on four remaining is 2。 It is 13。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_115.png)

We are on four。 remaining is 2 is 13。So we know this answer，13。We are on two remaining is three。

 We are on2 remaining is three is how much 15。 So this is 15。15。We are on three and remaining is 2。

 So this is 18。 So two remaining， we are on 3 and remaining is 2 is 18。 So this is。18。Now。

 I will show you from the table。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_117.png)

We were on one vertex and remaining only one vertex was remaining。 Now。

 if we say two vertices are remaining， what are the possibilities we are on vertex 2 and 3。

4 are remaining。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_119.png)

Or we are on vertex 3， and 2，4 are remaining。We are on verex 4， and 2，3 are remaining。

These are the possibilities， see。These three sets are representing this one。We are on 2，3。

4 remaining，3，2，4 remaining，4，2，3 remaining。How to get these values， minimumimum of these two。

 What is minimum 29 and 25。 So this is 25。35。So this is 25。We don't need this now。

 I will remove this。Now， this is 31 and 25，3，2，4 are remaining is 25。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_121.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_122.png)

25。 So remove this。 I'll write 25 here。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_124.png)

Now here answer for this also， four remaining is2，3， this one。Out of this， which is minimum。

 This is 23， and this is 27。 So 23 is minimum。 So 23 is minimum。 Now， remove this。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_126.png)

I'm right 23。Now， out of these， we can find out minimum that will be the answer for this。

 so that is finally G of1 and2，3，4，3 vertic is are remaining。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_128.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_129.png)

Out of this switch is minimum。 This is 35。And this is 40。And this is 43 out of this minimum is 35。

 So answer is 35。 So answer for this one is 35。

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_131.png)

![](img/2829678f34a2ebe97a4ddfe93bfd10ba_132.png)

So the shortest route for traveling salesperson problem is 35。 so that's it。



![](img/2829678f34a2ebe97a4ddfe93bfd10ba_134.png)