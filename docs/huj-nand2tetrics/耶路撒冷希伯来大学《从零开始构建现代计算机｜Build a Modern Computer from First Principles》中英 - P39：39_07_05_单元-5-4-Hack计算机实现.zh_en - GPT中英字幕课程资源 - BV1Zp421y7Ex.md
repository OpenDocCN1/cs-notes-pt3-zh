# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P39：39_07_05_单元-5-4-Hack计算机实现.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/86acf99aca187ac0e6c1c0c0f7950dff_0.png)

In this unit， we are going to talk about the overall hack computer architecture。

 and we are going to give you all the information which is needed in order to actually go out and build it。

So here we see the overall hardware architecture of the hec computer and we see that we have something new here。

 we have two fancy input output devices in particular we have Rster display unit that enables us to take values from the computers and actually display them in some sensible way that makes sense to humans and we also have a keyboard unit that will enable us to interact with a program that currently runs in the computer。

 assuming of course this program accepts us to enter some values into it so this is how the computer looks like and as usual it pays off to think about the abstractstruction。

 so from the user's perspective or from the programmer's perspective。

 we have some sort of a black box magic or a computer that enables us to run on it programs written in the hec machine language。

Now this is not to be taken lightly because if for example。

 we will write a Java compiler that translates from Java to heCC machine language。

 well this computer will be able to run Java programs and in fact this is something that we do something very similar to this in the second part of the course which we will describe at the end of this course。

 so abstractly we have a general purpose computer that can run any program that can be translated into heCC native code。

So this is the top down description or obstruction of this computer。

 We can also describe this computer bottom up。 How do we build this computer Well。

 it turns out that we can build this computer using some of the chips that were built previously in this course that actually you built and all we have to do is put them together in some judicious way and well get an architecture that enables us to realize the obstruction that we just described。

So once again， this is the overall architecture and what we'll do in this unit is focus on every one of these three pieces and describe first of all。

 what it does and second of all how we can actually build it。Let us start with the CPU。

 which is the centerpiece of the architecture。 and I don't want to talk too much about the CPU because I just spent about 20 minutes talking about it in the previous unit。

 So I'd like to kind of gloss over what the CPU is supposed to do in the overall hardware architecture。

Here is the interface that we've seen in the previous unit and let us explore this interface in the context of three possible hackCC instructions。

 How will the CPU or how does the CPU supposed to do to deal with these instructions。 Well。

 everything is being done according to heCC language specification contract， if you will。

 So if the instruction mentions the mneumonics DNA。

 the CPU is going to manipulate the respective DNA registers， which reside inside the CPU。

If the instruction is an A instruction， well in this case the CPU is going to take the data value。

 the 15 bit socalled X in this instruction， and it is going to put them inside the A register。

If the right hand side of the instruction mentions the p mneummonic M。

 then the CPU expects to see this value or some data value in the in M input of the CPU interface。

 That is this input is supposed to contain the value of the currently selected data memory register。

And if the instructions lefthand side contains the mneummonic M as one of the destinations of the operation。

 and we see it in the last example here in the third instruction in the slide。

 So if this is the case， then the L output should be stored in the main memory。 In this case。

 we discussed it before， we have to provide three different pieces of data。

 the value that we want to store the address where we want to store it and the control bit。

 So this is done by the CPU in the way that was discussed in the previous unit。

Moving along let's see how the CPU handles jumps so once again we have a typical jump situation。

 the A register already includes the address 00， we assume that this is the case and now we have a conditional jump D equals d minus1 and if the result of this operation or the AU output is0 we want to jump。

 jump where to the address that was specified before to 100。How do we do it？ Well， if reset equals 0。

 which is normally the case when a program is running。

 reset equals 0 because the user doesn't touch the reset button。

 then the CPU logic uses the jump bits and the A output to decide whether or not there should be a jump。

If there is a jump， PC is set to the value of the a register。 if there is no jump， PC is incremented。

And the updated PC value is emitted by the PC output of the CPU。 If reset equals1。

 it means that the user wants to reset and rerun the program from the beginning。

 so in this case PC is set to zero and that's the end of the story。

So this in a nutshell is the contract according to which the CPU is supposed to operate in the overall computer architecture。

Moving along， let us discuss the data memory。The data memory， if you recall。

 is the area in which we store all the data of the program and， and here is how we do it。Well。

