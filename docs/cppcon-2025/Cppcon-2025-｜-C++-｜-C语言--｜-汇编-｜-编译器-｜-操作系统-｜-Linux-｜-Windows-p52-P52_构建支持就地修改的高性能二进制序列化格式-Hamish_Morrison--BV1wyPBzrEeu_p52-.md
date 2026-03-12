# Cppcon-2025-｜-C++-｜-C语言--｜-汇编-｜-编译器-｜-操作系统-｜-Linux-｜-Windows-p52-P52_构建支持就地修改的高性能二进制序列化格式-Hamish_Morrison--BV1wyPBzrEeu_p52-

🎼The other conferences that I attended。

![](img/aeee70cdae16e7f39b4955b06c4d7a71_1.png)

🎼I would say that they've been pretty straightforward where you attend the talk and then it's kind of over。

 take a break and you go to the next talk what's really unique about CTP content is the fact that after the talk is done。

 it's welcome and encouraged to engage in dialogue with both of presenters and other attendees。

All right。Hello everyone， I'm Hamish。

![](img/aeee70cdae16e7f39b4955b06c4d7a71_3.png)

A software engineer at Bloomberg， and I'll be presenting on。



![](img/aeee70cdae16e7f39b4955b06c4d7a71_5.png)

On building a high performance binary verization formats within place modification。

So so just to start off， I'd like to give a definition of urization。

 So I'm saying that if you have a data structure and you want to say kind it over a network or persist it to a file or to share it between processes essentially。

You're going to need to turn it into a sequence of bite。And then on the other side。

 you're gonna have to turn those bytes back into the original data structure again。

So an example of a data structure is this one。It's a trade because I'm in finance。

 so kind of makes sense。 So how do I stize this。Okay， does anyone got any。Problem with this。

Anyone can see anything that could go wrong with this。Yeah， Chris。Yeahep。Go padding bites。

Just go back to the original。Type， it was this。So anything else？Yeah， exactly。

 alignment could be wrong as well。 I guess that ties into padding bys as well， yeah。Sure， exactly。

 Yes， it's even more deep kind of problem with this。 Yeah， yeah， perfect。

 So by just for the most kind of。IsIple problems with this， I've said。

I've said the endinginess is a problem。 So on different platforms。

 these types could be in different by orders。 So are they like。

' either like a big engine or little Indian。And then the size of type is a problem as well。

 So on different platforms along could be a different size， for example。 And then at the end there。

 you can have some padding bys in between your strings and your last unsigned flags there。

 now typically。Be two padding bytes， but it could be different on different platforms。

 So here I've got a better version of this code。 So I'm taking each member of one by one。

 I'm swapping it to network order。 And then I'm just writing it into this buffer。

And then each time I increment by this size of that type。So， it's better， but it's still not great。

 still have a lot of boilerplate here。I have to have my earn and receiving code have to agree exactly on the format。

And evolving the schemeche is' not possible。 So， and it's also not easy to see how to encode like more complex kind of nested documents like maps and arrays and that kind of thing。

So like how do we improve on this。 So two broadbased approaches we can use our schema based approaches and schemaless approaches to in a schema based format。

 the receiver has to know something about the shape of the data in order to make sense of it。

 It has to sort of like sort of see some information about how it's encoded。

 and then in schemaless standards and receivers can share data without having to know anything about its format。

So in your typical schema based format， we define。A type is's usually in some kind of DS SL。

 So here's an example of my tradestruct。As a proto bus message。

So often you use these DS SLs in order to generate code as well you generate classes that can access these in。

 in A plus plus Java， Python or whatever language you're using。

And the sender and the receivers made to agree on the schema to an extent。

 but they don't have to agree 100%。 So I'm still allowed to evolve this in some ways。

 I can add a field， for example， and that won't break existing receivers。嗯。On the wire。

 it typically looks like a sequence of tag and value pairs。 a bit tag。

consists of the field numbers that's a number that's given on the right and the DSL after the equals。

And then the actual value itself， as you can see here， it gets turned into a sort of。

A sequence of these pairs。And then almost every field is encoded as this variant type， which means。

Of favorable length。Integer。So， yeah， as you can see this this format is somewhat self describing。

I converse through it without knowing the exact schema。If I want to make sense of it。

 I need to know a bit more information about it， though。

If I only saw the like fields on the right here， I wouldn't know like what the field names were and what。

And what the original types of the original message were。

So what if I don't know the shape of my data up from， So， you know。

 I just like wanting code anything。 And I potentially。And I potentially。

 one think would arbitrarily complex documents as well。 I want to have maps nested in arrays。

 nested in maps and so on and so forth。If I need that， I'll need to。Move to a sche of this format。

 So in sche of this format， you can encode anything at all pretty much。

