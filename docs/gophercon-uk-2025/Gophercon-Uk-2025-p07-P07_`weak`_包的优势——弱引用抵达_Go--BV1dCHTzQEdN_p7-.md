# Gophercon-Uk-2025-p07-P07_`weak`_包的优势——弱引用抵达_Go--BV1dCHTzQEdN_p7-

![](img/54d9358da5fff52157cd8756856e5246_0.png)

Sam Burns， he was here at Gophercon last year talking about cryptography。

 He is a regular at London Gophers meetups。 So I see him almost every month。 And just recently。

 he gave a smaller version of this talk at London Gopherers in May。

 but this is an extended full version。 I'm really excited to see it。 Yeah。

 he's going to tell us about the package in Go。 Please welcome Sam。😊。



![](img/54d9358da5fff52157cd8756856e5246_2.png)

Thank you， Annana。So thank you very much， everybody for coming。

 This looks like a really fantastic event this year。 I was really excited when I saw the schedule。

 I hope you're all having as much fun as we。 And welcome to my talk。

 The strengthth of the week package。 So this is about new feature that was added in Go 1，24。

 and we'll be talking more about recent development from the last 36 hours as we go。😊。



![](img/54d9358da5fff52157cd8756856e5246_4.png)

So。My name is Sam Bens。 I work for G hardless。 I've managed to。

Get past security to stop by essentially being a Ruby developer at this point。Interest。

 software development， architecture， information security。Other than that。

 I enjoy posing for photos on cliffs。There is， no， there isn't。 There will be in about an hour。

 a link to the slides on that blog。 But I forgot to spread out before I came on the stage。 Sorry。

 So if you'd like a copy of the slides， have a look and I'll。

Make sure that they go up go online as soon as possible。So the blog。

 there are some blog posts there about Go。 There's also some stuff about concrete and laptop stands。

Maybe there's anything else so。Maybe it's not for everybody I don't know。😊。

And if you have any questions， you're welcome to come and find me after the talk or there's an X handle there。

 I'm not really very chatty on social media， but'll get your questions if there's anything you'd like to know。

😊，上一。What we're talking about is I'm going to do an overview of the W pointers package。

EGuide to garbage collection and go。 And what happens on Bi Day。

There will be some hastily added slides from yesterday， about Co1，25。

The go team the go team liked to do this last year。

 I was up here talking about cryptography and all the N standards changed two days before the talk。

 so。I think there maybe timing the product roadmap around my public speaking commitments。 but yeah。

 so this this， this is an explanation as to why I've always got bags under my eyes in the videos。

And then we'll do comparison to other languages。A quick look at week references in some other languages。

And we'll go through a couple of examples of where you might want to use the weak pointers F and go。

And very briefly go over some best practices in the end， although。There'll be more of a recap。

 because I'm hoping we'll be able to cover some of that as we go。Sa。Section 1。

 a guide goes near week package。That's my attempt to explain the concept of a Gopher to mid journey。

 not much of a consistent artistic style through the presentation。

 but I'll be sure to let you know the backstory of every Jpe as we go。

 So this is a new feature that was added in Go 1，24。It has special references， which do not。

Excuse me， which do not prevent garbage collection。 So they're non owning pointers。

To an object by object， I mean the thing in memory。

They allow the object to be collected when unreferenced。

 So theyre a way of having a reference to an object that you can keep pass around。

 but it doesn't prevent garbage collection。 That's the core concept。

 And we'll look at why that's good under certain circumstances。 and when you might want to use it。

🤧So。One reason to use weak pointers is to prevent memory bloout in caches。

This can allow you to avoid unnecessary retention of objects。 You can have cache， which is in memory。

 but still subject to garbage collection。 That's going to be one of our examples we go over。

And it enables sort of automatic cleanup in long running programs。So this is。😔，Important for caching。

 there are some other use cases as well。 we're going to talk about observer and visitor patterns and。

Sting andning and canonization maps， if there's time。So conceptual overview。

 weak pointers don't count for the purpose of garbage collection reachability。

If you try to dereference a weak pointer after the thing it points to has been garbage collected。

 it returns nil。So a normal， what I'm calling a strong pointer。

 they're not really called strong pointers， but a pointer that's not a weight pointer。

