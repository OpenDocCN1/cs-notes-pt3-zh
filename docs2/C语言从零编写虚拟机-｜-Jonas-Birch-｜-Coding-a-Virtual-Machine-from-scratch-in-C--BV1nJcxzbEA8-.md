# C语言从零编写虚拟机-｜-Jonas-Birch-｜-Coding-a-Virtual-Machine-from-scratch-in-C--BV1nJcxzbEA8-

So today， we'll decoding our very own virtual machine completete with a virtual CPU and virtual memory。

 It will have a 160 B CPU and 6 different CPU registers。

 We also need to develop our own assembly language with instructions like Mo Noah hold as。

 We will have 65 k of virtual memory。

![](img/fe8ce403cf7cf58356ce32702c603a81_1.png)

And it's going to be divided in a code segment， which is read only and a stack for data。 Okay。

 let's start the project。

![](img/fe8ce403cf7cf58356ce32702c603a81_3.png)

So guys， welcome to today's show。 Today， we're going to do something very， very exciting。😊。

I am going to code a virtual machine， and I have never done anything like that before。

But I have a general understanding how we should do it and let's see how it goes。So let's get to it。

I will start by logging in。My。A code planted server。And you know。

 you can get access to this Linux server if you become a member， if you become a tier1 member。

Enough advertisement， let's。See how we'm going do this。 I'm going to go into my folder。

 and I'm going to use our own build system。B B， yes。And if you remember。

 bash build system is a tool which generates the。Dot C and dot H file her basic。



![](img/fe8ce403cf7cf58356ce32702c603a81_5.png)

Starting point。Based on a template。 And if you want to get BPS S。

 you can always download it from the repo， repo doctor Birch dot com。

A lot of stuff here is not always available。But BPSS is always available and so it's the birth jules。

 which are used quite frequently。And also all the code for this episode will be available for 48 hours after I publish this video if you want older stuff you need membership。



![](img/fe8ce403cf7cf58356ce32702c603a81_7.png)

All right。So let's see。 I will run the B， and I will call this project。What should we call it。

 What about。Bch V， I don't。 It's not a great name， but I'm not coming up with anything bettercur， so。

And which template， we only have one default C template。And there we go。

 If we go into the perrch Vm folder。設定 to。好。We do have a make file。



![](img/fe8ce403cf7cf58356ce32702c603a81_9.png)

I don't see。 A little d。So let's launch Sociopath and CP client。one of my。Best programs that I made。

 I think。And so I will go into the TNP， and I will。Right click on burst V and open an editor。

So now it will download everything and it will be synced。

 so whenever I save or create a new file or a directory。

 it will automatically upload it to my Linux server。Cold planet。So let's see is this correctly sized？

Pretty much， yeah。So let's see what we got。 We have a simple make file， which will。

Compile everything with virtues。嗯。We have a very simple C file， which only includes the H。

Tinly main function。And then we have the H5， which has a bit more， a couple of includes。

Including the virtue ths。And then I have my integer numbers， and I have my。Tite cast macros。

But one of my viewers asked me， why do I name this after the。

So the six is the six here and the two is the two here。

 Isn't it better to name them after how many bys they are， And indeed， that is a better way。

So this is one byte。This is2 Bs。This is4 by。 This is。

So thank you for that That's a great suggestion and if you have any suggestions。

 please put them down below in the comment section， I mostly listen to all my suggestions。Al right。

 so let's say this。 How should we create a virtual machine， What is a virtual machine， Well。

 basically， it's a computer。 So it has the same thing a computer does。

It has a CPU with different registers and so forth。

 and it has memory and perhaps any auxiliary reports， etc。So let's start simple and build from that。

That's usually the best way， too。Approach this since I have never coded anything like this。

 and I haven't really planned， I will just。Do as I go， so to speak。And as always。

 I begin by creating the data types and letting the data types guide the entire project。

 and that's a good way to do any project because if you have all the data types。

 you only need to create the functions that use these data types and you're done。All it。

 So we need a structure for the actual virtual machine。 So let's call this V N。

And what does a virtual machine contain， Well， it contains a CPU， right？See and some memory left。

Let's say， we have a。嗯。Shall we。Just name it memory and then divide it in the different sections and stuff。

 Or should we。Just use that。I think we are going to use stack for now。

 at least if we need other types of memory。That's later first。Right， and。Let's see。

I make this a pointer so we can。诶。By the way。I have some limitations with this project。

 so it will not be too。Difficult。This virtual machine would be a。16 bit virtual machine。

 So like the 386 computer， if you had one of those back in the days。And 16 bits。Theft space，65536。

Different memory addresses or different possible values inside of the registers。

And that means our memory will be 65 k。It's 65 kiloB of。Memory。

And our CPU will have a couple of registers， and registers are basically the。Process words。Memory。

So we will have an AX。We will have a big。C x and啲嘅。

So these are the general purpose registers that we use for like addition and。Stuff like that。

But then we need a couple of other registers as well。 We need a stack pointer。

 which basically points to the top of the stack， the memory。And we need a。Dction pointer， I P。

 which points to the next instruction。In the program to execute。And we could。

Add a lot of other stuff here， but。Let's make it simple。 And I think we will start。でス stuff。

And then I would probably add some kind of， I don't know， a cereal。Come work or something。

But that will be a later question。And possibly。诶。Hard describe， or maybe。F。相对来的。

But this will also be a later。thing。So the first thing we are going to focus on is getting the CPU to work。

And the memory。I'll keep them。For now， so we will have a CPU and a stack。And。We also need a program。

So basically a sequence of different instructions。嗯。So let's start there。嗯。嗯。

And I want a typed if thisstruct。So。で。李。And this would be。ないです。Okay， but what is a CPU。

 what is a stack and what is a program？Let's begin with a CPU。This will also be a structure， yes。主。

And as I mentioned before， we need a couple of registers。So， registers。R。嗯。Or maybe we shouldn't。

 should we have these many levels。Maybe we can create macros to make this a little bit easier later on。

I think the structure will be better， if we do it。In this kind of way。

And what else do we need in the CPU。Maybe we should just。そ we need。歌いて。理由。They我口。です。And then。

 we need to create。The registers as well， which would be。Different structure。本です。嗯。

And as I mentioned before， we will have a couple of different general purpose registers。

Let's say this is Greg。And we will have。I will use lower case for convenience。We will have a。

Have the。Cエエ。The。Those are the general purpose once。 And then we need the stack pointer。嗯。

We need the instruction point。嗯。特别的粉能。系 did。主。Right。诶。对。And what is a rag。Well， for now。

Or possiblyssibly forever。This will be。当。She。嗯。Because we are dealing with 16 bits。Registers， right？

Okay， so that part is done。What about the stock。What is his stack。Well， basically。

 it is a memory space。Yeah。How should we define。った。Perhaps we will just do this。It will be an。

Let's see。It would be a sequence of a to B。Characters。嗯。So。We'll only do this。

First that could be in age， basically。Or several。 actually， it will be an array that。We will not。Ora。

一週 actually。Maybe we should not make this pointer。对。嗯。Can we do this。

I'm not sure if this is possible， because I won't。Basically， this， right， all once。

And that is the same as this。 But I'm not sure if that is correct。 We will see if it works。

 It would be kind cool to。All right。 So let's see we have the stack。 And what about the program。

 What is the program。It's a sequence of。Instructions， right。So。Basically， we will type the。

The sequence of instructions。是。And this will also be an array。But we will not define its size。

So I will only do this。And now we need to define what an instruction is。And what is an instruction。

Well， it's something which we look。Psically。And instruction is a sequence of op codes， right？So。

 let's define that。I个。诶。Upcode， that is basically the machine code。Version of the。

Assembling instructions。Because we need to invent our own assembly language in order to make this work。

It will be a basic assembly language， but it will be our own。So let's see， typed upcode program。

And since program is a pointer， this will be an array when we use it。And what is an up code。Thing is。

 up codes look a little bit different depending on they have different size， for example。

 So let's say we have something like move to the。A X register。Number 5。How will this look like First。

 we will have something with defined that it's a move instruction。So， let's say， for example。0。

1 is a move。And then， we need to define。What the。That we were moving to the AX register。

So we could do something like another 01， which would suggest that this is the A X disturb。

But I think a better way would be to。Take this one and do some mathematical operations to it。

So let's， for example， say that we。嗯。That we do an or operation。And then， we have this。エエキスティ。

And if we go and check out the binary representation of this。So we have we have two bytes to use。

 which basically means four hexadecimal characters。So if our remove instruction is a one。嗯。

And the difference。し。So， the right most。But if that is a one。This is a move instruction。

Or maybe if if those two。Let me see。We actually only have one bike， at this point。But one by。

If you goodbye me。It's this right，8 bits。So this is how we should think of it。

So the move instruction， let's say the move instruction is defined by。Putting a one。

Inside of the right most。For。Bits。So then the rest of these bits。Can be used to define。

What we are moving to。So let's， for example， say that this， if this is a one。

 then we're moving to the A X register。If this is a0 and this is a one， were moving to the Bx。

And then， we have。C x。We have。啲嘢。We have。Have S P is the that pointer。

And we can't move anything to the EI instruction point， but it seems that our bits will be enough。

So this rightmost one。Should be a one defining there is a move instruction。And those three。

We will use this or operation， So if。We want to order it with AX。嗯。We have this right。

 This is the move instruction， and we want to flip this bite to one。And you will order this。By0， two。

That对。Flip let's do a well。So that's basically how it would work。 And if we have an entire in the5。

 by the way。How do we put the five in there。Well， we have these。4 untouched。別？Yeah。

And how many combinations is the， that's2。Power of four， right？What is that two times to is four。

2 is 8。2 is 16。That's not enough。So， basically。We need。How much do we need。

 We need an entire 16 bit thing， right。So， this first bite is。The instruction。And then we need one，2。

3，4。Before。你如问。Or。W。We need。All this。To define the5。一服一2歌。

If it's going to be possible to use all the 65，000 different combinations。So in this case。

To get the5， What do we need， We need。2。We need this to be a one。 So we have4， and this will be a 5。

So this whole thing together will be a move to the A X register。Number 5。

I hope you were able to follow along。嗯。And， if not。Try。Rewinding and listen to this once more。

 I think you will get the idea then。Otherwise， you will definitely get the idea when we start coding this thing。

Because then it's not as abstract。As it is， at this point。Okay， so。Program is a sequence of op codes。

Which can be a variable length。So， we need to define。It's not up code。

 It's actually upcodes and arguments， right， because the up cold is just the Ax in this。

 they move A X in this case。Okay， so。Instead of making this a sequence of up codes。We need to make。

Right。We need to make this a secret of instructions。And we need to define what an instructions is。

Instruction is basically a command。To the CPU。So the first part。Will be this。The actual up code。

So well have an up code， oh。And then we will have a variable length。Of arguments。So， let's say as。你。

And this would be an array。With a non predefined size。So， this can be basically。0。うう？0 to 2 B。来首。

We type thes dress。To。And now we only need to define the up code。 and let's make that。E能。So。乐子。

Maybe we should have some kind of table。Which tells。Our virtual machine。How big this instruction is。

 right， Because all those instructions will be of different length。 So we need some kind of table。

T us。嗯。So instead of op code， what should we call that。It will be the actual instruction。

Maybe we should just。N is是林。Let's say， a program。Is。An instruction。Sequence。So。

 instead of singular areas。Instruction。Drection sequence。m。きし。く。2 is an in。

And this will be how we do this development。We will take two steps forward and possibly one step back and then edit some stuff and then move forward again because I'm not sure how to do all this stuff we need to figure it out。

All right， it's so and least now we have an instructions set。An instruction set will be。嗯。

Willll have an instruction。Ae。And arguments A。Possibly arguments a。嗯。Will be。你。St as。

And here we will have it of awkward。But we will also have。诶。See。Am I making this too complicated now。

Maybe we could just pass the up code to a function。

It will look inside the table and tell us how big that instruction is。Yes。

 let's move back a little bit。I hope you bear with me。Okay。

 so a program is a sequence of instructions。An instruction is an up code with impossible arguments。

The old code is an email。六意好好。And we will have a whole lot of these， but。For the time being。

 we will simply have。And I never seem to remember the order of this thing。

 but the compiler will help us。So we will have a move instruction， which will currently be。1。

But then。We will。I will probably change that later on， to match the intel。Specation。But for now。

 it will be one。And。What else we can have a noah。Its。This boat will be two。 and let's start there。

And we will type5 our E norm E of code to just。やか。And now we have all the different building blocks。

 right。So， let's create the table of。Op code。2。Size。So we know how big this thing is。

And how should we do this。See。Let's create。诶。Structure， highlight structures is。え。Is that chill。

So let's call this。Instruction。And it will take off cold。And。A size。So this would be even a。さ。

And possibly we'll have something more in this thing。 But for now， this is enough。Type of。しん。

I will call this I am。SoLet's go down here。Let's create this table。 And this would be a static thing。

So， let's say we do。したて。Yeah。Static I and。E equalals。

And now we will have those different things in here。So first， we will have。Sa。How will we refer this。

 Let's use our Eum。So， this will basically be。O cold door。m。And the size of the move will be。But。But。

没有。3 events。Let's see， let's double check first we have this which defines actual move instruction。

I'm not entirely satisfied that we lose these four bits， but let's do this for now。

And then well have two additional bytes， so three bytes。And we will also have。Oh no。Which will have。

Size of one。This should be possible to do like this， right。来。

Let's try to compile this and see what happens。

![](img/fe8ce403cf7cf58356ce32702c603a81_11.png)

う。アのンタイプ nameオプコれ。

![](img/fe8ce403cf7cf58356ce32702c603a81_13.png)

7。Because we define this。ello。This is 1，2，3，4，5 lines。



![](img/fe8ce403cf7cf58356ce32702c603a81_15.png)

Again， so we do。You jump down a little bit to clear with screen。 you make and。Still some errors。



![](img/fe8ce403cf7cf58356ce32702c603a81_17.png)

An type of art， said my name。 It's always a little bit。Difficult to put this。

 these ones in the correct order。 Okay， we haven't even defined those as。 Let's do that。And what is。

An argument， S vlar is。Well， it's basically。Yeah。See。A sequence of。Bys。So。他自己看也对。嗯备。



![](img/fe8ce403cf7cf58356ce32702c603a81_19.png)

So we make clean， we jump down a little bit to clear the screen。ねと。嗯。Okay， it didn。

 It didn't like our。Minus thing there。

![](img/fe8ce403cf7cf58356ce32702c603a81_21.png)

嗯。Let me just try one other thing， before we。Before we fold， so to speak。

If we put this inside of the parenthees。And before this， we do。And in this。put the whole thing。

Inside of。错了。All right， if it works。

![](img/fe8ce403cf7cf58356ce32702c603a81_23.png)

It would probably work this year。It seems like it did， isn't he a beautiful language？😊，All right。

 what does it say here， braces around Scalar initializer？Okay，97。



![](img/fe8ce403cf7cf58356ce32702c603a81_25.png)

Okay， so static， I am。Instrument equals this。 Okayk， doesn't like being pointer。 What if。ち中。Yes。



![](img/fe8ce403cf7cf58356ce32702c603a81_27.png)

Okay。Now we talk it。Okay， we can do up code dot move。



![](img/fe8ce403cf7cf58356ce32702c603a81_29.png)

Mmm。How do we reference， though。Genums， I never really learned how to use genomes。

Let's see Eum E up code。 And we typed if this as up code。

Do we need to create an instance and reference that？Or can we do E up code do。Think。Let's try that。

 first。二。可。嗯嗯。

