# 【马萨诸塞大学】分布式系统-UMass-CS677-Distributed-Systems-(2025春季)-p09-P17---Lecture-09-----Process-and-VM-Migration--BV1jmNbzrE2F_p9-

![](img/8777185eaaeaf50a2c84cfdc62cb7b0c_0.png)

Okay， so let's get started。So today we are going to start a new topic which is going to be code process and VM migration Okay。

 so we did a the the。Two lectures on virtualization so far， one was on virtual machines。

 the other one was on OS virtualization and containers。

 we are going to continue from that point on we'll talk about process migration that we are discussed when we are discussing distributed scheduling we'll talk about that well talk about virtual machine migration and container migration okay so that's the agenda for today so this is a set of things we are going to talk about how does migration occur what happens to resources when there is migration and then how do you do this migration the process context virtual machine context and also for containers so before we do that I wanted to show you a quick demo of virtual machines and containers there is going to be a lablet another lablet coming out once the lab is done where you will actually play with virtual machines but since。

Spent almost two classes talking about virtual machines I thought I should show you and somehow we ran out of time last time for me to show you this so what I'm going to show you is essentially our type2 hypervisor running on my laptop here okay this one is called parallels desktop but there are many of them including multipass and Bmware fusion Vmware workstation many different products the by and large do the same thing Okay so what I'll show you here is。

Essentially so this is the dashboard of my type 2 hypervisor you will see that I have three virtual machines configured in my typey 2 hypervisor there are two Ubutu Vms there is a free BSD VM via BSD is another operating system I want to start one you can just see for those of you never actually used it you will see so this is now Linuxux Ubutu has started up so this is running inside a virtual machine right so this is your prompt so if you now actually look at this you will see that it's a Linux Ubu222 virtual machine that's running so there is a fullfledged VM so its in this case an arm based PC that's exposed to Linux Linuxux is running on that armbased PC which is a software emulation of a physical machine it's a virtual machine and you have a fullfledged OS running in there and you have my Mac OS。

That's running on my laptop so that's the post okay and then you have the type 2 hypervisor and this is Linuxux running on a type 2 hypervisor and you can have more than one Vm running I think I showed you this I'm going to start a second one just so that you can see that right so here's the second Vm that just started up so this one is running a completely different Os is running3bssD if you actually do you name you will see that is running 3 bsD 13。

1 right so that's a second Vm so now we have two virtual machines each of them is running a full fledged guest operating system both of those Vms are running on a type 2 hypervisor which is running on my native Mac。

So it's just an example to show you that you can essentially have these operating systems and processes running in them that run in an isolated environment on top of in this case on top of the desktop and you can shut it down just as you shut down a PC you'll see that it actually went back to sleep in this case I actually suspended it I didn't really shut it down so now they've all gone back to suspended it so that's one thing I wanted to show you the other thing I wanted to show you was and this probably you know now I'm just going to start up Docker。

Let's just start Docker from the。So， this is your。Doctor desktop。

 you probably seen this when you built your。Built your。

Class Docker container Im going to start container here so first of all I have multiple images thats the class Docker image I have an Uuntu image you can download these images or build them yourself and they show up here and then you can construct containers using this I started one which is the Uunto one you go here I can actually start up a shell and you will see that。

This is essentially in this case， it's also running Linux this is。

Essentially running on top a container that's running on top of Linux so Docker is running Linux And last time you remember I told you that although my native OS in this case is a Mac this Docker is a Linux containerization technology is runs on Linux not running directly on Mac so what you will not see here is there's actually a background Linux Vm running and this docker is running inside that VM that VM is not made visible by the Docker desktop but that's only way you will run Docker on Windows or in Mac because you are not able to run Docker directly on Mac because it's a Linux containerization technology but be that as it may this is now still a container that's running on my machine you can start multiple containers youve done this already for your course so now this is much more lightweight because there is as far as the container is concerned there is no OS inside the container the container is running on top of the。

In this case， it's top of Linux， which is running in the back。

This is something you want to keep in mind you can also shut down and pause Vms and containers using both command line as well as。

Using these types of interfaces and there' will be several more you will play with as part of your。

As part of your lablet， Okay， but this was just a very quick glimpse to show you how virtual machines work。

 how containers work Okay before I move to the。Topic for today。

 are there any quick questions about any of this？so in any case you will do what I showed you on your as part of your lablet on your machine but let's move on and talk about code process and VM migration first part is going to be code and process migration so I'm going to quickly tell you what this is about so essentially this is the ability to run application on a different machine from the one that they they started on that essentially you could either migrate the code for the application and then start that application on another machine so this is called code migration and you move the code which is either the source code or the binary and then you run that on another machine that's one way you can migrate the other is you actually start the application on machine one so now it's a running process and you actually move that process and this is called process migration so your code migration and process migration or also referred was code migration also referred as weak mobility strong migration is called strong。

Here we will use just code and process migration to keep things simple There are many examples a few classes ago when we are talking about distributed scheduling in particular I introduce this notion of a process migration I said process is running on some machine with I resources when the machine is back and use you are to move that process back to some other machine and you said the way you do this is process migration youll say a little bit of details of how an OS actually implement code migration is much simpler right because if you just have a Python program you are just going to copy that program over it's a binary you'll copy the binary over and you start that application on some other other machine that is much simpler to achieve but process migration is more complicated because you are moving a running process。

Now there are many reasons you want to actually have code or process migration in particular this is showing an example of code migration that allows you to download code on demand and run it drivers are now actually distributed in this manner where your machine operating system does not come pre-installed with lots of different drivers if there is a new printer or a new piece of hardware you connect to it。

 your OS has the ability to connect to some other repository dynamically fetch the driver for that piece of hardware install it and run it that's an example of code migration where the code is brought on demand for more flexibility。

嗯。There are many other use cases as well that we'll talk about but let's just get into a little bit of details of how migration is going to work so in this case we are talking about process migration okay so what is a process look like if you process essentially has some memory allocated to it that memory is called the address space or that process typically that memory partition into what are called segments okay to take an undergrad OS or undergrad architecture class youll know what segments are okay segments are regions of memory that are allocated to a process different type there are different types of segment within a process there is the code segment that is where the code of that process list there is the resource segment so this is essentially where you have resources allocated to there' is also the data and segments which are deep and the stack and so on so different segments that you have and so thats the address space of the process。

