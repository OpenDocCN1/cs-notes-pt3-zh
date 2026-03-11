# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p24 -24-Lec12 Video_ Virtualization - Part 1 (03_03_20).zh_en -BV1iP2CBaEHr_p24-

你给喝。I want to say a few words about where we are in the course。

So you understand what we are going to do next and then what is coming。Down the by。

Beyond those spring break。So what we will do this week are essentially two lectures on virtualization。

Thats what for' there to talk about。R concepts on virtualization。

 And then next time we talk about a specific type， which is OS level virtualization。

 which is how Docker and Li。T that you。Look that actually work。Now。

What we have covered so far are essentially process management， CPU scheduling and memory management。

Both from a general lowest perspective and the perspective of Linux。

 virtualization is actually a process management concept， typically in a most advanced OS class。

 this should have come earlier， but I held off on doing that because I wanted to cover more Linux stuff before we get to this because it was related to the lab。

But we have now covered enough ground that I can now go back to virtualization and finish some of the material I wanted to cover。

What we will have on next week， So this week will be all virtualization。 next week， Tuesday。

 there is no class。theres exam date， to just covered the exam in the evening there one lecture。And。

The Thursday class is going to be the second lecture on Linux remember I said there' will be three to four lectures on Linux we did the process management lecture of Linux already。

Look at more memory management。Because we now covered it back from a business perspective。

So that's Thursday， then the spring break。 And after we resume your two big topics to cover one is。

IO and device drivers， the other one is on file system。

 and then towards Z we'll talk about some networking and things of that sort as well。

So once we do that， we kind of covered all the components of the。So that's the bigger picture。

 So today。We talk about virtualization I'll give you a definition of what virtualization is I talk at a high level。

 different types of virtualization then we start looking at today we are going to look at what is called hardware virtualization。

On Thursday， we are going to look at over socialization。

 which are the two types that are most popular。The ones that are used often。

Some of this is material that's actually covered in 677 as well I put my 677 slides and I modified them。

For this class， because here we have some interest in covering virtualization as well。So。

 so let's start with the。The background and definition virtualization is not a new concept it originated in the 1970s Nevertheless it has become popular in the last 15 years or so and now it is used in a variety of environments you all use it in for your labs because thats code development is also one of the use cases for virtualization and so as cloud computing and many other things as we will see okay so what is the definition。

virtualization。 So it starts with something that looks very simple。

So virtualization is defined as the ability to take one interface of some system and use that interface to emulate a second interface。

So you are providing an abstraction that abstraction is an interface and you are going to provide an abstraction using a different abstract so in some sense you might use the native interface provided by some system and write a layer that emulates the second interface using that in that's our definition and in the picture you will see that to your。

You will see that there is essentially a machine A， which has some interface A。

 You can think of that as the OSs interface or some other interface。

And there are programs on top and on the right you will see another picture and that is where the virtualization comes in here。

Do I have a second machine be。Which has different interface deep。

So here the virtualization there is essentially look taking interface B and emulating interface A。

In doing so， it allows programs that were designed to run on a machine with controversy to now run on a different machine with。

So that' is a very high level general definition it going to get much deeper but that definition is enough for us to understand why this technology was developed to begin with back in the 70s。

😊，IBM and many other manufacturers used to sell these expensive machines called veinfr Okay that cost millions of dollars to buy basically big machines that took the size of an entire room and so on。

But was an expensive investment for customers to make。Now， suppose。

As some customer of a main frame says my machine is old， it's 10 years old。

 starting to buy a new machine。Yeah， so you would go to IBM。

 which was a big vendor at that time saying， I would like to buy a new ma。And they could say， yes。

 we have now the latest and the greatest， it's much faster than your old hardware。

 it runs much faster， everything is better。And then that they're told you by the way。

 none of your programs are going to work because we change the processor we change the OS so everything has changed since you bought your machine because technology was evolving very quickly yeah architectures changed and the changed and whatnot so if we tell the customer nothing that you have on your old machine is going to run because everything has changed but you will get a better machine。

