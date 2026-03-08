# 【精译⚡算法与数据结构】PavelMavrin p18 p17 A&DS S02E01. Segment Tree -BV1NLB8YfEMq_p18-

，🎼嘟嘟嘟嘟嘟嘟。🎼The。🎼Welcome everyone to the second semester of this course。in the second semester。

 we will talk more about trees about some segmentaries， binary research trees。

 some different tree requests like hair light decomposition， link cut trees。Central decomposition。

And maybe something else in the end of the semester will。



![](img/6302264eb1ef7156fc8cf6261efc9f60_1.png)

I would pick some interesting topics for the end of the7 or just to keep things interesting。



![](img/6302264eb1ef7156fc8cf6261efc9f60_3.png)

啊，哼。Let on so we will start the semester with segmentsaries。



![](img/6302264eb1ef7156fc8cf6261efc9f60_5.png)

![](img/6302264eb1ef7156fc8cf6261efc9f60_6.png)

I have a whole lesson in the code forcess into section。If you know about court horses。

 you may already see this lecture soon today， I basically repeat everything which I。

Already told in this lesson maybe something else in the。啊。But basically。

 it will be the same as one called courses。开ible。So opposed to all。What is segment3。

 if you Google segment3 you。We will most commonly find updated structure。So， it's。

kind of strange terminology because。There is another data structure， which is also called segmentary。

But it's completely different， so it's used。for them。Computational geometry algorithms。

It's basically you have some segments and you want to find segments which cover your point。

 sufficient。So it's different data structure in it it。ふついな。It was developed before this also。

 So it's kind of this name is reserve for this data structure。

 but I will use this name for for for data structure。

 it's got big just because because of two reasons， first of all。

This term is widely used in combat programming。 so some of you again are from code forcess。

 so you may be familiar with。This is structure。一。In some theoretical books。

 like computer science books， they usually even don't mention this data structure。

They go straight to binary search trees and stuff like that。And I think it's not good。

Cause secondary is。It's， it's kind of basic structure。 So in order to。

To be able to construct more complicated data structure。

 it's very useful to understand how the segmentary works because segmentary give you some explanation about what operations you can do in longer time manam。

Slack like that。Thats that's。That whole introduction。Let let's go through the real stuff。

So what is segmentary？You want to solve the problem problem。



![](img/6302264eb1ef7156fc8cf6261efc9f60_8.png)

You have some array of some elements。

![](img/6302264eb1ef7156fc8cf6261efc9f60_10.png)

是么。我全是죠。

![](img/6302264eb1ef7156fc8cf6261efc9f60_12.png)

And you want to be able to be able to perform two types of operation。



![](img/6302264eb1ef7156fc8cf6261efc9f60_14.png)

Your step of operation is to change some value in this way。 So you want to be able to。



![](img/6302264eb1ef7156fc8cf6261efc9f60_16.png)

P some element and change the value。

![](img/6302264eb1ef7156fc8cf6261efc9f60_18.png)

一次。啊。有鬼。哎哎。

![](img/6302264eb1ef7156fc8cf6261efc9f60_20.png)

Quite simple operation。 and the second operation is to calculate something on the segment。

Let's stop with cculating the sub in a second。 So let's。



![](img/6302264eb1ef7156fc8cf6261efc9f60_22.png)

Let's have the function sum from L to R。

![](img/6302264eb1ef7156fc8cf6261efc9f60_24.png)

And this function will return the sum of all elements on this segment。



![](img/6302264eb1ef7156fc8cf6261efc9f60_26.png)

So we to return the sum of elements from L， let's say to r minus1。

 I won't have this left border inclusive and right or exclusive。

 and I will try to always make left border inclusive and right or exclusive。



![](img/6302264eb1ef7156fc8cf6261efc9f60_28.png)

![](img/6302264eb1ef7156fc8cf6261efc9f60_29.png)

So I I need to press some of all elements from L to R minus1。



![](img/6302264eb1ef7156fc8cf6261efc9f60_31.png)

Like this。Why are you so quiet， Is my chat working Yeah， no it's working。You are just quiet， okay。



![](img/6302264eb1ef7156fc8cf6261efc9f60_33.png)

共。

![](img/6302264eb1ef7156fc8cf6261efc9f60_35.png)

Let's move back。let's stop here a little bit。

![](img/6302264eb1ef7156fc8cf6261efc9f60_37.png)

First， first， first， suggest。For an exercise， if you don't have this firstspiration。

 if you only have this sound operation。

![](img/6302264eb1ef7156fc8cf6261efc9f60_39.png)

![](img/6302264eb1ef7156fc8cf6261efc9f60_40.png)

So you have some fixed array。You will never change the elements of this array。

 All you want to do is to make this separation room to be able to calculate the sum on the segment。

How can you do it using。Very basic structures resulting in trees stuff the clip。



![](img/6302264eb1ef7156fc8cf6261efc9f60_42.png)

Is it clear or not。

![](img/6302264eb1ef7156fc8cf6261efc9f60_44.png)

So if you don't have this set operation， you have only same operation。

How can you solve this problem using very basic data structures？We the right， right。Whaterate。不。

If you just use the simple array？Then you have this separation in constant time。

 this separation in linear time you want to make this separation faster in。



![](img/6302264eb1ef7156fc8cf6261efc9f60_46.png)

Lner代。Yeah， perfect sum。 perfect sum is is good solution。

 So if you don't need to change the elements of the array。

 you only need to calculate the sum on some segments of this array。

 you can precalculate the sums of of of all pres of this array。 So at this array。



![](img/6302264eb1ef7156fc8cf6261efc9f60_48.png)

