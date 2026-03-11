# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p26 -26-Lec13 Video_ Virtualization - Part 2 (03_05_20).zh_en -BV1iP2CBaEHr_p26-

Okay， so just scroll。Those of you were just walked in。

The PA is not have special office hours right after this class in this building。

 four to five third floor conference room。3ト two。So if you have any last minute questions about the lot。

 please stop。I put down the minorityia on the whiteboard。Announcing this in every class， I guess。

What this point is not Tuesday is exam， so there is no class。that day。

The exam is an evening exam at 7 pm in the computer science building room 142。Gest book。

 lowest load 19 winner。And now I have actually finished settinging the exam。

 so I will let the end of the class say a little bit about what strategy might work best if you want to start to。

Here on more of a study writer。不是当时在代理人。But let's continue our discussion on virtualization we wrap that up。

 and then we'll talk a little bit about example。So last time we were talking about virtualization and I introduced two types of virtualization。

Hardware moistization。U大 one大 hyper。So that。Allowed you to emulate a processor interface using the native process。

So all of that so that's virtualization at the algorithm today we are going to talk about virtualization at an OS level。

 this iss called OS level virtualization so you are going to take the system called interface exported by the OS。

Use the virtualization layer or expose other abstraction。

Thats by large the picture you want keep in mind， there is essentially a figure here that shows what OS virtualization does so if you heard the term container or docker all of these things are actually OS level virtualization。

Unlike virtual B and VMware and parallels and KVM， those are all hardware virtualization。这是 doctor个人。

等着如我是。Okay， so the picture you want keep in mind is one that is shown here here there the one on the right。

Look at the one on the left， so you have a machine， you put a normal over of that machine。And then。

You might have some processes， you encapsulate them inside what is called a container that provides OS level voltageage so what does this do for us it provides us isolation so anything that is running inside the container you can limit what it sees outside the container。

Okay， so for example。You can say you cannot see any processes that are not running inside this condition。

Although there are processes coming outside the container does not see the or you can limit what files are seen and so can also allocate resources to containers as we will see Okay so this is a mechanism that is going to be a lot more lightweight。

It then regular。大我面大と。Vtralization and to understand why heres a picture I don't know if anyone can see this in the back but let me explain what these three things are so this is type 1 hypervisor I showed you this picture last time the one in the middle is type 2 hypervisor we saw that picture as well the third one is OS virtualization。

So what should be clear from this picture is OS virtualization is a very lightweight virtualization technology as compared to both type 1 and type 2 which are more heavy。

What is that。The first thing you have to realize is in both type 1 and type2 inside the virtual machine。

 you are going to run a whole operating system。It's windows or Linuxups or whatever it is。

And then you run processes on top of that OS。In was virtualization， you will see that。

You only have one OSs which is the OSs that booted on this machine。

 there is no second OSs that is running inside the virtual machine or inside the containerer our only processes is running so that is going to make it faster because you don't have to boot up a second OSs you don't have to boot OSs inside every VM there only one OSs thats a native OSs。

So it's going to be。Faster and also bely lot more lightweight because you have only one OS okay you don't have here the more the softer layers。

 the more overhead you are going to in so you have the postOSs， the virtual and the hypervisor。

 a guest OS that's already three layers that you have to deal with so all of that becomes one layer which is just the way。

Yeah， so so think of OS virtualization as a much more lightweight platform Okay it's much faster to start a container because you don't need to boot than over as you just start it and put the process in and just start the process that's all you need。

So that's the good part。Looking at this picture， what do you think might be some downsides to OS virtually？

The upside is more efficient， more lightweight， less softer， overhead and so。た youけな。Yes。

 so you cannot run multiple over。 That's a huge。 So of course。

 that's going be anything you could do by running multiple overseas you cannot do。点该。这。So。

There is less OS level isolation in this case。So if you have a bug in the OS。

And you either inadvertently or maliciously trigger that bug。In OS virtualization。

 everything goes down because the OSs goes down。All other containers will fail as well。

But in both type 1 and type 2 virtualization， if you exploit a bug in the guest operating system。

 only that VM is going to go down。Other victimss have independent os and the。And at least type 2。

 there is something that's running Manith， which is the host to us so neither of those are impacted。

So that is the right way to say this is there is more isolation that is provided by type 1 and type 2 hypervisors than you have in OS。

So this is by isolation， I mean by exploiting OS bugs is more safety than isolation。

 but there's also some impact on isolation。Exactly。

So now let's look at what does this mean and how does it work。

 so essentially it's a very lightweight mechanism for you to isolate processes that are running on your machine。

And then provide some resource allocation to a group of processes that is essentially what it is and I'm going to draw picture here。

所有我。So let's assume that you have a machine。It。Learning some processes， which I showed certain。

The size are this。The disc has some fights。you course。

So typically if you did not use any containers or any virtualization。

 all of these processes can see other processes， the presence of processes is visible。

 all processes see the file system， so long as your permissions you can access all files and all of that is true。

Now what containers allow you to do is to actually drop boundaries， so you can say。

YouCan draw groupsop saying we cross the seas。Whatever I in today。So I grew this。

Boundary which is basically an encapsulation of processes and an encapsulation of files and you can say that's a container so what that means is processes that are inside these boxes cannot see anything outside that box that means these processes only these two processes can see each general they cannot see these other good processes these processes can only see those files and nothing else because you can limit what files you see you can limit what processes you see furthermore you can say this container gets two G of memory。

It gets so much CPU， so you cannot actually get even though the machine might have more memory available。

 more processing capacity available， you are going to limit what these processes actually get。

