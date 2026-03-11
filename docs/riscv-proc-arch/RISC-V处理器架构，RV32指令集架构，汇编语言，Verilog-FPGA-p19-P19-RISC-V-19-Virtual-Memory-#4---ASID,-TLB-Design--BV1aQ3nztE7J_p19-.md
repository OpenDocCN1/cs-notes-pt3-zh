# RISC-V处理器架构，RV32指令集架构，汇编语言，Verilog-FPGA-p19-P19-RISC-V-19-Virtual-Memory-#4---ASID,-TLB-Design--BV1aQ3nztE7J_p19-

![](img/7ba56c68cfb5cb399825583547900703_0.png)

Welcome to another video in a series on virtual memory and paging。😊。

There are six videos in this series， and this video is number 4。

These six videos are part of a larger series on the Risk5 architecture。In the last video。

 we described demand paging。Demand paging allows the total amount of virtual memory to exceed the actual amount of installed physical memory。

As pages are needed， Page faults occur， and the colonel will respond by reading pages into memory from secondary storage。

We saw that most programs have a fairly small set of pages that they need。

 and this is called the working set of pages。From time to time。

 the colonel needs more physical pages， So it'll select a page in main memory to evict。

 which means to write it out to secondary storage。The page table entries contain a dirty bit。

 which can help the colonel to know when it necessary to copy an evicted page back to secondary storage。

Obviously， the colonel doesn't need to copy a page if it hasn't been modified since the last time it was written out to secondary storage。

We also discussed the accessed bit and suggested that this might be useful to the colonel in selecting pages for eviction that have been least recently used。

In this video， we'll see that there is such a thing as an address space identifier for each virtual address space。

We'll also look at the SATP register in detail and see that in addition to the address of the route of the page table tree。

It contains the address space identifier。It also selects which paging scheme is turned on。

Then I'll describe the translation lecoide buffer。 So we'll see how that functions。

And once we know about the TL B， the importance of the addresser space identifier will become clear。

Will also describe global pages， and the global bit。Okay， let's get started。

When the operating system is running many user processes。

 each will have its own virtual address space。 So there will be a bunch of address spaces。

 and consequently， many page tables。There's a whole page table tree for each different address space。

To implement multitasking， the kernelel will be switching between user processes constantly。

 and this is called time slicing。Before the colonel starts at time slice for some particular process。

 it'll need to install and make active the page table for that process。And to do this。

 it will load a pointer to the root of the page table tree into a control and status register named SATP。

SATP points to the page table tree that will be used during the process's time slice。

To make virtual memory usable and to avoid a huge number of memory accesses to the page table。

 all modern processors implement a so called TLB or translation licoide buffer。

This is sometimes called the address translation Ca。

The T L B cash is used by the coreps whenever possible。 This makes adder's translation much faster。

 and it makes the whole virtual memory scheme practical。But， there's a problem。

Which TLB entries go with which page tables？😡，Imagine that the kernel is ready to switch from one process to another。

 so it loads SATP with the address of the new page table for the new process。

But the TLB is full of cached page table entries from the old page table from the previous process。

So if the core uses these old page table entries to avoid accessing the full page table。

 it's going to be using incorrect page table entries and this is going to cause havoc。😡。

The solution is really quite beautiful。The idea is to assign each virtual address space a unique number。

 So the address spaces are numbered 0，1，2，3， and so on。

And this is called the address space identifier or AcId for short。For 32 bit machines。

 riskk5 uses a 9 bit address based identifier， and for 64 bit machines。

 riskk5 uses a 16 bit address based identifier。9 bits will accommodate up to 512 different address spaces at the same time。

 and 16 bits will accommodate up to 64 k address spaces。

The translation licoide buffer will use the address space identifier to keep page table entries straight。

When a pable entry is stored in the translation liukcoide buffer。

 its address space identifier is also stored in the TLB as part of the entry。Then， during execution。

Each time the core needs to translate a virtual address。

 It'll first check the T L B to see if there's a matching entry。 If there's a matching entry。

 the core will also check that the address space identifier for the entry matches the current address space identifier。

If they match， then everything is good， the cached page table entry is used。

 and the core avoids going to memory to read from the page table。

But if there's no matching entry or the address space identifier is not current。

Then the core will have to read from the page table tree in memory。To repeat。

Each page table entry cached in the translation licoide buffer is also tagged with an address based identifier。

