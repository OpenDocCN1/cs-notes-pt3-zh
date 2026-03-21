# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P40：40_07_06_单元-5-5-项目5概述.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/2e9763448bb928798310a99fcd593948_0.png)

So throughout this week we talked about the computer architecture and how the various chips are synthesized into a single overall architecture and in Project 5 you actually have to build this architecture and test it using our project materials。

 so the purpose of this unit is to give you all sorts of tips and advice on how to do it。Well。

 before we get started， I want to begin with some overall broad overview of what we have done so far or what we are doing in the course in general。

 Well， we are building a computer。And the computer is implemented as a very high level chip。

And this chip makes use of two main components， a CPU and a memory unit。

 The memory in turn consists of several REM units which are pieced together。

 and every one of these REM units is basically a collection of many registers。

The CPU also includes several registers， if you recall the D register， the A register。

 it also includes a program counter and of course the AU that we built in project2 we can continue to resolve these chip partss into simpler or more basic chip partss。

 for example， the program counter makes use of a register and an otherer and the AU also makes use of another instance of an other chip and of course all these chips at the end of the story are based on elementary logic gates。

 those that you built in the first week of the course and also other chips。

 higherle chips make direct use every once in a while of these lower level gates。

Now if we look at what I've just described bottom up， then in Project1。

 we built the elementary logic gates in Project2， we built a family of adds that led up to the ALU in Project3 we built a family of registers that ended up with RE units and finally in this project we are going to take the fruits of all this hard work and put it together into a complete computer system。

 so basically we have to implement the CPU， the memory unit and then we have to implement the synthesis of these two highlevel chips into a complete working general purpose computer so that's what we'll do in Project5 so here is the abstraction of the hec computer and here is also the implementation that we discussed in the previous unit。

And we see that the architecture is based on a CPU。

 a data memory unit and an instruction memory unit which we call wrong so let us begin with the CPU once again here is the CPU in abstractstruct terms see we see here the API or the input and output units of the CPU and if we delve into the implementation we get this diagram that we discussed earlier in the course and here are some tips on how to build this relatively complex chip。

Well， first of all， if you look carefully， you will see that all the chip parts here are chips that we've built before in previous projects。

 So it's just a matter of taking these chips off the shelves。

 so to speak and piecing them together in some clever way。

 So how do you do it Well another inspection of this diagram reveals that we have all these C control bits that you see here and most of these control bits come from the current instruction。

 So here's， for example， a C instruction that consists if you recall of several fields and they used color which obviously is meaningless for the computer。

 but it helps me communicate with you So we see an instruction coming in。

 and your job as the designer of this chip is to unpack these control bits。

And send them or root them using HDL to their correct destinations in the various chip parts that make the overall architecture。

 So if you do this carefully， if you figure out which control bit has to go away。

 you will basically glue all these parts together in a logical way。 and at the end of this synthesis。

 you will get an overall CPU architecture。Now， actually I really glossed over quite a few details because it's not just a matter of taking these control bit bits and sending them to some destinations。

 you may have to add some logic that does some processing of some of these control bits in order to achieve the desired effect and also bear in mind that there' are also some control bits that come out of the ALU if you look at the diagram I actually forgot to circle them as well。

 These control bits also play an important role in the overall architecture and once again you have to write some HD logic that takes these control bits。

 combine them with some other information that comes from the instruction and piece them together in a way that achieves the desired effect Now we have intentionally we haven't giving you exact instructions on how to do it and intentionally。

Just use this catch all C label because we wanted to think about it and figure out yourself how to put all these things together。

 Once you do it， you will achieve the overall architecture of the CPU。

Here is also the stub file that we are giving you。 The stub file contains， you know。

 the documentation of the CPU， the names of the input and output units。 And then obviously。

 you have to provide the the missing implementation。Alright， so moving along。

 we have resolved the CPU。 and the next thing that I want to discuss is the memory unit。

 the data memory unit， which is the the unit that contains。😊。

The running program and the data that the program generates， the variables。

 and in a higher level language， objects， arrays and so on and so forths。Alright。

 so this is the memory obstruction。 It's a single address space that has an in and address inputs and an out output。

 and it also has this nice side effect of refreshing a screen and probing what the user is doing with the keyboard。

😊，Now the overall address space of the heCC memory consists of three logical segments。

 you know there's no physical separation， but there's a logical separation， if you will。

 so the first 16K of the memory are dedicated to the running program and the data that he generates。

 the next 8K of the memory dedicated to a screen memory map and the last register in the memory is represents the keyboard memory map。

So how do we build it？ Well， we have to realize this abstraction using chips that we already built before。

 and here is some high level diagram of this architecture。 So we have three basic chips。

 We have the Ram chip that we built in Project 3。Then we have a built- in screen chip which essentially is just a regular memory chip。

 so it's not really terribly interesting to implement it if you implemented the RA before。

 but it has the very nice side effect of refreshing the physical screen and finally we have a humble register called keyboard which holds the currently the scan code of the currently pressed key。

So。You have to write HDL code that takes an incoming address。

 whatever this address may be and funnel this address to the right chip part within the the overall address space。

 So if the address is below 16 k。 well， there's nothing to do with it。

 you simply retrieve the right register from the RAM chip part。 But if the address is between 16。

384 and 24，575， then you have to do something to take this address and and route it to the right address in the screen memory chip。

 and finally， if the address is 24，576， then you want to route it to to the keyboard memory map。

 So that's basically what your HDL code has to do。 And if you will do it you will achieve this glue that holds together these chip parts and delivers the。

Overall functionality of the data memory。All right， so we've resolved the CPU and the memory。

 and the only thing that remains to do is to figure out how to implement the ro。 Well。

 the ro is really a simpler version of the Ram。 It's it's just it's a Ram chip。😊，And yet。

 it's a read only device。 So it's actually easier to build than Norren chip。 And therefore。

 we decided not to bother with with asking you to build it。 and we supply it as a built end chip。呃。

We didn't do it only for that reason。 we also we supply a builtin version of the roomm because we also endowed this built in chip with the ability to load the program within the the hardware simulator so it's very convenient that we have this built in chip and all you have to do is take it and plug it into the overall architecture。

 So this is probably the easiest thing to do in this project。 So that's it。

 we built all the the three components that make up the architecture and the only thing that remains is to actually effect in HDL the very diagram that you see here in front of you。

 So you have to write a few HDL statements that connect the CPU to the memory and to wrong 32k in the same way that you see here in the diagram。

How do we do it Well we start with a STub file that gives you the API of the computer and then you write a few lines of HDL code that basically implement this diagram in HDL。

In order to do this project as usual you have to go to the website。

 read the project page that gives you all sorts of documentation about the files that you're going to need。

 all these files are already available on your computer as part of the Nanttetriris folder so you all set and you have everything you need in order to finally complete the computer architecture。

 there are a few more resources as usual that you're welcome to use and that's it。

 if you'll do that you will end up having a running computer and this will be the end of the hardware part of this course。

The next unit as usual， is perspectives。

![](img/2e9763448bb928798310a99fcd593948_2.png)