So to move that process or migrate that process， you have to essentially take all of the memory state of that process。

 move to another machine， you have to take the register state of the process。

 move that to another machine then you are to instantiate a new process on that machine and load that state into that process and start executing it that is by and large how process migration is going to work we'll get into some of these details in a bit but let's try to think about some issues related to how the process migration so process migration can be sender initiated or receiver initiated sometime go and we're talking about distributed scheduling I also talked about sender initiated and distributed receiver initiated there the receiver or the sender are initiateditiating distributed scheduling is the same kind of issue here who is actually triggering the migration is it the machine that where the process is running then it sender initiated or is it the machine that is going to receive the process。

Another way to think about it is there are like examples of how sender initiated and receiver initiated works so here's an example of sending a query to a database server or sending a query to a search engine this is not process migration but you can actually think of it as code migration because your query is a small program it might be sent off keyword you type in a search engine but still a query so you're telling the search engine find all pages that are relevant to the keyword as a tiny program that you sent off to the server where code has actually migrated to the server the server executed it and sent back the response that is sender initiated receiver initiated could be essentially things like jascript applications like you think of a jascript application you started in the browser some ja is actually sent from the server into your browser and it executes in the browser because it as a ja engine so if youre node J。

😊，Things of this sort， you can think of those applications that run in browsers as being receiver initiated your code is migrating from the server to the client in the other case it was going from the client to the server。

😊，Now once you have migrated the code， then there's a question of how that code is actually going to be executed on the machine that it has moved to okay there are two examples not two examples two cases one is the code starts a new process and execute that that's the standard approach where I said you have a Python program you want to migrate this code using code mobility and then it starts a new Python process okay so that's a separate process but you can also have the code that is moving to that machine execute in the process that initiated the migration the browserbased example is exactly that where I said the browser connects to the server you get some JavaScript code okay that code is executing inside the browser process is not starting a new process so that's an example where the code migration causes the process to actually execute in a target process。

That's for code migration those are the to its scenarios in process migration you have something called remote cloning in remote cloning you are not actually moving the。

The process you're cloning the process and then a clone of which starts so there is still the parent process still runs on the running machine but you clone it and a second copy starts somewhere so that's called remote cloning or remote four the other cases where you physically move the data of that process the memory state register state and start the process because so these are the two scenarios。

That you have or who is going to execute that migrated entity it is a very high level over we are going to get into OS level details quickly but just to give you this scenarios you will see that there are many combinations of how you can implement process or code migration you are in the mobility mechanism at the top you have code migration path here is this process migration in either case the code or the process can be send initiated or receiver initiated and then whether it's send initiated or receiver initiated you can start a new process or you can run it in the process that initiated it and in this case you can clone the process or you can migrate the process so many different combinations of how you can implement a system with process or code migration。

So these are this is a very high level overview， but now we will talk about some of the details of how you make all of this happen。

😊，Any questions here？Okay。So let's talk about one of the more important details that you are to deal with when you are going to have either process or code migration。

 let's just take process migration for just a sake it easy to say let's move the。

The memory state of the process， the register state。

 that's just data that you' are going to copy and then you start a new process there。

The complication arises when this process that you are trying to migrate was accessing resources say it was it had a file open and it was reading and writing to that file now you move that process to another machine it's going to continue to do IO but the file is still on the previous machine so how is that going to work because then it is going to get an error somehow that I is not either redirected to the file or somehow the file itself moved because you moved the process so dealing with resources is actually the hard part that youre to deal with then you have process migration resources could mean things like files it could mean hardware resources saying maybe there's a printer attached to machine one you could have a process print to that printer you move that process to another machine its trying to print to the old printer is no longer on that other machine how is that going to work it will fail to print unless you have allowed it to print to a remote machine or you might have。

like like network sockets right you already know how to do RPCs and socket communication。

 you have a process that is actively communicating with a client you move that process to another machine。

😊，Now if you remember how sockets work the sockets essentially have the IP address and the port number as the end point that you communicate you move this process to another machine the IP address of the new machine will be different the client will still send all of its messages to the previous the machine's IP address and then your socket connections will break。

😊，So all of these complicate the task of process migration okay so you might have resources that you ought to deal with so how are we going to deal with resources when a process is moving so I'll give you a highle framework to think about how to move resources and the answer is going to depend on what type of a resource it is so we have different strategies of how to deal with resource access when a process is moving so there are two types of dimensions well talk about first dimension is how is what is called the resource to process binding how tight is this binding so you can have three types of bindings by id by value by type identifyentifier means that that process needs to access that specific resource that it has named the identifier you cannot actually replace it with some other resource its only specifically talking to that resource example of identifiers could be its a website。

So you you have a URL okay the process is communicating with the server and that URL you have to continue to allow that you cannot change that so it's a hard binding by value means that you essentially have a resource where you specify a type of resource but you can substitute it example is Java libraries so if Java process running is running on JVM is accessing Java libraries if you move that process to another machine so long as that library is present on the other machine you can use the copy or the library so you can substitute that library with an identical copy on another machine that's acceptable。

When you have identifier based bindings you cant say I am going to substitute this URL with some other URL so you can access some other website。

 that's not a thing because you are actually accessing a specific website you can substitute it but when you have binding by value is so long as youre the same type of resource you can substitute and the least type binding is by type like things like printers。

 so so also you can have a printer， lets say H printer of a certain model that is a color printer right。

😊，Now when you move to another machine， maybe you have a canon printer is still a printer so you can substitute it with a resource at the same time。

 but it doesn't have exactly the same thing so in the Java case you can't say I have a C library I'm going to substitute a C a jar that's not something you can do your code will not run So so here again you are allowed to substitute but the binding is weaker so by identify or the strongest binding by value you have somewhere somewhat weaker binding by type it's the weakest binding so so depending on what type of binding you have to the underlying resource that the process is accessing we will perform different actions after the process is migrate it so that it can continue to access the resources it needs。

