# 【精译⚡算法与数据结构】PavelMavrin p46 p45 A&DS S03E14. Y-Fast Trie -BV1NLB8YfEMq_p46-

🎼。

![](img/4c8aab7e16c598b369a4aa9f336382c4_1.png)

So it wass start a new topic。We finish talk about strings， and。In the last two lectures role。

Talk about something different。I will talk about specific structures for integers。

These kind of strange topics in it's mostly theatical。

 so the data structures we'll discuss today and next week are mostly useless in practice。

 but in theory it's kind of cool to have the data structures because in theory you can say that actually we can do this。

Now， solve this problem in these10 complexes here。 in pra， usually you don't need it。 but okay。

 you'll see why it's not that very practical， but。Like what what is， what's the stories about talk。

 The stories that like。Usually， we have data structures like binary search trees。

 like segmentaries and other data structures。 And when we use these structures， we use， we。

 we have some。Absstruction mode， so we have some abstract objects。

And some of absorb operations with objects。And。Like we proved， for example。

 for binary research trees， its like impossible to make binary search trees faster than en logan time。

If you you only can compare to to two objects， if you can just if you have comp。

 you need to run this comp login times to find the place of your objects in the sorted list， right？

ああ、そう使えない。But sometimes you actually need data structure for integers。

 so you know that the objects starting your data structure are not some abstract objects。

 but they are integers。And we can do various stuff with integers。

 We can do do all our ametic operations。 We can do some other stuff。

 so we can index with integers in in array， so。But you have much more freedom when you work with integers not with some abstract objects。

And so people at some point starting to research what actually？

Ha can you actually improve the time complexity boundaries for this standard。Well problems。

 if you worked off with abstract objects， but with integers。

And it turns out that in some computational model， you actually can。

So I'll talk about what computational model were working。Let's say we have all this， basically。

What's， what's the motivation。 So if you， if so usually we work in the Ram model， right。In red model。

 you have Yeah you have this you have。

![](img/4c8aab7e16c598b369a4aa9f336382c4_3.png)

And you can get。Any element from your M in constant time just by index。

 So you need to store this indices somehow。 Yeah， so this I should be stored somehow。

And how to store ins no。Most usually you saw the integers in some beautiful form。 so so so this eye。

It is just a sequence of zeros and ones。Maybe not。 but usually let's， let's， let's， let's say。 Let。

 let's do。 And what， what can we we do with this integers。 You know， if we。

 if we need to index in the array we。Most probably will need to be able to perform some arithmetic operations。

 So we need to be able to calculate sum and difference and so on。Because how to index in the array。

 you need to find the first element of the array here。 So if you have the array in your。R。

 and you want to index in specific element of this array。

 You need to find the first element of the array， then add the difference。

 So you will have the index of the element of your array， right。

 So you kind of need to have plus separation for your integers in constant time， right。And。

The minus is actually the same as plus not， not， not an Neoleic。 What about multiplication。

 multiplication with it more complicated。 Usually， you kinda need multiplication， but not exactly。

 we will say we。Can multiply to two inches in constant in time。

This actually is an open servicealment here。Because multiplication is actually kind of。

Multipplicationation is is hard operation。 Yeah， so adding two integers is actually。Quite simple。

 You just go from here here and add these bits。 Yeah， you， you can do it in parallel and so on。

 So So for multiplication is little bit more complicated。For example， you cannot build the。

Multiply your if you just use there。Bulion operations。 Yeah。

 so you can build build a Boolean scheme of。Constant depth with polynomial number of fila。

So it's so for multiplications， slightly different but we will assume that we can multiply to elements in constant time。

嗯。你vis也讼得你。Integer division is very a strange operation。Again， it's even。

Even more complicated than multiplication usually。 So to divide one integer to another integer is kind of strange。

 You kind need to put each bits。 when you put these bits。

 you need to multiply this by this and check if it is not and so on。 So。

 so the integer division is complic operation， but we will say that we also can divide on this。

 We actually don't don't need it that much。 But let's just edit。啊，那。What else。啊。Yes。

 you can use you can use the for multiplication， but still it's not in constantstantaneia。

But we will assume we can multiply to integers in constant time。 So if we have this integer。

 So we have this in。Whyhy you may need multiplication in in your standard run model， For example。

 you have some array of objects。 Yeah， so if you have array of objects。

 you want to find the position of these objects。 You need to multiply the index by the size of the object。

 So you know the position of your object sounds like that。It's actually not quiet。 You can do it all。

 but。Still， let's， let's， let's say we can multiply elements。Okay， that's a strange theory。Now。

 what else do we need？We will add also， E bitway operationss。We will add bitwe and bitwise or。

 bitwe so， and so on。啊。You actually do it without you can do the of this stuff。

 but I will just say it because of that。In practice。

 these operations are actually simpler than than all arithbetic operations。

 So the bitwise operations are actually。Easy to parallel because you can just you can just apply the bullet operation to every bit in parallel。

 yeah。So these operations are actually easy to implement in any processor in constant time。

And the multiplication is kind of complicated， but this bit variations are actually easy。So。

So I'll just say that we can do the separation in constant time， and we also will need some。

 let's say。Bitwise shifts。 So we have。Shift to the left and shift to the right。

So this just move all the bits to this number of positions left。 Al right， you can。

You can avoid the separation。 If you have multiplication， you can actually avoid the separation。

 You can just multiply by the power of two。 You can precalclate all the powers of two you need and then multiply by the corresponding power of two。

 So we actually actually can avoid the separation。 but I'll say， again。

 these operations are much easier to implement in processor than this multiplication。 So if。

 if we allow to use multiplication。It's safe to assume that we can also do all these operationss of course in time as well y。

Okay， little scary， right？No。Now。啊。We need  one more parameter in our system。

 This parameter will be the size of the integer we using。 So we will say that in our system， we use。

We use intes of size， doubleubling。So the size of the word in our model will be equal to this W。

 so all integers in our model have size W。And this w will be the parameter of our computational model。

 so when we calculate10 complexity， we'll have two parameters well have size of input and the size of the work in our model。

