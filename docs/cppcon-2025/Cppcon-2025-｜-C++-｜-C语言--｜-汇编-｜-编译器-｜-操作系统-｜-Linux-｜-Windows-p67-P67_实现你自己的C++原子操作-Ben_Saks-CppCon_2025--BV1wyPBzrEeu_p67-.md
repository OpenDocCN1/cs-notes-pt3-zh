# Cppcon-2025-｜-C++-｜-C语言--｜-汇编-｜-编译器-｜-操作系统-｜-Linux-｜-Windows-p67-P67_实现你自己的C++原子操作-Ben_Saks-CppCon_2025--BV1wyPBzrEeu_p67-

🎼If you've never been to CPPCon before from year one。

 this conference has been designed to be a festival for C++， other groups。

 they go to their keynototees， they dis disperse these people all day long or buzzing。

 talking to each other or learning from each other and it's that vibe and that community that's really good。



![](img/34086f0e254b5ff60abd97075f4e2ee0_1.png)

All right， welcome， everyone。 I'm Ben Sachs。 My company， Sx Associates。

 offers training in CNC Plus plus for companies all over the world。 I've got plenty to get to today。

 So let's go ahead and dive in。 Hope you guys have all been enjoying the conference so far。

 And I hope I can live up to your expectations。😊。

![](img/34086f0e254b5ff60abd97075f4e2ee0_3.png)

Okay， I usually like to start by setting down some terms to make sure that we're all talking about the same thing here。

 where say you know what I'm talking about， so the way I use the term concurrency。😡。

Is for any program that appears to be doing two or more things simultaneously。

 So common way to do that is with multi threading。But I don't yes necessarily。

Need the ability to execute multiple instructions at exactly the same time in order to be concurrent。

 I refer to that ability as hardware concurrency。 I'm borrowing these terms from Anthony Williams book。

So a system can be concurrent if it's not hardware concurrent， then。Behind the scenes。

 there's task switching going on so that。The multiple things more or less appear to be happening at the same time。

 but in reality， they're just switching back and forth very quickly。When you have multiple threads。

 regardless what kind of concurrent programming you're doing。

 you typically need some way to communicate between those threads and the atomic objects and operations that I'll be talking about today。

 are one way of doing that， but there are other tools like muttexes， semaphores， condition variables。

 all of which can be used instead， atomics are in particular designed for more fine grainined control。

UTexas and Semaphos are more for coarse grained applications in general。Now。

 the atomic header from the standard is supposed to be available as of C++ 23。

To pretty much everyone， it's labeled as part of freestanding implementations。

 And so that's what your tool chain is ideally supposed to provide for you。 But unfortunately。

 not all of us have access to a Z plus plus 23 tool chain at all。

 and not all of the ones that are available out there necessarily implement every aspect of the standard in that regard。

 And so I happened to be working with the Arduinoomega 25，60。

 I was trying to implement a queue using atomic objects。Pretty similar to the one that Charles Frosh。

 sorry if I mispronounce your name。 but Charles Frosh presented here a couple of years ago。

And I found that at least when I was using Arduino IDE 2。3。6？I didn't have an atomic header。

 so I had to go ahead and implement my own version of the statomic template。

So I'm going to talk to you about how I did that here。

 but first I'm going to make sure that we're all on the same page about what it means for something to be atomic。

 what properties my atomic type needed to have。😡，And in particular。

 there are two that I think people are often referring to when they say that something that an operation is atomic。

They might be referring to the fact that the anop is non preempttable。

 that it can't be interrupted in the middle by another thread or。Another context。

They might also be referring to the fact that the operation is synchronizable。 The notion that。

There is some way for the results of the operation to become visible to other threads of execution in my application in some nice predictable way。

😡，And so for the purposes of this discussion， when I say something is an atomic object。

 I really mean that it supports operations that have these two properties as a certain minimal set of those operations。

So I'm going to talk a little bit about how the Q works so that we can see what would go wrong if we don't have these properties。

 and then I'm going to go into how we can actually get those properties for our atomic objects。😡。

All right， so this particular queue design， it uses a it's designed for single producer。

 single consumer applications。😡，In my case， I was using a queue of 32 bit integers， but。

You can use it for a cu of anything。嗯。This design uses。

 The elements are stored in a fixed sized array， and the elements are used in a circular fashion， so。

This is often called a circular buffer， or the name I use was ring buffer because that's what I'm familiar with。

So the ring buffer type contains that array and it also contains these two index indices head。

 which is the location， the index of the first element， the element at the front of the queue。😡。

