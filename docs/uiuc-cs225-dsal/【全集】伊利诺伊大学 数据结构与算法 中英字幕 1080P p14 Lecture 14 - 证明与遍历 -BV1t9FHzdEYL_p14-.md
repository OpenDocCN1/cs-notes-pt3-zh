# 【全集】伊利诺伊大学 数据结构与算法 中英字幕 1080P p14 Lecture 14 - 证明与遍历 -BV1t9FHzdEYL_p14-

Okay， today we're going to continue with trees。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_1.png)

Andm。And we're going to start with what I tried to jam in at the very end， on Friday。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_3.png)

Which is that。Trees are really similar to what we've been doing with lists。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_5.png)

But we're going to do a lot more with trees。 In fact， we're going to spend most of this month。

 I think。Working on trees， maybe even a little bit more。嗯。I havenn't looked at the full schedule。But。

In hardware， what's going to be going on with trees is this picture， right？ So we have。Root。嗯。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_7.png)

Root。The picture here， right shows the actual layout of tree nodes existing with a left and a right and data。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_9.png)

Which are pointers to tree nodes。And it it gets a little bit messy。

 but that's actually what's going on in memory。 When I talk about and reason about trees。

 what I'm going to tend to do is write the tree on the left。 And， in fact。

 as we add more and more data to trees， I'm only going to note the parts we care about in that particular discussion。

 So right here is the same tree on the left。But written in a much easier to visualize manner。So。

 okay。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_11.png)

But there's one thing that bothers a lot of people in my experience that if I say trees are like linked lists and you were telling me if I had something like C。

 S。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_13.png)

A one。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_15.png)

2，2，5， x。Stored in a linked list， right， And I said it was a linked list。Or an array。

 There isn't that much space used， whereasas， right， if this was a linked list。

There wouldn't be that much space that was sort of extra or wasteful。But here， man。

 we've got all of these null pointers。All of them。Whereas in a linked list， we would have had one。So。

We're going to do a proof today。To show how many null pointers you get in any binary tree。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_17.png)

Okay。So。Our theorem is that we want to say is that if there are n data items in our representation of a binary tree。

 that there are how many null pointers do you think？



![](img/e27caf7ee56efecf116f85e5d9af8ac3_19.png)

What's your guess。Let's go back and look at this。 Let's see。 we had 1，2，3，4，5，6，7，8 items。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_21.png)

And we have one，2，3，4，5，6，7，8，9，9。 So the n plus one seems to work okay。N squared。

 N squared would be pretty bad。2 to the N plus one，oo。I got。End the end factorial。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_23.png)

Okay， we could do a Big O， but we're going to do a precise count here。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_25.png)

We're going to try， and we're going to claim that it's going to be n plus 1。

 At least our one example seem to be n plus one。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_27.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_28.png)

So。We're going to say that we want to prove the following。Let。The following function nulls。Of Anne。

Bi。The number。Of no pointers。In a tree。It's actually say binary。Ci。With。And nodes。Okay。

So does this seem to work。 Let， let's mu around with us a little bit more。

 Let's see if we had a tree with one node， it has two nullles， right。

Now I'm going to stop stop bothering to draw the root most of the time。 One note it has twonollles。

What about， what if I draw a really weird tree。Right。So there's one， two， three， four，5 okay。Yes。

 how are we going to prove this， We're going to prove it inductively。

 but I wanted to do a little bit of scratching around to try and show that this seemed。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_30.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_31.png)

Reasonable， and in fact， a lot of the time that's what you do is that you will start with first。

Working through an idea very loosely to try and get an idea， try and understand the problem。

 And then you try to formalize it。 And that happens with code， too， right。

 you' you'll come up with the way you want your program to work and you'll describe it very loosely。

 But then when you have to go to code， you have to change from loose to very precise。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_33.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_34.png)

Well， we want to prove it for all， so I agree we're going to do induction and what's the first thing we do with induction？

