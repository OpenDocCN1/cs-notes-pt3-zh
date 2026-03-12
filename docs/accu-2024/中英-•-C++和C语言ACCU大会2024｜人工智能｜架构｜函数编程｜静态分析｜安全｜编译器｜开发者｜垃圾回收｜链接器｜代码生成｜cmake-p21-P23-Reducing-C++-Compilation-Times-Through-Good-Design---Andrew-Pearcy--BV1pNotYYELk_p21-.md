# 中英-•-C++和C语言ACCU大会2024｜人工智能｜架构｜函数编程｜静态分析｜安全｜编译器｜开发者｜垃圾回收｜链接器｜代码生成｜cmake-p21-P23-Reducing-C++-Compilation-Times-Through-Good-Design---Andrew-Pearcy--BV1pNotYYELk_p21-

![](img/9b6ced6067645c21f6042dd7d7aa9500_0.png)

Thank you， everyone， for coming today talking about how to reduce compation times through good design。

 So we'll kick it off。 I've got obligatory slide here。 So who am I。 I'm Andrew Pierey。

 I'm an engineering team lead at Bloomberg in the multi asset risk system department。

 which we refer to as Mars。😊。

![](img/9b6ced6067645c21f6042dd7d7aa9500_2.png)

A little bit about me。 I've spent the last four years working for Bloomberg。

 mainly on their C++ stack Before that， I have a master in mathematics and computer science from Imperial College London。

 and I'm here today presenting to you because we managed to reduce our compilation time down from one hour to six minutes。

 and so I'm going talk you through all of the steps we took to achieve that。

The fun fact about me is I have kayak on six continents and I actually led an expedition once。

 So if you don't have any C plus plus questions， you can ask me all about that at the end。我看。D again。

 So what are we gonna go through first we'll go through our motivation。

 Why do we care about compilation times， I'll then do a quick recap of the C plus plus compilation model so that we all know we're talking about the same thing're going go through some quick wins So some ideas。

 something you can just drop into your drop into your tool chain without having to modify any code that might give you some advantages We're going look at how we identified the bottlenecks in our compilation。

 then go through the techniques we applied and the improvement we saw from each of those techniques and then I'll summarize sort of the main takeaways and things we learned。

你看。One thing to get out of way first， this is not a talk on modules。

 I assume everyone knows what I mean when I'm talking about modules。

 Please put your hand up if you don't know what modules are。Okay， cool， but yeah， modules are coming。

 They should actually really help with the compilation problem because of the C plus plus model being backwards compatible outable with C。

 There's a lot of copying and pasting of code。 We have one question already。 Yeah。

 but I've related that the to do some of the lighting。 you got co like that stopped。

 that is a perfect point。 Can we get the lights dimmed in the front， please。😊，Because otherwise。

 yeah， all of my slides are going to be very difficult to read。😊，I'll give that one second。

But I will just keep going on the module front So the idea is modules should fix this problem。

But it's going to be a lot of effort to migrate。 you need to rely on all of your third party libraries as well to migrate before we can do that。

 So the main issue is going to be what can we do in the meantime in order to actually speed up our compilation before we can fully transition to modules。

Oligatory XKCD comic， who has gone off to get a coffee whilst their code is compiling。Exactly。

So our first motivation is we're looking at improving our local Devx。

 if it's taking a while for you to compile locally， you really have a lot of context switching。

 you set off your compilation。 you go get a coffee。 Someone interrupts you。

 you start looking at emails， etc。 you lose that context。

 you then have to try and regain that context to get back into your flow。

 You also suffer from something I call refactoring inertia。

 If it's gonna take an hour for you to build locally。

 and then it's gonna take another hour to run that on your C pipeline and then youre get someone to approve that as well。

Just making a small change to improve your code base is there's a lot of， yeah。

 inertia towards it so。The main thing here is if we can reduce compilation times。

 when you are starting a new project， you can check out， make your refactoring change。

 get that merged， and done quickly， and then actually do your full change without having to worry about your build types。

Next thing， speeding up C。 Everyone likes faster C with this， I mean， time to market。

 So if you're trying to get new features out quickly， if it's taking hours to compile。

 that slows everything down because you need to wait for it to compile。

 need to wait for all the tests around， you need someone to approve it。

 the other one is if you need to hot fix production or anything。

 then if it's taking hours to compile， then that could actually be crucial if your if you notice a bug in your production system。

Finally， the third sort of motivation is unlocking of tooling。

 we specifically wanted to look into static analysis， So by that we're looking at clang tidy。

 can I run some static analysis over my codebase identify bug prone things and just to check that I'm using best practices。

But the issue is if we're already taking an hour to compile。

 it's taking almost two hours to run static analysis and that's just prohibitively long。And finally。

 resource utilization， when you're working in a big company， if I can cut down my compilation times。

 I need fewer machines in order to actually do my compilation， cheaper to run less electricity。

 etc cetera， etctera。 So that's that's why we care。So simple plus compilation model。

 we have preprocesor by that。 How can we actually can people read that， okay。No， okay。

 Any luck on the lights。I'm want to try one thing real quick。These buttons don't do anything。

