# 用-C-语言编写自己的-MS-DOS-操作系统--BV1NUNzzQEkC-

。The operating system we are going to create。

![](img/533c584db0c61dd8560bba16520c0967_1.png)

Is also a real operating system。All right， so let's describe this project。 I'm going to do it。

Very differently from everybody else， because if you have watched any videos or read in books about coding an operating system。

And people usually start with the really low level stuff。

But I don't think that's very beneficial for you guys， my viewers， my subscribers or members。

And because it's very difficult to。Test that。You need to create a virtual machine and write a disk image and a whole lot of different things。

 and we are going to do all of that。But during development。

We are going run this on top of Windows or MacOS。Or。

And I'm going to show you a lot going because this project is divided into three different projects。

So if we start closest to the user。Let me just draw a perfect rectangle。Nns。And let's do another one。

Okay， that wasn't business， but I will not get stuck on。Aesthetics today。All right。

 so these are the three components of our project。So the thing to the， let's say， the user。

It's closest to the right。嗯。And so， it's like the。Another the moment tour。AndThe keyboard。Well。

 perhaps a mouse。 Why not one of these old school。Mice with three buttons like this， Never mind。

 let's stick to。What's important。So， this thing。To the right。I will call。The following。

Command dot com。So this will be the command prompt， basically。嗯。So， the user will be。

Welcomed with a prompt in something like the way。So。C in the colon and the forward slash。

And this character， and then they have this blinking marker that they can use to write command。

So that is command。 co。And。And what is that going to。

What kind of responsibilities is that going to have。

 I'm going to list a little bit more than what I'm doing。Be doing it first。

 but let's start with the two most basic。Thanks。It needs to read commands from the keyboard。So。嗯。

It let's do it like this。Read。Commaned。So this is one of the primary tasks。

And the other is when they run these commands and they execute the programs and whatnot。

 it needs to print the results to the standard out or to the screen。So let's write that as well。Sols。

She。Yeah。Sccred， that's。All right， so now we have two different things。 let's say highlight。

In different colors， so it becomes a little bit more。Intuitive。So red will be pink。嗯。Print movie。

All right， so this is the most important things about this command round。And by the way。

 this sketch that I'm doing right now。This is。It's during development。

So there will be changes when we go to production， but during the most part， like probably in 90%。

This would be the thing that we are working。With。All right。

 and then we have this other pillar in the middle here。And this I call the O S。

A And if you don't know what an AI is。It's basically。A set of。Functions。Yeah。

That you explore from a library。So the user of that library will not need to know the internals of that specific library。

 all they need to know is that they call the function with a specific names so on and so forth。

So this OS API， it will be the glue， so to speak。It will handle all the things that we can't handle directly in New Zealand land。

So like file IO and。Was reading and writing， cream， keyboard， exiting the program， perhaps。

At least earlier。And well opening aisles and directories and listing the contents of directions so on and so forth。

 so everything that in Linux， for example， is called system cost。

Those will have inside of that OSF API。And。If we。To lay it right here。Focusing。courseols。え。

Inside the O API， we do。AP。Of course。so if we， for instance， wishes to read。One character from。

The keyword for standard inputs。Then we're going to use a。An exported function from the OB API。

An API call which is named Lode。So let's do this well。Pink as well。So this load function。Will read。1。

Character。Thronged。A further description script。So we， we will have a concept of highcurs。

 It will work a little bit differently than。Pss， for instance。But quite similar， so we open a file。

 we get an integer back and we give that integer to load。

 and then it will read one character and return it。Simple enough。

 no need to use an alternative strings and on。Always one bite。

And then we will have another API called， which is called store。And as you might。As you might do。

Dresed。This will。Right。One fasterer。2。50。Which means that this will be our green thing here。

Because if we write to the standard output， we will print it to the screen。

So we can easily make these connections。These two are linked together。And these two are linked。

So basically， it's just another set of functions that we use instead of the regularular system calls。

And I'm going to tell you real soon why that is a good way to build this thing。

And what do we have farther to the left here during development？So this， these two to the right。

 they don't change when we go to the next step。 The only thing that will change。

Is this to the left here。 So at this point， during development， this will be。It does。It will be。Al。

Or it it might be litter。嗯。So maybe you are starting to understand why this is such a great way of developing this thing。

 especially。When you follow in the video。Because while we are developing this command prompt and this always a gap。

It will run on your regular system。So Windows overback core Linux。And it will do that。

All the way to the last。To the last。Pse of the project。So if we have functions to the right。

 we have API calls the middle to the left here， we have regular system calls。

Which means that this load function， for instance， that will read from the keyboard。In the。Pss。

 which is a standard that all these insists support。This system called is called。Read。

And it's usually。Depicted with a2 inside of a parenthees。

 And that's to indicate that it's system called。 If it's a library called called theres three here instead。

But that's only how you express it。So。In this sketch， the Re S is going to be the pink one。



![](img/533c584db0c61dd8560bba16520c0967_3.png)

Which connects to the load and connect to the reading keyboard inside of the command form。

And as you might have， guess。There is also a rights system book。And in our sketch。

 this will be our green。对。Connecting to door function。嗯。Yeah了。So。All the API calls。Will be met。To。

The postex standard。System calls。Inside of window my OSs were finished。

So during the whole development， you will be able to follow on on your regular system。

Pretty nice and。One note， you， you need to have a post six compiler。So if you run Windows。

 for instance， you should download something called Sigwind and there are others as well。

 but Sigwinind works with all this code for。And it has the exact same command like GCC for compiling and stuff。

As。Well， as I do of Venice。So you can just type what I type and itll work。For Mac OS。

 then you need to install GCC somehow。I think in used， there is a Mac OS。Toolkit。

 which is called Bw for home breww。And you can use that to install GCC。And only 12。

