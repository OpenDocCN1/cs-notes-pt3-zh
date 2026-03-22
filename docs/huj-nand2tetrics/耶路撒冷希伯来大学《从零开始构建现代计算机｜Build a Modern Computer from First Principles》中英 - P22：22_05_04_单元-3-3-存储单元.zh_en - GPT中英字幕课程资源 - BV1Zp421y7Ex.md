# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P22：22_05_04_单元-3-3-存储单元.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/335f2c4e0e57970f8a64f540b7874bd0_0.png)

So now that we went through the theory of sequential logic and time。

 we can go ahead and begin building the memory units that we need in order to build our computer。

Before we do that， let's revisit the phone line on architecture and observe that one of the major players of this architecture is something called memory。

Now， when we say memory in computer hardware， we mean many different things。 First of all。

 there's main memory， which consists of the memory that resides actually inside the computer and hardwired into the computer's motherboard。

 and this main memory also divides into several different categories of memories。

 The most famous one is called Ram or the random access memory。😊。

And then there is secondary memory like hard disks and memory sticks and and so on。

 And then there's also the distinction between volatile and nonvolat memory。 For example。

 when you pull out the plug of the computer。 the Ram is effectively erased。 at the same time。

 the information which is stored on the disks and on flash memory and so on。

 Pers even when the computer is not connected to a power supply。 So we have this distinction。😊。

The REM is used to store both the data on which our programs operate， as well as the instructions。

 which are the building blocks of the programs themselves。

 and we will talk about this duality later on in the course when we talk about the overall computer architecture。

And finally， another comment that I want to make before we actually start this unit is that like anything else。

 when we talk about memory， we can talk about it from a physical perspective。

 how we actually build the memory， what kind of technology we we do we use in order to realize the memory。

 and we can also talk about the logical organization of the memory。 Now， in this unit。

 and in this course in general， we always focus on logical considerations。

 And we focus in particular on the Ram unit， which is once again。

 the most important element of the computer's main memory。😊，Alright， now。

 before we actually talk about the Ram， we have to step back and talk about the elementary building blocks from which memory is designed。

 So the previous unit ended up with a description of how a single bit register works。

 And it doesn't take a big stretch of imagination to understand that you can take several such1 bit registers and put them one next to the other。

 And by doing this， you can create an abstraction of a 16 B number。

 And we call this abstraction register。The width of the register in general is a parameter。

 We call it W。 And in some computers， it's 16 B in other computers， it may be 32 B or 64 B。

 it turns out that it's not a terribly interesting parameter because everything that I say in this lecture works for any width of of memory that you might encounter。

 But from now on， I'm going to use W equals 16 because we are building a 16 B computer So we do this without loss of generality。

Another thing that I'd like to say is that I'm going to use a lot。 The term registers state。

 And in fact， this term was introduced in the previous unit as well。 A state is the value。

 which is currently stored， quote unquote， inside the register， to say it more precisely。

 This is the value， which is currently being expressed by the internal circuits of， of the register。

 This is a more， I think， accurate description of what's going on。 It creates an illusion of。

 of storage， if you will。Alright， so here is the register。

 And let's take a user's perspective of this of this device。

 How do we read the value of this register？ Well， it turns out that all we have to do is probe the out output。

 Why Because at any given point of time， the out output simply emits the state of the register。

 So if we just look up the value that comes out from out。

 we know what is stored inside the register in this particular time cycle。 Now。

 let us talk about how we write a new value into the register。 So， you know。

 we want to we want the register to remember the number 17 from now on。 What do we do。 Well。

 we set in to this new value， let's say 17。 and we assert the load bit。

 when I say assert the load bit。 I mean， we set the load bit to one。 So here's what will happen。

The register state becomes V。And from the next cycle onward。

 the output of the register will also start emitting this value V。 So from the next cycle onward。

 the register will effectively store the new value 17。

 and it will keep on storing this value forever until we decide to change this value in the very same manner that I just described。

 Allright， so we are now ready to give you an example of a register chip in action。

 and in order to do this， we will fire up how the as simulator and show you how the register chip works。

 So to get started， I'm going to load one of my built in register chips。 And in order to do it。

 I will select the N to Teris folder and within it， I'm going to tools。😊，And within tools。

 I'm going to build in chips。 And by the way， everything that I do， you can do also on your computer。

 You know， all these folders are available to you also if， of course。

 if you have downloaded the Ntotetriris suite to your computer。

 So I'm selecting the built in chips directory。And opening it。

 And I see that I have all sorts of built end chips available to me。

 and all these chips are part of the hack chipet。 you know。

 these are chips that will come to play when we piece together the computer architecture。

 And one of these chips is call de register。 So let us load the de register built in chip into the simulator。

And if I look at the HDL code， I see that the HDL code is a little bit strange because it's a built in chip。

 you don't have to worry about it because you don't have to build built in chips in this course。

 you have to build them in plain HDL， but this code here says that this chip is actually implemented by a Java class called D register。

 which delivers the functionality of a 16 beat register。

