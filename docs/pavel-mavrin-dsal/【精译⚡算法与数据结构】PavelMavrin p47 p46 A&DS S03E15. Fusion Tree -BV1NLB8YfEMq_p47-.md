# 【精译⚡算法与数据结构】PavelMavrin p47 p46 A&DS S03E15. Fusion Tree -BV1NLB8YfEMq_p47-

🎼。

![](img/b1dc2a2d2e3220a9182fbad554ec5cf7_1.png)

🎼So today's the final lecture of this semester。 we will continue to talk about integer data structures Last week we talk about them about why fast tries。

And today， will。Discuss an another data structure， which makes the same thing。

 but has a different time complexity。 We'll talk about fusion trees。So what is the fusion tree。

 Fusion tree is another data structure， which used for。

For integers and actually do the same thing as a binary search tree。 So again。

 we have a set of integers and we want to make operations like insert integer。

Or it could remove wind the。And okay， let's do like last week， well make a。Copation， lower bound。

So again， it's like in C plus plus lower bound in sets。

 So you need to find the closest integer to this x。 so it will find the。

Minimal y is such that y is greater equal x。Mmhm。😊，And last week again。

 let's repeat last week we discussed the structure called Wifa trees and these whiteface trees。

Make all separationations and then complexity is。Why first。Right。So in my first try。

 we make all this operation in。로려。Also， you can use binary search trees if you use just regular binary search trees。

You can make all these operationss and then relax will be logan。So when W is less than n， actually。

More efficient to use。Why first tries or or maybe violentom the trees。 We we。

 we didn't discuss one in the trees， but the has and complexity。

 So you may use violentol the trees or white first price if your W is small。And again。

 w is the size of the words in your computational model。 So in your computational model。

 you work with integers and the size of this integer。一だ。Yeah。I just repeated。

 We discussed it last week。Today we discuss one more data structure， it has all the same variations。

 but different time complexity time complexity of the data structure we'll discuss today。

Will be something like not exactly but close to W of M。So what's interesting about this。

 The interesting about this is that in。Why first tries or in bottom the both trees。

 the complexity actually increasing when you increase the size of the work。 So if you。

 if you make longer integers， the tank complexity is increasing。 Okay， because this。

Lob double is increasingly。Here the time complexity is actually decreasing。

 so if you have bigger integers， your data structure actually works faster。Thats kind of interesting。

And white。Why can't be possible， Why can' we get a fast structure when we increase the size of the integer。

 It's basically because we allow to make all the magic operations in constant time。

 So we have these long integers and we allow to make all operations in constant time。

All operationss like。You， you can make some。 You can make multiplication。 So， so all。

 all the standard arithmetic operations work in constant time。 Again， the most。

A strange thing is that we can multiply it just some constant time。 So we。

 we will allow to calculate the multiplication of two。Long integers in constant time， this actually。

This is a big assumption that we can multiply to long injus in constant time。

 We still don't know how to do it， so we don't know how to build the long integers。

With fast applicationplication。 But we if we allow to make them。

 usually when you think about real model， you think of you assume that you can multiply integers in constant time and these data structuress are all about this so so if you assume that you can make arithmetic operations in constant time then you can make these operations and again。

 if if you multiply long integers in constant time。

 you kind of make a lot of things that in constant time。 So if you make long integer。

 then you multiply you make many small operations in a single operation so you multiply all pairs of widths in constant time and if you have longer integer。

 you。Bigger number of operations performing constant time， so。

Actually this is why this tank complexity will be decreasing。

So we have like more parallelism in this when you increase the size of the world。

 you will have more parallel operations， so dplex will be decreasing， that's the idea。Okay케。啊。Okay。

 let's go。So what's idea。The idea is to make a search string， but not binary the search string。

 but something like this so。So we'll make a search tree， but in this search tree。

 we make will make not two children， but many children。こ's。In each note。

 let's have each you like liking bittering， right。That说。Al。So everyold has exactly bi。

 not exactly biot you can so if you want to make。If you want to make insertions and removals from this tree。

 you actually need to have some gap between minimal and small material。 What does matter。

Well actually， what you what you need to do is make a be tree。We discussed Beatri last year。

it's not that interesting， so it's not lecture for today。

 but you need to make a B tree so you need to make a tree when each node has about B children so in B3 you has some gap you have so the number of children is between like B over four to B so you can balance this stream not important today。

Let let's say that each node has be children。Now， we need to find the value of B。

 So the height of this tree is。So I want the height of this tree， B big O of log w of L。

So what value of B should I pick。Any ideas？Again， if you。If it's your first time here。

 you need to say something in the chat at least every minute。Okay。So I am understand send you here。

 you understand what's going on and so on。So， so B is like a branching factor。 So with in each note。

 we have B branches。I want to pick a value of B such that the height of this tree is big go of logo base W of N。

Yes， every minute， just say something。If you don't know what to say， just see something。

