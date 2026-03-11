# Cppcon-2025-｜-C++-｜-C语言--｜-汇编-｜-编译器-｜-操作系统-｜-Linux-｜-Windows-p79-P79_实现C++标准库_设计、优化与测试（以Libc++实现为例）--BV1wyPBzrEeu_p79-

![](img/cfccf7a3f8642eabdd03da4e0cd77753_0.png)

![](img/cfccf7a3f8642eabdd03da4e0cd77753_1.png)

Alright， hello everyone。 Welcome to my talk。 Today。

 I'm going to talk about implementing standard libraries。



![](img/cfccf7a3f8642eabdd03da4e0cd77753_3.png)

I'm going to share the design decisions， optimizations and testing in Lips C++。

So Lipsy purpose is a standard library implementation。 It is the part of the LLVM project。

And it is the standard library that ships with the compiler Klan。So in today's talk。

I'm going to share some interesting examples about optimizations in the library。

 I'm going to focus on some standard types like expected and also some algorithms。And in the end。

 I'm going to share some testing with techniques we've been doing in the library。

So the first example， oh sorry。 So my name is Hui， and I'm a software developer at QrRT。

 which is a hedge fund based in London。And I am a Lips CP contributor for the last couple of years and I'm a member of this in the committee。

And the UK National body member。And mostly working in a range study group。

 and sometimes I write C purpose proposals。The first example。

I'm going to share is about study expected。 St expected is a utility class added in C purpose+ 23。

 which is used for error handling。 so the user can call a function that returns the study the expected。

And then he can query the the expected has value or not。

 And also can they can retrieve the value or the error out of the expected。Another question is。

 how do we implement this classness on the library。And before I go into the details。

Let's first look at this example。 Imagine we have a class fo。Which contains an int， a char and a bo。

What is the size of this class？给你。Idea， guess。Yes，That's right。 So on most implementations。

 it will be 8 by because we get got a4 by for the end to 1 by for the child 1 B for the bull。

 Then we have two bys tail padding in， in the end。 That's a typical implementation。

Another question is， what should be the size of stood expected of F and an error code。16。好right。Yeah。

 I think the answer is it depends on the implementation。

Let's first look at the first implement implementation。

So this is an implementation and GCC's lip stood safe purpose us。Basically， we've got a union。

 which contains either a value on an error。 And then we have another poololeion afterwards to tell whether or not we got an error。

 of got an value。So with this implementation， what will be the size？Right。可以。Well it's 12。

 So this is why。You first we got the fool。Got the full bicent and China Bo Go the food patterndding as well。

Then the compiler puts the boion after the the full， right。And because of the alignment of the int。

 the compiler has to put 3 B tailpadding at the end。 So that's 12 B in total。

And now this is the implementation in Lipsy purpose， implementation。It looks very similar。

 we've got a union and a bull， and the only difference is that we apply this attribute。

 no unique address on in frontile members。And how does that make a difference so。

So no unique address attribute standard defines this way。 Basically。

 it tells the compiler that our members are potentially overlapping。

So what does that mean in concrete examples in this particular case？We first， we still got the full。

 We the In Chinabo。 We still got two by padding for the full。

 And because we tell the compiler that our members are potentially overlapping what the compiler can do。

 they can。 It can put the boolean has value inside the ta padding of Fo in this case。

 so that makes our state expected only8 bytes compared to GC implementation。

And what's the benefits of having like， smaller types。Any。Ideas。Right， exactly。

So while the euro benefit， we got smaller memory footprint prints and we got better cash locality。

And I have one more observation because stood expected。

Is a type that is likely to be used as a return type of a function。

 So imagine we have this function compute， which returns as stood the expected。Right。

 and for simplicity， my function only returns just create value full insight。

And with Gs's implementation。Oh that's basically the code generation。

 thanks to the return value optimization。Gcc directly put the value inside the collar stack。 However。

 you still need some code to manage the stack pointer。 That's what it is。

 It's managing the stack pointer。And with our implementation in this particular case。

 because our study expected is only 8 bys， it is smaller enough to fit into a register。

 So the compiler directly write the result into the return value register IA X。

 So that's how we can get some benefit of having smallerish types。So the takeaway of this example。

 I'd like to share is that you can use this attribute。

 no unique address to reuse the tail paddings inside your class。

So that also includes the tail padding of an empty type。

 because an empty type naturally has 1 B tail padding。 That's the rule of C plus。And traditionally。

 we've been using empty base optimization and now we can use no unique address。So。

