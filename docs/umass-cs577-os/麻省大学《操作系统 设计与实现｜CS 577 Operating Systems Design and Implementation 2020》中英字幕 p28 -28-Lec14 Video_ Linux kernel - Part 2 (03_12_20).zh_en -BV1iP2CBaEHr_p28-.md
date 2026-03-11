# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p28 -28-Lec14 Video_ Linux kernel - Part 2 (03_12_20).zh_en -BV1iP2CBaEHr_p28-

还有没问的。I always hope that this thing works when I start especially today。

So were going to go on with the Linuxux vector， as Bran said， there would be an evi。

Strucs for people。Could not make it toate so you don not where you would get all the information。

 we' do our best to make this。So。Last time when we started talking about Linux。

 we have covered basically roughly four chapters in the book。啊。The one was the introduction。

Like the first two introduction chapters， then we covered also process management。

And we covered the process of getting。These were not very different in many ways from what you have studied in Medis。

We have also hinted that there is。Data structures， kernel data structures that you can use in minuss。

And we have， basically。We didn't go through them， but we just mentioned some of those that are there like double linkeded list。

And so on so today we're going to build on what we have covered。

 the first part of the lecture might be a little bit reluctantund in some sense because the is schools is basically very similar in many ways。

Some very might。Some very minute changes between the Min and Linux differences。

But then we're going to take a much deeper dive into the interrupt handling mechanism that you have not covered the mimics almost。

 I mean， you're just touch opponent。And then we are going to actually talk about top halves and bottom halves。

So。System calls and the inuxes which is the only interface between user and。The extra Carolina。

There is no way， it's not like in Venex where you have the servers and so on。

That the only way between you to go from user space to kernel space as a user is via system goes。

 as a single command layer between the user and the kernel。

 almost everybody now tries to be compliant with physicsOSs。Theux tries to beco also with another。

Standard SUS V， the Uni specification。Lenux has been trying to minimize the number of system pools as much as they can。

Are there reasons for that They going to quickly go through them。

All system code and Linux need to return a type dunk。Each system pool has a number just like Min。

Nothinging hurt cha。呃。You have， it's basically， it's mostly architecture dependent because there are lots of things that requires understanding the architecture。

 so you have them and this is underscore cool underscoreed。Under score tables。

Where you have all the entries for the Cis now the difference between one of the major differences between nano and minutes。

Is that Linux had system calls per server right so each server had implemented its own system calls and exposed it to the users and NO you do not have that you just have whatever the number is today。

 number of system calls and they are all implemented short of like，And the same table。I mean。

 they are all defined at the same table， not implemented at the same table。the cool。

The cool stack is very similar， so you go from the user space where you have the you could print on C or Python or something that talks to basically a library。

Usually see library green。Where you call the print and the sea library and the print and the sea library actually pull right。

In the C library。Right basically correct to a device and right basically is。

Has one one map into a system group， so you go them to the current level。O。System code definition。

 this is how you define the system code ci Cisco underscore defined zero， okay。

 zero here means that you're having zero。Zero parameters。Okay。啊嗯。For example。呃。Basically。

 this is a system goal that returns task ID。本说 number。のたし。So this is， you don't need。

Any parameters for this you just need to get Pigi， basically， it's the get piegi。Cool systemem cool。

 you don't need any parameters for that to get PID of your current course。

And each system pool has a defined handler， very similar to minutes。

 where you actually have the handleer is actually what does the actual work。Okay。嗯。

The way that system codes work in Linux is that system code results in an inter。

 they actually result in an exception。People use the two terms interchangeable。

As we are going to say in a couple of slides， interrupts and Linuxux are basically hardware and drops。

 they need to be stemming coming from the source should be hardware device。

 so it causes an exception or a trap。And the control is switched to the current speech。Okay。You have。

A certain number that is defined for the exception for system goals。

For needle and that's 128 Okay that's the interrupt number so all system pools have this interrupt number once you go there okay then you start basically looking at the input at the parameters of your system cool to actually know what system code are you actually using。

O。嗯。The system called handler for the general system handler that actually takes that system cool is cool system underscore。

This is where you actually try to go to the different system goals that you have。

It's architecture dependent， obviously。Well next 86。

This system code has actually implemented an entry under  score64 with S， it's a simply code。

I answer it actually tries to go and beat registers and stuff。

You pass the actual kernel to the actual kernel， the system cool number via the EX register。

 one of the general registers in X86， that's how we actually pass the number。Okay。

And this is done in user space， so basically part of what your compiler does。

languagegu if you have an interpreted language， part what is being done is that you have the library。

 the system called library， musical changing theEX。Register to actually go into the correct。Asant部。

