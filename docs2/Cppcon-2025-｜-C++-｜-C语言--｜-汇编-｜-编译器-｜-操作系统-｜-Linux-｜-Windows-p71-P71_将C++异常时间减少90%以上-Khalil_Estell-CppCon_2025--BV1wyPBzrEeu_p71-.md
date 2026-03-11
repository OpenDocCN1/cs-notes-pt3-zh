# Cppcon-2025-｜-C++-｜-C语言--｜-汇编-｜-编译器-｜-操作系统-｜-Linux-｜-Windows-p71-P71_将C++异常时间减少90%以上-Khalil_Estell-CppCon_2025--BV1wyPBzrEeu_p71-

In my experience of languages I've worked in and industries I've worked in。

 most other fields are specific to the field itself。

 I've never seen this level of passion specifically for a language and the enthusiasm and level of detail and knowledge and attention detail about nuances of very small parts of the language and that extreme attention to detail has been really cool to see。



![](img/e434420cf0f20f8cbf4d8de3d1e4e8e3_1.png)

Hello everyone。 My name is Co Stll。 I'll be talking about cutting C++ exception time by 93。4%。

Which is actually incorrect。 It's actually closer to 90%。I improved my benchmarks。

 and then things got more accurate。 And then I realized I'm not as good as I thought I was。

 So while Im trying to change everything， I'm just going to show you what the results are as they are。

If you see this handle， cas see and you see this logo。

 it's pretty much me or someone trying to impersonate me。

And a little bit about me is that I an alumni from San Jose State University。

 I've been working there after I graduated for about eight years。

 I've been on the ISOC++ Committee for about a year and a half now。

 and I've worked on these lovely products from Google The first Google Pixel Watch。

 Google Pixel Buds Pro and the Google Pixel Buds Pro2 Last one was my favorite。

This talk is broken up into six chapters， I'm going go over how all this all started。

 we'll talk about benchmarking， I'll go over how I optimize you see exceptions to a certain extent。

Then I'll talk about my own runtime。 then I'll go I'll tell you about how this search in a search algorithm called Nearpoint works。

 And then finally， I'll finish up with the future of exceptions， at least the way that I see them。

So Chapt0， CP Col 2023 SG 14 ISOCom meeting。

![](img/e434420cf0f20f8cbf4d8de3d1e4e8e3_3.png)

Here， I' am presenting the conclusion。Of my， what became my seat by。

MyO C+ what became my keynote talk for C++ exceptions or code compression at the bottom there was something that was not included in that talk。

 It was this statement down here， improving unwind performance。

 removing the need for dynamic memory allocation and removing thread local storage requirements would make exceptions an extremely attractive option for embedded embedded systems。

And here's the thing。 I had never heard anyone in my life say that before。

Even though I said that in my own head before， I never said it out loud。

 never told it to other people like this。 And at this point， I was nerd sniped。 Now。

 for anyone doesn' know what that is， nerd sniping is when you give a very interesting problem to a nerd and that nerd gets so absorbed into it。

 they stop doing everything else。 they focus just on that particular problem。Me saying this out loud。

 had this happen to me because at some point， I realized， wait， I do embedded systems。

 This would be attractive to me。 Why not do something about this？

 And I wasn't sure about anyone else in the world do anything about it。

 So I decided to kind of pick it up。Let's talk about how I went about measuring performance and how I went about doing my benchmark design。

First lets get into the test setup and hardware。So for the test setup up。

 I use this little device here。 It's called the Hboard P3， my fiance inventedventative。Basically。

 it is a device that includes a debugger and a logic analyzer， all in one complete package。Basically。

 my fiancee was really annoyed with having to rewire all these different components together all the time。

 She wanted all in one solution。So I use this for all my benchmarking。

 and here's a little slot for where the MCU goes。The debugger is used to analyze memory。

 control the state of the CPU， and the logic analyzer can be used to measure the signals of any of the external signals of the MCU。

On the back of the device， there are a bunch of channels that you can use and sample and read the voltages of any of those signals and decocodeed them。

In this case， we are using G0， which is on channel 4 of our logicg analyzer。For the embedded people。

 if there are any in here， I just want to talk about this particular protocol called Micromodud。

 It is fantastic。 I love it。 Ba， it's a way to swap in and out different microcontrollers without having to change the penouts for your application and your products。

😊，This entire talk will be focused on this very low low power， high constraint system。

 only 64 kilobytes of rom and 64 megaHtz of CPU speed。

But I will say that all the measurements that I've done here have been tested on this device as well。

 and I got pretty much the same results。And here's just a slide showing you how you could swap out the different controllers whenever you like。

For those who have never seen the logic analyzer software before， Here's what one of them looks like。

 General， you will see something like， oh， this is our G R D 9 or our D 4。

 This is our signal we're looking at。 We can see if the voltage is high or low。

When we want to start a benchmark， what we do is we pull one of those lines low and we hold it low up into the point where we go and catch or handle that error。

 so from here we would start when we see detect an error， pull this line low。

 hold it low and when we reach the handler， we pull it back high and that pulse is what we measure to determine how much time it took。

 this is kind of closer to real life like I have to turn off a relay in order to do something important。

😡，And you might be wondering， why did I benchmark on a microcontroller when I just do it on my laptop。

 I could have。But there are a lot of benefits when it comes to working with a micro controllertroller。

 In my first talk， I talked about the constraints of microcontrollers， which are all these things。

 but。These constraints are actually powers。 I have no opera system。 I have no network。

 I have no threading in the background。 Nothing else that could get in the way。

 It is solely my code in here。 I can isolate exceptions on its own and have nothing else running。

So that's why we're stuck with microcontrollers。And with that， let's talk about the benchmark design。

For my compiler， I have people ask me， how do you even have to expect it in C++。

 isn't it like can't yout not do that any of that stuff inside embedded。

 totally can My tool chainin is the official Gcc arm 14。2。

 and I'm using for my C library Picoippsse 1。810。Theifications for our benchmark between expected and exceptions is that our goal is to measure the propagation time up the stack from air detection to the handler。

It should it be idiomatics that expected in exceptions？

The two programs should be isomorphic to each other。 so with results and exceptions。

 I keep them at separate files so they don't interact with each other。

 and the program should be identical except for the way that they return errors。Or propagate errors？

And everything's run on 03 so we get the highest performance possible。

What I'm not going to test in this in this in this benchmark is allocation speed for exceptions。

 because it's kind of trivial to provide a relatively fast allocator for a specific implementation。

 So I'm not going to include that part。So here's the basic code structure。😡。

You call run tests that then invokes test depth 50， which calls a function called depth 50。

 which then calls 49， 48， keeps going down until eventually you hit depth 1。

 that is where the air is detected。From there we're going to call start。

 and we're going to prop the air all the way up the stack until we reach the color of our depth function。

 and from there they'll handle it and call end。We also have a setup for all the different cleanup cleanup percentages。

 So we have a sequence of functions that have no deor objects。

 We have one that has nothing but deor objects。 And this one has every other function has an object that needs to be cleaned up on the stack。