So by performing this isolation。Of processes， isolation of fights and doing resource allocation。

 we get this abstraction， which is called a container。 that's really all there is to it。

And there is no act。Ipervisor that's running theres doing anything special is just a way to provide a better way to isolate and allocate resources to process。

Any questions on this？So the way we are going to do this is really through some mechanism。

 so there is something called namespaces we are going to see very soon that is going to give us this process level isolation so you can say that these processes in this namespace cannot see anything else。

We are going to look at。Ca C groups Okay that's a Linuxux mechanisms。

 not specific to virtualization or containers， but C groups will allow us to say once you draw this boundary。

 you can say what resources it should get how much should get on CPU you should you get so you can then do resource allocation。

the first one is isolation。 The second one。also look at things like cha root。

 which allows you to say only see these filess of this subdirectate tree on my disk and nothing else。

So the combination of these three things allows us to actually implement Linuxux containers and then we'll see Docker actually runs using Linuxux container。

Here so let's go through these one little time。So let's start with namespaces。

So one ares namespaces an abstraction that allows you to restrict what a process can see。

 which is what I already mentioned， so you essentially get the illusion that you are the only process in the system。

So let's try to think from an OS perspective， what does that mean？

What does it mean that this process cannot see another process？Any thoughts on what is。Message。

 any other。So you cannot saying if you are a process in a container。

 if you trying to send a process message to a process outside the container is not going to work。

But more fundamentally what's happening is if you actually do something like PS which allows you to see all the processes that are running。

 you only see that subset even though if you run Ps outside you see all the processes in the system from inside you only see those processes so the presence of other processes is not even known to。

Hence， you cannot even send a message to such a process because it will just look like you're sending a process to a non message to a nonexistent process。

So you only see across I， you cannot send messages， you cannot do any signaling。

 so all of that is limited。Once you actually put the process in unname space。

You can have as many namespaces as you want that dense looking picture at the bottom shows you three and you created a blue green and。

Right， and you put processes in each of them， and none of them can see anything outside that name space。

So。Can also yes does it also mean that for the process。

 it appears that hundred percent of the CPU is utilized by itself or。

Okay so the question is does it look like you are using 100 percent of the CPU itself at this point we have not limited what resources are being used by this names we are just limited what you can see。

 not how much you can use Well come to how much you can use when we do the next slide。

So that is going to be a C group， this is just saying I cannot see so if you other processing。

 but it doesn't limit you from using resources。You can use as much unless you are limited that you can use as much memory as you want。

 you can use as much CPU as you want。 There's no limit at this point。

 only thing is you don't actually see the presence of other processes。 That's all the is。

Now you can not only limit the presence of other process。

 you can do other things like you can also have users that are assigned to na spaces。

So just as you have let's say， set of login names and passwords on your machine。

 you can say these users can only be seen in these names places so inside that name space some other users who exist in the system may be invalid because you cannot actually see them。

For the presence or users can be limited you can also limit which network interface cards are seen。

 And so if your multiple interface cards you can say this namespace or this container can only use this card So for example。

 you might have an ethernet card and a wfi。あ那ク。Okay， so wireless and the wiredNe。

 you can say this container can only use my Wifi interface。

 so in that case if it tries to send any data on the wired interface it won't be able to go even see it。

So you can limit the network interfaces， limit user IDs， limit process IDs， and so on。So also。

 you can actually limit mount points and so on saying you can only see certain value。

So that's the concept of a namespace。Next is the question that was asked now that I created a namespace which is a grouping of processes that basically only see each other but nothing outside that grouping and some files and users next is how do you limit what what resources this namespace can use that is done through the C group abstraction C group is essentially a command。

That in fact， you will do a lab where you will change all of these things you will create a namespace。

 you see groups to allocate codes and memory to that name space so youll understand how actually a container is built。

In a subsequent la。WeCom after spring break。So C groups allow you to do resource isolation or exactly you can set upper bounds or how much resources can be used an upper bound or how much CPU can be used an upper bound or how much memory can be used and upper bound or how much disk bandwidth can be used and so on and so so you can set these upper limits and then the processes inside that da space are only going to be limited to using those many resources and no more。

So how you do this， Im going to tell you about one technique to do this。

 which is called weighted proportion scheduling， but to some degree you should know how to actually do some of this because you break the lottery schedule。

A lottery scheduler is a way to allocate resources。

It does not actually put a hard upper bound but it is going to give you an upper bound so if you have two name spaces or two containers you can the amount of CPU you get so if you give one is to one to two of them they are going to get 50% of the CPU you give one is to2 the first one gets 33% the second one gets 66%。

And so on and so forth So that's one way you already know how to do this what I'm going to talk about is a different type of a CPU scheduler that allows you to do exactly that in a deterministic fashion which we have not encountered so far but so there is a deterministic version or lotter scheduler which also allows you to do the same thing。

And so that's called fair share or rateed fair share skin。I'll talk about in just a moment。

And but you can also do other things， you can also say I map namespaces of containers to course。

 I say that if I four course， then one course is given to this container。Only run on。

 even though other course may not be used by。So you can do all of these things。二十せ。

so let' us talk a little bit about proportional share scheduling and this is also named fair share scheduling in the literature。

 it is simply a deterministic version of a lottery schedule okay how does this work。Essentially。

 every resource that you want to allocate， you can essentially assign a way to let's say。

 a namespace or a process。That's a process one guess me， W one process is。嗯。WX。

And then the scheduler is deterministically going to schedule a process so that the resources are located in that proportion。

And exactly the same concept as lottery tickets， the waits represent same as lottery tickets。

