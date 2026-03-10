# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p08 -08-Lec04 Video_ Microkernels (contd)  (01_30_20).zh_en -BV1iP2CBaEHr_p8-

Yeah。So。Let we get started。So let me start with a couple of notes。First is the last call。Scrs。た。

Sttures that are most screens。interestedtered in volunteering please。W just。在3月份。

It's not a lot of work， as I said。If you volunteer， you might get a few。last。

That's helpful to my entire of course。Is the first。Second the announcement screen is。

Just a periodic reminder that we have no device no laptop policy in class。

Alread we saw people using that。You're not supposed to。ら。Please respect that。The second announcement。

 third announcement is someone asked about the victim exam。As I mentioned it。

 it is the class right before the。Before spring break。W I think we serious that on。

So keep that in mind if you have plans to take off。

The first spring break it might interfere with the exam。でここ。

I put that up with the course graphic and then someone asked about where the course is being recorded and posted。

If you go to the class web page and go to the lecture schedule。

 you'll see that the lecture slides that I show you here。

The videosos for the lecture and the notes that。Eventuallyally。min。all posted。じゃあ。Not this I agree。

So let's startutter。So today's lectures will a bit shorter than。

Usual and going to finish our discussion。Also。Give you a very quick。Introduction to La 0。

Yeah the name La zero suggests it's not a real lab basically asking you to set up your machine because next week we'll actually have the first lab。

So let's continue from where we left up last。 So we talked about minis and micro kernelals。

 I talked a little bit about why micro kernelnals。Makes sense。 Okay， there are many reasons。

 One key reason that we。I decided it is a good enough reason for us is that drivers are very buggy if you put drivers stored inside the OS terminal。

 those buns can impact the stability of your terminal cost or crashes etc。

So it makes sense to pull the driver code out of the car。Outside the kernel。

 micro kernelals are a natural way for us to do that because any component。

That is not core to a microconmnel can actually be run as a user level process。

 including drivers as well as other processes。And that's what is shown in this picture here。

 so you will see that drivers that are outside the kernel as well as several other components and I started talking about each of those we'll go through all of them today and I introduce you to。

Noob0， I。So let's start with the microcuror， except， as I said， there are three key pieces there。

is the IPCTs interprocess communication， so it allows you to send and receive messages。

 allows processes to send and receive messages that it enables， hey。

 there is a S task and there is the clock task which Im going to go into。Next。So。The sister。

 which is also shown in the picture here。You see that the this task is inside the micro。You。

 assist task is responsible for all interactions with all of the other servers that are running outside the terminal as well as。

the drivers。So essentially the micro kernelnal exports interface， which are called kernel calls。

And the processes that are running outside which implement various OSs hostity actually implement a system called interface。

 This is slightly different from how you expect the traditional OSs。Moletic OSS。Export and interface。

 so essentially。It starting line here at the top。Below which you have all the OSs processes。

 system plus and a microconner。 that is the system called it。

So the cis calls are implemented by the collection of those processes。The terminal itself。

It is the micro kernelnal Excel， exports an interface that we are going to call kernel callss。

Tpically， cardal calls can only be called by these。Privilege processes by privilege， I mean。

 there are system processes there the components that uses with user processes called system calls system processes called kernel calls to for IPC and other things。

So you got to distinguish in Linux between a system call and a kernel call。

They kind of sound the same thing， but they are not。

This kernel call is basically the micro kernelnal interface system call is the OS interface。

 which includes processes that are running outside。So as far as this is concerned。

 it actually implements。Gner告。So and as it says that all kernel callss are essentially transformed into a request message that goes to the kernel。

 the kernel handles it and sends back。And there are several different types of kernel calls for process management。

 memory management， access to current data structures， doing high and things like that。

So you some examples。So all criminal calls。Start with。

This underscore for something versus devicei or virtual copy set alignmentment。

We'll go into some of this in more detail， in fact。

 the first real lab will require you to implement a small。You understand how to extend the microcon。

So there is another component in the kernel， a microper， that's the clock task given。

 as the name clock suggests， is essentially responsible for time or timer management。So。

It can do it this can be used to schedule another process when the quantum expires。

 you can set timers of various sort So then the timer expires， you get a notification。

 you can interact the hardware clock changes time whatnot。 And most importantly。

 what it does is every clock tick it registers an interpret handler。