And like you usually get some kind of like。嗯。A dictionary style API。You can。You can set fields。

 You can get fields。and so on， and so on。Examples of Sless formats include Jason， Beesson， Me pack。

 feebo， Flex buffers。 And there's a ton of them actually。

 And what these have in common is they usually encode the data as a sequence of tag and value pairs。

 not always， but。but it's quite a common enco。So here's an example of a document encoded in both Jason and in Messp。

On left hand side， you have Jason on the right， you have message pack。 As you can see on the right。

 you've got these tags in green and the values in blue。

So this tag 84 means I have a map of four elements。

Then this tag A 5 means I have a string of length 5， and it's followed by the string price。

And then there's the value 100。And then here have a string of length 6。 It has a value of volume。

 and then tags E D means it's a u 16。 And that's my value。5000 after that。 So as you can see， these。

 these taggged formats are pretty creative about encoding。A lot of information in a small space。

 So in the previous example， you can see that my integer 100 actually doesn't have a tag on it。

And that's because if my integers are less than 128， I actually just store them as themselves。

And they happened。And then all other tags must have the high bit set。

 So it's possible to know if it's a tag or if it's an integer， that's less than 128。

And they also include true and false as a single tag and so on， so。Yeah， a question I want to ask is。

 like， what's the cost of using a sless format。If I have a message and I want to be able to read it and operate it and change it in some way。

 I I usually need to decode it into an in memoryory data structure first and then make my changes and then like re zeroize it into the packed form。

what if I want to avoid this。嗯。If I'm doing a lot of these。嗯。好。Operations every second， I might want。

And like， for example， to like， pull a document out of a database and make some。

Small and targeted changes to it。And then write it back into the database。

 Or let's say I'm like receiving messages on a stream or something。 And I want to just like。

 pull a single field out of each one of them。In this case。

 I might want to be able to do this much more quickly without having to re serial my document every time。

I thought it'd be kind of interesting to try and build a stimulus sterilization format where you can change its contents in place without having to re sterilize it。

So yeah， in the rest of the talk， I'm gonna， I'm going to show you how I tried this。

So so the first thing I want to try was to build a baseline。 So a very simple kind of format。

 which just stores everything as a sequence of T value pairs and makes its modifications in the。

 you know， in the simplest way possible。And the purpose of this was to build as sort of like a baseline to benchmark against。

 really， sort to have a point of comparison。 and then。And then is something to optimize and improve。

my baselines， serialerilization format。 I created one that supports strings， ints， floats。

 maps and arrays， itss encoders。As a sequence of tag value pairs。

The tagging encodes the type and the size， if necessary。

The values are a little endian to be friendly to modern CPU use。

Our maps are encoded as a sequence of key value pairs。

And then our arrays are just encoded as a sequence of values。 So it's pretty simple。

And our interface is going look a bit like this。 So it's pretty similar to why I showed have previously。

 And we have a bunch of accessors at the top to access the current build as various types。

Then you have a bunch of， I guess， like。I guess like muttators。

 so you can turn the current zoom value into an array or turn it into a map。

You can assign a value to it for some kind of primitive type。You can alsoend to an array。

 you can set a key in a map。And then at the bottom of the accessor is if if your value is a map or in a rate so you can pull out a。

A key in value。 if you know， the key。And then if you're in array。

 you can pull out of value at a certain index。So to implement the common operations。

In order to implement and read。I just implemented it in the most simple way possible。

 So here I have a document on the left， and I'm going do the code on the right to it。

 So I create a value。I try and get the timestamp balance of it， and then I return it as an integer。

This how the code is just going to iterate through all these fields 1 by one until it finds a matching key。

 It's going to find times stampamp， and it's going to return it as an integer to the user。

 It's just a simple， linear scan through the tags and values。And then to make modifications。

 we're just going to modify everything in place。So in the quote on the Right， I find price。

And then I turn it into a map， and I set it， I set it Mantisa and exponent to be these values。

 So I loop through my container。 I find price。I replace its value with a map。

And then I start to insert these new keys into values into that map。 So I insert Mantea。

I am sorry size。I'm sorry， I exp。 And then everything else has to move。And down each time。

 So it's quite expensive to make a modification。 everything else in the buffer has to move。

So how does this perform？I created a simple benchmark。And I parameterized on a bunch of stuff。

 So I parameterized it on the number of fields in the document。

The the number of operations we perform in a row。And。