At every time the address translation cache is used。

 the core will search for an entry that matches both the virtual page number and the current address space identifier。

Now let's look at the SATP register in more detail。This is a control and status register。

 which is accessible by the colonel running in supervisor mode。For 32 bit machines。

 it's a 32 bit register with this format。Bit 31 tells whether paging is turned on or not。

 and if it's a zero， there is no virtual memory and the other fields are just ignored。

 Every program generated address would be used as is as a physical address directly。

But if paging is turned on， then the second field contains the address space identifier。

 and the third field contains the address of the root of the page table tree。

The combination of the acidId and a pointer to the page table describes the current virtual address space。

Since only two level trees are possible with RV 32， if paging is turned on。

 then we get the SV32 scheme that we've been focusing on。And by the way。

 a given core might not even implement virtual memory at all。 And in that case。

 SATP would be hard wired to 0， forcing paging to be off for all time。

All node in the page table tree must be aligned on even page boundaries。

 So for the address of the root of the page table tree。

It's sufficient to simply give the physical page number。

 The core will fill in the lower 12 B to give a 34 B page aligned address。

When the colonel does a time slice and switches to a new process。

It has to load the SATP register with a new value that contains both the aId of the new address base and a pointer to the page table route for that address space。

For 64 bit machines， things are quite similar。With RV 64， the control and status registers。

 including SATP， are now 64 Bs in size。And here's the layout of SATP for 64 bit machines。

As you can see， the upper field is enlarged to four bits。

 and the ater space identifier field is enlarged to 16 bits。

And the physical page number of the root of the tree is enlarged to 44 Bs。

The upper field tells whether paging is turned on or not， and if it's on。

 whether the course should use the SV39 scheme with 3 level trees or the SV48 scheme with four level trees or the SV57 scheme with 5 level trees。

The other bit combinations are reserved， and shouldn't be used。Also。

 your corps might implement some of these schemes， but not all of them。

I suspect that your core probably doesn't implement SV 57。 after all。

 who needs such gigantic virtual address spaces。As I mentioned。

 now the outer space identifier is 16 bits and the physical page number is 44 bits。

With 44 bits plus the 120 bits that force it to a page aligned address。

We see that the SATP register effectively contains a 56 bit physical address。

 and this is the address of the root of the page table tree。Of course。

 most systems would almost certainly ignore some of the upper bits of the physical address。

But all these paging schemes support a potentially very huge physical address space。In fact。

 with a 56 B address， it's 64 petabytes or about 70 quadrillion bys。To see how this all works。

 I want to describe an implementation of the translation leukcoide buffer。

Let's restrict ourselves to 32 bit machines with SV32。

And I want to make clear that the implementation described here is purely conceptual and hypothetical。

The Ri 5 spec doesn't describe any particular translation leaide buffer implementation or go into any of the details like this。

 But I wanted to show you a concrete TL B design。 so you can see how the memory management unit works。

Now， I've actually implemented a translation leukcoide buffer very much like this in Verrlog。

 So I can say that while this TLB is purely conceptual and fictional。

 it is nonetheless less realistic， and it would be workable。So first of all。

 the TLB is an associative memory。It consists of a number of entries shown here with one entry per line。

Each entry closely resembles a page table entry， but there are a couple of differences。

 For one thing， the two bits that were reserved for software use are not stored in the TLB。

Program code can't access these entries directly， so there's no reason to store those bits。

But most importantly， associated with each line is a key。

 and the key consists of the address space identifier and the virtual page number。

This is the search key。 So this is an associative memory。 So to retrieve an entry。

 a search key is provided， and the hardware responds by providing an entry whose search key matches if one exists。

So a search may result in a match， or maybe there is no matching entry in the TL B。

 and the corps will then have to do the page table walk after all。

The M M U or memory management unit is the part of the core that manages the translation lecoide buffer and performs a walk of the page table tree。

 if needed。The MMU is given a virtual address and the current SATP from which it can extract the current address based identifier and the address of the root node of the page table。

The memory management unit will return the physical address and the associated privilege bits。

 which are later used to determine if an exception must be triggered。

The idea is that the memory management unit will use the current address based identifier and the virtual page number from the virtual address as the search key into the translation licoide buffer。

If there is a matching entry， then the MMu will use it。Otherwise。

 the Emmeu will walk the pagetable tree。This will involve a couple of memory reads。

 as we described earlier， and it'll end with the retrieval of a leaf page table entry。Then。

 in addition to building the complete physical address to be returned。

 the memory management unit will also save the page table entry in the T L B for use next time。