So every clock tick you essentially the clock task runs， it says。

 is there anything to do as a quantum expired I something else happen in that clock？

handling and so on。 And if so， you will essentially do whatever you need to do in that interruptangle。

And then there is at least one kernel call that it supports。

 which is set alarm that a user process can essentially use to use the functionality。这そ有点。

For example， call sleep and then that sleep duration expires。

 that call is going to trigger and then send you a note。So， as I said before。

The right way to understand some of this is actually go and start looking at some of the code。

 it's not very hard to understand a lot of it as nice documentation so even if you just look at comments you get start getting a feel for what this is about。

If any of you have a copy of the book， the entire source code is actually printed as an appendix in the book。

 however， as I said， a better way to see it is using the hypertext source graph plugin that I showed you that allows you to go back and forth and understand the code。

Yes， we should。Free areas， which is。えこう。That's a good question the question is there are three types of layers here if you see this picture as the microconnal Excel there are these processes that belong to the OS that implement OS functionality and then there are user processes how does the kernel distinguish between call from a user process versus a system process。

as I had said， maybe you missed it。The kernel actually only deals directly with system processes。

A user process cannot directly make a criminal contact。

User processes has to call an enterprise that exposed by one of these system processes and the system processes typically make a work。

Or put another way。There are the restriction servers。

The incarnation service excuse me allows you to impose a set of restrictions you can decide a policy that says who which process can is allowed to do what。

So in particular， any user level process is prohibited from making a kernel call。If it does。

 it's not。这个す。Only these system processes are allowed。Does that make sense？So， going back to。

Se alarm so so now let's go into each of these other processes that are outside the kernel。

 So first one is process manager Okay so it implements a standard projects interface which allows you to create processes that or not imp probably know。

Things like for and exactly should dont do very soon。That in some detail。

 these are all systems per that allow you to process management。

Psits the interfaces that it actually supposed to do that。It basically also has。

IPC that makes it look like an ordinary moving for us。So there are three or so things it does。

 one is management， creating processes， delet processes。

 and changing their priority levels and things of that sort。Second is scheduling。

You have to essentially decide which process gets to。

Next yes so you are going to implement CPUQ sched you will see that CPU scheduling implementation is not actually very clean it is spread across two or three different things which makes it a little more clunky and normally you would expect all of that to sit in the process manager if some of it does said there were not。

The third is your signal handling which allows processes to send signals which are kind of software in to one another so you can essentially also do that through the process。

NowAs far as the signal handling is concerned it just essentially looks like exception handling okay you have to register a signal handler okay and then when a signal is actually sent to you that signal handler will run it essentially looks like an exception handling routine and you do whatever you want。

这个。Now that's a standard Lu functionality I don't know if any of you actually use signals in Linux process and things of that is exporting exactly the same abstraction except that the signal handling here is actually being done in the process manager。

 not inside the OS itself。Any questions。We haven't gone into any details of any of this。 Okay。

 this is just one slide overview。 we will when we talk about process management actually look at。

That process manager in a lot more detail。It is just for you to understand what this company is。

Next one is the memory manager， as the name suggests， is responsible for managing the RAM。Machine。

Again， from implementation standpoint， some of this is actually implemented in the process manager。

Why I don't know because you technically should have been part of the memory manager。

 but some of it is the port is actually not very clearlyly separated out。

 but that's the way it is technically it's part of the memory manager and some of that quote sinces actually the process。

But that's aside as an implementation detail what does the memory manager do okay it implements a hardware independent memory model okay what does that mean basically says that the layout of a process does not actually depend on which architecture the runs on you just do this because you want your po to be easily portable on a wide range of machines should run on an Intel X6 machine it should run on an R processor maybe another as very pi things or。

So to do that， you want to make sure that you don't actually incorporate a lot of hardware。

 specific dependencies in the memory manner。So the layout。

 what it expect of a process is very simple， it's the same picture I showed you last。不道是谁。

So there is a layout of a process， a process it has。这是不是这错。

ButThere's a text segment for every process that includes the code of that process。

In machine cord essentially that is what is called the stack and the heat。議会選挙 calledデタ here。

Is going upwards。 Okay that's the purview of a process youve got to keep in mind Okay the memory manager essentially implements that logical view when it starts a process。

 going allocate memory that makes it look。So the other things it has to do is it has to essentially track which parts of RAM are in use。

 have been allocated or process， which parts are free。

 and when the new process starts up youve got to go find a piece of memory that is not yet allocated and allocated to that process and things of that。