How to prevent a system called Linux？This is actually a link to a pretty recent tutorial because this has changed over the years and basically this is for 2019。

 so it could work。It's a little bit different compared to minutes。

 but not the whole looked different。So now why not to implement the system cool。

 so we you guys have regret the system cool as part of your lab one， right？But there are many。

 many reasons for you never to implement the extra system code and and em manage if it ever picks up and becomes a system that everybody uses。

So first of all， you need the system cool number。That number when， if it's my own。Carlonel。

 if it's my own kernel version， if I'm obtain my own kernel， then I can just like add some number。

 you know。But then if you actually want to implement a system call that actually does anything。

 so if you're a hardware company trying to add a system cool to the Nis，To the main Linux。K能 okay。

You cannot just like go。GitHub and push your changes and say， okay。

 I just added a system pool with number 500 it doesn't work that way so you need basically somebody to assign that to you and that's basically that usually is quite hard。

嗯。The other reason is that once you have system cool， you do not remove a system cool。

 do you know why？F。Exactly backwards of compatibility。

 you cannot just basically start adding some cool in random and you decide that， oh。

 I'm just removing them。And that's one of the main reasons that Linux tries to keep its system calls to a real absolute low number compared to Windows。

 which actually has thousands of system goals。Okay。

So you don't want to break user space applications and becoming ten。

Now each architecture needs to separately register the syncola port。

 one of the main reasons that we run Linux is that it's。Architecture independent。

 it turns most on anything。 So if you have， if you have a small device or a large device， go to your。

Good to run， basically without caring about the architecture。So you're only the respberry price。

 but you run also one of the big fast servers， you run it in sum。On some microsystems。

 and it covers everything， right？So if you change one number somewhere in some architecture。

 you want to make sure that you can have that theme system pool available for all other architectures。

 which is a pain。O。呃。And basically， system codes are not easily used from scripture， I mean。

 now you have added your system code， it's not like the system code exists nowhere。

 you actually need it to add it to some。Language library， right like the C library。

 otherwise it's completely useless， nobody's going to code and system code， right？啊。Basically。

 maintenance becomes an issue because we have the numbers and basically the system code is almost always an overdue。

For anything that's here going， so in reality， nobody implementss the pose， accept and laps。我。

The other alternative is to actually build what is called the Linuxux kernel module and talk about that later as basically。

Linux way the Linux way of actually adding servers short of， it's not for adding servers。

 but it's for basically extending the kernel with some modularity。

 some form of modularity where you actually hook up code to the kernel using a simple command line that is mono basically without even touching the internal kernel code。

Okay， so that's something that we are hoping to be able to cover。剖福利。

Now to the main meat of this lecture， that basically interrupts an interrupt。Okay。So why it？

Basically， you have these very fast。Running chips， processors， basically that front。

That can run hundreds of millions of instructions。Or millions of instructions。And a second， right？

In the very short time you have this very enormous capability。

 most hardware it does not run at the same clockak speed of the boost。

So you want something you want to be able to。Basically。

Make the processor talk to all the other very slow devices。And that way it basically interrupts。

We're actually two ways to do it， one of them is using trucks， the other one is using pullingen。

Most hardware that exists somewhere earth worse with terms were basically once the hardware is ready。

ItS sends an electronic signal on the chip to the processor saying that I'm ready okay？As a hardware。

Very few。Hardware。Runs with pullinging pullinging basically means that that your processor will every some。

Designated time units， go and ask。The对。The hardware， if there's something ready for it。

there's something for the hard work that she processs。ok。So。

The good thing about interrupt is that enables hardware signal to the processor。

 so you have the keyboard， you have the mouse， you have your memory， chip， all these things。

 there are ways go compared to the processor， your network and so on so you have this way of making each card。

 every peripheral， everything， basically pull or sorry。

 interrupt the processor and tell it that there's something running out for it。

The hardware then does not need to。We don't need to try to synchronize between the different hardware chips。

 right because that would be hopeful， basically trying to synchronize two computers。

 two processors is' already harding now trying to synchronize your entire。

Computer with 100 subsystems， it's just never going to work。So everything works at synchronous now。

 electronic signals going from hardware to hardware to hardware and the processor that is basically called the interrupt controller。

 the interrupt controller is a very simple chip。A chip that basically has a vector table has a table that basically says that if I get a signal in this pin。

 then's this， if I get a signal in that pin， it's that。So it's a very simple。Certainir。So I'm that。

