# 【精译⚡算法与数据结构】PavelMavrin p21 p20 A&DS S02E04. 2D Segment Tree Problems -BV1NLB8YfEMq_p21-

。🎼追冲冲冲。🎼。🎼，So today we discuss some two dimensional problems what does it mean basically your standard。

segmentegment 3 is one dimensional destruction。 You have one dimensional array。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_1.png)

Okay。Sorry， a。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_3.png)

And you make one dimensional request。 So you you calculate something on the segment。

 segment is one dimensional thing， right。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_5.png)

So have this fundamental segment and to calculate sentiment from this segment。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_7.png)

But basically life is not always one dimensional， so sometimes you need to take care of some two dimensional operations or even three dimensional operations or even more。

So sometimes you need to answer questions which are two dimensional。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_9.png)

And today we how to learn two techniques， one technique is how to use one dimensional data structure to answer two dimensional queries。

And another technique which will kind up。啊。Make two dimensional data structures in the same way we make one dimensional data structures like special technique。

 not very special， but some kind of， which allows you to make two dimensional structures to answer the same two dimensional queries。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_11.png)

![](img/cabea0d72aeb07c490dd8831d3f3cfce_12.png)

So let's go on first。Now， first let's start the following problem。

 let's have some simple two dimensional problem。 One of the simplest dimensional problem we will learn is the following。

 Let's say we have some rectangles。 So simplest two dimensional object is rectangle。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_14.png)

![](img/cabea0d72aeb07c490dd8831d3f3cfce_15.png)

![](img/cabea0d72aeb07c490dd8831d3f3cfce_16.png)

Let's have some of thatling。啊。😮，嗯。응 그렇지 그렇게 막 뭐。And something here。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_18.png)

Yeah。嗯咩。嗯。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_20.png)

Yes。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_22.png)

And one more here。Okay。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_24.png)

So you have some rectangles on a plane。And you have some requests， so each request is a point。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_26.png)

嗯。We have some points。This wing。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_28.png)

And you need to answer for each point， you want to calculate the number of rectangles which covers this point。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_30.png)

うん。Toup boring here。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_32.png)

YesSo for each point， we want to find the number of rectangles， which covers this point。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_34.png)

![](img/cabea0d72aeb07c490dd8831d3f3cfce_35.png)

So for this point is zero， for this point is1， for this point is1， here is two。

 or this point is zero again， and here is1， here is one to three。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_37.png)

诶 응。에 그지요。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_39.png)

Very a basic problem。啊。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_41.png)

And now we'll solve this problem using technique， which call a sweep light。

So the sweep plan technique works as well so， we need to answer someques in two dimensional plane。

So what we will do， we will reduce this problem to one dimension problem。Its。Get done but simple。

We'll create a line。Let's make a up。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_43.png)

And we will move this line across our pictures， so we willll start from the line in the far left and we will move this line to the right。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_45.png)

![](img/cabea0d72aeb07c490dd8831d3f3cfce_46.png)

![](img/cabea0d72aeb07c490dd8831d3f3cfce_47.png)

And。Each time we will maintain the current state of this line so we will maintain not the state of the plane。

 but only the state inside of this sweep line。B plan。

 basically we will split the plane into some vertical lines。And for each vertical line。

 we will answer the query， that's the idea of this technique。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_49.png)

So what happens when we move this line to the right？唔司。What we what we need to maintain so when we。

Move this way intoさ。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_51.png)

W so when we have some point here and when we move the line to this position。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_53.png)

We will need to answer the query for this point。We need to find the number of segments which cover a number of rectangles which covers this。



![](img/cabea0d72aeb07c490dd8831d3f3cfce_55.png)

Poin。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_57.png)

SoSo inside this line is basically one dimensional problem， so if you look up inside this line。

The response to this line here。 So this is your reply。And this three one。

 you have these two rectangles， first rectangle， second rectangle。

So if you make a projection of this rectangle to this line， you will have some segments。

 so this rectangle is this segment and this rectangle is this segment。And that's your point。

 So your point is somewhere here。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_59.png)

そう。This is this。This light。So now when you need to answer this query。

 you need to answer the following problem， you have some segments and for given point。

 you need to answer how many segments cover this point。Right。

This is a basic one dimensional problem which can be solved using segmentsries。Let's the hope one。

 so again， we will move this line from finallet。Do the right。And each time we find some point。

Which is inside our s plan。 We will answer the queries correspondingent to this point。

 So for this point， we will be able to answer the query。

And we will answer thisqueries using this segmentary because in the segmentary。

 we know how to solve this problem， we know how to find number of segments which count at this point。

How to solve this problem using a segment tree the easiest way is the following。

 let's split all the Y coordinates into some segments。 So for each segment the number of。

Reectangles cover at this point is always the same。

 so we will take all white coordinates of all borders of all rectangles。啊，好吧。爱你什么？Carlors。

Let's take all Y coordinates of all rectangles。呃，都没有的。嗯，可以。嗯。Now this picture is kind of busy。

 but that's fine。I just split all the white coordinates into some segments。

We need session no no no no well need only one segmentary。Again。

 I will split all the white componentss into some segments。うえクええク。And for each segment。

 for each this small segment， I will maintain the current numbers。

 current number of the rectangles which covers this particle segment。

So we start from far left when this line is in far left position。

 all segments are covered by zero rectangles so put number zero in all。Elements of this。S。嗯。No。

When we move this line to the right？At some point these numbers will be changed。

 whether it will change， we will change when we find some border of some rectangle。

 so when we move from this position to let's see this position。我给你。Too many lines on this picture。

So when we move to this position。🎼。We now okay， what is the difference between the this position this position difference is that now we have this rectangle。

 so these segments。Are now covered by one re time also。This here have zero， here here 1，1，1，1。

 okay again， 0，0，0，0，0。そ。AfterAfter we find this left corner of this rectangle。

We need to increase this number for all segments inside this rectangle。对。啊，那我 can we move this line。

To the right， let me find this left border of this rectangle。Whether're playing beastle or again。Now。

 these segments。A covered by one more rectangle。 So we need to increase this number for all segments inside this rectangle。

 So we find these three segments and increase this number by one。 We have here we have 2，1 and1。

 all all other numbers are the same。九九六。M哼。😊，Yeah， we actually don't care about how big coordinates are in this technique。

 we actually may have。Any coordinates， even not integer coordinates。

