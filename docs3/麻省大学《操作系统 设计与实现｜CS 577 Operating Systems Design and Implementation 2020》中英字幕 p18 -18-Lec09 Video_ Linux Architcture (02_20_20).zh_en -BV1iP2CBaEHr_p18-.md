# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p18 -18-Lec09 Video_ Linux Architcture (02_20_20).zh_en -BV1iP2CBaEHr_p18-

嗯。For coming。Today will be。Different。S。We are going to the Latins。

Some of you actually took the undergrad class with me。Actually the the lump of。

Many of the concepts have been going back and forth between the two phrasing systems。

So in some cases。啊。And we can look at a little bit of history。

We look at a little bit of history of how Linux started versus Linuxs and so on。

There are just very few practicals。I I would point you to。There were go。

It's actually a pretty cool book。It's on a very old kernelel versionnon。Like it' we're talking。哦不。

Still， most of the concepts there have not changed。Of these many of them。has been。

I mean more and more stable？Over the years。So this is also available in hardco。The newMas library。

 you can also get that。You as library as a legitimate ebook。You can also。

And see where you can find it all over to please。So's pretty all。So this is part of the course。

Going from menix to Les， which。That does not basically mean that you this part of the course is this part of our midterm exam。

 yes， it is。There is an assumption that you guys know minutes。公。M。

Between minutes and names except in various places on the slides。

I would expect that in some cases you would see， okay， this is very similar。

You know two minutes and in other cases， you'll be like， no， this is different from。

So a very short history， so this has started you started as a project from。Someone who was drunkled。

 who was very angry。How he could get minutes because of all sorts of licensing issues。

I undergra in the University of theokeki。啊哎。I'm just wondering if it's too small。诶你哋希。

It is not the first try。To do that。had its own licensing issues。

 there was a parallel effort proposal that was called the No project。Which was basically trying to。

Memic。To basically rebuild the entire units。Ecosystem that started at Bell labs and everybody was N Bell lab。

I mean， we wouldn't have Nux and Linux if the lab had just open source Uni。呃。

It started in the early 90s。But people really took notice of it。It9ters。

People think the first adopters were basically in NASA。To reduce the。T was to an operating system。

That was free so let's just use it， it's also EX compatibleible has all the different things that you would want from an operating system so why not just use it？

嗯。Lnus we started writing that food is actually like a gut figure in that community。

There are also of flamemores between him and different people。And he also is a little bit。不in。

So he has these like flames with different people I think you already read。The bomb。まマイナス。

Wars and the Kid War， but he does that all the time。I used the mud past to actually show people。Ba可的。

Like a table with all the coufffeine words inside the Nino kernelnel。

 you can actually go into the GitHub and search for everything that you can think of。

You're probably going to find it。And the people basically saying， please do not change this。Beep。

 but Im there because we don't know how to change。 I mean， they're also。O。呃。

This is something that you have probably seen that basically the Linuxux system model is very different from the system model。

 what you have， and it's very rich to walk between these two screens。

What you have is that you have applications running on top。

These applications can only contact the kernel via the system code interface。

Which serves sort of as a programming interface。And then the system code enter on interface can talk different parts of the criminal subs systemsem。

O。The N kernel is a beast， and it's not a small thing， and we will actually see how beast is。

Each processor， each computer processor， each CPU is doing one of three things and see they're running the user process。

Or running a kernel space process that is basically。And on behalf of something that the user wants。

 like right to this， for example。Or're running a fewer kernel forces。

 Maybe if you're running something that only the kernelone can touch and only the kernel can。Okay。え？

And there's a be of different nature。You have no access to common programming。

Preventitiveatives that you have if you're a C programmer。

And that makes it a little bit harder to actually program as in no CN。

 there's a difference between UCCN and SC。to get to that。Now this is the kernel。

 so you no longer have anybody to tell you， you know， oh you。

 by the way you're accessing memory locations that you cannot touch， you need to reconsider， right？

I mean， there are no protections， if if your kernelnal， you have full control over the entire memory。

Okay， so care protection is non existing。And that's for。I mean。

 that has two sides of it will actually cover。Andlinos。李er。But one side of that has。

 if anybody gains root， basically get。It becomes part of your care of anybody。

Put some maliccious code in linear kernel， you're basically exposed because they can read your entire kernel。

Now the Carolina account。Excuse voting point This was actually something that there was I think there was a question on the is schools。

If we can。If we should as。Baically the only。On the integers， or can we do floating point operation？

No， you always do。The current one should never lose building point to purchase。Almost never， okay。

And that's not just for Ns， that's for N Karen by way。So I mean， as a current programmer。

 you' not just go in and say， oh， I'm just going to do some weird modifications in there。啊。

It the current has a small pair pulse， fixed size stack， so each process that runs。

Well talk a little bit about the proceed later， has its own stack， has its own。Thats for that course。

There are as synchronous interrupts， so basically when I type on my keyboard， I am actually。

Having my kernelels stop to basically process the iO that I have just sent in。

 which means that since I can't stop at any point in the entire。