If we think about this data memory from a programmer's perspective。

 it's convenient to think about it in terms of three different segments。Logical segments。

 if you will， addresseses 0 up to 16 K are used to store the data that the program generates and manipulates。

 The next 8 K of the memory are used to store the screen memory map。

 If you want to draw something on， on the screen， you have to manipulate bits in this memory segment。

 And finally， the last register in the memory is used to reflect or to tell us which key is currently being pressed on the keyboard。

Now， once again， this is an obstruction， right， This is how the programmer expects this memory to operate。

 And now let us turn to discuss how we actually make it happen。 Well。

 we do it by building the memory from three different sub chips， if you will， or chip parts。

 as we call it in our HDL jargon。 So the first segment is just a standard ran chip。😊。

The next segment is a special chip called Sc。 and the last segment is yet another special chip。

 which we call keyboard。 And in the next few minutes。

 I want to say a few words about every one of these chip partss。 So let us start with the Ram。

 The Ram is trivial。 We've built it in project3， I believe one of the chips that you built was called Ram 16。

 So we just plug it in and this gives us the necessary implementation。

 And notice that the inputs and outputs of the Ram 16 are identical to the inputs and outputs of the overall memory chip。

 So whoever builds this chip has to make sure to take the outside inputs and outputs so to speak and connect them and make the connections that will funnel these values into the inner chip partss into the Ram Ram 16 k chip part。

😊，Moving along， the next segment in the memory， if you recall is called screen and before we talk about the implementation of this memory segment。

 let us remind ourselves what we mean when we say memory map Now we discussed it at length when we talked about hack programming So I'm not going to repeat it。

 or will just gloss over the main ideas。 So we assume that we have a display unit consisting of so many rows and so many columns。

 it's a black and white display device we assume that we have an area in the memory that controls this units so that when we change when we change bits in this special memory area。

 the architecture refreshes the screen accordingly and this refresh happens several times each second。

Now there's also a mapping that tells us how to relate。

Coordinates of pixels on the display unit with specific bits in the in the memory map。

 And once again， we discussed this before。 you're more than welcome to stop the video and make sure that this mapping makes sense。

 And this is how the memory map is specified and designed in the context of the he computer。

So how do we implement it Well， we use a special built- in screen chip that knows how to automatically quote unquote。

 refresh a connected display unit。 Now I want you to notice that in the most part。

 there's nothing special about this chip。 It's just a regular RAM chip。 However。

 it has this nice side effect of refreshing a connected display unit。

So this is the chip that we are going to use in order to implement the memory。 I'm sorry。

 the the display effect of our computer。Moving along， what about the keyboard？Well。

 the keyboard is implemented with a single register， a 16 bit register， which we call keyboard。

 and this register is connected to a standard keyboard similar to the one that you are currently using。

And we discussed it once again， we discussed it in week four， how do we handle inputs well。

 if we don't touch the keyboard， the keyboard register is going to emit the value zero。

Or and it's going to contain the value 0。 If we take our finger and touch or press one of these keys。

 the scan code of this key is going to be stored inside the keyboard register。 So， for example。

 if we press K， it turns out that the scan code of k is 1，0，7 and 1，0，7，1，0。

7 is going to appear in binary in this register。 So as long as our finger is down， we'll see 1，1，0。

 1，0，1，1。 Once we take the finger away， it will show 0。Likewise， if we click something else。

 the number 4 turns out that the scan code of 4 is 52。 well see this value。 If we click space。

 we'll see 33。 if we click up arrow， we'll see something else。 So that's the deal。

 That's how the keyboard operates and what we see in the keyboard is called or we usually call it the keyboard memory map。

How do we implement it。 Well， once again， we use a special chip which is connected to the keyboard。

 And as I said before， I want to repeat it now， there is nothing special about this chip。

 It's a regular register。 that has a nice side effect。 And the side effect is it always reflects。

What the user is pressing on the keyboard。 And most of the time。

 it's 0 because most of the time the keyboard is not used。Alright。 how do we。

Read the keyboard well we talked about it in week four to read the keyboard。

 we simply probe the output of the keyboard register right we see that the keyboard register has an internal state that we don't see in this diagram here。

 but it also has an output pin just like any regular register so can we can read what comes out from the keyboard and from this information we know which key is currently pressed。

But if we use the keyboard in the overall context of the heCC memory。

 we have to probe the contents of memory register 24 or 24576。

 because this happens to be the address of the keyboard interface or the keyboard memory map within the overall address space of the memory unit。

