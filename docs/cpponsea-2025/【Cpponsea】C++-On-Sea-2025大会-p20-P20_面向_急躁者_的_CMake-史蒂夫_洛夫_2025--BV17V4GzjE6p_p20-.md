# 【Cpponsea】C++-On-Sea-2025大会-p20-P20_面向_急躁者_的_CMake-史蒂夫_洛夫_2025--BV17V4GzjE6p_p20-

Hi everyone， thanks for coming along and last chance if this isn't the talk you intended to come to。



![](img/d26792cad1c0bd6090276fb8a0896106_1.png)

You're going to do a talk about CMake， I really hope you're not expecting anything really startling because this is a talk。

From a seam beginner。I just will become parent。But these are things that I've picked up that I found useful。

Excuse me， and I just want to pass that on and hope that it's useful to somebody else。😊。

So this is me in various places。And。I'm not hard to find。But please get in touch if you got。

Any comments after the fact， but yeah， speak up with questions if there's anything that's not clear on the way through。

Anybody that。Recognizes me at all， knows I'm not a C++ developer。And I'm a dotne guy。

And so written a couple of books about donet， but that's not what we're going to talk about。

But it is relevant。😡，Which will become also found in a minute。So is this talk for you？😡。

I wonder if you're one of these three eggs。There's a guy on the left and looks a little bit anxious about something。

In this case， C make。嗯。Or drumy about it if people mention it because。You know。

It's difficult or you in the middle just sarcastic if somebody says see me， I'm not doing mate。😊。

So I was all three of these when it became apparent that I needed to do some stuff with Cic。

So if you're any of these eggs， then hopefully。😊，I'll have something that can help。My background。

Although I've been doing got that development for。Decades I originally came from a CC++ developer role。

And。Microsoft Miss Studio has been a constant companion。Really throughout my career。

 but doing C+ Preler particularly long ago in。Sort of C++ 98 kind of environment。

But the setting up visual Studio hasn't changed that much。In all that time。嗯。And doing things like。😡。

Figuring out where how to include custom include paths。Liinked to static libraries。

Set the version of the standard library that you want to use。

 all of these things are usually done in visual studio property pages now IDs vary， some are easier。

 some are harder。🤢，If you're already familiar with command line tools like make。

 particularly on the Internet space systems， then。The seamate stuff will probably be less unfamiliar to you。

🤢，But if you come， as I did from a Windows， predominantly youre in those environment using dialogueog boxes like this to configure your system。

Now this was the property pages in visualual studio they're very， very comprehensive。

 You can swiwindddle all sorts of switches and you can even import property pages as。

Kind of as text so that you can put them under version control so that everybody can share the same settings。

 but it's properly arcane stuff。You know， working with custom property pages in Visual Studio is really not for the faint of heart。

嗯。Even。Less for the fact of heart than using seamakers， I think。So。I wanted to get away from this。😡。

About a year or so ago， I was。Doing a C++ talk and again。

 this was a C++ talk because me is not a C++ programmer。

But it became apparent that doing all of the configure using Cmate was just going to be easier because I wanted a little packed environment that I could put into person control and it would work for。

Feaial Studio we had worked for。GCC tools on Mingo I could use Windows substem for Linux if I wanted or needed to and the config would just work and that is the magic of Seemate that's the headline thingme。

Right of why you want to learn Cmates because you've got this little packaged environment for simple stuff。

 it genuinely is quite simple。And you don't have to worry about twiddling switches in property pages。

So that was my motivation really， for getting to grips at least a little bit with seaing。

Set the plan today。Is， I want to show some simple examples and do a couple of little demos。

Introduce some core important concepts。The idea is not really to make you into CMake experts。Sorry。

 but it isn't。What I hope to get across at the end of the day is to or well I want you to be able to take away。

😡，Is to be that you can recognize the general structure of a CMake project or。In the small ACM file。

 but slightly larger than that because you can have more than one。And we'll talk a bit about that。

 but it also might help you get started from scratch。嗯。Rather than trying to。

Figure out from first principles what a Cm file is and if you're not， if okay， quick shot of hands。

 anybody never seen a Cm configuration file ever。One person so。