Let me move on to your next example。Still， still stood expected， still with no unique address。

And this is an actual bug we shipped and lift the purpose for one release。

And the bug is inside this copy constructor。So in this copy constructed I expected。

We first initialize the Boolean has value。From the others expected makes sense。Right。

And then if has value is true， we got in value。We're going to call the copy constructor of the value。

 The state construct will eventually call placement new and invoke the copy constructor。

And if we don't have that value， we call the copy constructor of the error。So。

Looks very simple and reasonable。However， things are not always simple。

I will show you the bug report we have， so this is the user。Users code。

They create an expected with a value fool， right。And they call the copy constructor。

To create another one。And they check。It has the copy has value should be true， which makes sense。

 however， due to the bug。It's， it's false。 So why is that。Any guess？通。Exactly。So， this is a。

The book boils down to the rule of Cp 0 initialization rule。So the standard says。

 during zero initialization。All the padding bits are zeroed。And this isn what happened exactly。

We first initialize our Boolean。Which is true in this case。

And then we call the copy constructor of the fool。At the memory address of our inside our union。

And eventually it will invoke， it will do a zero initialization。

And because our bullolean lives inside the tail padding， inside the padding， it's got zeroed out。

And that's why we got this bug。And to fix this particular bug。

 we have to initialize this boion after we invoke the constructor。

 invoke the initialization of the full， the， the value or the error。

But the takeaway from this example I'd like to share is that no unique address is great。

 and you can use it safely in most of the cases to make your memory more compact。😊，However。

 don't mix it with manual lifetime management like union or construct at or Place New。

 Otherwise you run into the possibility of a memory got overwritten。Right。

Any questions before I move on to the next example， Yes。カてい。Well mam copy。

 you can decide how many bys you mam copy。Yes。Yes。I mean copy be includingd its help。Yes。

 that's a very like very， very good question。 And very。

 I would say is a very dangerous implementation of assignment。 if you just do Mem copy， because yeah。

 you might run into cases like this。But that falls into the same takeaway。 Thats I I。

 I conclude that as a manual lifetime management。 You use ma copy。

 unless you really know what you are doing。はい。What time。Well， we。嗯。We don't actually care about that。

 The user needs to。It will work for most of the type unless the user has a really withiz。

With implementation like demand copy， which is really dangerous， right。

So the next example is about stop token。 So these three classes are adjutency purpose 20。

 they are used for。Concurrency， they are concurrency utilities。And basically。

 this slide shows an example how you can use it。So on thread one。

 you can ask the stop source to register stop token to get a stop token。

 then you can periodically query。The stop requested flag from the token。 So if that。

 if stop is not requested， you can do some work。 Otherwise you exit， then do some cleanup。Right。

And on thread 2 and 3， you can register as many as stop callbacks as possible。 They callbacks。

And on another different thread at certain time， you can say， oh， stop source request stop。

And what happened。When you call that function is that it will set the stop request to flag。

 So threat one， that wire loop will exit and do some cleanup。

And the stop callbacks you registered on the threat 2 and thread 3 will be sequentially evaluated on the threat4。

Right， so now let's think about how we can implement these three classes， I mean。

From what we can see that all these threads， all these classes。

 they somehow communicate with each other。And a simple way to achieve this is under the hood。

We can have a stop state， a shared state。And all the stop source， stop token stop callbacks。

 They hold shared pointer to this share state， and they can mutate and like inform each other。

But how do we design this shared state。And let's go back and to look at the requirements we need to have。

 So we need to implement lots of functions。 The first one is we need to implement this stop requested function。

And to implement that function， we need sort of a flag to tell us if it is requested。

And there's another function we need to implement， which is called stop possible。

So the way it works is that if all the stop sources are destroyed。

 then nobody can make a stop request anymore。Then stop possible should return false， right？

But to implement this function， we need to keep track of number of livestock sources。

And for the stop callbacks， as I said， we need to sequentially evaluate the callbacks。

 So we need to somehow store a list to the reference of all the callbacks so we can。

It's way through them。And then because this is about concurrency。 So we， we can't have a normal list。

 We need to。 we need to synchronize this list with some sort of synchronization。However。

I can't really use a vanilla muttex because muttex locking and unlocking can through exception。

 And all these functions are required to be no exception， so。We need news。 We can。 Yeah。

 we can probably try cash and a wire loop， for example， but we can't directly use a mutex。And lastly。

 because this is a shared state， we need to manage its own lifetime。

 So as showing the previous slides， we can use a sharedd pointer， for example。