And the percentage of operations that are of different types。So like how many reads。

 how many writes and how many。Of what I call structural modifications and structural modifications are simply either adding a new key to a map or removing one。

 And then rights are just changes to existing values， basically。So。

 so just a bit of information on the benchmarkings is I used。

I used I used this machine described here， GC 13 all too March native and so on。

 used a machine on which I didn't have too much load。

And then one thing I want to say is that all these benchmarks are， of course。

 micro benchmarkchs is oh they're subject to all the problems where， you know， in production。

 it may work completely differently I' not tried this in production at all yet。 So yeah。

So here are the results from my baseline。You can see that we do about a million reads a second on very small documents。

 and then we get progressively worse and worse and worse as you add more fields and as you do more write。

So I've got a low scale as well。For the most number of fields is a good maybe two orders of magnitude slower than the small number of fields。

 so it scales extremely poorly。And that's kind of what we hoped for it。 It was like， you know。

 it's like a baseline。 It gave us lots of room to improve。So the first question I asked myself， oh。

 actually， yeah。Actually， one thing I want to do as well was to。

To compare it to how much it would cost to simply keep all of my data in a map and then periodically re serialize it。

 So on the green。Is a benchmark in which I yearized after every operation。

 and then red has after every four operations and on blue its after every6 Dean。As you can see。

 it's slightly faster than serialerilizing after every operation。

 and then it's about half as fast as。As eraizing every four， again， it's a log scale。 So。

 and then it's about maybe a fifth。As fast as is sterilizing every 16 operations so。Yeah。

 if your like requirements， let you say， like make a bunch of modifications and then only reseialize after a whole bunch of operations。

 it would still be faster to just keep everything in some like memory data structure and just like resealize it。

So yeah。For the next question I asked myself is， how do I make？The search is faster。So on profiling。

 I found that it spent a ton of its time just looking at like what's the size of these various elements in the container。

So about 60， 70% of the runtime， or at least of the CPU titles is going on that。

A lot of time in the searches is basically spent skipping over elements I'm searching for a certain key。

I essentially just need to keep on skipping over elements until I find it。

 and that means I had to keep on checking for every element。How big is it， basically？

So one idea I had is kind of put my keys into sword order。So I take these two keys。And I swap around。

AndNow if you ask the question， can I do binary research， you'll find the answer is still no。

 unfortunately， because my keys and values are variable size here so。My keys and values。

Are like not a regular size。 It's very hard to jump to a certain element。

 as part of a binary research。 I need to jump into the middle。So an idea I had to sell this was。

To store a table of offsets at the start of the map。 So essentially， I take my map。 and at the top。

 I put a sequence of offsets。Of which order do the elements are supposed to appear in。

 So in this case。I'm basically saying the Kia offset number 6 comes first， and that's。The key。AA。

And then the key B comes next。 and then the key C comes last。

This means I don't need to store my actual elements in sword order。

 I just need my offsets to essentially put them in sword order。So after making this change。

 we perform a lot better on the searches。I would like to compare this to the previous 1。

 I just might create a more。Kind of。A more specific benchmark just for this。 And it wasn't。

It was just was doing less work than the previous benchmark。 So it was a bit of an unfair comparison。

 But you can see here we're doing a lot more operations a second on the smaller arrays。

 It still scales pretty poorly。 as you go down to larger arrays， you're doing a lot less still。

So yeah， and idea did that I had after that was， what if I put a。嗯。

A list of hashes of my keys had the start of this map， as well。essentially like this。 So if I put。

An array of hashes of my keys at the start of the map。 I have a smaller array to search。

 It's just an array of units16 T。 It's quite easy just to loop over this and find like my hash。

 And then I know which offsets out。 Of course， I could have hash collisions。

 And I might need to check multiple offsets， but。It's a good bit faster。 So if I add hashes。

 I get about a 20% improvements on the smaller containers。 and then on the large containers。

 I actually get quite a big improvement。 So I'm almost doubling the speed there。😊，So I asked myself。

 can I do even faster than that， Perth。I profiled these these search rating。And I found that。

It's spending a lot of time on this instruction in the middle of the lower bound。 So in lower bound。

 you got a check in the middle to see if you should go to the upper half of the array or to the lower half of the array。

 And it seems that in this check。He's spending a lot of time。

So my guess is that even though it's attributed all this cost to the instruction sub。

 it's probably attributable to to the branch that's just above it。So if you think about it。

 it's almost impossible to predict this branch just because every time， you know。

 I want to narrow down my array to a half of the array， it's pretty much unpredictable。

 which way I would go if I could predict it。I wouldn't need to search in the first place， so I。

Oh the misproded branch is this one here。haveAn idea that we can use to work around this。

Is to use a conditional move instruction， which which people sometimes call branchless programming。

 So I had the idea of using branchless binary search here。

