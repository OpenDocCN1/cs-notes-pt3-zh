# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P47：47_08_07_单元-6-6-项目6概述（编程选项）.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/eb72431736e0238444de784e5ca78c2d_0.png)

So in this unit， we finally come to a point in which we describe how to develop Project 6。

 which is implementing the assembler。And we wish to remind you that we have two options at this stage。

 if you want。To write a program that actually implements an assembler using a programming language。

 you're welcome to listen carefully to this unit and use the guidelines that we provide to actually develop this program。

 if you don't have a programming background。 then theres another unit that describes an equivalent project that implements an assembler without actually writing code。

 but。I think that every one of you， even if you don't write the assembler using a programming language。

 it may pay off to listen to this unit and see an example of you know how to put together how to carry out a complex software development project。

 So without further ado， we have to develop a heck asmbler and here's the contract。

We decided that we will call our asmbler heck As。 This is an arbitrary decision。And。

 and this program should translate hec assembly programs。

 programs that are written in symbolic he code into executable heCC binary code。

And we assume that the source program is written in。Or supplied in a file， a text file called。

Some name dot A SM。 And given that this is the input that you have to operate on。

 your heCC as program should generate a new file called the same name as the input file dot he。

 So different extension。And， you know， once you create this file。

 we should be able to take this file， put it into the he computer， and actually execute it。

Now we are making a big assumption， which is that the X excess that the supplied input file is error free。

 so we don't have any programming syntax error errors in this file and in the last unit of this week we'll talk about whether or not this assumption makes sense so。

With all that in mind， you have to develop an assembler that follows this contract。

 And just for the sake of the argument， let's assume that you did it in Java。

 although you can do it in any other high level language。

 if you did it in Java and you want to actually use the assembler。

Then we assume that you operate in some shell environment and you type， you know Java。

 the name of the Java virtual machine。You provide the name of your asmbler， heck asmbler。

 and then you give this asmbler， your asmbler， an argument。

 which is the name of the input file that you want to translate and once you provided this command and hit enter your assembler goes to work。

 it translates the supplied file， the Xxx dot ASM and it creates a new hec file that can be actually that that contains the the binary code。

 And if this file already exists， it overrdes it so。This is what you normally do， right。

 you write a program， you assemble it。Translate it。 if you don't like the result， you。

Make some corrections to the source code。 You reassemble it。

 So it makes sense to override the same target file again and again。

 So that's what we have to do in this project。Now， how do we do it。Well， once again。

 you are welcome to write this asmbler in any high level language that you please。And yet。

We recommend that you follow a certain software architecture。

 and we describe this architecture in the previous unit。

 so I don't want to to spend too much time talking about it。

 but I just want to remind you that the architecture that we propose consists of four different software modules。

 Each of these modules should be should be a standalone software module that can also be unit tested in isolation from the other modules。

So we need a parer that unpacks each instruction into its underlying fields。

 We need a module called code that actually translates the symbolic fields， the p mneonics into。

It's a corresponding binary value， and by the way I should say it more precisely。

 it's not that the module translates。 the module has a set of methods that are used to carry out this translation。

 we need a symbol table module that contains a set of methods that manages that manage and create create a manage a symbol table and finally we need a main module which actually drives the show and you know it opens the input file。

 it creates an output file and actually goes through the entire translation process by calling methods from the previously described modules。

This main module will probably be named the heck Asmbler or something like that。

 depending on the language that。That you will end up using。

 So this is the proposed architecture that we recommend that to use in order to develop the asler。

Now， how should you actually go about it， How should you actually do the implementation？Well。

 we recommend that you follow what what is sometimes called a staged development。

 We want you to develop the assembler in stages。 So first of all， as I described in previous units。

 we want you to write a basic assemblymbler that can handle programs or heck assembly programs that contain no symbols once you write this assembler。

 we want you to actually test it in isolation that is test it before you move on and do other things in this project once。

This assembler basic asmbler works through your satisfaction。

 you can go on and develop the symbol table module that can also be tested and you should verify that you can create a symbol table and manage it in isolation from the other pieces of the project。

Finally， once you have these two abilities in place， you can。

Put them together and create an asmb that can actually translate any given assembly program。

 So this is， you know， yet another example of divide and conquercare。 You know。

 you take a complex task。 You split it into more manageable tasks and complete and un test each one of them in isolation。

Now， in order to carry out this unit testing， we provide a set of seven test programs that you are welcome to use in order to make sure that your assembler is actually working。

Now， the first program called Ed dot AM is very simple， and it's provided in one。Flavor only。