嗯哼。😊，嗯。Yeah， I believe that's all we need by now。Now， let's move to data structures。

 What we'll discuss today。 Today， we willll discuss data structure。

 which is actually a binary search tree。So we will make all decorations which we have in binary research tree。

 So what operations do we need in binary research tree in binary research tree。

 we need operationsations like insert element。A。And find the element。 find element。

 Let's say we have some li and C plus but who have lower bound。So， it will find the minimum。W。

 which is rhetoricgon X。like in C++ setting in SL， right？It will be enough。

 So if you just use a binary search tree。You can do all these vibrationbras on log and timeium。

It was BSD。You have logan。For all operations。And again， like we proved。

 when we discussed the lower balance for sorturing algorithms。

 you cannot do binary search faster than loggan time because if you do binary search faster in loggan time。

 you can sort the elements faster end loggan time， you can sort like absorb elements in faster and loggan time。

So。Now， what if we have integers again， what if we have integers？We can， actually。

Make B shri faster than in Logen time。 how， how fast they can do it。

In this lecture and in the next lecture rule， it's discuss two data structures first this threshold will discuss today。

First data structure comes today and the time complexity for this data structure。

It's called white question。Yeah， I called lecture X X Tri but。Actually。

 at the final was going called Yfi twice straight naming they have x first try and y first try like this。

So x first drive will be like the middle point before we actually achieve the complexity of y first try。

And for wife first try， we can do all these operations in time。Lo battle。

So the logarithm will be not of the size of the input， but of the size of the work you working。

There is now the structure of symptom complexity is called oneom the bow screen。1 am the ball string。

I will not cover today。 Maybe we'll do it in San Buno lecture。 It's kind of interesting。

 but it has all the same time complexity sort。Not that。

It's not that important in this in this course， but the say that this two structures basically have the same time complexity to do the same thing。

 but have absolutely different structure， but do the same thing。

And there is not data structure we'll discuss next lecture， it's called the Fusion for。

We actually have and complexity。Log and bay doubling like this。Now， let's let's look。

 So what happens here。So。X fast try and Yfitry， yes。

 X fast triesries just will be just the middle point before we actually get a Wifa try， yeah。啊嗯。Yes。

 white first strip is basically extra strip plus some tricks。 Yeah， that sounds fine。啊。

What's interesting here， What's interesting here。 So if you look how the time complexity changes when you change the size of the wordd。

 the time complexity of one of the Bo3 and whitefitry is actually increasing。

 So if you increase the size of the word。These time complexityities increase。

 So if you just increase this double your soul， this time complexity goes up。

 but this time complexity goes down。So， so these data structures work good and you have small size of the world。

 so number of bits here is small。 So if you have small number of bits。

 you can use these data structure。And if the size of the world is big。

 you can actually use this discharge because if you increase w。

 then this logary will will be decreasing， right？And that's interesting because。What we can do。

 We can check。 We can。 We can， We can see， we can。Just choose one of these data structures based on the size of the word。

We can。So so if at some point。You need to build data structure for the given size of input and given size of the word。

 You can check which one is better and choose one of the data structure。And if you do this。

 you will achieve quite good time complexity better then。En login for the sourcecing algorithm。

 Well discuss it next time when we will talk about fusion trees。啊。Yeah。そう。Today。

 we'll talk about visit structure。Mmhm。😊，Again you forgot to say things clear every mean。ok。Soわです。

That's our plan for today。Let's go。What so what's this structure rule will be built to these structures will be also to build extra spray。

Then will modify it to be wife first right。main idea of the X try is build this structure which have this tank complexity for the lower bound。

 so first we will make this tank complexity for the lower bound function and then we'll apply some more tricks to make the insert and remove operations working。

In in log double time as well。Go走。What is X try。 X try is basically try。

 So I like this exc here because it's kinda connected to the all the previous topics。 So in in the。

 just in the previous topics， in the previous lectures， we talked about stringed structures like tri。

 When we talk about aho can I it and stuff。 So just we will apply the。Its basically。

 the same instruction twice。To4 integers。 So what we'll do， We'll make a try So every。

Every integer is basically a string of bits。So what we'll do we'll build a try of these strings。

 let's say。Let's see what we have， let's say。Let's see W equal to。Let's take four betweens。So。

 we have。Elements， let's say0，0，1，0，0，1，1，0。왕 zero 지 왕 왕。이지로 뭐 태는 좋아하는 뭐 되지 이로。Yeah。

So let's have these five integers now set。What we do will then try from this industry So again。

We look at each of its integrals as a string of four characters here。

 so we have two characters such as 0 and1 and just build a trial of this。So go from here we have 0，0。

1，0。The first element。 now we have 0，1。1an。0ero， peace element。아 오버네지 이러。0，1。Here。11。Ziru。W。

And why like this。有。嗯。No even if you could had bit。

Like can all of these structures is not a problem when you have repeated elements。

 You just can you can have a array of counters。Yeah。

 so if you have some repeated elements in your set， you you can have a counter for each element。

 how many elements of this type you have in your set and so on so。So it。

 it's usually quite easy to move from set to multi set。II'll talk about set， but it's so。

 So I don't have any repeat elements。 But even if you have repeat elements， usually。

 it's not a big problem。어。Now， how to find the almost。 Imagine you build this stream。

How to find the lower bound for a given chip now。You want to find lower bound。For something， we say。

I don't like this。So given sub integer。You want to find the lower bound of this inter in this。3。

So what you can do you？Just follow these。Follow this by from， from from the。

You try to try to find the smallest integer， which is greater or equal than this。

So we try to find this integer。 first， let's try to find this integer in our try。

 so we just go from top。Go here。 Go here。 Go here。And at this point， we want to go here。

 so our x must be in the left sub of this boundary here。But we don't have the last with the left sub。

So the next element in the tree will be in the right sub of this element。 So what happened again。

You are looking for some element x。You start from the route。 You follow the path。

This path is a prefi。Of the element X。And now， the path goes to the right。To this right up。

And your x must go to the left function。 So in this x。You followed this path。 and here you have 0。

 so x must be here。But in this， in this node， you don't have the left left child。

 So you you cannot extend with0。 Yeah， so you need to go to the right child。

And then in this right subre， you just need to find the minimum element， right。

 So in this right subre， you just find the minimum element。

This minimal element will be the next element， after x。So， again。X must be here。

 so the next element is in the right sub， and it is the smallest element in this right sub。

So can how can we do it， We just， we can just preulate the minimum element for each sub。

Like in segmentsaries， exactly。 So for each sub， let's precalulate the minimal element in this sub。

 So here we willll say the minimum element。Is 0，0，1，0。 Here is 0，0，1，0。 Here is 0，0，1，0。如は忘。

