# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P38：38_07_04_单元-5-3-中央处理器.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/56510cee9eda4f28448670bfa1252b36_0.png)

The central processing unit， also called the CPU is the centerpiece of every computer hardware architecture。

It is the hub of computation， if you will， because this is where all the calculations of the machine take place。

 and it is also the seat of control。 This is where decisions are made about which instruction should be fetched and executed next。

In this unit， were going to talk about the hec CPU。

 the specification of the of the CPU and how we actually are going to build it。Now， as usual。

 it always pays off to start with the abstractstruction。

 so we can think about the he CPU as some sort of a black box magic that performs to truly remarkable things。

 First of all， well， it's a 16 B processor like the entire computer。

 And the first thing that it can do is given a certain instruction written in the hack language。

 it will execute this instruction。😊，Now this is something which， in my opinion。

 is truly remarkable and dramatic because up until this point， when we wrote programs。

 the programs existed on a piece of paper。 they were completely static。

 they were simply a bunch of symbols that describe some fantasy of the programmer who wants to actually make something happen。

But now we can actually take these programs and put it into a machine that turns them into reality。

The programs become music that you can listen to or or video clips that you can watch or some airline reservation system or whatever。

So。The CPU is this very unique and special agent that takes this program specification and turns it into a reality。

😊，And if this were not enough in its own right， the CPU can also do something not less remarkable in the process of executing the current instruction。

 it also figures out somehow which instruction should be executed next in the program which is currently running。

And， of course， since we talk about the he computer。

 we assume that all these programs are written in the hec machine language that we studied or looked at in week4。

 So given that this is the CPU abstraction。 The next thing that I'd like to discuss is the more detailed specification of this apparatus。

 Well， the first thing that we have to remember， is that the CPU does not work in isolation。

 it is connected to other devices inside the computer。 in particular。

 in this particular he architecture， the CPU is connected both to the instruction memory and to the data memory。

 With that in mind， here is the specific input and output connections of the CPU。

 And let us begin to review them from left to right and from top to bottom。 So， first of all。

 we have three inputs coming from three completely different sources。 First of all。

 there is the 16 bit。😊，Data value， which is the value of the currently selected。Data memory register。

 This is the value that the CPU is going to operate on。Now， what exactly do we want the CPU to do？

 Well， the next input， which we decided to call instruction， which is a very sensible name。

 describes a 16 B input， which is。The value of the selected instruction memory register。

 And remember that at any given point of time， there is always a selected register in the instruction memory。

 and there is always a selected memory register in the data memory。

 So always something comes into the CPU。The third input， which we decided to call reset。

 is a1 bit input， which I will discuss later in this unit。On the right hand side。

 we see the outputs of the Alu。 So first of all， if the Alu wants to write something to the data memory。

 it has to specify three different things。 Number one。

 what is it that we want to write and this is stored in or emitted through an output called out to M。

 Number two， where do we want to write it， we have to provide an address。

 And this is the the job of the next data output。 and the third output is a load bit that enables the data memory for right operations。

 So these are the three data outputs， if you will， of the CPU。 In addition。

 there is one extremely important output， which we decided to call PC for reasons that will become clear in a few minutes。

 and this output holds by some sort of magic the address of the next instruction that has to be fetched and executed。

😊，In the next cycle of this computer。So。How do we implement this magic？

 How do we make all these good things actually happen。Well， here is one way of doing it。

 This is our proposed implementation of the functionality that we just described。

 It is not the only way to build the CPU， but this is a pretty good one because it's very elegant and simple and relatively easy to do。

So。Before we get into the actual details of this architecture， let us look at the interface。

 If we look at the interface of this hardware diagram。

 we see that it is10 percent identical to what we saw before。

 we have three inputs coming in and we have four outputs coming out and given that we made this observation。

 we can now delve into the details of the actual architecture。

 Another important thing that we have to look at before we begin to understand what is going on here is that within this architecture。

 we have many labels labeled by the catch all symbol C which I use to represent the notion of control bits。

 So in order to make all these chips work together。

The designer of the CPU has to make sure that different bits。

 different control bits arrive to the right locations。

 and these multiple messages together will cause the CPU to do what what it's supposed to to be doing。