And the tail index， which is the index where the next element will be inserted at the back。

 So when the container starts out， if it's empty。😡，It looks something like this。

 Both head and tail are referring to location 0。And then I have a pushback function。

 or a try pushback function on the ring buffer that tries to append an element to the end of the queue。

Which if the queue is not full， it should succeed， and it will go ahead and write a new element to the tail location。

 and then。Move the tail index forward so we'd get a picture that looks something like this。

And after I go ahead and insert a few more elements， my cu might look something like that。

Once I've got some elements in the queue， I can go ahead and call the TriP function。

 which is going to attempt to read and remove the first element from the front of the queue。

Assuming that the queue isn't empty。It should go ahead and。

Advance the head index and then give back the element that had been at the front of the queue。

Most of the time when we advance an index like this。It's just a simple increment。 but as I said。

 the elements are used in a circular fashion。 So if that increment would place the index out of bounds。

 it's going to wrap around to the zeroth element of the Q。

 So if I keep adding elements to the to the Q from this point。

 I'll eventually wind up with a picture that looks something like this where the tail element。

Is is back to0， and head is somewhere after that。Now。

 it turns out what we will need is that head and tail will need to be atomic objects for this to work。

 Now， I wanted my， to be able to test my atomic class template that I was going to write with different underlying types。

 a type that I knew would be。was relatively easy to make atomic on my target platform， the Arduino。

 and one that would take a little bit more work。So I went ahead and I wrote my ring buffer in terms of this index type type alias。

Here I'm showing it as a UN N 80， but。It could just as easily be a UN 16 T。

And I've tested this code with both versions， so my ring buffer is going to be a class template that takes some number of elements expressed as one of these index types。

😡，And again， it stores behind the scenes。An array of the elements。

That are actually going to hold these values。As well as the two indexes here， head and tail。

 I would have liked to use a stood array for this rather than using a building array type。

 but as it happens， just like this platform doesn't provide an atomic header。

 it also wasn't providing me with an array header。 So I went to ahead and used a built in array instead。

As we'll see this version that I'm showing you right here wouldn't quite work really I'm going to eventually need to turn head and tail into objects using my atomic template that I'm going to be showing you how to write。

😡，But for right now， we're going to try and get by without that template。

And I'll show you what happens， what kinds of things go wrong if we don't have that。

The size constant here is adjusting for the fact that with this particular design。

 the ring buffer never has every single one of its elements being used。

 There's always one unused element in the array because。😡。

Head equal equal to tail is the empty condition。If you tried to insert elements until every single element was used。

 the tail would wrap around back to the head and it would look empty again。In this case。

 because I was working with 32bit indexes。Or sorry， not 32bit indexes。

 32 bit integers as my elements。😡，I was able to stick with a simple array for something like this。

If I wanted to adapt this cue to more complex objects with more sophisticated constructors and deors。

 I would need to do a little bit of additional work to get that work here。

 but that wasn't the element of the cu of the design that I really wanted to focus on here。

 so I stuck with things that were trivially constructible and trivially destructible for this talk。😡。

The class interface， I've already gone through some aspects of it。

 but you go it has a value type type alias that in this case I set to unsign long， but again。

 it could be other types。With relatively minimal adaptation。

 it's got a default constructor that sets the ring buffer up as initially empty。

The empty function just returns true or false， like a standard STL container。

 and then we've got the tripop function， which attempts to remove and give back the first element on the queue。

And it will return back false if the queue is empty。

And we've also got the try pushback function that is going to take in an element and try to insert that onto the queue。

 and if it turns out that there isn't room because the queue is currently full。

 then it'll give up and return false。Now I've kept the interface here fairly simple。Partly because。

 again， what I really want to talk about is implementing the atomic indexes here。

I've omitted a bunch of qualifiers that I could have used to make this interface probably better。

 more effective， faster， safer， like contexts per no discard。

 no except in this case because I didn't want to clutter the slides with details that weren't the things that I wanted you guys to be focusing on in reality。

 if you go and look at the real code that I'm using， it has these qualifiers in it。😡。

I just didn't want to clear things up too much。So I'm not suggesting that you don't use these things just。

I was trying to make life easier for the people who are going to be， well。

 for you guys in the audience。All right， so that is that let's go ahead and take a look at the properties of some of these atomic operations and see how things go wrong when。

 well， we don't actually have atomic indexes for these。All right。

 so here is what you might write as a kind of first attempt at implementing the trip pop function。

 It checks to see whether the。The Q is empty， and if it is。

 it goes ahead and reads out the element into the output parameter V。😡。