I a concept you probably have looked at or studying in an undergrad o class。

A process man is actually going to about implement similar。Features in Linux are very different。

こ前大六た。The next piece， which is very interesting piece for perspective this class。

 because eventually you will。Start looking at this in some detail later on in this course is the file server。

So the file server process implements the file system for Linux。

In earlier version it was actually called FS now it is called VFS or the virtual file system and the reason for that that is the VFS layer is a standard way any Uni OS actually supports multiple file system。

If you take any operating system you will realize that it actually has inbuil support for not one file system but multiple types of file system so MacOS is going to support HFS which is its native file system and now it's called APFS actually stick a USB drive thats a fact file system its fat formatted so it loss file system and then if you have a C wrong。

That has an is system。So these are all different kinds of file systems so to enable the OS to read or write data to storage devices or disks that are formatted in many different ways you need inbed support for different types of file system at a minimum you might have a native file system and youve got to at least support things like CD RoMs and USB drive and so on that's already three file system。

But there may be many more you may want to support， okay， the next says EXT 2， EXG3。

 EXT4 and whole bunch of other file system。So。How is an OS， not just Linux。

 but how is any OS supposed to support all of these diversity of file systems？

The way this is done is to what is called a VFS layer， VFS essentially stands a virtual file system。

You to draw pictures here。か丈。많干。Explain what a VFS player does。

There is an abstract concept of what a VFS layer is This is a virtual file system layer。

This is going to expose， calls like green。I open。We think sometimes that so。

So which allows you to open a5 equal to and high to。So you have user processes that are。Mning。

 that is simply going to make those points。You can note that these calls are independent on the type of the file system that the file resides on。

This is basically file system independent。So the VFS layer is going to receive a file system independent request。

And then it is going to figure out what kind of device does that file map to what kind of file system does it map when it is essentially going to then forward that call to the right file system module。

So underneath the VFS there， you might have something like a pack。We might have E X2。对。In DFs。

And so on and so forth so every file system that is supported by the OS is essentially going to sit below the VFS there and when this calls arrive this is essentially a forwarding layer。

 it doesn't actually do anything interesting other than around that call is going to be handled by this fat module because that file is actually on the USB drive。

 it's a fat file system。Or if that file is actually on your hard desk it uses EXT3 or EXT4 is going to get forwarded so what each file system live module has to do is it has to implement a file system specific version of open and write and so on。

 so you might say this module might do an NFS read。

Which actually is the real code for reading from an empty file system。

So each of these modules are going to implement their own versions of a reader by that is file system dependent。

YeahAll of that good ofs is going to。So this is a concept of a virtual file system layer。

Now any OS actually is going to support any units like OS I say OS。

SoThat is going to sort indexux as this and many of the five systems have gone。Yes， wish should。

Can these modules be added on later on to support new types of file system Yes the question is can the modules be added later on to support new types of file system The answer is yes。

 theres a red file interface that the VFS layer has if you want to write your own file system you are simply going to write to that interface and then register your file systems a new type of file system in the kernel and that's all you need to z and you can actually add them they are in the monolithic kernel there are modules you can actually load them dynamically or a boot type because you can add support for new file systems very easily in this。

AndThis morning。Yes。申述。Or it is a more complex。Is the question is of EFS performing a translation or is that work conflict？

It's actually simple as not doing the translature， it's a big case statement。

Okay saying if this read belongs to NFS call NFS3， if this read belongs to EXTFS call EX3 is basically just taking this each of these calls and just saying if this belongs here called the read here read。

 so it's just a forwarding layer its called the EFS switch。还是是。

Okay question is can you embed different file systems within one another。

 actually if you look at virtual machine essentially that the way you will embed a file system in another is you basically have a file。

If that it looks like a virtual disk and you can embed a file system inside。

Not advised because no you doctor yes。Now let's come back to Linux。

 this is the concept of a virtual file system and Linux is also going to have that support now。

Old days， if you look at this picture。She's now a little bored。

You will see that just as a simple file server or a layer。

 because it had only support for I think one file system like that。

Eventually they said we got to support more than that， so they turned that code into a VFS layer。

The virtual file server。 So what it does is。Essentially now you can have a E FS。

And you can write your own file systems good， and then the two can talk to you。

So if you want to just as you could have a module， you can now have。