That's not a good way to sell machine。But if you told them instead say I can sell you this nice machine everything is faster。

 it has a better processor OS and you can tell them everything is changed。

 but all your programs will continue to run because we are going to give you additional software that essentially make that machine look like older machines or all your legacy applications will run as and you can now write new applications that take advantage of the new features of the machine that's a much better way to sell your machine because writing code is actually expensive。

 It requires people time。Cootting code also takes people time and that's an expensive。

 laborgoious operation。 You don't want to tell your customer rewrite。If you buy that， that doesn。

So that is the whole reason that developed this concept they said if we change the hardware we change the OS application should not have to be rewritten so we got the right of portability layer that was essentially a virtualization so what that meant is you had all these layers that emulated older machines in this case interface a is a machine interface for an older machine。

And B is the native interface on this new。Well that's basically how this technology was developed。

So that and that allows essentially in this case if interface A is an OS interface it is emulating an older OS。

 interface A is a machine interface as we see it actually emulates an older processor or an older machine it depends on what you are trying to em。

Any questions on this definition？And now let's talk about。😔，Todays not what happened in the 197。

 So there are different types of virtualization。Depending on which interface you use to emulate another interface。

 you are going to get virtualization at different layers of the hardware and software stack。

At the very bottom there is essentially the hardware。

The interface provided by the hardware is essentially the CPU instruction set。

So if you essentially emulate one processor using another processor or a matime machine。

 hardware hardware using another machine hardware， you get what is called hardware level virtualization。

What you are actually seeing in most of your virtualization is essentially could be hardware level virtualization because things like virtual box emulate an entire PC in software。

 it emulates a processor， it emulates all the peripherals of a PC and so so youre essentially emulating that interface at a PC provides at a hardware level。

That's one hardware level of。Next level up is essentially the operating system。

So if you take the interface exposed by an OSs and emulate a second interface。

 youre going to get OS level mod。So you could do this for the same reason is that IBM they essentially emulated a software interface okay the OS look like an older OS so you can have a more modern kernel emulate and older system while interface otherwise the applications right there to be rewritten could change the OS interface where OS interface in this case is a system called interface。

对。You could also do this at the application there， so you could essentially use libraries that are written at an application there to emulate some other library。

That is called application level virtual。I this clear。Yes which us that' wine appss in the。嗯，好嘞。

Good question， which category does wine fall in and come to that in just one slide。So。

So let's talk about now different types of virtualization with that background。

The most basic kind is called emulation。 So here we have a piece of software。

So that is emulating another machine， an entire machine， entire CPU CPU instruction set。

 the register sun machine or the peripheral on the machine is this called emulation so you have essentially a software implementation of an entire machine。

Typically a PC。But you are emulatorators that can emulate any processor。So you have box there。😔。

Essentially QA， pumo， which we are going to talk about our Linuxux。

 all of these essentially a support for emulating all kinds of processor。

 so you could essentially run programs that were designed to run on those other processor using this emulation software that's running on your native machine。

So that' is called emulation that is the basic most basic kind and as you can see that is going to be slow because you are essentially doing binary translation of assembly instruction。

Every time that native code executes some assembly instruction for its native processor。

 you have to essentially translate it into some equivalent number of instructions on the processor the emimulator runs up。

Because it em a processor。Eating all the benefits。So if you have more instruction on one machine or one CPU that are emulating you order to translate that to some move or some other equivalent instruction on this machine。

 this goes for every instruction its going to be slope because you are doing instruction by instruction。

也没有。Next is full or meta virtualization。So， in this case。Essentially， you're going to emulate。

The same interface using the native interface。So what does that mean I if I go back to the previous picture。

没有。The interface A that you are emulating is same as interface B。Here。

 the mutulated interface is exactly the same as the underlying。

That's called hardware optimizationization。没对我这个。So you might ask。

 why would you actually want to emulate the same interface？

Why couldn't we just run the program native？So for example， we are emulating x86 using X86 process。I。