If I'm asking a question， better to try to guess the answer。嗯。Okay。Again， B is a branch factor。 Yeah。

 each note has be children。So if each node has a big children， what will be the height of this tree？

The height of this stream will obviously be。Log and。Basby， right。

And I want to pick a value of B such that this height is actually a big O of。Log and base W。

So the question is， what is the be。老得还会去。Any ideas？而伟。Just say something。

B equal to W is good to correct， okay。Bal to W will will obviously give you this complexity， but。

Unfortunately， unfortunately， it's not possible to no， it's possible。

 but not exactly to be trip with this branch infection。So I。

 I need to make a small branching factor and logo。으 저 저 저 저 저 좀。Yeah。

 it's actually also works like and power log WN is the same thing。Yes， so sorry。

 I saw I need to I need B2 B N power length。 So， but if you put end in the power of lock。

 it will give you w。아 너 너도 그렇게 시작해。だの。No， I can like this back。那怎不说啊。Yeah。So B equal W is。

Will be good， but， but， but unfortunately， we will not be able to make this。Large great in factor。

So we will actually build more that branch factor on。 The branching factor will be double euro。

 So if you pick。B is。W any power。You will still have this time complexity， because。Log B M will be。

아ああ。Log in over。Log B， right。So if E B is W power N， then this is log。And this is alpha log W。

 so it's1 over alpha log Wn， right？So， so you can pick for B， not W， but W in any。In any power。

 it it will work。And in our solution， we will pick B as。It's whether alert will make P。

 W and power 1 over 5。Mhhum。So the branch infected would not be double。

But it will be big enough to make the height of the tree big O of lower in best W。あ。

Let's's stop here for a moment so why this structure is not very practical because let's see if we want to make branching vector。

 for example， let's here， if the branching factor is， for example four， if it's less than four。

 we can implement it without all the stuff yeah， so to make this structure at least somewhat。

Effective， we need to have branching effect this for。 If your branch factor is2。

 you can make a binary treasury， right。So if branch factory is at least 4。Then。

Double you should be like，4 power 5。 So it's hundred24。So， so we need 1024 beat integers。

To make branch in factory4。So even this。Even the slightest step to make this structure effective is only possible when you have these huge integers so the size of again W is the size in bits of all the integers。

嗯哼。😊，Like in modern processors， we have like4 64 bits integers or 1，28 bit integers。We don't have。

 usually the machines with。다 우승 다。24 beat integers。Yep， so it's kind of hard to implement。

But to make this structure work， we actually need to to， to have the integers of size。

 at least 1224 Bs。If you want to make this structure even more effective， for example。

 if you want to have a branch in factor of them。So。So's that's something。

 that's something interesting， right， So if you have two children or four children。

 that's not a big deal。 but if you have 10 children， that may be something interesting。

 but if you won't have branch in factor 10， then the size of the integers should be。1 power five。

Sorry， you need to have hundred000 bits in each of your integers。

 We don't know how to make such big integers and still have multiplication constant time。そう。

Not for the practical data structure， but in theory， it's cool， right？So again， in theory。

 all these data structures are about what to do do I think you have big interest？So。

 so if at some point， we will manage。To build the machine which has very big integers and it can calculate all the arithmetic operations in constant time。

 then we can do very cool stuff。Okay。Okay。What's the idea？Again， we will pick this branching factor。

And in each note， we'll have big children。So how to have big children in this search tree。

 in binary search tree and the binary search tree， you have a single key， again。

 what happens in binary search tree， you have a KX。Here you have all elements less than x。

 Here you have element greater than x， right？That's how binary works。If you have big children。

For example， if you have let's say you have four children。so 그。And has four children。嗯。

You need to split all this segment of possible integers into four segments， right。

So here you have all elements less than x1 here greater than x1。

 but less than x2 here greater than x2， but less than x3。And here have a great as X。

So you need three keys here。 So you need in each node， you have three keys。

And when you step into this note。You need to again。 what happens， You find the lower bound of x。

So you move to this note in your cache let's how it's the same like in binary the research tree but now you have B children instead of two children so you have value x and you need to find out in which of these subrises the value x should belong here。

So。What do we need to do。You need to find the segment which contains your value X。Right。

For how you do it， you， you basically need to make a lower bound in in this set of integers。Mmhm。😊。

So you have this set of keys inside your node。And you need to calculate lower bound for this incoming value x。

 Yeah， So you have this value X。 You calculate lower bound of these elements。For the value x。

And then you find out which segment actually contained your element X。Then you go to this sub。

 and so on。So again， you start from the rule。With some value X。You want to replace lower bound。

So you， you have big children。 You need to find out which child actually contains value X。

So you could create a lower bound of of the keys inside this note。 select one of the children。

 Now go here。Again， you have big children。 You need to select one of the one of the children and go to this sub。

So you again， you calculate lower bound inside this node。

 select one of the children and go to this node and。

 so each time you have big children and you need to select one of them and to go there in your recursory。

嗯哼。So now the only thing you need to make is to calculate lower bound in this small set of be。