![](img/6302264eb1ef7156fc8cf6261efc9f60_49.png)

And you precalulate the sum with prefacees and put these sums in some another way。

And then then you need to calculate the sum on the second。You get these perfect minuss。

 These practice will be equal to sum on this second。嗯。Yeah。

 and you can do this trick with almost any operation， which have some inverse values of it。For some。

 you havet your video。 So if you have plastics， you have -6。

So if your operation have some inverse failure， then you can perform a this。哦，OK。那。That's again。

 this only rows， if you don't have the separation， so if if the array is never changed。

 you have some fixed array and you only calculate these queries。哎6666。see if you have celebration。

 you cannot do the trick because this celebration will change all these perfect sum。



![](img/6302264eb1ef7156fc8cf6261efc9f60_51.png)

Yeah，不。So how to make these two operations in fast is in linear time。为什么？



![](img/6302264eb1ef7156fc8cf6261efc9f60_53.png)

So what is the segmentary， Let's build the following binary tree。 Let's have some array。

 Let's see we have some。

![](img/6302264eb1ef7156fc8cf6261efc9f60_55.png)

5，1，3，2，6，12。For sale。So let's have this sorry。

![](img/6302264eb1ef7156fc8cf6261efc9f60_57.png)

Let's build the following tree， let's build a full binary tree。

Suchci that these elements are the leaves of the threshold these are the elements of the array A。

 so this is array A。So we build the tree， and these elements will be the leaves of this array。

And each next element will contain the sum of the children of this。

 here we have some parent element and here the sum will be5 plus the6。



![](img/6302264eb1ef7156fc8cf6261efc9f60_59.png)

Here we will have some these elements of5。You we have8。1。And on the next level again。

 we will have some of these。哦。And。嗯。So this is the segment3 for sum operation for this array。

 So we have this array a。So we can build this， this will be the segment three for for some。

 so you have a program some of this。Okay。lets do it in this slow way。我索。そう。We have this array A。

 We build this tree。 We can build this tree in linear time。 right。

 So we just build this three layer by layer。 We put in first layer， then build second layer。

 third layer and so on。The total number of all elements in this three will be 2 m-1。Y is2 n minus-1。

 because here we have。And node here we have and over two nodes and pre and on。

 The total number of four elements will be 2。 but will will be2 n-1。あ。In this example。

 this tree is very symmetrical and。Beautiful， just because this N is the power of two。

So if this n is the power of2 to empower power of K。You will get something symmetrical like this。

If your M is no power of tool， you may build something not that that not thatsymmetricriculs。

 You have like three elements。You may build something like。Something like this。Not very cool。

 but still worked。h I will not talk about trees like this just because。😡，Im too lazy for this。

 So I will can。 I will assume that I always have an equal to power of2。

So this tree is always the perfectly balanced。W is the so I have。All the subies are the same。

 So each element have exactly two children like left child， right child and so on。 So。

 So I always have three like this。 I'll never have something like that。 Just just for simplicity。

 You can actually。You can take all the algorithm results today and just modify them a little bit to work on trees like that。

It's up to you。嗯。😊，Okay， why can I， why can I assume that n is equal equal to power of 2 Because if n is not equal to power of 2。

 I can always extend the array to the closest power of 2。 So if you have n elements。

 you have this array A。You have found elements。You can add some more empty elements。

I that the total allow。Willll be part of two。And this。

A number of these additional elements will be no modern than n， So this。

This UM will be less than 2 m。So if you extend your array to the closest power of two。

The total number of elements will be increased most twice， so it will not affect the asymptotics。

 We will talk only about symotics today， mostly， mostly not exactly。

 but mostly we will talk about symotics。 So if you extend your error device。

 that will not affect theymptotics of the algorithms。消费公。아对浙江。have this kind in Coltok， who maybe。

It's， it's， that's mostly technical stuff。 It's not that interesting。 So you you you。

You can modify guidance to work on these not perfectly balanced assets。It's just technical stuff。

 that's not， not， not that interesting。 but really you can。そ。那那。

So we have this perfectly balanced binary tree。 What is the total number of elements or the total number of layers in this tree。

The number of lays in this tree will be lower。What was oil， like please。

And we will build both these algorithms in such a way that the asymptotics of both the separation will be。

Log at it so。Both the separation will depend on on the total height of this tree and the height of this tree is。

Logan， so that both this。Operations will have ayotic log。Okay， that's all preparations。有是。

I'm just trying to save some time。If you have any questions， Okay， let it go。嗯。Now。

 let's talk about other。

![](img/6302264eb1ef7156fc8cf6261efc9f60_61.png)

Let's you。We have this dream？Each element of this tree。Is responsible for some segment of the array。

If you think。For example， if you take this8， this8 is the sum of these two elements of the area。

 so you have this six plus  two。If you take， for example， this 11。

 this 11 is some of these four elements of the area， so it is5 plus one plus 3 plus2。Mmhm。😊。

And so on， each element in each node of this segmentary represents the sum on some segment of this array。

Look like well this 1 is the sum of these two elements， this 19 is sum of these four elements。

 This is some of these element， this is some of these elements and so。

 each each each number here is sum on some second of the。啊。The numbers in the lymph nodes。

Just the single elements。 but we can represent sigma single element as the sum or on the segmentment of length of  one。

 So let's say that these numbers are the sums of one element。

So each element in this bottom layer will be just some of one element。

One element is the sum of itself like。And this root element is the sum of all elements in the。

 So again， it is sum segment which contains all elements of it。我比的上哦别爽很爽。No。嗯嗯。Now。

 how do concentrations？Let's start the first version。 First version。

 we need to change one element of the array and rec this terms。

 So if we change one element of this array。 let's say。Coabration sir。

