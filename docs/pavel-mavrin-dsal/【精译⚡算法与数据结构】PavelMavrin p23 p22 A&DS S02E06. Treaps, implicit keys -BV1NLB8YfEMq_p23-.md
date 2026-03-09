# 【精译⚡算法与数据结构】PavelMavrin p23 p22 A&DS S02E06. Treaps, implicit keys -BV1NLB8YfEMq_p23-

。🎼追冲冲冲。🎼。🎼，So today we discuss one more。

![](img/584d94033a656a21a9120a432ef8042a_1.png)

Binary search tree and this binary tree， she usually called tree。



![](img/584d94033a656a21a9120a432ef8042a_3.png)

。

![](img/584d94033a656a21a9120a432ef8042a_5.png)

Okay。啊。

![](img/584d94033a656a21a9120a432ef8042a_7.png)

Sometimes it's referred as cartesian train。

![](img/584d94033a656a21a9120a432ef8042a_9.png)

。

![](img/584d94033a656a21a9120a432ef8042a_11.png)

So it is basically the same structure， but when it's used as a binary search tree。

 it's usually refer as strip。

![](img/584d94033a656a21a9120a432ef8042a_13.png)

So what is drip is basically？Just another method how to balance your binary research tree。

 so when we discussed last time when you have a binary research tree。

 you need some mechanism to make the height of this tree logarithmic and T is one another method how to make this height logarithmic。



![](img/584d94033a656a21a9120a432ef8042a_15.png)

So what operations can you make the three thing， it's a binary search tree so you can make all operations we discussed in previous lecture。

 you can insert element， remove element， find the element， find the closest element and so on。

 find the next element， previous element， minimum element， maximum element。

 all the same operationss as in all binary search trees。But we to make the things more interesting。

 we will introduce two more operations， operations split and merge。



![](img/584d94033a656a21a9120a432ef8042a_17.png)

![](img/584d94033a656a21a9120a432ef8042a_18.png)

Oh我。

![](img/584d94033a656a21a9120a432ef8042a_20.png)

So how this operations works operation split makes the phone up in operation split you have。

三 parameter x。

![](img/584d94033a656a21a9120a432ef8042a_22.png)

And it makes the phone， you have a binary search stream。

And you split this binary street into two parts。

![](img/584d94033a656a21a9120a432ef8042a_24.png)

So you make two bin trees。

![](img/584d94033a656a21a9120a432ef8042a_26.png)

The first binary theos contains all elements， let's say less than x。



![](img/584d94033a656a21a9120a432ef8042a_28.png)

お。And the second binary tree contains all the element greater or e ones。



![](img/584d94033a656a21a9120a432ef8042a_30.png)

![](img/584d94033a656a21a9120a432ef8042a_31.png)

Like thisす。basicallyically， you have the order of。Some order set of elements。

 you like split this order in the middle and have ordered set here and order set here。



![](img/584d94033a656a21a9120a432ef8042a_33.png)

啊。Nge operation and make the opposite operation。 So you have two separate binary search trees。Yeah。



![](img/584d94033a656a21a9120a432ef8042a_35.png)

And in these two separate binary search trees， you need all elements of one binary search tree to be less than all elements in another binary。

You need all elements here， but less than all elements here。

And this separation just combines these two binary trees into one big binary tree。



![](img/584d94033a656a21a9120a432ef8042a_37.png)

But basically， if you look on elements like。Elements in binary three just some elements in the sorted border。

 right so here you just， you have this set of elements。



![](img/584d94033a656a21a9120a432ef8042a_39.png)

sortrted。

![](img/584d94033a656a21a9120a432ef8042a_41.png)

And we just split this set of elements from here， so one part goes here， one part goes here。

 and here you have two sets of elements， one set and another set。



![](img/584d94033a656a21a9120a432ef8042a_43.png)

![](img/584d94033a656a21a9120a432ef8042a_44.png)

So all elements here are to the left to all elements here。

And you just combine all these elements into one big set of elements。



![](img/584d94033a656a21a9120a432ef8042a_46.png)

Like these。对。No。啊。Let's talk about structure of the tree so how the trip is what is the structure of the trip and how do we maintain that the head of the tree is log very simple each node of the trip contains two keys。



![](img/584d94033a656a21a9120a432ef8042a_48.png)

Let's it here so in each node of the binary search tree， we will have not one K up two keys。

 let's say X and y。

![](img/584d94033a656a21a9120a432ef8042a_50.png)

![](img/584d94033a656a21a9120a432ef8042a_51.png)

And we will maintain the following property if you look on the left subre。So on the let upstream。



![](img/584d94033a656a21a9120a432ef8042a_53.png)

诶。The first key of all elements in the left sub is less than x。And the second key is less than1。

And now if you look on the right sub。The first key is greater than x。