That chip enables the processor to basically talk to all kinds of hardware that the processor knows it exists or that the processor does not know it ever existed。

 so in many cases you have a laptop， you have a computer and then there's this nice piece of equipment that comes out new。

 right？It's basically something that was not there when your computer was made。

 but still you can't actually run it on your computer via USB or using something different。嗯。

So each render around。Will have unique number， unique value Now this take this with a grain of soap。

In reality， not each interrupt has a number。And that's that's。He part of this picture？

And these values are often cool， they interrupted with the higharchs。

The IRQ mines is basically slight that this software is like very slow as compared to the hardware and that is why we sort of do the fold rather than the push so but like why is it the case？

No， the hardware， most hardware is much slower than the processorer。喂。If you continue poll。

If youre basically to sit down and have your poster every five milliseconds， go un pull the keyboard。

 did he type anything， then maybe I'm not typing like I'm doing right now and then the poster has to go。

Cont switching because if it's boringing， then it needs to go on ask something about something right so it needs to ask the keyboard if I'm typing right now。

 which I'm not。RightSo with forces or resources， that's why you want't interrupt that basically push。

Push notifications are deposit。So each RrQ line is the same。Fue。IRQ0。

 the number zero is the timer interrupt， which is basically your clock， your CPU clock。

All got Q1 is the keyboard of interrupt dropped。So。It goes like that。There are a bunch of numbers。O。

Unlike I said schools， not all IRQ numbers are defined。

 so you have basically a range ofRQ numbers that are just not defined。

there's just like some member that gets assigned dynamically to different hardware。

 and this enables basically the processor or your computer to talk to any hardware。

Because if we have。The number assigned to each inter。Then I have already defined that this is。

This number is for the keyboard， that number is for the memory， that number is for the mouse。

 but then there are 10，000 types of mice now that each one of them many of them acquired very specialized drivers because they have all sorts of different buttons that do all sorts of weird things。

 you have 10，000 keyboard layouts， you have Chinese keyboards， you have the keyboards。

 you have Hebw keyboards， I mean you cannot just like define everything right away。

 you need to actually have the system。あ。Get these with the drivers。

And another example is that interrupt associated with the devices when the PCI bus are dynamically assigned。

 so you have a PCI bus and you have basically a range for the PCI bus。

Components that you're going to connect。嗯。The important notion is that the specific interrupt is going to be associated with。

A specific device， and we'll see how this is done。So the difference between interrupts and exceptions I sort of said that already basically interrupts our hardware。

Exceptions are software so when you have。the schools， that's the software， right？

Most people would just call everything in drugss。So enter our timers。

The concept is very similar to this is code handle。

OkayEach interrupt each device generates an interrupt that is basically associated to an interrupt handle so you need to that's basically your device driver so that is actually what you're doing when you install your device drivers just。

Teaching your processor how to handle dens。Okay。Besides all the other things， right。

 but the device driver is in essence stack。嗯。Basically。This enables the processor。To again。

 communicate with any device， but enables you also to basically update the drivers。

Easily because now what you're going to try to do when you get a new hardware。

I that you're going to install the new driver， but then if you want to update it。

 you should just be able to update the tender， basically telling the processor that now this is what。

是吧。What need to be done？Dvicice drivers can be implemented as in the kernel， many of them are。

But also can be implemented as an L and you external with you。Enter up handle or return C。

 so they are not as。There is an interface obviously with assemblyly。

Andter panthers in general are just seat。They run in a special kernel context。

 which is called the interrupt context。 It's different from the user context from the process context。

 It's different from the kernel context。 It's an interrupt context。Okay。The handle is atomic。

And thus cannot block。So you want your entire handler to just run from the beginning to the end。喂。嗯然。

Thus， this must be very quick because if you have something that is atomic running into the kernelmal。

 that basically means that you know what。A the device driver that goes headwire can just like make your entire computer not reply to anything because you it's very slow。

 it's not blocking and very slow。嗯。Even if your device driver works very well。

 but you still have things such as attending internet card that just produces。A lot。

Data packets that needs processing。It requires copying and requires all sorts of things and then all of a sudden。

The faster now devices like the ni parts， can actually hug your entire post。

So the new way of actually solving that is that all device drivers are divided into two houses。的。

pass and嗰同。Sounds very， you know。Intuitive， right？So。

The top half is basically the first part of the interrupt handle。

 and it is the real interrupt handle that the kernelel breeze will。

 and this should be basically things that you absolutely need to do。Right。

Everything that you absolutely do not need to do right now can wait。So， basically。

You run an interrupt handler upon receipt。Okay， and it's not looking。So it just run。Untilm it's done。

And you perform only time critical work， time critical work should be。

That you add the sending device that you have received that interrupt， so you're going to process it。