so on so for each sub， you can precallate the minimal element in this sub。うんふん。😊，응 응 응 응。嗯。And so on。

For each sub， we can precalculate the minimum element in this sub。Yeah， yeah。

 yeah that's a good point， I'll talk about。😊，Yeah， no， that's a good question。

But let's first solve this situation。Now， in this storage， what happens， we follow this path。

 We end here。 Now we want to go to the left。 So we go to the right sub and find the minimal element in this sub。

 This minimal element will be the next element。4 the x。

What if Els bigger than oh just return something， just return something now something。

So if your elements are great than all elements3， you just return something like you control exception or something。

 you just say that there is no element in your subri， which can do it。What's interesting。

 interesting thing happens。When you， for example， have。L bound of， let's say。Let's say 0，0，1，1。

So here we have slightly different we go we try to follow this path and go here we have 0，0，1。

 and here we want to go to the right sub。But we only have the left su。嗯。So it's like。

Me your situation， So if you。So here now here you want to go to rest but but you only have left something。

And you want to go to the right option。How to find the next element in this case？哎。

It's a bit more complicated。Since the next element is not in your factory。

So you kind of want to go up， then go to the right substrate at some point and then find minimal element there。

 but that's。Do much work。Let's， let's do it Egypt。Let's do it like this。

Let's go to Le up and find the maximal element here。

So this element will be the previous element of x， so it will be the closest element to the left from x。

So here we will do this element。So it's not the lower bound for eggs。

 but can the previous element for eggs，So it's maxim element， which is less than x。

 so we want to find minimal element greater than x。

 but we actually found the less max element less than x， but we find the closest element。

 but from different sake here。So how to move from here to here。

 So this is element we're actually looking for。Very easily。We will just add a。Liinnk list。So。

 we will just。Link all the it。Link all the leaves of these tree with the list。 Oh Ed。These point ups。

そう。Now the solution is very simple， so if we have this situation， we try to go right。

 we actually go to the left。Find the maximumimal element in this sub， and then use these。Po enter。

 go to the next element， so this element will be the element we're looking from。Okay。😊，That's all。

Again， what's the structure， We build this tray for each sub。

 We could create the minimum and maximum element in this sub。Yes。

 we yes we need to calculate maximum values for each sub。

 we calculate minimal and maxim element in this sub。NoActually。

 we need to calculate and notice integers button this。Asポs。So actually。

 what's going on for each sub tree？In the root the root of the sub， you have pointer to the。

To the maximum element and for enter to the minimum element in this option。

So you need these two pointers。And also， you you need pointers for each leaf to the next element。

To do the next leaf in the order。All the leaf， actually。Link for this link list。

What if no live option。There must be at least one option。

And every node in this trial have a list stuff has least one subject。嗯哼。The the only elements。

 which has no surprise other leaves。 And if， if you， if you follow all the path end up in the leaf。

 then this is your element you're looking for。そう。Every node， except leaves。Has at least one sub。

So if we cant continue this path， then there must be another sub。 So if it is left sub。

 you go to the maximum and then next， if it is right sub。

 you go to the right sub and then to the minimum。嗯嗯嗯。으。You can avoid disconnect connectinging lift。

 or now。How can it work。呃对对怼怼一怼。You might have another solution for it this wasn't the most easy solution for this for this problem。

I believe if you actually want to save some memory， you can do it。Yes。

 you can find a little bit easier solution， but。That's the easiest easiest way to solve this problem and then do the thing I want to do next。

Because right now right now is's not what I'm looking for。

 So right now time complexity is not an example you as expected。Right now。

 tank complexity is actually a double you。So term complexity of this solution is actually because of doubleing。

Why it is so big because we need to follow this path， so the size of this path。Maybe be up to W。

So we need to follow this perfect friend。So for this perfect we kind need to follow this path from the route to this。

The first， first first time we don't have the edge。 So to follow this path， we need to spend。

This time。Yeah， also， the memory complexities to begin here also。The memory is now N W yeah。

So we used too much memory and。We actually use too much time to make us。 so let's fix this。

 So by now what do we have？Let me fix the results here。So right now。

 if we want to work with this data structure， what can we do how to insert new element in this data structure。

 just you just like you insert the element in the tray。

 you follow this path and add all the edges you need to add so you can insert element。

 just follow this path at all the elements， then rec the maximum minimum in each sub time double。

You can remove the elements in the same way。 so when you need to remove the element you again you follow this path。

 then remove all unnecessary edge so if you don't have any children。

 then you remove the next one and so on， so you remove all unnecessary edges and remove all unnecessary nodes。

And then they minimums。 again， you need only to update this。One path in your tray。

 So this path has length W so you can remove element and time double。

Basically the same like you remove elements from the tri。In string colors。

And how to calculate it lower bound when you calculate it lower bound， again。

 you follow this path then go here， here， here， and you find the lower bound。 So thank you very。

W and memory complex is N W。うふ。That's not put I， actually。Not what we expected， here。

 we tried to build it pressure for log W， but now it have W and W is more than log W， right？

So let's fix it。 So the first thing will fix is this lower bound time complexity。

So for the low bound darker places， you will do the whole trick。Let's let， let's see what's actually。

 what's actually the most。Thank I you in part of this。Of these， the structure type。

 most time consume in part。That's， that's not extra string I will apply this trick and it will be extra string。

 The most time consuming part here is to find this。嗯。Find this note。 So to find this note。

 I follow this path from here to here。 That's very time consuming， right， So what we'll do。

We will try。To find this note first than in time W so。

How to find this node faster than an engineer time。It's actually quite easy。

What's this note this node？Actually represents the maximal pre of x。Which has a note in our try。

So we need to find the maximal prefix of x。Which is actually in our tray。

And how to find the maximal prefix which exist in your try using binary research， of course。

 let's make a binary search。Over the size of this pre。

Let's micro a binary research and find the largest prefix。Which actually exists in your tribe。

But to make a binary search。We need to be able to check if given pres actually exist in our trial。

Can you니까。Again， the you given this。given this integer。

And we do binary search to find the longest prefix。 So first， we check pre 0，0。 Oh。

 we have perfectx 00。 Okay， so we extend it。 So make binary search here。 We check prex 0，0，1。

