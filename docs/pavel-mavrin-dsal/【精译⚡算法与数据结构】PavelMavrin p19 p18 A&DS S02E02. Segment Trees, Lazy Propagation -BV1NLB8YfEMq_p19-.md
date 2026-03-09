# 【精译⚡算法与数据结构】PavelMavrin p19 p18 A&DS S02E02. Segment Trees, Lazy Propagation -BV1NLB8YfEMq_p19-

，🎼嘟嘟嘟嘟嘟嘟。🎼The。So today we'll continue to talk about segmentaries。This is。Again。

 if you watched the lesson on code forces you do section。

 it will the first part of the lecture will be exactly the same as in the second lesson。

About segmentsaries。

![](img/8e23048da9de8cf66f20bff534bd38a7_1.png)

Let's go so let's remember what we did last time。

![](img/8e23048da9de8cf66f20bff534bd38a7_3.png)

So look are the cemeteries。あね。Gce。So last week we discussed the following instruction。

 we have the array。

![](img/8e23048da9de8cf66f20bff534bd38a7_5.png)

And we have two types of queries， first queries to change the element。



![](img/8e23048da9de8cf66f20bff534bd38a7_7.png)

like set element I and V， and the second query is to find like some on the segment or minimum on the segment or any other associative function on the segment。



![](img/8e23048da9de8cf66f20bff534bd38a7_9.png)

Some。

![](img/8e23048da9de8cf66f20bff534bd38a7_11.png)

And we discuss how to make the segmentary in such way that both the separations workers in the workile。



![](img/8e23048da9de8cf66f20bff534bd38a7_13.png)

We have both these operationss in the loggan time。Cool。那。Today we will use again segmentsaries。

 but we will try to handle different types of operations today we will handle two types of operations first operation will be to change the whole segment of elements。



![](img/8e23048da9de8cf66f20bff534bd38a7_15.png)

So we will change。

![](img/8e23048da9de8cf66f20bff534bd38a7_17.png)

Let's say we will add to some else。 we will add。

![](img/8e23048da9de8cf66f20bff534bd38a7_19.png)

From L to r value。

![](img/8e23048da9de8cf66f20bff534bd38a7_21.png)

So we will change the segment from L to R by adding the value v to all elements on this second。好。😮，好。

So make A plus equal v for all I from L to carbon。

![](img/8e23048da9de8cf66f20bff534bd38a7_23.png)

Now， the second operation will be to get the current value of the element。



![](img/8e23048da9de8cf66f20bff534bd38a7_25.png)

Let's see。

![](img/8e23048da9de8cf66f20bff534bd38a7_27.png)

Let's see we I get。 I will simply done。Element and position type。What's the plan today。Now again。

 if you have simple array， if you just have an array， then you can make this query in constant time。

 but for this array you need to iterate all elements of the segment so it will cost you linear time width so we kind of want to make this separation faster so。



![](img/8e23048da9de8cf66f20bff534bd38a7_29.png)

We want to make a。Appperation， which adds something to all elements on a segment faster than just direction or all elements of the segment。

And by doing this， we also want to be able to get the current value in each element in some good time。

 we'll do it both operations in log and time action。



![](img/8e23048da9de8cf66f20bff534bd38a7_31.png)

Do have on fence， not yet， who knows？

![](img/8e23048da9de8cf66f20bff534bd38a7_33.png)

嗯。Okay。

![](img/8e23048da9de8cf66f20bff534bd38a7_35.png)

Now。

![](img/8e23048da9de8cf66f20bff534bd38a7_37.png)

Let's go。 So how to make both the operationss work and work in time we will kind of build。This。

Segmentary like in previous lecture， so' let's build segment three of like eight elements。



![](img/8e23048da9de8cf66f20bff534bd38a7_39.png)

E elements。お。Yes。哦。ふ呵。😊，I used almost all that。B。

![](img/8e23048da9de8cf66f20bff534bd38a7_41.png)

Okay， I'll try it back。嗯。NowNow we will build a segmentary。

 the structure of segment three is always the same。

 so we'll just make a full binary tree when these elements are the leaves of this binary tree。

 so we'll make one element here element here。没死我。ここ。And now all elements of this tree just empty。

 all contain zeros。那。What will be the meaning of all these node？No， like before。

 each element like corresponds to some segment of the array like， for example， that these。

Eleement corresponds to this segment and this element corresponds to this segment and so on so each note of the segment trick corresponds to some segment of your array。

And the numbers we will put in these nodes will correspond to the numbers which we should add to to this segment。

So if we have some number in this node， it means we should add this number to all segments corresponding to this node。

啊，好。That's错。Now， how to make both aspirations。That's pretty simple， so you have some segment。

Let's write some segments we have a segment。I always use the same segment though。Okay。

This's just in a good segment， it has free parts， so it's kind of a good example but。

We used the same segment on the previous lecture。Okay。

 so let's have some segment and try to add some number two to this segment。 let's add something。嗯。

5 to all elements of this segment。How can we make the separation using this segment， now。

 we will split this segment into some parts。Such that each part is contained in some note of this segmentary。

 like in previous lecture gallery， we have this segment， we can split it in this segment。

Which is in this node， this segment in this node and this small segment in this node。

So if we want to add number five to all elements of this big segment。

We will add it to these three small segments， so we we'll put。5 here， five here and five here。

Thats all， that's how you add something to the whole segment， you split your segment into some parts。

IAdd five to all these parts and so you have all evidence increased by five。Okay。

 so how to find this。Nots so how to find all the notess which combines in your given segment。

 not exactly like we did in the previous lecture， so in previous lecture we need to split the segment in some parts。

Toここれリさ。So if it wasn't the previous lecture， I hope you kind of remember what's going on。

Now we need to do the same thing， but instead of coating the sum， we will just put this this。