![](img/fe8ce403cf7cf58356ce32702c603a81_31.png)

No。Can't do that either。

![](img/fe8ce403cf7cf58356ce32702c603a81_33.png)

That's a little bit annoying。So。What use do we have of these actual enums。嗯。So we have Eum。

 the up code contains this thing。Do we need to create an instance then。T that。So if you do study。嗯。

P good。mm。Sure how to do this。Yes这是。回。Right， either。う。



![](img/fe8ce403cf7cf58356ce32702c603a81_35.png)

Let's try it again， at least。Request for member。Move in something。Not a structure。



![](img/fe8ce403cf7cf58356ce32702c603a81_37.png)

我有你。Because。😔，Op code is defined as。Eum E of code。Isn't the whole point。

That we should be able to reference it。えっと。I will consult Google， I think， in this case。

Google and check see Juion。 No Juveion。 wait a second。You say union。

Only now or did I actually know it you。那。B floor。Cリの。Oh， the annoying papa。Okay， so inner level。

Me un level my bar。In a level， my bar equals something。And then we can access my v。

Andm in a switch statement in minimum level， my var equals medium。Kay。Maybe we can just。健全すてぜ。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_39.png)

Instrument defined， but not used， Up code， defined， but not used， O。We are。



![](img/fe8ce403cf7cf58356ce32702c603a81_41.png)

Alive and kicking， ladies and gentlemen。Wasn't this kind of beautiful。



![](img/fe8ce403cf7cf58356ce32702c603a81_43.png)

I think it's beautiful。Right。So let's make this code look a little bit better as well。That's。Tother。

Yes。This one thing。There。Together。オケ。together。We have other type de。嗯。客服。Isn't this really。

 really beautiful？So strap as V M。 And then we have that。 Let's move this together。

And now we have something。Okay， let's make a constructor function for creating a virtual。旅行。So。

What shall we call this。mm。嗯。It will return。OfThe end。A pointer to the end。And let's call it。Virtual。

美しい。Right。And we don't need to give it any arguments， because this would just create an empty thing。

Alright。So let's define this function。嗯。しを。She need。And no arguments。We will have a V M。

Po to the end。We will also have a。Sイize？The size will be equal to。Size of a struck。Yeah。

And the P will be equal to。VM cast it。Mi localical。And we will send the integer value of size。

And we can。Sir。死皮。O no。Make this a little bit more。Portable， I think。嗯。嗯。So if we don't。一。

What shall we do。Maybe we should do something like accept the error number， to。Some constant。Maybe。

No。嗯。What just airmen。And then we will see。Turn of the。日了。So let's create this error thing。水分。Iffin。

没有。M。诶。0 work。And can we think of any other errors at this point， creating an empty virtual machine。

Probably not right。Okay， so what do we do next。We will zero out this thing。Probably0 anyway。

 but let's make sure。So， we will send。In a。Cated。皮。30。So now we have zero left here。

But we need to do some more steps， right。So let's see what we have currently。嗯。This is what we have。

So the CPU is probably not much we need to do。Let's see， where do we have the CPU？😔，Right here。

 it has a couple of registers。And all of those will be zero from start， which is fine。All right。

 so that's nothing we need to do about。Eventually we have a stack。And what is the stack？It's 65 K of。

But。And that is。Also。Not anything we need to。Do。The program， however。There， we need to allocate。

Maybe we should supply the program。To the constructor， instead。I think。So it'll take one argument。

 which is a program。Or rather a appropriate point to the program。Let's go in here and we say program。

PR。And。What shall we do with this program。You need the size of that program， as well。So， let's see。

St。No sizes。Already use。Let's call this。W， let's call this。Program。

And let's not forget to update our。嗯。Signature。So this will be again 60。

And we could just use this pointer and put it inside of our str。But we don't know really what is。

 this is coming from。 Perhaps this is something of a stack in a function somewhere。

 And then when the function terminates， this memory thing will probably not be available。

So the program should be copied to a safe place， right？So。Let's。

 let's do some sanity checks in the beginning。 by the way， Let's assert two things。

Let's assert that We have a program。And that we have。The size， which is like0。

That is basically all we need， right？嗯。嗯。Alright， so at this point， we can。都。Pilgram pointer。So。Po灯。

And we will allocate the necessary size。Which basically will be P。Equals。个。ぶ。In analogo。

 we send an integer of the program size。We don't have a program pointer。We will。3ree。Oh。

Virtual machine。With an error number 2。M again。And would return a virtual machine cast in ce。

If we do have。At P P， we want to copy that program。So。There is a manme copy。等你。

But it would be kind of interesting to write our own， right。So， let's just call this copy。

And the destination。Will be our program pointer。The source will be。This program， here。

And the size will be programmed。And now we are。Ready to。Return this P。

But we need to make this copy function。嗯。I don't think I want to put this inside of this project。

This is a function which will probably be used many times。

So let's put it inside of birch u tills instead。So， let's go to sociopath。



![](img/fe8ce403cf7cf58356ce32702c603a81_45.png)

And our cold and virtious。Let's open this to in editor。



![](img/fe8ce403cf7cf58356ce32702c603a81_47.png)

Let's see。 I will simply do。对。I will take this whole thing and put it inside of here。😔。

Can close this one。And now we have access to the bird jus。So let's see。 let's。

 before we do any changes， let's modify our make fight。So， we are using。The latest version。

 unless we can do this。Let's see。Let's make。そで。And comment out one of them。BeWithout this。し？

Birch VM will depend。嗯。No。Hung。Co。You do slash。🤧。You。哦。こですね。And。You probably need to put it here。

 right。So， let's。You only need。First。alsoに。Because I want this to be automatic。

 I don't want to go and manually compile。Birs you all the time。So， this depends on。やつです。Change thisす。

死。うです。8。う。So what do we want to do with this？We w to save our current working directory。So。

 let's say。个人。Working directory is equal to。嗯。😊，How do we do this。I think we could just do。

Not really sure。How do we execute。How do we exit， maybe we just。No sure actually。Because I want to。

No let's just do this。Equal to PVD。Then we see D in2。To this pathth。嗯。CD into this path。We want make。

And we return to the saved。To the saved。Working director。Will this work。



![](img/fe8ce403cf7cf58356ce32702c603a81_49.png)

I'm not very used to this kind of multile level make file。嗯。E first。Conversion from long。

 outside in to insect。T， okay， I have never seen。Size of complaining before。That's interesting。

 That must be because I have the newest， newest GCC。 this will probably not。



![](img/fe8ce403cf7cf58356ce32702c603a81_51.png)

Be in your。Environment。Let's see do do do。To。So。Where did we reference the size of。ItHere。So。

 let's make this。16 with size of。

![](img/fe8ce403cf7cf58356ce32702c603a81_53.png)

All right。And what else the copy， it complains about the copy， but we haven't created that yet， so。



![](img/fe8ce403cf7cf58356ce32702c603a81_55.png)

That's okay。Let's remove it。

![](img/fe8ce403cf7cf58356ce32702c603a81_57.png)

What else。Define but not used。 Define， but not used。 I don't care。 Why do we get an error。 Oh。

 here is something。PR size。Unecclared right， pro size， not PR size。



![](img/fe8ce403cf7cf58356ce32702c603a81_59.png)

Fさ。

![](img/fe8ce403cf7cf58356ce32702c603a81_61.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_62.png)

嗯。原来 say。Pro。😔，Sa。

![](img/fe8ce403cf7cf58356ce32702c603a81_64.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_65.png)

Something wrong with this， no。It did update。 Is this another。Another line， perhaps。8。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_67.png)

As well。And now， I think it should compile。Yes。And what if we make an alteration。



![](img/fe8ce403cf7cf58356ce32702c603a81_69.png)

Into the biles。Let's just。るスペ。Not sure if that's enough， but I think so。



![](img/fe8ce403cf7cf58356ce32702c603a81_71.png)

And。If this works， it should recompile。嗯。The virtue of this。Okay， that's quite a loop there， guys。

 I have never seen anything like that。😊。

![](img/fe8ce403cf7cf58356ce32702c603a81_73.png)

How is that possible， okay。Let's check out this big file。

So what I would do and we run in May inside of that directory。sDouble check the dependence。

So in order to make this dot O。We need that C file。It will at age5。And then we can deal。

And in order to make ver V M。You need that哦。So why does it live。Let's do something like。



![](img/fe8ce403cf7cf58356ce32702c603a81_75.png)

Are able to see what's happening。Make。Okay， I didn't really do anything。up。



![](img/fe8ce403cf7cf58356ce32702c603a81_77.png)

つまらせて。嗯。Okay， perhaps it's because we run the cl， but no。



![](img/fe8ce403cf7cf58356ce32702c603a81_79.png)

What happens if we do this。せて。K， this is an unusual type of error。What's happen entering directory。

You said this。We see the to that we make。Okay， maybe。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_81.png)

What if we were to change this to。没。理由て。No。What would happen then。



![](img/fe8ce403cf7cf58356ce32702c603a81_83.png)

人家。录音度。Noルるね。Okay， that's better。So we go into virtue dealss。No rule to make pursuit stop oh。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_85.png)

Maybe we need the entire。Yeah。Do it really。What if we were。

Maybe it would make is smart enough to understand。If we just did。If we just did。佢为咩？

P you tills start oh， but we just。M兄弟。

![](img/fe8ce403cf7cf58356ce32702c603a81_87.png)

Entire path right there。What happens then？

![](img/fe8ce403cf7cf58356ce32702c603a81_89.png)

水。駅？And we loop again， yay。A directories。Let's just do a simple Google。嗯。お。嗯。

Do all those annoying popups。 Why don't they make a pop up blocker that deals with the new kinds of popups。

Do。C， D， blah， blah， blah， and me。嗯。In。いです。By the way， this should also be inside。This is。

Let's try this solution。

![](img/fe8ce403cf7cf58356ce32702c603a81_91.png)

Sle jumped on a little bit because there the ski。べ。Cant city。



![](img/fe8ce403cf7cf58356ce32702c603a81_93.png)

It's a little bit tough to seed into an object file， right？Rookie mistake。Shame on you。

 Doctor the birch。

![](img/fe8ce403cf7cf58356ce32702c603a81_95.png)

Clean， jump down a little bit。 clear the screen。 We run make and。



![](img/fe8ce403cf7cf58356ce32702c603a81_97.png)

Those works。It recompiled。Our birth tus。And。It used that in order to link this thing。Great。

 thank you， Internet。I had to break my no Google rule in order to fix this， but。

It's all for a good cause， right？All right， so let's see。We have virtue till do see。

 Let's put it there and make fact we don't bleed。Let's also open the old file。And。As I usually do。

 I will update this version number。So both you and I had a little bit more。Knowledge， right。

About which version were dealing with。And let's see we will create a copy function。

 So a new section of character C。I have made those labels for the different starting character of the function。

Because this will probably be a lot of functions in a couple of years， right？Alright。

 so we'll have a void copy。Which will take。Avoid pointer， or maybe。

Maybe it will be easier to do it in date。This is the source。 This is the destination。And。

And should it make it for bigger sizes than in16， I don't know， but let's not at this point。

 it least， it's very easy to change。嗯。Alright， so how do we make our own memory copy function。

Shouldn't be too hard， I guess I've never done this， but。Let's see。So coffee， and have。So。

 we a destination。It will have a source。在。And what do we need， We need a pointer。P。We need。T and。

The for loop。So we set n equal to。Size。We said P equal to the。worst。Right。Maybe we need two pointers。

Excogen。そしてねし。Source。So our destination pointer will be equal to。

Nation that our source pointer will be equal to the source。That's our starting point。

We're going to loop as long as N is enough0。And at each iteration， we are going to decrease and。

Were gonna increase the， and we're gonna increase。And what are we going to do at each？😔，Lieration。

Well， we're going to set。The destination， current destination by。Equal to。そすか。有的区别。Oh， you do。



![](img/fe8ce403cf7cf58356ce32702c603a81_99.png)

Pesting。你全到。诶。And this is a little bit annoying。 the as printer function in this case。

Is not truncating anything。So。嗯。I want to get rid of this。Message。

And I never seem to remember how to do the。I have some example in my code somewhere。Where。

Let's go into my。ho。と 비투이。和物品。Let's search for。P。だって先ラ。是吧。Okay。

 maybe we should just search the C files。Or H5 is rather。So。And。H file。喺我嚟。You。G。Based on the。嗯。

Do we need to escape those I never。Remember。嗯。生死你。this I guess。All right。

 but we didn't get the name of the file。オッケー？So， let's go。Search file and some other file。

 just to get the。Alright， Cat 22。 see。 there we have it。Thing and we have。

 where do we get Here it is。And then， we have a。听唔多少。妹被心帅了你。Yeah。



![](img/fe8ce403cf7cf58356ce32702c603a81_101.png)

O。Make sense。Let's go into our virtual teams。And add a couple more problems。And the truation is。

get rid of， let's know this。 And know I am right here。The end of the。C file。売って。



![](img/fe8ce403cf7cf58356ce32702c603a81_103.png)

We say this。です。And let。くい。没有。Okay。That's a little bit easier on the eyes， right。

A little bit easier on the eyes。

![](img/fe8ce403cf7cf58356ce32702c603a81_105.png)

。

![](img/fe8ce403cf7cf58356ce32702c603a81_107.png)

Yeah。All right， welcome back， you guys。So what's next。We have。

 we are able to create one of these things。Use our copy function。And maybe we should try this out。

 So we know that it will crash。 and maybe， or probably it will crash since。Memory operations always。

 or at least many times result in a s fault before you have。Fix it。That's the ugly truth。

 But I think it will work。Out of the box。So， let's create a。VM。Yeah。And the PM will be equal to。中行。

And we need a program。And what is the program。Somethinging like。Yeah， what is the program。

Program program program。Where do we have the program。Program， show your face。

 Here you are type of instruction， All right， justs a sequence of instructions。😔。

Instruction is this kind of thing， up code and our。are。So， let's see。うふふ。Let's say。

 we have a program。我觉。It should be equal to。WellLet's do。Program。B。Yeah。Prorog will be equal to。Sle。

A little bit。More structured approach。This is a program。こ。Avoid。

And since this is an example thing which should not be in the production code。

 I would just make a little space here。Which will make it very easy to differentiate later on。

Those small little hints。Are very useful， I believe。So， a program。え？Pointer to our example program。

 with no arguments。And how do we define this， Let's do static。对对。可。Or it needs to be a sequence。てるやつ。

We can't do that。And。What's in here。嗯。So。First， we have the up code。哦。So， the O equals。

And I think we can just move， right。What's the next part。It's the argument。So。A is。Another。Aray。

Which would be a sequence of bites。So， let's say， we move the。LetSee。We want to move。

A5 into the E X register。That means that the。First by will be 0。The second I could be5。

The lefts have one more。So， this is our first。Iの。Maybe we need to do。More level。 I'm not really sure。

 I usually don't go this way， but。I think。Good位。So if we have this additional level。

You should be able to do。And this time， the O will be equal to a noer。And the a will be equal to。No。

 I。So let's define a constant like that。This is where the line ends。And then们 see。Thirdd。真体旋。

Correct in mannerer might be wrong。I might indeed be wrong。So let's see what what of no as。So。Next。

No eggss。To be。It should be a zero row。But it should be a 16 bit。0。

So how to express that correctly in C。I think we have to do。Okay， so when we have the。

Wech the machine。Or maybe we should start with the program。Let's print of。The pointers so we see。

Does it returns correctly。And this is。Well。And let's do the same for the V。语人。で space。And then。30。