And then it goes ahead and moves the head index forward and returns true。

Or if the queue happened to be empty already， it just goes ahead and returns false。

But this section of the code for actually advancing the head index is not going to work properly。

 It has a few problems with it， actually。The first of which being that。If I'm using an index。

 that is。Something that is of a type that takes more than one。Processor cycle to write。Then。

This increment， for example， could be preempted in the middle。And that's a problem because。

Over here in try pushback。This function also reads the head index。

In order to figure out whether or not the queue is full。So。

This is being called from a different thread， Try pushback is always called from the producer thread。

Whereas TriPop is always going to be called from the consumer thread。And so if the consumer thread。

Happens to be writing， updating the head index。😡，And the producer's thread preempts in。

And tries to read the head index in the middle of that right。

It's going to read some half written nonsense value。That's going to be that's not going to be good。

And the same thing could happen。If I were talking about updating the tail index as well。

 so the ring buffer's design really depends on both the head and tail indexes being able to be accessed in a non preemptive fashion where we can read and write those things without worry of something else interrupting us in the middle。

It also depends on having only one producer thread and one consumer thread because。

The increment of the index。Nes be that needs to be not competing with any other threads that are trying to do the same thing。

Now， some operations are just inherently non preempttable because， for example。

 they take just one processor cycle to complete just。They start。

 There's just the moment before they start。 And then the next moment， they're done。

There's no opportunity to interrupt them in the middle。But。For a longer operation。

Those absolutely could be preempted in the middle in a typical multi threading system。

And so if you want to prevent a longer operation like that。From being preempted。

 you either need to use。Some tools like locks to prevent that， or you need to go ahead and use。

Instructions that are going to ensure that nothing else interferes。

With that operation that you're trying to perform。 And so if someone who was using a lock in this situation。

 sorry。I've sometimes heard people describe using a lock like that as making the operation atomic。

I'm always a little bit hesitant to use that phrasing because it's easy to get confused about things that are。

As I'm calling them here， inherently non preempttable。Versus things that we've made non preempttable。

But。I think that but for this purpose， either one of them。

 as long as the operation is non preempttable， that's really what we need in this situation here。

So this is where I'm going to go ahead and apply my atomic template to the head and tail indexes。😡。

And here is the minimal version of the my atomic class template that I put together。

 the real stood atomic class has more capabilities than this。

 I'm going to focus on implementing these just because，😡。

we getOnce we understand how to implement these basic operations。

 implementing the others is something that we can build toward。

But I want to make sure that we get these pieces out of the way。So。Here。This， my atomic template has。

Trivial default constructor， it's not exactly a copy constructor。

 It's a constructor that takes an object of the underlying type as an initial value。

I chose to make this version neither copyable nor movable by deleting the copy operations in this situation。

😡，It's not copyable in the traditional sense， I should say。

 you need to use the store and load functions in order to the load function in particular to get the value out。

😡，As a nonatomic version of the object。And then you can store that into another myatomic of the same type。

 if you want to。Behind the scenes， it's all just using a single object of the underlying type。

I chose to make these functions pass by value， pass and return by value。

 rather than pass by reference， because that's how the stood atomic template is written to work。

 and I chose to mimic that in my design here。So the constructors are nice and straightforward。嗯。

As I said， this version of the type isn't really copyable or movable in terms of the atomic itself。

But you can use these functions to access the underlying value stored inside the atomic。And that's。

 in general， really what we need。So the operations that stood atomic supports， by and large。

 none of them is preempttable。 So that includes things like the store and load operations here。

 Store would be used for setting the value to something in particular。 If I'm working with， say。

 an atomic int load gives me back the value of。That object as an integer。嗯。And。

The atomic might be working by just using。 it might be that we're on a platform where itt is。

A naturally atomic type， something where operations on ints generally aren't preempttable。

Or it might be that St atomic uses some kind of internal locking mechanism to make it so that。

Those operations aren't preempttable。My atomic somehow has to accomplish the same thing。By the way。

 when you are using stood atomic， you can find out whether or not it is using a locking mechanism。

Each one has this is always lock free data member that you often see used in a static assert like this。

😡，So if I'm expecting that int 32 T is going to be。A lock free atomic type on my platform。

 I can verify that by doing a static assert on that is always lock free property。

 and that's generally what people recommend in order to test that kind of thing if that's what we're going to need。