Double put this V in this node。So again， we will make the。A recursive function。

 it will start from the root。And each time it will recover call from the left ring from the right tree。

And we have the same two cases when we stop the recursion。So we go left to go。

Here we stop the recursion because this segment doesn't contain any interesting elements。

 So we check this。Note， this node represents this segment of the array。

This segment contains no element of the segment we need， so we stop the regression here。And go back。

And when we go to the right， this segment is completely inside our segment。

 so when this segment is completely inside， we just put our number here and also stop thecursion here。

So we go here， see what it is inside， add five to this node， stop the recursion， go back back here。

 go go here， go to the left， This segment is completely inside， so we add five here。

 stop the recursion， go back， go here， go here， add5， stop the recursion， go here。

 stop the recursion So the procedure it' is exactly the same as on the previous lecture sorry。

I know I dropped the markers right near the microphone on it， maybe。嗯。I believe。

 I used to have a separate table for my markers， but I kind of moved it。Sorry。

 technical difficulties。啊。Now。Let's write the picle just。Just to make it。

Perfectly clear we make a recursive procedure again。This LRV。

 and we add three parameters like before like the current node。And the borders of the current node。

And now we make the that is same to checks， but first we check if this segment is completely outside。

So if it is Lx greater equal than R or if r x greater。い。

L is very called R that we're completely outside， if we're completely outside， which return。

If we are completely inside。嗯。And our ex are。And then we add this。

 add this value v to the current node now。s3。V plus equal 3 x plus equal V and return。

If none of this， then we make three recursor calls like before， exactly like before。

 this whole call this exactly like before。Make an wepartex plus for over two and make twocis。그백 키 백。

Left sub and right sub。嗯。六。P on。And this code works also in logarithmic time exactly by the same reasons like we discussed in the previous lecture。

 so the total number of node we visit in this re is up to loggan， so this end works in loggan time。啊。

And。Now now to the second function， now we need to find the current value of the node。

 So how to find the current value of let's first， let's make some。

Let's make some more operations just to make the tree。More interesting。 So let's。

 let's add something to something。Let's have something small。Whats it。Let's sit。

One to this small segment。So when we add。One to this small segment， we make the same recursion。

답빠빡답빡방스럽빵。So we start start on the row， go to the left， go to the left， go to the left。

 stop the recursion， go to the right， stop the recursion， add the one to this node。Then we go back。

 go to this sub， add one here。Mmhmm。😊，And let's add something else just to make it more fun。

What's important for these two， let's have this segment。

Again we split each second this second split like this， so again here here we start the recurs。

 go to the layer， this left sub three is completely inside so we just add add water I need some number。

2。So let's add two to to this segment， so we got go to the left sub。

 this segment is completely inside， so we add。To do this sub， then go here， go here。

 go to the left sub here。 We need to add2， and we already have five here。 So we add5 and then add2。

 It is the same as add 7 to the whole second here。 So we need。To take all elements on the segment。

 add five to all of them and then add add to， it is the same as add7 to all elements of the segment。

 so we just increase this five to7。cool。And now let's go to the second function。 In second function。

 we need to to find the current value of some element of the array。

 So how to find element of of So how to find the current value of the element。

 Well It's quite simple。 So we take some element。If we need to find its current value。

 we just need to apply all the deparations to this element。

So we just follow the path from this root from this node to the root。And。不。

Apply all operations on this path， so we apply all these operations to this node。

And find the final value of these elements， the final where will be like5 plus2。boom， it's seven。

But if matrix is complicated。So we we getting get off。Oh。

Thats that's how it went and this operation also works in log time by it's always。Okay。

So now we have both inspiration works and log time。I you not保 guitar talk to him。

I don't usually to play guitar， sometimes I may be liker， but it's before the lecture。

Just ask me before the lecture next time。Sorry， I don't play but like a during lecture it kind of。

Killing the wipes of the electron。I'm trying to keep everything serious。I'm very serious。啊。

Why are we eating five only once？What do you mean？嗯。Oh， good directions。Why do mean only once？

We have one operation plus5， so we apply operation5 only once， so for each element on this segment。

 we should apply operation plus 5。Only once。When we add l to all second， we add two twos in this。

When we had performance we added。The numberumber of elements in the cemetery of times。Okay。

Now we added only one。 So So this separation just increases all the all the elements on this segment by but by V。

H。😊，What。嗯。嗯。Let's say there is24， then the not current24 should be8 at 10。W then。You mean this note。

No this not just contain the operation it doesn't contain like the sum of operations No no we will go to this later now's you move into phase now no no no that's what we do we just maintain the operation so we have this operation plus5 and we need to apply this operation plus5 to all segments to all elements of this segment。

We we don't try to calculate the sum on the segment and sos， we will do it later。

 but but another by now we just want to find the current value of this element and to find the current value of the element。

 we just add all operations so we like go go up to the root and find all operations which should be applied to this element。

Okay。We will talk about laser propag just in a few minutes。别 patientO。Now。

 before we go to laser propagation。Let's stop here for a few seconds。嗯。What I want to do is again。

 I want to try to apply different operationss， so we just create some segment three for some operation for this operation plus。

So in this function， I apply operation plus to all elements of the segment。

And sometimes you want to apply some different direction。

 so sometimes you want to have something like。Moify from L to R with parameter by D。

 So you apply some operation with parameter B。So we have something make。AI， then you have some。Again。

 we need some special sign for inspirationperation。Let's kind of start also。

 so this is some special direction。So we just apply this it to all elements。Offf theing。哦哼。Now。

 let's think about what properties do we need from this operation to make this work。

 So if we just change， so I want what I want to do， I want to change this separation here。

and also change the separation when I calculate the result， so when I calculate the result。K。

Cl this gets。嗯。get the simple， so in get， you like make this recursive pole。嗯。그。You add this。

