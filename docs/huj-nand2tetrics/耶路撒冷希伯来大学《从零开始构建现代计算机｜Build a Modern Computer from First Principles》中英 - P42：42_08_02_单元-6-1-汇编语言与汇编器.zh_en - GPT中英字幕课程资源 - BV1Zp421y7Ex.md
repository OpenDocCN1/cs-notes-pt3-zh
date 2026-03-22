# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P42：42_08_02_单元-6-1-汇编语言与汇编器.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/8aba3528b36e0a26d612b05364f73e4d_0.png)

Last week we've built a computer that can run a code， machine language code。Two weeks ago。

 we've actually programmed in machine language， but we didn't really program in binary code。

 but rather in assembly language and some kind of nice syntax。 So there is a gap in the middle。

 and the gap is supposed to be a simple software program called an asmbler。So specifically。

 you've seen this slide already twice。Two weeks ago。

 you've seen this slide to focus on the left hand side and the actual assembly language format in which you were supposed to program。

 That was your perspective， two weeks ago。Your perspective last week was what happens on the right hand side。

 the machine language， since you had to actually construct a computer that can actually execute the ones in zero that you see on the right。

Our focus， our perspective this week is going to be in the middle。 How do you go from left to route。

 How do you do from left to right， How do you do the operation the assembly operation， I。e。

 how do what is the assemblyler， which is the program that translates what you have on the left。

 the assembly language code to what you have on the right， the machine language code。Now。

 notice that for the first time in this course， this is software。

 this is going to be a program that takes as input file written in the left hand side format， i。

e and assembly language and produces another file that's written in the right-hand side format， i。e。

 zeros in ones which directly can be executed in a computer。 So this is a software。

 the first time that you do software in this course until now it was always hardware。

 and it's really the first software layer every in every the first software layer is that basically we have in every computer。

 there are much more there is much more software above it。

 but this is the first level and we're doing it together with the hardware to give us a complete picture。

 So we can have a computer that we can understand how you program it and understanding how you program it does not mean programming it in zero in ones。

 but rather in assembly language， which is still a very， very low format。

 essentially equivalent to machine language， but still。😊，Something that humans can relate to。

 So let's see what kind of software is this going to be this asemler。In principle。

 youve only we've only created a computer that can run machine language code。 So in principle。

 we should write our program in the only language that can be directly executed。 I。e。

 in machine language code in zeros and ones， which is going to be pretty annoying。

But the best way to think about it is that we're not writing the first。

 We're not constructing the first computer in the world， but rather the second one。

 So let us assume we already have a computer that can run some high level language。 In particular。

 I'm talking about your computer and the high level language that you already know。

So we're going to write the assembler in that language and it will be a software program that runs and your computer。

 What it's going to produce the machine language it is going to produce is machine language for the hack computer。

 for a different computer， the computer in which you will actually run the produced program。

So we're thinking about a cross compiler。 sometimes it's called it's running on one computer and producing code intended for another computer。

 This way， we don't has this loop。 We don't have this bootstrap problem of having to write our asmbler in machine code。

 but whether we can write it already in the highlevel language that we've already implemented on another computer。

 So the asmbler program is really a very simple program。

 It does the following basic loop and repeat it again and again。

 It reads one assembly language command from the input。It basically breaks it into its parts。

 and each of one of its parts can be translated to binary in a unique way that's specified by our language。

 And then we take the binary code of the different parts， puts them together。

 And we get the machine code that directly is equivalent to the assembly language command that we've just read。

We output that and we move on to the next assembly language command。

 We keep on doing that and translate one command after another without having to remember anything that happened in the history。

 Very simple。 So let's look at the different stages。 each one of these different stages。

 slightly more carefully。So how do we read the next assembly language command？ Well。

 it seems that we just read the next line from the input。 This is almost exactly what we do。

 the only other difficulty is that we may need to to skip what's called white space， for example。

 comments， we need to make sure that to read what is really the next command and not any kind of comments or any type of spaces or blank lines that are read there。

 So when we read it from the file。 we have a file that let's say has a command load R 118。

 And this is just a fictional language， assembly language。😊，Later in the next unit。

 we'll start actually talking about the hackle language specifically， but in this unit。

 I'm still focusing on a generic assembly assembly program。

 So let's assume that our hypothetical assembly language has this type of command， load R118。

 which we expect is would probably mean taking the value 18 and putting it into the first register。

 but this is not something that we need to go to know when we're actually doing this translation。

 We actually want to read that command and put it into some kind of string variable into some kind of array of characters that we can later work on。

 And that is basically what's involved in reading a line by line from the input。

 So the next step is taking this string of characters and breaking it into its different parts。

 So when we look at it， we see that the different parts of this command are load first part。

 R one should be the second part。18 should be the third part。

 Each one of them has meaning and there is。So a space in a comma。

 But these are not really the interesting parts of the command， but rather just some syntax。

 which helps us break and understand what's written the important parts in the command。

 So the next thing we have to do is basically understand the syntax and break the original string into these three different。

 if you wish substrs， the three different interesting parts that are involved in this command。

 So that involves basically some kind of simple string manipulation until we get the different parts。

Once we have these different parts， then we need to translate each one of them to machine language to actually its binary part。

 its binary counterpart。 Now， how do we do that。 Z has to be part of the specification of the machine language and assembly language。

 Basically tells us what is the code for each one of these commands， for example。 So it would so。

 for example， the load command。 we would probably have some kind of table。

 which tells us what is the machine language code for each command， in particular。

 we can look up in that table and see what is the machine language code for the load command。

 Other parts of the input maybe for example， numbers or maybe other things that we can directly translate into machine language。

 just because they are number， for example， the number 18 may be translated into just into the binary representation of the number 18。

 Again， this is part of the language specification。 This is the basic part。

 This is a part where we need to understand exactly the mapping between assembly language。😊。