I have not seen many Linux distribution that that does have a。A packageage with a GC compiler。

So this is during development， right？嗯。What about。The real low level stuff。

 We are coding an operating system a real operating system。

So we're not just going to code a command prompt or some API library， we are going to code an OS。

 which means that when we are done。With both of these right。Sections。Then we will do this。

So let me just。Clean this up a little bit。That's。Here。Go。

I'm going to remove the headline and this whole。😔，Ting lift。Okay。

 so the last phase is creating all the real low level operating system things。

So let's draw another of these rectangles。Good enough。And。So let's see。

So now we are at the low level of us。And this is primarily。Divided in two different parts。With。

One part being much smaller than the other。So the thing on the top here。

It is what's called a bootloader。So when you start your computer or virtual machine。

You need a booth loader， which actually。Finds information on your hard drive。

 what operating system you wish to。R。And then it should launch back。A brief system。

So a both loader is the first thing that we need to do at this level， and a bulk loader is always。

Programing assembly。I don't think it's even possible here in another language。嗯。

The rest of this so far， is C only。And then we have and that is called the。Operating system kernel。

 I'm sure youve heard of that word before， like the Linux kernellin。Such。And。

And the kernel is programmed in assembly。But also， you see。

There is a possibility to do some of the work in see。So。

Now we're not at the system call level and longer now we are at。That the doctor calls。

So a doctor call is what I call a system called basically。

But it's my own system calls thats programmed inside the operating system kernel。

So in order to differentiate those system calls with my system calls， I will name this Dr。 Colson。

So if we want to see an example how one of these doctor calls is invoked。

Let's say we want to run this load。そがつい。嗯。Yeah， let's run the load。

ApiI call and thus the doctor call。And in assemblyly， this is done like this。First， we move into E。

And here' got the number， and that is the number of the doctor call。

So we will have some kind of a list。And so let's say。Let's say we have a。Doctor calls， dot H。嗯。

And then inside of this file， we will have a couple of definitions。So， we are going to define。

And all the doctor calls their identifier and start with DR。So this would be D R load。

And then we give a number， so this may have the number。😔，I don't know。2， perhaps。

And then the list continues on like。So then we have Dr Store。And that might be。Let's say，4。

And so on and so forth。So that means that in this case， we move into EX。Ner two。

So that's how we decide at the low level what system call what the call we want to call。

Then we have need to。Push to the organ as well， because the lower function will take one file thescriptor。

As an argument。 So the first argument will same as in the calling convention of。Well。

 regular exceed6。We move it into EVX。And let's say we are reading from standard input。In this case。

 we will give this。A0。Because zero is standard in。嗯。

And then we need to execute an instruction which will do the actual cost。We will do an interrupt。

And the interrupt。To be the same each time， it's going to be0 x。Doctor。And you know。

 it's a little bit off the rails making T7 DR but。If you think about it， an R looks like this。

 And if you look inside of a mirror， let's say it can look like this。

So it's easy to remember that way。Always D7。To execute this code。All right。

So this is the high level view。Of the low-leve operating systems， so speak。

We also need to create a list of different things they need to do at this level。

So let's just write a couple of weeks。First， we need to have the boot loader so we can load our operating system。

After that， we need to。Be able to use files interrupt。

So basically in the same way that we have used it here。They interest。

To give control over to the inner workings of the rating system。The same is done for the computer。

 through the bioos。So there are a list of dios interrupts。

 which one can use to print things to the screen and do colors and communicate hardware and so on and so forth。

 So that's a big of it。And we are going to use these interrupt to read。From the hard describe。

So we need to be able to。Use first them。And I haven't yet decided on which one。

 maybe I will create my own even。When we are able to open and read files。Through the file system。

 then we can continue on and load our parallel。So basically。

 we just read the whole file containing the code for the kernel， the assembly instructions。

We put it inside of the memories somewhere and we jump to it。

Then we need to set up our own interrupt Tlers。And that's so we can use these doctor calls。

 for instance， and maybe some other ones as well。And literally really tedious work is setting up these draft handlers。

 It's a lot of repition and a lot of filling in different structure with the numbers and stuff that。

 So let's save those things for last。And we do also want to。Be able to use the VGA。

So we can communicate with a monitor， handle little colors and write to specific portions of this line。

And possibly I haven't yet decided。And we might want to set up paging as well。

So Beijing is basically a way to handle the memory。Because the memories have been so huge。

InL couple of years that we can no longer reference all of that in just 32 or 64 at this point。So。

Basically， each process will have its own complete。Ispace。And then the Colel Will Me。

Those different areas to real membrane。But it's strictly not necessary in our case。

 as we are not recreating windows， we are recreating dos。Which is。It's16。Ohs。

So we will only be able to handle。65 K。他 run。So paging is not really something we have to worry about。

 but if we have a lot of time on our hands。Which has never happened as of this far。 but anyway。

 I'll put it on the list。And we also need to do the。And low level。哎有。

So low level input and output reading from files and network devices and from。

The keyboards and other hardware and writing to them as well。So this is not an exhaustive it。

A few of the most important things that the operating system had deal with。嗯。

But to tie this back to what we had before， when we were at the developing stage， we were linking。

This load Os call and this door Os call to， two different poleit。S。But inside of this。Low level。

And operating system， we are going to rewire。V。So basically， we will have a similar thing here。

We are going to have a。Lad， Dr。 Cole。And。Store Dr。 Co。And as you can imagine。

 this store is green and will be wired to this。Store in the middle。

And this load will be picked in wheres this。 So that's the beauty of this API layer。

 It's a little bit。Extra work。 but the upside is that we can code almost the whole project directly on our wings machine。