And that you basically research。The hardware is so that you can receive a new interrupt on that same pen。

 because otherwise， if you do not reset your hardware。

 then all interrupt so if you're typing and they type。

AndMy interruptive handler does not actually handle that， then I cannot type anymore until basically。

And that that。The hardware is re。The bottom half you do the rest of him。

So let's go to the network only your time critical。In the previous slide。

 it is given that as noishment on receiving the interpret rate。 Yes。

 so is that only the time period the process is there something else also which happens。

 There can be other things that are time critical。 Well actually give examples。好。

So there can be other things and we actually say when you should use what when you should put your code in the bottom half of when。

那个と发。That's。So basically you have a network card that receives packets from the network？

Then the first thing that you should do is that you alert the kernel of the availability of these packets via an interrupt basically。

Now the current response by executing the register interrupt for the network card。

They interrupt runs， so they interrupt and runs。And adds to the ni that， OK。

 I'm processing this data。And now this is what you were asking about。

So in this case the network interface card， it has a network buffer， right？

The hardware and I took buffer。If you do not copy the data from that network buffer to your memory。

Then what is going to happen is that you're going to overflow the buffer。

So once you receive that interrupt， then it's time critical for you to actually empty。

The buffer copy everything into the main memory so that basically you can。

Receive more network network packets。Does this only work？Copying the data without walking。Thatdirect。

That works because exactly so because you have direct memory access。

 so now that that's exactly why were saying that this can be in the background。

 obviously if you do not have the direct memory access。

 which is like a very essential thing now for most computers to actually perform。

 then you're sort of school because you have to wait until everything gets copd。Otherwise。

 other you know。You lose the data， so it works actually partially because of the。Dir memory yeah。

Okay。So。So basically the kernel now， when you have an interrupt， your interrupt tenderder acts。

Copy data。Or gives the order to copy data and just what you know。It doesn't do anything after that。

And then。Basically it's done， it clears the hardware and you can overwrite whatever is in the buffer right now。

O。There are new things when it comes to this， there's something that's called DPDK。

Which basically tries to even。You know circumvent going from the kernel whenever you receive it because you have DMA because you have direct memory X DPK。

 what tries to do is basically tries to minimize even the kernel requirement to handle the listener to just play go。

Yes。Magically。ょと面な。Okay。So。Each device is associated with one。With one。Driver。Okay。

Each interrupt based driver registers 100 only and they have interrupted based because if you have a pullinging based system for some reason。

 very few components work with polling。For this occasions。But basically。

 almost all the things that you deal with registers and interruptop tender。Okay。On success。

 I' this basically。Don using something that's called request underscore RRQ defined then slash s interrupt H most of the definitions for interrupt handling is done and on success the request RQ return 0 basically saying that okay。

 I have registered this interrupt handle to the current now， so now the device can run。Okay。

The common errors。EBy， which basically says that your IRQ is already in used。

 which basically means that well， this line or this number is already in use。

This is how this thing looks like so you have。The request IRQ。You you define an interrupt number。

 okay？And then。You have some flags。 Talk about the flags in a little while。And you have a name。Okay。

 you have actually sorry you have the actual handler， which is a pointer for the actual code。Okay。

 so for the flats。You have the equivalent handler that points to the actual code。

You have a name for that device and that's basically if you're looking or if you're looking through your D message。

 it basically to where you have all your logs on stuff， you'll see the name of the device。

And then you have something I called that will talk a little bit about it when we talk about it。So。

 flats。So I started by telling you that。When you have an interrupt， everything gets book。In reality。

 you cant actually control that behavior。So you have flag。

 one of the flags that you define when you actually attach a device when you attach a handler。Okay。

 is the IRQ disabled client？And that basically instructs the kernel to do one of two things if you have it as set。

Okay， that means that everything all drugss are now blocked。Nothing worse。

 so as you have it set for your device driver， for your keyboard。

 that is basically telling your computers that if you have an interrupt from my keyboard。

 everything else stops， nothing waits。Okay， no inters will care between them。

When I'm typing and so on。Okay， so for most。If you have it， consent。that means that， well。

 everything else runs， so network packet， my network card can basically interrupt。卖低平。But， you know。

No two key strokes will basically over each other。So you only dis able interrupts that earn like you。

So which one do you think is used more？谁？Yes， the second one。

 basically because you want your computer to work， right？The other one is the IR QF。

Actually that question of the one， the example？Just what we have。

TheMost things that I would think are looking at time， okay， so the time is really。 Yeah， I mean。

 I mean， basically things that are complete that you completely do not want anything to through。

