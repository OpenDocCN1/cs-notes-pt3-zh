# 【精译⚡算法导论】AbdulBari p76 p75 10.1 AVL Tree - Insertion and Rotations -BV1hhPXeTEWM_p76-

Tpicic is aviaries。 and these are the things I am going to discuss in this one。

 That is what is binary search tree， drawbacks of binary search tree。

 how binary search can be improved。What is an avi tree。

 how the rotations are performed in avi tree and how to generate aviry or create avi tree from given set of keys。

Let us start with the binary search tree。 This is a binary search tree。Here。

 the keys are arranged such that for any node， all the elements on the left hand side are smaller than that node。

 the elements on the right hand side are greater than that node means for any node。

 the elements in the left sub are smaller than that key element。

 and in the elements in the right sub3 will be greater than that element。

 So3 is greater in 2010 is less than  20。 So in this way， the elements are arranged。

 reason it is useful for searching。 How suppose I want to search for a key element， say 30。

Then I'll start my search from root。 I'll check with the root element。 Is it 30。 No。

30 is smaller than that key element。 So go on the left hand side。Now， is it 30。 No， this is not 30。

30 is greater than this key element。 So go on the right hand side。 Now， right hand side， yes。

 this is the key element found。So total  three comparisons， we got the element。Let us take one more。

 If I am searching for the key element 60， then is it 60， no。60 is greater than this one。

 So go on the right hand side。 I it 60。 No 60 is greater than 50。 So go on the right hand side。 Yes。

 I got the element。 So only in three comparison， I got this element。😊。



![](img/991d152afafa33a68c0aa8e5f4c6c636_1.png)

Let us take one more key。 Suppose I want to search for a key element 32。Let us search for it。

Start from here。 This is not 32。32 is less than this one。 So go on the left hand side。

 This is not 32。 So 32 is greater than this one。 So go on the right hand side。 This is not 32。

32 is greater than this one。 So try to go on the right hand side， but there is nothing。

 So now search fails。 So for this， we cannot find the element。

 So the point here is that when you are searching for a key element。

 Pos is it can be found or it will not be found。So search may be successful。

 Also search may be unsuccessful also， but when the search for unsuccessful。

 how many comparisons I made1，2，3。 So total 3 comparisons。

 So maximum number of comparisons required for searching any element in a tree depends on the height。

😊，So the time taken for searching in a binary search tree depends on the height。

 Usually we mention height starting from0 onwards， but I will take from one onwards123。

 So let us say height of this binary search tree is a3。

 so the time taken is dependent on the height for binary search tree。



![](img/991d152afafa33a68c0aa8e5f4c6c636_3.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_4.png)

So this is one of the property of a binary search tree that is useful for searching purpose。

 The elements are organized， smaller on left side， greater on right side。

 and the time taken for searching is depending on the height。 Now。

 the question is what is the height of a binary tree。

 like binary search is nothing but a binary only what is the height of a binary tree。

 height of a binary tree can be minimum login。

![](img/991d152afafa33a68c0aa8e5f4c6c636_6.png)

And maximum。

![](img/991d152afafa33a68c0aa8e5f4c6c636_8.png)

And。So it depends for same set of keys， we can form different binary search trees。

 It may extend its height up to n also， or it may reduce its height to log n also。

 so it means the minimum time taken for searching in a binary search tree maybe log n maximum time maybe n。



![](img/991d152afafa33a68c0aa8e5f4c6c636_10.png)

So let us observe the next thing what is the problem with binary search tree。

 let us see how to create a binary search tree， I have set off keys here and the same keys I have taken here also in the different order something I want to show you by creating a binary search tree。

 let us first create a binary search tree for these keys。



![](img/991d152afafa33a68c0aa8e5f4c6c636_12.png)

What is the method of creating a binary search tree。 So we have to insert one element at a time。

 So first key element that is 30。 So there is nothing I have taken 30 here。 Now。

 inserting 4040 is greater than the root that is 30。 So insert 40 on the right hand side。

Then 10 is a smaller than root that is less than 30， so insert it on left hand side。

Then 50 check from root for every element we should check from root 50 is greater than 30 and it is greater than 40。

 so insert it here。20，20 is smaller than 30 come this side， left side and 20 is greater than 10。

 so insert it on the right hand side。The next is 5，5 is smaller than 30。 Come to left side。

 It is less than 10。 Its smaller than 10 also。 So insert it on the left hand side。

35 is greater than 30 go to right side， less than 40， so insert it on the left hand side。

