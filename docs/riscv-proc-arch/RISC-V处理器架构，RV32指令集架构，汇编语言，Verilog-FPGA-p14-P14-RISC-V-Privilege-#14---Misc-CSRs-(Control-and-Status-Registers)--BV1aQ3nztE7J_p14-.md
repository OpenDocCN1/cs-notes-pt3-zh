# RISC-V处理器架构，RV32指令集架构，汇编语言，Verilog-FPGA-p14-P14-RISC-V-Privilege-#14---Misc-CSRs-(Control-and-Status-Registers)--BV1aQ3nztE7J_p14-

![](img/a8f0ee5d8312acc75bac0b4bfde36510_0.png)

Welcome to another video in a series on the Risk Five architectureure。In previous videos。

 we talked about interrupts and exceptions and described how traps are handled。

 both in machine mode and supervisor mode。And we also went over all the fields in the M status and the S status registers。

In this video， Ill be describing many of the remaining control and status registers that are available in machine mode and supervisorvis mode。

This includes providing more detail about some of the registers associated with trap processing that I've already mentioned。

 as well as introducing a number of new registers which describe and control the core and its configuration and a number of counter registers。

 which are used to monitor hardware performance and registers associated with the real time clock and timer interrupts。

In this video， I won't be covering the physical memory protection system。

 I cover those registers in a different video。Here are some of the control and status registers that I'll be describing in this video。

The first is MIISA， which describes the instructionstruct set architecture and tells what parts of the risk5 specification are implemented。

M heartRT ID is a register that gives the number of the core that we're currently executing on。

M Ca is a register that after a trap will be set by the hardware to contain a code number。

 indicating what exactly caused the trap。M T Vc will contain the address of the trap handler。

And then。M vendor ID， M Archecture ID and M implementationple ID all give more specific information about the core and its capabilities。

😡，And finally， the M configuration pointer， which points to some information about the platform and the system as a whole。

And as you can see from the fact that these all begin with the letter M。

 they are accessible only when running in machine mode。Let's start with the I SA register。

 which has a field of 26 Bs with one bit for each letter of the alphabet。

These correspond to all the main risk five extensions。For example， bit number5。

 which is corresponding to F， will be a1 if and only if the floating point extension is implemented。

And bit number3， which is D， will be set if the double precision extension is also implemented。

The upper 2 Bs is a field called M X， L。 And this tells whether you're operating on an RV 32。

 an RV 64， or an RV 128 core。Rell that the length of the machine mode registers is denoted symbolically as Ma mode X length spelled M X LEN。

The M X L field is read only， and you can't change the size of the registers。

 at least as seen by code that's running in machine mode。This register is required。

 but if it's not implemented， it will read as all0 bits。Now。

 if you want to write some code that will work on any risk5 computer regardless of the register size。

 you probably want to start by determining what kind of core you're actually running on。

So you should look at these upper bits with some code。

But since you might be running on a 32 bit machine。

 your code had better be using only 32 bit instructions。

 but you might be trying to read bits 62 and 63， or maybe even bits 126 and 127 using 32 bit code and that's just not going to work。

So heres a code snippet that will branch to one of these four labels based on the upper two bits。

It will either branch to registers R 32， registers are 64 or registers are 128 or no info。

As you can see， this code tests the sign bit and then shifts and then test the sign bit again。

But what are you to do if there's no information if both bits are zeros。

 you're going to need some other way to determine register size。

 So here's another code snippet that determines register size without using this ISA register。😡。

First， it loads the value 4 into a register。If this is a 32 B machine。

 the register will now contain this value， which has a single bit set to one。

Then we shift left by 31 B。 We can't shift any more than that because we might be running on just a 32 B machine。

If this is a 32 B machine， that 31 B shift will shift the1 bit all the way out and we'll have all zeroes。

 So we test and take this branch to Reggsar 32。But if it's a 64 bit machine。

The register will now contain this value， which is non zero， and we continue executing。

Next we shift by another 31 bits。If this is a 128 bit machine。

 the one bit will now be in position 64 as shown here。If this is a 64 bit machine。

 the register will contain all zeros， so we test it and jump to Reggar 64。

 and otherwise we know we're running on an RV 128 Cor。

Since this code snippet is shorter than the one on the previous slide。

 and since we know we have to execute it anyway， it's not really clear to me why you'd ever want to bother using the M X L field in this register。