And the idea of this is that you essentially。if you keep the contents of your statement down to a single assignment。

 the compiler is much more likely to replace what you've done with just a conditional move instructions So instead of having。

A branch in the middle of your loop， you know just。Have have a conditional move。

And this conditional move， essentially。It's。It's not gonna like。It's not gonna， you know。

 it's not going to be predicted either like one way or the other。

 It's now like a data dependency instead。In this article。

 I actually took this implementation from this article。 in the article。

 they actually take this sort of like predicate of， of like base half as less than key。

 And then they multiply it by half。 and then。And then the increment based by that。

I think that was a kind of like an older trick to make the compiler。I meant to sea move instruction。

It seems it's not necessary and more recent compilers。

 And I was able to just have an if statement in here。 and it works just the same。

So after making this change， I know。And the assembly I now have this nice theme of instruction。

 and then most of the cost is going on the comparison instead。Yeah， and as a side note。

 I also like went down a bit of a rabbit hole on searching， I found this great blog article as well。

 which I'd really recommend adding a number of implementations of different kinds of searches。

So this one vectorized counting linear your search is basically that you。Like。

 you have a loop in which you run through the entire。Aray， and you count。

How many elements are smaller than your one？And then at the end。

 like your result is your index of your position。It's nice and。It's nice and elegant。

 and it doesn't have any branches in the middle。 So it's completely branchless。

At the cost of having to run through the entire array。 So it depends on how big your array is。

 If it's tiny， it's really good。And then just a vectorized standard linear search。

 which is like loops through a lot of elements at the time。

 And once it finds the element it' looking for， it just breaks out。yeah， it's a great article。

 I'd recommend that one。The comparison of all the of all the search algorithms I tried is here。

 So I'm counting A V X， which was the counting search is actually great if you have small arrays。😊。

As you can see， it gets slower and slower if you have more elements。And then in。

then in red is my branchless binary research。And it's pretty consistent even at the like really large array sizes。

Which makes me prefer that one。 So I went with branch this here。And after that。

 I'm pretty happy with the search performance I moved on to the question of how do I make modifications faster。

😊，so in our baseline format， we perform modifications by just moving everything around in the buffer。

And now we've introduced offsets。 It's a bit problematic。Can anyone see where that is？Yeah。

 you to update yeah， exactly。Yeah， each time I date anything in my map。

 I now need to like run through my offsets and update all of them。

So if I were to take this int value， which is the value of key B and turn it into a double。

I'm going to increase its ties in the process。 And the two elements afterwards are going change position。

 And then I'm going have to。I'm gonna have to go into my offset array and change the positions of these offsets。

 So the。6ix and 13 are going to need to change into a tenant。And so it's1 in 17。

And you might think that's not a big deal， right， I can just like run through this offset array and conditionally update ones that。

Are greater than the offset of the al are changed。And it's true。

 But the real problem comes if the map is nested inside other maps。

 So to understand why it's a problem， I've created this。

 So it's sort of three maps nested inside each other。 So here we have A。

 and that has another map inside it。 that has Q B， and that has another map inside it。

I've kind of color coded them Well the document on the left has the has the same colour as the encoding on the right。

In this case， I was to go and update the the end at the key C。And turn it into a double。 I've now。

Changed the offset of D。 And the problem is， D is stored in a map。

 that's actually a few parents above my current map。So now， if I have a large amount of nesting。

 I have to somehow do some kind of like walk up all my maps and update all offsets as I go。

And that all leads me to。You know， either store parent pointers in my maps to be able to track through and locate my parents。

 or I need to track through like which。By what path I've taken like through my document in order to find my current element。

And if I add parent pointers， I'm going have to solve exactly the same problem for my parent pointers as well。

 so。I decided not。I decided not to do that。 And instead to move elements out of line if theyre containing elements。

the idea here is now my offsets can point it。Anywhere at all in the buffer。

So here I have my first map is now pointing to my second map。

 which happens to be the end of the buffer。 And then that's pointing back to the to the third map。

 that's kind of in the middle。 So now， like my offsets are now expressing how my nesting works。

 essentially， and my offsets are basically just become small pointers at this point。

When now I have pointers。 I need to answer a question of how do I allocate space for all these elements。

So。I potential idea is to implement a bump pallicator。

And the idea of a bump allocator is that you keep a pointer to to the first bit of free space in your buffer。

 So here I start out with an empty buffer， and my bump pointer points to the start。

And I allocate a map， and my free space pointer is now bumped up and points out after that map。

AndThen I allocate a key in value。 And now my free space pointer is pointing after that。

 now my map is also pointing at its value that I continue within it and I allocate another key in value。

