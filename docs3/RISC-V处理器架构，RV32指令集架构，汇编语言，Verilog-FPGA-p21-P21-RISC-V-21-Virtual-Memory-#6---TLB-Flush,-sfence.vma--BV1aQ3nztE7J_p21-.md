# RISC-V处理器架构，RV32指令集架构，汇编语言，Verilog-FPGA-p21-P21-RISC-V-21-Virtual-Memory-#6---TLB-Flush,-sfence.vma--BV1aQ3nztE7J_p21-

![](img/b5c198153b8331394916f52a3b64fba6_0.png)

Welcome to another video in a series on virtual memory and paging。

There are six videos in this series， and this video is number6。

These videos are part of a larger series on the Rik5 architecture。In this video。

 I'll be discussing the translation leukcoide buffer in more detail and discuss how entries in the TLB can be flushed or invalidated。

And then I'll describe the SFence do VMA instruction。This instruction does two things。 First。

 it is used to flush the T L B entries for pages that have changed。

 This is needed when the entries in the T L B become out of date。And second。

 it can be used to force an ordering of certain operations that must be enforced in a core where operations can be executed out of order。

Previously， I sketched out how the translation lecoide buffer could be implemented。

Remember that the address translation cache is an associative memory。

 which is sometimes called a content addressable memory。

 where each entry has a virtual page number and an address space identifier as its key。

 and it maps these into essentially a page table entry。

And that would include the physical page number as well as the other bits from the page table entry。

One of those bits was the valid bit， and I want to discuss that in more detail。Each T L B entry。

 as I have described it so far， contains a valid bit。The question I want to ask now is。

 why would we even want to store an invalid page table entry in the address cache in the first place？

Let's assume that the program tries to use some virtual address。

 which happens to be within an invalid page。The memory management unit will first walk the page table tree to locate the page table entry for the page that contains this address。

Let's assume it sees that the valid bit in the page table entry in the page table is zero。

 so the page is not valid。Should the memory management unit now store this pagetableable entry in the TLB？

Should I keep a copy of it in the address translation cache？Well。

 why was the page invalid in the first place？Maybe the program has just tried to access a page that's unmapped and unallocated。

😡，The programme has made some sort of an error trying to access memory that doesn't even exist in its virtual address space。

 So the colonel is almost certainly going to terminate this process with a nasty error message。

Or maybe the program is trying to access a perfectly good memory page that just happens to not be resident in memory at the moment。

The colonel is doing demand paging， and this particular page happens to be paged out to secondary storage。

 So the colonel will respond by temporarily suspending the program。

 reading the page back into physical memory， updating the page table to point to this physical memory that is just allocated and at the same time。

 changing the page table entry to make it valid。 The kernelel will then restart this program。

But in either case， the old page table entry， the one with the valid bit set to 0。

 will simply never be needed again。So there's no good reason to cache this invalid page table entry in the first place。

😡，We have a second problem。From time to time， the colonel will need to update the page tables。

For example， new pages may be added to a virtual address base when the stack or the heap grows。

 and sometimes a program will return pages to the kernel that it no longer needs。 Also。

 many contemporary operating systems allow large chunks of data to be moved between processes by moving entire pages from one address base into another address space。

To perform these actions， the kernel can update a page table by using store instructions to modify various page table entries in the page table。

But the TLB cache might contain older versions of the entry that the colonel is modifying。

 and these would now be out of date and incorrect。The kernelel needs a way to invalidate an old TLB entry。

Essentially， it needs a way to get rid of an obsolete entry in the Tl B。Previously。

 I didn't really dwell on the valid bit in the T L B entries。

The way this is going to work is that the valid bit will mean something different and be used in a slightly different way。

The valid bit in a page table entry in the page tree tells whether the page is OK or whether the memory management unit needs to cause a page fault。

😡，But with T L B entries， this bit will mean something completely different。

 It'll tell whether the T L B entry is empty or in use。 In other words。

 is the slot in the cache occupied with a usable entry or is it free and available to hold a new entry。

So to repeat the V or valid bit in the page table means that the page is valid。

 while the bit in the TLB means the entry in the TLB is valid。And these are two distinct things。

So while these bits might both be called valid， this is definitely confusing。

 so I prefer to change the name of the bit in the TLB。Let's not call it a valid bit。

 let's change it from V to N。The N bit in a TLB entry will be set to one when the entry itself is in use。

If set， N indicates that this entry in the TL B is not free。

 and I chose N because it can stand for not free or in use or needed。