And that's that's basically that this would be interrupt。That。for example。

 if I think also some of the memory interrupts are like that。哦。So there are very few to run that。

 but here's the thing you can't actually define that。So basically if you're writing your own driver。

 it's up to you to actually set it in which way you think now if your driver will be accepted in the main Nos streamline。

 that's a different thing。Probably people will frown a point， but yet again。

 most drivers do not come。And show you download them from some。Weird place， right。

 so if you don't lose somewhere weird drivers from somewhere weird place that nobody has looked at。

那女。Device。ADri designer decided that I'm setting this whatever。So I mean。

 that's why you shouldn't go order out there。Go five drivers。

The second one is actually interesting art the RQF timer， and that's basically。

The flag that tells the system if it can use。Meta data from this interrupt to actually as enpropy as basically an input to its random number generator。

 basically there are no two random numbers generators。

 but still we need random number generators for all sorts of different security purposes。

 privacy purposes， including in the kernel and including in some of the tripp to libraries in the kernel。

So to get these random numbers， that currently needs to do something that is more brilliant than just trying to。

Do use the python and run a number three which is just cap right so what it does is that interrupts happen at any time of the day。

 right？When you're designing your device driver， you can actually tell the car that， oh， by the way。

 you can use， for example， the time when my interrupt happened to actually。But as。

As food for your random numbers today。And you can use all sorts of different metadata on the interrupt handle。

 So this is basically something that you're。Helping the colons to be better with。Okay。Now， if you're。

System， for some reason， has interrupts that happen at certain times of believe。Example。

 some of the systems that do back。Okay。They start exactly at the same time of day every day right。

 you should not be setting that for that flag for this sometimes because then you're basically。

Messing up here。Number。Dog RQ actually and depth。That is actually one of the parameters that we talked about。

 the I youF sure is a flag that actually enables。Different， multiple。Devices。是都。

So it's enabled multiple devices to actually share。The same interrupt number。

We'll talk a little bit about sharing terms。啊。I actually messed up two things。

 So Sam for randomum is the one thats just random number generator， I'm sorry just。Meest up these。

The other one actually。Spifies that this handler is for the actual system time。

 I so it's something that is probably going to be very high priority for the system to run right away。

确rry about。So。The entranceancy and inter tenders。嗯。So when one of your interrupter。

It basically masks all other interrupts of the same coin， no matter what。How do we sell the flag？

This is basically to prevent two interrupts of the same kind to overwride each other。

 so you wouldn't basically end up having interrupt。The same term overriding the second。

Happening at two times after each other， one of them over to the other。

Some of the drops actually require mask and cool drops， as we said。嗯。

The same interrupt tender is never invoked concurency。You never have it on two processors。

 you have a multiprocessor system。You have two processorors， they're are going to have it。

Happening in problem in two different。嗯。This basically makes striking interrupts much easier for the current of them。

They not need as a driver， the developer to think about concurrency issues。

So you just know that if that happens， nothing that interrupt will not happen again until。

It's not basic。O。哪个。So why interrupt？As we said， we have this kind of。Of这。Right。

That basically knee has a certain number of fins。And this is the maximum number of interrupt that you're going to support。

Okay。So since you have a limited number of pen pins and you have a infinite number of devices that you can attach。

Then you want to wait to be able to actually overbook these pen。

And the way that you do with that is using interpretion。喂。And。For inter sharing to work。

 you need the hardware to actually support that。 So you need the hardware to understand that。

Is sharing the drop handler number。So when when so the。And you need the software。

 the kernel basically to know that too。So the way that this works is that once the currental gets。

Thator upcumber， save5。Say that this is shared between five different devices。

The carrier should be able to go on hold each of these devices。

To to check which one is raising that control。So you need hardware support。That name was the colonel。

To actually pull the device， if it has raised an interoper。

 it's a very simple modification in terms of ay。Typically， an extra register for you。Not much。

but it allows you to basically support an infinite number of devices because all of a sudden each device can basically say different thing obviously if you're sharing and you're pulling all like 10。

000 devices then when interacts no longer makes sense， but luckily nobody really runs 10。

000 devices on a single machine， I mean nobody does that。And this is how the interrupt flow works。

 so you have two devices， they share the same IQ number， okay。You basically go to the pick。

 which is your interrupt。roller。O。And then the drug controller basically。Checks on each device。Okay。

当然。Once it knows which device is the one。When basically people go to。

To the actual interrupt of that device and then run the。The actual handler。

 once you run the actual handler， you just。Now you have done the most important parts of the world。