![](img/584d94033a656a21a9120a432ef8042a_55.png)

And the second key is less than one。

![](img/584d94033a656a21a9120a432ef8042a_57.png)

That's all。That's the basic property of the trip， how that's the only property we need to maintain。



![](img/584d94033a656a21a9120a432ef8042a_59.png)

Now， why it is comp to you and what is the most visual way to show how how this tree looks like。

 So if we look on。Like for in place， we have Y here and exhale。

And just use these two keys as coordinates on this plane。 So if you have some node here。

Then all the left sub must be in this part of the way。



![](img/584d94033a656a21a9120a432ef8042a_61.png)

So your left are must be here。And your right sub must be in this part of the brain。

So if you just put all the elements of the tree。On a Cartesan plane you will have some good picture which looks actually like a normal tree。

 so all elements in the left sub are to the left and down and all elements here are to the right and down。

Well， let's build some content。Some dream。For example， you make have。From element here， element here。

 element here， and here it makes you have something let's put it。T 티。Something like this。



![](img/584d94033a656a21a9120a432ef8042a_63.png)

So that's the nice treat。Now each node has two values， each note contains two values X and Y。

Why you have two keys inside of one key， let we will talk in a minute， just wait a minute。

 let's look on this key， so if if we look on the first key， if we look on this X key。

Then this tree is just a standard binary search tree so if you if you just ignore the second key。

 look on the first key， you will have a perfectly normal binary search tree， right？

And if you look on the second team。You have something like a he。

 so if you remember the hips from the previous semester in the not new binary hips in all hips。

 like in binary hips and minimalomal hips and pibonac hips。

 maybe you remember we have this properties so the key contains the maximal element and each each child is less than its parent。

So why it's called trip trip is。Actually， come from to works。So it's。Three plus he。



![](img/584d94033a656a21a9120a432ef8042a_65.png)

Baically the story behind this name。Good。So while we need this second key。

 because I try to build a binary search tree in binary search tree， we have only one key here。

 so this x， this x。Yeah。Is the keys of your binary search string。

And the second key we will use to maintain the balance of the structure。

 so we'll just use this second key to balance our data structure。And how we will use the second key。

 very simple way。Asign。Second key in random just。Just put random values。



![](img/584d94033a656a21a9120a432ef8042a_67.png)

In old keyies。And I claim that if the second key is random。

Then the height of this tree is located different。So if this is。

 then there is expected by expected rate is。

![](img/584d94033a656a21a9120a432ef8042a_69.png)

老感。So that's the plan we need to build the binary search tree， right so we have。

We have this axis as the keys we store in our binary research stream。Additionally， we will assign。

Some random value to each key。Just just pick00 million。

And then we will build this tree using this property。

And the fun fact is that if you make random keys， then the height of the tree will be logarithmic。

 so we only use this random keys to maintain the logarithmic height of this tree。Let's the plan。Yes。

 yes， this。So unlike the AL tree of red belllect and other data structures。

 which are deterministic binary search trees， this is random binary search tree so this height is actually not determined it is random。

But with that good probability， it will be logarithmic if these keys are actually random。

 then that good probability this hyper will be algorithmarithmic。

We discussed in the previous chapter when we discussed randomized algorithms。

 we discussed that sometimes it's better to use randomized algorithms for various reasons。

 first of all， sometimes it's。Much easier to design randomized algorithms。

 and sometimes they actually fe and determine the algorithms。

 So this that's one of the cases when it's actually when we I plan to write the whole code of this binary search tree on this portal this。

Let's put the。So it is not deterministic。But it will be much easier to maintain this property and the code will be much simpler and it is。

I don't， I'm not true， I think I real try slightly faster， I'm not true you can check this。

But still sometimes it's just better to use randomized data structures。在。Let's prove this。

 let's prove this。Why the paint is a lowmic for the students actually， let's see。

Maybe you have some set of elements in your binary search tree so you have all these points。

You have some random points。This is x， this is y。Let's see the Cartesian if all x coordinates and all y coordinates are different。

 then there's only one way to construct the correct strip from these keys。

 so if all x's are different all Ys are different， then there is only one way to construct the correct strip。

Y is only one way because let's see what element should be the root of this three。

 The root of the three is operates the element with the maximumimal possible y。

 So if if all ys are different， we have only one maximum。 So this element must be the root of our。T。

Now， all elements to the left must belong to the left sub。

 all elements to the right must belong to the right sub。So again， we have no validity here。

 so there's only one way to build the trip because we pick this element。

If all elements are different， you have a unique maximum so you pick this unique maximum as a root and now you build the same in these two parts so you build here you build you take again you take the maximum element make it the root of this part you find maximum here build make the root to this part and now here again you split all elements by X coordinatenet。

 so these elements must be the left sub， these elements by runs a so these element must be here。

 this element must be here， this element must be here for this part this element must be here。

 this element must be here。

