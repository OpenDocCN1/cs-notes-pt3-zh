# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p15 -15-Lec08 Video_ Process Management I (02_13_20).zh_en -BV1iP2CBaEHr_p15-

Okay， so let's get started。我来个就是做责。final parts。CP scheduling November。

 last time we were talking about。我。I did a refresher。Undergrad concepts and CPU scheduling。

 And then we talked about。The mix。Iplements the 16 level。

A few more things I wanted to mention before moving on， I do that。

Then I'm going to say a little bit about IPCs。Inter。M， there was a question， I believe。

 either last class of the class before。All messages working。

Me next because you had encountered that when you your system calls， right。被个 that他。just is。广播面试的。

Discuss that when。Ma of them， but we do that。And then we basically continue our discussion。

From the last time。🎼G magnet。We've done the scheduling part of process management to talk about process creation today。

And then we still have one more lecture on this。Or to focus on the。The process manager itself。

 how Mins has implemented some of this concepts。ちっます。So， that's really。Where we are。

Ms of process management。 But I do want to say one more thing about。A slightly longer term roadmap。

 So if you remember at the beginning， I said that the course is going to。

Include some coverage of Linux and Linux。And so far we've only been doing Linux because that's directly relevant to what you are doing in your lab。

 but there is a mini course of Linux going on into this course。So next week。

 we are going to do two lectures on Linuxox。Which will basically。

Be very similar to the concepts we have covered already， the Linuxux architecture。

Seal Linuxux CPU scheduleched so you'll get a feel for how things are different in Linux versus Linux and maybe why they make different design decisions and so on。

Then we will resume discussion on Linux for seven board classes and towards the end we'll do two more final lectures on Linux。

Which will， again， cover the rest of what we're done。

It's basically a four lecture sequence in the next that we kind of。Atro。こですか。

So next week is won't we all Linuxux。か所？Then will resume one minute discussion。And just to be clear。

 I'm going to be doing Linuxs， our secondary instructor is going to be doing Linuxox。

So that guy those。Okay。But the purpose of this course， that's how you were to think of the two of us。

So， so that's the logistics。 And then we will。Have have more things to say。

 but let me just finish our discussion on。設求しけ。Okay， remember I said I put this picture up last time。

So that's our 15 level。There it is scheduler that does MLlFQ。 There were certain things I should。

Add to that the first of it is that not all of the CPUU scheduling actually happens in the microcursor because this is Linux after all。

 a lot of stuff has been moved out of the micro。So in particular。

You will see that there is essentially a scheduleular process there on layer  three。

Theres actually implementing most of the scheduling there's a little bit of the scheduling that happens inside the kernel and then it invokes the scheduler processing how you can tell what process to run next and that's the one that will implement much of the bulk of it but it's a two split in to its not a two level but it just split in。

So， so how does the user level do it and what does it do。

 So here's the picture you want to keep in mind Okay where there is essentially a scheduling server like the process manager like the。

File server， you essentially have a process that's entirely responsible for CPU scheduling。

And these is the process and the terminal they going to interact。

In several ways so there are two kernel calls， this schedule and scheduler control that are designed for the scheduling process to invoke the kernel service and then there are several messages the kernel can actually sign to the scheduler to tell it certain things that have happened right。

We need to start the schedules with the next classes and things are there。

You know the priority is changed， so there are some messages that the colon can send to this process。

 there are some kernel calls that the process can meet， that's the interface。

Given this interface you can implement whatever CPU scheduleulularula you want inside that process。

 of course the standard one implements an MLFQ， the same picture I showed you is actually implemented in the bulk of this decision making as the code actually sits in the scheduler process。

Any questions on this？You are going to modify it， so it's better to pay attention and ask questions。

So some more details I already mentioned some of this there are two kernel calls where the scheduler control and the schedule calls that are actually going to be used so essentially。

They are going to send messages to the colon saying let's start scheduling the process。But whenever。

The process that is being executed， its quantum expires。

In order to get a message back from the terminal saying， run your function and decide what。

Now a kernel Excel does some work for you the work of actually enqueuing dequeuing process。

 etc cetera can be done inside the kernel or the task of choosing what to run can actually be implemented in the user level schedule so there is some work that the kernel do but by。

 the policy。No。然。Despite moving the policy out of the kernel and putting it into user space。

 there's still a small default policy that are left inside the kernel。

Just in case if the CPU scheduler process crashes。And then you're not going to be able to do anything。

 so there's some default thing that will still take care of doing the basic stuff while the bulk of the work is actually done inside the seat。

So that's why you want to keep in mind because you don't want the government do not have a scheduler process if we crash it。

Nothing can run in the system so there still a small policy that is in there。

 but most of it essentially is。Use process， some data structure there that I just added for sake of completeness。

 we are going to come back to that process table entry when I talk about process management。

Yes I'm not who to cover that table。I already mentioned this。

 but let me just skip that an instead say something。有 friend做个。

Implication of running your scheduler and user space is that you can actually have more than one of them。

This you are not seen a monolithic curve， essentially。

That way there are kernels including Linux that have support for multiple CPU scheduling policies。

 but when you compile the kernel， you have to pick one。You say。

 I want the kernel to be compiled with this policy and that's the one that's going to get baked into that binary。