And you can guess how 25% works。Here are the two types that I work with。 And here， it's very simple。

 We have a simple object in a de object。 They are identical。 They don't do much。

 but they do enough to make the compiler think I should keep them on the stack。

 I should keep them around。The only difference is that one of them has a nontrily de that modifies a global。

 volatile variable。 So it looks like it has a side effect。

Now let's go into the benchmark design and all of this is auto generated with a paththon script。

First things first， let's talk about the note in line at the top。

I could have allowed it to just be in line and let things get in line where they are。

 But the problem is， I want to see the worst case for exceptions specifically and for result types if it comes out。

 So I want to make sure each one of these functions is now in line so I can see how long it takes when you cannot inline things。

 because I think that's very important because that's the worst case you have to expect。

Here's the object on the stack。 It does some stuff。And then more importantly。

 I have this array here of volatile bytes。And a little check at the end here。

The whole point of this is to prevent tailcoization。

So if you have a function called fo that calls bar and calls ba。

 the expectation is that ba will turn back to fo， and then borrow will turn back back to fo。Sorry。

 Ba to bar， bar back to food。If Barr determines that it doesn't need its stack anymore。

 it can unwind itself， call baths， and then allow baths to return right back up to food。

Now this would be great， but you can't always get this， so I also eliminated this from the benchmark。

And then finally， just to show what it looks like to call another function， there's depth 49。

 it's 50% cleanup， so one function will have simple object and the other function will have deor object。

 and the arrays are also randomly generated for their numbers so that not all frames are exactly the same。

Now for error types， I went real simple for this， there's just types that are arrays，4 bytes。

 16 bytes， 65 bytes， and if you might have an idea of what the 65 bytes might be useful for。

 you'll see in a second。All these are trivially reloctable。

 meaning that you can mem copy them without disturbing the object。

 They're trivial constructible and trivially destructible。

 I want to make this very clear I have tested this。

 The array of four bytes has identical performance than as returning back in single integer or a standard error code。

 So any metrics for that is pretty much identical。For the expected case。

 because I haven't shown that yet。The only difference between the code is that when you call this function。

 get back a results。 you have to check it before you propagate it up。 And that's not it。

 They're all the same otherwise。Including the variables for the sizes of the stacks。

 for the different preserve frames。As for admitttting errors and exceptions。

 you' all pretty much know this， you can throw anything of any size at any point doesn't really matter。

 exceptions don't really care， but with result types。😡，Oh， weird， I'm sorry。

 the screen turned off for a sec。For result types， if I were to try to return all three options of 4 by。

16 by and 64 by as a variant， it would， it would be the size of the largest object。

 which would pessimize all the rest。 So in order to keep these separate from each other。

 Ive separated them into separate files for each error type。Before we propagate。

 we call start in order to start the benchmark。As for cleanup it's pretty simple。

 you call the function， you check it and。You try catch， and simple as that。

Here we have the ordering of all the different tests， all the test cases that happened。

My script also generates a CSV with all of the test cases and leaves all of the pulses empty for their column。

 and we fill that out with another part of the process。And that process is here。

 So we have a test script。 What it does， it flashes the device。

 and then it starts the lo analyzer in a command line program and then recess the device so it can run through all the experiments。

 and that can get all the pulses back， put them into the CSV and get you the data that we're expecting。

And this is it just going through all the different programs and doing this thing。So results time。

I must say this is a logarithmic scale， so that you actually see something on the screen。

Between exceptions and result types is pretty bad。Currently with GCC with a 0% cleanup and four bytes as the errors you have between 113 to 141 times slower than returning turning up your integer。

Not very good。Well， let's look at how cleanup percentage affects things。Well， for exceptions。

 you might have guessed this， doing more cleanup takes more time。 And for the most extreme case。

 depth of 50。 and kind of look at the milliseconds。 here It's like 2。3 milliseconds。 It goes up to 3。

3 milliseconds。 We increased by a whole millisecond by going from 0% cleanup up to 100% cleanup。

You can see the rest of the format here。So it expected same exact shape。

 except the magnitude is far less。And I might even attribute the majority of the gain here just from running the des themselves。

And now get to something interesting， the error object size。If you used exceptions。

 you already knew what this was going to look like。 It doesn't matter。 It just doesn't matter。

 Exceptceptions don't care。 You allocate your thing。 You set it up。

 and then you forget about it until you get into your catch。For result types， not the same way。

 as your result type object gets bigger and bigger。

 you have to do more work to move it up and up the stack。 So it takes longer。

But it gets really bad when you get past a cache line， if your air size is around 65 bys。

 the amount of time it takes skyrockets。If you were to compare it to exceptions of the same object size。

 you would see that V percentage or the multiple， like if you would use exceptions。

 it would only be about 2。6。2 times to 2。3 times faster or faster。

And it gets only worse as your expected。 Ob gets bigger and bigger。So why the slow down。

 That was quite simple。 After a certain point， GC will just turn that into a mem copy and just simply having to do that mem copy for so many bytes just takes so much time for every single frame。

嗯。There's probably some way in GCC to force this to become instructions。

 like just register instructions to do this， rather than making a function call。

 but I didn't look into that I。This is what you get baseline in Gcc。So with all of that。

 what have we learned？ Well， one， result types are very fast for errors less than 64 bys or less than equal to。

Canup perceptions is quite slow。And here are a couple things that I found I sorry。

 as I was looking into this。All of the runtime parameters， no matter how I change them。

 all of them are linear。 So you can extrapolate between 0 and 100% and you pretty much have your answer for pretty much anything。

Also， I couldn't find a lick of no determinism at all in this experiment。And from now on。

 we're not going to worry about 65 by or 16 by errors。

 We're gonna to stick with just error codes for the rest。

So now that I've seen where the numbers are at， and I'm wondering， well。

 where can I begin to start improving things？And this is not always the best idea。 But I thought。

 well，'s look at what takes up the most time， because maybe if I make just a slight tweak to that。

 it would have outsized impact over the whole runtime。So I wrote a script also in Python。

 It takes control of GDP and steps through each instruction。 So I wait。

 I control it to get to the throw expression。 Then I step through every single instruction from that point to catch。

 And then I compile it together to generate this little ref。

This shows the occurrence of how often I've been in any one of the functions for the GCC un wind unwining routine。

And with this， I now have all the information I need in order to start performing my optimizations。

So let's get into it。First step， we're going to look at search exception table。

 exception index table table。Before we get into this。

 I need to explain how the exception index table works。It is a list of index entries。

 each of them containing the address of function that it corresponds to and the unwind information or an offset to the unwind information to how to handle that particular function。

The ordering of the index is ordered relative to your functions in the assembly。

 so if you have some function called F next to bar， next to BS。

 well their entries will be right next to each other as well。😡。

This allows you if you have a program counter in the middle of F to perform a binary search and determine which function you are within。

So here's what G C GCC has for search exception table。 Do not try to fully understand all of this。

 It's a lot。 It's kind of complicated to see how， how it looks。 The first time I saw this。

 I immediately thought of one of the one of my favorite keynote talks from Andre Alex Alexand Drscu。

😊，About robots or after your job exploring generative AI for C++。

 he talked about binary search and how it's typically taught。So let's consider this。

