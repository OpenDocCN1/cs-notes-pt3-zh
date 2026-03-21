# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P32：32_06_08_单元-4-7-Hack编程第二部分.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/5eb0d9cedbe21bad5ac5d7b63b9ee9f3_0.png)

In the previous unit， we talked about working with registers in memory。

 which is the basis for doing everything in lowle machine language and in this unit we'll see things which are more familiar to high level programmers like branching variables and iteration。

So let us begin with branching branching is this fundamental ability to tell the computer to evaluate a certain Boolean condition or Boolean expression and based on this value to decide whether or not we want jump and execute some other section in our program or simply move on and execute the next instruction in the program。

Any programming language has various branching mechanisms， for example。

 if you write programs in Java or in Python， you have things like if else， while， repeat。

 switch and so on。In machine language， we typically have only one branching apparatus and this thing is called Goto。

 and here is how we use this Goto in a particular example。In this program。

We want to look at a certain data value and decide or determine whether or not this value is positive or not。

 so we decide as a matter of convention that the value will reside in Ram 0。

 so you know the user of this program has a responsibility of putting a value in Ram0 and then when the user press execute。

 the program spins its wheels and at the end of the execution， the program will put in R1 in Ram1。

 either the value1， if Ram0 is positive or the value0 elsewhere。So this is the typical if else。

 and unfortunately we don't have a way to express this thing directly in lowlel programming。

 lowlevel programming is much more Spartan and minimal and therefore we have to work hard to make this happen in particular。

 here is some code that I have written to accomplish this this operation。

 it's probably not the only way to do it， but it works。

And I've used red ink to highlight the areas of the code that actually refer to this computation of if R0 is greater than0 set R1 to1 let us ignore the rest of the program for now so in the two instructions 8 and9 I'm taking care of setting R1 to1 and in instructions2 and3 I check the value of the data input which is now residing in D and based on this value I decide whether or not I want to jump to instruction number8 in which I will actually set R1 to1。

Now。If you're not sure exactly how this thing works。

 I recommend that you stop the video and simply run this thing in your head or with a piece of paper and convince yourself that you understand how the branching is actually working here。

Now， as a matter of experiment， let me remove the line numbers and also remove the documentation and just stare this piece of code。

 and if I will also remove the preamble documentation。

 I would argue that what will remain is quite unreadable， you know。

 this is an example of cryptic code， very difficult to understand what this code is trying to do。

And and yet the code will work perfectly。 You know， this is a flawless program。

 If you will load it into the computer after you translate it into binary code。

 it will work perfectly。 It will deliver the signal obstruction。 The user will be very happily。

 and yet the program is not readable。😊，Now， this is the perfect point to invoke a quote by Donald Kuth who said that instead of imagining that our main task as programmers is to instruct a computer what to do。

 let us concentrate rather on explaining to human beings。Fellow programmers。

 what we intend the computer to do。 This is super important because if we don't have this capability。

 if our programs will not be self documenting， we won't be able to fix and extend them。Al right。

 so what can we do to make this program more readable Well， fortunately。

 we have a very nice feature in assembly languages， which is called symbolic references。😊。

So let's take a look at what I did here， I have introduced a label that I made up and I decided to call it positive because it's a sensible choice of a label because it describes roughly what I'm trying to do and this positive label appears twice in the code in the first place that I want you to look at I declare this label。

And basically， what I'm saying here is here is a piece of code。

That I want to jump to from some other place in the program。

 And I'm going to call this location in the code positive。

And when we designed the heCC assembly language， we decided that label declarations will be made by just writing the label and enclosing it into round parentheses。

 So this is how we declare a label in the hackCC assembly language。 and this is how we use the label。

So instead of saying at8， we now say at positive and it is the job of the asmbler and the translator to translate these labels into concrete numbers and let us observe how this actually takes place so once again the general rule is that at label will translate into at n where is the instruction number following the label declaration。