Code for a particular file system that runs a server process。 You can know the VFS code and。それでけ局じな。

So those modules are now essential in processing。Useer space。Thisspec。你个做。The question is。

 why are we doing this？Now EFSL， why is this not being done at all？This is just quote。

Transparency to end application。 So when you write a Python。to open a file。

 you shouldn't actually have care whether that runs on NTFS or something else。

 you just want to open that file and let something else deal with it for you that something else happens to be the OS is going to figure out what the right type of file system that file decide are and the part of the OS that decides that is essentially。

So everything about that daily applications， nothing else about。so the read and write。

 because the question is， does that where do you do this so the read and write call as soon as they arrive。

 those they immediately come to the VFS there。嗯。A process is calling maybe a library and。

A open or something like that。 the library is calling open open directly comes to the there's nothing else quickly。

 So once it comes to the， it comes to the。So these are lightweight costs you dont not implement them。

I had user space because that is not extensive if I had a new file system I had to go change the life。

那理要这。Any other question yes。Okay， which good question。 I this a few sp system。

 I come to use in just one moment。 Let me just finish this and talk。当啊。This is not read。

 So I'm going to go back。ちち？TheOne other thing every file server has to do is to talk to the disk driver。

No matter what that file system is， whether it's NTFS EXTFS。

 it has to talk to a driver that actually talks to the storage to us if your files are on this your NTFS will eventually take its read call and write call and send it to the disk and can you go read this block or whatever it is that you need to read。

说。The two interactions that are shown here which is a file server and Ra three files of interaction is a VFS process is a file server process and there is a device driver process Okay so the three are actually working in concert。

You没 find。Now let me come to this question that was asked aboutfuse file system。

 how many of you actually heard of fu？给说了。At least some people have actually heard of what is excuse afuse is essentially a way to implement a user level five system on top of any other voice。

There has nothing to do with my Linux here you have few support， I believe at least in Linux and OSs。

 I don't have this views or Windows maybe。这。So。What some clever designers did as they said， why。

Lit this idea of a V FS layer to。可那。ToTo an OS curve can we actually implement a similar I and users？

So few a allows to write you。process that sits in user space。

 it provides a file system that you can actually implement yourself。找好我再说。

I go back because this is more related to Linuxux and we' to go back to the old picture。

 not the Linux picture， which is our VFS layer。If Mu this made us and has in。分是。这人做。

So in this move one if you are to write a new file system。

 you want to write a OS thermal module and plug it into the OS。

So now let's say you want don't want to do that， you want to do this in user space just as a microconor actually allows you to do。

So you want to go to actually the same there as I user there。The way this works is in thefuse layer。

 you essentially have。fire system you written， which is for yourfuse file system。

This fuel file system is essentially a wrapper code that allows you to then stop the user learn process。

So now you can write your own process as a file system。

Process to connect it tofuse and now your entire file system code is actually going to sit and loseer space。

 it allows you to write your own file system very easily without knowing anything about an OS Sc just start to go fuse interfaces。

One of the suggested projects later on in the course is going to write afuse file system。

The other alternative is to write a Linux file system by writing a new file summary process and you can decide which one you want to do。

 but that's coming later， but let's go back to this。So how is this entire flow going to work？

Your user process， let's say process A。It was to read a fight。

Let's say the files that it wants to read has actually been handled by thefuse file system。

And what do you think is going to happen That recall call is going to come as a system called let's say it Linuxux is going to come as a system called a Linux。

Go to go to the VFS layer。VFS layer is going to say this is afuse file system call。

 so it is going to send it off to thefuse model which some the few developers are already implemented for。

So it's going to come here。Thefuse layer is going to say you can actually multiplefuse file systems incidentally。

 but let's just assume there is one， sofuse layer is going to say where is the port to handle read。

It's in that process， so it's actually going to make an up call back to the user process。

That user process is going to get the ring call。And now you have written that tour to Bhi。

So you might have actually put that data on some disk for wherever it is。

 so you are going to actually implement your own version of read It's going to come back。For doors。

As another recall call， it's going to go back to a device driver。

 go to whatever that storage devices， and then come back and go all the way back to the process。

That's one way to write a few responsess。The other interesting thing you can do with use is you can layer file systems one on top its called stackable file system you a question。