We just have all these y coordinates put in here， sort them and split all possible y coordinates into some segments。

 So here we have about n segments or two n segments yeah。

 so we have two n different if we have n rectangles we have two n different borders。

 So here we have up to。Two n seconds。So actually don't care about how big coordinates are。

 even if coordinates are big。They still split this line into some2 n segments。别走。Okay。

 that basically also， so when we when we find the left border of some segments。

 we just increase all the numbers inside this rectangle by one。So now now we have this point。

 so when we have this point， we have this state of the data structure in this data structure。

 we have something like。ちて。We have0， then  one，1， one。1，1，1， here。 we have two， Here we have1，1， 0。

00。So this is just this state rotated。90 degrees right。 So we look on our point。

 see in which segment this point by source here， this point is inside this segment。

So our point is inside this segment， this segment has number one， it means that this point。

Its coveredd by exactly one rectangle。嗯哼。😊，Thats all， that's the whole technique。

And when we find the right border of some rectangle， we decrease number by one。

So when we move from this position to this position， we see this right border of the recangle。

 we just decrease all these values by one。Letsこ。So we need the data structure which is which can maintain three types of requests so we need to have。

the following request， we need to have plus or minus1 on second。我。

And find the current page of the elements。그런。Yeah。诶没没有。And we we just have the。

We have even more complicated data structures before so this is very can be very simply prevent using segmentaries or even in fact fan viies。

 you can do it using fan viies doesn't matter so now we just use a segment tree。

To maintain the current state of our sweep plant。嗯哼。So when we again， again。

 what happens when you have the left border of the tri。So you move from here to here。

 you take all segments inside this rectangle。So here you have some segments。

 you have plus one for all these elements when you see the right border of the rectangle。

Can you move from here to here。You need to take all segments here and make minus1 for segments。

And when you have a point inside your sweep line。You just find the current value of the segment correspondent to this point。

Now you can find this segment in using binary research。 it's simple。 So so when you have the point。

 you need to find the segment correspondinging to this point， you can do it using binary research。

 Now again， you have all these wises in in a big sort terrain， So you just find。

Your Y coordinate in this sorted array。And you will find the index of this segment。It's very similar。

So， that's all。And what will be the total time complexity here。

 So first we need to first we need to sort all this y sort of this X and so on again， first。

 you need to sort all the y coordinates to to find this。

Set of segments then you need to sort all possible x coordinates because you want to apply the separations in the folder so you want to apply operations from left to right so you can put all the x coordinates in another big array and sort this array by x so now you can go from left to right and apply all the separations in in order That's all So this all takes you an n log time both these two sortings。

And here you。Actually， you can make both des in log and time using segment3。

And you have at most two ends such events， so for each rectangle you have one event when you have the red border and another event when you have the right border。

So you need to make up to n operations。On the segmentary， each variation goes a loggan time。

 so total1 complexity will be a loggan。고。That one thiss one of the simplest implementation of the sweep line method so simply simply application of seat or sweep line method。

 I don't want to make up an implementation I believe you can do implementation research so implementation is pretty simple。

 you just sort all these wises， get all these segments。

 make a standard segmentary then get the list of all possible events。

 sort this list by x and then apply this events one by one when you see this event。

 you add one when you see this event you。AStract one and when you see this event。

 you find the value and put this value in the result it's quite simple implementation after after you implemented the second traits actually it's actually very simple。

O那そ。W， that's one of the easiest problems solved by Swland。

Sweep line method is actually very powerful powerful， you can make a lot of values。

Operations using S line， how to see if your problem can be solved using Sp line basically what you need to solve is to check if your problem can be solved in one not sorry if you if you can solve the same problem in one dimension So if you have this one line。

You need to， you need to think how to solve this problem when I have one this vertical line。

 if you can solve this problem inside your vertical line， then you think is it possible to。

Change the current state of data structure when I move from one vertical n to another vertical N。

 you need to see what changes need to be made to your data structure and to see if these changes can be made using your segmentary。

If you can make this change using segment3 and you can make the separation inside one vertical line。

 then you can perform a sleep by method so you just its right from left to right。

Apply desperations and that's how you supply methods doors。

Let's solve one more problem because it's kind of trickying。

I will leave some more problems in the home task again， we have home task。

And we will discuss it tomorrow。Last time we had only one submission， it was kind of said。

 so I expect to have more submissions because。When I don't have anything to discuss。

 it's kind of boring to have discussion of homedesk when I have no ho。ああ、そう。

And let's guess one more problem。あ。It's kind of classical problem about sweep line and this technique The problem is from again you have some rectangles。

And you want to calculate the total area of the union of all these rectangles。没有。エレ 아オ。十にお増えてます。終。

it's kind of boring to have area of intersection of electrons so when you want to calculate area of intersection of electrons。

 it's kind of boring because the intersection of rectangles is always rectangle。You have two littles。

The intersection is always a rectangle， or it is empty。そ。Area of intersection is kind of boring。

 so but area of union is it。Much more interesting。So in this picture， for example。

 I will ruin this picture， I want to complete the area of this figure so I need to have this plus this。

 plus this and also this。And also this and this and and that。啊。So I could。The least figure。

This is clear， I don't think it's great， well， it's fine。

 so I have this strange picture with hole of bit center。😊。

And I want to calculate the total area of this figure。Let's go， so how to implement this。Again。First。

Let's solve this picture。 Let's solve this problem in one dimensional case。 sorry。

 if you have one dimensional case， So you have only。Only one light。

And each one one dimension or thing assignment， Yeah， so you have some segments。On this land。

And you want to find the total length of all points covered by at least one cent。

 So you want you want to calculate total。Total length of this union。S sign find some。Makes sense。Yes。

 you can do it using segmentary with two operations。

 our first operation is to assign value so we will assign one to so if you have zeros here and ones here。

Then what you need to do。 Oh actually you don't need you don't need once。

 you you know that doesn't matter。 So you need to assign one。

 let's let's let's think that all segments have equal sorry if all these segments have equal。

 So you split your。Line into segments of equal length。

 So each each small segment have length equal to one。

 So you need two alters assign one to the segment and calculate the sum segment。こ怖。不行。

And you can do these two operations using segmentary。Great， we discussed this。啊哼。

So assignment and some are good operations， they are associative， they are distributive。

 what else mean that's all so you can make a segmentary with these operationsations with laser propagation like we discussed。

Perfectly normal， it will work。No problemラ。No， actually， if you have different lengths。

 let let's see in this problem， we actually have different lengths of these segments。

 So in this problem， each segment have some length。 So we don't need this sum， we need to。

