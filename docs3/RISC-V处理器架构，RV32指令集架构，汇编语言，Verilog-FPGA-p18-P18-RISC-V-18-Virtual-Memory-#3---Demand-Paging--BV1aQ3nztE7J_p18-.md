# RISC-V处理器架构，RV32指令集架构，汇编语言，Verilog-FPGA-p18-P18-RISC-V-18-Virtual-Memory-#3---Demand-Paging--BV1aQ3nztE7J_p18-

![](img/6e9ac7ebae3d3122c5212eadf948f0f5_0.png)

Welcome to a video lecture series on virtual memory and paging。There are six videos in this series。

 and this video is part three of the series。These six videos are part of a larger series on the Risk5 architecture。

The previous video described how page tables are used and how page tree walks are performed。

In this video， we'll introduce and describe demand paging。

When there are more virtual pages than there is room for in main memory。

 some of those pages will need to be stored out on secondary storage。

We'll see that the valid bit can be used to get the kernelel involved when necessary to bring pages back into to main memory。

In this video， we'll define the concept of working set and discuss page eviction。

We'll see that it's important to know which are the most recently used pages and which are the least recently used pages。

We'll also discuss the dirty bit， which indicates whether pages have been modified and therefore need to be written out。

 and we'll discuss the accessed bit and how it might be used to determine which pages were least recently used。

 And finally， I'll describe the S V A D， E extension to the main risk 5 specification。Okay。

 with that， let's get started。I want to describe the A and D bits in the page sample entry。

 but in order to do so， we first need to learn about demand paging。😡。

So let's take a moment to describe what demand paging is and how it differs from what we've seen so far。

And will motivate this with an example。Let's imagine that we've got a physical memory of1 gigab。

 And at some instant of time， there are seven user processes running。 And to make the number simple。

 let's assume that each user process requires 100 mebytes。And for this example。

 let's assume that the kernel also requires exactly 100 mebytes。

 so with seven processes of 100 megabytes each， plus the kernel will need 800 megabytes of physical memory。

And by the way， in this discussion of demand p， let's ignore mega pages。

 That's a completely separate， unrelated issue to what we're getting into here。

So 800 megabytes is less than1 gigabyte， which is what we have to work with， so we're okay。

 everything will fit into memory。This is the assumption that we've made so far that there is enough physical memory so that every virtual page can be mapped into a physical page of memory。

But now let's assume that some more processes are started。

 and now the computer is running 12 user processes。So with 12 processes and with the kernel。

 we now need 1，300 megabytes or 1。3 gigabytes of memory。This is no longer smaller than one gigaby。

 so we don't have enough physical memory。The question is， what is the colonel to do。

And the solution is to use demand paging。Operating system kernels today implement something called demand paging。

This will allow the kernel to run a bunch of processes。

 even when they exceed the actual physical memory available on the computer。In other words。

 if you add the sizes of the virtual address spaces of all the running processes with demand paging。

 this number can now exceed the amount of memory available to store those processes。

Let me also mention something about the term paging， which is a bit vague。Basically。

 if a system implements virtual address spaces via page tables， then it implements paging。

If it also implements demand paging， which I haven't yet described。

 then you should probably say demand paging。If you hear the terms virtual memory or just paging alone。

 remember that this doesn't tell you whether demand paging is implemented or not。Probably it is。

 but these terms are more general and might refer to systems that do not implement demand paging and can only run so many processes before memory is exhausted。

And again， your Linux or UniX like system is almost certainly implementing demand paging。

With demand paging， the idea is that at any point in time。

 a process doesn't need access to all its virtual pages。Of course。

 it will need some pages in order to execute instructions。

 and that's called the working set of pages。But a process doesn't need its entire virtual address space for every instruction。

Instead of keeping pages for a virtual address space in memory。

 let's now think about it as keeping all the pages for the virtual address space out on secondary storage。

And by secondary storage， I mean permanent storage， like a flash drive or a hard disk。

The idea is that the kernelel will bring the pages the process needs into main memory when they're needed by the process。

All the pages will be stored out on secondary storage， but for some important recently used pages。

 there will also be a copy in main memory。The copy in main memory may very well have been updated and no longer exactly match the data that's stored out on secondary storage。

So when a page is stored both in storage and in memory。

 obviously the version in main memory is the more recent version that contains the current true data of the page。

As time goes on， the kernelel brings more and more pages from storage into main memory。

 consuming more and more of the physical memory。And at some point。

 all of the main memory will be used for pages and the kernelel will just run out of free unused memory。

