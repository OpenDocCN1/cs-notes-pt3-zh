# 【精译⚡算法导论】AbdulBari p64 p63 6.1 N Queens Problem using Backtracking -BV1hhPXeTEWM_p64-

The problem is in queen's problem。First， let us understand， what does it mean by in's problem。

 Then I'll explain you how back trackinging is used for solving this problem。See here。

 a chess board is given。Of four cross 4，16 cells， a standard chboard will be of 8 cross 8。

 but for reducing the size of a problem， we have taken four by 4。And four queens are given。

 So in a game of chess， a queen will be there， which will have its moves like horizontal that is in a row or in a column or diagonal it moves。

 So here also， it's the same queen。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_1.png)

And that queen we have to place them on this board。

 So all four queens we have to place such that no two queens are under attack So when do you say they are under attack if they are in same row or same column or they are in same diagonal。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_3.png)

So if they are in same row， same column or same dial。

So we have to avoid this and arrange them such that they are not under attack。

So is it possible to arrange them， Yes， it is possible。 We get some solutions。

Is there only one solution no for this， we will have more than one solution and we want all those solutions。

So now we want to know what all their possible arrangements from there。

 we want those arrangements which are satisfying this condition。

So for this type of problem backtracking is used， we want all possible solutions which are satisfying this condition。

 not just one solution， if we are looking for optimal then we should go for dynamic programming。

 we want all solutions which are satisfying this condition， so backtracking is used。Now。

 let us discuss how to solve this one。 Those four queens， I'll place them on this4 by4 chessboard。

 So in how many ways I can place them on this 16 cells so I can place them in 16 C4 ways。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_5.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_6.png)

So this will form a lot of possibilities， and the problem becomes big。No。

 to reduce the size what we will say that a queen cannot be kept anywhere on the board。

 but first queen in Fast row， second queen in second row likewise。

 so it means now what we have to decide we don't have to decide the cell we have to decide in which column or Q will be placed so those columns will write here first queen which column it will be then second queen third queen and fourth queen so itll write on their column numbers。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_8.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_9.png)

So now the problem is reduce。 And one more thing we'll do。

We will try to avoid keeping two queens in the same color。Okay， actually。

 we have to check this condition。 So one we condition we already solve what we will not keep all the queens in a single row。

 every queen in an x row。 So first row is problem is solved。 Then we know we are placing them。

 We have to solve it。 So for that， we will try to avoid keeping two queens in the same color。

 So these two are directly， we are taking care。 Now we have to check other queens in the same diagonal or not。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_11.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_12.png)

Right so now by checking all these conditions， what we will do is we will try to solve it and prepare the solutions in the form of a solution tree that is state spacee tree。

 so I will generate state spacee tree now。Let us generate a state space tree。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_14.png)

This is the root。Now first queen， I will keep it in first column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_16.png)

Queen1 in first column。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_18.png)

Then queen2， as we decided， will not keep it in the same row and same column， but in diagonal。 Now。

 actually， it should not be in diagonal。 They should not be under attack。 No。

 I am not checking that attack without attack only just I am drawing what are the possibilities。

 Okay， then afterwards， Ill show you how to check the attacks and how to generate a tree。 first。

 without attacks， I am preparing a state space tree。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_20.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_21.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_22.png)

Second green in second column。Then third queen can come in third column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_24.png)

Yes， third green can come in third column。So For queen in For column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_26.png)

There's one possibility。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_28.png)

Now， this is one possibility， right， though they are under attack， right， but。Beyond this。

 is there any possibility of moving fourth queen， No， So move back for third queen， there is a place。

 So move third queen to a fourth column。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_30.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_31.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_32.png)

Then this will be filled with four queen。So third queen goes into fourth column and fourth queen comes in third column。

This is how we represent the possibilities。 That's what I am showing you。Now， continue。

 Can in key fourth queen anywhere。 No， third queen， there is no place。 So take out。

 see this is the last cell。 Now， move second queen， second queen in third column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_34.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_35.png)

So second queen in third column， Then third queen in second column。Third queen in second column。

 then fourth queen in fourth column。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_37.png)

Fort queen and Fort Ga。Now， fourth queen， there is no place。 Take out Third queen。

 Can I keep it here， We decided it will not keep in the same column， so keep it here。

So third queen will go into fourth column， then fourth queen can come in second column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_39.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_40.png)

Then， here。Now， is there any place for fourth queen， no place， third queen， no place， second queen。

 you can move it to fourth column。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_42.png)

Second queen， can we move to fourth column。Then third queen in second and fourth in third。

 then this is third， this is second， then go back now for second queen also there are no places available。

 then take out this move queen one。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_44.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_45.png)

Queen1 in second column。Now， below this also， you get a huge tree like this。 Then again。

 third column， you get a tree。 You get a tree like this。

So total how many cells we will be checking like this for this one。See， this is first node。

 Let us check the nodes。 So here I will get four nodes。

 This is in third column as well as fourth column。 So four nodes then below each node here，3。

3 nodes are there， so4 into34 into three nodes plus then below this two two nodes are there below this every node。

 so four into3 into two nodes plus last 1，1 nodes are there。 So4 into 3 into2 into one。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_47.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_48.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_49.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_50.png)