Something different， we need to sum of all lengths。Llance。Whistle lemon。

Besides to that they have equal to one， so we need something like a v。开。

But it's just a small tweak to your segmentary， can you can make this function in your segmentary with no big its no big difference。

 not just when you apply operation assign one to the segment。

 then this sum will be equal to sum of lengths of all segments in your sub， makes sense。

So you just maintain the sum of all segments in your substrate it simple。

And when you make assign operation to your segment。

You make this sum equal to the total length of your segment。嗯。Yeah。

 that's a good question what happens when you remove rectangle？

This solution is good in one dimensional case。It's kind of tricky to transfer it to your two dimension picture because when you move from one line to another。

These ones and zeros will be changed in some strange way， right？So when you， it's easy to add。

More rectangles。 So if you add， so if you， if you find the left border of the sub segment。

You just assign one to this segment， right， take you can add another segment to this picture。

 So you add another segment。 you need to assign one to all elements of this。呃，sd and。

But when you find the right order of the segment， you need to remove the segment and when you remove the segment。

Some elements should became one and some elements should become zero， so like like here。

 if you remove this rectangle。You need to make zeros in this position， but not in this position。

And it actually may be complicated， so if you have a lot of small segments。And one big statement。

So now you have all elements equal to one， we have here all elements are once。

But when you find the right border of this rectangle， so you need to remove this deep segment。

You need to put zeros in these positions。And we don't know how to do fast because it's it's kind。

 it's it's strange expression。 It's not segment operation。

 We need to put zeros in some random positions in our array。 It's not a segment operation。

So we need to find another one dimensional solution so this one dimensional solution is equal in one dimensional。

 but it can be transferred to your problem because you can move from one solution to another solution。

So we need to find a different solution。Let's move back what we can do， what we can do。

 we can increase by one and decrease by  one， let's use this solution and try to adapt it to our problem。

So， we will。Instead of having these ones and zeros。

 we will have various integers and this integer will be the number of segments covered at this point。

 so here we have two。Now it is simple yeah so for this picture we can change the picture when we move from one line to another line。

 we can we use like the sample so when we have left border we increase the segment by one。

 when we have the right border， we decrease segment by one。

But now we need to find a way to calculate the total length of all non zero elements。

 so we need to find。M oh elements are non0ソ。Greatト than0郎。Yeah。That's what we need to find。啊。

So we have， we need to have a segment three with two operations first operation is。

Plus minus1 on segments。And another equation is to find the total length of all non zero elements。

That so。But that's the problem we need to solve。And this problem actually can be solved using segmenting。

Any ideas？嗯。What's the problem here， Problem here is that。Now again。

 some elements may become zero or on zero in random so again again。

 if you have the same picture if you have the same same picture， you have a lot of ones。

 but when you remove this， I' you have some zeros。Inside the segments and the position of the zeros is kind of random。

 so we kind of need to be able to perform this separation on some random elements。But we can do it。

Okay。The idea about how can do it is very simple。 let's change this problem。 So this sum。Is actually。

So if you want' to calculate the sum， it is the same is the sum of all elements。

Minus the same sum of zero elements， so minus sum of then I for this I equal equal to 0。Okay。

So this service constant。一。So all we need is to。Find the way to calculate Lisa。

So we need to find a way to calculate the total length of all zero elements in our area。

And we actually did。About。About the same data structure in some home discussion。Again。

 let's have all elements have length equal， so if all length equal to one， so all we need here。

Is to find the number of zeros。Number of elements。以コー2 zero。Can you do this segment three。

 so I need segment three of two operations first separation is to increase or decrease the segment by one and second operation is to find the number of elements equal to zero。

옆 let do some。Yeah。So if you watch my code forces lesson about segmentsaries。

 I discussed almost the same problem and if you was on on last Qas discussion we discussed。Almost。

This problem last Saturday。嗯。Oh no， no no， let me it wasn't the first that is yes I believe it wasn on the first capital。

嗯。Okay， give me some more h， so here is very simple， all elements of this array are not negative。

 so all elements。And these three are always no。嗯。啊。Yeah good good thinking。

 so if we want to calculate number of zeros after we make minus1， then on the previous step。

 whether we make up before we make minus1 sorry。If we have minus1 and after this minus1 operation we need to find number of zeros right it means that before this separation we need to know the number of ones so we have summary array then three。

So if you apply minus1 operation to this array， you will have this array。And in this array。

 after you play， you want to know the number of zeros， you want the number of these zeros。

It means that in this segment you want to know the number of ones。

 so I want to know the number of ones。だずこちたや。That's actually， that's actually a very nice idea， so。

So in this array I want to know the number of zeros in this array I want to know the number of ones。

Now let's think about what number we need actually we actually actually need no only one number in this for each segment。

ううん。그。And again， if you apply minus1 to even more so， let's have one more operation。

So if you have one more minus-1 operation。 So here we have 3，2，4，2，4。

So to be able to know this number of ones， so in this array。

 you want to know the number of two sphere。So you want to for this three， you wantt download。や。

That is very simple， all we need to know is the number of elements equal to minimum on this segment。

So we will maintain we discuss this in process session， we will maintain the pair of values。

 we maintain minimum on the segment and the count of minimums。Yeah。So say it's， it's number。

Of elements。你こト見。O。嗯h哼m。😊，And we can reculate this value when we apply this separation。

When we make plus or minus1 to the whole segment， we will just increase or decrease this minimum。

 this count will be the same。And we can reculate this pair from the pairs of our children because this is actually us no。

combinationbination of these two segments is some associatedci function， if you know。For one segment。

 for the notes， if you know minimum here， minimum here， count here。Co here。

 then using these two numbers and these two numbers。

 you can recalulate the minimum on the whole segment and the number of minimums in this whole segment。

嗯。Let's错。And you can just you can just use the same brush to calculate this sum of lengths in the same way。

 so instead of this counter we will calculate not the number of minimums， but the total length。

Of elements equal to minimum。So we calculate the minimum on the segment and the total length of all segments。

W we have this meal。And that's all and you can rec this number when you make a contaminat of two segments and you can rec them when you apply the separation。

 so when you apply the separation， again this minimum is changed by this counter is not change and when you combine two segments into one。

 you just take the minimum of these two minimums， if minimum is different， you take one counter。

 if minimum is the same， you take the sum of these counters。好。嗯别错。