In multi core systems， code needs to be able to determine which core it's running on。And for that。

 we have this control and status register， the hardware thread ID。

So imagine that you have a multi core system with eight simple cores in which each core is executing only a single thread。

 so this system would have eight hardware threads。Now。

 imagine that you have a simultaneous multi threaded system where each of the eight cores can execute。

 let's say， two threads simultaneously。 So now there are 16 hardware threads or hearts。

 and these would presumably be numbered 0 through 15。In fact， one heart must always be numbered zero。

 and that thread can act as the master heart doing the initialization and start coordination for the entire system and the other cores。

When a trap occurs， the hardware will store a number into the cause register。Actually。

 there is one cause register for machine mode trap handling。

 and there's another register called SCause for Supervisor mode Tra handling。

A trap can be caused either by an interrupt or by an exception。

 and the most significant bit here will tell whether an interrupt or an exception caused the trap。

Putting important bits into the s bit position makes it easy to do a quick check with a single instruction that will branch if the value is either positive or negative。

So here are the code numbers that are used for exceptions。

 and you can see all the different types of exceptions that might occur。

I have talked about these different exception types in other videos。

Here are the code numbers that are used for interrupts。

 and I've talked about these different kinds of interrupts and other videos as well。

And so now let's put all these numbers together on a single slide。

You can see that there is quite a bit of overlap with these numbers。 For example。

 the number 7 is used for the store atomic memory operation access fault exception。

 as well as for the machine mode timer interrupt。So that sign bit is crucial for telling exactly what a seven means that is for determining what sort of trap just occurred。

So what happens when a trap， either an exception or an interrupt， occurs。Well。

 the hardware will take an immediate jump to the first instruction of the trap handler routine。

 And when the corps resumes instruction execution， the trap handler will begin running。

To take this jump， the hardware will get the address of the trap handler from a register called M T Vec。

 This is the so called trap vector。MTVc is for machine mode traps and there's a similar register for supervisor mode traps called STVc。

 and that works exactly the same way。Presumably， software will have preloaded these registers with the addresses of the machine mode trap handler and the supervisoror mode trap handler。

 so when the trap occurs， the hardware can immediately jump to the right place。

The trap handler must start on a word aligned address。 That is the address must be divisible by 4。

 so the last two bits must be zeros。Actually， the last two bits of the address are implicitly zeros。

 The bits in the register are not used to form the address， but instead。

 they contain a2 bit code number。This is the simplest code number 0，0。

 and it indicates that all traps will go to a single trap handler。The handler routine will。

 of course， need to look at the cause register to determine which actions to take。

 But the idea is that there will be only a single trap handler for all machine mode traps。

 and the same thing for S TVc。 If the code 0，0 is used。

 there will be a single trap handler that will deal with any and all traps that are handled in supervisor mode。

But there is a second option。 If those lower or 2 Bs contain 0，1。

 then there will be multiple trap handlers， and the hardware will jump based on what kind of trap has occurred。

There's one trap handler that will handle all exceptions。We can call it the exception trap handler。

The starting address of the exception trap handler is found in Mtyvec directly。

 as we described before。However， interrupts are dispatched a bit differently。

There will be a separate trap handler for each kind of exception。The starting address。

 the address that the hardware will jump to when an interrupt occurs is computed by taking the interrupt code number。

 which is in the cause register， multiplying it by4 and adding it to the address that's in emptyVc。

The hardware will then force a jump to whatever address is computed。Let's see how this works。

Here again are the cause code numbers for the exceptions and the interrupts that we saw a second ago。

Let's assume that the MT VC register contains some address， which we can call the base address。

Here are the addresses that would be used by the hardware to invoke one of the trap handlers。

All exceptions would go to the address base。 that is the address that's directly in the MT Vc register。

Now consider what happens when， for example， a machine mode timer interrupt occurs。

That's code number 7， and 7 times 4 is 28。 So for this。

 the hardware will jump to the location that is 28 B past the base address。

The trap handler for supervisor mode software interrupts will begin just 4 B past base。

 So it would seem that the trap handler for exceptions must be extremely short since the beginning of the next trap handler is only 4 bys away。

 The exception trap handler could only be 4 bys long。

 which is obviously not large enough for anything。 So instead。

 what the software will do is place a jump table at address base。

A jump table is just an array of jump instructions。