And this is how a naive implementation look like。We first， we need the atomic boolean， right。

 to indicate that flag。And then we can have atomic integer and that atomic integers count number of stop sources。

And to implement this stop possible function。And for the stop callbacks， or naively。

 we can use a stitch list。Of the Colby pointus。And lastly。

 we can have a new text to guard against this list。 We probably need to try catch and do some stuff。

And with this na evenval implementation。The， the stop state is 72 B in lipsy purpose。And plus。

 additional memory allocation for each node in a stood list。RightAnd for the stop token。

 because I said we need a shed pointer and the shed pointer is 16 by because you need a pointer to the control block and a pointer to your object。

So that's a lot of memory， I mean， and which is not very efficient， memory efficient。

And maybe let's look at how we implement this shared state。We first have a 32 B tinageger。

Atomic inteigent。But we use this atomic integer。For multiple purposes。 so for the lowest bit。

We use it as a stop requested bit。At the end of the day， we don't need a boo。 A boo is a bite。

 but we don't need a bite to store us flag。 We just need a bit。for the second bit。

 we use it as callback list locked， so we don't need a mutex。

And thanks to the C purposese 20 addition to the atomic API。

 now we can implement an atomic a unique lock with atomic weight。

 atomic notify and Comp exchange loop。So you just need one bit with all these operations to effectively implement a muttex or a locking。

 a unique lock。Right。And for the rest 30 B in this integer。We use it as stop source counter。

That's for the stop possible function。And now for let's stop call back。Because we。

 because we don't really own these callbacks， the actual user who creates them own them。

 So we don't need a stood list to allocate all the memory。And in lipsy purpose。

 we have a very lightweight thing called intrusive list view。

 So it is just a lightweight view on the list。 And under the hood。

 it will just store a pointer to the root node。😊，And each node was still pointed to the previous and next node。

Right。And for this lightweight class， it only holds a pointer。To the written note。

And if we look at this class， we got a4 byte integer at the beginning。

And8 byte inte8 byte point at the end。And what you can notice is there is a hole in the middle。

 What is that。That's the padding。So if you have a4 byte intertegender A by pointer。

 you will have a4 byte padding in the middle of your class。Which is a waste waste of memory。And。

We happen to fit another 4 by engine in the middle。

We don't really need a shared pointer because we don't need a control block。

 We don't need a weak pointer because all we all we need is to manage the lifetime of this class itself。

 so we can just have a reference counting。For the stop token， stop call back and stop sources， right？

And with this reference content inside this class， we no longer need a shared pointer。

Because we can use something。 Well in ellipy purpose， we have a thing called intrusive ShaPoer。

 which is just a share pointer without the control block。

 It tool because we store the reference content inside the class itself。So， with this implementation。

The stop state is only 16 B， compared to the 72。Fights of the previous。

All of the previous naive implementation。And for the stop token。

 it's down to 8 by because we don't need the sharepoint anymore。

 We don't need the pointer to the control block。 So we just need a。

Like intrusive Shapointer to the object itself。And the takeaway of this example。

 I like to share is that sometimes we can try to reuse unused bits to save some space。

 In this example， we use a 32 32 bit integer for three different like objects， not objects。

 but like three different purposes。And the second takeaway is that you when you design your class。

 you can look for。Some hole inside your class。 You might have lots of paddings in the middle of your class。

 And that's a place where you can fit something else for free storage。Right。

Before more I move to the next example， do you have any questions？Okay， okay， please。Yes。

 but you have to do memory on patients。The evaluation has to be no except like the registration。

And the registration。 But we don't， we only allocate the stop state when we。

 when we first create the stop source。 use the microphone， please。

You have to allocate the not to store the call by doing it into linked， right。

 The node itself is actually stock callback。 Stock call itself is a node。 So the the the the。

 the user who creates the callback。They probably are create on the stack， right， or on stack。 Yeah。

 they're probably gonna create on the stack。 So the note is on the， on the stack， right。We hope。

 so the in SharePo intrus list is not allocating for those。The note is the stop callback。 I see，Cool。

So now I'm going to move the。Topic 2 algorithms。And the algorithm I like to talk first is for each。

 the simplest ever algorithm。Imagine have a stood deck， right。

And all I want to do is I want to iterate through all the elements。😊。

And I modify each of the int to apply a cap and the floor。 Just clamp it。 and I'm。