Machine language， which is usually usually very simple and specified completely by a bunch of tables and a bunch of rules of word you put intoger numbers in the binaryary form。

 and that's about it。The third part is now we have basically that translation of each part of the input and we need to put them together。

 usually just some kind of concatenation。 maybe we will need to put also some kind of other bits that are defined in the specification to actually pad them and complete the language because sometimes the translation of of a command does not fill all the available bits that are available in the machine and the other bits are specified to be some。

 let's say， a constant01。 So now we have basically the number the binary number that we need to output。

 and we just need to print out into the some kind of file。

 How exactly we print it out is according to there's going to be some kind of specification of the file format of machine language which may binary format。

 which may just in character 0 and one that will be not something that you would usually have and so on。

 but then you just need to basically translate the numbers you have in your memory。

 the ones and zeros you have in your。😊，In your memory。

 you have to translate that into a format that the machine language can actually that the computer can actually execute。

So far， we've described the basic operation of the asmbler。

 and now there' is one extra complication that we need to worry about。 and that is symbols。

 handling symbols。 As you may recall， one of the major services that an assembly language forgive the programmer is the ability to use symbols rather than direct numbers。

 And we usually use them for two different types of things。

 One of them is for labels in the program to jump into a certain part of the program。

 you give it a name rather than really hardcode the address。

 And the other is you want to give a variable name。

 rather than always refer to some to its exact address and memory。 So， for example。

 we can write and you most assembly languages jump loop and loop is some kind is going to be translated automatically into some kind of address。

 Similarlyly， we can load into a register variable weight。 And again。

 weight is going to be some location in memory， which is the assemblymbr needs to figure out which location and will basically translate this access direct。

😊，To accessing that location in memory。 So basically。

 what our asmbler will have to do is replace each one of these symbols。 For example。

 the weight in in the previous in the previous command into its equivalent address。

 And it will have to remember where exactly is that address in the memory。 Similarlyly。

 it will replace the the the label of a loop of a jump with the exact address inside the program。

 And again， remember where that is。😊，How does that happen， How will that be done， Well。

 it will need to maintain some kind of of a table that basically has the information about the translation between symbols and actual addresses。

 And whenever it needs to do this translation， it will have to actually look up in the table。

 It sees weight in the assembly language program， it will have to look up in the table and see what is the correct address to put instead of it。

 once its replaced the symbol with address， then it can continue as we previously described。

So let us see now， how do we maintain such a table， How do we enter information into it。

 and how do we look up information from it。So， for example。

 let's see we now our asmbler is reading command by command。

 and it encountered this command with a variable weight in it。

So maybe it' the variables already in the table。 We need to look it up in the table。

 If it's already in the table， then we know exactly how to translate it。 This is the easy part。

But what happens the first time we see this variable weight。 Well， we look at it。

 we look in the table and we see that it's not there。

 So we know that we need to allocate a new memory location to hold this variable。

 And this is one of the things that our assemblymbler will have to do。

 So it will actually find the next memory location that's available。

 and the exact definition of where does it allocate memory addresses should be part of the assembly assembly language specificification。

 and it will basically allocate this new memory to this symbol。

 And now it has this pair of symbol memory address that it can put into the table and use from now on。

 including for now。😊，And this is how basically we put variable locations into the table and how we use them。

The other kind of， the other kind of symbols that we have are labels。 So let's see we have。 Well。

 let's see， for example， we have a piece of code that has inside the that has in it， a label loop。

What does this mean when our asmbler actually looks and reads this line label， it knows， well。

 this is just a label。 It's not a real command to execute。

 but I have to remember that the next time somebody wants to jump to this symbol loop。

 I have to remember where exactly it is。Where is it， Well， I have to remember， where。

 what address is the current command going to be put into the the into the memory。

And that is going to be the address that's referred to by loop。 So， for example。

 if our program if our current， if this current piece of program is being allocated into being put being being written into memory location 671。

672，673 and so on after the program memory。 when we see this label。

 our assemb will have to remember the next program is program 673。

 So I need to remember that loop from now on always refers to location 673。😊。

And this is basically the kind of thing that it needs to do。

And then when we actually get to a place that uses this label， uses this symbol。

 then we already know we already have in our table。 what exactly is the correct address。😊。

So that's basically how information is about labels is put into the table and read from it when needed。

Now， there is one extra complication that we didn't talk about that sometimes we can use。

 we can jump into a label before the label was actually defined。 This is called a forward reference。

 So， for example， it's a very common in programs that I will need to jump。

 let's say into a label called continuing con before the label actually record in the program。

 If that is the case， when I reach the first jump when I first the jump instructions。

 that uses a label。 that happens before I've already seen the place that defines the label in the label command。

 And how can I handle that because it's not in the table yet。Well， there are two ways to handle it。

One way， which is usually a little bit more complicated。

 is to basically remember that I've seen the label that I don't know where it is yet。

 Keep it in a side table。 And when I actually get into the definition of the correct address。

 fix it back。another option， which turns out to be sometimes easier。

Is that I actually do everything in two passes。 In the first path， I read everything。

 only paying attention to the labels and remembering where each label refers to。

That that's when I actually build the table for the labels。

And only in the second pass do I actually go and put and convert each and every label into its correct code。

 into its correct address that now is already in the table because I've put it there in the first pass。

 and that's a usually slightly easier to do， but you may use each one of these two possibilities。

So now we finish talking about the general process of creating an assember。

 the general thing that an assembler must do。 And what we're going to do in the next few units is start talking specifically about the hack machine assember and talk about the different parts of how you actually constructed it。



![](img/8aba3528b36e0a26d612b05364f73e4d_2.png)