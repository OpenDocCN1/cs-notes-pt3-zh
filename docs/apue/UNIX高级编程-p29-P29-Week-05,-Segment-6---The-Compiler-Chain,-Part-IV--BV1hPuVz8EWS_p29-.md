# UNIX高级编程-p29-P29-Week-05,-Segment-6---The-Compiler-Chain,-Part-IV--BV1hPuVz8EWS_p29-

Hello and welcome back to CS631 Advance programming in the UniX Envi。This is week 5 segment 6。

 and we'll be wrapping up our discussion of the compilation process and the compiler tool chain。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_1.png)

In the previous videos， we've seen how the compiler performs the different steps of pre processingcess via the CPP command。

 Comp proper， and assembly of the intermediate code into an object file。

The only remaining step left is to then take this object file and link it to produce an executable。

The stage is performed via the L D command， which combines a number of different files as shown here into the final output file8ed out by convention。

As we can see， the linker appears to be doing a bit more than just using our file， however。

The only file we control， the output of the previous assembly stage is the dot O file over here。

So what' with all the other things shown here， Well， let's take a look。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_3.png)

To pick up where we left off， let's review the previous stages。First。

 we called the pre processorcessor to create the dot i file。

Then we perform compilation on code generation by RCC producing the assembly code in the dot S file。

After that。We used AS to produce the dot O file。Then we tried to execute this object file。 But。

 of course， we were unsuccessful。So let's go ahead and use the LD command。H， too bad。

 I guess it couldn't be quite that easy。Seeing some sort of error display here。

 perhaps we should start by looking at the manual page。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_5.png)

Okay， as previously noted， Ldius invoked as the last step in the compilation process。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_7.png)

Here are some options。It sounds like we should be able to run this command shown here。

So let's give that a try。HNow we just get a different error。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_9.png)

Let's go back to where we started and look at what the initial error actually was。 After all。

 I keep insisting that the error messages in Uni are meaningful and should provide us with a pointer to how to address them。

The error shown here indicates an undefined reference to printf。 Why would that be。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_11.png)

Let's check the manual page。As expected， printf is part of the standard I O functions provided by the standard C Library。

 A K Lipsy。 and the manual page tells us over here what the right flag is for the linker to link against Lipsy dash L C。

So let's add that to our L D command。Okay， that looks better。

 No longer do we get an undefined reference to Prif And the command succeeded。

 only showing a warning。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_13.png)

And look at that Here We have our executable aid out。Let's run it。Damn executable failed。

 But why is that。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_15.png)

What type of file did we end up with。HThat looks right， more or less。

Perhaps we are missing some other libraries to link against。

What libraries do we have on this system besides Lipsy。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_17.png)

Oh， okay。 That's a lot。1100 libraries to be precise。 What library might we need here。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_19.png)

Let's look again what the manual page had to say earlier。There。

 it mention something about a file named CRT0。0。C T stands for C runtime。

 and this file provides the various execution start proteins。

 so you probably want to include them in the linking process。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_21.png)

But didn't we try this before。Perhaps we have some CRT files in our directory user Li。

Looks like there are several。 Which ones would we need。Let's look again at the warning we got before。

 After all， I also keep insisting that warnings should be paid attention to。

 even if they don't prevent the command from completing。

We are looking for the symbol underscore start， which of the C T file contains that symbol。There。

 CRT0。0。Let's blink against that。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_23.png)

HOkay， different warning。 Now we're missing a symbol named underscore Finninni。

This symbol appears to be present。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_25.png)

In these two files here。 But maybe Gr isn't the best way to determine which of these files defines the symbol。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_27.png)

The better2 might be an M。A command used to explicitly list the symbols from an object file。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_29.png)

Here， N M user Li C t0。0 gives us this output， which indicates which symbols are defined and which ones are referenced from this object file。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_31.png)

Symbols marked with a T are defined in the text segment of the file。

 Sms marked with a U are undefined。So underscore， underscore start is defined， but fine is undefined。

In the file C D I dot O， however， we find that the underscorecoinni。Is definedian。

 So it looks like we need both CR T 0 dot0 for underscore start and CR T I dot0 for underscore Fni。

Hey， look at that。 No more warningnics。Let's run our program。W what it had out not found。

But the file is right there。Why did it say not found。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_33.png)

Let me run file against this。It tells us that this isn't executable， That is dynamically linked。

