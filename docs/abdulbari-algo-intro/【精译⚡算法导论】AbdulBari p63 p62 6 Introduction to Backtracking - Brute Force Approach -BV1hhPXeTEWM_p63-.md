# 【精译⚡算法导论】AbdulBari p63 p62 6 Introduction to Backtracking - Brute Force Approach -BV1hhPXeTEWM_p63-

Hi， the topic is bike tracking。 This is one of the problem solving strategy。Using this approach。

 we can solve problem or we can write our algorithm by following this strategy。

This strategy uses brute force approach。And brute force approachse says that for any given problem。

 you should try out all possible solutions and pick up desired solutions。

This we were already following in dynamic programming。

 but in dynamic programming we were solving optimization problems。

Backtracking is not for optimization problem。 Backtracking is used when you have multiple solutions and you want all those solutions。

So for explaining backtracking and how it follows brute force approach。

 I'll take a simple example and explain the strategy。So let us take an example。



![](img/22e7cb1c27f40cc40adc230502c9664d_1.png)

If there are three students， two boys， and a girl。And there are three shades。



![](img/22e7cb1c27f40cc40adc230502c9664d_3.png)

We have to arrange them in those three chairs in how many ways we can arrange。



![](img/22e7cb1c27f40cc40adc230502c9664d_5.png)

![](img/22e7cb1c27f40cc40adc230502c9664d_6.png)

There are three number of students are three， so we can arrange them in three factorial ways。

 That is six ways。

![](img/22e7cb1c27f40cc40adc230502c9664d_8.png)

Now we want to find out all possible arrangements。So for finding all possible arrangements we can solve the problem and the solution can be represented in the form of a tree that is solution tree and we also call it as state space tree。

 so we will represent the solution in the form of state space。3。

Let us generate a treeN solve this problem。So let us start。 This is the starting of a solution。Now。

 let us take all possibilities。 So first， who can set first chair， Boy，1 will set。 So this。

A is showing first boy。 So in the first level， we will consider each one of the students。

 So let us say boy  one is sitting there。 Now， next， next level for next chair that is next seat。

 who can sit there。 Boy， too。 So boy， too can sit here。



![](img/22e7cb1c27f40cc40adc230502c9664d_10.png)

![](img/22e7cb1c27f40cc40adc230502c9664d_11.png)

The next is girl 1。

![](img/22e7cb1c27f40cc40adc230502c9664d_13.png)

The third level for third seat。 So girl one can sit。 So we have finished with the input。



![](img/22e7cb1c27f40cc40adc230502c9664d_15.png)

Now， for another arrangement， take out girl from here。So take out， go back here。

 Any other possibility。 No， take out boy 2 also， So take out boy 2。 And in the second place。

 who can sit there， girl can sit there。 So girl  one can sit there。 Then at that place next。

 boy 2 can sit there。

![](img/22e7cb1c27f40cc40adc230502c9664d_17.png)

![](img/22e7cb1c27f40cc40adc230502c9664d_18.png)

Boy，2 can set。Right， so this one more solution we got。 take out boy2， take out girl1。



![](img/22e7cb1c27f40cc40adc230502c9664d_20.png)

Any other possibility no， so pick out boy one also Now next is boy， too can sit in first place。



![](img/22e7cb1c27f40cc40adc230502c9664d_22.png)

Then who can sit here， Boy，1， boy，1， then girl，1， girl 1。Then take out girl 1， Take out boy 1， girl。

1 and boy1。 right the next。Girl  one sitting here。 then boy 1， boy 2。 and here， boy 1。

 boy2 and boy 1。

![](img/22e7cb1c27f40cc40adc230502c9664d_24.png)

So these are the possible arrangements。 So 1，2，3，4，5，6。 So from the route。

 if I follow one of the path， I get one of the solution， I wanted all six possibilities。

 and I have all possibilities。 If I take this route， this says that first share， boy2 will sit。

 then boy 1， then girl。So I have founded all possible solutions。

 the problems that we solve using backtracking， those problems usually will have some constraints。

And we will try to check those constraints and get the solutions which are satisfying those constraints。

 Now I will impose one constrain here I'll say that girl should not sit in middle。



![](img/22e7cb1c27f40cc40adc230502c9664d_26.png)