And then at the end， all we do is rewire this API， So instead of letting load point towards the read system call。

 it will call this load doctor call instead。And that's it。

 So when we have written the kernel or the story of the kernel and the Boloader。

 we can just switch off this left layer。All right， so this is the general idea and to put this headline back。

And the last one was jury development this will be。Duringing。Oh。Production。

It deserves to be highlighted with a tele pencil， I think。Okay， it's a lot of moving parts。

 I hope you got the live part of it anyway and that you。Appreciate。This way of building the project。

So we will focus on all the fun stuff。Today and beginning the first episodes。

 because writing thiscom dot co be really interesting。Also， this。

APpiI layer will be very keen to right。and when we get to the assembly stuff and the tedious feeling of the structures and numbers inside the sea。

We only have a couple of them。Steps left， too。Have an entire operating system。

 And this is not going to be a toy operating system。 This is going to be our own version。

 and theills。So it's not going to be compatible with the programs inside of them those。

But we will be able to file programs for our own。D。 Dus。

AndAnd was my hope is to implement as many as possible of the duals command。

 So just to mention view of them。You probably know a couple。

But we used the Cd command to change into another directory and folder。And。CD， without any arguments。

 will just print the current directory。We use the DIR command to list the contents of the directory。

 so the different files and subdirecties。And some information like file size and whatnot。

What else do we have， We have echo， which prints something on the screen。

If we wish to start the program in the current directors say。Let's say we have a program。

 which is called。And。I don't know。发育我。Then we can either just type firewall。

Or we can type the entire file name。Is firewall。 co， We are not going to have support for ex files。

Because I don't freeless see the boy。Of having two different executables。

The dotcom format is very simple， it's just a long list of instructions to the CPU that you load into memory and jump into it。

So we will have something similar to that。But they， as I mentioned。

 they will not be compatibleable with the MSdos dot com files because we have different principles。

And then there are different commands， which are useful when you do script。scripts。

 I think we should support their code both files。It stands for batch files。

 So basically you will do a batch of several jobs or similar。

And there is a four command you can use to iterate through a list of files。And。What else。

You can set environment variables like the path。With a set command。And then， we have。C big。

Wehich will copy file。 And you can also do。C be。Calm。And that means that far。

Copying the content that。You type on the keyboard into a file。And then there's move。

 if you want to move the file and there's the run， if you want to rename it。It's still。

 if you want delete。There's old Z。RMDIR， we're removing the directory。嗯。A lot of it things。And were。

 as I mentioned， we will not be using the backslash。

Because it's annoying that all other big systems use the forward slash and it's a compatibility issue and you code for multiple operating systems。

So let's do the forward slashing instead。But。When we。Use some of these those commands。

So let's say we do DIR。Slulash S and then the name of the file， say。So let's say， I don't know， ABC。

So this is a switch slash S it domain in this case as we search also directories as well for the file。

But we cannot really use slash for the， these switches since we already use the slashes for anything else。

So I will do a regular dash instead。 So dashes。All right， that's。A very。Deep。

Introduction to this whole project。But I think it's necessary know all of these things before you start。

 so you don't just call in blindness。And they don't understand what you are building， a big picture。

And maybe you didn't understand this， at least all of this while just listening to these ones。

 I recommend when you have watched this entire episode。Watch it again and rewind。

So you make sure you understand everything because this is a very。

 very good project to have done to have finished for your resume。All right。

 so the next two hours or something like that， we are going to start implementing this command prompt and this API。

There。And and we want to。Make at least load and store work linked to what we had here before。

 so the system called Read and Write。Hopefully， we can achieve that in hours。

 including any graph you think。Loted。

![](img/533c584db0c61dd8560bba16520c0967_5.png)

Sub guys， welcome to today's show。 So let's create our own operating system， shall we。

And this will be three parts。 The first will be the low level operating system。

 But we're gonna start with part 2 and part 3。And this will run on Linux and on Windows。

 and on Maccos。AndWhile developing。So， the second part。I'm gonna call O S API。So， I will do bash B。

 S。OS S API。Then I will use the default C template。And if you don't have bashbis installed。

 you can find it at the repo。Readpo doctorbich dot com。You can also check the video。

 which is called coding a build system。呃。And the third part will be the command prompt。

So I will call this command。And also， the default fall C template。So， I'm gonna open up。

These folders。Let's see。几道地道。D doose， I will call it Swedish pronunciation。

 And that stands for Doctor dous， this cooperating system。So I will open this in V code。



![](img/533c584db0c61dd8560bba16520c0967_7.png)

So now I have these two folders。And I'm going to start by。Eiting the make file a little bit。

I'm gonna use the C 23。 If you have， you don't have the latest compiler， you can use C 2 X。

 And if that doesn't work， you can remove this。Part。

And I will remove virtue Ti from the link flags because I can't use any libraries。

 I can't even use the standard C library because I'm coding an operating system。

So we need to do everything ourselves。嗯。We will not even be allowed to use the system calls。

And that's why I have this O S API， which will take care of the。诶。Translation。Of system quilts。Mh。

So I will do the same for this。Like so。And I'm going to open up all of these。

So command C and O S API and it dot H file。And I'm gonna change this up a bit。 I'm gonna。

Use the number of bytes。For these。And same here。Like so。EAnd I need to remove virtue this。And。Well。

I need to remove all of these， as well。I will， however， for now。

keep the SDDI O because I might need print F while developing。To make things a little bit easier。

But that's all。So we only have this S T I O， dot H。And they can remove its definition， as well。

Alright， so let's see。嗯。In the O API， I'm not gonna have a main function because this will be a kinda library。

 not。A regular shared library box。Something similar。嗯。So I need to change this make file。