Are you familiar with when I say CMake， do you know what I mean。

 have you run a CMake command line to build somebody else's software， okay？

You might be the ideal person in the audience。I。What I want to do is this is one of the Cm files that I use to build the code that backs this talk。

 I'm not going to be showing an awful lot of code to be honest。But what I want to do is to stop this。

🤢，From when you open a file that looks like this。From turning into gobbledy。😡。

And if you don't see the difference between those two slides， then this talk really。

 I hope will be useful。Because when I first。Soce you make。

I suppose Ill to step back a bit is although Visual Studio at Microsoft Visual Studio has been a companion of mine for a long time。

A few years ago。Discovered sealine from Jetbrain's people， and I love it。

 So I've been using their tools four years in dotnet world。

 and I've been using widerder as an IE for sea sharp development for a long time。😊，And。

I wanted to go into sea lion。And see how that worked because it fits into my personal environment a bit better than visual shoelia does。

And it's got support for different compilers in a way that visual Studioo makes that difficult。

Sea lion has seaMake support built in from first principles and it was it can work with visual Studio project files。

 it's one of those things that you know the ID kind of turns its nose up and goesAll right。

I'll open that file and then set up a project for you， but you really should be doing this in CMake。

And that's kind of why I wanted to figure out because I wanted to fit into sea lion's natural environment because it makes my life easier working in that talk。

So I wanted to get a simple example， up and running。And so this slide， I think this is， you know。😊。

Traraccycling is the smallest C++ program。There are。Bits of controversy in that source。

 but don't worry about it， it's4 IC++ programming。INot really going to talk about the code。

 want to build it。😡，The simplest CMake lists doTxT file。🤢，To make。

An executable program that runs from Na source。So CMake lists is the configuration for your build system。

So CMake itself isn't really a build system， although。

I don't get precious about those sort of things， but it is there。To create a build system for you。

And this is the minimum you need。😊，嗯。Just from the top CMake minimum required that's the version of CMake that is needed because CMake has been around for quite a long time has gone under quite a lot of revision in that time with new features added。

 existing features changed and so on so you need to tell CMake what version to expect what？

Actual version of the environment you're using。 So it isn't that。

CMake minimum required volume is needed in every CMake file。

And then we're going to create a project and project here is just a label。

We're just going to call the project hello。😊，And that is just a name to hang other things off in the Se confit。

Doesn't really create anything from what？Does create something is the ad executable。And that's。

That's doing the heavy lifting here。So a executable names a target where the target in this case is called World。

😡，And that。When we build this， we're going to end up with an executable program called World。😡。

Because I'm the that on Windows， it's going to be called world。Ac。

And it's built from a source file called main dot CPP， which is that thing on the left。

And that's what you need。To get started with that。 so it's a single line。Sorry， a single source。

 simple C++ program。But in principle， it shows some quite important concepts。In all of。

Create that exccutable program。These are the steps that you need to take Firstly。

 we take the se list text and build。The build configuration， so it's when people talk about。

 is it okay， is anybody？Ever heard the expression that seamaker is a make make。And in a sense。

 it is it can be used to make make files to be。Built using meat。😡。

Which has obviously a long history in programming。What they that top？😡。

Command the moment big B bin is does is it's going to create a fold called bin and put all of the configuration needed to build your source into。

🤢，An executable target in this case in there。You only need to run that。

Command when you change the configuration itself。The seamakerlist stopped interesting。

Before I forget。It is now possible allegedly for the Cmate conflict to be called something other than CMake listTXT。

 which even I think is a pretty ugly name for a make。make configuration。But it's not recommended。

I see me basically expects。The file to be called CMakelist。

txt and if you're working on Linux or any un like environment， then it's also case sensitive。

Just remember that。The next command you need to do is to actually run the build。

So C make minus minus build。扁。Is going to use the configuration it generateds in that pin directory。

To produce the executable。And this performs in incremental builds on any changes to the source files。

And those are detected by CMake or the build system depending。And then we can run it。Right。Hello。

So the question is， does it create the configuration in that bin folder or is it using one that's already there？

