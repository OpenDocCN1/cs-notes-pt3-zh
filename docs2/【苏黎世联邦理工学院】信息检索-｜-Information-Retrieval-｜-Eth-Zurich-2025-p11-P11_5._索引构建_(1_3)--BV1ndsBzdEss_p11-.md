# 【苏黎世联邦理工学院】信息检索-｜-Information-Retrieval-｜-Eth-Zurich-2025-p11-P11_5._索引构建_(1_3)--BV1ndsBzdEss_p11-

Welcome back， everybody。 I hope you had。A good break to digest everything that we've been doing。

Correcting mistakes。 and the spell checks。So now we have a new lecture， a new section。

 And before we do that， I will just repeat and repeat and repeat all over again what we've been doing。

 So， you know， this thing right here， it's called the standard inted index， absolutelysute beautiful。

 The yellow cells on the left are called vocabulary。

 They are enhanced with the data structure called the dictionary。 Then we have in the purple boxes。

 the。😊，What are the purple boxes。Yes。The length， yes， and what is it equal。

 What is the name for that。Document frequency， exactly。

 So we have the document frequencies in purple， which are the length， as you say。

 of the posting exist。 Then in blue， we have the postings， which are pairs of term documents。

 But as the term is always the same on the same row。 we don't repeat the terms。

 So we just put the document I D。 And the document that is are just the integers in that case。

 So that's the standard inverted index。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_1.png)

We saw that the vocabulary is enhanced with data structures。

 such as hash tables or trees like the B plus trees， the prominent example。

 We saw that we are able to fix spelling mistakes and answer our wild card queries。

 which is kind of related。😊，We did that with new indices。 One of them is the perm term index。

 where we rotate the world。 You imagine the world is written on a ring， and then you rotate the ring。

 having a dollar to not forget where it starts and ends。 Then you have the kgramms。

 also with these dollar sign。And here it's a sliding window of length K over the world。

 And we build indices。 We have the Lenstein edit distance to tell us how far apart two words are based on the edit。

 And again， that is exactly this what what is used for the deep algorithms except that its lines instead instead of letters。

 We have the jackard coefficient， which is a renmalized version of the count of the intersection。

 because we divide by the count of the union。😊，The sound deck encoding。

 which is based on a fingerprint of the world of the。

 especially focusing on the consonants that allows us to retrieve world that sound alike。

And that's it。 That's a very brief summary of everything we've seen so far。Questions。Zoom。

No question， either。No questions on Zoom。 Feel free to ask questions on Zoom。 it's easy for you。

 just have to write on your keyboard in the in the chat window。

 You don't even have to to speak in front of everybody。

 and then we'll repeat what what what you ask The great idea by the way to speak in front of everybody。

 This is why we have the seminar because the first times it's a bit difficult。

 but then you you get used to you get used to to it。 but it's still very scary to。 I mean。

 I cannot say I'm not scared of being in front of a lecture hall。 you remain scared。

 but it just becomes a bit easier with with in general on Zoom。

 the comment I made is that you can raise your hand And I'll tell you to wait。

 there's someone who wants to write something in the chat and they can have enough time to write it if needed。

 Yes， absolutely we'll give you all the time that you need to to ask your questions。um。All right。

So now we are going to look into performance improvements to build larger and larger and larger indices on larger and larger and larger collections。

Whenever you look at performance improvements， when you write computer code。

 because all of that is done with computer codes。嗯。You cannot。Not look at the hardware。

 You need to understand the hardware on which your code is running。 That means the hard drive。

 the memory， the CPU and so on。 And you have to have at least some high level understanding of how the hardware works in such a way that you can fine tune and improve your code。

There are plenty of hardware specialists and hardware professors at E T H。 I'm not one of them。

 So for me， it's a little bit of something I don't understand in all the details。

 but I know just enough to make my code fast。And so what I know。

 And that's the perspective of database people looking at hardware in this way。

 We know that there is somewhere the brain of the computer that has the CPU that is just computing stuff。