U as long as the garbage collector can see that you still have that。

 it means the memory can't be freed up。😊，With weak pointers， you can have a pointer。

 but it can still be subject to garbage collection。So。This is just a screen shot from the website。

 but。What we see here is an object。 This doesn't mean object in the sense of object orientation。

 It just means any variable that's in。Memory， essentially， for garbage collection purposes。

 we're gonna call it an object。mightight have a strong pointer to it。

 That's an ordinary reference or a pointer that you can pass around in your go code and weak pointer pointing to it as well。

Now， what then happens if we。Delete the strong pointer。Is。

Strong pointer has gone out of scope or it's been nailed or it's been cleaned up itself or some in some ways。

 Strong pointer has been got rid of。 The weak pointer still exists， and。

Testing my Photoshop skills to their absolute limit。 The gophers change colour slightly。

 What I mean by that is。It might exist。 It might not。

 It depends on whether or not the garbage collector has run。

 that can be sort of non deterministic in its way。 but the weak pointer still exists。

 and you can still try and use it。If the garbage collector were to run when there are weak pointers pointing to an object。

 But there's no strong pointer to it。What happens is。The memory gets freed up。

 This is from Juan dela Cruz Garcia， who's much better at artwork than I am。

 who's come up with this diagram showing a realistic depiction of garbage collection。

 So what happens is。So if we look back at the object initially， there was a strong pointer to it。

 would have protected it from garbage collection。 Week pointer doesn't。 Strong pointer goes away。

 and then garbage collection happens， and it disappears。🤧。Okay， so。How weak points is working go。

 There's a new package， the weak package that was added in Go 1，24， and subsequent。Using generics。

 the pointer type is a pointer to in anything， essentially。You can make。

Week pointer using week dot make， which is part of the quite small public API of the package。

 But the important thing about it is it's it's receiving a strong pointer。

 So this is some object memory here。 There's a reference to it， and。

We're using the strong pointer to make a weak pointer。

So this is how the weak pointss has been constructed。

 It can be the underlying object can be any type， basically using generics。

And what you end up with is a weak pointer which can still be used to retrieve the original valley。

But its sort of provides a layer of indirect， which means that the garbage collector kind of can't see what it's。

 that it's there， essentially。Now， if we look at a practical example。

We've got a weak pointer here being made from strong pointer。

 They're not really called strong pointers。 But you know what， I mean， online 12 there。

For the sake of argument， we're going to assume that this pointer is pointing to something that's in the heap and not one of the stacks we'll go over in a little bit more detail what that means and why it's important。

 but for the sake of argument our pointer is something which is，Vulnerable to garbage collection。

We can overwrite the pointer online。 So， first of all， the other part of the。

 of the public API of the week package is value。Some of the very early documentation suggested it might end up being called resolvesve or something like that。

 but its value and value is。Get well， get to see the value back as it sounds。 or a pointer to it。

 So you've got a strong pointer now， as you can see， online 16。What we've also done there。

 And this is going to be a。An important thing to remember when you're using weak point is you don't know if it's gonna return nil or if it's gonna return a reference。

 So this line 15， this is quite a commonly recurring pattern that you'll see wherever weak pointers are used。

 so。What we've done is。Got the value and then done a nll check before attempting to dereence it。

And then。Online 19 were deliberately getting rid of the what is taken to be the last remaining reference。

To pointer。 So again， this is sort of go eque pseudo codes。More illustrative than it is perfect。

 I'm not sure that actually comps。 But what， what， what we're doing is getting rid of the strong reference and then running garbage collection。

You don't usually need to trigger the garbage collector manually。

 We're doing it for the sake of argument here。 There's also。

More to be said on the subject because of concurrency， I'm gonna go over in more detail。

How the garbage collector works and what parts。Stop the execution of your code。 What parts allow it。

 Some of it concurrent。 We're kind of assuming that somewhere between line 20 and line 22。

 in the example， garbage collection is finished before anything else happens。

 not necessarily the case， but for simples to。We're forcing the garbage collection。

And then we try and call value on our weak pointer again。Online 22。

 And what happens is we get nil this time。 So it says so it prints after GC value is collected。

 and what that means is。We've been able to get the original value back from the W pointer。

 garbageb collectors run。And then we check again， and it's now inaccessible。Excuse me。🤧。I be it on。

 so。So we made a couple of little assumptions about the。