So you can give it away the rate is one is to1 you get 50% in this case it's going to schedule deterministically what does that mean so when you run the scheduling across the schedule function in lottery schedule you do a random number generator that allows you to say which process one the lottery and that gets to run next here you are going to explicitly track what process but schedule so if you do one is to one you are going to alternate the quantum。

so this one is going to run and then that one is going to run。

 so you're going to try to do one is to two every time this is going to get two points。

 so you're going to schedule that twice explicitly and then schedule the other one。

 so you are essentially doing a more deterministic version of that randomized schedule。

I leave out the technical detail， there's a equation that allows you to track how many quantum each process has received and is it in proportion to the weight that is what is used by the scheduling function instead of using。

拉定。But essentially， that is what it is doing。So this is going to be used in， so as you can see。でか。

Lottery schedulers， deterriministic versions on like fair share schedulers。

 they are used in virtualization frameworks quite a bit。

You can also use them in routers and on your network interface cards。

 essentially to partition your bandwidth。You can say for every one packet you send this cross。

 this container gets you send two packets。でく just。By assigning either lottery tickets or ring so you can say do that and that will allow you to give more network bandwidth to one container over。

So all of that is essentially done using this notion of proportional share scheduling。So this。

There areMany variants of this。 This is not one technique。 There are literally dozens of。

Varians of proportional share schedulers and many， many research papers that have been written。

 but by and large， they all do this one thing。which allow you to give a weight to either a process or a process group。

 which is essentially a container and allocate resources in proportion and doing so you essentially also give bumps now what is the maximum amount of resource that you can use。

Now there are some issues you want to keep in money。

The some variants of these are actually going to cause starvation。So for example。

 what might happen is you have given two processes which1 is to one。

That's just called managed to take。Now， if both processes are active for every one quantum received by the first process。

 the second process get10 qua。Then typically the way the scheduler tracks this is keeps a counter。

the counter is going to take every time you schedule it right so basically you say if this counter is5 this has to be 50 because you have to have 10 times Al because that it I used five quantums and this one should I use 15 on。

Now let us suppose that the process with weight 10 or Lotery ticket 10 starts doing I it becomes is block is no longer active it is going to go off and just wait。

In the meantime， the first process is active， so it's going to keep getting scheduled because there's no other process to run。

So its counter value keeps growing。Because it gets scheduled more and。Now。

 after it gets runs for a why， let's say this process actually becomes active and it's I always done。

Its counter as an increase since it was doing I still like I stuck at an old value。In the meantime。

 this process has executed many many quant its counters increase significantly。Now。

 if the process CPU scheduler looks at this and say this should have gotten 10 times as much as this other process。

 you will essentially start this process for a while and keep running the second process。

For no fault of the first process， all it was if it was just。I a CPU by just by doing I or。

 this process seems to be getting an unfair share of the。

That's one that last point is saying saying that you can actually if you just do this in some trivial way you are going to get all kinds of problems so you have to deal with all of this and that is why you have many variants of the skills。

 the early ones suffered from this problem。Okay， so essentially。

 if you got blocked and became active again， you could run for long periods of time and star everyone else。

Okay through the share based scheduling。Varianance of this。So there are many variants of them。

 so I think if you just do allocate credits。That you have this problem so but what you have to do is account for when you block。

 you don't want your counter to reflect the old value。

 Youve got to still take it as if its executing。 So there are ways you can get around。I look。

 you don't accumulate credits because you're not running and then use them on。Is this here。说。

You will see that actually Linux has support for multiple of week， and this is just。Bachelor。

you should see is that we put in a fair scheduler that tries to use weights and tries to get around some of this starvation problem。

 they call it a completely fair scheduler。But haven't proved that expectation。被诉人。多这个。

But it is a variant of our proposed skills share。So it is something that you can actually use。

 you don't have to use for scheduling containers， you can actually change the CPU scheduler。

 the default scheduler from MLFQ to credit based and then that is what Linuxux you use to schedule all processes just as you made your Linux on lottery scheduler which became the CPU scheduler that default。

 you can do the same thing in Linux as well。Thank for their support internally for many different。

So this just puts it all together as far as containers is concepts and are two or three concepts one is you are going to have the core notion of a namespace to isolate。

 you are going to have the notion of a C group to allocate and then you basically have some other tools that we are going to see which a user space tool that allow you to use this in an easy fashion。

So if you take all of these techniques and put it together。

 you're going to get inux containers or talkcker and things like that。就说。

So what does Docker act on this so Docker is a software layer or a set of user space tools that essentially uses Linux containers underneath。

So what it has done is added tools that make it very easy to create packages that you can download and run as building。

被告你有没么信？So its easy to create these packages， you can use a git repository to have version control of these packages。

 you can push packages to developers， you can download things from a Docker repository is essentially a Gitripo and then run it without having to do much than download ads。

So it provides many software engineering benefits that have very little to do with containers at all。

First thing it does is it allows you to package complex applications so that you can just download and run。

 you don't have to sit compile them， configure them and then run them。

The old way is if you want to get a new application to run on your machine。

 you got to download the source code， you got to compile the source code。

 then you have to read that documentation because there' will be some configuration file that you got to go and change and then you run。

The best case， you don't have a compile， look and go to a binary depositosory and download the binary。

 but you still have to configure。And configuration non tria as the software packages get more complicated there are ever more configuration details you got to worry about。

It takes a long time for you to actually get anything complex to run。

Theer simplifies this because somebody has already made a packet。

as a docker image there the binaries are installed。 there's some good configuration already done。

 So you just download and you start the container process this。

So a lot of complex software is not distributed as containers。

 so you don't actually have to download something complicated a databases。G value stores of。