Apply to this element and change it， let's say， too。はい。

So we take one element of the array and change it for。Now you need to rec the P sumalms。

 You need to rec the sums which contain this element。Which sounds。Contain this element。 No。

 you need to take all the the notes。We should present the segment， which contains this element。

 You have exactly one node on each layer。 So you go from this element after the root and trickulate all the sun。

 So you go here， here you have。Oh，6 plus 5。It's alone。Now you move here and calculate this sum。

 it will be 22。And then you go here we calculate please some some will be prepared。别走。

That's how you that's how you recal all the sums after you change one element of the。

 So you change one element here。And then go up to the root and recalulate the sum。

 So you could reccoulate this sum recalulate this sum reculate this sum。Good so。

The total number of sums you need to calculate is up to the number of the layers of the tree。

 and if you have the per tree， you have log from end layers。

 so the total number of elements you need to recco is logan。This separation will work in more with。嗯。

嗯哼。😊，嗯，一错。That's how you perform set separation。Where is it。

 You just change one element rec the sums。 You calculate morgan sums。

 You have the new modifiedified segmentary。That's not very interesting because。

When we have simple array， we can modify in constant time。

It's much more interesting when you need the group to collect this song。 Now， let'。

 let's see how these。Segment 3 will help us to calculate this sum。Just era this。诶66。不ち。Now。

 how will we calculate the sum on the given second？Let's see。

So you're given some segments let's use some。More colors。有这。Let's use this blue。

 So you're given some segment。大工。Now， let's have some。哦。He it visible。French template in New market。

Just new from the new box。 No No idea。What is another one。Okay， so you have some segment。From L。读啊哼。

Again， L is inclusive， I is exclusive。嗯。So you need to calculate sum on this second。

How this segment really will help us to calculate this sum。Very easily。

 we will try to calculate this sum using the thumbs already stored in this segmentary。

 so we will build this sum from these numbers in this segmentary。For example， this sum。

 how can we construct we can take this sum。嗯。에다cade만 뭐。拉水少。And不 this。

So some here will be equal to five， some here will be equal to 11 so the total sum of this segment。

Will be 5 plus 11 plus 4。Ohrithmatics。My a and。Great， right。So that's the plan， that's the plan。

Again， what is the plan， We have this segment3。And we need to calculate some on some segment。

We will take some of these precalculated sounds and combine our segment from these precalculated segments。

没错。The digital laser progressionional we will do it next next week。

They will use some basic techniques about segmentsaries。Avocation we will discuss next lecture。嗯嗯。No。

そ。How can we find these segments。And who are to two questions。

 First question is how to find the segments。And the second question has how how to make it first。

 Because we need to， we need to kind of find the segments in in log and time to make good syntheticotics。

very easily。It's a very easy algorithm。嗯。So how we make this celebration？

Let's start from the root and make a reversal of the cold tree。

 So we just make a recursive procedure we call it from the root。And each time we。

We say in some node X。If we're not in the lift node。

 we just recursively go to the left tree and then recursively go to the right tree。

So we everybody go here。Tverse this sub then go right， traverse this。if we do it like this。

 we will eventually will roll through the whole tree， so we will find all the segments we need。

That's， this version。啊。But if we have traverse recursively across the whole tree， it will again。

 it will take a linear time here because the total number of nodes in this tree is linear。Yeah。

 so if we just make a recursive traerssal across the whole tree。

 we will have a linear total of 1 complexity， that's not what we want。

So we will make two simple optimizations for this recursive through。

First optimization is the following。Let's say we stand in some notice。So again。

 we have some recursive procedure， right， So in our recursion， we have some current node X。

 So we need to calculate sum of all elements in this sub。These substrate x。

Represents some segment of this array， So these x represent some segments from here to here。

Optimization， number one。If this segment is not intersecting with this segment from L to R。

 So we have this segment from L to R。So if our re。moves to this sub and we need to calculate some of this segment。

Then in Big sub3， we don't have any important elements。😡，So we we can。

When we move into this recursion， we can immediately return the back because in this sub， nothing。

Is interesting。 all elements。 We don't need them to calculate the sum。

So so this is the first optimization。If you have something like this， we is just。

I will write the quote later。There's just some pictures。 I will write a shelter called it。

 It's very simple。Second edition。If the segment is completely in sight。

 So if we have again we have the snow depth。Le node X represents something。

And this segment is completely inside the segment from L to R。 So we have something。

Then we just add this segment to the result。 So we add this segment。Do they result themselves。

Because this segment is just a part of this decomposition。

 Yeah so so this this segment of x is part of this decomposition of the given segment。稍微嗯。Yeah， yeah。

 yeah。 So we just stand least。嗯。Yeah。哦，7。맨일죠。This is plus equal。I will write the quote later。

 It's just， just， it's just。' some illustrations。来走。That's all we need。So again。

 we make these two optimizations。 so we make a full recursive drivers of the whole tree。 Yeah。

 so we make recursive procedure。 We start from the root each time we。Try to go to the left tree。

 then try to go to the right。😡，Then we have only two optimizations first optimization。

 if the current segment is not going segment the given segment。

 we just return and do not the one thing。If it's completely inside。

 but then we are add this sum to the results。 So we add to this。

Some like the second to the resulting some look like this sort go here。And again。

 we return from it let's illustrate the on this example， So we start from the road。Then we go here。

 Then they go here。 This。 This segment is completely outside。 so it has stop the recursion here。

 Go back。 go to the right sub3。 See this segment is completely inside。

 So we add this value to the result。还有那个。s stop the recur here。 Go back， Go here， go， go here。