So the decision so even if there is support for multiple。

 you choose that at compilation time and that's what that nerve will run。In this case。

 because you have a user level process that implements scheduling。

 you can actually run more than one of them。And you can say if。This is the process of these。

 this is the device called this scheduler versus that other schedule。

So you can actually have multiple policies and say for these class of processes。

 use this one from this other class， what how you decide this orthogonal？

The point is you can actually do this on。Groups of processes or any other criteria on a user basis or whatever else you want to do and say I can actually support multiple schedules because the kernel is still do the basic thing。

 but then depending on what is happening might remove one of the。That functionality。

 you will typically not see。A traditional monolythical this is saying that I can support multiple policies at rent rather than saying I've implemented them you were to pick one national point。

So that's an interesting thing to keep in mind that Linux allows you to know。

 of course it hasn't actually been implemented in Linux Linux are only one scheduler。

 but in theory you could actually add。说。That's all I had to say about CPU scheduling what I'm going to do now is spend a little bit of time talking about interrupt handling and IPCs because there are some questions about messages and how messages flow。

When you make system calls and so on， it is some more mimic specific background。たえてけない。

Then we'll resume the discussion on process。So let me start with。IC。The short picture first。

 and then come back to the sky。So there is a picture taken from the book。来番上。

It basically shows you different message types that Linux will support。

Youll see that there are essentially seven different types of messages that are predefined for you。

Okay， and the messages basically differ in。What they can take， So this ones。

 if it says i1 that says that's an integer， you can have a message where there are two integers and four points。

And have a message there are four in teachers or two points。You can now one with the who characters。

Po intes and cool lungs。So they are defined some message types already。Of course。

 you can define new ones as well if you want to， but by and large。

 I think you can make do with these because they have been。Use within the terminal for comment as。

In particular， where this comes into play is if you are implementing a system call or to use a message type。

 it's just good to just pick one of these。And just use it rather than trying to define the new one and so on。

So depending on what kind of message you're trying to pass。

If it maps to one of these doesn't mean every field has to be used。

 but if you can make use of that message type saying okay， this one actually is a character array。

 I can pass a string into it right so you can just use that message type if you want to pass strings。

Processsses so there are these predefined ones。And my general suggestion is if youre using it for any message passing for any code you write。

 try to stick to a predefinine one and see if you can just make use of。

Adding message types is going to add more complication。But that's aside how to use it aside。

 the thing you want to keep in mind is， there are essentially seven predefined verse types。

And then essentially what you're going to use is messages are sent using send received using receive。

 and then there is another one called sendend receive and notify there are the four calls that you can use to actually send messages back。

Typically there you may not use it， but something you might invoke within the kernel or a system call will actually use those internal。

 but you can also use that API to send messages and receive messages is explicit。

So seven message types yeah， so the other thing is they are all。You are a strap。

 which is essentially a union of all of those types。

For this you need to understand what a union is this is essentially a concept that is there in C at C+ because you may not find it elsewhere。

So essentially， it says that you have a structure。which had different fields but it could act as one of n kinds and its here is one of eight types and you can say now if' a message of type4。

 that structure look like that type otherwise it can look like something else and so on。So。

 it's just。It's a union of structure。That's really not important what you can simply do is you can define a message and then there are all kinds of macros returned to make things very simple so you can index a field say message type M one field one。

 which is an integer I， so that essentially allows you to access。Essentially， if you。

So you can just access it as any str and not worry about the certainties。

 but you should know that there are certainties in that the way they will live。

They try to be very efficient in terms of memory use and so on by defining。A somewhat complex data。

So。Don't try to define new message types is the simple message you want to do。

But I can use one of his life as much。Now， if you want to actually go deeper into how IPTC works。

 most of those are implemented in this frog。c。说了三。There is a function called Vnie and Min receive Min notified。

 that is where all of the hard work is being done into understanding receivingness。

The other thing you want to keep in mind is these are all blocking cord。

 the user rendezvous framework which essentially means you are doing blocking sends and receive these are not non blocking so if you send a message the receiver is not ready the block sender will block。

the receiver is ready a message is I people will be pop into the receive buffer and then both the center and receiver can continue receiver can continue it。

That's how standards inch the sense and receives work。Any message possible。

You can also have asynchronous， but it's not implemented in general。

 message passing can be asynchronous as well。To take a 6，77 class。

 we go into all of these concepts a lot more。And here， you don't need to worry about。

You should just know that sending and receiving are blocking operations。Yeah。

 and then essentially you're going to use this simple framework of a send， send receiver or go。

Let's start you any questions。I'm going to spend a little bit of time talking about some hardware concepts。

I don't know how much of this。Encountered in some other class because part of this is actually architecture concepts and part of this is OS concept。

As to do interrupt handling the picture you see there essentially is shows you how interrupts are handed on a Intel Xate6 processor。

This one is a 32 bit processor， older processor， but the concept is very similar。

you remember anything or inter。でけ。So we have gets？So。

What are I presume one of you know what an interpret is like。Essential， these are。

Hardwares can send a signal to the processor， which essentially interrupts a processor。

 which is why you's called to inter。The interrupt is typically sent。

An electronic nerve by simply raising a voltage on a certain pin of a chip so if you think of the voltage level being 0 or 1 in binary okay if the voltage is low that means there is no interrupt if you want to raise an interrupt you simply increase the voltage on that pin to high then the chip sensors that you will raise an interrupt and then does something。