She suppose if I am inserting again 50 then start from here， 50 is greater than 30。

 50 is greater than 40， 50， its already 50， 50 is already present here so don't insert it so we don't insert duplicates in a binary search。



![](img/991d152afafa33a68c0aa8e5f4c6c636_14.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_15.png)

Now this is the binary search tree I got based on these key elements what is the height of a binary search tree。

 This is minimum height that is login， what will be the time taken for searching any key element in this one it will be login that depends on the height of a binary search tree so height is login。



![](img/991d152afafa33a68c0aa8e5f4c6c636_17.png)

So for the set of keys， when I have created a binary thirsty， I got this height。Now。

 same keys I have taken them here Also see50 is there，40 is there，35。

 all the keys are as it is so but the order is different。 Now let me create a binary 3ir0 for that。

 start from the first key element 50 next is 4040 is less than 50 so it will come as a left hand side then 35 is less than 50 and also less than 40 So it comes on left hand side。

30 less than this less than this as well as less than this so it will come on this side then 20 is smaller than smaller than smaller than it comes this side and 10 come on this side and 5 comes on this side。

😊。

![](img/991d152afafa33a68c0aa8e5f4c6c636_19.png)

So this is the height。 height is what n。Height of a binary searchtry is n。See。

 the keys are given such that the binary firstir when I am creating， it is becoming height。And。

So this is the problem with binary search team。The method of creation is。

 we insert one element at a time， the method I have shown you。

 But what will be the final height that is not ener our control。 The height may be log n also。

 the height may be order of and also。 it depends how the key elements are inserted。

If the height is login， then the time taken for searching is login and if the height is n。

 then the time taken for searching is n。 and it is similar to linear search then If I have to search in this binary search tree。

 It is similar to linear search。 Like see if I want to search for5。 then I should start from here。

5 is smaller than this and smaller than this and smaller。 So finally。

 how many comparisons I have to make all 7 comparisons。

So this is the problem with binary searchtry that height is not under control。

 It all depends on how keys are inserted。 So this is the drawback of binary search。 Next。

 Can we improve binary searchtry。 Is there any chance， Let us look at this， I have three keys here。

 Let us create a binary searchtry using those keys。



![](img/991d152afafa33a68c0aa8e5f4c6c636_21.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_22.png)

See these keys， if I insert them and create binary the research tree then the tree that I will get is 30 then 20 is smaller than that。

20 comes on this side and 10 is smaller than that it comes on this side。

 So what is the order in which I have inserted。I have first inserted 30， then 20， and then 10。



![](img/991d152afafa33a68c0aa8e5f4c6c636_24.png)

Can I insert the same keys in a different order。 Yes。

 there are many orders possible for the same set of keys。 So if I am getting the keys like this。

 then this is the tree， what I am getting。 If the order is different。

 let us say it is 30 than 10 and 20。 Then how a tree looks like。 So 30，10 is smaller than this。

 So it comes this side，20 is smaller than 30 but greater than 10。 So it comes on this side。😊。



![](img/991d152afafa33a68c0aa8e5f4c6c636_26.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_27.png)

So this is the shape of a tree I am getting。And can I take a different order？ Yes。

 I'll try a different order。 That is 10。

![](img/991d152afafa33a68c0aa8e5f4c6c636_29.png)

30 and 20。 So this is 10， and 30 is greater。 So it's come this side and 20 is greater than 10。

 but less than 30。 So it comes this side。

![](img/991d152afafa33a68c0aa8e5f4c6c636_31.png)

another shape I am getting。If I take 10，20 and 30， then this is 10，20 is greater。

And 30 is greater than that。

![](img/991d152afafa33a68c0aa8e5f4c6c636_33.png)

So for different orders， I am getting different shapes。 So for three keys。

 how many orders are possible， three factorial orders are possible。 That is6 orders are possible。

 So 4 already have taken。 So Ill take two more，2 more are possible。 That is 6 are possible。

 So two more。 I will take That is 2010 and 30 or20，30 and then 10， Let us create 20。 It comes here。

10 is smaller than this。 So 10 comes this side，30 is greater than this。 So it comes this side。

 And for the next order Also 21t then 30 comes on the right side，10 comes on the left hand side。

 So I am getting a thing like this。So it means that for the same set of keys。

 if I insert them in different order， I am getting different shape of binary search trees。

If you look at these trees， the height of these trees is1，2，3。

 all these trees are having height 3 for just three keys height is3。

 so these are with the maximum height。But this tree is of height to2。 so this is of minimum height。