Go to the left at this segment。 Go back from the recursion。 Go here， go here， go to the left child。

 add this segment。Go back， go back。准备走。嗯哼。Good。到。Is it clear life。

 I'm still trying to give you some time to ask the questions。 so if you have any questions。

Just ask them immediately because you have we have some delay between me and you。 Okay， okay， good。

Now let's calculate the total number of node we visit during this tu I claim that the total number of node we visit is about loggan Why is it true。

 let's see because almost all the time we have one of these two cases。In almost any decursive coal。

 we have one of these two cases。Let's see white。嗯，那我听啊。So。If we don't have。

If our current segment is not completely inside and not completely outside。So。

 we have our current segment。有。And some elements on this segment are insight segment from L to R。

 So let's see some segment is insight。And some some elements， some elements are inside。

 some elements are outside。It means。That we have one of the borders of this segment inside the segment of even exon。

Some work here。Something like this。So one of the borders of the segment。

I is inside this green second。Mhhum。😊，L or R is。Inside。是。

So if we don't have this case and don't have this case， it means that some of elements are inside。

 some of elements are outside。It means that one of the borders of the7 either L or R are inside this green segment。

How many segments can have one of L and or R inside the segment。

 Let's see on each layer of this tree。All these segments do not intersect。

 So we all these segments on each layer just split the whole range of elements into some non intersecting segments。

So on each layer。We may have at most one segment which contains R and at most one segment which contains L。

😡，And we have log and layers。So we may have up to two loggan。Segments we situation like this。

No more than two logan。Segments。Weve situation like this。So basically again， let's let's draw an our。

 So we have this L this R。So on each layer on the cost layer we have like this segment and this segment。

 on the next layer we have like this segment and this segment and so on so。

 on each layer we have only one segment which contains leftpo。

 only one segment engineer contains very important。So the rightmost two organ segment。

 which contains one of the borders of the second。And if we don't contain the bottom of the segment。

 then we' are either completely inside or completely outside。

 so one of these optimizations will work。那嗯。What is the total number of implications of this recursive procedure。

 So we start from the root。So start from the root of the tree。Then each time we have。

 if we don't have any。Of these cases cases， then we make two recursive calls。 So for for rule。

 for example， we make two recursive calls。Now here again。

 we check these two conditions if we don't have this and don't have this。

 we'll make two recursive codes。And so on， for example， here we have one of these conditions。

 so we stop the recursion then they go here， we stop the recursion and so on here we have two recursive calls again。

Here we stop the。penil。Yeah， it's exactly like cute， interesting。那。え。In each of these nodes。

We didn't stop the recursion， so it means we have this case。These these these。Please notes。😮。

A one of these two analoggan nodes。토 토가겠나。So we have at most。Most too again。Nots like this。

SoAnd what is the total number of nodes？😡，So we have these nose。Last。

 these leaf notes when this regression terms。So if we have two log nodes here。

 then we have up two log nodes here。Because total number of elements in the tree in the by if you have full binary tree。

 then total number of elements， total number of leaves can be more than total number of internal nodes。

 because now each internal nodes give you like two branches。So一一。If you have loggan branches。

 then in the end， you may have up to loggan。Les， break。And clear enough。Again， you too quiet。

 so I will just rip。That's the that's， that's my problem。

 I know I I I just repeat the same thing and until you just。And until confirm that you understand。

So is。 So the total number of nodes。 So if you have log and this nodes， then we have。At most。

呃 do go game。Now plus  one million node here。 So the total number of node we visit in this procedure will be up to4 again。

So the total number will be about four local。🤧Let's all。Again。

 listed the total number of nodes we visit during this recursor procedure。

 and we don't do anything except this this recursion。 So that's that's the whole time complexity。

 time complexity will depend on the number of nodes we visit when we log nodes。

 So total time complexity， you will be log。呜。你错。So don't get why' order anything。

 why we have two organs here。Because let we make a recursive procedure in each recursion which set if the current episode we just regard this this tree。

 if the current segment is completely outside， then we go back from thecursion。

 just we don't do anything。If we are completely inside， we can go back on the discussion。

So if we don't have this case and don't have this case。

 it means we are not completely inside and not completely outside。

It means we are somewhere on the border of this cycle， so we have this segment from L to R。😡。

Then our current segment is on the border of the second。

 so it may be here or it may be here or it may be like this。Okay。😊，啊，手。Okay。

 the trick is that this green segment will contain one of the borders of this。A couple segment。

So it should contain L or or R， So one of these borders should be inside this grid segment。

And on each layer， these green segments do not intersect。So。

So on each layer we have at most one segment which contains L and at almost one segment which contains r。

嗯哼。😊，So the total number of these segments is at most two on each layer of this tree。

 and we have loggan layers， so the total number of these segments should be up to up of two login。

This forwardgan， again， we have this recursion。 this is the recursion right So we start recursion here。

 go here， go here and on。 We have two cases。 We use one of these musics。Or we have this case。

If we have one of the optimizations， then we go to the cursion and immediately go back。😡。

And if we don't have one of these case， then we make two recursive code。

 like here we have make just make two recursive code。That's what。

So let's go create a total number of leaves in this tree。😡，So we have these elements in each element。

 we have two branches， and we have up two again such branch branching node。

Each of these nodes have one input edge and two output edges。

 so it can increase the number of branches by one。So you have one branch。

 and here you have two branches。So each of these internal nodes just increasing the number of branches by one。

So on the bottom layer。😡，You have these leaves， each leaf just terminates one of the branches。