And that use as an interpreter， Li L D 64 S0 dot1， meaning this binary file is interpreted by that。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_35.png)

And so the not found message does not refer to Ado A here， but rather to the interpreter。

 Li L 64 is Odot 1。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_37.png)

Which does indeed， not exist。So now what？Let's compare to an executable that we know does work。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_39.png)

There， L D is also a dynamically linked executable， but this one uses the interpreter。

 user lipig Zec， L D， L， S O。What's Ldi dot Allfso anyway。Oh， hey， it has a manual page。

 How convenient。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_41.png)

So LDLlf S O is a so called runtime link editor used to load and executable and all required objects at execution time。

So let's tell L D to use this L D Allfso thing， asked the dynamic linker。Okay。

 now let's run the executable and。Oh， man。 Now what。You know what。

 I don't think this approach is working。 Let's try something different。

Let's see what C C does when we invoke the linker。 Remember。

 the dash V flag shows is exactly what commands and runs。And here it is。Well， that's a lot of flags。

 but we see several of the ones we derived。Here's our dynamic linker。The CRT objects。

Are I hello at old fire。Oh， and over here， a few more CRT objects。

As we will see in a future video a bit later in the semester。

 when we talk about shared libraries and the start of a process。

 we need to provide a bit of a book into a program provided by the C R T objects。

 beginin and end objects to allow the program to start up and return from our main execution。Anyway。

 let's add these to our command。And。Finally， a working executable。

To see what our linker invocation is quite a bit more complicated than just running L D Hello Dodo。

 But wait， why is it that we had to specify the CRT files by absolute path。

 but we could simply say link against Lipsy。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_43.png)

Here， the manual page tells us that to link against the given library， we need to pass L Na spec。

 and the linker will go and look for a file named lip names Spec do A or in the case of Elf。

 Li names spec do S O。To tell the compiler where to look for these files。

 you can pass the dash capital L flag。Which specifies a search directory to be used in addition to the default。

We can ask Ldi to show us its defaults by running it with the D dash Robbose flag。

Which then shows us that it targets the Elf 64 x 86 architecture。

That it uses the start routine for program entry。And that it looks for libraries under user Li。

So we should be able to find our seat library right there， and indeed we do。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_45.png)

Liip C dot A and Li C dot S O， albeit Press some links。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_47.png)

Again， we will revisit the details of the shared libraries in a future lecture。

 which is why I'm kind of hand waving the details here。

For our purposes in the context of the compile process， though， let's briefly review。

If we want to run through all the stages ourselves， we'll have to。Run CP to prepro source file。

 Run C to compile C into assembly。Run A S to turn assembly into object code and run L D to link the object file with the C runtime code and the standard C library to create the executable。

But of course， we can make our life a bit easier and have the compiler driver perform all these steps for us in a single command。



![](img/66f7d27f47acaf03f62deedcc5ae3f6d_49.png)

Here we create the dot S file。We observe the default include path used by the preprocessor。Over here。

And finally， end with the invocation of the linker。And if all works out。

Then we get a working executable。Horay。Now， as you can tell。

 what we described as a simple sequence of steps ended up being separate commands。

 each with some perhaps surprising complexities and many， many command and options。

But we saw that we can let C C drive the whole process， as we are used to。

Sees he takes all of the different command and options and may then pass them through to the other commands as needed。

In so doing， it is important for us to understand that the order of the flags may matter。

This is perhaps a bit surprising in that most uniquex tools do not care about the order in which command and fls are given。

 But for this tool， it does make a difference。We will illustrate this by example in a future video。

 For now， simply make note of this and perhaps review the manual pages to see where the order might play a role。

We also saw that the compiler may have a set of defaults built in。

But also that the behaviour of the tool can be influenced as so often is the case with our tools via the environment。

Again， a lot of these details will seem eoteric to you now。 But with time。

 you will come back to the behaviour of the compiler as it goes to the different stages and repeated references to the manual pages will be inevitable。

Now， while this concludes our high level coverage of the compiler。

 you may also have noticed that throughout this series of videos。

 we occasionally made use of another tool to help us save ourselves some keystrokes and to build certain files using previously specified rules。

 the makeg utility。Makeake is an incredibly useful b tour and as part of the Uni development environment。

 equally important to understand， which is why we will cover it in our next video。😊，So stay tuned。

 And thanks for watching， cheers。

![](img/66f7d27f47acaf03f62deedcc5ae3f6d_51.png)