So this means that if you have some set of keys， you can form a very long binary search tree also or a short hide binary search tree also。

 So what we prefer is a minimum height binary search tree so that the search time can be reduced。

This is the objective。So the drawback of binary search tree is that for same keys we can get differentiate shape binary that can be of maximum height or even of minimum height。

 what we prefer is we want minimum height binary search tree。

So now let us see whether binary surgery can be improved or not。See， for the same set of keys。

 if I am getting in these orders， I am getting these shaped binary searchries， but I want this one。

Is there any way to convert this。So there is no way just we say that just remove it and take this one。

 if you' are getting any other shape。 Just take this one。 but there should be some method。

 which we should define some procedure for converting that one into this one。 So for that。

 we define rotations。 We say that we rotate this tree around this node that is will pull this 30 on this side。

 So 20 will move up and 10 will move at this place。

 So we say we will perform rotation around this node。

 and we will change the shape of this node like this。 And similarly， will。



![](img/991d152afafa33a68c0aa8e5f4c6c636_35.png)

Rotate this tree around this node， and we will change the shape。

 So 10 will come down 20 will come this side and 30 will come this side。 It's just like you imagine。

 there is a nail fixed here。 And around that does a thread。 And you are pulling a thread。

 So if you pull that thread here，10 will come this side 20 will move up and 30 will move up。

 So you say that we will perform rotations and convert this larger height binary search trees into smaller height binary search tree。

😊。

![](img/991d152afafa33a68c0aa8e5f4c6c636_37.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_38.png)

So this is how we can improve。 And this gives the idea of aviary。 Then how about this。

 How do you perform rotation。 So in one step we cannot do。 First， we' will rotate around this 10。

 So 10 will come this side and 20 will come up。 Then will rotate around this 30。

 So 30 this side and 20 will move up and 10 will remain on the left hand side。 So we get this shape。

 And here also around 30 will rotate in this direction。

 Then around this 10 will rotate in this direction。 So we will have four different type of rotations。

 which we can convert binary search tree into a balance binary first tree。

 So that is the idea of aviary。

![](img/991d152afafa33a68c0aa8e5f4c6c636_40.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_41.png)

So in any shape， we want this shape。Now you may ask one thing that just we have three nodes here。

 what if we have many nodes in a binary search how rotations are done。

 So remember rotations are done only on three nodes always whatever the size of a binary search sheet maybe we look for only three nodes and we try to arrange them or adjust them by performing rotation to get a tree like this and the entire tree will get balanced。

Entire tree will be of minimum height only， so this is based on three nodes only now Im going to explain what is avial 3 then I will show the rotation。

 then I'll show how to create avi 3。Now， aary。Aviial tree is a high balanced binary search tree。

So for balancing the height of a binary search tree， we define one factor or one property。

 that is balance factor。 We calculate balance factor for each node。 What is balance factor。

 height of left sub3， minus height of right sub 3， and ensure it can written as balance or balance factor is height of left sub。

 minus height of right sub 3， and it should be either minus-1 or0 or1。



![](img/991d152afafa33a68c0aa8e5f4c6c636_43.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_44.png)

Not greater than one， not less than -1。If any node is having balance factor out of these three only。

 then the node is balance。 Otherwise， the node is imbalance。 If any node is imbalance。

 we should do something for balancing it。 That is， we should perform rotations for balancing that one。

How to calculate the balance factors， Let us see one more formula I have written here that is absolute of balance factor should be less than or equal to1 means minus or plus if you take it as positive only。

 then it should be either 0 or 1 positive1。

![](img/991d152afafa33a68c0aa8e5f4c6c636_46.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_47.png)

So we'll use this one。 Now I here I have some binary trees。

 There are no keys just I have taken empty nodes unlabeled nodes。Now。

 let us see what are the balance factor of this one。

 So how to calculate height of left sub minus height of right sub for this node。

 What is the height of left sub， So you take the longest distance in the left side，1，2。

And the longest distance on the right side，1，2。 So this is 2-2。 This is 0。 same way for this node。

 the longest distance on the left side is 1。And right side， there is nothing。 So 0，1-0 is1。

 And for this one， left side， it is one right side， it is 0。 So this is also one。

 and there is nothing on left hand right。 so it will be 0 only。



![](img/991d152afafa33a68c0aa8e5f4c6c636_49.png)

So for all the nodes， we got the balance factors as 0，1，1，0，0。

 These are within this set only so this three is balanced because every node is balanced。