There you can。Give me an example of where you were use。you want to。O。It knows the door。

This way doesn't actually have the access。So you can run one o one another。Yes。

 wind creation open the next。Make this wrong。But is properly。The native and the inter。

Or to get do this。It's too to be。So you can use it for code development you are essentially using this for your lab using virtual box。

What does virtual box do。Okay， the muulate an X86 PC。RightThat's what the Muix is running on。

What is virtual box running。Turning on your laptop or your desktop what is that that's also an X86 PC essentially emulating X86 PC in software using a native PC thats of the same ca。

So that essentially means that the interface that virtual box is providing to whatever is running inside it is exactly the same as your PC is providing to whatever voice is running。

So those two interfaces are the same there are many reasons to do this for development。

 you can now run Linuxux on or you running Linux on your native machine。

And theon Windows on theon map on。Then so you can run one over on top of the other without having to reboot The only other way you could have done this is made it make a machine view which is different from running it。

し。So you have essentially virtual box， parallel， VMware workstation。

 I and VM family that I all do this full native virtualization。

 we are going to see how to do this in quite some detail。Here， but let's complete the list first。

There' is another type of virtualization called para virtualization， So in this case。

You essentially are going to simulate， not simulate the hardware。

 but you are essentially going to change the native over。

 not the native of the guest OS that' is going to run inside the virtual machine to make some special cough。

If you do that， you essentially have a para virtual assistant。

The one big difference between para virtualization and everything else we talked about on the previousmic is that we are so far assumed that your code does not need to change and runs on this virtualized interface code runs unmodified。

 you are not changing the code。there's OS code or application code runs exactly the same as it ran on the native mission in para virtualization that assumption is not true you are actually going to run a special version of the curve so you are change the K code to run in a virtualized environment the applications don't change but the OSs does change。

And willll see why that makes sense。现在那个。本来是没你的损子。And then we come to OS level virtualization so here you' are using one OS interface to run another OS interface interface or you to look at doctor or yours containers next time。

There are other things like PSSD gels and solarlar containers and all am newulate。

O virtualization framework。 and they did effectively what IBM did 50 years ago。

They essentially said we are going to keep changing the OS interface。

 the fiscal interface is going to change， but if you want to run your code using a previous interface you can just create an OS virtualization where you can emulate an older version of the curve because of that so in that emulated environment or in that virtualized environment。

 it looked like you're running an older version of the OS。

That way the code does not have to be equal。 That's how they started and now others have actually done similar things。

In most cases， you don't necessarily。Eulate an older interface， you emulate the same interface。

 but I use just for things like isolation and performance management and so on。

And Docker allows you to then also package application and download a run without having to configure things of this。

Because there are many advantages on that part of it we'll talk about next step。

But let's just complete the list last one is application and virtualization。

 so here we are going to essentially emulate using some application library application and another interface。

Simpst example is Java。JVM Java virtual machine is an abstract machine。

That's essentially being emulated using C library， JVM is written in typically in C or C plus plus or some language。

So you're essentially emulating one interface using algorithm， but there are many other examples。

Somebody asked about white。So I don' know how if you know what line is。你什么 people况。What does it do。

关闭。Okay， run Windows apps on another machine。 How does it do this Okay it is not running Windows。

So it is essentially emulating the win 32 or win maybe it does win 64 number but win 32 inter 0 that is the interface that Windows export so they simply reimmented that library using a native library。

Okay so it is simply saying Ill expose a win 30 to API。

 so any application that wants to run win 32 can just use this library it doesn't actually need to use Windows itself。

Where as emulating one application level interface using another AM。There are many others。

 so there is another one。ロゼタ。I don't know if how many of you heard of this one。

 So this actually was an Apple technology。About 10。But some number of years ago。

 Apple switched its hardware configurations from using power PC processors to Intel processor it raise max run on X86 Intel processor。

 but at one point there ran power PC which was a different kind of processor altogether。