In a typical binary search， you will go into the middle of the list so it's sorted。

 and you're going check to see if that's your answer。 If it's not。

 you can check less than a greater than， and if it's one of those， you shift to the side。

 cut your list in half and you do that operation again over and over again。

 But here's one thing I never thought about until I saw that talk。

 What's the chance that the first time you do a guess that you found the answer。Right。

 it's one out of 10，24， right， cut it in half。1，1，1 out of 5，12 cut in a half，1 out of 2，56。

 When you hit 50，50， when you hit coin toss levels。That's right。 at the end。 only at the end。

 you get a 50，50 chance of actually getting anywhere。 So let's try something real quick。

We get the coin flip going。Heads or tails when we run a program。Tales， fantastic。

Right before I run this， if we did all these other checks and none them resolved。

 none of us got us in early return， we wasted all of our time。 It was a waste of time to check early。

If he's right， at least at the end， we got something。 So he said tails。Heads。Unfortunately。

 we waste all that time。Here's the probability of the chance that you will actually early return for any one of the increments that you make only about a quarter once you get around to the second to last iteration。

How do people first do it。It uses slower bound and upper bound。

 and the design of it is that it uses indexes。It has no early return。

 and it always performs log end steps。😡，But that's branchy。So here's what I did。

I took all of this code。And I threw it into the bin。

I then replaced it with standard ranges upper bound。

Put some like cycle counters so I can see how many cycles it took。

And then I looked at the results for around 710 functions inside our program。

GCC had between 379 for the average cycles that it took on the 64 meHtz device。

 and you can see what the spread of the numbers are from 128148 to 477。So that bound， though。

 the average is around 270 and the minimum is 261 and the maximum is 288。

So we end up reducing our runtime by about a quarter percentage，28%。

So that takes this function from 25%。Now to 10。7% of the whole runtime。Cool， we're making progress。

 Let's keep going。Unwind virtual register set popop， this is popping things off the stack。

 put them beside your registers。Again， there's a lot of code here IGCC is'll see code。

 don't worry about， we're going to pop up the part that really matters。

Here's the code that actually performs the pop。 The first time I saw this。

 I knew for a fact this was going to be s， purely because we almost never push all registers onto the stack。

 therefore， looking through all 16 values is not useful。

Theres this amazing talk by Andre about amortize 01 was a lightning talk， I believe。

 And in this talk， he used these little coins represent operations， and I loved it。

 so I'm stealing it。😊，So we have an operation here， we have a comparison， increment， a shift。

 and a check， and then we dereference and we assign seven operations， I'll keep this as just one。

So with this， if we look at our discriminator， and we have a one in this position。

 we're going to perform all these operations including the check and the increment。

 so that's about seven operations in total。Do it again。 seven operations for zero， though。

We don't take that branch to the bottom。 No， no， no， we skip that。 that's only five operations。

 so it is less。When we you do the rest， the total is about 46 operations in total。Okay， cool。

But what if I could just eliminate all the zeros， because they're not do anything useful for me。

 I don't need to look at them。 I just need look at the ones。 How could we do that。

 Because if we could do that， we could bring the runtime down to or the operation down to 21。

 That is 54% off。 That is a bargain deal。 So how do we get that bargain。

This is a really cool API in C++ called count Rightmost zeros。 It was added in C++ 20。😊。

The way that it works is that you just look at your number。And you say， all right。

 how many zeros on the right hand， Most side of the number before you hit a one。In this case。

 there's none， so it's 0。In this case， there's six of them。 So it's 6。 The cool thing is。

 it tells me exactly where the ones located。😊，So I could use this to write， rewrite my algorithm。 Oh。

 and one last thing before I go into the algorithm， this all just turns into single instructions。

 or maybe two instructions。I can't tell you what's happening with Rik 5， though。

 They're doing a function call， for some reason。But this is what the algorithm looks like。

Pretty simple has the same number of operations。 I've not reduced it in any way。

 All I have done is reduced the s amount that I actually searched for。

So use countar 0 in the discriminator to get back the index of where the one is。

You put it into your table， you dereference， you pull it out。

 and then you clear that bit from the discriminator。

 and you keep looping over and over again until eventually you have finished。

That takes this VRRS pot from 24%。To 7。3% in terms of runtime。All right。Alright， can you unwind。

 execute？ This is going to be a fun one。This function is long， very long。

 it's for every single un instruction for arm。One of the things I noticed， though， is repeatedly。

 there were functions called Nexon1 byte， V RRS， get and V R S set。 Let's take a look at those。

 Maybe there's something I can do about them。 Maybe I can optimize them。I look at this function。

 It's a little complicated。 It's lot of stuff happening in here。

 I'm going to look at other functions before I go and look at this function。All right， this one。

 I looked at this one， and I said， what is this？It's a little bit paranoid。

 So the only useful part of this function is this part here。

 which takes a value from the register set and puts it into whatever this pointer is de' referencing it。

This part has nothing to do with my architecture whatsoever。 And this part， Reg numbered。

Greater than 15。 This can only happen if my compiler was messed up。 So in general。

 I don't like to program assuming that my compiler is messed up。 So I'm gonna eliminate this。

The set functions identical， simply the opposite of the previous one。So here's what I did。

I removed all the rest of the code and put always in line at the top。😡。

I did the same thing for the other one。And then for next on line by。

 I just put always a line on the top again and just didn't change anything about the code。

That took G new unwind execute from 24%， 17。1%。And now with all that， with those three things。

 kind of try to imagine how much we might have reduced the runtime。

If your answer was somewhere close to 50%， you'd be good。 You'd be correct。

 So this is for like the 0% cleanup mode。 and I could go over all the benchmarks again。

 But for the most part， just doing those three things brought the exception runtime down by 33% to 43%。

So at this point， I'm excited。 I think I got to like 64% before I started telling people about it。

 But I started being like， I need to tell people who can I talk to。 Well。

 there's one person in particular I gotta to talk to， which is Jason Turner over here。

 I had his consulting。 He did a fantastic job。 I recommend if you haven't had him over at your company。

😊，So I go and we talk about the exceptions and all that。

 And I tell them I brought the cycle count down to 270。 In reality。

 I told him another number because it was different。 But regardless， I brought it down to 2，70。

 And he said， that's fascinating。I wonder if you could reduce the space you need to check by doing some sort of like linear trippolation。

Which I said， oh， so like， maybe if like the program counters in the middle of the program。

 maybe the entry youre corresponding to it's also in the middle， right。

 Like when there be some sort of relationship there is's like， kind of。

 then there might just be some sort of structure that you can take advantage of， but I'm not sure。

And this became the seedling to the idea called Nepoint search algorithm。

The T LDR for it is basically， I want to be able to go use some。Process。

 do you take the program counter and get back immediately the answer to which entry corresponds to。

At the same time， I'm talking to one of my students， Madeline Schneider。

 she's doing a talk in Friday。 So on USB， I recommend you go to it。Also， she's a rust station。

 So obviously， she would say the comment， well， acceptance could never be faster than result types。

To which I said， oh， yes， yes， No， I totally get you。 I get you。

 Now I can never be faster than results types。But now she brought that up。

 I'm going to try to what she said。Hows that even possible。Now， here's what I told。 I was like。

 consider this Madeline。 I want you guys all to know this data is actually completely incorrect。

 It is delusional。 I had misconfigured my flash for my device。

 so more cycles were required to do with certain operations。 But with this delusion。

 I went to her as I right。256 cycles for six frames， right， divideivide that by 6。 That's 92 cycles。

