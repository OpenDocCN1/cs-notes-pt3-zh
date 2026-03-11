# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p22 -22-Lec11 Video_ Minix Memory Management (02_27_20).zh_en -BV1iP2CBaEHr_p22-

。えつけ。M memory matter。ォ来工財の。plus one is。You。Good evening exam。7人 B。Where do go。说歌干不行。

So to get the exam。It a go to the Cs building。1，42， That's the larger of the two class。

So that's something that we should keep in mind。The other thing is there is a lab view next。最護？

You have started， if you have not， please do immediately。take some time and effort。

Do not wait until the last。And just to give everyone a sense of what is coming。

After this lab is done。There will be。One more two more labs。

Which one is a really straightforward for a lab and a project。So。We do the midterm。

 and then just before you go out for spring break， the third lab will come on It's going your memory management。

Some of what we talked about last time and today will be。Concepts that you should full memory。

And then we willll have one more mini lab really afterward。

 which is going beyond Doer and OS virtualization。And then the project itself。

It would be really like a longer lab， but well call it a project that kind of a cap store thing you do for the court that's where be on the voice drivers and file systems。

So the idea is implement a small device driver， and then implement a user's face files。

So that's what so essentially there are really two labs。

 one regular lab and one a little bit longer lab。If you call the project。

 that the Docker lab is really interesting。啊是没有。At much time， but it gives you some exposure to。

Lenux is the only Linuxux lab in the course。Everything else is good experience。

So there's going be Linux。St with Docker and。Is that here what' coming。

 so I just wanted to give the big picture here because they have been。What be to。主要给这个。Next。

 so let's get started with Vi memory management。 So if you remember last time。I did a refresher on。

In every management， we went through several different memory。schemes and so on。

 So we continue the discussion， but we make it morely specific。就说 that all。So。Now。

 as far as Linux is concerned。Peverry management and process management are intricately tight。

And the reason for this is memory is allocated to processes。So when you start a process。

 you have to memory terminate a process， you allocate。本诉。So。

So the functionality that you see in terms of the source tree and so on。

 you'll see that process management and living management is closely tied to one another and the functionality has also evolved over time。

So if I ask， what does Linux do for memory management。

 there is no one answer because it may depends on the version。

And I'll show you how things that you want so earlier version you simpler memory management。

More recent versions have actually made them more sophisticated so I'm going to talk a little bit about both so you get a sense of not just the evolution but also how things can be done if you made more simplifying assumptions about how memory issue behind versus how you should handle memory if you have all of the features we talked about last time segmentation than paging and virtual。

So。So let's talk about the simpler variant of the we。So3到 one。In mimics。Because I think 3。

1 is around when they started adding a lot more newer functionality。

 So the older versions of Linux made lots of simplifying assumptions about how delivery should be handled。

So the first thing is there was only one user space server。

 which was the process manager that did both。So if you look at3。1。

You have to look at the PM code to see that it's handling not only processes。

 but also memory allocated to the。There was no separate memory manager。

Everything was essentially in the process learning。Now what was the scheme that they。

 they assume that a process is a collection of segments。

 so essentially using the segmentation approach that I presented last time。

 so every process was assumed to have a stack segment， a tax segment， a he segment。

 few other segments and that's basically what they assume。Furthermore。

 presume that each segment was continuouslytiguously laid out in Mel。And I'll picture the。

So you have。So let's say your process， they process are mindful segment。

 so it' say this in the text segment of the process。そした。So you assume that's just one process。

 we assume it as three segment， each segment is contiguously laid out。

But the seways themselves don't need to be adjacent to one another， they could be anywhere in。

That' is the assumption that was made。 Okay， so so essentially， if you look at this picture。

 you will see that。Once there are multiple processes re and your RAM essentially looks like a collection of holes with an allocated segment。

 it's a sequence of holes fored by segment， whole segment， and so on。

So all of the stuff we talked about that relates to coniguous memory allocation。

That is basically what this approach used as far as allocating memory was concerned all of the processes in this case are in physical memory in rank there is no virtual memory here okay there's no demand paging in earlier versions of。

As a thing you want to keep in mind， get low Beijing below up your live。

Now the reason they did this is if you want to implement more sophisticated memory management techniques。

 we will see soon that you actually need hardware support for it。

 you need to assume a model processor for example that has paging hardware that has TLBs and so on so if your CPU does not support this feature and fundamentally you cannot implement those approaches in your operating system。

So the， when it was designed， it was designed for。Older CPUs it was designed for more embedded processor。

 which typically do not have support for ph， which is why they're with the segmentation so if you take any lower end CPU essentially you have to make this assumption that the entire process is resonant maybe the process is continuously laid or you can on a zoo paging with things。

thought so early versions are things like raspberry pie or you know you would actually have to make these kinds of assumptions if you were to build that O model。

Now as hardware evolves so as Linuxs， some modern versions of many which are really force 3。2。

 including what we use in this class， which is 3。2。1。

 essentially assumes more sophisticated memory management。

 anything that a more general purpose OS also supports。So the support for paging。

 the support for design paging， virtual memory， and things like that。

Now to do this there have made some changes in the code so you will see that around 3。

2 they started introducing the notion of a virtual memory manager。

 so there is now a VM server that is separate from the process manager。

 all the memory management code has been taken out of the process manager input in its own server that is responsible for memory memory。

