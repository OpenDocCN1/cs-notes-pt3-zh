# RISC-V处理器架构，RV32指令集架构，汇编语言，Verilog-FPGA-p16-P16-RISC-V-16-Virtual-Memory-#1---Page-Tables,-PTEs,-Sv32--BV1aQ3nztE7J_p16-

![](img/2aea54bad80210dd157f129b36ded58c_0.png)

Virtual memory， virtual address spaces， paging。 These are fascinating concepts。

 If you're looking for both an introduction and thorough description of these topics。

 then this is the lecturer for you。Frankly， I'm particularly interested in this aspect of computer architecture。

 and I've been looking forward to making this video series because this step is very interesting to me。

😊，Virtual memory and paging are complex topics and full of details。

 But you'll see how cool this scheme is once you understand it。 This stuff， for some reason。

 just tickles my brain。😊，All the main computers， Intel， arm， risk 5 have this capability。

 but its implementation differs in the details。Because of all these minor differences。

 which are completely irrelevant to the main ideas。

 trying to describe virtual memory and paging in a general way。

 just makes it so abstracted and full of assumptions and notation。

That it makes much more sense to learn about it by studying a particular concrete example。😰。

Some topics are best studied in the abstract， but paging is not one of them。

Virtual memory and paging are implemented by Intel， arm and risk 5 in pretty much the same way。

The main concepts are the same。 It's just all the details that differ。

Once you understand how this works on one machine， learning the other implementations is pretty straightforward。

And if you are going to learn by example， I recommend first studying the risk5 implementation instead of say。

 the Intel or arm implementations。Risk 5 was designed more recently with the benefit of the experience of the earlier systems。

 So it's a bit cleaner and easier to understand。Even if your goal is to understand Intel or arms implementation。

 starting here is a smart approach。You need to understand the main ideas first before you can handle all the details。

 and with older architectures， the main ideas tend to get buried under details and historical baggage。

There's a lot of material here， so I'll be covering virtual memory。

 address spaces and paging over six videos。Here's a rough outline of what I'll be covering。

These videos are part of a larger series on the Rik 5 architecture。

 but they can be watched independently in isolation。 You don't need to know anything about riskk 5。

 like which registers or instructions it has in order to get the full benefit of these six videos。

I'll only assume you understand assembly programming for some architecture。

 but not necessarily for risk 5。These videos can function as a first time introduction to virtual memory and paging。

Or for more experienced people as a specification for paging as it's implemented on risk 5。

And to get started， I'll begin by going over the basic concepts。

 but I'll move quickly into specifics。There are a lot of details and complex ideas that I'll cover pretty quickly。

 So if you are new to this topic， then at some point。

 you're going to bog down and get overwhelmed or confused。

If you're a serious student intent on acquiring this knowledge。

 then I recommend you be alert to the moment that you start to struggle。 And at that point。

 just stop。 Go back。And start over from the very beginning to solidify your preparation for the material that's giving you problems。

I think with enough repetition， any one can learn anything no matter how complicated it seems at first。

This is neither a university lecture nor YouTube clickbait En。Instead。

 these videos offer a complete but fast paced description and documentation of how virtual memory and paging are implemented on the Risk 5 corere。

There's a lot here。 You're going to need to study it rather than just watch it for entertainment。

 especially if it's new to you。 And if you really want to acquire this knowledge。And by the way。

 if you'd like to see more content like this on YouTube。

 would you please do me the favor to like and subscribe？Also。

 I think sharing and commenting have a big impact on the algorithm。

And I certainly enjoy reading viewer comments as well。Okay， that's enough for this introduction。

Let's begin with a basic concept of a virtual address space。

Each user program lives in its own virtual address space。

 and this address space contains all its code and data。

 but none of the code and data of the kernel or other processes。

Virtual address spaces can be contrasted to the one and only physical address space。

The physical lateralspace contains the main memory and the various memory mapped I devices。

Each of these has a fixed address that's determined by the hardware。

The physical address space is managed by the kernel。

 which uses it to implement a virtual ladder space for each of the user processes。

Each virtual ladderer space is broken into a number of virtual pages， and similarly。

 the physical ladderer space is divided into a number of physical pages。With risk 5。

 the page size is fixed at 4 kB。 Each 4K virtual page will be placed into a 4K physical page。

 And how this is done is the topic of this video。Here's a picture showing a single virtual address space and the physical addressro space。