We know that there is some working memory that goes away when you switch off the machine that that the the that is used to store the all the intermediate values that you have when you compute and plenty of。

 of useful data structures。嗯。We have some disk， which is distinct from a memory just because if you switch it off。

 you still have the data。 So that's the durability of it。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_3.png)

And then we have the network that is especially useful when you have multiple machines and you want to。

 for them to communicate with each other。And what's incredibly powerful， because， of course。

 all of these things are very complicated。😊，But as a database person。

 it's enough to know you have CPU， memory， disk and network， right。

 We even like them so much that we have affectionate names for that。 We actually call that computes。

 So when you have people talking about the cloud， the clouds， they call that computes。

 That's computes。 That's memory and so on and so on， right。

 So this is this is the beautiful world of hardware abstraction for database。😊。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_5.png)

It seems very little just knowing these f things， but this gives you the basic fundamental on which you solve your bottlenecks that I explain more in the in the big data lecture。

 But whenever you have something that is slow in your system， you can blame one of these four。

 almost always。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_7.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_8.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_9.png)

Right it's one of the four that is responsible。 And once you have identified which one。

 then you can fix the the bottleneck。 So today， we have this in mind。 We have the hardware in mind。

 and we'll， we'll basically have the the， the， the。

 the look inside the machines to understand what happens。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_11.png)

I assume you kind of know roughly all this hierarchy of hardware。 So who， who is aware， you know。

 of the cache， the memory， the these， the tapes， you know all of that， right。

 So you know that there is here a specific order in in in the other of magnitudes on the。

 on the quantities that defined how fast you can read， how much it can store and so on。Alright。

 so let's look at these four levels of storage。The cache is a small amount of memory that is on the CPUU volatile time。

 You switch up the electricity。 It's gone。 The working memory is the same。

 And the disk and the types。 this is， the， this is what remains。😊，Tapes are still there。

 You might not know that， but E T H has tapes。 We， we make backups on tapes of your home directories here。

 and there is somewhere probably on the hunger bear。 I don't know if it's still there。

 some facility with the tapes and little robots that go and fetch the tapes takes a few hours to retrieve a backup。

 But they still exist。 And the reason they still exist is that this is incredibly cheap in terms of the cost per door bite。

 right。嗯。But the problem is that because it's so cheap。

 usually it comes associated with some drawback。 And the drawback is that it's very slow to read。

 because if you want to access the tapes， again， it's going to take hours to get them and put them on the tape reading machine and and retrieve the bys。

 But the higher you get the disk is going to be faster， right。

 it's going to be within some milliseconds， the memory even faster and the cache even faster because it's very close to the to the CPU。

 right， So the higher， the faster it is to to read。😊，呃。

But the problem is that just as much as the tapes are cheap， the cost per bys of per kilobyte。

Keeps getting higher， the faster you get。 So if you want to store a terabyte of data on the cache of CPU。

 that's going to be absolutely terribly expensive compared to doing it in on memory or on tape。

 right。Now。Once you know about this， the the the storage possibilities and every system。

 like information retrieval or reading data， writingri data。

 database system will use this hierarchy of storage layers and use them to the best that it can。

But if you want to scale things。And if you want to be able to index very large collections that keep growing。

 because every year we keep creating more and more and more books and more and more computer programs and more data and more web pages。

😊，You have to unoc a problem。That we have and that we have had for a couple of decades now。

 that's also a bit of preview of big data。嗯。We need to look at three things。

 The first one is capacity。 How much data can we store， right，600000 words。

 The second one is throughput。 How fast can we transmit the data， For example， if you read a book。

 it's100 words per minute。 And the third one is the la C。

 How much do you need to wait until you start receiving the data。 right。

 in the case of the book that would be to go to the shelf and take it， That's the latency。

 There are people who define the lat C as the time until which you stop receiving the data。

 Just be aware of that， I'm using it as when you start receiving the data until you start receiving it。

 So capacity。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_13.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_14.png)

Fhputs。Latency， these are the three。 and we followed them over decades。

And so if you look at the evolution of storage over 70 years。

 and you realize that the capacity increased absolutely enormously。

 the speed at which we can read barely in comparison and the Latin Sea don't even talk to me about it。

 right， This is absolutely catastrophic。And so the real， real。

 real big problem that we have is that we just have too much data and so much data。

 we cannot even read it fast enough anymore。 And everything， this。