Hopefully this little demo will make that clear。😊，But no it creates the configuration and puts it in that bin folder。

Thank you。Seng。I have got a little candy environment。

Where I've got my Cmic list Txt and my main Do EPP， is that clear enough to everybody here？Okay。So。

If。Through the seeMake list do Txt， it's just those same three lines。And。

The same C++ program then actually the code in the slide is just including these files。

 so I know that it's the same。So the three steps I've gone though。

Thing to note is there is only those two files in that folderer。 So I'm going to first create。

The bin folder。Using CMake Mo Bb。And that has detected that I've got a visualual Studio。

Automatically， because it's looked in some well known places。 and it's creating me a build。

Based on visual Studio project files， so it's now created。That bin folderder。Which is go。

Basically the scaffolding that you would expect for a visual studio project， there's a solution file。

 a VCX Pro file， which is just the project file。Which refers to that one source file that we've got。

And this is the build configuration that seamakers just generated for us。

 having auto detected my toolkit。It's not built anything yet。 There are no exccutables in there' not。

不用。The source code， this is we have created the configuration for the build。

So the next thing to do is。See make minus minus build bin and what this will do is use the configuration in that bin folder。

And run the tools to build it。So again， it's also detected that I'm using MS build。

 the Viual Studio toolkit。It's gone through， checking the build system， building the RAAT。

 found main CPP， found there's a VCX Pro file that it can use to build using the build tools and it's generated。

Will Di X in bin Dbug。Also under that bin directory。

 So you can change these defaults where the outputs go。But these this is the simplest case。

So now I should have under been。In Dbug， something called World。Xy。Though I can run。You can app name。

Okay。So it's all very that's a pretty value。😊，That's the simplest example I could come up with。

But if I delete that folder。😊，对。And I just run out。The windows sub and t Linux。So this。

 if you're not familiar with that， it's basically， in my case。

 it's a new bune distribution running on my Windows box。

But it has its own environment and its own tools。 And in this case， so I've deleted。

The bin directory， I'm going to recreate it with that minus B bin。

And this time it's the find that I've got guut tools。

It's also detected the Gning tools for in my Linux distribution。And it's created。The build system。

For the new GCC component。Yinbin。And in this case。It's created me a make file and this is where the term make file maker comes from。

 CMake has just created me a make file。Just a box standard to make fun。That I can now use。

To build the code。For the current target， so if I run the build， see me。It's smart building in。

It compiles using GCC and this time in bin， it's created my world。

Excutable just it hasn't put it in a deep work folder because default faults are different for GC。

Like Ronnie， I get the same output。That's from the same configuration file。Two different platforms。

With no changes。And that's quite profoundne。😡，That's。

What Cmaker is giving me is a platform independent way to configure my code。For compilation。

And comp it with the toolki that is native to the system that I'm on。

But it's cutting my back out of the bank。Because I can also。It's under windows。

It previously also detected that I got Vi Studio installed。

 so just by default when I ran CMake Mo Big B。It also detected the visual studio stuff。

 and it generated me a visual studio solution pack。I can change because I've got。Ai。Minggu。

ComWith the GCC tools on my Windows box as well and I can ask SeeMake to use that instead。🤢。

See make minus be bin， and I can see minus G， which is generator。

 and I'm going to use something called Linja。And as you can see。

 this is now that I'm back in Windows， I've come out of Windows subsystem for Linux。

This is now also de。By telling it about Ninja。😡，That I've got GCC 14 and it's created me。

Well it hasn't created me a make file， that's a bit odd。네 응 네。

This time it's creating me a build ninja。F요。I'm going to talk a little bit about in in a moment。

But now when I run the build itself。😡，It's now created me a world。ex using Gcc tools。

 so not only have I got cross platform configuration for my build。

I've got cross tool as well on the same platform。And that's pretty powerful stuff so I could have。

I could tell see me。😡，from the same configuration file to use GCC tools。

 to use clang to use the Green Hills compiler if I had it， to use Vi Studio for one two。😊。

Whateverever tool I've got。I can provide support for CMmate to generate the builds for that and then anybody can build from it so if I'm working in a team。