I keep on increasing my bump pointer。Right if I。If I now want to allocate another key in value。

 put it in my map， unfortunately， my map has now reached its capacity。 So it says to out to there。

If I want to allocate another map， I'm going to have to allocate another one。So that's going to look。

Like this。 And now the free space of my original map is now wasted。

 So I can now allocate my other value， and I can put it into my map。

 and I've got a of I've got a bit of wasted space at the start。Of my container。So。Yeah。

 clearly so clearly in the strategy waste a lot of space。Eventually。

 I'm going to need to compact my entire buffer。 I'm just going to run out space。

So how can I improve on this an idea that I had was to add a free list into my container。

 So basically， like thread a free list through all the free spots in the container。 and then。

And then preferentially allocate from that first。So a freeist allocator is gonna look something like this。

 I'm going to store elements in my map that basically tell you how much free space is at that point。

 So here， my free list starts with a single element。

And the free size basically encompasses the entire container。 So I've got free size 100。

And then each free list entry also has to include a pointer to its next entry as well。 here。

 it doesn't point to anything。 So just as next is。Its0。

So how this would look if I was going to create a map。I'd create a map。

 and I would carve a bit of space out of my first entry of my free list and then reduce its size。

 So now size is 88。 I have a map。So I can add keys， I can add key AA， and I can add keyB。

 and now I just keep on like taking a chunk out of that free spot。And then， here。

I've got to the point of need to allocate a larger map。So I carve a bit of space out my free list。

 and I leave free size 47。And now what I can do is I can put another freeist entry into the space。

 I just readed up。So now I have free size 12 at the start of the container。

 And now my free list is pointing there。 And then that's now pointing to my。

 to my last freelist entry at the end of the container。And then I can allocate my C in there。

 instead。So I can use space a little bit more efficiently。

 there's a couple of algorithms you can use if you're implementing an algorithm。

If you're implementing an allocateator， actually， there tons I've only listed to here。

 but I tried doing first it， which is where you basically take the first block from your free list that can satisfy your allocation。

And then， I did。And I also did best fit， which is where you take the smallest block。

 which can satisfy it is sort the best fitting。And then I benchmark both schemes in terms of performance and wasted space。

In terms of performance， you can see that the first fit starts off performing pretty well。

 And then as you do more operations， it starts to perform worse。 So it's kind of as you expect。

 you know， as your buffer just gets more fragmented and you keep on sort of taking chunks out of large blocks and leaving irregular sizes left。

 you get may get more and more fragmentation。On the other hand。

 it seems that best fit is getting faster， which。Is kind of strange。

 And I suspect that it might just be just because。After performing a law of operations。

 a law of the container is in cash。I don't think it's actually improving in complexity as you do more operations。

And then with first fit， though， you can see that the space wastage is absolutely massive。Yeah。

 after doing 16000 operations， you're wasting about 40% of your buffer， which is a lot of space。

And then if you are using best fit， you're only wasting about 16， which is still maybe quite a lot。

 but it's not as much。So。Yeah， I was curious to profile this and to see where all the time is going。

And in the free list。Like walking algorithm， It essentially spends a lot of time grabbing the free space and the current entry of the free list。

 We're just looking at how much free space is in that entry。

And you can see a lot of the time is being spent on that mo。

 which is the reading of the free space size。An idea that I had then was what if I can prefetch free list entries as I walked through the free list。

So， in。In my freeist walking thing。 And this one， is's the first fit one。But is this first fit。 Yes。

 it' first fit。 So yeah， essentially at the end of the loop and at the start of the loop。

 I prefech the。I prefetch the， the entry I'm about to look at。And you might think， like。

 why would this make anything faster， I'm just about to read it anyway。

 And I suspect what makes it slightly faster is that。It can。

Is that it can do this in parallel with checking if the free list offset is not equal to 0。

 so it can be free。And can be prefeting that and doing this comparison at the same time。

 And then if it turns out that the freest offset was equal to。I。What was equal to zero。

 I've just done a harmless prefech of the star of my buffer and the star of my buffer just has like a header in it of the like free size left and the free list pointer and so on。

So after implementing that， I get about a 15% performance boost if I'm using best fit and I get no improvement at all if I'm using first fit。

I guess， in。And first， it's likely to find its element pretty quickly， so。

It doesn't benefit too much amount the elements prefeched。So。Yeah， after doing this。

 I got quite excited。 and I started to。I start to throw in prefetching around the entire color base。