😊，And we'll see what those actions are I'm just defining what the bindings are your actions we'll see in the next slide the other dimension to think about is the type of attachment or what is the cost of moving a resource so so again that also depends on the type of resources if you might have let's say unattached resources like files which can move they might not be expensive to move so that is an easy thing to move to another machine if you have to and there are fastened resources fastened resources or resources that can move but at a high cost think of this as either a large file or a database。

😊，You can certainly move a large file is a 10 let's say iss a 10 gigabyte file process moves you can move a 10 gigabyte file but it is going to take some time you want to incur them over it we will call these resources as fastened resources that you can move them but at a high cost the third type of resources are fixed resources these are resources that you cannot move。

So examples are socket endpoint you cannot actually move that socket endpoint because it's tight to the IP address of the machine or if it's a hardware resource a printer is plugged in you can just move it well you can physically move it but that's not what you will do right when you move a process you can say the hardware resources attached to the machine stay behind so you are not going to be able to move so again。

 what action we take when a process migrates and is accessing resources also depends on whether it's even feasible to move that resource what is the cost of moving that so you have these two dimension how tight is the binding and how cheap expense or feasible is it to move。

So that' is going to give us this table which gives us all kinds of combinations so here on the columns or each row is essentially the binding so you say by identify this tight binding can't replace it by value you can replace it if you have something and by type means it's weak binding you can replace it easily and then on the columns are essentially the cost unatta means you can easily move it par means you can move it at a high cost fixed means you cant move it is tied to the original machine so you cannot really move so depending on these combinations of how expensive or cheap is it to move and what type of binding it is you will see that there are nine different types of actions you can take for each combination。

Okay， so what are the actions that are available to us， lets talk about。😊。

So you will see that there are essentially four types of actions we will think about for any combination we have to pick between one of those four。

😊，When a process moves， the first one is called。Essentially establish a global reference this is just a fancy way of saying allow remote access resource is not moving just allow the process that just move to a new machine to access that machine the resource remotely access it over a network well call that global reference so which just means remote access move means move the resource when the process move move the resource with this like a small file that it was reading or writing move that file with the process so it can continue to access let's move copy means copy the resource you have original copy you make a copy and you move it as the third action fourth action means rebind rebind means substitute with the local copy。

Okay， so you are basically going to say I have a similar resource here。

 just access that one instead of the original。So four things you can do when a process is going to move and accessing resource。

 allow remote access， move the resource in the process， copy the resource， it follows the process。

 substitute the resource with a acceptable another copy of the resource。哎。

Now for each of those we have to pick one of these four choices you will see that often there are multiple possibilities in each one so we are not going to go into all of those details。

 but by and large。😊，So if you see what happens is the resource is unattached it is easy to move。

 you'll say let's move it you can also copy it if it's if you want to you don't have to move it。

 you can make a copy only when it's by type you say it' by type it's a very loose binding I don't even need to move it you can replace it with an equivalent copy but you can still do a copy if you want so you'll say when it's cheap to move。

 you prefer to move but if if don't have to move and you can substitute it that's even cheaper I don't have to perform any copy over it so I can re so that's unattached fixed essentially remember what fixed means that you can't actually move the resource like a communication endpoint or it's a printer that you cannot move so by and large here if you want to continue to allow access you have to say remote access thing then move So if you want to continue to access that resource allow remote access which is why it says GR but essentially when youre lose binding。

Then you can say even if it' is fixed if its subs subsary theres a printer okay you have a printer on another machine that you move it okay you can res substitutestitute it you don't allow remote printing that are still fine but if you can print to another local printer that' is acceptable so when it's fixed allow remote access is always a good choice when its unmattached cheap to move essentially moving or copying is a good job and when it is fast and that means it' is expensive to move okay you can move it but it is expensive you will。

Most likely allow remote access， but in some cases you can say I can move it and so and then for type you always say I can substitute it always re。

So this is how you will design your process migration framework you have to see what within that process migration framework。

 what are the resources that processes can access for each type of resource after the process has moved how can it continue to use that resource sometimes a resource will move with the process sometimes you will have remote access in other cases you will substitute it but you have to think about the cost the type of binding to decide what is the right action for each scenariory。

I is clear， any questions here？Okay， so。That's all I will say about resources。

 I do want to say one thing before we move on to virtual machine migration。

 which is what if your process is migrating in a system that is heterogeneous？

So we implicitly although we didn't say this implicitly we assume that when a process is moving from machine A to machine B okay the OS hardware is all identical which is why you can copy the state and then you can resume the create a new process and resume that execution on another machine can so what if the machines are heterogeneous what if the target machine is running Windows the source machine is running  Linux what can you do。

Yeah。Short answer is just too complicated， you don't support process migration is one answer right because you can't really move a Linux process to a Windows process because the binary formats are different so you can't really do that code mobility is fine because you actually let's say Python code doesn't matter so long as it's a Python interpreter on the target machine you can move the code and run it but process migration is much harder because the binary formats are different you can't just copy binary of a Linux binary and run it on a Windows machine because you will not do not work so in this case people did try to make this work and what they did is essentially say if you had access to the source code of the machine of the process I can recompile it and create a new code segment I can move the data segment the data I can move the code I recompile so it's now working on a new machine and then I recreate the process on that machine and then it works。

Sometimes not all the times it depends on the assumptions you make so migration and heterogeneous system typically you avoid but there are some people who try to do it it is a lot more complicated because you have to recreate the binary at the minimum。

😊，Other than they put the data in the binary and you move it okay that is one way to do it another way to do it is you have an abstraction layer so that the underlying hardware details and the OS details are hidden from the process okay an example is a Java process。

A Java process you can actually move because it runs on a JVM okay the JVM abstraction is not going to change requirement whether you are running on Mac Windows or Linuxux is still a JVM so your code is going to run the same because running on a JVM and the JDK is actually running on the original machine so you can run it on an abstraction there so that all that differences are hidden because it will look the same so if you had things like Java processes now those are somewhat easier to deal with when you have heterogeneous systems。