Girl should not still sit in middle。 This is the constraint。 So girl should not come in between。

 Then what are the possible solutions。 So let us check。 So again， I will just trace and draw3。

 So first boy，1。 Okay， correct。 Then boy2。 That is nearer to boy 1。 Then that is that second place。

 then third place girl 1。 Yes， correct， answer。 go back next possibility。 Second place， girl。 No。

 not allowed。 So no need to go further。 stop here only。



![](img/22e7cb1c27f40cc40adc230502c9664d_28.png)

Right constrain is imposed and we are not generating the tree further from here and we are killing this node we are not going further because what is the condition girl should not be in the middle so in the second level girl should not come so we got girl here in this combination so we stop here and we say this node is killed and how this node is killed we say we are imposing a condition and that we call it as bounding function。

That condition is called as bonding function。 So we applied bonding function and kill the node。

 So this is how we are trying to get a proper solution。

 as well as we are trying to save our work also。Now， go back。 Boy， who is sitting here。 Boy 1， Okay。

 Second level， Second chair。 boys there。 no problem。 Then girl。 Yes， this is also a solution。

 This is also a solution， right， So second solution。 Then go back， girl。

 girl is again coming in between。 That is second chair。 So kill this one。 Ki the noded。



![](img/22e7cb1c27f40cc40adc230502c9664d_30.png)

Right， by applying bonding function， go back， girl， no boy， then boy， No problem here。

 No problem here。 Then this is also a solution。 This is also a solution。 No bonding function。

 If no bonding function is applied until you reach at the last level， then you got a solution。

 So total  four solutions we got。

![](img/22e7cb1c27f40cc40adc230502c9664d_32.png)

![](img/22e7cb1c27f40cc40adc230502c9664d_33.png)

![](img/22e7cb1c27f40cc40adc230502c9664d_34.png)

There are a few problems that comes into backtracking like N queen's problem and some of the subset problem graph coloring problem。

 right I will show those problems。Yeah， one more thing。

 the same approach that is brute force approach is used by one more strategy called as branch and bound。



![](img/22e7cb1c27f40cc40adc230502c9664d_36.png)

![](img/22e7cb1c27f40cc40adc230502c9664d_37.png)

Branrunch。And。

![](img/22e7cb1c27f40cc40adc230502c9664d_39.png)

Bound。This is one more strategy。Let me show you the difference between backtracking and branch and bound now itself。

See， both follows root force approach and both generates stay pasttry。

 But the approach is a difference。 What is that in backtracking。

 the way we were generating the nodes where first this one， then this one， then this one。

 then this one go back and come to this site。 Go back。 So this is DFS we were following。

 So backtracking follows defer search。

![](img/22e7cb1c27f40cc40adc230502c9664d_41.png)

Whereas branch and bound will follow breath surge。

![](img/22e7cb1c27f40cc40adc230502c9664d_43.png)

I will show in branch and bound how we generate the tree。First， this one， then boy 1， boy 2。



![](img/22e7cb1c27f40cc40adc230502c9664d_45.png)

Gir 1， see， we generate all the nodes in the level。 This is birth for search。

 So we are exploring a problem to find a solution breath wise， right， So then here who can sit。

 Boy 1 already has taken a seat。 So boy 2 or girl1 can take the seat。

 So this is boy 1 or girl 1 can take a seat。 This is boy 1 and boy2。😊。



![](img/22e7cb1c27f40cc40adc230502c9664d_47.png)

![](img/22e7cb1c27f40cc40adc230502c9664d_48.png)

安平液。

![](img/22e7cb1c27f40cc40adc230502c9664d_50.png)

Girl 1 will take a seat。 Boy，2 will take a seat。 Girl，1， and boy1。Boy to。



![](img/22e7cb1c27f40cc40adc230502c9664d_52.png)

bo one。So in branch and bound it is generated level wise level wise。

 so only the difference how the trees generated I have shown。

 I did not discuss branch and bound this we will discuss in some other video。It's a different thing。

 but the common thing I have shown you， so this follows defer search that follows breakfast search so in the next videos I will cover the problems related to backracking。



![](img/22e7cb1c27f40cc40adc230502c9664d_54.png)