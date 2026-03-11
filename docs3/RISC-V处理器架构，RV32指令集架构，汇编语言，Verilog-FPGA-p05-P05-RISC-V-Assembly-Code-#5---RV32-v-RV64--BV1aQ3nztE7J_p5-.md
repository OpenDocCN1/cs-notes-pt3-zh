# RISC-V处理器架构，RV32指令集架构，汇编语言，Verilog-FPGA-p05-P05-RISC-V-Assembly-Code-#5---RV32-v-RV64--BV1aQ3nztE7J_p5-

![](img/bf9937527349a9fee99803c60fefd507_0.png)

Welcome to another video in a series about the Rik 5 assembly language。

The basic set of full sized instructions is called RV 32 I on course with 32 B registers and RV64 I on machines where the registers are 64 bits in size。

In previous videos， I described the full sized instructions that are available on any risk5 machine。

 regardless of register size， and I didn't make too much of a distinction between the two。However。

 there are some subtle differences between the 32 bit machines and the 64 bit machines。

And in this video， we'll be looking at those differences more carefully。

There are some differences and also a few additional instructions for the arithmetic instructions。

 the shift instructions， the load upper immediate and add upper immediate PC instructions and the load and store instructions。

 and that's what we'll cover in this video。The RV 32 and RV 64 notations refer to this size of the registers。

 In either case， the number of general purpose registers is the same。

 There are 32 general purpose registers。The I notation， as in RV 32。

 I or RV 64 I just means the basic set of full sized instructions。 If the I is not present。

 it's assumed since every risk5 core is implicitly capable of executing the full set of basic instructions。

Sometimes you'll see other letters after the RV32 or RV 64 to indicate various options。

 which we'll be describing in future videos。Now the basic set of instructions works on the entire register。

 and good examples would be the add and subtract instructions which perform a 32 bit edition for RV 32 machines and a 64 bit edition for RV's 64 machines。

I guess the goal with the basic instructions is that the same code should work regardless of whether you're running it on a 32 bit machine or a 64 bit machine。

Although there are some minor caveats that we'll need to be discussing some minor differences between the two。

 And in addition for 64 B machines， there are some additional instructions that perform 32 B sized operations that we need to discuss。

The basic instruction set contains only three arithmetic instructions， add， subtract。

 and add immediate。And on a 64 bit machine， these things perform 64 bit addition and subtraction。

But we've also got three additional instructions， add， subtract and add immediate with a W appended。

 the W stands for word， and these things perform 32 bit arithmetic。

What these things do is look at the lower 32 bits in the source values。

 and they perform the additional subtraction， store the result in the destinations， lower 32 bits。

 and then they fill the upper 32 bits of the destination register with the s extension of the value。

 the result in the lower 32 bits。Now I would recommend in all your assembly language programming that you use only s 64 bit integers unless you have a very。

 very good reason to use anything else。 I mean， even if youre limited on memory space and you're storing the result as a 32 B word。

 then you can use a load word instruction before you start your computation to get your values for memory and a store word when you're done to put the only the 32 Bs back into memory。

The purpose of these instructions， I think， is to allow languages like C and C plus plus to be implemented correctly。

 and in particular， these languages have particular overflow behavior that is expected of 32 bit operations and so these instructions are used to fill the upper 32 B with a known value and duplicate the overflow behavior right。

 Also they make it easy to perform a conversion from a 32 bit value into a s 64 bit value。

 you can think of these things as performing a 32 bit operation and then automatically or implicitly also doing the s extension to convert it to a 64 B signed value。

Now， if all you're doing is add add subtract and multiply。

 then you can safely use 64 bit arithmetic and just ignore the upper 32 Bs because as you may recall。

 the upper 32 Bs of an opera end will never impact or effect or alter the lower 32 bits of a result。

 Of course the lower 32 bits of the upper end can have an impact on the upper 32 B of the result。

 but the data flows basically right to left for addition subtraction and multiplication。

 so it's safe to just do your operations and ignore the upper 32 bit at the end。

With division and some other operations like shift， that's not true。

 the upper 32 bits of the opera end do become significant， but in summary。

 I recommend you just use the 64 bit signed arithmetic operations and leave these for use by the C or C++ compiler。

The basic instruction set contains six shift operations， and these are shift left logical， shift。

 right， logical and shift， right， arithmetic。 And then the same ones again。

 where the second opera brand is an immediate value instead of a register。

And the extension from 32 B machines to 64 B machines is very natural。In a 32 bit machine。

 the shift amount， when it's in a register is taken from the lower five bits and we ignore the upper bits and in the 64 bit machine。

 we take the shift amount from the lower 6 bits。The immediate value for 32 B machines is between 0 and 31。

 and for 64 B machines， it's between 0 and 63。So that's a natural extension。