And it didn't make any improvements anywhere。 In fact， it just made things a lot worse。

 So I'd recommend not going wild on prefeting And really。

 like you only want to use it if you are prefeting an address that's very likely to not be predicted by the compilers in the freeist case。

 you have your freeist entries are scattered。Are scard throughout your container at random addresses。

 So it's completely unpredictable。 And it kind of makes sense。 But like if you're。

If your access is predictable， it's not going to improve anything。

Actually it's going to make it slower just because now you have an extra instruction linear I having to do。

So after doing these optimizations， I was pretty happy with the performance and modifications。😊。

And I decided to do some final benchmarking。 So so I decided to benchmark against it。

IAgainst the baseline format that we made at the star and then against unordered map。

In the unordered map version。I have two levels of nesting of unordered maps。

 just to replicate how my container is being used。It's because I'm creating like。

I'm creating like maps inside maps in my benchmark。And then our leaf values are gonna be。

Varianance of int， double string and vector event。And then I used heterogeneous look up on the map to make a nice fastera And I use the same hash format as my。

 as my format is using。the same hash functions are。And I also tried。

I also tried benchmarking against the flat hash map from Abail just because I suspected it could be faster。

 but it ended up just being slower in every benchmark， so。I think I might。And might。

I might be missing a bit of a trick there。 So I just stuck with unordered amount for now。

So in terms of performance。And read only workflows。 It looks like this。

 So our an optimized format is doing about tell me。And， and， and 10 million reads a second。

Which is pretty similar to an order map。 Then our baseline formats in order of magnitude slower。

And then as we increase the number of elements in the document， we only get slightly slower。

 And then our baseline is not even appearing now just because it's really slow。 So at the yeah。

 on the large number of elements， it's about two orders of magnitude faster。不。It is pretty nice。

And then in the mixed operations workload， which is doing equal amounts of write。

 reads and structural modifications。It can do about 8 billion operations a second or close to it on this map。

On this benchmark， I wanted to show the difference between the first fit and the best fit as well。

 optimized F F is optimized with first fit。 and then opt optimized B， F is optimized with best fit。

as you can see， they're pretty closely matched until you get。

to the large number of fields in the document，Having about 1000 build in the document。

 it drops off quite a lot。I'm suspecting it's because it spends a long time walking through the free list。

 and trying to find the best fit。So that's also great。😊，So， yeah。Those number。

 Im a field it'spar to use first bit， although。Although， as we've seen in the previous。

And like benchmarks， if you're using first fit， you're also like wasting tons of space in your container。

 So its go， it's trade offs。So yeah， in terms of limitations， as you can see。

 if you're using first bit， you've got a problem。With fragmentation。

 And then if you're using best fit， you're actually getting slower as your document gets larger。

I was trying to figure out if I could find a middle ground between the first and the best fit。

In practice， I've not got that。the，ar。They might involve having like multiple free lists and having like free lists for small items and medium size and large items。

So yeah， and then the other thing as well is that， is that because of the added metadata。

 we're actually having a bit of overhead and per key in value in our arraysin maps。

 So if you're in a map， you got an overhead of 4 Bs per key value pair。And if you're in。

And if your elements in in it。And if you're element in an array， Is got an overhead of two bytes。

And the other thing as well， is that our format that we've created has a lot of offsets in it， so。

It would be pretty easy to make this cold go and read out of bounds if you wanted to。 So， so。

 so currently， I don't have any like bounce checking at all in this。So if you were to like， read。

I serialized document out of a file。 and it wasn't a trusted file or something like that。

 You could easily just go and crash。Id all the benchmarks in here。Are done with no bounce checking。

Yeah。So yeah， conclusions are we've created a pretty fast schemaless stization format。

 which you can edit in place。It compares pretty favorably to using unordered map memory。

And I guess the unsurprising conclusion is that if you basically create an allocator and then create all your same in memory data structures in a small buffer。

 you essentially are able to match your in memory data structures。 So yeah， it's。

It's kind of unsurprising， I guess。So yeah， I guess all conclusions to take from this is that if you're trying to improve performance。

 I'd recommend。Creating benchmarks that are highly parameterized。

 If you parameterize on a lot of things， you can spot how your code like misbehaves in like very specific kinds of scenarios。

 So， for example， having a lot of fields in the document or performing a lot of it or performing a lot of。

Or performing a lot of。Operations in a role， for example。And you should profile。

And then try to make algorithmic and。And data structure improvements。 And then， yeah。

 explore all of the， you know， like all the fun stuff， like， like。Like factorization。

 branchless code and prefeting and all this kind of stuff so。Yeah， in future work。

 I'd like to explore how to compact the buffer in place。

 So I think I might be able to achieve my higher performance in rights if I keep the fragmentation in the buffer under check。

 so。I was looking into a few algorithms from garbage collectors in order to do that。

 I didn't make much progress yet on implementing them。Yeah， another thing I'd like to explore is。

 is to build a format which doesn't have any offsets in it。

 So essentially a like a format where you would。create an index in order to search it on demand。

 So I was quite inspired to。By the S D project， I'm sorry。

 as is is is M D Jason project where they essentially。