X x or x， you make this a cursive call like a to x plus one and so on。 And then in the entry return。

S plus。Three of exit。 so I want to change this plus with this abstract operation。

 this abstract operation here and here。And I want to understand what types of operations actually works。

 I want to find the properties of separationations we need to take care of when we try to make segment three with this operation。

Lets go so let's think about what's going on when we apply theation。

We used several properties of the。Plus separation， when we make this algorithm。

 the first property is pretty simple when we let let's see what what happens to this node。

 why we have seven here， because we add five and then add two， right？So when we have some element。

So when we had some element。We apply operation plus five。Yeah， and then apply plus2。

So it's supposed to be working like this。But I put seven here because。

This sun is the same as if we end up。Some of five was two。嗯哼。

And that's the property we discussed in previous lecture is just a social activity。

 So if we want some。To be working in this algorithm， we need this operation to be associative。

Like before。ag呃。What this sensitivityivity gives you for these algorithms。

 it gives you the opportunity to change two separate operations into like one big operation。

That's why assertciivity is working because if you have some element， you apply one operation。

 then apply second operation。Let the justice write it。Let merrate it like this。

So I want to follow a property team， so if I have some element。

I apply operation x and then apply operation y like this。

I should be able to change these two operations with some mega operation right so I want to make some combination of two operations to be the operation of the same type so I want to change these two operations with one operation。

And that's a socialivity。啊。In practice， sometimes you have some strange cases in practice。

 sometimes you have like different operations so you have some operation which you apply to the element and you have some different operation which gets you the combination of two operations so sometimes here you have different operation it doesn't matter a lot but。

You always can change the operationsations in such a way that you have the single operation to all these cases like you have the single operation when you apply it to element and operation。

 you have the result of operation， when you apply it to two operations， you have combination of de。

Just for simplicity， you can think about the link you have only one operation。

In practice sometimes when you implement this operation。

 you kind of have two cases when you apply operation to element and when you combine two operations。

 so sometimes when you implement this separation you have this if so if you have this case or this case。

 that's not a big deal。啊。O。😀呵呵呵。😊，いや。Good。那。嗯。The second property we used the second property of the sum we used is here。

 so when we try to calculate lets let's try to calculate the final value of this element。

 so when we calculate final value of this element， we do it like this we apply all operations。

To this element。So final value of this element will be one plus 5 plus2 equal to。8ight。

And that's not what actually happened to this node。 Actually to this node happened the following。

 we had this node。 We first add five。Then we add one。And then we add two。And for plus separation。

 it doesn't matter。Plus operation is commutative since this plus operation is commutitive so you can change the order of deations。

So we don't care about what of what is the order operations。

 we just have all the separations in some order， we apply them in any order and we have the same result in the end。

 that's because plus as a associative。不连说。treesWe will talk about trees next week。Let's go。 so。

 so we need following property。 We need first， we need the separation。That's quite okay。Issociative。

そ。And then we need then communitymun。共 you。야 정말。And commitivity is。Not that。Not at common property。

There are a lot of operations which are associative but not commutative， for example。

 if you multiate like mattresses if。If you have some metricses in all these elements and you want to multiply the elements by some metrics。

Then the multiplication of mattress is commutative sources is not working。

 the simplest operation which is not commut but it is assertorative is of course it is。Just。

Hows going。응 응 응。Let because the set of versions or when you。嗯。Let's call it a assign operation。

 So when you assign value to some element， I don' know really the good term。ね。

So simple separation is basically a s value。To the element。It's pretty simple operation， yes， if you。

Have x you assign value Y， you will get y。So it's。Quite some comparison。

 it's obviously associative if you're assigning several values。

If you have if you assign x and then assign y， it is the same as assign x assign y。

 and so this will be equal to y， this will be equal to y， not this will be。So意。So suppose sociative。

 but it is not commutative if you assign x， then assign y。

 it's not the same if you assign it in the different order。🤧そう。

And this is actually quite common operation， so when you want to have a operation like set。

If you apply this operation here， you have some satellite you have set from LB。

 which simply sets all values to V on this segment。

Quite useful very operation and it is not associative well it's not commutative so we cannot assign values in different order will get the different final result。

So how to get rid of this cognitive property？It's actually possible so we can modify our output mass way that we don't actually need this commivity property。

How do we do it you can do it you do it in following so to get rid of this comm we need to remember the order of operations like we need in these three we just forgot about the order of operations we just put these elements in some order so for each element we don't know the order of these operations。

🤧啊。그프치 스테。有。Yeah， that is， I believe you can Google the good definition of assertivity of income commivity。

 okay。😊，呃。It's not about terminology， right， it's more about algorithms。I think it's quite clear。

How do you remember the order of operations very simple way。

 we will remember these order operations in this tree。Like。So when we have some element。

 we will apply all the operationsations to these elements from bottom to up。

 so if you have some leave here。Then， you have。The path from this leaf to the root。

 so this is the root。You have some operations in this note。

 the order of these operations is from bottom to top， so here we have some old operations。

And here we have some new operations。That's the plan we will maintain the following environment end。

So I'm trying to speak in the moment of mathematical terms。😊。

It's just to scare it so we'll do we'll always keep the things in such a way that for each node all operations that should be applied to this node are sorted from bottom to top so here in the bottom are the oldest operations and here in the root are the new operations。

So when you try to calculate the value of this node， you just go from bottom to top like we did here。

Here in this recursion， we calculate from bottom top so we recursively calculateulate the value in the child and then apply the operation in our current node。

这不这是不。Now， how to maintain things in these order？Sometimes we will have some problems maintenance。

 for example， you have some preparation here。So you have some pressure here so for this node。

 you need to apply ratio like plus x。I will just write plus just for simplicity。

Because plus is like more common than this like and， okay， let's have this start。