Where we got this pointer from and where it stored a memory and so on and assume that there aren't any other references to it。

 for example， and。The the。Garbage collector is going to finish before the next line runs。

 but this is a simple example showing how you can use weak pointers。So。

How weak point is working though？The autoil behavior means the weak pointer returns nil when the object collected。

 there's no risk of dangling pointers。 you always need to to check the value before you use it。So。

Another thing to remember is。This has caused some confusion in the past。

 because if you look at a thing like this at some point。We get on line 22 here。 We get a value。

 No not line 22。 So on line 15， we get a value， which is essentially a strong pointer。

The fact that you've now got that strong pointer is visible to the garbage collector。

 So when it's trying to work out if this value can be garbage collected。

 it now knows that it can't because the strong pointer exists。

 So the fact that this v variable exists on line 16。

Is preventing the garbage collector from removing it。 So it's not possible， for example。

 to do the nil check and then have the garbage collector run。And then you've still got the reference。

 but it doesn't work anymore。 So it's the fact that we've called week pointer dot value or weak dot value。

Means that the。The strong pointer exists。 The garbage collector can see that。

 and that kind of immuns you from the sort of race conditions that some people have。

Raise questions about while it was being built。🤧。Okay， so we've covered the autoil behavior。No。

What happens on bin day， I go to， I go to go to garbage collection。

With a little gopher who looks like a raccoon going through the garbage。

So we're gonna go in a little bit more detail over how。How the go garbage collector works。

 And then there'll be some slides telling you， ignore all previous instructions and telling you how it now works。

 But basically， Go garbage collector uses。 it's a tracing garbage collector。

 So it uses a mark and sweep approach。え。Strong references keep objects alive from garbage collection。

If there aren't any strong references。That means that an item in memory is eligible for garbage collection。

嗯。To explain what that means in a bit more detail。The way that the memory allocation works。

So there's a heap， and each go routine has a stack。The he。

I've oversimplified things a bit by saying it's got global variables in it。

 that's not strictly speaking the whole story。But a stack is。Kind of local to a go routine。

 So an individual go routine will have its own stack when it enters a new function。

 when your go routine starts executing a function， it'll have a stack frame of local variables for this function。

 which get kept on its stack。 When your go routine finishes that stack's not needed anymore and is automatically ditched。

 Meanwhile， the heap。Contains。Anything where the life of the variable is a little more complicated。

It's possible for an item in the stack to essentially point to something that's in the heap。

 So you might have。🤧You might have something that's。Local variable。

 but it's got access to something that's in the heat。

 And that's going to be important for the garbage collector to know about。Excuse me。no。This。What。

 what the， what the compiler has to do when you're trying to create a new variable is work out whether it wants to put it。

In a stacker heap， there's。There's a couple of things it could look out for。

 It's called escape analysis。 And what it's doing is analyzing the code and trying to find out。

If variable local scope within a function is somehow escaping that function。

 there's a couple of ways this could happen。え。One obvious one is being used as a return variable。

Another is go channels， which facilitate communication between go routines， obviously。An item that's。

Or a variable that's in a。That's in a local function that's being run by one go routine。

 but is going to be written to a channel or might be written to a channel conditionally。

The compiler is expected to see that and make sure that it goes in the heap because it life expectancy is more complicated than just。

Kill it as soon as the sc routine is finished。嗯。Another time when this might happen is a function can write directly to a global variable。

 You might， for example。Have a global or package level variable， which is a pointer。

To some kind ofstruct or whatever。And then you。Within the scope of a local function。

Get the data that you want in your variable， save pointer to a global V package level var。

 Once that go routine is finished， you kind of expect the pointer to still work。

 And so the compiler has to do this escape analysis and identify， okay。

 this variable is escaping local scope。 We can't just store it in the stack for that go routine has to go in the heap。

So that's， I've said the heap is for global variables。 Its a little bit of an oversimplification。

 But that's kind of how it works。没有。Try color， Mark and sweet， so。This affects only the heap。

 not the go routine stacks。 Obs are variables， my bi struck or backing ready for a slice。

 that kind of thing。Root nodes are。Anything in the heap where we know that， we know that。

There's a stack variable somewhere that's pointing to it。 or there's some other reason why it's。

Known that we can't clean that up。 So we've got this root variable here。 little star。 That might be。

呃， any pace。Any data structure where a go routine stack has a reference to it。