Yes so now you will see that the code is flex of this， but the end is different。

We have introduced support for Beijing， virtual memory， and so on。Now， in this case， also。

 they assume that。Processes are a collection of segments。

And that segments are continuouslytiguously laid out but they are not laid out continuouslytiguously in physical memory。

 they are laid out continuouslytiguous in were children。So。

So this was a picture you want to keep in mind as you have ran here。Independ Baam。

 you have this abstraction of all children。And notice that I've made it bigger than physical memory。

 because that is what you want to assume that virtual memory is effectively infinite a large。

Religion and what you use is processes are first laid out in virtual building。

So I do basically have segmentss see it。That said this is process1 States segment。した。是我。まトゥセて。Thanks。

跟坐的 so forth。So you are assuming that in virtual memory processes are still contiguously later。

 but that is no longer the picture for physical memory because physical memory is now paged。Okay。

 so here we're going to have a collection of changes。Some subset of these。

Pages are now going to be mapped of physical memory。

 so now the entire segment is no longer in physical memory。

 only parts of it are going to be physical memory and there going to be demand page and virtual memory is going to your desk。

Very similar to what any modern of us would do and what we discussed last time。

So more modern versions of Linux will essentially use segmented paging because I introduced both this notion of segments and I introduced paging。

 so essentially you are going to use segmented paging and you' are going to use virtual children。

Thank you。So。page so now with that picture in mind we are going to now go and look at a whole bunch of these concepts all over again。

 but with more of a Linux orientation we will see what does Linux do to implement various concepts last time I just introduced many of these concepts in a more generic way so essentially we are going to discuss the BM。

 the virtual memory manager in some detail and we discuss parts of the process manager as well but when're still doing some things to allocate memory and。

So， then now。ANice document that you can go to the Min 3 Vii and if you global look on theDevelop doc。

 you'll see that there's a description of the virtual。Memory manager in it。

 some of the contents of a lecture are taken from there but it's a good document to read to understand what is going on as far as the book is concerned if you actually go and read read about this in books the book which is specifically in chapter 4 it is assuming the older worship of memory management it does not actually have the notion of a VM in it so the book is out of sync with what you are seeing in this class that as far as memory management is。

So do not use the book to actually get a feel for what Linux does as far as this course is concerned because the two do not match up。

The book talks about an older version where you did not actually have paging and things of that sort of in the。

The current was the things doesn't have all。So here's an example of an interaction between the process manager and the virtual building。

Here so let's say。You create a new process， you are going to call fork。

So the fork that is going to be handled by the process manager here to implement for。

 so that's a quality and maybe if it' readable in the back。来也算。Look at it。

 so what you will see essentially is。Theic process is applied as it comes to the process manager。

Process manager tells the virtual memory manager saying I allocate some memory for a new process。

What is the virtual memory manager going to do is going to look in virtual memory。

 find some holes that are big enough to accommodate the new segments， which are the text segment。

 the heap segment or whatever the segments are。So you're essentially going to go and look for scan the holes and find a region of memory that can hold that cross that's what become done essentially when you do。

ゴールけ。address space and then you tell the terminal saying， okay。

 this is a new virtual address space for this process。被三人。

Com back and then you'll actually do four to create the new process I input and that sort。

 and then the return back。Okay， so you will see that process creation is intimately tied to how memory gets allocated。

So that tells you that this was the reason in early versions。

 all of the code that the VM has now was actually the process manager， but now they're separated。

That all of functionality， two different processes。

So let's go back to the VM server and I try to understand what kinds of concept is Okay so first thing is。

It will have architecture dependent code or hardware， dependent code or hardware independent。

Unlike things like processes which are really hardware independent。

 there are really no hardware dependence but when you come to memory management。

 you'll see that the code actually has some architecture dependence is you'll see code for 3 x86 and code for our architectures and whatever hardware you need to support will need code for it why do we need hardware dependent code the reason is lot of the memory management。

 the lowle memory management details is actually going to be dependent on what the CPU does as far as paging is concerned and how segmentation works and that is very much hardware dependent so theres some parts of the memory manager that is going to be very specific to a particular processor that your overseas support。

Once you have done that the rest of it is hardware independent okay what technique you use to design is this first fit best fit。

 all of that is not dependent on the hardware that's hardware independent but as for as setting up the process page tables and all of the things are concerned there will be hardware depend。

So this is probably the first time we are actually looking at a component of the OS where you will see theres a code that is actually going to be dependent on what processor of the OS is going to be done。

In this case we are going to assume an Intel XA6 processor。

 we are not going to look at other processors as far as the lecture is concerned because your virtual box respectively emulates an XAA6 processor and that's all you need to know as far as the class is concerned。

 but you should want just X86。Thank you。But does our architecture dependent an independent code now there are some data structures that you want to keep in mind and what Linux uses is this collection not collection but terminological regions。

 we essentially a particulart section of mimic so there are virtual regions we stand for virtual chunks。

There are physical regions which are essentially a referring to physical pages in the。

Memory allocation is essentially done through those data structures saying giveive me a chunk of free memory virtual address space that you'll essentially use the first of those data structures or if you say give me some number of physical failure you're going to essentially use the second data structure and look at that。

So you have to work distinguish between what is happening in virtual memory and what is happening in physical memory。

two are different in this case， you are essentially going to look at con here you are going to look at pages。