Every one of the next three programs is supplied in two different versions with symbols and without symbols。

 So the without symbol version of each program has capital L suffix， which stands for。Less symbols。

 you know， max， less symbols， rectangle， less symbols and so on。 And in the next few slides。

 I'm going to talk about each of these programs in isolation。

And that's exactly what you should also do in your project。 You should test。

You're assembler on each of these programs in different stages of the development。

 And this will help you once again。Manage the process in a， in a good way。 Alright。

 so here's the Ed program。 The Ed program is a very simple hack language。 It contains no symbols。

 It's just a bunch of a few A and C instructions， and it is designed。To verify that your assemble。

 your assseemmber， can handle white space and instructions。 That's it。Now。

 when you look at this program， you probably tell yourself that this is a very limited test， right。

 because well， for one thing， we haven't， we， we， we didn't even test all the possible white space options because we also have in line comments that。

We we don't see in this program and indeed， we don't claim that we provide programs that that amount to an exhaustive testing of your asmbler。

 It's just a very basic test。 and you are welcome and encouraged。

To take this program at ASM and maybe make it more complicated， you know， add more comments。

 add more white space， add more instructions if you want。

 and just make sure that you're asse can handle these kinds of programs。

 simple programs without any problems。 So once again。

 the programs that we provide is just a minimum that that you are welcome to extend with your own testing as well。

Alright， so this is the Ed program。 The next program is called Max。

 and as you can see from the documentation， it is designed to compute the maximum of two values。

 This is really not interesting at all from a translator's perspective。 you know。

 the translator has no idea what the program is trying to do the translator is interested only in the syntax。

 but I'm saying it because， you know I wanted to know what is going on here。

 So this is the max program。 and here is another version of this program without labels。

 So without I'm sorry without symbols。 And so the only difference between these to programs is that the second program in the second program。

 we replaced every symbol with its numeric。MeingAnd once again。Once you write your basic asmbler。

 you should test it on max L， and only later when you add the ability to handle symbols。

 you should test your asmbler on Max ASM。In a very similar fashion we also provide a program called rectangle that draws a rectangle on the screen。

 as we see here in this snapshot from the CPU emulator so here's the code of the rectangle program once again we see that we supply two different versions of the same program on the left hand side you see the full blown version with symbols on the right hand side。

 you see the same program without symbols， we basically replaced every symbol with its numeric meaning and once again。

When you write your basic assembler， you should test it on rectangle L first and only later when you write the full moon asmbler。

 you test it on rectangle。 ASM。The last program that we provide is called Pong and this is quite an elaborate program。

 It's a program that implements a pg game and the simplest way to describe it is to just give you a demo of how it works in the CPU emulator。

 So that's what we'll do next。 Here we are in the CPU emulator。

And we would like to demonstrate running a pun game。In the CPU emulator。

 So we go ahead and load the pong program。So， let us go to。Projects and within projects， we go to。

Project 6。And we see that we have a folder called Pong。Open it。And we see that as usual。

 in this project we have two versions of the same program named pong。asM and ponglessss。

asM Now in the CPU emulator level， it doesn't really matter if you load into it a program with or without symbols because the CPU emulator is going to resolve the symbols into physical addresses on the fly。

In other words， the CPU emulator has built in aseler in it。 and when you load a symbolic program。

Into the roomm， which， by the way， is something that you cannot really do。

 We can do it only because it's an emulator。So once again， it。

 it translates everything into binary code。 And to prove it， let us do that。 Let's， let's， you know。

 let's select this version of the program and。Loaded into the room。 And I see that I get。

A symbolic program， but there are no symbolic labels in it， all the symbolic labels like。

 you know this is probably has been at R0 and it was translated into at three so and once again。

 this is just you know for illustration purposes because in reality the program looks。Excuse me。

 I think I have to do it here。 Yeah， in reality， the program looks like this。 but then obviously。

 it's very difficult to。To follow it。 So in the simulator level， we allow。Looking at the program。

 both symbolically， as well as。Nummerically。Alright。

 so this is a program that implements a simple punk game。 and it's quite a huge program。

 If you scroll， you know， downstream。😊，You will see that this program is lo and behold。

 It is something like， let's see。哦。Something like 27000 lines of code， which is a lot， right。

But it's a little bit deceiving because the program itself， the， the pong logic。

 the logic of the pong game is， is much shorter。It's only， maybe。

 I don't exactly remember something like 200 lines of high level language code。

But by the time you translate this code into。Binary code。 And now I'm talking about the compiler。

 you know， translating from a high level language into assembly。