And we're doing tricol marking。 So when things get marked in black。

 that means this is definitely still needed。 Use land code can still reach this。

 garbage collector should refrain from messing around with it。Yeah。When something is marked in white。

 that means as yet， we haven't found any evidence that it should be allowed to live。

Or it shouldn't be garbage collected。 And grey is。 So it's a tricol marking sea。

 The significance of the grey， as it means。This variable here is definitely being used。

 but it hasn't been scanned yet to find out if it has any children。

 meaning references to other things it might be astruct with multiple properties。

 which need to be looked at independently。 It might be。Could be in a array。

 So it could have basically other other。Poins of its own to other items that are in the heap。

 So what we're going to do is essentially a paralleled graph flood。On directed graph to work out。

In the end state。Which are the items which are in some way related to a thing that we can't get rid of。

う。And which are still white at the end， meaning we haven't encountered any reason not to garbage collect them。

So once again， we're just scanning through the heap， not the stack， I a simple graph flood。

 starting with root nodes， which are。Anything that's in the heap that you know is currently pointed to by one of the go routine stacks？

And we're traversing this directed graph， looking for。呃。Any children still need to be scanned。

 if there are children that need to be scanned， might be it'll be black。

I sorry it'll go gray if we're definitely using this variable and no further scanning is needed。

The object in the heap will be marked as black and anything white at the end。

 we can just scare it off。So。🤧Excuse me。 I beg get pun。

If we take a look at what this means in terms of concurrency。

 this is something that happens very differently in different programming languages， but。In go。

Much of the garbage collection is done concurrently。 Seping， for example。

 can happen while your code is running。 So if we've already done all of the marking phase and got all the way here and identified that there are some items in the heap that are no longer reachable from Newland code。

There's no reason why that cleanup can happened， why userL code is running。

 there's no race conditions possible because you haven't got access to those variables anymore。😊。

The sweeping of unused memory， essentially delocating the memory。Can be done concurrently。

There is a brief stop the world identifying root objects at the start。

Benchmarks will vary depending on what you're doing。 Sometimes it's about 100 millisecond。 Sorry。

100 microconds a big one。Doesn't really increase that much with the amount of memory allocated。

 If you have a lot of go routines， it might take a little longer to go through multiple stacks。

 but in general， it's a mercifully brief stop the world。The other aspect of the concurrence is。

 while the marking is in progress。If your code is running at the same time。

That has an effect on what color things need to be in the graph。

 So if you were to create a new variable in the heap while the marking is happening。

It kind of needs to be marked on creation。 So there's this concept of right blocking where there is a little bit of a performance impact if you're trying to allocate new memory while the mark phases in progress。

And there is another brief stop the world at the end。

 which involves doing essentially tidying things up a bit。 But overall。

 compared to some other languages， the。Mark and sweetet garbage collection。

 and the way that the concurr is handled is quite high performance。

 I'd say the garbage collector seems to basically run faster and。It does in some other languages。

 earlier versions of go。 I think it was stopping the world for more of the process than it needed to。

 But in the modern era， it's a pretty high performance garbage collector。🤧。So， to recap。

The way things work in the default garbage collector。Trycol， mark and sweet。

 garbage collection on the heap。Stops the world when necessary， But in general。

 a lot of this stuff is happening concurrently。It's what's called non compacting， so。

🤧What that means is， if you imagine。All of the memory that's been allocated to your program as a kind of linear block of memory。

 If you've gone through the heap and unallocated bits of it。

 that means your allocated memory now got holes in it。 There are some programming languages。

 including some Javascript engines that do what they term compacting。

 which means moving everything around。 It's a bit like kind of def fragmentmenting the memory and making sure that all the free spaces in one bit。

Go is not doing that。 One of the reasons is that requires a lot of moving stuff around in memory。

 which is kind of slow。Another reason is， if you imagine。

ca it's a language where you use as direct access to pointers。

 If you've got a pointer to an object and the object gets moved in memory。

 then the pointer would need to be changed as well。 Be a little bit of a mess。

 But what Go is doing is it's quite good at。Keeping track of where the de allocated memory is。

 So if you were to say， okay， now I need an in 64， then I'll go， okay， well。

 it happens to be 64 B of 64 B of space there。 You can have that bit。 So it's pretty good at。

We're using memory that's been freed up， but it's not doing post garbage collection compacting。

It's also non generational garbage collectors。In some languages， like。PHP， and I think Java。