Let's go back to my picture of the translation lecoide buffer。

This is the Associative memory using the address space identifier and the virtual page number as the search keys。

Each entry contains roughly a page table entry with the physical page number and the bits that I've shown here。

Recall that for SV32， we needed to add a bit to indicate when an entry indicated a mega page。

That bit controls exactly how the matching of the search key is done and how the physical address is constructed。

When we describe the paging schemes for 64 B machines， SV 39， SV48 and SV57。

We saw that we can also have giga pages， and we might also haveterra pages and even petda pages if the core implements SV57。

So like the Mbet， we'll need to add。G， T and P bits to handle giga pages。

 Terra pages and petta pages， depending on which paging schemes the core actually implements。But。

Moving to the bit that we're interested in， we've determined that we are simply not going to cash invalid pageable entries in the translation lecoide buffer。

So we don't need the V bit at all。Instead， we need a new bit。

 the N bit to indicate whether a slot in the TLB contains usable data or whether it's empty and unused。

😡，Again， if n is one， then this entry is needed， not free， and if n is zero。

 then this entry is free and available to store some new page table entry。😡，Now。

 your core is doing many things at once。Most modern cores are probably pipelined。

 which means that at any point in time， several instructions are in the middle of execution at different stages of completion。

And many cores also take this to an extreme and may reorder and overlap the operations in order to achieve greater performance。

The instructions may， to some extent， be executed out of order。

Most of the dependencies between instructions like which registers are used in which order would be tracked by the coreps。

 And if operations are done out of order。They will nevertheless be done in such a way as to ensure that the results are identical and unchanged to what they would be otherwise。

Unfortunately， the corps may not fully understand all interdependencies。

So here are the operations that affect the virtual memory system that we need to think about。😡，First。

 memory is accessed。 load instructions and store instructions， read and write to memory。

 and instructions are fetched from memory。 And these all use virtual addresses。

 So the coreps will be using the T L B and the page table。And from time to time。

 software will update the page tables， and this would be done when the core stores into some more or less random addresses and physical memory。

And finally， software will be altering the SATP register every time it switches from one virtual ladderer space to another。

Of course， modifying the page table or the SATP register will have an impact on the loads and stores and the instruction fetching。

The problem is that an out of order core may not be able to detect or to understand the required ordering constraints which nevertheless need to be respected。

We need a way to impose an order on certain operations regarding the page tables。

 and we need a way to keep the TLB in sync with the page tables。If software changes the page tables。

 the cached entries in the TLB will become out of date and incorrect。

We need a way to force the corps not to use old， incorrect entries。First of all。

 we need a way to get rid of old， out of date TLB entries。

The colonel must be able to invalidate certain TLB entries whenever it changes the page tables。

We talked about how the endbit flags or marks， TLP entries as free and not in use。Now。

 we need an instruction that the colonel can use to clear this bit。

 That is to flag obsolete T L B entries as no longer valid。And second。

 we need some way to order the operations that must be done in a certain order。Next。

 we'll be introducing a new Ri5 instruction that will force the Corps to finish executing some operations such as ABC before it starts operationserations X。

YZ。And in general， such an operation is done with a so called fence instruction。For example。

 if the software updates the current page table and then executes instructions XYZ that use the newly modified virtual address。

Such as a load from or a store into that virtual address space。

 Then the core must be forced to complete the update of the page table before it uses it for the load or store instruction。

If the load or store or fetch happens to access that part of the virtual address space that was affected by the modification。

 then we need a way to make sure the court doesn't reorder things。It must not start the load。

 door or fetch until after the page table modification has been completed。Likewise。

 if the software executes instructions， ABC that make use of the current page table。

 and then it modifies the page table， we need to make sure that the core actually respects the order that the software tried to do these things in。

If the code issues a loads door or fetch from some page in the virtual address space。

 and then subsequently the page table entry of that page in the page table is modified or maybe we switch to a completely different page table by modifying SATP。

Those earlier operations have to be completed First。

 the Corps has to wait to finish certain operations before starting other operations。With risk 5。

 we have one single instruction that will take care of both of these tasks in validating the TLB entries and forcing order。

 and this instruction is called the S Fence do VMA instruction。

The op code happens to contain a period here。This is part of the spelling the dot is treated just like an underscore。