I did some math and math on on the whiteboard。 Probably totally incorrect。

 But I got 65 cycles per frame。So if I could take the 270 cycles and bring it down by an order magnitude。

 I could fit。So that became the requirements for Nepoint。Not that need to be faster。

 but simply that I wanted to have some sort of search that was an order of magnitude faster than binary search。

 and would also try to preserve the space savings that you get from exceptions。

So on a flight back from a business trip from Missouri。I decided to kind of graph out。

 this is all using Sito data， just kind of ma some random generated data。

 but I want to see what it would look like if you had the function address space on your X axis and your entry number on the Y axis。

I zoomed in。I took a look and said， why isn't this smooth？

Why can't I just put a line through this and get my answer to some degree。

 you can kind of do that with this what I'm showing you here。 But I looked at and said， well。

 this dot right here represents a function。 So does this one。

 What's the difference between these two。 Well， this is actually the function body size， right？

 So this function is big。 This one's small。 What if I sorted them by size。

So you got something like this。And I was like， oh my goodness， I could just do a curve fit on this。

 view some floating point numbers， throw the program counter into the equation。

 get back out the entry number。So that was the goal。Reality struck。

And I looked at an actual bit of code and I was like， oh， it doesn't going to work so well。

But it was cost enough。 And I was super excited。So then I took this and went to my first ISO committee meeting in Japan。

 hosted by Wooven by Toyota。Yes， I spoke to a lot of amazing people and learned a ton there。

 but there was one person in particular who who gave me a new requirement for Nearpoint。

 and that is Ben Craig。 So I told them， oh， we can just make the graph use following point numbers。

 It'll be great。 They're not that't。 They're not that bad in terms of performance。Whi she says。

The problem isn't the performance。 iss actually the space budget。 You see。

 I have devices without floating point units。 We we have to emulate all of that。

 all those operations in software。 that could exceed the amount of memory that we have。I'm like。

 all right， all right， desktops and servers。 What about them。 I was like， no， no， no。

 if you can do this this for system engineering。Gloport operations will corrupt user mode state。

 So no good。 He made it very clear。 integer math only understood。When I talk to this individual。

 Robin Roe， I'm yamandering on about exceptions on embedded and stuff like that。

 And he says something that I don't think I've ever heard anyone say to me or anyone else before。

 And it was， you know， I agree with your premise。But I don't know if I agree with your conclusion。

And my response was。So we had a five hour conversation about this， I like other things。

 We into a whole variety of different conversations。But out from this came two things。

I formalized my talk that became a keynote at ACC and CBPCon， and he was inspired to work on。

 if you ever heard of it trap C。 trap C came from our conversation。

And then you also from our conversations， has been working on other memory safe things like memory safefe T string。

 a safe string for C。So some months go by。I end up at St。 Louis meeting， the ISOC++ meeting in St。

 Louis。And specifically people that I was targeting to talk to。

But there was one person who gave me a very explicit requirement for my runtime。

And that was herbseutter。I show my current runtime results。 and he says， that's very interesting。

 How do you handle catching exceptions。 George I said， O， well。

 I've done some optimizations to kind of just catch directly。 I don't do polymorphic catch。

 but I plan to implement that at some point。Tohich he said。

 make sure your dynamic cache like algorithm。Implementation has deterministic performance。

It should have an upper bound on space and time cost。😡，Understood。And with all of that。

 I can now start talking about my runtime。 We're gonna go into all the details about it。

 I'm gonna go over like the optimizations that I made。

 and maybe we'll get some useful information from that。😊，Before we get into that。

 I can tell you about some of the things I noticed when I was looking through G C's implementation。

One is that I noticed that the exception searches were happening twice per frame。 So you get。

 you do the whole search， Pay all of that。 get the pointer， use it， then drop it。

 and then later on in some other part of the code， do the search again and then use the pointer and then drop it。

 So we could have cache that。 It's only like a pointers worth of memory。

 I think that would have been fine to just cache。啊。Next up。

 the dynamic casting a little confusing or complicated。

 I know there might be some way to kind of speed that up。

And then the thing that really kind of upset me was the multi length support。

 I didn't fully understand this or appreciate this。

 but you can like throw exceptions in Java and then catch the me S or， throw them through Java。

 have Java call S plus plus， and then call Java and have it propagate back up through the entire stack。

You can pro get through any language really， but I don't have any Java on this microcontroller。

 So I don't have a need for this in my code。The other great and fantastic thing about this was the two do's in the source。

 It's quite a few of them。 One of my favorites is take advantage of the fact that C will always word a。

😊，That particular todo has been there for 20 years。Next year。

 it'll be old enough to drink in the United States。 A little earlier in Europe， can already drink。

Let's get into the optimizations。 Here's the first  one。'm gonna to be real quick about this。

 optimization 0， simply wrote it in C plus plus。 I think a lot of the heavy lifting kind of happened from just doing this and using a modern compiler。

I got a lot of dividends from just rewriting it at C++。Next up。

 I'm going to talk about single phase exceptions。So。

For those who don't know where the exceptions work is that when you throw an error。

The first thing that it does is it propcateates up the stack to find a handler。

 and then when it finds the handler， then it'll start unwinding and it'll start calling des。

With my single phase exceptions。I unwind the stack and perform cleanup immediately。

 and I keep going until eventually I find something I terminate。 That's pretty much what I do。

Some of the consequences of this。Well， someone told me， well， if you do it this way。

 then I can't do a core dump because what I want is to know that I'm need to terminate and then do a proper core dump。

 And then nothing in my system has changed completely。I think that's actually a valid use case。

And then I heard from other people that there are some applications that may require this。

 I don't have an exact idea of this， I don't have a use case， but some people told me that。

The' positive， though。It's faster without any additional storage。 I could just do it immediately。

 It's also easy to write， not going to lie。 Also， it has the same behavior standard expected。

As someone who's done throughout my， I've used I unexpected and something like that for my entire programming career。

I am so used to instructors being called when I prop errors that didn't make sense to me to like。

 not make my exceptions do the same thing。 This would make this more at home for me。

 So I went with this behavior。So optimization level 2， T L S control block。

 Ive talked about getting rid of T L S thread local storage。

 I found out that's actually really useful。 And I don't use it almost ever。

 But there are some cases where I think that this is really useful。

This is more of a storage optimization。 And the main thing is if you saw my previous talk。

 I talked about how when you allocate exceptions， you over allocate the amount of memory。

 and then you use the section behind that memory that you allocated to hold all of your state。

The problem is that costs you around 128 B per exception when it could just be 128 B per thread。

 and that's smaller I think that's better。 And I have ways to get thread local storage to work really easily on embedded systems。

 It's not too bad。I just know how to implement it。My next optimization is PMR allocation， again。

 not exactly the biggest optimization， but it really gives you control over being able to control how you allocate your exceptions。

So for my runtime， I have a exception allocator and a get exception allocator。

 takes a polymorphic resource， and then you can control how you want to get out your memory for exceptions。

But I do have a header for my exceptions when I do allocate them。

 so I do have to hold a bit of information after I allocate。

 which is the pointer to the memory resource that allocated it and its size。