Thiss phase like that。Now there's another data structure that you want to keep in mind and that has to do with a disk cache。

So the memory manager also holds the disk cache。And I'm going to come back to why you need a disc cash in the memory manager shortly。

But there is a disk cache it holds blocks of the data that you read from the disk and it keeps it in the memory manager and we look at why that is needed in just little bit。

So these are three data structures you want to keep in mind。

Now let's take a look at a few more details of the virtual memory manager that shows you how the code is laid out。

 how the interactions work and so on。So at a very high level that is essentially。Calls to the VM。

 they either come from user space， get to allocate revenue for heaps and so on。

 or they come from the process manager when you're doing a for or an exit and things of that sort。

 or you might get occasionally calls from the curve。Now， regardless of where the call comes in。

 the handling is always done in the following if in the main not are going to receive that call okay you basically you have the me。

No， that's basically looking at waiting to。Any of other。

And then once you have received a call for allocating memory Dalocating memory and so on。

 youre essentially going to go to the code of your EM and call specific files of specific functions which could be memory mapping or caching or page files and so on。

 and have them do certain tasks and then youve got to do some bookkeeping which is update data structures etc written。

So every deliveryever management calls involves taking some actions and updating some data structures like page tables or the caches and things over。

At a very high level。And so yeah did this。Picture youll have an example of M math。

 which is memory mapping。I don't know any of you know what endMap is in a generic concept and operating systems。

The think the verdicts。No remember what I map does。Yes。It gives you a pointer to block the。It does。

 but that's not quite what it does then。Even my love would do that。And map also gives you a pointer。

 but it does something more than that before it gives you。

It doesn't that that point of memory is accessible。So it does track memory also。

 but there is something it does before that which the word map should tell okay M map stands on memory map。

Memory mapping is used in a it's a generic concept of Uni that is used for a variety of things one thing you can do with MMap is take a file and emm that file because what that is going to do。

I essentially create a memory abstraction for that part。an example， so let's say I'll file on disk。

所后费一。3。小。If you em this file， essentially it going to allocate some memory。

And mapap a certain region of memory to that file， so now you can read or write to that memory region as if its just the array of bys and then every time you read or write to it。

 those requests are actually going to be satisfied internally by making a this or the re that map。

affected it looks like the final sitting thing here in memory and reading or writing to that memory region triggers this guy or so youre not explicitly reading or writing to this。

 youre reading or writing to memory regions and the OS is reading to that writing from that disk。

That is what an M map call does。 It can do other things but does。'Some memory map。I， I think。

 I think because on here you have time mapping the essentially this。One I look at memory to do that。

对。Is it like for efficiency that whenever you make any changes for the file it will happen to memory and then at the end of once you are done with it？

Come down to disk。 So question， why do you need M because Okay， not a unique specific question。

 So this the。Programs that will use m maps rather than explicit this style because they have just a simpler abstraction if the file just looks like an area of bytes in RA。

 you can just read or write through it as if it was all there the can even cache portions of it for human memory so that it can be fast and then。

You can just learn how to adhere what actually this。😔。

That's one way to do one reason to do it and memory mapping is also sometimes used to share memory regions across processes and so on。

You can also actually map regionss of one process into another processes at it doesn't have to be a fight。

You can essentially take one processes library and map。 So it can be also used to share delivery。Yes。

 does memory map I also use the M map code of the memory map I use a map yes。is essentially0 doing。

这你在过性。So， as far as the。Our discussion of BM is concerned Mmap is not really of concern though I just wanted you can know what that M call does there Okay。

 that's essentially what's doing。 but from our perspective really what's happening here is you are。

The work of the memory manager is essentially implemented in several functions that are part of Map doC。

 or Pay4 doC， which are able to come and come to region doC。

 which is actually allocating entire regions， pool and things of that。

So that's the structure you want to keep in mind。So now let's start because Linux。

 the new version of Linux essentially uses paging。demand specifically demand tracking。

 you are going to have scenarios when the process tries to access the page。

Or some memory address and the page is not in， so you are going to get a page point。Yeah。

 that's what the page for it means I try to access。

Memory address and that location is not actually part of that process is not resident in parameters。

 actually no disk can you to touch it。And here is code that shows you how this can be handled。

To understand this， we should not try to distinguish between two types of page files。

 which unless you are gone really deep into an OS， you probably are not being told about。

There are page faults or something called anonymous page fault and there are page forms on the files。

I'm going to talk about anonymous page files first and then I'm going to talk about page files or files and then I'll try to also answer why there are these two kinds of page so anonymous page files are the usual kinds of page files where you have something in virtual memory the process try to access it and address there its not present and run youve got to go and fetch that page in memory and bring it to。

So this process is referred those handling an argument speech。

So it's the usual thing that you will see in that picture again。Essentially how a pageboard message。

 it comes to the virtual delivery manager， the assignment of pageboardC is going to go and ask。

Actual frame。 So you allocate a frame where this page can be fetch from this。

 So you have to go and throw something out。 This is where you are going to have page replacement coming。

I remember I said you can use things like LR you and one from。

You're going to edit the page and then once you edit the page， you're going to essentially go。

need of that faith。see that the。在不理在这。So handling a page form requires you to decide which page to e。

Okay， then you go and get the page from this and it。Okay， typically virtual memory。