This is your Internet Victor Tieble on Nis。So you have from zero to 19 non maskable interrupt and exceptions。

 these are basically 19， the only 19 that you should basically。Hopefully use that do not share。在我。

Then you have a bunch that Intel has reserved for whatever。

Coal processors that it has and different things。And then you have basically different。

Different numbers for different。Interrupt types。 So external interrupts that are coming maybe from USB or from your。

Camera or something， you have numbers， then you have system cools， then you have external interrupts。

That is goes on and then there is like even some that are for future use maybe Linux evolves into something different。

 so they have kept like a bunch。份。For themselves。O。So how do you implement the interrupt handler。

 you have the hardware。to interrupt。Okay， goes to controller。

The processor processor interrupts the carerone。Do IRQ， is there an internal time there for this？

Okay， it's either yes or no that you have a resist device。Already， or not， if not。

 then you just like， you know， exit。 If yes， then you go and run。あですか。判案子。没。

So for some synchronization purposes that we're going to achieve cover。

 hopefully the next time we talk about Linuxs if we ever do that。啊。

There are ways to actually mask interrupts。On a single portion。In the multiprocesor system。

 you might have eight quarterss of 10 cores of 12， I don't care。

 right each one of them will have its own sort calendar。

There used to be a way in the old days where you just internally inside the kernel would cool a single line that will basically mask stop pole interrupts。

On own processors。Now， if you have lots of people using that to be in maximum， you know。

I want maximum speed， I want my device to look flashy and nice， give me the best output。

 then if you have people visiting asking interrupters all the time and theirre device drivers， then。

Your computer is basically useless right so Linux basically pulled that out， it used to be like that。

 so now there's no movement way to do that。So if you're building a device driver。

 that actually is with multiple processors。As as a device driver developer。

 you need to actually start thinking about synchronization between the different。

Cool processor or the different processors on the chip。Okay Linux gives you ways to do that。

 some of them is basically synchronization mechanisms。

 looking and sephos and these very nice lovely things。

 but also gives you some of these callss that are internal to the Linux system。

 to the Linux kernel that you can actually use to enable some IRQs， disable them and so on。

Butom have。Okay。So now that we have covered them。The most important part of your handling now what actually does the work？

It comes at the bottom half。This is basically where。The actual driver is in。ok。优势。

I' fluid as much of the work as you can to the bottom half。嗯。

That's basically because good drivers should make your computer work， not make it still work。嗯。Now。

When you're writing your bottom half good， you should know that this is basically a promise。就 run。

Rather than a time to run。So when you are preventing things at the bottom half。

 that means that you cannot assume any synchronization or any。When it will run。

 I don't know the processor doesn't know， the current doesn't know， I mean。

 we're just run when there' is time for it。However。

 typically what happens is that right after you exit the handler。

 which is the most important part of the。where when you have all your interrupts masks and so on。

You actually start running your bottom half。Of the same court。Okay。

But then all interrupts are enabled back。So。This is how we， I mean。

 there are no magic tools for this that nobody， nobody actually。Checks behind you。People， I mean。

 there are tons of drivers being with every day， but this is what you should keep in mind。

If the word is con sensitivetive， it goes in the top half， if the work is related to the hardware。

 it goes in the top half。If the work needs to ensure that there are no other interrupts that are interrupting that work。

Can， it can go to the top half is you can also do other things。

Everything else should go to the bottom half。So in our network example。

Everything that we said should be in the top half， everything else like processing the packets。

 actually doing TTP IP or whatever protocol that you're using should go in the bottom half。

And there are no simple way to implement bottom half。

 There are actually at least four different ways to build the bottom half in your Linux curve。O。

All days， people actually had something that they called the bottom half。

It's actually a technique that is called the bottom half to implement the bottom half。

But that was until 2。3。 Then they started evolving The way that the bottom half worked is that it had 32 predefined。

 well definedfined bottom half that you can only use It basically means that， you know。

 people back then thought that any hard disk and memory and it mouse and it screen you know。

 bunch of。Of devices， and thats it。嗯。So we needed more than 32 bottom halves and this quickly became a bottlene。

They started building these different mechanisms， jointly improve the system the first one was task use。

 it's also dead。Okay so this is their first answer to the bottom half of working and the idea was that you define a family of cues sort of quite similar to the prior cues that you had in thescateator minutes。

 but now for interrupts so he had a family of cues basically a bunch of cues with some periodative and the colon would go into each task queue they were doub niless。

And basically， it will go through the queuees and start the queing things。One by one， okay。

 based on their priorityity。Again， this became a bottleneck in terms of how the system was performing because there。

 for example， for networking。It can't work that way with thinking。Even in one gig course。

 it cannot work better way you cannot just have tossed you that you have things as as stuff。

 they get tossed and so on。So now this is replaced by something that's food works use。