And part of the team we're working on。A Linux platform and part of them are working on a Windows platform。

 the same configuration can be used by everybody rather than exporting property pages from Viual Studio or whatever or generating make files or however all that stuff fits together。

So。The simple stuff。😊，I hope you agree。Is pretty simple， but also pretty powerful。

 even in the most simple case。 And I'm sure you， it doesn't take much imagination。 I hope。

 to see that。That power scales a to real projects。So ninja。

I said earlier on that CMake isn't really a build system。

And some Seemate enias get really upset if you call it build system because it's much more than that。

 but it's also a bit less than that。Ninja really is just a build system， so if you know what make。

Does。Then you understand at high level what Ninja does and Ninja is kind of a replacement for me。

And instead of make files， it uses the Ninja dot config that we kind of saw in passing。A moment ago。

Like make， Ninja is independent of the tool chain， so it's independent of Gcc or Visual Studio but I can use Ninja to build bows。

Can't get it for one2。And it's fast， so it's， in fact， fast is its principalable reason for be。🤢，嗯。

Make。😡，Which historically has been used as。We kind of。The linguafca build system。

 particularly for CNC++， but also， I mean， it goes back to building For and and forth and all sorts of other kinds of things make has been around a long time。

🤧And。But it works on a set of rules， and it builds based on。

The declarations you put in your make file make inibles from it as it goes and then builds the targets by their dependencies within the file。

Ninja doesn't have rules， you have to tell it what to do step by step。

It doesn't do any rural generation or rural understanding。

 you basically say build me main dot CPP and it goes okay I'll build CPP。

 regardless of anything else where the main CPP depends on something else。

 well that's not quite truell it comes to fact。😡，But it basically you give it a list of files to compile and it goes through one by one in comparison。

😡，Really， really quickly because it's that。What you guys。It's not a rule system， it's a build system。

Makeake is kind of slow because it tries to be both。But the configuration is by non humans only。哼。So。

If you're familiar with make files。As those should probably have left。And make for there。

 let's create one again。San。嗯。This is what a make file looks like we've got a bunch of stuff that's been generated by。

SMake on our behalf， including a loan of implicit rules。And some dummy targets， phony targets。

 they're called which handle things like dependencies which aren't they yet。

 which might be in the future or being able to build targets that don't generate something like a clean target。

And。Thanks for。You know， it's quite big， but it's human readable and if you understand make files。

Then， you know you can get the grip of that。If I go to my bin directory， which has my bill do ninja。

跟你。会不可一般。Weigong。This is the important bit， the bill。This is not human configurable。

It's not intended to be。In fact， on some platforms， the buildviningja file is a binary。

But you can't edit。By hand。And that's deliberate， right they they what ninja is supposed to be configured by other tools。

 specifically CMake doesn't have to be， but CMakes good at it。🤢，And do I mention he's fast。

 he's fast。It really is fast， it's much， much quicker than meat。

 even in the small single source file case。But an injury is just a build tool。

So one of the I could also say， if you remember I added a minus G ninja。

 so telling CMake what generator to use， it's there's a whole list of generators for various compilers。

 including Minggo make files， UniX make files。🤢，You can create generators for lots of different platforms。

If you're interested go and investigate， it's quite fun building for different things and getting different tools lined up。

It's just my geeiness anyway， so SeeMake headline positives。

 we've got a common builder configuration that's independent of my toolkit。😊。

I can use the minus G generator on the command line to switch between toolkits if necessary。

 and it's a consistent process for everybody on the team。Everybody knows how to build it。

 they might be using slightly different command line switches for their own environment or they might not。

 but the point is that we abstract away the complexity of the project。By using CMake configuration。

And this means the build process can be version controls， so if you are familiar with make。

Historically， the make is just a text file then it would go into version control。

Things in Windows are slightly different as talked about the property pages in visualual Studio that's for C++ programmers on Windows。

 visual Studio property pages was kind of the thing。There is something called EndMake。

 which is the visual Studio version of make and it's a different dialect to ordinary make and it does some slightly different things and it just。