I just don't like to draw a lot of staris。It looks strange， so we have this separation。

Which should be applied to this element。And then we have some another， so we have some another query。

 so we need to modify some segment which contain this element as well。 So we have some。

We have some operation like this， so we have some operation we need to apply。

Apply value Y to this second。So we again， we start the same recursive function。

 we start from the root， go somewhere， and we need to put y here。어 무슨。If we put y here。

 then the order regression is changed， yes so so we when we try to calculate this value we first apply y and then apply x and we want to first apply x and then apply y。

啊。啊哼。So will how we'll fix this very simple way， we will try to move elements deeper in the tree。

 so we will try to move the separations。Deeper in the tree in such your way that all operations will at some point go to the leaves of the tree。

And this。techniqueique is called laser propagation。Oh。

It is lazy because we move operations down to the tree only when we need to。

 So when you when when you when you have some operation which like here when some some operation in your tree just and。

When you need to add separation below this current operation， only in this case。

 you move the separation down the tree。嗯。How to do it。It's quite simple。我就就 two。

How to update on this side element， but not middle ones。没。I am not sure what you talking about。嗯。そう。

So 들어 sorry sorry。If you have any questions， just give it some。

Some short explanation about your question， if you have any short question。

 I'm not sure what are you talking about he kind of lost the contact。够。

So how to move operations down to the trim it's pretty easy， so we have some node。In this node。

 you have some operation。These note have some children。

 and you have some permission here and some par here。What does it mean。

 It means that for all elements in this， in this segment， you need to apply。Y and then apply X。

And for all elements in this segment， you need to apply that。And then， apply X。や。So what we'll do。

 we will move this x to both children。 So so we will move it to the left child in the left child。

 we need to apply X and then apply X apply Y and then apply X。 It is the same as just apply。

The sum of Y and x。So we're just to get the combination of these two altererations and put it in this node。

And the same here here， we just apply the combination of Z。And why。

And then we need just we can remove x from this element。I mean those regulation of。

 but they want some specific note to update in constant time。H。😮，嗯。H。そ。

I'm still unsure unsure what I about。啊。This operation works in constant I assume that I can calculate the result of operation constant time。

 so this propagation in one node is working in constant time I just remove a from here。

 apply it here and here， so I have constant number of operations。不咩。Now呃。

What going on here here I run the same recursive procedures here so I start the regression from the root then go here then this at this point I need to go deeper to the tree so I want to apply y to one of the children of this node to the left child for for example and I also have some right child here。

So in this node X， I want to go to the left child of this element。So what I will do。

 I will propagate this operation x to both children of this color， so I propagate x。

Do they live child？I propagate X to the right child。애들이 뭐 toでの？

And now I go to the left charge here and I I want to go even deeper I don't I don't have this。

 I want I want to be why here， but not yet。So I go to this left child and again I want to go even deeper so I need to propagate this value from this node。

 so I take this node， apply the same propagation so I move this x here， move this X here。

And go deeper into the direction go here。And here I stop the regression because I want to apply y to the whole segment。

 so I just apply y to this segment by adding it to x。Quite。没的错。そう。

So every time you want to go deeper in the recursion。You just call this disproagation。

And move the operation from your to both children。And when you stop the regression。

 just apply your operation to the current element。 let's change what will be changed。

 so we need to add props。So this separation put up again。おはどうです？To take the current element。

 take both children， apply this x to both children and remove it from this node。

let's say I want five elements to update， but a randomly。And each operation take constant time。Okay。

 let me read again， let's say I want five elements to update。Okay， but annual your random name。

What do you mean randomly， a， not in a segment， but some elements？Of the array， not the segment。

 but some random elements。O。Yes， you can do it。One of the reasons you can do it because to update。

And random elements， you need to read and random indices。

So how do you describe N random elements when you're in constant？Anmount of memory。そう。

Like to describe and elements you kind of need。And integers of indices just。不看。

So you it will be strange if you can do it faster than and lock it down so if you just change some random elements。

You can do it faster than just reading all the indices of these elements。

 so you can do it faster than linear time。嗯。Yes， this stuff only works on segments。

 this is why it's segmentary。Fortunately its。There are a lot of different situations when you need to work with segments。

 so in various different situations， when you like in various different problems。

 when you look on the elements we need to change， they form some segments。

 sometimes it's going from like for the chemistry problems wrong。啊。Just from monoity of something。

 you have something something is monoonic， so if you just look on the set of elements you need to change。

 they form some segment of this array。Not always， but sometimes this works so if it's not working。

 then we have some problem。X is the old operation， yes， then the old operation so X was here。

And then we apply y to this node。So we need to apply x and then apply y。

And that what happening so now now for this node， when we try to apply all operations from bottom to up。

 then we we go from bottom to up， we apply all these operations， so even older operations。

 then go to this node， apply X， then apply Y and then go up here， there are no operations。

So we apply x and then this y will be the last separation of applied this node。公。꼭。多くて。

We spent an hour on this。O。Its。ALittle bit slower than unexpected， Okay。

 but it's good but we discussed everything quite。Well so so， I hope now it's。Must be。

Absolutely clear in the way separation， y is y before x。No， these are different ys and x。 No Okay。

 I have these two pictures nearby， but they different pictures， I have different X O I。

 different X O I。Here I have situation I first have this white and Z。The deeper in the tree。

So I first apply operations from bottom to up so first apply this y。

 then apply x and in this picture I have here I have y and here here I have x and so。

There are different ys and nees in these two pictures， Okay。

 so here I apply X and y and here I apply Y I should use different letters for this， but。我给你。嗯。No。

No implementation is very simple no no，If your implementation is hard， you're doing something wrong。

 this is basically the whole implementation。So this is the complement of this L function。

And this propagation is a very simple function when you call propagate。

You simply take this value from here and apply it to both children so you just。Take this。