Is anyone noticing any change？No this might be a difficult presentation if you guys can't read the slides so much have to read everything out to you but hey preprocessor so hash include directive pulling in your headers you've then got macros and defining the meaning of life to be 42 you then have your if deaths and your if not deaths and then we get into compilation so once you have your intermediary file you do all of your passing and tokenization on that and then you do your template instantiation and then you get into the linking I'm not really going to talk about linking too much we're gonna focus mainly on the first two phases of this。

So going back to the preprocessor， suppose you have an A dot H file that is really hard to read。

If you're gonna hashing include a string， and then all I'm doing is just defining a class。

 which is returning a string。 Okay， very simple。So declaring class， not defining。

 And then in your CPP file， you have the definition for that function and so you include your header。

 you're also going include vector， for example， after you run the preprocessor。

 your 10 lines of class is going to be 17000 lines from the string preprocessor directive。

 whatever you have declared in your header and other 13000 lines from pulling in vector and then whatever you have in your CPP and very much what I'm trying to illustrate here is that the headers and includes in everything you're pulling in can actually dwarf the size of your source code so the time spent by the compiler passing through everything and building the abstract syntaxt tree might not actually be your code but all of your dependencies and that's what we're gonna to come to you。

On the compilation model as a whole。 So we've done the pre process aside。

 you get your doI files as your intermediaries。 you then pass that to the compiler。

 The compiler builds that abstract syntax street， does template instantiations。

 creates the assembly code in your do o files。 You then pull in any libraries。 the linker steps in。

 resolves all of that to a single executable and we're done。 Okay， so that's what we're dealing with。

😊，But before we do any of that， let's， can we actually modify this tool chain。

 So what are some of the drop in things where we're gonna look at the build system。

The linker and compiler caching because these are things you should be able to just modify before having't changed your source code。

 So kicking in with the build system if you aren't already using ninja and you have the ability to。

 So if you're using CMake。 I'd really recommend just dropping in ninja as your build system generator you can just do dashg ninja in your CMake and vacation and itll use build system it has much better dependency tracking than make a lot of profiling has shown that you can almost be an order of magnitude faster。

 then make when you are doing an incremental build on a clean build， there's a very little benefit。

 then incremental actually determining what needs to be rebuilt Ninja is significantly faster。

It is designed to be used with a metabilt system you're not meant to write Ninja files yourself so it integrates nicely to CMake and a few other tools。

 full documentation on the website， it was originally written for Google Chromeium I believe when they were just getting far too frustrated with the amount of time it took for make to figure out how to build things and there's a little bit more profilings well that yeah order made suit if on a noop build it can go from 73 seconds for make to figure out that nothing needs to be rebuilt and Ninja can do in a second so less time having to wait figuring out what needs to be built。

 the better。So that's just a quick drop in replacement on the build system。

 Oh and yet it uses all available cause by default。 You don't have to specify how many cores to use。

 It just assumes you want to use everything。 you can tweak it if you want。

 but one less thing I have to default。Next up， Liers， Okay， have we had any luck on the lights yet。

Okay， I'll take that as a no， but we'll just crack on I'll just。

 I'll just use my voice to talk through all of the code。

So if you aren't ready LLD significantly faster than a default linker so if you're using LD or gold。

 please do look at LLD a lot better parallelism and custom memory allocations。

 which gives it that benefit and it can be 10 times faster than LD in a lot of cases very easy to use you can create a similarim link or you can just pass dash dash F use L where I'm already getting tongue tied at trying to look through code you can just pass it as a command line argument if you want to。

But even more recently， mold， you can try out mold as well stands for a modern linker even faster than LLD written from the ground up by Ruy。

 who also worked on LLD。 So he knows what he's doing even more parallelism and efficient data structures。

 the design do on the website is actually well worth a read because it details exactly the design that he tried why they wouldn't work and the final design he went with。

 So if you want to learn the internals very， very well documented。

One of the downsides is open source on UniX platforms only。

 I believe it is paid for subscription service on Mac and Windows。

 so I apologize if you're on one of those platforms。

And the only of a potential downside is it does use more memory than LLD。

 So if your memory constrained， this does use a little bit more memory because of the data structures it's using under the P。

Quick comparison So just looking at building clang with the standard linker 42 seconds gold 33 LLVM we get down to five it's pretty nice mold is almost five times faster than that so you can just drop in mold and not even worry about it linking is solved maybe。

Okay。Thats linkers next up， compiler caching。 Who is currently using compiler caching。 hands up。

 please， want it。 Okay， a few， great。 for those of you who aren't really recommend。

 Ccash is what we've gravitated towards。The whole idea here is you create a hash of the preprocessed translation unit。

 the compiler and the flags that you're using， and you hash that to your object file。

 And what that means is if you are doing a clean build ordinarily， you working on a branch。

 you check out a new branch， all your timestamps are updated， you have to do a clean build。

With Ccash， because it's hash the actual preprocesor of the translation unit。

 if it hasn't actually changed， it'll just return that directly from the cache and you can get an order of magnitude speed up on your builds。