哎。That by and La， this is not something you will see supported when you are talking about process migration is much easier to use code migration in this context。

😊，Is that clear？Okay。就。We will switch gears and now talk about a different way of migrating processes and we will see how you can implement process migration by migrating an entire virtual machine or a container and everything in it migrates including processes。

😊，So process migration whatever I told you so far these are all concepts that are well known but you will not see any operating systems that support process migration out of the box you run Windows you run Macs or Linux you probably never seen a system or a command and Linux saying move this process to another mission okay that's because typically OS is still don't support it it is too complicated because you have to deal with resources and so on okay。

So the way now you migrate processes in today's world is you run them inside containers or you run them inside virtual machines and move that virtual environment to another machine that will move all everything thats inside the virtual machine to another target machine and then the process continues to run so this is implemented on every virtual machine platform so you can easily move processes without any problem if you run them inside virtual machine so we will now look at essentially this is process migration in today's world because this is how it's done you don't actually do whatever I told you for in the last 20 minutes or so I mean you don't as in you can do it but operating systems or today don't support it。

😊，But this is supported by every OS and every VM platform so now our goal is to see how to take a virtual machine that' is executing so this is a virtual machine that is executing on machine a so it has an OS running inside it it has a bunch of processes running inside it I just showed you right and you want to move that VM to another machine。

😊，NowMoreover， we will make it more challenging by saying that this migration has to be live Live means you cannot pass the virtual machine or shut it down。

 move it and restart it， you will move it while processes are executing on machine a so processes will continue to execute they will see no downtime you will move the Vm and magically the process will not switch over to another machine and will continue to run so as far as the process on users are concerned they will not see any impact of this migration from the sense of whether the process takes a downtime there will be no downtime at all you will essentially do this process migration VM migration live that makes it more challenging because one way you could have migrated it was you say let's shut down the Vm or pause it I'm going to move it state over than I resume it somewhere that would have been easier to but we are not going to let pause it because we don't want downtime can we do it live。

I'll show you two techniques， how you can make live migration work and then we'll talk about what happened to all the resources and so on。

The first one is called pre copy meA migration and the next。

Technical talk about is called post copy migration okay so the difference between the two is when the memory state is moved over the first case is moving before the migration step is actually taking place in the other case you will move the VM then migrate some of the state but let's talk about precopy here's a picture that you are going to keep in mind this is machine A theres machine B theres a virtual machine thats shown there thats a blue rectangle okay that's the memory state or the virtual machine okay so inside there is an operating system theres going to be some processes running and we are going to move this Vm from machine A to machine B while those processes are executing will not stop and we'll move it like。

So how do we go about doing this？So here here' is what we will do right so we will take let's say this memory is the set of pages right so all ram is set of pages so this Vm's memory is going to have a set of pages we need to copy them over well so okay let us do it one at a time you will take page one you copy it over take page two you will copy it over youll do all end pages okay sequentially。

😊，So you just basically write the loops and go do page1 page2 i i plus1 and so on okay so once you are done with this you are transferred n pages over。

Okay。That clear what I just said okay so now what is happening while these pages are actually moving over。

On the original V。systemystem is live processes are executing processes then stop because we are just copying the memory contents over if processes did not stop what does that mean for the memory on machine a。

It will change because you you are not put any restriction I could start new processes in there。

 I could terminate processes processes could do malloc they could change their memory in any way they form they could write update variables so that memory is going to change right so we copied n pages over。

But now that whatever you copy it is no longer up to date because original contents have changed。

So we can't just take that memory that you copied over and use it because that's not going to reflect the state of the virtual mission which changed。

So what do we do now？Only one thing can you copy it again。喂。Right， so well。

 we are not going to take a look。That will not let them be live so so so we will say okay some memory has changed but an interesting thing to keep in mind is not all memory would have changed only only the memory that the process touched while this copying was taking place only that has changed hopefully thats not all of the memory on the machine but maybe some subset of the memory。

😊，So we are going to track this this is what the first step is we'll call enable what is called dirty page tracking dirty pages simply means track all the pages that have been written to when a page is written it's called the dirty page in an OS terminology so we enable dirty page tracking so as we are copying this first end pages we track which which pages have changed those are actually the red pages so in this case only two pages change but in typically a lot more pages would have changed so in round two well only take the memory contents that have changed and well copy hopefully those memory contents are much less than the original end pages we send those are all the entire memory now we send some subset of it so we send them over。

Okay， but then this processes are still executing。On machine aid。

 so yet more pages will change while you copy it。So what do we do？

Yeah we trade right because the only thing you can do is keep sending so now we will send them yet again but the thing you will keep in mind here is in the second round we send much fewer pages than the first round first round is sent all end pages second round we send some subset let's say 10% of the pages okay so 10% of the pages should take me approximately 10% of the time it took me to send the original 10 pages the network bandwidth is identical。

so it took me much less time so if you assume that some average rate at which pages are changing there will be some rate at which pages are changing based on process behavior each time I decide to send this there should be fewer and fewer pages that have changed since the previous round because around duration keep shrinking。

😊，So let's say you're changing 10 pages a second That's much average rate at which memory is being changed in that So if it took me 10 seconds for send the original page I have 100 pages that are changed then to send those00 pages maybe I take one second and only 10 pages have change thatll take me 110 second and so on so so I'm iterly copying the pages that are changed over and over again but the round duration keep shrinking and the number of pages that I send hopefully shrinking doesn't have to bes no guarantee you might I kill 00 processes on this machine user can do whatever they want right and say let me kill 0 processes a lot of pages might change and so it's never a guarantee but on average the round duration will shrink。

So， after some number of round， we will reach a point where the actual memory that change is small。

Anyway its down to two pages like is shown here？So。

 in this case because there are now very small amount of pages that are to be sent。

 you will actually pass the VM until now Vm was running so now you will pass the Vm which the stop execute is frozen in memory。

Where frozen memory will not change anymore because you actually paused it for a short duration。