So now the problem we're solving is the following。We have。The note inside the note， we have B keys。

So x1， x2， and so on， X B。Actually， be -1， but does' matter also plus -1。

I will limit all the customs unless， right。So we have note in in the note， we have B keys。

And we need to calculate lower bound for income value x。Inside this note。 So we will。

When we calculate lower bound inside the note， we'll select one of the children， then go there。

And do the same thing recursively。So the depth of this diion will be the height of the tree。

 the height of this tree is long basically。嗯哼。So now we'll solve the whole problem。We have B values。

And we need to calculate lower bound inside these B various in constant time。

 if we will manage to do it in constant time， then each time we go to some note。

 we calculate the lower bound in constant time， select the children to select the child。Gool there。

Again， calculate lower bound in constant time。 Select one of the children， go there and so on。

 So time complexity will be。The height of the street， the height of the street is log grade W。嗯哼。

You forgot to say something， say something。I just need to see your life here。Okay。

You everything in the spirit or say everything is spirit。 Okay， that's。哦。到。

Let's move to this problem。So here need we need to calculate over bound in this small set of integers。

Let's say， for example。Let's say W is， let's say8， and B is。It must be double power one per per。

 but it will be too。 just， just to show you what's going on。 I will pick。

Usually I'll try to pick B W power 1 or fires。If you put 8 and power 105， youll have less than2。

 it's not。So， let's say B equal to。What's it。F。Yeah， just just for this is just， for example。

 that's not usually the values you need to pick， but。啊。Again， to make all this things work。

 you actually need big value of a W。啊哼。I I will not try to write the。2024 Bs Intergerial。

So let's have some four integers。Let's。 Let's have something。Let's have0，0。로 뭐。뭐지러지러 원。Okay。

 is the first one。let's use the front part。Let's see a one。Ca I will have X later， so。

So a2 will be let's say，0。1，0，1。싫 싫어 원。not。Mr。 Warren。0 kiloロ。And one here。Yeah， good love。Now。

 the third one。 let's say， one。10。응 that make。It's really hard to make a good example。에 일로 완 번。이로 이로。

For something like this。Yeah。But like， let's make these more。也不知道不知道。So， again， we have。

We have B integers and the size of this integer is double。What we will do， We will build it。B， B， B。

 try， like in previous lecture。 So let's try to build a try from these integers。Oh go。Okay。

 let's make a compressed try like like in like in six3， right， So here we have 0。응 응 응。

So here we have 0，0。Here， to the left， we have 0，1，1，0，0，1。To the right， we have。1，0，1，1，0，1。

And to the right， we have 1，0，1。And here we have elements。然后。Okay入ると。

I wanted talk to to be an increasing order。Okay， and here we have。ジロワンジロ0ロしロエンとドライト。So 왕 왕왕 one 야。

Like this。So let's a compress try of this。In the dress， right。So if you again。

 if you represent these integers as a strings。And try to build a try of these drinks。

 You will have something like this。No。What will happen if I want to find something in this tray， so。

For example， you you given some integer。 You want to find this integer in this tray。What you will do。

 you will start from the root。And then， follow the path。

Each time you come you comparing your digit and the digit in your try。

And then follow this path from the root to the leaf of your tree。Right， it's how this right。

Now let's see the only important spots in this tribe are the sportss when you have two branches。

 so this is important spot here you actually need to select which way to go and heres important sport。

 you need to select which way to go and here is important spot。

So when you follow some path in this try， you actually have choice only in these points。M哼。

This points。You， in these points， you check one of the bits of your integer。 So let's。

Mark these bits。 So we have we have， So actually， we have only three important bits in your integer。

 so。Important bits are the bits when you need to choose your weight。

 so you need to go to the left or to the right。So you make this then。What you make。

make this choice in three points here， here and here。So when you're standing here。

 you look at the first bit of the in， so the first bit is interesting。Again。

 this beat is interesting。Yeah。Here， at this point。YouYou look at the third bit， right， So you all。

 you you have 0，0， and you look at the third bit of the answer。 So the third bit is also interesting。

Let's mark。So this beat is interesting。And here you look at the fourth。

So the fourth fleet is also interesting。So these three bits are interesting bits。Now。

 how many interesting bits you。That's a question。 You need to answer。Again。

 we have interesting bit when we have。Some something like that。 so we have a two branches。

 so in some note we have both children， we can go to the left or we can go to the right。

So the number of interesting bits is no more than the number of these interesting points。

 So how many interesting points you may have in your try if you have B values。

So the number of values here is B。Yeah。So the number of interesting points is at must b minus1。

So you have at most B minus-1 interesting bits。I will say be just for simplicity。 I will again。

 I will admit all the non important constants here， so。So we have no more than B interesting bits。

Yeah。Now， what we'll do， we' will make a small this cage of each integer。 so for each integer。

We will make a sketch。 This sketch will contain one of the interesting bits of this image。😊。

So let's split it here。 So a one prime， a2 prime， a3 prime， a4。