The entry at the first offset at offsetet 0 will be a jump to the first instruction of the exception trap handler。

And the next entry of the jump table will be a jump to the start of the trap handler for。

Supervisor mode， software interrupts， and the next entry will be for machine mode。

 software interrupts， and so on。With risk 5， short range jumps can be implemented with a single machine instruction。

 which is only4 by long。 But for long jumps， we need two instructions， which would require 8 bys。

So note that with this scheme， there's only enough space in the first entry for a single machine instruction。

 So that means the trap handler for exceptions had better be pretty close to base to the jump table。

Because the interrupt code numbers use only odd numbers here。

 the remaining entries are spaced out by8 bytes so they can accommodate long jumps。And by the way。

 if you're programming a 64 bit machine， you might have jumps that are so long they require more than8 bys。

 but I doubt this is really going to be a problem in practice。Next， we have the vendor I D register。

The idea here is that each risk 5 chip manufacturer is assigned a unique I number。

 and software can query this register to determine which company made the chip that it's running on。

There's a trade organization that already has a system and a procedure for numbering electronics companies。

 and the numbers assigned by this organization are to be used for this register。

This trade group is the Joint Electron device Engineering Council。If you care about this stuff。

 you can go off and read about the numbering system that's used。

This register is required and is read only， but it could be hard wirered to 0 if it's effectively unimplemented。

Next， we have something called the Architecture ID registerister。😡，This register is read only。

 but it might be0 if there is no information available。

This is used to further describe the implementation by specifying the microarchure of the chip。

The sign bit tells whether the implementation is an open source or a closed source project。

For open source projects， the number encoded here would be assigned by the Risk 5 organization。

For close source projects， it would be assigned by and particular to the specific manufacturer。

There's no further specification about exactly what this value is。Next。

 we have another read only register called Implementation ID。

This would give additional information about the chipIPS implementation。

The riskk 5 spec doesn't say anything about how this register might be used。

Risk 5 also supports a number of hardware registers that are used to monitor and measure performance。

These are counters which are incremented automatically， as execution proceeds。

A one register counts the number of clock cycles since reset。

 and this would be incremented on every clock pulse。

Another register counts the number of instructions that have been executed。

And then there are a bunch of additional registers that count things。

 but what exactly these things are is implementation dependent。

But they count so called hardware events。But what exactly counts as a hardware event is left up to different implementations。

As examples， we might want to count the number of page fault exceptions that have occurred。

 or we might want to count the number of translation leukcoide buffer misses。

Things like this would be important to know and to measure in order to tune things either to tune the core implementation itself or to tune the code running on the core in order to give the best performance。

The names of the counter registers are shown here。 We have cycle。

 which counts the number of clock cycles。 We have inst Re， which is instructions retired。

 And that's just how many instructions have been executed to completion。 That is retired。

Then we have a bunch of registers that are just numbered。These are called hardware， performance。

 monitorit， counter 3，4，5， and so on， up to 31。These are the versions of the registers that are accessible in machine mode。

 So their names all begin with the letter M。Now， if I add numbers to this。

 you can see that we've actually got only 31 registers， not 32 registers。

In earlier versions of risk 5， there was a register called M time。

 which contained a real time clock value， but M time is no longer a control and status register。

I'll be talking about the real time clock later in this video， but in any case。

 that register is gone， leaving this gap in the numbers。And by the way。

 these numbers are not the 12 bit addresses used for the control and status registers。

 but the actual 12 bit register numbers follow this pattern with a gap where M time used to be。

These counters are all 64 B in size。 After all， a 32 B cycle counter is going to overflow in a second or two。

Now on a 64 bit machine， the registers are all 64 bits in size， so this is exactly what we have。

 but on a 32 bit machine， each counter has to be implemented with two 32 bit control and status registers。

The low order word has the name exactly as shown here。

 and the upper half of the counter is in another 32bit register with the same name only with a letter H4 high appended to the end of the name。

These registers are required to exist， but if the counting functionality is unimplemented。

 then the registers would just be hardwired to0。We know what the cycle counter and instructions retired are counting。

 but for the other hardware performance monitoring counters。

 the speck leaves it unspecified and implementation dependent。However。

 they also provide a second register for each of the counters。

 these registers have the names hardware Per Monitor， Even 3 and event 4， and event 5 and so on。

Exactly what these registers are used for and how they work is left unspecified。