So all of this what I have shown here is stored on this in a special  partition which is not stored on the file system partition。

 is stored on a special partition does't even know what that is stored。

It's called a swap partition on this so typically you will not see that partition what you see on disk is your file system。

 you will see all your files but there's a region of your disk that is actually reserved for storing all of the virtual memory data。

 all the processes that are active they are all stored and you don't want users to see this because theyre going over it's a process with correct because that's data for a process that is actually stored on。

So that's an additional interview all of this is actually reading or writing through a swap partition。

So when you read when you do a pagePo on a swap partition， that is called anonymous pagePo。

 that's what we just discussed。If you do a page part on the file system， that's called。

Handing a page for a file map region or handling a page for the file system。

So you can have page fault on the parts of the process that trigger reading or writing from the file system。

Let's ask why is that even going to happen？Why do you think that if a process actually fit？

If causes a page part that's going to require you to read or write from a file system。

 Why is it not adequate for you to read or write from the swap partition。Yes。那这是。

That may be the first stomachaxs is the beach。You could， but why was that phase not in for children？

And where is it。Go of the program。 That's the important part。say wouldn'。

We have the same cost of access。It's the same cost。

 but the question is why is there stuff on the file system？

ForThat belongs to this process as opposed to virtual letters。And this is where， as I said earlier。

This is where you actually have to think about what the page point is doing for us and what is trying to fit remember that a process has at least three segments is a text segment。

There's a heap segment and there's a stack segment。The heap and stack are data segments。

They store data for the process， those segments are actually always kept in virtual women on the swap partition。

But the text segment， you don't necessarily have to keep in virtual memory yeah I do a picture here that showed that it is actually in a swap partition。

It need not be it could actually be swapped directly of the file system if that file is actually an executable so if you create an executable you compile a C program it creates an executable that is essentially a text signal。

 it has machine code already。So you can directly swap off that file rather than copying that file here and making a text segment。

Because I just was， it just wasted some space because all of that is exactly the texting。

So what many OSS do as an optimization is if you are executing a binary。

 this is not going to work if you are executing Python code， which is really an interpreter。

And so that doesn't work， but if you have a compile binary。

That compile binary is essentially the text segment of your process so in this case when you start that process you are not going to load that process in RA。

 neither are you going to copy that process in virtual memory and create a text segment you are directly going to swap off the file that is stored on this。

That really are just。Optimizing for some display and not creating multiple copies。

So now if you have a standard page for where I'm just executing something in that probe process and I data instruction and that page is not in memory。

 I got to go fetch it from disk。But where is it on disk it's on the file system because I'm paging directly of that binary file Im not paging of the swap part。

Exactly。So the sense a few implications， first of all。The file system is now involved in P。

You are paging directly of the file system as well， not just the swap partition。

 so there is some paging activity that' is going to go to the file system as well if your text segments are actually stored on the file system as an opt。

You did not have done that。 You could simply copied that entire file into the swapwab partition and allocate it in that。

That would have been fine as well， but as an optimization， it decided not to lose。

So that' the first thing， so there's where to be。Page points on the swap partition and the file system。

optimizationim is just don't， hey， you have to make a copy。

 which means it's going to cost you somewhere and second youre going to。

Use more space than you need to with all of the data already on this。 Why make a second。I说 was。Now。

 the second implication is if you have an executing process。

That has stored its text segment or that swapping off the file as its text segment。

 if you delete that file while the process is executing， the process is going to crash。

And you can actually try this if you want， on minutes。

 you can just execute a process and write a C program。Compile it。

 start and while it does running if you delete the file， your process will actually crash。

Because now it cannot page in any more pages unless all of the pages are already in memory if it add another page for it。

 it's actually going to crash it right。They're are some os。I don't have Linux does it。

 but I know there are some voices that are smart enough and when you delete a file。

Your are paging of that file， it will actually make it invisible in the file system。

 but it will not release the data of those files it will contain。

 but those optimizations are extra optimizations they are to put in the file。Theたァ。

Some OSs will be smart enough to know that the user doesn't want this data。

 but the OS still needs it to swap off it for the process。that here。

So now let's go back to this picture， so this is the other kind of paid where you are actually。

Svicing the page file from the file system and you will see that in this case you have a VFS in the loop because got the go of the VFS is file server in a file server process so you are going to handle your page for。

 go to the file server saying please bring this file。嗯。

And this is where the disk cache is going to come in。 if you remember， I said earlier。

 there is a data structure that's called diskc。That this cash in this case。

 is simply storing blocks of。The text segment in memory。

So you will see here to read this carefully first。Essentially go and look for the five catch and if it's not there。

WeF say go， bring that page in and put it in the cache， and then you restart the entire call period。

This done your cache， so you essentially read that page and then it。

So the this blocked cache is in the virtual memory manager for this reason because you are off paging tech centers on the file system and you to keep some of them in memory。

Or sketch。So these are all additional details that are specific either to Linuxs or any。

Other OS this。等你给我宣楚。All right， so some now I'm going to switch to some other details。

 some data structures that you need to know about that。 So the first thing is， as I said。

 you have to track。Which regions of memory are allocated and which regions are in。まだのけ。

In early versions of Linux this was being done for physical memory in later versions of minutes you still have to do this but more for children。

Because physical memory in that case is speech。So a question is how are you going to track what is in use or not。

 there are two data structures you can use for either a bitmap or a linked list。