Then you copy the remaining pages away。Because you pause the Vm。

 now its contents are no longer changing now this is our last round。You send those pages over。Now。

 the memory contents are identical on machine A and B。

Because nothing is changing anymore the memory contents are identical that means the state of the VM on both machines is exactly the same。

all the data looks the same。So now what you can do is you can terminate the Vm here。

And you can resume execution or that Vm there okay it will resume exactly at the point where you stop here because you will actually start executing the next instruction as if nothing is that because it is identical。

And then the process starts executing so there is a very short downtime I said it is live but the downtime is very small its milliseconds are smaller to send the last few pages over because you are on a fast network so the downtime that the application is almost imperceptible they don't actually see it because like one millisecond passed and the process didn't execute for a millisecond you don't actually see such a small gap so it looks live it looks like nothing stopped when you executed this processes they were executing here certainly the VMmo machine B and now it' is executing。

😊，Exactly。Okay so essentially that those are all these steps okay but after you resume the VM at that destination you have to do one more step for the networking to work which is you send what is called R packet to the switch okay so theres an ethernet switch where all the traffic is coming you send R packet that just causes the switch to send all the traffic for the VM to the new machine otherwise it must still send them to the old machine and then the VM might miss it and so you need to tell the switch saying send all the packets here and then all the switch sends all the data there in all this good。

So this is called pre copy migration。That clear。Okay，All right。

So this is basically now you mood so this process migration which is all the processes not just one processes but all processes migrated the entire OS migrated everything mode and nothing seems to have actually gone down in that process well let's go back to a discussion and say what happens to resources。

What happened to the disk of the machine， what happened to file Io， what happened to network sockets。

 how is all that going to work， but I said nothing has changed everything moved over。

So let's start with files lets say this VM was accessing some file on the disk you moved the VM I only talked about memory state I didn't say anything about disk。

😊，That's what happens to all the fileile？So the assumption that we made， which I didnt mention。

 is that all the file Io is happening to files that are stored on a network file system stored on a file server。

which is not shown here so we will assume that if this VM is performing any IO it should not be to the local disk of this machine。

 it has to be some files that are stored on the file server so the files are stored on a server somewhere this VM that moved over to machine B can still access those files so if you make that assumption you don't need to move any files。

Okay。If you do not make that assumption， then in addition to moving the memory contents。

 you also have to move all the files from machine A to machine B that are being accessed by that。愿。

And you will allowed to use the same iterative mechanism。😊。

Because you will be moving this live if you copy the file it you may do IO to the original file some blocks and the file may change so you will send block by block all the files same thing you can do on the disk level that you did on the memory level so you can do one of these two things either you assume all file iO is on the network files or so I don't move any files easier and only move memory I don't need to worry about files all is good right so I don't have to worry or if you say it's local files you got to move them with the memory you do the same iterative process so you will move them iteratively eventually you will take a pause move the final memory pages move the final blocks and then you resume。

そ予見どう です。Well that's one what happens to the network sockets？

so let's say there are processes in them they are lets say doing socket communication。

 GRPC communication， they all have active socket connections you now move this VM to another machine。

How do we deal with that， how do we make it work？Anyone have any thoughts on this？Okay。

 the first thing you have to think about is what。Are the connections you have established with that virtual machine。

 Okay， So the process is running inside the virtual machine。Yeah。

 not running physically on the machine， what is the IP address bound to？

The IP address is given to the physical mission。That IP address is not going to move that is going to be attached to this machine its not that youre going to move the IP address okay but if you remember what I had said last time this virtual machine has an emulated ethernet card because it is a full flight virtual machine it has its own resources that are emulated using physical resources so its a physical ethernet card here on this machine but is an emulated one that is attached to the virtual machine because it emulated ethernet card the virtual machine has its own IP address。

That is different from the physical address of the address of the physical interfacefa here so when you have an virtual machine there are actually two IP addresses is IP address or the physical machine is IP address or the virtual machine there are two different IP addresses although the physical machines IP address cannot move it is bound to the ethernet card on the machine the IP address or virtual machine has no such restriction is is bound to the logical ethernet card on that machine since the entire Vm has moved you can move the IP address with the machine has no problem。

Right so the IP address will move with the VM this is the IP address or the virtual machine not the IP address or the physical machine that will stay unchanged right because you moved the IP address over network connections will stay as this because the switch will start sending packets now to this machine the IP address will just show up here its almost like you physically unppllugged your ethernet cable from one port and you plugged it into another port and then the switch just start sending a packet it the same thing it just looks like this IP address has just moved a different port on the switch and the thing has changed this is why you need that R step there。

SoSo this is the interesting part here in physical when you move processes。

 you could not move the IP address because the IP address was bound to the physical mission because the process is now running inside a VM we decoupled them the VM has its own IP address that you are free to move with the VM。

The only restriction is there better not be another virtual machine here to which are given the same IP address。

That will not work and these are private addresses so they can be reused they are physical real addresses that you cannot reuse them but if you have a private address you can reuse them so long as you don't make some conflicts you can move the IP address and then all is good in this case。

Yeah。So so your TCP connections will stay as is your client server communication will stay as everything just moves over clients don't see clients outside that are connecting to services in there。

 don't see a problem， processes don't see a problem so there's a much easier way of implementing VM migration sorry process migration using VM migration。

Is this clear okay so these are all steps that the hypervisor will implement to to EMM migration so if you got to tell the hypervisor move this Vm or migrate this from machine A to machine B it will run this algorithm and after some time the machine would have moved over。

Okay，All right。So are there questions before I move？

I will show you a different approach of implementing VM migration is also live but it is a different algorithm implement live migration。

 this is called post copy migration。So in post copy migration the different approach of implementing live migration so your first step okay in post copy migration it says stop but you are really pausing the VM so the first step is pause the VM and then you say move the register states over are not moving any memory just moving registers and there are some small number of registers on any processor so you move a small amount of data and then you say I resume the VM on the rest。

So， all I did in this case I paused the VM， I moved the registers which is a tiny amount of state and I started the VM on another machine that VM is starting with blank memory only has registers。

