# RISC-V处理器架构，RV32指令集架构，汇编语言，Verilog-FPGA-p02-P02-RISC-V-Assembly-Code-#2---ALU,-Load,-Store-Instructions--BV1aQ3nztE7J_p2-

。

![](img/d41651270b9c2b82c5f857d14d960ff3_1.png)

Welcome to another video in a series in which I describe the Risk 5 core and the Rik 5 assembly language。

Previously， I described the 32 general purpose registers and discussed how they would typically be used。

There are actually two main standards for risksk 5。 There's the RV32 and the RV 64。

The size of the registers is 32 bits or 4 bytes for RV32。

 and the registers are 64 bits or 8 bytes for the RV64 standard。

In this video I'll begin describing the instructions。

 and I'll focus primarily on the main RV32 I instruction set。Nevertheless。

 all the instructions I'll be talking about here can be used regardless of whether you are programming a 32 B or a 64 B risk5 core。

Here's an example instruction that adds the contents of two source registers and places the result in a destination register。

 which is T 0 in this example。In the op code field， we see the name of a machine instruction。

 but there could be other things in the op code field。 For example。

 we might see a pseudo instruction， such as the call instructions。

 and we'll talk about pseudo instructions later。 This video does not discuss compressed instructions。

 but we might see compressed instructions。 Those all begin with C and a period。And finally。

 we might see an asmbler directive， And those all begin with a period。

 And here's an example of an asmbler directive。There are actually two styles of comments。

 The first one begins with a pound sign and runs through the end of line。

 And that's all we've seen so far。 And that's very typically used to describe individual instructions。

 as we see here。The other style is with the slash and asterisks as you have in see。

 and these comments can span multiple lines， and they're particularly useful for removing code that you don't want to be included and also for large block comments that describe entire functions and so on。

The line might also begin with a label， which is an identifier followed by a colon。

 The colon is not part of the label， but it's necessary to identify that this thing is a label as not。

 say， an op code of some sort。The label itself is an identifier containing letters and digits and underscores。

 and might even begin with an underscore。Some asmblerers have additional syntax， for example。

 it might involve periods and so on。The label is essentially a symbolic name for some value。

 and that value is the address of the next thing that occurs。 And in this case。

 it's the ad instruction itself。 So if it's on the same line as an op code as we see in this example。

 it's the address of that instruction。If it's on the same line as some a simple directive。

 such as a byte or word directive that define a data item。

 well it's the address in which that item is placed in memory。

We can also have labels that occur alone on a line by themselves。

 in which case its the address of the next thing that occurs in the file。

 which is presumably an instruction or some data。After the op code。

 we have zero or more opera rounds， and if we have more than one， they would be separated by commas。

These operas can be either registers， as we see in this example， or they can be immediate values。Now。

 in the case of the add immediate instruction， the third op brand is an immediate value。

 which will be a small integer。 Sometimes we call it a literal value。

 and this value will be encoded directly into some fields in the instruction。Okay。

 so the immediate value can be represented in assembly code in either decimal， as we see here。

 or in hexadecimal notation， or it could possibly be a symbol that's defined somewhere else。

 or it could be a rather complex expression involving all the above。

The operarans are given in a particular order， and that order is critical， and for most instructions。

 the destination will be listed first。 and in the case of the ad。

 the destination register is in t 0 in this example。 and then we have two source operarans。

 which are a 0 and a1 registers in this example。In order to specify the various risk5 instructions。

 we use the following notation for describing the operarans。

 So this allows us to describe the instructions in sort of an abstract way。 And down here。

 we see some examples for the a and the load word and the store word instructions。

 And you can see that we don't specify the actual registers。

 But instead we say that in this particular position， we expect to see the destination register。

 which would receive the result of the instruction。

And we use Rs1 and Rs2 to indicate where we would specify source registers。

 and we use things like immediate and I 12 and offset to indicate where immediate values would be required for the instruction。

Immediate 12 indicates that the immediate value is restricted to 12 bits， and so has。

 it has a limited range。So in these examples here， we can see how these instructions would be written。

 and I've got some comments over here indicating what they do。

 The parentheses would be included in the instruction。

 so this is the way you would write load word and store word instruction。For most instructions。

 the destination would be listed on the left end as the first operaand。

 but for the store instruction， the opera end are listed in the other order。

 so this copies of value from Rs2 to a memory location which is specified using both an immediate value and a source register。

We can also see the general form address which is used in several of the pseudo instructions。

 and this indicates any address in memory which could be as much as 32 bits or maybe even more and so pseudo instructions would end up being translated into multiple machine instructions。

 we'll talk about that later， but this is the general notation we use for specifying operas when we talk about risk 5 instructions。

Given all that I've said about assembly language programming。

 there is still some flexibility in how you code your program。

 And I would say there are two main styles of indentation。

 free form and the other using tabs and so on。 So let's look at a couple of examples to see what this looks like。