![](img/584d94033a656a21a9120a432ef8042a_71.png)

Here， let's see this。SoSo there's only one way to build the correct trip if all keys are different。

On。Now， let's see how the let's。 what about the head。 What about the head。

Let's see on this let's see what is this root element。

 This root element is element with maximal value of h。 this element is maximal value of y。

But why is random， so all elements get the same random value from the same set of random values with same probailities。

So because of the symmetry， all elements have the equal probability to be the root of the tree。

So any element may be the root of the tree with equal probability。嗯。😊，So basically what happens。

 we pick some random elements。With equal probability from from all elementss and make this random element at the root of our tree。

And now we recursively make the same thing for both house so we split all elements into house。

 make the same recursive procedure here， make the same recursive procedure here。嗯hhu。😊。

So basically it's the same procedure as in the quick sort so if you remember how the quick sort works is done in the same way。

 we pick some random element， then split all elements into house like elements less than x elements greater than x。

And the coast really make the same thing in both this house。And by the same reasons。

 like in the quick sort algorithm， the height of the tree。

 like the depth of the recursion in the quick sort algorithm， it will be logarithmic。

So the height of the tree will be looking。Oh， expected。Again。

 how did you prove it when we discuss the quicker algorithm， you may prove it like this。

 you have the whole set of elements， so let's pick the middle third of the elements。So。

 this probability。1，30， you will pick one of the elements in this。In this group。

 and if you pick one of the elements in this group， you will。Make two recursive calls。

 each call is no more than two thirds of hand。Mhm。😊。

So you will pick one of the elements in this group with probably you one third。

 So it's every third time you pick one of the elements from this group。

 So every third time you split the elements in in this way。

 So the total height is no more than three multiplied by。Log base free to fan， something like that。

Yes。It's not quite very precise， but。不れ道。We need to no no no no we will not reconstruct the tree from from scratch every time we will try to maintain this property after we add one element when we add one element。

 we will only reconstruct some part of this tree Now if you need to reconstruct the whole tree every time it will be too much。

That's counter the point。It will work like in A tree in A tree you have some property and you can need to maintain this property after you make some small changes so you make some small changes then you adjust something to maintain this property and that's exactly what we'll do here so after every small change。

We'll try to make some small changes in the structure of the tree to maintain this property。

And again again， I will by help point this， so this is the only property we need to care about。

 so we will only maintain this property and if we maintain this property then the gate will be a graphic discipline。

For what curve rating you to build strips no， we discussed last time so。

In the modern competitive programming。Not that popular to use some binary search trees but now。

So it's my fashion， so a few years ago， it was quite popular to use some trips and other binary research trees in the contest。

 but not now， maybe it will be popular in a few years who knows。嗯。Again。

 this course is not about competitive programming mostly。

It's more about fundamental computer science topics binary search trees are fundamental data structure for the algorithms theory。

 so it's widely used in all various different。Very complicated data structures。作回忆。Oh。Basically。

 what you do with the binary search tree， you have some set of elements and you maintain this set in the sorted order。

So you can insert， remove， find elements， and so on。

 and you can do all the separations in log n time。That's a very fundamental result that you can maintain the sorted order of the elements and make all decorations in loggan time。

obviously can I do it faster like we discussed。Tomorrow in there。Hoometel discussion。我给他送。嗯h。😊。

You stop posting that everything is clear。ふふ。😊，You can start can continue to post that everything is clear every 30 seconds。

 it was quite helpful for me。So that's the whole， that's the whole plan。

 we will build the binary search tree， assign random second key and maintain this property。

That's the whole one cool。Now， how to make preparationations， I will start with these operationss。

 so first I will。あ。Explain how to。Implement these two operations。

And then I will explain how to implement all the basic operations like add the element and remove element。

question let's first explore these operations， so first how to split the three。Let's see。嗯， what's。

I need some more space here。I plan to put all the code and picture in this。Part of the board。

Let's try if I can do it。First， the most important thing is a picture。

So these data actually is very visual， you can write a few picture like this and see what's going on so how to make split。

Let's see you have at these。嗯。Subary。You have the sub and you need to split the sub by the value x。

 so you have the sound value x。And you need to split the sub in two parts。

 first part is elements less than x， second part is elements is greater than x。

Let's work on the route of this train， so this route。Should belong to one of the parts of the tree。

 and it's easy to see to which parts should belong so if this root is less than x。

 then this root should belong to the left parts of the tree。If the root is greater than x。

 then it should belong to the right sub。こ。So for example， if this root belongs to the left part。

 so if this if the key in the root is less than x。Then。Let's see。

 let's look on both subies of this view。So this we haveb left sub。And the right。



![](img/584d94033a656a21a9120a432ef8042a_73.png)

这样。In this left sub， all elements are less than x， so if the root is less than x。