Oh we have this pre。 Okay， let's go first。 So we check ref 0，0，1，1， or we don't have it。So。

 it's plus， plus， plus。マイナ。So after log durations， we'll be able to find the longest prefix yeah。

And we can check if the pre is in our try using hash tables。We can just for each， for each note。

 we can precalculate the integer corresponding to this note。 put all these integers in a hash table。

And then well be able to check in cost and time。Again， what's the trick here。

 T here is that these strings are actually strings they integers。

You can put these integers in a single word，So and you can work with these integers like like with integers so we can calculate hash function of this integer in constant time。

Put these integers in a hash table in constant time。

 and then you can check if your given integer is in your hash table again in constant time so you can do the binary search and either step of your binary search。

 you just calculate this prex。 You can calculate the prex again using all these eriithmatic functions here。

So again， if you need to calculate this pre， we just need to erase all the bits here。

 So we just make the string of all zeros removed it from your string and then。You only left this。

Bs here。 So you can use these bit decors just to erase all bits here and only left bits in this side。

 So you have this prex as an integer。Look， look up in your hash table and check if this integer is in your trying。

If it is， then you continue buy the research that set is not continue this。So again。

 you can find this pre。In log and time， just using binary search plus vegetables。Yeah。

 that's downside of this instruction you can need to have a good hash table for this instruction。

 but we'll assume we can make a good hash table so we actually can for integers。

We can actually prove the。ああ、そう。So now the lower bound is actually working in log double time。お多。

Mhmm。And that's actually the x tray， so x try is actually the structure which can find lower bound for the given element in log W time。

 but all other operations are pretty small。嗯哼。No no that' 어。I think quite quite a cool idea。

 So so again， the the own idea we need。Is that we can find the maximum preface。Of。

 of the given integer， which is in our try using binary research。You actually don't eat this tree。

 You can， you can do it without trees。 You can just。You can just make on on the Hh table。不理。

You actually you actually don't need all these tree as a structure， yeah。

You only need a hash table for each for each integer。 you can calculate them。So if if you want to go。

 go， go to the left， you just add 0 to your value。 If you want to go right。

 you add one to your value。 So you just。Represent your node， not as a node， but as a。Integer。

You still need this link， Please check。嗯嗯嗯。Okay， is it， iss it clear enough。なな。Now。

 we will solve solve all all problems。 Other problems here are in certain remote population works in。

In time double not in log double and also the memory complexity is to be。

 so the memory complexity should be linear。W decisions different leads writers， which。别别别别别。

いやや不要やや用这对对 그렇지。That's a good point。 So we yes we actually if we just take the some prefix。

 you may have the same integer for different levels。 for example， for this node， you have integer0，0。

0，0 because you removed all you take only prex of size 1 so your element is here and for this element you have integer 00 because you removed all everything except first。

 so so injuger is the same， but yes there are different ways to deal with is。

Easiest way is to have different hash maps for different levels。 So for each level you have。

 you can have different hash map。Only for ingers in this level。

 So you only you always know the level you're working on。 So So it's easy。

 Another way to solve this problem is when you want to represent the pre of injury。

 you take the prex here。And then add one here and put all other zeros here。

And this one here kind of says， what level are you working on。It's not ways of solving the problem。

 so。So you again， he will remove all bits。Accept your pre and then add one in this position。

It's not the way it's soft， yeah。Yes， you， you， you need。 you need to have W plus 1 B。 You need。

 you need to have one extra bit for this situation。 But yeah。Yeah， so so。

 so there are some small details I I I。don't talk about。 But， yes。

 all other details are actually easy to solve。Whoof。Let's go next， so next。

I will use the trick so so again， to solve this problem to to reduce this and complexity and this memory complexity。

I will use the same trick we used in the previous semester。

When we talked about about about least order maintenance， may maybe remember。 So。

 So when we have this list and we try to find。In constant time， which element is to the right。

 Which element is to left， maybe a remember。So we had kind of the same problem。

We have first time for to check which element is to the right one。

 but we have a big time complexity when we insert or remove the element。Okay， it was。

It was a semester ago， maybe you forgot， but we'll use kind of the same trick。 What we'll do。はいち。

We you have all of it interest me。And we will split all these integers。Into groups。Okay。

 we need bigger examples。 So So let's have some big example。 Let's have again。But。

 let's have1 points in the phone。Okay， for44 should enough， let's have some more images here。1，2，4。嗯。

5，7。え then。12。1515。So we have this big list of individuals。So these are the elements。

We need to put in， in our data structure。We will split them into blocks。And the size of each block。

Will be about w。ややや。うんトるんトるトる。う什。Let's load one element again。Like this。

 So the size of this block will be from。嗯。From double， divided divide divide by 4 to double。嗯m哼m。😊。

And now we will build the data structure。The same structure we used do。

 So we can build X3 not over the elements， but over the blocks。

 So each block will be represented as an element in our X tree。How to do it？Basically。

 what you need is to build something like so when we split all elements into groups。We have some。

so let's say so all， these elements are less than these elements。

 So let's say we have these elements are less than， let's say free。

This element are greater than free， but。Less or equal than 7。Y。So elements here are greater than 7。

 but less or equal than。11， for example。 And these elementss are great to them。11。

So each block is actually a segment of values， right， so let's find the boundaries of these segments。

And now let's just add all these boundaries to the express train。So with the curve of this element。

Free element，7， and element。Thank。Oian 3，3，3， freeze 1，1，0，0，7 is。0，1，1，1。And 11 is。It's 8 plus 3。

 right？ So it's 8。Last free of like。응 해。So that's how this structure will look like。Again。

 what happened？These are the elements。We split them into blocks。

 The size of each block is in the range from W over 4 to W。Now， we find some， some， I know。

 some middle points。Which can distinguish these blocks 1 printer so and we put all these little points in this express try。

Now how to find the next So first， let's see what we didn't break anything。

 Let's say which we still can find the lower bound in this data structure in log W10。

 So how to find a lower bound in this data structure。Okay。 so what do we need again。

You want to calculate lower bound。Let's say， for。4， let's say。6。So how to we click over bound for6？

What we need to do is to find in which block actually sixs masblanto。

So how to find the block for the element 6。We need to find the closest point in this。Upper tray。

Which is above this6， So we。啊。Yeah， so we on a lower bound for this tray。