It's just another letter in the name of the instruction， though different from the other letters。

 No spaces would be allowed within the instruction opcode name。Frankly。

 I would have preferred it if Rik 5 had used underscores instead of periods for this sort of thing。

 since that's what's done in other programming languages like C。 But they didn't ask me。Also。

 it's important not to forget the dot VMA part。 there's also an instruction named just S fence。

 but that's a different instruction。Here's the form of how this risk 5 machine instruction would be written in assembly simply code。

 It takes two opera brands， which must be register names。

The first register will contain a virtual address， and the second will contain an address space identifier。

The virtual address and the addresser space identifier together describe a particular page in some address space。

To execute this instruction， the coreps will first complete all prior operations that access this page。

Then if the T L B contains an entry for a page that contains this virtual address。

 then that entry is eliminated and more precisely， any matching entry would have its inbit changed to 0 to indicate that the entry is not in use。

 It's now free and available to be used for some other page。And finally。

 this instruction will force the core to complete all updates that might affect this particular page before proceeding and starting to execute any instruction that might access this page in terms of how the Sph VM A instruction is actually implemented。

 I suspect that most hardware will probably implement it as follows。First。

 all prior instructions are completed， regardless of what they do and which pages they access。

In other words， the pipeline is first allowed to run until it is completely empty。

 thereby completing all instructions that came before the Sphence ViM A and no instruction from after the Sph VM A would be allowed to begin execution。

Any that had already started would be cancelled。And then the relevant T L B entry， if there is one。

 is changed to market as unused， free and invalid by setting in to 0。And finally。

 after the change to end has been done， instruction execution would resume with the instructions that follow the S fence do VM A。

However， the risk5 spec describes and specifies this instructions more like I've actually shown here。

The actual specification is a little more general， but as far as I'm concerned。

 I just prefer to imagine that the Sence Vima operates like a total fence。

 finishing all prior instructions， then altering the tail B and completing that before starting any subsequent instruction。

ATechnically， total fence is more than is strictly required。

 So the risk5 folks have specified the instruction in such a way as to force only the limitations that would absolutely be necessary。

But the total fence implementation that I just described would certainly be a correct implementation and would have the correct effect。

In any case。This is a fence operation plus an invalidation of TLB entries。

Let's take a look at how this instruction might be used。

Imagine that a user process is executing away and suddenly it gets a page fault。

 so the process is suspended， trap handling ensues， and the kernelel gets control。

Let's assume that the process was trying to access a page that's currently paged out and not resident in memory。

 So the colonel will need to bring it in from Secondaries George。

After the page is read into main memory， the kernelel will update the page table to replace a page table entry that was previously marked invalid with a new entry that points to the newly allocated physical page。

 and that's now marked as valid。The colonel will now go back to the suspended user process and retry。

 That is to re execute the instruction that caused the page fault。But before it does this。

 it really ought to execute the S fence VMA instruction。First。

 this will clear out any old entry for this page in the Tilby Ca。

That we're assuming that the T L B cache doesn't contain invalid entries。

 but maybe something else is going on。 And for some reason， the T L B does contain an old entry。

For example， maybe this page was a copy on right page that was marked read only so that the colonel could get control and copy the page whenever a user process tried to store into it。

But in any case， the S fence via A will clear out any old information from the T B。

 which would force the memory management unit to perform a page table walk in the process。

 fetching that new page table entry。Second， the S fence VM A will force the coreps to wait before performing the page table walk to make sure that any modifications to the page table have completed。

The colonel has presumably executed a store instruction to update the page table。

 So that needs to complete before anything else happens。Now。

 I'm sure that before the colonel can return to the interrupted process。

 it'll need to complete trap processing， restore the registers。

 do a bunch of bookkeeping and so on before it can even execute the Ssrad instruction and retry the instruction that originally needed the page。

But to be fully correct。We need to imagine that things could be so completely out of order that a fence operation is truly needed。

Maybe this cor has a very， very， very deep store buffer in its caches or something like that。

 So to make absolutely certain that updates to the page table are fully completed before the page table is actually used。

 we need to execute that fence VM A instruction。What if we're running on a multi core system。

We have other cores， and they'll have their own T L Bs。And quite likely。

 every coreps in the system would have its own private T L B。

When one core updates a page table in memory， there is the problem that a page table entry for this page could be cached in the T Bs at all those other cores。

Unfortunately， the Sence VM A affects only the core that executes the instruction。

 We've still got the problem that the other T L Bs and the other cores are operating independently and are not affected by the Sence VMA instruction。