Okay， so we know how to handle how to handle and build roughly the CPU。

 We know how to implement the memory。 We are going back to the overall computer architecture and I've added something little to this architecture。

 and this is the reset button， I want to remind you that if we actually set out to build this computer。

 We are going to have a black box with a reset button。

 and this reset button corresponds in my diagram to this orange reset oval that you see in front of you。

 And we are going to refer to this reset in the remaining slides in this unit。Okay。

 so with that in mind， the next thing that we want to implement is the instruction memory of the hec computer system。

 and we implement this instruction memory using a chip， which we call Ro 32 k。

 Let us assume that we have this computer sitting on the table。And next to this computer。

 we have a program written in the he machine language。In order to run this program。

 the first thing that we have to do is somehow load it into the computer， right。

 So we load it into the computer。 and in particular， we load it into the Ro 32 K chip。

 We press the reset button that we just discussed， and the program will start running。

 This is the abstraction that we want to implement。Now。

 I'm sure that many of you are stretching your head and saying， well。

 how do you actually get a program which。Res on a piece of paper or in some text file and put it inside the computer。

Well， it turns out that there are several ways to do it。

 One of them is to use plug and play rom chips。 So we burn our code。

 the machine instruction code into a RA chip， we take this RA chip。 We plug it into the computer。

 We press the reset button and the computer will start executing this this particular program。

 If we want to run another program。 we take this chip out and we plug in another rom chip that has another program burned into it。

 And this is actually quite similar to the way some game consoles operate。

 You have some cartridges with games that you plug in。You play a certain game。

 you want to play another game， you plug in another cartridge and so on。

So that's one way to implement it。 Another way to implement it is using hardware simulation and that's what we're going to do in this course。

 we use a hardware simulator。 if we use a hardware simulator。

 we have the freedom to do many different things and indeed we are going to use a built-in Rom chip that actually once again there's nothing special about it because it operates very similarly to a RAM chip that you built in in project 3。

 but it has a nice side effect that it allows you using simulation to load programs into it residing programs that are residing on regular text files and let me take a minute and and illustrate how this is actually being done in our hardware simulator。

Welcome to the HeEC CPU emulator。The CPU emulator is a Java program that gives you a visual rendition of what is happening inside the he computer when a program is being executed。

And indeed， if you look around， you will see all sorts of familiar elements from the hackCC platform。

On the left hand side， we see the instruction memory and right next to it， the data memory。

And below we see the current value of the a register here and the current value of the D register there。

And there's also a visual rendition of the Alu operation。

Another control of interest is this one which shows you the current value of the socalled program counter。

 the program counter is a register that contains the address of the instruction that will be executed next in the program which is currently loaded into the instruction memory。

Now， right now we have no program in the instruction memory， so let's go ahead and load one。

So I click this control here。And。I have this folder called program examples。

 so I'm going to select it。And inside program examples。

 there are all sorts of hack programs I'm going to select the first one， add 2。

And click the low drum。Button。And I see that now the instruction memory contains what seems to be a sequence of he machine instructions written in assembly。

 I'm sorry， written in assembly language。 Now， if I want。

 I can look at these instructions in binary format。And yet， as we argued before。

 it's much easier to think about the program and display it and understand it when it's visualized using these assembly commands。

Now， according to the rules of the game or more precisely according to the rules of this program。

 in order to run it， we first have to enter some numbers into the Ram。

 so let's see I'm going to enter， let's say， 12 here。And seven there。

These are completely arbitrary values， and hopefully the program will end up summing up these two values and putting the result in Ram2。

So to check that this is actually the case， I can begin running the program and I do it by using this visual metaphor here of。

In advance sort of VCR control。 So let's let's advance and execute the first instruction。 Well。

 nothing dramatic happened。 Let us execute the next instruction。

And I see that the D register became 12， so we managed to load the contents of Ram 0 into the D register。

 Moving along， I now execute the next instruction which was at one。

 and indeed I see that the value of the a register is now1。

Let's do the first instruction D equals D plus m， and indeed we see that the current value of D became 19。

 which is 12 plus 7。And finally， we execute at two。

Wwhich selects this register here in the RA register number two， I see it here as well。

 and finally m equals D and indeed we see that Ram 2 became 19。

 so lo and behold it looks like the program is actually working。