So just a couple of points here。When the memory management unit walks the page table tree。

 it might retrieve a leaf page table and tree that's invalid。

That would probably not be saved in the T L B。 Instead。

 a page fault would be generated and the process would most likely be terminated。Also。

 in order to store a new page table entry in the TLB。

 it will be necessary to replace some existing entry。

The T L B cash will be fairly small and have a fixed number of entries。For example。

 it might contain 1 hundred and 28 entries， but different implementations might have different sizes。

In any case， the memory management unit will have to choose some entry to be replaced。

And for what it's worth， the T B that I implemented maintained an order among all the tail B entries。

 always keeping the most recently accessed entry at the top and replacing the least recently used entries at the bottom。

It was a real nightmare dealing with flushing entries。

 but it's safe to ignore these details here and just say that the new pay table entry is saved somewhere in the T L B。

The SV32 scheme also allows for megaages。😡，As I've sketched it so far。

 only normal 4K pages are handled。 Mega pages are not handled。To accommodate meggaages with our TLB。

 we'll need to add another bit to each entry in the translation leukcoide buffer。

And we'll call this bit M， and when set to1， it means that the entry in the TLB represents a mega page。

So let's modify our TLB design and add an Ibit to each entry in the TLB like this。

So now when searching the address cache associatively for a page table entry that matches。

The matching process is a little more complicated。If an entry in the TLB has the Mbit cleared to zero。

 then it's a normal page to determine whether the entry matches。

 the memory management unit will compare the current address space identifier from the SATP register。

To the address space identifier in the TLB entry。And the 20 bit virtual page number from the virtual address to the 20 bit virtual page number in the TLB entry。

However， if the M bit is set to one， then the entry in the TLB represents a mega page。

 so the matching is going to be a little different。

The memory management unit will still compare using the outer space identifiers as before。But now。

 only part one of the virtual page number that is the upper 10 bit index from the virtual address。

Will be compared to the upper 10 bits of the virtual page number in the TLB entry。Okay。

 I'm going to stop here。 There are some more details to how a translation looks side buffer would actually be implemented。

 but I just wanted to give you a sketch of what's going on inside of the T L B hardware。

Page table entries have a G bit， which is the global bit。

We now have enough background to discuss what the global bit is and how it's used。

Let's take a look at how the virtual address spaces are laid out。

This diagram shows how a 4 gigab address space might be arranged for a 32 B risk system using the SV32 scheme。

The numbers in this diagram might not actually match the details of your specific operating system。

 but the ideas are the same。So every virtual address space will be divided into two parts。

 one for the user process and one for the kernel。This particular operating system places the boundary at Hex C 0。

0，0，0，0，0，0， which means that every address base has one gigabte set aside for the kernelel's code and data。

And that's located in the upper one quarter of the address space。

While the user pages occupy the lower three quarters of the address space。

The user process will have some pages for code， and those pages would be marked executable and would typically be placed starting at Add 0。

The process would also have a few pages for variable data。

 and those pages would be marked readable and writeriable。

The data pages would typically be placed immediately after the pages for the code。

Some programs might also have some read only pages， and those would be somewhere in there too。

The user process would also have a stack growing down from high memory。

In this particular operating system， the user stack will start at address Hex 0，0 Hex C 0，0，0，0，0，0。

0 and grow downward from there。 So there would be a few pages marked readable and ridable for the stack at the high end of the user area。

Between the code and data pages and the stack pages， there would be a bunch of unallocated memory。

These pages would be marked as invalid， so any attempt to access them would cause a page fault。

If the stack grows downward beyond the pages that are allocated for it， a page fault would happen。

The colonel would respond not by aborting the program， but by allocating a new stack page。

And that's a guess， a little bit like demand paging that we talked about earlier。

When the program accesses an invalid page in the stack area。

 the colonel will allocate a new page and then retry or re execute the instruction doing the access。

 So the programme would never be aware that the stack pages weren't there all along。

There's also a heap， which grows upward in the direction of the stack。And basically。

 this involves just allocating more pages to the process。 So from time to time。

 the kernel will add more pages to the area marked data as the heap grows upward。

Each user process has its own virtual address space。

 and each address space has a different page table。

The user areas and the address spaces will all be different。

They will have different numbers of virtual pages， and the readable， writeriable。

 executable bits for the user pages will generally be quite different。And of course。

 the user pages will map into completely different physical pages。