If you try to mix， make an endm， then you're in for a world of pain。But。With Cm， we can。

Coaleesce all of that complexity into a single seamic list do TXT。

Giving us multi platformatform and multi target builds。

And the build process is part of the code in the same way that a make file would be。

 but it's much smaller and more compact。And it's therefore CI server friendly。

 so if you're doing a continuous integration build on a shared server somewhere， you can your c make。

Even if that。My shared build is running on a different platform。

 it doesn't matter because we can as long as the tools are there and CM knows how to use them。🤢。

Then we can build our system in a different environment。

So the build agent environment can differ the one that I use on my workstation question here。

So the question is can I mix and match backend tools from the command line， and yes you can。

 I don't know how。😀So I don't know， for example， how to make Ninja build a visual studio project。😊。

I don't need to do that， I haven't needed to do that， but I know that it's possible。没都告意。は。😊，Yeah。So。

Yes， ninja so。Ninja is independent of the tool chain。

And Vi Studio does come with its own ninja built in and the Mingoo。

Download comes with ninja built in， but to it might just be。Which one you use thats， you know。

 top of your path。I I really don't know。 I know it's possible。If you find out， let me know。嗯。😊，So。

Okay。Hopefully I'm getting across the idea that Seemaker is really good。😡，And then it's quite。

 you know， it's simple than the alternatives， particularly the historical alternatives。

 but shouldn't we just use make because make does all this stuff already。😊，Well。

Makeake has its own issues if you've ever had to do anything sophisticated with make。

 you'll probably sympathize。Muld file projects are a bit more difficult because you're setting up dependencies between them。

 compilation time is an issue， particularly for C++， I mean。

 obviously C++ compilers have got better over the years。back when I was built using。Visual C+ plus。🤢。

96， maybe。C++ took a long time to compile， especially if had templates in it， it was a nightmare。

Depenency management。Also feeds back on compile time and link time stuff。

So make allows you to do the。😡，Depenency management in a reasonable way and the incremental builds in a reasonable way。

But all of the compile time stuff， it's difficult。 Yes， so the basic question is。Are there aspect of？

Things that seaMake supports that only specific generators align。

 So the particular example was program compilation database for introspection with Kang。嗯。

Don't know what that is。Sorry， not a E++ programme。That's previously explained。😊，So yes。

 I think is the answer to that and the longer answer I don't know not tried， not played with it。😡。

There are definitely things that are。Back in tool specific。

 so by this I don't mean the bill generator， I mean the compiler。

So if Kangger's got support for some specific thing。

Then that's probably only going to be float up through。🤢，It would have to be ninja or make。😡。

Probably。I don't know， Visual Studio has claimed support。

 and so it might be the MS build that allows you to， I don't know。I'm not sure。That's yeah。

 that's kind of way off my radar。Any others before move on？Okay。So back， yeah。

 make comparison with the proliferation of platforms， tools， configurations， environments。

 all of the other stuff。Make。😡，Environments get out of hand real quick if you've ever seen a large project that was based on make power。

 the build system can be a little hard to understand。And。Ven。On top of all that。

 we've got different dialects， so inmate， make others。All of the dependency dependency management。

 the rule sets that are either， you know， they might be implicit and so you're trying to figure out what。

Mked might be thinking as well as the explicit dependencies and rules。

Autto tools for Linux and Uni based environments was。Partly around helping to manage this。

 particularly the proliferation of different platforms and targets， so that auto tools configured。

Would generate you a build configuration in a very similar way that CMake did。

 but it wasn't its cross platform support was frankly， a bit poor。It was mostly just Linux。

 and frankly， really。For all intents and purposes。And then precompd headers and things like that。

 which support for that really is platform specific and proprietary。

And although that's called Penero over the years。😊，Make was starting to show his age， I mean。

 it's varies。🤢，60 years old， maybe？Sorry。Seemate。It's cross platform build tooling。

Primarily for C++ projects。It doesn't have to be C++， it's not specific to C++。

It is really the de facto standard format for configuring build， na， that just is the truth。

AndBecause it does。It supports everything。 It does everything you need。

And it's a metal to make fileMake for many platforms。