The point。The point of afuse file system is the user can implement does quite a few interesting you can write a user land file system。

 you can also do what's called a stackable file system。Talk about that。

 That is not allowed in VF Okay what is a stackable files， So lets say you have a normal file system。

You want to actually implement encryption， order to encrypt audio and large security。

You can essentially write a crypt Fs layer。So all the recall to the actual file system go through your file festival first。

 which is just doing encryption and decryption， that's all it's doing and then making a regular call。

So its just a layer that is not logically just sitting as a layer between the process and the actual file system and basically get an encrypted file。

As part of a read， you decrypt it and give the decrypted data and you have to write some new data。

It comes to your layer， you encrypt it， and then just send that encrypted the data back to the device we return。

So you can actually so in this case it's not a new file system it's just a layer that sits on top of a file system。

 you can do that as well， so these are called stackable file system where you essentially have a cryptographic file system that's sitting on top of a regular file system。

So there's data on the regular file system， it just looks like gibbper and was all encrypted。

 every file is automatically。WI this what AFS does。OkayQu， is this what AFS does。

 which is a Mac system， AFS does not do that。 it actually has specific hardware to do this for because it has really a hardware level。

This is software encryption。 we go to process。他说没有。Doing this more efficiently。说。

So this is the kind of stuff you can do with use use also allows you to do other things so you can essentially mount the file system or SSH if you use SSH FS。

Basically， you can essentially take if your SS access to any server anywhere。

You can take all the data that's on that machine and just mount it as a file system。

And then all of that is essentially being run over SS。Yeah。

 that's why I said the has a few slides system come as well。

This allows you to mount any disk from anywhere using an SS。All you need is a S protocol。

 then're essentially sending command or SS and that process is then going。

There's not even a local fileist on there data is actually going a remote mission or this。

So a variety of interesting things will not belabor this so all wes or right cause are going tofuse file system instead of BFs like boys wouldn't know right to question is is。

So you are still going to have VFS is going to be what you receive the recall call you just have a fuse module just like your other file systems you hand that saying this is your call figure it outfuse will send that it just so happens that。

Instead of having that code here its outside thats all it so this allows you to put that code outside those normally you would have to take that and make this module here you just put that there and you put a forwarding layer。

Are you asking of？Okay， what is views so views is just a way by which you can drive user level file system instead of making them kernel model。

So that's all it is。 So instead of writing more modules here。

 you can write modules there and use that to send you the。そよす。Yes。Everything has to go for we of us。

 because that is where all the calls go。So two levels of in direction come here。

 comes here then grow。Any else' see。So that's move as we talked quite a bit about file server and VFs and whatnot。

So。We talk about the reincarnation server。Here so this one。Is responsible for O drivers and server。

The process manager and its user level processes。The in combinationnation or harness system level processes。

Yeah， so that's the other than that， I think that。Some similar things。

 but there is more things happening in the reincarnation survey。

So if you want to start or stop a server， device driver， those calls are handled by the incarnations。

The interesting thing it also does is point recover。We the wise driver crashes。

It does not because these are now running as user level processes。

 it does not bring the rest of the system down， but something has to figure out that that device driver crashed and maybe restart it。

They're excited by their incognition。The way it does this is very interesting， So it basically。

When you start up or boot up your machine， it takes all system level processes and it adopts them as two child processes。

Technically， if you are starting them， they automatically become your child。

 but assume that the incarnation server is either a parent or a direct ancestor of all system processes。

So now if one of these system processes crashes or is terminated。

What will happen in any un like operating system is you are essentially going to get a sick child signal that says one of your child processes has been terminated or crushed。

So because it has adopted all system processes， all the signals comes to the reincarnation server。

 it figures out what happened to which device what process crashed and then it can take any recovery reaction。

 one recovery action restart so say let me restart that device。

So you automatic restart without rebooting your OS， restart text system processes。Now， of course。

 that component is buggy。It make rush again。So if it crashes frequently after a while。

 it'll stop saying that there is something wrong with the code。

 so it has a built- in mechanism that says that you can only do us so many restarts in a certain time period if you see repeated crashes your road essentially back off and say this top shouldn't run。

 theres something wrong。So Linux has automatic fault handling printeded。

You would not normally see this in other operatinggra system now there is something very somewhat like this in Linux。

If you know what IinNED does。So ID is like a demon that starts in the processes system processes。

 So ID can also track when processes crash and restart。

We're doing this in users So this is similar things happening in the range garation。