A bitmap essentially keeps a bit for every chunk of memory and mark0 or1 depending on whether it's in use or not。

Mix has this notion of clicks Yeah， I don't know what that word means。

 but it just essentially stands for a chunk of maybe。They don't call it a page。 They call it a click。

你做。So essentially a have one big per click， which you can just think is one big per。

Chunk of the way that looks like a page and you can essentially have that big shown that you'll see that there is the one means it's in use and zero essentially means it's not in so theres one。

Click for one bit per page。That's one way to track for an entire region of memory。

 whether it's physical or virtual albany。Clicks or pages are in use of not。

The other data structure is you can use a linked list and this is the second data structure shown here。

You have。Consider the piece that for the process。是。

It's tiny better than all there's the fastest parts of all and so on。But that's very youre saying。

Sone segment， allocate located Se， allocate segment allocate segments。

So just a link list of all of these regions。It is continuoustiguous。Thank you。

So these are data structures that。Dely see。Now。You will see in minutes there's still port for things like first fit and breast fit and so on that can scan through that link list looking for a chunk that is large enough for a new segment or a new process。

For early versions of meaning， this was done for physical memory。

 Now we still have to do this for what children。How you go into process。So now with that in mind。

 let's look at a little more hardware details to understand how paging works。

So first thing you want to know about paging is what the hardware needs to support。

 So typically a CPU needs a component called a MMMU for you to support paging at all MMU stands for memory management unit。

Typically an MU will have the picture has show that's a little better than this depict you'll see that the are green boxes there MWU will have an associated TLB which is going to essentially help you cache some parts of the page table and things of that。

So once Intel introduced MU and its hardware you could implement paging more efficiently。Otherwise。

 if you remember what I had said， paging it will cause a factor of two slowdown because a page table is in memory and then if you try to access that data structure to get good address translation youll don di so you need hardware support to speed this up all of that is implemented in your image the logic to good translation and so on as's a picture。

To show you how this works。 So here's an example。 Okay。

 so this is an M that has entry for a page table of size 16。 This is your virtual address。

In terms of bricks。哎， look at。You more significant bits that tells you the page number。

So essentially in this case， there's page number two because it's。我自有。く。

Baically look up the second increase， So that tells you the frame number that's 110。

 So you take 110 and you substitute this 110 in the。Physical address。

But that essentially has to be all done in hardware for you to make it efficient。

And you will use the clear B to do all of that as well for。Now。

 another concept that modern CPUs will provide is support for multi level page tables。

Does anyone know what a multi levelve page table is。Yes。One page。我。てどうす？ないと。

The lower level of fish do as。There are two levels of page table that you could see that there why would you need a multile page table to begin let ask that question this。

One the festival is too large。Pa cables would be too large。

 So let's assume that you have a single little question。

You a page table and its just a table and it's just a hash table。Aray， essentially。

 So if you had one level of pace table and when you start a process。

 you don't know how large it is going to get。RightBecause you don't know if the process is going to go a lot of malllos and it's going to become larger it's going to stay stable。

 so your pay table has to be pre allocatelocated and you start the class。

So if you don't know how large the process is going to get。

 you have to allocate the largest possible pace table for every process to allow it to grow to the maximum possible value。

So this might mean a lot of wasted space if most processes are going to stay small。

 you know allocated a giant pace table thinking that maybe the process will grow big。

That's going to waste memory because the paste table have to be stored in ground。哎。So what do you do。

Okay you make the page table two levels。 You essentially say that I have two level page table and the first level is going to be。

Also fixed， but it's smaller。 And then as the process grows。

 you essentially are in a second level of。And then you can allocate these things are allocated on the fly and then depending on how large the process goes。

 the second level entries grow only as the process goes， the first level is pre allocatelocated。

 these things can be dynamically。Okay， so thats a multi level paster It requires two levels of lookup。

 you are to go to table one， level one to figure out which of these second level entries to go to go there that tells you the。

Where have you seen this data structure before？おク。Probably seen it in a database class as well the input career class。

In the database， course sets is a binary tree， a B tree actually uses multi level。Okay。

 but you've seen it， if you've taken a worse class， you've probably seen it elsewhere。

AndThe exact same argument towards as to write some people。This is called a multile。

Just a tool in this case， two level would decay K levels。啊实。

We used it in a file system I nodes in a file system also use the same multilevel structure for exactly the same reason but when you create a file the OS or the file system doesnt know how large the file is going to be。

The index node is essentially exactly the same mapping as maps block numbers to locations on disk。

And the only way you are going to keep it efficient is to have a small。Data structure called the in。

 and then have multi levelve index that grows as much or as you need to。

 rather than creating a gigantic index for everything。

Exactly the same concept holds even from memory allocation。

 So more sophisticated processors will support multi level English and you see in this case。

 you have your address you have two。Offf food point as。They do 11 and12。

So that's something you want to keep in mind。Let's work。We'll skip the P andB go to separate。

So let's take a look at how hardware supports segmentation so that you get a better feel for how being to implement it。

So I said that every process has at least three seconds。

Start heap a text but typically processes will have more than three seconds that can have many segments。

What is shown in this picture？This picture shows an extreme case where every data structure that you allocate for the process is its own segment you want to create a large array。

 make it its own segment， you want to create a day maybe you want to create a hatch table。

 lets make it its own segment as so。So what this does。Now each of these。You see that's the start。