The alternative of any process running means that there are all sorts of synchronization issues that one needs to take care of and conations that need to be handled。

You can actually very easily get this condition in the。

I suppose that everybody here knows what is conditional。Ptability is important minutes。

It's a pretty nice project because well it's。Con the number of lines of food is numb southward。

It looks very clean。You cannot really run menex on any。Hardware that I came。

Actually you'll find like running ven and recipe pie there are people who are trying to port it。

 but it's not as easy as running peanuts。So Linux is almost1 if it's a processor。你たら。

Portability is very important for dens。And that actually made Linux the Go to choice for many， many。

 many use cases。I mean，For non power users who actually just use Windows。They do not really have。

 I mean you have Windows machine that will have either an Intel or an AMD core and that's it。

 there are no other variations， but for power users who actually have like they're going to run this on an embedded system in a car or they're going to run this on somewhere else that this is important for them。

 servers and so on。ニ is the beast。This is actually one of my favorite graphs on earth。

 so this is the number of lines of cool and ens as time progresses。

Basically many of the design decisions that were made in Linux and the early stages were basically saying that you we need to keep the Linux smooth。

But then of sudden I like at 2。5。Or to going forward very。The I个 could just。Explludeed。

 and now we are looking at 23 million，25 million lines of good。 I don't have track of the number。

 This is actually， this is a few， actually a。This is a few。ers and this is with the version numbers。

Now。From a point of view of somebody who is doing systems programming。

You have to understand that this is a huge issue， this is code code built and one of the the main issues with that is that as a programmer。

 maintaining 25 million lines of code， making sure that gold dependencies are up to date。

 making sure that your code is secure， making sure that there are no， this is the current on this。

 the thing that is actually going to control your processor and stuff is a very hard task。

 I mean there are different statistics on how many bug。

Does the most professional programmer introduce？Each 10000 lines of code。

 there are many statistics on that theres an average number which I can I don't have it out of the top of my head。

 so now we have this 26 million lines of code that runs almost everything you can think of a trans servers in the cloud。

 it runs most of the database servers。Right now， it runs on many of the embedded devices。

I mean and so on so， so how do you actually？Manage that and there is a huge work now that's being done in the bloating the kernel。

这三。Yes。Yes， but then this is why Min can look much， much better and Min is。

Mix is in some way the most used operating rating system apparent but in other ways nobody really knows how Intel are' using it it's still something that's never picked up there is another phenomenon that Praant has probably talked about SEL for cell for and this is a very interesting operating rating system because it it's。

It's a formally verified operating system that actually runs and does not problem as a monolithic operating system it's very similar to Linux so people especially in the defense industry and so on。

 they run SL for it's formally verified so you know that the code runs it's very small so I mean the code。

Base is very small， and then you can basically add only the drivers that you need。

So there are all these sorts of issues where if you try to support everything。

 you end up with lots and lots of good， and this is why many people are actually trying to endorse the care。

That there are many， many。Things that are being done in that space。Again。

 floating point comparisons in the kernel are a very， very bad idea。Building coin requires。

They take time。If you want actual real so point operationss， you're actually。Looking。Pion。I mean。

 if you could just do like the simple， they're very simple。Inplicationplication。

Pa with the numbers that you do with integers。The we can make them fruits and so on。

But at the end of the day， this is not what floating point operations or floating point operations require position。

 you don't keep them at the kernel， you do them as user space， you。

 you want to keep them as user space for multiple reasons， many of them architecturally。

These decisions。I定。It's something that you actually really， really need to take care of。

I don't know how many of you will end up being to a current program。

 but that's something please give mind。O。Concurrency in synization。

As said race conditions can happen and will happen in the country。Okay。

 so now how do you handle them now if you're under operating systems tasks。

 you have probably studied base conditions and different algorithms to actually detect them as own。

But as a general， and many of these are actually implementeded in the k。But as a general concept。

 you need to always keep in mind when you are doing kernel programming， that's not just for Ns。

But more so deals， because everything is inside department。Mins， I mean。

 if you're forcing like the votinging layer， we need to take care of that also very much。

If you're not working with the servers， even if you're working with the servers。

 you need to take care of these conditions， but you will not basically have what we call the hoops。

 which is basically the caral package。O。So Linux is a preemptive multitasking printing system。

 so you're running multiple。Things， which is similar to Linux。

Process are scheduled and rescheduled based on some weird algorithm。

O system implements we'll talk about how Vens makes these Kian decisions a little white。

But in general， I mean， you can't add your own state to them， right？

And the current must synchronize between these tasks。

 so you should make sure that you know if your task is waiting for IO。

It owns some parts of the memory， no other cluster just teaming that part。なです。

There is also the issue of interrupts， which is the same with Min again。

 you have interrupts and you have to basically make sure that the executing code。

 if interrupted comes back to a state that is correct。O。And。Then， basically。To do that。

 there are multiple techniques。That are used in the perm， we actually try to cover them。

In the course。没准。InSome ways from the Min source tree。However， you see that there are no servers。

 everything is in current。So you see that there's a driver， there's a firmware。

 there's the file system， the virtual flight system interface。