For this value S for this value 6， find this value 7。Now。

 we know if we have six in our in our in our set， these six must belong to this segment。

 so6 is somewhere here if it is in the set。Now， inside this small block。We can run the lower bound。

 try to find the lower bound inside this block。 How to find lower bound inside this block。

This question。So again。We split the operation into first， we find the block。

 and then we find lower bound inside side block。We can find the block using the same lower bound function for this express tray。

So we can find the block in log W time。And now we need to find lower bound inside this block。

 How to do it。Yes， you can use binary search inside this block。 actually。

 we need to update this block。 So we we need to use binary search tree。 Yeah。

 so we so for each block， we actually build a standard binary search tree， AL tree， red black tree。

 the one you would most like。And we're run by the research here。

 so we'll spend a little bit double your time。No， no， no， it's not。 It's not the hate。ItsSo we spend。

Log W your time to find the corresponding block plus another log W time。

To find the position inside the block。Still be looked up。啊。It may happen。 It may happen。

That you actually find the block， but your element is not in this block。For example。

 what happens if you calculate lower bounds， Let's say 4 element 11。Soここれも。Or3，11th right。So again。

 you very quickly to bound for 11， youll find this element。So if 11 is in your set。

 it must belong to this block。Now， in inside this block。

 you try to find the lower bound 11 and see that all elements in this block are actually less than 11。

 It may happen。So you try to find the position。 But you see you find out that in this block。

 you actually don't have any element， greater equal than this。

What you can do mouth you can can you can， you can make a linked list。But actually。

 what you can do it easily， you can just go to the next block and find the minimal element in the next block。

 So if there is no element in your block， you go to the next block and take the first element in this block。

 like the minimal element in this block， and it will be over bound。

So you can you need to check at almost two blocks， you need to check your block and the next block。

Your lower bound will be in one of these blocks。嗯哼。That's all that's how you find the lower bound。

In look double your day。So we didn't break anything， right？So by now。

 the time complexity of the lower bound is the same。😊，So we material。Yes， we can。

 We can maintain blocks and linked list to the faster。 So we need to move from one block to another。

 We can maintain linked list of these blocks， here。Now， what about memory complexity。

 What about memory complexity so。The total size of all these。Binary search trees is linear， Yeah。

 size of binary search tree is linear， so the total time of total total memory complexity of all these binary search trees is linear。

And what about number of elements in this。Try。In this try， we have。About and over W leaves。Yeah。

Because each leaf represents some block。And the size of this of each block is at least w over4。

 So it's like like。Snow more than4 n over W， right。The size of each block is at least w over4。

 So there are at most。4 pen over W leaves。 So the total number of elements。

In this trial is at most4 M。So the size of this tray is linear。Again， it was multiplied by double。

But then we reduced the number of elements by w。 So now the total number of elements here is linear。

Okay， let's update this。P。And finally， finally， we need to update this insert remove versions。

 So what happens when you insert your element。Let's try to insert something。

Let's try to insert something。 Let's try to insert a， for example。8 it will be here。응。

Can I insert something to make。To make it overflow。嗯嗯。Okay， listens sort of6， for example。

So what happens when I insert6？But first， let's find the block。The6 must belong to。 So again。

 we on lower bound here， find this block， then add 6 to this block。Yeah。So again。

 we run lower bound operation here， find this7。We'll find the six must belong to this block。

 Add 6 to this block。We do this in log W time。And then insert6 here in log W time again。

 we insert six just by inserting this element in the binary search tree side of this binary search tree is w so we insert6 in this binary search tree in log W time。

At some point。There may be problem。 So this size of this block may be too big。

 So it it will not fit in this range。So what， what what we need to do。

 then the size of the block is too big。 For example， let's say this block is too big。

 So it's it's4 it actually， it's actually fits， but no。Let's just imagine this block is too big。

 So the size of this block is。To need to do something。So what we what can we do。

 Then the size of the block is too big。 We can actually split the block into so we can take this block。

And split it into two blocks。So again， what happened。

 I inserted new element in the in the data structure。 I inserted into some blocks。 Now。

 when I insert new element in this block， this block。It too big。 I need to do something。

 So what I will do， I will split this block in half。そ。So Ill have this block and this block。

I will adjust this。Border stone in in left border， I will put all elements greater than free and less。

Or equal than 5， let's say， And here well greater than 5 and less or equal than 7。Mhm。And now。

 so this five is a new border on this， let's make a threadread。Now。

 I have this new border board border between these two elements。

 I need to add this5 into this excess tree。 A I I can add element in an excess string。

 I just add this 5 to my excess tray。So 5 is 1，0，10。Mmh。So again， what I did。

 I split this block into two blocks。Now， I get one more border between these two blocks。

 I add this border to my express tree。Ex try。애드청。That's how I deal with big blocks。

 So if I have big block， I split it in2。Make a new border。 add new element to my express train。

So what's our complex for short？嗯。So what's some for this insert operation。 First。

 I need to find this block。 So I need to find the block。 I need to add my new elements。 So I need to。

Spent a log W to find book。だなにと。B double you to insert。嗯う嗯。How to split the block quick。

 I will just split it manually。I will spend W time， please。So I need to add new element here。

 So when I need to add element here， I need to spend w time。

 so I can spend another W time just two its right through all elements here。 find the middle point。

 and so。And two split。Block。Yep。So again， when then the block is big。

 I need to spend double time to insert your element here， so it doesn't matter if I do it slowly。

 so I can insert all elements of the block， find the middle point。

 just make area of this element area of this element， I just hold the border sensors。So。

 you don't need to do it first。You actually can do it first。Yeah， if you have binary search trees。

 you can split binary search trees in two。Using split abras， yeah。But you actually don't need it。Now。

 let's see。そう。So this expression is actually。Cosely。 So so I need to spend W time to split blocks。

 but it actually happened not very often。 So what happens if I split the blocks。

 then now I both sides of this box or both this blocks up。 So if the size of this block is。W。

 I split it into two。Now， size of both these box is W or2。Now。

 before these blocks will overflow again， I need to insert W or two elements in in these blocks。

So the size of this box is far away from the next overflow point。嗯哼。So this split operation。Actually。

Need to perform the separation every。Do about operation。

So we don't split blocks every time we split blocks when they everflow and if the blocks are flows。

 it will split into two blocks of size W over2， so it will be far away from the next overflow。

So before the next workflow， we need to add another W over two elements here。