The text， youll see that there's a tree in that there。这个是他这。

They are located at the Mar phone segment and Melissa Bur table is also。

The good part about doing this is each segment can grow independently of others。

And so if you want to grow the particular segment， that segment can grow and other segments can stay the same。

 but that allows us some flexibility because we store heat segment independently and that continuous region heat segment can grow a shrink based on the needs of that process tech segment never changes incident that segment is static but the heap can grow stack can grow。

If there are data structures， the heap that are stored a separate sector， they can go and so on。

So that gives us that flexibility so depending on how much flexibility you want。

 you can actually have multiple segments in a process。Shared libraries are also their own segments。

And you can not only have shared libraries， as we see so the entire text segment can also be shared。

So there will a multiple shared segment which allows us to do this granular of sharing。バ processing。

Now there are many advantages and disadvantages of using paging as a we management scheme using segmentation we talked about this last time。

Okay。So' going to quickly talk about this here。So you say。干。

If you have these tables or data structures， it's much easier to change their sizes if you are using segmentation and page because paging has no concept of what is in the page。

Process is a collection of pages。The voice doesn't know what is in the page， Does it have code or。雷打。

But segments essentially have a purpose， either it has code or it has data。

 there are only two kinds of segments。So so we can essentially say this segment can grow because it's a data segment that so。

 The other thing you can do is in the text segment， you can make it readly。

Because code once you load for a process doesn't change， so typically text segments are made read of。

That's also a security measure。Because you make the code segment writeable。

 you are now vulnerable to things that code injection attacks and your hackers can essentially take over your process and inject code and start executing so you don't want that to happen so code segment。

Typically my readers。Data segments like stack and heap are read right。

 so you can write to them because you can change values of data that are stored and there and so on。

But data segments are also set to no execute， which means that you can never fetch something from a data segment and execute it on a process。

For the same reason。Because that's a security vulnerability。

If I could actually inject some code into an area and then tell the processes saying go to that location and execute that code that allows you to take over a process。

 inject malicious code and execute。typicallypically， a data segment is set to no execute。

There's hardware support to do is there's something called an inex bit on Intel processor which essentially stands for no execute okay that allows you to mark all the data segments as no execute because it became such a big problem that they introduce hardware features。

But typically if you have segment level information you can do these things very easy and that segments can be markeded as read only so you can't change it and segments can be marked as no execute so you can't execute anything and you have just read or right to it and so on。

All of that in comes with segmentation is harder to do in Beijing because you need to then assign semantic knowledge of what is in a page you can also make pages read only or no execute but you need to know what is in there by definition you know whats in a segment because you created that segment for a。

So you can assign meaning to it and have all these additional features assigned。So。

That's all I'm going to say here we wanted to。最近。What I'm going to show in this slide and the next slide is the picture of how Intel X86 processors have support for segments I talked a little bit about paging and let me not talk a little bit about segmentation What they should tell you is Intel processors allow you to do both segmentation and page so it's very easy to go segment that page。

这个不是。You mentioned that segments can grow in strength independently。

 but that will also depend on the size of holes in what extent they can， there will be a limit right。

It will depend on how much holes you have between two segments and there will limit to that certainly so this goes back to how you allocate segments so if you actually assign two segments very close to one another one of them is a data segment and it goes it will be limited by how much it can so there are only two things you can do at that point either given an error staying out of memory because if you do maloff eventually will get another or you got to move that segment or a bigger hole which involves memory cost。

So both of that extra work or causes inconvenience。

 so doing this well when you allocate segments to virtual memory regions is actually a smart thing to do。

 so you want to leave enough of a gap between segments to allow you to grow specifically in data set。

And how do you know and what is good enough based upon history？

So how do you know what's the good of gap， that could be a parameter that the OS designer fixs。

 for example。You could say every process at least gets。

The hole of a certain size because typically the heap or not the heap。

 the stack will be very small and the process starts。

 so you cannot give it a 10 by chunk and assume that it will be done so it will actually allocate the hole as much bigger。

And so that it can go so that all of those are designed decisions as to how large you make a stack by default。

现在过去。So let's talk a little bit about segmentation， So as far as In processor are concerned。

 there are two tables that are kept in hardware， There is something called local descriptor table and theres a global description。

They don't call the paste or not paste。 They don't call the segment table， but theyre essentially。

Segment table is called a descriptor table in Intel Archecturelingu。

Okay so this is a name for segmentable what they call a descriptor so essentially the global descriptor table is one for the entire system。

 every process has its own local descriptor segment table and then there is one the system why it is meant for the OSN system segments and so on。

How does all this work？So here is a picture， it looks fairly complicated and but it really not。

 so thats an entry in the segment table。Essentially。

 the only two things here that are really you care about is like a base register at a limit register I you store。

That tells me where does that segment start in virtual adverse space and what is the size？

There's all base are limited。So what you are going to do is you are going to use this selector。

Enry with segment do I care about because there are multiple segments of the process So if you need the fifth one you're going do that entry have five and then you're going to essentially that's going to be a table of several entries So we're going to look at the fifth one and then extract the base and limit list Okay then once to do that this hardware that is going to allow us to find actual address So here is our virtual address to take the virtual address and save segment as it did to get the segment I look up the right segment table entry that gives us the base address We take the base address and the offset and that gives us a 32 bit address on the 32 bit machine。