And now we take this data instruction。And apply to our two dimensional case， so we just， again。

 we move from left to right。Each time we maintain this picture。

 so we maintain the number of rectangleals carrying all segments of our segmentary。

And when we when we have left border， we increase by one。

 when we have right border we decrease by one。 and each time when we move the。

Will we move our sweep line from here to here？So when we move sweeping from one position to another position。

 so between two events。You just increase your final result by the length of this。So this is Delta X。

And it should be multiplied by the total length of four segments covered by at least one rectangle。

So you take this。Forula， so you take the total length of all segments。

 minus length of all segments north covered。Get the total length of four segments covered by at least one rectangle multiplied by deelta x and add to result。

あそ。我的送。Okay， this。This one is not very。Three well tasks about sweep line most of problems about sweep line are positive so so you just again。

 you just go from left to right and see what operationss you need actually for your segmentary。

Usually it's kind of usually if the problem is solvable by sweep line it's kind of obvious so you see what operations do you need。

 you see if it is possible to build segmentary operations you need。

 usually it's kind of trivial that you kind of find what operations you need。

 see the operations are associative so you can make a segment3， make a segment3。

 That's all sometimes it's kind of tricky like here。Last part again， should， which part is lost？

Again， we have the following segment three， we have the segment three with thirds plus minus one on the segment and find the total length of all segments with value at least one。

嗯哼。呃蹦。Soょ whatです。Now we use this data structure to calculate the total area。

 how we calculate total area， we go from left to right。

And each time we move our sweep line between two events。

 so we have a here and some event here between two events。

 the state of this data structure is the same so well。Between two changes of the state of theter。

 we have some segment when we have the same picture here。

 so we just take the length of the segment multiplied by total length of all segments covered by at least one rect。

Okay， again， you take the segment between two events So we have like event here's ruin this picture once again。

 So we have。Let's go。 We have event here and another event here。So inside this street， we have。These。

These retangleles should be added to our result。So this area is the width of this area multiplied by the height of this area。

 the width is just the。Difference of access of these to elements。

And with height is just the sum of all segments， which covered by at least one of the channels。

So I calculate this sum multiplied by delta x and have the total area of this。unionion of effect。

 and then you add it the result and the on。嗯。ち。Approximate obvious maybe in the end of the course will toxs。

Maybe only some basics。We will see。h，Okay， that's what was the first part。

So this is the first technique。😊，Which is widely used when you need to solve some problems about some two dimension problems using segmentries。

啊。Oh let's'ss let's solve one more。One more before I raise this picture。

 let's solve one more problem， so let's say if you have some picture of rectangles。

 you have some number of rectangles。And again， you have some points for each point。

 you need to answer how many segments cover this point。

But you don't have all these points in advance， so you are given these points right one by one and you need to answer the question for each point in online。

 so you're given some point， you need to say for this point how many rectangles covers this point。嗯哼。

So the same problem like the first one， but we don't have this point or all points in one。

 so we need to answer all these requests one by one。So what can you do， you can do the phone。

 you can make the same sweep plan technique so you can form this sweep plan technique。

But do it in a persistent way， so you instead of having just simple segment。

 you make a persistent data persistent segment。And now when you have a persistentence segmentary。

 you kind of remember all the states of this segmentary。So when when someone asks you手上不做，所以点you。

You just run your sweep line from left to right and remember all the states of this sweep line。

And now when someone gives you some point， so someone gives you this point。

And asks you what is the number of rectangles covers this point。

 you find you look at your your system data structure and find the state of the sweet line corresponding to this x coordinate。

 So for this x coordinates。You have some state of the sweep line。

 so youll find this state of the sweep line in your persistent data structure。

And for this state of this reply line， you answer this query。

So if you want to answer some queries in online， you may just make a sweep line。

Before like in precalculation， you make this sweep line。

 remember all the state of the sweep line in persistence segment。

And then when you need to answer the query， you find the corresponding state of your sweep line and get the result from this state of the sweep line。

That's basically when you may want to use some persistent data structures。

Mostly persistent research used in some two dimensional problems， you have two dimensional problems。

 you use one of the dimension as like time of your own persistent data structure。

So all difference different lines correspond to different states of your data structure and when you need to answer query。

 you find the state of your data search correspond to this vertical line and then find the result of your in this state of your data structure。

呼呼。Okay直そ。That's all about threeing I want to talk about。

 so we'll have some most replying problems in the home task plot。I think we get all the basics。

Now I want to move to next problems because oh bought。Next topic。啊。Let's try to。

Let's try to build two dimensional segmentary basically。So I try to show you technique。

 which will allow you to modify your data structure to make it into two dimension dimensions。

Baically not only two dimensions， you can add any dimensions to your discharge。啊。哦。So again。

 what is the segmentary， segmentary is data structure， which like very basic data structure。

 very basic segmentary， which one we do make two requests， so you have some segment。

I just love to write small segments here。 So you have some array and you have two requests。

 first request is to set a value of someone。嗯。Let's make it increment like in just for simplicityistic so increment。

value in I J by B。ThisI gloss call。I sorry I just added second dimension。

So it's basic segmentry and you have some salmon segment。

Which returns the sample I from from left to A's one。

So that's the basic one dimensional segmentary Now we will try to make the same in two dimensions in two dimensions you have two dimensional rate。

そかでしま。You have this table， so this is one。This is true。In two dimensions。

 we have this two dimensional rate like table and we have okay， we have the same request。

 First request is to。Change the value in some cell of the tables increment。I J V。

Which will increment the value of some element。thisて。And the second。

Operation is to find sum in sum two dimensional second。

 two dimensional segments is it rectangle okay， so we will have operation some。

On some rectangle of this。Two dimensional array we have let's left left， right to bottom。

You will return the sum of sums for O iPhone from。Well we have to Ar one for O Js from。

P from top to board to minus1 a I。We are simple transformation right。

 so so here we have one dimensional request， here we have the same two dimensional requests。

 so we change change the value of some element of two dimensional rate。

 so we can take any element in my an。Plus feet of its element， or we may take some rectangle。

Then find the sum of this recangle。So this is left， this is right， this is top， this is bottom。哼。

I keptt control hold， right？Usually the first index is there role of the tno。Just like this。

And here's from left。Not a big deal but it just。Just to make it clear。Good。Now。

 how to implement two dimensional series？Very simple data structure。Let's have some。

Two dimensional array， so let's have like two dimensional array， 4 by4。Yeah。

This is your two dimensional array。There are some numbers here， like 5，4，6，1，3，7，8，6，3，2，7，1，7，5，3，6。