Now there is actually some of these are quite interesting， like Kpto， for example。

Inside the N kernel。Because you know， you might want to do cryptographic operations in the Kma。ok。

 so how do you do that。If I'm telling you that Linuxux has no。

Access to Lipsy or to any of the user level libraries that you can use for cryptographic。Practient。

Then you either have to implement ADS by your hand， which is a really bad idea。

Or they just provided to you so Nox has this。Wite number of algorithms implemented in the crypto。

And they kept to。Fuler。Where you cant actually just like inside the cur。

 you can do cryptographic equations。Similarly， they actually have multiple other things that。

First side they are just strange， like for example。

You have the sound subs systemstem is now part of the kernelon。I mean。

 education has to keep it up there but。And the kernel。I think。I think there's one。Byい。嗯才。I believe。

 include。You also have a wide range of implementations of different data structures that you study in your data structures course。

 double linked list。Red batteries， they it， theyre just going implement。So I mean。

 even because they want their kind programmers to just not access to these things and they want to make sure that these things are performing the way that they should。

 so there are lots of these。T within inside the curtain。So Nox process management。

So you guys have looked at the forces abstractstruction。

This is how you info you that you have threads that share a virtual memory。I mean。

 there are no real boundaries， it's just virtual， but each。

And each of them have their own virtual courses or so through any application that is running。

You give the feeling that you own that processor there as well。That cut first accept。喂。

And the program itself is not a process， the process is basically create the program。sorry。

But the process is the active program itself， so the code itself， the data， the open files。

 and so on。And in the Linux code base， all processes are task， any process is actually the task。O。

And As has this elegant， very large plastic structure。

 which basically describes every single thing about a tasks。Okay， it's 500 lines of code。

 It's a structure of 500 lines of code。嗯。It's。Actually。

Each structure is connected via a double linked list to other dust structures so all structures have。

T three。Oros。For a single tasksk， the tasks structure can be as larger as 1。7 kiloys。For a single。

So this is basically and this is everything you can think of that would be related task。

In that to us。I suppose the same thing as the。This。Yes。So。我か。Yeah。

 don basically just they were giving them。There are a couple of different ideas in there。

We will actually cover some of them。So you have thetoskius。

 which is I believe that men does not have theosskius。

Where you actually have this double linked list and you have everything connected to everything。O。

And this allows the kernel to actually quickly go through all the tasks that the kernel has。

 theres even the creator that you can use to just like go through all the tasks if you want to get task information that programs like EdgeTlk。

 for example，到。If you have used these， they would just like go and read for all the proceeds or P minus AX。

And this proceed just。The three either work the entire task structure。In fact us this。

Which is a double name this。Basically to get all the information needed。Okay。

 you can use that for all sorts of things。We're pretty inside the kernel。

They are definitely used as part of。I'm just getting， as we would see。Okay， so this is the task list。

 it's a double linked list， each task basically points to next task and you have a parent for each task。

An appearance is either the process that's founded， the process that started， or then a process。

 which I think is called the zero process and the men or something like that。

 like the first process that ever starts。There's like the parent process for homes。Do three。

Is it full zero process？Something I mean。方明。So you have a he closestosis tree。

All procedures are descendants of any process， then processosis is basically kernel。

 starts then process， anything that says that starts after in it says that this is my brand， okay？啊。

And diet process has PID form。Of course， I do one。And the relationship between procedures is stored in the process descriptor so in each task structure you have process descriptor that they has pointed to the parents taskstruct so you get a point to your。

You in process or that point to whatever process that started you so if you are， for example。

 doing multiproces on ons and basically start different。快风。Proceeds。Right。So， the first。

The first course that you start like Python， whatever paralyzed the py is going to be your parent for all that proceeds that come in after that。

 okay？And basically， having that allows you to basically know like who started what and to build that entire of your entire system。

For each process， as you said， there's a paramount stack。

And the stack is basically where the process has all data happening。

St right because each process will have like would be operating on data。

 so suppose that you're paralyzing web server， you are basically going to run some code to handle some requests。

 right？So basically for。You need some data for each of these proceed and that data will be stored in your and your paper process and stack。

O。And this is the highest memory address， and this is the rose memory address。

 and then you would have thread structure the task structure towards the bottom of this。

So towards the bottom of the stack， you would have all the information for the。For your task。Okay。

We'll talk about threading in the sick。So process creation， just like。Minutes。

Here this force to go for Exec， right？So I mean， it's the same idea that you divide how to start the new process to two parts for it and then your exact。

 and then you have the copy on right and all the things that makes possible。O。So just。

Just a reminder， Ford basically creates the new PID。

 the new child pose with a copy of the current task。And difference only in the first ID。And then。

The parent ID for that。Process in the task structure is now set to the original process ready。

 the one that's owneded the new process。And then there are a few other signals that differ。

 but they are very few signals。Is it an exact same copy？

Exact basically loads the new circuit into the address space and again， it's using it。

 so it actually wants the extra code that should be running。And then you have copyright right。

 I think you will also cover that。Where you have。You you deny any changes in the structure that you just copied to the data that you just copied？