So it also says that this chip is clocked because， you know， it's， it's a registered chip。

 So it receives a clock input。 And because the HDL includes the magical word clocked。

 we see that a clock icon has opened up in the control panel of the。Of the simulator。

 And this clock is used to simulate the progression of time within the computer。 or more accurately。

 it simulates。 it can be used to simulate a train of cycles。 So each time I click this clock icon， I。

Move one phase in the cycle。 So， you know， this was a tick。 This is a talk， tick， talk， tick talk。

 tick talk。 So I'm progressing the clock。Manually， and， of course。

 I can also write a test script that includes a command like while true Tiktok。

 which will cause the clock to to tick and talk forever or I can say something like repeat 10000 Tikts and so on。

 So but now we're going to do everything manually， and that's what you normally do when you build the chip and and test it for the first time。

 So because this chip is implemented by a Java class。 we added to the to these Java implementations。

 all sorts of nice features。 For example， the de registergister has a goi that it's a goi side effect that shows what is the current state or the current contents of this register happens to be 0。

 because this is the default。 So let's go ahead and change。

The the contents of this register is something else。In particular， let's change the register to。17。

My favorite number。 So I'm changing the in input， which is a 16 B value。Into 17。And I will。

Run the clock forward。 And I see that。Actually， nothing seems to happen。

The contents of the register remain 0。And so is the output of the register。 Well。

 nothing happens because I forgot to assert the load bit。

 So let's go to the load bit and turn it into one。And then we go back to the clock， we do a tick。

And we see that the contents of the register change to 17 which is very nice。

 but the output of the register is still zero and that's because you know it takes a complete cycle for the register to actually stabilize and begin to emit the new state so let's do a talk and indeed I see that once I move to the next cycle the output of the register is also 17 and from now on。

The register is in a stable state and the state is 17， and it will remain 17。

Until a point of time in which I will decide to change it into something else。Now， you know。

 one thing which I may want to do。Is set the the load bit to 0。

 And this will serve as a safety so that if inadvertently， you know。

 someone changes the value of this register， nothing will happen until the load bit will be asserted。

 So， so let's go ahead and， and change the value of the register， which is presently 17 to let's say。

23。Which is another one of my favorite numbers。So 23， and I as a little bit to one。

I do a tick and I see that now the register is kind of an inconsistent state because the state of the register is 23。

 but the output is still 17， once again I have to complete the cycle in order to get to the register into a stable state so I do a talk and now the register is 23 but both the state。

 the internal state of the register is 23 and also the register itself has committed to this new value and it emits the value 23 as well。

So now I continue to click the clock and the value of， of the register became 23。So， you know。

 this has been a demo of the typical behavior of the register and let's continue with the lecture。

 So now that we understand how the basic building blocks of memory work registers。

 we can begin to stack them together and build actual memory units。

And the general architecture of these units looks as follows， in fact。

 I can talk about it in terms of abstraction， the RA abstraction or the way we are used to think about memories is we think about them as a sequence of addressable registers as if every register has an address that range from0 to n minus-1 in case of a RA device that consists of n registers。

Now there's one thing which is very important to emphasize which makes this whole notion of RA much easier to understand and to comprehend。

 and this is the fact that irrespective of how many registers you have。

In this Ram unit and it may well have millions of such registers at any given point of time。

 only one register is selected and only one register is interesting all the other registers don't take any part in the game so to speak so at any given point of time we have to say which is the register on which we want to operate。

 which is the register that we want to read or which is the register whose value we want to change。

So we have to make a selection。 We have to determine this the address of this register and we do it using an input。

 which we call address。 So think about it。 if we have to select one out of n possible registers using some sort of a binary code。

 how many bits do we need in order to create such a code。 Well。

 it turns out that we need log of n such bits。 For example。

 if we have8 registers we need three bits right log of 8 on base2 is3。

 So register number 0 will be represented with a code 0，0。

0 register number 7 will be represented with a code 1。

11 and then we have all the possibilities in the middle。

 So the length of the address input which we call K in this diagram equals log of n the number of registers in this particular。

Ram device。 And finally， we have this W， which， as I said before， is not terribly interesting。

 W in our computer happens to be 16， but if you want。

 we can make this W equals some other number like 64。

 and everything that we say from now until the end of the unit will be just the same。

 So without loss of generality， W equals 16。Finally I want us all to remember that this is a sequential chip。

 it depends on a clock input and that's why we have this little triangle in the diagram and this means that it has a clocked behavior and the behavior is defined as follows if we use the label M to stand for the state of the selected register then if load equals1 M becomes in and from the next cycle onward the output of this register becomes M as well and if load is not one the output of this register will be exactly as it was before so this is the basic functionality of this RAM unit。