But it is more than that because it is giving you the flexibility of。Switching out your tool chain。

 switching out the generator。Probably combining。The switching those out for other things。嗯。So that。

End goal of all this。😡，But SeaMake wants to support is a very small。In the symbol cases。

 configuration files Seemic lists doTXT that can work for all the developers on your team regardless of their tool chain or platform。

That's its goal to take all of the variation away。😡。

So that you can have a single configuration that works for everyone or at least nearly everyone。

Jason。I just not point to confirm that it is only the mentioned generator in the ortho block。

So Jason Turn has just looked up that support for modules is specific to Ninja。

And oh and visual Studio but yeah， yeah。For the recording。Thanks， Jason。Yeah。So。😊，SeeMake is good。

 but and it's very powerful， but with great power。😊，Comes an enormous amount of documentation。😊。

So if anybody has ever gone to the Cmate documentation type。

wasParticularly with the only thing you ever known about seamakers。

The instruction said run C make minus minus build in this folder， which was me。

When you look at the documentation you go。That's a lot of documentation。And it's。

Extremely comprehensive documentation， but you've really got to know what you're looking for in order to make sense with。

So。The thing that I really wanted to show you was that simple examples really are simple。

The simple stuff。Just works。Second。Moving slightly on from。😡，The most simple C++ program。

Is let's changed things up a little bit。And。Here instead of just。Writing a string literal out。

 we're going to include a file。And。The file is going to check and contain the string that it gets written to。

B。And this is dependency inference。So if we change the head of file。What gets recomped？So remember。

 the simple sea make list stop TxT file that we had。

 this is almost the same except that the name of the project and the name of the target have changed。

And obviously， the source code has changed。Let me see if I can do it， Emma。Yeah。

So here's my seamic list。嗯。Project。😡，As I say， that's just a label here what I'm creating an executable called custom Me。

 but again from my main gott CPP， which is including。

My message got Hged so I am going to scaffold a build。Just because。嗯。Oh， what have I broken。Nothing。

 just for lot to clean up。A scaffold did a build using Ninja， using the GCC tools。嗯。Oh， build there。

runun it。So that says， hello see me。Ni。And。那是别的电。🎼Make a change to。Wch。

A change to the dot H file remember。And。I don't need to run。

We Bill scaffold the big be command again， but I do need to remake。Rebuild code。And that， hopefully。

 has detected that。 I changed。The head of file with it being mentioned in the configuration。

So Cm has inferred that dependency and it does this use it， so。

All of the mainstream compiles support the。Forcing the tool to output the dependencies for all of your source files and CMake makes use of that。

To figure out what the dependencies need to be， actually it passes it off to Ninja in this case。

 but visual Studio supports it natively so it avoids that extra low brain。But。The point being。

 but I don't need to name all my head files。I I have to head upon him。Even。

Recompbining the code is enough， I don't need to rescap all the build。I just need to recomply。嗯。

That is。That's the nerve of an incremental built。You rebuild for changes to source and if I rebuild again。

 it's not there。Do anything， says no work to do because I haven't changed anything， sorry。

Incrmental bills out in the box。That's not really difficult in me。😡，To arrange to do that。

 but you have a lot of extra manual steps to do， including particularly the dependency database that you need to get。

Whichever compiler you're using to spit out so that you can feed it back into the build。

Don't need to do it at the seaMake， it does it for you。Other things not in the box。

I might have a non standard system include in this case， I'm using the magic genomeum。

 which apparently from after this weekend I don't need anymore。Is that right with reflection？嗯。😊。

What magicic genome does it does it basically allows you to use。

Introspect on inum classes is headline， don't worry about that。😡，The point being。

 I'm using some third party include， I need to tell Seamaker where to point it。

 I might have it in a well known place。Of really using system include syntax。😡。

Because it's not a local include。And that's just housekeeping， not that you know。

 it doesn't really matter it's just。I tell Seemaker where my include directories are。

In the configuration， now。What I'm introducing here is something that needs all the developers on a team need to have it in the same place。