Alright， let's see what kind of errors we get， Because I sense we will get some。



![](img/fe8ce403cf7cf58356ce32702c603a81_109.png)

It's very clean。 Let's move down a little bit。 clear the screen boom。And so got。

Implicit declaration of copy。

![](img/fe8ce403cf7cf58356ce32702c603a81_111.png)

And that is because we are including the wrong vitous age， I believe。Old version。Yes， yes， yes。So。

 maybe we should。嗯嗯。If we do this。And we alter our make file a tiny bit。So。You know。

 this is a road make file。This is the one。So we add a flag， and let's not do C2 X， by the way。

 now in the latest version of GCC。

![](img/fe8ce403cf7cf58356ce32702c603a81_113.png)

Which is。嗯。No， I have the old version on this machine， Bummer。



![](img/fe8ce403cf7cf58356ce32702c603a81_115.png)

Never would。Let's add。Flag， and I think it's big eye for include director。So， let's。

Select this directory。对So。

![](img/fe8ce403cf7cf58356ce32702c603a81_117.png)

AndNo， I think at least that error。To be wrong I ought to be way gone。Yeses。Is good。

But it does like our argument types。

![](img/fe8ce403cf7cf58356ce32702c603a81_119.png)

Which is sun。So lets say。Here we make it too。年哋。So let's do the same here。

 Everything is a sequence of bytes， right？So， let's。One。Is also a one by thing。



![](img/fe8ce403cf7cf58356ce32702c603a81_121.png)

And one error should be done。Okay， initialization of flexible array member in a neststead。Co的。

What does it mean。Initialization of a of flexible array member。In an nest context。



![](img/fe8ce403cf7cf58356ce32702c603a81_123.png)

And that should be something wrong that we have it in a nested context。嗯。Because this program。Is。

It is basically an area instruction。An instruction。 That is a structure。Which has an0 and A。

So it's a structure， which has an O。有啲你气。Okay， maybe we shouldn't make this into this layer。

What if were just going to do。It doesn't feel right， either， does it。Right， at least。



![](img/fe8ce403cf7cf58356ce32702c603a81_125.png)

We are。Exploring new territory。To be personally。Feel name。Not in record。hold union。



![](img/fe8ce403cf7cf58356ce32702c603a81_127.png)

Good。B。No， we do need the additional layer。But why doesn't it。

Because this is the first thing in the array， right。This is structure。嗯。

Because if we were to just do one instruction。嗯。Instruction， I is equal。对哦。Move。With a is。0。fi。

And this will be the whole thing。But now， we are doing。Several of those。So， basically。对。系。Well。こなで。

And isn't this pretty much。What we've done。Sttic program progue equals。What if we were to do。

Call this。お。Will that make a difference。呃能去我。😔，I haven't really explored these new C functions。

 which is。

![](img/fe8ce403cf7cf58356ce32702c603a81_129.png)

Flexible。Initiallyized se and stuff。Nization of flexible array in a nested context。Okay。

 now it's just complaining on this。

![](img/fe8ce403cf7cf58356ce32702c603a81_131.png)

Okay， well， I didn't remove the example later。No， I did not。But， this seem to be working。

Until this point。And what is a。A is。어 이 어。Can that be it。This is。Unfined size。

So we can't probably do it like this。That's right。Makes sense。So let's。Do this differently。Yes。

What do we need to do instead。We will still have a program。Prove。And。

The program will have several of these instruction。

 and it's an instruction that we need to allocate properly。就。We could。Program。确实。An array of two。

And then we can do something like instruction。 I won。嗯。2。嗯。I won。Will be equal to。

And we need to allocate for this。But how much do we need to allocate。嗯。1 in6。

In order to figure that out， we need to use our。Instruction upright。

 This tells us how big the different things are。So。We need some kind of a function。Returns the size。

Let's call this。That's just cool。For now。And what it will take is。The type of instruction。

In this case， it's a move instruction。And then we have the size。So， now we can。Declare this。

Initialize this thing。你 this should be。Construction castage。Vopical of the integer of size。

If we don't have one of those。We simply。No， let's。Keep the same。Structure。

So we will send the error number to。And then。Turned。Program of。这。你的。喂 will。可。They。To long once again。

This time， with a。No instruction。AndThis will be I2。2。And now we have our two instructions。

So I'm not sure if this is correct syntax， but let's try。Can we do program equals。

And now it should just be equal to I1， I2。Greatight work。嗯。And then we will return。多分？Alright。

 something like that。 Let's see what the GCC says。

![](img/fe8ce403cf7cf58356ce32702c603a81_133.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_134.png)

Okay， we don't have the math function。 That is very， very true。Also， true。嗯。

But that should be easy enough to remedy， right。So。The mathfunction。It will return。At is 16。

And it will take。Yeah， what do it take。ううです。Is it an instruction or is it an op code。

It's an up quote。So。嗯。哦一哦。just of。And we need to create the function。So。6ティ。一せつの？哦。And we have。嗯。语人。

And we need to search this map。俾士。来。し？Yeah， let's do this properly。Let's create。

We need a pointer to an。爱。Yeah。And we need the size。Of the iron or the number of。The number of。

Instructions。So， let's say we have。Let's make it constant to make things easier。I am。あず。Size of。

When I am。And an I am is astruct。就是的。So this is one entry。嗯。You need to take， let's。

We need to take the size of the entire instruction。So。Size of。D。And we did buy the。By size of。なドです。

And then we should have the numbers。Number O。Right。I think this is okay。

And let's make it a one liner， so we don't have to do all of these。Okay， this makes。So。

 this makes our lives a little bit easier。So， let's divide the duties。嗯。red。And we need。哎。Inter。嗯。

So we do a four loop where we set n equal to。系啊。你是 P。First。Entry。We live as long as Annies。

0 and at date straight duration， we do F minus minus MP plus。Let's set the red。0。And it it we check。

If。He。What's the for it。Find the deflation of。么。😔，Okay， so we have O， and we have。サイズ？練し。

Cose S instead。And that's an int A。オッケー。嗯。よ。P。哦哦。It's equal to oh。That's our。

Argument parameter to the function。If those are the same。We will set。没没有。Se equal to。He says。

The break。And。At the end here。Third。So it's either zero。It fails。Or it has。I love very。

I think this should work。We need to update our signature， though。呢啲。Bits。

8 Bs off to be enough for everyone， right。It is now we have our math。Sure。Let's see if it compiles。



![](img/fe8ce403cf7cf58356ce32702c603a81_136.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_137.png)

Almost。Pgue， okay， It didn't like this。Syntax。If I'm not entirely。

Out and riding a bicycle as we stay in Sweden in a suburb。I think we can do this Javava scripts。

 like syntax。来了你。

![](img/fe8ce403cf7cf58356ce32702c603a81_139.png)

I'm not sure。嗯。嗯。Let's see what happens。Nope， it didn't like that either。



![](img/fe8ce403cf7cf58356ce32702c603a81_141.png)

But I think one of these is is okay， but only at declaration。Which is pretty annoying。

We will have to do。This。As you all know by now， I loathe。Declaring variables， and giving them。

Content of the same line。 and I don't like at all。To。

Declare variables like this everywhere in the code。But， I guess， we can have。

I want to see if this works。

![](img/fe8ce403cf7cf58356ce32702c603a81_143.png)

Or fun。 still riding the bicycle。

![](img/fe8ce403cf7cf58356ce32702c603a81_145.png)

Yes， I am。Traampmppoling。对。对。It probably work fine， I guess。



![](img/fe8ce403cf7cf58356ce32702c603a81_147.png)

Incomp types， when initializing。

![](img/fe8ce403cf7cf58356ce32702c603a81_149.png)

Kay。Yes。Probably。Because we need them to be pointer。See。

Who said coding your own virtual machine should be easy， right， We should expect to。

Drive our heads into the wall， sometimes。Another Swedish proverb， by the way。Okay， so registers。Cold。

The instruction。It's not a point。But since it contains this， we need the mail look for it。So。

Instructions should be。Poiner by the。

![](img/fe8ce403cf7cf58356ce32702c603a81_151.png)

嗯，我也没。jumpump down a little bit， share the screen。We will make and boom。Oh， even more errors。

Types of stroke。

![](img/fe8ce403cf7cf58356ce32702c603a81_153.png)

Okay。Star wrong。去理。Yeah， where should it be。St as。 it should probably be here， right。Maybe。

Maybe does matter it。 This looks better。

![](img/fe8ce403cf7cf58356ce32702c603a81_155.png)

So we make it to jump down a little bit there。嗯。From incomparable pointer type。

 struck as instruction。Double star。

![](img/fe8ce403cf7cf58356ce32702c603a81_157.png)

Because now we don't need to do cast anymore。Since we are already dealing with pointers。😔，你啦咪。嗯。

Program pro。In to this。Is this right。Yeah对。

![](img/fe8ce403cf7cf58356ce32702c603a81_159.png)

Seems a little bit。Initialization from incompatible point of type strap as instruction。

 doublele star。Program pro equals。I won。

![](img/fe8ce403cf7cf58356ce32702c603a81_161.png)

How did I define I1 and I 2， I made those points。That should not be。



![](img/fe8ce403cf7cf58356ce32702c603a81_163.png)

嗯。嗯嗯。Still， it says struck double star。嗯嗯。

![](img/fe8ce403cf7cf58356ce32702c603a81_165.png)

We need to change all this stuff at so many places。とてし。St there in the。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_167.png)

Okay， we're down to one screen。Exs elements in Scalar initializer。It。可以。Because three分。This。



![](img/fe8ce403cf7cf58356ce32702c603a81_169.png)

Returning program。Instruct this instruction star。From a function with income， Ok。

 the return type needs to be altered。Well。Cha this。And。And probably。The literature is program。

You that's。Let's try。We。Since it will be a pointer anyway。 So just。Well。We call this。Do。

 and then we could。From。

![](img/fe8ce403cf7cf58356ce32702c603a81_171.png)

Let's see what it says now。First， error will probably。有。嗯。うスです。



![](img/fe8ce403cf7cf58356ce32702c603a81_173.png)

知。VN。

![](img/fe8ce403cf7cf58356ce32702c603a81_175.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_176.png)

没异。Maybe I should just search for all the stars and remove them entirely。

This is getting a little bit tedious， to be honest。



![](img/fe8ce403cf7cf58356ce32702c603a81_178.png)

But that's programming。

![](img/fe8ce403cf7cf58356ce32702c603a81_180.png)

52。你。You is know。

![](img/fe8ce403cf7cf58356ce32702c603a81_182.png)

You don' to one。screenreeen again。😔，A sudden stress me un double star。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_184.png)

P， P， where do we have P， P。reallyally。Search for all the programs。Make sure。

We don't have any stars anywhere。

![](img/fe8ce403cf7cf58356ce32702c603a81_186.png)

Okay， let's see what happens。Okay， this is something weird。

There are too few arguments to function virtual machine， right， we alter that signature， didn't we。



![](img/fe8ce403cf7cf58356ce32702c603a81_188.png)

We added。The program size to it。But we have that right here。Maybe it's the call。

Where do I call this virtual machine， It's not a main。所以呢就。I need to define。How many。Instructions。

It is。What is the program sizes。Let's see。Sorry for my cat it's going crazy。Let's see program size。

 we use program size。To aloque。以后。Program。All right。So， basically， it should be。

The size of this example program。Let this returns the pointer。嗯。Yes， it returns this pointer。

 so we will not really be able to。Figure out。嗯。But we can use our map。So。

 let's do something like this。A size。And。So。いく。The matter of moon。Plus。哦。No。

That's the unnecessary parentheses。And then when we call our new。Virtual machine。

So the size alone for the right。CompP this thing。 And okay， this time it did comply。

 But we still without this annoying。R。What's the world rather。Let's see。 Where do we go。Format tru。

I had that。嗯。Cold。Let's see。 Where should we in。Where did I put with them。P it here。Stng， string。

Do need to have this stuff inside of。take care of it。Id， blah， blah， blah。Let's see what happens。

Inside of our other thing as well。So， inside of here。什么人。You baby。And then， we need。嗯。

Need this at the end here。But it should not be pushed it should。好。

Did I put in this pop thing here as well， No， it's a push okay。So we say this。てうです。そいです。Sa。



![](img/fe8ce403cf7cf58356ce32702c603a81_190.png)

So， we do。Please jump down a little bit you clearance screened。It comps。

 but we still got the warning， but I don't really want to deal with that right now。🎼It did get this。

We do get， too。We do get a program and we use it to create a virtual machine。 ladies and gentlemen。

 we have succeeded with today's task。

![](img/fe8ce403cf7cf58356ce32702c603a81_192.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_193.png)

Did you learn anything useful today day， And you want to support this channel。

Go to Doctor Birrch dot com flashlash support。 You can also click the button， Bee a member。

 Thank you for your support。

![](img/fe8ce403cf7cf58356ce32702c603a81_195.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_196.png)

Alright， guys。 welcomee back。And now I have gotten a night's sleep。



![](img/fe8ce403cf7cf58356ce32702c603a81_198.png)

And I have decided to change up a couple of things with our virtual machine。

Because I don't want to utilize。The heap， the way I have done it this far。

 So if we look at this instruction， for example。This is good in itself。But， I'm not comfortable。

With how I use。Let's see。 the program。Where do we have the program data type？😔。

Maybe I should put these in。Alphabetical order or something。Let's see。 We have itemss。 We have。

I can search。I don't。 I like being able to find it without searching， but never mind。 All right。

 so at the moment， we define program as a。series of instructions。

An instruction is basically a pointer to this structure。So I don't want it to be。

 let's stop being a pointer， so we're going to refactor our code。To use a new expression。And。

The program is not gonna be。Well， it's going to be。A series of instruction。Yeah in the end。

 so to speak。But。At the abstraction layer， I only wanted to be a string of but。So basically。

 a pointer to a program is just a pointer to a string of bites。

And then we can put our instructions in there manually。😔，Using our copy function。

I think that is a much cleaner solution。 Plus， we will be able to。

We will be able to utilize our own stack for that， or at least our own memory。

 That's one more thing I need to change。This here， the virtual machine has a stack。In this case。Well。

 it's going to have a stack for sure。But I don't want this to be just a stack。 I want this to be。

Memory。Because I'm going to divide this by a stack or a data segment and a text segment for the code。

So in this。Instance， this will just be a memory。And。When we have a memory。We can define。A stack。As a。

See。Let's define。The memoryory。Pointer。To be is there。Thats。How I like it I。死。Yeah。

 let's keep it like that for now。We'll see if we do any additional changes。 Alright。

 so now that we have a string of bys instead of。Instead of。Well， basically an array of instructions。

We need to change a couple of things。嗯。So let's see if we look at the map function。

 nothing things is changed。😔，The version machine， on the other hand， the program will be a pointer。

Which is basically just a string of bites。I put it。え。Program。Yes， string us indeed。So， let's see。 P。

 P will also be。m。How are we using P at the moment？😔，We are me looking。Right。Okay， so P。

 P will also be a pointer。And let's search for。And。Byer。P屁。我儿。嗯。What was the input。Value。

Very difficult to see when it highlights this way。😔，嗯 PR。So let's search for those two。

 We assert that we have a PR。的。Since。Next， we are locate。The program， which is just。水 red。

We should得 okay。And then， we copy。the yeah， we cop the entire program。We don't need to cast。

That is the only difference， I suppose。And that's all for this function。