But the idea is that the software can store something into these registers to control exactly what the corresponding register will be counting。

We've also got another control and status register called inhibit En。

 which is used to inhibit or stop the counters。32 bits of this register are defined。

 and of course for a 64 bit core， this would be just the low order 32 bits of the register。

Each bit corresponds to one of the counters。 So you can see that this bit here is unused because of the gap that I mentioned earlier。

And normally， by default， the counters are counting away。

 but you can momentarily stop or freeze a counter by storing a one into the corresponding bit of this register。

Here again， are the counter registers。These registers are only available to and accessible by code running in Ma mode。

😡，In addition， we have a second set of these same registers as shown here。

They have the exact same names， except there is no M prefix。And they hold the same values。

 that is they are mirrors of the machine mode versions。😡。

The machine mode versions are not accessible in supervisor or user mode， just like any machine mode。

 control and status register， but these registers may be visible in code running in supervisor or user mode。

😡，Of course their 12 bet register address numbers are different from the machine mode versions because they are。

 in fact， different registers。And these registers are strictly read only。

And note that there is now a register named time。So now we have 32 registers， not just 31 of them。

The Risk5 specification says that this time register shall be a shadow copy that is a mirror of some memory map register containing a real time clock。

The next question to ask is whether these counters are actually accessible and usable by code running in supervisor mode。

 and that is determined by a machine mode register named M counter enable shown here。😡，Again。

 we have one bit corresponding to each of the 32 counters。

 and this now includes a bit for the time register。If machine mode code sets a bit to one。

 then the correspondingent counter will be readable in supervisorvisor mode。😡。

If the core doesn't even implement supervisor mode。

 then the register would be visible in user mode instead。

But if the court does implement supervisor mode， then the question of whether a counter register is visible in user mode is determined by yet another register with a very similar name。

This register is called S counter En， and it can be modified by code running and Supervisor mode。

It has an identical format， as shown here。This register is used to determine whether to continue passing visibility of the individual counters on down to user mode code。

If the bit is set to one， the corresponding register will be visible and readable by code running in user mode。

 and otherwise the counter is not visible。😡，Any attempt to read a counter register that is not enabled and therefore。

 that is not supposed to be visible， will cause an illegal instruction， exception。

Now let's discuss the real time clock， which is called M time。

This is not a control and status register。Instead， the spec says that there shall be a memory mapped register that contains the current time。

And this register shall be 64 bits in size and shall be read only。The details。

 such as exactly how big the ticks are， for example。

 does it increment every millisecond or every microsecond or what？

And how is the clock to be set or reset or corrected？ Well。

 these details are not defined and left to the specific implementations。

But it is expected that all hearts in a given system will share a common real time clock。

M time is specified as a memory map device， rather than as a control and status register internal to a core。

 because the core might have a clock speed that changes or it might go to sleep altogether。

But the real time clock must continue to run。Also， the clock might require a separate battery and other hardware outside the core。

There is also specified to be another register named M time Comp。

 which tells when to generate the next timer interrupt。Like M time。

 this is not a control and status register and details are left to the system designers。However。

 M time compare isriable， and now there is one per core or more accurately one per heart。

 since each hardware thread is scheduling its own timer interrupts individually in isolation from the other hearts。

M time compare tells when the next timer interrupt should occur， and it's based on the current time。

 M time。Whenever the current time reaches or exceeds this limit， a timer interrupt is to happen。

The hardware will do this by setting the pending bit， which is the MTTIP。

 that's the Ma mode timer interrupt pending bit in the interrupts pending register。In fact。

 the pending bit simply mirrors the Boolean condition shown here。But the colonel。

 which is running in supervisor mode， will also need timer interrupts。

 So how are timer interrupts to be handled in supervisor mode。

And the first answer is that machine mode code will simulate timer interrupts。In other words。

 only code running in machine mode will get a real timer interrupt。

 and then that code will cause a timer interrupt to be seen by code running in supervisor mode by manually setting the supervisor mode timer interrupt pending bit directly。

😡，This bit can be modified by code running in machine mode。

 by updating the pin bit in the machine mode interrupts pin register。In supervisor mode。

 this bit is mirrored in the supervisor mode interrupts pending register SIP。

It's read only in supervisor mode。This approach will work， but there is a bit of overhead。

For example， the supervisor mode code will need to interact with the machine mode code。

 perhaps on every time slice。However， there is another approach which involves an optional extension called SSTC for Supervisor Time Compare。