But you can make variables for this kind of thing I'm not going to go into that but you can arrange so that C may can your well then includes in different places depending on what platform you're working on。

 obviously that introduces complexity to the conflict。

 but it complexity you would have had to do with make files too。

But the point here is that in my Cmic file， I've got my excutable cards， which is the target。🤢。

And I'm telling SeeMake for that target。Here is the path to the include directories and I can there can be more than one path。

 there's a list of paths that I can add in。And that can be relative to the wherever in this case。

 because I'm using a relative pathax relative to the location of the Cmate list。

TXT file that I'm currently compiling。Oh， currently。Scafffolding。嗯。

You think that's all I need to say about that？A similar idea if I've got a static library that I want to include in my build。

 so here I've got target include directories。That are bringing in the small fast media library。

So the include directories， I point off to the includes。

 I've got target link directories which are going to go off。

 that's the location that contains the static libraries for whatever platform I'm on。

And then my target link libraries， there will be a separate target called Bs with the source files for it in the same way。

Lucine just put。Shortness of the slide here I'm saying when I link。😡，My target called Bs。

 I also want to link against the。Effectively， the import directories for these。

 which are dynamic libraries。By default in SFML。And。Hopefully。Yeah， this is the same thing。

 So here I've got my。And excutable。Con banks。Up here。And pulling in the include directories。

The link directories for the bows and linking against the S FML。Libraries at the end。

And it's clean so if I did。For this one， I do need an ninja build。Because I've only downloaded SFML。

 but the GCC toolkit。How building that。And then。嗯。Bill simple window。

 so that depends on the actual dynamic libraries for SFM being somewhere on my path。

Just because they。They are not copied as part of the bill now you can arrange for CMake。

To figure out what your dynamic dependencies are with some caveat and create a package into your outputlet directory。

Not gonna touch that at all。Today。😊，Because。It's way off the scaleative。嗯 am。

Complexity in seem it falls frankly。But it is possible to do that。

Or you could just write a script and does a copy， hello。

So the question is what's the best way to manage different build types on the linked libraries？嗯不。

你们这里这我。So debug mode versus release mode， static library versus dynamic libraries， a bit like this。

 so a slide ahead of me， so it does allow me to specify within with a really simple syntax。😊。

When I'm doing a debug build。I want。To link these libraries that have got dashD at the end。

 which is that's the Debug convention for SFML， particularly。For an optimizeised build。

 so an optimizeised build is basically。Anything that's not azepot built。So in SeeMake。Language。

 you only had two variant， it's got debug mode and not on debug mode。

But the question is when I'm doing a debug versus a release build。

 the target that is being linked together to be inexecutable。

 I've got a release version and a debug version， is that what you mean？🤢，When I built， I can。🤢。

I can't remember the command line syntax for this， you can by default。

 when I type C make minus minus build， that builds me debug。And that will put it into。One folder。

I can specify a new， I can basically configure a different folder to take a release mode build and it will have all of the。

🤢，Built targets in there。Talk to me afterwards， I'll show you because。

It's about the invocation of seaMake that distinguishes between debug and release。

And you can arrange for those two things to output to different folders。

But it's the Cmic list configuration that tells it what to link。Not what to build。

It's a kind of a point distinction。It's a really good question I'll try and yeah。I've got to move on。

 speak to me after。There is a better way to do some of this。Where I can set variables within CMake。

So this is going to build a standardone executable。嗯。

Couple of changes here are creating a variable for the pre the。

The main location of my SFml libraries and includes so that I can use。

That base path in the rest of my conflict。I'm also here saying。Rather than。Specifically specifying。

So which libraries to bear？Which specific libraries the linked against？What I'm saying here is。

I'm telling Cmates to go and find a package called SFML。

And this works because SFML has built in CMake export。

 so theyve the SFML developers have created the CMake build files for their own stuff。

 exported enough， including this name SFML。So that my C makewell can find it。

And then find package will go off and look in some well known places， which I am。

Helping it along with by setting this CMake prefix path。And。

I'm in the fine package I'm telling it which components to build in。

 in this case components called graphics window system， and those are SFML names。

 they're not CMake names。But what this also allows me to do is that when I'm。Linking。