That be done。With this translation。And remember， this is segmented paging。

And I showed you a more general picture last time it said segmented paging has two levels of translation。

This has simply given us an address， but that's an address in virtual memory。

You not there any pay table lookups。So you will take that address and then you will do another level of translation。

 which you already looked at。Which is this。Because youre going to take that address。

 find the page number and then actually find a physical address that was essentially trying to figure out relative to based on a relative offset in a segment。

 what address do you have in the virtual address space then you take that virtual address space and say each page。

Maam do I need， And that requires us to go through the M logic to go second level of。

So that's something you want to keep in mind this is just given us a technical linear address。

 and here is what you have to do the next level of。Depending on whether material pay table。

 youre going to take that address。essentially find enough physical。

The good part is all of this are done in hardware。 the OS is not really doing much。

Other than executing a program that just generated and addresss and all of this is actually applicable of。

That is our intel architecture， that's what x86 does for。

Something you want to keep in mind because when you look at the code。

 you will see all of these things going on and you need to know this is what is happening with。

I this clear any questions here？This is obviously not Min specific， this is XA86 or intent specific。

Okay， but Linux is going to use it to implement and segment and pay。So。With that in mind。

 I'm going to show you a little more of the process manager and we'll see some things in there that are specific to memory band。

So here are some of the system calls that are。Implemented in the process manager。

 you already looked a little bit at4 and4。Ex which is here here which are going to allocate memory for us。

 so that's the part of the process manager that's intimately tied with memory allocation。

Spped and there are lots of others that have skipped form。即 you see that want here I。Re memory。

 so you can use that to do things like mallo dial memory。For can ex allocate memory for a process。

 user processes when they try to dynamically allocate memory and go back to the process manager。

 which then talks to the memory manager and allocates more memory。

Now this is a picture that here shows us an example of sharing entire text segments。

 so you will see here。There are two processes。Thats the segment table for process one。

 theres a segment table for process two， forget all the hex numbers here thats not importanted。

 only thing thats important is you see that a text segment for both。

A pointing to the same segment in virtual address space， or there's one segment。

But he put the stock on separate， so you' can see that there's a separate stock。

This is separation for each of this process。So you could ask why do I need to share a text segment across two processes。

 when will this actually happen？Okay， if you run two of the same process， you start two terminals。

 you start two of your。The programs for like。And what it was called for lab 2 if you start multiple copies of the same process。

Why should the West Lord those twice？It's going to essentially have only one copy and then share that text segment across processes In this case。

 the text segment remember is read doesn't gene， so it's perfectly safe to share it。

Same as true shared libraries。You have two processes that are different。

 but they still use the same library， youll load one copy of the library and the library segment will be shared。

So this allows us to make more efficient use， not have redundant copies and so on， and furthermore。

 in this case， the text segment can also be stored on the file system as we talk。

I'm actually already be on the assault fighter I。this does not。

There are quite a few optimizations that are used to make efficient use of virtuals space。

 memory and so。そして。Virtu Ispace with the。For glad space they shared。Thank。second。

So the question you are asking is， is there one virtual address case or multiple address space。

 is that your question so there is one swap space？When I say virtual address space in this lecture I actually mean that swap space so this could be a 10 gb disk partition。

 so that is our virtual address space， it will start from zero and go all the way to 10 gb in size。

So let assume assume get one large edit。That is shared across processes because there are multiple processes running。

 each of them is using some part of that list。So in that sense that virtual address space is sharedd now we have also used the term virtual address space to mean relative addresses for that process。

So each process has its own logical view that's independent of virtual memory。

 that is this week saying that I I'm a process of size n。

My actress is worth of0 and here is my tax segment。Theres my he that goes up here as the stack。

That grows up。 So each process thinks it's never looks like this。So以 generate。Virtual agacies。

 but those virtual aacies are relative to this virtual address。 So So we use that。

The term virtual in an overloaded manner as the virtual address space of a process。

 which is just memory you can see as the virtual memory。

Wwhich is not the same as the virtual address space or the process that just says that that's the swap partition on this from which I'm paging。

 so there are virtual addressesg that go from0 to n that's the disc partition this is the virtual addresses or related addresses in the process so slightly different things the term has been somehow misused in you。

我没有。有げなで。Atly to distinct concept。 The reason they call it virtual is essentially is distinct from physical。

 That's why I's called virtual。But virtual memory is not the same as the virtual adverse space that the processs。

Well these are addresses in virtual memory。 These are addresses in the virtual address。Is that clear。

So this is about segment sharing text segments。But if you look at the code again。

 you will see that there is a structure that is used to track holes that's called the O wrist。

The list of holes is that's what youre going to scan to allocate memory for a new segment or if a process completes。

 you're going to take that segment where you work it with that adjacent holes。

 make a bigger hole and reinsert it and things of that。

But that's the data structure you are to manipulate essentially allocate and realcate a memory from virtual memory。

And because physical memory space， so that's not used continuously。左边。

we talked about fork I mentioned some of this， but。What step so forth。again。

 you would see that essentially。Look， you'll see that there is essentially some memory management exploring on here。

あのけ。We for the time process that you essentially。that。

The process table so in case of four and exec are the two parts of the process manager that make very very close integrated with how memories allocated at。

