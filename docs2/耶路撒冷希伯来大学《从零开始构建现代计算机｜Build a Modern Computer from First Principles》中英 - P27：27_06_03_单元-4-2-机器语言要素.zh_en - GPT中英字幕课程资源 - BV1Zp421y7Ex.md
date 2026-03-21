# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P27：27_06_03_单元-4-2-机器语言要素.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/5e528bc0364ec31227736504d7c3f03e_0.png)

In the previous unit， we talked about the general idea of a machine language and how they control computers。

 What we want to do in this unit is discuss basic elements that appear in all machine languages。

 The main reason is to give you some context for what you will learn about the hack machine language in the next unit because most of the elements that you find in the hack machine language or。

 of course， elements that appear in some way in some form in our other machine languages。

 So we first start with a general description of the kind of elements you find in machine languages。

 a very elementary description that is missing a lot of more sophisticated features that youd find in many computers。

 and then you'll have this context for for the hack machine language。😊。

So the first important thing to remember is that the machine language is the most important interface。

 probably in the whole world of computer science。 It is the interface between hardware and software。

 is it is exactly the way that software can control the hardware。😊。

This kind of machine language needs to specify what does the operations that our hardware performs。

 where does it gets the data that it operates on， what is the control of the operations and so on。

In principle， and usually， this kind of interface is done in almost one to one correspondence with the actual hardware implementation。

 The idea is that the hardware is built in a way that directly corresponds to the type of functionality that it provides to the software layer above it。

 This need not happen always， sometimes you can want to provide nice functionality。

 even at this level， even to just so the compiler writers will be happy about the code they need to emit。

 and the hardware will be another layer removed from it。 But we're not going to talk about it。

 And in first， from first principles， basically the machine language specifies exactly the kind of things that the hardware can do for us。

😊，Of course， when we actually go to design a machine language。

 the basic element is a cost performance trade off。

 The more sophisticated operations that we want to give our machine language。

 the more large data types or sophisticated data types that it operates on。

 the more costly it will be to actually build this costly in terms of area of silicon costly in terms of times that the hardware actually needs to operate and so on。

😊，Of course， in our computer， we're always taking this kind of trade off to the simplest。

 We're trying to present the simplest kind of thing and not really worrying about real performance。

 But in any real machine， the whole thing that drives the design of the machine language is a cost performance trade off。

 So let's talk about the type of operations that our hardware work can perform。😊。

Each machine language defines a set of operations， and these fall into several categories。

 For example， they are arithmetic operations。 For example， addition of two numbers。

 subtraction maybe also multiplication or division。There are logical operations， for example。

 taking the end of two Bs or maybe the bitwise the end of two words。

And then there are also operations that controls the flow control that tell the hardware when to jump inside the program。

 So these are the type of instructions that we usually will have in any machine language and different machine languages define different sets of such operations。

 which may differ from each other in terms of their richness。 For example。

 some machines may may provide division as a basic operation。

 while other machines will decide not to do that because it's too expensive in terms of siliconon。

 but rather as the software will of course， have to provide that functionality。

Probably even more important is the question， what data types can our hardware access primitively？

 So there is a big difference， of course， between adding 8 bit numbers and adding 64 bit numbers。

 If your software program really need arithmetic and 64 bit values。 then， of course。

 hardware that performs in one operation addition of such 64 bit values will be at least eight times faster then hardware that needs to actually implement addition of 64 bit values by a sequence of additions of 8 bit values。

 Similarlyly， some computers can also provide so op provide richer data types。 For example。

 you may have your hardware support directly floating point operations， numbers that are not integer。

 but rather real numbers and deal with them provide addition multiplication division of them as a basic operation。

 If you want to do scientific computation， which works with these kind of floating point numbers or real numbers rather than just integers。

 Of course， such machines will be much faster。😊，Then machines that can only handle integers。

 basically。Well， the difference in set of operations that we've seen previously is quite obvious。

The next issue is probably even more important， although slightly more subtle。

 And that is a question， how do we decide what data to work on。

 How does the hardware allow us to specify what type of data values are we going to work on。