And each is broken into a number of pages。This diagram indicates the physical address space of this system contains some memory here and some I devices located at these physical addresses。

The pages of the virtual address space are mapped into physical pages， and here's a sample mapping。

For example。When the user program reads rights to address0。

 which is in the first page of the address space as the user program sees it。

 it's actually reading or writing to this page here of real memory。

We also see that some areas of the physical address space contain nothing。And also。

 some pages of the virtual address space are unmapped and are effectively empty and unusable。

And we also see that a page containing an IO device has been mapped from this page in the virtual address space。

 which gives the user code the ability to read and write to that particular device。

Here is another virtual ladderer space that exists at the same time。

You can see that its pages are also backed up by physical pages。

 but it uses a different mapping and different physical pages。

Both these processes can be in memory and execute at the same time since they use different parts of the physical memory。

At any time， the colonel will be managing many virtual address spaces。

 one for each user process and possibly one for the kernel itself。I'm only showing two here。

 but it's enough to give you the idea。😡，Also， in real outer spaces， there would be many。

 many more pages than I have room to show in this diagram。To simplify。

 let's get rid of all but one virtual address space。

 and let's focus on the mapping from virtual pages to physical pages。

Virtual addresses are translated into physical addresses by the hardware。

 and this is done using a page table。There's one page table for each virtual address space。

 Each virtual address space has its own page table。

The page table can be thought of as a function that's given a program generated address that's a virtual address。

 and it translates it into a physical address and some protection bits。

This mapping is used every time the user process executes a load instruction or store instruction or fetches an instruction。

The address used in loads and stores is a virtual address。

 and it will be translated into a physical address by the hardware。And when fetching instructions。

 the program counter is used， and it contains a virtual address。

Before the hardware can retrieve an instruction， it must first be translated into a physical address。

This mapping is implemented by a so called page table， which is a data structure in memory。

Hardware must read from this data structure every time memory is accessed。In fact。

 each instruction fetch may require several additional memory read operations。

So in order to make this scheme efficient and usable。

 we also have something called the translationlation lecoide buffers or TLBs。

These are nothing more than a cache of important entries in the page table。

 which actually makes it unnecessary to read from memory most of the time。

So I'll be describing TLBs later on。Also， each virtual page can be marked with access privileges in order to implement security and protection。

Each time the page table is consulted to map a virtual address into a physical address。

 these security privileges are also retrieved。The hardware will check to make sure the operation is allowed and prevent any access without proper privileges。

So we can mark a page as either readable and or writeable and or executable。

 which determines whether we can load from the page or store into the page or fetch instructions from the page respectively。

😡，If， for example， the program attempts to store into a page that's not marked writeriable。

 then the hardware will generate a page fault exception。And normally。

 the colonel will then abort the process with some sort of error message。

We can also mark pages as either valid or not。In the previous slide。

 we saw virtual pages that were not mapped into physical pages， and those were colored gray。

Any attempt to access such a page would cause a page fault。Virtual address spaces are big。

 typically4 gigab， but most of the pages are never needed。

 And so no physical memory is actually consumed。These are then said to be invalid。

 that is unmapped pages。Also， we can mark each virtual page as either a user page or a supervisor page。

There's also a single you protection bit。If it's set to one， then this is a user page。

 And if it's clear， it means that this page is a supervisor page。Recall that with Rik5。

 user programs are run in user mode and the kernel runs in supervisor mode。

Some pages belong to the kernel， and these would be marked as not user pages。

User code that is code running in user mode can access pages that are marked you。

But any attempt to access a kernel page by a user mode program would result in a page fault。

To protect against malware， we want to make sure that any code in user pages is never executed with supervisor privileges。

So for that reason， the kernel that is any code running in supervisor mode may only access supervisor pages。

Any violation of this would cause a page fault。Actually。

 the Risk5 architecture prevents the kernel code from all accesses to user pages。

 including load and store instructions。However， in some circumstances。

 it's necessary for the kernel to get data from the user's address space and store data back into the user's address space。

For example， the passing of arguments to and the returning of results from system calls sometimes requires this access。

So for this， there's a bit in the status register called SUM for supervisorvis user memory access that can be used to override this protection。