And the first way of doing this is a rather range for loop。And cost a clamp to modify it on the fly。

And the second way I'm doing this， I'm using this ranges for each。And with exactly the same thing。

Do you think there will be any performance difference。

Hands up if you think the performance should be exactly the same， these two versions。Hands up。

 if you think。The second will will be faster。Right， a few。Okay， so that's the benchmark。

We can see on with ranges for each version， it's between three times to 12 times faster。

How is that even possible， Like ranges for each is just a full loop， right。And let's look at。

 take a step back and look at what the deck is。A stood deck contains a number of memory blocks。

 and each memory block is a fixed size， contiguous memory。And the stood block will have an array of。

Block pointers pointing to the beginning of each memory block。And like。

 if you you can think of the deck as a array of arrays。And now， if you write arranged for loop。

Because the C purpose iteration model is based on iterators。 So， well。

 this is not exactly what the compiler would generate， but that's the simplified version。

Where the compiler will generate， if you write a range for loop， it would say co begin。

 and you will write a traditional for loop with implementing your iterator。

And our decade trade looks like this。 Well， some in the operator plus plus something like that。

 We're gonna increment the element pointer。And if that point， I reaches the end of the。

Reaches the end of the block。And we're going to increment the block iterator。

 then reset the element inator to the beginning of the next block。 So it's not super complicated。

But it's complicated enough for the compiler to understand the whole picture and to do any optimization on it。

And let's look at our library solution。So first of all。

 there is this segmented iterator concept coming from this paper and we' introduce this concept into C live C++。

So a segment， segmented iterators are iterators over a range of of sub ranges。

 like our flat our decade is exactly one of this is a range of sub ranges。

And if we perform optimizations on segmented digitaltator。

 we can allow algorithms to operate on the sub ranges more natively。 So how does that work。

Let me show you this helper function first。 This is the the key of the optimization for each segment。

So first of all， if you pass to a ring like a begin and itator that models the segmented iterator concept。

 we're going to first ask the trays， can you unwrap this itator and give me the outer iterator。

And then we're gonna to write our for loop to iterate through this outer iterator。

 So in the deck case。This will be a loop over the memory blocks。And for each block。

 we're gonna ask the traces again， can you unwrap the iterator and give me the inner iterator。

So the inner iterator in this case is for each block， is the element iterator。

And now for ranges for each。And we have an optimization。 if your inputs model this concept。Well。

 this morning， I think most of you attend the generic programming and concept talk。

I know we are like a concrete example in the library。We we optimize based on concept。

 If your input bay models the concept。 we're going to call this our helper function。

And which gonna write outer a loop。 And for the inner loop， we're gonna a it for each again。

 But on the inner iterator type。So if you look at these two blocks of code together， all we did。😊。

Was to rewrite a flattened ranges for each into a nested for loop。

And the key thing here is the inner loop。It's rate type。

The inner loop inner the block is a contiguous block memory block。

 and the iterator type is just a row pointer。And the compiler is really good at optimizing follow loop with row pointers。

And if you look at the code generation on the right hand side， it is the range for each version。

 You can see the compiler generates lots of C D instructions with these X， M M wide registers。

And what it does is essentially， it vectorize the inner loop。That's why we。

 we get a lot more faster with ranges for each version。K。

So let me move on to the next algorithm ranges copy in this case。We don't have a deck anymore。

 We have a vector of a vector。A ventt， like a nested vector as an input。

 And all I want to do is I want to copy every single element of this int into my out vector。

And there are two ways。 Well， a natural way。You would write a nested for look like this and keep calling pushback。

With a reserve， of course。And because our， in this case， our inner loop is iterating over a vector。

 So it's already contiguous。 so our compiler can already vectorize this operation。 So in theory。

 it should get an optimal performance already。😊，And the second way。Is we use ranges copy。

 And because our inputs is not really a sequence of ins。 It's a nest structure。

 We have to use this C reviews join， which is a C purpose 20。Rangers adapter。

 which will provide you a flattened view of an nested ranges。

And then we can call ranges copy on this flattened view and copy all the elements into the out vector。

So hands up， if you think they should。Perform exactly the same。The performance。Hands up。

 if you think the ranger's copy is faster。Right。Yes， so this is the benchmark。

 You can see the ranges copy is still 50% to flight times faster。

Even though the full loop version should already been vectorized。