![](img/991d152afafa33a68c0aa8e5f4c6c636_51.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_52.png)

Now， let us look at this。For this node，1，2，3。Height is。 I'm counting edges。 Okay。

 the longest part you should take。 don't count the nodes。 We are not counting the nodes。

 We are finding the height。 So 1，2，3。

![](img/991d152afafa33a68c0aa8e5f4c6c636_54.png)

-1。 So this is 2。 This is imbalance。 The nor is imbalance。

Let us look at others also this is0 left side， right side is1，2，2， so this is minus2。

 so this is also imbalance。This will be 1-0。 It is 1。 This is 0 only， and this is 0 only。

That is c for this， also。

![](img/991d152afafa33a68c0aa8e5f4c6c636_56.png)

Left side is one， right side is  one，2，3， so I am taking height。Right， so this is 3， and this is -2。

 It is imbalance。 See， I'm not counting nodes 1，2，3，4， not 4 height。 So take the longest distance。

 Now for this， the balance factor will be 0。 Leaf nodes will have balance factor as 0， This is 0-1。

-1。 This is 1-2。1-2 is-1。

![](img/991d152afafa33a68c0aa8e5f4c6c636_58.png)

That's all。These two trees are im balance。 They are having some nodes which are not high balance。

 but disit is perfectly balanced。Now we'll learn about rotation。

 If any node is im balance based on the balance factor。

 then rotations are performed for balancing that node。 So let us learn what are the rotations。



![](img/991d152afafa33a68c0aa8e5f4c6c636_60.png)

Now we go for the first rotation。 the name of the rotation。 I'll write afterwards。

 Let us look at this。 I have a binary search tree， the initial binary search tree。

 just there are two nodes。30 and 20。 Let us check whether it is balanced or not。

 The balance factor is one and 0。 So this is one， and this is0。 So this is balanced。



![](img/991d152afafa33a68c0aa8e5f4c6c636_62.png)

Now， in this tree， if I insert。

![](img/991d152afafa33a68c0aa8e5f4c6c636_64.png)

And。Then where 10 should be inserted 10 is smaller than 30。

 It goes on left side and it's less than 20。 it goes on left side。

 and there is no 10 here so I can insert it 30。

![](img/991d152afafa33a68c0aa8e5f4c6c636_66.png)

20 and 10。It is inserted on this site。Now， count the balance factor。 This is 0， and this is1。

 and this is 1，2， and that side 0 only。 So this is 2。 So this node became imbalance。

 that node became imbalance。Now， I have to perform rotation for balance that one。

But let us see why it became imbalance。 This became imbalance。

 because I have inserted on the left off left。 So this is。Left off， left。Imbalance。

Let us call it as left off， left imbalance， N， perform rotation。After rotation。

What type of rotation I should perform。 See for this node， the balance factor is a2。

 So it's heavy on the left hand side。 If its balance factor is -2。

 then it means it's heavy on the right hand side。Okay， I don't have to check which side it is heavy。

 but one important thing is this node became imbalanced because we have inserted on left of left。

 So perform this rotation on this one over this node。

 So over this node will perform this type of rotation。

 So how it looks like 20 will move up20 moves up and 30 will move to the right side。



![](img/991d152afafa33a68c0aa8e5f4c6c636_68.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_69.png)

And 10 will take the place of 20。

![](img/991d152afafa33a68c0aa8e5f4c6c636_71.png)

10 now， this is perfectly balanced。

![](img/991d152afafa33a68c0aa8e5f4c6c636_73.png)

This is balanced。

![](img/991d152afafa33a68c0aa8e5f4c6c636_75.png)

So because this was L L imbalance， I have performed this rotation。

 So let us call this rotation also as。

![](img/991d152afafa33a68c0aa8e5f4c6c636_77.png)

And L rotation that is left left rotation。

![](img/991d152afafa33a68c0aa8e5f4c6c636_79.png)

So， this is the first rotation。This is initial three。

30 and 10 balance factors are this is zero and this is one。



![](img/991d152afafa33a68c0aa8e5f4c6c636_81.png)

Now， I will insert。20 in this one。

![](img/991d152afafa33a68c0aa8e5f4c6c636_83.png)

So 20 is less than 30， it goes on left side， but greater than 10， so comes on right side， so 30 here。



![](img/991d152afafa33a68c0aa8e5f4c6c636_85.png)

10 on the left hand side， Im 20 on the right hand side of 10。



![](img/991d152afafa33a68c0aa8e5f4c6c636_87.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_88.png)