Everything is driven by this limitation。 All the systems we built today when dealing with a lot of data are built。

 having this huge problem in mind。And so when you look at the capacity， for example。

 of these of these components。 So you see， we can get to the petabyte range on types。

 a few terabytes for this。 Now it's even 100 terabytes。 that are 100 terabytes。

 The Ram in data centers， you can even have terabytes of Ram that actually exists。

Rby not on your laptop。 and the CPU cache can be a few megabytes。

 It's good to have as a computer scientist， the orders of magnitude， not the exact numbers。

 but the orders of magnitudes in mind。Then you have the la C that's the time it takes to access them。

 I told you for the tapes can be ourwells because the little robots needs to go all over other place to to find them。

 The disc it takes a few milliseconds， mostly because we use still a lot of mechanical disk。

 So it needs to rotate。 The Ram is two or three digit nanoseconds and the cache。

 the the CPU cache is nanoseconds right。Okay。And the throughputs in terms of the speed at which you read for tapes。

 it's quite slow。 That's one of the drawbacks， right，200 MB me per second， the disk。

500 MB per second。 It's order of magnitude， right， because it varies from disk to disk。

 It varies If it's SSD flash drive， mechanical disk and so on。

 But it's the order of magnitudes here for the Ram，10 GB per second， the order of magnitude。

 it's much， much faster than the than the disk。 and the CPU cache，1 TB per second。 Of course。

 it sounds enormous，1 TB per second。 But again， don't forget。

 it actually just have a few MB in in total， right， So it's only a speed。Alright。

 so you see there's always， it's， it's， it's funny because it's always ordered。

 either decreasing or or increasing， but always in the same way。 these compromise。 So it's。

 it's a spectrum。😊，Baically。I have this little animation on why there is la and C on on a hard drive。

 It's really because we have these rotating paths。 And so the heads。

 these are the little triangles that you see at the bottom。

 They have to wait until the disc rotates and goes below the the these triangles。

 And then this is how you when you can when you can read that。So by the way。

 I will probably share a link with you of somebody who did a really great job at explaining the mechanics of disks and related to to latency and so on。

 I think that would be very interesting for you to read just， just like that act of curiosity。😊，um。

Now。What you need to understand。That is not only true for big data， but also for your laptops。

Is that。If you just want to read one more by from the disk。You need to wait until it rotates。

 And so most of the time is going to be spent waiting。 You're going to So I zoomed in here。 it's。

 of course， it's a very short amount of time in comparison。 But you basically wait， wait， wait， wait。

 wait wait， wait， wait， wait， wait， wait。 rotate it rotate it rotate it rotate it rotate。

 And then you read the bite。 And that is actually very quick。

 And then maybe you want to read another bite。 So you wait， you wait， you wait， you wait， you wait。

 you wait。 and then you read the bite。 So if you look at if you do it all the time in repeatedly。

 you basically spend most of your time waiting right。

 just like in the military least that's the memory I have of the military is。 you just wait。

 So basically， this is how it how it how it wet things happen。

 if you just if you just fetch small amounts of data。😊，Now。

 this is the reason why we do not actually read data in very short in very short amounts。

 We actually read them in blocks。 And that's something that I think I already mentioned a few times。

 And for that reason， we read them， the order of magnitudes is roughly 4 kB。

 So here I basically wrote 64 kilo。Beat so， but it doesn't matter It's just an order of magnitude。

 right， But a few thousand characters is the is the order of magnitude at which you。

 you read from disk。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_16.png)

And the reason we do that is that if you never read single bytes。

 but always a few thousand of bytes at the same time in these blocks。Then in relative terms。

 you're going to wait。 But then much of the time is going to be spent in the actual reading。

 So here you have the reading head， the disc rotate that you actually read things。

 And now you see in comparison， most of the time is now usefully spent reading bys。😊。