In the case of the first style， typically we see a comment， and then we see a bunch of code here。

 and we're using spaces to separate the op code from the opera rounds。

 And I would say that this is a little bit hard to decipher。 and in the second example。

 I have exactly the same instructions。 So it does exactly the same thing。

 but I'm showing the other form of commenting and indentation。

Here we're using tabs or spaces or whatever， and we're making our op codes line up。

 and we're making our operaans line up， and we have a comment on every line。

 and we leave a plenty of space。 So where the labels occur， it just stands out， just jumps out。

And so what does this code do， Well， if you look at my comments over here。

 it's pretty clear that it's some sort of a loop。 we're checking something and jumping out of the loop。

 and we get something from memory put it in T1， increment it and then store it back to memory and increment our pointer in T3。

 So then we can look over at the assembly code and see that that is， in fact， what's going on。

 we'll talk about all these instructions later。 But I just want to point out that there are two different styles and I think that this lower style here where things line up is definitely preferable。

 And it's certainly what I try to do in all my assembly language programming。

Risk 5 has a bunch of arithmetic and logic instructions。

 And so let's begin with the addition instructions。There are two ad instructions。

 The first one is a register to register edition， and you can see where the source and destination registers are。

 and the second one add immediate involves an immediate value。

 and that immediate value is limited to 12 B。 so it has a limited range。 The value is sign extended。

 so the range is -2 k to plus 2 k。So this gives you pretty much all the information you need for these two instructions。

I do want to point out that for the RV 32， this is a 32 bit edition because the registers have 32 bits。

 but for the RV 64 standard， the registers have 64 bits， so these would be 64 bit additions。

Another thing to ask is， how are these two instructions encoded into binary？Now。

 I'm not going to show the encoding for all the risk five instructions。

 but I want to show these two to give you an idea。In the case of register to register instructions。

 we have an encoding that looks like this。 So we see that we've got five bit fields for the various registers。

 right，5 Bs is enough because2 to the fifth is 32， and we have 32 general purpose registers。

The op code is shown in the bits that are colored brown。

 and you can see that they the op codes for these two instructions are almost identical。

 but not quite。And in the case of the ad immediate instruction。

 we've got a field shown in blue that is 12 B for the immediate value。

 And this would be sign extended to give us something in the 4K range。

The other register to register instructions and register to immediate instructions are encoded similarly。

 but the op codes are different。Here are all of the risk 5 arithmetic and logic instructions using the register to register format。

 So you can see that both operas are coming from registers。

 and the result is being placed in a register。So we have addition and subtraction。

 and then we have the logical operations and or an exclusive or。These are bitwise operations。 So。

 for example， with the and instruction。Each bit of R S 1 is logically added with a corresponding bit of R S 2。

 with the result being placed in the corresponding bit of register R D。

We've also got three shift instructions， shift left logical， shift， right， logical and shift right。

 arithmetic。The shift amount is coming from Rs2。And with theillogical shifts。

 we put zeroes into the vacated bit positions。 And with the shift right arithmetic。

 we place the sign bit where we duplicate the sign bit into all of the vacated bits in R S1。

So shifting left can also be used for multiplying by a power of two。

 and shifting right can be used for dividing by a power of two。 If we've got unsigned values。

 we use shift， right， logical。 and if we've got signed values， we used shift， right， arithmetic。

We've also got a set， if less than and set， if less than unsigned。

 These two instructions will move either a 0 or a one into the destination register。 They move a one。

 And if R S 1 is less than R S 2， either using signeded or unsigned comparison。Now。

 we've also got some variations of these instructions that use immediate values。

 and so you can see it's the same exact instruction set only the second operaand has been replaced with an immediate value。

Except there is no subtract immediate instruction in risk5。If you want to subtract a constant value。

 just negate the value and use an addd immediate instruction。Otherwise。

 the operations that are performed are exactly the same。Now， this 12 bit value is limited。

 and it will be sine extended。 So this means that these instructions require the immediate value to be something between - 2048 and positive 2047。

Now， let's look at the load and store instructions starting with the load byte。

 load halfward and load word instructions。These go to memory， and they fetch either one。

2 or four bys and place those bites in the destination register。

The memory address to be used is computed by adding the value in register R S1 to the immediate value that's included directly in the instruction。

That's a 12 B value that's sign extended。 So you can think of it as an offset from whatever R S 1 points to if you want。

Now， with the load word， we'll be moving4 bys into the register。

 and most risk5 processors are little Indians。 so the bys would be moved according to that by order。

If the registers are 32 B in size and we are loading just one or two bytes in the load by or load half word instructions。

 then we need to ask what happens to the upper bits of the destination register。

 And with these two instructions， the answer is that they are sign extended。 So effectively。

 we're going to memory。 and we're fetching a signed by or half word value and moving that into the register。

If the value that we want to move is unsigned， then we have two more instructions for loading an unsigned byte or an unsigned half。

 and these would fill the upper bits of the register with zeros。And finally。

 if we want to store values， we have store byte， store half and store word， and these will store one。