The other one for rebuild on incremental builds， generally speaking。

 you've changed what you're working on， so you're going to have to rebuild it anyway。

 Ccash doesn't step in but he。You can set up similar link for that。

 or you can do it as a commandline argument。Or you can just prepen anyvocation you have of your compiler with Ccash。

 They recommend just letting Ccash masqueraadas your compiler because just forward everything on nice and easy。

 One nice thing is it does support HtP and Redis backends for cash sharing between users。

 So if you have a team of people or working on the same thing。

 you can set up a Redis cache between all of you。 if one person builds everyone else gets the benefit。

 if you can do this for your C pipeline even better because then like company wide。

 you're getting a huge， huge benefit。Trade off being is that if you can't set up Ccash for your CI pipeline。

 there is an overhead for the cold cash because it has to write everything into the cash in the first place。

 So if you're doing clean builds in a completely new environment。

 you're not going to want to use it so it really depends on your use case for your CI pipeline。Okay。

 that's everything on the quick wins。 So just let drop in replacements。

 So we're going to drop into the hay study next。没有。So as you can see。

 what we were dealing with here at a mono repo。Building multiple executables out of that about 1200 translation units。

 not the largest repo， not the smallest repo using CMake， as I at a build system and ninja。

 you kind of see why I was suggesting everything beforehand and compiling with Gcc。

 And when we started out， our build time was about one hour， which we thought。

We thought was a little bit too long for the size of our project。

 It'd been building incrementally over time。 I feel like that naturally happens with a lot of projects。

 the larger it gets， the graial compilation time gets until it is annoying enough that you go and do something about it。

So what did we do？Well， the first thing you need to do is actually figure out why your compilation time is slow。

 and this is where I love premature optimization is the root of all evil。

I am a big fan of do not try and optimize until you know where the problem is。

So how do we figure it out。Any， any ideas from the audience。

 how do you figure out what is taking so long in your compilation？

Sure apply you build process Profiling your build process， exactly， how do we do that。

 There's open source tooling。 So Kang's Ftime trace flag is what we relied on heavily for this。

 And what it does， it will create a flame chart Jason file of every single translation unit in your build。

 And as you can see on the right hand side， you can actually see how that is expanded。

 You can see which headers is pulling in， what headers those are pulling in all the way down to the actual function instantis through that tree。

😊，I do have a quick demo because I discovered the other day that you can do this in Godbalt。

 So if we're on Godbalt and we're including I O streamream。You then have just your square function。

 and we're just gonna print the input。 and we're gonna print the output When you run this with F time trace on Kang 9 or newer。

 it'll generate adjacent file for you。 And you can actually view that。

 So you got the front end the compiler。 We have I O stream and then Istream going through Ios all the way down all the way down does。

String and it'll actually tell you what percentage of the time in your compilation was spent on every single component。

 So this is where we started to try and actually understand in each of our translation units。

 what is taking the longest time and what is there that we wouldn't expect to be there。

Theres the original blog post about this guy who implemented it。 That was where we started。

 and then you have Kang build Anar， which is another layer on top of the output。

And what KangBuildd analyzer will do is take all of these J files， figure out， sorry。

Which were your largest targets what most time to compile， what headers were included the most。

 which template instantiations took the longest amount of time and is generally where all of the time is spent in your compilation phase across the entire project so you get both the high level view and you can look at the individual drill down of every single translation unit。

Okay。So this is what our build time evolution looked like。In December of 2022。

 we decided we had a problem and we' were like， okay， this this is too long guys。

 let's try and do something about this。 So what we decided is that in our team。

 we have biweekly hackathons where every two weeks we take half a day and we try and improve the system to make our own lives easier。

 and that is where a good two or three of us in the team would use those biweekly events to try and analyze what the problem was and how do we actually reduce the build times。

By April， we'd gotten down to 15 minutes just by applying some of the techniques。

 and we were reasonably happy with that a quarter of the time。 That's quite nice。

 And we kind of left it like that for a another little while。 And then around about August。

 September time， we took another look at it is like can we get this even faster when we got it down to six minutes by the time we were done。

😊，对。So how do we do it， The techniques we applied is nothing revolutionary， but forward declarations。

Removing unused includes， as I showed with the pre processorces， even whatever include you have。

 copypy and pasted into your translation unit。 The compiler still has to read it and still has to go through it。

 I definitely have suffered from this where I'll try and write one implementation。

Of a new feature I'll include like say I include the set and then I change my minds。

 I'm actually gonna to use a map instead， but my Inence has really helped me out and included both of them。

 even I'm not using them So trying to do trying to actually disem you're not using include just get rid of it you're giving you're giving the compiler additional work Spitting protocol and implementation or'll go through an example of that but just trying to really separate the interdependencies of your code base if there's implementations that other parts of your code don't need to know about make sure they don't know about them because then you don't have to pass through the same files multiple times。

Object libraries touched on that real quick。 slightly more on the linker side and just sort less again。

 less work the compiler。 I'll give an example of that and how we tuned that。

 Looking at pre compileiled headers。 Is everyone using pre compileiled headers already。Few， okay。

 see a few。 if you're not， please do。 That ones should be very straightforward。 And finally。

 we'll get into Unity build and how we transitioned our project to Unity build。嗯可。