We've also got six additional shift instructions。 They have the same names with a W appended。

 and these would be used if you want to perform 32 B shifting on 32 B values shifting in the appropriate amount。

 not using the upper 32 B。 So these will just operate on the lower 32 Bs performing a 32 B shift and the result will be placed into the destination register。

 and the upper 32 Bs of the destination will be set to these sign extension of the 32 result in the lower order word of the destination register。

And furthermore， the shift value would be restricted to only 5 bits or 0 to 31。

 so we would ignore the sixth bit in the destination in the second opera end register。

 so these could be used to implement shifting as it would be required by the C or C++ compiler。

For 32 operation for 32 B values。Remember that the load upper immediate instruction takes a 20 bit immediate value。

 and it shifts it to the left 12 bits and places the result in a destination register。

On a 64 B machine， it works the same way， except theres one important proviso or caveat。

 and that is that the result is sign extended from 32 B to 64 B。

 That is the upper 32 B of the destination are set to be a sign extension of the low order word。

If your addresses are less than or equal to 32 Bs， that is。

 if you're dealing with a 4 gigab address space or less， then there's no problem。

 The upper bits of the address are going to be ignored anyway and you don't care about the sign extension。

However， if your address space is larger than 4 gig， then I think you need to be very。

 very careful with this instruction， because with any address， it's greater than 31 B。

 That is it has a sign bit set or it's an address2 gig or larger。

 then you're going to have upper bits in the upper word of the address being set。

 And so you might not be getting the address that you expect。 So watch out there。

So the addd upper immediate to PC instruction is very similar。

 except it computes a PC relative address。The immediate value is shifted。

 and then it's added to the current value of the program counter。

 and the result is placed in the destination register。

The only thing with the 64 bit version is that the immediate value is first sign extended to 64 bits。

 so this is naturally going to work very well and support PC relative addressing as long as the offset from the current program counter is plus or minus2 gigabytes。

U。Now， you're probably not going to be using either the load upper immediate or the add upper immediate to PC instruction directly。

 Instead， these two instructions are going to be used by the asmbler and Lier whenever they need to translate pseudo instructions。

 And instead， you're going to just use pseudo instructions to not worry too much about either of these two instructions。

Now， take a look at the load and store instructions。

Here are the load and store instructions for any 32 B risk computer。The load instructions。

 go to memory， fetch some data and move it into a destination register while the store instructions move the data from register R S2 into memory。

And for the load instructions， we can either load1，2 or4 bytes into the destination register。

 And for one and two by loads。 we have a choice between signed and unsigned。 So by default。

 the upper three by and a load by instruction would be filled with the sine extension。

 whereas with a load by unsigned， those three bytes would be0 filled。

 and likewise with a half word load。With a load word instruction。

 we're moving 4 bys into the register。 and that filled the entire register。

 So we only have one load word instruction。And with the store instructions， we can store 1。

2 or 4 by from the register into memory。 Now， with a 64 B machine。

 we have several additional instructions。 We have two load instructions， and a store instruction。

So we now have a load double word， which goes to memory and fetches 8 bytes and fills the register。

 And now with a load word instruction， we have two variations。

 One will fill the upper  four Bs with the sign bet。 That's the default。

 and the other will the load word unsigned will fill the upper four Btes with the0 bits。

 and for the store double word， we can store 8 Bs from Rs 2 into memory。

For other instructions in the basic instruction set。The register size doesn't matter。

 It doesnn't matter whether you are executing on an RV 32 or RV 64 machine。 There are no differences。

The logical operations like and or an exclusive or are bit wise。

 And if you want to ignore the upper 32 Bs， that's fine。For set， if less than and set。

 if less than unsigned， these will work， even if your value is only a 32 B value。

As long as it has been sign extended。And by the same logic。

 the test and branch instructions will work just fine。

 regardless of whether youre comparing 64 B values or 32 B values。

 As long as the 32 B values are s extended。 Even the unsigned comparisons will work properly for s extended values。

For some pseudo instructions like jump， call and return， well。

 these will be compiled and translated by the assembler into jump and link and jump and link register instructions。

 and those two instructions work the same way。 So there's no issue with those。For fence。

 the system call and the brake instructions， the register size doesn't matter。Actually。

 I haven't so far talked about fence or the brake instruction in the earlier videos。

 but these work the same way because the registers don't come into play。

 and I hope to describe those in a future video。Okay。

 that wraps up my discussion of the basic instruction set and the differences between the RV 32 and the RV 64 standards。

In particular， we saw that the add and subtract and the shift instructions were very naturally extended to operate on 64 B values。

 And we also saw the addition of several instructions that were needed to properly mimic the overflow behavior。

 and these would be used by the C compiler for 32 B quantities。

We also saw that there were a couple of new load and store instructions to load and store 8 byte quantities to and from memory。

And also talk a little bit about the load upper immediate and the add upper immediate PC instructions and how they would work in a 64 bit environment。

The remaining instructions saw no changes。Okay， that's it for this video， thanks for watching。

 and I hope to see you in the next video。

![](img/bf9937527349a9fee99803c60fefd507_2.png)