It doesnt have any data at all okay I started you start executing it there and now that VM is going to start fetching data on demand from the paused Vm on the original so let's say you execute an instruction okay instruction touches some memory content okay because the memory is now no longer there is going to cause a page fault。

so this is now a network level page for because you will say this instruction that you transferred the register touched page number five in RA okay that page is still on the previous machine because you didn't copy anything so it'll immediately our page fault will pause execution willll go to this other machine will fetch the network page over that page will appear here you resume execution and maybe you will run some more instructions and it'll touch another page it still not in memory was another page for so you'll fetch that page。

And so on and so forth， so you will start fetching contents on demand as the processes that are executing there start faulting。

😊，So every time you have a page for you will see that you have to actually pause to handle the page for so this will slow down the execution of the process because it is faulting a lot if youve done undergrad OS you know that page fault takes time to service youre bringing pages in that case you are bringing them from disk to Ram here you are bringing them from Ram of machine a into Ram of machine B same concept but you are going to spend some time copying the data so you are copying the data while the process executing so it will see some page faults and some performance hits but you are fetching them on demand now。

After you fetch some number of pages once you have the working set of the process it will start executing without page fault but theres still the rest of RA to fetch you don't wait for page false worker you also start a background process to say okay what are pages that you have not fetch so far as a result of page falses bring them slowly in the background don't wait for page for let's just start prefeting them and then you also have page faulting that is actually bringing pages on demand so if you combine the two after a while all the pages are not fetched into in this case。

and then you can then discard the VM that was running on machine a and then you are done the machine process is mode over。

So these are two different approaches。We can think about pros and cons of the two approaches。

 so let's think about what are some advantages and disadvantages think。

Having thought about these two techniques。See what might happen， yes you have something to say。都。嗯。

To begin。Yes。Yes so question is even in post copy will the machine VM in machine A and B have the same IP address IP address will move like previously in this case the IP address moves immediately right so you stop the VM you move the registers。

 you assume that the IP address is also moved so everything is now happening the VM is no longer executing on a you start executing on B even though very little data has actually moved over youre fetching all the data on demand or using some background process。

Okay。All right， rows and cons。Yes。s poppy， there is less chance。

 you have to transfer a lot of memory。 You're only transferring。Yes。

Yeah so the memory overhead of post copy is going to be much lower than precopy because each page is transferred exactly once okay because you paused immediately paused execution on a and you started executing on B so as memory content not not changing anymore right so each page is going to move from a to be exactly once either it's to a page fault it moved there and then it changes on B or you fetch it in the background while it does not change and you moved it so so you will the number of pages the total memory overhead transfer is exactly n if there are end pages you will never transfer any page more than once in precopy you can transfer many pages many times depending on how frequently they are changing and so so memory over copy overhead is higher in。

Pre copy， then in post copy。Yeah， yes。Yeah。Take it。

Okay question yeah so the point is in preco of a small downtime in post copy is somewhat of a slowdown that's right but I' amend that with one thing in both of these approaches theres a tiny downtime first thing okay in precopy it was at the end of the last round there was a downtime okay。

In precopy in post copy the downtime occurred when you pause the VM and you copied the register and you resume right so there was a very tiny downtime that downtime was the time to copy some registers but there is a downtime in either one but the other point was there's a slowdown so you will see that in postcopy applications will start seeing a performance hit right after the migration because theyll see a lot of page force until enough pages have been feed over where they can execute at full speed there will be a slowdown in precopy there was no slowdown because processes were still executing as if there is still nothing has happened that there is no migration going。

So there is a performance hit that application will see for a short period of time after the migration has occurred in precopy that was not in the case okay so one has lower migration overhead memory copy over it in the other case there is a performance overhead those are some pros and cons to keep in mind as question you。

😊，对要。Okay as the question is if there is going to be a performance hit or memory copy over at why don't we pause the VM and just copy it right so first thing is I don't want to say that you cannot migrate a VM without pausing it that would have been the simplest case right dont want to migrate a VM you stop it。

You copy all of its contents only once。And then you resume。

There is this that step zero or sort of algorithm zero okay we tried something more complicated than that but in algorithm zero no processes are executing while this par you are paused and youre copy and remember that the VM state it could be you might have 8 gigabytes of RA or 64 gigabytes of RA so you are copying several gigabytes of memory is going to take you several seconds tens of seconds to copy that data so until then applications are paused。

Right now， if that is acceptable to users， that' is the easiest you don't have to do any of this。

 but lets say there was a web web server running。😊。

So users from all over are accessing that Web server certainly it stops responding 30 seconds just stop responding after 30 seconds it comes back that's not a good experience for your end user especially let's say if it's online store you are about to buy some product right and then the server just freezes so these are not types of scenarios where you actually want to take it downturn but if you' are running some other noncritical application maybe it's okay you can pause and move and then it's much simpler so live migration is design for server environments where you're running active services and the services are serving end users and you don't want to see that downturn that's why it's more complicated but otherwise you can do all of this in a much simpler manner which is what I'll show you for containers because containers actually don't support live migration you only support what you call suspend resume you suspend move resume。

So that's much simpler。Okay so here's a picture to show you time diagram of what's actually happening in precopy and post copy okay so x axis is is time okay so you start the copy process your multiple rounds okay each round is as you can see shrinking shrinking that's the last round you pause at this stop which is called stop but it iss really pause you copy the remaining pages okay the copy of the registers restart okay but this is your downtime。

It's small but it's nevertheless there and here is your post copy as soon as you start the thing you will take a downtime because you'll pause immediately move only the VM state which is registers it should say register state not VM state and then you restart and then there's a long process where you are either doing demand paging which means that I take a page for and then I bring it or I do what's called prepaging prepaging means I have background process and just fetching the other pages in the background to avoid more performance it than you to take so this is where your performance degradation。

But each page is being transferred only ones。Okay so that's basically showing you pictorially what is actually happening in both of these cases。

So the last thing we will talk about is containers and how are you going to migrate containers？

So you could implement live migration for containers。But container technology is not。

You all to a point where it supports live migration primarily because。

Containers by default by default， containers don't have their own IP address because they are simply encapsulating a set of processes those processes used underlying OSs and OS has。