We need base cases。So how about how many null pointers are there in a tree with zero nodes？One， yeah。

 right？A tree with zero nodes。Is root。So this holds for a tree with zero nodes。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_36.png)

Yeah， these nonexistent trees are really weird， but they actually make a lot of the things we're going to do in this class。

 a lot cleaner as long as we always talk about these nonexistent trees。 So a tree was0。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_38.png)

Nodes is。And then also， we can say that n plus1 is。Wen。4 n equals0。Okay。And equals one。 Well。

 that was pretty easy， right？ And，0 nodes is an empty tree。 It still has a root pointer。

 So our data structure with0 nodes， that is a tree。 If that data structure exists。

 it's using one pointer to tell you， hey， there's nothing in me。Our tree with one node。

That's all the trees that there can be with one nodes， right？And then one plus  one equals 2。Check。

How about a tree with two nodes， Can we draw all the trees with two nodes， all the binary trees。

 Let's see。 I think I've got this thing。And that thing。That's all the binary trees， right？

That have only two nodes。So I can still exhaustively do this。And I get three。

These checkings are easy。Okay。We're going to do one more。

And we're going to do one more partially to try and think about what structure looks like because the next thing we're going to have to do is is we're going to have to write our inductive hypothesis。

 and then we're going to have to actually do our induction。 And to do our induction。

 we need to really reason about the structure of the that we're working with here， right？

 So with nulls of3 and equals 3。 Well，3 plus 1 equals4 is easy。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_40.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_41.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_42.png)

But。The lower， okay。Let's try and draw all the trees with three nodes。Let's see。Here's one。

Anyone have a suggestion for another tree with three nodes？All left。 Okay。

 we can have the all left tree。like that。C its see。 Okay， we。And we had the all right tree before。

 I believe， so we can draw that over here。Okay， those then left， right， right left， right。

 so we've gotten more。You have left right。And。Right left。Let's see we've got one to。3，4。1，2，3，4。

 okay。So。Okay， I think we've got them all now， right all the way left。Left， right。Balanced， right。

 left and all the way right。So this is left left。Le， right。Right， left。Right， right， and balanced。So。

I think this is all the binary trees that exist with three nodes。And they all have four。

 so our base case works。But we really didn't need this deeper a base case， but it was helpful to。

Reason about it。Is there any theorem about how many trees are possible， I'm sure there is。

It's an interesting question。哦。We'd have to inductively prove how to prove the number of different trees at every size。

 but here are all the trees with three nodes。Right， but it。Okay。Um。

So what is the same between all these trees？Not much is there。But， there is one thing。

That all of these trees。Have a root。The number of null pointers， the number of nodes， those are true。

 but the structure that we want to work on。Is that。All of these trees have a root。

And then they have two sub trees， don't they。Because remember， we talk about。Empty trees。

So all of these trees can be thought of as a root。With two subtes。

And I realized some of these subtes。Are funny。But。All of these trees have a root。With two subries。

 Now， could we do this。In a that we are adding one node， this one we might be able to。

 but you're going to find that when dealing with a structure。U。

That you don't want to do induction by adding to the end that that's going to often be really。

 really hard to show what's going on。 and you're going to find that with trees and with graphs。

 we almost always want to take the structure and break it down into smaller structures。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_44.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_45.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_46.png)

So if we look at this， right， we have a root。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_48.png)

With。Two subt in every case here。 And that's a really nice， clean structure。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_50.png)

And what can we say about those subtes？Well。Because we've removed the root。No matter what。

 all of those subtes are smaller than than the。The total tree， right？So。Hong。Are smaller。ELess nodes。

Then。The full tree。Okay。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_52.png)

They have two subtes， but will note that some of the subtes have no nodes in them， right。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_54.png)

Right， yes， and we can use0， one or two for them。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_56.png)

Okay， so let's write our inductive hypothesis now， because I think we have conformulated is we're going to want to say that suppose。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_58.png)