They have this concept of a generational garbage collector。 So what's happening is。

A variable which has existed for a long time and survived multiple rounds of garbage collection doesn't get checked every time anymore。

 whereas a variable which is quite new， will definitely be checked regularly by the garbage collector。

 That's what generational garbage collection means。 And some languages like P B has this feature。

 But the goes garbage collectors and nongenal one。It's configurable as well。

That doesn't just mean using weak pointers as' other things you can do。

 There's this environment variable here called Go G C， which defaults to 100。

And that means 100% of memory allocated already。 So it's about deciding。

 at what point do we need to run the garbage collector again。

 And it's based on how much bigger the memory how much more memory is being used now than last time it ran defaults to 100%。

 but you can change that。If you're interested in that， there's。

 I think Uber I written some articles about。嗯。I think they're profiling their services and configuring garbage collectors settings based on。

The nature of the service and how it's using memory。

Cloudflare had a couple of cryptography or hashing based problems where they found that just kind of switching the garbage collection off entirely in some cases。

Gives a significant performance improvement without。

Significantly increasing the peak memory footprint。Again。

 it very much depends on what your code is doing。 Probably shouldn't do that most of the time， but。

If you've got an application where you're creating a very large object graph of lots of things which are interrelated。

 all of which you're still using。 and sometimes under some circumstances。

 pausing garbage collection can make it run faster without。Causing additional memory usage。🤧。🤧。

And obviously， in addition to these various features of Go's garbage Collector。

 there are obviously languages which don't do garbage collection， C， C+ plus， for example。

 all in the memory managements done manually。That can。

Lead to slight performance improvements over using a garbage collector。 It also can cause bugs。

 There was a survey not long ago of cryptography libraries that suggested that， I think。

25% of common vulnerabilities and exposures in crypto libraries。

That are written in languages with manual memory management or things like buffer overflows and other other memory management Is。

 So by using go and having a garbage collector， kind of avoiding this failure mode。ふ。

So that's how the garbage collector works。And in breaking news。

The go team are very kindly Phil built Go 1，25 for， which is fantastic upgrade。 in a number of ways。

 one of which is there's an optional alternative garbage collector。😊。

So this is an environment variable that you can set。

To let you use an experimental opt in garbage collector or green tea。Green tea is。As far as we know。

 it basically， if your code works with the old garbage collector。

 it will work fine with a new garbage collector。 There will be some performance improvements。

 It's opt in。 It's an experiment。 If you're using Go 1，25 and production now。Well done。

 But if you want to use a new garbage collector。And you would need at build time to have this environment variable set。

And that'll let you use green tea now。As it only came out 36 hours ago。

 I've had a little bit of time to find out about it。

 But I have spent most of that time animating a go for instead。い。Now。So。😊，This is。

 this is a link to the original issue in Go， which was opened earlier this year to talk about the green tea algorithm and how we're gonna add it as an experimental opt in。

Garbage collector as a drop in replacement for the existing one。

It changes the way marking works for small objects。 so previously。🤧In the old garbage collector。

The way marking was working was we were looking at every route node。Excuse me。

 I beg you on previously we were looking at every root note and doing a simple graph flood。😊。

What's happening now。Is。If you've got lots of small objects in memory。うう。

They're grouped together into。A memory span which is kind of， to some extent。

 treated as if it were a single item in the heap graph。生日。

And it's based on physical locality in the memory itself。

 So physically proximate memory addresses have we group together into the memory span。

The garbage collect marking has this concept of that span being。

Gray in the sense that it needs further investigation， part of it's still being used。And。

That speeds up the marking phase of garbage collection。

 It's at its best in applications where garbage collection heavy。

 So that if there's a big turnover of memory usage。There's lots of small items in memory。

Then that's when you're going get the most benefit from switching garbage collectors。

 You could try it and do your own profiling if you wanted to。

 There has been some profiling done already。🤧。And what they found is a 10 to 40% reduction in。

CPU cost of garbage collection during the marking phase for high GC intensive applications。Now。

 an important thing to say about these benchmarks。IAs far as I've been able to tell。

When I wasn't busy animating my gopher， it looks from the dock as if much of the benchmarking was done on Intel hardware。

😊，嗯。I've read a little bit about this。 didnn't understand any of it。

 I've gone off and found some clever people in the deepest， darkest depths of a Google data center。