So forward declarationations in headers。What is it。Formerally。

 forward declaration is when you can declare a class type， which will be defined later in scope。

 And until that definition appears， a class has an incomplete type。 That's the formal definition。

Generally speaking， if you don't need to know the memory layout， you can forward to it， okay。So。

 what we're looking at is if you have a head of file， I'm going call it A， I quite like A And B。

 I'm sorry。 I'm not necessarily the most creative person in the room。But if you have A dot H。

 and that includes some large header because my A dot CPP is going to need that large header。

And then you happen to have B dot CPP， which pulls in some of the features from A dot H。

 you're transively including your large header。 And so now suddenly B dot CPP has to know about this very large header as well when it doesn't use it。

 but when you're compiling that translation unit， you still have to pass it， okay。S。😡。

With forward declarations， can people read this one？Yes， okay。

 Maybe I should have gone for for that sort of font， or sorry。Sade。

So the fourth declaration is my class at the top。 Okay， we then have another class。

 which is going to use that on line 7。 You're gonna have the declaration of a method totally fine to take a reference or a pointer to that class。

😊，On line 8， you can also take an instance of that class as long as you're not using it。

 So it's fine in the decoration for member variables。

 On 10 and 11 reference and pointer but fine for exactly the same reason。

 you don't need to know about the size。 They have a standard size。And on line 12。

 you cannot take an instance because you would need to know the size of the object。Line 14。

 you can return the pointer and use it as long as you're not accessing any of its members and just forwarding it around。

 you can't return an instance of the new class in the definition because you would need to know its size to actually use it。

Ls 16， similarly， you can't actually use the glass for exactly the same reason when you're doing the definition。

 you' got need to know what's in it and for somewhat completeness。

 if you're trying to use the incomplete types。 So if you're trying to access any members via the pointer or via the reference how you can't do that because you don't know they exist。

嗯，看一下。So that then brings me on to forward declared headers。 hass anyone used iOS forward？Yes， yes。

 okay。 Okay good you number people。 For those of you who don't know。

 Ios forward is literally a header of forward declared classes for ios streams from the standard library。

 And the idea there is， if you have a header， you have a print function or some of a function that's manipulating O streams within the header。

 you don't need to know about the implementation as long as you're just taking a reference to the stream so you can use ios forward in all of your headers。

 which means you're not forcibly including the full Iio stream header everywhere。

 you only really care about the CPP files where you're actually going define these functions。

Significantly smaller than the standard I S header。

 It is genuinely 128 lines versus 26000 lines that you have for your compiler has to pass through。

 So if you're not using that already， I would recommend it in your header files。

The other one is consider creating dedicated header。

Dedicated headers with four declarations for your classes or if you are a library owner。

 please create them for your library because users of your library can then take the forward declaration as long as they don't need to know the size and they can actually reduce the amount of times they have to compile and pass through your headers。

On that note， there is a Google style guide on this on four declarations when you should and shouldn't do it。

 The rule of thumb is very much you can declare what you own if you don't。

 if you let don't forward declare what you don't own and it is strictly undefined behavior if you try and forward declare anything from the standard library。

 don't do that。K。There we go。Removing unused inclas。This one always finds a little bit tricky。

 There is some open source tools， like include what you use to try and scan through。

And figure out if you have any headers that don't actually need to be included。

 It is a slightly tricky tricky problem。 If anyone knows of any better tools。

 I'm all ears because we really struggled on this one。 We tried to write our own。

 We've had a few issues。 They're kind of some false false positives a lot of the time。

So that's one option is just trying to scan through， get rid of headers。

 Another one is if you want to do this yourself， if you haven't used graph this。

 you can take a look at that。 it， you can plug it into the CMake API。

And it'll generate a graph of all of the dependencies within your project。

 So you can see what depends on what。 And if there's anything a bit unusual。

 you can drill in and be like， well， why does this depend on that。

 And that actually helped us identify that we had some cross dependencies from unused includess where things were forcibly relying on our libraries。

 even though they didn't use it。On that note， another thing we found is that we had a lot of code Gen via like proto buff for certain types。

And generally speaking， when you need to know about the types from another library。

 we were just including the entire schema for of those types。

 and some of the schemas are 250000 lines long of code that you need to pull in and then pass through every time。

 And so this is where we came down and said actually， the more granular you can get。

 the better for your includes that you're pulling in to headers because you're just trying to reduce the amount of work that you're putting on the compiler for every translation unit。

And then， yeah， you're also using graphes， so。In combination with clangbi analyzer。

 again getting that visual representation of dependencies within your code。

 is there anything unusual， what are your heaviest includes。

 what is that dependence bond can I break this up a bit so there isn't so much interdependency and all the code is being called in everywhere。

That everything on sort of includes and for declarations。Next up spinning protocol implementation。

 which another favorite quote， and so of any problem with an extra level of indirection。

 I think that sums up sums us up very， very nicely。 So again。

 the point nothing revolutionary but pmple idiom points implementation or inheritance in this instance you're trying to hide away the implementation so that not everyone needs to know about it and again。

 decoupling your system。So get that implementation specific include out of your header you should only ever need to know about it in one place and then everyone can sort of try and rely on something more abstract。

 it also gives you a really nice sort of testing architecture because you can swap things in and out。

