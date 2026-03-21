# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P23：23_05_05_单元-3-4-计数器.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/03440b7bfe8f80a2eee6936ab33e2906_0.png)

The last chip that we have to build in in this week is called counter。

 and before we set out to describe the counter， I'd like to say a few words about the context in which counters come to play。

So let us assume that I have a domestic robot in my home。

 and I want to cause this robot to bake some brownies for me。So here's what I'm going to do。

 I'm going to write a very specific program consisting of something like 50 instructions that tell the robot exactly how to bake these brownies。

 and I'm going to mount this recipe on the kitchen wall and next to the recipe。

 I'm going to put a counter that emits a number that tells the robot which instruction the robot has to execute next。

 So it will begin with a number0 because my instructions are numbered from 0 to 49。

And the contract is going to be as follows when the robot carries out a certain instruction at the end of this cycle。

 if you will， the counter increments by one， and then the robot takes a look at the counter and the robot sees that it has to execute instruction number one。

 it executes instruction number one。Counter becomes2， executes instruction number 2， and so on。Now。

 in addition to this basic increment， I also want to be in full control of the situation。

 so I also want to be able to come in and change the counter to a specific number like 17 irrespective of what the counter shows now。

3，4，5， whatever it is， I want to come in and put the number 17 instead and then have the counter continue to count from 17 onward。

Now， this is very important because， you know， suppose that the robot finished baking the brownies。

 and I want to now bake another set of brownies。 Well， in order to do this。

 I can go to the counter and put the number 0 in it。

 And this will cause the robot to start from the beginning。Now。

 another reason why we want to set the counter to some to some other values is because。

 you know when the robot starts to bake the second batch of brownies， the oven is already warm。

 So we have to skip a whole set of instructions that tell the robot how to turn on the oven。

 So the first instruction in the program will probably will probably be something like if the oven is working。

 go to instruction 11 or you know skip all the instructions that that deal with turning on the oven。

That's another reason why， why we want to be able to set the counter to a particular value。

So we see that basically we have to support three generic or primitive operations。

 which are as follows。 fetch the first instruction。 in order to do this。

 we want to set the program counter to0。The other operation。

 which is kind of the default operation is fetch the next instruction。 And in order to do this。

 we have to be able to increment the current state of the counter by one。 And finally。

 we want to be able to go to a particular instruction， fetch and execute it。 And in order to do this。

 we have to be able to set the program counter to to some desired value。So what is a counter。

 a counter is a chip， a hardware device that somehow realizes this obstruction。

 that somehow supports these three primitive operations。

So let's talk about this obstruction in more detail。

And I'm going to use the same chip diagrams that we used earlier in other units in this course。

 So we have a black box description of a program counter。

 we see that we have a 16 bit input coming in。Containing a a certain 16 B value。

 we have a 16 B output going out， and we also have three control bits。

 which are called load ink and reset。 You know， ink stands for increment。Now。

 how does this thing is supposed to work？ Well， here is a more formal description of the desired operation of this 16 B counter。

If the reset bit equals1， if the reset bit is asserted， well， in that case。

 I want the counter to emit 0。 So in the next cycle， the counter will emit the number 0。

If the load bit is asserted， well， in that case， I want to set the counter to a particular value。 So。

 you know， if I want the counter to to go to number 17， well I。Put the number 17 or in binary。

 You know， I， I put a 16 B value that represent 17 in the in input， and I assert the load bit。

 You know， this will bypass the regular increment of。

 of the counter and it will set the counter to the number 17 in the next cycle。And if ink equals one。

 if if the ink bit is asserted， well in that case， the output of the counter will be the current state of the counter plus one。

 This is the default operation of the counter。 And finally。

 if none of these control bits is asserted， the counter does nothing。 It emits its current state。

So this is the desired functionality of the counter。

 and your job is to write the necessary HDL statements that will actually realize this desired functionality。

Now， if you don't see how to do it， don't worry about it because we're going to have a complete unit dedicated to Project 3。

 and in this unit were going to talk about various tips and guidelines on how to build every chip。

 including this counter chip。Now， before we go on to talk about this unit。

 I'd like to give you an example of how the counter chip actually operates using our hardware simulator。

 So this is what we're going to do next。To get started， we load the program counter。Built in chip。

 So we go to the tools folder。And we look for built in chips。And inside the built chip。

 built in chips， we。Search the program counter dot HDL。File， here it is。This is a built in chip。

 and we see that it has a gooey side effect that shows the contents of the program counter。

 which is essentially a register with some control bits。And indeed。

 we see that it has a 16 bit input， a 16 bit output， and three control bits named load。

 ink and reset。So let us load some value into the program counter。So we want to put in the number 23。

We have to run the clock in order to commit this value。But we see that actually， nothing happens。

 We are running the clock。 Nothing seems to happen。

 and nothing seems to happen because we forgot to assert the load bit。 So let us assert。Theload bit。

 and run the clock。And indeed， we see that the program counter now contains 23。

But it doesn't really count anything。 does it， It seems to be fixed on 23。 Well。

 it's fixed because we forgot to assert the ink。Lo bit。 So let us do that。We assert the ink。load bit。

 and。Still， nothing seems to to happen。Well， nothing seems to happen because in every cycle we do two things。

 we tell the register， the program counter to increment， but we also load it with 23 in every cycle。

 so it stays at 23。So if you want the program counter to finally count anything。We have to。

Turn off the load bit。Round the clock。And finally， it looks like we are cooking with gas。

The program counter advances in every cycle by one。

 and this is the classical operation of a program counter。In fact， we can。

We can click the fast forward icon。And this will。Do sort of an infinite loop that runs the clock forward and we see that indeed in every cycle。

 the program counter advances by one。Very nice。 Let's stop the clock。

And let us reset the program counter， so。We set the reset bit to one。

 and we hope that the program counter will turn to 0。

And let's run the clock and indeed we see that in the next cycle， the program cycle。

 the program counter is zero。Well， it doesn't count again， because。Because reset is still one。

 So we have to。Turn off the reset bit and run the clock。 and we see that now， indeed。

 the program counter progresses nicely in every cycle。So this has been a demo of the program counter。

 and let's go back to the lecture。So this is the end of the unit that describes how to build a counter。

 and actually this is the end of the description of all the chips that we are going to build this week。

 and in the next unit we are going to give you all sorts of tips and guidelines on how to build these chips and how to submit Project 3。



![](img/03440b7bfe8f80a2eee6936ab33e2906_2.png)