Until you it， so you don't actually write the actual data。

Until you actually have a reason to write it， right？Like the new child。

It's trying to change something in W。So let's talk about running needle。This is from NAA。We do。

This is Max basically we have multi user threads all of them go to the same kernel thread， Okay。

 there is a single one kernel thread。O。This is Ns where each user。

Hows it equivalent parallel procur threat？Okay。So if you have 10。

000 threads running for different applications， you're going to have 10，00 kernel threads。

 that map to this user。Okay。This is actually also nice。Abil have M to N mapping of threads。

 So you might have。100 user threads that happen into four or three terminal threads。

This was implemented in Eslars， but now it iss actually implemented in Golan。

 this is how Golan is threading or works now。And this is just side note。

G I decided to go to that model where they have actually their own threading。Library that actually。

Wortion， the different trends are。Different routines。And go。As an M ton， so they X map。M go。

M go routines or subrs to end user credits， and there is a really room for them to do that it's basically because it decoups concurency for parallelism。

So basically， if you're building web server and you want have to be able to support 10。

000 requests per second and you want each request to have its own。ああ、それ。Okay。

To basically answer that。The way Latinx would do it is that for each of these requests。

Or for each of these users， you're going to have an exact。Car no threat that actually。In the。

 which basically makes the car， I mean， complicate scheduling and does all sorts of weird things。

Basically on how large you can support things， you need to change parameters and so on and so forth。

If you're writing this in gold egg， then what you're doing is that you create 10。

000 user routines on these map。A smaller number of user threads that add do exactly the same number of kernel threads and then context switching is much faster。

He that this is starting turn？Sure。Yes， so how does going？就是。It doesn't just like， I mean。

 they have their own。I I'm not in turn sure how this is implement。

 but my understanding is that they have something that's just like the JDM in some way。

And I don't know what is called。I don't know what does the whole term for that？And actually。

 it's something that people have granted also in other languages like Air， for example， I mean。

 which is the first very highly parallel。Programing。Back。

The kernelel has no real threats in the sense thating is， yes threading is supported in the kernel。

 but there is doom。Separate notion of threats except that there are just another course of tool。

And then you need to manage。The proceeds。That are now that to the user level threads。

 we come back to the as kernel level proceeds。Car 11+。

 I need to do this mapping by just using the post tree and basically who's parent what and so on and so forth。

So everything in the kernel is a process。The current had no special data structures。

Semantics for trends in that sense。 so it does not try to。For example， say that you know。

From getting in the point of view。That task。Or that sorry。

 that user process had 1000 threads and that user process had one thread。

How do I should differentiate between that。 No， doesn't try to do that。 So that's 1000 separate。

K season。 And that's one。P sources So there's 1001， and then we go through all of them。

And each thread will now necessarily have its own task structure。Because， you know。It's's。

It's now just like users have a process。嗯。Windows， scenarios and many other operating systems have achieved explicit support in the kernel for drilling。

So that's the difference。 that's a huge difference between。这这 two。operatingating systems。

The only thing that you need to make sure of is that threads you share process resources in many ways。

So， I mean。It''s a way to basically make some shared。あ。Some shared data between different processes。

 at least this is what he used。View things。And threads are created using the Cl to School。

The clone basically has multiple size， Did you cover a clone by any chance？Okay。

 so what drone does is that。I mean， names says a tool， it clones。没据。对。And then你 have。Huge number of。

哦。parametersrameter that you can pass the clone that actually controls how drilling will actually occur。

O。So basically you have， for example。Do you clone file。

theyAre the parent and in the same threading group？Okay。

 so maybe the parent will just start the threads and doesn't need to be in the same training group。

Children will be together。AndIn the same triling。Then there's like child ID， create ID。

 and lots of other things that you can control how your threat is created。

But youre just passing these。Okay？Now there is a very long debate。What to so you how mouth fork？

Before。L one。There are a bunch of others that we can actually see in the system pools library。

 and which one to use is a user debate， which one is better prevented and so on。So。Now this。

 we're talking about user level threats， okay， now we shift to current level threats。

 which our kernel level perceives basically。And these are threats。

That the kernel starts for doing kernel stuff。Okay， there is no correspondinging user level threat。

 so that means that you're basically only working at inside the kernel。

 the user side can control these threads can do anything to it。Okay。

Although they are terminal level friends， they are scheduled。Skule level and preemptable。

 so you can't schedule them， you can't pre them。嗯。You can actually see the current level threads by just drawing PS minus EF on your machine。

This should show you basically what threads are for the user。这是是概。

We'll cover a little bit more on this in different parts of neo structuress。

With probably half or four of them。嗯，安规。Our game is very high。

 we aim to finish the book in these three or four lectures。

 and that's basically because you guys have covered a lots of minutes and many of the concepts are the same。

So basically the ideas。呃，给 you。The dump huge。If you dump on， what is the difference？です。

So process and termination。Process， destruction self induced。

So there are two ways to kill the process， okay， there's the normal way where it process basically dies。

 finishes and thus dies。And then there's the sixth term。

 basically sending signals to that process to kit。Okay， if you're talking about like the normal pass。