And on reading the the Jason document for the first time， they essentially create an index in memory。

 and then you can use this to really quickly search it。And they use Duny heavily to make it fast。

 So it seemed kind of cool。 I wonder if the same concept could be applied to。

 to a binary eization format as well。 It could even just be a bit more friendly as well。

 like you wouldn't need to worry about things like， you know。

 I like a quote character appearing in a string or anything like this。

And then the other thing I want to explore was compressing repeated keys and fragments of keys in order to save even more space。

Yeah， a couple of like resources I'd recommend a lot the top one is this is a book that's available online。

 it's called Algorithms from Modern Harbor。It covers all this stuff in like extreme detail。

It's very useful。And then I started reading this book called called the garbageb collection Handbook。

 which is essentially how to implement various garbage collection algorithms。

And you wouldn't think you would necessarily apply in C plus plus。

 but it is actually extremely useful in forting an idea of like what allocation algorithms are out there and so on。

 I've not even scratched the surface of this stuff in what I've done There's tons more to do there。

And then I'd recommend this talk by Chandler Curruuth from E on 2017 called Going No fasterster。

 which I think was the first talk I watched that sort of explained how to I like how to benchmark and profile in a lot of detail。

 So that was very valuable。And then also， I hadn't attended it at the time of doing most of this work。

 But at start the conference， I attended the Do Pikes class on performance and efficiency in C plus plus it was。

It was exceptionally good。 So I'd really recommend that。 Like， I realized like walking out there。

 I thought。I thought， yeah， I'm not really qualified to give this talk now。 I， I don't know enough。

 So I highly recommend that one。 And yeah， I think that's it， so。So thanks。Yeah。

 anyone' got any questions。Hey， thanks， it was a really interesting talk。

 One thing I'm curious about。 I was actually a little bit surprised that you only have four B of overhead for everything in the map。

 So I was wondering like with only like 16 bit hashes。

 like do you have any idea how bad like collisions are in practice。

 And then the other thing I was going say is that I guess the total buffer length is limited to 64K Indeed。

 whoever offset in the buffer is encoded in 16 B integer it's only good for documents there are less than 64 kilotes。

 if you wanted to extend it to more you would pay for little by larger offsets and they have like more overhead。

 So yeah。😊，Yeah， and then your other question is about the hash collisions。 Yeah， no。

 I didn't measure it。 So I don't know。 mean， in the worst case。

 you have to walk through a few hashes and。And since they all appear in the same order as they appear in。

In the buffer， you could just like walk through all the hashes they were conflicting and check if the actual strings match。

 So yeah， yeah， I'm not sure that's a good question。 Yeah I should try and measure that。

 well one thing that I was going say so one thing that's interesting with only having four bytes for key value pair。

 I had done some work not too dissimilar from this in the past。

 and at really small like not necessarily small buffer sizes。

 but it's small numbers of keys it makes your offset storage really small and especially because you're using hashes here like unless you have a collision。

 you don't actually have to go look at the packet data And so what you can find is that at small numbers of fields you can get really。

 really fast performance because everything stays entirely inside of the offset storage until it has to actually go get the data to return to the So it's like in my testing can in my particular format I could have up to eight keys beyond a single cache line。

 And so you would have essentially identical performance for like the first eight keys and then it would start to significant。

rop off I see yes。And extension is this when your keys are particularly small and you can fit them into a small amount of No。

 So the idea here， the idea here is that if you can make the entire binary search algorithm confine itself to just the offset storage because you're working with hashes or something like that。

 So actually go look at the key data until you've already found your match essentially。

 So I was just going suggest that's another interesting benchmark case。 Yeah that's cool。 Yeah。Jers。

Hi， great， thanks。I was wondering you have added actually the list of offset and the list of hass because you are interested in searching and adding what if you're only interested of serializing and this youre as fast as possible recommend to have those list or just a key tag No I think if only if all you need to do is just write out keys and values as fast as possible I would just use a tag formats and none of this stuff So if you're just if you're just going to pin a bunch of keys and values into the buffer it's going to be as fast as it can be so yeah。

Hello， thanks for the talk。 I'm interested in your benchmark setup when you mentioned。