I only need to。 Let's see。 I don't need to do a binary exable。SoThe only thing is always API P。

 I dot O。来首。😔，And。历史。Inside of the make file for。The command。E project。

Go to change this up a little bit。 I'm gonna call that。Executable command dot com。And。

We're gonna link in。O AI。O S API dot o。Like so。嗯，And can I create an additional dot file in this project。

Which I will just call O S dot H。And this， I'm gonna put inside of。They include file of。嗯。

Of command age。So I'm gonna do include O S dot H。And update date。This。So， I have the include。

Diirory of O S API。Alright， let's see if。

![](img/533c584db0c61dd8560bba16520c0967_9.png)

This will compile。嗯。

![](img/533c584db0c61dd8560bba16520c0967_11.png)

Forgot to remove maine inside of the sea。

![](img/533c584db0c61dd8560bba16520c0967_13.png)

There we have command plus code。All right。So now we have the basic setup of our program。



![](img/533c584db0c61dd8560bba16520c0967_15.png)

Or operating system。So how do we do this。Well， we need to be able to。Input a command。

Because our o S will be pretty much like this command window right here。

We're gonna have a prompt say what directory we're in。

We're gonna to do commands like the IR for printing the。Fileles in the current directory。

 we're gonna be able to change directory with a CDD command and so on and so forth。

So the first thing we're gonna need is the ability to read。A command from the user。So。

 let's see where we start。嗯。嗯嗯嗯。I think we're gonna start。

 So we have an ability to print something to the screen。So， I wanna have a。诶。Doctor call。

 I'm gonna call my own system calls， doctor calls。So， let's see。 I wna include。O， S dot H here。

 as well。Alright， so we're gonna have a function。Co。Let's see。So。Load。So。I think we're gonna have。

诶 they。不。We're gonna call this one store。W way。Write something to either file or the screen or somewhere。

And it's gonna take a。F thescriptor。Let's see。And in 16。And then we're gonna have a single bias。

That's it。 I think。And we're gonna have a。Load us well。See。😔，No。This should be called load。嗯。

Maybe I can do this。This is。Right。文学儿。And then we're gonna have something which reads1 jar。

So it will return the chair。And the list will be called star。 And it's gonna take a file descriptor。

And。Nothing else， I think。So these are the first two things。Inside of our API。And。

And we don't have the bo data type。😔，He。Maybe we can do something like。We define bowl。Sen in 8。

And we define true。As when。Then falls as a0。And I think。We need to。bl。These。最 hear。Right。

So let's create these functions， the load and the store。Did know。So。

This would be inside of the O S API。So， it'll be a。Store。And it takes an in 16 file descriptor。嗯。车。

In one character。Maybe we should have an own data type for file descriptors， actually。

This will be a file descriptor。This too。Then we need to name it something else。Let's say， file。

Alright， so。Since we cannot use the standard0 for standard input， the one is， etc cea。

We're gonna need to define our own such things。So。Let's see。嗯。嗯。Yeah。If file is more than one。

Which means it's not standing in or out。 We're not going use standard error。In that case。

 we need to check that the file is open。And in that case， we need to produce an error。So。

 let's say we do。嗯。Return and。It's a role。呃。Oh。F district。And what is return error。

 we need to find out。mhm。😊，So。Define。It turn rather。It takes an argument。And we gonna do。Zm。

I'm gonna to say。The error number， which we need to define ourselves。To whatever x is。And then。

 we're gonna return。0。And will do this， while。Fals。谁。So we have a loop， but it will not loop。

We'll just have this， so we can have。嗯嗯。It inside of this breath。And we need to define the errors。

 and the air number。So， let's do。F。嗯。But。第一。Then， let's start with。A。Because we。

 we probably have some  errors which are more common。 And I want them to have the lower。

Representations。Okay， and we need this air number as well。So。What do about that。Here maybe。

So this will be an in。8。Their number。😔，Maybe even unknown data type called error。

So we type F and in8 to error。And why is this red。Comment oncloed。Is it。That's weird。Oh。

 never mind that。Rightれ。So we return an error if the file isn't open， and we need to create。

 This is open。And since this is a。Logo。😔，粉丝。We're not going to put it inside of O dot H。

 because they exist。Exported stuff。嗯。So， let's go here。嗯，Let's see。So， we're gonna have a。

Bll is open。And it's going to take a file descriptor。And I think we're gonna mark functions。

 as either。Exported or not。So， let's say this is a private。Fction。And these are。Public。Fction。So。

 let's define public as。Let's see。 We can use。The tribute。And what are we gonna put here。



![](img/533c584db0c61dd8560bba16520c0967_17.png)

Let me just check real quick。If I go to。Cd不是。😔，有的。😔，Lets shake the dot age。No， let's try。C she。

Think I did it in this project。Here it is。So， this means that it's。Exported。



![](img/533c584db0c61dd8560bba16520c0967_19.png)

And we're gonna define private。As that。Which means that it's only。For this。嗯。

For this translation unit。I'm just going take a sip of water。All it。 So let's。Do this in C files。

 as well。So this will be a public。这个群。😔，Now let's create。 this is the open thing。So。Private is old。

Private pool is open。Then it takes a file descriptor。And how do we know if it's open or not。Later on。

 when we swap this， always a APII and connect it to our own low level operating system。

We will have some kind of global。State。Which。Has this information。But as of now。

 we need to invoke a system call to check if it's open。



![](img/533c584db0c61dd8560bba16520c0967_21.png)

AndLet's see what we can use。 maybe death。嗯。So let's see。 con strict path name。 knowing we need to。

I have a file descriptor。嗯。St。It the。This takes a file descriptor。人 then。Stucture like this。

Which we are not interested in。 I wonder if we can just give it， no。是的。嗯。