This is very much where sort of the title of the talk comes from is that this technique really saved us and just gives you good design as a result as well。

 less dependency between your code， less work for the compiler everyone wins。

No apart from maybe at runtime， we'll get to that。But yeah， we， again， we profiled。

Trying to figure out what are our most include headers。

 And one thing we found is we have 1200 translation units。 Okay。

 we have this translator and it relies on TCP protocols to call out to another service to translate basically on like a hash mapap idea of things like I have a key。

 I need to know what this key actually translates to for a given language and that that TCP client was included 500 times throughout our code base almost every other file was knowing about it。

Here's a quick diagram for everyone。Left hand side， if you have your large header。

 I've got translator on the left hand side。We have this large header。

 which is our TCP client and that needs to be known about in the translator do CBP。 then you have A。

 B and C do CBP， which all need to know how to translate something and they're transitly having to pull in this really heavyweight header when they really shouldn't have to know about this。

 And so the term which actually I've seen in a few talks and is referenced on is on CPV reference is trying to create this compilation firewall。

 you inject your interface between A B and C and the actual implementation and now A B and C only need to rely on this very lightweight abstract interface and you reduce the heavyweight lifting to just the only implementation class that needs to know about it。

Okay。So。This is okay， I'm going to have to talk you through this。It just实。

So I mentioned before we have a TCP client。 That is our include。 Okay， that's quite heavy。

 We then have a class， which we're gonna call label translator。

 and that label translator has one function called translate。

 which takes an I D and a language that we need to translate it to。

 And that's what all of our clients care about is that I'm displaying messages。

 I'm auditing something I need to give feedback to the user。 I I'm going take this error message。

 translate it to the appropriate language and return it。

 And what it had is a unique pointer to a TCP clients， which we're including。😊。

For those who have been paying attention and haven't fallen asleep。

 we haven't forward declared this TCP clients because it's not in a namespace that we own。

 So in this case， we do actually have to include it because it's not ours。

 So that's why we're not forward declaring。And so what we did is just split that protocol up。

 create an abstract class for label translator where it has a virtual method for translate to the only thing it does。

 only thing has to worry about very， very lightweight and then。😊，You create your implementation。

 which we're going to call a caching label translator。 it implements the translate function。

 and then it holds the pointer to the TCP client。So in this case。

 now you're doing the abstraction away， only the implementation needs to know about this really heavyweight class。

 everything else doesn't。 it can use the really lightweight label translator interface。

So what that get us So I said， is included 500 times。Big。Before we refactored。

 it took three and a half seconds on average to ask。And the aggregate build time was 1500 seconds。

 so we're spending 25 minutes looking at this file every single time。

It I was going to say I should have mentioned actually what hardware is compiling on。

 I technically can't tell you what hardware we compile on。

 but we'll just assume for all intensive purposes that it was a9 gen I7 of 16 cause and 64 gigs of RA and yes。

 I can't put on writing。But I said。Three and a half seconds to pass they include every single time。

 25 minutes aggregate compilation time， we got there down to 20 seconds and so just removed 25 minutes compilation time just by doing a small refactor because 500 less times having to pass this really heavyweight header。

 okay。I was spending like a round of applause or gasp so， thank you。😊，Perfect， see。

That then takes us on to object libraries。 Is anyone using object libraries。Okay。

 a few people so and standard C+ plus compilation model is you have a file， you have your header。

 you combine those into a translation unit， you take that。

 create an object from it okay so you have one object for every file with an object library what you're trying to achieve is grouping your files together so that you're actually creating one object from a collection of files。

 the idea being you can reduce some of the linkage time if there's common shared and limitations between all of those objects and just generally trying to create fewer files in general。

So one thing we had is 40 individual test executables in our code base。

 so all of our different test files， each one of those is creating a different object file。

 each one of those object files is being made into an executable。

AndWhat we noticed is that there's a significant amount of time redoing the same work between every excutable and the same linking because all of these use G test。

 all of them have to put all of that in。 And so can we。

 can we sort of de duplicateuplicate that work。And so what we ended up doing is with CMake and the a library directive is you can actually merge audio test executables into one。

And then you build just one executable。 You run that for of your unit tests。

 We run that for all of our integration tests。 and that took out two minutes of linking time just by doing it this way。

 And so what we end up doing is that。I'll skip skip through。 Yeah， there we go。

 So on our CI pipeline， we merge everything into one giant executable and run thatca we're building from scratch when we're doing iterative development。

 we are we are compiling the individual test executables because it's very likely that you're touching a small part of code。

 you don't want have to recompilele all of your unit tests every time you're just changing one or two implementation details。

 So for that， you can make it configurable in CMake when on a pipeline。

 build everything into one executable and run it when you're doing it locally。

 we can actually get the granularity that we want to make our lives easier。😊，Precomped headers。

 I think I' I mentioned this one。 We did some hands up。So， formally。What are preconed headers？