noles。Of n equals。N plus 1。For all。And less than k。And again， in this case。

We could think about this in a different way。But I want to show you the technique that we're going to use to prove lots and lots of properties about tea trees and graphs。

 So this particular proof is on a very simple property。

 So we could approach it a different way and get a clean proof as the properties get more complicated。

 It is much harder to get it right。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_60.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_61.png)

So， but do we all agree。That suppose nullles of n is equal to n plus1 for all0 n less than k greater than or equal to 0。

So now let's try to write our。Induction。So now we want to consider an arbitrary treat T。With K nodes。

So we have some tree T that has K nodes。I waited for a little bit， I would take more questions。

But treaty。Hows knots， okay。So， I'm going to draw。Treat T is this。It has a root。Plus。Two subtes。Okay。

Since it has k nodes。I want to express how many nodes are in each subte。So first。

 let's pick a letter。 somebodybody give me any letter。A， okay。M M was in first， So wins。

 So we're going to say that there are。M nodes。In left subre。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_63.png)

Okay。And we're just choosing that。 We haven't said how many we haven't constrained M in any way。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_65.png)

U but it's a real number of nodes， so it's zero to u k minus1， right？



![](img/e27caf7ee56efecf116f85e5d9af8ac3_67.png)

Okay。How many nodes are in the right subte？K minus M。 is that right？It's very close。-1， yeah。Subchi。

Yeah， because we have a root。Okay。So。We have M in the left and K minus M minus1 in the right。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_69.png)

Okay。So let's now use our inductive hypothesis， and we can say that。Om。Total。Noles。Equals。Noles。Of。M。

Plus。Noles。Of K minus M-1。Does everyone agree with that？

So there are a couple of tricky pieces here to make this true。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_71.png)

First of all， we have to accept that the root has no nullles， right， because。

We've already taken care of the zero and one cases。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_73.png)

And if the right sub tree， for example， is empty。 So or let's do the left subre because it's a little bit easier to word if the left subre is empty。

 if M equals 0。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_75.png)

The null to the left of the root pointer is charged to that subre。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_77.png)

That's why I kind of tried to draw that these were going into the tree because we're。

 we're charging the tree。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_79.png)

For the pointer。Okay。So then we imply inductive hypothesis and we get M plus1。And we get。K M-1 plus1。

And let's see the M cancels the M， the plus1 cancels that， and we get K plus1。W。And we're done。So。

What's important to see in this is both to refresh thinking about induction。

And to think about induction in this context of a data structure。Yeah。

 you're going to find that with a data structure， it is almost always going to be better to be doing induction by breaking it down into smaller data structures and there's a nice thing to mirror this is that method of taking a large complicated data structure and breaking it down into smaller structures is exactly what induction does I sorry what recursion does。

😡。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_81.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_82.png)

Right， so this is exactly the same structure。 How do I get M plus1 and K minus M minus1 plus1， Well。

 nullles of M， right is。呃。By inductive hypothesis， one you'd have。Our inductive hypothesis was nules。

Of。And equals nullles。Are equals。N plus 1 for。おお。And less than k。Righti。

So we used our structure to label how many nodes there are。Okay。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_84.png)

And we're going to find that algorithmically this technique is very useful in showing the running time of algorithms。

 that algorithmically this technique is very useful in figuring out how to construct algorithms that have guaranteed properties and that proving constants of our data structures。

 proving that our data structures hold properties is essentially going to be that same structure whereby doing this recursively。

😡。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_86.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_87.png)

How many base cases did we explicitly need， You need here0 and one。

Do we have any proofs on the exams， We will not have any full proofs。

 but we may have things that ask you to use techniques from the proofs or use ideas from the proofs。

Would zero be enough as a base case， the problem is。With 0。嗯。Think about this。Yeah。

 I guess actually zero is enough here， and of course it should be。Yep。0 is really all you need。

 I would always choose to write it as0 and one because it's a little bit cleaner。

 but0 correctly handles the one case， as you say that R is。V。Using the structure， not the base case。