Dealing with the physical interface card but since youre played with Docker and you've probably done lab when you know that you can actually give IP address to containers and then containers can talk to one another technically what's happening there is the container still does not have an ethernet card what you have actually done when you say you assign an IP address to container you actually created a logical interface on the machine itself not for the container created one on the machine and you just said this IP address is dedicated to this container and these other IP address is dedicated to this container so you will see that this IP addresses are actually created on the underlying machine and simply allocated to specific containers so it looks like the container has its own IP address so logically that's still the case but in a VM the VM actually has a physical interface that is executing it has its own ethernet card so you are actually assigning the IP address to that interface。

It is on the machine so its somewhat different but by default unless you do this extra work that Docker does if you just take basic Linux containerization there are no IP addresses to containers we just move a process if it was communicating with some other processes all the connections are going to break Docker has simplified some of this by using Vm like technology for containers but thats not true for basic containers so it's a little bit harder so they essentially do pause copy and resume techniques。

😊，For there are three techniques that you will see for container migration。

 all of them involve downtime。😊，well， unless you do it live all of the other ones involve down so cold migration essentially says that you shut down the container。

😊， so it is not nothing is running， not even pause you completely shut it down。

 you just transfer the image over。😊，And then you resume the image by creating a new content。

So that's called cold migration okay so process state is naturally not preserved right so essentially it's like if you have your 677 docker image if you know where on disk it is you can physically copy that entire file to another machine and started that that's essentially what cold migration means you took the image of the container which is the disk and you move it processes are not moving because you shut it down there are no processes and you start a new container that's cold where migration means you are migrating a container that' is running but you are not going to do it life。

😊，We will suspend the container。え。And then we will move the disk image and the suspended state over and then we will resume it then on another mission this is like saying I suspend it in Ram I copy the Ram contents okay I copy the disk contents then I start the container。

This is called war migration okay so you essentially you suspend okay in fact you do not actually have to suspend in memory you can do what' is called suspend or disk which is your first suspend the container you write out this memory content or file on disk so theres a this file that has the RA content there is an actual file that is the image you copy both of those files you resume so essentially so this is why you essentially I said suspend and resume so this is what war migration okay and then you of course you have something called hot migration which is also called live migration you can do whatever I said for Vs。

You can do it pre copy， you can do post copy some container technologies have tried it but doesn't work very well because it doesn' not deal with things like network sockets and so on。

Veryry well only Docker supports that basic Linux container don't even have concept of IP addresses So if you just do live copy connections are going to break because they're tied to the physical machines IP addresses but in the Docker world you could do it much better a Docker doesn't support this although you could use exactly what we said or via migration to also migrate containers so long as you can decouple things like virtual machines IP addresses sorry not virtual machine container IP addresses and you assume that all files live on a different network drive you make these assumptions you can implement。

but not yet done Vm migration very common almost every Vm product will do it out of the box Linuxux will support it out of the box but not for containers only for virtual machines。

😊，对。So I'll go tell you another concept which makes this suspend transfer process much easier okay and that is using a technology called snapshots so what is a snapshot okay the basic definition of a snapshot snapshot exist in many different context there are this snapshots VM snapshots and so on but by and large the definition you want to keep in mind is its called a point in time copy so it's a copy of the contents of that process VM container at a certain time it so the way you want to think about snapshots is。

Let's say you want to take a snapshot of a VM you will pause the VM temporarily you will assume that you can instantaneously write out all of the memory content and then you resume whatever you captured is a snapshot that is the contents of memory that existed at time T when you took the snapshot。

You can take this snapshots both Macs and Windows support that these snapshots are used for backups and so on so you can roll back saying something got I deleted a file back accident or a corrupt it something I can go back to a snapshot and get it back but in your case here we are only talking about virtual machine snapshots and container snapshot so snapshots are a way to preserve VMt you can take different snapshots of your Docker container for example you can try this if you want Docker will support a snapshot so you can take a snapshot of an image then you modified it later and if something get messed up you't have deleted you can just go back to the previous snapshot restore it and then your container will look like whatever it look like when you took the snapshot so you can go back to the time you take a snapshot and execute from there。

So lots of interesting use cases for a snapshot， but you can use it to take memory copy。

 snapshots or disk state snapshots and it works like a backup。

We can also use what is called a virtual snapshot okay this is an optimization okay of taking a snapshot so remember I said snapshot is a point in time copy So if I want to take a snapshot I have to pause。

The Vm I am copy it the reason I have to pause it is I can't do things like live because if I didn't pause it I start copying it it will change while I'm copying it so that's not a snapshot it has to be exactly what it was at time T so the only way to take a snapshot in this case is I have to pause it copy it and then I resume but the overhead of that copying is going to be high right because if it is 16 gb or memory I have to write out 16 gb somewhere to preserve it。

Same with this if I make a snapshot of a disk file or a database thats let's say 100 gigabytes I have to literally make 100 gigabyte file copy so snapshots can incur high overhead because they are making a copy of either some file or some disk memory contents and so on so to make it more efficient the OS researchers came with an idea called a virtual snapshot which means you make a virtual copy。

What's a virtual copy and how is it different from a physical copy。

 a virtual copy essentially says that it' is a copy but I don't really make a copy。

 I just essentially have a pointer to all the old data。

So think about I have 10 pages instead ofm making copy of 10 pages so I end up with 20 I just create an index that is just pointing to all the 10 pages so in the copy if I want to go to page five I look up the pointer I go to the original page and I fetch it。

😊，Now you can say if I just did not actually make a copy， I made a virtual copy。

 what happens if the original data changes？I may musical go and update page number  five okay my virtual copy is still pointing to that page5 I modify it and now my old copy is gone。

😊，Because a snapshot is supposed to preserve that data as it existed when I took that copy。

So this is where you are going to use a OS mechanism， which is called copy on right。

OkaySos also called cow， which is an acronym for copy on right Okay， so this is called。😊。