The idea here is you can speed up compilation by creating partially processed version of some of the header files and then stores that in memory。

 and it will reuse that instead of having to go through the headers again。

To this was actually added in CMake 316， it works very well for headers that are often included and don't change by this I mean standard libraries。

 So you're looking at vector string as well as third party libraries。

 we decided not to do it for our own headers because we find they're actually changing significantly often and the issue you get with precomplied headers is you create a target for them。

The build system will generate the precomp part headers first because it then gets forcibly injected into every single translation unit。

And then you you get that benefit of it's already in memory， you don't have to pass through it again。

 you have the abstract syntax tree。 And so instead of having to pass through stood vector 1200 times you've done it once。

 So the benefit you get from this is heavily dependent upon how much of these standard of how much of these headers are used commonly throughout your code and how much commonality there is between each translation unit。

It does require some tuning because if you try and just add everything to your precombald header。

 you actually start to get diminishing returns because it gets too large and then you're forcibly injecting too many things into each translation unit and you're you losing that sort of common shared code that you only have to go through once。

I mentioned that。And determining which ones， this is where clangolds analyzer can come in because it'll tell you exactly which headers are used and give you the count。

 And I think you can parameterize it to say how much output you want to give it and just tell me everything。

 and it will list all of your headers How many times they're included。 We add， yeah。

 huge benefit from the standard library headers。The example is is quite。

 So what I'm trying to demonstrate here is that if you have CMake and you have a library there you're creating。

 which we're gonna call F， and then you have two CPP files。

 you can then just have target precompiled headers against F and you can either just list in here。

 So we have ios functional string C math。 and it'll actually generate the precompiled headers for you。

 So just create a C make， underscore precomplied headers or HSx。

 it'll hash include all of those for you and then do the representation。 you can。

 if you want to just write this own file and then target it whatever suits you but just a quick example of how to do it in your project。

😊，그。Some of the gotuchchas， as I said， less is more。 as this gets too big。

 you get diminishing returns。This was a fun month。We discovered that we enabled prega mod headers。

 and then we tried to compile and clang where we didn't have pregaard headers and it wouldn't build。

Reason being， if you have vector in your pre compilelied headers and then you have a new source file and you forget to include vector。

 it gets forcibly injected into that translation unit by the pre compileed headers。

 so you don't have to include it。 Great。 I have to include less things。

 but that's lazy programming and you're broken your build。

So we had to actually go through and fix all of those and so we recommend is that on a regular some sort of regular cadence just in a regular C bills or something with precompiled headers turned off so that you're ensuring that you're not breaking your bill yeah。

And we got a 20% decrease in build time just by turning on pre and B headers， a little bit of tuning。

 trying to find the right spot。 we started very small。

 we then started adding third party libraries and then we tried adding some of our own diminishing returns once we got to our own headers。

 some people depending on your project by your differences but yeah for all。

A quick change to recompile list some letters， terms and decrease。 I'm pretty happy with that。😊。

This is just a visualization of yeah， the pre compileed headers that you're generating up front。

 you then forcibly inject。 One I got you with these is that if you change your compile flags。

 that also invalidates the precompiled headers is that you have to ensure that you're using the same the same flags at the start。

 And so you do have this now big dependency at the beginning of your build。

 which could force a recompile of everything。 So it's just being aware of that。Okay， so。

All of those techniques so far。Got us to April， so we got down to 15 minutes just by four declarations。

 splitiing protocol implementation， pre compileed headers and then object libraries。

And then we left it for a little bit we okay， let's let's give this another go and let's try and take this approach of limiting the amount of redundant work the compiler is doing。

 Let's take it to the extreme and that's where we come into Unity build。Who knows what UNtu build is？

Okay， phone number， who's using Unity build。A few， a few less。Okay， for those using it， I'm。

 I'm sorry， I might not have too much revolutionary for you， but those not using it。

 you can see what we did。The idea of unity build is you have your translation units。

 all of them are using vector， similar idea to precomplied headers， remove the redundant work done。

 and you're putting those into a library， if you just hash include those files directly into one。

 you only have to pass through vector once or whatever header it may be that's shared between them to create your library。

Taking this all away to the extreme， if you hash include every single source file into one。

 you only have to pass your code once fully， and so there's no redundant work being done。

If you go to that extreme， you then completely lose parallellyization because you just have one file to pile。

 So the thing with unity builds is， I think you're really trying to find the right level of granularity。

And that's where the default configuration comes in。

 So you can enable unity build on your product if you're using CMake by default。

 if you just say enable unity build mode true one， whatever， and it will default to a batch size of8。

 and what CMake generates， which you can't see。Is just a file that hash includes all of your files。

 So we have widget。 we have component。 We have my act database accessor， just hash included into one。

 and it will bulk those into eight files at a time。

 one so that you don't have too many files in one go and could eat up your memory a bit more。

 but two， you still want to get some parallellyization。嗯。If you in theory。You can enable unity bills。

 your project compiles。 Everyone's happy。 If that works for you， I'm very happy for you。

 That didn't work for us。😊，The first thing we noticed is anonymous namespaces， each translation unit。

 anonymous namespace， nothing is accessible outside of that translation unit。