So do you see that by using blocks， we no longer waste so much of our time waiting。Right。

 for whom does that make sense。That is super important。 This is the basics of。

 and the fundamental of many， many optimizations you do when you build large systems and big data。

 It's to， to try to group together the， the reads and the right so that you have less。

less Latin C in relative terms。So this is the reason why also on your laptop。😊。

Whenever you read and write to and from the disk。It's done in blocks。I probably really meant 64 k。

 So this is typically use for database system。 So I should make it a big B here。

 also just to consistent。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_18.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_19.png)

Allright， So we read and write in blogs。Now， to optimize things a little bit。

 it might be that we are going to read multiple times the same block。

 So of course we do a few optimizations and we have caches。

 so we keep somewhere in the memory copies of the blocks that we have read recently or that we read frequently。

And then we don't have to read them again from disk。 So we keep some sort of cash or buffer in the。

 in the， in the， in the memory。Now。We have on top of this because now I focused on the disk and the memory。

 but we also have the CPUU that is actually doing things on top of that。

And so what happens very often when you start reading very large amounts of data。

 like a huge collection， the integral works of humanity since the beginning of times。

What's going to happen on your machine。Is that the disk is going to read like crazy。

 reading all of other place， like rotating all it can to， to read what you want to read。

 And the CPU is kind of going to be mostly id。 And that's what I told you about these four levels of of hardware。

 right， CPU memory disk can network。 always one of them is to blame。 And here in that case。

 is's the disk that is to blame。 So the bottleneck is the disk。😊。

And so when your bottleneck is the disc meaning that this is the one doing all the work and the CPU。

 the memory， the the the network， there they are basically either。

 There is a trick that is often used。 Do， do you know what you do in these cases。

 assuming you still have only one machine， You cannot use the data center。

What can we do to optimize in this case。W wants me to tell you。Okay， you can compress。

If you compress the data like a zip， think of a zip or a orta a G Z， you compress the data。

 So you agree that the number of bytes you are going to have to read from these is less， right。

Because it's compressed。But there is a cost for the compression。

It's that you need the CPU to decompress。 So it requires computations to actively decompress the file to get the original bytes。

 But here has very good news。 The CPU was id。 So now we have a job for the CPU。

 The CPU can actually be useful and can decompress。 And so now。😊，We。

 we basically moved the balance a little bit by alleviating the workload of the disk by compressing。

 so there's less to read and giving a bit more work to the CPU to2 decom。

 And you just need to find the balance of of that。 So that there's just enough compression to to to give less work to the disk。

 but not too much of it that the CPU doesn't become the problem， right。

 So it's a Goldilocks scenario。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_21.png)

Who is with me？Right， so。We use compression and decompression。Okay。

So we are going to actually have a full week dedicated to compression， probably next week。

 that is that is you're going to see it's amazing what people have done and the brilliant mathematical ideas that they've had to compress in particular standard index。

😊，But today， I'm not going to go only in on compression。 I would just like to compress one thing。

And what I would like to compress are the postings， the raw postings， the pair of term and documents。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_23.png)

Here's why。This is a standard inverted index。 The standard inverted index didn't appear just out of magic。

 We built it， right， And because we built it， I'm going to rewind on that。

 Go back in time on how we actually built it。 I had animations a couple of weeks ago and how it was done。

 So you remember that if I go back。😊，These postings here。

 They only contain the document idea because the term is the same。 but before we actually saw them。

 they used they used to be pairs right so now if I go back in time。

 we had the pairs in here if I continue to go back in time。

 we didn't organize them yet as as posting this So these were just the pairs floating around in memory So the pairs of terms and document ideas。

 if I continue to rewind， they used to be group by documents because originally we were reading the documents and if I go even further back we have the original document if I go forward。

 remember what we did， we take the document， we extract the term document pairs。

 we sort them alphabetically by term then we create these posting this one per term and then we get rid of the redund done terms by just having the document I So if I go back well it's this but the critic。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_25.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_26.png)

Moment is this one。Because when we have。All of these spells of the。Terms and document I。

 They are in the wild floating around in memory。 And on top of that， you need to solve them。

 That is a lot of data。 that's taking a lot of room in the， in the memory of the computer。😊。