If the kernelel temporarily sets this bit to one， then loads and stores to pages marked as user pages would now be allowed。

With Rik 5 and some other systems， too， the page size is fixed at 4 kiloB。 That is 4096。

Since 2 to the 12th is 4096， we can use 12 bits to select any byte within a page。

All pages are required to be aligned on page boundaries。That is。

 each page must be located at an address that's evenly divisible by 4K。

 which means that the lower 12 B will be  zeros。Every address， whether virtual or physical。

 can be broken into two parts。The upper bits can be thought of as the page number and the lower 12 bits are the byte offset into the page。

We'll see that the page tables really map page numbers to page numbers， not addresses to addresses。

They map a virtual page number into a physical page number。

The offset portion of the address is just copied over， unchanged。

There's a 32 bit version of risksk 5 called RV32， and there's a 64 bit version called RV64。

 and on this slide I'm showing all the options with regard to virtual memory and paging。

With 32 B machines， paging is either turned off or it turned on。If it's off。

 there are no page tables and no virtual memory。 All addresses are physical addresses。

But if paging is turned on， then every memory address generated by the program is a virtual address in some virtual address space。

The current page table， in effect at the moment， determines which address space。

Registers are 32 bits in size， so every address generated by the program will be 32 bits in size。

The page tables will map this into a 34 bit physical address。

The 32 B addresses limit the size of address spaces to 4 gigab， but with paging turned on。

 a 32 B machine can actually access and use a 16 gigab physical memory。

Risk 5 describes a number of paging schemes called SV 32， SV 39， SV 48， and SV57。

With 32 bit machines， there's only SV32。A given 32 B core may or may not implement S the 32。

 So paging might be hard wirered to off for simple core。Now in this video。

 we'll spend most of our time talking about SV32， and once you understand that。

 the others will be pretty simple to understand。On 64 B machines， the registers are， of course。

64 Bs in size。 so programme generated addresses that is virtual addresses would be 64 Bs。

But the upper bits would be ignored。With SV 39， only the low order 39 bits are used。

 The upper 25 bits are just ignored。And this allows a much larger virtual address space。

 actually a half a terabyte。And virtual addresses are mapped into a 56 B physical address space。

 accommodating a truly huge physical address space。All these systems are quite similar。

 with the main difference being how large the virtual address spaces can be。So for SV32。

 the virtual addresses are 32 in size for SV39， the virtual addresses are 39 bits in size。For SV48。

 there are 48 bits and for SV57， the virtual addresses are 57 bits in size。For 64 bit machines。

 all physical addresses are 56 bits。Of course， no system is likely to have this much physical memory。

 So some of the upper bits of the physical address will be ignored by the hardware。

And a given 64 bit core may or may not implement all of these paging options。

We'll see later that each page table is represented with a tree。

The primary distinction between all these options is how many levels the page table trees will have。

SV 32 will use2 level trees。 SV 39 will use3 level trees。 SV 48 will use four level trees。

 and SV 57 will use5 level trees。Now， let's begin our description of SV 32。

Phys addresses are 34 bits in size， and we can see that every physical address can be broken into two pieces。

 a page number， which is 22 bits， and an offset into the page， which is 12 bits。

22 bits gives us4 million pages， actually the exact number a power of two。

And 12 Bs for the offset gives us 4000 bys in each page， or actually 4096 to be exact。

And that multiplying 4 million times 4000 gives us a 16 gigabte physical address space。

If you want a data structure to map virtual page numbers to physical page numbers。

 which is really just mapping integers to integers。

 you might consider arrays or linked lists or maybe trees。Now。

 rays won't work because we have some huge gaps， and we don't have time for linear searches of linked lists。

 And you might also think of binary trees or red black trees or something like that。

With a binary tree， each node has two children， what we actually use is something called a radix tree。

With a radix tree， each node has in children。Here's a Raix tree where each note has four children。

The SV32 approach uses a Radix tree where each node has up to 1，024 children。

These trees spread out very quickly， so for an SV32 page table， we need only a two level tree。

And note that2 to the 10th power is 1024。With just two levels of interior nodes。

 we get to 1 million leaves。 And this is exactly what we need for our 4 gigabte virtual address space。

This tree is full of what we call page table entries or PTteEs。