Now notice that the program counter is6， so if I keep on executing commands。

 I will continue to execute whatever resides here in memory in all these addresses。

 which is a little bit worrisome and I will get back to talk about it later on。Alright。

 now let us suppose that we want to rerun this program from scratch。

 So what we can do is rewind the program so to speak now there is no rewind in computers。

 but this visual metaphor here indicates that the program counter has been set to zero and this actually causes the computer to to set itself to a position in which it can start。

Executing this program again。 So we can， you know， try some other values here。Let's。

 let's enter just the first value is now-5。 and I'm going to rewind once again and now I'm going to fast forward。

 which actually means just， you know， let the whole program execute。Autoomatically so to speak。

 So we see that the program is indeed executing without any help from us。

 And let us pause it for a little while。 And we see that we got the right answer。

 which is 2- 5 plus 7 is 2。 And if we continue to execute it。 the computer will kind of。

Spin its wheels， so to speak and we'll execute all these null instructions and indeed we see that nothing is actually happening but the program is kind of out of control and we have to think about way to resolve it。

 But for now， what is more interesting is the fact that we learned how to execute a program and how to inspect the various controls here and convince ourselves the program is actually doing what it's supposed to do。

So now that we understand how the realm comes to play in simulation。

 let's go back to the general specification of the realm， it's。Almost the regular。Memory chip。

 It has an address coming in。 It has some output coming out。 It's a wrong device。 read only。

 so we don't have any machinery that enables writing into it。And if you recall。The output of。

 of the rom is always the contents of the register that is selected by the address input。

So if I enter 17 into the address input， what will come out is the contents of register number 17。

So it makes a lot of sense to take this room and connect it to the program counter。😰。

Because the program counter always emits the address of the next instruction。

So if we feed this address into the room， we are guaranteed that the rom will always emit a 16 bit value that we can treat as the current instruction。

And if the PC is doing what it's supposed to do， then in every cycle。

 the PC will provide the address of the next instruction that we want to execute。

 and this is after taking into consideration all the gotos and the conditional gos and so on and what will come out from the realM is always the current instruction that we want to execute。

As if by magic， of course， we know that there's nothing magical here because we are going to build everything all of this ourselves。

😊，So having said that， we can now finally wrap up this discussion and talk about how we build the overall computer architecture。

 Okay， so we start with a CPU。😊，And as was just discussed， we connect to it the instruction memory。

 which we call ro。 and we connect it in exactly the same manner that we just discussed。

 So the instruction input of the CPU is taken from the output of the instruction memory。

And so we have a current instruction to operate on and in the process of executing this instruction。

 we are going to compute the address of the next instruction that has to be fetched and this address is going to emitted is going to be emitted by the program counter and it goes all the way into the address of the instruction unit of the instruction memory unit and this unit in turn will then emit the next instruction that has to be executed in the next cycle。

 Now the CPU in this subdia here is kind of spinning its wheels and nothing is actually being done with with its outputs。

 so in order to do something useful with the outputs of the CPU we connect them to the memory unit according to the contract that we describe several times what we want to write where we want to write it and load it and finally we take the output of the memory and we connect it back into the CPU because many。

Instructions will want to operate on the memory and not only write into it。

And this is all this is our computer architecture， all we have to add now is the overall interface of the architecture and the output and input units。

 and we see that the only thing that the user of this computer sees when he works with this computer is the display unit。

 the keyboard and the reset button。And this once again wraps up everything that we want to say about building this computer architecture。

And when I look at this architecture and reflect back on everything that we did so far。

 I'm reminded by this quote about what it means to be beautiful。We ascribe beauty to that。

 which is simple， which has no superuous parts， which exactly answers its end。

 which stands related to all things， which is the mean of many extremes。

 This was said 120 years ago by Ralph Waldo Amazon。

 I hope that you too agree with me that the heck computer is is beautiful according to this standard。

 And one reason why it is so aesthetic is because it's incredibly simple。 Now。

 all you have to do in order to build this computer here。

 provided that you build these three chips is write something like three lines of HDL code。

 which is quite remarkable。😊，And so this exactly is what we are going to do in the next unit now that we describe the overall architecture。

 we will show you how to actually build these three chips， put them together。

 and have a head computer that you can actually use to run every program that comes to your mind。



![](img/86acf99aca187ac0e6c1c0c0f7950dff_2.png)