Let us say a few words about how we read and write values using this Ram device。

 So to read a particular register， we do two things。 first of all。

 we set the address of the Ram unit to the desired register number or address you know register number5 or something like this and then we probe the out of the register we probe out of the Ram unit and the out of the Ram unit is built in such a way。

 I mean the internal circuitry is built in such a way that the out always emits the state of the selected register。

 So in this case it will emit the state of register number I So that's how we read one register out of the millions of registers that may be present in this Ram device What about writing Well writing is slightly more involved if we want to write something into。

Register number5 using the same example， we set address to 5， we set into 17 for example。

 we assert the load bit and here is what will happen the state of register number 5 will become 17 and from the next cycle onward the RamM will start to output this value as well and from now until further notice register number5 will contain the value 17 until we change it again using precisely the same procedure so we know how to read and write individual registers from a given Ram device。

Okay， I would like now to give you an example of a RAM chip in action。

 so once again we are going to fire up the hardware simulator and we'll see some examples of how the values of the registers change over time。

In this demo， we're going to illustrate how a Ram device operates using the how simulator。

 So let us open our built in chip directory and look for some。RM device。

 We have several Ram devices in the hack chip set。 Let's select a Ram 8。 So I load the chip。

And this is a built in chip。 It comes with a nice gooey side effect。

 which we see here on the right hand side。And I can use this goi in order to put some values inside the Ram。

 So let's do it。啊。So I'm just putting some， you know， random numbers， really。

Inside some of the registers， and。We can leave some registers as0。嗯。I'm just。Entering values。

 you know， nothing interesting here。And， and that's it。Now。

 it should be understood that what I did here is is kind of cheating。

 That's not how you manipulate a Ram device in a low level fashion。

 so so let's let's go ahead and do it the right way， so to speak。

 let's decide that we want to read say register number 5。

 How do I read the content of register number5。 Well I go to the address input of the Ram device。

And I put the number five there。And nothing seems to happen。But if I run the clock。

 I see that the out output of the random device begins to emit the value8，3，7，3。

 which happens to be the contents of the selected register of register number 5。

 If I want to read another register， let's say register number one。Well。

 I change the address to number one， I run the clock and I see that I get the contents of register number one。

What about changing the contents of some of these registers。

 Let's say that I want to set the contents of register number 4 to 12。

 So I go to this address here to to I'm sorry， I go to the address input of the Ram。

I set the address to 4。I assert the load bit to enable the right operation。I set the value。

Of the in input to the desired value， which we decided is 12。And then I run the clock。

 So in the first tick， I see that the internal state of register number 4 became 12。

 but the output of the render device is still something else。

In order to commit the Ram to the new value， I have to complete the cycle。 So I do it。

 and I see that now the Ram device is also emitting the value of the selected register。

 which happens to be register number 4。 So let's say that I want to change another register。

 say register number 2。 Let us set register number 2 to the number 17。 So I go to。

To the address input， I set it to2。 I go to the input。To the in input， I change it to 17。

I run the clock and I see that register number two indeed changed to 17 and the out output of the Ram is now emitting this value as well。

So this has been a demonstration of how a Ram unit operates。 Now， in this particular course。

 we are going to build a family of 16 bit Ram chips。

 All of them are going to have exactly the same generic architecture。

 but the details are going to be slightly different。 So。

Here are the chips that we are actually going to build。

 we'll build a Ram 8 consisting of eight registers and the length of the address bit is going to be log of 8 which is3 log to the base two of8 Ram 64 contains 64 registers and six address bits then we'll create RA whose size is halfk of registers and then we continue with the Ram 4K and Ram 16k which is what we finally need for our hec computer platform so these are the5 chips that we are going to build and the construction of these chips is going to be surprisingly simple as you will see in the next unit Now sensible question is why do we need these five particular chips and the answer is quite simply because thats。

What we need in order to build our hec computer。And another interesting question that I sidesteppped until now is why is this thing called RAM to begin with。

 Well， RAM stands for randomom access memoryory。And。

I would like to note at the end of this unit that maybe we didn't give this chip the respect that it actually deserves because something really remarkable happens with this chip。

 and here is what actually happens。Irrespective of the size of this chip。

 irrespective of whether it has 8 registers or 8 million registers。

 I can select every register from this chip and apply an operation on it in exactly the same access time。

 which is truly remarkable。 All I have to do is enter the address of this register into the address input and boom。

 this register is going to be selected and all the other registers are going to be ignored。

 Okay now there's no boom in reality。 I'm doing it for dramatic effect。

 But actually it's quite dramatic because once again， if I now want to select a register number 5000。

 All I have to do is enter 5000 and boom， this register becomes irrelevant and register number 5000 becomes active and it kind of opens up for business。

 and it doesn't matter if I have 8 million。😊，Registers or 8 billion registers。

 I have this basic ability to select at random any register in this configuration and either read it or write it in the same access time。

 So this is truly a remarkable functionality and later on in this week you will actually build this functionality using HDL but before we do so we have one more chip that we need to describe and this is the chip that implements accounting operation and the chip is called counters and counter in singular and this will be the subject of our next unit。

😊。

![](img/335f2c4e0e57970f8a64f540b7874bd0_2.png)