I guess we can just see if it returns E bad file description。By the way。

 since we are going to use some of these。

![](img/533c584db0c61dd8560bba16520c0967_23.png)

电dia o s a。We cannot name that。Ting。嗯。I rememberberg we need to have an own thing for this。So， let's。

Call it error number。This。So we need to update this as well。 Our number。Okay， so let's see。Yeah。



![](img/533c584db0c61dd8560bba16520c0967_25.png)

Forge我的。是。So it's gonna bring gonna juice。If the。

![](img/533c584db0c61dd8560bba16520c0967_27.png)

But we still need to have some mapping between the filescriptors。So。How are we gonna do that。嗯。

Were using an in a。No in 16。Do we really need to have more than 256 open。File descript files。

Our operating system is gonna be pretty simple。 So I don't think we do， actually。

Which make the this a little bit easier。So let's redefine our file descriptor as an in a。嗯。

Then we can just create a global。Variable。So， let's do。File descriptor。File descriptors。

And this needs to be private。And we can have 256 of those。So， we're gonna have a。Signed into。

W we call pose six。50。Andpopo 6， F。Will be equal to。Yeah。Oh，6。5， we give it the file。

And this will always return。上day。Because， either。It will。Find an open file， or it will find a0。So。

 if。Is0。Then， we can early return。Can just do this。We also need to check if。I post。

5scripter is less than。2。I wonder how we're gonna handle this standard in， standard out。死。

Maybe we can let it open return false。In that case。You can do new statement here。

If the file is less than。2。Re false。That is the post 6 file descriptor。Well， it still can be。

I think it's better to do this since it is a signed integer。We can check for-1。Right。

 so now we need to call this stat command。Mhm。😊，So， if that。We give it the。Ple 6， F D。

And I think we can。Just a no here。I'm not really sure。He1 to。Why is it complaining O。Still。

 in this case， were turn falses。

![](img/533c584db0c61dd8560bba16520c0967_29.png)

Let let say人。Return value。

![](img/533c584db0c61dd8560bba16520c0967_31.png)

-1 on error。So。😔，This。Its equal to-1 return false。Otherwise， true。上ber呢。

So we need to define this get pulse exactly。 And I'm doing this as a macro because perhaps we will change。

How this works later on。So this we can put inside over here。Dfin。Yeah。Pll 6，50。And takes an argument。

And the only thing we're gonna do is return。The F is。Indexed by。We need to have some include files。

 I guess。

![](img/533c584db0c61dd8560bba16520c0967_33.png)

![](img/533c584db0c61dd8560bba16520c0967_34.png)

![](img/533c584db0c61dd8560bba16520c0967_35.png)

![](img/533c584db0c61dd8560bba16520c0967_36.png)

![](img/533c584db0c61dd8560bba16520c0967_37.png)

Alright， let's see if this compiles。So。We need to。Sin this a little bit。



![](img/533c584db0c61dd8560bba16520c0967_39.png)

m。YouNeed to check something real quick。

![](img/533c584db0c61dd8560bba16520c0967_41.png)

Or。Same simple enough。

![](img/533c584db0c61dd8560bba16520c0967_43.png)

We need to edit our make file for this project。😔，Let's。Let's call this。OCI。N O S， API requires。そうです。

Yeah it。哦。And we run。Make得 sea。我识别。I think this is how it's done。 Let's see。



![](img/533c584db0c61dd8560bba16520c0967_45.png)

Mmm。

![](img/533c584db0c61dd8560bba16520c0967_47.png)

K， I forgot。2。Change one thing in this make file。We do need to have。They include director。3。😔。

Like so。

![](img/533c584db0c61dd8560bba16520c0967_49.png)

Always better to see。O。

![](img/533c584db0c61dd8560bba16520c0967_51.png)

一。mhm。Maybe we need a full qualified path here。

![](img/533c584db0c61dd8560bba16520c0967_53.png)

No， still doesn't w to go。It doesn't give this， though。



![](img/533c584db0c61dd8560bba16520c0967_55.png)

M。

![](img/533c584db0c61dd8560bba16520c0967_57.png)

![](img/533c584db0c61dd8560bba16520c0967_58.png)

Should we perhaps put the flags here as well。

![](img/533c584db0c61dd8560bba16520c0967_60.png)

In that。No。

![](img/533c584db0c61dd8560bba16520c0967_62.png)

![](img/533c584db0c61dd8560bba16520c0967_63.png)

Oh its a big city。

![](img/533c584db0c61dd8560bba16520c0967_65.png)

![](img/533c584db0c61dd8560bba16520c0967_66.png)

Still the same。

![](img/533c584db0c61dd8560bba16520c0967_68.png)

m。

![](img/533c584db0c61dd8560bba16520c0967_70.png)

How do we pass that along to the other May。Because no none of the flags。It's wrong。Can I get some。

You bag output。Hm。Quite a lot。😔，So let's see。 looking for make file。嗯。

It tries a lot of different combinations。Can here we go。Found an implicit rule。

Considering target file。Looking for a replic rule。Must to make target。

But why does it remake it this way。Do I need another switch to pass on the flags， perhaps。



![](img/533c584db0c61dd8560bba16520c0967_72.png)

Yeah。嗯。

![](img/533c584db0c61dd8560bba16520c0967_74.png)

Let's see if there is a make flag。For。Include。Director is。There is。新闻人问。😔，Included make files。



![](img/533c584db0c61dd8560bba16520c0967_76.png)

Well， let's try that。

![](img/533c584db0c61dd8560bba16520c0967_78.png)

So。嗯。So maybe we can do something like。没。😔，Flas。Is equal to。Flash。What happens then。



![](img/533c584db0c61dd8560bba16520c0967_80.png)

What still isn't passed along。Compiler。