Just so that when I cleaned it up later on， I can use that to just decate it。

The allocation functions really straightforward。 You just sum the size of the thing that's thrown plus the exception header。

 You get the， you get the resource。 You allocate it， get the pointer。cast it。Set the size。

 set the allocator， return back the pointer the to the data。 Oh， and this little aligned by here。

 So I should have talked about that。 This is just a little shadow that I can use to reference where the object starts。

That's from that。All right now we get to the real optimizations。Optimization number4。

 skipping the first search。 I realized， why do we even need to like。

 So one of the things I realized when I was doing the unwinding was。When you unwind。

 you first have to unwind throw， and then you can get to your actual function startwinding them。

 But I know I'm in throw。 I get just unwind throw immediately。

 So I just cache unwind instructions for throw， and then I windd it as part of the throw function。😊。

I have a function here called Ca， which you give it a pointer to a function。

 and it'll search the index， give you back the unwind instructions。Now。

 I have it pre cash in ready for me to use immediately。Proroptization number 5。

 I prearrange the unwind instructions。 So in Gcc， we had this kind of complicated function called Next Unwindbyte。

 The data that it was dealing with with something like this。 And you can see that it's kind of weird。

 Like instruction 1 starts at bit 23 to 16 and then kind of goes from 15 to 8。

 and it's kind of just confusing。 So they have this logic to manage all of this。The fun fact， though。

 I don't show this program this function in here， but all the information about where all possible instructions can exist is noable at compile time。

 I know that its bit 16 of the 23 instruction 1。 So I wrote a very simple function that would take all of that and just flatten it out into an array that can easily iterate through。

😊，So I should do that then to try to not do that。Which then leads us to probably one of the most controversial parts of this entire talk。

 optimization number six， just in time unwinding。So。Just recap。 Swcase are great。

 I think you should use them。 They're fantastic。 I've always had no cases in my。

 in my career or I've ever not used the switch case for something like this。

 But the compiler trying to be smart， trying to optimize things down a little bit make things a little bit。

 not not as big。 And I realized I needed to just break the glass and go all the way。😊。

I need as much performance as I possibly can get。 What I need is a jump table。

 So let me show you how to make a jump table in Gcc。So here is an array of addresses。The array。

 the jump table is 256 in size， and that's because all the unwind instructions are 8 bits in size。

I now have a label for every possible unwind instruction that could occur and you can use this little double ampersand on labels in order to get their address。

 it's an access to GCC， it's not portable code， so this is one part that I don't really like too much。

 but that's how we have to do it here。Now for the actual engine。I grab the instruction point。

 I get an itererate from the instructions。 I throw them into the jump table。

 It pulls me back out a handler of the address of the handler that I need。

 Then you can do a go to de referencefer instruction handler。

 and it'll jump you straight to that handler。You can see some of the other instructions that are here。

 like finish unwind and reserve thus terminate。So here's one of the functions。

Or one of the sections here。Here's when of the labels pop off stack R 4 to R 11 and link register。

 This will do exactly what it says。This function is a bit long， kind of big。

 But the main thing here is that the majority of the code in this is compile time。

 And since this compile time， the compiler knows there's only a certain sequence of operations that need to be performed。

 And even though this is a runtime checked value because it's not cost back here。

 The compiler knows everything it needs to know in order to unroll this for loop。

So the actual assembly for this ends up turning to this。 Now， this is a lot of assembly。

 And I thought it'd be a lot smaller。But then I started trying other things to make this smaller and faster。

 And I found out that this actually is very performant for some reason。

 They can probably know something that I don't。 And I'm still working on making this even better。

 But for the most part， I'm pretty happy with the results。

 There is no conditionals in this block whatsoever。😊，And then finally， this is for herb。

 optimization 7， flattening the runtime type information hierarchy。So to Arthur。

 thank you so much for making this talk， because he basically explains in detail how to do everything that I'm gonna to do here。

😊，I'll go over it for you guys really quickly。This is the layout for run type type information in C plus+ for the ittanium APII。

If you have something like standard exception， it has no class that inherits。

 therefore it ins the aI information inherits class type info and has a single field called name。

We have class type with one parent， so it'll have a name， it'll ap that parent。

 and then it has it inherits the class single inheritance class type info。

And then for multi inheritance， we have VMI class type info that we inherit。

 and we have a couple more fields， flags， length， and we have the list of all of your parents that you inherit。

As a way to kind of visualize this， if you had a standard out of range and you have logic error and you have sit expected or exception。

You can see how this all connects up to each other。So we're going go over the fighting algorithm。

 assume that this7 is figured out at link or and or compiled or actually at link time in order to figure out what hierarchy within your program has the most。

 has the highest amount。 And you make that your fixed amount of memory。From there。

 the first thing we do， let's say we have a hierarchy of D， A， B and A or A sorry， A，B， C and D。

 first we're going to do is put D onto the list。And now we're going to evaluate D。😡。

D has multiple inheritance， so we're going to say， all right。

 well let's just push its parents onto the list。She brushr on the list。The movie evaluator over。

 and this evaluator is the thing that you use to figure out what step you're at， you're on。

We check its only single inheritance。 as one parent push a onto the stack or onto the list。

Move over to C， see has no parents， don't do anything there。A has no parents。

 don't do anything there。Once the size and the evaluator are equal to each other。

 your algorithm is finished， this is O of n number of entries。

 and the n is the number of entries inside of your class hierarchy。The dynamic cast is quite simple。

 when you have your cap V and cap C， all you have to do is check to see if the address is in this list。

 If it's not， it's not there。If it is， cool， that's your catch。

I is implemented very simply in a for loop。 You just got to say， here's my list of types。

 Here's my type entry。 I got to check to see if it's equal to my catch type。 And if it is。

 install the context， if it's not， then move on。So the operations that you have to take before you get to your handler is O of n times M。

 where n is the number of entries you have in your class。

 and M are the number of catch catches that you have to go through until you find your handler。

So now for results time。With this， I got to around 83 to 85。4% faster than what GCC can do today。

And I've now moved the range that we're in from hundreds to thousands， from tens to hundreds。

 I'm so not the ones to tens， but I'm getting there。

And now we went from hundreds of times worse than said expected to now 17 to 21 times。

Compared to it expected。And then for 100% cleanup， I'm doing better， not as best。

 but you know I can I'm between 81。62 79。7。And then here's the multiples， when you look at it。

ed with respect to result types。Now， here's a question， where is the nondeminism？

I never found any on my American controller。 There is no nondeminism that I found with exceptions on this device and any of the devices that I tested on。

But all of y'all use shared libraries and therein lies the rub。Well， it was before 2023。

 someone fixed it。 So in my previous talk， I had this slide talking about the reasons why former our developers avoid C++ exceptions。

And that little hidden section was shared libraries。Here's the fun fact about this one， though。

 Someone how to fix it。 So there's this bug and Gcc called concurrently throwing exceptions is not scalable。

 Well， why is that， Well， when you try to access a shared library if I'm remembering it correctly。

 it has to， if that library has an accepted index and needs to be merged into your exception index。

 So you you need to hold a mut text for the index for the duration of that time。

 And if you're having to read from flash or read from storage in order to move it in。

 you could consider that to be non deterministic。😊。