Now， let us calculate balance factors。 This is 0， and this is -1， and this is2。



![](img/991d152afafa33a68c0aa8e5f4c6c636_90.png)

Again， this mode is imbalance。 Why it became imbalance。

 Because I have inserted on the left and then right。 So this is。



![](img/991d152afafa33a68c0aa8e5f4c6c636_92.png)

L R imbalance。

![](img/991d152afafa33a68c0aa8e5f4c6c636_94.png)

LR imbalance。Then you remember， I said that whatever the binary searched you get with three nodes。

 we will take a balance3 we1 that one。 So on this we have to perform rotation。

 So the rotations these are two step rotations。 so I will write down here30。10 and 20。

 So first you perform rotation on this one。 So how it looks like 30。

 then 20 comes here and 10 comes here。So we have performed rotation over 10。

 pull 10 this side by fixing a nail here。 So who will move up，20 will move up。

 that will not be affected。 So 10 is pull this side。 So 1020 will move up。 It looks like this。 Now。

 perform this rotation。 If you perform this rotation Again。

 the result is 20 will be in the root and 10 will be on the left hand side。30 on the right hand side。



![](img/991d152afafa33a68c0aa8e5f4c6c636_96.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_97.png)

6是呗。Now， this is the fixed point over which rotation is done。

 so 30 is moved that side 20 moves up and 10 moves up。



![](img/991d152afafa33a68c0aa8e5f4c6c636_99.png)

That's it。 So this is two step rotation。 This is not two rotations。 This is double rotation。

 We count this also as single one rotation only， but this is having two steps inside。

 So we call it as a double rotation。Now what is the name of this rotation。

 the imbalance was left right type， so let us call this rotation also LR rotation。

So so far we have seen two rotations that was L rotation， it was single step， then L rotation。

 it is a double steps two steps are there。Now， similarly， we have two more rotations。

 I will quickly cover them。This is initial 3。 The balance factors are 0 and1。 Now。

 insert 30 in this one，30 is greater than 10 and greater than 20。

 So 30 comes on the right side of 20 Then the balance factors are 0 and this is -1 and this is -2。

 So this became imbalance。 So which type of imbalance because you have inserted on the right of right。

 So this is R are imbalance。

![](img/991d152afafa33a68c0aa8e5f4c6c636_101.png)

When R R imbalances， there will perform this type of rotation by fixing this node will pull 20 here。

 So to 10 here，20 will move up and 30 will move up。 right， So it looks like this again。

 And the balance factors will be 0，0，0。 What was the type of imbalance R R。

 Let us call this rotation also as R R rotation。

![](img/991d152afafa33a68c0aa8e5f4c6c636_103.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_104.png)

So this is the third rotation， again， this is a single rotation。Now， next rotation。Initially。

 the tree is 10 and 30 B factors are 0 and minus-1。 insertsert 20 in this one。

20 will come as right side of 10， but left side of 30。



![](img/991d152afafa33a68c0aa8e5f4c6c636_106.png)

Balance factors are 0 and 1， and this is -2。 So this node became imbalance。 How it became imbalance。

 The insertion is done on right， left。 So let us call this as R L imbalance。Now。

 for this also two steps are rotate required。 that is double rotation is required。 so that3。

10 and 30。20 first， it is rotated around this one。 Then 10 comes here。And 20 and 30 comes here。

 Then pass a rotation over this one， over this node。Over this node。Then the tray looks like this。

 The balance is imbalance is R。 So the rotation is also R rotation。



![](img/991d152afafa33a68c0aa8e5f4c6c636_108.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_109.png)

So that's all。 These are four rotations。 And now I will show you how to create a aviL tree by inserting keys  one by one。

 So we have seen total  four rotations out of which。



![](img/991d152afafa33a68c0aa8e5f4c6c636_111.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_112.png)

L， L and R， R are similar。 These are single rotations and L， R and R， L R。Similar。

 these are double rotations。Now， I'm going to show you special cases in these rotations。Suppose。

Our binary search tree is like this。These are the node， A，BC， and A is having some left child。

 right child。 That is right child of a。 And there is B is also having some right child and C is having left child and。

Right child。 So it means it's a very big tree。Don't know how many nodes are there below this one。

 So we have just taken it as right sub3 of a。 So any number of nodes below that one。

 But suppose this node became imbalance。This note became imbalance。

Because of insertion on the left of left， the site， the site。 So an L rotation。

 how to perform this one。We have to perform rotation around this node。