These many nodes will be generating when we have avoided same row and same column。

 but we are allowing diagonals。So then how much this is， This is one plus sum of。

Now this I takes values from 1，2，3， four terms are there， so I takes value 0 to3。

 so I am starting from 0 to 3。 then this is product of product of what4 minus J and J takes the values。

 this is0 to I。你的是在。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_52.png)

Right， this will be a formula for knowing the number of nodes。 If I simply calculate。

 this is one plus 4， and this is 2 L plus。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_54.png)

24 plus 24。 So this is 48。60。And 65。65 node will be getting。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_56.png)

This is for four queens if you take8 by8 it will be 8 minus G for any n queens this will be the number of nodes that will be getting generating for solving this one。

 so this is showing the maximum number of nodes So formula is for maximum number of nodes。

 we will not be generating all of them but maximum this will be generated。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_58.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_59.png)

Now， we will solve the problem by following this method only right。

 And what is the condition for us Boing function is that they should not be in the same row and same column and same diagonal。

 So I will consider that， and I will generate a tree。 and now we will be solving the problem。

 So I will rer the tree again by applying bounding function。 That is the condition。Now。

 let us solve this with bounding function。 So what is bounding function。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_61.png)

Bounding function is condition right， So what is the condition not in same row。

 same column and same diagonal， right， we will check this one。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_63.png)

Now， we'll draw the same tree once again。 First step is Queen 1 in first column。

 Queen1 in first column。Then going to in second column， going to in second column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_65.png)

They are another attack。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_67.png)

So don't go further， kill this node。By applying this condition， bonding function。

 this has violated the condition。 So we have killed this node， so we cannot keep it there then。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_69.png)

Pick up going to from there。And keep it in third column， queen to win third column。

 So the next possibility is a queen to win third column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_71.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_72.png)

Is it under attack？ No， continue further。 Queen 3 in second column。

 We will not keep it in the same column， right， Second column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_74.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_75.png)

Second column， it will be under attack。 So queen 3。In second column， bonding function。

 this will be under attack。 Don't keep it there。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_77.png)

Now， let us try another cell。 This will not keep it in same column， so we'll keep it here。 Q 3。

 this column， co 3 in fourth column。 So co 3 in fourth column there also it is under attack。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_79.png)

So no question of placing fourth queen at all， right third queen itself did not find its place。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_81.png)

Is there any other cell remaining for third queen， No， now we have to move second queen。 So okay。

 move second queen。 So second queen is moved in fourth column。 So this is in fourth column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_83.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_84.png)

Now， third green。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_86.png)

食紧角龙。Third green in second column， yes。This is possible for third queen。 They are not under attack。

 Now， fourth queen， what is the cell remaining here， Four queen， if I keep here。

 it will be under attack in third column。 So if it is in third column fourth queen， right。

 this will be under attack。 So killed。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_88.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_89.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_90.png)

So pick up fourth queen。 Can I keep it here， No， All cells are over。 No queen 3。 It can be cake here。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_92.png)

So that is in third column， third column。But that is diagonally under attack， so don't go further。

 this is skill。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_94.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_95.png)

So can I keep it at this place。 No， we are not keeping in the same column。 Now move queen 2。

 queen 2 cannot be moved。 So pick up queen2 also and move queen 1。 So queen  one in second column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_97.png)

So green one in second column。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_99.png)

Not going to。 It can be kept here。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_101.png)

军度。At first column， this is enter tag diagonally。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_103.png)

Second column will not keep it third column。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_105.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_106.png)

Third column， again， under attack， diagonally。Now let us keep it in fourth column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_108.png)

Ford color。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_110.png)

Yes， this is possible。 They are not under attack。 Now， let us keep third queen。

 So if want a place for second queen， then only try to keep third queen。 Third queen。

 Can I keep it in。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_112.png)

Column 1， yes， third queen in column 1。 So x 3 in column 1。 So third queen is here。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_114.png)

They are not under attack。 Now， fourth queen， this cell， the cell will not keep here only。

 This is the only place。 So queen 4 in third column。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_116.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_117.png)

Is it under attack， No， we got a solution。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_119.png)

What is that solution，2，4，1，3。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_121.png)

2，4，1，3。 Actually， these values， we were trying them here in an array。 Now。

 I have written the answer finally。 So 2，4，1，3。

![](img/232d9c227bf87aa0688a2fe16a8a92cc_123.png)

This is one answer。Right。And I have to continue further。

 and I try to find out any more answers are possible。 So， yes， there is one more answer。

 If you continue doing this。 What is the other answer， See mirror image of this one。

 So Q1 will be on this side and Q 2 on this side。 and Q 3， this side， Q 4 here。

 mirror image of this one。 So that is 3，1，4，2， So3，1，4，2。 So what are the answers， solutions are。

 There are two solutions，1 is 2，4，1，3， and 3，1，4，2。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_125.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_126.png)

![](img/232d9c227bf87aa0688a2fe16a8a92cc_127.png)

That's it。 So I have shown you before this 1， I have shown you all possibilities。 Now。

 I have used bonding function and solve this using backtracking。



![](img/232d9c227bf87aa0688a2fe16a8a92cc_129.png)