![](img/533c584db0c61dd8560bba16520c0967_82.png)

What if we make a rule。And says O A P dot。

![](img/533c584db0c61dd8560bba16520c0967_84.png)

That make a difference。

![](img/533c584db0c61dd8560bba16520c0967_86.png)

因为。😔，P。Compilr。Flags。S备。

![](img/533c584db0c61dd8560bba16520c0967_88.png)

![](img/533c584db0c61dd8560bba16520c0967_89.png)

Cea flag。

![](img/533c584db0c61dd8560bba16520c0967_91.png)

![](img/533c584db0c61dd8560bba16520c0967_92.png)

No。明妹吻你最爱。😔，Sport。

![](img/533c584db0c61dd8560bba16520c0967_94.png)

![](img/533c584db0c61dd8560bba16520c0967_95.png)

Still no。

![](img/533c584db0c61dd8560bba16520c0967_97.png)

![](img/533c584db0c61dd8560bba16520c0967_98.png)

It was tough to find this answer， actually。

![](img/533c584db0c61dd8560bba16520c0967_100.png)

M。But we are learning， aren't we。We learn by our mistake。



![](img/533c584db0c61dd8560bba16520c0967_102.png)

Mh。

![](img/533c584db0c61dd8560bba16520c0967_104.png)

So， if we do。

![](img/533c584db0c61dd8560bba16520c0967_106.png)

C粉。Is in。2。All right。

![](img/533c584db0c61dd8560bba16520c0967_108.png)

Still the world。

![](img/533c584db0c61dd8560bba16520c0967_110.png)

And if we were to change into that directory。Al A。The the run。没。



![](img/533c584db0c61dd8560bba16520c0967_112.png)

Will it make a difference。

![](img/533c584db0c61dd8560bba16520c0967_114.png)

Not really。And if we add this。If we can do。This。

![](img/533c584db0c61dd8560bba16520c0967_116.png)

![](img/533c584db0c61dd8560bba16520c0967_117.png)

Still does not want to do that。

![](img/533c584db0c61dd8560bba16520c0967_119.png)

It doesn't care what we put in here。Just doesn't pass it along。



![](img/533c584db0c61dd8560bba16520c0967_121.png)

And what if we name the rule after this。Somethingなです。



![](img/533c584db0c61dd8560bba16520c0967_123.png)

Okay， there we go。All right， we learned something today， didn't we。Too few arguments to Ftats。



![](img/533c584db0c61dd8560bba16520c0967_125.png)

Oh， up but the parenthe is thg。Stir。这斯。对。

![](img/533c584db0c61dd8560bba16520c0967_127.png)

Or even to null where none null expected。 How does it know that it's。Its not expecting enough。

Maybe it's this restrict thing。But it's not here， though。Well。

 I think we need to create one of those， even though we're not going to use it。



![](img/533c584db0c61dd8560bba16520c0967_129.png)

So let's do something like this。 and we'll call this。

Undercore to indicate that we are not going to use it。



![](img/533c584db0c61dd8560bba16520c0967_131.png)

![](img/533c584db0c61dd8560bba16520c0967_132.png)

Coning types for store。You have F file。In the。嗯。Maybe I got the mix up inside of here。

This should be load。And this。Other one should be store。So， we're gonna have a public。In a。Store。

Which only takes an f file。And at this point， returns。6 real。



![](img/533c584db0c61dd8560bba16520c0967_134.png)

![](img/533c584db0c61dd8560bba16520c0967_135.png)

Control reaches， and27。Right， because we're not done yet。Let's put。Return。Falall soonerer。



![](img/533c584db0c61dd8560bba16520c0967_137.png)

嗯。Maybe uninitialized。Okay。

![](img/533c584db0c61dd8560bba16520c0967_139.png)

Let's do。Let's not make it a pointer。And then we give the address here， instead。



![](img/533c584db0c61dd8560bba16520c0967_141.png)

All right。So what is the multiple definition of error number。



![](img/533c584db0c61dd8560bba16520c0967_143.png)

Because we include。Header files from multiple。Locationations。Maybe we should add to all of these。He。

Proragma once。So they will only be included at once。I'm not sure it's gonna help in this occasion。

 though， but let's try it。

![](img/533c584db0c61dd8560bba16520c0967_145.png)

![](img/533c584db0c61dd8560bba16520c0967_146.png)

No。Since this is happening when the。Where we live。It doesn't work。So we need a way to differentiate。

If we are including from。The main program， or from the library。So， let's see。

It's inside of the O S dot age。So。Let's say， if we have defined。That we are inside of the。Library。

Then we're going to do this。Otherwise。We're gonna do。Extern。嗯。Exterern。Public。I肉。A呢。And live。😔。

And we're gonna do the same here。 We make it public。

And where do we define this library thing that must be inside of this file。So。We do define。Libra。



![](img/533c584db0c61dd8560bba16520c0967_148.png)

I know it works。Fretty eyes。 Fty eyes。

![](img/533c584db0c61dd8560bba16520c0967_150.png)

Alright， let's。Finish this function， shall we。So we have checked that the file is open。No。

 we need to。Read one character from that file。So， we need a buffer。Let's say we have an in a。But。

Of size 2。And。We also need to have a sideine integer。With the return values。So。

 let's just call this and。嗯。And let's clean this out， first。So is it bathuff。Equal to。Buff plus 1。

Equal to。0。And it should be。In a。Cal。And then we set n equal to the read。哦。Over。We need the pole 6。

Frely scriptor， as well。So。Still。Sign in pro 6，5 D。Close 6，50 is equal to。Get post 6 safety0。好烦呀。😔。

And。How do we。Show a failure here。If this is 0。It has failed。The thing。嗯。The indices are， actually。