So we take the first integer and select only interesting bits。 So here we have 0，0，1。

For the second injury， we have 0，1，0。For the third one，5 1，1，0。And here have one on one。Okay。そ。Again。

 you have， you have a array of big integers。 Each， each integer has W bits。You make the phone。

 You select only interesting bits in each integer。And then， construct。This cage of this inte。

This cage contains all important bits of the internet。Mmhmm。😊，So it's actually again。

 these bits are enough to distinguish these integers from one from each other。 So when for example。

 these sketches are always sorted。Because again the first bit is interesting。

 so it will be presented in this cage。 So first we have all integers of zeros。

 then we have all integers with one。An so on。If you look at the difference between two consecutive integers here。

thenで。The beat it we the when we differ it is actually important。 So， for example。

 first and second integer。have different shortbe。Second and third have different first bit。

 and these strangers have different fo。So if two consecutive interests are different in one bit。

 this bit will be important。嗯。So it will be presented in this sketch。

 so these sketches will be sorted。Good。Now， how cook， how to calculate it lower bound。

 calculate lower bound。We will do the same thing at the value x， so for example。

 you are looking for some value x。Oh know let's say something。응 응 응 응。うんうんうん。嗯哼。Let say 0，0，1，1，1。0。

1。W。So you have some value of x。And you want to find this value in your try。Again。

 like in previous lecture， what we're doing to find the value。

 We will follow the maximum prefix of x in the tray。

And find and find the position when we actually go away from this path。For example。

 if you try to look for this value in this try， you follow the parts。 you start from the route。

 You have 0，0。Then you have 1，1， one and so on， so you have one here， you have one。

 so you stop at this position。And in this position， you actually try to go to the right。u。

So in the try， your path goes to the left， so you have0， the next the next bit is0。

 but your x is trying to go to the right。That's what you need to find。

 So you need to find deposit positions0，0， and so。So this will be the maximal prefix of x。

 which actually present in your train。Again， we discussed it last week which it's almost's the same thing。

So to find the lower bound。We need to find the position when we go away from the try。

So we'll find the maximal prefix of x， which is presented in our try and then find the direction when we move so here we stop at this position and move to the rank。

If we know the position and we know which we move， we can find the next。The lower ball。Again。

 the same thing like like last week， but that。The idea of how to find these max prefix is slightly different。

嗯哼。😊，你 is clear吗？You acquire it。Always nervous when you are quiet。Second， last week。

 we discussed the Wifi trial and we kind of make the same thing。

 We try to find the maximal prex of x， which is presented in the trial。If we know the maxal prefix。

 then we know that our x going like here and then move to the right。

So it's easy to find the next position in a tray。We just follow this follow the。

 find the maximum here， go to the next and so on， do the same thing。Yes。

 lower bound minimum wise greater recording。Yep。You light and see plus plus lower bound。Usually。

 it's called different in in in in in papers， but。Just。

To make it close to reality so in simple plus set， its， It called lower bound。not make difference。そう。

Mmhm。😊，So again， if we find this maxwell prex。Then， we actually done。

So we know that we follow this path， then go to the right。

This information is enough to find the lower bound。嗯哼。Now， how to find this maximum pre。

We will use these sketches。So first， we will build a sketch from this X。So from this X。

 we will again， we will。Find all these important bits。 So we have first。

 third and4 bit are important bits。So we will construct this sketch of x。The same to。

 So we will say it0 explain。呃，忘 one。No。We need to find for this cage。The sketch from this list。

 which has a maximum common perfect success。So well find this。This is the maximum preference。

 because it's here。So how to do it？So you have sketch of X。 You have list of sketches。

And you need to find the maximum prex of x， which is which is common to some of this。Sketches。

How to do it we need to do it in constant time， right？

 So we need to in constant time to find this value two like two。

 we need to say that there are two beats common in these two sketches。How to do it in constant time。

The same trip， like in previous lecture。So all these beat all these sketches are very short。

 so the size of all these sketches is B。And B is about。That will empower  one over 5。 What's exactly。

오십팔십 분 뛰。So what we can do。We can put all these sketches into a single word。So， if you just take。

All these cages put them in in a single world， Really they fit in in one world。

So you will make one work。 sorry Im out of space here。But。So we'll put a1 here， a2 here， a3 here。

 a4 here。Prim， prime， pra， pra。So we'll make a single work containing all the sketches。And then。

 in this。Bep integer。We need to co something like lower bound， again。

We can calculate our bank using the same technique we discussed in previous lecture。So again。

 you take your X prime。You build something like this。 You build X prime。Multiply it four times。

Like this。Then you subtract one from another， you get this array of Booleions。

 you make the sum of all these Booles using again the same technique like computer lecture。

And you will you will find the lower bound of this ex prime inside this smaller。So again。

 since the size of all these integer is small and the number of integers is small。

 so you have small number of small integers。You can feed all these small integers into one big integer。