Is it random enough。예，看懂。So this is your two dimensional array。Let's make first。

 let's make a segment three over one of of the direction of this。 Let's let's make so let's take。

The first indices of this array and make a segmentary or this first dimension of this array。

So we'll have something like this。 So we'll have this。不了吗。く。Okay。か。

So this is a segment three over the rows of this two dimensional array。

 so we have four rows of this two dimensional array。

 let's have a segment three of size4 so for these four elements。

 each element corresponds to one row of this。都里面说的。Let's anate them。Okay。

 let's have this index what0 let's have this one。 store free。45s。So this is your first segmentary。

Now， let's see。Each element of the segment trick corresponds to some segment of your array。 Now。

 for example， if you take this。This node of your segment3 corresponds to this segment of your array。

 so this node corresponds to these two rows of your array。Basically， the element corresponds to this。

😊，Three of yourarrow， so it's correspond to this。Two bottom rows of here。Now， what we'll do？啊。

We will put into this node another segmentary。Which will take care of the second dimension of your so in this note tool。

So this node two。Will contain inside of this node another segment tree by another coordinate by way person。

 so you take the second dimension of your dimensional array and make another segment tree。So么开不开。

Let's contract this。Yeah。So inside this node of your first segmentary actually is this segmentary。

And inside each node of this segmentary is some segmentary by this second coordinate。Good。Again。

 you're too quiet， it's not housework cancer you just。If everything is clear。

 just say everything is clear everything 30 seconds。什么。啊、。In this again。

 each element of this second segmentary。Let's number it。嗯。对。

Each element of this second second matrix responds to some second by the second coordinate furorraer if you take。

Let's use some more colors let So if we take some elements， let's say this one element。So， this note。

Of this segment corresponds to this segment of your。

And if you look inside so this segment3 is inside this node。

 so this node corresponds only to this strip and this node correspond to this segment of this strip。

 so this node corresponds to this。recectangle。嗯哼。That's all so in this note。

 we will put the sum on this rectangle because these node corresponds to this rectangle of the array。

So also here we have value equal to。517。So in this note， we will have value 17。

This 17 is the sum of all elements inside this rectangle。

 this rectangle because this don't correspond to this segment and this note is inside this segment3。

 this segment three corresponds to this segment， so this note corresponds to this segment of this segment。

 so it's correspond to this rectangle。And so let's feel all elements here。

 so here we have three plus zone1。Here， we have 7。You we have ba。D again。Here where I' said looking。

My random generator is not very random， okay？😊，So I here and filter for here。

Let's change something distribution。Just wait at now。More random fine。

Just to make it look more at them。嗯。Thats so we again。

 we make a first segmentary in each node of a segmentary， we put another segmentary。

And now we have this segment tree inside the segmentary and each note of this inner segmentary corresponds to some rectangle ser rate and it contains the sum of all elements inside this rectangle that's all。

How to implement this is actually quite easy to implement。😊，嗯。B code we need is some not here。

 what is the easiest way to implement segment three is to implement it inside the array sorry。

Index yes make indices for all elements and make the array and just put this node in the array of like seven elements so each element have some index。

 just put this element in using this instance。And now， inside of each。Each of these arrays。

 you need to put this segmentary， these segmentries also can be prevent using some using an array。

 so you have array of seven elements inside this array of cell n。

 So actually you need to maintain one array 7 by 7。嗯。So make two dimensional secondary。

 basically two dimensional array。So here you have array of arrays。

Just have a two dimensional array so you might just array 7 by 7 and put these numbers inside these big7 by 7 array。

 That's all that's how you implement to and now to how to。How to implement operations？Quite simple。

 so let's have some brush shot。Let's have some duration， let's have transspirationration。

 so what happens when you want to implement some number？那嗯。So's。

 let's say like you take some number here and you want to make plus one to this element。

What you need to do， you need to find all the elements which contain this element of your egg。Yeah。

 we put segment three inside the segment tree yes West Coast customs approved， yeah， yeah no。

 no so what happens when you increase one element of the area。

 you need to find all the rectangles which contain this element。How to find all the rectangles。

 very simple。Soよ。First， you take the first segmentary this first segment。And find all the segments。

 which contains this element。 So we need if， if if this rectangle is contained this element。

 it should contain by this first dimension of hearing。So how to do it very simple。

 you just make this same operation as you make in the regular symmetryy， so you start from the root。

And find all these notes。On the path from the root of this element。啊哼。

So we take all these roots or all these nodes on this pad。And each each of these。呃，n。

Contains some strip， which contains our this first this contain this strip。

 this will contain this strip， and this one contain this strip。嗯哼。

So we need these signalss to be updated。In each of these three nodes。

 we need to update rectangles containing these elements。

 So how to find all elements containingangle this element。 when we go into this sub。And to。F。

And find all the elements containing this element。 Okay， we do the same procedure。

 We just take all the notes on the path。From the root。都で小了。Not please。 not please。So。嗯哼。😊，So first。

 we make the standard procedure for the segmentary to find all nodes contained this element in this outer segmentary。

And then in each of these node， we call the same recursive procedure to find all nodes in this inner segmentary。

嗯哼。😊，不。And in each of these segment three， we just increase the value by one because this element will be in total sum of each segment will be increased by one。

 So we have plus one here plus one here， plus one here。What's the whole plan。酷。

So what will be total time time complexity， total time complexity here will bit hormone。

 so we need to find this nodes here well have up to log n node and in each of these nodes we need to run this。

Aperration， and in each of this operation， we need to update these loggan nodes。

 So we have logan small trees in each of these logan trees。 We need to update logan nodes。

So it will cost a log n multiplied by log n， so the total time complexity for the separation will be log square。

こ。别走别走别走别走。到。What about the second direction， how to perform the second direction again we need to calculate the sum on sum。

Oh， this picture is going be O， let me just remove something from this picture。如。どか？Now。

 what happened when you need to colate on some rectangle also in this second equation？

You are given some rectangle， let's say something like this rectangle。

So you have this rectangle and you need to find the sum of all elements inside this rectangle。あ。

So how to do this using this structure again， you make the same procedure like like in the regular segmentary。

 when you calculate sum on a segment， you make this recursive code and find all the segments which combines into your givencing。

So you start， again， you start recas here， go here， take this segment， go back， then go here。

 go here， take this segment。So this node corresponds to this segment。

 this node corresponds to this segment， together you have your segment by first con name。

