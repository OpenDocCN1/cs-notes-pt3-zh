# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P49：49_08_09_单元-6-7-视角与展望.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/70e2b8dee7b635af8589454966af284b_0.png)

Welcome to the perspective unit of week6， which is also the last week in the Ntoteris course。

And there are seven questions that come to mind about what we did during this week。

 which was mostly writing in As。And the first question that I'd like to discuss is the following one。

Can you possibly improve the symbolic hack language without changing the binary code or the machine language。

 which is underlying the symbolic level。 So indeed， we have two layers of of expression here。

 We have the symbolic level。 and we have the the binary code that lies below it， if you will。

 and the asmbler bridges this difference。 And indeed we can take this level。

 the symbolic level and make it more user friendly or more programmer friendly and are various ways to do it。

 and in order to explain them， I will go to the board and and show you some examples。

 So how can we make the hack symbolic language more programmer friendly。 Well。

 what we can do is introduce the notions of macroassembbls and macro commands so。

Let me say a few words。About。This added layer。Of obstruction。

Let's take a typical operation like loading the D register with the value of some memory register。

 It is quite natural to think about a command that looks like this。 V equals M， let's say。ハ分。

Which means go to register number 100， take its contents and put it in the D register。

 This will be a natural thing to write， and yet the standard hackck language does not feature such such a command。

So what I can do is I can take a command like this and translate it into two valid commands in the hack language。

 which will be at。10red。And V equals M。 Okay， so this is an example of what is sometimes called a macro command。

 And I can decide that whenever I write this command。

 I actually mean that I want these two commands to get executed。Likewise。

 think about jump instructions。 For example， it will be very natural to say something like jump。

To this particular label。 But once again in the heck language， such an instruction is not permitted。

 So instead I can expect this instruction to be translated into two instructions。

 which would be at loop。And followed by standard jump commands， so these are macro instructions。

 these are actual instructions and in order to close this gap。

 I have to do something to my assembler， I have to extend the assembler and write it in such a way that whenever it encounter a command like this。

 it translates it into two machine language commands rather than a single one。

 which is what we normally did in the standard assembler。

 one question that often comes up when students work on asseemmbblers。

 is that will I ever have to use an assembler outside school。Well， Noram， what do you think？Well。

 the answer is exactly the same answer we gave to the question。

 will we ever need to use machine language that we gave in week for？Very， very rarely。

 Most of the time， people write in high level languages and do not worry about the machine language when they do worry about the machine language。

 Of course， they will do it in assembly language， and thus they will need to use an asmbler。

But this is very rare， only in the special cases where performance is of utmost criticality。

Now in these cases， sometimes they will only want to focus on a very small part of the program and do it in assembly language and do the rest in a highlevel language for example。

 C compilers allow you to do this kind of combination to write most of your program in the C language and in it embed a few commands in assembly so the assemblymbr is sort of part of the C language compiler and allows you to deal with very specific points of the program that you want to extremely optimize and write them in assembly language beyond that you will probably not worry that much or at all about assemblymbrs or assembly language programming Now this course is about building computers and we had the tremendous luxury of using other computers in order to build the hack computer and in particular when we wrote the asmbler we wrote it using a high-level language like Java or Python or whatever language。

hi students have chosen have chosen to to use when they wrote the as。

 Those of you who actually programmed the asler once again used highle language to do it。

 So the question is， historically what happened when the first computers were designed when you didn't have this this tremendous luxury。

 How was the first asmbler actually written。So Noam， do you want to take this question？So this。

 this is a very mind bendending question。 Before I， before I answer it。

 I would like to reemphasize again that conceptually。

 it only holds for the first time you write an assembler。 In reality。

 most of the time there are already computers and usually you use the computers that you already have with the high levelvel language that you already have to write code and assembblrs and basic function and basic functionality for the new computer。

 Now， given that we are still talking about the first computer conceptually in history。

 How is that done。 Well， in this course， you also saw that。

 remember that students that are not programmers in this course。

 simply had to compile something by hand。 they got an assembly language program and needed to to translate it one command at a time into a machine language。

😊，That you can always do。So conceptually， what you can really do is you start。

 you write a high level assembler。 You write an assembler in a high level language and translate it。

By hand， for the first time only into a machine language of your computer。

 once you finish this translation， which is extremely time consuming， extremely annoying to do。

 but only needs to be done once， conceptually。 Then now you already have a machine language that runs your compiler or your asmbler or any high level help that you want。

 And then you can keep on using it for the rest of time。😊，So folks， that's it。

 We had done building the computer， We started with Nand gates six weeks ago。

 and we worked our way through several different types of chips。 we built an ALU， a CPU。

 a memory system， we've put everything together and we got a fully functioning computer。

 we add it to it an assembler so we can actually program this computer in a relatively friendly language and that's it。

 We have a computer that can run any program that comes to your mind including of course Tetriris。

So I'm very happy with this computer。 Noam， are you happy with it Also， Well， Shimon。

 part of the motivation for this course was demystifying computers。

 leaving the student with a clear understanding what goes hand beyond this amazing beast called a computer。

 I think we've only partially done that。 We basically understand。

 I think the students now understand how the hardware works。 What is still quite mystifying， I think。

 to almost anyone that looks at computers is all the different software layers that exists above it。

 When you actually use a computer， you talk with an operating system。

 you write in a high level programming language， It's very far from writing programs in this little assembler that we have already shown。

😊，It would be nice， wouldn't it if we actually had in a second part of the course that actually does talk about all these software layers that are above the hardware。

 the hardware level that explain again in the same manner that we' explained so far how you can actually construct the different software layers。

 the compiler and what is required for it， the operating system and getting to a level where the software hierarchy is demystified like we've demystified the hardware hierarchy so far。

 So thank you， Noam for this criticism and luckily。

 I'm just reminded that we actually solve this problem also because we have a complete second part of this course。

 in which we do precisely what Noam just described。 and so in the second part of the course。

 we start with the hardware that you wrote or developed in this course， and we add。😊。

soffter hierarchy that needs to operate on top of it。

 and then we end up with a language which is very similar to object oriented modern programming languages and then you can really write programs like techs and anything that you want on this computer and see get execute on the hardware that you actually build in the first part of the course。

Now， how should you go about doing this？ Well， there are two ways to do it。 First of all。

 you can get a copy of this book which gives you everything that you need in order to develop the softer hierarchy of the computer just like we did in this course。

 the softer hierarchy will be divided into six or seven different projects that you work on each week of the course。

 So that's one way of doing it， do it yourself。 and the second way of doing it is just waiting until the second part of Nant toteris will be available on Cosera and and then you can just take the course just like you do this one and complete this second piece which is still missing。

 So with this folks the course is practically over。 We hope that you enjoyed the ride。

 we want to thank you for the time and effort that you invested into taking this course and we hope very much to see you。

In the second part of Ntoteris。 So with that。Bye。