So R comes from the structure of the tree。And we would prove one then by zero and zero。So M is zero。

K minus M minus1 is also zero。啊。Exam one will cover through last Friday。

 it will not cover this material。the practice exam is out。So。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_89.png)

For the induction hypothesis， let's go back to here what is n represent and what is K represents。

 Well， they're both just variables， right and。We have produced is a K is a variable that has no fixed value。

 but is bounding n。Right。They're both variables。And we are bounding。With K。So's right。

So instead of if we just said this was true for everything。It would not work。

But we need to say it's true for well， at least some number of things。

 And the number of things is when we sort of start。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_91.png)

Zi。Base cases， but as。We are proving larger and larger examples， we are saying K changes。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_93.png)

Can we say K -1 has k null pointers， no。We have nothing that's we can say that。K-1。

 a tree with K-1 nodes has。K null pointers。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_95.png)

But。How are you going to take it off？If you， if you think about your big tree， how do you remove？



![](img/e27caf7ee56efecf116f85e5d9af8ac3_97.png)

So with small trees， it's easy to aman it。 imagine what you mean by removing it， right？



![](img/e27caf7ee56efecf116f85e5d9af8ac3_99.png)

But you have to show that I can always remove this thing。

So what's happening here is I'm breaking my tree down into。3 parts。

And I'm showing that these parts are always removing。V。If I was trying to guarantee I remove a node。

 there has to be a node to remove。 what node am I removing？😡，And how do I know I get back？



![](img/e27caf7ee56efecf116f85e5d9af8ac3_101.png)

You really need to have a way that this， this description that I wrote here， this part here。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_103.png)

Right。Correctly describes any tree， no matter what K is， right。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_105.png)

But to describe removing a node at the bottom somewhere or in the middle。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_107.png)

What does it removing a node in the middle mean is unclear。 It's okay。 And。

 and let me be clear that particular construction。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_109.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_110.png)

Part of why I'm stressing on this so much is that。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_112.png)

It's really tempting often to write that construction where you kind of remove a node。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_114.png)

But。Here， this construction。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_116.png)

Works on basically every tree proof you'll ever exit you'll ever encounter of what do I do with the tree。

 I remove the root， and then I have two， or in a Krie tree， K trees。

 and that I can construct how things work that way。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_118.png)

And the other thing I want to say is what we see nicely here。In a sense。

 is the fact that we're talking about zero trees so that we， in this class。

 talk about trees that have zero nodes as being trees。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_120.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_121.png)

Is a very clean way for this proof to work。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_123.png)

Okay。So that's the refresher of sort of how proofs go in recursive proofs。

 inductive proofs on recursive types of data structures。

 and you're going to see that almost everything we do from now is going to be a recursively defined data structure in some way or form and that we are going to want to prove various properties to guarantee runtime。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_125.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_126.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_127.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_128.png)

And we're going to be doing this inductively。All the time。Okay。So。With that out of the way。

 I want to start talking about how do we traverse One of the things I described in the ADT for a tree was a traversal。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_130.png)

And in a list， a traversal of a list is really straightforward， right。

 you get the first thing in the list or the zero thing depending then the first and the second and the third and until you get to the end of the list。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_132.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_133.png)

You're all writing this。 and hopefully most of you have written the iterator because it's quite easy part to get done for going forwards。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_135.png)

And going backwards。In MP list。But。How do you think we should traverse。A tree。

If I want to visit everything in the tree。How do I do that。Any suggestions？Left to right。

 So like this would be here and then。Do I choose up there or down here or？



![](img/e27caf7ee56efecf116f85e5d9af8ac3_137.png)

Check every note on a specific level。 That is absolutely one， but let's， let's。

 let's do a recursive version here。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_139.png)

We got a lot of different choices。 So see， unlike a linked list。

There are lots of different ways we can visit a tree。