Then all elements here are also less than x， so all elements here must belong to this left part of the splitted tree。

And in the right sub， some elements are less than x an element are greater than x。

 so let's recursively go to the right subre and split this right subre into two trees。

 so well recursively go here。Split this tree into two trees。Now， these elements are less than x。

These elements are greater equal next。And now all we need is to put this left。

Part as a right child of this of this road， so go。Put this left part here。

That's all and now we have two trees， this is the first tree， these are all elements less than x。

 so all elements less than x are the left sub， the root and the left part of the splitted right sub。



![](img/584d94033a656a21a9120a432ef8042a_75.png)

And all elements greater than x are just the split part of the right sub。哼，そ别说。Yeah。

How I will implement this， I will implement this it， so I will make split。哎呀，嘿嘿。😊。

I need letter for this route。I ought to use X。It's always always complicated， so let's call it load。

嗯。Andの byで。So this will be recursive function。It gets the node。

Which corresponds to this sub and it splits this sub into two parts。

Elements less than x element greater than x。And it returns two roots of these trees。

 so when we return from this function， we will return these two roots。

 we will return this root and this root。No root of the three is the basically how how do you when you need to get the three。

 you basically need to get the root of this tree right so root is sometimes describes the whole sub below this root。

So this split receives a root of the tree it needs to split。

And it returns two roots of the two trees after this after you split this tray into two parts。

Makeix it。Let's just implement about these。Just like in this picture， so we look on this route。

 look on the key in this route if this key is less than x first and very。

NowFirst we need to stop the recursion at some point， so if this node is no。If the tree is empty。

 that's important。We need to split the empty tree into two empty subies。No and no。

So that's the case when the current tree is empty， if you have empty tree。

 you need to split empty tree， you split it in two empty trees。Make sense。Now， if it's not empty。

 let's look on the road to。衣服。If it is less than x。Then it belongs to the left sub。

 We need to split the right sub into two parts。 So lets say P equal to。Split node， right。W yes？

So we split this right substrate into two parts。Now this。

Split returns you two roots of this episode returns you these two routes。

 these root and these routes。Now we need to take this first route and place it as the right child of node。

Right。And so now we've just returned two roots of the constructed tree so first route is node。

 second root is the second part of this split of the right substrate。So just strict。boom not。

And be second。Thats all。So that's the whole code of this case。

 so if this node belongs to the left subre， we take this node， take its right subre。

 recursively split this right sub into two parts， put this as a right child and return these two roots。

Did you miss the first part so this is the progress we need to maintain。

This is the property we need to maintain。I will use this later， I will use it， I promise。😡。

I didn't say why I need the separations， I will need the separations， okay。嗯。Now。If not。

 let me just finish this code。So if node belongs to the right substrate here， we do the same thing。

 but in a mirror。Sorry I will not travel the same picture。

 so we just imagine the same picture mirror horizontally。Yeah， so we just split。The left subt。Now。

 we put。As the left child， the second。The second tree。From this left su and return。The pair of first。

😔，And note。嗯。That's all， that's the whole quote of this split operation。嗯哼。😊，挂。Now let inspiration。

In other version， I need two trees， so I have one tree and another tree。Let's say have three A and B。

So how to merge those two trees let's see so one of let's see which of these to those meat will be the root of the merged tree。

 so the root of the tree is always the element of the maximum maxim at y。

So element of maximma y is one of the roots of this tree， so let's look on the root。

On these two trees， check which root is have the maximum value of y this element must be the root of this nurse tree。

For example， if。if y coordinate of this a is greater than y coordinate of this with B。

Then this root will be the root of the whole tree。Now， let's see testal sub。嗯。

So these elements will be the root of the tree。And now we need to put all elements。

 all these elements must be in the left subre so we just don't change this and all these elements must be in the right subre。

 so we need to put all these elements in the single tree and put this mergech tree in as the right subre。

 so we do it recursively， we just call recursively the same procedure for these two trees。

So we call for these two trees。Norge than into one big。And put this tree。

 Here is the right child of this baby。不错。That's the whole picture of what's going on。

So this a is the root， left child is the same， right child is the merge， right child plus B。嗯。

Let's go。Where A and B。But first again， we need to check and check if the tree is empty。

 so if a is empty。We're just B。IfV empty。We're just return。诶。Now both trees are not empty。

 so let's check which three have the minimum or max value of y。So if A Y is greater than By。

Then this egg will be the root of the nutrient。So what we do， we just take the right set tree of a。

 merged it the with B， and put this merged tree as the right child of a。Let write it in the one line。

 so hide it right。Will be mech。Of eight， right？Andy。Like this。It's much。喂。嗯 not the better okay。