Then you get you know many more lines of code， but still you don't get so many lines of code。

 the reason we have so much code here is because what you see here is not only an implementation of the pong game。

 but also an implementation of the entire operating system。That enables us to control the screen。

 the keyboard。And mathematics operations and numerous other things that are needed when you implement and run high level language programs。

So once again， just to summarize。It's important to note that the code that we see here was originally written in the Jack highlel language and then it was translated by a jack compiler into eventually into the code that you see here。

 so this code was not written by a human being， it was written by a compiler。And， of course。

 this whole business of writing high level programs。

 writing compilers and operating systems and so on are not covered in Nantotetry Part 1。

 but rather they are covered in Notetry Part 2。 and yet。When you write an assembler。

 all this information is completely irrelevant。 You know what you have is a file that consists of numerous lines of a symbolic code。

 and you simply have to translate it into binary code。Alright， so having said all that。

 let us try to run the program。 So I click the。Fast forward， so to speak。

And there seems to be a lot of action going on， but nothing appears on the screen。 I'm。

 I'm a bit disappointed because I expected to play。A pun game。 And instead， I see。

Something that looks like a program executing。 But once again， nothing is really happening。

And indeed you have to realize that what is happening here is the execution of a lot of setup code。

 the operating system is initializing all sorts of data structures and all sorts of drivers are loaded and so on and so forth。

 and it will take a while before the programmers's code proper will actually start running so if we lose our patients as I'm sure that every one of you has done already。

 we can stop this processing， we can you know rewind everything if we want。

And we can tell the emulator that we don't want to see the program flow。

 and we do it by clicking this control here the no animation。Now。

 what we mean here is no code or execution animation。

 So let's do this and then run the program again。And hopefully， we'll。

 we'll get to see some pong action。Alright。And hallelujah， there's a pong game going on。

 That's quite amazing。 Okay， so I'm playing pong now。 I'm not very good at it。 Oh， dear and。😊。

You know， let me try another game。 Alright， maybe I'll make an improvement now。 Wait， I have to。

 to do this。Okay。Playing pong。 let's see if I'm any better than before。あ。Oh， hallelujah。

 I got a score of 2，3。 That's my world record so far。 and4， very impressive。And game over。

So what you saw here is a pong game in progress。 I'm always excited to see programs like this working on the he computer because。

 you know， this is a program that was written by us in Jack。 It was compiled。😊。

Using a compiler that we wrote and then the executable code。Could run on。

 on a computer that we actually built or a computer that you actually built throughout this course。

 So this is， I think， very， very satisfying。 So this has been。A demo of a pong game。

 you are welcome to play a pong on your own， on your own computer using the CPU emulator。

 which is stored in your Nanttetriris tools folder。And once again。

 I want to emphasize that as far as the asmbler writer is concerned， all this story about pong。

 playing and so on， it's， you know， it's a very nice background story。

 but it has no relevance whatsoever to writing an assembler and asmbler could not care less if it has to translate 12 instructions or 12000 instructions。

 It's a computer program。 it will process， you know whatever file。

 we give it to process and and that's it。So I hope you enjoyed playing pong with our pong game and it's time to know open the black box and look at the Pong code。

 so here's the beginning of the Pong。asM program that we also supply as one of the test programs that you have to that you have to process that your asmbler has to process I'd like to make some observations about this Pongga。

asM program because it's quite different in some respects from the previous programs that we saw in this project。

First of all。The code of Pong was originally written in a language called Jack。

Jack is a Java like simple object based language that we introduced in the second part of this course in Nantoteris part2。

And in Nteris part 2， we introduce this language， and then we write a compiler that translates from this language all the way down to heCC assembly code。

 And， and so what you see here is the result of this translation。So。Writing this compiler。

 And there's also a virtual machine in the middle that I don't have time to to talk about。 You know。

 writing these software layers is quite an elaborate undertaking， but。

We do it in a very similar style to what we did in this course。 We do it one step at a time。

 and this is done in the second part of the course。

 The result of all this translation effort is the ASM program that you see in front of you。

 So the special thing about this program is that it was automatically generated by by the compiler and and by the virtual machine。

 The result in code is about 28000 instructions long。 If you wonder why it's so long。

 it is because it also includes the jack operating system。

 and the operating system is another thing that we develop in the second part of Nanttotetris course。

And。You know， taken together， we have an assembly language program。

 And if you translate it into binary code， then bingo。

 you have something that causes your computer to play pong。