So this operation happens with each element， at at least after the next double operations。

So the like average time for this version， like amortized time。

 So if you remember how amortized time complex。 So the amortized time of this。

Split will be constant here。But so， so now the total amortized time of insert operation is log W。

 log W here， plus amortized one here。気持ち。嗯哼。😊，The same thing with remove elements。

 when we remove element from the data structure， we remove it from the block if the block is too small。

Then we merge this block with some neighbor no when this block is small。

So you have some block of size W over 4。 and you want to remove some element from this box。

You take some another block。And try to merger this book。比个。

I don't remember if you discussed be trees。Do you know how beach trees work。

It's actually the same algorithm we used when we。work with beaterries。

So what what's what's happening when the size of the block is too small。

 You take the neighboring note the neighboring block。If the size of this block is。

 let's say less than W over2。Then we just mark this block into one。

 Then we have block from size of size from。Again， the size of the block will be from W over 4 to W or4。

 So size with this merge block will be from W over2，2，3，4。저。And if this book is big。

So it size from W or two to W then。You can take this block and just split the elements even。

 So can just。Have something here and something here。 So the size of these things will be from。

W of4 plus， is it just split B or is this split fit。3，8。Right。Again。

 the trick is that after this separation， the size of this block should be far away from both points。

 you have like you have two extreme points。W over4 N W。

And the trick is that after all these operationsations， when you merge something， split something。

 your size of size of your book must be far away。From both these points。

 So it must be some alphat here。So if your size is in this。In this range， you are fine。

Because before you need to apply the next。Slow operation。

 you need to add at least these many elements here。Or remove a this mean。

 So you need to remove these elements or add these number of elements。 And if both this。

Gaps big enough。 Then you are far away from the next slow。Yes。

 we discussed Peter is when we discussed external me Oh yeah。

So it's kind of the same trick like in be trees。That all。

So that's how we that's how we make remote operation look like。嗯。Everything a little bit more test。

なななんてなくてだけわけ。You can say it something is mostly something。嗯。Good。So let's let's buy first string。嗯哼。

Again， you can use WiS3 when you have a small size of the interso if the number of bits is small。

 you can do something like that and actually have better time complexity than you have the regulatory structures。

So again， you can sort， for example， again， this is the binary search tree。

 You can sort elements using this。 So you can actually sort the integers using the data structure in。

And look I believe them。嗯嗯嗯嗯。응 응  응？Though it is at least， yet。

 it is at least trim And since it it most double you。 So the max size will be。E5，8， I think him yeah。

So again， both these borders will be far away from the next。嗯。For， for， for from look。

 for is 6 points。Mmhm。Now， before before we next。Let's discuss this one。嗯。

What is actually better to have outlift moon？AL， double complexity here。Or。Loan。Which one is better。

 What do you think。嗯。Thing is usually in practice， in practice。W is much smaller than N。

 W is the size of your in size of the word。So it's usually like 32 or 64 or 1，28 at maximum， yeah。

So usually this w is pretty small。啊。Yeah， and usually we work with them big data structures。

 so usually number of elements is much more than number of bits。But in let's this practice。

 And as I said， these structures are not very practical。 In theory， what's the。

Connection between this， W and N。And。For theory， the only connection we know about W and N。That。And。

Again， how this W and N are connected？They connect， very simple way。啊呃。N is an integer。

 n is the size of the input。 So we need to be able to store this n in in this war， right。

So this number of Bs should be enough to fit number N。So W should be at least log。

And the problem is that' actually the test all we know about W。

So no w is at least login because if it's not， we cannot store the end in in this from in in this work。

 and it's kind of strange。But we don't have any upper bound on this volume。 So W company bigs。

 why not。 So have we can have small structure with a very big integers。 Why not。So again。

 this infrastructure works when the value is small。ややや。What happen if that E W is big。Again。

 next lecture will discuss Fusion trees。It's very cold。 It structure。It will help。

ItIt will take the full advantage of this big W。 second now let's have yeah。Yeah。

Just to give you some。呃。Cls about what's going on in next lecture。I will。This discuss how。

 how big W can actually help you to make first algorithms。 Why big W may be a good thing。 So why。

 why may we have the algorithm which actually decreased complexity when we when we。我 we没啊。坐。

Why it may be that we increase the W and then complexity is decreasing。

It's actually maybe because there when we。When W is big。

And we still can make these arithmetic operations in constant time。

Then we actually can no like arithmetic operation on big inger is like many small operationss like yeah。

You， what's happened when you have two individualsteger here？And they co great they a loss of desper。

So when it quickly sum of two elements， you actually need to sum these elements and these elements and this and this and this and this and this instance。

 so you make many small operations in constant time。And if this w is big。

 it means you can make more operations in constant time。So by increasing the W。

 you kind of increase the like。Increase the number of small operations you can do in constant time。

And we can， we can use it so we can。Actually， use this like parallelism， yeah。

To make fascinating structures， in theory。嗯。Yeah。So for example， for example， what do we can do？

Let's solve your problems before the next lecture。 So in the next lecture we。

 I've use this technique at maximum， but but now let's just。

And I' was just let's just solve some small problems。First small problem。 For example。

 what you can do if if number of double USB。You can split it into blocks and put some small integers into this block。

 So let's put some small integers。살 of fit。He1， a2， a3 and so on， a。MK is like double overp。嗯哼。😊。

Imagine you imagine you want to do something with small integers。

 and you have a big register of your processor。 Yeah， that's actually what processes to do。

 but not exactly like like this， but。Whatち君도？You can apply some operations to all elements of this list advancer。

 So you have list of k， small integers。😊，Stored in one big integer。

You can apply some to all of these integers at once。 For example， you have this integer。애한테 나 이。

이만 미통。Be free， and so on。Wei。So let's say this integer A， this integer B。

So what will happen if you calculate a plus B？そううんうんふ。う嗯ふふふ。Ric sort yes， Redd sort is actually yes。

The time complex of ra sort is actually increasing when you increase the size of theia。Yes。

 what' happened in Ra sort， you apply operations for the different registers one by one sort its clear by the attempt。

嗯。So icシs not the go得个散。Let's see。So what will happen if we calculate some of these elements again？

What will happen to calculate some of these elements。 You take this。Two blocks of bits。

And calculate their sum。 So the sum of these two small integers will be put into this block。

 So this block will contain actually Sam sum A K plus B K。