Let's on。诶。그 좀핑。again， like here， when you merge to trees， you return as a root of the new tree。

 right？😡，嗯。気持ち？El else we have the same thing。If B is the only you。

 then you merge A and the left are three of B。嗯。That's all。

 that's the whole code of these operationss。嗯。Like I mentioned。

 this the coat of the tree is one of the simplest of all binaryse trees。こ。Let's talk about syntotics。

怒。If we believe that the expected height is logarithmic。

 let's prove that time complexity of both the separationations is linear by the height of the tree。

Not list loop here in this split operation， so we have the accuracy split operation。

 so we have this split of node and X。And here we have recursive calls and each recursive call。

Here and here。By x。In both the recursive calls， we go to one of the subaries of nodes。

 so each time we go deeper in this in the binary the research string， so if the height is locric。

 then the number of recursive codes will be login。Here we have the same thing so here we have A and B。

 and here we have two recursive calls， one recursive call， what two recursive calls。

In both a cur of course， we go deeper in one of these trees。

 so we either go deeper in the tree A or we go deeper in the tree B。

So the total height of this tree will be decreased by one so each time we go in one sub one step deeper or we go in in another sub one step deeper。

 so total time we can go deeper in this sub three is up to two logan equal we may have at most logan steps like this and at most loggan steps like this so the total total number of records of course will be up to two logan so the time complexity here results logan。

嗯，没走。🤧嗯。Now。Let's move to。Others， so let's see how to add elements or how to remove elements。哦系。嗯。

We're discussing trips。嗯。So how to add new element？😡，How to add new elements in the binary into trip。

啊，对。There are two ways， one way is easy to implement。

 but it will be a little bit slower in the real world。

 but what you can do just using these operations。You can take your。Bu the search tree。Then split it。

By x， so we have one element less than x， and here we have elements greater than x。

Then you make one small three of one element。Contains1 to x。And then you make two mech generations。是。

And you have the same three， which contains all elements of your previous three plus x。

So you' split it by x， put this x in the middle， then make mech and merge。

 and you have the whole tree contains all elements plus element x。

That's one of the simplest implementation of the additional lines， but is it is little bit。😊。

Look how how， how can you remove。So when you need to remove elements。

 you can do it in the in open direction so you have this M， you can make those splits。

Splilit by X and split。Let's say by x minus1。So you have all elements less than x then you have this x elements greater than x。

 and then you make one mergerch。Oh。So just remove this element， make me of these two trees。

I看 someone。哦。Why you can use this tree is a binary you can use any type of the binary search tree。

 we just discuss various different strategies how can you build a balanced binary search tree so tripp is one of the way to construct a balanced binary search tree。

And I just explained this because it's much easier to show how to make splittton merge operationss in the tree。

Because if you take， you can make split emerge operations in other binary research trees in thisministic binary research trees。

I'm not sure about AveL trees buts。You can do splitlits and mes and in the red black trees。

 you can do it in two freeies， in beaties。In various different trees。But it it it。

Tp is like the easiest way to explain that its possible。

 it's possible to make split in merger operations。😡。

That's why I use research only for integration purposes， basically。In real systems。

 you most probably will use something like redlect or something like that， that's true。那这个俾看。

Let me go back here so this possible you can just use the operations meta but it's。对啊。

It's a bit too slow， so you can you can make free operations instead of one。

It's easier way to make addition removal of elements。 So when you need to。

When you need to add new element， what you can do actually。Let's say no this。呃。

It's just two make the hole， so let's check if this x is the so what element will be the root of the new tree if you have to have this three and plus one element。

What element will be the root of the new tree， It will be either the root of this tree or this new element。

 so let's check。What elements have bigger value of why， So if。嗯。嗯。呢。哎喂。So some way。

I need to generate this way before I start this regression。So let's say if this。

Why is bigger than non white。Then this new node。This new node is the new root of the tree。

So we have this plus this element， so this element is the new root of the tree。

So how to add this new root to your tree， you just split your tree into two parts and put them as a children of your own。

be split。Your node by X。And just see。不 dont biteす。I need something to call this new note。嗯。Newal。

That's better。嗯。I'm not very creative， okay in name。So if this new node， but so we make this。

 so we just split。Our dream。By no new note。Yes。And just put these two surprise as the children of this new node。

Yeah。Okay。And do you not。嗯。Like before we return the new route of the train。And if not。

 we just put this。New note in one of the subies of our or if。New note。X is less than node x。我那喝水。

So then we add this new node in the left sub， just see node。Left， people through ads。Not left。

I just love one letter in the inators。You note and you note。

And else you do the same for the right chat and so。I try。

you need the same line to add new element right， so basically you can make one additional recursive function。

 which adds new element in your tree。And instead of calling three different functions。

 you shall call split then merge then merge， you would just call one function。

 it will be like three times first。Okay。Good， good enough， right？Again。

 you stop to say it everything is clearer。嗯。那。What I want to talk about？Okay。