![](img/e434420cf0f20f8cbf4d8de3d1e4e8e3_5.png)

But now someone else figured it out and they made some sort of like lock free systems so that that's no longer a problem。

So as far as I'm concerned， type comparison and shared libraries are not determin not not deterministic。

 They're very deterministic。 So yeah。But here's the thing。

Those numbers we showed before had an 8 in front of them。 I want there to be a 9 in front。

 at least a few of them。 So now it's time for me to work on near point。 How can I write a system。

That allows me。To quickly just jump to the answer I'm looking for。Let's get into it。

I've added a new requirement。The maximum guess must be less than 8。 Why is that？

It's for cash locality reasons。So let's say that we do a guess。 and we're right around here。

 This is our little cache line cache line1。 And for those who don't understand how cache lines work。

 Basically， when your C wants to access some memory that it's never seen before。

 it reads out a block of 64 B into its internal cache and then modifies and works with them。

But if it's never seen these cache lines， has to go out。

 pull them in and evaluate them or basically bringing them in， which takes a bit longer。

 then just looking at your cache。So if we evaluate this function or this entry here， we guess here。

 and our answer in the next cache line， I'm gonna have at least one cache miss。

 Unless I'm on the money every single time， I'm gonna have to move over。

 So I knew I can't get beyond， I can't get down to just one cache miss。

 if I stayed within 7 or less than 8 of my error。 Well， the cache line is 64 B。

 exception entry is 8 B。 So there's eight of them in a cache line。

 So if I stay less than 8 error out， I'll never exceed more than one cache line。

And here's probably one I'll probably blow your brains In coalescence。

 I talked about this in my paper about no except in arm， T based exceptions。 And yes， I did， in fact。

 misspell no except in this title。So if you have two functions that are right next to each other。

And their unwind information is identical。You can merge those entries into each other because it doesn't matter where you are between function X or function Y。

 the unwind procedures is the exact same thing。So the first step that I do for nearpoint is I group all the functions by their ownwin information。

 including all the nocept functions as being the biggest one。

 no except has like so many things you just throw them all into one entry so that there's only one no except entry in the entire program。

😡，And then I take that， and I sort it from greatest block down to smallest block。

 almost always is no except like the first one。Then looking back at this graph。

 I'm going to graph out the entire address space and all the entries。

 and I'm going to block up all the memory into chunk sizes that are like powers of two。

Why powers of two well？If you use a power to， let's say 1024。

 all the bits above 10 can tell you which block you are in and all the bits nine and below tell you where you are within the block。

So now I can figure out， I can hold down， I can take some information for each one of the blocks。

 store it and use it for finding my entries。If you zoom into any one of these。

 you'll see that they're pretty much aligned。😡，So we're just gonna to do a quick。

 linear approximation。And normally I use robot sizes much bigger than this。

 but this is the example I'm using here。So for this。

 it's real simple to kind of come up with the approximation。

 You just take the first entry that's inside the block，42， that becomes your B。X and X。

 not where you are within the block。 You get that from your program counter。

 So don't to do anything special there。And then for M， well， M is your slope。 So let's rise overrun。

 So your rise is the number of entries inside of your block and your run is your global block size for your program。

 So you want need to record that once。So the only two numbers you actually need in order to approximate where all the entries are is the entry count and the starting number for that block。

Heres some code that shows like I have a script also in Pthon。 I'm writing in C+ next。

 It's been a pain to in Python not going to lie。 Here's what the table looks like。

 And then here's what my descriptors look like。 I need to keep the block power。

 as well as the starting address of where my text section， where my code starts。

And here's how the algorithm works。 Step 1， pull the information out of the descriptor so that we have them available。

 Use the block power to create the inter blocklock mass。

 basically a mask for that particular for that block size。Now break apart the program counter。

 pull out the block index as well as the inter block location。😡，Use the block index。

 though into the block table， the normal table is what I call it。

 and get back out that block information， you break that apart。

 and then you just perform the linear approximation at that point。So you take the inner location。

 multiply it by the entry count， and then you shift to the right in order to perform the division by your run。

 so multiply by your rise， divide by your run。And then you add it to your entry start。

 And now you have your guest location。Then after that， you have the iterates to left into the right。

 and iterations very fast， very， very fast。 So this ends up being quite efficient。

And for the results， I have finally reached 90%。At least for frames above 11。So。With this。

 we're actually faster than binary search， thank you， thank you。We are around 87。

1% at just one frame and up to 91% or 90。 Yeah，91% at up to 50 frames。

 And it's kind of linear between。The multiple is around 14。7 times to 12。

2 times slower than returning back integer。 or as they expected with the integer as air type。

 so we could do better there。 still quite a bit。For the 100% cleanup。

You'll notice that for a lot of these numbers， the green。

 which is the near point and the Et exceptions， are very close to each other。

 and that's just because the cleanup ends up taking the cleanup procedures end up taking up so much time embrassing everything else。

 even though binary the near point search is fast， doesn't not about that much。

And then here are the multiples here， 18。6 to 27。9 times slower than those expected with an integer。

Now， I'm， I'm the guy who talks about like code size。 So now we're adding more tables。

 What is the damage here。Is negative 588 bys？Well it make sense， right， What did I do with Nearpoint。

 I deuplicated the entire exception index。 I took all the entries that were unique and different or that were that were the same and combine them into one。

So yeah， I， I save quite a bit of memory from doing all of that。

 And this is assuming block size of 12 or 11。 if you have anything higher than that。

 then it gets bigger， your error gets a little bit bigger。

 So get a little bit of a difference in runtime。 But that's what you get。Now。

 let's compare with standard string， but it' empty。No idea allocation， none of that stuff。

 we're not talking about that here。 I simply want standard string to be two things。

 It has a nontrivial move constructor， It is not trivially relocatable and it's a bit of a stand in for complex type。

 This does a little bit more stuff when you move it around。😡，So I replaced my test error 16 and test。

 I did two tests， one with one string and one with two strings。And when I did that。

I know the number is a little different。So if you just have like one string inside。

 if you have like the red thing here。 I'm so sorry for those who are colorblind。

 The red and the orange， the red on left hand side is one string and the one。

 the bar over here on the right hand side of the of the graph is the two x strings。

You'll notice that the runtime blows up。Quite a bit。 And you can see that it's only 9。6 to 1。

5 times faster to return was it expected with a string compared to just using my runtime。

And then for the opposite side for doing two strings， which is a little bit crazy。

 who returns up two strings with of stuff。 But if you had one of those things。5。6 to less than one。

 meaning that my runtime will be faster than you trying to propagate two strings。

 you could not propagate us down that far up 50 frames on my micro controller faster than my algorithm can calculate where your cache block is。

😡，Sorry， I was little scrambled up there。Now， obviously for the 100% mark， not a chance。

 still pretty far out because it takes so much time to jump in and out of functions。

So why is standard expected affected so impacted so badly。Well。

 result types and exceptions have most of the same things they have to do to do。

 But for result types， you have an O of N operation。

 You have to move and copy your object up the stack each time。You can use copy to some degree。

 but sometimes it's not always available。 And you might have to actually copy things up。