So for each interrupt that you want to handle， there is essentially a specific pin on a chip。errors。

 essentially。A specific bins on the chip and you can then connect peripherals or whatever you want that essentially use that interact to signal the processor。

That's essentially a concept of what an interrupt is。Now you will see this is in the In architecture。

 you can 30 to In architecture， you can support 16 ins。So there are 16 pins there。

 in fact there are two chips， a master chip and a slave chip that you see here。last。张单图片。就是是。16。

 but in reality only a 15 because of zero to enter this clock。every time of koptics。

 it raises an interrupt and then the processor can do something same if the quantum expired and something else needs to be done。

There a clock。And you will see that there are some very simple things that。

What is here so interrupt1 is keyboard every time you press a key on the keyboard that keyboard is essentially a raisezor interrupt then the interrupt panel will run and figure out what key you press and then that is how the machine knows what you are doing。

Same is true if you're clicking on the mouse， you'll raise an interer that that might go through a USB bus and a lot more。

That is by and large。Of interrupt kindly from a hardware person。

 Theres nothing to do with Os iss all implemented in hardware。

 You'll see what the Os does when an interrupt is raised in just setting。Any questions on interrupts。

Is this you。Here are some architectural details before we get over stuff。

So I mentioned most of these only thing I didn't mention here is that when an interrupt is raised。

The hardware essentially also has a table。where you can fill in entries of memory addresses thats your interrupt vector so as I mentioned two or three classes ago if you have interrupt5 you look at the fifth entry of that team that fifth entry will have a memory address go to that memory address and start executing whatever instructions are stored as your interrupt handler。

So theres hardware support for this， in fact， that is you can actually have table of。

If six entries Linux users 56 of these。And they are called。In tell why that point。

gave this script as I。Essentially saying。Inter vector。Able of interest we configure figure our way。

Where the interpret kind store。that's something you want to keep in mind as suppose。

Let's look at a few details of。Iably next act is ours all。

Given that intratling will be dependent on the processor。

Because every processor will have its own input handling capability。

 some of the port in the kernel has to be architecture specific。It's not architecture independent。

 So this is the first time you've encountered architecture specific code。

 everything we talked about so far system calls and。

Schedul theyre not dependent on what the CPU type is。

Intertran has to be focused on what CPU you're trying to support。 If it's an entire CPU。

 the interrupt controller is called the chip number is 85 and9。 So essentially the。

When look at the source tree， you see that there is an IA259 do C source file that is where all intel specific inter handlingling。

You want to support an arm architecture。I a point that is specific to heart。Now。

 the concept is not different' just that it is specific。

That just you have an vector there that the index that allows you to essentially。

Indux into the table and jump to the encrypt。That's the basic concept。

A Linux makes things a little more complicated。The reason being。

 Linuxux has pulled a lot of things out of the curve and they are running in user space。

In particular， device drivers are running in loser space。

And interrupts are used heavily by devices to tell the processor saying something has happened can network packet arise on your Ethernet card。

 your Ethernet card raises an in。IfThe device driver for an internetnet or wfi card is running in user space。

 the kernel is going to receive the inter， but it does not have the inter handler because inter handler is in the device run。

s learning in user space， so some extra work has to be done by the kernel to then invoke the device。

 right device driver to then say this is the interactiveive order。In a mononethic kernel。

 this would not be the case because the device driver is inside the kernel。

 everything is in one address space， so you will simply look at the inter vector。

it will be an address that is。I it's in the user space。The address please， excuse me of the kernel。

 and you start executing that。Here， that's not going to be the。

You have to essentially pass that inter prompt to either a device driver or some other entity。

 which is then going back with the inter。So this is the additional work you have to do because of。

Do things out。And you see this is going to overhead。

And this is why you start seeing things slowing down because things that you could just implement as a code that is just part of your address space now essentially has become a message that you' are going to send to a device driver to then go and。

Yes wish。In minutes are the vice driversrs still considered part this？嗯。Ple applications。

User space is what？Yes。So the question is are device drive still considered part of the system application there indeed。

 so there are four layers actually。Everything that runs in layer4 is a vanilla user process。

The lowest layer is the kernel， and then there are some layers that are specific to system processes。

 device drivers are one of them you see that。So the priority level is just right about right below the kal bar。

So they're considered system processes。Even of technically their user processes。the system。

Or whos our processes？😔，Yesす。I that any for schedule？

Qu is do they run well the terminal runs to look at this and what I said last time the only thing that actually runs at the lowest priority level is the system and the clock task inside the plug everything else is not running at the same priority is running at a lower priority and includes the device drivers。

Having said that the other thing I did say as the picture here is the top five priority levels are essentially kernel and system services。

So think of them at not the same priority level， but something close to the。User processes are 7 up。

So user system。But notでか。It is zero1 through four are device drivers and process manager in the scheduler。

So not the same with gratitude the Lord。😔，But higher than processes the。这有点过审。在哪边？

AndTo much time on this。 You should know that。There is some additional complication in how the interpret kind ending works。

 but beyond that is's still the same。And so。The picture here shows you all the steps that the kernel has to perform in order to handle an income。