To x plus one。Updated with value of3 x。 You take the second child。apply ready dream。X。

 and then remove it。Okay。It can not no no， no no it's very simple。

 there is no place in this algorithm， which is kind of hard to implement。No， no， no。

 So that's basically the whole code。No。Let's move next。

Now we will make things a little bit more complicated。

We will try to merge these two data structures so first we build data structure which can calculate sum on the segment。

And here we tell we make the data structure which modifies the segment now we we'll try to make both。

 we will try to make data structure， which allows you to change the whole segment and find the function in the whole segment。

통 부릉 부릉 부릉 부릉 부릉 부릉 애이 또려있어。For example， let's make data structure which have two operations。

 first operation is to change the segment like let's have end。Will add value from L to R value。

 So again， it will add。Where you read to all elements from L to R minus1。And the second expression。

 let's say， we' calculate the minimum on the second one。我我会。明有感西咁做不有都。Okay。Like these。

So also I try to merge the techniques from previous lecture when we completed this minimum and technique from this lecture when we add the element to the。

Lets go。So how to merge these two techniques a very simple way。

Take both these techniques and apply elements and same time。

 so we will build the segment in each element we will maintain two values。

Let's build some secondary and let have some values， have two， five， six， one，4， three， seven， four。

So we have this array， let's build a segmentary， so we need to calculate minimums。

 so let's build the segment three for minimum version。So this's the simple segment trick for minimum。

Yes。え。嗯。This is a simple segmentary you used when you try to calculate the minimums on a segment。啊。

Now， you want to be able to add values to some segments， so we will。

Maintain the same thing as before so for each note， we will maintain the another value。

 which is the value we need to add to this segment。

So these values are the minimums and we need another value。

Which is the value we need to add to this segment。 Well again。

 let's let's perform the same expression。 So let's take this segment， make plus5 to this segment。

So what happens when we add five to this segment？Again。

 we will find the same free nodes and try to add five to this second， so we add five here。Plus 5。

 plus 5 here and plus 5 here。嗯。那。When you apply de you need to recallate the minimums so after this separation you want to again to be able to calculate minimums。

 but all these minimums are wrong， so sorry you need to kind of change all the minimums here， right？

啊。What we do。We will change。 We will rec the minimums， but not all minimums here because it's。

There's run too many elements here。 So okay， you're going need to change all these minerals。

We can all change all these minimums at too many of them。

 so we will change only the minimums which are above these changed elements in the second。

So we will recalulate these elements while let me show you。So we to calculateulate these minimums。So。

 here。How to minimum， so you have the previous medium here， you have minimum on this segment is one。

Now you add five to all elements of the segment。So the new new minimum will be6。 what。

You have some segments， the minimum， you know the minimum of this segment it is one。

So if you make plus five to all elements of the segment。They all change by the same value。

 So minimum is。Is minimum。 Yeah， minimum minimum says stay the same。 So this。

 this element again will be the minimum on this segment。

 but the value of the minimum will be increased by 5。 So the new minimum on this segment is 6。6。嗯。

哼哼哼哼哼。😊，こ。And also change the elements。 So here will be8， and here it will be。boom2。

And now we'll recal the minimums above these elements， so to keep it like correct。

segmentment  three for minimums。So we'll go here and rec this minimum will be two。

 go here here here minimum will be4， this minimum will be minimum of8 and for this4。

And this minimum will be2。不错。So we to calculate these elements。And all elements about these elements。

Can we merge to most entries， what do you mean my me？Sometimes you can。Cos。

And you make some specific operation。Usually the answer is sometimes you can， sometimes you don。

It depends on what actually do you mean by this version。This can only all the basic operations。

 if you want to some special operation， you need to think is it possible or not。

 sometimes it's supposed for something minutes。Sometimes you can prove that you can enjoy operation just because you will make socing algorithmgams。

我想봉。那。送。Let's see。Let's see so so this this is the segment tree for these two operations。

P add to the segment and find them in。Let's see what's going on here。

 so what are these minimums for these minimums？啊。Are the minimums on this segment。Which。

Don't take into consideration all decorations above this second， so in some node。

So there is some note text me。In this note。You maintain the minimum on this segment。

But without all decorations above this element， you have some more operationsations here。

And this minimum。Do not include these operations。About this X。So here you have minimum。Weout。

Aparations above。For example， let's add something more so。Let's add let's add something。

What segment do you like？So let's do something like let's to this segment， let's add three。

what what will go。What will change。아뿜뿜토뿜뿜뿜 또뿜뽀빠뿜。Again。

 you start from the root to make the same recursor procedure and so on make the same recursor procedure here。

 so go to left to left to left go find this node。And free here。When you return from the recursion。

 you recalculate the minimum， so this new minimum will be po 5 plus3。

 so you see the code will be eight。Then you go back from the recurution to calculate this minimum it is2。

 go back from the recursion， go here here you apply a plus3。So here you have。 now you have。Plus 8。

Apply the separation to this node。9， I can do it。So it's 6 plus3 is's now9。

 you go back from the recursion we call this mini minus2， then go back。

 go here yeah this segment is completely inside so we just apply it here here we have plus3。

Change the minimum to seven。Then go back to calculate this medium that's all。Now let's say again。

 this minimum is eight。よ。Because it。It only uses this pressure so this minimum is minimum on this segment without this separation plus3。

 so the real minimum in this segment is actually 11 because we need to to all element we need to add five and then add3 so this element is actually 11。

Yeah we added five， it was free， we added five and then added three so this but this medium was 8 because this this medium doesn't know about this de separation。

And that's fine， that's what we want， we want each medium to know only a inside this segment if we have some operations above we just don't care about them。

 we will take care of all of them later。When we need， we will take care of depers。Okay。

Should I write the code？と。Well， it's right the cool。嗯。So how to cook late menu？Where's this？