And let' let's choose what to me is probably the simplest。And the simplest one I'm going to say is。

 well， we started the route。And we'll start by。Om。Observing the first thing。

 And we're just going to talk about let me yell or print。 And so I'm going to do it。

 So we're going to start by visiting the first thing。So we're going to go plot。

And then I like this left。Go left， go right idea， right so。

I'm now going to having to traverse this tree。I'm going to visit the root。

 and then I'm going to traverse the left subte and then traverse the right subree。 So visit。Root。

Traverse。Weft。Tverse。Right。Okay。There's my nice recursive function， so traverse。Root。

Works as visit the root， traverse the left， traverse the right。Okay， so doing that， we've got a plus。

We visited this guy。Then we do a minus。And we recurse。And we do an a。And we recurse and。

 what do we do？If not， no。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_141.png)

So we don't do anything if the root is not null。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_143.png)

If the root is null， so then we recurse left， we recurse right。We recurse up。 We recurse up。At minus。

 we recurse， right。So we now visit here。laughed。Vis it here， get B。Left， right， doing nothing。

 recur up， recur down， get C。Recur down。 Get star。Recurse down， get D， left， right， left right。

 already got done。 recurse up， get E。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_145.png)

Left， right and recurse up， recurse up， then we're done。Well， we did that， right。

 I guess not in this。 So let'。So we are explicitly visiting the nulls， right， We visit the null。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_147.png)

And then go。 So we are recruit we。The way we wrote this particular version of the recursion。

 we recur into the null。 So let's if I put， say， A E， we'll put。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_149.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_150.png)

F down here。We do E， we check there， we recur down to F， we visit F， we check there， we check there。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_152.png)

Right。So now we have one is not null， but it still works， right， because traverse the root。

 we visit the root if it's not null， which was the plus， then traverse the left。Then visit the root。

 Its not dull。 Traverse the left。So we go， chunk， chunk。Chongcheng。Cheng。Cheng。Cheng。Chun。Cheng。😔。

Right。There is our  one，2，3，4，5。six。7，8，9。10。11，12， sorry，12。13，14。15 stas of of it。

Is there a difference between a null and a null pointer in C++ there is right now we're just talking about a theoretical idea here。

 this is not an implementation， the implementation will be in C++ but right mean？

It's a null of some sort。It's a nothing。So， okay， so we're going to call this a preor。Tversal。Okay。

And speaking of C+ plus， let's try and actually write this。 So we want to do traversal。

 and we will have our pre order traversal。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_154.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_155.png)

We're getting past the a trino pointer current。Let's see。 how do we write this。So right。

 we are going to for yelling， we're going to print。Xia out。Let's do。Was datato。So， that's how we。

Visit a node。 We print it， right， and which means we act on the data in some way。Okay。

 and then we do。P order。Weft。Pre order。K。Right。Is that it， are we all good？If not null， Okay。

 so let's see。 how can I write that if。There's our base case， now。

Anyone have a problem with how I wrote this？Some people like it。

what's going on and this is a very standard way for CNC++ programmers to write something like this。

 but it's also a little confusing。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_157.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_158.png)

That's right。 Ke might be null。Well， what do we do if cur is null， it is 0 and 0 is false。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_160.png)

Remember。No。Pointer and null is equal equal to 0， and。0 is。False。So。

I'm not arguing that this is the best way to write it。But this is a very standard way to write。

What you probably wanted to see， which was。Right。The base case。Do nothing。It returns。

You fall off the bottom of a function you return， right？Returning void， so I could write return。

A return statement that returns nothing。 but when you， when you leave the end of a function。

 you return to the calling function。So。Right。How do we come back up well here？It goes down the left。

 down the right， and then it hits here。Right。Not cur would be。0 is false， So if。Perrr is true。

And I guess， and not zero。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_162.png)

It's just outting into the council， I mean， you could do other things in a sense， right？



![](img/e27caf7ee56efecf116f85e5d9af8ac3_164.png)