😡，Now， it's actually， the reason it's called is always lock free。

 There is actually also an is lock free property that doesn't have the word always in it。

 It's implemented as a member function。And it's done that way because the standard allows for some statomic specializations to use locks conditionally。

 for example， they might allow you to create an object that's not aligned to the expected memory boundaries that an object of type T would normally be aligned to。

And in that situation。Is Lock free might return back true for a specific object？

If that object is aligned， for example， and it might return back false for a different。

 unaligned object。In that case， is always lock free for that type would be false。

But you could check for a specific object to see whether or not it uses locks by calling that is lock free function。

A lot of times people want the guarantee that that static assert gives us。

And I certainly wouldn't blame you for wanting to stick with those。

You have both options available when you're using statomic。All right。

 so now that we're we have the revised。Now that we're using the myatomic template to wrap up the head and tail indexes。

 let's take another look at the try pushback code。 It looked something like this。😡。

But this version still doesn't work。 It was where it tries to increment the tail and then check to see if we've gone out of bounds and set back to zero。

 But because that's actually performing multiple operations on tail。

That's not going to work correctly。It's past， even though。

If I've implemented my atomic type correctly and we'll talk about how to do that a little bit later on。

 but for right now。Let's just assume I've got that taken care of。

This code still wouldn't work correctly because preemption could still occur between the two operations。

 between the increment and setting the tail to zero here。😡，So。If that happens。Another thread。

 maybe one that's calling Tri pop at this point， might be confused because it would see the tail as being equal to size at that point。

Which isn't supposed to be possible， given the class invariance， It's supposed to be that。

The tail is either is always somewhere inside the bounds of the array。So that's no good。Instead。

 we want our try pushback code to look something like this。😡，Where。

We go ahead and we read from tail using the load operation。

 we store it in this local index next tail， and then we do our work with next tail。

 figure out what the value of tail after it's been advanced appropriately is going to be。😡。

And then we can go ahead and store that new value after we've done all of our calculations locally。😡。

Into。The actual tail index in one fell swoop。That's going to give us something that really is an operation that can't be preempted。

 We see the tail index having its old value。 And then we see。

 we immediately see it having the new value that it should have after the operation is finished。

From any other thread that's observing this stuff。Because this is this process of updating the index is pretty similar for both head and tail。

 I chose to create this next helper function as a private static member function for my ring buffer that would go ahead and actually calculate the next index。

 so the function looks like this， it's not particularly complicated。😡。

It' pretty much does exactly what we just described， but it means that， well。

 when we look at implementations of try pushback and tryP that actually use this net function， well。

 they'll fit nicely on a slide for one thing。😡，And I think it makes life a little bit easier to read。

 so here。Going through this。After we calculate where the next value of the tail index would be。

Assuming that there is actually room to hold another object in it at the moment。We check to see。

 is that actually true？Or would advancing the tail index give us the head index at this point。

 in which case。The queue is going to be full。That not is already full。

 That's not something that we can accommodate。Assuming that。

That we don't find that the queue is full at the moment。

 we can go ahead and actually take the value that we've been given V。And copy that element。Into。

My underlying storage， my array。 again， this kind of thing would look a little bit different if I needed to use types that were。

That had more sophisticated constructors and destructors here。

 I'm sticking with trivially constructible and destructible types。

So that we can focus on really the atomic part of this。As I say here。

 this part is actually preempttable。 If， this is the 32 B element that's being written in my example。

And。I haven't made these objects atomic， and it turns out they don't need to be。

It's just the tail and the head that need to be accessed in this nonpreemptive fashion in this way。

 once I've actually gone ahead and written the new value， the value of the new element。

 then I can go ahead and advance the tail index。😡，And as long as I can do that in a non preemptive fashion。

 then。All of this should work out just fine。Now， this is a slightly simplified version of try pushback。

 this isn't ideal because it's actually reading from Ta twice here once inside the next function and once there to write V into the underlying array。

😡，Here's a larger version that's a little bit more sophisticated。That。

 but it does prevent that issue by。It doesn't use next。

 It calculates the the next value of the tail and also keeps a local value of the current tail locally and works with both of those up until the point when。

It knows that it's succeeded in what it's trying to do and it's ready to go ahead and move on to the next tail location。

So。This is probably how I would actually write this function。For demonstration purposes。

 I think it's a little bit easier to see to make sense out of this version here。はい。

Try pop winds up looking fairly similar。 Again， it is making use of the next function as well。

It is checking to see whether or not the queue is empty。

 goes ahead and reads out the value of the front element。At that point， and then it goes ahead and。