And then inside each of these nodes， you call the same procedure for this inner segmentary。

 so inside this inner segmentary， you go to， you take this node and this node。嗯哼。😊，ほ。

So first you make recursive procedure in this outer segmentary， find these two nodes。

In each these each of these dons correspond to some strip of your dimensional array inside of this。

No， you call simplicity by wipe ornet so you find these two seconds。

So you have these two nodes in each of these two nodes， you find these two segments。

 so they will correspond to some to do this rectangle， this rectangle。

 this rectangle and this rectangle。Now we have some of these of stringtangle will just combine into the your given rectangle。

Let's so again， this recur procedure works in logan time like like before。

 and this works also logan time。 so total time complexity will be again log square。啊酷。

And that's how you make the dimensional structure basically and you can add more dimensions to your data structure using this so this con technique to add more layers of your data structure just some layering technique so you have first layer of data structure in you have the second layer if for example。

 if you need three dimensional arrays。Then you can add another。Segmentary on top of this。

Like segmentary by Z coordinate， and in each note of this segmentary by Z coordinate。

 you have all these two dimensional instruction。嗯。And again， to apply these deerations。

 you need to make a request in this outer third segment and inside each of the node。

 you make this two dimensional request。So total temperature， you will be local cube。故。

Can you make this one？In implementation， I think you can do kind of。

 I I don't know how I don't know the best way to implement this。뽀뽀뽀뽀뽀로뽀뽀。I think you make some。

Cold for the segmentary and then put segmentary inside of the segment。

I'm not sure how to do it using C+ templates， I believe you can do it using C++ templates。I'm not。

Such a good professional about C++， but I believe you can make it just so the same code right inside the same code。

I'm pretty sure I can it in any object or programming language just make this class segmentary and as an element you put another class of segment three。

 I believe it's possible in mostly all programming languages but。

If you're talking about efficiency here。I'm not sure old about it。

I think it it will be kind of efficient。 So if you just make a segmentary and using a array and then。

Make a segmentary and put as an element， another array， just make a array information。

It should work just fine。I believe he can do it so。He， you can do it as an exercise。

 just take your favorite programming language and try to implement this in。

In the simplest possible point。We have one more time， yeah， we have time。

So let's go talk about other instructions。😡，Let's try to apply the same technique to all other data structures we discussed on previous lecture。

 so let's try to apply it to feic trees and to spa tables。よ。It is quite easy。

 we just do all the same thing， but in fan viies and then in spa tables， for example。

 if you have two dimensional fan batteriesies。How the usual Fenix3 works， So in just regular phix 3。

 you have this array F and。If。Of I equals2。It goes to the sum of OJ from， from P of R to I。

Like we discuss。Last week。有。What happens in- it's one dimensional it's one dimensional thing。Goワデ。

イトリメンションケース。We will do the same but twice， so we'll have two dimensional standards。F呃I J。Oh。

And each element of this two dimensional array will maintain like again。

 we need to make feic3 or feic3 yeah so this first dimensional is just feic3 by y coordinate。

 second index is the feic3 by second coordinate。So each element will maintain the sum of all sum。

I need two more indices。X and y from P of I to I and y from P of J to J。X， Y。我没事。可能。

This is new market just from the books。こ。They just。They just oh， this looks sorry。

This this element of RAF will correspond to some of all elements inside the cell， so this is I。

So this is p of I， this is P of j。So this element of RAF will contain this sum of elements in RA。嗯哼。

And now how you implement this operation what operations do we need in the family tree？嗯，哼哼。😊。

Just write。So in three。We need to find the sum on sum。So the regular independently fee。

 we find the sample on the segment。Yeah， using two sums on the prefaces。

 so we have this prefix minus this prefix will equal to the sum of on this segment。

So in two dimension case， we just do the same trick twice。Well。

 we need to find the sum on some rectangle。没。We first split this rectangle into two。

have this element， minus this element。おほ。And now we split both of these。

Pfis rectangles into like two corners or so。 So we complete some of of this rectangle like。

Difference of。This rectangle minus this。 So we have。It's to complicate the future。So we take。This。

Rectangle plus。Mus this。This will give you the sum of this area。

And then we need to subtract this area and add this area。嗯哼。😊。

And this will give you the sound on this right。So when you want to calculate sum on this rectangle。

 you kind of want to split this rectangle into some sum prefies it is like two dimensional prefix sums。

 something。So you have two dimensional graphic summary just sum all elements to the left and to go。P。

And up so you have this sum minus this sum minus this sum plus this sum。

 it will equal to the sum on this。あそ。And now。You want to be able to calculate the sum on these rectangles like this。

 so I given this point。You need to be able to calculate some in this area of your dimensionary。

 how to do it using these precalculated sums again， you doing the same way like infinries。

 but do it twice you start from this point， this point contains the sum sum segment of sum dimension some table。

You add it to your result。And then move to this point。When you move to this point， you have， again。

 you have some sun。You add to your result， move to this point，And so now you move from this。

 I coordinate to this。So you move from here to here and calculate this here。

 you have some sum of this rectangle plus this rectangle plus this rectangle。

 and you move here that this rectangle plus thisangle this。本とそ。

So the code is again I just write the code Yeah， so the code is symbol。

 So if you start from point I J and you want to calculate them。你你你十三轮你写呗。So you start from point。

 let's say like here， let's have x equal to I while。X is at least 2。This is look again。

 this is one dimension case。One dimensional case forlips。One dimensional casell it we just E。

A result of x to your an x equal to x and x plus1 minus1。And if we want to do the same inment case。

We just make the same well loop twice， so we start from x equal equal to I。

I can do it in C plus plus type make get a4 loop， but I will not do x0 and here make another loop y equal to j。

While y is exactly0， we add。Where to x Y？And then move white。Y and y minus1。不错。And after this， while。

 we remove X。Like this。出以。That's all just have the same codes applied twice by first coordinate by second coordinate。

 and in the end you will have the result。一没见。こ？Practical have some cemeterries。

Basically all the examples we discussed all I believe in the first lecture。呃。Op。闹。Finally。

 I want to discuss the two dimensional sparse stas also two dimensional sparse staples。Again。

s's how the regular parrsse tables work so in the regular sparsse tables。Yeah。In the recordss per。

 you have you have table。M I G， and this contain take minimum on segment from I to I。

I plus two power minus oneね。Again， we discussed it last lecture， right？啊。

So this is a regular spars table。 You have this。A ready。

 this array contains minimums on different segments of your array and you pre connuation。