And then using all these operations。No， you youく。You can calculate operations on big integers in constant time。

 So you just put all small integers in one big integer。

 and then you calculate all this operation in constant time。 So in constant time。

 you can find the lower bound of this X prime。Inside the set。嗯哼。😊。

And when you calculate lower bounds， it's easy to find the maximumimal common prefix。

 Maximal common prex will be something like one of the two neighboring elements。

 So you know your lower bound is here。So your x must be here。 So one of these。

Neighbouring elements have the maximum common pre。Is it clear enough。Again。Again， monster again。

So I have this number X。 I want to find the maximal prefix。

 maximal common pres of my x and one of the integers in this set。So， before I do this。

I calculate the sketch of x， this small in。And then find the maxim sketch。

 which have maximum common preference。嗯哼。So instead of working with these big integers。

 I work with these small integers。For this small integer， I need to find the maximum projects。

 which is common to one of these small integers。I can do it in constant times because these size are small。

So I can fit all these integers into in into one big world。

And then I can call it lower bound and constant time。Again， the same。

 same trick as we did last lecture， so we put all these ins into single word。

 then subtract these from this。Will have area of booles for each individual， if it is smaller or not。

And then we just need to have some of all these booles using the same p as was structure。给 hold物作了。到。

Now we know that now we found this sketch。So we found this kitchen with maximal。Maximal common pre。

What will do next。We will take the whole number corresponding to this case。 So we take this number。

And for this number， we will simply calculate the longest column pre。

 so we will calculate longest common pre of this number a2 and this number x。It will be free。

That's all that's all。夜关时间。I have number X， and the list of integers。

I want to calculate the longest pre of x。Which is also a pre of one of this individual。

If I know this common pre， then I can quite lower bound。Because again， what happens， I have this try。

I will go from the root to this position when I'm trying to find x and then go away from this train。

If I know the position， where I go away from the tray。I know the lower bound because I know if。

 if I go away from this position to the right， this will be the next element in in my array， right。

So I can ple quite all this stuff and it's actually exceptional at her。So， if I know。

The position when I left there， try。I actually can't precalclate the lower bound。Mm。

So it's all I need。So how to collect the maximumim pre of x， which is common to some of this。

Integers， I will calculate sketches of all these integers。 So I leave only important bits。

So I calculate this array of small integers， and then I calculate k of x。

So I have area of small integers here and small integer x。

Then I calculate collect lower bound of this small integer in in these area， small integers。

And find the integer with maximumim common practice。

So this x prime and this a2 prime has big common preference。Now， I take this this x。And82， so8。

Put back all remove bits。 So I have。This long integer here and long integer X。

And then calculate the maximum common prefix of x and a2。And it。

 it will give me the maximum common profit。嗯哼。Why it is correct， Why it's correct。

 Because if you try to follow the path from x from the root using the bits of x。

You will make all the same choices in all important bits。 So if you look at the integer x。

10 integer82。And try to follow the path from the root using these bits of x and bits of a2。

 Then in all these junctions， you will have the same choice because all the important bits are the same。

 So you have bits in x and bits and A2 all first first important bits are the same。

 So in all junctions you have the same choice。But。야 됐어 야 야 됐어。Okay。😊，そう。

So if you if you leave the try at some point， you will leave it at a point when you when you have different bit of x and A2。

So the first different bit is actually the bit when you leave the try。Yeah， that's very nice。

 but you'll better to answer to the question。It be much more productive。Go。That's all。Yeah。

 by by the way， how to calculate， how to calculate a maximum con pre。So if you have two integers。

 how to calculate a maximum common preference。I didn't mention this。 Let's do You are in the Q。

So if I have integer A and integer B。Sorry。How can I calculate a maximum common pre in constantine。

嗯哼。Oh let's put some beats there。So you have two integers。You have some beats。 Let's say is 0，1，1，0。

0。And here we have something that one。So here's a con prefacex。

So how to find the length of the common projects of two integers？Dong。It's actually quite easy。

 You just calculate the sort of these winters。 So calculate the。A or B。

So all these bits here will be zeros， and the first important bit will be one。

So you need just need to find。Yeah， yeah。 so you just need to find the highest bit in Xor of these two integers。

 So you calculate the Xor， then find the highest bit。

 We introduce our lecture discuss how to find the highest bit in constant time。

 So we apply all the same technique to find the highest bit in constant time。

 Then you will find the LCP of two integers in constant time， thanks。It's good to have you back，No。

No。That's all。Second again。Again， the full algorithm。 How how to do it。

You have the list of big pictures。And one big big integer x。

 you need to find lowest common prefis of x and one of these integers here。You do like this。

 You find all important bits here。Calculate this sketchs。Calcs cage of x。

Sketch is just the interior contains only important bits。 So So leave only these important bits。

You build this， build this and so on。 Now you'll find the lowest coin traffics of this sketch and one of the sketches from your list。

This will give you the closest integer in your set。Now you back， you go back to this。Integer。

 so integer which correspond to this sketch。And calculate LCP of this x and this integer。