Whereas with exceptions， you allocate once。You construct the object。You leave it alone。

 and you propcate up the stack。 Excepts do not care about return values。

 They don't need to worry about that。So a bit of a recap on my talk。

 How do I reduce C plus plus exceptions by GCC on arm cortex M by 90%。

I use the standard S+ Librarians when appropriate。I move as much code to compile time as possible。

I apply data driven design on the exception index and the unwind instructions。

I cache and preatted data when appropriate。😡，I wrote the whole thing in C++。And then finally。

 I think the most important thing was I believed that it was possible because I didn't believe it。

 I None of this would matter。 I would' have done this stuff。And to wrap up。

 I just talk about the future of exceptions， at least the way that I see them。Get some water。

 actually。I'm doing so much better on time than I thought。 I'm sorry if I ran to this so fast。

 apologies。So part3 of this series， some people don't know。

 So this is actually part two of this exception series。

 The first one was about code size and how exceptions reduce your code size。

This one's on improving the performance on the Sapath。

 And the third part will be about how to actually write software with exception。

 specifically using a tool that can。Analyze your binary。

 find where all of your throw expressions are， find where they propagate up to。

 and then give you hopefully a really nice UI that can show you where the different pathways go。

The point of this is that I write software that is portable， modular and cross platform。

And because of that and the fact that I use abstractions quite well。

 the happy path for all my code is identical， no matter what things I move in and out of my program。

But the sad path， the errors。 Those always seem to be platform， application and modular specific。

And I could try to create some sort of， like。Smoothed out air for those specific things。

 But at some point， I realized rather than trying to abstract out the types of errors。

 What if I let them say as they are be be as much context as they can for your application and then tackle each of my errors for all my application on an application。

 my application basis。 The things I have to consider for one application compared to another application are very different in terms of error handling and responsibilities that I have between them。

So I want a tool that will make me be confronted with every single error in my program and make me either say。

 I excuse these errors because I will never be able to handle them It's not possible。

 I don't care about it or say， wait， wait， wait， that throws here。 Wait， actually。

 I think I could do something about that。 We put an extra sensor there for redundancy。 Oh。

 we actually put another valve there for this other bit of redundancy。 Oh， actually， I can。

 I can retry this thing and actually get this thing to be handled because it's very rare when it messes up。

 But if I try again， it'll work。So that's what this whole tool is for。

 That's what the exception Insights tool is meant to bring in。Another that I'm working on。

 the unique exception format， it's not much different from what I've talked about before。

 There's just a lot of data you can de duplicateupate。 Obviously。

 I showed that with the exception index。The exception data table is next。

 and that is mostly to reduce down and improve the performance。 So this gives you two things。

 D duplicates a lot of the data and also improves performance because I'm going to rearrange some of the and wine instructions that they're properly ordered。

Other things I've been considering。 I don't know if other people agree with this。

 but I would like to have this function。 I've a of people tell me that really want this functions inside the Santa C plus plus Library。

Basically， a set allocator and a get allocator may not be in this format。

 may not even go into the standard， but I feel like this is the first step to getting C+ plus freestanding exceptions。

Also， I've been doing a lot of work with co routines。 I love Co routine。

 C+ Co routines are really cool， really powerful。 They're just very complex because they give you so much control。

😊，And I noticed something about a sync unwinding that I think might be able to be improved。

 I don't have a full idea， but I'd like to work on that project。And then finally。

 I think one of the most important things here is people always ask me how I'm going to enter this technology。

 and I've spent a lot of time thinking about this， and I've come to the conclusion that， know。

 I will at some point update GCC and Kang to support the exceptions that I've worked on。

But if I want to get this tool into your hands like tomorrow， it's not available yet。

 but if I had it， I want to get this to you tomorrow， I would just give you this file。

Raise your hands。 Who here knows what link time optimization is。Cool。

 did you know that that was implemented as a linker plugin。

Meaning that you put it into your linker and it does all the work there。 Make sense。

 But it's a plugin and。 You don't have to include it。

 And then I realized that I don't need to change your compiler。 I don't need to change your standard。

 I don't need change your A。 I don't need to recompile your binaries。

 All I need is for you to put my code into your linker， and I can do a set of things。

 I can take your unwinder。 Except run time。 throw it in the bin。 place it with my own。

Take all your functions， order them in the way that I showed before， generate the tables。

 inject those symbols into your program。 and now you have my exceptions。

I am hoping I'm not sure about that last part， but。Exception insights。 I how I can make as a plugin。

 So it could be part of your build process。 You just kind of add it into your link command。

 and then you get all information right there。And one other cool thing here is that exceptions become modular。

 You don't like that jump table， takes up too much memory on your on your device。 No worries。

 I give you a file that doesn't do that。😊，Oh， you don't like the two， the single phase。

 You want two phases。 No worries。 I give that to you。

 I just have to write it and then just give you the file。 like， what else would I need to do。

So that's pretty my chip。 That's how I plan to distribute out this technology。

 And hopefully this will be really easy。 So one last thing I want to add to this。

This would not matter depending on the version of G C you use。

 It only matters about the linker that you use。So the people who I work with who were like， oh。

 we only at Gcc C 12， we can't go up right now because we have some process for that。

 I can still give the system they can try it out。Spial thanks to every individual who's on this list here。

 they've all had a massive contribution to this whole work。

When I have to give a special special thanks to Guy Davidson。

 because if it wasn't for him pushing me to do my first talk at AU， this would not exist。

 I would not have done all this。😊，But also， as you noticed。

There were a lot of talks that described in this talk。

 if it wasn't for the people who do talks to see Bcom， but not to CB Bcom， but all the conferences。

I would not have able to do what。 I would not have been able to do what I did here。

It helped me so much to be able to look all this range and learn so much from everyone else。

 So for the people who are online who are watching this。

 I highly recommend that you come to at least one T+ conference in your life。😊。

If you use it as a tool for your career or just for fun。I have learned a lot。

 my whole life really changed a lot after going to my first CBP con in 2023。

 maybe it might happen to you。And with that。Questions。Thank这个。I just got two things to。

 So had you've been using this on this small controller。

 Have you used it on sort of more an enterprise compilation and had it work。 Yeah， yeah。

A student of mine has tested it， and they have made it work。I have students who work with me。

 I've been telling them everything about my exception stuff。 they got inspired。

 One of them changed from aerospace to computer engineering specifically because they got inspired by the exceptions work I was doing。

 And then they got some stuff working on X 86 for Linux。 But that's like very beginner stuff。

 We haven't built that up yet。😊，All right， the second thing I have is， where are you going with this。

 Are you sort of saying， look， use exceptions everywhere they're kind of free now right or are you saying。

 look， if you're in the embedded space where you've been kind of barred from doing stuff with exceptions。

 this is kind of a little more niche for there So Yeah， is's gonna to sound really weird。

 I don't like how most how most software developers handles errors and exceptions have this really cool property of the space savings。

 And the fact that I can see as part of their A calls to CxA throw and calls to cache begin and all that stuff like that。

 It's all built into the binary。 So what I realized that what I wanted to see was all my errors laid out bear on an application by application basis。

Excepts became the tool for this， but to kind of go a little further。嗯。