Then we have our example program， and this will be very different。

 So I actually think I'm going to delete the whole thing。来声。Before we rewrite that1， I will。退出击。So。

 let's search for drugs。Will be the example program。 And then we'll simply， yeah。Okay。

 so the only thing we need to completely rewrite is the example program。thhing。

Which now will return the stringinggabytes。So， let's define this as a program。An example。

And let's create。嗯嗯。See。How do we do this in the best possible way。Maybe。Yeah， let's do it。

Similar to how we did it before， we will create the instructions。Iワ。はい2。Instruction。

We find it in the code so we can look at it while we write it。Here it is。

So an instruction is basically this structure then， an upcode and possible arguments。嗯。So。

 let's also do。We need to know the size of these specific optical instructions。

So let's create that in 16 S1 and S2 for the two sizes。And let's also create。Well。Argument。

We have this or thing。Let's use it。So， we'll create an a。A1。A2。嗯。We need to make those two corridors。

嗯。All right。Or actually， we don't need the A2 because it doesn't have any arguments。

But the first one does。And we also need to create the actual program that we're going be to return。

Let's call this probe。And let's start by allocating that。No， let's not。 By the way。

 let's start with instructions。So the first instruction I won。Will it be。你怎么了？

We get an integer of size1。The same thing for size too。 So we need to first。Get those sizes。

And that's pretty easy。 We just call our map function， and we supply the op code move in this case。

And in this case。no啊。Okay， so now we have room for these instructions。So， let's say。I won。

And let's see the best way of。Doing the。嗯嗯嗯嗯。Well， we could just do that。Those。

So I1 or not right right that we need to do I1， and then。哦。一口。Move。And what about the arguments。

The arguments we do also need to allocate for。嗯。Or maybe we could just make this an array in this case。

No。We need to know how big the arguments are。So let's make this dynamic。 Sorry from the to and throw。

 to and fro。But I have never coded anything like this before。 So it's a little bit。Two steps f。

Forward and one step back。But you're learning same as I am right now。

 so I think it's a good approach。Okay。So move instruction， we need to figure out。

How big the argument is。So let's create another size variable。 But this time it's going to be these。

 the size of argument。 So S a。And that's pretty simple to calculate since all our instructions is going to be one bite on its own。

Which means that。え？Will be equal to。え。The S1。冷算。So the rest of this thing is the arguments。Alright。

 so let's。え这。S1 is0。It is not 0。 And if it's not。We will proceed with。Yeah。Aoc for the argument。So。

 let's see。We will have。A文。ToBe equal to or。哦。诶。没了。Into their canvas。And。问。This should also be S A 1。

Okay， now Ive allocated。Space for the arguments。It's also by the。S out those。

This will be cast to an in the8。And I will。And we wanted to have a size of。Thank you do this。We do。N。

 too， it is to。Okay， now they are zeroed。 I do also want to zero out this a1。Let's。

Check that we do have an a1， though。And if we don't。We would like to。

 since this is an example program， let's just assert a one。The same here。Before we do the zeroing。

Yes a Sir。I will。We will not use this in production code。

 but it's good when we're doing these kind of example functions。And case with this。う。Ohl this thing。

I think we need to cast this。诶。And this is a world。And we have the size of S1。Okay。

 so let's start with the argument， if you remember。We have the instruction。Which is。B long。

And that will be the move。い。Part of it。So if you remember。

 this one means that it's a move instruction and these other three bytes means that it's into the EAC。

And possibly， that it's a。A number that we're going to。Give it as a second argument。

And not another register or member address also so。And then， we have。Two more bys。Of arguments。

And all we want to give this is。5。Which will basically be。So it's smooth A。05， right。嗯。

So these two bitetes need to be put inside of this arguments thing。Let's， by the way， assert。No不。

Let's see。In our case。We will have two bikes。The first by being a one。So， let's say。A文。0。That is。

And then， we have a。A 1， plus1。And we will set this。The发。And this is。Our arguments today。

So now we're done with that。😔，Now well do the instruction。

 and we have already allocated and zero that out。And we have actually already said it as well。

 So all we need to do now is。Copy this to our program。And did we allocate our program yet？So， no。

 because we did not know how。Big it should be。And we do know， though， because。We do have。 let's see。

 We do have these S1 and S2。 So we know the sizes of both。え。So， let's。3 a。It's a lot variable snow。

I think it makes the code a little bit easier to understand PS will be the program size。😔。

And the program size would simply be。It sizes 1 plus size 2。Is it。program with be。Program。

And we now like this。It's a lot of malllos。 Didn't I say I would not use Malo。We can use my look。

 by the way。For these temporary arguments。And hour。Instructions。But the program。

The programme I want to be。On the step。In the memory。How do we achieve that in a good way。

Because we need to。Well。We could give。No， this is a little problem。We use our function to create。

Virtual machine， right。Or a virtual machine needs a program。As an argument。But。We kinda need。

The other way round， too。So they are dependent on each other there。 That's not really。Good。嗯。嗯。Maybe。

It makes sense。To。Not give the program to the virtual machine construct。Let it just create。

An empty program。 And then， we will have。A specific function which will load the program into the virtual machine。

That's better。Which means we do not need this。皮皮。So what is this P。That's the me machine itself。

 All right。So let's just， let's comment this out for now。Soう。And I was also。皮丁。And I will not give。

The program。Or a program size。To the virtual machine。So certain this should be。Size equals。

Deciive diverse version of machine。We should serial the virtual machine。But。

That's where we can leave it。So we say rather virtual machine that we return it。

 So it's an empty virtual machine without any program。Okay， so if we do it this way。

 then to our example program， we can give an argument of a V。啲啊。

And let's update the signatures before we forget。This should be empty。

And the example program should take a PMM。2 steps forward， one step back， right。

 But I think this will be a good。Good way。 Because if we give this。

Example program a virtual machine as an argument。Yeah。Then we do not need this。Program。Saing。

And we do not need。Program， we do need the program size， though。Or maybe no， yeah， believe。

But will not mall up this。And。We will simply。Use。The stack。

 basically or the memory inside of the virtual machine。We need a pointer， though， to this。Program。So。

 let's do a。Let's do a program here anyway。う。And this。P be equal to。In the end。呃。Memory。

Did we call it M or memory or what。え。Memory。Memory and memory is this 65 king， All right。

So we point this towards that， and this is where we will copy our stuff。

So let's copy this first instruction and its arguments。So， let's do a copy towards our。He。carで。

To our repeat， which is pointing towards。How to speak， how to call it。The top of the memory。

 I suppose。Or the bottom， depending on how you watch it。And what are we going to copy it。

 We are going to copy the instruction。Which is。I want。I won。And I won。Is。我为网。エクセスいーせ。

They we increase tea。we科对。ピピ exposition。This time， we take the arguments， a1。This as well。

And what's the size of the argument and essay1， right？Which means we're going to increase P by S1。

So now it's pointing to the next point。Of the stack。Okay， that's instruction number one。

The second will be much easier。Since it's only the up code， basically。So let's see how we did this。

 We calculate that this size， we allocate。This。So basically， all we need to do。嗯。对。I， too。

I to up code， we set to the one。And that's all we need to cook。We copy it。Into the new P。m。Over。I。

 too。one by in size。And this is the whole thing。 Now we can clean up a little bit all our malllos。

And what's that。 We have I 1。 We have I 2。We have possibly a1。왜ビし。Checkick for that。So。

Before we copy a1。In this case， we will have an A1， but perhaps。We will。

You make this visionerinary cute later old。So if we have an A1。We will copy the a one。And afterwards。

 we will free a won。And we can just free。I will。3， I to。And then， we can simply return。

Our example program。Which would just be in this case。And a pointer towards。The top of the memory。So。

Let's just return。Let's just return， VM。Am I doing this right。Yeah， I think so。

A little bit disruptive this because it modifies the virtual machine。But the。That's okay， for now。



![](img/fe8ce403cf7cf58356ce32702c603a81_200.png)

Let's see what the compiler says about all this。you can dont be clear on you do。Conflicting types。

 for example， program。

![](img/fe8ce403cf7cf58356ce32702c603a81_202.png)

I didn't update signature enough。Example program takes a VN。Example， program takes a PM。

It should return。这个后你知了。

![](img/fe8ce403cf7cf58356ce32702c603a81_204.png)

其。See， cast from point to to integer of different size。嗯。This one。Cas from pointer to in。The P is。

He is point。

![](img/fe8ce403cf7cf58356ce32702c603a81_206.png)

I'm casting it around me。 Okay， I should read the。Erero messages。More literally。Okay。

 so let's see which one。嗯是。Search for。系。Maybe we need to escape that build system。没了。Copy I。 No。

 it should be one there。

![](img/fe8ce403cf7cf58356ce32702c603a81_208.png)

So let's try this again。I choose a pointer。 Yes， I need to do that，84。



![](img/fe8ce403cf7cf58356ce32702c603a81_210.png)

So， this should。Arrow， instead。

![](img/fe8ce403cf7cf58356ce32702c603a81_212.png)

P， S， let's remove that。

![](img/fe8ce403cf7cf58356ce32702c603a81_214.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_215.png)

Too few arguments to the example program， that's right。



![](img/fe8ce403cf7cf58356ce32702c603a81_217.png)

We do not update。放 you狗。Okay， so we need to change up the order here。

 We can't create the virtual machine after the program。 we need to do it the W。

So VM is a virtual machine， no arguments。Don't need the size。 I don't think so。嗯。See。

Be spiritual machine。The program will be equal to this。And we sung over the end。



![](img/fe8ce403cf7cf58356ce32702c603a81_219.png)

PS。

![](img/fe8ce403cf7cf58356ce32702c603a81_221.png)

Because we don't really use P， S。right。

![](img/fe8ce403cf7cf58356ce32702c603a81_223.png)

Okay， no， this should be fine， I guess。你。所。Space down a little bit， clear the screen。

Run make and boom。It complies with an annoying warning。A1 may be used and initialized。



![](img/fe8ce403cf7cf58356ce32702c603a81_225.png)

嗯。We copy from a one。Let we do if a。And where do we create this a1。Let' see。If we have an F A1。Okay。

 so if we don't have an essay1， we don't allocate for this。So maybe we should check for S 1。



![](img/fe8ce403cf7cf58356ce32702c603a81_227.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_228.png)

嗯。A baby used。点点会 fix啊。This is。来 a你。If S1。We free everyone。Okay。

 the compiler doesn't really seem to know this。The difference。So let's use both just to shut it up。

 right。

![](img/fe8ce403cf7cf58356ce32702c603a81_230.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_231.png)

不准。嗯。There should be something like。对。It will just。Tell the compiler that I know what I'm doing。

 Don't complain。And yeah， we can suppress the warnings。But we shouldnt really have to。Right。

But alright， let's move this to an old if statement， if S A， if a1。对。



![](img/fe8ce403cf7cf58356ce32702c603a81_233.png)

Simpple for you， G C。Cle and down little bit there the we I make and。不。No我。Copy。



![](img/fe8ce403cf7cf58356ce32702c603a81_235.png)

咦。

![](img/fe8ce403cf7cf58356ce32702c603a81_237.png)

Which line。

![](img/fe8ce403cf7cf58356ce32702c603a81_239.png)

修理被。いつですか。Stillill with this essay1。Okay， let's do something like this instead。If F。我。Then。

 we allocate。And then， if。A worm。We do this。And we change this to a1。We move this free。给。

Imine we are。Wasting several minutes of code， and just。



![](img/fe8ce403cf7cf58356ce32702c603a81_241.png)

To shut up the GCC for something。I's really a problem。Oh no我。A1 same thing。 A1 equals 0。



![](img/fe8ce403cf7cf58356ce32702c603a81_243.png)

A1 equals 0。it's it。

![](img/fe8ce403cf7cf58356ce32702c603a81_245.png)

How can that possibly be。

![](img/fe8ce403cf7cf58356ce32702c603a81_247.png)

A 1 may be used un initialialized at line 67。诶。And the line above。Or two steps above。

 we we assert that we have an a1。In this holy statement。Make sure we have an A1。

So how can that possibly be used un initialitialized。Am I missing something here。If S。

He really is allocated。A1， we do this。嗯。I don't really get it。



![](img/fe8ce403cf7cf58356ce32702c603a81_249.png)

I don't think this is the problem。And I am sick and tired of this error or warning， rather。So， let's。

Remove it。

![](img/fe8ce403cf7cf58356ce32702c603a81_251.png)

And do stuff like this on your own risk， perhaps not in production code， etc ce， etc， et ce。本。

I just wanted it to be quiet。Okay， so which syntax is the right to work。

 Is it the equal thing or this。定。Well。Try to find out。



![](img/fe8ce403cf7cf58356ce32702c603a81_253.png)

So we make lead， which can don a little bit， clear the screen right making it。There we go。

 We have a binary， ladies and gentlemen。All right， does it crash everything when we wrote it。

It does not。And it does give us a virtual machine， and it does give us its memory。



![](img/fe8ce403cf7cf58356ce32702c603a81_255.png)

Pretty good。 Let's also。let's check if it， its memory contains the right thing， then。So。

I could write。 and maybe I have one of those hex stamp functions inside a pursuit that I think I do。

Pnt textex。Right， and it takes three arguments。 What's the third。吹。😔，四。我て。그린 해。对。

So it takes a string， makes sense。 its size also makes them a dilimit， alright。That's pretty nice。So。

 let's do。い。And we give it。Program。And we wanna print how much。We have。Well， basically。

 we're going to print this， right？没有。ble。是。6万。And what kind of deliverer do we wish。嗯。Space。えて。

Or maybe just enough。I don't know how to express。I you。We will recompile this thing。



![](img/fe8ce403cf7cf58356ce32702c603a81_257.png)

Let's run it in， Brch VM。Okay， so this is our memory。The first， maybe we should have a deiter。

 This was tricky to see。

![](img/fe8ce403cf7cf58356ce32702c603a81_259.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_260.png)

Compar。All right， So first， we have。The one。Then， we have0。That's our remove instruction。No。

 this is our move instruction。This is our argument。The number 5。And。This is our renewal。

So it does exactly what we wanted to。Okay。So what is the logical next step。

Now that we can create the virtual machine and we can load a program into its I remember one thing I do want to put in there。



![](img/fe8ce403cf7cf58356ce32702c603a81_262.png)

Because。If we look at this thing， we have a。嗯。We have this。This right。 This is our virtual machine。

And then we have our memory， which is 65 k roughly。Of the。Memory。So， let's say， this is it。

We have a bunch of。Cold here。So this will be our text section。可。C。Do we have some kind of。AGraal。

Representation of our code。うて。Like this。 So this is our record。Then if we go to the bottom。

We have section data our stack or heap or something。Which will。Grow the other direction。

And then we have this space in between。So。This will be pretty static When we have loaded our program。

 we know how much this。With this stuff is。And this can vary along。Program session。

So there is an imaginary line in between here。嗯。Basically， directly following。です。C。And this space。

 which is being used。As the stack。嗯。So as soon as we have loaded our program。

 we want to set this brake line。Because then we can differentiate between different types of information。

So we can， for example， limit this。So， we have。We can help us read access and we need execute。

But we don't need right access so we can make this。Theri懂的。And the data section， in turn。

 will also have read if we not have executed because we don't want it to be executed in code on the stack。

It's a security risk。And。We needed to be able to write and open the data。

And if we have this break line， we know the different types， and then we can。

Put those restrictions in。So this will， this brake line will simply be an offset。え？Into this。

The address。Of this last bite here on the program。So。The memory。Is still this。But in addition。

 we will have。A break line。I'm not really liking putting this in addition。To the memory。