In enloggan time。And also query。In course系。So this is one of the my case。In two dimensional case。

Again， we will do all the same thing， but twice。😡，So we will have not two dimensional array。

 but four dimensional array。So we need four dimensional array to maintain all， all all the ring。

 So we'll have to。是。I need four letters。Okay， let's have I J， K and。It will be minimum。On a segment。

From I to I plus2 power J minus1 by y coordinate by by one coordinate and。

K plus than k2 k plus2 power L minus1 by the second coordinate。

So I need to maintain this four dimensional array to make my two dimensional parts stable。

How fast can I calculate I calculate calculate this two dimensionary in the same way I calculate one dimensional one dimensional sparse table I just again I just do the same twice each time I split my segments into two segments by one coordinates then I split into segments by second coordinate and then recalulate this minimums so I can。

我。I can calculate all these minimums in linear time by the size of this。

 so this rate is size n squared。诶。Lo Square。So here I have this log square in this precolc time like like this works in log square time also。

Ohpevis。So here I have this log square type complexity in reccoculation and also memory complexity will be increased in instances。

 so this amount of memory I need for this data structure is again it's n square log square。

Because I need all these。一分那 different分的电脑。And how to answer the query again。So to answer the query。

 you have this rectangle。You need to cover this rectangle with the rectangles from your array。

So again， you find this segment by the first coordinate， cover the segments with two segments。

And then you have your segment by the second curve H。

 so you cover this segment with two segments here。And now you take these two segments in each of these segments。

 take these two segments so you have these four rectangles。So you have this first rectangle。

 the second rectangle， the third rectangle， with four rectangle。

 and these four rectangles covers all your different rectangle。 So you get minimum here， medium here。

 minimum here， medium here and find the total minimum in the York。recangle。Thisそそうそうこ。嗯。🤧W。Okay。

That's basically all I want to discuss today。 I have some more。Problem， if you。We discuss them。Okay。

 we always has one more problem， put？嗯。Yeah。啊，他点有点饿了。

Let's have one more problem just to show you another technique。给饿死。's not the kicks actually。

It's also kind of important to Google。We'll talk about this technique later in this curve box。😡。

Let's stop it now。Let's solve the phone problem。啊。The's called iron。 It's。

I don't remember the name of this problem。 Let's go on。 so the problem will be following。

 so we have some points。Oh。Oh。嗯。あとね let's have8 points。So let's have some points。And。No。

 this point correspond to some objects， right？😡，Let's make it more。More practical look like。

Let's have。でた。告诉他。Every time somebody asks， what is the practical use of your data structures let's let's find some practical use for this expression lets have。

Where you have some。Online store。 So you sell something like。What can you sell？Hello。

Some computers test boring。So we have some computers。And。This the boarding what do you sell？嗯。Trees。

嗯。I it's something complicated to have various types of。嗯。Give yourself something not very boring。

 not very technical ex。So let's have something fighting。Csstone it's not funny。Aobics scoop。

Donuts make sense， oh make makes sense this sold， okay， you sold donuts。And you have values。

Various types of dons。Good。And each donut is specified by two parameters。ふ。😊。

I need two parameters don't obviously have two parameters is size of dont size of the hold down。

 right？😊，そう。So each donut is obviously specified by two parameters plus this outer radius and this in the radioius here。

It makes sense。嗯。啊，我差都系。How to measure a flavor is an integer it's kind of compate so need I need two nu parameters。

那吃过着呢。啊。So you have various， various size of donors and so each you dont specify by the。

 So let's call them X and Y the simplicity。So you sell some nodes。

 it has two parameters and each dont specified by these two parameters and you kind of want to be able to select dons in the given constraints。

 so you're getting some constraints on these two parameters and you want to find all the dons which satisfies your constraints。

还有 this事。why this X？So someone give you some constraints that x should be between x1 and x2。

 and y should be between y1 and y2。Price， price is nice， Radius and on it's weight and price， yeah。

 makes sense。知吧。액셀2놈벨 parameters 만들。Okay， and you want this first parameter to be inside this range。

 the second parameter be inside this range。And so is the whole problem。

 find all the objects which ss this construct。Or find any object or find number of objects or find anything。

So do something with this range of objects。So how it looks when you have two dimensions so can you can look at this as a two dimensional problem。

 so we have this two dimensional plane， so each object is some point on this dimensional plane。

And you want to find all the objects inside the rectangle， so you're given a rectangle。

And you need to find all the points inside this rectangle。That's all。

 that's how this corresponds to reality， actually。that's actually。😊，Kindly useful。够。

So how to do this using the segmentaries。First of all， you can do it using persistent segmentaries。

I will leave you as an exercise because were too late， but you can you can。

You can answer this queries using the persistent searies。You may think about it。

 we also talk about sec persistent trees today。I want to show you another technique。Actually。

 persistent three？😊，They're very powerful to for operations like this。Why。

 I don't think this part okay。はい二と目ですか。Let's。Let's make a segmentary or first or X X as exor。What's。

Find the X coordinates of all pointss。Okay。不说。And build the seary over this exorance。Yeah。My always。

Yes。No。Inside each of these so again， each node of this segment corresponds to some segment by this x coordinate。

Inside each of these。No， we will maintain all the points inside this segment by Xnet。

We'll put not one value in each node， but all the points which belongs to this segment。

And we will maintain this point sorted by Y coordinate so lets。

Let's just enumerate on by y point for simplicity， so this will be one。と。Was free。Fs。5。6，7。

So I just merit them by why coordinate for simplicity。So in each node。

We will maintain the list of all points inside this segment by X coordinate。

 sorted in by the Y coordinator。So here we have lists of five。So here we have simple lists。3，7。2，6。

8 and 4。In the second layer， we will have lists of two elements。

 so here we have lists of1 and five sorted by x。 so first we have1。

 then we have five Here we have three and 7 Here we have2 and6 Here we have four and8。Again。

 each of these list is sorted by white coordinate。Here we have all elements from these two list sorted by white coordinate。

 so we have one， three， five， and seven and here。That's fine。 Okay。

 we have all old number here or even number here。 Okay， here we have2 C6 and 7。

And you look careful in this。有说。So let's maintain this segmentary again。

 this segmentary by each note of this segmentary contains not one value， but a list of values。嗯哼。

