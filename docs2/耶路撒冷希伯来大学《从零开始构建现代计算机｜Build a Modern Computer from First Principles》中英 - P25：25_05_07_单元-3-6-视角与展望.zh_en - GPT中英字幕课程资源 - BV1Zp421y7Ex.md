# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P25：25_05_07_单元-3-6-视角与展望.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/d41319e54bfb33c563bfa358f7efe01f_0.png)

Welcome to the perspective unit of week 3 in which we do two things。 First of all。

 we answer frequently asked questions that typically come up when we teach how to build memory systems and we use this opportunity also to say all sorts of disclaimers about various things that we covered during this week。

 So the first question that I'd like to talk about is as follows during this week。

 we used flipflop gates without actually building them， We treated them as black box abstractions。

 What does it take to actually build a flip flop。😊，So Nom， maybe you will take this question。

In many courses on computer hardware， students are taught how to construct flipflop gates from basic Nand gates。

Once that is done， they continue with the usual thing。

 which is also done in practice of a complete separation between the way you use combinnatorial circuitty and the way you use sequential circuitty。

But at the beginning， they do constructed a flip flop from basic N gates。 In our course。

 we decided to skip that part and really focus on at the beginning and the difference between the combinatorial point of view and the sequential point of view。

 Nevertheless， it is probably a good idea to see the main trick。

 How can you get Nand gates to remember anything。 And this is as follows。

 So the basic idea is to take two Nand gates and connect them in a loop。😊，So we have here two inputs。

 each one fitting into one land gate， where the other input of the land gate is fed the output of the previous Land gate。

Now normally this is a noO， you're not supposed to connect combinnatorial gates in a loop， in fact。

 the hardware simulator we give in this course explicitly forbids it。

 and this is done for pedagogic reasons。Now， let us see how this thing works in this particular case where it's actually used。

So normally， this kind of circuit is supposed to be used when both of its inputs are set to one。Now。

 in this situation， we don't know what this nagate was to do because we don't yet know what this impus。

So because we don't know what's the previous value or the previous， there is no real previous here。

 but we don't know what the value here is。So we don't know whats the value of' the input test and we don't know it's the value of the output test。

 so at's the beginning we know nothing。But then what happens once we take one of these inputs and turn it to zero for a while？

At this point， because this is a land gate， we can immediately see that the output of this gate is going to be one。

Independently of what this question mark was。Once this is1， we know that this is going to be1。

 the output of this9 gate is going to be0。Now， once this is zero。

 we can fill in this question mark and make it zero。And then we have20 that are output 1。

 and everything is very stable here。Now， so what's so interesting about it。 Now。

 let us see what happens when this input if go goes up back to one。In this case， nothing changes。

Because this is a mandate gate， this output remains one。 So this these2 remains 1。 This remains 0。

 This remains 0， and everything is completely stable。

 So somehow we remember now that the last input that became 0 was this one because we have a0 here。

 Now， let us see what happens when something changes， for example。

 where at a different time step at a future time point， this one becomes 0。😊，Now， once this becomes0。

 this immediately， the output here becomes one。The output here becomes one， this becomes one。

The output here becomes zero。The output here becomes0， this changes to zero， and again this stage 1。

 so we're again stable。Now when we turn this back to one。To the normal state of one。

Everything remains the same because one N 0 is still one。

So everything is completely stable in this such new situation。

 which is different than the previous one， because now we have 0 here and one here。 While previously。

 we had the opposite values。 So now we remember that the last。

Input that had that was went down to 0 was the bottom one。

And this kind of behavior allows this loop basically to remember the last input wires that went to zero。

 and it's stable in each of two different situations。

 That's why flipflop is called that's why the name is flip flop。 It can either flip。

 So we have0 here and one here or flop that we have one here and0 here。 In any case。

 a change a momentarily change the input changes the output for the future。

 Now this is just the basic functionality that gets you to remember stuff。 Of course。

 when you want to actually uses in a nice flip flop like we have used the D flip flop。

 You first of all， need to put something around it which actually makes sure that the inputs are behave nicely and and choose which one of the outputs you want to take。

 And also you need to actually how somehow separate what happens within one clock cycle from what happens in the next clock cycle and that is done usually。