So when you add something to the segment， you make the same recursive procedure so you start on the route if it is completely outside。

 you do nothing， if it is inside you。Make the phone， so we need we need two values。

We need these two values。So when you stop in some node。

 you apply your operation to this number and also to this number。

 so you change this operation and also recalulate the current menu here。So we need two numbers。

Let's have this add number。So this add number in node X will be increased by V。And also。

 this minimum in node x will be increased by B。So we take both these numbers and increase both numbers by V。

Then they return。If it is。If it is not completely inside， not completely outside。

 then we make two recursive calls like before we make two recursive calls and when we go back from the recurs。

 we calculate the value in this node。To calculate value in this node。

We just say that the minimum in node x will be equal to minimum of two minimums to minimum in node to x plus1 and node。

To x plus。And also， if you don't have this propagation， you need to apply a that end。Like this。Also。

 you can apply propagation in the same way。We can do the same propagate operation。

So what happens when you make propagation you like move this separation to both children。

 when you move this person to both children， you need to change this。

Red where you like to calculate this operation， new operation thats combine these operationss into one。

And also， you need to rec these two minimums。Because these minimums are now before we have this minimum without the separation。

 now when we move it down here。We need to calculate new minimum concerning de separationhu。

So we just apply this separation to this。Two values like before what operation we need to perform and also use this the same value to modify these two minimums。

Make sense。that's how you propagate。Yes， and if you have propagation。Actually。

 the quote became even easier because when you have propagation， you。

Guaranteee that all node from this note to to the route are empty。So when you use propagation here。

 this n actually is zero so you can remove this n。Poroppoage should be inside second， if I think。

Inside what a second。Now you can move this propagate to the beginning of this function。

 but you should be careful because you can't propagate from the live node。

 so if you are in the live node，It has no children， so you can propagate。

So you can move this propagation to the beginning of this function and then inside this propagation check that current node is not the leaf of the tree。

Because you will have some integer out of bound， exception， no something like that。

From no point of exception depends on how you implement it。Okay。Now the code is very simple。

 again you can watch a lesson on Ydo if you are interested about implementation in Ydo。

 I have a special video where I implement all this from scratch like in a few minutes。

 it's actually it's not hard to implement。那。No， no no， no， no， no， no， no， not important stuff。

 what other operations can you use instead of these operations。

 Let's try to have some abstract operation again。嗯。Some extra operation。

So we need some two durations， first operation we use when we apply functions always say something。

Mo D5 from L to R B have this AI and then apply a B。And。C them， calculate。From L to R。

This pressure will calculateulate some aration on this segment。What version we used。So like that。

 we have some operation here。Las wrong， some and so on。That is one。So we have two special operations。

 special operations， we have one operation we use where we change node change the element。

And another operation we use when we calculate something。嗯。least operation。Now。

 let's check what properties do we need from depers。 No， first of all， we。

 we need all the properties from the previous lectures。 So， so this。

This operation should be associative。こ。This separation also into social。Yeah。

Just by the same reasons as before， but there is one more interesting property we need to have to maintain all this data structure。

Let's see what's going on This property is very interesting。

 so we need to be able to recalulate the function when we apply function to when we apply operation to the whole segment。

 we need to be able to recalulate the function so like here when we apply this plus5 to this segment。

We just take the previous minimum， add the five to this minimum。And get the new minimum。

So why do we do this？We use the fact that when you calculate minimum of slack。えく。

Like x plus V V and y plus z。It is the same as previous minimum。And then make plus V。

Or in terms of these abstract operationss， we need to following in we need so if we take some element X。

And then apply operation with the。And take the sum of these and y we've applied operation V。

 so if we apply operation to x and apply operation to V， then calculate the result。

 it must be the same as if we just calculate the result of this and then apply V to this result。行。

That's the property you need and this is distribut so when you you have two operations。

 they need to be both to be associative， but also they should be distributive to each other sorry you cannot take some separate two functions and just apply it to the secondary you need these functions to be good working with each other or sorry like one functions should should complete another function that's what that's what you need。

嗯。So we need these two functions。To be distributive。Oh。Okay。嗯。For example。

 minimum minimum and plus are distributive， for example。

 sum and product are distributive calculate if you have this plus operation and multi operation。

You have the same thing here， for example。Some strange operations are minimum and minimum distributionive maximum and maximum。

 you have bitwise or and bitwise and perfectly distribution operations and so on so。

 some pair of operations are good。if your pair repress is not good。

 you kind of need to think about what's going on， so maybe you need to change operations a little bit。

 just to tweak a little bit。Just to make them distributive or maybe you should add some additional parameter to your function to make them distributive sometimes sometimes。

That's what we want to do。But basically what you need to do to make some dis。嗯。什ご。

So this that's all the basic stuff I want to discuss。I want to talk some more about。

Do you have some more time？は。😊，I want to talk about some additional problems about seism。Yeah。

 unfortunately， I spent too much time on this。I think it's fine。

 We can spend another like 20 minutes on summer from。

Let's talk about some interesting problems when you need to use some special searies again。

 we will we will discuss some some problems in the home task discussion。

But I want to have some more problems now these problems haven't been in the home task。

just since we was talking about some。Interesting stuff。Let's try。嗯。嗯。

Lets so the problem on discuss this problem I have let's have some some。Everyry。

And you have a number of segments。哦。Sa个名。嗯。I what this。So you are given some array。

And a list of different segments。And what I want to do。

 I want to calculate for each segment the number of unique elements on this segment。No。

What's the difference？诶喂。And on each segment。Yeah。So you have all these segments in investors。

 so you have the list of segments。And you need to answer through all these questions for each segment you need to output a number。

 which is a number of different elements on this set。This problem。嗯。

