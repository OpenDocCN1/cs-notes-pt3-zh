# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P35：35_06_11_单元-4-10-视角与展望.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/7033610f9b1d08e9401d2209fc1bfb7a_0.png)

Welcome to the perspective unit of week four in which we introduced machine language and wrote some low level programs in the HeECka assembly language。

So one question that normally comes up is， how does the heck machine language differ from the machine languages of typical computers like personal computers？

Well， the heCC machine language is very simple because it is designed to operate on top of a very simple hardware platform and we built this computer in purpose as a very simple architecture because we wanted to be able to actually build it in the space of six weeks course and therefore the computer is very simple but it's sufficiently powerful to offer almost everything that you need for reasons that I will explain in just a minute。

 so typical machine languages are much more rich than the heCC instruction set。

 they offer more commands more instruction types more data types like floating point and more operations like for example。

 multiplication and division and yet，As I said before。

 there's no need to worry because all these fancy things that other languages offer can be delivered at the softwareer level。

 at the higher level of abstractstruction， and that's exactly what we do in the second part of this course in NterisPA2。

 we build an operating system and we introduce all sorts of operations that are currently not supported by the machine language。

So here's the next question。 It looks like in the heck language。

 whenever you want to do something meaningful， you need two machine language instructions。

 one to address the memory and one to operate on the selected memory register。

 Is this the standard way to do things。 No Well， most machine languages are more sophisticated more powerful than ours and usually do allow you to specify both operator and opera in a single machine language command。

 For example， you can say， I want to add， and I want to use this memory location and put it all in a single machine language instruction。

Now， in our computer in the Ha computer， we only have 16 bit instructions， and in 16 B。

 it's very difficult to put both a lot of information about the operation and a lot of information about the operaand。

 in particular， you can't put a whole memory address。

 as well as more information about what kind of operation you want to do。 So in our in our case。

 you have to split the point where you specify the address。

 which requires 15 Bs of its own and the place where you actually specify the operation。

 which requires a few more bits。😊，In other machine languages。

 some usually they have wider machine instructions or sometimes even variable widths machine instruction。

 and then they could fit more information into a single machine instruction。That said。

 the basic idea of taking part of the address on which the machine operation is supposed to work on taking part of that address from a previous command is not an unusual kind of thing and many machine languages do have that。

 So a related question that we often get is that the hec machine language indeed has some strange or peculiar syntax rules。

 can you say a few words about the choice of the syntax and how it differs from the syntax of regular machine languages。

 Well， unlike high levelvel languages like Java machine languages are not designed to make people happy。

 they are designed to operate on hardware platforms。

 So the commands of machine language must deal directly with the AU with the memory and the registers and they must be extremely efficient and that's one reason why machine languages are so simple。

As we discussed before， so as we said before， the heCC machine language is very simple and therefore we also decided to make the syntax somewhat simpler than what you normally find in machine languages for example。

 if you want to compute addition and store the result in some register in the hec language you say something like D equals D plus n。

Whereas in a normal machine language， typically commands like this start with the specification of the operator。

 So normally well have something like add。The along with some address and you can specify both the address and the register of the destination and the the the operator in one instruction because normally in machine languages。

 you have 332 bits or 64 bits。 So there's enough space to pack all this information into a single command。

 whereas in he， we do only this。 Likewise， if you want to put the contents of one register in another register in hack。

 you say something like D equals M， for example， whereas in a normal machine language typically will say something like load。

M or something like this。 And once again， instead of M， you can write。

An address and pack all this information into a single instruction。

So the last question in this perspective unit is， do people actually have to go through the trouble of writing programs in machine language？

Well， the answer is that people don't really write programs in machine language Instead some developers sometimes write programs that generate machine code and these programs are called compilers and a compiler is a program that takes another program written in some high-level language like Java and translates this program into binary code。

 so in order to write a compiler， obviously you have to understand the machine language that the compiler has to generate and that's exactly what we are going to do in the second part of the Nan tote scores where we actually write a compiler for a high-level language and this compiler will generate heCC code that runs on the machine that we build in this course。

Now there's one exception to what I said before， and that is that in some applications in particular in real time systems or in applications where performance is incredibly important。

 programmers sometimes have to look at the gory details of the machine language code。

 if they want to optimize their programs， so they don't write the programs in machine language。

 they write them normally in in in a language like the C programming language， but。

Once they translate the program into machine language。

 they look at the code and if the code looks terribly tangled or unnecessarily long。

 they can go back and rewrite their high level code， but in the most part。

 most programmers write in high levelve language and that's it。