So they had the same problem IVM if you buy a new Mac。

 none of your old applications run because that。For a completely different CPU altogether。

So this said we do the same thing we will essentially give a library that does binary translation。

 it can take a power PC executable and run it unmodified for an X86 machine。

And this was thatta interface would essentially execute every assembly instruction that was powered This instruction would get dynamically translated to equivalentent x 86 instruction on the flight。

While you are executing and you would just run because there'll be some performance overhead of doing this because you're doing binary translation。

 but your applications would run unmodified， you didn't even have to start Rosette you just started your application by double clicking on it as if it was a normal application and it would just run you wouldn't even know it was not an exit they made it very seamless。

So this was another of this application level virtualization。

 of course it also did something at the processor level because we were doing translation or processor instruction which is all an application everything。

就没。Use cases for virtualization。 We won't talk much about application level at all。

What well do in the rest of today and next class is talk about the hardware virtualization。

 which is what I talk about here。And I'm going to talk next time about OS level optimization and talker and things so。

This year。Let's start with part of a little watching。

So the one term that you need to know when you talk about virtualization is this term called hypervissor。

Hypervissor is the name for the virtualization layer。

 The software that does virtualization is called the hyperros。

So this picture shows us two types of hardware virtualization。

 and they have some part game that got type1 and 2 per number。Yeah meaning。

 but let's just go over that。So the first picture here its going to type one hypervisor。

So in this case， when you start your machine。The OS is not the thing that bootss up the hypervisor that starts up so the hypervisor takes the role of an OS kernel in the type 1 hypervis。

Okay， so it就 power up。There is no OS thats booting up your OS is the hypervisor is essentially functioning as the o so it is going to start up and then once you start up your type of hypervisor you can start multiple one or more virtual machines and in that example you see two virtual machines。

 one called Windows and one called Linux us。So each virtual machine is a full emulation of the underlying hardware remember this is native virtualization。

 so you are doing x86 on x86 or something equivalent so each of those virtual machine presents abstraction of a full x86 in。

Mishhi， and then you can boot an os on it， and then you can run applications on that box。

In this case， you are actually two oss that are running side by side。

 you can have as many as you want。They don't have to be the same either。

So you can Linux coexisting in Windows or whatever runs on an x and6 can be put inside a option。30。

Most likely， you never encountered a type1 hypervisor unless you actually work with something to do with servers。

Because this technology is only used ins， they're not used on desktops or anything like that。

Cloud computing essentially runs on Ton hypervissors。

 so essentially when you go to a cloud provider and say give me a machine。

 they are not giving a physical machine。And essentially making a virtual machine for you and giving it to you。

 and you can put whatever words you want on it。And the reason they。Those is twofold。

 One is they dot want give some third party customer access to a machine， physical machine。

Because then they lose control of the physical， but if you give access to virtual machine。

They still control the hypervisor。 They can shut down the Vm if it miss beams or do whatever they need。

 They still control them。That's one the second reason to use alviss is your machines maybe may have lots of resources that an application may not need。

 so you can carve it up into smaller units by making virtual machines or virtual servers。

So that means that。One machine can only menu only maybe one or two course or some smaller amount of RA。

 you don't have to take an entire machine and dedicate it for a small applicant you can run multiple virtual servers or virtual machines on that physical server and get better multixing of resources。

本第一关系。Here there are examples of dataers。GM has some ESX so what is an example of a typepo。

We actually used heard of theX。The second picture is called a type 2 hypervisor one thing I did。

For forgot to mention is when an OS runs inside a virtual machine。

 it's called a guest operating system or a guest to us。So that's a term you want to keep in mind。

 So in this case， there are two guest voices。Windows and，1 each。我 machine of送。The type 2 hypervissor。

Essentially， you have a forced os that is actually running on the machine。

 you will see that when the machine boots up， it just boots up a normal os。

They just probably the host operators buildings。The virtualization layer actually runs as an application on top of this post operating system。