Doesn't really seem right。But let's do it for now。 Maybe we can clean it up later。So， basically。

This will also be。They the same data type。No。This let's just do this as an date for now。

So let's call this break。B。嗯。Or maybe we should make this。I interview since it's an officer， right。嗯。

So， let's make this an in6。That's appropriate。And let's call this bee for Gregland。

And when we have loaded our program。As we have inside of here。Before we return this day。

What we do is we're gonna set the V and brake line。To be。The size of our program。

Which is basically S1。Argument。Size， or what do you call it， size argument 1。It too。That's over。

Offf the。To the brake light。Yeah。Or it's S1， S A1， S2。没给委。Because。This is a 16 bit variable。

The let double check。This is what it is。 We have S1 is 2。And essay say1。That这。That's just S1 minus1。

 yeah。Okay， no， it looks right。Let。Make sure it compiles。 I didn't change much。



![](img/fe8ce403cf7cf58356ce32702c603a81_264.png)

Pro。And this you steal around。 No， no Se faults。 That's pretty interesting。



![](img/fe8ce403cf7cf58356ce32702c603a81_266.png)

Itful。And all I did was adding these stuff。S 1， S1。I to。V and B equals this。

Did I add anything else between the。Reculation。

![](img/fe8ce403cf7cf58356ce32702c603a81_268.png)

Can this really。对不对。其动。

![](img/fe8ce403cf7cf58356ce32702c603a81_270.png)

唔。VM。B。VNB。We're just setting。A variable inside of the structure that we have pre allocated。我我的。

The about。S 1， S A 1， S 2。S1。S， A 1， S 2， All of these are in 16s， by the way。

 So I don't believe this。But， still。How is this possible。In  sixteen。B。Am I crazy。

A blind or something。

![](img/fe8ce403cf7cf58356ce32702c603a81_272.png)

![](img/fe8ce403cf7cf58356ce32702c603a81_273.png)

Need to know what's happening in this。Is it the free call。对。3， I 1，3， I2。

And we have pre allocated both of those， right。I1， I too。We have asserted。We got them。

Is it a double frame， perhaps。The free a1 here。If three， I1 here and I too。And why does this matter。

I think we need to debu this more thoroughly。

![](img/fe8ce403cf7cf58356ce32702c603a81_275.png)

Let's open this in GDP。Before we do the。可别烦了。😔，Let's go。2。まち。嗯。Oh it's inside runler。

So we go to cold。嗯嗯。Good this。嗯。The file in my home。Com me and I paste this。 This is my。

settingstting。To直 be。So。Ca this state。So guys， welcome back， everyone。

So now I have moved my project to my 32 bit machine。 So it will be a little bit easier to。To the bug。

 if we need to。And。On this machine， I am running the absolutely latest Gcc version as well，14。2。0。



![](img/fe8ce403cf7cf58356ce32702c603a81_277.png)

And you probably need to compile that。😔，Yourself， if you want to run that version。

 you can download it from Gunew。 Let's see， from G C dot Gnew。たとき。And so， I want an update。thing。

Instead of C to X second L。Do the real。C，23 standard。So let's say。

 and I have it the new version does a couple of things differently。 So when I。

 I mean the new GCC version。

![](img/fe8ce403cf7cf58356ce32702c603a81_279.png)

So when I run my make， do get a couple of new errors。First， this one。That it's too large。



![](img/fe8ce403cf7cf58356ce32702c603a81_281.png)

嗯。And not really。Okay。Of course， it is。So， let's see。Because。我认识。Where are you。Okay。

 so I do have an on in there thats。Basically， a 4。3 billion。Big thing。え？I don't want that。 No。

 I want this to be an in 60。Soold 65 k。That's more like it。And then noticed another error。

 we are returning the memory address of this thing。And those。Returning it this way。

 because I thought， well， it's a point， right， but it's not really。It's a memory。Yeah。Data type。

 And this is anchar array， which is not necessarily the same thing。 So I think we actually need to。对。

Really。So if we say， what does the compiler。Hello。

![](img/fe8ce403cf7cf58356ce32702c603a81_283.png)

I've done a little bit to make， okay， we've got rid of almost every error message。What's this。

Returning in blah， blah， blah。From a function with incompatible return type program star。Okay。

 so it doesn't like us returning the address of this thing。



![](img/fe8ce403cf7cf58356ce32702c603a81_285.png)

When it's actually in a rate is probably still trying to。Well。I think we need to cast this basically。

And I hope the font size isn't too small。 I reduced it one step so I could see all my code。

But it should be all right， I hope。Otherwise， please let me know in the comments so I can fix it to the next。

Alright， so this is。Well。We wanted to be a program star。So， if we do。Okay， so know it works。

And I'm still getting those warnings for truncation。I wonder why。

Because we should have eliminated those， right。Which reminds me， I forgot to load up。

Let's go into the so， but I forgot to load up the virtue till so。Let's do that。

Because we probably is going to change stuff inside of there as well。 So I will load bi till。

And I will drag this into my project。 I love it work。We can do that。And then we'll close this one。

So ni。Okay， and let's double check this thing。 We have the virtue of the age。And this。

 this is probably。Including the。The global thing。Wherehy did I put it like。呃乐。

That's most definitely why。We do still get those warnings， even though I suppressed them。



![](img/fe8ce403cf7cf58356ce32702c603a81_287.png)

See。clelean着灯。ねき？Isn't it lovely。

![](img/fe8ce403cf7cf58356ce32702c603a81_289.png)

And came around this thing。 And it does not crash， ladies and gentlemen。That is pretty nifty。

 I think。And I wanted to double check one thing。嗯。Because we are allating。Our V M instance， right。

And I want to double check how big that thing is。So， let's say。Close per suited for now。

 And the make file。んです。Okay， so let's see。So inside of main， we create this virtual machine。

 instance。那次。Also do。This equals pointer。It size。て？And then， willll seem to do。S on。对。Yeah。

And if this works correctly。Let's see how much memory this will take。First。

 we have a CPU and what is a CPU。嗯。是。Where do you have it here。

It's a structure with only one member and that the registers are。Registers。22。第嘴。Couple of registers。

 iss 1，2，3，4，5，6， right。And how how big is a register， It should be like 32。Steam with red。

But let's double check so we know。So register singular。 This is the one short the 16 bit。Okay。

 so we have 1，2，3，4，5，6 times 2。 That is 12 by for the CPU part。AndThen we have the memory， which is。

Is 65530。6。嗯 so。Basically， that plus 12。Maybe we shouldn't do this in， in the head， by the way。



![](img/fe8ce403cf7cf58356ce32702c603a81_291.png)

So， let's。We have。5536。But it's。Plus，12。So this is the number we have this far。



![](img/fe8ce403cf7cf58356ce32702c603a81_293.png)

And then we have one in 16 for the break line。We add。2。

And then simply we have a pointer to a program。And the pointer is always。Wait us I again to point。嗯。

How did we do that thing。Example program， printer。And when we initialize that program。

Do we ever set this？Ping。真分手。😔，Because that should basically always point。To the top or the but。

 the bottom of the stack。Basically。Yeah。So it's really a point of having it。 I don't think so。

 Let's remove it。

![](img/fe8ce403cf7cf58356ce32702c603a81_295.png)

Okay， so hopefully。Our memory will be this than 65550。65550， okay。

You can double check the same on your GCC version because sometimes it has a little bit trouble with these kind of syntax。

 like when you。

![](img/fe8ce403cf7cf58356ce32702c603a81_297.png)

Type de。An array with a predefined size。So double check that it does that all right。

And that is probably by the way it works now in this version。 And we had problems before。

Since it calculates that correctly and they enough。Memative。Okay。

 so now we can basically load an example program into our virtual machine。And that's it。

What's the next logical step。Well， executing our program， right。

So we need some kind of execute function。And。And what will that take。是。对。Here， I think。First of all。

 what， what should it return。And it should have like。Possibly a return value like。Like Maine。

 you know， returns something at the end。え。But， not necessarily。We can for now。

 at least it will be a void。AndIt's called execute。And all we need to give it is a virtual machine。

And。And program。都是这。And I'm not 100% sure how I'm going to do with this program。

 because currently since we did the refactoring。え？We are。

Changing the virtual machine when we love the program， so。Basically。

 if we create a program with this example program， we are putting it inside of the virtual machine。

Mly， so to speak。I think later on， we will divide that stuff， but。It's okay for now。

 It's only an example function。Which means this should be。The syn。We。We could omit this。But the。

Let's have this for now。 We're not gonna be using it for a while， but let's do it anyway。No。

 let's know。That we are not currently using。 It's better to add later on。Okay。

 this is better All we need is a virtual machine and we can execute。Instructions and。

Remember one thing， we need some kind of end instruction。Because we， our instruction are。

 are basically an a stream of bites。And every instruction has a different length and so on。

 We don't really know how long our program is。And that makes it troublesome we could。 we could well。

 we could use。The break line thing， because that's。Let's see。 where is。です。

Do you remember the brake line between the stack and the dayev。Tt segment， the code segment。

In the virtual machine's memory。So this basically tells us where the。

C section ends not necessarily the same as the programme。 Currently it is。

 but not necessarily always。So I think I'd rather， at least for now。Have an end instruction。

 like in the good old days when you have had a halt instruction， you know。

 that the halted the the CPU。And I think it's still there， but yeah。

 not used very often in today's code。So， let's take a look at our。Instructions。

So here are our up codes。Let's add one more。And this will be hold。should win。

Should it be three or four？Well， we are never going to execute two different instructions at the same time。

Except if we were to implement like concurrency and threads and stuff inside of our virtual。

Machine in CPU course。But even though， even then， we wouldn't use this kind of way to do it。

So let's give this the number three。And we also need to update our math。This one。Until our。System。

How big this instruction is， how many argument or how much argument。So， this would be。

A single instruction， exactly let they know。And。And it would， basically。对 this。Right， one bite。Okay。

 so let's go to our execute instruction。嗯。And let's， by the way。 No， let's do。

Let's go to our execute instruction。And it's void， executes， and it takes。CBM。And what does it do。

We need a program。Poiner。Which is the。Medical EP。And。Let's double check， but a program is justice。

Drinks still， right。We did a couple of two and froze there。

I need to find a better way to start looking for things。Innstrument， V M。Memory。Program， yeah。

 indeed。All right。So we can assert that we have a VM。And。And that。The VM。Has a。Program， loaded。

And how do we check that？Well， we do have access to its memory。And。It called Em right。Yes。

And this memory is an array。Of the。バ。So if we just check the first bite。If that is0。We will。Quit。

Because we don't have zero instruction。So this will always be one if we have loaded a program。

Alright， and if we have， we can set the P P to that same address。The you诶。So to point to the first。

First thing there。うん。嗯嗯嗯。And then， we will start parsing。The instructions， basically。So。We will。

Need some kind of aloof。Let' see how we do this。We will look until。P皮。Where are we going check。

If the。If we hit the halt instruction。In that case。The current position of P P。Will be equal to。

How do we put this。Maybe we do this。六。后。Is that it， I never reduced this kind of construct before。

With an enum。Well， instruction。Instruction is astruct。

 so we need to go into the up code all inside of there。So。This should be instruction。

This should be or cold。And。Yeah， of cold whole。Because up code。Is defined as the in and y up code。

 and we have the hold here。So I think we should be able to do this， right， it makes good sense。😔。

So if the current position。E iss not equal to this。We will continue，And do we have another condition。

 by the way。I think we do， actually， I also want a chef。Yeah。Let's see。Check the P， P。

 the address of P， P。Is。Less than or equal to。The brake line。To be。B。

 because if we have gone past the brake line。We are inside of the stack and executing instructions from the stack is not something we want to do。

 In that case， we want to actually。We want the program to crash。Or not our program。

 but our virtual machines program should crash with a segmentation fault。

So we can put this under here。Do it， if check of the same thing if。え。你 please。P， P is less than。

Let's say， in this case。P， P is big then。The same the。B。Then we should sefold， right？Thankful。

And what does sful do。Well， void。Fs。We are you here so we can clean up a little bit。

Not that we need to， but。语音。We have the that we。The the。What else should we do。Well。

 we want to print some errors to the screen。Or maybe we should just call this error。

And we can be sgfold later on。 So we'll have a VM。The error code。A。Pment。没嗯。

And then we can have like， a switch statement。哦。The个。And if it's equal to。Yeah。That， I think she。

But I would this in lower case。In this case we going。強てい。Scrreed to the error buffer。Sation。そ。

And let's add VM in front of it so we can distinguish from。Regular sfuls in our code。74。So。

Maybe you did this。Habit。In order to。Make the coat。A little safer from formal string bugs。嗯。嗯。

What shall we do more。For the。B。For。こうす。嗯。我算这个X one。上度的。Okay， so now we got a new function。

As a bonus。Goodness is avoid。嗯。And we give this a BM star， and。Cold。

What is an error code We haven't find out yet。But。It will be。 where do we have。

They are pretty spread out。Let's put it。 where we have。Several。In the road like here。

And why would I want to do that， No reason， really， I think it looks better。Okay。

 and let this be an inside。小儿。That code。And we need to。Find the different error code。

Maybe its own section of defiance here。So。😔，But we have errors here already， let。you。おあオッケーです。せ？

If are。Thank you。そいつた。And this。2。It's also。But。00。0，0。0。And this， we can move。To something。Thank you。

It should be。Okay。え。So。And let's also create。Macro forgot that。 Do we have any macro all right here。

So。I。水服。And if we encounter this。What are we going to do？Well。We are gonna call error。

With the specified PM as an argument。And。Sa鱼。Easy page。

And that's basically what we did inside of executed， right， sgfold V。对す。Al right。

So if we are still traveling on inside of the。Tt segment， the code segment of the memory。

We will do something at it。Iteration。And P will be equal to the first。It's maybe。Well， basically。

 it will look something like。Instruction 1。I give to。Inscript。十？Section 3。So this is a lower case。嗯不。

Instructions do we have while we havet move。2。Yeah。Number 5。Let's see， how can we separate those？

Yeah。cleway。です。that's。Let's do this for now。And the second instruction， that was our no。

 and we will also at the hole at the end。And in binary， or in the。诶。Yeah， I mean binary， basically。

We will have this。Sah1， which is the movie， Mo Ax。And then。0 and then05。This is our move。

And directly following that。We will have our。Other instruction。怎么弄啊？And finally， we'll have hope。

So this is basically our memory， and P will point to this first thing。

So the first thing we want to check if is is this thing something that has arguments？

Because we need to split up。The instruction and the possible argument。So， let's say， we have as。

Data type。 So let's say we have a worm。And we have。2。possiblesible arguments。嗯。

Maybe we should zero initialize those。比如说。Because they are。Pointers right。

 And that's how we have used them this far， I suppose。Well， we do have it as。An array here。

 But poetry is fine。So， these are the arguments。And。Let's also create。Destruction。嗯。

Maybe the instruction does contain。The argument。So we don't really need to define those ourselves。😔。

All we need is an instruction point or an IP。And that's not the register I。Now。

 I'm just talking about。We know code so speak。For it， so。I。Equal to。It true。Did。皮屁。

With points to the same thing。But it will interpret as an instruction。And we need a size variable。So。

 let's create。See。嗯。Ss。And size we get from。第一。包括。We are currently pointing to。In the mapfunction。

And then we will know how much we should increase。皮屁。I did。Right。

So when we are done with this instruction and its arguments， we will。Add that to the P。

 P and go to the next it。But how will we use this？Well， basically。

 we should just be able to do something like。Let's say， we have an exit。Construction。

