# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P24：24_05_06_单元-3-5-项目3概述.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/d59ecbbcb6076a740e996481ccb300ca_0.png)

We are now in a position to take everything that we learned about the theory and practice of memory devices and actually set out to build chips that implement all this functionality。

So project3 begins with all the chips that you designed in projects1 and2。

 as well as a primitive data flipflop that you can use as you say fit and based on these building blocks we have to build the following chips we've seen all these chips in one way or another in the previous units and now we actually implement them Now most of these chips all of them except for the program counter constitute a family of increasingly complicated sequential chips beginning from one bit register all the way to a random device that contains more or less 16。

000 register， 16k registers。So let us begin with a one bit register whose diagram and documentation is repeated here。

 We've discussed it before。 Here is the stub file。 there's nothing special about it。

 and the implementation is something that Nom described in previous units so you can just follow up what is written here and build this chip in HDL  moving along we can take a set of such single bit registers and build from it 16 bit register the HDL is shown here and all you have to do is create the right wiring and what you have is a 16 bit register。

 So now we are ready to move on and build our first RA device consisting of8 registers Here is the API of this chip Here is the stub file that describes its input and output pins。

So now that we have all this information let's figure out how we can actually build such a RA device so I can give you two very important tips。

 The first one is that you have to take the invalue and fitted simultaneously to all eight registers so-called at the same time so you use HDL statements to fend out this incoming value and send it to all the registers in the RAM device and then you use some MOOCs and DOOCs logic in order to select the exact register that you want to be affected by the respective read or write operation so once again you send information to all the registers but only one of them is going to be selected using this MOC and DOOCs functionality now I want to leave you the details because。

Otherwise， you won't be sufficiently challenged， I think， and with these details。

 you have everything that you need in order to build this RA device。

Moving along we have implemented the first three chips and we are ready to construct the more elaborate RamM 64。

512 and so on chips in the hierarchy so this is our next task and here is how we do it we start with the RA chip that we just discussed and we stack together eight such RamM chips and what comes out is or what results is what we call a RamM 64 we can take eight such RamM 64s put them together to yield the next chip in our hierarchy which is RAM 512 and we can do two more steps of a very similar nature and end up with the most elaborate RamM chip the one that we have called RamM 16 k so we basically repeat the same。

It recursive ascent， if you will， and by using this strategy。

 we can build more and more elaborate RA chips。 Now， how do we do it？Well， first of all。

 we note that a Ram device can be built by grouping together smaller rampar， which is。

 you know an HDL description of what I did before in this diagram and we can think about the address input which is not shown here。

 but you know it's in the background we can think about the address input of every one of these chips as a binary value that consists of two logical fields。

 one field can be used to select the exact ramp part on which you want to operate and the second field can select the very register within this rampar that you want to effect by either reading or writing something into this register So taken together this these two tricks can enable you to build Ram devices of arbitrary。

Length and you useOOCs and DOCs gates in order to affect this hierarchical addressing scheme that I just described。

 So once again， you have here enough tips to to enable you to complete the implementation on your own using HDL。

So this basically completes the construction of the RA devices and we move on to construct the last chip in this project which is something completely different。

 it's a program counter which is just a fancy name for a counter。

 in fact it's not a fancy name it's called program counter because later on in the overall construction of our computer。

 it will serve as a program counter， but effectively it's just a counter。

 has an input value it has an output value and three control bits。

 Now the overall behavior of this counter is somewhat elaborate。

 we discussed it when we talked about counters before。

 I want just to emphasize the four most important things about it， this being a counter。

 we want to be able to set it to zero， we want to be able to set it to some other value。

like 17 or 19 or whatever we want to be able to tell the chip to start counting。

 to change in every cycle into whatever it was before plus one and in some cases we want to tell it perhaps to stop counting and freeze so to speak so what you have to do is to come up with the right functionality。

 the gate logic that affects every one of these four operations it turns out that you can do it using a registered chip。

 an incrementer chip and a bunch of other logic gates that were previously described。

So taken together， this is what you have to do in Project 3， as usual。

 you go to the Nan to Tetri's website and you will find the project webpage with lots of additional operational details。

Once again， I want to emphasize for the third time in this course that if you have downloaded the course soft or suiteite。

 there's no need to download anything in addition， this is just for documentation purposes and you already have all the necessary files on your computer in the directory project slash 03 and you have your hardware simulator and you're set to go and build all these chips on your own。

As usual， it makes sense to consult these resources when necessary and finally。

 all the best practice advice that was given in previous projects is relevant here as well so you might as well read it before you set out to build a project and in addition。

 as usual you will have to use chips that you implemented in previous projects and as I explained before the best practices to ignore your HD implementations and use the built and implementations instead。

 Finally there's one more point that I'd like to emphasize on this project and that is that the HDL files of this project are stored in two separate directories called A and B。

And this structure should remain as is now why do we do it Well。

 if you recall our RA devices are built from smaller Ram parts and the smaller RA parts are built from even smaller RA parts and it goes on and on。

 it's like a Russian dollar system and if you take one of these huge Ram chips。

 let's say a Ram 16k and put it into the hardware simulator。

 the simulator begins to evaluate all the chip parts and it does it in some sort of a recursive drilling downward all the way down to single bit registers and it turns out that this can be too much too much memory or too many objects to handle for the hardware simulator。

 which is just a humble computer program and therefore by putting the registers I'm sorry by putting these Ram chips in two separate direct。

We force the simulator to at some point stop using the HDL files and use and start using the Java implementation of these built and chips。

 and this will make the implementation。 or I'm sorry。

 this will make the simulation much faster and smoother。

 So please just leave the directory structure as is and you are set to go。

So this has been a description of what you have to do in Project 3， and as usual。

 we will now turn to the next unit in which we give you some broader perspective of the notion of memory devices。



![](img/d59ecbbcb6076a740e996481ccb300ca_2.png)