Let us remember that instructions have implicit numbers and here they are。

 So when I take this piece of code and I load it into the instruction memory， here is what happens。

 first of all。😊，Whoever makes the translation has to operate according to a certain contract。

 you know， if you write the asmbler， for example， something things we're do in week six。

 we will tell you that the language makes some assumptions and some conventions and you have to write your asmbler or to carry out the translation according to these to this contract。

 So first of all， notice that label declarations are not translated。

Now we have two label declarations here， positive and end。

 one is just before line 8 and the other one is before line 10， they are not translated。

 they are ignored and they generate no code， surprisingly enough。Okay。

 what about the references to the labels Well the references to the labels definitely get translated and what used to be at positive becomes at8 because8 is the instruction just after positive and what used to be at end becomes at 10 for the same reason。

So the second part of our contract is that each reference to a label is replaced with a reference to the instruction number following that labels declaration。

So once we keep this thing in mind， we can happily use。

 invent and use as many labels as we want in our program。

 and then we can use these labels to affect the notion of branching。😊，Okay。

 so having dealt with branching and obviously it's something that willll return to because you cannot write any nontrivial program without branching。

 let's move on and talk about another obstruction called variables。Alright， so what is the variable。

A variable is an obstruction of a container that has a name and a value。And in high level languages。

 we have different types of data， different types of variables。

 and yet in the low level of machine language or at least in the low level of the hec machine language we have only one variable type。

 we have only 16 B values to worry about and this obstruction can be delivered or can be implemented by using a single register in our data memory。

 so we use a single registers to represent every one of our variables if we want to create variables in our in our program。

 So here's an example in which variables come into play。

 and in this program I want to flip the values of Ram0 and Ram1。

And I do it using a classical programming idiom that appears in practically every basic programming course。

 I create a variable， typically we call it something like temp to denote the fact that it's a temporary variable。

 and I need it only for this purpose， and I do some manipulations that end up delivering the necessary flip operation。

So the question is how do you do it in machine language where so far we didn't have the notion of variables so this is a good opportunity to introduce them well here's how I decided to do it and let us focus only on the red instructions in this program and in particular in the first red instruction I declare a variable called temp and then I immediately go on to use it。

Now， what is the meaning of this cryptic command at temp and notice that unlike labels and references。

 we don't have a corresponding label called T。 So what do we mean when we say at temp like this。

 Well， here's what we mean Basically we we present the following pledge to the computer。 please。

Go to the memory unit。Find some available memory register。

 Let us assume that it's register number N and use it from now on to represent what I prefer to call the variable temp。

So from now on， whenever you see a symbolic instruction at temp。

 I request that you treat it as if it were an at N instruction that we already know how to handle。

Okay， so this is the meaning or that's how I realize this variable obstruction。

So let us observe what happens when you translate this program and load it into instruction memory。

Well， the first observation is that when you look at the code。

 you see that what used to be at T became at 16 and because at T appears twice in the program。

 we have two occurrences of the at 16 instruction。So how does this happen？Well。

 whoever wrote the asmbler or implemented this translator worked according to a contract that we as the language designers have put together。

 So the contractor has two rules as follows， first of all。

A reference to a symbol that has no corresponding label declaration is treated as a reference to a variable。

 We assume that the programmer wanted to create a variable。

 And the second rule is that variables are allocated to the Ramm from address 16 onward。

In this particular example we have only one variable so it ends up being allocated to RAM 16 if well have more variables in the program。

 we'll use RAM locations 17， 18 and so on and so forth and practically you can use as many variables as you want and I can say safely because typically programme are used only you know half a dozen or a dozen variables or something like this and in the heck language you can actually use thousands of variables but no one actually comes up to this to so many variables。

So in closing of this little section about variable， if you look at this piece of code。

 you will realize that this program is relatively easy to read and debug。

 you know we have a symbolic label and we have a symbolic variable T and it's much easier to understand what is going on here compared to the program that we wrote before when we used actual numbers to represent addresses。