I turn this in the first letter。question。Explicit so the device raises an in that's going to raise a voltagege on some pen。

Specific to an intra I then essentially word。Inter on the processor。

 first thing that the processor has to do once it gets an interrupt is essentially save the current state of whatever is running on that processor。

Because now something else has to run to iron the interrupt。

 So you save the state of the currently running cross all the registers。

 et cetera are saved and then you basically index into a vector。ぱ度 said then our there。

Now in Linuxix world that address is going to be just a stop because not the real intratangler code。

 it can say that this intratangr is actually in that device driver so that stopub is simply going to then send a message to the device driver。

And then the device director takes。Otherwise， it goes with actual court。So， this is the。

The flow of what happens is actually show the internal handling。这是。

That you send the notification messagees to the device driver。 it's going to do whatever it's doing。

 and then you'll restart。Now system calls use a very similar process。

In system calls we are not raising a hardware inter。

 you are essentially raising a software inter So is a software that's sending a signal。

 It's not a real signal like hardwares actually don't change the voltage or any pin or anything like that but you can essentially call up instruction that says there's an software inter and then rest of the process is very similar。

He opposed to essentially next to vector。Figuring out what system called the exit。国选证的事。

So this is a little bit of background I wanted all of you to have because you are。After all。

 implementing a system call， even though you don't see any of this。

 you're not going to actually touch any interrupt or make a specific interrupt or anything like that。

 That's what is happening under the hood。To execute that system called。

Does this clear any questions on this。So I'm going to go back to process management。

 we had a bit of a digress。Some things I just want。没证据 for。So let's get back from process。

So I'm going to start with another refresher。😔，Which is basically a define for you。

Concept of processes and threads and so on。 And then we'll start talking about。

How process creation works。We look at the For system call。

 which presumably you know something about if you took an undergrad class in O， but if not。

 I will mention what it is and we look at how the next deal is all of。So， let's start with。

Some very simple definitions， so。What is a process？😔。

So I presume you know what a program is program is something that you write， score that you write。

 then if you write it in some languages that are compiled languages that you basically have a binary or an executive。

A process is essentially a program in execution。When you execute the program。

 it essentially becomes a process in users。So this you should know is just a standard definition from the another universe。

Of course。So now what does the process contain what's the definition of what's in the process？

Process essentially has some memory allocated to， it's called the address space of that process。

A process has stayed associated with it。Hey， what is part of the process state。

donbody anything things。For less。ReJust is a part of process rate。プラブラ。也不给他搞。Stag point of。

He pointed。Okay what about what the process is doing？And that's also part of the process。

 Is it ready random waiting。All of those things are all part of the process。

There are other things that are also part of the process state。

 which is memory management information， what files are open。

All of that is essentially part of the process。Now。

 how does the West keep track of all of this information？頑張です。every process。

 the worse has to keep track of all of those pieces of information。系度跟住。Okay。

 so you have to have a data structure， which is called the process table。

Where skip this is just showing four processes executing patch。So。

So here's a picture that just shows you the layout of a process I already mentioned this before。

 every process has three segments， the text segment which holds scored the stack segment and the heap is dynamically allocated every stack is essentially located variable as well and this is the picture to keep the right always the text segment so not going to look like that we can't put source scored in the text segment。

And there's a stack that's growing up。第该是录音道。And there's a program counter has keeping track of what is executing。

 but this is a sequentially executing process because essentially executing one instruction at a time you can now groups and things sometimes。

So now you'll see here you already have the program counter stack point that you have to keep track of where the stack is。

 where the he is， where the process is loaded in RAM and so。

Here's the other part of the process state that I was mentioning that basically trash what the process is currently doing。

 typically an executing process will within one of three states which I mentioned last time also as we talked about CPU scheduling。

 ready running and week。Read means that it is ready and waiting for return turn on the CPU running means is actually executing on the CPU wait means it's blocked on。

And then there are two other states coming in it。Which means it's finished and new。

 which means it just started。So it cycles through those states， but the CPU has to keep。

See the OS has to keep trying。W state the processes in？

All of this information is kept in a data structure called the process table the process control bar block。

TCB。So the essentially the OS has to have a data structure on a table for every process there is going to be an entry。

 an entry has all of that information and several more priority of the process。そ状。那。

Given the amount of information you have to track in that data structure。

This was Linux' is concerned。No single table that tracks it off。

You will see that Linuxex actually splits the process table into three parts。

There is essentially one part that sits in the process manager is one part that actually sits in the memory manager。

And then one there6 in the5。The fight of。Because these are user level processes。

So what we have done is logically， you have a single table。But physically。

 you split the implementation of the table and each process keeps that part of the table that is relevant to it。

Okay。So that's the way you want to keep in mind keep this in mind So if you go Linux phone to look for the process table。

 you are not going to find one table that has all the information because it's actually not stored that。

Like a monolithic kernel that will have a signal data structure heres actually split across multiple entities in the third。

 That's again， an artifact of a micro kernel。Thank you。Okay， so moving on。

I to talk a little bit about that。 We are not going to go of your question。何ずだとパスして。嗯，他。

If you have one process table you can。Know which ID goes like which you can see all the fields are connected。