Updates the head index。😡，Once the element has been read out successfully。

 then it can go ahead and move on to the next element。And then return true。

Now you might be concerned inside empty， it looks like this。😡。

Couldn'tn't we be preempted in the middle of this empty function。Yeah， we could。 Actually。

 there's nothing here that's preventing some kind of。Preemption between。

The point when we load the value from head， for example。

 and the point when we load the value from tail。But the design of the queue is such that although we can be preempted in that situation。

 it shouldn't cause any problems。Because empty is actually only called from the consumer thread at this point。

 it's only called to see， is there an element there to read？And so。

The only if this function happened to be preempted in the middle。

It would be because someone a different thread was calling。

 try pushback and actually inserting an element into the queue。At which point？

We get back to empty after that pushback has succeeded。And we see， oh。

 the queue is not empty anymore。Which is what we were hoping to see。

 that's actually a little bit nicer than getting the answer， oh， it's empty。

 actually it was empty until it just became full and then we have to go through another loop and check again at some point to see to get the next element out of the queue。

So the updates to the head and the tail indexes need to be non preemptive。😡。

It I made a very big point of trying to write indices in the slides。

 and I keep finding myself saying indexes。I。This is one of those things。

Although it updates those indices atomically， non preemptively。

It doesn't need any other locking mechanisms。As written。

 because only the producer thread tries to call try pushback。

Only it and it's going to write the new elements's value before it actually updates the Ta index。😡。

If it's preempted in the middle of writing that new element value。

 that's okay because until the tail index advances。😡。

The consumer thread doesn't see any sign that that new element that anything has started being written to that new location。

 It's effectively invisible。Until the tail index advances forward。

And that's done all in one atomic operation。And the same thing is true for TriPop。

 only the consumer thread actually calls the TriPop function。

It updates head only after it's finished reading out the front value。

If it's preempted in the middle of reading out the front value， that's okay because until。

The head index moves forward。Try pushback isn't going to be able to overwrite that element in the middle of the read。

 because it will see the queue as full。Until the head advances。So。That's how that winds up working。

 And this is the kind of thinking that you do need to engage in when you are working with atomic objects。

It's nice that we can get this fine grained if we need to。

 because these can have very nice performance characteristics， but。

It's also one reason why using a more coarse grained tool like a MuTex。

Might be the way to go if you're still getting used to this if you're trying to get your head wrapped around some of this thread synchronization stuff。

Atomics are probably not the place that I would start there。

 The thing that I would move to when I find that using a more coarse grained synchronization mechanism is not doing the job for me the way that I need them to do too。

Okay， so now let's talk about synchronized ability。

 So I mentioned the accesses to the head and the tail need to be handled in this non preemptive fashion。

It's also important as I just went through， that those indices advance after。

The corresponding element is read or written。 And that's where synchronization comes in。

 because in general。In a multithreaded application。

 we can't trust that the results of an operation performed on some thread A。

I are immediately going to be visible to some other thread B。

And there are lots of reasons that this could happen， but just to pick one example。

A and B could be running on different cores， A could be running on core1。

 B could be running on core 2。Depending on your architecture。

 Core1 and Core two might have different caches。And it might be that just because an operation has been performed on Co or A or on thread A on Co1。

 Co2's cache may not have been updated to reflect the changes made。😡，By the other processor。

 by the other core， as I said， this is， that's just meant to be one example， modern computers。

 modern optimization is a pretty complex set of stuff。

 so there are lots of ways that this kind of thing can happen that these synchronization problems can arise。

😡，That's just trying to give you something to la onto there as one possible way that this could go。

 but there are lots of different flavors in which this kind of thing can go wrong。

 The generalital statement is that operations on two separate threads。

 A and B are unsequenced as the standard puts it unless the threads do something too synchronize with each other。

And the net effect is that thread A and thread B。Might see the same events happen in different years。

Which is kind of mind bending。It's one of those things that you look at it and you say。

Really that can happen and yeah， unfortunately it can， it does make life kind of confusing。

 so in a situation like this， for example， here， thread A is writing to both X and Y。

 and then thread B is reading from X and Y into local variables I and J。

And because X and y start out as zero。And then thread A is writing them to one。

Looking at this code on the surface of it， you would say。Well。

 there's no way that threadreadB should read x as zero and y as one。

 because the right to X should happen first。Tly looks that way from the code。But。

One way that this could go wrong is the optimizer might， for whatever reason。

 choose to reorder our code。 It might see that it can do things。😡。