The normal process that you have。The process is itself quitting because it's done with whatever it was doing。

And this occurs when the process cool the exit system cool。

 it's basically a way for the car to know that okay， this process is now entry。And basicallyically。

 once you have that。Once you have that system cool。Wol。The process does not just disappear。

 this is not quick。No process。There is a for the process to disappear。O。So first。

This happens when it's explicitly ready to terminate， so it's literally in the last line。

And the componentss were。But or something。Elicically on return from the Mesa protein of Ed program。

 so you have returned。Because basically that's that last thing that you。

 you need to return first and kick the pulses next。

 you do not kid the pulses and then try to return because well if you have killed the pulses。

 well have do you return。So in reality， if you're callinging a function or a method or something in your programming language。

 what you're doing when you type return， stack your return， and then you keep the courses。

Can be that way。It can be basically induced by the kernel using the sixth term or some signal or some exception that happens。

 so if you basically if if user level process tries to access， for example， protected memory areas。

 then in that case the kernel will hit it。Right， okay。bulkk of the work is handled by the two method。

 and that's defined in that folder and in that file can easily find them。

And after the do exam completes， the process de scriptor for the termative process still exists。

 so since a process is everywhere， I mean you find it in your task structures。

 it might be variant to another process， it might be trial to another process。

 I mean that process cannot just disappear without cleaning all these cases。

So once the process goes to exit。It becomes a zombie process。喂。嗯。

And this enables the system to obtain all sorts of information that is needed before it actually kill the process and thus do all the necessary cleanup for that process to actually terminate。

O。We finished at 330， right。So process on termination。是。First thing， first。

Each process that has a parent， the parent is in charge of dealing of。Okay。house school。

And the acts of feeling after processosis and removing its process of the scriptor are separate。

And then the removal of the process descriptor is or two separate things。Fends。

Once since the process has already returned。Then the parent has already gotten a signal or gotten an upco from the course that that。

 oh， I'm done。i I need to wait time， I'm his zombie be now， okay？

So the parent has obtained information on its terminated child or signify to the curriculum that it does not care so maybe the parent just started some bunch of proceeds that does not care about them there are actually cases where when。

You programmatically do that。嗯。And then the trans task structure is aggregate。

 so you start by workingipping the trans structure。And then after that。You actually need to clean up。

After your process， so the parent basically starts to end up， okay， this was my child I clean up。

Now there's a case when you're parentized， okay？And if your parent dies， you need to be repaired。

The car does that， but actually either parenting。A process。

To some other process and its good group and that might be your grand parent， for example。

 so maybe the process started a process and that started process and then the parent dies。

 so you get the。The orpha to his grandparents very simple mechanism， okay。

 maybe you are completely empty and the grandparent die。Now， I mean， now since you cannot basically。

Have the process just like wander around having no parents， we need the system in the system。

 so what the parent does is that itpars the process to the end process。

And that's what we call an orphan process if you have been working with New York long enough。

 then you know what the orphan process， you can have cases when you kill the P your Python。

 the Python code that just started the00， 10，000 threads and the threads still run。Okay。

 although the parent is that， the program is no longer， you see it in your memory。

 you see it when you type it for something。And then basically what has happened is that all your threads or all your subpro。

 because actually Python does not have。But well， they did not have explicit credit so you actually creating new proceeds。

 so all these proceeds ended up elevating to diet process and they started becoming their own thing。

 they living in their own world。Okay。So this then you actually have to do。

You go and kid each of these orphans by hand if you actually meant to kid all these orphans。O。So。

 I mean， restart your entire computer and then you have kid like me。Forefather。No more antry。

First scheduling。Okay。Any questions。In legs， of feared， our process dies。

Depending on what parent process it was。两解两。No， yeah， it' something if you so that's that。

If you do something。So if the kernel process does and that kind of process causes。Was important。

 one of two things would happened。You either have a non functioning system， which basically。

 for example， so one favorite part is sometimes the process that di is your sound card。

It's not that important， but still， I mean， if you're watching a video。

It's kind of important then you end up with visiting new sound。喂。You can explicitly store。

In some cases。Not for proceed。If your process has basically died because I did something stupid in the kernelel。

In the current stack， basically messing up the memory。

 then you end up with the whoops probably and the hoops is basically current panicking you know。

You need to start your machine or something。So it depends on what course it is if your criminal level pulse is just。

Like mapping to use doesn course done。そです。Do we actually does that mean like is like as a friend？

We talk about。Let's say sound apart。我。Right is。Yes， so that thread is a process in reality。And your。

And of them I mean some of them become very。I mean， if you are doing assist community administration。

 some of them when they die， they actually drive degrees。

And sometimes just fine because you school something。Then some with that kind of forces。三位。

Proros the states， we know them。hopefully。So you have any process is either running on a processoror or waiting for a processoror。

Or zombie。Ba， right， I mean， this are pretty much。So to running to。So you have。Waiting for something。

 you have tossed running， okay， here， tossed ready。No still running。

 so it's in the wrong queue to run next。You have some things that are actually waiting for termination or something。