Web services and things of that are where you might a multiple software component。

 It's much easier to actually deploy them as。And clearly， that really is most of。

 there's a way of packaging and。Distributing software without having to put too much burden on the end developer this really has nothing to do with containers。

 but containers made it very easy because you can also run that package in isolation。

So what that also allows you to do is if the library is that that package needs are different from the ones on the native machine。

 you can actually ship those with your package so you don not have all kinds of other dependence because one of the other problems when you try to install a piece of software is it depends on 10 other fix then you got to first get all of those 10 things and。

Install them， and then you can get them。Application So all of that dependency goes out because you can package everything you want and send it in。

So it is portable， it will run across OS platform so once you have a docker image all the dependencies are in there so it will run on different versions of OSs even though the native OS might have different library different version it will still run in that sense it basically going back to the definition of virtualization I said youre essentially emulating the interface where the package was designed you don't really have worry about what's the OS interface what libraries are installed。

So are going to affordability。As the deployment brain that someone you build。And self continue。

Here is the picture。So this same picture I showed you earlier， this type1。

So I think that's con the work that you doing here。Those are the containers。

 and then the green thing is essentially what you added to the container。 We set of user space tools。

 really。Docker does not changed anything inside the virtualization part of Linux that is a plain Linuxux container what you did was added a way by which you can create and distribute containers easily。

Using repositories and software development。国コシぞです。So。Here are some things you wanted to think about。

So I said Docker is a Linux container technology。I don't know how many of you use Docker。

But if you have， you do know that it actually runs on multiple platforms。佢近嘅打嘅 for。

For windows of documents on Linux。So we are to ask， why does that。好他再多。

er is actually a Linux container or Linux virtualization technology。Do understand the question。So。

 it's basically。If you are not running on native Linux， the way Docker works。

 a Docker actually runs on Linux， can't turn on anything else。

So if you are running Docker on Mac or Docker on Windows。

 there has to be Linux somewhere in the picture even though you don't see it so whether you installing Docker it will create a very lightweight Linux VM which is running under the hoods。

And all of your docker images are actually running on that lightweight Vm。

 even though you no longer see that its not actually running on Windows。 it just looks like it's a。

So keep in mind that Docker for Mac and Docker for Windows is no different from anything I said here。

 except that when you do run it on a different platform， you actually have a Linux VM， a proper VM。

 which is like a virtual box VM that's running in the background， which you don't see。So earlier。

Ptainers are running on that Linuxux kernel a knot on your native machine。

But if you're running darkcker native Linux， you don't have that extra power。So on other platforms。

 it's essentially because containers inside a type 2 wheel。

We have our Linux VM that's running as a type to VM in the background。

 They did a good job of hiding it。 They don't make you install Linux and they installed。说で。So。

That I didn want to mention that， but as a result of what they have done。

 it looks like you can make a Docker image and you can run it on Windows Mac Linux adjustment。

Yeah because they essentially made the next run。Other platforms， as well as。

what that gives you looks like your cross platform competitively。

 You can essentially take a docker image that's built。

 and then you can run it on a map if you're docker on。So from a developer standpoint。

 that's very good because you don't care what your development machine is， it just runs。

You the same application and it doesn you don't have to create three types， three binaries。

 one that runs on Windows， one that runs on the next and。The sameme thing runs on on。Ts of capulator。

The other nice thing about Docker is it actually makes very efficient。

Use of the underlying file system by using a special file system called a union file system。

 which we have not seen so far。So what does a union file system do？Okay。

 so let's say you have some file system on your machine。 So there's a root directly this user。どかう？Oh。

能不能说。That's your file system3。要么你还我找嗯。Image， it has its own file system that it has been built to。

If you did not do anything special。The disc of this。

Container is going to be as large as a normal file system。

Because they basically say everything that this thing needs is packaged with it。

 which means that all the file systems， the file libraries are packaged with it。说。

So if you would actually install this without doing anything special。

 this image is going to be large because it has to have a copy of the all file and some other filess may be duplicate of this file。

ね指出せ。If I a union file system， what do do？This file system come and this files are literally the a set union。

 which means that if the files are the same， you don' only have two copies， you only one cop。

So only the extra di is added on to that file system。That is called a union file system。

 so it makes a very efficient use of the files that are actually stored because you don't have two copies。

 you essentially take a union of what is there earlier and what。

So everything that is here is still visible and all the new stuff is just like adding a date that just the extra file is added to your file system and it just looks like one big file system。

You see that there are two files over layer on top。That's called the Union file system。Now。

 it makes good use of your storage space， but there are some subtleties to deal with。

So so let's say you have。发 user。他律是。It is a find user。

Which is visible both outside the container and inside the。Now， let's say theres an application here。

对。Modify is this by user。Based on our understanding。

 those changes should be visible inside the container because you made the modification。

 it should not be visible to anything else outside the container。That's what we said。

 isolating whatever is inside。 you can make changes this not。

But if you are because of the union find system， we can go and modify this file。

Its going to become visible to every other process in the system。

 which violates a assumptionsumption of isolation。We had kept two separate copies。

 This would not be an issue。 You have your own pilot copy。

 and this is the root file system you make a file chain to your private copy。 That's fine。

 Nothing else。とし料。But we said we are going to be smart and we are going to make a union file system to save storage that space。

So now many fights are common。So if you make a change， it becomes visible outside。

 so you've got to deal with this issue。Is that clear what I said？这我东信。かです。都考虑。Of first two copies。

 but this technique has a name。This is called copy on right is is called cow So a very important technique it not just used here it's used in lots of different scenarios in operating systems。

 distributed systems and so on。 So this is called。So this called copy right。