So if you have two again internal nodes， then in the end you will have two organ branches。

And each of these leaves just terminates one of this branch。Makes sense。

So the total number of leaves will be something like that。嗯哼。嗯。

There' are another way of thinking about these。😡，But that's actually the easiest easiest way to think about this。

There are many very small number of nodes which have branches。 So most of the nodes just terms。

So in most of the notes， you just go go go on the recursion and then immediately go back。

Almost all knows immediately terms your question。There are only a small number of notes。

 about two organ notess。In which you have some recursive concept。So total number of this don smoking。

嗯。😔，O。Okay， you may， you may you， you may， you may want to rewash it later Its。

 it's not that complicated。 It's just。Give yourself some time to think about its。

It's not that important for the next。😡，But on I'll just。你手。Now， let's implement some code。

So how to implement this segment。 there are different ways to implement segmentsaries。

 One of the way is classical ways is just to have these nodes and each nodes So to have click click。

我什。嗯。Something like that。 And you have like two pointers to the left node to the right node like like that you have like。

They can make it in C block plus way。我也。soundss like that。I never， I。

 I never mentioned like these folks。It's actually possible。

 so you have some pointer to the left node， some point up to the right node， and you have this sum。嗯。

没。硬子。我也理我。哦。Looks very industrial and。诶必。O，It's possible to implement segmentsaries like this。

 and in some cases that's the most useful way to implement the segmentsaries。啊，But。Not， not。

 not the fastest way。 So you for each again， for each node。

 you you need to have this class and in Java， for example。

 if you have a lot of small classes you need to。 then garbage collector will go crazy。

 So if you have like million of small classes， the garbage collector will say， okay， I can handle it。

 but it will take some time。 so。A lot of small classes not in J Java。

 but also it uses a lot of memory so we have least two pointers each pointer calls you some memory stuff and so on so it's possible。

 but it's not very not that efficient。啊嗯。I'll try to make another implementation。啊。

Another recommendation。Which is kind of motor efficient and。It's not that universal。

 so for some problem you can adopt this implementation。

Usual usually it can be used like this and it's mypoli。Let's see。

 So how we will implement this segment， We will implement it in the same way， implement the。Bary hip。

 So if you remember the binary heaps。We implemented this tree using very simple technique。

 We just enumerate all the nodes in such a way that it's easy to to see which element is the sound of each element and so on。

 So we will just enumerate all the nodes from top to bottom。So we'll say a。

 I I need another color or piece。So we'll say this node have in the0 this have 1，2。Three4。

 five and on。So we'll just assign the indexes for all indices， for all nodes。

In such a way that it is easy to get the index of the child node when we know the index of the parent node。

 again， it is absolutely the same as we did in the binary hips。 So if we have。If we have no X。

Then how can we find the index of its children， It's quite easy。

 So the left child will have key index2 x plus1。And the right shelf have index to x plus2。

Now if for your zero indexation， I keep you quick， you will stopping in this from0。

Then left shell will have two exposed one and right shell will be two exposed2。分从。

And now we don't need least two pointers because instead of these pointers。

 we just calculate the index of the two。哦赛是。啊。Second position。 Second position forward。啊，我我去。

When we apply these to optimizations。😡，We kind of need to know this segment correspondinging to current node。

 So when we you when we make this recursion， we go to some node X。

We need to know the borders of this current segment of of the segment， which responds to this note。

 right。So we need kind of to store these borders of this second， but I will not store this borders。

Instead of storing these bowls， I will just。Calculate these borders on the go。

So when I use the recursion。I。When when I am in the nodede X， I will know that itss current second。

 So I will know the second which corresponds to nodede X。It will be some segment。From L X to R。嗯。

So I will not store this value in some fields of this node and some that。

 I will just calculate these borders on ago so when Im in this node X。

 I have this border from L X or X when I move from this element to is chart。

I will recalulate the current borders， so when I move from here to here。

I will know this for for this left segment。The borders are like from Lx to some middle of this elements to some。

L x plus R x。And so when I move from here to here， I will just rec the current borders。And so on。

 so I don't need to store these borders in some additional memory。嗯嘿嘿嘿嘿。哦。O。Okay。

 now let's implement something Okay，s go。SoPro let's implement its separation。

 so we to have this set。Se theration again just puts element V in position I。Well， I will make it。

 I can。 I will make both operation in the recursive way。 So I， I will make recursive procedure。

 which。Make decoration in the given sub。So I will pick this operation and add three more parameters。

The current don。And its photoss。And this will be re procedure。

 which sets the element I to2 value of B。告。Po you。 So how to set the the the value of the element if we are in the leaf node。

衣服。How to check if the current node is the leaf node。

 The easiest way is to check that the length of the segment is one。Its the lamp of the segment。

Is one。Then we are in the lymph node。So if we're in the live node。

We just set this value to this element and return from the re。哦。アさ。

I need some array to store these numbers。Let's it dream。So I will put this video in。中。Three。

 so I I think you where you of X， right？对呀。So that's if we are in in in Li note。

 We just put this value here under the terms。If we are not on live node， then we need to go to the s。

 which contains element I。Let's see we have went off here。We need to select。One of these children。

 which contains element I。呃，好 do it。Let's put this to some variable M。

 Let's say M is the middle of the segment。Now， left segment contains。All elements。From L X。

To m minus-1 and second contains from L to Rx minus-1。So we need to change element I。

 so we'll check which of these segments contains element I and go to this subject。衣服。

This I is less than m。Me need to go to the left。We go to net sub3。😮。

It means we call the same aggressiveive function I V。不 three the node number is to x plus one。