The two methods that most of the bottom have are implemented in today are so iron use and tests。

Soft IQs is both of them are。嗯加中国体。Completely remove bottom half that very old system。In kind of 2。5。

Soci basically said that there are8。There are eight bottom maps， not even 32， just eight。Okay。

And this a。Are defined， statically defined。You can add one if you want， I mean。

 the book has like more ways to add the software at you。But the nano of really this。O。

And that finding ways to do the bottom half on top of that there's theosslets so softwareqs can run in parallel。

 the same softwareq can run on two processors together。

 so it does not provide you with even any synchronination or adding just runsns okay。Now。

 testlets are implemented on top of software IQs。They actually are use two of the numbers of softwareQs because soQ also has a number table。

 okay so they have two numbers， one of them is for high period testlets。

 one of them is for low testlets。And they run that there are an application on top of the software loyalty。

 so everything in computer science we do。You know， morecapsidulation solves some problems， right。

 so we encaps the so acute use in the hospitalss。Soar cus are used when the performance is totally。

I mean， important， so a networking subsystem。It has its own predefined priorities。

So this is a time summary of how things evolve， so you have software use in version 2。3 work use。

 we'll talk about them， work to use introduced in version 2。5。

But then on these two were decommissioned in version 2。5。嗯。In terms of performance versus easefuse。

So you have very high performance for so cus， theyre completely built up designed for basically the absolute to be the absolute fastest。

You have dusts in the middle then you have work cues， which are just super far easy。

To use for implementing your driver， but they are less performing。

There is another way that's Core to interrupt， we're not going to go through that。That much。

T interrupts is， basically。A way that basically sell that no one。

Instead of even trying to implement the bottom half of the top half and everything。

 your top half is just adding， basically sending an acknowledge。Then。Clearing the hardware。Okay。

 and then everything else is the current threat。So if you have everything as a kernel thread。

 then what happens it gets scheduled as a kernel thread。

 so all of a sudden you have this system that basically enables you to write an entire device driver by just writing normal thread without thinking about top hs and bottom hs。

Will not cover it more in the lecture？So as I said， there are only eight software IQs， these are。啊啊。

Zero for hyperearhos。One for timers， two for sub network packets， three for receive network packets。

 four for block devices， which is basically your hard。Pably for number prior to task this。

S for the schedulener7 for how distribution timers and8 for earthculo。

 these are the only eight as that are。typically you only go for the software IQs。

 you only deal them as a programmer， as the current developer if you're working on the network subsystem or the IO subs system？

So items that softwareQs are for high frequency and high creditd use because you can run them in parallel also。

 so you might be able to process multiple packets， multiple buffers。

Worth of network packets on different processors in parallel。嗯。And use thoses for everything else。

As everything is defined in the car load， there's a tuslet structure that basically has all the tuslets linked together。

This is actually the definition from the code， so you have with something that points to your next dustnet。

You have the state of the taskknet， which can be basically if it's scheduled， for example。

 So if if it is scheduled running， if you have multiproces assistant。

 it will read that flag and see if oh， it's already scheduled。

 I should not try to schedule that task because it's really running somewhere Okay now as we said。

 tasksknet cannot run。Two processors at the same time， you have the count。

You have also data that cluster can use。呃，这 is区异。没异见对。But each field。

And the tuscallet structure means okay？So I think the only one that we do not。

Covers the cons in the look counter。And。Fk is basically the pointer to the actual。汉族人。Now。

 if there are too many， anys are implemented as soft Is。 So in essence。

 they are soft hiarchs the to the kernelone they soft Is。Now each software atQ has one handler。

 so if you're going to the high tasklets， then the kernel will do something and that thing will be basically go to the task。

 the taskletstruct and basically go through them one by one。However。

 it can be the case that you have lots of input coming in from software IQs and the kernel can just cope with all that。

Okay， so if there are too many software fire queues。

 you can end up basically again hoing the entire system and not doing anything。Because again。

 when you finish an interrupt tender， you can go to the you go there the bottom have。嗯。

The sad thing also is that many of these so accuseds can call themselves。Basically， meaning that。

And I' start you。Can basically， if there is more data， for example， the network buffer。

 can just re cool itself。So I can start from all it。 You have a question Yeah。

 So I was just wanted to know the sort queues。 Are they sort of written assembly and they like architecture specific dependent。