And so this is why at least today， this is what I would like to compress to take a bit less space in my working in memory。

😊，Who has any idea。On how I can compress these pair。By taking less space。

Remember that what you see here are the actual terms。 Informationform is an actual I N， F， O， R。

 M A every time， right， And then you have， let's say 32 beats for the document I D。

How can I compress that？Anybody on Zoom， maybe。读个电话上吧。Let me formulate it differently。

 Imagine that you feed the entire computer's memory like this。

 and somebody gives you $1 million if you manage to squeeze even more of these pairs into your working memory without loss of information。

What do you do。Yes， go ahead。Like all numbers， like just create lists now。不。对。就道。对。是不是对？不思。

So you are correct。 So you basically suggest to， to already eagerly organize it like this。 In fact。

 you are correct。You， you're just。Already ahead of your time in the sense that this is exactly how it was done later。

But the early techniques did not do that yet and had another way to compress。

 But your answer is absolutely correct。 You will see that will be the second generation of of system that I will show today that does exactly that。

 So， so， yes， you are absolutely correct。 Let me ask， can anybody see any other。

 even simpler way that people would try it first before optimizing in the way you describe。

And even先不 wait。How about。we。Replace these wells that repeat lot with numbers。 also。

 like information is well number one。 CPU is well number2。

Who sees that this will compress everything， Because then instead of storing the actual wells。

 I'm replacing them with intes that take less bys， right， an integer is like just 4 B or 8 B。

 That's less than the long wells。 I just need to keep track of the correspondence。

 Who this sees that it compresses。Right， so that is the trick。 That was the first generation。

 And again， the second generation that's absolutely what you describe。 I'll come back to that。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_28.png)

So， indeed。We are going to， to， to， to compress that。

Just to give you a few because when you compress， you need to run some math in order to understand if you're doing a good job at compressing。

 So here's an example of collection that's probably a few decades All there was 1 GB of text。

 It was enormous at the time this1 GB contained 800000 documents。

 and there were 100 million of positional tokens in there。So if you take these real world numbers。

We have 1 GB with 100 million tokens。 You just do the division。

 and you arrive to the conclusion that every token takes roughly how many B。10， right。A gigab。

 a GB of text is a billion。 If you use the powers of 10 billion B for 100 million of tokens。

 So you do the division 1 billion divided by 100 million。 That's 10。 So on average。

A term is going to take 10 Bs。 Do you agree。Right， simple division。

And so that means that if I look now at my key value pairs before I compress them。On average。

 I'm going to need 10 B for the actual term that is really spelled out character by character。

 And then let's say 4 B for my document Is。 I'm assuming so4 B is 32 B。

 So this is assuming that I have atmost 4 billion documents to squeeze it into into 32 B to document I。

 But this is reasonable for now。😊，So now it means that every pair is 10 by for the world plus 4 B for the document I。

 That's 14 B。So now if we have this 100，100 million times 14， that's 1。4 GB that it's going to take。

Now， let's scale it up to feed a laptop。 The， the laptop is 16 GB， let's say。

How many tokens So more precisely， how many pairs， How many such pairs can you feel。

So you divide the 16 gig divided by 14 per per positional token。

 and you realize that you can store 1 billion100 million tokens that gives you 11 GB of text。

16 GB of memory。 you can build having memory pairs that are able to contain 11 GB of text。

 So it's a bit less。 There's a bit of waste of memory。 We can store a bit less than the 16 GB。

 So it's a bit redundance。 But now we are going to do this optimization I told you about we are going to replace the terms with the number。

I put the T， the T， of course， wouldn't be written down is just to differentiate from the document I。

 but we have term 1， term 2， so T1 T2 T3。 So this is assuming that T1 is ETH T2 is Xuric T3 is computer。

 T4 is data and so on right So now I will keep this correspondence stable just somewhere in memory a list of older terms with their term I saying that one is ETH2 is zuric。

3 is computer and so on。And that means that now。My pair of term documents is going to be 4 B plus 4 B。

 and no longer 10 plus 4， because I replace the term with the term I D。

 So I have 4 B for my term I D and 4 by for my document I D。 So it means that a pair takes 8 B。