That you compiled with dash O2。 wondering why。OhI have to go back really far for that。To be honest。

 I just， each time I try 03， it doesn't make things much faster。 So I just stuck with O2。

 and sometimes O3 is actually made things a little bit slower， so。Y。

 it would be interesting to try with0 three as well， though。 So I should probably do that with。

I'm sorry。 Do you run in Prad with that World2 as well in Prague World2， yeah。Thanks， sure。H。

 that's a great talk question mostly related to like depend on the question， which was fantastic。



![](img/aeee70cdae16e7f39b4955b06c4d7a71_7.png)

Question here。 So if we only look for a search and not go into modifications。

 do we have benchmarks or did you benchmarks on how the updates work。十风 me having几分钟。

Updates through the map。Adding elements and not really of changing anything。

 So you don' need the previous or。No， I haven't， but yeah， I suspect it could be quite a bit faster。

Yeah。I think if what you want to do is just if you have a message and you want add。

And you want to write it out， then the fastest will just be append only and just write out all of your data。

Yeah， if you can avoid having all the other。All the others little。All the other。

 like machinery and stuff to make the searches faster and to do the freeless management。

 it'll just make things faster。No worries。I was just wondering。You said like。For the best fit。

 you have like not so good performance。And you said something like this， but just for clarification。

You， you have just one free pointer this basically where you point to the free space。

And your idea is basically to upgrade that multiple free space pointers to point to basically equally or kind of equally size spaces。

 That's the next step you want to approach right the best fit faster Yes。

 so basically keep say three or four free list pointers and then you would have a freeless pointer of say like space that's smaller than 16 bytes and then space that's smaller than 32 and then smaller than 64 and so on。

 Why do you not using the offsets have like basicallyh list you have like the offset list so you can also have that parallel to that and use the offsets sets as like the size Well my problem is my offsets don't actually tell me how large my values are just because those offsets don't all need to point to contiguous the allocated values。

 I could be pointing here here here right and I would say you know like offsets of like6 like 200。

And had a thousand or something。 It doesn't tell me that my。Like is it also including the conflict？

So that makes probably the problem， right。No， conflicts don't really play a part in this。

 Like in what way would conflicts。Impact this。 I mean， if you have a hash conflict。

 it's only in the array of hashes。 So it doesn't really affect like where， like where in the value。

 I mean。I mean， like where in the buffer your value is going to be。 So it shouldn't play any part。

 yeah。Thank you。对。Before implementing all the allocation logic。

 have you tried using a caching arena locator to see what would they would do because they're usually very good a handle in these kind of situations。

 Yeah， I'd say arena allocator if I'm。If I remember correctly。

 is pretty similar to a bump pointer allocator。 So it's roughly the same as the first one。

 I kind of showed。 But yeah， I didn't benchmark that one much。

 And one thing I want to explore is if I implement compaction。

 could I combine that with a bump pointer allocator and then have extremely fast allocation and then just periodically like pay for a compaction。

 So yeah。I'd like to explore that for sure。Thank you。 No worries。



![](img/aeee70cdae16e7f39b4955b06c4d7a71_9.png)

Hello， I have two question。 One first one is what are you con to choose the scheme of civilizationization。

And the second one have you benchmarked。Against other。四先诶十倍啊。没。So the first question。

 like what made me choose schemaless， I guess the sort of motivation for this whole project was that in our code base。

 we have a number of serialization formats that are basically specifically tuned。

For certain workloads。 So there's some that are just having， like a sort of。You know。

 by just a single map and you can put in a bunch of entries and then there are ones that basically provide you a sort of like array of maps and then there's ones that are just sort of like more like a schema based ones。

 And I was just kind of thinking to myself， can I create a thing that's， you know。

 essentially as flexible as all of them and then just replace all of them。

I which I guess is the classic kind of thing， you know， as a software engineer， you always think。

 you know， Yeah， and then your second question was， have I benchmarked against another。

Seerialization format， which， if I can scroll back far enough to the benchmarks where。

I compare against serialerizing， you know， every operation or every four operations or every six operations。

Which is going to take me A as wonder if it's faster on this one second。Yeah， much faster。嗯。

So if I start chose。Yeah， so here's the one where I compare against serializing every so many number of operations。

 and in this case I've picked a popular schemaless format to do this serialization。😊。

I don't want to name it just because it feels a bit unfair。 It's not exactly。

That's not what it was made for。 So I don't want to。

I don't want to sound like I'm like I'm comparing myself against。

Against them and calling them like slower or something。 So yeah。Thanks。All right， cool。 In that case。

 yeah。thanks for coming to the talk。 If anyone has any more questions。

 you can just catch me outside as well。

![](img/aeee70cdae16e7f39b4955b06c4d7a71_11.png)