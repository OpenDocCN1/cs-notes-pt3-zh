# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P46：46_08_06_单元-6-5-开发Hack汇编器.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/dfb694934ac8bdc4b512c265ce28c23e_0.png)

In this unit， we're going to describe our a proposed architecture for an asmbler。

 You've already seen the basic algorithms， the basic logic of what an as needs to do。

 But now we need to translate that into a real program and think about its architecture。Now。

 the truth is an assembler is a pretty simple program。

 and those of you who have already had significant programming experience can probably ignore this unit very safely and just go ahead and write the asmbler。

For those of you that has slightly less experience programming。

 you may want to look and remember our suggestions for reasonable architecture。

 reasonable components of an asmbler。 Again， this is only a recommendation。

 You may want to look at our recommendation and then do whatever you feel most comfortable with。

So let us see。 what are the types of modules that probably will be useful when we write an asemmbler is a type of operations that need certainly need to be done。

 Well， three of them can be very easily identified。 So let's talk about them。

 One of them is basically the parser， something that is able to read a file and gets a different commands in it and breaks them into parts。

That's the first part reading in parsing command。 You will need to do that。 That's one thing。

Another part of the code probably will have to actually understand how you convert。

A pneumonic an assembly language command or part of an assembly language command into actual code。

So that will have to understand the mapping。 And that's a different。

 Another part that will need to be done somewhere probably in you an asmbler。

And of course there is another part that will need to be able to handle symbols。

 the symbol table itself， so let's talk a bit about these three different components and once we talk about them you'll see that the rest of the program using these different components which we think about as classes and writing the complete program。

 there is not much left to be done。So let's start with the first part reading and parting command。

The most important thing that we have to think about what we don't need to worry in this part。

 So the whole point of the parser of the components it reads in parse command it only needs to be able to read the input and break it into its parts。

 It doesn't need to understand anything。 It doesn't need to understand what the commands mean。

 It doesn't need to understand how they are translated to machine language。

 it doesn't need to understand the symbols or their addresses。

 the only thing it needs to understand is the format of the input language and how it breaks into a different components。

 So let us now see what are the different things， what are the different actions that it does need to worry about。

 So let us see what are the things it does need to do。

Well first of all it needs to be able to read a file with a given name。

 so it needs to start being able to start reading a file， so in particular for example。

 you may want if you're implement it as a class in some programming language。

 you may want a constructor to actually be able to accept the file name and then open the file for reading so you will need to know how to handle text files。

 how to read text files in the languages that you're implementing thatmb。The second thing is。

 once you've started reading a file， you should be able to every time get the next command in the file。

So getting the next command， if you look at it， what does it mean in terms of methods operations that this part will have to do Well。

 you'll probably first have to know whether you finished the file already。

 Are there more commands or have you reached the ends of the file。

 and then you'll need to be able to read into some kind of line into some kind of string。

 the next command in the file。So the kind of thing， So what that entails is basically。

 you will need some kind of string capability， string handling capability。

 and you will need to know how to read line by line or something like that in your language。

 The third thing you will have to know how to do is to basically break the command that you've just read into its components。

First of all， you need to know what kind of command is it in our language we have a commands。

 and we have C commands。 And also， there are pseudo commands， if you wish， that define labels。

 These are not really command and the sense of being translated to machine language。

 But for our assembler， it will have to basically know that here we have a label definition。

 so we can handle it so that will be another third if you wish pseudo command that our asmbler will have to know。

 Once we know that we will probably want to give the rest of the program。

 easyy access to the different parts of the command。 So， for example。

 an assignment command will probably want to give access to the destination part of the command to the computation part of the command and to the jump part of the command。

 Similarlyly， in a label or an a command will just want to give our user access to the actual string which may be a symbol and maybe an actual number that provides it。

 For example， the following set of methods if you wish in Java or C in a Javalike language probably would。

😊，Give you this type of access。 But of course， the whole point。

 the important thing is that you get the pieces of information separately and in any way that you wish that one wants to provide them。

 The next thing that we have to do is translate each one of the components of the command into the actual machine code into the binary code。

 Now， recall that in a specification of the language Basically。

 we have each part of the assembly language command has a separate part inside the bits of the machine language command that correspond to it。

And this is basically what we need to do， this translation。Now， again。

 the important point is what we don't need to worry about。

 We don't need to worry about at all the way that our mnemonics。

 the pieces of this code of the command were obtained。 We only get a destination， for example。

 D or computation。 for example， M plus one and need to be able to translate that very short string into the code。

 We don't need to worry about how we got it， what part of the input line it is and so on。

 So this is a very this is a very well defined in small tests that we need to do now。

 And the way to do it was really already specified。 How do we， for example。

 translates the destination part into the three bits that specified it。 Well。

 there was a little table that already appeared in the previous lecture。

 that specified that translation， for every thing that can happen there for every string that can be part of the destination。

 we know what are the bits are。 So we just need to be able to do this translation that's written in the table Similarlyly。

 as there was another table to specify the jump location and yet。😊，Another table。

 the biggest one to specify how you takes the computation and translate it into the seven bits。

 one of them called a and the other called C that specifies the computation in the machine language。

 and recall again， that machine language that is a C command actually starts with 3，1 B。

 So we also need to put the  three1 Bs andvoa， we have our our machine language code。

 So let us use see an example， how to use this parser object and the code object to actually do that translation。

 So our parser object， presumably， gives us access to each one of the part， for example。

 the computation destination and jump parts。 So we basically take each one of them and ask the parser to give us the string that corresponds to each part of these pieces。

 once we have these three different strings we actually go to the code object and ask them to translate each one of them separately。

 according to the table it has in it。 So now each part of these now we have。😊。