More efficiently if it writes to Y before it writes to X， and as far as it's concerned。

X and Y are these unrelated objects。 It's not like changing one of them is going to affect how it writes to the other one。

So。The compiler may happily reorder these things。I think that's pretty unlikely if they're really both integers like this because。

They writing them should be effectively the same kind of operation。

But it's the sort of thing that could occur。And again， optimization is a complex topic。

There are lots of reasons why things might happen this kind of way。

But even if the compiler doesn't reorder things。Just because X is written first on threadread A。

 that doesn't mean that that's what TreadB actually sees。😡。

Because it might be the case that X and Y are， for example， located on different cache lines。

And it might be and if whatever cash line Y is on is actually written out to memory。

Before the cache line that x is on。Then the results of that right。Might show up in thread B。

 the right to Y might show up in B before the results of the right to X。

So we can't rely on the idea that。Just looking at this code that it goes in the order that we would expect and what that means for our ring buffer is if we look at the code for TriPop here。

 I showed you this code and I was saying， okay。😡，We won't be updating the head index until after we've already read out the value at the front of the queue。

 so everything should be fine。😡，But。If neither， but。

If the compiler happens to reorder things or if for some other reason。

 the producer threads sees line two happen before line1。😡。

It might go ahead and let try pushback run in such a way that it would overwrite the front element in the middle of it being read。

And we could get a synchronization of problem。We could wind up with corrupted data so this is this code winds up being safe only if line number two there is performing is what we call a synchronization operation。

 So there are certain things that the standard recognizes as synchronization operations。

 their operations on muttexes and other。😡，Library thread synchronization tools like semaphos。😡。

And then there are also operations。Many， but not all operations on atomic objects are synchronization operations。

😡，And so in order for the producer thread and the consumer' thread to synchronize with each other。

 they both need to contain one of these synchronization operations。😡，Actually。

 when we're talking about atomic objects in particular。

 these synchronization operations actually come in these two flavors。

 release operations and acquire operations。Typically you think of when you want to think of an example of a release operation。

 you're thinking of a right， typically when you're thinking of an acquire operation that would be a read。

But it's not forced to be that way， the rule is that thread A synchronizes with thread B if they're both accessing the same object。

😡，And thread A。Writes to that shared object X， with a release operation。And then thread B reads X。

 and it sees the value。Performs an acquire operation on X。

 and it gets back the value that was written by thread A。Actually。

 it's a little bit more sophisticated than that， if it sees the value written by thread A or a value that was written after the value that was written by thread A。

😡，If you want to be technical。So that's what needs to happen in order for these two threads to synchronize with each other。

Now I say that these operations can be release operations and acquire operations by default operations on satomic objects are both release operations and acquire operations you have to take action to make it not that way。

 so I'm going to start with the idea that we want our operations to be both release operations and acquire operations。

😡，And we'll talk about how to implement that。And then if there's time。

 I don't actually have slides on making them just release operations。

 but I can talk a little bit about that if there's time at the end。Okay。

 so how do we actually go ahead and implement this myatomic class template so that it has these properties？

😡，啊。The constructor just goes ahead and calls the store function。

 so really it's just the load and store functions that we need to focus on here。😡。

The techniques going that we're going to use here， they could be used to implement the wider stood atomic interface。

😡，Without too much additional difficulty。So。What are some ways that we could do this？ Well， again。

 some threading system， some multi threadreaded systems are not hardware or concurrent。

 They don't actually run multiple operations at the same time。In that case。

 most of those systems have some kind of scheduler that's managing the threading system that's deciding how and when each thread is going to run and that scheduler is controlled by an interrupt。

And so on those sorts of systems where you're dealing with something that doesn't have real hardware concurrency。

😡，Disabling interrupts is often a way of stopping preventing preemption from occurring on that kind of system and that's what the Arduino mega 2560 recommended so that's where I started for the code that I was writing for this。

😡，Disabling interrupts exactly how you do it is a platform specific operation in general。

If you're using something like an Rto， there might be helper functions built into it that would let you do that。

 but on the mega2560， there's a global interrupt enable bit in the status register that you can set either by writing to it directly。

 or there are these macros， SEI set enable interrupt and CLI clear interrupt。😡。

That you can use to clear or set that one bit in particular。

AndSo the code that if you look at the data sheet， the mega 2560 suggests that your code that would disable interrupts would look something like this where。

They use an example that involves writing to some hardware register。

 so that's what HW Regdge is in this case。😡，And next Regdge value holds the value we want to write to that。