2 or four bytes from the register into a memory address and the address is computed in exactly the same way。

Now I have described the instructions here， which are implemented on all risk processors。

 and if our processor is an RV32 processor， then the registers are 32 bits and we have only these load and store instructions。

But if we've got an RV 64 processor， then the registers are 64 bits in size。

 and so there are several additional instructions。We have a load word unsigned instruction。

 and we also have a load double word instruction， LD， and for storing。

 we also have a store double word which will store 8 bytes from the register Rs2 into memory。

We also need to talk about what happens with small integers。

 particularly bite sized integers or halfward sized integers that have one or two bytes of value。

If our computer has four bytes in the registers that is 32 B registers。

 then the question is what's going on with the upper bits of the register？

And that depends on whether we think of the integer value being signed or unsigned。

If it's a signed value， the upper bits in the register would be filled with copies of the s bit。

 whereas if it's an unsigned value， the unused bits or the extra bits in the register would be filled with zeros。

So as we do our computation， these upper bits are computed， but they're ignored。 And so when。

 for example， you go to store your computed result into memory， if it's a byte sized value。

 you would just store one B into memory and the upper bits would just be ignored。

But sometimes we want to convert the size of a value。 For example。

 if you have a by sized integer and you want to store it into a word sized variable。

 then that works just fine。 if it's assigned value。

 then the upper bits are filled with the sine bit and those would be stored into the upper three bytes of the4 byte word in memory。

 And likewise， if our value is unsigned， then the register would contain zeros in the upper bits。

 And if we stored an unsigned byte or half word into a four bit variable in memory。

 then those extra zeros would be just copied into the upper bits of that word。

Now there are some differences， it's not so simple if you want to convert between a signed and an unsigned。

 and for that， you'd need to use some other instructions。Now。

 let's define alignment and describe what it means for a memory address to be properly aligned。

Nowadays， pretty much every computer has bite addressable memory。

 That means that every by in the memory has a unique address。

 and every address corresponds to a bite。So we can define a half aligned address as an address that is evenly divisible by two。

 That is， it's even。And here are some examples first expressed in hex and then in binary。In hex。

 every even number ends in either 0，2，4，6，8， A， C， or E。And when expressed in binary。

 it always ends with a0 bit。We could also define word aligned addresses。

 and those are evenly divisible by4。 So in binary， they always end with 20 bits。And in Hex。

 a word aligned address always ends in 0，4，8 or C。And， finally。

We can define double word aligned addresses， and these are addresses that are evenly divisible by 8。

 and binary nearly， they end in 30 Bs。 And when expressed in hex。

 a double word aligned address always ends in 0 or 8。

Now that we've defined what it means for an address to be properly aligned， we can ask。

 what are the risk 5 alignment requirements。And the first requirement is that all instructions must be located on even that is half aligned addresses。

Of course， full size instructions are word in size。

 but we could have compressed instructions intermixed。

 and the compressed instructions are only half word in size。

 So instructions must be located on half word aligned addresses。

As far as load and store instructions go for bite sized operations， there's really no problem。

Any address can be used for a load bite or store by instruction。

But for a load half word or store halfward， do we require that the address be properly halfward aligned and for word operations。

 do we require word alignment。Well， the risk 5 specification says that this question is implementation dependent。

Of course， properly aligned addresses will work。 But what about addresses that are not properly aligned。

And there are really three options as to what the hardware will do。

The first one is that unaligned addresses will work just fine and the instruction will execute as you expect it to。

The second option is that when a loader store uses an address that's not properly aligned。

 an exception will occur， and that will cause a trap handler to run and that trap handler， well。

 the operating system might decide to just abort your program and issue a message that your program used an unaligned address。

Or the trap handler might emulate the operation in software。

 And that means that the trap handler will run， and it will use properly aligned loads or stores。

 and it will perform the operation and then return to your code。

 and your code will never be aware that this trap occurred and will just think that aligned addresses work just fine。

And the third option is that the behavior of the hardware is undefined。 The instruction may execute。

 but the result may be wrong。 According to my reading of the risk specification。

 the third option is simply not allowed。 Either the hardware will execute the loader store correctly or a trap will occur。

 And because you probably don't really know what the hardware is doing。

 My recommendation to you is that you avoid unaligned addresses altogether。

 And you can do this by locating all of your variables on properly aligned address boundaries。

 For example， if you have a word size variable， make sure that you locate it on an address that's evenly divisible by4。

Okay， I've now covered the ALU instructions and the load and store instructions。

 and with that I'll conclude my discussion of the instructions that manipulate data。

In the next video， I'll be describing the instructions that change the flow of control。

 In particular， I'll be looking at both conditional branches and unconditional jumps。

 as well as instructions like call and return。So thanks for watching and I look forward to seeing you in that next video。



![](img/d41651270b9c2b82c5f857d14d960ff3_3.png)