So there are different approaches how to solve this problem。I want to discuss one them。For laser。

 alwayss talk about laser propag。哎看了 half an hour we。嗯。这个。是。Okay。So let's have some。

Let's have some array like five。1 three。뭐 잘 나오다 원 너 나와 봐。Okay。pre是的是猪。5 again1。有人锁。So this is sorry。



![](img/8e23048da9de8cf66f20bff534bd38a7_43.png)

And you have some segments of this right。 we have some segment here， some segment here。Sement here。

So we have a lot of different segments。And for each segment。

 you need to output the result of a number of different elements on this segment。对。So how to do it。

ど lets go。啊。Let's start by home， let's try to answer all the queries of the segments。

 which starts in the leftmost element of this direction， let's find all the segments。



![](img/8e23048da9de8cf66f20bff534bd38a7_45.png)

Which start in the first element of this resultso。 So we find all the segments。Like these。

Where L equal to 0。So let's find all these segments。Now how to answer the query， it's pretty simple。

 we need to find the number of unique elements on this segment。啊，说。To answer query。

 we will just mark all the unique elements。And since the left border is here。

We will just mark all the leftmost elements。😡，Of each kind。 so for each element。

 we will mark the leftmost element equal to this value， so for example， for these fives。

 so this we need mark this element， this is left leftmost five。This is the leftmost one。

 this is the leftmost free。We don't need this， we don't need this， we need these too， and so。

So these are the leftmost elements for each variable。Okay。

So to calculatec the number of different elements on some prefis。

 we just need to calculate the sum in this array， so if you create another array like you put once in these positions。

And zeros in these positions。Yeah。Then to answer this query， you just need to have this prefix。

And calculate the sum on this prex， this sum on this prex will be equal to the number of different elements in this segment。

啊好。B plan。No。Is clear enough？Okay， hope不s good。Now we answer all the queries。

 which starts in the leftmost element。Now let's move to the next queries。

 so let's move to all the queries which start in the second element of this array。

Let's find all that。Samon。Like these segments。 so let's now let's find all these segments when left border equal to one。

Again， the left border equal to one。We need for each segment to calculate the number of unique elements on this segment。

 so let's find all the unique elements for each element to find the leftmost position when we have this element。

But this five is not inside this segment anymore。 Yeah， so this five is outside of this scope。

 So we need to remove this five。So this five is not the leftmost element anymore because this five is outside of these segments。

 so we remove this five。Now we find the next equal element， so well find the next element5。

And now this element is the leftmost element inside our segment。Take these five。And edit。

As as the leftmost element。哪哼。That's wrong。Now again， in this array。

 we mark all the elements which are leftmost element inside our segment。Makes sense。

So we can answer all these queries for each  query， we just calculate the sum on this segment。

 this sum will be equal to the number of these unique elements because we just put once in position when we have these unique elements。

And肃。Now again， we move to the next position， so we move to the next position。

 we need to remove this one， so we remove this one。Find the next element equal to one。

Mark this owner。もそうそう一タ。We do the following week answer all the queries with this left border。

And now we move the left border， when we move the left border， we remove this element。

 find the next equal element， and add this element。That's all。こ。So how to make the separation again。

 we need some data structure which allows us to remove elements to add element and to find the sum on the segment these perfectly done with segmentsaries。

 can you can do it the segmentsaries。So we will maintain this array of ones and zeros in the segmentary。

嗯hu。Each time we will take all queries of this left border， calculate the sum of the second。

And so the query。Then move the left border here to to of the left border。

 we just remove this element， find the next element at this element。So we update segment three here。

 update segment three here。And move the left button， good。

So we on each step we have two updates of the secondary and for each query。

 we need to find some in the secondary， so total time complexity here。Will be the。

We need to for each queryrium， so if we have mqueries。HaveAnd elements and mries。 So for each query。

 we need to。Make request to the second tree， so it costs you more than time。

And times we remove the left border， so each time we remove the left border。

 we need to remove something at something it goes to organ time， so it is un organ。소외 도서 검색ス죠。嗯m哼m。😊。



![](img/8e23048da9de8cf66f20bff534bd38a7_47.png)

그래나？Any questions by now？You forgot how to use this chat。

 you need to write that the everything is clear just every 30 seconds。If you don't do it。

 I'll try to explain everything once。Time complex second。 Okay， let's describe the satisfy。

 Let's look at the time complex。 So what are we doing， So we take。Every time we fix the net border。

 so we take all segments。We've left border equal to， so all these segments are equal to zero。

Here are all segments for L equal to one， We can split all the segments in these buckets in linear time。

 we just it all segments。Make these buckets of segments， take the segment。

 put it in one of these buckets， you can do it in linear time。

Now you take all the segments from this bucket so you will take all segments with left border here。

Calculate the sum on this segment， it costs you log time just。You just make operation in secondary。

 it goes to vganile， so for each segment。You will call one operation in segment3。

 it costs your logan time， so these operations， basically include sum in the segmentary。

You'll do it once for each second。And now you move to the next。Position。

 so when you move to the next position， you need to update segmentary here， update segment3 here。

So you make two updates in the second， each update costs you logan time so when you move the border of left border of the second。

You need to make two updates，2 updates。Of the secretary。嗯哼。😊，It goes two work。Also。

 you need to calculate the next element in the array， which is equal to your element。

 So for each element， you need to precalculate the next equal element。

 you need to precalulate these parametersers yeah。But you can do it in later time as well。

I'll just leave you as an exercise。For each element you need to precalculate the next element of the same value。

 you can do it just going from right to left in linear time using hash mapps。到时。Okay，嗯。Let's说。

Is it clear now？Now what I want to do。I want。Now， what I want to do， I want to be able to。

Answer this queryries in any order sorry in this algorithm。

I just I use that I have all these segments like it's an offline problem， so I have。