Copy and write essentially is a form of doing what is called lazy copy。所有没人给你写了。

2 entities share one cup，1 and5。And even though they should have two copies of it。

 or only when you make a chain， do you actually make a copy and have them damaged。so so in this case。

 if you write to the user who， there will be two copies of who are restored。

 one that is specific to that container and one that is still native to the files。

So only making a copy as you need to， but at that point。

 you've got to spend that extra storage space because you can。告别。There scar copy on right。

So you essentially have a union file system that is a copy on red or a cow file system。

 so lots of things are going to essentially save a lot of space for you。

 only things that are going to diverge from the native file system because you started writing to it will have a second call。

the file system has to track everything。 and this is exactly like you made a fork of a gi repository。

Okay， so then you can start diverging from the main pra and you have your own changes。

 which no one else can see in the main。看清早。That's a good question。entire is isolated。

 should it be able to use the RVC， the underlying OSss button。

So typically when you create the container you are going to allocate the file system to it。

 okay those are the files it should see。滚。Now， as I said， you can。

 the way you typically do this is you could say this container has no restrictions。

 You can see everything that underlying。Fight system。Has so all the files are this。

 or you can say this container is limited to the user。So inside here。

 youll only see slash use and you won't see slash links， slash local slash， those are not visible。

So that is basically the name space abstraction in company。

So you can limit those what you can see and what you cannot see。

that is what containers allows us to do。 What we are talking about here is a different concept。

We said we download a docker image that somebody else picked。

When the built they said these are all the files that you should see。

 you should see user you should see local and all of the libraries and so so when you download this what way to do is you should take all of those files and you download them and you keep them in your file system said that is wasteful so what you will do is something smarter youll actually look at which of those files are similar to what's already there and you will share them between the two because this is supposed to see those files so you won't make two copies。

So that is slightly different from saying what you cannot see。

 this is you are allowed to see this and OS is allowed to see this possible。

 but you only keep one off。Where is the copy it' actually stored on the native file system？So。

 if you have an external。Sorry。Yes。If external soil。

 how do you see that is why it's called a union file system Okay as I said。

 it looks exactly like a gate rep deposit if you understand how gate works Okay you have a main trunk。

By default， everything we all developer see the being。

But you can create a fork of your reportpo and then start following a for and if you are following the fork。

 you only see the files in the for， So if you are in the main， you don't see the fork。

Exactly the same thing happens here。You have a file system three。

 and now when you make a copy on right， there are two versions of a file system Okay there's a version that actually has these changes。

was made here and there's a version of the file system that is not does not have a change everything outside see is this part this view of the file system here you see this view of the file system。

Basically， all the files are stored as a union， but what you see is a view of that。

 You don't see everything。 You only see what you are supposed to see。This stores。My question is。So。

 so when you。关于案。到时我。ThePro。fi。storage。So if you're asking if I more some volume here and the the container is using it if the don on see。

So typically， if a process is using files in a volume or not。You will not pay allowed to amount。

 It will say that the volume is busy。There something to， even though there's a process as a final。

As a safety feature， the West will in a measure force。The哪被。So that problem is not working。

So so dark客户 basically。So not every single drive， as much as。

What root root file system it's supposed to see。If youre mounted at some other volume that's independent。

 you're not even supposed to see it here。If you're in the modes or sound bled。

You don't actually see them inside the f。 You can un them without any。

 It is basically the root file system that we have on。UFS is only running on doctor'。就是按照。

Our system is completely。So union affair is something that Docker will add。

I mean you need a little bit of terminal support for it。

 but so that this is actually going to store multiple copies of the file and all of that。

 but only some things are visible here and some things are visible。Sorry。あ。

Okay you can learn other file system。If I make a new file。Though it doesn't matter。

That's just a single file。So if you make a file， new file， which did not exist at all。

 you will basically have that file here。 It' is technically stored here somewhere in this file tree Yout be visible to outside entities but yeah that's one risk local。

This is just an efficient way of using all your storage。Easy way would I mean。

 you have your private copy， there's a root file system you make your changes that are not seen outside this changes here are not seen inside anything this stuff。

But that's going to waste a lot of storage space。 So they said let's make is efficient。

 So let's make a union of everything， but each entity see of you don't actually say everything。So。

I'm going to say a little bit about why virtualization is used to it。

Okay so we started with saying this is a 1970s technology。

But now it's even more popular than what it was designed for designed for ensuring that you buy a new machine app you don't have to quote all your application by rewriting code。

 they just not。So that was the original use case， but now the use cases have changed quite a bit。

 so you run them in data centers。Da center， essentially machine lots machine room with racks of servers。

This room used to be a data sector， that's why it has this funny floor。Ongo floor。Neither as it made。

Data centers now you have large servers here you might actually not want to allocate an entire big server to applications so construct virtual servers by adding VM and then run application。

But that's。A lot of virtualization is used all data centers are now virtualized。

 they essentially are virtualized typically either using typey1 hypervisor are the more popular ways to use containers and use framework like Kubernetes which we will get to。

theer， which is a cluster。But。So data centers with use scale， another use case cloud computing。

AndSo so it's a cloud platform。You essentially go and say I need a machine and the cloud provider Reds says。

 Amazon or Azure or Google。Computer engine。 So here is a machine。 you can now SS into it and use it。

Typically， they are not giving a real bare muscle machine。Because if you are rude。

 because you are root on the machine。If your root， you can do whatever you want。

 then they cannot take the machine， they lose control over the machine。

 so what they do is they essentially run a type one hypervisor and what they are giving is essentially a VM not a real physical machine。