Soマて asking。The actually basically inters all these processes together， right？

That's what Min also does， I mean， most operating systems are thankfully multi to。喂。嗯。

When a multiprocesor machine， you want， if you have 10 cores。

 you want your 10 cores to be utilized different parts， running on different。

Linux use prim multiosking， very similar to Linux。 Basically。

 you have some way to actually say that oh this process has already。

But got an fair share of running I need to PM and run。嗯。Now。

This printable multitosking is actually as opposed to。그거 때もた。

Some people at some point in time thought that， you know， it's so bad that we can proceed。

They we need to repair on them and on， let's do cooperative multit they also said that it's so bad that we pre him。

So let's let process play nice and you know， on application or just you know。

Stop using the processor， the CPU here its nice。And there are two。Fillient operating systems。

That were designed that week， MacOS9， and we those 3。1 these are ancient like 3D。Especially in。他可以回放。

I don't even know it before Windowss 95。ItVery nice just maybe leaving。So these systems。

 they were built with the assumption that conditions would mean us my future other。

Cooperative multitsking is a design decision that people make when they are designing operating systems and thankfully nobody makes this decision anymore。

And this is why I'm mentioning it。So then we usually of the Linux course schedule。

Before kernel version 2。4， it had a very done， very simple Nance sner that was。Not scalable。

 had lotss of issues at work。Now in version 2。5， the one is that know now multipocesing is the thing。

 we have multiplepocess coming up。We no longer have a single core and a single chip。

 so we need to be able to support multiple processors at the same time。So the first one did noky。

Try to build a constant time schedule that basically thinks all one。Yeah。

And they built and it worked。And it could skip to hundreds。

This had several shortcoms and the main short coming was that for interactive applications。

 and interactive applications is basically almost everything we use as users。Okay， it's。

What would happen is that you would press a key。and there was a non negligible probability that you wait for。

Sometime you see the letter fighting。Which is not pretty fun， so war processors chrom。

For web server where you're waiting for the guest responses。For all of these types of applications。

Which are interactive application。You had a pretty bad performance。来，还民。And measure 2。6。

They introduced multiple new cagiverrs， so they were like， okay。These two did not work。

 Let's just introduce a number and see which one works。Okay。

The one that is most notable is the rotating staircase the landscaper。

I believe this is very similar to the minutes to get to there。

IBecause the Linux uses a version of that。The staircase algorithm。

 you guys have covered the Linux scheduler already right so you know that you have with the multiple cues and you jump between cuess and you do all these nice things right？

So they introduce that。And there they actually introduced the concept of fair Staing， which was born。

Q， and this was actually before mainly。Basically interchange between the two。

Communics where people would implement something and something else would get invented 10 minutes。

The completely first me basically was the lock， which is actually the current version that people use。

I don't want to sne into themic。That was hard。It was I was in October 2007。

 so it was fairly now stable， it has been there for almost 13 years。

And this is the default kid today， there is a very nice explanation。And this link。

 I'm sorry I have not supplied the slides before the lecture。

 we promise that we'll do better the next time。So， basically。

What people think that processors are going to do is that they say that have one CPU。

 one single task。It takes 100% of the CPU， have two sc tile。

 it takes 50% of the CPU where each of them were they run in parallel， right This is what people。

Think that the computer is doing。 Everything is drawing in parallel。 my work processor will。

My U would whatever， and I get the same。It feels like everything's running in proud。

 nothing is stopping， right？In reality， what's happening is that you run a single task。

 you run 400% of CPU you run two tasks， you run a single task 100% of CPU， you run four tasks， again。

 when only 400% with the CPU， and then you play with the coachess and time slices and so on。就。

You know that there are I01 versus CPU1 applications from your undergraduate C systems course and through this course。

IObound applications are similar to， for example。Board forces are like you're an board editor。

re here。Per programming editor。While other like CPU you want applications more like MAlab when you're running Si then you just like know press run and then wait for 10 hours or think it's something。

 or you're in a network expert。Need to talk about deep efforts。

Where you basically wait for weeks and then get some result。

Now for MattA when you're running the simulation， that simulation ends one second earlier。

 one second late。You wouldn't feel the difference， right？I took one minute。One second or 59 seconds。

 what is the difference， I don't feel it。For interactive application where you're actually pressing stuff。

 I mean， if it's sggish， if your editor is sluggish， you're unhappy。就。Basically。

 what most processors try to。Now。Do is to favor I based applications。

Where you actually interactivity is much more important than CPU bond。

Obviously the world is not like that because your MALb editor can your MAlab is going to write codeV and then it's an interactive application。

 but then when you press run it's more CPU bond application and then you want your processor to be able to out of the blue。

Detect what is running right now and whatfi program is in other ways。I mean， you get very bad。

There is the concept of priorities which all these operating systems actually inherited from UniX where you basically say there are two kinds of priorities and names。

 one of them is nice values。If I'm nice minus20， that means that I'm very bad with everybody else。

 if I'm nice 19 that I'm very good to everybody else， I'm very generous。

 I'm happy to basically be kicked out of the processor， everybody should run。