And this will give you the lengththropals P。 And again， if you know the value of Op。

 you know what will be the lower bound。Let's how。 That's all。嗯。There's only one thing to live action。

Just。One small detail of this algorithm is actually。No discussed。Okay， can you spot it so。Basically。

 all elements are pretty simple。 Now here you here you need to calculate the highest bit。

Here you need to calculate the lower bound inside a small array of small integers。

 you can do it like we discussed in previous lecture。

The only thing we need to discuss is actually how to build these sketchs。That's not trivial。

 That's not trivial。So what you need to do， you have some， you have a long integer。

And you have some important bits。 So you have a list of important bits。呃这东题。

Okay this matterll be shortcut。So I have a long integer A。Can you have a list of important bits。

Positions here， here， here and here。See positions B1， be2， be3 and B4。

And you need somehow to construct the sketch of this inter。一にトもイク。TheInteger a prime。

Which contains only ins， a 1， a，2， a3， and a 4。衣服。That's not easy。So if you。

 if you think about it a little， so what。What is the problem here。

 The problem here is that you can remove all other bits。 That's not that's easy。

So you can just end your integer with some mask， which only contains these bits。

 So all other bits will be 0。 So let's， let's just say all other bits are 0。

So here all bits are zeros。Yeah。You can you， you want to kind of shift these bits to the same positions here。

But again， again， what wass the problem， You have all these beats， but they are far from each other。

 And I want to move them closer to each other。So I want to move them in in these fours。诶。Yeah。

 and I want to do it in constant time。 So in constant time， I want to move all this。Separated4 bits。

Into this small window。啊。How to do it啊。Oh if you remember again， again， if you， yeah， yeah。

 if you remember the previous lecture， not divide， you can multiply it yeah。Oh。

 you can you can do use you need to in last lecture we。De kind of the same trick。

We had few separate bits， and we put them together using multiplication。

 so we multiplied by special mask。And this special mask just again。

 what is multiplication by a mask you shift and add shift and add shift and and and the multiplication by the mask is basically the sum of your integer shifted to these positions。

We'll do the same trick here， but the difference is that in that problem with cast last week。

 we have them that。The distance between these bits was even。Yeah。Last week。

 we discussed almost the same problem。 We had different bits。

 but the distance between these bits was the same。So this distance was always be y。

So when distance is the same， we can just， we can shift it to B -1 elements Add， shift to B -1 add。

 shift to B -1 Add， and we can do it in one multiplication。😊，Here。

 the distance between these bits is different。So it's kinda more complicated。

 but we can still apply the same trick。But slightly。Moァ。S what room。I ate by some mask again。

So we'll multiply M by some M， M， M， M M。M will be just a mask of zeros and one。

 so I have one in some positions。M 1 M2， M3 and M。So if I multiply a。By this value， M。

 what will I have in the result in the result I have。对。I have a big picture， one。This。

A1 will move to positions P1 plus so。Four elements equal to a1。In positions B1 plus M1。B1 plus M2。

 be1 plus M3 and B1 plus M4。嗯哼。So for each beat， I will have four copies of this element or B copies of this element。

 if I have B beats。I have BBs here cells。So number of bits will be equal to B。So we have B B here。

 BBCC。 So for each bit， I will have big copies of this bit。In these positions。No。

What do I want to do？First of all。I have many copies of eachbe。

 If I have these copies in in the same in the same position， they will it will be something。

Something I don't want to deal with。 So I want these beats be in all in in different positions。

So I don't don't have deal with。 You have some。Some of two one and have0 on this position so so。

So yeah， if you put the bits in the same position they will sum up and make something strange to the previous bit。

 I don't want to deal this so I want all these positions to be different。

So I want all positions B plus MJ be different。Mhhum。No。啊。

The positions I will use for that for my sketch are positions B， I plus M I。So positions B plus MI。

Will be the positions I use for my sketch。And I want these positions to be in increasing。

So in the final sketch， I have my bits in the same order。And finally。I won。

All these positions for my sketch fit into some small window。So I want be to be in some window。そロ。

L to R such as R minus L is no more than being powerful like this。That's why you have。

that's why I have B S w in power one over5。So I can fit this number of B。Sketches， actually。

 the size of the sketch will not be B。 size of the sketch will be B， power4。Mm哼m。But still。

 if the size of the sketches B power 4， I can feed these sketches into single word。M哼m。

How will achieve this， I achieve is using very very simple trick。 I will say that。B， I plus。

 M I actually should belong to the window from。Wle plus， plus I B。Ft。Yeah。2 double your。H plus 1。

3-1 somewhere。食乜唔错。So。AM。Will， look like this。Yes， I know bit from left to right。

That's not convenient， but。Usually you in a very bit from right to left。

But I enumerate all arrays from the left right。 So I enumerate the bits from left to right。

 So here's the least important bit。 Here's the most important bit。So I will put them here。응。

Here I will make a four groups。So bit A1 will be put here， beat A2 will be put here， B a3 will be。