Now if you look at this architecture you know after the first minute or two of bewilderment you will realize that everything here is extremely standard。

 you see the LU which you built in Project2 we see three registers which we call AD and PC and these registers are identicals to chips that you built in project3 and we see two moCs which we built in a week one of the course in Project1 and therefore putting together this architecture is just a matter of assembling chip parts that you've already built in previous weeks in this course another thing that you see in this diagram is all these C labels which indicate control bits that go into various locations in various chips now we have intentionally left those the specification of these control bits somewhat op because we want you。

To figure out how to actually piece all these things together。

 and we'll have much more to say about it in the unit that discusses how we actually build this architecture。

 Now， before we build it， we have to describe what this architecture actually does。 And in doing so。

 I find it kind of interesting to think about this architecture as an orchestra。

 an orchestra that works together many different instruments in order to produce some great symphony and the symphony is the execution of the current program。

 know just like a regular orchestra it can it can play many different pieces of music and the current program determines what it actually executes。

😊，So I would like in the remainder of this unit to focus on different sections in this architecture and let us begin with this section that deals with the current instruction So zooming in on this section we see that it consists mainly of a register called a and an instruction input that connects with this register through a multiplexer and here is an a instruction arriving to the machine in the current cycle or some cycle and here is also the symbolic pnemonic of the same instruction which is easier to read。

 but obviously the computer doesn't care about it at all。

 this is just for communications between me and you。

 So we see that this instruction seeks to load the value 3001 into the a register。And， of course。

 to do everything in binary。 So in order to carry out this instruction。

 the CPU has to do several things。 First of all， it has to decode the instruction。

 It has to take the 16 B value and separate it into an up code and a 15 B address or a 15 bit value。

By the way， how do we know that it's an a instruction Well， we can look at the op code。

 the Op code is 0 and according to the hec machine language specification。

 it means that it's an a instruction。 So the CPU says aha， I know what to do with it。

 I have to take the next 15 B value and put it inside the a register and notice that this is exactly what the gate diagram does。

 the 16 bit values go through the register。And and into the register。

Another thing that the CPU does and we cannot see it in this diagram in order to avoid clutter。

 but this is something very simple。 It takes the output of the a register and emits it outside the the CPU via the output。

 which we call I think， address M or M address。 You can look it up in the overall architecture of the computer。

 So this is how the CPU handles an A instruction。Now。

 the next thing that we' are going to look at is how the CPU handles a C instruction because after all in this hec machine language we have two generic instruction types and a instruction and a C instruction。

 So we have to be able to entertain and handle any one of these instruction Well。

 the C instruction like the a instruction consists of different fields。

 And the first field is the up code which happens to be one。

 This is how the CPU can tell that this is a C instruction。 But in addition to this。

 we have several other fields and we can we can see them more clearly if we look at the symbolic manifestation of the same instruction。

 Now notice that I'm using color coding to associate the bits with the symbolic pneumonics。

 but these colors obviously are completely meaningless for the computer they are just a way for us to communicate more easily in the course。

 So how does the CPU handle with such an instruction。 Well， you may have guessed the first thing。

That has to be done is to decode the instruction。 So the AU takes this 16 B value and it decodes it into four different fields。

 and these fields will later on be used in order to power up and manipulate different elements inside the computer architecture。

 What we discussed so far was how the CPU handles the a instruction。

 but if you look at the gate diagram， you see that the same a register can be also fed not necessarily from the instruction input。

 but rather from the Alu output。 So we have to decide in some cases。

 we want the a register to be fed from the instruction and in other cases。

 we want the Alu to be fed from the Alu output。 Now you may have guessed how we do it。

 we know that in different situations， we deal with two different instruction。 In some cases。

 its an a instruction with an upcode of zero。 And in this case。

Want the input to come from the instruction。 In other cases。

 it's a scene instruction with an up code of one。 And in this case。

 we want to to root the input of the A register in such a way that the input will come from the A U。

 So it is the job of the CPU designer to inspect the op code of the incoming instruction and decide from which source。

 the a register will take its its next contents。 So to speak。All right。

 so this is roughly how the CPU handles incoming instructions and let's go back to the overall architecture and focus on the next section that I'd like to discuss。

 which is the operation of the ALU， which is by far the most complex part of this architecture。