So you see that now， these hundred million tokens of my CV Reox file of before， instead of taking 1。

4 GB。Of memory for all the details。 I only need 800 MB now。 Who sees that。We've compressed。So now。

 if I try to squeeze even more into my laptop of 16 GB。

 now I'm able to squeeze 2 billion tokens in this way。😊，Right。

 so now it's incredible because I have only 16 GB of memory， but I'm able to squeeze pairs。

 documents， term pairs that are worth 20 GB of text。😊，Right。

 so now I have even more under working memory， right， thanks to the compression。

 So this is what compression is for。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_30.png)

So this is great， right， So this is what， why we have to this yes。😊，The size of the。Oh。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_32.png)

要。So this is right here as a author of magnitude。 So I think I gave you half a billion as as at some point as as half a billion。

 like 500000 is very common， typically in a language， if you can't the size of a dictionary。

 So in the sense of a book， you typically have 10020000 words in a language。

 if you push it maybe 30000 English probably has even 60 or 70000。

 because in English you have two versions of every world。

 you have the French looking version and you have the Anglo Saxon looking version like to keep up to sustain。

 So there's a lot of words， basically in English。 but basically it's a  five digit number。

 the words in a dictionary。 Now， if you index the web。

 you're going to have a lot of tokens that are not in the dictionary， the book。

 And so this is where you can have even 6 digits。 So typically 5005000 tokens。嗯。

We'll see when I do a bit of stat next week， we are going to give them letters。

 So big N will be what we have for the number of documents。 Big M will be the number of tokens。

 So this is the size of this is what we call big M。 And again， in your mind， just as。

 as order of magnitude。Let's say， half a million。Is4 M the。

 the number of tokens in a typical system that would be sufficiently large scale that it's interesting for us。

 right， So it's actually quite reasonable because this is 500 K。Compared to。2 billion of pairs。

 right， So， so you can see that the dismacking between the two is ridiculously small in the memory compared to the actual pairs。

 So this is why we have an actual compression。Did I answer your question， Yep， awesome。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_34.png)

Did we have any other questions？Yeah。They have like， let's say。

 three different documents of like three different languages。

Isn't there like some sort of overlap ramp factorss？

There does not really compress anymore because they have so many different towards and not so many different birds。

 Yes， absolutely。 And in fact， when， when you start getting to the scale of the Web。

It shifts the sort of techniques you are going to use because here。

 what I'm showing right here is still something that fits on a computer。

 So you basically have a copperus that you can assume it's the same language and so on。 And。

 and then you basically have a vocabulary size。 So we hear that corresponds to the tokens in one language。

 If you have multiple languages。 Let's say you have 1020 languages， you could arrive in the 6 digit。

 But then we are still within this half a million that that that I give you。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_36.png)

And of course， when you reach websites。And you have not only the languages。

 but you have all the names of the fancy programming languages that people invent that give you new tokens and the brands and the company names and so on and so on。

 And then it grows。 And in fact， this is what I showed you。

 I think was it last week or two weeks ago， these LLM kinds to way to tokenise that when an LLM tokenizes it no longer tokenizes in this way world by world。

 it's going to tokenise by optimizing in entropy and the probability distributions。

 This is the algorithm that I give you the the other day。

 And when you program an LLM to do that to tokenize in this way。 you decide on the number of tokens。

 you say in advance， I want。😊，2 million tokens。And then you're just going to create your tokens all the way until you reach 2 million。

 And when you reach 2 million， you stop。 So it means that this size you control in， in terms of。

 of the， of the tokens， right。All right， awake。Any other questions？All right。😊。

So this closes my term ID compression algorithm。 So now all of these pairs of the term document that are flying around happily in the memory of my laptop。

 we manage to compress them and to fit even more in my laptops memory。

 So now we are going to use that for our indexing algorithms to build larger indices。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_38.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_39.png)

I'm going to start with the first generation。 we see the second generation implements your Id。

 So the first generation， West called it's a tongue twister。

 So maybe you manage to pronounce it better than I do， but blocked soft based indexing right。

 So B SBI to keep it simple。 So that's the first generation of algorithm。😊。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_41.png)