And this is the optimization we've been doing so first of all。

 JoinVi iterator is naturally a segmented iterator because JoinVi is naturally a range of subranges。

 so its iterator will model this concept it will benefit from the same optimization we've been doing。

And for the ranges for each algorithm， if the inputs model this concept。

 we're gonna reuse that for each segment， which gonna own。

Going to unwrap youratortor and write out as the outer for loop。And for the inner loop。

 we're gonna delegate to the Rs copy again。 So we recursively call Rs copy， but。

The type will be the inner iterator type because the concept or algorithm algorithmm already unwraps the。

 the iterator to the inneritator in this case will be the vector int iterator。

And it happens that we have an existing optimization on ranges copy。So。

 there's an existing optimization。If your inputs is contiguous and if your element type is trivially copyable。

 we can lower the lower the。The operation copying the whole range into a man move， or manm copy。

So this implementation is this because our our inner ranges copy is operating on a vector in。

 which will satisfy this constraints。 so it will reuse this optimization。

 So if we put these two blocks together the segmented iterator concept。

 help us to unwrap the iterator。To the vector int。 and the second case is an existing optimization。

 which can be used because the at is already unwrapped。And that is why we gain performance， because。

Yeah， the in loop is effectively a man move。So the takeaway of these two examples I'd like to share is that we constantly add optimizations to algorithms。

Pce to use them。And we do optimization based on concept， we don't just pick a type and say， yeah。

 we do it， we trying to categorize them， trying to do generic programming on the concept。

 which is exactly what Bono was talking about this morning。

And our optimization are often generic and composable。 So we， in this case。

 we can see we managed to reuse an existing optimization without any more work。

So any question before I move on again？Okay， please。Generalizing this。So in our case。WeGo for one。

We need questions on the microphone and the recording won't get them。All right。Y。

You tried generalizing this to what people call tensors。

 so energy arrays instead of what US essentially have like a two dimensional array。I'm just curious。

being so prevalent or energy arrays or whatever do you see the same improvements in performance Well。

 because go could you you know， essentially haveductive recursive Yeah。

 you had the look there Can you do this recursively basically Yeah， it is recursive， but。

There needs to be some optimization mechanism because we do optimization only for the standard library。

 The tens is not part of the standard library。 have you sort of like empirical just tried let's say three dimensional three dimensions。

 in theory， if like if NRA is adopted， we will definitely it a type modify this model this concept。

 it will definitely like benefit from the optimization。 but NRA is still not in the standard yet。

 theres M D span， which。Which were potentially。Imp in civil， yeah。Thank you。Okay。

 now I'm going to move the topic to， to。To container us。

So the the container like to talk about is flatmap。

 Flmap is a container adapter added N C purpose 23。 It provides the same interface as a standard map。

But the difference is that under the hood instead of storing a tree。

 it stores two sequence containers。 So I'm going give you an example。

 If there's a flat map from int to double under the hood。

 there will be a vector int to store the keys and a vector。Double to just all the values。

 and we keep the keys always sorted so that we can have log n time looked lookup。Right。And now。Well。

 by the way， there's no unique address like everywhere。 Yeah basically。

 no unique address is everywhere in our lipsy purpose implementation。Anywaywhere。

 anything can have tailpaddings or empty。No unique address will be helpful to reuse any tail pas。

imagine we have two stood to flatmap， M1 and M2。And all I want to do is， I want to。

Insert every single element from M2 into M1。And the naive way of writing this code is you write a full loop。

And then you in every single key value pair into the first one。Any problem with this full loop？Great。

So the problem is about time complexity。As I mentioned， we need to keep this vector always sorted。

So every insertion， it will do a binary search to find the right place and insert it there。

 and because it's a vector it needs to shift all the elements of to the right， further to the right。

 So every insertion is a linear right makes sense。And because this is a full loop。 So overall it。

 it's got quadratic complexity。Which is really bad， I mean。And luckily。

 standard provides a different API called insert range。

So if you want to insert the whole range of pairs， key value pairs。And the standard says。

 with this function， you can get M plus M log M time complexity to insert the whole range。

And now you can， what you can do is you can do M1 dot in range M2。

That will give you a like M log M plus N complexity instead of a quadratic function。

Which is much better。And even better， there's another overload。

If you know your inputs are already sorted。You can tell the library pass this tag type。

 so it is unique。And to tell the library， my inputs are already sorted。

And the library will skip the sorting steps。 so you get a linear complexity。And in this case。

 you can just do M Y insert range sorted you come to。But now the question is， as a library vendor。

 how do we implement these insert ranges？So in a nutshell， this is not exactly how we implemented。