So if the reincarnation server is adopting all system processes as its children。

 is the process manager doing the same thing and adopting all user processes as its children or the user processes is not children of the process manager？

Okay， so a question is， if reincarration center adopts all of these processes， who would。

Who is adopting user processes So typically process manager does not do anything about user processes。

User processes are started by other user processes typically most user processes are either started by your terminal shell or user graphical user interview if you double click on something it starts a process then essentially the parent process is yourbuoI manager and it's a child process if you are in a terminal and you basically type a command then the parent is the shell and the child process is essentially the process that started so there is essentially a process hierarchy。

In any UniX spine system and the direct process I is the same in Linux as well。

Now there is essentially a combined if you have any access to Linuxar， you should go and type PS3。

PST will allow you to actually see the process I show you parentchil relationship all processes what that typically。

And you'll see that typically， the shell is the one that's starting over this。

What happens are inincarnations。I think that then the system was。That's my belief。

 but you can actually start， kill it and figure out what。意。

Just to ask allows you to actually answer your own question。这过性。So。

I think there are only a couple more components。 and then well talk about。

secondSo there is a data to company。This is a small。

I believe in memory database will publish subscribe functionality。

It allows system processes to store their state in the database okay so theres anything important that is part of your state。

 you can also publish it to the data store this way if your process crashes and restarts。

 you can just load your state from the data store and then you have all the information that might have been in Ram that disappear on your process。

So it's a generic database， but。めぶり。But it is actually used by system processes to keep important information that they might actually need for variety of things。

 So also provides you a sub interface， a public subscribe with。

They don't know if any of you heard that probably subscribe to take 670 and let go through this in some detail。

 but basically it's a mechanism by which you have essentially a producer that produces a data item it publishes it and then subscribers can subscribe to date variety of。

Tys of events。 And then whenever an event occurs， then the data store in this case going to forward it to。

it's called public up a general mechanism that allows you to receive events or messages from other processes。

Data store essentially allows you to。Do public subject can essentially subject。

Soing events and so on and the last functionality it provides is a very simple naming service。So。

You could ask the question if process manager wants to send a message to the memory manager。

How does it know what address to send it to？So the way you are going to do this whenever a OS component starts up。

 it registers itself with the data store saying I have the process manager。

 Im going to listen at such and such port number， if not a network one but an IPC mechanism and then if you want to figure out where the memory manager is a new process manager is only。

 you just essentially send a request to the data store。Each of these processes are。

Because it does a naming service on top of it。How do you know where the data store is run？

Do it have a fixed name？😔，iss a standard problem with any naming service。

 nothing interesting that I asked Every naming service needs to be listing on some well known location so you can actually ask it about something else if you don't know where the naming service done。

 you can't ask it in。Yes， so you might not need to know where anything else is executing。

 but at least as to know where the naming service are。

 so has to listen to some wellknow location when you can register itself at some well known location so anyone can make request of。

I'm Friday the meeting。5位。Is it it with the incarnations。

 the data source is kept with the incarnations。No， data store is actually a separate component。

As you see here， the incarnations over and data store are two different。 again。

 if you have these kinds of questions， what you should really do is you go into the code and then you'll see。

5月。And youll see in servers， you have the data store， which is here。

TheIncarations of these a different。いでし。datata store can then very little bit of information on faults and so on。

这回家。So。We already said that then has good features to detect fall and recover from falls and so on。

 but there are also features to isolate form。Ss and drivers， they run in their own address space。

 their own user level processes。They are protect them many them in protection so one process。評か？

There many spaces belong in other user processes have the same level of。Now。

 the other thing is the restrict。We reincarnation server or sets restrictions or user level processes。

 which is what I said we cannot make re kernel calls and so on。 only system processes are allowed。

Orinary processes cannot request。So they have to contact a Po server。

 which is then essentially going to。Was for。说。You use the data store to essentially figure out what may have changed。

 what may have crashed it so。Your file server， for example， can subscribe to this image。

When there is a driver crash， okay the incarnation server will essentially figure out that it crash。

 it can essentially tell the file server or saying this device driver has crashed。

Okay maybe that finds others next that he started。At least time So some of this qua handling logic is built in。

 It's like exception hand I have written Java code order。

So all of the same kind of stuff has to actually happen here。