I actually think most code should be designed in such a way that you cannot even have errors。

 I think that people are a little too flippan about like， oh， I'm gonna have an API。

 I don't to do this spot。 now I'm gonna just return an error when in reality。

 what they could have done is change their API to enforce that errors couldn't actually happen。

I'm trying to think of an example。 I can't think of it right now。

 I'm kind of blanking my student Madeline。 I probably remember because we've talked about this recently。

 but there are a lot of cases where I've seen APIs where I'm like， oh， well。

 if you choose this as an API here， you're giving the opportunity to a user to make a mistake and have an exception be thrown or an error be returned。

 should write your code such way that that cannot happen。

 And only in cases where you have errors where you know and have expectation of how someone will handle them。

 Youll handle them。 that goes into my idea of what's called exceptional software design。

But I'm so still filmiliulating。 I'm buildingling up。 we should talk more。 All right，Hello， hello。

 thank you。 I had one question you mentioned that you would want for the flattening of the the flattening algorithm。

You need to pull that data at link time。 how do you do that， How do you do that。 Yeah。

 so in the linker in the linker plugin， you can actually see all the symbols and you can kind iterate through them until you find all the R types And then once you find all RT types。

 And they have a very specific way that they're like build up。 For example。

 underscore underscore class type info。 I can find that symbol。

 and then find everything has a pointer to that particular symbol in their V table or that symbols V table from there。

 I got click all of those。 then perform the same thing I just showed you to get the length maximumim use a vector in this case。

 And once I find the maximum， I just kind make the size I put in And there's some other trickery that I do in order to actually embed like an array of that size。

 that part isn't finished yet， I know I haven't I how to do it。 I just need to implement that。

's how it And one other question。 you。😊，With the jump table for GCC， very creative。 Love it。

 how would you make that more portable， Do you have ideas for clang， MSDC， et cetera。Not yet。

 Think about it。 Yeah， yeah， thanks。 have an idea about that。My previous experience。

What I would do is have。Call a function jump table。callll each other。Chll call optimization。Okay。

 I'll try that out。 Thank you。Oh yes， thank you。 Alright， So I hopefully， I'm doing it right。

 But basically， the idea was that you can have a set of functions。

I't know if I'm not if I'm gonna do this the most justice， but basically。

 if you have a set of functions or you have your different operations for all the different codes that you have。

 you can make them a list of functions。 each one of them will call the next handler for the next unwin instruction。

 And the idea is that tailco optimizationization can get can help you so that you just kind of call all the way down and becomes very efficient。

 I'm not sure if I'm doing it the best justice there。 But that's kind of close。 cool。😊，Thank you。

 yes。For what it's worth， Josh Haberman's blog has a really good blog post on that exact technique。

 It's the pro parcel So if you' you can read that， I had a question you mentioned unwinding through foreign languages。

 like unwinding through Java。How do you trigger the finally blocks in Java when you're doing that。

 Oh， I have no idea。 I've not spent any time looking into。

 I've spent no time looking into how the inter process stuff works because I told you， I really。

 when I write C plus it's C， and I don't have interaction with that。 I as Google as a Google。

 So it worked at Google and worked on a lot of Android stuff。 technicalically， I should know that。

 But there was a point where I think I was like。Figuring out how something was working。

 And I got like 60。 something functions deep。 And I told myself， I don't want to do this anymore。

 yeah。Yeah。I claim talk。 I had a question。 You talked about control block size。 Yes。

 and how you changed it from a per exception size to a per thread size。 Yes。

 I was wondering if you had ideas for architectures that have a lot of threads。

 but not a lot of memory per thread。 How would that change。 Try out for like GPs， right。 Yeah， Yeah。

 You know， I I had that exact talk with Bryce before。 I have not spent a lot of time on that。

 unfortunately， just because I spoke to Bryce， He said， he's like， he's like， dude。

 we don't even allow function calls with our GPUs。 We try to flatten everything out as much as possible。

 I'm not sure where the value would be， not seeing that there doesn't exist any yet。

 I just haven't spent the time because he's made it very clear。 probably right now。

 maybe not the place you want to spend a lot of effort into。 That's just what I got。

 But something I might consider。 Thank you。 You're welcome。So。Yeah， I mean， exceptions。

 we've gone for the trade off that they're basically super cheap until you throw them。 right。

 If you were to keep the way that， I mean， the stood expected has a cost， right， Yes。

 that youre always paying。 if we were to。Take that optimization or that trade off decision away。

We could make you something that put something on the stack for every call avoid did these searches and other things like that。

 I anybody thinking of doing that or is that I just kind of like taking the thone type throwing it onto the stack。

 So if I if I remember information， let's say's for the wife。 Oh yes， yes。 every time you call。

 you could theoretically put something on the stack。 I would help Yeah， Brna said no。

 specifically back in St。 Louis， I talked to him about some of the ideas that I had and made it very clear He's like whatever you do。

 do not pessimize the happy path。 Do not make the normal process of the code any slower。

 I had this idea too。 I had him near point spent I know this may seem like maybe it's simple I went over it's obvious I spent like six months with a bunch of ideas。

 And that was one of them。 And I didn't want to have an operation that you call or you had to do when you call the function before you go further a bit out of time。

 But maybe put the next few， I think maybe go for。first of all， it was amazing talk。

 I really loved how you I really loved how you deliver this。 and thank you for that。

 second thing is that I don't know if you're aware。

 but Ru using linker for for Microsoft ecosystem you might have accidentally' it's really nice you might have accidentally been able to optimize well you for bringing this up because I had some slides that specifically said that some I was going put this in the future was like no care Yeah Ru does use exceptions。

 if you have a choice like have+ if you panic you can catch the panic that's a catch handler effectively as as I'm concerned So you can either have it panic and then abort or you can panic and somewhere else So yeah this would make panic and rust faster decided use last thing I just wanted to ask actually。

😊，I really love the techniques you've used it's actually really for cash for data drivenven optimization et cetera。

 so your plugging in the linker I think it will be interesting to actually observe this not just for exceptions if you could go over the binary and just optimize for all the parts of the code repeating all of that so I just I thought you it would be really cool to explore that and try to you know have that on it definitely。

Yabi。 Hey， think it the first time you having these kind of Yes， So two things。

 The first one is the interpreter。 So you probably know Python214 now is using the state columnptization。

 I really like it。 It's much faster。 It is so faster than M as youC got you know。

 kind of drag into doing it the same kind of thing。😊。

Reason why I like it is it is purely standard super fast。

 whereas the address of label is exactly requires these extensions。 you just need one thing， though。

 which is that you need a compiler to tell you when it cannot do tape column translation。

 So But it is more like， I can't do it。 So I'm telling you're supposed to。

I think if you could try that plastic make the patent on interpreter which is shipping with 3。

14 is much faster than the one that is labels driven。

 The other thing is the dynamic cast type of thing like when you matching the perception hiy。

 I think Bian， about04005 had the scheme that is based on Chinese Romanthereem。

 Oh I was wondering if you， if you try that。 I never heard。 I would love to see what send this to me。

 Yeah， yeah。awesomesome， thank you so much。 Thank you， everyone， for coming to my talk。



![](img/e434420cf0f20f8cbf4d8de3d1e4e8e3_7.png)