There are a couple steps to insert insert range。As I mentioned。

 we have a vector keys and vector values。 So the first step is。

We appentt all the new elements at the end of the two actors。Right。

Then we partially sort the newly inserted elements。 so after this step。

 we're gonna have two sorted subranges inside our vector。By the way， for the sorted unique overload。

 this step can be skipped。And then we can in place merger to sorted。

Ranges into a single sorted range， sorted vector。And then we can remove the duplicates at the end。

There might be some optimization you can do to combine the last two steps。

 the merge and remove duplicatecase in the one pass。

But the thing I'd like to talk about is a bit is for the simple thing。

 How do we append the new range at the end of the vector。Sounds quite easy。

So this is the most generic implementation。All， all you do is write a full loop。

You're given a range of pair like things。 You just write off for loop。

And you get a pair out of each element。And then you insert Paedal first at the end of the key vector and Paedal second at the end of the value vector。

Well， this works， so。Because it's most generic way of implementing this function。

But it insert one element at a time。And we're gonna to miss some optimizations on another on a vector insert with a arranged version。

 So vector insert has another overload where you pass a position and a pair of iterator。

 and it's going to insert a whole range of elements。

And we have lots of optimizations on this overload。 For example。

 if your inputs are contiguous and the type elements are trivially copyable。

 we're gonna just do a ma copy to copy the whole whole range。And ideally。

 we can use this overload and to benefit from our existing optimization。

But the element types are not the same。 We're given a range of pairs。

But we got vector vector ins and vector doubles there。Elements。Type don't really match。

And we can't really use that overload。However， because we're inserting one F mapap into another F map。

 even though Fmap presented us a range of pairs， but we know that under the hood。

 Fm has a key vector and a value vector。So at the end of the day。

 we're just inserting two vectors into another two vectors。 So in theory。

 we should be able to use this vector insert。 We just need to do some clever things in the library。

And to solve this problem。We introduced another concept， called product iterator。

Product iterators are iterators。That aggregate multiple underlying iterators。

And flat market traitr is naturally a product a because it aggregates the key vector each and value vector traitator。

 right？And because we have this concept， we can write an optimization based on this concept。

If your inputs happen to model this product iterator concept。What we can do is that。

You can ask the trace。 Can you unwrap this product itator and give me the underlying。0 and1 s。

 I mean， by0 and1， I mean， because Flmap has it has two it。So with this technique。

The trace will unrap the flat map into a vector key vectorator and value vector。

 Then we can call that overload the ranged overload。 And with this overload。

 we're gonna benefit from the existing optimization where we can map copy the whole thing into the vector。

😊，And we can do the same for the values vector。Right。And thanks to this optimization。

 we gain about 22 to 10 times performance gain。Just to unwrap this iterator。Right。

Thanks to the existing optimism as as well， because。Because yeah。

 that's what's worked like the mem copy is the key thing that makes it faster。

So the second example is slightly different。 Now， I don't have a second Fl map。

I have a vector int for the new keys。And vector double for the new values。 And now。

 instead of inserting the second fly map into the first one。

 I want to like to insert all the new keys and new values into my fly map。How would you do it。Well。

 don't use a full loop。 That's quadratic。So to use insert range。

 you need to have a range of pair like things。 But here we don't have pairs。 We have vectors。

 yins and vector doubles。in C purposese 23， we have another range adapter called View zipip。

So it was this view sip。You can。 it can zip multiple ranges into a single range that provides a tuple or pair like。

Elements。So what you can do here， you can just say。Im doten Sir Ra views zip New New key。

 New valleys。And because Z view iterator is naturally a product iterator。

 because Z view naturally zip multiple ranges and Z view itator。Naturally。

 aggregates multiple iterators。And because they model that concept。

 you benefit from the same optimization of the insert range。And you will get the same optimization。

And same performance speed up。That's also。echochoes。Beyond this point of generic programming。We do。

 you you do generic mappinging， based on concepts。So， the key。Message I'd like to share here is。

When you use standard library or containers， try to use the most precise API。

 So when you would like to insert a range of elements， There is an insert range。

 You don't row your own full loop。And if you know your inputs are already sorted。

 you can pass the sorted unique tag so the library can skip the sorting step。And also。

 try to use the library facilities like use zip instead roll your own zipping mechanism or write of。

Like lockstep for loop or whatever。Because if you use library facilities。

 you're going benefit from the library optimization。Concept based optimizations。ok。