So where we are now at the execute function， we are executing a program。but。In here。

 we are executing a single instruction by I。And I P will contain all that we need。So， basically， the。

Instruction up code。And its arguments。Because they followed directly。Afterward。And that's。

Proablyly if I suppose。Well。Talking about instruction pointers。If we look at our registers。

 we haven't spent much time with those， but all these are zero from the end。

 right from the beginning。😔，But now， we can need use。Some of them。

 So with the stack pointer and the instruction pointer， we should actually。

Have initialized and where should we do that。For the time being。Well。

 when you create a reversal machine。We don't need to do that。Because。

Then it should be zero because we don't have a program。

 We don't have anything in the memory and so on and so forth。😔。

But when we have loaded our example program。Which we have pretty much done done down here。

Here we set the break， but we should also set， let's see， VM。え？CPU。Registers are。And。IP。

And what should it be equal to， well， it should point to the first instruction。Which is， basically。

The register。Let's see。Well， its an point。We should actually put the address in there。

So it should be the registered。Version。Of the address。奥迪。In memory。そう。But， this is a little bit。

Weird syntax。So let's see how we can do that better。Maybe we should create。Alias is for it， so。

Macros， basically。Yeah， we should definitely do that。So， let's create them。

ACo more of those dollar things。Let's define。AX。Which will be。Good see。So we put the CPU in here。😔。

In Nor， the virtual machine。 and then we go to the CPU。 We go to the registers in the CPU。

 and we go to the A X register。Can we do this？It looks。Kind of like weird syntax， but。

I don't do this思呢。So let's see how many do we have6 at the moment。就会啊哎嘢。BX。C X， we have D X。With a S。

We have。だいてい。A。いレス。いいえ。SP。And系。Have you seen seaequ code like this before，Alright， so let's see。

 Then we could change this to the dollar。I。Is it to。です。Read is。いして。Of the。O。A lot easier， right？

And what about the stack pointer， the stack pointer is always pointing towards the stack and since we have not put anything on the stack。

 it will point to the beginning of the stack。And since the beginning of the stack is the end of the memory。

It will have the last possible memory address。手臂啊。Stack pointer。Will be equal to a register。With。

The last possible address。 And that's always-1。嗯。Yeah。This should be it today day。Which also means。

If we go。If we go to our execute function。Where is it here。So when we are done。

 executing the instruction。We do not only want to increase P， P。 We also want to increase the。

Instruction point。So， the V end。Instruction pointer。Should be plus equal to size as what。All right。

That's all good。 and well。No we maybe to the exactec instruction。

 we should also pass the video because。Otherwise， it will be difficult to do stuff reallyly。

How should the execute instruction function。So。Let's see。It to you。Dion， we take it the。And we pay。

An instruction。嗯。To create the signature before we forget。So we have avoid execute instruction。

With the。当儿。跟我去比的。😔，I the thing。 we should have it least。A poll duty。Instruction。Alright。

Let's also create。No error definition。有得。This area。It。Because when we go get to the halt instruction。

 I want to。Ex using。So basically， I would run the error function with a0。For convenience。Okay。

 so instruction， then we will have an up code and all that。 But let's start with the size。

And it's not optimal that we need to recalculate this， but。Never mind for now。

So we give this the eye。哦。Sttches up code。Map that to size。And basically， we wanna check if we have。

Any argument。So here it might make sense to have。A1 of a2。As those， right。It。

The argument size will not always be the same。So， for now。We have。 We do only have arguments to our。

No， to to her move instruction。Where is our example program right here。So以。5 a1。0。0，5。

So in this case， our argument，16 B。 Will it always be a 16 B argument。Ls。Take a couple of examples。

We have X， or it's gonna be 16 bits and same with all the other ad and multiply and stuff。In。

Saing there。嗯。What else we are also going to just compare。う。就。Yeah。The instructions will。Yeah。

So how does this a ex look， Maybe we can define that in there。Okay， it's just a。サイズ。And。No size。Aray。

An orgs is just a string of bites， I， where do you have orgs。Type if in。 Yes， it's a sh bite。

 But what's this first hit we got。No or。So I put zeros when we don't have arguments。

That's not really what I want。 Am I still doing that， even after the refactor。Let's see。So。

The first instruction。In the argument。Then， we have。The second instruction， I， to， somewhere。I， too。

 Here we copy I 2。T位科学。And is zero arguments， No enough。And it's a bad idea to do it this way。

 because then we are wasting a lot of。Memory space。For no really good reason。

 well it will be easier to code。And perhaps less error prone while calling it， but。No， thanks。

All right。So。These arguments will be 16。bit size。So why don't we just make them 16 bits things。

 every of them。 Why do we have to worry with without buys and stuff。Because when we set those。

How do you do that。In this case， you just do a1 this。对。We could just have done。They will。This。

 if we let it be。A 16 bit thing。And I think that's how we're going do it。Do a word like this is that。

Where do we cook。The a1。It's done here。So no a1 would be a reference to a1 instead。Not the value。

Where do you have a， So we don't。Lis。Well just define it as a one like this。They were。

And then we don't need to mallic anything for it。If they were。Necessarily。But lets zero来 to。

The Thursday went no。0， a 1。 No， not like that。And when it was 5。Maybe we should do it， like。make it。

Extra。嗯。Extracer that were dealing with the 60 bit structure。Ex obvious， I mean。If a one。

 we don't need。To do。Perhaps it does。u。If we have an neighbor， and we copy。He文。

We increased by SA What was SSA。1。Size of a1。喂。S a1。Is the S1， minus-1。Yeah。

We don't really need to do it that we got。It's okay。Then， we will simply define。Argument。A。

 it can be several。Which means we can leave this as is。this will change to6。



![](img/fe8ce403cf7cf58356ce32702c603a81_299.png)

Compile。嗯时。We will probably get errors because were in the middle of。



![](img/fe8ce403cf7cf58356ce32702c603a81_301.png)

I'm created under our function， but I just want to see if this part works。



![](img/fe8ce403cf7cf58356ce32702c603a81_303.png)

After we have cleaned up。Some are the errors。In 16 size， but juice。And is variable， bla， bla， blah。

Worn in comparison between pointer and integer。If p。Thiss less。Orre equal to the V and B。

 But shouldn't we be allowed to compare those things， right。It's just address。

Maybe you can cast it somehow to make sure。We。That word。Okay， and this， we need to change in line 28。

嗯。Expens vegan or。see。对。And how does it live。If we look inside of here， what do we have？😔，We have a。

VN， and then we have the CPUU C。And if we go to what a CPU is。It's a structure that looks like this。

And this has an R， which is not a pointer。 That is right。So， let's see。VM pointer。

 This would be like that。 C is。Is worth definitely。See if I do。No， that's not a pointer。

And neither is our， which means， let's see if in do。we。Do the。买 short。What's the name。 Short case。

 short command。Isn't really configured the way I want。They should be able to make this bigger， right。

Topossible with this keyboardword。Keyboard。Let's just said sun。 Yeah， said the magic or。Theim motion。

 magic。So let's see， what are we going to change。We are going to change the string。Yeah。See。哦。

Something。Into。し。Dont are dot。And what else we had one more arrow that I mentioned。诶。Right to page。

In the right file， perhaps。て。嗯。Yeah。对。Can we cast this comparison somehow， Let's see。 P。

 P is a program pointer and this。Memory pointer。Perhaps。😔，No，700。Stay。Let's call this。AppPro。た。

Can we do this。Entirely sure。Okay， let's see。嗯，贝的小。Just had an epiphany。No。

Because it is the actual value that we want to compare， not its address。See the value is an address。



![](img/fe8ce403cf7cf58356ce32702c603a81_305.png)

Right。So we。リジト。Clear the screen。Make and boom。A couple of warnings， blah， blah， blah。

To pointer from integer of different size。What different size is it really。P， P， well in the。

But we're still only interested in its value， Sir。We shouldn't worry too much about those。

A statement with no。Expansion of A A V。Okay， well， it will have effect when we are done with this thing。

Okay， it didn't like this。 I Se。Dine。Right， we cannot name it。Wai a second。 Allright。

 we need to have a keyword in front of it。그。It have the。He wording， warning， warning，3， a1。 Yes。

 that'。A little bit hard to do， when it's not。朋一队。So let's see where do we free the thing。

 probably inside of。This。所以。飞飞飞 this series。Were done to one page more or less。

 And what is this register unde declared， right， It should be just re。Apppear。怎么。😔，I think。嗯。してる？

Yeah。So this。See cast。Pointed into here。Of different size。Well。

 that's not really a problem in this case。Shouldn't be， at least unless she is interpreting my。Code。

 otherwise than I am。In this one， maybe we should。Cas that will， at least。

To make it more clear what we are， but we want to achieve with this。Because this should be treated。我。

ポ。Program。Well， either that or we cast both as memory。 But that we can do that since memory is。

Always。ASpec size。Dont know。Can't do that。I think we will leave it like this for now。

I don't care too much about the warnings。 I even think。For the time being。

 since we get so many warnings， that's not even relevant to our code。I will actually change。

My make file， and。We。我。2 should be。诶。Okay， I'm in the wrong make fight。你。K的电视。Qu it should be this。

So。2 is okay， but remove the wall for now。Do we still get words if we do like this？See。

 we make clean。We're down a little bit you clear the screen with run make and poem。

Kid still couple of them。I don't like this word is。And this is not really a good practice。

 suppressing warnings and。Stuff like that， but。Since I know what I do。呃。こ。

Da there is statement to do。If I do get make error。Later run。Let see。There is。This kind of sign here。

 the dash。 It's not the dash。By those other ones。现爱。😔，Should I remove that now。Winter pointer。

 Winter pointer W。This is something else。And if our program crashes now。

Then at least we know that okay， those warnings were correct， but I don't。

 I know I can't even be correct。I have a hard time seeing them being correct。With。Thisげ。

I was thinking about something else。Never。Good， so let's remove this and we do past this paste。

With the point the cast， that's exactly what we want to remove， right。And we have not heard already。

Which means。嗯。嗯。우 왜。对。Win the pointer。And what was the last one， I that what we have in。

I will copy baby paste。The food。Let's see。Doubleュ pointント。And wind by。W。You do have this though。

It's exactly the same。And all of those don't have a this。对。Let's try this and see what。Unknow option。

After blah， blah blah。J C his diagnostic， ignored。W。Which one is it。诶。对。The one with a dash。

So if we were to remove。的。Will it work。No， I don't think so。 Maybe we shouldn't have the whole thing。

Maybe， we should just。You remember。Stone。Maybe it's just。Like this。It's really weird， though。

This should be。对对。Save and try this。Yeah。唔都。Okay。嗯。So， and we run。They forget。We get a little less。

 but still we get this word。So let's copy this specifically and see what we are missing。

Win to point their cash。Will disappoint your case。Good。Pro。なんで right。Iello its been nice looking。

 yeah。I like it。

![](img/fe8ce403cf7cf58356ce32702c603a81_307.png)

And no crash。P的。Alright， let's see if we can finish this execute function。

 and then it will probably be it for today。え。Let's see。Where are we。

 We are executing this inside of here。 Okay， so we have calculated the size。

And these shouldn't be pointers at the longer。We can still have A2， though。That's0 initialr。

 Did you know that you could do this， by the way， A1 equals a2 equals 0， and everything will be 0。

We need the trick。Ochids。So。Let's see。 We have a couple of different room。Possibilities。

 at this point。See。Let's do a switch over。We have K 0。Did break。 we have。

Its one then we have one argument。Let's set a1。To work。Well。A1 will be the first。In the array。

Basically。It would be。系。A for arguments。给了。왜래。We bring And if we had。嗯。We will。没我。各位屌。就せ。Its 2，2，0。

What。And if we have something else， then。Have been terribly wrong。And in that case， we will。So。Okay。

So these are different things。And know when we have。They divide。We can switch for the up code。So。

 we switch for O。No I。哦。Any。Don't understand what these are。 I instruction here， right。

And an instruction contains。And up code， which is named O。So that's basically。

And if we switched for that， we should be able to put something like。

I have never done this with Enum， but logic dictates。That this would be possible， right。

🤧And if we have a move instruction。We will call。No。And。Will give it。

And should have different kind of moves。Yeah， the op code wouldn't tell that so。So give the we give。

第一。嗯。Stion。Bookp code。That we give。The two possible arguments， A1， A2。Okay。

We can also have a case for blow up。In which case， we does nothing。And then we have a case for whole。

And then we will simply do something like。うん。Will do error。Or maybe we should have its own for this。

嗯。It's not really an error， but。Let's call this system halted without error just to show that。嗯。

Using the error function is good， though， because that exits everything。shouldn't return。

So let's go to the error function。And add our。Case。To the case。What did I call it。对。哦，对。

At which point we will。Simply， write down something to。But for。Sysem。冇。对。嗯。And then， we。B。An exit-1。

没个微信。Create an exit code。We only need any date for this。歴 code。Let's exit code。word。

But with the possibility of changing it like in this case。Where will set the X is going to a clean0。

In没。嗯。いえ。对对。Interition。Our ex。Okay， so we have new functions。Don't we， Well， will。

 we will have a new function， which is move。Which takes one， two， three， four arguments。

And maybe we be， there will be a lot of those functions。 Maybe we should like。

Because there were own section here。Okay avoid。Move。And it would take a BM star。It will take an in。

Dction。And know， no instruction and up code。And it will take。All。

Maybe we shouldn't have that impural， but。我认为。Can。And what should the move instruction do， Well。

 it can do a whole lot of different things， but at the moment we can only move into a value into a register。

 which makes it a little bit easier。Seeed void move。嗯。Maybe we shouldn't have void。Because。Yeah。

 if we need to return something， we will put it inside of a register like。Excused。Okay， so let's see。

 We have Van star， thean。Then we have the up code。Quote。We have as， a1。Or。To possibly。

And what are we going to do at this point， well。The only thing is， we're gonna update the B。

We seem to do this。The Vms A。Register。Should be should be equal to。你。为。没问。Yeah it。

So if we run this program。See。We should be able to。切我俾爱人。🤧。嗯 this should be了。4 digits。Yeah。16 bit。

可是 you。And it will be this dance end。So。In。Reform。

![](img/fe8ce403cf7cf58356ce32702c603a81_309.png)

Okay。clean we don live it to a week。 Okay， that's a red redarrow。Good move。 move， re declaredlared。

As a different kind of symbol。 Okay， so we can't name something from an enum into that。



![](img/fe8ce403cf7cf58356ce32702c603a81_311.png)

Okay。So else should we name them instead。I want basically， the same structure for all my。

Instruction functions。嗯。し？Let's put。嗯。I don't really like those things。

But let's do that in this case。Two other scores in front。And where do we call。No。The message。

Where do I call this room。Well。So right here。Can you ever else me。

Just will have some kind of symbol to differentiate those functions。

 because there will be a lot of those。Probably。We very clean。 We will go。This it's red still。

Vid move。人的情戚。I believe啊下一句。😔，Yes。And I'm not disconnected， either。Well， let's see。

And the space here is saved we。Same。Please don a little bit to the stream of。Okay， lets。

TheS of a ray memory is too large。嗯。Oh， sorry for the foul language。But， it's like。

We're moving back in time。This is like。My code from before， right。

It's like really living the same memories。You get it begin。Thank见。Groundhog day。Okay now do。51。😔。

Very weird。Maybe some buffer or something new。The speaker is the。Laggedgged up for something。Well。

 well。You always undeclared， is it。A1 is equal to O， A。The argument of。去配爱爷一。嗯。哦。Its good。