Let's move to something something new what I want to do next。Es。Little bit， little bit different。

I want to build an out structure。Based on buying research trees。

So I want to do the following data structure， let's see。I want to do data structure。

Which maintains some lists of objects。Let's have。So the basic objects of these instructions is list of some objects。

Let's。What says you have some objects。He was。嗯。比。诶。I'm better like all this okay。C W。诶 and。

So I just name all the objects of different letters。 Okay， so we have list of some。7 objects。

And I want to do the following operationss。 First operation is to。

Combine two lists into one big list。Deper knowledge。So I have one list。Of elements。

 last and not least of elements。嗯哼。And I want to combine these two lists into one big list of elements。

Okay。What is simple。Let's scroll this list like A， A and B。So we have list A and list B。

And I want to be able to combine this two list into one big list。

And the second version is split over this。So I have one big list。Yeah。

And I want to split this list into too big into two small list。Okay。Like this。

So where to split I want to have， for example， I want to split taking the first K elements。Also。

 so let's split list a by k。 so K is the size of this first list。So I have this list A。

 I want to take first K elements of this list and put them in one list and all other elements put in the second list。

嗯，ふふふふふふ。😊，And also so I want to board the get element by the king。

So I just want to be able to pick one the element by the index。こ度ナ。那こ乐。

the separationations you want to have， you want to have。

You want to have some number of lists and you want to change the visible。

 so you want to be able to merge to list like it con continue to list into one big list。

 you want to be able to split the list in the middle and get two separate lists。

And you want to be able to get any element of these lists by its index。没错。嗯。No， let's。

 let's have another example。Let split this into。Let's plus something。The a。And something like。B。

So I have two lists okay， so when I make this mepo， I did。At least big lists。Okay。嗯哼。

Then I call something like split。By you can say five。And I have at least the lists。Oh。Okay。嗯。

So how we make both the separations using binary search trees？😡。

How are you making using binary search trees？嗯。That's simple we will maintain these lists as binary search trees that's the plan so in these binary search trees we have split and merge operations。

 so we will maintain all these lists as binary search trees and when we need to make make merge we merge these trees when we split we split these trees。

😊，But in binary research trees you need to have keys of your elements right so we'll just use the indices of of the elements as the key of the binary search tree so here we have keys like one。

 two three4 here we have elements like one2， three。嗯哼。Now。

 what happens when you need to merge two lists into one list？啊。

You only can you only can merge to trees。Then all keys of these elements are greater than all keys of these elements。

😊，嗯哼。😊，So how to make all these keys greater than all keys here。

 No you can you can use mass operationsations and lazy propagations like in segmentsries， yeah。

 so you can just make lazy operation in the root of this tree， just increase all the keys by。By four。

So you take all these keys， increase them by four。Using lazy propagation。Then you have the keys five。

 six and seven。And now all the keys in this sub in this tree are greater than all the keys in this tree。

So you call this vation。And merge these two trees into one tree。哦。And how to make split operation。

 you just split you take this binary search tree split it by the key K。

 so you take first K elements here's all elements key。Now we have here you have keys， one， two。

 three， four， five， here have six and seven。And now you make minus5 to all these keys， again。

 as as mass separation using laser propagation。And you have key one under here。

That's one of the possible ways how to implement this so again you take this some binary search tree。

 for example you can take these trips or any other binary search tree which can merge and split these trips。

啊。Then you use laser propagation to change the values of the keys。You couldn多 it。

Why not just put separation plus4 in the root of the tree and use laser propagation to change all the keys below。

あ。And now you change all these keys。You can merge these two trees into one victory because all keys here are greater than all keys here。

 so you merge these to trees using this merge operation。And get these。Mmhm。😊。

But it turns out you can do it like this， but it is overki， you can do it much， much， much much。😡。

So how to make this without all these mass separations， laser propagation and stuff。

You can implement the same operations without any keys。

 so if we know that the key of the element equal to its position in the list。

We just don't need to store all these keys because the key is always equal to the index of the element。

So we will just ignore all the keys， we'll just just ignore them。좀뚜렁뚜름뚜렁 동뚜。

The index of element is defined by its position in the tree，あのけ。How the binary search tree works。

 binary search tree contains some set of elements and these elements aresorted by the key。

Here we have some elements， but these elements sorted not by the keys， we don't have any keys。

 we are sort them by the position in this list。So what I want to build。

 I want to build the binary tree， which contains these four elements in this order。P。Well。

 for example， let's see， let's say we have elements。So let's put some。

 we still need some second key sold。So let's say， so this is key wipe。 We need some wipes。

 So let's say we have。2， five8。have1，6。啊啊。2。吐。I have two case for。

 let's make all these different just for simplicity。