it is a technique that is essentially doing lazy copy a normal copy you can think of as an eager copy where I physically made for 10 pages Ive made copies or end up with another 10 pages this one is saying change on demand the original data has is not going to change why bother making a second copy keep that original data and just point it but then I don't really need to make a second copy I save a lot of overhead。

😊，But if you make some changes to the original data at that point before you write to that original data。

 make a real copy and then change the original and then have the virtual copy point to the copy you just made。

え。Is this clear what I said or no？So copy and write techniques allow you to reduce the overhead of making a snapshot by not really making a copy at all but rather just pointing to the original data the original data never changes this is very efficient because it doesn't take any time at all I just basically make a virtual copy and say the virtual copy same as original data and whenever I want to access the snapshot I'm actually going to the original data and accessing it and so long as data doesn't change it fine the book but both of those copies would have had the same content and I only make a copy when the original data changes for any reason by the user this is essentially lazy copy also called I copy it when you write it if you modify it only then I'll make a copy because I want to preserve the original is part of the snapshot。

so this is a technique that is widely used in operating systems。

 we will encounter copy and write in other contexts。

 the first time you have encountered it here here we are using it to make snapshots more efficient but we will use it for other purposes as well。

so this is why you can actually make copies of Docker images or virtual machine images that maybe tens of gigabytes in size you say take a snapshot in less than a second it says done it looks like you made a copy right but you are not really copying tens of gigabytes of data in less than a second you just used virtual copying or virtual snapshots to make that work and then slowly as you change it it will make sure the original is preserved。

哦。that's just snapshot mechanism。Any questions on this？All right。

 so the last thing I'll talk about or the last few things I'll talk about is checkpoint restore mechanisms okay so this is yes。

很包。Can tell me their data。对对。Okay， that's a good question， very good question。

 the question is what if I make a virtual copy rather than writing to it I delete it。

Then what happens， original data is gone， the snapshot was pointing to it。た。

so the way you deal with deletion is no different than right okay so you think of deletion as a modification okay you are modifying the data by erasing it so you treat it as a modification so you will do copy and write if you try to delete a data you will actually make a copy and in the snapshot you preserve it but in the original you delete it。

The question is， does that when you're doing a soft delete。

 it's not a soft delete in the sense of in soft delete you actually keep the data in the original here you will make a copy。

so youll actually have the two let's say two files right so you delete the file these content you can overwride but then you made another copy so there are two blocks that file one is the original one is the cop so you deal with deletes as if they right you think of a delete it like you erased it that's like a right operation you make a copy on demand so it's not a soft delete essentially means you don't delete it at all you just migrate as delete where data still resides on this it's not what we are doing here you are actually making a copy of it and then erasing the original。

Okay that's a good question so let's talk about checkpoint and restore so checkpoint essentially so this is the way Linux containers are going to do migration is called a checkpoint restore technique so checkpoint essentially says that take a snapshot write it to this restore says restore the snapshot and resume execution so so this is how warm container migration is going to work okay so you want to now migrate a container from machine A to machine B you will pause its execution。

then you will take a checkpoint the checkpoint really is a snapshot but in this case you don't have to make because the container has stopped you are simply going to write out the memory content to this you don't really need to make a copy in this case but you could have done a snapshot and copy it but here you are going to simply save the memory contents of the container to disk and you are going to copy that checkpoint which is the memory contents you wrote and the disk image of the container a new machine and then you start execution of the container there。

The memory contents get reloaded， all the processes that were running will actually appear back in memory ander restart so it just looks like there is a downtime。

😊，Between the pause and the resume。Okay。You are clear so this is called checkpoint and restore。

Now the virtual machine example I showed you at the beginning of class was essentially doing that I did not reboot the VM I'm going to show it to you just so that you can remember so here's that virtual machine I was showing you is actually suspended and checkpointed to disk right I could reboot it from scratch then it will just boot as if I booting a new machine but just for speed I just suspended it which I been I checkpointed it so I can resume it。

So it's going to restart and as soon as it loads it and you will see that all the processes have just reappeared right so the processes that were running previously they were all paused and saved on disk I just loaded it back and I resumed it so I could in this case have copied this contents onto another machine and I resumed it there it would resume exactly that as if I restarted it here so in this case I'm just using suspend resume on the same machine but if I include the copy step I copied that state so I can just suspend it back here so this is not taking moving all the memory contents got written back to disk I can take this Vm literally the V files move it to another machine and I started there all of those processes will reappear network connections in this case unless you deal with the migration will not but if you deal with that that even that's fine so that is how containers were Vms have supported it of course for a long time containers by and large only do this save copy。

You can just save and restart right that' is what your docker does by the way。

 then you pause a container and restart it right using Docker desktop it is essentially doing checkpoint and restore。

So that's essentially the Linux mechanism is called CRU just checkpoint and restore in user space It's an acronym is used for war migration。

 sometimes loose for live migration not often so these are all the over test steps you to perform you have to go into s pro get all the information about slash pro is the way you track all running processes in Linux so you will essentially say what are the running processes in the system you will get a list of processes so say let's suspend them all and they'll be paused they'll say okay take contents of process one write it to this take content or process two write all the memory content so you go and look at all the processes that you have systematically right all of their contents register stay to disk at that point you have essentially said all the processes state put it on this then you can take that。

啊。Checkpointer state and just copy it all over another machine and then you have the restore step which is going to repeat that whole process is going to essentially say Al can new process or blank process started take process one that are saved to this copy it into blank process one process one is restore take the second one do the same thing you do all of that and then you're restore you will see that you can also do what is called TCP repair if you actually move the network state it can restore the network socketets also by default they don't work they will break but if you have the TCP repair step you can actually deal with that as well。

Is this clear？对。All right so I will skip because we ran out of time this last slide on viruses and malware the only point I wanted to make here was viruses and malware are essentially a form of code migration right because they are just migrating malware which is bad code from one machine to another starting a process they attacking your machine moving that code to another machine and so on and so forth。

 so code migration has been around but in a more nefarious way as viruses and malware that keep propagating from mission that's all I wanted to say here but we will come back to this next time。



![](img/8777185eaaeaf50a2c84cfdc62cb7b0c_2.png)