So size of each of each group is beef。Of course，So the size of this cage will be before yeah。嗯。

That's all， that's the whole plan。那。I claim that its always possible to pick values L。

Such that these constraints。So how can we pick the values of M？Let's just pick them one by one。

 So we pick。Where you M1 equal to something M2 equal to something and so on。

Let's try to pick value M。How can we pick value M I， will just bru all the possible values of M。

And check that this constraint ase this by。Actually。是。This thing will give us both these things。

 right， So they will be increasing because they。Belong to different segments and they always belong to signals。

 So we only need to take care of this thing。So we need to take careful all these sums will be must be different。

So let's see。 let's try to pick value M。 So how to pick value M。哦。

So what have so we we we need do have。We need to have B I plus M I belong to this segment。

not to some second。Okay， w plus。2 W plus I plus1。Plus one different。So were right beef。

Q possible values。や。So if I want this sum to be inside this segment。

 I have B square BBQ possible values of。And， right？Now， some of these values can be used。

Because they will not satisfy this country。そう。So I cannot use value if。

Some of these sums will put will be the same， so how many values I actually can be used So for all previous elements here。

 So here I have I minus-1 elements。These I minus1 elements。Actually， generates。I my response permit。

嗯。So there are I -1， I I-1 busy positions。 So so I occupied positions。 Yeah。 So yeah。

 I put I-1 bits here。 I multiply this I-1 bits by this I-1 bit。 So I have I-1 square bits occupied。

I can't use this cells anymore。Now， if I put some value MI I。

This value M I will generate I-1 values here。Mmm。Soう。So each value of MI。Will January 8。

 I possible bed positions。Mmhmm。😊，And I don't want these positions to interfere with this。

Acccued positions。So。Since every you calculate eye positions， then I have。Something like this。So。

 this。So this is the total number of positions I cannot use for my MI。嗯。How to call them。

 How to call them。응 흐 흐 흐。Let's call them Bens。Brand is a2 M。I。And you see。

 this number is actually less than。B cube。Since I is less than B。

So there I beQ possible positions for possible values from M。

Some of them cannot be used because if you use this value of M。

 we have some of these sums will put the bits into the same position。

So this is the maximum number of these unusable values。

 So we have this number of total values and smaller number of unusable values。

 So there is at least one possible value for M Y M。Okay， we we need。 we not need to pick it fast。

 We can do it slow。 We can just eat。Check all possible values of M。 Find the good value。

 then move to the next one again。 check all possible values， find good one and so on。It's slow。

 but it's， it's still。Can be done。That's all。That's all， So again， how you build cake。

When you need to have sketch。Of these logo， long con， a。

You just take your in A multiplied by this pickle gl mask M。Have something like this。

Now you have your bits in in these windows。 you just again， you apply another mask。

 which only removes， then removes all bits except these bits you need。

And then you have this sketch of size B powerful。B power is enough。

 so it's small enough so you can feed these sketchs into single world。那's走给你。Nice。O。那错的错错。

So now we now we can calculate sketches so we can we can in each note。

 we can precalculate all this stuff。And be able to， to。

 to find the lower bound inside the open constant time。 So the complexity for the bound will be。

Hello， W of and。や。Unfortunately， for insertions and removals is slightly different because when you insert the remove。

 if you want to have the dynamic structure。You need to construct this structure in some good time。

 but。We need some time to construct all these stuff， so we need some time inside each node。

 we need to time to sort all this element to find all these important bits to precalccate this mask and so on and this actually takes time and no for example here it takes something like B power4 so if you want to insert in this element。

Then your time complexity will be actually multiplied by B in power of， let's say four。

Let's say load B。And heroes。So what we can do So what we can do to remove this。

Be powerful from them complexity in。We can do the following。

 We can do the same trick like we did last time。So we can split all elements into groups of size。

Again， you'll have all your elements。对。You split them into groups of size we powerful。

And apply it the same technique like can beat re。 So when the block is too big， you split the block。

 when the block is too small， you merge blocks and so on。So again， again， thiss the same trick。

Now how to make operations first you find the lower bound to find the corresponding block and then you need to find your element inside the block to find the element inside the block。

 you simply use the binary search trees so inside each block you have a simple binary search tree。

So your time complexity will be lockedgged in us。Lo B with's log B powerful。

 but log of B Power4 is the same as log B。 So it's full log B。And here。 and here。Like this。Cool。

 and the final moment， final moment。Now， let's try to use both these techniques。 So again， let me。嗯嗯。

最的や。Now we have two techniques。 We have a Yfi trace from the previous lecture， which works in log W。

 and we have。This fusion tree。With time complexity C， log B， plus log B， N。Let's try to merge them。

你个。Okay， let's start from the sorry。 So if this is log based and。

 So if you have these two instructionss。If you increase the value of W。

This time complexity is increasing， this time complexity is increasing。

So when you have your values of n and W， you can select one of this data structure。And use it。