They make a copy of the current status register's value into CS Regdge。

They call the CLI macro to Disable interrupts。😡，Then they actually go ahead and do the right that we wanted to be non preemptive。

 but。Since the Arduino is an eight bit platform writing to a UN N 16 normally。

Is something that can be preempted unless we take an approach like this。

And then when we're finished with that， we can go ahead and restore the value that we saved from the status registered before。

 and that will go ahead and re enableable interrupts for us。

We could have called the SEI macro instead。But this is the approach that they show on the data sheet。

So in C+， I would generally go ahead and write this as some kind of RAII type like this one that I called interrupt Disabler that does the work of capturing the value of the status register in the constructor。

 clears interrupts at that point and then its deor goes ahead and restores the saved value back to the status register when it's finished。

😡，Not that you really， I mean， a lot of the times when people talk about RAI types like this。

They're citing this as a good a good reason for this is to do things like， well。

 if an exception gets thrown， your deor is going to run。Please don't try to throw an exception。

 I mean， Maybe once we have Khalil's stuff， Kahalilt's stuff that he's working on。

 maybe we can talk about throwing exceptions in there， although even then。With interrupts disabled。

 I'm not sure I would give that a shot， but yeah， with the exceptions that we have right now。

 I don't think that you're going to be happy with the results if you throw an exception while you've got interrupts disabled。

But there's very little reason not to follow that general pattern。 There are lots of， you know。

 it's another way that we can avoid forgetting to do something like restoring interrupts back。

All right， so here is a version of the myatomic load function that goes ahead and uses that interrupt the Disr class to read out the value and it's pretty straightforward。

Really is just reading out the underlying T value into RV so that it can then return it。

The corresponding version of the store function。Similarly， just disabledables interrupts。

 goes ahead and does the store。Okay， so I talked about how the interrupt disr。

 It interacts with the thread scheduler。 So that makes things non preemptive。

But where's the synchronization going on here？If you look at how the SEI and the CLI macros are actually implemented on this platform。

 here's when they're implemented with a conditional compilation。

 but I've chosen the code for GCC here just because，😡，It's relatively easy to explain。

 it's got some nice pieces to it and。code， the underlying idea works similarly with other compilers。

😡，So what exactly is this are these macros doing Well。

 the underscore underscore ASM underscore underscore。

 that is a G new extension that lets us embed blocks of assembly code into our CNC++ code。😡。

The volatile underscore underscore volatile underscore underscore。

 it's a qualifier that goes on those assembly blocks and what it says is to the compiler is that this assembly code has side effects that。

😡，Are not necessarily obvious just from looking at these blocks can take input and output values。😡。

I'll talk about that in a moment。Ordinarily， the compiler would assume if it saw input and output values here that those are the only things that would be affected by this block。

 The volatile qualifier there lets it know that。That's not the situation。 It needs to assume that。

These instructions affect the wider ecosystem。So it can't optimize things in certain ways。Similar to。

 but not quite exactly the same as the typical C++ volatile qualifier that we use。

The quoted SEI and CLI there。Those are， they chose those names for the macros because those are actually the names of assembly instructions in AVR。

 the assembly language that the art we know， omega 2560 uses。😡。

SEI is an instruction that sets that global interrupt enable flag and CLI clears the same flag。😡。

So those are just the assembly instructions that are going to be run by these blocks， in this case。

 there's just one instruction in each block。😡，There are those three Colbins there。As it happens。

 these assembly instructions don't have any output operas， but if there were any。

 they would be listed after that first。Colon there， the one that's shown in red here。

 and then if there were input operaans， they would be listed after the second colon， which is。

whichhich is shown in teal here， I don't know if that's visible on the screen all that well。😡。

But yeah， the second colon there after that would normally be the input up ends。

These instructions don't have any of either。So we just ranmmed the three colons together。

 which seems to be pretty common。The third colon begins what the documentation calls the clubers section。

 which normally lists out the registers that would be overwritten by this assembly block。

 the idea being that。The compiler behind the scenes， it's been working with your C and C++ code。

 and it's been using registers， choosing what to put into various registers at different points and now we're taking control away from it to run our own assembly if we start using registers。

😡，That the compiler was already using。How does it know that those registers have different values when we get back from our handwritten assembly block。

 that's what this clolobbbers section is meant to tell it， it lists out those registers here。😡。

But there are also these special klobbers arguments。is one of them。

And that turns out to be the thing that's really doing the synchronization part。Here。

 that special club argument memory， more or less what it's saying is this is an assembly block that affects all of memory。