There is also real time prioritization in Linux that is used for the real time scheduler that carries values from 0 to 99。

 where basically now here minus 20 is I have a very high a very important person from me。99。

 the real time prioritization is why have the has priorityity。Okay， so they're op in some sense。嗯。

There's time slices where basically you have a quota the quantum for an application run for processor。

For the poster certain application。And CFfS basically has a nice way of completing time slices。

 which is a combination of both the。Ts like that， the actual。Dural coter that you had。

And the niceness values。Now， this is opposed to minutes where you have the different。

Ces moving between the queuees meant your half higher period to low period。嗯。

The way it manage does things， at the very fine identity is that。It assigns a share of the process。嗯。

By share of the processor， we mean that there are two applications。

 each one of them should get 50% of the procedure die。Okay。

 and that adjusts this chair using the niceness values。 So it uses the niceness values as an actual。

Wait to how things are。あ。つけるよ。喂。So， let's give an example。

The process as is running your favorite word editor Open office。Your favorite encoder， Vi encoder。

 E back。actually， that VC is basically an encoder， which basically means that it takes a video on。

 does all sorts of very heavy pose in it to actually get。To do that， including for the video。

 open office， open office， our favorite。So the scheduler idea of the scenario would be that have the award ever run really fast？

Actually， you see， nobody really cares if you encode the video in an hour or two hours， I mean。

 well people might care， but it's not like，It sounds like if we're talking about in 10 hours or 11 people I。

Those is the notion of timing。喂。Is it one coffee or10 coffee but I。So。The idea in an ideal world。

 what you would have is that。You have the。That word editor get the highest priorityity。

And that's the high CPU time since this is an IO bound application that means that it will be blocking on IO for so long too many times。

 that means that I can basically start trying the EVC during that time and make sure that it runs but never the word editor needs。

AThat needs。See if you get。So other operating systems。

 the way it does that is that it hit higher priority and higher times slices to interactive applications。

Minix has this。在上下。Nos grantees the text editor a certain proportion of the processor， 50%。

We have two applications。You get 50%， right。When the word edit is or lost。

 it runs whatever else is running。which is the video encoder and when it's back and basically since I promise 50% and you've only run for 1%。

Then you have 49% of the procedure toD。So thats way interactive application。Ca文。我那份给你。

Because they got promised。A pretty large。Basically， proportion。あ、どし。Now。Before I get into that。

 I will also cover it later a little bit。Now the problem is when you have a very large number of applications。

Right。Because now it's no longer 50%， so if you're running maybe 100，1000，100 applications。

10 thread one year。When your're server。I I you to remind everybody of the。

Vinic isvis policy and the fast。啊。So， basically。Basically if you have 1000 applications。

 then you are going to have a very small share of your processor。

 which means that it might not be enough for you to run them and Newux has a solution to that we'll talk about data。

One thing to note again， which is a huge difference between Linuxs and other prison systems is that the。

The scheduler is modular Now in Linuxex Mac used to event that by basically saying， okay。

 the scheduler， all schedulers should be user level processor service， right？

Linux does not do that Linux what Linux does is that it actually has multiple schedulers running in the kernel in parallel and you can specify what scheduler runs which applications you can actually do that with a simple command line。

space。嗯。This means。This is not， I mean， it's a concept of minutes。

 I am not aware of people who have actually。Developed multiple scheduleulrs and run them in minutes。

But Nox， this is used every day， right？You have three main very。Very popular schedulers in Leino。

 and these are the CFS， completely very scheduler。You have the very kinds of scar。

And you have the deadlines kit。In many cases， you run all three of them parallel， especially I mean。

 people who do real time systems， they actually do that all the time。Actually。

The Real time schedule came out with the project。In Europe， where they were actually doing that for。

For high。For baby。System for real time systems， which are like， you know。

 they're like computer systems and stuff where you actually have different。

A real plan constraints basis。These has the definition of scheduleing classes。

 each scheduler has a class and each class has a priority so if you're the real time scheduler。

Or the deadline is can， your priority is higher than CFfS。Okay， and there is like。

You pick bass differently and the base case are is defining kernel that just good see。O。呃。

When you run， you always start with CFS unless you basically say that I'm going to use something else。

Okay， so CFS get there。The mean the bees。You can see the different available schedulers here。

 but you can also see them in this very nice clean natural that they。Where you actually have。

Different definitions for the policies。There's actually an id policy for。For the post one idle。

 and this is mostly done for energy and power efficiency reasons that actually have an id post policy。

For running the trailer， sched norm is basically you're schedulecheduling and getting a CFS。

Ske5 whom wrong robin， sketch that line， there is real time and so on Each one of these you basically look at the different schedules the different schedule classes you have。

The biggest schedule based on its highest priority。

You basically look at what tasks have been assigned。Toけど。This ist comparison to minutes。

 but this is a snapshot for me not lecture where you actually had you couldn't。I mean。

 the concept is that you can't implement everything was like a revolutionary idea and massace。