It turns out that this is a problem that can't be solved in hardware。

 Software has got to deal with it。What we really need is for an S fence VA instruction to affect all cores to flush all TL Bs of an obsolete page sample entry and perform a fence anywhere that the page could be used。

 but that's not what the instruction actually does。 It's local。

So the colonel somehow needs to execute an Eph Vime instruction on every corps。

And achieving this will involve some coordination and some inter core communication。

In order to get these other cores to execute this instruction。

 the core that's altering the page table in the first place will need to interrupt them and ask them to please execute an S fence VA instruction with this particular virtual address and this particular address space identifier。

😡，This is what's called a TLB shootdown。In other videos。

 I described the software interrupt mechanism， and in my opinion。

 this seems ideal for implementing a TLB shootdown。

 but I don't want to get into kernel operations and operating system issues in this video。

One thing to point out is that at least as far as I've described S F ViMA so far。

 only one address space is affected。But imagine that the TLB happens to contain an entry for the virtual page that's indicated by the address in Reg 1 that has its global bit set。

That Tl B entry could be used by the memory management unit。

 regardless of whatever address base identifier the entry happened to contain。So Sphs VMA。

 as I've described it so far， wouldn't necessarily get rid of a global entry that could end up being used for this virtual page。

Fortunately， there's a variation of the instruction shown here。Which would do the trick。

This would be used for global pages。If the second opera brand is x 0 as shown here。

 then all address bases are affected and any entry in the T B for this particular page will be removed。

Remember that with risk 5， the x0 register is the so called0 register， which is hardware to0。

You've got to use that register in particular for the Adderspace identifier argument and not just a register containing zero。

 since that would just direct the instruction to page table entries for address space number0。😡。

Using Register X0 for the second Op brand will make the instruction apply to any and all address spaces that have mappings for the given virtual page。

If the translation luukide buffer contains an entry that matches this virtual page。

 then regardless of its address based identifier， that entry would be removed。

 This includes any entries that have the global bits set to one。

 So this form would be used for updating global pages。

Their in bits would be changed to indicate that they are now free， unfilled。

 empty and available for other usage。Now， let's look at another common situation。

Imagine that some process has terminated， and the kernelel needs to completely eliminate an entire virtual address space。

Since there are a limited number of address space identifiers。

 the kernel also needs to recycle the associated address space identifier and use it for some other processes virtual address space。

Well， there's a form of the SF VMA instruction that can be used for all pages in a virtual ladderer space。

 and that's shown here。In this form， the first operaand。

 which is normally the register containing the virtual address， must be x0， the0 register。

It can't be just any register containing0， since that would indicate address 0。

 meaning the first virtual page in the address space。 it has to be the0 register itself。

With this form of the instruction， all entries in the T B for this address space would be flushed。

Any and all entries in the TLB that have a matching address space identifier will be freed and marked empty by changing their inbits to0。

So when a virtual ladderer space is destroyed， the colonel will execute an instruction like this。

This will eliminate from the TLB any entries associated with this Aspace identifier。Of course。

 the instruction will also perform the fence function。

 So the instruction forces any previous references involving this address space identifier to finish up。

 and it delays any future references to any new address space that happens to use this same address space identifier。

Finally， you might ask what happens if both opera brandss happen to be x0， the0 register。Well。

 this would cause a complete flushing of the entire translation licoide buffer。

Every entry in the Tl B would be eliminated。All inbits would be changed to0 to make the entire TLB empty and all entries free and available for future use。

I don't think the colonel would need to do this very often。

 but it would probably be needed at start up。When the system is booted or when a system reset is performed。

 it might be a good idea to make sure that the TLB doesn't pick up some random data。

It needs to be properly initialized and executing this form of the Eence VMA instruction would do the trick。

Okay， that concludes this set of six videos on virtual memory and paging。

If you have made it all the way to this point， then let me congratulate you on your perseverance。

 Hopefully， you now understand how risk 5 supports the colonel's implementation of virtual memory。😊。

And if not， then relax， there was a lot here， take a breather。

And after you've had a chance to reset yourself， why not just watch all these videos all over again？

That would really help burn this knowledge into your brain。But even if you move on to other stuff。

 let me close by saying， thank you very much for watching these videos。 I really。

 truly hope you learned something here。😊，And finally， please like， subscribe。

 share and comment if you'd like to show your approval of this sort of YouTube content。

 Thanks again for watching。

![](img/b5c198153b8331394916f52a3b64fba6_2.png)