L L rotation means imagine that assume that insertion is done on left of， left of this A。

 and a became imbalance。 So let us look at how rotation is done over that node。 L L rotation。

 So don't look anything。 Just look at ABC and draw this one。 So this is B and C and A。



![](img/991d152afafa33a68c0aa8e5f4c6c636_114.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_115.png)

As I said， rotations are done always within three nodes。



![](img/991d152afafa33a68c0aa8e5f4c6c636_117.png)

Now， what about others， see left child， right child， they will be as it is。

 C left child and sees right child will be as it is。Then Ari Chad will also be in his own place。

Then what is missing there， B' is right child。 So this is right sub3 of B。

 So it should be on the right hand side of B only。 Then where it should come。

 Where is the space remaining。 Here is the space remaining。 So B's right child will come here。



![](img/991d152afafa33a68c0aa8e5f4c6c636_119.png)

Bes right child will come here。Alright。 So this is。

 you can take it like a formula or an example in a big size tray with lot of nodes beneath this one。

 Just we are looking at these three nodes out of which this node has become imbalance。

 So this is how we perform rotation。

![](img/991d152afafa33a68c0aa8e5f4c6c636_121.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_122.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_123.png)

I have shown you a little rotation， it will be similar for R rotation also it will be from that site。



![](img/991d152afafa33a68c0aa8e5f4c6c636_125.png)

This means that see， if I remove everything and just take this one。Just take this one。

 So imagine there is some nail fixed here。 and there' is a thread。 And to a thread。

 something is attached。 So there's a nail， and there is something attached to a thread。

 And when you pull a thread on this side around that nail， it looks like this。

Then what about this thing that is attached， It will go that side and look like this one。

 So same thing is happened。 A， BC and B was having a right child。 When you pull this on this side。

 A on this side。 So A goes there。 And what happens to B， R。

 it will come as a left of A removing all this。 If you just see this， the effect is similar。



![](img/991d152afafa33a68c0aa8e5f4c6c636_127.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_128.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_129.png)

Or if you keep AR。 So AR is as a。

![](img/991d152afafa33a68c0aa8e5f4c6c636_131.png)

It is just like there is a thread and a nail and you are pulling a thread on that side。

 something is attached to a thread。 So after pulling that side， this， this thing， right。

 if it goes there， the stick like thing， which goes there。

 So it looks like looks like this this is the shape。 So the same shape we are getting here。



![](img/991d152afafa33a68c0aa8e5f4c6c636_133.png)

So that's all about LL I have shown you same thing you can apply on R。

 Now let us look at LR rotation。This sub binary search tree。 I have not taken a big size tree。

 Let us first look at just three nodes。 Suppose this node became imbalance because of insertion on left right。

 So we'll perform LR rotation because it is Lr imbalance。

 So already have shown you how this rotation is performed first step like this。

 then second step like this。 But finally what will be the result。

 if first step is performed A B on this side and C on this side and B comes here。



![](img/991d152afafa33a68c0aa8e5f4c6c636_135.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_136.png)

Then again， when this rotation is performed， C goes here and B remains here and A will be on the right side。

 It looks like this by taking two steps。

![](img/991d152afafa33a68c0aa8e5f4c6c636_138.png)

I'll remove this by taking two steps。 it looks like this。 Now， can we show it in a single step。

 How we can show it in a single step。 Just see this。

We can say that when you have to perform Lr rotation out of three nodes， the last node。

 just you bring it into root。C， left side is B only that a， you take it on the right side。Next slide。

We say that we can directly。Always rotation is within three nodes only out of these three nodes last node you begingging into root。

And the route， you send it on the right side because it is L rotation。In Ral rotation。

 you can bring root on the left side。😡，So L R and Rl will be same。

 So I have shown you how we can directly perform L rotation without looking at these two steps directly。

 we can bring this note up here and send a on that side。 Now。

 let us look at how it is done on a bigger size tree。If I have a tree like this， A。

 B and C on the side。 So A is already having its right child， B is having its left child。

 and C is having left child and C is having right child also。

 and this became imbalance and imbalance is L R imbalance， L R imbalance。

 and I have to perform L R rotation。Now， they are already having some children with them。

 Their subies are there Then how rotation is done out of three nodes。

 as we know that this should move up。 So C will move up。 B remains as it is。

 A will come on the right side。

![](img/991d152afafa33a68c0aa8e5f4c6c636_140.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_141.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_142.png)

Now what about the left child of B， It will be as it is。 What about the right child of A。

 It will be as it is。