And drag them outblery eye into the light to ask and all this means。From what I gather。

 we haven't got a lot of information in the public domain about profiling the new green tea garbage collector on AMD hardware yet。

 but。AD epic processors， particularly the Rome and Milan generation。嗯。

Sort of extreme examples within commercial hardware of places where there are a lot of CPU core。

 but the memory bandwidth per core is lower than it is on In hardware。

 So what that means is basically。It looks like we get a 10 40% performance boost， depending on。

The way your application behaves， how much memory it's using the turnover。

 it looks like we get a 10 to 40% boost on Intel hardware， it's probably higher on AMD。

 but we don't know because I was making Gophers instead of benchmarking it。😊，So。

So what this is about is essentially。grouping。Collection of objects in memory together into a local span。

 which are physically proximate within the realm that allows them to be read out together where overcoming problems around memory bandwidth and memory latency and multi core processes。

 ultimately， CPU clocks， outpacing DRAM clocks is。Exacerbating a situation where the old graph flooding algorithm wasn't the fastest way of working out what stuff can be collected and what can't。

As I say， it's a new experimental garbage collector。 You're probably not using it。

 if you would like to。This is the environment variable you can set to use the green tea garbage collector at build time。

😊，It seems to be a drop in replacement， the Go core dev team are not aware of any examples of UseL code where it doesn't work if you swap garbage collectors should be okay。

And try turning the experiment on and see if it leads to performance improvement in your application。

No。Understanding reachability to relate this back to where how。

This garbage collection process affects weak pointers， strong references， keep the object alive。

 weak references of weak pointers are essentially invisible to the garbage collector so it provides a layer of indirection so the garbage collector looks at the weak pointer and it can't see the strong pointer inside it。

嗯。When the garbage collector is delocating something。

 it tells the weak pointer that that needs to be known now。嗯。

So it's as if we've created a kind of indirect reference that allows us to access something when it might be garbage collected。

Now， to look at preventing early garbage collection can be done。

 the runtime package has this keep alive， for example。

 which you can use to keep a value indefinitely if you don't want it to be garbage collected。嗯。It's。

Only really needed， cause there was some。There were some legacy approaches to how file handles worked that meant that keep alive was perhaps more useful once and it was now。

 has some fringe uses involving Sego。 and what happens if you pass a pointer from go to C and then the garbage collector can't see it anymore。

 but the sea code can。 you might come across this issue if you're。Integrating kudo with Go。

 But that's another talk。And another thing just worth mentioning as well。

 If you find yourself using weak pointers and run time dot keep alive， it might just be worth。

Considering the question of whether weight pointers are definitely the best fit for your application。

So in terms of other languages， there are a couple of other languages that have got a weak reference feature。

One of the major。Arguments that was put forward both for and against adding weak pointers to go was that it would make it more like Java。

 So Java's got。Java's got this concept of a weak reference。 It's an object oriented language。

 user doesn't normally have access to the pointers， but it's got references。

 and you can get a weight reference using。Java dot laang dot ref dot week reference。

 There's a method get on that class。Which can return object which can return on reference or null。

And has the same underlying principle of non ownership。Similarly， in Su sharpp。

 there's weak references feature as well。This is called system dot week reference with a generic type。

 And the relevant method in C sharp is called try get target。 The principles are same。

 It's just a non own reference that can return。 I't think it's called Nil。 It's called null。

 but same thing。The， it's a non own reference system that may become nu when garbage collection runs。

So we've got time， I think， I'm not gonna get beed offage yet。 We've got time to look for。

Look at some example code of weak points as being used and go the first use case a lights to go over as caching。

So。This is one of the more obvious uses for。The weak pointers featuring go， basically。

 the concept is， it lets you have a cache， but。The fact of something being in the cache doesn't stop it from being garbage collected。

 So let's say having in memory cache。 but without having to manuallyic things to save memory。

So cache entries shouldn't prevent object collection， basically。

Weak pointers let the garbage collector reclaim。Cash items， which are otherwise unused。

 even if the thing is in the cache。And as always， with weak pointers， we need to do a n check， so。

Here's some more clip art that I cutt gophers that I've cut and pasted。

 If we imagine we've got a cache。 It's new memory date structure。 It's a map。

We're using string keys called things like Key1 and key2。And each of these maps to a weak point， Sir。