Yeah， this looks exactly like like what happens when you make a meer， you can call it Mercer treats。

 not very common but。Again， here exactly if you look about how merge that algorithm works。

 it works exactly exactly like this you start from the single elements each time you merge to two arrays into one search array and so on。

 so you can build this segmentary in endloggan time。So n loggan time。You can build all these lists。

Again just take bullet list from your children and make a merge operation。

So total total total time will be linear among all the size of this this。

 the total size of this tree is analog loggan。Okay。Now。

 how this tree helps you to answer your question Q queries。 So yeah， you have this querying。

Qu is a rectinal， right？So you take this rectangle。And make a query first。

 you make query over first accessory for you make take this。X1 and x2。

And you try to make a regular segment to request on a segment on a string。

 So again instead start recas here， start go here， go here， go here here。

 You need to take this segment。

![](img/cabea0d72aeb07c490dd8831d3f3cfce_61.png)

So this segment isn inside。And then you go back， back， back， take this segment。

 so this segment is supposed。And now you find all the points which are inside your segment by the first coordinate and now you need to inside each of these nodes you need to find all the points which are inside your segment by the Y coordinate so here you get you have this。

Let's， let's have an hour mark。So this is first calculate， this is second co。

You need to find all points between these two points by the y coordinate。

 but they are sorted by y coordinate so we can use binary the search。

To find these two borders in this sort terrain。So the first border will be here。

 second border will be here， so we need to output this free。As a result。

And now we go here and see that the first border will be here， second border will be here。

 so we need to output these two and forth。Mmん。😊，So again。

 we need to find all the points inside the rectangle first we find all the points inside the segment by X coordinate just by using standard up regular secondary request。

So we start from the root and apply the same recursor procedure to find these two nodes。

 so these two nodes corresponds to this segment by x coordinateate。And now inside each of these to。

 we need to find all points inside this segment by y coordinate。

But they are supported by white coordinate， so we make two binary researchers to find these two points。

And all elements between these two points。Actually correspond to some points inside your rectangle。

嗯哼。😊，我 so。So if you apply it like this， you will have login or time to find these segments in each of these segments you need to find you need to apply binary research to find these two borders。

And it will cost you log and time to file and then log and time to final。

 so total time will be square。Cool， it can be improved to work in log and time using technique called fractional cascading。

 I will not discuss it today， but。You can find it。 It's not。Its actually not oldsts， let's go。Yes。

It nots very late like， let discuss it。啊， you can。You can do it without this additional logo from using a technique called fractionction of cascading。

 let's discuss it。不こ。Well actually， in this case， it's not it's not。

 it's not even inf fractionctional。 It's just a skding。 It's not， we don't need。What is？

What is the idea？So一次。We need to find the， let's have these two positions。

 so we have these two positions。Y 1 and y2 and we need to find these two positions in these two sort arrays。

Instead of making these two binary searches， we will make only one binary search and we will make binary search in this first eraser。

 well take this first array in the root。And then this array， we will make a binary search。

For example， we need to find y1 so y1， let's say y2， y2 is between five and6。So y2 is somewhere here。

そう。So we will make one binary search。And find the position of y2 in this big sort array。

And now when we move。Do the children？We can actually articulate this position。

In constant time how can we do it Well let's see if we move to the left then some of elements of this array actually move to the left so so this array split it into part some elements move to the left some elements move to the right let's look on all elements move to the left so in the left we have this one。

 three， five and seven。So if we know that our current position is between five and six。

 we know that if we move to the left subre。We will be between five and7 always。

 so our position depends only on our position in this array。

 so if we know position of y2 in this array， we know the position of y2 in this array。

 we don't need to make a binary search to find it。alwaysway what we stand here。

And move to the left Suri， we will be here。So we don't need binary to rec position。

 we may precalculate for each position in this array。

The position we will be when we move the left sub， sorry for each position in this array。

We will precalculate。The position we will be if we move to the left secretary or if we move to the right secretary。

If we move to the right subre， we will be between four and6。

 we will will also preculate this position。this just can be done in linear time in linear time。

 we can precocate for any position the correspond position in the children node。For this position。

 we will precocolate where we will be when move the recipe， when will we move the recipe。

 so if we move the recipe we willll be to win four and6， so we will be here and this one。嗯哼。

So we will do it before the query， so just when we calculatec all these three。

 we will precalculate all these moves so for any position， pre calculateculate these two positions。

And now we don't need to do by the research， we do by the research。

Only once in more than time and when you go here you just use this precocoite position move here and here when you move to this child。

 you also look on the elements。So three and seven are from this。Cil。

 so when you move here you always be between three and seven。

 so you know that if you are here and move to this child， you will end up in this position。退错。

That that's the whole的。Veryty simple actually so yeah what is the it's kind of the idea is very simple。

 you have multiple binary searches instead of making multiple binary you make only run by binary research in the first array and then use the result of this binary search tool。

Make open next binary the researchers and some。Because you actually don't need these binary search。

 you always know your position， you know your position this array。

 it means you have enough information to calculate your position in this array。So you move here。

 then you move here， you move here， and each time you move from one element to his child。

 you know your current position in this solitary。ButSo so if you just precalculate all these moves。

 then you will have log n operations and all only one binary search here。

 so we will log n for this binary search plus log n for all these moves， so total time will be logo。

呼。Is it possible to change the elements that's complicated？😡，啊。

Simple answer for this you can change the elements but it's complicated we will talk about it in the future lectures I think so again。

Structure is kind of fixed。 so if you have some number of points。

 you've built this data structure and if you want to add another point to your data structure。

 it's kind of。Brainful， yeah， so if you try to add another point。Okay。

Then you need to complete to whole the structure because these orders will be changed so you need to get this point all these segments and so on。

 it's complicated。It's actually possible to do it but。It's complicated。 if with have， I。

I hope we will have enough time。Yeah。To discuss。 So if you want to just put this point inside this sorted array。

 you can do it using binary search trees。 So when you want to maintain inside each of these node。

 So instead of having the sorted array， you'll have to need binary search tree inside of this node。

But to maintain this outer segmentary， you kind of need to some special binary research tree because。

We will talk about it。啊。Now if you just want to change why coordinate。😡，It's kind you just。

 you need to maintain this arrays， not not as sort array， but as binary research trees。

So when you change the Viker's name， you iterate all these notes。

And to kind of remove this element from the binary search tree， change one coordinate， put them back。

So by theHT will allow you to do the operations and look them down。Yeah。

I believe this song the off today。So again， thank you for joining me today。🎼。🎼Yeah。🎼。🎼Yeah。🎼The。🎼う。

🎼う。