![](img/991d152afafa33a68c0aa8e5f4c6c636_144.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_145.png)

Now who are we meaning。Left subre of C， right subre of C Left of C will go in the left left side only。

 So C is here now。 So its left child will be on the left side only。

 but it will become a right child of B， and right sub will remain on the right side only。

 but it will become a left child of a。

![](img/991d152afafa33a68c0aa8e5f4c6c636_147.png)

This is the method。 You can take it like a formula now。

I have shown you that when you have to perform L R L R rotation。

 we can perform in a single step directly， so that single step I have sent it up。

 So be on the side only a have moved to the right side， then rest of the children are arranged。



![](img/991d152afafa33a68c0aa8e5f4c6c636_149.png)

So this is like a formula， formula， like you can take it and always follow this method。Now。

 the last thing is， I will take some keys and show you how our avi tree is generated。

 Let us create an avianry of these nodes。 I will insert them1 by one。

 We will calculate balance factors If any node is becoming imbalance。

 We will look at it Which type of insertion is done Why it became imbalanced。

 then perform corresponding rotations。So let us take this first key for T is inserted。

There is a single node， and it is balanced。Then insert 2020 will come on the left hand side。

And balance factors are this is0， and this is one。 Everything is balanced。Next is 10。

 insert 10 on the side。Now calculate balance factor。 This is 0， and this became 1， and this became 2。

 So height of left sub is 1，2。 So 2， right， sub is nothing is there。 So 2-0。

 This is how it is becoming 2。 So that became imbalance。



![](img/991d152afafa33a68c0aa8e5f4c6c636_151.png)

Where the incision is done on the left of left。 So L L rotation will perform L L rotation around this node。

 So 20 here。

![](img/991d152afafa33a68c0aa8e5f4c6c636_153.png)

10 decide40 here， and the balance factors are all zeros。



![](img/991d152afafa33a68c0aa8e5f4c6c636_155.png)

Now it is balanced。I'll remove this and use that one。 Now， insert next，25。



![](img/991d152afafa33a68c0aa8e5f4c6c636_157.png)

25 is greater than 20， but less than 40， so it will come this side。Let us update balance factor 0。

 This is one， and this is。1 and 2。 So 1-2。 it is -1。Perfect。😊，Next。😡，Turdy。

30 comes on right side of 20 left side of 40， but right side of 325。 So 30 comes here。

 updateate balance factors。 Bance factors are 0， and this is -1， and this is 2， and this is -2。

 This is one-1，2，3。 So this is-2。 Oh， two norms became imbalance。 This is also imbalance。

 this is also imbalance。 Now， we are learning one more thing。

 If multiple norms are becoming imbalance。 Which one we should perform rotation。

 where you have inserted here。 from there you go towards the ancestor。 The first ancestor。

 which became imbalance， perform rotation over that。 So this is the first ancestor。

 So perform rotation over that one。 automatically， that will also become balance。

So according to this imbalance node， insertion is done with side left right。 So this is L R rotation。

 So well perform L R rotation。 L rotation means what。Instead of showing two steps。

 we can simply take this 30 up and 40 this side。 So this becomes 20 on this side，10 here。



![](img/991d152afafa33a68c0aa8e5f4c6c636_159.png)

And here comes 30，25 remains here， and 40 this one。This is how L R rotation is done。

 The update balance factors，0，0， and this is 1，1。 This is also 0。 This is 0。 This is 1 and 2。

 So this is -1。Everything is balanced。I'll remove that one。 Now next node，22。

 where 22 will come right side of 20， left side of 30 and left off 25。 So it will come here，22。

 Let us update balance factors。 This remains 0 only。 This is 0， This is 1， and this is 1，2。

 and this is 1。 So this is 2-1。 This is 1 only。 What about this， this is1， and-1，2，3。

 longest distance is 3 here。 So 3 is -2。 So this became imbalance。 All our balance only。 you see，0，0。

0，1，1。 And that became -2。 So this node became imbalance。 Now， one thing to observe。

 according to this where insertion is done。Right。Left， left。R L L。No， just take two steps。

R L means consider only these three moons。 No， we inserted this one now， whatever it may be。

 wherever you insert who became imbalance， this became imbalance。

Then only take two steps or three nodes from that imbalance node， So just three nodes you see， right？

See even if I have not inserted 22， if I would have inserted 26， it would have came here。

 Then also insertion is on right left， we say it will be right left， right。

 So will not take all steps。 Just two steps from a imbalance mode。

 Whoever became imbalance from there， just two steps。 So if you just take two steps。

 performform L R rotation。 So asperella rotation， this 25s can be sent up25 sent up。

 and on this side comes 20。 So what about 1010 will be remain as a left child of 20， And this side。