Before I move on to the next example， do you have any questions？Right。Okay。

So now I'm going to move the topic into testing。Testing standard library is quite different from testing application code。

Becauseuse the standard library implementation is。We have a very， very， very clear spec。

 That is a standard spec。 there's very clear requirements。 And also we don't。

 the risk of having a bug is too high。We cannot change our A BI。

 We have to maintain our A BI stability。 And sometimes if you have a bug and if you need an A BI break to fix a bug。

 we might， we might opt to just live with the bug forever because a。

Like changing the AI cost is way much， way higher than just having a。Like small impact bug。

And that's why we test almost every single word in the standard。I'm gonna show you an example。

 That's a snippet of text I copy pasted from the standard。

This is the move constructor of the stood expected。

And got lots of text underneath and like a declaration on the top。

What do you think as a library implementer， what do you think we should test？Any suggestions？

Contrain exactly。 we need to test when the constraint fail， the function should be spinningned away。

As I said， we test every single word in a standard。 So for example， the first word is constant Exp。

 We need to make sure this function works in the constant expert context。

And this is a move constructor。Because as a constructor。

 the absence of the explicit keyword is also tested。And there's a no except specification。

 We need to make sure。The no accept specification match the standard。 So why。

When the condition matched， and it is no except， otherwise。It can throw。We got effects。

 We got pro conditions。 We got。Exception specifications， everything needs to be tested。

I'm going show you the first example about how we test cast Exp。

So the way we write tests for K Exppo， is very simple。We just write our constant Expo function。

Which returns a bullolean。And we' we're going to just write our normal test points。

 So like what you do in your normal union test。You you exercise your function。 In this case。

 we exercise the move constructor。Then we check the results expected。

And we're using like vanilla As ma because this macro is blessed。In the exp context。

A third macro is only a constant expression， only if the thing inside the parentheesis is true。

So if it is the thing， if the thing inside it is false， it will generate a non constant expression。

 then the compiler will complain if you use this function in a cost expert context。

And then in the main function， we just run a test like a normal function。

 so that's how we run a usual runtime test。And then we call static a third with the same test。

So that will run the test in the context expert per interpreter。So this way。

 we can share the same test between the compile term time and run time。

So you don't need to write separate function testing unit test for your accounts Exp。Implementation。

 you just use the same same tests。And now let's talk about testing constraints。

Constraints is keyword in a standard。 it can translate to requires。So for example。

 this is a move constructor， there's a constraints。

That the underlying type needs to be more constructable。

So if there is a violation in the constraints， the implementation should fill out this function。

 so this function should be wiped out。And to test that is quite simple。

 You just write some negative case。 So I write a fool， which is not move constructstructible。

And then you can just write some static assert， either with some concepts， help or concepts。

 So you can So all we need to test is to test that when this is violated。

 this expected move constructor doesn't exist。RightThe way you test it。

 you either write a concept saying。Move construct exists， then your extraction is a move constructor。

Or there's already a standard trait called I move constructable。 So in this case。

 we can just use that traits。To test that this expected function no longer exists when it is violated。

And for testing mandates。嗯。The mandates keywords is slightly different from the constraintsstrain keywords。

So the mandates keyword means that if a violation in the mandates is guaranteed to generate a diagnostic in the form of the compiler。

So the mandates translates to static assert。Right， so if you we violate this constraint this mandates。

The function still exists。But if you call it， you get a static third failure。

Does that make any sense， right？So to test， static assert is very different。 We can't use。

 we can't use concept concept to check the existence of the function because the function always exists。

And we effectively need to test that if you write some code that violate the mandates。

 we should test that this code should not compile。And this is not something we usually do in an application code。

Right so only in the library implementation， we need to test。Well。

 we need to emit static assert at the right place with the right error messages。

And the way we test that is that。We write some code that doesn't compile， shouldn't compile。

And we write a comment with some keyword， expected error R。e。 or something with a regular expression。

Of that expected compiler error messages。And Klan has some magic。 We can past some。

Compile a flag to Kan， and says。Dash cllan dash verifyifier。

 What Klan would do is that it will try to compile this code。

And match the compiler error messages with your regular expression。If you match， compiler is happy。

 if it doesn't match compiler with image errors， so that's how we test static Ass。

In the standard library。And now， for the preconditions。