This should be。嗯。It should be the instruction。And then A is the argument。Does this just be。は。系。

It like this。Ks were the clean with jumpbone to make and move。 O， still errors。E。Shold undeclared。

 Yes， it is。This is在心里。Sens sensible thing。我。う。う？We have our men。 We have。At addition。There's that。

But。Maybe。We。Increase those。So this。唔。比如。Let's put our。Oh。Here。

So we differentiate a little bit from the actual。嗯，就是就是说。You know。Okay， no， it might actually work。

There were and there all the other stuff。B no。ステルの。E isizzled too few。Too few arguments to error。

 What could we possibly want to give that function。An error code at a V N。Who would have thought。

W would have thought。不さ不さ。Okay， so let's see this whole。To put in the V end here， right。嗯。Ba it。

 I guess。See with。Okay， one more。And that's just， oh， I love these errors。

 It's so easy to fix without having to。😊，But thought into it。Say this。

 And now I can for certain say that we run me clean。 It jump down a little bit。 We clear the screen。



![](img/fe8ce403cf7cf58356ce32702c603a81_313.png)

R make and boom， it compiled。 It's compile。 ladies and gentlemen， Does it run without crashing。

 et cetera， et cetera。 Yes， it does。 It does。 It does。 but A X is 0， do do do do。What is a x0。不爱太恶心。

Because let's see。 we creative which machine will run the program。No， you don't。

 We don't run the program。We just create the example program。Let's execute it， as well。Execute。

It what's your argument， I think with is the V。I suppose suppose。Exece excuse excuse just just a be。

Okay， so we have to work this way。But see。No， no， it's se faults。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_315.png)

不同。But， that is not so。Entirely wrong， though。Because we don't have a halt instruction in our approach。

We do not have a halt instruction。I think the brake line should。 Well， what kind of s fault was。

 It's the VM segmentation fault。 That's correct。 Yes， it should be， it should be crashing， right。

 because we don't have a whole construction。 So now it was trying to execute。On the stack。

 it is instructions on the stack。 and that's not allowed。 So it's safe faulted。 Co。

 Then it works exactly as it should be。Perfect， perfect， perfect。Okay， let's see。 We will add a。

Third instruction here。Okay， let's just。さ。This is the instructor。嗯。睡衣。嗯。嗯。Let's see。

 We will allocate for。This will also be a size too， right。あ。你。いエス。2。

The size would be same as S 2 basically， but this would be MRI I 3。With0， I。3 with S 2。And then。

Reterial copying。Yes so we need。三点了。This saided。But this will be I 3。

 and it should be a whole destruction。We up to P。 We also need to increase P。

To copy to P our third instruction。 Okay， now we have。Program。In room。A VM segmentation faultult。

 In't that beautiful。Our own V M thankfulfold。And our own Vm is still sfolding。

Because we are not updating correctly。L维。Let's see the execute。Let's first see that。 really updated。

I think we had problems with。4。Let see， we changed the。Except the program。粉清。We increase P。是置。听就好。

I will write to pay this instruction size 1。We update。See。Instruction point or point to the first。

Destruction。别出来。But。When we have run。The instruction。Are we going to update it in here。Or。

Maybe it in here。So we execute instruction。And we update an instruction pointer。

So that should not be the problem。And the size is also correct。If P look is， maybe this。Is。Exly。

 right。 Maybe the warning was correct。But， pe， P。I's a poeter。With。And the pointer has an address。

Yeah， I want to compare that。Address。2。Value。Of this V andB thing。Maybe we should not cast this， too。

Maybe we should not care it to us。Maybe we should just cast this to。See。And then we cast this  two。

260， What happens then。And we need to do the same。Here。

It's always difficult when dealing with these kind of。嗯。Po do。These are the things related to pos。

The only way know。Can't give this error for two reasons。The moment， it can be this。

 that this is true。So， that' the current。P， P， well， it's increasing right here。mm。So。

 it will always。At the end。B。Couple of more。But one more。Buildill the gray。

What did we set the break to， by the way， We said it to。确。😔，Where do we said it。Let's search for。B。

就是语文。V and B equals。The first size。Mmhmm。Its argument。

Second as we should also add the third right here。The babyで。C direction。带动。S 3， right。

 S3 is the same as S 2。So， let's just。Very。Good looking。 but this is just an example function。

 So we don't have to care some。

![](img/fe8ce403cf7cf58356ce32702c603a81_317.png)

No， that's correct。But， it can also be。The other。文。一次性。This case， when we execute an instruction。

Which has a size。Which is not0， not one， and not2。But， that's not。Really is。

Must be this other the case。Nonoing， how do it。Compare。Toyers addresses。Or one pointers address。

 and one value。Maybe we need to specify that。 This is actually。Reference， we are。Very。

At least on the right here。Is。那个。这子呢。😔，Well， this is just a security feature。

 We can remove this for now。 I will have it in。And code。 But it's not really that important。不知道。嗯。嗯。

Yes。谁的。And in this version。We only it。No， that's这个。M。Okay， so the only thing we check is the。

The program pointer is not equal to the whole destruction。Okay。

 now it should not be able to take fault。K is Luke。Probably it never finds that whole destruction。

But it should be there， right。 We can double check easily by going to the main。Temporarily。

Removing the execution there。Looking at the stock。Or not the stack。And we're looking at。It a second。

Plus。哦。Well， the memory。 I with memory looks。Let's see。This。Okay， so we have。Move。5 into E into a x。

Then we have this， which is。嗯嗯。No up。And this is the halt。 So we do have a halt。

 which should halt the programme， and it should not be an endless loop。But it is。 It is。So let's see。

 where is our execute。And we have。Program point to P， P begins at。For number address。

And it should increase。At this size every time。But， maybe。A我的 section。No that tree。嗯。

I think this is a big way。So let's run while， down and while。嗯。十？どな。Well。我过来。我P屁。No。好到。Oh。m。

Will this make a difference。Well， currently， it will not make a difference because we're not even calling the function。

 but not。F in the snow。What if we were to express this thing and see if it gives us an information。

ItTo right。What about Els。No。嗯。😊，Let's go into this execute function。

Because the P P is a program pointer in it。What is a program。That's only an alias for。3 say，3。Da。

 so it should go through this。连。V member。嗯。认识的生点里。对对。Murder in this。动。嗯 응。

If you don't matter why does it even。K。😔，This is a memory。



![](img/fe8ce403cf7cf58356ce32702c603a81_319.png)

Sa啲。嗯。I think we need to add some debu messages。But。Third VM and V L。Ping the program beyond then。

The current instruction is equal to the instruction of P， P。This is something that。A。我去。😔。

Do to the references。

![](img/fe8ce403cf7cf58356ce32702c603a81_321.png)

Maybeby。Yeah， actually。 that could be。Okay， now we get an actual thankful。



![](img/fe8ce403cf7cf58356ce32702c603a81_323.png)

I basically with an instruction。This is notm currently pointing to an instruction。Is a structure。嗯。

I have so many types。Yes， it's a stretch。So doing this is not really sayingane。What is。A work to do。

 This is then。So instead of pointing towards this。I will call别。Into。大皮。嗯。

I will copy the contents of P， P S position。那度0。Because I own want to read what they。Of course is。

we can remove that。对。This changed。Work great。有咩对。Yeah， instruction point。From this point or two。で。

Right。Happ this。嗯我。エテシ。Size it was my I。s notてな。Pointer makes sense。别人的。P。嗯。G。

 we should probably send。嗯嗯。嗯。Let's send the reference。So the。Ebe is the square one。

Why is this happening。Thatpri。And think of size。If going to something。で。Yeah。

imply do all these other things。As well。With is P。It是安卓。It's a pointer。Yeah。皮。What else do we have。

 We have。is I thing。So来。Well， were only interested。我定。那Iピを。That's all we have here。So for the sake。

Every that。Flash this。Well。And we run。Okay，嘞。Sirl to the beginning。和。对。我。Okay。O。So。

 V is equal to this。偶。O equal to this P。Poins to this address， size is 0 from the beginning。

What is I P。Strange number。P， P is equal to the problem of。The address of。VM。Memory， but the address。

Yeah。Thank you。不ふ。Did this。Make a difference。嗯嗯。嗯嗯。Because V andM is。Re。嗯。这是这是。就是。Very weirder。

Because at this point， we should have done something in the memory， right。

Because we have read in the program， and down here。We can actually read from the memory。

Because that's what we're doing right here。And this is。Program。Sa不是。And the program。Yes。Which is。です。

And the virtual machine is allocated on the heap。So that shouldn't be the problem。

And we return the program of V and the end。Here we use the reference。But we tried both ways。

Because P is equal to the program。And you have already asserted。At V andM。Does contain something。

And from that， we copy it into the IP。Maybe it's different size。Yes， an op code is 6。D呗呢。

Type this in of。 Well， that's not really clear。But it's probably one by。So up is one bite。

 P P goes through by by mi。And we copy one by。Into theIP。We can even do IPO。Maybe that's it。

 but it should be the same because that is the top of the structure。

But you never know maybe an he doesnt optimizations or whatever。没。If we de reference P P。

 what do we get。If we reference。嗯。To you。Cha 네。This。Itする皮。Do。请问问。If we。8 bit So double H。嗯。So。

 P P is equal to one。Why can't we exchange that one。For a size。We have done that before。

The size is equal to the I P dot O。嗯。He is。嗯。我 the dragon the。Maybe it's something special with ems。

 What if we were to do IP。0？It's equal to。行て。Would that make a difference。



![](img/fe8ce403cf7cf58356ce32702c603a81_325.png)

Still running out of ideas here。Okay， no it works。 Okay， so that's some， but no。Still precious。

 but no it's。At least， doesn't。Go on forever。But it does a VM segmentation fault pretty。



![](img/fe8ce403cf7cf58356ce32702c603a81_327.png)

20。The only thing that can cause。Well， almost nothing can cause that at this point。

Only that the size is。Something else since want to， right。It's up guys， welcome back。

I think I have figured out finally why this is crashing and behaving erratically。If we look at our。

Virtual machine structure。And。And the memory， more specifically。The memory is a 65 k buffer。And the。

Lower addresses is the code segments， the text segment。And the higher addresses are the stack。

 which we have。Youil it。Then we have the brake line in between。But what is this。It's an address。Yes。

But what kind of address？It's not a member address in there。え。C program kind of way。

 like the processes general。Sense of memory。This is more like an offset inside of this。

 so it is a valid memory address for our virtual machine inside our virtual machine。

 because that's how our addresses look， there are 16 bits。But。In this sense。This should be an offset。

do this。Which means。That if we want to use this。Like we are using it right here。No。Wd。Right。

 like we did here before。Let's put this back。Let's make this a general。Kind of。And。

What word am I looking for。我。A generalral kind of。No。Okay， so let's see in me repeat。

We compare it to the VM。B。But instead of V And B， we should compare it to。Let's call it。Break。嗯。

And where else do we have this thing。So。Search for。Let's see。It's virtual machine。And the break。

So here is。This should be the。Okay。And then， we are here。So here we see， this is just a couple of。

one and two and such like that， so this break variable might contain like a six or something like that。

 we cant use that as a member address on its own inside of our general programs to speak。No， no。

 We need to add。A prefix。So， let's see。What we need is a。Program pointer。 Let's call this。 we had。

We had a name for it， right。7。It should not be a pointer。Should it。Should just be。要设线。Break。

What did you call it。Bak， get and drift。And what is the break address？Well， the break is。

The break address。It。The memory。哦。Our。没证行。Plus。The break。

So this is what we should have done from the beginning。Now， we can remove this sheet。St。And。Co。你。

This。IP。Oh， we can do it both ways， I guess。Lets do this。A little bit more optimized， I guess。

最西公s map b。Okay。So we remain clean them a little bit hereless。Do like。And then do make。不。Kme error。

Assignment。Makes intuitive， okay， same thing。And not the same thing。

 but the same error that we got before and got rid of。え。Because。Let's see Which one is the problem。

 V And B is just。And end you。

![](img/fe8ce403cf7cf58356ce32702c603a81_329.png)

R making team jump down a little bit to the screen， Run making。B， it comp。Let's see if it runs。

We still get a VM segmentation for， but that my。B。うい？嗯。Let me see how many iterations this loop does。

I think it does more than。It did before， because。Before it didn't。Really， do any。Or one。So。

 let's print the dots。At the it。

![](img/fe8ce403cf7cf58356ce32702c603a81_331.png)

0。Let's see。 We're comparing the address of the pointer。指して。Okay， now we have one dot。So。

 we might have us。A little bit of and off by one。Situation， I suppose。Lets。Type this out。

 At least we are farther than we ever were before。But let's see， in the first duration。皮皮。The point。

嗯。0ero1 EX， move to EX。Al yes， you mean。At this point。Or the breakers will be a constant。

It consists of the sizes of all the other instructions and what do we have， who have zero going？え。

And then， we have。The thing we are moving， which is 0。笑了笑了。0，5。And we have。Two more instructions。

Which means that the break will be five。And break address will be。The memory address。This right here。

And what will the address of P P be。Well， first， it would be this。Basically。This whole thing。

At the first iteration， then we will plus it by。2 by。 So if point here， it will one。No three bys。

 right。So。1，2。Okay， no one's pointing here。And。The break address is here。What't that mean。Let's see。

皮皮。Let's， that's。Do it like this instead。So x is pointing towards。1 to。3。Sppons towards the third。

With the be on K。He spoiling words。Plus。See。So it's this and 1，2，3，4，5。TheP is 3。

And this means less than or equal to this。Something is still great。

Let's print the values that P is equal to0 x x。Or maybe we should just。いて here。And we do P。嗯等。え？

And this， we will do。どす？え。嗯。just。🤧TheP takes。And here we'll take the value of your K address。对对。

As an integer。AndWhat will be the result。そ。Just to separate it a little bit。



![](img/fe8ce403cf7cf58356ce32702c603a81_333.png)

我我0 get。So。Let's see。 the P is pointing towards this address。



![](img/fe8ce403cf7cf58356ce32702c603a81_335.png)

嗯。It's very weird。We do need new。

![](img/fe8ce403cf7cf58356ce32702c603a81_337.png)

So the PP is pointing towards this address。In the B RK。Okay。The variable that we created is only。



![](img/fe8ce403cf7cf58356ce32702c603a81_339.png)

Is only 16 bes。 And the addresses on a global system is。It's 32 in this case。So。What we need to do。

Is。We need to make the see。We need to make this is 32。对。Thing。And instead of doing in 16 right here。

 we will do。点。Do。人哋隧到你的。Oh。うう。Same here。月シピ？嗯。AndThis should be。As is。And now， ladies and gentlemen。

I believe our program is going to work。I can feel it in my toes。O。诶。Didn't。No， it didn't run。

It didn't do any iteration this time。Maybe we should。てです。Put it here， as well。嗯。B业。Bay。



![](img/fe8ce403cf7cf58356ce32702c603a81_341.png)

Okay， so this is the address。And BRK is still third16 with think why？Y o。Because of this。Okay。

Let's do it again。Okay， let's see。 So we have this address。This is the P， P。And。The break。で。

They are pretty similar all the way， but。This。Is。The tiny bit bigger。Quite a lot bigger。Too much。

Let's check the difference。能O。So，7。And then we have the next one。So this is the starting point。

And this is the same， I guess。有。And then。The Lou exits。



![](img/fe8ce403cf7cf58356ce32702c603a81_343.png)

K乐。Let's make one of these。So this is just before the next。Iteration。



![](img/fe8ce403cf7cf58356ce32702c603a81_345.png)