The FD type。 So we should make this a signed integer， actually。But then we don't have 256， different。

Maybe we can do something like。You can make this an int8 instead， And this is an unsigned thing。

And let's say，0。Is the failure。So， let's turn this back。To this。And let's do if file is less than 3。

Sugg just to remind ourselves。嗯。So if it's a0。It's an error。If it's a one。

 then we have standard input。And if it's a two。We have standard output。嗯。Okay。So， if。Poose， 6。

 F D is 0。In that case， we return an error of。But。File thescriptor。And if。Pos。FD is。If it's。When。

Let's see here。If it。Equal to。2。If it's equal to1， that's our standard input。

Maybe we can do it like this， instead。P 6， F D is equal to。If。Withpo 6 F D。Is 0。if it's。When。Then。

 it should be 0。And if it's。2。It should be。W。And if it。3。我去了。😔，Indicate standard error。

Then it should also be one because we don't have a standard error。Which means that we。No。

 we don't need this cloth。 We make sure it's never。Standard error。 And of that case， we will set too。

But we need an else clause， as well。嗯。Can we really sell it to itself， I'm not sure， actually。Well。

 we'll see you Wet we。嗯O。So， we're gonna read。From。Thepo 6， F D。Into。Our buffer。

We're gonna read one bite。And n should be equal to one， if we succeed。So if n is not one。

It means an error。And here we need another error code。😔，嗯。

It's just a it's a no error I O input output with error。Otherwise， it succeeded。And in that case。ち。

No。I'm doing this wrong， aren't I。Because we would。We're gonna write。 This is our right function。

Which means that we need to set buff equal to。In a。No to see like this。So， then， we'll run it。

If it fails。Return this day。Otherwise。Will return true。And we can basically copy this whole thing。

And put it here。And just modify a few things。Allright， so let's see。In this case。

 we are gonna read one by it。This should be， if it's。More than。The think。

This becomes a little bit tricky， though。OrMaybe not。Let's do 3。But then we waste one place。 No。

 let's， let's have it as we did。Alright， so we check if the file is open。

And we do this and this and this。 We get the pole6 FD。In this case， we don't set this。And。😔，We read。

晚安。😔，Then we just return that bite。As an in a。And that will be buff like this。

And we need to add this I O error。Let's also。3 a。An error。No error。Which is cereal。



![](img/533c584db0c61dd8560bba16520c0967_152.png)

Coright。We need to have。Some includes。

![](img/533c584db0c61dd8560bba16520c0967_154.png)

Unice姐姐。

![](img/533c584db0c61dd8560bba16520c0967_156.png)

![](img/533c584db0c61dd8560bba16520c0967_157.png)

Then it compiles。Alright， so we need to have something which sets up this。Aray。This FDs array。

So let's create a。Private function。So， private。Vid。是的。FT is。So first， we want to zero it out。So。

 let's do 0。50s。晒说。😔，What else？We need to deal with the。First couple of。Enre。So， F days。0。This。是么。😔。

To the standard input of one。5s。1 should be 2。No。Yes。And F is 2。Will be the first。Open real file， so。

We will not touch， touch that。And we need a zero function。that inside of the O S API。

It takes an in8 star， and an in 16 size。The，pri。How did I define it here。

Private zero can do that when it avoid void her。Private void，0。In a。Stray。And。In 16 size。So。

How do we clean this thing out。Let's do a simple loop。So， let's create an in8。P。And in 16 M。

And4 n is equal to。The size。And P is equal to the string。We loop as long as N is positive。

And at each iteration。We do n minus minus。We do P， plus， plus。And then we just set p equal to 0。

And we return。I you了。It should compile at July first try。



![](img/533c584db0c61dd8560bba16520c0967_159.png)

Almost。

![](img/533c584db0c61dd8560bba16520c0967_161.png)

Set up， if it's okay， We haven't used it。So， let's use it。m。I guess we can， really。

What I would like to do is something like this。😔，So， we run this。



![](img/533c584db0c61dd8560bba16520c0967_163.png)

But， this is not possible。

![](img/533c584db0c61dd8560bba16520c0967_165.png)

I don't think it is。

![](img/533c584db0c61dd8560bba16520c0967_167.png)

![](img/533c584db0c61dd8560bba16520c0967_168.png)

![](img/533c584db0c61dd8560bba16520c0967_169.png)

![](img/533c584db0c61dd8560bba16520c0967_170.png)

What if we were to post this。Yes。LetSee。😔，Can we put it。I don't think this is gonna work， is it。



![](img/533c584db0c61dd8560bba16520c0967_172.png)

![](img/533c584db0c61dd8560bba16520c0967_173.png)

![](img/533c584db0c61dd8560bba16520c0967_174.png)

![](img/533c584db0c61dd8560bba16520c0967_175.png)

呃。Which means that we need to have some kind of initialization function。Which we all。Always， Mr。

In the beginning。So。Inside of this。Then we need to have a public。In it。And we put it right here。

And what will this do public。In it。Public。Vid。In为。The only thing it's going to do right now。

 at least。Is coal over local setup。F is。Function。Then returned nothing。Which means， inside of。

This one。We need to do that， first。Which means that we need to check if this has been done。Otherwise。

 we cannot do any I。So how can we flag that。Maybe we can just use a global variable。😔，So。

 it'll be public。不。yy。起来。😔，And this needs to be false。And if we go here。

You want to set initialized to true。And we need to check that in every。Public function that does I O。

Or maybe we can use This is open because this would be called。In every occasion。

Though this can only return true or false， and we need to show that。