Alright， now we see here this segment that deals with the AU and we see a C instruction coming in instead of the an instruction that we saw before。

 and let us remember that the same instruction consists of different fields of bits。

 each one of which means something else。And another thing that we have to remember is that the AU is a combinational chip。

 It always computes something。 There's always some inputs coming in。

 and there's always some output coming out。 And when you look at the diagram。

 you see that the inputs of the AU come from two different sources， one of them is the deregister。

 the current value of the deregister， and the other one is either the value of the a register or the value of the selected memory register。

 and there's a multiplexer that takes care of this decision of where to take the value from。

 and the control bit of this multiplexer is one of the bits in the instruction。 So once again。

 the CPU designer has to take care to take this bit that determines from which we want to read the input of the AU。

 and the AU will then get the correct inputs or the inputs that the programmer intended it to receive。

So we have the inputs lodged in the input spins of the AU and the AU goes to work and how does it know what to do？

 Well， the AU also has six control bits that basically taken together tell or specify the AU which operation we want to carry out。

 Now these bits are taken from the instruction and I'm using some color coding here to help distinguish which bits go where。

 but of course these colors are completely meaningless as far as the computer is concerned。

 and I'm using them only for deductic purposes。 So the CPU designer has to take these six green bits or more accurately copies of these bits and route them all the way to the control bits of the AU。

 So now that we have all this information we have the input data we have the operation that we have to carry out we can actually the A。

Actually compute something and out comes the A output。Now inspecting the diagram。

 we see that the AU output is simultaneously fed into three different destinations。

 The first destination is the D register the second destination is the A register and it goes through multiplexer and the final destination is outside the interface of the chip so to speak。

 so the same AU is fedend out into three different places。

And so we have the situation that we have the same value output knocking on three different doors。

 But the first， the fact that it knocks on these doors does not necessarily mean that the doors are going to open。

 We have to decide or the programmer has to decide which door has to be opened。

This decision is made by the next field of bits that I want to focus on。

 and these are called in our jargon。 We call them destination bits。

 We have three destination bits and these bits determine whether or not to open the de registerg the a register and the data memory to accept the Alu output。

 So if for example， the green bits would have been 0，0，0。

 then it's very nice that the Alu compute something， but this value will be lost。

 no container in this computer will will be open for business so to speak。

 And if we set these green bits to 111。 then all of these containers will receive the same output simultaneously。

 So we can play with these bits as we've done in week 4 when we wrote programs although we did it in assembly and in symbolic way。

 we can do it with machine language and once again， we have a way to program this。

Architecture so that the A output output would be selectively absorbed by different locations in this architecture。

All right， moving along another thing that we have to remember is that the AU also computes and outputs to control outputs。

 which I think we call the ZR and NG and these two control bits document whether or not the Alu output is negative or zero and these two outputs play a key role in what will be described next which is the control logic of the CPU but before we talk about this logic I want to as promised I want to say a few words about the reset input that we see coming coming into the diagram from the left hand side at the bottom of the slide and of course when you build the chip all these sides up down left right mean absolutely nothing but it's useful to communicate about it when we talk about gate diagrams so let us say a few words about this reset bit and in order to do it we have to try。

To envision how the heck computer will look like if we actually set out to build it。 Well。

 it will be a black box。And as you see， this black box is equipped with a single pushdown button。

 and this pushdown button is called reset in our jargon。 and the idea is the following。

This black box， thex the he computer is already loaded with some program written in the hec machine language。

 And up until now it does nothing。 The program is inside， but nothing is happening。 Well。

 if you take your finger and push this reset button in and let go what will happen is that the computer will start running the current program。

 Well， you look at whatever comes out of this computer and in a few minutes。

 you will see that we can attach a screen to it and a keyboard。

 you look at the program's execution and at some point you decide to reset the computer or rerun the same program again。

 You take your finger， you push it inside the reset button， you let go and by doing this。

 the computer will restart running the same program again。 Okay。

 so this is the kind of behavior that we want to implement in in the control logic of the CPU among other things。

 All right， so now that we understand。How the reset button works from the outside of the computer。

 so to speak， let's go back to the CPU logic and explore the control logic of the CPU。