And that hypervissor， which is now called a type 2 hypervissor because it is not running on bare metal type 1 hypervissors run on bare metal。

Type2 hypervissors run on a normal。 They don't run on bare。So tied to hypervisors。

Essentially run on a host of， they also can create multiple virtual machines。

 and in each of those res you can learn whatever o you want。So that's called type 2。

To a loose case of a type polite。最好的。For them。Well your virtual boxes are tied to hypervisor because it's running on your machine。

 which has some us extra bo to us。Rchel boxox is diapervisor。You create a VM。

 youre running Minex inside that VM Minix in this case is the guest operating system so there are two voice running one inside a VM1 natively on the machine。

在听。So now。In both cases， regardless of your。Each type when hypovis came。

Still always start at the same time。Good question。 So question is in a time hypervisor and both Os is run at the same time。

So this is very so what typeon hypervisor does is what an OS would do so it has a scheduler。

Just as OS has a CPU scheduler， so does a type1 hypervisor in this case。

 a type1 hypervisor is scheduling an entire VM。Not just a process。

So to answer your question of can they actually run in parallel。

 it depends on the hardware right So the hardware has。The hardwareware has multiple courses。个女孩。MeM1。

业读。I oneプバイ。You could say this VM1 essentially gets two cores and this VM2 gets two dedicated cores。

In this case， you are going to get two parallelism because this OSs here。

I want to execute on these processors。And this was。

This windows is going to execute on those bad processes。 So you'll get true parallelism。

 This is similar or you have two processes that run or two cores， and you get two parallel。So yes。

 the answer is yes， even if you have only one core。

 the hypervisor would schedule these just as you did CPU scheduling is essentially doing the same thing itll give sometimes less to this VM then it's going to give sometimes less to that VM and so on So you'll get concurrency even on a single core but you have multiple course you'll get value。

好对。すね。So that they have just。Okay， so there is a question about how the networking works。

 I have a small slide on that data。 but let me explain this our picture here。

So this is a physical machine。This physical machine has an Internet card。

That's called the physical myth。Physical network interface the physical。

Each of the VMs is emulating an entire machine in software。You're emulating a processor。

 You're emulating this。 You're also going to emulate a software。You're going to I and software。

So to the OS running here， it actually sees that network interfacefiscade as its actual network。

 the OS doesn't know by the way it's running inside a virtual machine。

 it just think its running on a normal machine。Doesn't actually know its running in a ear。

 So it expects a ni it sees a except that this is just a software simulation of a ni， not a real。

Now when you send a packet on this， if you want to send some data on this network interface card。

 you can actually send it up you can just simulate sending it up so what is going to happen is the hypervisor is going to take these two network interface cards and theyre going to map them onto the physical card。

So you have want to multiple X a network multiple logical mixs onto one physical。

And you can also specify things like if this is a gigabit card。

 because this ni gets five and half backward then that ni gets half the。

This is where things like lottery schedulers actually get used。So you can give them weights。

 you can give them lot rate， they can say this gets half that gets half， this gets a third。

 that gets too and you can do whatever you want， and then the maximum bandwidth you're going to get is whatever you say。

So the basic idea is you going take your logical legs and vertical。也是不是的。

A doctoring termology is the guest and most of us only come the picture when there is type to supervisor。

이유 대원해볼 거에서 모든。question is， are the guest and host voices are the only present in type 2 or are they also present in type 1 right？

You will see that there is no guest OSs or type 1 hyperbo。As I said。

 when you boot your machine is the hypervisor that bootss up there is no other OS that boots up in this case when you boot your machine Windows or Mac is going to OSs is going to boot and then you're going to run virtual bo as an application in this case there is no such thing What boots is actually the virtualization software so it functions like a OS but it's not a general purpose OSs it's a special purpose OSs that's only designed to run virtual machines so you can't run your Chrome or browser on top of it。

The only thing you can run is a virtual mission So think of a Ton hypervisor as a very special curve that boots up when your machine boots up that only designed to run virtual mission。