And precondition violations in a in the standard is pure undefined behavior。

 So if a user writes some code that violates a precondition of a standard library function is up to the user。

 The user can get anything。Like， can crash or do some random stuff。But as library implementer。

 we would like to help the user to diagnose the error。

 diagnose the error in some debug build on some other。Built。

 so preconditions or hardened preconditions translates to assert or contract assert。

 Some of you might attend， might have attended， help start talk about contracts。

 So contract assert is。It's one year's case is for preconditions or some other certain macros。

Or some preop post。And to help the user to diagnostic the error。

 So if the user happened to debug build their program and they will see。

And they will see some assertion failure instead of some random error messages。

So the way we tested our own assertion is that。Well we can't really test it nicely。

 We need to test because it's purely run time。 We need to test。

Some code that violate the preconditions that will emit an assertion failure break down your program as expected。

As the way we test it， we have another macro test lip CPP assert failure with an expression and expected error messages。

So what this macro does under the hood is that it will install the searchion handler。

And then it will f the process。And then it will let the child process to run this expression to fail and trigger the assertion。

And then we check the standard error of that chart process。And then we match that。

 the error message with that chart process。 So that's how we test。Asc sessionession failures。

So the takeaway of this testing is that we。Share the test from the compile time test and runtime test with a simple constructs for function。

And we use negative tests to ensure things that failed as expected。Right right， so we。

If something fail， we don't just， just fail。 We， we need to make sure that it fails in the expected way。

 produce。Either a static assertion compiler error messages or a runtime assertion failure。And lastly。

 this compiler flag is very useful to test static As。Ku。So I past it。

 if you are interested to contribute to Liy purpose， it's an open source project。

And we have a clear documentation about how you can contribute。

And we also have a Github issue link where you can see all our existing bugs or unimmented papers or issues。

 and you can start to pick some simple ones。And lastly， Q R T is a hedge fund in London。

 and we are constantly hiring。 We've been using C purpose extensively in the house。

 And if you're interested， can check our website or talk to me and。😊，Yeah， so that concludes my talk。

 Any questions。

![](img/cfccf7a3f8642eabdd03da4e0cd77753_5.png)

Yes， please。Yeah。very。This may be a silly question。

 but when would the same test fail at runtime save but pass in the context or context。

 like with the same inputs， when would that happen？

Because sometimes we have a different code path in a constant for code path。 If youre aware。

 theres an if constant vow。Yeah， and we've been doing that a lot because there are lots of things we can't do at compound time。

 For example， for typeurasia。We usually allocate a memory for Charles and reinterpret cast into some object。

 which is not allowed in a context per time。 So there are different code paths。So it's possible you。

走。Yes， please。So do you have any testing process for AI compatibility。We actually do。

 but it's not thoroughly。 We have a list of symbols we export。

 and we just make sure all the symbols are the same。Yeah。

 test for like argument type either done type or anything。 I just relied human record review。Well。

 we have。Not really， I mean。We have a concrete unit test， like with a list of symbols。

 we make sure the dynamic library contains these symbols。Exact same symbols。 And also。

 most of our library implementation are had had only 90%， so。They're mostly in a header。

 and we have some A B， I tag to tag every single function。 So every release。

 each function will have a different symbol name。So that's how we work around A issues。有 problem。Co。

はい。啊。Something like this was earlier。 but how is is it to integrate with that that optimization for segment datas。

 I have a venture of。Still array， for example。Yes， well I get。Oh， I'm sorry。

 I think you already answered this from Judge but a veterantro vectors， yes。

Suppose I have a custom type， Yes， that is like a veteran， yes。Yes， so。Our concept is。

 is a is there is an op mechanism， so。Unfortunately， that is you you can， like if you。

 you need to implement some traits to tell the traits how to unwrap your iterator。But， however。

 these traits are double on the score prefixed。 So you would。

 It's like a library implementation detail name。 You wouldn't know that。So， so in theory。

 you can in implement the our trays for your own type。

That you would benefit from the same optimization。 But that that name is start with double underscore。

 so。Its up like for one， you don't know that name 2。It's undefined behavior to。

 to use name with double underscore the score。So it happens to be like a veteran race。

I you expose it as a span of asing？They kind of get the same time because it's Spanish student。Yeah。

 I mean， if it is a standard library type， it will likely get the same optimization。要 problem。

Al right， I think。No more questions。Thank you very much for your time。



![](img/cfccf7a3f8642eabdd03da4e0cd77753_7.png)

![](img/cfccf7a3f8642eabdd03da4e0cd77753_8.png)