So that's something you want to keep in mind， I want to go back to what fourth does we already talked about that。

So just to remind you that there's memory management that's implemented as part of work。

Save is2 exactly I。说。There are several other system calls in process management which you should know about but I'm not going to cover them in any detail。

 There are some that allows you to essentially do time when so on。

Maybe you are going to use some of this for your lab when you're trying to figure out the turn around times and so on。

 you use library functions， but those library functions essentially called some of these。

To figure out this is doing process accounting。 how long did the process run when it just started so。

There are several others that allow you to get IDs of processes， groups of processes。

 and so on with change process groups， which in this class probably have not known encountered much。

 but you should know they are there。And then there are， of course。

 calls that the process manager implements to allocate memory and whatnot and there is。Some不 do地。

so these are the three calls that are the most important。 Yeah， allocate memory。

 allocate some block up。We may be finger it and initialize memory by initialize。

There are some other calls that some voices support and I don't really know which does it。

 which says when you allocate a memory you should zero out its context。

As done for security reasons maybe I'm a process I put some sensitive data in my memory I allocated some memory in a free date if it just goes back to the free list and gets allocated some other processes it reads it it can find some other processes data so typically when you want to allocate new memory is good idea to zero it out some libraries do that and some don't but that's something that's an important consideration as well you want to keep things secure you want to zero things out or at least rewrite it with random bits so that other processes cannot see what was in that that was put in there by a three list process。

All things to keep in mind and implement at all。 So let me now take a few minutes。承在。

To show you some gold。So this is the main Giub。both of us go to an older worship。So let's take 3。1。

Theres an older version of Linux。And here if you're going into server us。

You'll see that there is no memory manager， Everything is in the process manager， there's no VM。D。

There is a process manager。And you will see again here。不多都。I love God see。

Youll see it says it concerned with allocating freeing arbitrary size of blocks in physical bill so in this case in 3。

1 there is no virtual memorys no paging， you assume that entire processes were always present in RAM。

And they were essentially allocated as a collection of segments。

 which means that this picture that you see in virtual memory was what physical memory？

That's what you see here vote essentially。Do equivalent length of to see that there are holes。

 then you can essentially you see this notion of a click that I was mentioning。

They have this abstract called the click， which looks like a paint， essentially in this case。

 it does1 kiloby or 4 kiloby。And you see that the's score to look for。 So here's three memory。Yeah。B。

So here is allocate menu， So this is what is going to implement something like。

First rate or west rate or something。Any policy that you want by scanning the list of all。

So I think just as an exercise， even though this is an old version of minutess that we do not touch in this class。

 you should just go to that version and just take a look at the code。

We have some fear for how things were。In a simpler version of the。Now。

What we have in this class is this one， 3。2。1。And you'll see here。To go to servers。

You'll see that now there is a process manager and the that's your process manager。

 But now your memory manager is now in the VM， the virtual memory manager。

So all of what was in the process manager Al。csmo here。

And now you will see that there is stuff you will see。Page filess dot C。

 because now you have to deal with paging and they might paging。

 So you have to deal with page files and whatnot。 So the code has it。Jane substantially。Between 3。

1 and 3。2 because they started introducing support for you hardware。This is what we will use in this。

the lab for this course， but it is good to see and compete。What has changed and so。 I mean。

 not a lot of code， but you get a good feel for how you can write a word very simple o。

It very simple。Now do you write a more modern one that uses a segmented page in？

The other thing I will mention here is。You see that there's a directly called R。

 Thats the architecture dependent。And you will see here， if you're going here。Intel theres R。

 The R1 is empty。Looks like it as of 3。2， at least support for R was not。Implemented。Xa x6。

 you will see that there's plenty of stuff。You will see that the page table。 C is here。

Because that is dependent on the architecture。Intel processors have a certain type of page table supports all of that is implemented。

这。Then， if you can go to。Or even more。These angle is 3。 feet。That's the US worship。

G has changed you look further here， so you got to go into Min。我。what my。啊。え。

I thought that they had support for。But yeah， so there I。I think there's a bit that there is some。

It's not it。 but in any case， if you have support for new processor。

 that's where you put it all the architecture in the patent code this level。

So that's the general lay of the land as far as mixed memory management description。

couple of minutes， are there any questions or。Lot of this is tied to。我打开队。

What memory management scheme is actually used and the modern and with the experiment looks as modern as any other over。

这被告。So， probably things for。If you look at 3。0， things are raised of six filess or so you implement at all of them。

How does the always know which architecture is there？

How does the OS knowledge each architecture that So this is designed and defined at compilation time。

 So when you compile your kernel， typically you set the architecture type in the make file So the binary thats created pulls the right architecture files and only compiles support from that。

So if you compile your Linux kernel， in this case by default， it's set to compile for x8x6。

 it's not going to run on some other attribute。SoSo the OS doesn't actually need to go because this the terminal is designed。

 the binary is designed to run on one architecture alone。

 the code might have support from multiple platform or if you compile it。

 its basically compile for one client。If you would compile a Linux kernel， which I'm not sure。

The Docker lab will require you too， but Linuxox is actually a support for many。

 many different architecture。 So one of the things you said in the make file is what architecture you want support for。

it basically pulls together all the architecture specific code。

 then you get architecture specific version。We're going to stop here。Theで start。