The basic problem that we have here is that what we're going to work on resides in memory。

 and accessing memory is an extensive operation。 It's expensive in at least two related points of view。

 First of all， if you have a large memory specifying what part of the memory do you want to work to operate on requires a large amount of just many bits to specify it。

Because you need to give an address in a very large memory。

And that's going to be wasteful in terms of the instruction。 If I just want to say， oh。

 add the last two numbers and cant I won't be able to just do that because I will have to specify two very large addresses in order to tell the hardware what to operate on。

The second element， which is closely related is the fact that just accessing a value from a large memory takes relatively a large amount of time compared to the speed of the CPU itself of the arithmetic operations themselves。

😊，So the way to handle these two things， the way to give us good control over what type of what type of data are we working on without requiring all these costs of specifying a large address and getting the information from a faraway place。

 if you wish， in terms of time， the basic solution was what's called a memory hierarchy。

 and this was already figured out by Voon Neiman when we built this first computer。The basic idea is。

 instead of having just one large block of memory， we're going have a whole sequence of memories that are getting far bigger and bigger。

😊，The smallest memories are going to be very easy to access。 first of all。

 because we don't have to specify a large address space because there are only going to be a very few of them。

 Second of all， because there are only very few of them。

 we can actually get information from them very quickly。

 And then there is going to be slightly larger memories， usually called cache。

 and even larger memories， sometimes called the big the main memory and maybe even even larger memories。

 that are going to sit on disk at each time we get farther away from the arithmetic unit itself。

 our memory becomes bigger。 accessing it becomes harder both in terms of giving larger。

 a wider address and in terms of the time we need to wait until we get the value。

 But we have more information there。😊，The ways that the different levels of the memory hierarchy are handled differ according to the different levels。

But what we're going to discuss now is the way that registers the smallest。

 the smallest memory that usually resides really inside the CPU， how we handle that。😊。

So almost every CPU has a few very small amount of memory registers that are located really inside the CPU。

 Their type and functionality is really part of the machine language and the main point is that since there are so few of them addressing them requires very few bits and getting the information of them is extremely quickly。

 They are built from the fastest technology available and they are already inside the CPU。

 So there is no delay in getting any information from there。😊，So what types of registers do we have。

The first kind of thing that we will do with these memory location registers that are inside our CPU is just use them for data。

 For example， we can put numbers in them and have operations saying something like add the register one to register two in this situation。

 basically what will happen is the contents of register one will be added to the content of register too if that is the meaning of this operation in our machine language。

 So once we have a small number of registers inside the CPU we can do lots of operations and a small amount of a memory very。

 very quickly。The second kind of things we do within these registers is use them as addresses。

 we can also sometimes put into one of these registers an address into main memory。

 which will allow us to specify which part of the rear of the bigger memory we want to access for operations that we want to access。

For example， if we have a operation like store， register one into memory address that is specified by the register called A。

 then what will happen is once we actually perform the hardware， perform this operation。

That number 77 will be written into the main memory。

 This can be an operation that takes a larger amount of time than internal operation to the CPU。

 But the important point is that the address into which we write this information was actually given by the a register。

 This is another type of usage we have for registers that are inside our main memory。😊。

Once we have these registers now we can think about go back to the original question。

 how do we decide which data to work upon How do we tell the computer for an operation。

 let's say a simple add operation。 What is it supposed to operate upon and there are a bunch of different possibilities here are four possibilities。

 These are sometimes called addressing modes and some computers have other possibilities as well。

 Sometimes we just want to work on these registers。 So for example。

 we can say add register to one to register to。 And this means， of course。

 it's addition operation is on two registers。Sometimes we have direct access to memory。

 we can have an operation saying， add register 1 to memory location 200。

 in which case we're telling the computer to directly address not just the register one。

 but also a memory address that we just specified inside the command。

Yet another possibility is what's called indirect addressing and this is an example we had previously for using the air register where the memory address that we access is not specified as part of the instruction。

 but rather is already written inside the address register that already was previously loaded inside the CPU with some correct value。