And the borders R L X， L。嗯。And else will do the same for the rights so you make the same accuracycur call for the rights。

Sati v。I V2 x plus2 m。那种怎么叫失来。One of the children。 And go recursively here。

And make this change inside the street。Now， when we go back from the recursion。

 we need to recalulate the current value in the node X。 So we are taking here。

 we make recursive call in one of these subaries， make all the changes here， so we change this。

 change this， and then we go back from the recursion， we need to calculate this vacuum。

What does Jeica believe this for you？嗯。Just simply taking the some of。别走别走。

That's how you set the element of the of of off， off of thinking。응 그려나。

Let's have the second operation， second operation。Whereor is this？我操。Yeah。Yeah。Again。

 second version is to calculate the sum。 so we need to calculate the sum。

1 element from I to R in the sub3 x with borders and X and R x。嗯。

And usually it's implemented point way， just by。啊。How is's cold。

There is a good water abouts this button。 I don't remember。嗯。

So we will assume that when we pull this sum。It will return the calculated sum。😡。

But it can calculate the whole sum on the second from L to R。

 so it will calculate the sum of all elements from L to R which are inside the current segment。

 so let me show。レやでしょ。So we call this recursive function from some node apps。

This node X represents some segment here。And we ask。Iim to calculatelate。

The sum on sum segment from l to R。嗯。So thiscur recursive function will return that sum of all elements inside this。

呃。Inside this sub and inside this segment。 So it will return the sum of all of these elements。Yeah。

嗯哼。😊，That's the easiest way to implement this section。We'll just call this some。And when it returns。

 it will return the sum of these elements， or it return on sum of all good elements in the given sub。

Yeah。거。Let's go， so let scene。Let's implement two optimizations。

 First acknowledge if we are completely outside。 So if。So if these two segments， not in the section。

 we have this segment from Ldo R and this segment。中。L， X 2， R， X。So they do not interscept if this L。

Is greater or equal than R x。Or if L X is greater equivalent R。Then they do not insect。

If they do not insert， then this intersection is empty。

 We need to calculate we need to find the sum of empty set。 sum of empty set is obviously 0。

 So we just return 0。If we're completely inside。This segment is inside this segment means L x is greater equal than L。

And R x is less or than R。It means that we are inside。

 so we just returned that sum of all elements in this we just return。These three of。If none of these。

 then we make two recursive。 let's calculate first sum will be。Some in the LED su。

 So go gl some are power to x plus1 L M。What does M M when need double break out？Again。

 we will we make a concert calls for this left sub and calculate the sum of all elements here again。

 like。Like let me sure with the game。So we make the graphic pole for the left substrate。

 graphic pole for the right sub。And we need to cote some on this segment。

The left call will return this sum。 The right call will return this thumb。

 Now we take some of these plus these get the whole sum。So this is left somewhere。大不被熟了。

Now we complete this term， it will be the same because a call for the rights。哦。Like this。That's so。

 now I'll just go relate the some of this on。You。So that is the full code of the segmentary for the sun。

是。哦。Notingcompate actually， you can just use this code in C++ and it will work。Very is simple。那。啊。我。

What decorations can you do using segmentaries。if it's only for culating sum。

 it will be not very interesting。嗯。But the。Cool part is that instead of calculating this sum。

 you can calculate many other functions on the segment。For example。

 let's calculate the minimum on the second。For example， if you want to calculate minimum on segment。

 so you want to function minimum from L to R。We should return me the minimum of all elements from L to R10。

嗯。O。I Hi Russian Huhi。 me， me I'm Russian。讲出去嚟噶。No， my rough accent is pretty annoying。

 and I just thought。哦。啊嗯。I was， you want to go late minimum on a segment instead of sum on a segment。

We will try to do everything the same， but in coequ in sum。 We will co the minimum。

 So can you have some。Secondmentary， let's have some elements like again it，3，5，1，6，8，2。4，5。So again。

 you have some。WeWe have some array。 We will build that same binary tree。 but instead of sum。

 we will have minimums。So here we have minimum of on three and5 to be free， here have one。

 here we can。And on the next level， again， we kind the s。But we look basically the same。

But each time instead of some w playing in your arms。And again。

 both operationss will do the same when we need to change element。

 we change the element in the bottom row， then we walk up to the root and realulate these minimums。

And when we need to calculate minimum on some segments， or given some segment。

 you need to calculate minimum on the segment。 You split this segment into some elements。

 this but least here minimum is 6 here minimum was 2。 calculate minimum of this。

 get the minimum on the whole segment。Yeah。嗯。Yeah。Just instead of。

 let's find all the places we need to change when we we change from sum to minimum。

Let's see in in this set。We need to change in the same the shook。

So here we need to change this sum to minimum So instead of this， we take the minimum of three。

2 x plus 1 and 3。Door back， plus two。In this function， we need to change here here。 we have plus。

So again here we need to make minimum of S 1 and S 2。And there is one more place we need to change。😡。

嗯嘿嘿。嗯。嗯嗯嗯。Yeah， I missed this comments sort。1，1 more，1 more place we need to change is this 0。

 This0 represents the thumb of empty set。 Yeah， so we have empty set。 The sum of empty set is。你思。No。

I don't say it's focused0 boxes。呃。靠声。It's very useful to to keep the sum of empty set equal to0 because it's it will keep every all all earth matrix good。

 So here， when we have minimum， you need to find minimum empty set。 minimum F set is something more。

Complicated on e。Psophically speaking， if you have no elements。

 it's kind of hard to pick the minimum elements if you have empty set。But。It's。Very useful。

To just say that the minimum27 equal to plusfin。Again， it will keep all the calculations correct。