When you3， how you connect。Which processes？就。Okay， the question is that if you had only one table。

 you would have an entry for a process， all the fields are in one place， if you have three tables。

 how do you connect of the information？So every process is going to have a unique I， the process I。

 so all the although it's not shown there， all of those tables have to actually have a process I field in it。

 so the same process will have。Enterries in all three tables， you index the process I。

 you have the information for that process in that case。你有在过审经。所今年。

the motion of threads Im to quickly introduce is you should know what it is。

 we are not going to spend too much time on this because Linux does not have support for kernel level threats so you will see no threading inside the kernel at all。

Mix only supports processes， all trends are actually done at the user level。失いたした。

So what is a threat？What's the definition of what。Use threats What do you think they do。

That a sub processs， or does it do？Ex。ラで。We won't use the term process but you all just thing makes sense so essentially what I described a process as an address space and there's one program counter that's executing one instruction at a time so there's a single thread of execution that' weve wov through that process。

But there is no requirement that there is only one entity executing code in that process。

 there could be multiple entities that are executing code of the text segment。

 each of those entities is going to be called a thread of control。

So essentially there are multiple threads of control that are sharing the same address space the text segment is the same for all of those so each entity can execute any part that segment of that text any function can be executed by any entity。

Each process。So each thread is going to get its own stack because when you call a function。

 youve got to expand the stack and so。So the stack is no longer shared。

 there has to be multiple stacks， one per3。The heap， on the other hand。

 is going to be shed because they're dynamically allocated。So the picture you want to keep in mind。

Is this one on the to your left is a traditional sequential process。Single threat of control。

One thing executing in that process at any given time。One stack， one heap， one set of registers。

 et cetera， eta。What they shown on the right。A concurrent process。 So there's a sequential process。

 concurrent process， concurrent process it has multiple trends in it。We'll see that for us three。

有谁的第。what is not clear is。No boxes here。 This is essentially one text segment， It's the same port。

Each thread has its own stack。There's own set of registers。Good do share the he。

So this allows you concurrent execution of code within an accuracy。就是。Let me know the same picture。

H that first second can show you。Same picture as put up before for a process。

 but now look at the thread here so there are multiple threads and in particular there are two。

If you look at that you see that it starts with next， this is what heard。

ItCom in a problem So theyre executing within the same tech segment。

 You see there are two program counters， one for each set in this case。

 one of them is executing that function other。那个。Here that are whose backs。this shape。

two stack one that。Just clear。So does anyone remember the difference between concurrency and parallelism？

We try my program， give you par。What is the difference between comparison。

What's the definition before we ask the what's the definition of chemical yes。

t need a multiple processor。来自审查院。So concurrency， the definition of concurrency is it looks like there are multiple things executing within an address space。

Theyre executing concurrently。But that doesn't mean they're executing at the same time because ifs a un processor。

 only one of those sets can execute at any given time。

But if you have a multi core system or multiproces system。

 you get two parallels of well both of these threads and execute on two separate cores at exactly the same time so you get two parallel。

So multi thread program give you concurrency， but you run that multi thread program on a multi core system you also get。

Fnalism， in addition。So you need to at least know these differences。you write theレ。

Now very quickly I'm going to talk about I mentioned this in the picture and we just skip this talk about the real reds and user land。

I presume if you remember anything from an OS class heard of these jobss。😔。

As the name cur level threads suggests。The OS Cornal actually has explicit support for trades。Okay。

 what does that mean。Or does having explicit government support for？It was like the number。

So explicit visit support simply being as a kernel can actually see how many threads are inside that process。

There two threads for， you can actually see that。So now that you can actually see how many threads there are inside the process。

 you can then explicitly schedule them。Now the CPU scheduler and no longer choosing a process for execution is actually choosing a threat within a process for。

Same CPU scheduler， you can have MLFQ scheduling， but you are now actually choosing a thread for。

When you choose a thread， you have to automatically pick。It's been its process for execution as well。

Now we can talk about user level processes。The user level clicks。Yes， the name suggests。

There is no card support for。Thanks。这来。Pre me Nes。应该改这个。

The next Government does not have any support for threats。Yet if you want the right credit programs。

 the way you are going to do this is you write a library that provides support for training。

It the journal has not supported threats for you So you write a library that actually implements our concept of a thread。

So now the kernel doesn't know how many threads are inside the process。Because it cannot see that。

That tags in the processes I thought just these processes。

So the CPU scheduler is simply on the choose a process for execution。

As going to let's execute process5。Okay then how do you decide how the threat gets。Processed。さ。Yes。

 the process can itself the site， so essentially。Here is a picture that shows you what happens the scheduling is now a two level decision。

 the CPU scheduler in the kernel。The OS scheduler， because in Linux is not in the terminal。

 the OS scheduler chooses the process。When you execute the process first the library runs。

 there's a scheduler in the library that says which of the thread should。And then it uses a pay for。

And so that's how you are essentially going to schedule threads as a user level system。

 thread system。Any questions on this？So the interesting thing about user level threads is each library can implement whatever scheduler it wants for its threads。

If you want to do round robin and process A， you can do round roing。

 if you want to do lottery scheduling in process B。

 you can do lottery skills because they' are all implemented as a library。

You can have multiple scheduler， one in each process if you want。Remember that in Linux。

 you can do the same thing at the OS level as well， because I said earlier。

 that you can have multiple schedulers。Exputing and跟个人。Most of the us don't remember。