So in other words， there is no guest OSs， hypervisor is the OSMS。If we don't call it a gasto。

 we call it hyper。But in a normal scenario where you run this in a desktop。

 you are actually are two osis to the guest and the host room we have more than one guestroom。

This be an question。So now we'll talk about how type 1 virtualization works。😔。

And we talk about how type 2 virtualization work。 And for now， I'm only going to show you。

How the processor ammunition is going to work。Maybe in lecture too， which is that。

Every processor that you have has at least two modes of operation， a user mode and a kernel mode。

 and this is specified using a bit。And in user mode， certain instructions are disallowed。

Those are essentially what are privileged operation。

 We only trust the permit to perform those operations。

 So those operations are only allowed in permanent mode。

When the bit is set to kernel mode its assumed that the kernel is actually executing and everything is a allowed and the bit is turned off。

 we assume that a user process is executing and some things are not allowed。

 some assembling instructions are not allowed。This is something we mentioned some time ago that is a concept that we need to keep in mind It will assume that the CPU essentially supports a kernel mode and a user mode in Intel world。

 these are called protection rates。A user mode is essentially ring 3 and kernel mode is ring 0。

 There are my intermediate privilege levels， which for now we are going to ignore。

 I will just assume that you have user mode and your kernel mode。

So we are going to now define two things， one is something called sensitive instructions。

 these are the instructions that we trust the permanent entity。

So those are all the instructions that run in kernel mode alone。

 so every instruction that only runs in kernel mode is going to be referred to as a sensitive instruction。

 So heart is a sensitive instruction I is a sensitive instruction changing my page tables for memory mapping sensitive。

So all these are un sensitiveensitive， only an in。You also have another town here。

 which you have going to。The which are called privileges and privilege instructions are those that cause trap。

Divide by zero， et cetera。Access some out of rain memory segmentation for also a trap。

 anything that causes a trap is called a privilege instruction。Now， theres a result here。

 it says type 1 virtualization is only possible on those processors where the sensitive instructions are also privileged。

 which means if you execute a sensitive instruction in user space。

 it should cause a trap saying that's an error。If your processor actually supports that property。

 only then can you implement type for virtualization， otherwise you cannot。

So you say what does this even mean， why do I need sensitive instructions to cause traps in user space and so let's go a little bit deeper and try to understand what virtualization is trying to do。

So I'm going to draw a simple picture here。pictureture is。

So this first picture just shows you a normal PC。My runs and O， O is running up。

W is in control of everything。It can do whatever it wants。That's why it runs in kernelal Mo。

 It has full access to whatever it needs to do。That's the general working assumption。

 O a school control of the machine。Now， let's look at this picture。 This is our type 1 hypervisor。

ATon hypervisor is running on this machine。 Here you have one Vm。Which is a guest choice。

As far as the guest voice is concerned， it doesn't even know it's running on a virtual mission。

 it just thinks it's running on a physical mission。

 so it thinks it can do whatever it wants like normally， it will when it runs on a normal piece。

So it can essentially do part or whatever it。Except that when in this world。

 you only trust the type 1 hypervisor， the type 1 hypervisor is the only thing that' is actually running in kernel mode that gets to us is actually being run in user mode。

Because we don't trust the guest os to do whatever they want。 there could be more than one of them。

 So if this guest choice is given access to everything。

 it can go and trample on some other guest tours。 So guest voices have less privileges than they normally do when they actually put on bareme。

So assuming you understand that in a type1 hypervisor， the guest O。

 although 8 things it can do whatever it wants and execute sensitive instruction in the reality。

 it's not allowed to do。Ton hypervisor is the only trusted piece of software。

 gas devices are treated almost like user processes where they are even less privileges。

I in this world。Think about what is going to happen if this guest always tries to execute a sensitive instruction because it thinks that it can do it。