Now you only have one translation unit。 so anonymous namespaces are no longer anonymous。

And so if I have print in one file and print in another file， or that's now a compiler error。

And you have a few options。 you can go and rename all of your functions that clash。

 You can rename all of your anonymous name spaces and reference them to the file if you want to。

 But thankfully the CMake with its unity build built in gives us something called unity Id。

 And so you can actually specify this in your C make on a per library sort level。😊。

So we specified our as Unity ID what it does is it puts a unique namespace in for you。

 And so you no longer get the clash between all of your symbols。

 There is a little bit of annoyance because depending on how much you're using your anonymous functions within because you're now in one translation unit you would need to be pen the calls with the unique unity namespace。

 This is something that can just be a little bit of annoying work to do on a late Friday afternoon or we experimented a little bit with trying to use clang query to try and replace and get this in。

 didn't quite get it working but got something almost working to do it。 So those options。

This is just gonna be a quick talk through again which you can't see， but in the CMake。

 you can set the target properties to say for whatever my target is。

 I'm defining a unity build unique I and then what that actually does under the hood is when each CPP file is hash included it defines a unique unity I and then undefins it Nothing magic going on but that's what it's doing under the hood。

Next up， bills template instantis。Sorry， template stas for unityBuild。So much talkingking。

 because you cannot read the slides。 I will bear this in mind for next time。Yes， sorry， a question。

 Oh let's get the Yeah。 we'll get the mic。It。We also had the problem as with anonymous namespace with static variables yes。

 because they also then are are doubled Yeah doesn't comp Yes。

 exactly the same issue but yeah thats again you can solve the same thing put it within a names anonymous namespace it's annoying but yeah。

Oh not thank you。 another question other thing that is a problem is that we usually in a CPP file also use using namespace because we use namespaces and then we should start to use namespaces in all CPP files that you put in your unity built you get in Yes。

 yeah， that is an annoyance。 So this is kind of I think the issue we ran into as well as if your code base was not initially written to be unity build compliance。

 it is surprisingly difficult to convert it to a unity build。But yeah， thank you。

Cracking on template instantaniations。 So what we have is a header file where I'm gonna have a templated function that takes a vector of type T。

 And I'm gonna do something generic with that。 And then in my CBP file for that。

 I'm going use a template。 And that's just gonna call my generic function。😊，Everything's fine。

 And then in another file， I include the template because。I might need to know about it。

 And then I'm gonna have a specialization of。Now function。

 So I'm going to now do something specific for vector of ints。

 and then I'm going to use that specific implementation and try and apply the function。

To my vector ins。 and once again， the compiler will complain at you because depending on the order that you include these files。

 you are trying to specialize a template after it's already been instantiated， which is disallowed。

 So one option is you can just reverse and lexographically order your files in the name they need to be included。

 I'm not sure anyone's happy with that。 but there is a solution which I'll come to after one more example。

Temp overloading。 So here I'm gonna have a print function， which is gonna take a vector of dates。

And we're just going to print out all of those dates on the same line。

 but we also happen to have a templated class of print anything which is going to print all of my vector of T on the same line with comma separated。

 and this will compile perfectly happily， but it'll change your implementation。

Because now you're hitting the specialization for dates and sorry the exact function for dates rather than the template and there's no safety around this compilerrs perfectly happy to do this。

 The only way we notice this is we have tests around the audit logs when when we're changing things and we suddenly noticed our tests were failing because the output format of the audit log was different because we had two different ways to print a vector of dates。

 So that's the one I really want to beware people of is that you could change the underlying implementation of your code and you wouldn't know。

So what can you do about it？This， I'm gonna skip I don't w to skip forward。 Okay。

 slightly out of line， but we'll， we'll come back to it。

 So I'll talk you through third party libraries。嗯。🤢，Yeah。Again。

 I'm gonna continue reading out code from the board， but we have astruct component。 We have an enum。

That enum has a widget， and it has a pulley。 I'm sure you can guess where I got my inspiration from。

We then have our unity file， which includes one file A do CPP that pulls in some other headers。

 we have B do CPP， which pulls in our component。And then we get a wonderful compiler error。

 Can you read that one。Yes， maybe red is about a colour expected。

 identify before numeric constant widget。And this one actually through me for a while because I wasn't too sure what was going on。

 Does anyone have any guesses。Okay， that makes me feel a little bit better because I was quite stumped by this for a while。

 So I went back and looked at component。 Okay， component is a third party library。 I look into there。

 we have widget。 widget is perfectly defined as equal to。

 Am I is something redefining widget somewhere， So I start going to look into all of our third party libraries。

 Do we have another Eum declaration for component defining widget。😊。

And I finally broke down and went， okay， let's just run the pre processoror and see what's going on。

 I was trying to get some inside。 And this is when I had that the enum value gets replaced with 7 equals 2。