So that's another use case so practically every cloud provider essentially used virtualization for reasons of retaining control over their physical issues。

Customer machine dies same while you still need control。说的是。ケ。

Third use is because there's stop computing and you can use this to do good development。

You can use this to run other OSss on your machine for whatever reason。呃。Development。

 core development， big use skills。So there are all VMs that essentially have a build and where you can write a code and then you build in a VM。

And you can test it in yet another VM， you can have test environments。

 in another VMs and so so software development processes use VMs quite a bit as well。

In addition to developers actually using them on their machines for。不能说。Heres yet another。

So kind of on the same positive there are certain servers called mand servers where independent server blades are combined less server and then。

Vatulation is done on top of that to divide into a particular pieces so instead of combining them and spliting them I don't they put an hypervissor and dedicate one to one person you asking what blades I mean usually blades are combined into a single moonshot and then virtualulation is added and then it is split again。

So that it would one over goes to each person。So instead of that you just support driver vior on each blade and then could you provide that to an user so there are many ways you can actually allocate resources right so the scenario you are talking about is a blade server which is made as one logical pool of resources and then you make VMs or topco。

A lot of clusters look exactly like that When you come to Kubernetes。

 you will say thats what it does， it takes a set of machines and makes it look like a largepo and you say give me a VM it will basically make a VM and give it to you so you don't actually control you don't say give me a VM on that machine。

What you are saying essentially says I will expose the presence of machines and I will say I want a virtual machine on that physical brain。

I that's physical sort， when you are lots of machines。Physical machines。 That is you don't。

 if you need a VM， you don't care where it goes。 So they have。

Fraamows that abstract it up one you are talking about abstract and or sold do many other cluster。

So they manage the placement of which VM was on which physical machine。

Is what the why that did could have run a hypervisor on each of the blades if you wanted。 In fact。

 I think it still does。M is is not exposed to。过し。So here is yet another use case， which is。

To do distributed research across universities and so on to actually very early use skills。

 There's a system called planet lab。 I don't know if anyone has heard of planet。Get some of feel。

So Planet Lab is a distributed infrastructure that allows you to run experiments across the Internet。

 so a networking researcher its a very valuable platform So you want to test a new networking protocol maybe you build a new video streaming protocol you want to test it on the Internet the old way was you call up a friends and can you give me a guest account on your machine。

 you run some code there， you run some code here， then you do some experiment or。

That doesn't scale if you want 00 machines in 1 hundred0 different sites that you want to test。

 So what these people did。20 years ago now was I let each university have a few machines。

 they are going to contribute to this large infrastructure。

And then we will basically run containers on them。And we can basically automate the creation of accounts and so on。

 so you can just go to a central node and say I need five machines across five sites and you can say I need one this university。

 this university， this university and so on， and then it will create a container for you on each other。

And you can log in into the once the experiment is done， you can z term it。

 it looks like a cloud except that it is highly distributed。In the cloud also， you can do this。

 but typically you might have only one site of some very small numbers。

So these are machines that are spread across literally hundreds of universities across the world。

allows you to do interesting research experiment。 Okay that is one of that is one of the early use cases for index content。

 They did not use type 1 hyperviss。 They decided to use。Alexi。

 Linux containers and the software or Vi goes that brand on top。

Because they wanted more lightweight machines。Each universityrs had only two or three。

 so you couldn't earn lots of years。W certainly lots of。So the last thing I want to talk about is。

An interesting technique that is possible using virtualization so we talked about lots of things you can do and you can take a machine。

 slice it into smaller virtual servers。かで。Iolate what a process can see and so on。

 So all of those are good things， but there are certain things you can do in virtualization that you cannot do without。

One of them is what is called virtual machine migration。

So let me explain what this is and why it is needed。

So let's assume that you are running a process on submission machine。Next same some。

For whatever reason， let's say the number of requests that start coming to this website just grows quite a bit。

 maybe a small web store， but maybe the product they're selling has become very popular。

 load goes up。Typically a load goes up， machine gets overloaded and then it basically stops accepting because if you go to any overloaded website you know what I'm saying so you say server are busy or your machine will just on request will just hand。

I was going just take that anything photo。So what is the answer to this question， you will say， okay。

 that machine is or that where application is overloaded， let's put it on a bigger machine。

Give it more chd， give it more memory， so now it has more resources。

The normal way you would do this is you would sh that。Webs size server down。

 you will move all the code， you will move all the data to another machine。

 and you start everything up and hopefully things will be better but that means there's a downturn。

You basically had to take the application down and move it which may not be desirable if you are actually running something important。

 you can't just take it down in the middle of。Users are accessing。Now。

 virtual machines allow us to do exactly what I said without actually seeing any downtime at all。

Through a technique called VM migration so you can essentially take a virtual machine on one machine and say just move it to another machine and this VM migration technique will do it while the application is running the application won't even know that it has moved from one machine。

So this is called VM migration， this kind of stuff you will not see with our virtual machines at top。

So， you might have。え？我新。あ不是。先售下点人 here。You can essentially just move there。

Different machine without having to shut anything now the OS will run。

 the application will continue to run。 Everything will look exactly the same No one will actually go。

てしいですね。So that's a good technique toll see how to actually make it work。

So that is essentially going to migrate the OSs running inside the VM。And all the processes。

 because the entire VM is going to move from one physical server to the other。

Is that really what I said we see how to do this question？That is我。Yes。有しよ。That's the bar。

So there are two ways to do this。I talk about a simple way which is called the pre copy that I talked about a different way。

 which is called post copy。So here is the here is an approach。 So initially。

 let's not worry about files on disk。Let's just talk about what is running in R。