And so the first idea is， could we actually use the disk to to to to index our collection right。

 But then you quickly realize that you can。 I mean， if you have a 12 terabyte disk。

 you can squeeze 530 billion tokens。 So technically， you could index a lot of things。

But you probably remember that the disk is very slow。 So good luck implementing that always written。

 reading and writing to the disk that's going to take forever。 So that's not an option for us。

 We really want something that builds things in the working memory of the of the machine because it's faster。

 So what we want。😊，Is to have a system that is not going to have so many requests from the disk。 We。

 of course， will have to read everything at least once。 That's the least we can ask。

 but we are going to try to avoid doing much more than that。

 And most of the work will happen in memory。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_43.png)

And so the key part that is also one of the key ideas behind the big data is that the collection that we have that might be terabytes on disk。

We are going to part it and organize it in batches。We are going to。

Find a batch size in such a way that we optimal use the memory。

 So the the size of a batch will ideally almost feel the memory， but not more than that， right。

 And if we have more， then we just do a second batch。

 a third batch so that when one batch is being processed like this。 I'm processing my first batch。

 This is using all of my memory， But I'm not looking at the other batches yet。

 So I'm parting my collection， one batch at a time。😊。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_45.png)

There is nothing parallel。 I only have one laptop。So it's sequential。 I have my first batch。

 I'm taking care of it。 Then I'm done。 Then I take the second batch， taking care of it。

 Then I'm done。 Then I take my third batch， taking care of it。 And then I'm done， right。

 So this is the idea of B， SB I block， blocked。😊，Blocked， blocked， blocked， blocked。

 So based indexing， right， So that's why it's called like this blocked。Okay。So the idea is that。

Every time we take a batch， we process it in some way that I will show。

 And then we write back to this， the intermediate results when we are done with that block， right。

 So we write that back。 Then we go to the second block。Process it。

 You have all the key value pairs floating in memory。 Then at the end。

 we write back the results to disk。 Then we have the third block。 process it。

 Then we write back something to disk。 That is the idea。 And now you see reading and writing to disk。

 It's under control。 We just do， we read once at the beginning of the block。

 And then we write once at the end of the block。 And that's it。

 We don't keep reading and writing all the way。 which would be too much。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_47.png)

And then at the end of the algorithm。We are going to retrieve and read back from these。

 these intermediate results。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_49.png)

Process them again a little bit to write the final mergeld inverted。Index to this key。

 So that's the overall idea。Of the， of the B SBI。So now I'm going to zoom in。

 So this is the overall I D。 batch by batch。 We write intermediate results。 And then at the end。

 we merge the intermediate results。 So now， if we zoom in on a block。

 what's going to happen is that I have。😊，Such and such many documents in such a way that the pair will feel my memory。

 So I packed that document， and I。😊，Read my tokens。And create my key， my。Term document pairs， right。

 So now I'm feeding my memory with term document pairs。😊，I'm going to use my compression scheme。

 meaning that I'm going to use term my D document I D pairs。 And you see on the left here。

I'm basically having this small mapping that maps the terms to the term Is。

 And here I have term Is document I， term Is document I。 So this is like， let's say 8 by。

 each four plus 4 by。 My mapping is here。 As one of you observed。 This is small。 This is this is M。

 That's the number of of unique tokens of what we call terms。 It's going to be small。

 And here I have my key value pairs。 Okay， So I create my key value pairs。 Two ways to do that。😊。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_51.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_52.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_53.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_54.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_55.png)

Either I do a first pass。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_57.png)

Over all my documents for that batch。 And I'm creating my term ideas。And then I do a second pass。To。

 to read again the document and now replace the terms with the term Is。 That is a first approach。

 first pass to create my term term my D mapping second pass to convert the terms to term I。

 according to that mapping。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_59.png)

Or second strategy， a bit more ambitious。 I do everything at the same time on the fly。

 So it means that I start reading my documents whenever I see a term for the first time， I。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_61.png)