If this extension is implemented， then a new control and status register called S time Comp is added。

This is a 64 B register， which is readable and ridriable by the colonel running in supervisor mode。

This register tells when the next timer interrupt should be generated。As always， for 32 bit machines。

 it's broken into two， 32 B halves。With this extension。

 a supervisor mode timer interrupt will happen whenever the current time exceeds the value in the S time compare register。

Actually， what happens is that the value in the S time compare register is constantly being compared to the current real time。

 and the result is reflected in the supervisor mode， timer interrupt pending bet in the SIP register。

 the supervisor mode interrupts pending register。With this extension。

 the supervisorvis mode timer interrupt pending bitt becomes read only for all code。

 regardless of whether the code is running in machine mode and accessing it via the MIIP register。

 or running in Supervisor mode， accessing it via the SIP register。

I also want to briefly mention a couple of additional registers。

The machine mode configuration pointer register is used to retrieve information about the current system。

This register will presumably contain a physical address。

 which might point to some special memory mapped hardware or perhaps some read only memory。

The details are implementation dependent。The Rik 5 spec also mentions a couple of machine mode registers for environment configuration and security configuration。

The details have not yet been finalized in the Ris5 spec。

 but they have to do with modifying various behavioral properties of the core。Okay。

 I think that's enough for this video。 In the next video。

 I'll be getting into the physical memory protection system and the registers associated with that。

 But in this video， we've gone over all the registers that are listed here。

The MIISA register describes the instruction set architecture implemented by the core。😡。

The heart ID register gives the number of the currently executing hardware thread。Now。

 on a system where each core implements only a single thread。

 this would just be the number of the core executing the thread that reading this register。

We also look more closely at what the hardware puts into the cause registers。

 both for a machine mode trap and a supervisor mode trap。

The addresses of the machine mode and supervisor mode trap handlers are storedred in the trap Ve registers。

And we saw that the software can optionally use a jump table to dispatch to the individual interrupt handlers。

 if it needs to。Then we look at these three registers， which are read only。

And these give implementation specifics about the core。We have the identity of the manufacturer。

The micro architectureure of the core and some additional vendor specific implementation information。

We also briefly mentioned these last three registers。

 the meanings of which are rather vague and left unspecified in the current risk five specification documents。

We also described a bunch of registers collectively called the Hard Per monitoring Regs or the HM Regs。

We have registers that count the number of clock cycles to give the current value of a real time clock and to count the number of instructions that have been executed or retired。

Then we have 29 additional registers， which are numbered 3 through 31。

 which can be used in whatever way a specific core implementer wants。These are all 64 bit values。

 and for a 32 bit core， there would also be high halves corresponded to each one。

 but I'm not showing those registers on this slide。There are also 29 registers called the event Regs。

 which can be used to control exactly what the numbered counters are actually counting。

The details of what an event is and what gets counted is left unspecified and implementation dependent。

The 32 registers listed on the left here are machine mode registers accessible only in machine mode。

However， there are less privileged， read only copies。That are mirror images。

 and that can be seen by code running in either supervisor or user mode。

The machine mode counter enable register determines whether they can be seen by code running and supervisor mode。

 And if so。The kernel can use the supervisorvisor mode counter enabled register to make them visible to user mode code。

These counter enable registers have a single bit corresponding to each of the 32 counters。

We also have a register， the In register， which can be used to temporarily suspend counting and freeze the individual counters。

The real time clock called M time is not actually a control and status register。Instead。

 the real time clock is treated as some sort of a memory mapped IO device。However。

 it may be visible to the core and pass down to code running and supervisor or user mode。😡。

Unlike M time， the register name simply time is a real control and status register。Finally。

 to implement timer interrupts， there's a control and status register named。Time， compare。

There's also one for machine mode timer interrupts。

 and there's another one called supervisorvisor mode time compare for supervisorvisor mode timer interrupts。

These registers areriable， and they will cause a timer interrupt。

 either in machine mode or supervisor mode respectively。

 when the current real time clock reaches the value stored in the registers。Before I go。

 please like this video and subscribe to my channel。 I really appreciate your help with us。😊，Okay。

 well， that wraps things up for this video。 Thanks for watching。

 and I look forward to seeing you in the next video。😊。



![](img/a8f0ee5d8312acc75bac0b4bfde36510_2.png)