So if the sum fits into block of size So let's say the AI plus B is less than two power of B。

 so so if if we if you guarantee that this sum fits into this。And so on， so every。

Every element here will contain the sum of these elementss。Mmhm。😊。

So we just calculate k sums into one operation。Again， this separation works in constant time。

 since we assume that we can work with these big interiors in constant。

 we assume we can make all these separationations in constant time。

If we can make operation because then we can take some of these to big integers and calculate this sum and it will contain all these small sums。

嗯hん。😊， let's let's do something more interesting。Let's do something more to。

Let's have an array again， array of K elements and have some integer case small in。

I want to find the number of elements generated a， which are， let's say， let's say。

 let's say greater equal x。不。What you need to do， usually。

 you can iterate all elements and check if this element is greater equal than x。

 but I want to do it in a single operation。Youen。All these beat tricks。

How how can you compare to elements using arithmetic operationss？

 So if you I do not make the comparison comparison It you Boolean value true or false。

 I don't want boan value。 I want some integer value。 So it will have more information yeah。

So how can you compare to elementss？Smon AI and element X。

How can you compare two integers using just integer operations？嗯。

Now base here we need to do is to subtract this element from this element。

And check if the result is negative or not。Yeah。basically， if you want to say。

Es is the same is n minus。X is greater equal to 0。有。But I don't want to have any negative numbers。

Negative numbers， actually。you can do it， but yeah， I want everything to stay positive。

So I will just add one extra bit here。Extra anyway， one extra zero here。

So I will make sure that this integer is actually great in these and then subtract them。Now。

 in the result， I will look into these bit。This beat will contain the result of this comparison。

So if a was greater or equal than x， then I will subtract this from this。Mmh哼m。😊。

This bit will be not be used。 So this bit will stay one。And if。A is less than x than when I subtract。

 I need to use this bit here。 So I will take this bit。 So in the end， it will be 0。

So this bit of the result actually contains information about this comparison。Okay。

And now what I what I can do， I can apply the same person to all these integers at the same time。

Ill do it like this。Let's put one extra one here， so。A 1，1， a2。W。Sorry I will add one。

1 extra bit here。And make the four。0 x，0， x。아 응。뭐。Then subtract this from this。

And look at these bits。M哼m。So all these beats will contain information。About all the computer。Heh。😊。

No， no， took them， took back get it。Yeah let once again， what I trying to do。

 I'm trying to compare x。To all elements in array array A。Using only integer operations。

 because bullet operation takes you to give good tools to， to too small information， yeah。

So when you compare how to compare elements using inter reparations。

 you just subtract element and look at this bit here。How to， how to count these bits。

 That's a good quality。 That's a good question， just。Different。Yes， we'll talk about it。Right now。

 let's let's stop here。 So Yeah， how to compare to interest you you you put one here， put0 here。

 subtract and look at this bit。So this bit contains information about this compassion。Now， good。

 good question is how to， how to count we need to take some of these bits。 So we now。

 now we need to take some of this。 Let's put some alphabetta。Like this。

So we need to calculate some of these two bits。Of four bit。And again。

 we want to do it in constant time using some bit magic arithmetic operations and stuff and so on。

So again， we calculated it as D。There's8 minus6。Okay。By the way。

 I miss this point how to build this array， how to build this array of x's。

 so I want to have x and multiply it k times。Is it clear how to make this ring。小衣服。

So we have this small integer apps。And you want to build。This area of access。

This is clear how to do it in constant time。嗯。So， again， what what happened You。

 you have some small integers。 So have some them0，1，1。And you want to make a big integer。

Containing blocks，0，1，1，0，1，1，0，1，1，0，1，1。Yeah。No， you can't make shift and take a bit because I want to do it in constant time。

 so I will just multiply it。Buy the following mask。I will put once in these positions。Hello。

 have this result。这别。Again， what happens when you multiply to integers？

You actually take these positions when you have one。

And shift these elements into this position and take the sum of the tone。I can do it in log W time。

 but I don't want to spend log W time。 I want to do it in constant time。

My plan is to do everything constant time。So， I will precoate this。Special mask。

And now my result will be just x multiplied by M。Again， why multiplication。

 not because what what I need to do。 I need to have this0，1，1 plus。This is 0，1，1， plus 0，1，1。

 plus this is 0，1，1。1 one。So this element will be x。

 This will be x shifted to the left three position。 so itd be x multiplied by 2 power of。Free。

 this will be x multiplied by doing power of。6， this the X multiplied by two power of。嗯ない。

So I just need to save some of all these elements。 So it will be x multiplied by1 plus twin power 3 plus2 power 6 plus twin power fly。

 And this is M。う哼。L， this M is  one in position 0 plus  one position 3 plus1 position 6 plus one position line。

嗯。Again， this just because how multiplication works。

So multiplication in binary is just you take these positions， shift your X。

Into these positions and then take some of all these elements。なってな。嗯。Okay。

 maybe it's a little bit easier to understand this in decimmo。 So in decsimmo， if you want to have。

 if you have digit。If you have some decimal digit 7。And you want to build integer， let's say，7，0，7，0。

7。You need to multiply it。Buy 1，0，1，0，1， and you will get this image。So that's almost also works。

 So if you if you multiply some digit by some integer of zero and one。

 you will just replace these once with these elements。 The same thing happens here。

 So you have these one in these positions。When you multiply this mask by this small integer。

 it will replace each one with this mask。Okay， hope it's good enough， not the final thing。

I need to calculate the sum of all these bits。First of all， I need to remove all other bits。

So I will remove all other be just by ending with this mask。So I would make a mask。

I will make a mask when I have here， I have xs。Here I have one here。 I have zeros and hold it。

So here I here here I have zeros。I will calculate bitwise n through this mask。 Now。

 all the bits except these four are zeros。Now we have this beautiful。Inters here have zeros。

The zeros。Gma zeros。India， now all bits， except these four bits are zeros。Now。

 how to calculate some of these to four bits。The same， same trick is here。I see。 So Ill take this so。

 So let's take this number and let's call it。Okay， let's call it D， so I will just deal and。

So we have this alpha beta gama。Now I will shift it left。By the size of this block。

 So this so better will be here Data and I forgot here。Now， again， I will shift it again。네 또 안 가。