By putting another one of these and driving one of them with a clock and the other with the opposite of the clock。

 But we would't want to get into these details。 but just to show the basic idea。

 which is quite surprising how you can remember something even though you only have a Ngate。

 So thank you on for this explanation which indeed was somewhat intricate。

 and a follow-up question that typically comes up is that is Ngate the only basic technology for building memory systems today。

 Well， Shimunn， the truth is this is not the only way to construct Fflps in many other cases。

 fliptop are constructed using some basic physical properties of the underlying solid state physics of the devices that are used for this kind of storage。

 Now this kind of the details of such devices and how they remember anything is really physics or electrical engineering and not something that we touch in this course。

 Okay so here's the next question during this。This week we built a memory device which you call Ram。

 is this the only memory device that computers use？Well， the answer is definitely not。

 computeruters use various kinds of memory devices。

 of which the Ram is indeed the most important one。The RA， which stands for R access memory。

 stores both data and instructions。And it is a volatile device。

 meaning that it depends on an external power supply。

 So once you disconnect the computer from the power supply or turn it off。

 the contents of the Ram is effectively erased。So in addition to the RamM unit。

 computers also typically use another device called RoM， which stands for readon memory。

 So the ro is not only read only， it is also a nonvolat device， unlike the RamM。

 which means that it maintains its current content a long time over time and it does not depend on an external power supply。

 which makes it very convenient because the roM is where you want to put the program that have to work when you turn on the computer。

 you know this is what is known as the booting process。 So when you boot up the computer。

 the program which is stored or presstore in the roM starts running。

 and this program normally initializes all sorts of things in the operating system and in the computer。

 actually not in the operating system， but in lower level code， and the next thing that the roM does。

or the program that resides in the room does， it loads from the disk。

 the startup code of the operating system， and then finally we begin to see some windows on the screen and the computer sort of comes alive。

Another technology which you've probably heard of is called flash memory and flash memory is a technology which actually combines the good things of both the Ram and the rom On the one hand。

 it's a read readrite memory， you can both read and modify its contents。

 and at the same time it does not depend on an external power supply like the rom。

 So once you turn off the computer。 the contents of the flash memory remains intact。

 So we talked about RA rom flash， another kind of memory which which you normally encounter is called cache memory。

 So the question is， what is cache memory and why do we need it When one actually build the computer The memory is going to be a pretty costly part of the whole system。

And as you can expect， there are many different technologies for building memories。

 and the faster the memory is， the more expensive it usually is。 the larger the memory。

 the more expensive it usually is。😊，So an architect。

 a computer architect is always faced with a tradeoff of does he want to put more a money into the memory and make it larger and faster。

 or does he want to get a cheaper memory and maybe put the money more in the processing unit？

AA usual trade off is to have a large， cheap memory， maybe slow， also， and a very small， expensive。

 fast memory。And try to make sure that what the data that is very often used by the processor reside in the very fast memory while the data that is only rarely used resides in the slow memory。

 This way， you get the speed of a very fast memory while you have the size of a very cheap memory to do this correctly is a very intricate arc。

 and today， computers usually have whole hierarchies of caches， these are called caches。

 the small fast memory called the cache。 hierarchies of such caches that are faster and faster and expensive and more expensive and more expensive and smaller and smaller as they get closer to the processor and doing that correctly allows you to really get amazing effective speed of a very fast memory。

 even though there is only a very small， fast memory and a very large slow memory。😊。

Okay so thank you， Noam for this explanation and indeed from a physical standpoint。

 we have many different kinds of memory units and we discuss some of them in this perspective discussion。

And yet it's important to emphasize that from a logical perspective。

 all these different memory systems， you know the RA， the wrongm， the cache， and so on。

 they all look alike。 They all behave like a sequence of registers which are addressable and we can access any one of these registers and do something with a bit contents of these registers。

 So everything that we said during this week is completely applicable to every kind of memory that we discussed in this unit。

😊。