Which is pointing to an object。It's possible for there to be a normal cache hit。

 So if you say to your cache， have you got key1 and say yes and give you a gopher。If you say to。

 if you got key2， you can say yes and give you a gopher。say， have you got key 42， can say， no。

 I haven't got that key。 There's another case as well， where。You ask for something like key3。

E the cache key exists， but the weight pointer is returning n。

 So our caching logic is going to be a little bit more complicated， but basically。

 it's there to handle the case where。The cache key is in the cache。

 but the underlying value is already being cleaned up。So in our example， we're creating a map。

Possibly don't do it like this for simplicity， this。This is not using sync dot map。

 It's not threadsa， but there are things that you could do to make this a little bit more production ready。

 But for in our example， we're just gonna use a normal map。

We're going to insert some data at a particular cache key。And then。

The way we do that is we take a reference to the data to a strong pointer。

Use the weak tot make from the public API of the week package to make a weak pointer and then cash the weak pointer and。

If we try and look something up from the cache。Online 15， for example。

We have been able to find the Kashki that's been requested。And we have been able to。Dear reference。

 the weight pointer。 and we've now got a strong pointer。 So we're able to return the value。

If the garbage collector were to run。And。The object that's being referred to is not being used anywhere else。

It'll get garbage collected。 And that creates a case where the Kaki exists。嗯。

But when you try and do a reference pointer， it gets nil。 So， first of all。

 it needs to treat that as if it are a cache miss。 And secondly。

 we probably don't need that key in the cache anymore。 so it can clean that up as well。

So if you ask the weak point of cash。For something it has God， itll give it to you。

 something has never heard of， it'll say no。If there's a weak pointer in there。

 but the thing it's pointing to is been cleaned up。

 it'll handle that by treating it as if it or a cashm externally and by cleaning up the old key。

So the benefits of a weak cash， this means。The cache itself is not interfering with garbage collection。

It's memory efficient caching without manual cash eviction。

 you don't need to actively remove things from the cache。

Is sufficient to let the garbage collector do its thing。 It can clean an object out of the heap。

 And then the cash will treat it as if it doesn't exist anymore。

 So we've been able to achieve having a cash without。Having to worry about memory bloat。In some ways。

 that simplifies our codeca we don't have to do a manual cache eviction anymore。

But it does mean that we had to do the set check to see if the weak pointer still works。

And handle it differently， if it doesn't。So that's an example of how you might use the weak pointers and caching。

 It looks like we've got time for another example quickly。 Yes， thank you， Anna。

Another thing that we might use weak pointers for is an observer pattern。 So if you imagine。

We want to have an object which can act as an observer to another object。

But we don't want that observer relationship to。Prevent the subject from being subject to garbage collection。

 We could use weak pointers as a way of creating a link between an observer and a subject。

Without the observer preventing garbage collection， so。This is。

If we're adding an observer pattern some code that already exists。

 we're not trying to significantly increase the memory footprint of the code。

 We're not trying to artificially lengthen the life of anything in the heap， but we just want。

To be able to have this observer， whilst at the same time。呃。Making sure that their subjects。

 memory lifepans not affected by the observer。 Then we might approach it like this。

So what we're doing here is we're creating a subject。 and call it topic K。嗯。And an observer。

Called I1。Which is then being added as a subscriber to messages。

 So this is an important part of the kind of event driven an architecture Our observer is now able to subscribe。

 mark itself as an observer of a given subject。We've registered the observer with the subject and attached。

Here， we just attach a finalizer on 9，76。 All this is really doing is it's just allowing us to print a message so that we can see。

When the object getting destructed。So the set finalize is allowing us to trigger some code that just gives us a little bit of debugging information when the subjectss being removed from memory。

We can call。Subject dot notify。With first p over here on my 91。

And then have the observer try to interact with the subject and might be kind of acting like a visitor pattern might be trying to change it。

 might simply be asking it for more data or whatever。 It is that it's supposed to do in this event。

So it's trying to touch a subject。 And we'll see how that goes。 Now， again。

 we are assuming for the sake of argument。That the memory that the subject is in the heap are not in a local go routine stack。

 It is the reason why it's a little complicated， but it is。

So when we drop the only strong point to the subject on 9，85， in principle。

 it's now garbage collectible。Now able to be collected by the garbage collector。是嗯。

We then force garbage collection to happen with runtime Do G。Again。