In the final line on this configuration。The target link libraries。

 I'm specifying the package name that comes from SFML rather than the specific libraries。

So that gives me a little bit of flexibility in the configuration。

 but it also makes it easier for me to share that configuration with other people。😊。

This is the most basic example on this because using Cmate variabless is really key to making your Cmate cong。

 particularly if it's relatively complex， being able to share that with other developers on the team。

🤢，ACouple of other things to note as I can pull in third part dependencies by art。

 so in this case I'm asking for Google test and I'm using a facility in seema called Fech content。

It's kind of an external facility to see， it's not part of CMake cause functionality。

 but it is a weight extension an include thing that you can pull in with including the fetch content package。

And then I'm declaring what it is that I want。E。Google test is the name of the thing that I'm after and this is where to go and get it in this case。

😊，I'm downloading from a URL specifically version zip package。And then I'm making it available。😡。

So that all the targets that are part of my own configuration， in this case。

 something called G tests can depend on。My name call Google test。

And what CMake will do here is if it hasn't already cacheed this package， it will go off。

 download it and unpack it。😡，Into its cached area。So that I can think I can use this include parts。

 which come again， this depends on Google test having some basic Cmate support built into it。

There is enough smarts in that configuration。To know that it goes here， therefore。

 the include paths on which。Tge where to find the libraries to link against so that I can just say I'm going to link against GT main so that I don't have to write my own main in my unit test package。

所。This abstractual away from。Mannually downloading it yourself。

 although obviously you can and refer to that， which is important under continuous integration server。

Situation， for example。Rather than a built package， I might do it by Git reference。

so here it's the same basic idea， but I'm doing it for catch two where。

Inlude fetch fetch content declare for catch2， this is now a git repository。On Github。With a tank。

And that what seemic will do under these circumstances。

Cone that tag to its cached area so that I can then use it in the rest of my program。By extension。

 then。For example， in the seaI build。I might want to。

Mannually clone it to a local place because my CI build server might not have access to the internet。

 it's quite common too。Fwall off build server so you can have your own clone that the build server does have access to and building it instead。

Realistically speaking。😊，We haven't got time to go through the next slide。

So I'm going tooo zoom across here， what I do want to talk about is a little bit about physical versus logical shape。

I'm going to do this really， really quickly， but here I can have a CMake lists pile for a project that's got in this case is a main project it's got a test project it's got a static library that it leaks to case internally and also makes available to other programs。

And an executable that pulls those things together。

 I can have a single CMmate lists file at the top level of the project that knows where all these things are。

 what the targets are to build。🤢，And I can specify dependencies between them。And it's， I mean。

 it's not。Terribly complicated in this case， for a large project。

 obviously a single sea make list finally is going to be enormous。

So you can split them up in the same way if you're familiar at all with make。

 you can have nested make files。The difference is that the sea make having nested sea make files。

 it just works rather than you haven't do anything else whereas as nested make would。

Anybody that's ever used nested make falls would。Would have had a proper eye switchy moment where of not being able to figure out why something hasn't been pulled into a bill seam。

 you just include the path to the seam far。As a directory。诶。

So in the middle under heating trigger is about halfway day。

 I'm telling it to include directories and I can say specify whether to include it before or after the current one that's being built。

And it all just works。And it really does。And then at the end， you can have。Your final target built。

But also it means though I can， for example I might want to build my tests independently of everything else。

 I might be changing the tests only， not want to build all of the infrastructure that's being tested because that hasn't changed I just want to build the tests because it's got its own seatMake list file I don't need to remember what the target called I can just go to the directory and build it。

So quick word about tuing。Cm comes with a goI and I can't recommend that you use it unless you already know Cm in a lot more depth than I did。

Visual Studio and sealine both have pretty good sea makes support sea lion in particular。

The support for CMake is properly integrated into the ID in Visual Studio it feels like a bit of a boltong。

 which is because it is。Sea lion support for teamMFs is outstanding。

I started off the talk saying I love chap panne sauces and I skillthy。So。That's me。All done。

 thank you very much and even the best。

![](img/d26792cad1c0bd6090276fb8a0896106_3.png)