It's because of the uninitialization。So， let's put it here。嗯。We can just do some macro。Let's say。

 a third。印力色蓝。😔，We put it inside our load， and our store。I possiblyssibly。Even。😔，Couple of others。

 later on。So， let's see inside of this。O S dot age。Or this should probably be inside of here。So。

 we define。The Sir。你 should来。So， let's do return。Ero。然而。嗯。Yiling。😔，Or maybe。😔，Aor E。It's good。

So let's say we have an R in it， which is one。

![](img/533c584db0c61dd8560bba16520c0967_177.png)

![](img/533c584db0c61dd8560bba16520c0967_178.png)

Hey， we run into the same problem。As before。So we need to use the same solution。



![](img/533c584db0c61dd8560bba16520c0967_180.png)

![](img/533c584db0c61dd8560bba16520c0967_181.png)

Alright， so let's， let's see if it works。Let's comment out this in it。AndLet's try to read。Let's see。

Ne to shape， which is which。Store is reading。So， we store。From the file，scriptor0。嗯。

And we read it to just。No。No， it's like this。Let's print it in hes。



![](img/533c584db0c61dd8560bba16520c0967_183.png)

Alright， let's see what happens。

![](img/533c584db0c61dd8560bba16520c0967_185.png)

Z could 0， which means in it's an error。 Let's also print the。I number。And by the way。

 in our in function。We should also set the。The error number。0。



![](img/533c584db0c61dd8560bba16520c0967_187.png)

Right。Okay， so。The return value is 0， and the air number is1。



![](img/533c584db0c61dd8560bba16520c0967_189.png)

And what is error number one。Uninitialized。So that works exactly as we wanted to。 What if we were to。

Put this back。Will we be able to read from the standard end。



![](img/533c584db0c61dd8560bba16520c0967_191.png)

We still get a one。But it didn't really recompile， didn it。



![](img/533c584db0c61dd8560bba16520c0967_193.png)

Maybe we should do and make clean here。In the OS S API。Maybe we put it in the other one。

Can we do something like clean。

![](img/533c584db0c61dd8560bba16520c0967_195.png)

哦。

![](img/533c584db0c61dd8560bba16520c0967_197.png)

Let's do。cle。And。Can。O。p i。😔，C that， so。Clean O API。We need to set this as phony。Mhm。

The phony basically means that it doesn't produce。那你。😔。



![](img/533c584db0c61dd8560bba16520c0967_199.png)

Anything。It just his phone。Okay， so know everything should be compiled。

But we still get our number one， why。

![](img/533c584db0c61dd8560bba16520c0967_201.png)

Because initialized is equally to true。And what we do is we check。Assert initially， wait a second。He。

😊，No， I will believe I know what's wrong。I made a stupid， stupid mistake。Yes， I return an error。

I need to do an if statement， first。😔，So。😔，Yes。Inlish。G。Then we do that。OK嗯。

So let's test the first case again。Now， we should return that error。Yes， it does。 Now。

 it should not return that error。

![](img/533c584db0c61dd8560bba16520c0967_203.png)

![](img/533c584db0c61dd8560bba16520c0967_204.png)

Okay， this is going on my nerves。

![](img/533c584db0c61dd8560bba16520c0967_206.png)

But did it recompile。The O。It's included here， but it does not。Does's no do that。



![](img/533c584db0c61dd8560bba16520c0967_208.png)

Those make failhu。We need to check the header file。As well， because that's the only thing we changed。

 So it。

![](img/533c584db0c61dd8560bba16520c0967_210.png)

Doesn't w recompile。 I think it's that。Yeah。Okay。It waits。 So let's。Tve been a character。

And it's returned。Our number is 0。And we get something back。 It works。That is so nice。



![](img/533c584db0c61dd8560bba16520c0967_212.png)

What about the other way around， Can we use the。Load there to print something。Let's see。

Think we should be able to do that， actually。Let's see。Instead of doing this。We use load。

And this should be。Standard。Output。And we want a print， let's say。😔，Xス。

Let's also add a couple of new lines。

![](img/533c584db0c61dd8560bba16520c0967_214.png)

![](img/533c584db0c61dd8560bba16520c0967_215.png)

And we get it next。 You work。And if we haven't initialized。In this case， we should just get。



![](img/533c584db0c61dd8560bba16520c0967_217.png)

Nothing。And we get nothing。

![](img/533c584db0c61dd8560bba16520c0967_219.png)

Alright， so we have。诶。Constructed our project in two different ways。 We have an OS S API。

 which handles the。Talking with operating system。 So currently。

 it's talking to either Windows or Linux or whatever。 But later on， it's gonna。

We're gonna to rewire it。To talk to our own operating system， Colel。

And we have also created the first small。Steps of our command co。And。So。Now。

 we can start building things。 And the first is going to be， so we can read。Com。

From the standard input。And。But that's all for now。I think this is going to be a pretty cool project。

 and you're going to be able to follow along on your own computer while we are developing this command prompt。

So the， the last single step will be to create the operating system core。

 And then we will need to rewire it so you can run it from a virtual machine or something。

 But up until time until that point。You can run it on your own computer because of our O S API。

So it's gonna be a very fun project that I hope you like and subscribe。

And hit the bell button so you know where when the next episode comes out。

 And also tell me what you think about this pro project down at the comments。

I'm very eager to hear your thoughts。 And if you have any suggestions of functionality of command or commands that we should add to this。

 please tell me。EThanks for watching。 Thanks for today。



![](img/533c584db0c61dd8560bba16520c0967_221.png)

Did you learn anything useful today。And you want to support this channel。

Go to Doctor Brch dot comlash support。 You can also click the button， Be a member。

 Thank you for your support。

![](img/533c584db0c61dd8560bba16520c0967_223.png)

![](img/533c584db0c61dd8560bba16520c0967_224.png)

![](img/533c584db0c61dd8560bba16520c0967_225.png)