But are you written in assembly。 And， I mean， there are different parts where were which are written assembly。

 but， but the most of it， no， nothing is written almost nothing is written assembly。 Okay。

 so it's like architecture architecture independent。 Yeah， because it's basically， I mean， the the。

 the whole idea is that you have。They could， so for example， the high testt IRQ。

 a soft IRQ it basically goes through a structure a structure and goes through each testt and tries to basically do the bottom halve for all the different。

Inrops that already occurred， right？The block devices， again。

 what they what it's trying to is basically trying to paint from a block device， right。

 most of it is going to be just like moving data and pointers and stuff。

A little bit of it can be device independent， but， but that's very， if any。I。嗯。

So case of our kernel soft IQ is basically the wave of the kernel to basically stop。

The system from getting。Completely overrun by the software hi that are happening the way it does that is that it takes。

It's like the the through。The was about what it does that basically it takes some of these testlets。

Some of these software acutes and convert them into kernel threads。

 and if you convert something into kernel thread， then it gets scheduled at whatever time。

It's no longer an interrupt handling process， it's more like as if there's a user process that is running and you just need one it。

And it transactions with the lowest possible priority， which is 19。

 so basically you take these bottom halves and you run them with the lowest possible priority and this is typically what happens when you press a key and then press another and press another and your computer is completely hooked。

And then you see， the letter is coming like， you know。And like after two seconds or something。

 it's basically it's being overrun by so accuseds， so it just goes to piece ofs。So Is care。

So the last thing is work use。And this is a different way offerring work。

 And what it does is ability for there are many of these kernel softwarefa toolss。

There are many of these software IQs， there are many devices。The need to speak。Okay。Now。

Soft air IQs and toasts are not built。 They are built to basically have some。Parts of the of the。

Poent are being completely run from in to the with north sleeping。However， if you're fetching data。

 if you're reading from this。You actually need to sleep because you need to wait for that anyway。

So the way the work cues work is that they actually take any。我仲怕。You convert it into a kernel threat。

And then these cars can just sleep whenever they're ready， they just， you know。

 they go through the normal processes basically looking on。

So you can't look on you sleep and wake up and lose sort of things as if it was normal。嗯。

The way it does it just that it actually implements a special kind of threat that is called the worker threat。

Which is。There' is one worker。一直不是。Okay。The worker threats or again threats。

 there are just special threats， and there can be only one of them post。

And this is how this very nice。Now architecture looks like， so you have basically for each。

For each processor， you have work girlfriend。And for each processor， you have a pair CPU。

Where you astruct that basically has all the things that are now scheduled are going to be fixed。

To be scheduled on this。On this quarter。他们。你好飞。You cant theoreticalically create other work threads。

Although the system does not do that by default， but you as a programmer。

 for some reason you can't create a work， so actually in the book。

 he gives an example by basically saying that I'm going to create another work I rather going to pull felt。

Okay， but that doesn't make any sense that nobody doesn't want。So in theory。

 you can have work to structure that is one per work of threat。

 but usually theres just one word inference threat where these will be。And then， you have。

All the bottom h that youre going to schedule you have a structure that basically links all of them together now one of them will get scheduled to the first worker thread。

 the second one will get scheduled to the second worker thread and so on so you have a list of who。

And the is processor and the work peripheral。Sttop here。Yes。

And then since there theres dispen between the bottom half then we have。So ourcc。You have dust this。

You have worker threats。嗯。Or you have work use。And you have whatever other。

OfThings that you're going to use for the welcome house， there is a deep need for being able to look。

嗯本当。Some of these things are' dealing with because of the same。

Partors of the same interrupt can be handled in different ways。

So Per of it will just be like the thermo matter timer， parts of it will just go on， you know？

Do software IQ or case software IQ horse can be a work。Work you。So this is the end of the lecture。

Iぱ the board出す。你个真。So I had a question about so we you said that the drivers。

 they are in atomic context。And so like the army context， like how is it actually enforced？

The top so the top half。Should be atomic music It should pull run Well。

 if you have all interruptse not not able， then it will just drum off it together， right。

 this is why you want the top half to be very true。So by atomical， I mean。It's atomic。Now。

 if you enable all the other interrupts， except for your same interrupttype。

 it's atomic in the sense that your same interruptetype is not going to override you， right？

But if your network card， which is very different from your keyboard。

If you're going to do something then you don't need to actually do any lock between them as you might be streaming something while you're pressing your keyboards。

And like the top half in the bottom half， are they like just like。

Moduleles or like are they like connected as in how are they sort of So the top half schedules the bottom half。

So the top half， the top half does all the sorts of like， you know。

Acknowledging and then after acknowledging it clears the hardware and so on。

 and then' schedule is the bottom not。So it's like one process。go the other process。Thank you。😊。