Well it doesn't make sense to talk about control if we don't have some instruction that gives a meaning to the control operation so here is an example of see instruction and it's a schematic instruction it's not zeros and ones but I use some mnemonics to and also color coding which is completely meaningless as far as the computer goes。

 I use these mnemonics and colors in order to emphasize that we have here here different fields of bits each field is designed to do something else in the overall computer architecture and when we talk about control I want you to focus on these three bits which we call the jump bits if you recall if the three jump bits are zero it represents a no jump situation if the three jump bits are one it represents unconditional go to and any other combinations of zeros and ones in the jump bits represents。

Conditional go to what I've just said is part of the heck machine language specification。

 and now it's the job of the CPU to turn this specification into reality。

 to realize this abstractstruction。So how do we do it Well the hero of our story is a humble register called program counter。

 it's actually a counter and the program counter is also called PC in our jargon and in what follows we want to focus on what happens inside the PC so here is the desired operation of a typical program counter。

First of all， and foremost， the one thing that we want the program counter to do is to always emit the address of the next instruction that has to be executed。

 so let's keep this in mind。Now， if you want to start or restart the computer， well， in this case。

 we have to set PC to zero because we want to execute the first instruction in the program。

So p equals0 makes a lot of sense。Otherwise。If we have a no jump situation。

 if the current instruction is such that the 3J bits are zero。

 then we want the program counter to increment by one step so that the next instruction that we will execute will be instruction number one and then instruction number two and three and4 and so on as long as we don't have a jump。

However， if the current instruction is such that all the J bits are one， then we have a conditional。

 I'm sorry， we have an unconditional go to and in the case of an unconditional go to。

 we want to set the PC to a why because if the programmer if the programmer knows what he' is doing then the programmer has already taken care to enter the address that we want to jump to to the a register。

 so if we do PC equals a PC， the program counter will emit the address of the next instruction that has to be executed and finally。

 if only some of the J bits are1 one or two of the J bits are1， then we have a conditional go to。

If we have a conditional go to， we have to look at the A output and decide if this go to should actually materialize。

 That's the whole idea of conditional。 We have to check if the condition is true or false。

 If the condition is true， then we want to make a jump。

 otherwise we want to ignore the go to and just do PC plus plus。

So I hope that you are convinced that this abstractstruction makes sense。

 that's exactly how a program counter has to work in every computer。

And what remains to be seen is how do we actually make it happen？Well。

 the answer is already on the screen here in front of you。

 the logic architecture is such that the PC will do exactly what we want it to do and let us convince ourselves that this is indeed the case。

Well， let's look at the reset input。And remember that in order to start the computer in order to cause the computer to start executing the current program。

 we push the reset button in and we let go so if PC， I'm sorry， if the register is one。

 we want to set PC to zero， otherwise we have to look at the current instruction。

And the current instruction may or may not have jumpbits if the jumpbits are。Well。

 given any combination of jumpbits， all the way from 0，0。

0 to 111 and all the possible eight combinations of three jumpbits。

 given every one of these combinations， we have to look at the jumpbits and simultaneously look at the Alu output and decide if we really want to carry out the jump So in the slide I describe this decision as a function。

 this F function which I made up completely meaningless in the computer architecture。

 but I'm using this symbol F to to try to say that we look at these two different pieces of data together。

 we combine somehow this information and we make a decision do we want to jump or not。

I store the result of this decision in the symbol load。And if you look at the diagram。

 you see that this load is actually the load bit of the program counter。

 So if load end ups being one， yes， we want to jump。

 So we do PC equals a PC equals the current value of the a register。

 which contains the address to which we want to jump。

 otherwise we do PC plus plus at the end of all this operation and when all the dust clears what we'll get is that the PC always emits the address of the next instruction that has to be fetched and executed。

This pretty much wraps up the description of the CPU implementation。

 and the only thing that remains to do is to actually build it。But before we set out to build it。

 we have to remember that all this complexity is just one element in the overall computer architecture。

 that said it is by far the most complex and interesting element in the architecture。

 and we are going to build it， not now， but after the next unit because in the next unit we'll describe the overall architecture of the head computer and then we'll get our hands dirty and actually set out to build both the CPU and the entire head computer。



![](img/56510cee9eda4f28448670bfa1252b36_2.png)