The tree contains 1 million page table entries， and there's one for each page in the virtual address space。

 So for every virtual page number of which there are 1 million。

 the hardware will search the tree to get the page table entry that describes it。

Here's a picture of an SV32 page table， which is a two level tree。

Theres a control and status register called SATP， which I suppose stands for Supervisor address table pointer。

 and this contains the address of the root node of this tree。

Each node is an array of 1024 page table entries。Each page table entry points to a node at the next level。

Since a page table entry is 4 B in size， Each note is exactly the size of a page that is 4 kB。

The page table entries in the root node point to nodes at the next level。

 and we can call these internal page table entries。😡。

And the page table entries at the bottom level point to the actual data pages。

 and we can call these leaf page table entries。And then at the bottom。Beyond the page table nodes。

 we have the 4 kilobyte data pages。 these pages contain the user， code and data。

 these are the bytes that are actually in the virtual address space。Here's another diagram。

 representing a page table tree。We've got the page size， number of page table entries per page。

 the number of data pages， and the size of the virtual address space。

We see that each node in the tree is an array of 1024 page table entries。

 and shown down here in green are the data pages。Now， this tree seemed to be fully populated。

 but in reality， many of the pages will be missing， as Ive now shown here in gray。

These pages are simply not allocated， and they don't take up any memory space。

We see missing data pages and we see missing nodes within the interior of the tree。

This gray indicates sections of the virtual address space that are simply invalid。

Any attempt to access data on an invalid page would cause a page fault。

Now let's take a closer look at the page table entries。And with SV32。

 they are four bytes in size and have this format。The first field is the physical page number。

Recall that we're using 22 Bs for physical page numbers。And then we have a bunch of bits。

I'll be describing all of these later in detail， but for now， let's just list them out。

The valid bit indicates whether this page table entry is valid or not。

The invalid stuff is exactly what was shown at grayray on the previous slide。

Then we have bits to indicate whether the data page is readable， ridriable， and or executable。

And then we have the U bit to indicate whether the page is a user page or a supervisor page。

Then we have bits called Global， Accessed and Di， which I'll be describing later。

And then we have a couple of bits that the hardware will simply ignore。

 the kernelel can use these bits in whatever way it wishes。

All these bits are important and used for a leaf page table entry。

 That is a page table entry that points to a data page。Every data page must be either readable。

 wriable， or executable。😡，If you can't access the data page at all， then what would that even mean。

So the readable， writeriable and executable bits are used to differentiate between a leaf page table entry。

 which Im showing here and an interior page table entry。😡。

The page shape entries in interior nodes should have these three bits set to zeros。Now， with S V32。

 which uses only two level trees， the only interior node would be the root node。

 but for 64 bit machines using page table trees with more levels。

 all interior nodes must have these three bits set to zeros。The page table entries at the leaf level。

 that is page table entries that point to the actual data pages should have these three bits all set to something that's non zero。

 at least if the page table entry is valid at all。Okay， I think that's enough for this video。

In this video， we introduced the concepts of virtual address spaces and the physical address space and showed how each is divided into a number of pages。

We talked about how a page table is a mapping from virtual page numbers to physical page numbers。

Each page is 4 kiloB in size。 So the offset into the page is the lower 12 bits of any address。

 and the upper bits give the page number。The page table is represented by a tree， stored in memory。

With SV 32 on 32 bit machines， the tree has two levels， while 64 bit machines use SV39。

 SV 48 and SV 57 with3，4 and 5 level trees respectively。

Each node in the page table tree is an array of page table entries。

Interior page table entries point to nodes at the next level of the tree and leaf page table entries point to the actual data pages。

Finally， we looked at the format of the page table entries。

Each virtual page has a number of protection bits to indicate whether that page is readable。

 writeable or executable， and whether it must be accessed in user mode or by code running in supervisor mode。

We also saw that each page in the virtual address space is either valid or invalid。In the next video。

 we'll describe how the memory management unit walks the page table tree in order to transform a virtual address into a physical address。

You might be curious about how that's done， but that's for the next video。So before I end。

Please remember to like， subscribe， and share， and perhaps even comment if you want to to show your approval of this sort of YouTube content。

Thanks for watching and I hope to see you in the next video。



![](img/2aea54bad80210dd157f129b36ded58c_2.png)