And so we thought that it's important that as part of this project。

 you will also translate a so called industrial strength program， and Pong is one such program。Now。

 when you look at this code。If you explore it， you know。

 and we recommend that you look at it at least briefly。 you know。

 you don't have to understand what's going on here。

 It's very difficult to understand code just from looking at its symbolic， I'm sorry。

 the assembly version of this code。 but you will realize that first of all。

 we don't have any white space。And that is because all the white space was lost in in translation。

And then you will see in this code all sorts of strange things。 For example。

 you see some strange addresses like 2，56。 You know， Where does this。2，56 come from。Well， you know。

 it comes from the way our virtual machine is implemented。 Now you may ask yourself， you know。

 what is the virtual machine， Well， to find out you have to take the second part of the course。

You also see all sorts of strange labels， like， for example。End underlying Ike， you know。

Where did this end I come from？ Well， this was generated by the compiler automatically when it translated the jack code that was written by the programmer。

 And you also see some all sorts of predefined symbols that we haven't seen before like S。 What is S。

 Well， S stands for a stack pointer。 And once again。

 this is something that we discuss in the second part of the course。So when you look at this code。

 you know， it's a little bit like reading genetic code， You know， DNA。

 you have all sorts of strange things that were created by previous generations， so to speak。

 and indeed。The code that you see here was created by several layers of of evolution。

 It's not exactly evolution， but we have a compiler that added some stuff to the code。

 We have virtual machine that addeds some stuff to the code。 And finally， you know。

 you have something which becomes somewhat cryptic。 But you can handle it to your assembler。

 and the assembler will translate it into machine code。 And then finally。

 we'll have something that actually runs on your he computer。 Okay。

 so this is a long explanation of the pong dot AsM program。 As far as your assembler is concerned。

 All this explanation is irrelevant。 You know， it just has to take。

This file and translate it into binary code。So。How should you test， you know。

 the results of your work？ Well， first of all， you have to use your asmbler to generate heCC programs written in binary code。

 and then you should test these programs and make sure that they actually do what they are supposed to do。

So one way to do it is to invoke the supplied hardware simulator。Load into it。

 the built in hack computer chip or or the chip that you wrote doesn't matter。

Although we recommend that you use the built in chip to avoid the errors and then load into this chip。

 the heck code and run it。That's， that's one testing option。Another testing option is to do the same。

 but use the CPU emulator instead of the hardware simulator。

 This will be a more user friendly way to carry out this test。 And finally。

 there is the option of choice what we recommend that you actually do。We provide a working asmbler。

 which is available to you on your personal computer。 If you've downloaded our software suite。

Our asmbler is called asemmbler quite simply， and you can use our assembler to translate any one of the supplied ASM programs。

 and then you can compare the code。That our asmbler generated to the code that your asmbler has generated。

If the two codes are the same， then you know that your assembler is at least as good as ours。

 maybe better。Okay， so we do recommend that you use this third option in order to test your work。

 And here is how you actually do it。What we see here is a snapshot of the asemmbler that we supply in the course website in actually in the N Nant to Tetriris website。

 so。You invoke this program， called theseler。This nice window pops up。

 and then it can load into the assseler， the ASM program， which you see here in the left pane。

Then you click a button and our asmbler which will translate the symbolic code into binary code。

 and you see the resulting binary code in the center pane in this snapshot。

Then you have an option to load into this program what we call a compare file and the compare file is the hec program that was generated by your asler。

 So once you do this。The program will not only load the compare file。

 it will also compare the two files， and then you will get a nice message saying that the comparison was successful or a somewhat nasty message saying that the comparison was not successful。

 which means that your assembler produces code， which is different from the code that our assembler produces。

In which case。Something is probably wrong in your assember。 And you have to test and fix it。 Okay。

 so this is。The recommended way to make sort of the final test that your assembler actually works。

 This is the source file， this is the hec file produced by our assembler。

 and this is the hec file produced by your asmbler。

So this basically sums up what you have to do all the resources that you need are available in the Nanttetriris org website。

 and the website describes the supplied files， there's no need to download anything because if you downloaded the software suite at the beginning of the course then all the files that you need for this project are available on your personal computer in the project s06 directory。

And there's another set of resources that you might find useful like the supplied assembler。

 the supplied CPU emulator， a tutorial， a proposed asmbler API and so on all these things are available in the website and you are welcome to use and consult them so this has been the unit that gave you hopefully all the information that you need in order to build the assembler on your own。

 and the next unit will sum up everything that we did in this week。



![](img/eb72431736e0238444de784e5ca78c2d_2.png)