Because you are going to be told what has If you' are writing a monolithic kernel。

 you will essentially have other problem。And if you have one component crashing is going to take down it happen in this case。

 only part of the overseas crash or you can take corrective action， which is essentially water。

So you are using a combination of the data store， which is going to drag these events and then deliver it to the right processes saying this。

Yes。You can handle that message。Aace time。So last piece， before we end the discussion of。

Next overview is performance。When we started this discussion， maybe two or three classes ago。

 we said one of the downsides of microcurls is that performance is actually going to。

Slow other mannerether， there lots of interaction between user level processes that implement OS functionality。

是。Yeah， the paper that is the turn of the paper that I。

Sken about last time has some details on what the performance had done。

 I don't think they actually ended enough。Profiling。Answer that question definitive。

 but they did have some information。 for example， they said what is the impact of taking drivers from the kernel at space and putting them as their own user forces answer is 10% not a big order。

 It's slowdown for sure and not a use slow down。You said what is the overhead of actually doing file out their answers is on the paper saying 7%。

换。Thats perfectly okay， what I did not answer is what slowed down to actual application processes see。

For doing a variety of comment as to that level of benchmarking is not presented and normally you would want to see how the worst as a whole is performing by running a standard benchmark。

That says what is the overall impact of building a microcon as opposed to doing it。

That was not shown in the paper。それすね。They did try to answer some questions。

 and they are presenting a view that says the overhead is an home。

You can actually try it and figure this out。Perform as well as they claim it to be。

Any questions yet for I show you。Yes是。Can usual processes access。

Qu is the user mail process can it access the data scope。I'm not sure I think that you are water。

Yes it looks like you cannot， but I'm not sure。The figure is somewhat dated。

 so it may not actually reflect what has actually happened now。Yeah。

 I don't think there is a direct interface it publishes， but I don't know。They answer the green of。

Hello。Let me。Spend a little time showing you。So first thing is。You have to start installing stuff。

 So you are ready for the actual lab。So the lab0 that's coming out later today is just set up。

 It is not real love， not grade。 You don't have to actually。Think of our。Greatre a。

 It's all about setting virtual blocks and setting up mimics and so on。

 So we are ready for doing something interesting， starting next week。Next week。

 I think we have the first lab or which will involve doing some sort of。System called kernel。

 called toy。S good process。Okay so you know how to try the OS component。

 how to change the interface of the OS。that's the first real lab， but。Perhaps zero is all set up。

 but thing you got to do is first go get the source graph pluginin。我这边都老实。

It's just to either chrome or fire from。我们都不道知是。I mean，Once you've done that， you see that button。

You can go to any Github repo and you see that button。

 you click on that and you essentially get that same repo in a browussable fashion。

So you can then examine Min score and so on and we will provide you pointers to where Min is we have a fork of it in our course repository of course theres the definitive version that we are。

doesn't like。So that's the plus thing， so you can actually。

 this is the description of lab zero experts be made available。So you got to install virtual box。

Okay， that's essentially all of your。The next stuff is going to run on virtual machine。

 much easier than actually running things on physical mission。

About 15 years ago when I taught this class， you actually had a set of PCs where you had to boot stuff and you would crash a kernel and corrupt the disk and then you got to reach all everything much more painful。

 Now you can do everything in virtual machine so you can use a snapshot a virtual machine you corrupt it to go to the previous snapshot everything is back to where it was So much easier to deal with so you are going to do everything inside of V so you have to get via virtual box as your free version。

If you really want， you can do things on me and there are panels， but we don't recommend it。

 Let's stick to virtualbox It's much easier。So you're going to install that。

 then we are just to get you started to give you a prepackaged Linux year。

You can simply boot it and look at what Linux looks like， which Im going to show you。

so here is virtual box， yes so essentially you can just boot， so that's your Min VM。

You can just start it。You just start boot。Okay so you'll get that good prompt。

 and then you can just start。Start。Then you go to get a。不知道。那げ面。

So this is basically just a EM that's running Linux next。给る。essentially means road。

 which means you can just delete whatever you want to。something that's bad。

 be sure you know what you're doing you type something， of course。

 if you delete and you can always go get something。But we've got to understand some basic commands。

I understand what you're doing。Now， a few things youll need to know you， there is a difference。

There's a difference between pausing a Vm and shutting down the。Pauses like hibernate。

 you can essentially resume from exactly where your left。Shutting it down is like powering it down。

So you need to know some ODC， the other thing you need to know is the source code for Linux essentially lives inside the VM。