So the compiler， when it's generating the code for this。

 it has to generate the code for the assembly block and the code that's around the assembly block so that it flushes any rights that have been stored in registers and cash up to this point。

 that is before it enters the assembly block。😡，It's got to take any intermediate results currently stored in registers or cash。

Fluush those out to memory。And。Once it's finished executing this assembly block。

 it's got to go ahead and reload any values that had been in registers or cash prior to running that assembly block。

 It's got to treat those as being。Overwritten effectively needs to go ahead and refresh its information there。

 And this is one way to accomplish that thread synchronization。

 The memory clubber's argument sets up what's often referred to as a memory barrier。Like this。

And that's what really needs to happen in order to mechanically make all of this go。Now。

 I've shown this to you in the case of using the SEI and CLI instructions to enable and disable interrupts。

 but you can use this same technique in other situations to employ assembly instructions that would go ahead and perform atomic operations directly like。

😡，Here what we see what we have is a small，s not it's a block。 Again。

 it's a single instruction of X 86 assembly。That is performing an atomic increment on the value X here。

 and here we are actually using the input and output operarans here。😡。

X is really both an input and an output operaand here， so it gets listed under the output operaran。😡。

The literal one there is just an input operaand。And we have the lock qualifier on that X add L instruction there。

This how you would this is an assembly instruction for operating on a true multi corere hardware concurrent system where putting that lock qualifier in there。

😡，Giveson tells the system to carry out the ad instruction in such a way that other cores。

 operations that are being performed concurrently on other parts of the system can't interfere with this increment。

 the increment will happen effectively all at once in that atomic fashion that we want。Now。

 an alternative， and this might be easier if you've got if your compiler provides these tools for you。

 another way of implementing my atomic might be to use some compiler intrinsic functions like GCC provides these functions。

 atomic load N and atomic store N that are designed for working with integral types and pointer types。

😡，And the first argument to each of these is a pointer to the atomic object。

That you want to read from or write to。So here， this first call reads a2 byte value from the atomic object into X。

mOh。And there's that extra argument there at the end， up type。

I'll explain what's going on there in just a moment。 And the second example does a4 Bte right。

Two atomic object two。啊。That last argument there in both of those。Up type there。

That is essentially an enumeration value that corresponds to the stood memory order enumeration that you can find in the atomic header。

 these are macros that are again， compiler built compiler intrinsics that correspond to the possible memory order values。

 in this case I'm using atomic SQ CST is the equivalent of the default that stood atomic uses。

 it makes each operation both a release operation and an acquire operation。😡，Actually， technically。

 it does a little bit more than that it ensures that there's a total ordering across all atomic operations in the system。

 So here are some implementations of the my atomic。Functions。Here using these intrinsic functions。

And the compiler figures out based on what type value is there， whether from looking at value。

 whether it's doing a one byte right or a two byte or eat， a four byte operation， etc ceter。😡。

There are a whole bunch of intrinsic functions like these that are at least that are available on some platforms Now your compiler may not provide all of these。

 I found that the Arduino was happy to provide one byte versions。😡，Of these functions。

But it was not so happy about two and four and eight byte versions。

So if I wanted to use a larger object there。I had to use a lock based approach。

But this is what GCC calls its operations， there are others on other platforms。

 MSBC uses these functions for the Ar 64 platform。😡。

And the default names Interlocked exchange is a 32 bit operation。

 but you can append a bit number to the end of them to get an8 or 16 or 64 bit operation instead。

So our atomic operations， we need to make sure that they're non preempttable。

 that they synchronize appropriately with atomic operations on other threads。

There were unfortunately subtleties about this I wasn't quite able to get into with regard to the memory orders。

 so you can see that enumeration for more details， CPP reference covers it very well。😡。

You can either use a locking approach to accomplish this kind of thing or you can make use of raw assembly blocks or intrinsic functions。

 I think all of those approaches can serve you very well。



![](img/34086f0e254b5ff60abd97075f4e2ee0_5.png)

はい。That brings me to the end。 Thank you all for coming。 Hope you guys find this useful。

 Enjoy the rest of the conference。 And yeah， I'm we don't quite have time time left in the official block for questions。

 but it is the end of the day。 I'm happy to answer questions individually。

 if you guys want to come up and talk to me after this。😊，やep。Enjoy the rest of your day。



![](img/34086f0e254b5ff60abd97075f4e2ee0_7.png)

![](img/34086f0e254b5ff60abd97075f4e2ee0_8.png)