Available to hold new pages。So at that point， the kernelel will need to move some pages from main memory back to permanent storage。

So。The colonel will select some pages。 We say that it will evict those pages from main memory。

 and it will need to copy their current value from main memory back to second storage。

 if it's changed。To make more room for pages in memory and to keep going。

 the colonel has to do two things。First， it has to select some in memory pages for eviction。

Then it must also write their current value their 4 kB of data from memory out to storage。

 if that data has been changed。For efficiency reasons。

 we want to keep the most important pages in memory。

 and we want to select unimportant pages to be evicted and moved back out to storage。

So what do we mean by important？Ideally， we want to retain pages in main memory that are going to be needed again real soon。

Obviously， we don't want to copy a page out only to have to copy that page back in immediately thereafter。

Of course， we can't know which pages are going to be needed again in the near future。So instead。

 we'll try to evict pages that haven't been used any time recently。To determine which pages to evict。

 we have this crucially important fact。Pages that have been used most recently in the past tend to be needed again in the near future。

Most programs have this behavior。They tend to use a small number of pages， at any point。

If a page is in use， then it will have been used recently and it will be needed again in the near future。

The pages that a process is currently using are called its working set。

Most programs have a working set that contains a small number of pages out of the huge number of pages in its address space。

Over time， the working set will change and shift around。

 and the size of the working set actually depends on how large an interval of time you're looking at。

In fact， you can go down a rabbit hole here and collect statistics on working set， size， and so on。

 but all you really need to know is this。The colonel just needs to know which pages were used recently。

Perhaps we want to know which page was most recently used， but what we really want is the opposite。

 we want to know which pages were least recently used。In other words。

 which page hasn't been used in a long time？The chances are that that particular page won't be needed again in the near future。

 And that page is just not an important page。At least at the current moment in time in the program's execution。

 the program is apparently just not using this page right now。

The idea is that since the least recently used page hasn't been used in the long time。

 it probably won't be needed again in the near future。

 And that is exactly the page we want to choose for eviction。If memory is short。

Then the least recently used page is the page that the colonel should select to write back out to secondary storage。

That's the best guess as to the page that is most unlikely to be needed anytime in the near future。

Of course， the question is， how do we know which pages are recently used and the opposite。

 which pages were not recently used。Fortunately， the Risk 5 hardware provides some support that we can use to help us answer this question。

Let's review the bits in the page table entry。We saw the bits that tell whether a page is readable。

 Wriable and or executable。 And we also saw the U bit。

 which determines whether the page is a user page or a supervisor page。

If an attempt is made to access a page in a way that is forbidden。

 then the access is blocked and a page fault exception will occur。

This would be an attempt to violate the privilege and protection system。

 So the colonel will generally deal with the exception by just aborting the process。

We've also got the valid bit， which tells whether the page has been allocated or not。

not every page in a virtual address space is mapped into anything。

 There can be holes in the virtual address space， and the pages corresponding to these holes are simply not valid。

In fact， with the virtual address space of say 4 gigabys。

 most of the pages of the address space are likely to be unallocated and therefore invalid pages。

And attempt to load， store or fetch an instruction from an invalid page is going to be an error。

 And it would also cause a pagevault exception。Now there are actually three different kinds of page faults。

 and if there's any problem， then one of these three would be signaled。

And exactly which exception type occurs depends on what type of operation was being attempted。

The program was either trying to execute a load instruction or a store instruction or to fetch an instruction。

But here's the cool thing。The valid bit can also be used to support demand paging。

With a kernelel that does demand paging， some of the pages may actually be valid。

 but these pages are just not currently resident in memory。We say that these pages are paged out。

 meaning that the only copy of the page is stored out on secondary storage。

 The page is not currently resident in memory。The colonel can also use the valid bit for such paged out pages。

The idea is that a page that is not resident in main memory will have its valid bit cleared to0。

If the program tries to access a page that is not currently resident。

 the hardware will also cause a page fault。But this is not an error on the part of the program。

 The user program doesn't even know which pages are paged out。 And， in fact。

 it doesn't even know that demand paging is happening。So now。

 if an invalid page is encountered and a page fault occurs。

 the trap handler and the colonel will run， and the colonel will look to determine what the problem is。

If the program is trying to access a page that has never been allocated or mapped to anything。

 then it's an error on the port of the program and the colonel would simply abort the program。

On the other hand， if the page exists but is not currently resonant in memory。

 then it's not an error。Instead， the colonel will need to bring this page back into memory。