You actually don't need to make all keys different all the time， but if you have a big range of ys。

 if sometimes you have equal Y key， it's not a big problem。If you have a lot of equal keys。

 that may be a problem， you have like the list of elements with the same key but。Yeah， rose off。

So now we just built the trip of these elements using these y keys。

 so let we use y key so the root of the tree is the key with maxim y， so P is the root。

The y of this is 8， so this is the y key。So in the left summary we have this white。5 here。

And here we have Q。Q has2。And in the right sub is key。You want。嗯。

That's all like this is the this tree。Describes this list。Again。

 if you look on this tree and just it all elements from left to right。

 you have element Q then y then p then K， that's exactly the order of the elements in this list。

And for the second。Three， you have this element W， Here we have element B。 here we have element A。

Yeah。6，3， and four。And this tree describes this list， sorry again， if you go from left right。

 you have W then and then B。别错。Now what happens when you want to merge these two trees， so you merge？

So。So you merge trees。Again， each tree is specified by the root of this tree。

 so you pick these two ruless and call the me operation of these two rules。So you merge P and W。

What happens when youmer trees， you look on the roots of these trees and look which tree should be there。

 which element should be the root of this big tree？嗯。YW is the road because y is bigger。

I just built the standard standard trip， so this key specifies the height of this trip or of even over not Korea why coordinate I I try to build the correct trip。

 so I just picked the element of maximal y as the root。So when I try to merge these two trees。

 I look on these two roots， just check which element must be the root of the new tree element P have bigger value y so this element must be the root of the tree so now I take this element as a root。

And now I need to merge the right sub of this element and double。そう。여게？So I have these two elements。

 this element is the root， so now I want to take these two elements， merge them。

And put the combined tree as the right child of two。So I quote Moch。From a K and double。



![](img/584d94033a656a21a9120a432ef8042a_77.png)

Now again， I welcome on these two elements， see what elements should be the root W should be the root of this。

 so I says I take this element as a root and try to combine the left child of double your endk。So I。

Okay， then the left child of W， left chart of W is not nu。

Now I want to return from this so when I to merge something and now I return this something yeah。

 so I return K from this。我个爽。啊哈。No。I take this murch tree and put it as the left child of this W here。

This key is the left child of W。And return this double as the root of this Nord tree。

And now I put this nu tree as a right out of this pe。The right child of the speed will be double。

That all。That's how we merge to trees， you actually don't need this key X when you mergese to trees。

 right？😡，So when youmer trees， you know that the structure of trees determine the border of the elements。

So you actually don't need any keys， just look on this y very to make everything balanced。

 but you don't need this key X。够。And now we have this merch tree， this merch tree explained says。

Deines this list again in this list you have elements Qd and y and P then K and W and B right right here。

😊，And how you make split operations to make these split operations， you actually need to。

To find where to split。So you need to find this position of the first five elements。

To find this position， we will precalculate the size of each tree so why is the size of this tree。

 one of this tree is two， here's one， here's one， two。For here。It7 here。

So I will precoulate for each element the size of this tree， the number of elements。Okay。

Now how to make split， so again， I call split。In the root。In P， buy the first five elements。

So I want to take this route。And split the first five elements of this rule。5。It's too easy。

Let's make it6。嗯。Yeah， still is。嗯。Let's pick by four。嗯。I want to add one more。

 let's add one more elements usually it's something here。Which letter we don't use， let's say。有。どす？

Just small个 adjustment。응응。Now you can use x as the index of the elements。

But actually you don't need to store all this excess that's what I mean in this in this data structure。

 we don't use the first key of this elements， the main key of your binary search tree。

 because the order of elements is defined not by these keys。

 but just by position of the element in this binary research stream。

So the position of the element defines its index。That's the idea。

 So we actually don't need these keys anymore。嗯，不不不不。

K positionss we use the key change after we emerge。不不不不。儿童'记的。

I explained here so when you merge trees the indices of its element will be increased by the same value。

 you can do it but you don't need to do it， you can you can just make your merge operations without any keys。

And the positions of these elements will be correct position。

 so the position of this elements will be equal to index of this element， That's what I want to do。

So I'll just I'll just， I need all these X keys and all notess， just just don't have this X keys。

 I don't need them anymore。What are you was talking about？我的我这了。啊。Yeah。

 I want to take this tree and split it by the first four elements， so I want to take this tree。

And cut first four elements of these tree， so I want to cut this Q Y P and K from this element。

 so I need to form one three of these elements and another three of these four elements。

I to split it here。维货。看看哼。That's the gl。啊。Just。Just small fix。So I take this list， split it here。

 and make these two lists。Let me adjust the sizes， so this is one now， this is two。This is5。

 This is8。嗯。Next。Let's use this。So I start from the root and I want to cut first four elements of this trim。