This program has another very nice virtue， which is more subtle。

 and this is the fact that this program is what is known as relocatable code。

I can take this program and load it into memory not necessarily to address zero。

 I can put it anywhere I want in memory as long as I remember what is the base address that I use for this program This is extremely important because as you know when you work with your personal computer you typically have several programs executing at the same time so you can imply from this that several programs are loaded into your main memory and once we write these program carefully using symbolic references we don't have to worry about where they will be located in memory。

 we can write something called loader that takes care of of this technical detail。

So symbolic programs are good。The next programming idiom that I would like to discuss is iteration。

So for example， suppose we want to compute the sum of the series1 plus2 plus3 all the way up to n where n is some given input how do we do it Well normally use some accumulator variable to accumulate the running total of the series so you set this variable to0 and then you do0 plus1 gives you one one plus2 gives you three。

 3 plus three gives you6 and so on and so forth until you reach n。

Now if you have to write this program in lowlel language it always pays off to begin with some lowlevel oriented soda code and this is what I did here。

 So once you convince yourself that this soda code actually delivers the required functionality we can move on and translate this soda code on paper into symbolic machine language so let us begin with the first part of this of this program in which we declare and initialize the three variables N and sum so first of all notice that there's a one to one mapping between the names of the variables that are use in myseda code to the names of variables in the symbolic language which is kind of nice So we have these three variables and let us assume that。

translatelate only this part of the program and load it into the instruction memory here is what I'm going to get at N would be translated into at 16 at I into at 17 and at sum into at 18 this should not be surprising because it follows the contract that we discussed earlier。

Variables are allocated to consecutive ReM addresses from 16 onward。Alright。

 so let's keep this in mind and complete the translation of the episodesoda code into machine language。

 the details of this program are not terribly important。

 well they are if you actually have to write this program。

 but they're not important to the things that I want to emphasize in this unit。

 but I do expect you to once again stop the video now and convince yourself that you understand what this code is doing。

And by the way， when you write such a program， if I told you if I gave you this program as an assignment。

I highly recommend that you first write it in soda code。😊。

And then I recommend that you debug yoursda code and convince yourself that thesda code actually works。

 and once you convince yourself that it works。You can reduce the task of of writing the machine code to that of simply translating from Paseda code to machine language。

 And you see， this is much easier to do。 You know， you look at thepsido command like n equals R0 and you write a set of instructions in machine language that do the same or take a look at the instruction that follows the loop directive in thepssoda code。

 you know， it says if I is greater than N， go to stop。

 So it's much easier to simply focus on this instruction only and translate it into machine language。

 So this is one way to write a lowlel code and convince yourself that it works。

And the second way to verify that the code works， which is no less important is once your program is written。

 you have to simulate it， or we recommend that you simulate it on paper using some sort of what is known as a trace table Now a trace table is a piece of paper on which you write down the names of all the main players in your program or the main variables of interest in your program and then you record in the table the values of these programs throughout the program's execution。

 So these are the values of these variables of interest in iteration zero and then you go through the loop and you figure out what happens after the first iteration after the second iteration the third iteration and so on and so forths so you do this for three or four iterations and you try to convince yourself that the program is actually working。

So in closing here is our best practice advice for writing hec machine language programs。

 first of all， you have to design the program using some sort ofseda code and you can follow theseda code example that we used in the previous slide。

Second， you have to take your Ob the code and reexpress it using the heCC assembly language and finally we recommend that you test this the resulting program on paper using some sort of a trace table and notice that I did all these things without touching the computer。

 everything was done on paper， but actually I probably wrote the program using some text editor but once again a text editor for me like is like using a piece of paper and it's very important that you convince yourself the program is working before you actually you know unleash it on the actual computer。

All right， so this has been the unit in which we talked about branching variables and iteration。

 and in the next unit we are going to talk about pointers and input output and this will be the end of our coverage of lowle heCC programming。



![](img/5eb0d9cedbe21bad5ac5d7b63b9ee9f3_2.png)