That guest to us will be running in user mode。Not good能。not a real lowest。I providess perspective。

 is the real goals。So if this guest to tries to execute sensitive instruction in user mode。

 what is good？それ。Typically the processor will disallow it because the user mold weight is on。

 so you can't do that。So now the West can no longer do its job。It things it can do whatever it wants。

 A processor is not letting it execute certain instruction， yet we want to let that happen。I other。

 the West can function。As it normally does， So what do we do？

We don't trust the guest to to execute sensitive instruction。 it' is running in user mor。

 you cannot actually execute it even if it wants to。So we've got to find a way to make this work。

Was a club。This is simulate food。same calls to simulate the calls。

 but who's going to simulate the calls。Theres no whole story there。

So only thing we trust is the hypervisor， so if the guest to us wants to do something sensitive。

 the only way to make this work is ask the hypervisor to do it for you。

This is exactly what happens in a system called We don't trust the process to do something。

 So we make a system call it causes a trap。 The OSs does the work for you。

You want the same thing to happen。You want to essentially make the guest OSs do something。

 but have the hypervisor do it for you except that we can't change the guest tos code。

 We are running it unmodified。 It is still executing its sensitive instruction as if nothing has changed。

So you want to do this transparently。The way we are going to do it is by enforcing this property。

 we are going to say all the sensitive instruction， if they execute and use mode。

 they should cause a trap。So in this case， if they cause a trap that going to go to the hypervisor。

 hypervisor will say the OS wants to execute some instruction。

 let me do it for the OS it will execute just as you execute system calls。

 same thing is going to happen。But you do it transparent。

 the who has never actually asked the Ivisor to do anything for。

It just executed a instruction caused the trap， went to the hypervisor， hypervisor did it。

So this is a very important property the harderline has to enforce if this property is not true on a particular processor。

 you can't implement this because all of that sensitive instructions will start getting ignored。

In fact， Intel X8 6 did not have its problem。It would simply ignore all sensitive instructions in user mode if you called heart and user mode。

 it would just ignore it， it would look like a no opportunity。

Until recently this was true so you wouldn't terminate the program you would just ignore think that's a sensitive instruction you can't do it so I'm just don't ignore it so you just ignore it so you couldn't have the gas to as cause trap because the OS processor would just ignore it so until new versions of exc processor came out you couldn't natively implement type 1 hypervisors or Intel hardware。

So what happened subsequently Intel actually added specific hardware support to support virtualization an Intel world that is called VT okay so if you actually go and muck it around with a bias on your processor。

 you will see that it has something called VT support， VT times for virtualization。

AMD has something called SVM， it does the same thing。

 so what these two technologies do is essentially they allow you to decide whether you want sensitive instructions to cause a trap。

In fact， they have a big mass that allow you to set saying when these instructions。

 this is one bit for every instruction and you said for these instructions， return turn the。

valuealue of those bits to be one and you execute those instructions in user mode they'll cause it。

 That's what the V technology so you can turn it on or off its off。

 It looks like the old Intel processor where sensitive instructions are ignored you turn it on for all the sensitive instruction and it will cause it and then you can actually implement。

対こないト。That here so this is better shown in a picture which I probably should have shown first。

 which is here。So you have a process， the process makes them called。Basically walk the guest to us。

So the guest to us is going to do something if it executes a sensitive instruction。

 it's going to cause a trap， a trap will cause the hypervisor to run and the hypervisor will actually execute an instruction when you go back。

Just to as an industrial as just think that actually did something where there the advertiser really。

So in this case， the hypervisor takes on the security of the system。

 but the OS Excel is running in user hold。hypervisor is acting like what a kernel would normally do。

 it allocates memory for the VM， it schedules them。

 it does not let trust the test to do something for by themselves。路的申层。

Having said that we still need a wait or distinguish between the guest and user processes。

 we can't say that the guest service is as interested as a user process because it is of course more familiar than the user process and this is where those other protection levels come in。

So。The ring zero is most preval， only the hypervisor runss。

Ring three least privilege user processes and in you have two other rings R one and ring two so you can run your guest overseas somewhere in the middle which gives them a little more privilege。