So the colonel will read the page from secondary storage back into memory。

And then it will adjust the page table to point to the newly allocated physical page。

And then it will change its valid bit to one and will restart the program。

And the instruction that caused the page fault originally， would be retried。

It will be executed again， and this time， however， the valid bit will be set to one。

 and so the instruction would work fine。So。You can see that the valid bit really has two functions。

First， it's used to flag pages that are simply unmapped and not allocated in the virtual address space。

Accessing these pages will get your program aborted。And second。

The valid bit is used to flag pages that are part of the virtual address space。

 but that are not currently resident in main memory。

Accessing these pages will cause the page to be moved back into memory。

 and this is the demand of demand paging。These pages are moved back into main memory， on demand。

The program will continue executing， it will never be the right wiser。

It will never know that the page faultult occurred or that there was ever any colon involvement。

 except possibly for a small delay in execution time。Now that we know about demand paging。

 we're ready to describe the dirty bit and the access bit。

The dirty bit in the pageable entry will be set by the hardware whenever a page is modified or written to。

This will come in handy whenever a page is chosen for eviction。

 That is when it's chosen to be moved from main memory out to secondary storage。

Does the colonel need to write the page out， Well， maybe， but maybe not。

If the page has been modified while it was in memory， then， yes。

 the new value must be written out to secondary storage before we can recycle the physical page it occupied and reuse it for something else。

Whenever a page is selected for eviction， if the hardware has set the dirty bet。

 then that page must be written out to secondary storage。But if the dirty bit is still 0。

 then the page has not been modified。The copy sitting out on secondary storage is identical。

 So there's no need to write it out。And whenever we read a page back into memory。

 we can go ahead and clear the dirty bit since the inmemory copy is identical to the copy out on secondary storage。

Also， the colonel may from time to time， decide to write out a page proactively。

 that is not when there is a particular demand for more memory space。

This might be done when the colonel is not busy with other stuff in order to save some time later when it actually does need more space。

If a page is copied out to storage， but also remains resonant in memory。

 then the dirty bit would also be cleared since the two copies are once again identical。

The in memory page is no longer dirty， and we say that it is now clean。

If later this page is chosen for eviction， there won't be any delay since clean pages don't need to be written out。

 and the space can be recycled immediately。Every page table entry also contains a bit called the A or accessed bit。

This bit can be used when the colonel is trying to select a page for eviction。Of course。

 we'd like to evict the least recently used page。Recall that we want to know whether a page has been used in the recent past。

 and if so， we'd like to keep it in memory and select some other page for eviction。

And the access bit can help here。So the hardware will set the access bit whenever the page is used。

 either read or written。I also want to mention an optional risk 5 extension called S V， A D。

 E or the supervisor mode， virtual memory， accessed and dirty bit exception extension。By default。

 if a page is accessed or written to the A and D bits in the relevant page table entry would be changed to one。

But if your core happens to implement the SVADE extension。

Then the hardware will still check the A And D bits as before。However。

 instead of modifying them by writing the page shapeple entry back out to the page tree node。

 it causes a page fault exception instead。Requiring the hardware to perform a right back to the page table tree and an atomic update of that might be too much of a burden to place on the hardware。

So instead， with this extension， the core just does a page fault instead of setting these bits directly。

 And then the colonel could take whatever actions it wants to。The thing is that， as described so far。

 the simple distinction between accessed or not accessed is a bit crude。

 It might be better if the colonel could keep track of exactly when the page was last accessed。

So to do that， the colonel would need to get control and then it would record the current time of the access or something like that。

You know， I've sketched out here an algorithm， but I don't want to bog down going over this algorithm。

 My goal with this video is to describe what the risk 5 hardware does and not to describe the various algorithms that might make use of the risk 5 hardware。

This is a good stopping point。In this video， we covered the basic ideas behind demand paging and discussed how the risk 5 hardware can be used to implement demand paging。

In particular， we describe the dirty and accessed bits of the page table entry。In the next video。

 we'll introduce address space identifiers and talk about the SATP register。

It contains more than just the address of the route of the page table tree。

And then we'll talk about the translation leukcoide buffer and how it would be implemented。

At once we understand the tailby， we can see what the global bit is and why it's needed。Before I end。

 let me encourage you to like， subscribe， share and comment if you'd like to show your approval for this sort of YouTube content。

But in any case， thanks for watching， and I hope to see you in the next video。



![](img/6e9ac7ebae3d3122c5212eadf948f0f5_2.png)