30 will be as it is。 and this is 40。

![](img/991d152afafa33a68c0aa8e5f4c6c636_161.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_162.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_163.png)

What about this 22 who was left child of 25， It still be in a less sub of 25。

 so it will come this site， 22 will come this site。



![](img/991d152afafa33a68c0aa8e5f4c6c636_165.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_166.png)

That's how the rotation is performed right This。 We have performed R L rotation。

 Although we have shown you how Rl is performed。 Now， last key is remaining。 that is 50。

 Let us insert there 50 comes this side that is right side of 40。 Now， if you check balance factor。

 these are all 0，0，0， and this is 1，2。 and 1，2，3。 So this will be -1， and this will be 1，2。

 So this is -2。 And this is -1 and 0。 So this node became imbalance。 Per rotation along this one。

 So which type of imbalance are our imbalance or perform rotation。 So 25 and 2010 and 22。

 they all remain as it is。 And this will be 40 and 30。



![](img/991d152afafa33a68c0aa8e5f4c6c636_168.png)

50。Now it's perfectly balanced binary Search TV card that is AVL3。

 high balance AVLT or binary search TV card。So this is the method of creating aviary。 Now。

 one thing to remember that don't allow any node to exceed the balance factor from -2 or 2。

 you should never get -3 or 3。 if it is becoming imbalance， then in their perform rotation。

Don't wait that first I will insert all the notes， then afterwards， I'll perform all the。 No。

 this is not possible。Whenever any node is becoming imbalanced， just after insertion。

 if any node is becoming imbalanced， then just perform rotation and balance the tree。Now I take you。

 Ill show you one more last situation than how rotation is done。 Let us look at one last thing。

 a big victory I have taken here。 Let us see whether it is balanced or not B factor for leaves will be zeros only these are all zeros。

Then this node 1，1。 So this is 0。 This is 1，2，1，2，3。 So this is  -1 balance only what about this 1，1。

2，1，2。 So this is 0， and this is also 0。 This is -1。



![](img/991d152afafa33a68c0aa8e5f4c6c636_170.png)

So all nodes are perfect， so they are all balance。 so the trees is balance。

Now I will insert a new node that is 42。 So 42 is greater than 40 less than 50 less than 45。

 but greater than 41。 So 42 comes here。 Let us see what happens。 I'll update the balance factor。

 This becomes 0。 This becomes -1。 This becomes 1，2， and this is 1。 So this becomes 1。 and this is 1。

1，2，3， and this is 2。 So this also becomes 1。 And what about this， This is 1，2。 So this is 2，-1，2，3。

4，4。

![](img/991d152afafa33a68c0aa8e5f4c6c636_172.png)

![](img/991d152afafa33a68c0aa8e5f4c6c636_173.png)

And this is -2。 This node became imbalance。 Now， which rotation I should perform。

Where I have inserted right， left， left， right， right， left， left， right， don't take all steps。

 Just take first two step， left right， remove this one。

I have to perform quotation by using just three nodes。So what happens 45 goes off 40 moves here。

 What about all other nodes Al have shown you the formula how they are adjusted so just you can follow that and complete this rotation。

So that's all the height of a avial tree is always balanced。

 so it is a balanced height balanced binary search tree a binary search tree only but it will maintain the height and it will try to maintain always log and height it will not exceed to n like binary search tree。

So at most the height of her。

![](img/991d152afafa33a68c0aa8e5f4c6c636_175.png)

Avial tree is measured as。1。44 into login。 So at most， it may be 1。44 into login， right。

 It cannot be always exactly login。 It may be little then little bigger also。

 but it will be multiples of login only。 So asymptically。

 we say the time taken for searching in a aviial trace。Login， that's all about A Vl3。

Just like aviial tree， there is one more hide balance binary search tree that is red， black tree。

The idea of red black tree is also same as avial tree， but avial tree is more strict。

 and there may be many rotations perform in avial tree while creating an avial tree。

 We may be performing a lot of rotations to avoid that rotations， more frequent rotations。

 Red black trees used red black tree is not having that much strict rules as compared to avial tree。

 but red black tree is also as efficient as avial tree。

 So these are two high balance binary search trees。 So we have discuss about avial tree。



![](img/991d152afafa33a68c0aa8e5f4c6c636_177.png)

That's all about this。