Each user process would need its own physical memory separate from the others in which to store its own code。

 data and stack pages。All user pages will have the U bit set since their user pages。However。

 the upper quarter of all virtual address mappings would be identical。 There's only one kernel。

 and it's located in only one place in physical memory。

 So the upper quarter of all the page tables will have exactly the same mapping with the same physical pages and the same readwrite execute bits。

All pages in the upper quarter of the address space would also have the Ubit cleared to indicate that these are supervisor pages。

Now， with 64 B machines， things are roughly the same， but the numbers are very different。

One thing that can be a little different with 64 B machines is that the space reserved for the kernel area can be larger than the entire physical memory。

In that case， the kernel might map the entire physical memory into the kernel area。

And this would allow the colonel to easily access any bite and physical memory。

 which would make certain operations a bit easier for the colonel。

But let's not get distracted with the details of how a particular operating system lays out virtual memory address spaces。

As they say， your details may differ。 Check your documentation。

To recap a Linux or Uniix like kernel typically maps the kernel into every address space In our example。

 on a 302 B machine， the first three quarters of the address space was reserved for the user process and its pages。

The last quarter of the address space was reserved for the kernel。

 so its code and data would be located starting at address Hex C0，0，0，0，0，0，0。

The user code and data would be placed， starting at address 0。

Those pages would be marked in the page table entries as readable。

 writeriable and or executable as appropriate， and they would all be tagged as user pages。

The kernelel's code and data would be placed in virtual pages starting at address Hex C 0，0，0，0，0，0。

0。And each of those pages would be tagged as not you that is not user pages and therefore only accessible by code running in supervisor mode。

The problem is that the kernel is mapped into every address space。The mappings are the same。

 same virtual page numbers， same physical page numbers， and same privilege bits。

But these are all in different address spaces， so the address space identifiers would be different。

This means that the T L B cache will often contain several page table entries that are otherwise identical。

 They differ only in their aerospace identifiers。Well。

 this is where the G or global bit comes into play。

The kernelel pages would all be marked as global pages。

The idea is that a page that's smart global exists in all virtual address bases。

A global page will have the same mapping to a physical page and the same privileges in all virtual address spaces。

Therefore， the TLB only needs to contain one entry for this page。

This entry can then be shared by all address spaces。The translation leukcoide buffer is a valuable。

 expensive resource， and we want to minimize the pressure on it。

So let's consider some page in the kernel， and we might want to consider the very first page。

 which has a virtual address of Hex， C00，0，0000。This page has a virtual page number of Hex C0000。

This virtual page will exist in all address spaces， so the page table entry for page Hex C 0，0，0。

0 will be marked as global in all page tables。And this would allow the memory management unit to only store one page table entry for this page in the TLB cache。

Then whenever we have a virtual address in this page and the memory management unit is asked to map the virtual page number into a physical page number。

 it will search for a matching entry。If any entry in the TLB has its global bit set to one。

 then the aid matching will simply be ignored。If we're searching for page Hex C 0，0，0，0。

 then an entry in the TL B will match even if the current adderspace identifier。

 which comes from the SATP register， is different from what's in the page table entry in the cache。

And this is going to significantly reduce the number of entries in the T L B that we require。

 We can also combine the global bit with the idea of mega pages。

Imagine that the kernel happens to be7 megabytes in size。Since mega pages are four megabys in size。

 this means we can fit the kernel into only two megaap pages。

 and we can mark both of those megga pages as global。

Then only two entries in the translation leide buffer would be required for mapping the entire kernel into every address space。

So you can see the combination of mega pages with the global bit makes a huge difference。Okay。

 I'll wrap up this video here。So far， we've been discussing the SV32 scheme。

 which is used in 32 B risk Co。In the next video， we'll move on to 64 bit cores and discuss the SV 39 SV 48 and SV 57 page table schemes。

 which are used in 64 bit machines。Because of the logical， well thought out design of risksk 5。

 we'll see that all these schemes are really quite similar。We saw that with SV32。

 we had some really large pages， which were called mega pages。As we'll see in the next video。

 the other schemes very naturally accommodate things called giga pages， Terra pages and Peta pages。

But before I end， if you'd like to show your approval for this sort of content。

 let me encourage you to like， to subscribe and to share this video and even to comment on it。

In any case， thanks for watching， and I will see you in the next video。



![](img/7ba56c68cfb5cb399825583547900703_2.png)