And once again。And now calculate some of all these shifts。When I calculate some of all these shifts。

 and here。I will get some of all these bits。And how to calculate some of all these shifts in constant time。

 using the same trick as here。So this sum is just multiplication by some metrics。 but by by by my。

 by by my， by the same mass actually。So again， this element is just D。

 This is D multiplied by tool in power of B。This is D multiplied by twin in power 2 B。

 This is D multiplied by twin。Freebie and so on。So when it calculates sum of all these elements。

 it' just d multiplied by 1 plus twin power B plus twin power 2 B plus and so on so。Its just M。

 the same M as here。Sure。So again， you take this integer this bit vector vector multiplied by the same mask as here。

And when you multiply it， then in this position。You will get the sum of these bits。Now。

 you just need to remove all other bits。And shifted to the right。And you will get this home。

That's the whole trick。Yes， multiplication is actually overpowerful。That's why actually。

 that's why all this theory is not very practical。 in this theory。

 we actually think that we can multiply elements in constant time。

 but also it also it only works when w is big。So we kindly need to have big integers。

 And at the same time， we need to be able to multiply them in constant time。

 No one knows how to do it。非 long。One more。Okay， let's have one more bi finalal problem。

In the final problem， I want to apply the same trick。To find the highest one beat in in in there。

In在这。嗯。I'll just do the same trick election。嗯， so what we have we have some in。Let's have something。

0，0，0，0，0，1。H zero one。I三1100。Slected。おます。Check having in a。And yプ。

The problem is to find the highest。没てで。Can you send trick to calculate some reason whole work you actually do。

You can calculate some of bits in hardware， but not like this。 The problem is you don't have space。

 I forgot to mention it。 Yeah， I forgot to mention。 Actually， when when you calculate this。

 the this one to calculate， we need to。So in this right position， we。

 we need to have enough spaces to store this sum。 So the size of this block should be at least。Loger。

Of this some O， right。So you need some space between these bits to store the summer yeah。Onng。Yeah。

 so the final problem， final final problem for today will be you have some integer and you want to find the highest bit of this integer。

How to do it。意ing。What we what we will do， We will split the block into block。

 We will split the integer into blocks of size squared of W。No。We will do the following。

 We will make a。嗯。What kind of short version of this integer。 So for each block。

We will check if this block is0 or not。So this block is 0。 This block is not0。 This is not 0。

 This is 0。Get size of this block sc top。那。We will construct this。スまでょ。Now， in this small integer。

 we， we will try to need the highest beat。So we will find this bit。

Now we know the block when where we have the highest bit。

 So we know that the highest bit is in this block。 So this is the leftmost non empty block。

 So this block。Now， we need to find the highest bit inside this block。 So we take this block。So。

 we take a2。嗯。Let's say they do like this。And find the highest bit in this block。表定。

And now we know where the highest speed is again。We construct this cage。 like for each block。

 we make  one bit if it work is empty or not。Now， we have this small integer in this small integer。

 We need to find the highest speed。This highest beat will tell you which block actually contains the highest beat of this inte。

 Now， we take this highest block。This this left most non empty block in this block。

 we apply the same procedure to find the highest bit。

So now we just need to find the highest bit in the small integer。嗯。

The size of both this integer is squared root of double。

So size of this is square root of w and because size of the block is squared of w。

 so we have square root of w blocks。And size of this is square of double。

So now we only need to solve the problem for the small integer。So again。

 how to find the highest bit rule height highest empty block。

 and then inside this block will hide the highest bit。

So both this problem is just to find the highest bit in a small integer。

We will solve it twice and then find the highest speed。

So how to find the highest bit in a small interger？没有意见。Let let's see。 you have some。4 B integer。

So if you have the first bid set。This bit said。呃。Then your interior is actually greater or equal。

 then。This。嗯。I want have less。What problem in this one。Does't matter。I other than this。

YeahSo if you have 1，0。And something。It is greater equal than than one of the0 0。If you have 1，0，0，1。

 something， then it's greater equal than this。E it is 4，0，0，0，1， It is better equal than this。Now。

 to find the highest bit in a small integer， I need to find the number of inequalities which is here。

We have this， have this， for example。You have 0，1，1，0。

So you checked if it is greater or equal on this， not。It is great recommend。 Yes， yes and yes。So if。

 if three inequ is satisfied， then they should be the set。Okay， we just check all this。In equations。

 and the number of satisfying equations will be the number of you bit。Yeah。

 and we just solved this problem。Yeah， no it looks slightly different， but it is the same problem。

 We have some integer and we have a number of in equations。

 So we will put this in equations in a big integer。And sold them in in constant number of operations。

 That's all。And now we just need to solve it twice。 we need to solve it here and here again。

Both operations suggest just to find the highest bid in a small integer。嗯哼。Now。

 if there's only one the day I actually missed。Can you spot the detail actionist。Don't let me I。

 I didn't tell you is how to find this， this sketch action。How to how to。

 how to build this small integer a prime， which contain information about all the blocks。

We can do it like this。 Okay， you can do it like this。 So first， you take your number a。

Then you use the same trick。To build the whole。 So you have number a。Again게 zero지 zero zero로。嗯。Now。

 for each block， you need to check if it is block greater or0 so。

So you need to check if is greater or0 for each block。You can do it using the same thing。

So you construct the following list。Again， you make this， you make this mask subtract and so on。

So here we have 0，1，1，0。That's almost what you need。So you need， you need this small integer。

 You have all these bits。 You have0 here，1 here，1 here and 0 here。And， but the problem is。

 these bits are not together。 So so they are in different points of your。Integer。

 and you want to move them closer。How you do it， You do it using the same trick as before。

So when we try to calculate the sum of these bits， we just multiplied by the matrix。

 So we shift them be positions to the left。And now we just stripped them B -1 position to left。Yeah。

So again， we will ship it to the left。 So this so one goes here。嗯。And then again。

 shifted to the left。 So it is 20，1。It here。And then again。

And then calculateate some of all these elements again。

 it will be some it's just multiplication by the mask。With once a distance B -1。

 So each time we should certain one plus。2 in power B-1 plus 2 in power 2 B-1。말슨 so。

So we' multiplied by this month。And now here you will have this。Here you will have 1，0，01。

Now we can do remove all all other bits， move these bits to the right。 and then you have this。唉。Okay。

 this's all for today。う。🎼，🎼Yeah。🎼う。