So what you have the OSs， we have some processes that are reset。

 we want to move them all to another and well see how to do files in just a minute that's not what you go。

最严的 what别是 do。Let's just number all the。Number all the pages in your Ram1 through and。

So next Ram has n physical pages。You have to move all of this data。

So let's just start copying them in sequence， so you'll copy send page one over so basically youre going to essentially go here page page one。

 send it page two send it there page three and it there so youll send all end pages。

So once you' are done with this， you have10 pages on the other machine。

But keep in mind that the applications here are continuing to run。

 they are going to modify pages new processes start processes will terminate。

Alllocate things on your heap。 So while you are copying this pages over some pages will change。

So those are actually the pages here shown in red， so that blue is essentially the ra of a VM that you are copying。

 but while you are copying it shows that two pages changed。実ちは少年ぐらい。

So what is now on the other machine is outdated because it has some pages that are the same as the first machine。

 but some pages are newer on the first machine， it doesn't have。To watch your read。啊对在まけ。

We do second round this time we once send everything we will only send what is changed So what that means is while you are sending you also have to track what is changing。

Right， so when you are sending one through end， when you are doing this。

 every time a page is updated， you say this is a dirty page， that's a dirty page。

 So in the second round， you are only going to send the changes。So in this case。

 you are going to send those two red pages， same thing is going to happen again while you are sending them some other pages matching。

But the important thing is since in the second round， you did not send all of that data over。

 you only send the changes， the amount of time it took you to send the changes is going to be significantly less than the first round。

If you assume that on average x number of change pages change every second since the second round is shorter。

 the number of pages that change in the second round will be less than in the first the number of pages that change in the second and so on。

So maybe now next time around， maybe only one page。So essentially， in every round。

 we expect that the amount of。Dirty memory is that has changed while you're sending the previous round is going to keep shrinking。

Eventually you are going to get to a point where that change pages is very small in our example in the third round there only one page that is sending one page ought to be fast。

So what we are going to do in this case is we are actually going to suspend the execution of the first rule until now the VM was just running。

 it could do whatever the OS was running those changing pages。

 but we are going to suspend it temporarily。And we are going to now send that page over。

At this point， the two machines have an exact mirror copy of only。

Because the first one now we supend。 it's nott change any memory。 Nothing is running。

 It just the hypervisor just stop scheduling。 That's what su。 Okay。

 hypervisor nexts not schedule that。 So the memory will not change。

 You send that payover now the two Vms look exactly I。Everything that's here is on the other issue。

Now the second hypervissor will just resume execution of that V。First。

 hypervisor will just delete them。And now the VM has magically appeared on the second machine。

And you will resume execution from exactly the assembly instruction that you left up here because you just pauseded it。

 you copied the last page， that state is identical here so if you resume execution of the realm it should basically be exactly the same as the first。

This is called virtual memory migration， the process I call you is called pre copy migration。

 so it's an iternative copy。It's copyping it round and the hope is every round will have less data than the previous。

If you are not， every V will be this well behaved。Because if you you could construct the workload which says every second just go delete all my memory and reallocate all the them。

 that VM is not getting migrated anything soon because I just want to keep on。

Sending data and then a lot more data and not more data but most processes are better behaved than that。

 So hopefully we will basically iteratively converse to a small if pause the wheel So there's a very tiny downtime where you send that last amount of data over which is almost imperceptible it's the order of nearly seconds or this so you can't see it to almost look like you are just waiting to be scheduled here and suddenly you are scheduled。

The Lord actually see it。So， everything is running。 So so what has happened is all the processes。

All of their contents they move over and they start executing on the second VM and our hope is the second VM act second machine has more resources so now your VM can remain bigger and things are that。

And that's the reason we moved it to the beginning。Do you see any issues with this problem？

This process。for start， there's still a small amount down checked。The tiny amount of the。

 but it is imperceptive。 Let's say we ignore it。 So let's say that we are willing to talk because you cannot actually not see。

It's too small。 It could be actually visible to。We don't know how to find any。You should have。Okay。

 we don't know how to find the new here， Yes， what does that actually mean？You should say。

 what about the networking aspects of this？That second machine has a different IP address。

 You just moved everything over。 Okay you， this machine now。

Active TCP connections that are tied to an IP address。

 You just move it over and I said as looking works you should say why would it work that does a different IP address So all my TP connection should break。

Yeah。たけを。And在。7问。Thankす。Yes。I what is said part partly to。We will use it hard。

 but we have to do it differently。So the first thing is youve got to realize。

Physical machine there and physical machine， B have two different ideas。If there's VMs。

Addres was tied to the physical Arab。I have a machines IP address。

 we are not going to get this to work because that IP address is changed。So here is what we will do。

Here what helps This VM has own logical network interface physical the last time I told you that the VM actually sees a different ethernet card from the physical machine。

 it's a virtualized card。It has its own IPs。And that IP address can actually be different from the not can be taste different from the physical machines。

Okay for now let's assume it's a real IP address you said we can do that and do it 192 let's assume thats not the case。

 this is actually a real machine that has a real IP address which is going to be distinct from the IP address of this machine。

So you can move that Vm over。This machine has its own physical IP。

Mac address and a physical IP address that machine has one too。

 but that doesn't matter for the VM because what the VM cares about is its IP address。

 not the IP address of the physical machine its on new and its IP address can move with it that is not tied to this physical machine It's only tied to your logical Internet card which is moved with you。

The only thing we have to do is there are switches here that believe that。