The machine codes for each one of these parts to put them together。

 we simply concatenate all of them together with the three ones that appear on the left。

 And here we have a simple piece of code that actually gives us a complete translation of our original string that held in assembly language command into a string that now holds binary bits。

 Let us now move into the third part that we've already identified the symbol table。

 The actual table that keeps the association between symbol names and their addresses。😊，Again。

 the important thing is what the symbol doesn't have to understand it doesn't need to understand anything about the machine language or assembly language about what the symbols mean。

 the only thing the only thing that our symbol table will have to understand is maintain association between a symbol and a memory address。

 that is it without understanding any more than that。So in particular。

 what kind of operations must our symbol table be able to handle， Well。

 we probably need to create a new empty symbol table。

 We need to be able to add a symbol address pair to the table。

 We need to able to look up into the table and see， does this symbol exist there And if so。

 what is the address there。 And these are the operations that basically we need to be able to do。

So that's very， very simple and most languages already have a class that does this kind of symbol table for us and we probably just need to use it。

 but let us look a little bit， how are we going to use this symbol table。

So here is the basic logic of handling the symbols in our program。We start。

 we will probably want to start with creating an empty symbol table。

 Then if you remember in the hack machine language in the hack assembly language。

 there are a bunch of predefined symbols， such as keyboard and so on。

 So we probably the first thing well probably just want to do in our program is add all these predefined symbols to the table。

Then as we go reading the program and translating it。

 we'll probably want to add labels and add variables to the symbol table whenever we see it。

 and then when we already have this updated table all the time in our program whenever we see an A command with a symbol in it。

We basically look up the new symbol， look up the symbol in the table and have a direct translation to a number that then we can keep on a handling。

So the only thing that we probably need to look a little bit more carefully is how do we put the symbols into the table。

 How do we put the labels and the variables into the table。

 So let us look at that piece a little bit more carefully。 So in the case of a label。

 whenever we see a label command and sign parentheses， then we probably need to add that label。😊。

To as a symbol， into the into the symbol table。 And what is the address that associated with it。

 We probably need to know， we need to remember what is the current address that we're going to put the next command in the file。

 And that is the address that's going to be associated with it。

 And this is what we need to put to add to the symbol table。Now， two comments are in place here。

One of them is remember that this we need to know where we are in the program。

 so we need to keep on maintaining a running line number， if you wish， in the table。

 specifying what is the address that every new address is going to be put into。

 because this is exactly what is going to tell us what is the current address。

The second comment is that if you recall， we probably want to have a first pass because there could be forward references to labels。

 we probably want to have a first pass and enter all the labels in a first pass into the symbol table before we actually start using them。

Now， for variables， the situation is slightly different whenever we see another a label。

 another a command with a new variable that we don't recognize yet。 then first of all。

 we know it's not a label because the labels were already all entered in the first part。😊。

Then if it's not in the symbol table， it means that we have a new variable name and then we need to allocate it the next available address and recall that the next the addresses is that we allocate to variables。

 Start number 16 and then keep on going 1718 and so on。

 So whenever we see a new a new symbol in an a command。

 What we need to do is allocate a new place for that new symbol， enter and enter it into the table。

 So up to this point， we've described three basic components that our assembler will have to use。

 And now let's see how do we use them。 What is the overall logic of our asmbler。 Well。

 we start by initial initializing， We need to initialize our parsor to start opening the file we need to initialize the symbol table to be empty and to start having in it all the predefined symbols and so on。

 And then we need to have our first pass where you go after the program only pay attention to labels and enter them into the symbol table。

😊，Then we have to restart reading the program from the beginning， read the command and translate it。

 read the command and translate it， as we do that， we need to keep on entering new symbols into the table only variable symbols now because already all the label symbols were already entered in the first pass。

And then our main loop is very simple。 You read one， you read a command from the input。

If it's an a command and and we we have a symbol， we need to translate that symbol into an address as we will have already described。

 if it's a C command， we need to split it into the three parts that the C command has translate each one of them into binary code。

 and then we have the binary code to output for to output as our output for that line in the file and we keep on doing that until the program is over and that's basically a simple piece of code left to right after we have the three modules that we' previously described So what that finishes the basic architecture our suggestion for a basic architecture of an assembler and what we're going to describe in the next unit is the basic mechanics of doing the project of how to test it。

 how to submit and so on。

![](img/dfb694934ac8bdc4b512c265ce28c23e_2.png)