So， if you actually go to。Useer source。So you will see all the code I was showing you and get up it's actually in here。

So to at least minimally to compileed near the wheel。

You can also develop the code inside the VM and I'm going to show you some examples of how to do that。

 but I would recommend that you actually use GitHub and checking things and then only once you develop the code。

 maybe check it out here or copy it here just for compilation。

So you might want to think how you want to do this in a smart way rather than to develop and build inside the VM and you crash the VM your code is also gone。

 you develop outside and then you build inside。Better way， but it's up to you。

Whatever you to save a copy of your book before you。Bha kernel that you actually。

So the few things you need to know is if you want to use that code。

 you can essentially connect to this using SFTP and do some stuff。You can we recommend use eclipse。

 but any editor that essentially has SFTP support allows you to directly edit inside the。、イ在に。

Just want to connect to the realm。对就是。You跟我是路。So now you can see that it's actually connected to。

That's the file system inside you can essentially go to user。Here。Do this。

 That's the code that's inside the V。 I can actually edit it in the browser on。Machine。

 this what we're going our to。Use VI and things of that so you can essentially use any editor that has。

Some sophisticated SFTP cable eclipses of everyone。Labric wire would at least minimally use eclipsse。

It also allows you to then build inside and water。Just a few things to keep in mind now of course。

 if youre just deciding you're just going to use GitHub。

 you can just use whatever you just check out the code from Giub， do whatever you want。

 check it back in， go inside the V check it out inside the V from Giub and then just build it。

The code is actually going to live on either your machine and Giub and not necessarily being built inside。

It's going to be built inside but not developed。 but the next book actually says this is a good way to do it。

 I don't think it's necessarily a good way to do it because we are going to crash a。part on。

All right， so a few of these things you need to keep in mind。我 was这是。

So so this is the prepackd VM which we already created for you all you are going to do is install virtual box。

 download that image and you just start it and thats what youre going to get but you also have to know how to create your own so the lab requires you。

Essentially， take make a blank VM， install Linux on it， not very difficult。

The installation instructionss are all there and then essentially create the same VMV created。

This allows you to know how to create your own virtual machine which you can well use。

So that's essentially your step number two， creating your own Min VM。And step number three is。

 you need to know a little bit of UniX commands to use my because it is always giving you a shell prompt。

Yeah， I think there is a way to implement X and so on。 but x windows better as。Complicated。

 if you want to can。We need to minimally know how to use a shell。

There are some unique tutorials they give you so you need know some basic commentss。

 if you already know this， then you can actually skip this。

I showed you how to access that machine remotely in the browser Yes Well just installing the VM will you immediately will the VM immediately have internet access to like question is if you install the VM will it have internet access typically what virtual box does is that essentially it provides a nated interface to the VM So your VM is actually going to use your machine's IP address but it is nated inside but you don't really need to worry about it you can access from inside that VM anything on it。

My twice。我是。All right， so you are going to install elipse。

 then you are going to compile a curve question。So the next step is that actually about to install not install。

 but know how to compile a kernel because the entire course is about making。Changes to the kernel。

 you better order to compile one。 So youll compile the default kernel。Install that kernel。

 and then you'll build that kernel and make sure you know how to do those steps。

 Of course that kernel hopefully will good。没。What。The good thing in Linux is you always have two kernels。

 that choice of two kernels to boot from the default one， and then the one you install so if you。

Write some code compiler kernel。 boot。 It doesn't boot。 You can restart the VM。

 And at that boot prompt， say do the other room。 So you always will then itll boot the default one。

 So you're never overr the default kernel just have a second one The boot。

 So your boot loader actually allows you。Decide which one you want Okay this way you can test on if it doesn't work。

 you still have access to your VM you didn't describe。

There are some nice features that you will have。对对。So that's your unique terminal。这。At that point。

 you set everything up。AReady for the actual lab like。So make sure you do all of that this week。

And next week， we are。我这拿。通我。We will also， for those of you who are not familiar with。

Unix shellll come。 you may have even use Juix。 But if you use KD or whatever some go。

 you may not know enough shellll。 give you a tutorial on shellll。 if you are rusty on sea。

 youll give you。tutorial on scene， but you better。No quickly。Becauseれました。Anding of governor that's。

The crawl and then jumped。Yeah。sure to get up to。That said for today， which shall end a。