I have all these queries and I just answer them in the different order。

 so I first answer all the queries。When lab borrow is here， then I answer all these queries。

 then I answer all these queries。And sometimes you have this queries come one by one。

 so you have not this list of queries， but you have like function and you need to be able to answer the queries in real time。

 so you have some segment and you need for this segment to answer the query。啊 what도。Again。

 you'll have some online problems， so you have online problem。Then we'll have some quoing here。

 let's some cuulke。On second from L to R。 And this function should return there。Number。

Of different elements。我成。啊。嗯哼。And here you just you can just save this order and enter it lately。

 you need to just return the result right now。So what我 how how can you do it。Pt simple。

So what we need to do。These， let's see。 What we need to do is to remember the state of this algorithm。

 Like imagine if you have this。A seconds before so。呃。In this， in this algorithm。

 you kind of have some states so first you you have this state of your data search let's see。

Let me remove this， I need to remove this。啊。So first you have this segment tree， right？

So if this L equals to zero， you need this segment three to answer this query。So if L equal to0。

 you take this segment3， get the sum and this segment three， and this will be。

Then we remove this fire and this fire， so we have this signal。똥 거。추 저 투 추 추。So if L equals to zero。

 you have， you need this segmentary， if L equals to1， you need this segmentary。Right。If l equals to2。

 you， again， you need to remove this element。And at these elements。不。And so on。Then you have。

 you remove this and this。If L equals to4 something of this。Go come add this。Okay。And so sorry。

 I need to stop at some point。那什。うふん。So now depending on the value of this L。

 you need to take one of these。Segmentaries。And call the sum function in this secondary。嗯哼。

Let's have a array of these segmentsaries， so let's save all the states of this segmentary。哪个如。

Like have the state。Of segment 3 and position L。And call them the sum function in this secondary。

So what we need is an array of segmentaries for each state， we will have a segment tree。Ahu。Now。

 when we need to calculate the value on some second， you should shall we give some segment。

You want give us like。Let's reset segment。And you need to calculate the number of different elements in this segment。

So you see that left border is here， so you need this state of the segment tree。

You take this state of the segment3， calculate sum of this segment。

And some this segment will be equal to the number of different elements of the same。Good。不的呢。Again。

 you stop to post the your hands clear。 Im kind of nervous。 Im very nervous when it's。When you don't。

Don't try it and everything's clear。Okay， maybe it's stolen long lecture。オ。Okay。

 this last problem we discuss this just little just。Let's listen。Just。

If you keep it for a few few more minutes， it will be over pretty soon。第二。

Now everything is pretty cool， but we need to maintain all the states of this segmentary and the total size of level segment three is n square。

 so if you just maintain all these states， the total size will be so you need n states。

For each states， for each state， you need to maintain this segmentary。

 so total size of all this segment three is n square， we can just maintain n square。Memos。

 it's too big。So what we do？We will use persistent segmentaries like we discussed in the previous lecture。

 so what we can do is maintain this segmentary is a persistent persistent segmentary。

So we will make this first。Smentary。Then we will apply these operations， So we。

WellEvery time we move from this state to this state， we apply only to operation。

 so we apply this operation。We apply this operation。Then we have the new version of this segmentary。

Then again， we take this version of segment three， apply to operations， so apply this operation。

 apply this operation。And get the next version of this segmentry。

And if we use set persistent segment three like on previous lecture。

Then we can have all these versions of the segment three in one big data structure。

And the total size of this big data structure will be just N Logan because each time when you make operation in persistent segmentary。

 you create loggan new nodes。So each time you move from here to here。You create a log in。

 your notes and use persistent symmetrytry。 So the total size。 So if use persistent。Co。Segment3。

Then the total size。We'll be inlog。嗯哼。That's that's all。So how you create this together。

 you start from this， you create this。You create a state of zero just by  addingging these ones into these positions。

And something， then you it for all I from0 to n minus-1。Then you。Create new state。有人。

State use A plus1。Just by taking the real estate。Okay。And apply in these decorations like sit。

Something to zero and set。三分多完了。の something you mean。You set i to zero。And you set next of I。To want。

So if you use persistent data structures。You can just apply the separation and。

Get the new version of this data structure。And you didn't break the previous version。

Not too many of them。Let's have four together， let's have eight elements。お。

I'll just repeat the same process from the previous lectures。So in the beginning， I have this， array。

 so I have this segmentary 1，1，1，0，0，1，0，0。Yeah， so I built this segment for for some。でと？到。

This is the segment three for this first state plan。This is for l equal to0。

 I have this segment three。Now I need to change this element。To0。And this element to one。

 so I use it I just do it in persistent way， I change this element to zero。

But I also maintain two versions of this note， this previous version and new version。

 and I changed this note to。One， listen no， yes， listen no to one。So for this note。

 I also have two versions， first version zero， second version of one。

And now I just create all the top node。 So here I need to have this node。

 So I clone this node to the new version。 new version will have one。

 I clone this node to two with this。とます。I clone these two one。I call this to2 and I call this two4。

And now I have both versions of this segment。So when I need this first version。

 I just call my recursive function from this root。And when I need the second version。

 I hold the same function but from this root。So I have different results in this segment or in this segment。

Okay。And so on， and then they apply next operations to get the second version and so on and so on。

Then you calculate all these versions each time you go to an exc。

 you create log n your notess in your segmentary， so total total number of nodes in all these versions will be N login。

不错。Yeah。Now that's basically one of the applications of the persistent data structures as well。

 so why you may want to use some persistent searies for example。Is when you have something like this。

 so you have some segment three。And when you。Need to answer query。

 you need to find one of these previous states of your segmentary。

 so just remember all the states of your segmentary in persistent distance segmentary。

And when you learn you need to find some previous state。

 you just find this state in your area of searies。And use this state to calculate your result。嗯哼。😊，酷。

Okay， I think it's enough for today。