😊，And this is when I looked at it。 I was like， I can see why the compiler is complaining。

 I can also now see why the error message is so vague because it's pointing at the source code issue。

 But the preprocessors manipulated that。 And I went and spoke to someone I was like， well。

 surely we'd won the pre post pre the post processing output。

 So we can actually see when this replacement is done。 Nobody realize that was a terrible idea。

 But the main takeaway here is that。Maros are really annoyed。In that。

 in our products in a separate third party library， you have a macro。 It defines Wiidgets 7。

 And as soon as you combine these two third party libraries， they are completely incompatible。

So that was a fun afternoon figuring that one out。 And what are your options。

 You could either not use these two third party libraries together。

 You can try and go to the third party library owners and say， hey， can you change that。

 Good luck with that one or you can actually use what you make for of。

 which is how do you isolate specific files that are known not to compile together。

 And you have a few options。 So coming back to the macrovocation as well as。😊。

The specialization where you're changing the code implementation underneath without knowing is that Cm will actually let you skip unity build inclusion on a per file basis so you can just specify that hey for this file。

 I don't want it to be in my unity build It is just gonna be compiled separately。 Okay。

 and then you get the isolation that you previously had Co the other option is you can group files together via unity group。

 So by default， CMake will just take eight files leographically mash them together if you want to。

 you can manually specify we've done this in the case with the third party libraries because。

We kind of knew that this set of files is using that 30 part library。

 the set of files is using that one will force these to be compiled separately because they should share a lot of the same code as well。

 So if you have some insider knowledge on how you're compiling and what's likely to go together。

 then you can use that。So what are the results？I spoiled it a little bit already with the graph。

 But when we got to unity builds， we had 1200 compilation， sorry，1200 translation unit。

 I think there's a slighttypo there。Took 15 minutes to build when we enableds Unity build by default。

 batch things in degrees of eight， creates about 240 targets and we go down to nine minutes。

 and then if you just set unity build to infinity so for each of our libraries just shove everything together we got it down to again the typo well I'm doing well six minutes sick。

Not 7 minutes。 So that's when the factor of 10 comes in。

 But the other thing that we noticed is I mentioned way back at the beginning that we wanted to try and unlock static analysis and try and apply clang tidy to our code base。

 And it was taking about 2 and a half hours when we started。 Well。

 when we got the compilation down to 15 minutes。 we're in about 40 minutes for clang tidy。

 which is okay。 But then doing it of unity build， It took four minutes。

And this is the one that actually surprised all of us。 And weve thought about it for a while。

 And the only thing that kind of makes sense is that if you think we're a factor of 10 different。

On number of compilation targets， we're pretty much a factor of 10 faster because for your static analysis。

 you don't have to worry about any of the linking or anything。 You are just。

Completely cutting down the number of headers you're including because you're not having to pass them additionally。

 And so as long as your includes to the size of your source code。

 I reckon you can get sort of similar relative speed up to this。嗯。But yeah。

 that takes us to 55 cent reduction in build time an up to 9% reduction in static analysis。

 so we can actually use static analysis now。A couple of considerations on unity build。

 You might not get a benefit for incremental builds， because if you're slamming all of your。

Soce files together， creating larger translation units。 If you're just changing one thing。

 you have to recomple the entire thing。 It's a little bit annoying。

That's when it depends on the Unity group build size， choose your granularity。

 how much do you want to build together？Next one is clean builds will benefit the most because you're building from scratch。

You have nothing whilst in the I build case， we made this configurable。

 so when we're building on our pipeline， we do a unity build， it's faster。

 run ourat when we're building locally because we don't want to have to suffer that incremental build sort of issue。

 we actually tend to build in the old school manner of individual targets because we're touching fewer things at a time。

Same thing as pre about headers you can break your regular build with you to build because transitive header includes from putting everything together。

Again， same recommendation as precomd headers just on a regular basis and make sure you're doing a regular build so that everything is happy。

 you can run into ODR issues and have a building abilities So a little bit wary or say much time it takes and if for whatever reason you don't want to do you need to builds or too much effort。

 my general advice would be try and reduce the number of files you have if you have lots of small files。

 you're trying to compile those in parallel if they're again pulling in all the standard library or just sharing any components。

 fewer larger files better than lots of little ones。 So just the general idea。

That takes me on to main takeaways so just a quick summary of everything we've been through。

First thing， profile your build， don't chart， don't start trying to reduce your compilation time before you know where the time is actually spent forward declarations。

 I'm going to say sort of reduced our bill time by 60% with an asterisksters because it was in combination with removing and even includes an in combination of splitting protocol implementation。

 just trying to remove the interdependency between all of your code。



![](img/9b6ced6067645c21f6042dd7d7aa9500_4.png)

Emerging excutables go about 10% difference on that just by not having to do additional link time。

 tuning pre compileiled headers， 20% difference on that really easy chopping replacement very level can go wrong with that in my opinion。

 very safe and then 50% of reduction with unity build， but there is a small risk。Just to be aware of。

That I think is everything I have for you。 I have rushed through that very quickly。

 The only only thing I would say is just a thanks that to my teammate， Dallas Clement。

 who I worked very closely on this project with and to the entire team of people I worked with because it's a big team effort over time。

😊，那是。Thank you。So totally。啊，调感。

![](img/9b6ced6067645c21f6042dd7d7aa9500_6.png)