What will be the worst worst time complexity？So imagine you have your data structure。

 you have some number of elements， right？So we have at doubles。行。And you have these data structures。

So if you increase the value of double young， then the time of these data structure will be increasing。

Not exactly like this but。This's not longer， but okay。This will be why first string。

And then complexity of this will be decreasing。啥子。Okay， not exactly like this and not below  zero，1。

 not below1 zero。Something like this。So let's find this point。Okay。

 this functions doesn't look like these， but。Close enough。One is increasing one is decreasing。

 doesn't matter okay so let's find this point， so this point is when when you when you choose one structure or another。

 so if if you choose the optimal data structure， you will have time complex to like this， right。

Because you know the value of W， you can select one of these data structures and use it。 Yeah。

 So in both cases， you have them complex to like these。So this will be the worst possible point。

 What will be the worst possible point。 Wors possible point is when you these。

 you have the same time complexity。 So this point is when log W is the same as。L based W ofM。

No what is the value of double it's easy to see in So log w of n is just log n divided by log double。

 right？So you just move this to the left。 and you see that log W is actually。The log in。Square root。

So in this point。Again， this divorce possible value of W for the given size of the input。

So in the worst possible case。Log double will be square root of logan。

So the time complexity of both these data structures will be squared of logan。uhhum。

What does mean it means for all possible values of W， you can build data structure。

With time complexity here。啊。Its good here。So four game。

We can build the data structure within then complexity square root of logan。5。Now。

 let's deal with this beam。 It's actually not a hard。Actually， we have log log based value。

 but log B。Okay， let's make it let's make it clear。 So So again。

 you have value of n and W and you want to choose one of these data structure。 So if w。

 So if let's say if log w。Is less than square root of log n。Then you use live trees。我了。

What one of the ball trees。のビースもいい。So use wife as th or one in the Bo stream。If you use。Wi Wifi。

 try urban and the boss train。10 complex。 you will be low w。我个 double no。

Is less than this curve so it will be both square root of loggram。嗯哼。Now衣服。

Lo W is greater than a square root of loggan。Then you use fusion tree。And now。

 let's find the optimal value of B。So I any again here then complexity of fusion tree is actually like this。

So let's find the optimal value of B， What will be the optimal value of B。 And then again， again。

 to find optimal value of B， I need to find the value which。Gives him the same radio here in here。

I want to have log B equal to log B， N。So B must be about。没有。Again， it's this same。

 so so logo be must be。Square of Loan。But I， I， I also need to B， B less than。呃呃呃。About 1。

 5 like this， right。嗯哼。やないし。So if I make B， let's say。呃。No。

 I want to make B 2 power square root of logan， right。嗯嘿嘿嘿嘿嘿。Let's make it like this。Yeah。

So if you pick this value for B。Then， log graph of B。Will be square root of log n divided by 5。

It's good enough。It will give you there。That complexity you need。

And B will be less than W of power one over5， because again okay。Squaret of log n is less than log w。

 so this thing will be less than 2 in power log w over 5， so it is w 4145。Yeah。Yeah。

 good enough it's working。收见。What you do if your logo for W is greater than the square root of logan。

Then you pick value B as2 in power square root of loggan divided by 5。Nice for you。

And then use this value of B as a branching factor in your fusion tree。

So the time complexity will be。Log B， plus log。Lo be。Is logo ifmorph be。Lo of this value is， again。

 square。Of lower end over5。L， could even be the base B of M。Again， it will be a logo。B。

Lg N divided by log B。 log B against。Square root of log N， divided by 5。What is。저게。

And for all possible values of double， time complexity will be a squared root of logan。

Why is it interesting， Because again， we have a data structure with time complexity。

 time complexity not depend on this size of the world。 So for all possible size of integers。

We can build data structure of time complexity less than logan。And again。

 we just built a binary search tree， not binary search tree。

 but data structure the same direction as binary search tree with that complexity less than in binary search tree。

And like we again， we proved for abstract objects， we just proved that it's impossible to build data structure which works faster than logan time。

But here， if we have integers and we can make operationss with integers in Constantine。

 we can actually build a binary search tree with time complexity less than loggan，'s coro of logan。

That's interesting result， right？For example， you can use this。

Structure to make a sourcecing algorithm。So you can sort integers faster than in and logan time。

It's magic。Or you can make heaps or anything else。 buy such trees。Basically。

 basically it does all the things。 So you can make sorting。 you can make。Pag use and stuff。啊。

That's not the best result people know。 People actually know how to sort integers in time。啊。

And square root of log loggan。So that's the best known result by now for sourcing integers。

So if you apply even more complicated stuff。So。actually they use quite crazy techniques and they try to build such algorithms。

 but if you apply even more sophisticated algorithms。You can build sourceing algorithm for integers。

 which works in n square root of log log and time。It's open question。

 if it's possible to sort in and dinner time， nobody knows， but。Looks like you might be able。

No one knows how。Okay。So that's all for this semester。Okay。See you in February。う。🎼。