It's kind of strange in Fosoko， but it。It's I mean， I mean， I mean， I mean， it's working。

 It's working。 that's the main thing。 So if we just。Place blossom peas here。嗯。E over。

Why is plusfinity， So it。What element we need to pick here。

 So here we need to pick some something called neutral element。

So we need to we need to put here some element， which will not change the value when we apply this function。

So if we have this plus infin here， and then we add one more element。

We will have minimum of this element， and plus infin。And it will give you least element。

So it it it is something which will change to the first element。 when we add this first element。

 So when you add first element to the set， you apply this function minimum。

And the result is this geldenome。The same is with the0 when you apply plus function to 0 and something you get this sample。

嗯哼。😊，那总。Oh。We are beat little bit of that，Will we have enough time to talk about？😡，Your system trees。

 I think will'll。We need some more time to talk about the。Just to make it more interesting， right。

 because because this hole is in in the court horses less。你对 something。Letず go。Next。

What other operations can we use in these in the secondary？We can use， basically， all operations。

Which have the access activity property。 So if we， if you want to have some operation。

 So you have the operation some。From L to R。Let's， Let's change it for something。

let's keep with another name， let's skip some some goate。

So calculate something from L to R and this something is just。A result of some operation， L。

 then some operation。L plus one， then some operation and so on。 then some operation。あす。嗯哼哼都快不了没病症种。

Oh， usually second3 is the binary three。Why don't。You you can make it challenge trick。 you。

 you can make it journal。Three as as a segmentary now each in time here。

 you will have not two elements， but three elements， but y。杜卫是呢？One is a little bit laier。

 If you have only one child， it's not a good。 if you have two children its。Its again。

 the height of the two will be low again。主意是呢。嗯。太阳了 go。

So you want to make some a which calculates something on a given second。And if this。

Aperration have the asivity proposal if this operation is associative。It means that。You can apply。

Right also。FDV。G。Yeah。There's very simple property。

It kind of means that you can apply operationss in any order。 So if you have like a， something， B。

 something C。Then you can apply these operations in any order， so you can apply。

Appperation to A and B and then apply C to the result。Or you can。Or you can do it like this。

 you can apply B to B and C and then apply A to the result。

So if you have some operation which have this property。😡。

Then you can use this separation in your signature。And then them。M。Okay。Now let's see。

Why do we need to assert where where we use that our operation is associated let me just change the code and you think why we need this operation to be associated。

So we need to change。So谓叫 changing。1。We change it here。And here we use some neutral elements。嗯。都。

So these are three points of。Or potential like all the risk code is the same always for all brief。

Again， let's go back why we need the separation to be associated。😡。

And basically because of the way how we calculate the sum。

 so if you remember how we calculate the sum on a segment。要不是。

What we did when we tried to calculatecolate the sum of the segment， So we have some segment。

We try to split the segment in in some subsments。Then calculatecoulate sum on each segment and then combine them in in the big sum。

Basically， we changed there。Or there of decorations， for have like per A B dean。

So when we calculatecoerate some of this ser， we may want to calculateerate it in this forward order。

 we calculatecoerate with sum of a plus B。Yeah， so this sum is in this node of the se。

 let also go call it this sum in sum another node of se。And then take some of these two sums。

And I kind of hope that well get to sum of the whole thing。8死。所谓。When we use segment 3。

 we apply these operations in some range order， So first we calculate this time， calculate this sum。

 then take some of these and so on。 so the order of operation will change apply when you try to calculate it using the segment3。

And to keep the results same， we need these shape。Makes sense。Now。

What operations can they use when they are associative， Many operations are asciative。

Like minimum maximum sum。A product。Many products like matrix products， model of products and so on。

Great common divisor。Some bitwise operationss like bitwises and Biwise for。Bed byor。

But a lot of what will is some。😡，Sometimes where will have some。More complicated。Operations。

 so for for some problems， you may need to some give have some， some custom binary operations。

 And just to prove by yourself that your operations you construct are also。Sometimes happens。

 So some sometimes in each node， you have some。Pre value， Let's see。

 And you combine these triples using some strange rules。

 And you need to prove that your strange rules give you some appropriate operation。上班时间。嗯。Co。

Let's move to the final topic I want to discuss they let have some financing。Let's make persist。

Second trick。嗯。If you remember。At some point in the last semester， we was talking about。

About linked lists， I think when we talked about linked lists。We build it a boom。Yeah， I I was about。

 I think it was。 Yeah， Yeah， I think it was about the business。 So when we talk about linked list。

 we built a persistent linkquest。And now we will try to do the same with the secretaries。

So what is persistent data structure？而且么。Well let's remember what is。啊。Okay， now let。

 let's go back again。 let's go back again。 We want to discuss few few lecture before in the in the prior semester。

 But let's just do it again。 So sometimes you want your。

Data structure to remember all the previous states。

 So you have some initial state of your data structure。Then you apply separation。

So after you apply separation， you have a next state of your data structure。

And sometimes you want to be able to access both the previous state and the new state。No， like。

 let's see。 you have like for the segmentary。 Yeah， you have your current state of your segmentary。

 So you have some。少之瑞。Let's have some smaller right。W。Three，1，6，有。

Why I always have the same number of you？Yeah。I have really small imagination。Okay。

 and so this is the current state of your data structure。😊，And then you apply some operation。

 which changes the current state here， so you apply some operation so you make operation set。

Let's check， for example， let's set these elements。The sent an element in the with。

So now this array equals23，1。And with a standard search， you just have this state。

 this is your current state， so if you apply next separation。

 you will apply this to this current state。🎼In persistent data structure。

 you want to be able to apply operations to both these states， so youll want to have this verois and。