What I really want to do is pass in some function here。 And I would do some， some amount of work。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_166.png)

Is not0， yes。So not0 is true， and0 is false。All of this stuff happens to be true in both C and C plus plus。

 It's really not a good thing that it's true， but it is a fact that people depend on in writing a lot of code。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_168.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_169.png)

Right， so if cur and if K not equals null pointer are exactly the same statement。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_171.png)

Assuming Ke is a pointer。And again， I pointed out the if K formulation because。

Many long term programmers will write it that way。Would the code inside。

 if not Ker only run if Ker was null。Yes， I believe so， but I've never seen people write it that way。

That is to say， if you want it in the case when it is， nu， I see people do it the other way。Yeah。

 theelts。Does nothing。This whole piece。Is completely optional。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_173.png)

I just thought it was showing it so it was a little bit clearer for people that were confused about what was happening。

 that were asking what the base case was and the base case existed even if I didn't write else and the base case is do nothing I'm at a null。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_175.png)

And if I was writing it， I would not have written the else。If Ke。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_177.png)

So the trick is that if treats any numeric result as a boolean and evaluates it that if the value is 0。

 it is false and if the value is true， it is。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_179.png)

嗯。If the value is not0， it is true。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_181.png)

It recurs up here。 So if I am at the base， I do nothing。

 and I return here when I fall off the end of the function。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_183.png)

So， I return。Either here。Or here， right？When I end this function， so I call this function。

 which calls this function， which calls this function， which calls this function。

 which calls this function。Well， I return， I returned to where I was。 If I was on the left。

 I returned here and then execute the right。If I was on the right， I。Go out and return again。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_185.png)

The complexity in the runtime are the same for the recursive versus iterative here。

 there is a slight space complexity that exists in the recursive form that could be gotten rid of in an iterative version。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_187.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_188.png)

It's not really important in most cases， with a tree。

And Te code is so much easier to write recursively， that's what we're going to expect you to do。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_190.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_191.png)

So we will not be penalizing you for recursive versions of tree calls。

Traversals will not be on this current exam。So what is the complexity of this？

So that's a good question。What is the total complexity of this？Nowao。

I could force you to do a fully inductive proof。That。Right， this is。

Going to have a complexity of one plus。The complexity of the left recursion and the right recursion。

 but I'm going to short circuit and say。It's going to have a complexity of an。So it's big Ovan。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_193.png)

Right and it's big O of N because as I do this recursion。

I will call this line the sea out once on every single node and not more than once， right。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_195.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_196.png)

I never return to a node。 I return to the code at a node， but not to the node itself。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_198.png)

It's also the minimum。In this case， the complexity is hard， it's also big omega。

 so we have a strict upper and lower bound。 the running time is exactly linear。So。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_200.png)

The most time it'll take is N， and the minimum time it'll take is N。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_202.png)

Can we pass a function on notess this traveral to do operations on each node， not as I wrote it。

 but absolutely you could use a function pointer or use a funor and have that operation happen on each node。

 absolutely。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_204.png)

And but in C+ plus what we're more likely to do is to write a。

YouFctors in C++ are not the same thing as they are in Haskell。

 they're ugly and clgy and we don't really do them， but they do exist。

Haskell funcctortors are much nicer C plus plus funtors R。

 you can create a class that overloads the parenthesis operator and that's a function So yeah。



![](img/e27caf7ee56efecf116f85e5d9af8ac3_206.png)

![](img/e27caf7ee56efecf116f85e5d9af8ac3_207.png)

Functors are similar to lambmbda does and lambmbda does。

 while their syntax and C++ as ugly are much closer to what you get with funcctors in。Haskell。

 but I'm letting myself get off the track。 This is all I'm doing for today。

 I'll answer questions more as we go。 But that's it。 I'll stick around and take questions。

But that's it for today。

![](img/e27caf7ee56efecf116f85e5d9af8ac3_209.png)