Use are level threats。can do that and they often do that way。So know。Third。バらでもとそ有。

Little bit of you probably written some thread code。

 so there are two or three threading libraries that are very popular the speed threads if you in Mu world。

 you essentially write your threading code using Po threads。

And C or C plus plus if you are writing it in Java， you write Java threads。

 the Java is built in support for threads So in the Windows world。

 you can use the win 32 light by and large they all do the same thing allow you to create credit dig threads managed to use some of course logs and all。

So here are some functional goals。不是。So I wanted to know like does user level threads also like allow us to support parallelism like let's say we have my a question I should have asked that question yes。

Quest is， does user level thread allow you to support panelists？Not concurrency。Currency， of course。

 any trading package。Well， unless the process to get started by the OS on multiple。😔。

So to get true parallelism， the process has to get scheduled multiple times or multiple than multiple course。

always doesn't know。That the process has threats in it。

 in fact the OSS is designed assuming processessthees have no threat。

 because it doesn't support threat， so the OS is are certainly not going to schedule the process for more than one thing because it thinks that the process is only one program counted。

So why would it schedule， so typically in user level threads package is a kernel and not。

Schedule a processor on more than one processor at a time。

 So you are not going to get two parallelism at a thread level。

That doesn't mean there is no true parallelism， you can schedule two independent processes or two course。

 so you will get process level parallels。That's still a real parallelism， but not level。

Gment things you can get for question。Could you design your own？Thread server， threat manager。Alex。

Yes， questions。 Can you implement your own。That's schedule as as you're see in this slide。

People have that because only way to support trends is through user package there's a very lightweight library called M times I think。

Implements projects like interface or threading。 There's also a goodru thread P threads。

 which is just taking a P threads implementation from。这。不是说我找不人。About do user levels。也是不是。家海啥。第一次。呃。

L第四。I like for job or would it be in the jobs？Is it somewhere in the Java virtual machine？😔。

Like they translate these。Yes， so。The question is if Java and Python is different because Python ask kind of threat support。

 but really not。そず。Let's just take jaw of。M。主是在这里。Okay so， that's a Java process。Thats end。

M chair court。So you找va price here。Now it's up to the JVM implementation to decide whether those threads are going to be user level or currently。

If you write your JVM for a OS that has native support for kernel level threads。

 then the JVM should take advantage of this so it can essentially map each of these Java crash or kernel level threads。

then all of those sets are going to get scheduled by the terminal and you'll get two parallelism for multiple course and all of those good things。

 but then you can also write a JVM。For an OSs that has no support for k level threads。

 in this case you essentially make the JVM implement it won't use a metal threads package。

That well then it basically still supports Java threats because the Java interface does not changed。

Java code has to run on any JVM， so you still get threads， but theyre just couple with the user them。

Same is true of any system， like threads， any concept of threats out in the user。どたにか使か。

Just one slide， I did skip。W I wanted to go back to。This point， which are trading more。

So the 3 models there show you how user and kernel level differ from an OS perspective。

The first picture here。So this essentially said many user level threads get mapped onto one entity inside the curve。

 this is user level threads so that entity is essentially a process if oversees a process it doesn't see the presence or threads in then it only schedules processes and then。

时间就。Picture on the top right is kernel level traits。

That's a one to one mapping where every user level thread gets mapped onto one kernel level entity that。

The kernel directly knows above。 So whether the kernel picks one of these entitiess to run that user level transaction essentially。

So maybe to one one to while and then you can actually have others as well。

 and we have four user level pair getting map。3 level。他做主。You can design your own mapping。

also say this user is doing important stuff， I create a special one thermal level thread for it。

 these ones just share these three and things of that。

So if you use the sophisticated feature of any threading library。

 it will allow you to deiate from this mod。And in New landscape， that's what youre stuck。

But a government level threat by default is going to give you one to one。

 but you can essentially do many to win。这也是过去。Okay what's the benefit of doing many too many so that is basically goes back to what work is each thread doing and how much CPU time？

If you essentially have the one to one model， that's the default model。

 each of your threads is going to get scheduled at the same。

Priority level might get the same amount of sleep through time and so on and so。

But maybe there are some tasks inside your application that are more important than others that might need more CPU time so you might create。

A special thread just for them and then others get to share so four of them share three of these then the secure time for these three is getting split technologies。

aggregate each of them is getting less equal time。So you can decide， if you have a browser。

 for example， maybe the GuI trend is getting macrocurnal effect for high responsiveness。

 but some background processing wouldn be shared so you can decide。If you want to。音月上么完。这我修息。Theres。

And as I said， there's really none of this applies to Linux other than the user level concept because that's all that Linux actually has。

不行。So let's talk a little bit about process creation。Okay。

 so now we are getting deeper into the process， manage it。

 so you're going to talk about four in exact and things。So what causes a process to be created？えなス。

And you boot up your process， certain processes start。The process were created。

Any process can create another process。I see。User can submit jobs after the interview process。 Okay。

 or you can essentially click on a。iconon on user interface that starts a process and so there are many ways you can start applications that start executing and then they execute their turn into a process。

But what is actually happening end of the hood to do all of those things。

 essentially you need to have system calls and allow it to create a process。啊。reality， as far。