What just happened。 quite in。 So you had these two versions。

And you want to be able to access the thembo。I paid this marker for him。Let's have another one。

到15万为米到15度。So you want to be able to access both these versions and in the same time。嗯哼。

So how you make it work using the persistent。在 countries。没意思。

We use almost the same techniques oflingistic。😡，Teciques called Weth cloning。Okay， let's go。

 so we have here。We have this。Segmentary。So we have this segment tree，3，1，6 and five。No。

 let's have segment three for this summer right here。have11。Beic to。

So we have this nice segmentary here for this state。哦，对。Secondary。No。We want to apply a thisper。😡。

So we won't change what these elements look for。But we don't want to forget the previous value。

 so we want to remember that the new value of this note is4， but the previous value was 6。😡。

So although do very simple trick， we will just clone this note and make a new note we a new radio。

 so we have this old value and we note here。We have the new will。 I hate these markers swung them。

I don't know。 This is new pack of markers。For some reason， some of these就 work don't work。

So this is the new version of this node。No。We go up to the root。And try to update our cemetery。

So we go to this node。And try to update value here。 So the new value here must be 4 plus 5。9， it's9。

But we don't want to forget this old value。😡，Saw Wicklo this north。And create a new mode。

We very unit。And just put this。😡，Note as the left child to hear。

 And this note as the right child to hear。去。这。哦。So here we have two versions。

 First version is this 11。And it has two children six and five。And second version is this9。

 and it has to two children four and five。So in this in this version we have 11。

6 and five in this version， we have nines，4 and five。And now we do the same for the road。

 but have this route。And we try to update the value。 So the new value here must be。13。

So we change this 15 to 13 and we when we change， we just clone this node to the new version。没灯又要上。

With new Williams。And put this element as the lecture this element is。That's all。

That's all now on this picture there are two versions of the same tree in the same time。

 so if you start from this route。You get the first version of this string。

 if you start from this row， you have the second version of this string。

And you can access both these versions in the same time。

 So if you want to do something in the first version。

 you just start your recursive procedure from this row。嗯。Just。

 you just called the recurs recursive procedure。 I era it。

 but you that that that recursive precision， you just call it from this route。

 And when you want to access the second version， you call the same procedure， but from this route。

And you will have the result in the first version of the result in the second version。嗯哼。😊。

They don't， they dont conflict you can， you can hold here。 you can hold here。

You will help some results in for the first version with signature。要 yeah。

The best thing is each of these updates will add a log and your notes to your data structure。

 So the number of node will be increasing when you want to maintain all the previous version。

 Yess right。So each new version will give you login new notes。That's not， not， not， not perfect。

 but you， usually， usually it's not a big problem because you you kind of want to maintain this login information。

 You need to have to have some log and memory to maintain this log information。 So it's。

It kind of makes sense。 Yeah，s。WellBecause you you you you have you want to save this v number somewhere。

 So you need you have， you need to have some memory。 So you you。

 you don't you don't waste memory here。 So each， each node contains some important numbers。

 some some on some segments， which will you use you your letter。

It looks likes we don't waste memory anyway， but yeah。

 each new version will give you additional log and notes。不错啊。

You cannot do it using this technique we discussed when we implement this。

 So you cannot just inumerate notes in such a way that the left child is to x one and right at to x 2。

So you really need to have some pointers from each node from from the current node to the children node。

So you you， no， because these two elements have the same left child Yeah so you you。

 you kinda need to implement this whole thing。 So each。

 each node must have two pointers to do pointer to the left child pointer to the right， and on。Okay。

Now， now what what what you can do again， what you condo， You can take one of the version and。

Call any of the functions we discussed the。 For example， you can take the first version。嗯对。

First version。And call some su。这とと。To start from here。啊，吃肉图兔。

So let's just go to here to do a cha some。They calculateco this， then go to the right shall go here。

 coco this。 So these plot pieces some will be done。能宠。Also you can modify every version。

 so this is the full data structure if you remember what of this。

It's called fully persistent data structure。 You can magnify any version of this HR。

 So basically what you can do， you take the first version。

And make another set operation and produce another。You now you have this first version。

 you make this separation， produce the second。What you can do is to take first version again。

Makeake another set produce the second。You can do it like this。

 or you can take this second version and make another a version produce like fourth version。

So you can take any version of data structure， apply any set operation and produce another version of this search。

 you can branch from any place of this version3， you can branch and make another version。

Why you want to do this？ It's a good question。 We， we may discuss it next week。So there are some。

There are various different problem this where you can do something like that。🤢，I will。Yeah。

 we will discuss some of the problems later in this course， but。嗯。Yeah， for now， it's not important。

 So for now it is you may think about it， but like about some。

 some magic source we have some data structure， which you have。

 which is possible to access some previous versions。Why you want to access the previous versions。

 it depends source。嗯。In some problems， it's important to have access to the all previous versions。

WellBecause the logic here kindness the following， so you make some operationss。And。

Then when you have request。😮，This。It's hard to understand that E。 ha， ha， have to explain it out。

Some more explanation。Lets do it let's do it in few weeks sorry maybe next week， maybe in two weeks。

 so at some point we'll discuss some problems which actually uses this property of processing data structures。

Not today。Yeah， it's already you delay it。Okay， so thank you for joining me today， see you next week。

I will。Publish again， I will publish some home tasks， and we will discuss the home tasks next。Next。

Saturday， right？I think we'll keep the same schedule as the previous semester so we'll have。

We'll have lectures on Fridays and home discussions on Saturdays。🎼不と。