😊，And yet another possibility is that we actually have a value inside inside the instruction itself。

 For example， we can say add 73 to register 1 and 73 is a constant 73 is part of the instruction。

 So all these are different ways we can actually tell the computer which values。

 which data to work on in each instruction。😊，When we are talking about how to where to takes the data from and where to put it。

 we might also add something that is usually piggyback upon it。

 which is how do we deal with input and output in most machine languages。 So as we all know。

 there are enormous amount of input and output devices。

 printers and screens in various sensors and keyboards and mice and mouses and so on。

 So one way to actually access these input or output devices is to actually connect them。

 connect the registers which controls them these output devices as part of your memory。 For example。

 we may have a mouse that is connected in a way that whenever the user moves the mouse。

 that last movement is written into some kind of register and that register is accessible by the computer in a certain address as part of the memory。

 This gives us access to input and output as though we're accessing the memory itself。 And。

 of course， the software that actually deals with it。😊。

Software that are usually part of the drivers in an operating system must know exactly not only what are the addresses to which this input or output device is connected。

 but also how to speak with it， What does the values in what locations， What do they really mean。

 The final element that to wish to discuss is what's called flow control。

 How can we tell the hardware， what instruction to execute next。So usually it's very simple。

 usually if I now was an instruction 73， the next instruction will be 74， that's a normal situation。

 but there are situations where of course we need to change the flow of control and not just continue doing instructions one after another。

😊，The first reason is sometimes we just need to go back to a previous to another location。

 for example， doing a loop or maybe jumping to another part of the software。

 just because now is the time to jump to another part of the program。

So this would be what sometimes is called an unconditional jump。

 And one of the main uses for it will be actually be to do a loop。

 Suppose we want to actually start and do something for values 1，2，3，4，5，6， and so on。

 The way we do it will have some kind of register holding these values。

 Each time we want to add one to R1。let's say if that is a register that we chose to actually have this value。

 and then we do whatever we need to do with this new value。Now we next want to do the same thing。

 but with the next value of R1， the way we do it， we have to tell the computer， oh。

 after after you do instruction number 156 in our example， don't continue to instruction 157。

 but go back to instruction 102， which basically adds one to R1， giving us the next value of R1。

 and then continue doing whatever you did with a new value。😊，So this allows you to do a loop。

And we should。 And machine languages always have some kind of capability that the software tells the hardware to do something again or to return back or to jump to a different direction。

 Notice that the actual address is 101，102 and 156 are not really that important。

 What is really important that when we jump to address 102。

 we need to be the address that we're actually meaning。

 So we could have do this in a symbolic matter in the same way in the following way。

 Just give a name to important locations。 For example， location at 102， I give it a name loop。

And then I say jump to loop。 This doesn't really change anything。

 This is exactly the same thing when we actually write it in bits in our machine language。

 but it's more convenient for humans to look at。 So we'll just do that as part of the way of describing programs。

😊，Then there are other cases which we need to handle flow control where we need to do what is timetime called a conditional jumps。

 In some cases， we want to jump to this another location， while in other cases。

 depending on let's say the last instruction that we performed or according to the value of some register or according to some other condition in some cases。

 we want to jump to another location， in other cases。

 we just want to continue for the next instruction。And this is called a conditional jump。

 For example， suppose I want to do something and the absolute value of a number。

 So if the number is positive， I just want to do some operation on the number。

 But if a number is negative， I want to first turn it into to be positive and then work on the positive version of it。

 The way we can do that， we can have a conditional jump。 jump greater than。

 which means if our one is greater than 0， I want you to jump to the label con。

 This is just a number， just the name that I made up。 Otherwise just continue。😊。

This means that if we have a positive number， then we're not going to do the next instruction。

 the subtract instruction。But if we have a negative number。

 we're just going to continue directly to do the subtract instruction。

 which really does takes R1 and negates its value， makes it positive。 Now， in both cases。

 we are continuing with the same sequence of instructions。 And now we already have an R1 anyway。

 a positive value。 So this is another is an example while we sometimes would need the conditional jump and machine languages always have some kind of some kind of apparatus。

 some kind of way to actually instruct the hardware to do this kind of conditional jump。😊。

At this point， weve finished a very， very quick， very high level。

 very basic overview of the type of instructions that machine languages provide。

 and now we are ready to actually talk about our computer， the hack machine language。😊。



![](img/5e528bc0364ec31227736504d7c3f03e_2.png)