Uns like operating systems are concerned every process。

Even on what I said on the pages that has to be created by some other process process don't logically appeal。

So every process is going to essentially get created by another process。

 which means that every process has a parent， a parent is the process that create that process。

So there's a parentch relationship between a。Acros the。

Between any process in the system and any process has a pair。Parent have terminated。

 but when it got created， it。So。And the question is how does the process create that process and this is done through a system called called4。

Can does anyone remember any of this。What does hold。So。

Essentially from the single process it's running it creates the second process then the second。

And then from that， they can determine whether they。So Fork essentially creates another process。

So if you want to create a new process， you call fork because you want to create a second process。

when you just do four， what is executing in that second process？

 so it's essentially an exact clone of the pairing process。

what Fork is just doing is essentially making a cr。The parent basically creates a child。

 The child looks exactly like the parent in every single day。Except that is as a distinct processing。

 you just take the memory and you essentially copy it。

And then when you created the parent and the child look identical。

 their program counters are pointing in the same place， everything is exactly the same thing。

And then beyond that point， the parent and the child can start executing different things within that process。

Remember to still a copy of that class。They're not obligated to do the same thing anymore。

So that's four。 can I go into some details of work。Of it works and so on。

 But then let me ask the following question， what's the point of creating clones of the same process。

We'll get hundreds of processes that all look the same。

That's presumably not what you wanted to do if you want to start a browser。😔，Okay。

 click on that interface，Essential a graphical user interface is created a clone of itself。

Not started the browser yet。You understand my question。

As we said For is a system call that has created a copy of that process。

Suppose you want to start a different process。Creating a copy of an existing process does not let you do that。

ThatSo what will we do to。当是是口。Okay， so child process is going to call another system called or an exact。

Or does that。W just starts make。但是。Yes。是4。So when you do exactec。

 you essentially specify the name of a binary or a program。

So what Exec is going to do is essentially going to aid that program。

And it's going to replace the contents of the current process with that program and start executing a completely new process。

Is that clear what I just said？you have process A。跟讲科。Its a copy of itself， which is big。

At this point， B just looks like it's not doing anything different。

 But what we can do is once it continues execution of reconciliation， it can essentially call。

Function called example。 under a system called called Ex。 And then here， you can essentially say。

/lash applications， slash probeme or whatever else you want to specify the name of a program and then what that exact call is going to do is it going to take。

Specified application from your disk。It's going to lower it into this memory region。

 essentially in wipe out， whatever is loaded there which is a copy of the parent process。

 it's going to load that program in there and then start executing。

So that is essentially how you start executing new programs Yota 2 system control1 was first to create a process and the second to tell that process to execute something different from the pair。

Otherwise， it's just won't exist you the same thing。

So for and ex as you can imagine going to as pairs。Yes。

 so the essentially process creation is a two step process， you could have said why did you do this。

 why couldn't you just pass that argument to four。It create a process and load the program from the beginning。

 you could have done that this is a design decision the OS designers did。

I went a new next years and I stuck with。There will be two calls to start a process not one。

 it was to create a new process， then to execute something different in that process。

So this is simply a design that is there's no real reason you may want to do this。

Because we could have simply done that in one step。So nowm there。In mind。

 let's going to look at some details。Of work and this is incidentally how your shell is also going to work your command like pro can you type a command the shell is essentially going to go a four is going to create a copy of itself so you have a second shell running and in there is going to call an exactec and just pass the string or whatever you type and then that starts executing。

This one the she is one what the city Mar all that things who exactly。

OkaySo here is essentially some sea code that shows you how work is going to work。 you will see that。

We going forward here。At this point， this process I was executing essentially creates a replica both of them。

Exactly the same， which is both of them have executed until this point。Now， the way you start。

The child can start behaving differently from the parent。I。

Through a mechanism that4 provides when4 returns after it is created a copy。

The return values are going to be different than the child and the parent。

In particular in the parent， you are to fork is going to return an in as is the process idea of the child。

So if we created a new process， ID is 5，4 will return 50。What is the time？Will that time was you。

So if you want the right code where you want your child to behave differently。

 you should just take the return value of4 and say if the return value is0 so you basically write a if statement so if the return value is 0 you go into the if and then you start doing something to your exact。

is going to be inside it here。So you can't just have work and then an exec because then the parent will also call the ex。

不作成。One of the parent who。changenge its behavior， because if the parent is shell。

 it has to stay a shell， it's not going to change。 So you only want the child to call the exact。

 not the parent。在接。是。Learn this in clear if you haven't， then this is what we need to understand。我说。

You want to make sure only the child calls the exact parent the way you do this is you change the return value for the worst guarantee is that the return the value of work in the child is going to be0 so you say if work has returned a0 who and an exact I havewise the else you are still the parent so this is the parent code so the child exs this the parent ex。

So that's the main difference。Between how the child and the parent are moving。

Those of you who don't know this from yourself in the worst glad aren there any questions？😔。

This is a subtle concept we need to understand。We'll be using some process management as soon。

So here is the same thing shown in the picture。Okay， what I do here it slightly picture。

 So youll see after the four， you essentially have。W office。我不。

Comers are essentially pointing the court。In the child go to the next statement。

 what is written here is a zero。The pair in what has returned from work is essentially that。一定要不在。