There are some hidden assumptions here。 We assume that there aren't any other references to the subject and the heatap。

We assume garbage collection garbage collection is completed by the time。The next line of code runs。

 it generally is， but it's possible for that to behave a little non deterministically。

 depending on how much other stuff the。Garbage collector has to do。

And then if we try and call try Touch subject again。

We're likely to see that the observer now can no longer reach the subject。

So if we look at our example code and see。What specifically the observer is doing， First of all。

 when we create a new observer online。56， we can see。

Is using the weak pointers feature to maintain a weak pointer to the subject。

 So the observer can still exist， but。If one of its subjects is no longer there。

The weak pointer will return Neil。 So what we see online 63 and subsequent when we do try and touch subject。

Is sometimes the subject still alive because the underlying memory objects still in use。

And we're able to interact with it， we can。😊，Get data such as this name field over here。

 whatever that may be。Otherwise， if there's a weak pointer。Which is。

 which is resolving to null when we try and call the W to Valley function。

Then the observer is printing out a message saying that it can't see the subject anymore。

 So if we look at what we were doing originally。creatingre a subject observer， linking them together。

 making sure that the subject prints something when it dies。

We're doing a notification to test the kind of event driven architecture of our observer pattern。

We're wiping the subject from our memories as if it as if it never existed and then getting the observer to try to touch the subject。

 And when we do that。receives the first ping， the subjects to life。

 Then the finalizer runs and lets us know that garbage collection has has happened。

 And then the next time the observer attempts to do the collection。

It can't reach it anymore because it's gone。 So what we've seen here。

 if we look at this piece of code is。The observers tried to contact the subject。

 It's got a weak pointer。 It's tried to dereference a weak pointer， find out what it's pointing to。

 hasnn't been able to。 And it said the subject's gone because of garbage collection。So by doing this。

 we've been able to have。An observer pattern without the observer affecting the memory life cycle of the subject。

Okay， so those are two main examples of things we're gonna do with weak pointers。 a quick recap。

 And then we can all have a coffee break。So a couple of best practices on using the weight package。

First of all， checking for Nil always verify weak point dot value before use。

 It's a very common pattern。 Every time you see a weak pointer being used。

 there'll be a if statement to see if it's nil or not。

 The runtime dot G C is a useful thing to use when you're testing the behavior of。

Your object life cycles and making sure that you're。

Making sure that the garbage collective runs when you want it to。And in general。

 think about when garbage collection might happen。If you're using weak pointers for a weak cash。

 you might find， for example， that。Changing the frequency of garbage collection will obviously change how useful your cache is as a cache you can turn it down I mentioned this the goGC environment variable。

 which is the one that lets you。Change how frequently the。

 I say how frequently the garbage collector runss is。

 how much more memory gets allocated before it triggers garbage collector running again。

 So you can think about tweaking that。 look at the performance of your weak cash in terms of how many cash hits misses there are and the memory footprint of your application。

 You can dial in the level of garbage collection， if you want to。

And a couple of other best practices to mention before we wrap up concurrency considerations。

 The weak pointers themselves are thread safe。 So it's perfectly fine for you to。

Use an inconcurrent code。 We talked a little bit earlier about how。They。

 when you doreence a weak pointer， when you get the value from it。

 the fact you've got a strong pointer， the garbage collector can see that。

 So it's now not gonna collect the item as as long as you're still using it。

We touched on earlier this idea of having a cache， which is a large map。

There's a package called sync with。Feature called syncnc dot map， which you can use。

 which would have made such examples safe for concurrent use。 It turns out that the regular map。

Structuring go。If you try to write to and read from it at the same time。

 from two different go routines， it can cause a panic， so。

Although the weak pointers themselves are threads safe。

Have a think about the broader data structure that you're using them in。And beyond that。

I guess never， ever， ever use weak points without doing the nail check。So。Overall， we're about done。

 So we've talked about。Weak pointers， examples of use， observer patterns， for example。

 which don't block the cleanup of the subjects。We talked about caching large computer data。

 and there are other features as well canon equalization maps in turning stuff。

 I haven really got time to go through。 But there's a unique package which was added to。 I think01。

23 was it， which has some crossover with string and turning。So other than that。

 that is everything you need to know about the weak pointers in go。Thank you very much for coming on。



![](img/54d9358da5fff52157cd8756856e5246_6.png)