They are allowed to do few more things that the user process would do。

 So the true user process in that V if it calls a sensitive instruction。

 you can ignore it because that is running in ring3， but in ring2。

 you can turn mey on and say maybe I will actually have these instructions cause a trap because the guest choices。

So you can distinguish between user processes and a guest to us。

 even though neither of them are actually producing。Yes question。在院里。是。我关的。也是我是。

As is the hypervissor simulating hardware it is。It is not simulating processors because you are running the same processor。

 So all the code runs natively， but you might have to simulate that picture I you earlier a network interface but some peripherals have to be。

But not process。Can the big bag not be handled in the hypervisor， not the hardware， you could。

 but the processor has to support it。Because it is actually the instructions are being executed on a processor。

The processor does not cause a trap。😔，And you ignore it。So it is a hardware feature。

 not a hypervisor。Because learning code is actually a machine code that's executing on CPU。

So you want your sensitive instructions that the user more isect to guest。My not。

See you more to on board and youll need。是我。Of the。はいそ。First of all， most code is going to run。

They nativeative， there is no translation， nothing is up。

The only problem is when the guest co is running sensitive instruction。

 that's the only time you actually want to do something special。

That is those are the instructions that cause a crack and then essentially a trap under where flag in executing a system。

You want do whatever it。Yes to。There's only time men essentially。

Execute those privilege instruction in the I words。 Otherwise， everything else is running native。

Theres no o， as that's way， there's no performance。Yeah公司。But in the second there is I the hard。

In what situation would？Okay， so em what you are asking about the last bullet so emulating the hardware and that depends on so suppose you want to write to this matter of file。

In the words nice work。That file that disk might actually be an emulated device。

 it' is not a real disk。 So for example， in virtual box you have files that act as a virtual disk。

So you still want that file to look like a disk as far as the OSs is concerned。

 so that is where some of this emulation comes in。To save is true of the network interface card on many other devices that emulate。

Any other questions yes。で question。M really。YeahSo I you come to that， it basically does。

You're going to essentially make look have a spa， something like a switch where you multiplexing multiple mixs onto one physical mix。

So， there are multiple things in network virtualization。 One is。

 how do you take a single ethernet guidance。And then share it across multiple views。 That's one。

 The second is all the things that go with IP addressing and so on that somewhat independent if it。

P has to be given an I address as well。 Thats our networking works right so that can be handled in many different ways。

 So you can essentially have a map。Inside your。Machine that gives it 192 addresses that are not real addresses。

 and then theyre multixed on the physical end。 exactly how your home router gives you IP addresses that are。

不来有个 idea点。You can also set up your configuration so that your VM actually is quite complicated it come to that in a little bit but there are many things that how you emulate a Ethernet device how to IP addressing。

 how to a。So type 2 hyperviss， How does that work。But in this case。I've if you go back three slides。

 And so here we are looking at how virtual box works and so on。

So here we have a post operating system that actually is the lowest。

 so there's a real lowest running。Then there is a hypervisor run， which we call a typepo hyper。

 The guest runs inside the hyper。So we have the same problem as before。

 The guest owner does not know it's running in a virtual machine。

 It thinks it's running in the physical machine， So it is going to execute sensitive instructions。

In this case， our previous idea no longer works because a type to hypervisor is simply an application。

 not even not even behaving like a OS as it did in the first case。

So just a typical application like any other could be running besides a mail application in a browser and so on。

So we need a different technique for us to allow the guest to us to execute sensitive instructions and make it work。

So now what is that technique， So youre to solve from。技术底夫系做。So we are tied to hyperviss。

 we are going to result a binary translation。So what the type 2 hypervisor does is before the OS starts executing some code is going to start scanning what the OS might execute。

 it is going to start scanning assembly instruction specifically。

And every time it actually sees a sensitive instruction。

 it is going to replace that with a function plot。In。In binary， that sort do in binary translation。

 say if you want to do IO， I replace that with a function。

So when the Os actually starts executing that court， when it comes to executing a sensitive。