process I didn check。 So if you basically look at this。As the if statement。

 you can make the child do different things。Ca hopefully the child is going to go and exit。

So here's a picture of what Linux is going to do for this。Right， so yeah， we have。

A and B two processes and the OSs loaded A is going to call for。

 you will see that you created a copy of a so that's a chain that you see here。This is often up form。

 you see that as a copy of a that's an identical。Looks exactly the same Karen And if a child calls exec and starts a new program。

Then then you'll see that that program is turning to see because that's executing something else at this point。

It size could be different depending on whatever that。this。They change the size of the stack。

 he text segment everything could be different。中国审计。So now， let's go back and。

those are the concepts that you learn。class， but now let's look a little bit more。

How mix is actually going。Vix is going。Okay so those are the steps that if you actually go and look at the do for。

Sstem called。Government rather， you will see all of those things happening in there。这哪こ的就是。

The first thing you is going to do is the process table full， process table is full。

 you can't actually work in the process。Typically， a process table shouldn't be full because you can always expand the size of the process table。

 but maybe we will run on or something。ためで。Assuming that。And create a new process。

 Here You are now going to allocate memory for that process。

Here the first things you've got I locate some of them。In this case。

 the same amount of land are located to the parent is allocate to China。

You want to essentially copy whatever is sort of in the pro memory into that allocated region。

 so just make an exact copy。それ你要。the process lot。Lo that。Find a new process I sequential。8是30。

Essential here has a new process。The created here an name on and so on。That the。Yeah， located and so。

So， essentially， create。ForEn in the process table， allocate memory。

 copy the contents of the parent into the allocated region。At that point。

 you're creating a process that's a clone over the paper。

Remember that the parent is not executing at this point in time。Okay。

 so the contents of the parents memory is not changing while you make this copy。Why is that？

Because you made a system called。Go for。What does a system called you。

 It supens execution of the process and goes to the government to execute that system。

 So by definition。Pros that in for has no not executed because waiting for the system called finish。

 So it's safe to copy its content。And assume that it will not change while you make this curve because the membrane region can be large。

 you can have a 500 M process。And can two gigy you to actually make a real coffee。Technically。

 you don't because you can use smarter things that copy or write。

 but in a simple implementation would actually copy it， but it takes some time implement。发嘅光边。

So but you know that the process memory will not change。という政府。So。Very quickly。

 exactec is not very different。 So in this case， you already created a copy。

 you're trying to start a new program。So you are going to check is that。ログラム？

The string that we passed。I it executability your permission is to execute right。

Andcept then essentially， are're going to allocate new women。

AndRea because the size of that new process would be completely different from the initial size of the parent process that created。

你没个。Okay， so you see that this is somewhat wasteful。

Work and allow you to create a new process in one step。

actually are to allocate me every and it because I made a copy through it all out started。That上。

So then you essentially create a stack， you create a heap。

 set up essentially some permissions for that process。

 and then tell the system that always that now this process is ready or not that new process is going to start executing from the beginning。

Because I knew the random new program when you first created a child。

 it did not start from the beginning， it actually started from there you were at4。

 you just started executing from the middle。But this is now running exactly I' going to start。

They clear。Any questions on thisす。Why does it need to allocate new memory。

 Why can't it just use the word。That good question。

 Why do you need to allocate room memory white and you use the old one。Technically you could。

 but you don't know that the child， the new program or the new process you are starting needs the same amount of memory as the old process So in this case you can see this picture。

So this是 the size意 of a。Whatever was executing， So when you made a copy thats the same size of primary you get in the child process now you start exact and that that process that you're starting needs a lot more women。

So it's much easier to then essentially allocate a new region。

 because you can't overwride this one yourself。We are located on。That's essentially way。Youre anyway。

 scrubbing whatever else in the crosses and we him all the stack。 Everything is erased。Theyre these。

But the size doesn't have to be the same， it will bit different。

 which is why it's better to actually allocate。Are you asking a for specific question or are？

 so if you call for on a multi thread process， child process is also going to be multi thread。

But if one of those threads calls an exec， then all the threads are gone because it just started a new process。

 but you don't have to call exec as you know， you can go a forward and all of those threads can start and。

客界的は事業し。没 share。他单。That's a very good question Okay。

 the question is if you had a monthly threaded process and you had two parallelism if one。

Cal threat calls for。And then you start making a copy。

 but there's another thread running somewhere else that is just changing something。

 mu around with memory and youre going to get a problem so that's I think a good point。

 So this is why you need government to do safe。Basically， when you are doing a copy。

 you can actually mark the memory region and read only and do things like that that allows you to do。

And so you have to do this if you have multi threadread kernels。

 lots of things have to you have to make the kernel Excel thread say called the reentering kernel because there are lots of other problems that can occur What if two processes call for or two processors at the same time。

That data structure， the process table will need a lock。We did room love。I'ming at on with N。

 so lots of things havent changed immediately。AndEn how work gets。

SoThe unicorn system much easier might take on everything next off。Including scheduling。

 tunnels are written and road locking。Our system calls are implemented。

And we have not looked at any of those stick。The basic。有在过性。So， let's stop here。共款当的。

Will continue our process management discussion。2 weeks。Next week。コスタティング。嗯。