So， A， N B3。And it's AC and B3。So， it's the same。It doesn't change from。我的视频。We have it before。

 the little bread。Which means。So this is what happens before we get to the loop。A AC M B3。

This is happening inside the Lou。

![](img/fe8ce403cf7cf58356ce32702c603a81_347.png)

Okay， so it's。Existiting。Here， somewhere must be inside of the exit instruction。

And that can only be because。This size fails。And where does the size fail。Because。

It's not able to grab。The IO。Let's also。Print。P皮。And let's print both of these as。

As a one bite Hexedadeimo。Yeah。う。S。品？AndLet's make it。So。I know。Great good。s right。No。那之类的是。

All right， now well get a little bit more information。If we manage to put the semi correctly。



![](img/fe8ce403cf7cf58356ce32702c603a81_349.png)

Okay， so the P is one。 the iO is one。这肥了。我s天。It can only mean that the size is failing， right。So。

 let's check that。Well。都他一大头的卖了点。And the she背的。you as well。The size is 3。Still。

 we get this segmentation fault。And we get it。It must be coming from the exit construction。

 And what are we sending to this？We're sending the reference of。Destruction。Whenver to the machine。

What is the。Definition of this function。Be an instruction star， okay。And what does he do？It。嗯。See。

It takes the。Saize。So it does another map called。That's not very optimize， but never mind。

And it should be able to grab。Besides that way。But is it。What if we were to cheat a little bit？

And use one of the new sea features。So we can send the entire contents of a structure。As a value。

To function。So no pointers at this point。Mhm。Let switch on the。对哦。First off this。

Does this make a difference。So in this case， in order call this function。it太。Here somewhere。Yeah。

So now we send the value of this structure instead of the reference。



![](img/fe8ce403cf7cf58356ce32702c603a81_351.png)

K能 one。Right。That makes the signature。Slightly different。Which means we need to update our dot H5。

Ex construction。た。forgot。And that is some 36。So this should also just be a top。

Let's see if this negative。So don't think it should。 but who knows。The bill is one， size is 3 exit。嗯。

This I say。对。いう。你可的嗯。Let's also shake。Size。Same as we do at the other end， but。

We need to know if this is no。Transported。Correctly。So。do something like啊。



![](img/fe8ce403cf7cf58356ce32702c603a81_353.png)

And we have an eye of one and a size of three。 So it's not that that causes this thing。

 and we are switching on the sides。And the size was， what was it。再说。3。We shake for one and2。

 and see a row。For one and 2 and 0。We should。Remove this。And谢 for。It。It can be one。Or two。3。

Let's see。If it's2。This is what we do。If it's three， this is。Let's keep。す？As well。Or not zero。

But one。这被。Okay， I feel you're confident now， I can remove all the printers。Annoying little thing。

 right。But， that's。That's coding。can remove。Yes。This。ス験拷ーマンです。Yes。对。Clean move down a little bit。

 clear the great brown bake and。

![](img/fe8ce403cf7cf58356ce32702c603a81_355.png)

Okay， it's still same。 but， but it's not the same thing。 now I。Think the of by one situation is。

Is occurring。Which is a little bit more anticipated。



![](img/fe8ce403cf7cf58356ce32702c603a81_357.png)

嗯。走了只我他笨死人。😔，A FB 3。Be 0。Be嘴。So we can go for A F。G be 0。That's one increase。And then it will。

Increase。外湾。As well。I have two many of those now。This。AVery interesting。Interesting。And。

The end of it。Interesting。And we have A F，B 3， B 0， B3。So this is the state。

When it decides not to live anymore。But， this is still。



![](img/fe8ce403cf7cf58356ce32702c603a81_359.png)

Lower。对。And that's right。What about this， If P， P is not equal to。cold holds。

So if it's equal to up hold。We should still around this one more time， O。

So let's move this thing down here。Let's just do as we did before and put a do here。

And this basically means that we are going to run this no matter what and then check the condition。

And that is probably what we need， I think。

![](img/fe8ce403cf7cf58356ce32702c603a81_361.png)

So A F， B3， B0， B3， and then sec fold。

![](img/fe8ce403cf7cf58356ce32702c603a81_363.png)

I need one more thing。 Let's put in。Kind of se thirsty here。So we know when it starts。



![](img/fe8ce403cf7cf58356ce32702c603a81_365.png)

Maybe I should call this a course of troublehoing instead。Okay， so here。It starts。 Here it ends。

And then it dances。可。Don't want to have this as。Let's just make a brief statement that handles that part。

嗯。We already have one。And where should we put it。As soon as we。Tryries to execute。An instruction。So。

うね。Well， it doesn't matter。 We can have it here。一个。So， if this。Memory address。嗯。Letsten。

If this member address is more than it be O。Then we say fault。Otherwise， we do all this stuff。

And we know。As long as。We have this thing at the bottom。 So this。

Mixing up or changing up or the wire loop doesn't do much。h。P， P because see was the size。

Can't we have that in the beginning instead。But I don't want that to happen。 the first iteration。

I can do this though。Its size0。 It's already0，Size equals 0。So at the first iteration。

 we will not add anything to this。Then we do this， and we check this and this and this and this。

And we update。The instruction pointer。Maybe we should do that at the same time。

And we update size as soon as we have read。Instruction， okay， this makes sense， I think。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_367.png)

L。I must miss some kind of。Yeah。嗯。Did the function really end here？I can't remember。

But I can control Z， and I can go back。Yeah， can。So， let's just do。嗯。です。There was itss this。

 It's the。出に。Or yes did it。And fingers crossed。Mium水。We didn't get any print this time。No than this。

Yeah， we did get that。So， this happens。And this。I P 0，2。P p。And if。This， P。

Maybe we shouldn't have this。That could actually be there。Yeah， here we go。All right。

So it's a little bit tricky when with all of those poems and stuff。So okay。

 let's clean this up a little bit。嗯，对这里。Do。Thisす。嗯。And what do we print。We want execute。

 then we want to pray。this。你 did。And then we will put it in manually somewhere just temporarily so we can see what's really going on。

😔，Perhaps inside of the error。Because we are doing this system hold kind of thing。

So why not use it for。Displaying the contents。Our A X register。And if this is5。

 I am celebrating with champagne。

![](img/fe8ce403cf7cf58356ce32702c603a81_369.png)

No。No。It's different each time。

![](img/fe8ce403cf7cf58356ce32702c603a81_371.png)

Which suggests that it。Hasn't been the altered。We are going into the VM and doing a extra。

We are executing this move。And。Going into the Vm。 we're setting the A。2。😔，Argument， a1。

And this is a 16。对。整。This is。How big is an argument。 I have moved it around。嗯。嗯。We are so close。Okay。

 and the as is。In 16。We're callingly move。Let's be from this。It instruction。

We'reically move by the VM， the op code A1 and a2。And A1 and A2 are set。To。0，1 and 0。

Or0 n1 in this IA， so inside of the instruction。There is an argument。And we2。Using them like this。

And we only have。When are。No， we have。2。😔，Let's see。 our instruction is one。

 and then we have one additional argument， which is 16 bit thing。So， it will still return。3 bys。

A 1 is equal to a 2 is equal to 0。That's interesting。 We are 0 initializing them。Which means。

It is set， but its set right wrong。So the argument is not pointing to the right place。

And where do we copy the argument。See。Right， we are only。 yeah， we change this， okay。

So what we should do。After we have。个等记。Size。Is。你 should科别。超地超地。IP。그래 안 돼。St bites。

You should copy from。P屁。Should。We don't need to。I like so。Okays we can just。Refer。

As long as we tell that it should。I enough talking。All right， let's try this game。そ明き。いめっちゃたまるけ。

Clill the screen， and we're running。Like so。And now we must it up again。P表情。This hasn't changed。

Besides。We get from this。Weird。What it will keep is， does it make difference。No。

What if we change that could cause this to happen again。If P， P isn't equal to。不可能。😔，By the way。

 I don't think we should。Compare the P， P。Better way would actually be to。To compare。嗯。

To compare the value of。By P and BR K directly。So is。If the instruction puller。Its more。Then。The V。对。

English cell forth。But I don't think this would。Difference in this。Sense。The size will be 3。

 So we copy it 3 by it。From our。B dream。We you execute that。你 shake that is好。We increase by size。

this again。い the chair。I'm not even sure what I did that could mess this。



![](img/fe8ce403cf7cf58356ce32702c603a81_373.png)

Thank天。We were always。We're almost done， right。嗯。一し？Instruction pointer。Yeah。Still了。

We only see the red here。And here we see。Right so worsem。What did I change。

The only thing is is I use this。颗对。て。That's really something thats will。I this in this kind of way。

No， so what else did I do。What else did I do。H。Okay， so let's control that that。Until we get this。

Run again。Kid。So this verse okay in the same。This annoying cat I hate it。Yeah。Okay。See。Okay。

 so this version should run。Sytister号。So， why does。The change I did。嗯，那事啊。Possible to。Yeah。

So we have this print that's wont change anything。嗯我。We heard this copy。It just didn't seem to be。对。

So， at this point。Should still work， right。No。Okay， so the copy does change this， right。有冇嗰边。嗯。

This it were。No， we do get it。But why does the copy。

Why that's the proper result in that kind of behavior？Do we override them。Important thing， perhaps。I。

It should be a flat structure。对。I he。哦。Maybe it's this inum thing again。

They must be saved some weird way。Inside of the memory。I that it。So， let's not copy the enum。

There could be any too。LetSee。The address。哦。嗯。IP。Plus world。Or how big。It even。

 I don't know the tired。But we do have the total size。This is someone by。

So this is a destination when the source is。我这会。P， P is spoil2。And we want to cook。Size，-1。嗯。

What happensapp when we run this？Well， it doesn't break。This time。



![](img/fe8ce403cf7cf58356ce32702c603a81_375.png)

You should go to this。 A 1 and a2 is equal to 0。Can we perhaps print our arguments and stuff。

So what do we have VM？And we have the instruction。So， we have I do。哦。Let's just do regular numbers。

 now。And we have I。呃。0。And we had。 I got。Ogs。1。I don't know， we have。哎 know。Or。嗯，所以说。We have idt。嗯。

Okay， this will give us a little bit more info information。So。Okay， so the second argument is。

Empty all the time。But。And it looks。Kind of okay。We were on the second time。The one is okay。

 And then we have2。And in this case， okay， we don't have any argument， right。아 좀。Let's see。你。

Upcode 1。And this weird argument。We have up code 2， and then we have a two in the argument。

And then we have up code 3 with a0。Very weird results。嗯。Very weird results， indeed。

But we should only do this cop that。サズ。我gan one。Let's do this。 and let's all soak at the same time。嗯。

你个。

![](img/fe8ce403cf7cf58356ce32702c603a81_377.png)

So either can see the difference。Times， it's gone。Okay， so we have a one。And we have a two。

Thats the argument。The two is there。Every time。S it two。Where does。To come。Okay， it probably okay。

 it probably comes from。It must come from the second up code to where off by one。嗯。C。Okay。

 let's just。It's just do I， But we did that before， didn't we。This feels intuitively。Ro。

But what are we cooking fed。P。Maybe we should keep this。别克缤纷PP。If we should take it once。明呢。

But then women my my running to travel the first time。But let's try。So， we have。The world the two。

吹我吹。Am I displaying this。Bad。😔，还有。小爱 si。😔，I won send the whole instruction。Yeah。

TheS is more than one。We could to the structure。Poion。Are we increasing this。Incorectly。

The first time size is 0 second time， size should be 3。A piece。3 bigger， P。뒤 big 길。嗯。

Then how many invite we caught being。3-1。 We're cooking two bite。I don't know what I'm doing， right。

I don't see the logic in this， too。Where does come from。I哦。I a Sarah。So what if we just work to do。

I a0。Is equal to。一个す。That's the first 16 bit number。系。え。1。Should be good to。P plus。3。We don't have。

 We have an argument for that。This doesn't matter。And this should only be done。See。我的想。

I'm copying this。Donown here。Then they executing the instruction。Stulation。Right。Why don't here。

Because I need the size。对。The last position。嗯。We know this for no。See。We need the size for this one。

嗯。All right， I'm not really sure what I'm only doing anymore。 Let's see。啊可以。Its undeclared。

 So okay what's its name then。BIP。P， what just called this P， P。Sometimes you get into this。

Kind of song where you just feel like everything。Even though you know this。てるです。Weird too。

 everywhere。Doesn't seem to make a difference。Whatever I put inside of my code。It's always this， too。

Pautiful， just。Don't care about this。struct at all。Let's move all that stuff。And reference this。

 instead。And here， we will just give。This Supreme别。Sa many anyway。Let's just do something different。

 right？So， instead of an instruction。We think you have a。うん。1。いつも。Instead of。Oh， we will just do。T。

And in case。When。We will set a。く。Because one。The same here will set a2 to be equal。P plus。Re异。

Let's update our。Our signature。And this would be a programme star， okay。

So now we're doing the same thing， but in a different。诶喂。It always still connected by the way。うす。26。

For I will need to switch for。Same here。Instead of I O。11。And what happens now。Same， same thing。嗯。



![](img/fe8ce403cf7cf58356ce32702c603a81_379.png)

Okay， guys， now I know what's wrong。

![](img/fe8ce403cf7cf58356ce32702c603a81_381.png)

And as I expected， it was a very stupid error that I have troubleshooted for a long time now。

If we go to the error function。Where I will print the value of the A X register。In the V。

This sentence。After I already have deleted the wheel。Pretty lame，hu。 So if I take this code。

And I put it down here， instead。And这。Well， and just save。



![](img/fe8ce403cf7cf58356ce32702c603a81_383.png)

So if run make clean， jump down a little bit。 clear screen， run make。And this time。No。0。Okay。

 so where is one step closer。

![](img/fe8ce403cf7cf58356ce32702c603a81_385.png)

你死。So now we get a zero， then we want the five， right。Fian， freeian。And this happens before。

Then we go into the register。This looks right。How does this look。I think we are pretty close now。

 A one is peopleless one。To。嗯。See when we run the。We we run this。Whats的。Inside of the。And。

Even the parameter。

![](img/fe8ce403cf7cf58356ce32702c603a81_387.png)

K doesn't run the move。

![](img/fe8ce403cf7cf58356ce32702c603a81_389.png)

为呢。see， execute instruction， okay。The it。Okay。This is moved。You need to do the actual call well。

Send V m。卫生地。😔，嗯。Let's see。第二 code。Poing to by。皮。We send。Are one and possibly our。

I think we got them all so VM upcode Args。BM of口罩。

![](img/fe8ce403cf7cf58356ce32702c603a81_391.png)

No， I believe it will work。Yes， no it finally works。So what we did was we ran and。Our program。

Which will move a5 into the A X register。 It will do no app。 It doesn't do anything。

 and then it will halt the system。And then we get this。嗯。So our virtual machine works。

The only thing we need to do is add more functionality to it。And basically add more instructions。

 for example， I want to get the stack up and running so we can save data onto the memory and also I would like to add so we can move things not only from。

From the static numbers， but from other registers and from the memory as well。

But this is all for today， if you like this episode and wish to be notified when I release a new one。

 please like and subscribe。And also， you can enable your notifications by clicking the bell inside of YouTube so you get an email or similar。

Whenever I release an episode， which is usually。And during the night， every fourth day。

Central European summertime。All right， exciting project。 would be。

 it will be interesting to keep following along here。Thanks for watching and thanks for today。



![](img/fe8ce403cf7cf58356ce32702c603a81_393.png)