Let's look on this route， let's see in which part of this splited list will be this root element。

 so how to see where we will build root element。So this root element will be after first two elements。

 so we have two elements in the left sub3， then we have our root。

 so our root have index equal to3 so we have first two elements here so index of these element is free。

Okay。And I want to cut first four elements。So this P should belong to the left part of this split stream。

So I take take this P， put it in the left part。And them。I need to cut this W。Into two halves。

 such that first half contains one more element。So以。

I want to split this tree taking the first four elements。

 so I take this whole left substrate two elements here。Plus these elements free elements。

 so I need one more element from the right sub， so I go to the right sub and try to cut first one element from this sub。

From here， I call split。Of W cuts in the first element of this。And go here。

 try to cut one element from this tree。How to cut one element from this tree。

 let's look look on the index of the first element index of this W will be again2 plus one。

 it will be free。So this w should belong to the right three。嗯哼。So I put this to the right tree。

And then go to the left sub and try to codecut one element from this left sub。From here， I go to。

And try to cut one element from this left subject。嗯哼。Now again。

 I look on the position of K has index1。Because left substrate is empty， so case in index 1。

 so when I need to cut one element， I just take this key。And cut zero elements from M。

You can just shoot on this left sub， but I will just。For simplicity， I will call。

I will hold it like this。嗯哼。😊，No now it's simple， you just from here you just return。

You return two trees， first tree is empty。Second trick contains camp。Now again， for this K。

 do we need to take first element K。Take this now as the right subre。そ。

So the right sub of k is now this now。And return these two trees as a result。

So from here you return left up is K， right s is M。嗯哼。😊，Again， you'll have at least K and M。

You try to split it， taking the first one element， so now you have one this contains K another contains M。

That's what youre do this one is the second list。Now you go back here back here， so you take this W。

Connect the right subre as the left sub of this W。So you connect this M and the left substrate to this W。

Instead of key。Mmhm。😊，And now you have two subies， first sub is this key。

And second factor is this this W。So this k contains the first element。

 I need to cut first first element from this sub， so I take this sub3 k and this sub w。

 this contains one element， this contains all other elements。中。呃KNW。

And now I connect this K as the left child of P， right child of P。Okay。this。你得错。Now again in this P。

 I had three elements， I cut one element from this subre put it as a right shell。

 so now in this tree I have four elements that's what I want I want to cut four elements from this。P。

 so now I take these free elements plus this one， so now I have four elements here。

So let's all so now in the end， I have。This tree contains the left part of this list。

 this tree contains the right part of this list。嗯。Makes sense。That's all。And now when you。

 when you have structure like this， you can perform some。Strange operation of the list， sorry。

 what you can do， what you can do。For example， you have some list。We have some list of elements。

You can split it here， split it here， make this free list， so first list， second list。

 the third list， then take this third list， put it in the end。What's aBC。

And merge them in different order so you can take all elements in A， then elements in C。

 and then in the end take all elements in D。So you can cut some segment of your elements。

And merged in the end of the same。take it from here， merge this A and C and merge the result of B。

This segment will be moved to the end of your array。

And you can do all the operationss in loggan time， so each of these operationss works in login time。

 so you make these two splits plus one me or two two merges。

And so can you can make some segment operationss， again， like light。Like before。

 when you have segment3， you can perform any segment operation like in segment3 so you can。

rearrange all these elements and then calculate some on some segment or rear some elements and。

Add something to the whole segment and so on。 so。 You can make all the sames like in binary like in segment trees。

 but also， you can rearrange the elements using these splits and merges。感燥。看 this方。

Should we talk about persistent infrastructure structures？Let's just mention that you can do it。

All these separationations using persistent trees。And actually with trips it's very easy so if you use if you need some persistent trips。

 you just make all the same procedures， the code will be the same。

 but every time instead of changing something in the elements。

 you just create the new version of this element。嗯。Go for that， let's mic。

Just remove everything not necessary。So。For example。

 you have this list and you want to insert another element here so you want here you want before this K。

 you want to insert another element， let's see B。So you want this B before this K。So what you do。

 you want to connect this B as the left child of k， but you don't want to change this case。

 so you just copy this K to another node。And make this be the left child of this new node。

And now you want to connect this gate as the right chart of pin， so you just copy this pin。

Put it as the right chart of this new copy。And connect with this left chair with led。

And now you have two versions， this is version one without B， this is version two with this B。

And so on so it's very simple to change all the code I I was era it。

 but you can do it by yourself every time you need to change something in your。

In your node to change some of the children to change the value and so on， we just copy your node。

And return this copy as a result of your function。Very， very simple。

 And you can do it all the operationss in。嗯。P为。嗯。And want to talk about problems with persistent trees。

Maybe we will discuss them in the next。本ータす。But。Sometimes you need something like this。

 it's not very often。Sometimes you， you do。Any more questions？That's basically all I tried to is to。

🎼The。🎼Yeah。🎼。