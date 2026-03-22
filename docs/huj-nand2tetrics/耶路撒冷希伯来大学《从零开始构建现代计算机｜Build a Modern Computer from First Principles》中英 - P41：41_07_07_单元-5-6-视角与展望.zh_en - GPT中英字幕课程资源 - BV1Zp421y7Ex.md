# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P41：41_07_07_单元-5-6-视角与展望.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/84a9fad02291dbb626a0178cdf207b0c_0.png)

So welcome to the perspective unit of week five in which we integrated all the chips that we built before into a full blown computer system。

And during this week， we discussed two different computer architectures。

 the Fon Neiman architecture and the Harvard architecture。

 so perhaps we can start the perspective unit by asking you Noam to summarize for us the main architectural differences between Fon Neiman and Harvard。

Well， in our hack computer， we had a separate read only memory for the program and a separate data memory that was readr。

 separating between these two different memories is sometimes called the Harvard architecture which I tend to view as just a flavor if you wish of a vonuyan architecture in a classic vonuyan architecture。

 you have a single memory that contains both the data and the program。😊。

As we explained in the second unit of this week， doing it。

 a classical way has a tiny complication that you need to separately fetch an instructions that is access a program instruction and separately at a different time at the next cycle。

 execute the program which requires accessing the data memory in our Harvard architecture we had the program in a separate memory unit basically we could do both of them in a single cycle which made it a bit simpler。

😊，Now this architecture as is is probably very appropriate for sometimes what's called embedded computers where for a computer that does a single thing that was pre programmegrammed to it and just put into Rome a general appropriate computer in which you want to keep on changing the program that you run。

 you would probably need a full real ven Neman architecture the differences are not that big between these two architectures as we saw in a unit two of this week and we chose to take the simplest one again keeping with the simplicity of our whole approach so nowam if I the studio explanation one implication of moving from Harvard to Phmon architecture is that in Ph Neman we expect the computer to do different things at different cycles or different points of time so is there some organized way in computer science to model this different behavior of computers Abutely the standard。

way of doing it is via the formalism of a finite state machine。

 A specification of the different things that the computer is supposed to do at different time steps and how it' supposed to move from one state into another。

 Let me demonstrate。Okay， so the idea is that for every possible state that a machine can be in。

You have a circle。And you have arrows between the different different circles or different states of the machine that tell you from which state do you move to which other state and why。

In each state， you can write what are the kind of things that the machine needs to do in that situation。

 For example， maybe in this state， you want to add one。To the program counter。

 and maybe you want a certain address。To get a certain value， for example。

 the value from the memory address addressed by a。And so on in every different state。

 you can write this information in terms of the state。

This gives you a very clear picture of what needs to be done in every possible state and where。

 what kind of state do you move for， do you move to after everything that happened， For example。

 you may move from here to here。 if the clock if the current clock cycle changed or if the current memory location has value 0 or various other situations that are can be found in the hardware。

 the values of the different hardware logic。 So once you specify this in this kind of formalism and this kind of finite state machine formalism。

 Now we can translate this to the normal registers and combinator logics， it will already know。

 the trick would be to simply add another register that is called state。😊。

It registers it will encode in which one of these cycles are we。

 in our situation well need two bits to encode three possible states。So we'll have here too。

Once we have this state register， now we can write combbininatorial logic that basically affects everything that we need。

 so for example， if the two bits。just a register。 It has two bits going in and two bits going out。

 but all the combinatorial logics that we have can also accept the state as part of its input like it except the program counter is part of its。

😊，And so on， different combinatorial parts of our our computer accept various inputs。

 Now they also have this input， the state。 and， of course。

 they can do different things according to the different state。

 including deciding what the next state is going to be， again。

 as a function of the current state and all the other hardware signals in the computer。😊。

So the way you translate from this formalism。From the finite state machine formalism to this actual implementation is pretty straightforward and completely technical if you wish。

 once you actually coded everything， it's just like you organized hardware previously and that's an organized way to design computers that do different things and different times and move between the different times and different states in an organized manner one question that typically comes up when we teach this part of the course is that the he computer can interact with a keyboard and a screen and the question is what does it take to connect a computer to more peripheral devices you know in addition to a keyboard and a screen so indeed real computers have many peripheral units which are the screen。

 the keyboard mouse microphone disc and so on and so forths and also this architecture is scale。😊。

We can add more devices as we please， and the question indeed is how can you possibly do it？Well。

 just like we did with the screen and the keyboard。

 we can allocate memory space to represent every one of these peripheral devices and when we want to write something。

 for instance， when we want to sound something on the microphone or write something to the disk。

 we can write into memory certain codes that are later will be translated into physical signals that actually operate these peripheral devices。

But at some point， when you add several such peripheral devices。

 the CPU becomes extremely overloaded because the Po CPU has to not only run your program。

 but also manage all these peripheral devices。 So the typical approach is to offload the CPU from all this headache and use what is known as device controllers。

 So typically， when you add， for example， a disk， the disk will be equipped with the device controller。

 which is a dedicated hardware， which knows how to manage the disk。

 which knows how to translate operations from what the CPU wants to do to actual movements of the disk and so on。

 And something like this happens with every particular IO device and for example。

 take the screen in the hack platform， the screen is managed in a very simplistic way。

 When you want to turn on and off a pixel you simply。

TurOn and off a bit in memory and you assume that at some point this manipulation will be refreshed or will cause the screen to be refreshed So the CPU is in charge for everything If you want to draw a line the CPU has to actually write all these points all these bits into memory and and the line will get drawn at a certain point of time。

 in a real computer the screen comes equipped with a graphics card or some graphics accelerator and this is a dedicated computer that can do all sorts of things internally so if we want to draw a line from one coordinate to another we can simply tell the controller go ahead and do it and the controller will will do everything which is necessary to compute which pixels have to be turned on and off and so on。

 So once again we can add many I devices as we please。in principle。

 it will be very similar to what we did with the screen and the keyboard。

 but there are numerous details involved which are specific to all these different devices。



![](img/84a9fad02291dbb626a0178cdf207b0c_2.png)