On the fly I need a term I D in my in my mapping。 So I extend my mapping as soon as I see a new term。

 And if the term is not new， I just look at the term I D that I need to take。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_63.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_64.png)

In order to compress it， right， So two techniques， either two passes。

 one f pass to create my mapping or only one pass。 And I just create my mapping as I go。 Well。

 Who is that here。😊。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_66.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_67.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_68.png)

Okay， so these two ways of doing that。So。Whichever way I do that。

 I'm going to end up with my laptop memory completely full with term document pairs。

 More exactly term my D document， I D pairs。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_70.png)

So what I'm going to do is once I'm done， I just write them back to the disc。Socked it。

 So I sorted all of my term I D document I D pairs。 I sort them f by term I D then by document I D。

 and I write it all back on the disk。 The right is sequential。 I sort it in memory。

 And then I just write sequentially to the disk。 So this is quite efficient that I can do writing in these 64 kB blocks to the disk。

 Very efficient。 sequential right。😊。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_72.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_73.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_74.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_75.png)

![](img/a55f08ff9dd16a69fe9d52e2895a9111_76.png)

So， that is my first。呃。Face。😊，呃。So I soed and right back to the disk。嗯。

And once I'm done with all of my batches， I have done exactly that with all of my batches。

 I end up with plenty of sorted lists of term I D document I。😊。

And what I'm going to do now is I'm going to merge them。More exactly。

I don't have to sort completely because every one of them is already sorted。

So who sees that what we have to do now corresponds to the second part of the merge sort。

Remember how we do a merge sort， We partition the what we want to sort。

 We sort every batch individually， and then we merge。Do you remember that the me is linear。

Right the en log n comes from the first path， but meing already sorted list is linear。

And the way we merge already sorted lists， that's the second part of mergerch So is I have a pointer to each one of my intermediate results。

 and I just in parallelel， go through them sequentially。😊，So， for example。

 I'm going to go all the yellow ones。 And you see my pointers that just move in sync， right， red。

 red， red， red， red， then all the greens and all the ps。Again。

 this is something you already know from your data structures and algorithms lectures。 mergech sort。

 second part， linear time。 I emergingrging already sorted sublists with with me。Right。

 so this is linear， beautifully linear doing that and very efficient， because again。😊。

We are reading everything sequentially。 We are writing everything sequentially。

 Your hard disk is going to love you for doing that。 This is the best way to use a hard drive。

 fully sequential。Okay。So the complexity of doing that。In my first step of。

Soing my key value pairs in memory for batch by batch。 It's going to be tool T lock T。

 where T is the total number of positional tokens。And my second step， as I said。

 is linear R because that's the second part of my me salt。 right， So overall， I have O of P log T。

 Who agrees with that。That is the overall complexity of what I'm doing。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_78.png)

And then we have a second generation algorithm with an even harder thing to pronounce called single pass in memory indexing Spmi S P。

 I M I， I like to say Spy， So B， S B， I and Spmi。But that will be for next week because it's already。

 it's already time to to go and have some meal。 And you will see that with your idea D that we would actually implement an even better way。

 a second generation way， an improvement of our B SBI to do it even more efficiently。😊，So。

Before you go， just。S needity check of。Whether you on with every or comments。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_80.png)

Sorry about that。 That's， of course， the my effect。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_82.png)

第一个。

![](img/a55f08ff9dd16a69fe9d52e2895a9111_84.png)

Yes。Just checking that you are with me。Okay。So this is great。 So the speed， the speed is good。

 So thank you， everybody for following today。 read chapter 3。 The 。

 the quiz is going to be released the two day，3 PM I correctly understood。

 You have one week to solve it。 That is one of three。

 And you need to pass two of the three weeks of graded quizzes to get the bonus news points， right。

 So this is one one week out of three。 if you have any questions。

 send an e know to the to the Ts to myself。 if you find a medium6， let us know， Thank you very much。

 everybody， thank you for moderating。 Have a good meal。

 Enjoy your exercise session and see you next week at 10 AM。😊。



![](img/a55f08ff9dd16a69fe9d52e2895a9111_86.png)