This port is the one that has this IP address。 So what you're got to do is send what is called an arm message to your switch。

 it says that。Please rediscover this IP address。 It may have moved。

 This is no different from if you actually had a wired connection。let's say you had a wired ethernet。

 if you actually unplug the cable from one port and plug it into another port。

 you should know that your machine actually works just as fine。

And because all that has happened is the IP addresses appeared on a different port。

 The same thing actually happens here。So the IP address will actually move with you because the IP address is tied to your V is not tied to the physical machine there's another IP address tied to the physical machine that is irrelevant。

This is why the networking part is also seamless。None of your connections are actually going to break at all if this was a web server and a browser request come into it and you moved it there now the request just start arriving there was a switch just start sending all the packet because it just sees that the machine result nothing much has to change at all the OS moves。

 the application move， the network address moves， the connection just work as is So everything is actually exactly how you would expect it to be。

This is why it's actually a very nice mechanism because you can't do this with normal without virtualization。

 you cannot actually move a process from one machine to the other it just doesn't work because that process。

 if it has open socket connection network connection goes that tied to the to the ni on that machine and the other machine has a different IP so this is why fundamentally things great when you try to do process。

When you do VM migration， you basically have your own N and your own IP address， which can move with。

This is what actually happensing。Thank you。So let's precopy migration and talk about a difference。

 So you see that the last step here is you got to send an art message to the switch saying hey。

 the IP address that goes on this board is not different， please read this score and。はそうい近かり提験ある論んで。

Here's a different approach that does exactly the same thing it is called post copy migration。

In pre copy migration， we had an iterative copy where we tried to copy the Ram of E1 onto another physical machine。

 I took us several rounds to do this。Even on a very fast land， that says a 10 gigabit land。

 this can take tens of seconds， it can take you up to half a minute to move a V from one machine to the other。

That the application is not downtime， but it just still takes some time for you to。

What if you wanted to do this faster where this technique allows to do that。

For post copy post copy migration， what you are going to do is what is essentially called lazy copy。

So you will suspend the VM， you will copy a tiny bit of memory over just maybe a few pages over。

So now the second VM basically essentially has lots of blank memory and a few pages that you fit and you start executing that VM。

So let's say it executes an instruction， what is likely to happen。

Is going to page for because it looks like that when page is not in。

Except that now this is a network page for it， because all that memory is now sitting on a different physical machine。

 not sitting on your disk。It's not a virtual memory which is on this。

 So it looks like virtual memory is sitting in a different V so start paging it。

And youll launch a background process which is just going to keep copying lazily and as there a page forms you start bringing eventually you'll bring a working set and you start executing without paid pointing and theres a different process that' is going to run in the background that will keep bringing it over and after some time all the memory is going to be。

The good thing is。The first VM has already been suspended， so its memory is not changing anymore。

 so you don't have a problem yet had in the first case where processes are executing and changing the content。

 you already passed it and started executing it here in using。So here the transfer time is very low。

 but in the first several seconds there are going to be a lot of pagefall as you try to page in your working set。

So that's that double set。The other case， it takes a while to transfer with then in both cases。

 there are no。Visible。Signs are the transfer from an application standpoint。

 other than you see some painting activity in the second。So there's no real downtime of Amazon。

 but it may actually see your performance。So this is referred as post copy， so most of the。

Things you actually see， which is KVM and others。 You actually all support live VM migration。

 You can start a KVM VM and you can say move it on us we got two pieces。

 you can actually move it live and you see that it just moves。保持。

And post copy the model for research。对本案中。It was implemented。

 but most commercial systems don't yet use it because they think the overhead of this page files is going to be high enough that the application might perceive a slowdown。

 so it's better not to store anything to the application that season。Those are two。

here is essentially the analysis of how much time it takes to move， you see in this case。

This is precopy， you're essentially sending things in routes and then in the end you're going to basically move the VM here。

 smooth it immediately and there's a that post copy phase where there is more demand p as well as a background copy process。

In both cases， the total time might be similar because you're essentially copying large amounts of data。

 but in one case， the switch happens earlier， the other case。So I'm going to pause here。

I just want to take two minutes to talk about the exam。I will put up。Brief study guidance。

 no sample exam I have。To hand out。 But I'll put a study guide on the。For we pay。

 But here is the basic thing。My expectation is that you should focus mostly on the four slides。

Course notes， you don't have to go and read the book end to end or anything like them and not expect anything that I have not covered in class is not on the list。

You are only expected to know what I've actually covered in the lectures that's the only thing you should focus on so your best be is to actually start with the slides look at the material see what you understand don't understand and then go either go to the notes or if necessary go to the book or anywhere else the next documentation and read upon but if you understand whats on the slides very well you should be in good shape for the exam。

So that's my expectation， so don't go beyond what I have covered here and what's on this slide。

That should be the baseline case of how you prepare for that。

Then I put some more instructions on what concepts。From lecture on important。

But that should be so everything I have done till now is on the test。Lecture 1 to， lecture 3。

Including that when you solve its closed book， closed not， but maybe it shouldn't。Thank you。你主要系啲。同意。

是说是。What is a structure， So no multiple choice。SoSome short short。Answerered questions。

two to three sentences you should be able to answer。

And then so those are more concept testing saying what does this concept， answer it？

And there are some slightly longer ones where you are to say， given this concept， how does this work。

 should God to explain the work you。So that's the kind of question there are no math problems。

 there are no multiple choice problems。No programming。 You don't have to understand any code。

 memorize any code。' is going to say what did this file in Linux long。我过去过。Okay。

 just one that covered。They are set for the House， so next week we have the test and we have one more the children's week。