That's kid here。对啊。User space。But。It's not a really revolutionary idea because Vens has had that support forever。

 it's just much more complicated and much more。こ練しす。scheduleI mean。

 the amount of input that you understand is huge。Well minutes having these。

In terms of the idea that theoretically， you could just like。I canU schedule without having to。

vertible Linux。It has to be。Yes， yes， you need to rebuild that entire。

 but yet again if you're writing your own scheduler。I mean。You're going throw something like 20，30。

000 lines of wood。I mean， at least you're going to write something in the thousands。I mean。

 unless you copy all the scheduler I mean because there are all these functions that you can actually。

Just copy from the other standard， but suppose that you're writing it from scratch you saying you have this brilliant idea。

It becomes pain testing。我子先费。啊，你呢。对。You're re writing scheduleched， you're adaptable， right？

Not anyone is going for getting better server。Also， and as right you know。

 there is the concept of Phoenix kernel views。Where you can actually write Ster as an handcm。

 and this is something that we're try to cover。And that came the way's answer to how do I write？

either down is point。And the weight is basically attached to the current。As you wish。

There are many reasons behind picking TFS。I just wanted to make sure that I'm。

they start interactive proceed， so one revolutionary ideaM in CFS is that there's an interactive process that has already used all its quota。

You can start it once it becomes like once its run。

Although it has used old scter because you know you know what。

 I mean you need to average things across time， so directed for we're always wrong。

 we take Christmas。There is also another reason， which is the hardware reason if you're aiming for portability。

You're not supporting a couple of architectures。But not supporting a couple of our pictures means that youre when actually。

 I mean time。And the， the processor does not have a watch to look at the title， right？

So the way it does that is basically you can at this book frequencies。

 how long have how many things have happened since whatever？

These are drastically different between different processors， some of them are very slow。

 some of them are very large， so all processors when they talk about like， okay。

 I'm doing the time slice。There are。There are things that need to be understood about the hardware。

Like the cooking frequency。Now you can obviously change these parameters as you basically change for port reasons。

 so if you're doing that for a different processor，But here an idea that you know。

 I'm not looking at time slices。And your time is that I'm going to divide it。

And basically not care because otherwise， I need to calculate Da quota for each one of them。

There are multiple other reasons， so we're not going to them。Fairness is an important thing。

 yet again fairness comes at cost if you have a very large number of processors。

If you have a very large number， of course the。But then you end up with a very small quotas for each process。

 right？So although fair is important， it comes at the cost that might do a lot of context switching in the system。

 so if you have 100，000 per seats running，You dont know， I mean。

Just context switching will keep your computer around and context switching is basically when you move from one process to the other。

 we need to do things regarding the cache， okay so you need to basically flush your cache。

 you get to flush your registers， you need to go to jump from one process construct structure to another。

 you need to all sorts of these things that take time， very small time but not。

it once you have a very large number of course。So instead of from roing。The way that。

 the way that Ns does that is that it turns wrong ro。Starting with the least one process first。

 so it keeps track of what each has how long each process has been running。嗯。

And each process runs for a Chinese line a slice that is proportional to how much。

Of the kernel percentage of the kernel should take， but also as a function of domestic values。

Then if there are too minutes。对。CFS defines the floor fine and that's by default one this second。

Okay， so any process cannot run for just down millisecond。

 you can't change that it's a configurable parameter， but there's。

There are very few reasons for people to change that because they don want they ago。

So the computation of CFS， you have time accounting， you have process selection。

 you have scheduler entry point and you have sleepinging and waking up。

 These are the four sports that。That one can look at。啊。

The scheduleular entity structure is basically a structure that defines everything about the scheduler。

 each scheduler has an institutional structure and basically says that okay。This is。

This is for each of us I have a time for which I'm looking for that。I have a virtual run time。

 that's how long my posts has been running number of tick。O。And。I have basically。

 if there are groups， there are different things that basically if there's a parent and some。

 pointers to parents and so on。The most important part is the Vent time， it's the virtual run time。

Tnal basically importance here。The kernel keeps。Track of the wrong page。

That's the smallest runtime course。我不。The uses the red black3 to manage the list。Of process。Now。

 this is partially what I told you about in the early part of the。The lecture。

 where I said that they implement lots of data structures， including red vacuum。Im going出。

Sular entry point the first。Hello， the scheduler， it starts at scheduler。

 a function called scheduler。the internal notes schedule fee。

And it points the highest priority scheduler Okay， because we have different classes and stores by earn that I'm running the。

Different tasks in that。There are a couple of optimization。

 the kernelel one of them is that a task that is waiting for a processor can be that is waiting for oil can be either a task interruptterrupable or task uninterrupable。

And aninterrupible is basically a to that is waiting for I did not get its eye。

 so it's going to wait until it gets its eyeO right So no matter how many times the kernelel tries to start that to because is just going to not。

Okay， to interruptible is basically a to that is sleeping， sleeping。But it's winning to wake up。

 it has its theater or something Okay， these are on the coolings and Ban I think with that。

I conclude exactly on time， surprisingly on time。So any questions？

