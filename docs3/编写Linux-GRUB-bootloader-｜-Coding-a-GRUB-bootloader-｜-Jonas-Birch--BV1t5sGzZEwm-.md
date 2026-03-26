# 编写Linux-GRUB-bootloader-｜-Coding-a-GRUB-bootloader-｜-Jonas-Birch--BV1t5sGzZEwm-

When the computer starts at。After the bios has run all the hardware checks and initializations。

 it will boot the computer by reading in the first 512 B from the disk into the memory location 7 C 0。

0， boot sector consists of 3 different things。 First， we have 440 B of code。 Our boot loader。

 Then we have the partition table， which consists of 4 entries， one for each partition 160 by each。

 Finally， we have2 by with the signature 0 x A A 5，5。

 and that is so the bios will know that this is a valid boot sector。

 So our boot loader will need to go through each partition。And check the boat old flag， if it's true。

When it finds a partition with the bootable flag， then it will check the CHS start field that is the coordinates。

 so to speak， the hardware location under the Part tribe。

Where we find the operating system and our job is to copy the first 512 by from that location to the memory location 70。

0，0。And then we can boot the operating system。So let's get started。



![](img/9764a1b27c27c31115c7b182ba11ec48_1.png)

So guys， welcome to today's show。 So today we're going to create our own Bo loader to load Linux。

And I'm going to call a。ItLook。Boot。老汁。And that's short for Linux built loader。

So let's first take a quick look at ourbo loader。Is organized。It's 512 by。

AndAnd the first 440 is the actual code that runs。Then we have 6 bys of optional values， which。呃。

Are usually not。Used， or it's not necessary to use them。If we can't fit our code inside of here。

 it's possible to use these6 bytes for code as well。And then we have the partition table。

So we have 16 bys for each partition up to 4。And then we have two bytes at the end with a signature 5。

5 A A， which tells the bios that this is a valid bootloader。All it so how does this。

 this partition table look。Yeah。It contains a different kinds of stuff。

 The important stuff is this first one， the drive attributes。And that。Most significant。

 most significant bit。If that is set。That means that this partition is boable。

 So we need to check and find the first。Botho the ball partition and use that one to boost the system。

And then we have the CHS address， which is the location physically on the hardest describe。

 where the。Boot code is located。So we need to read in this stuff from the hardestscribe and。

Let it load the operating system。Then we have some other stuff here。

 which isn't really necessary in our case。嗯。All right。

 And we need to perform three different operations。First， when they boot。TheLoer is initialized。

 The bales has copied it to the location。7 c，0，0 inside of Ram。All the way through to 7 E。F F。

That's 512 by。So what we need to do is we need to locate the boostable partition。

And use this CHS address to read in from the Hardyscribe，512 by of。The boat called。

 starting at the position here。And we need to copy it to the same location，7，0，0。

And then let it boot the system。So you might notice that we have a problem here。

We are located at this address， and this code needs to be at that address。 So it's a conflict。

So the first thing we need to do when we start our boat loader is to copy ourselves somewhere else。

 And that's called a re low。relocating。So we can copy it basically anywhere inside of the Ram。

 I'm gonna copy it to 7， a。0，0。 So we have plenty of room。

Because I want to use this address as the base of this stack as well。 And I don't want it to。

Conflict with each other。So this is a good e enough way。So we need to copy the entire bootloader。

 including everything into this location and then reload it。So we start from the beginning。

 but at this address。When we。Execute the code the second time。

We need to know that it's a second time so we don't start copying ourselves all over again。

And then we can start reading from the hardest drive。

 copying this stuff to this location and let it boot the system。So， that's basically it。And。

This gives us some trouble， because if we make our code。Use this as the base address for locating。

Variables， for instance。It will only work the first time we're on the code。

 then the base address will change and our code will remain the same。

 which is a problem in some cases。 so we need to take that into account also。

But we'll cross that bridge when we get there。

![](img/9764a1b27c27c31115c7b182ba11ec48_3.png)

So， let's start by。Setting up a project， I'm going to create a folder called looks。

And I will go into it and set it to my home。And I'm coding this on my Linux server。Remotely。



![](img/9764a1b27c27c31115c7b182ba11ec48_5.png)

And I'm going to launch A VS code remotely through the sociopath SDP client so I can edit the files remotely。

So I'll take this looks directory right click and open an editor。So each time I save a file。

 create a file or create a directory， it will automatically update on the server。Mmhm。😊，Okay。So。

Let's see I we gonna structure this。 I wanna have a。A main assembly file。

 which I'm going to call looks dot asm。And all the。Both loaders。

And needs to be coded in 16 bits assembly。Because the computer always starts up in 16 B mode for compibility。

嗯。Right。So let's also create a make file so we can compile this thing。So， let's see。

We want to create。Maybe we should start with some flags。

We're gonna have some kind of flags and some kind of linker flags。

I also want to create an include directory where I can have some include funds。To choose new folder。

 So let's call this include。And in order to set the include path。 So we， we just can say include。

5 dot H， for instance。Without specifying path and so on。We need to set an environment variable。

Which is called。And asm end。And we w to set the dash。I for include。

And we want to provide the include directory like this。

 And we need to export this environment variable。 so it will be。Part of the rest of the file。So。

Let's see。嗯。So， we want to create。A looks dot O file out of looksdot am。

And in order to assemble this， we run anm。With some possible flags。

And we provide the input file like this。When we have that。We w to create the。Binary。So， first。

I w to create an L file。It's not necessary to take that step。 but if we want to include other stuff。

 it makes stuff easier。So I wna create a looks dot F。Out of looks dot O。And I'm going to use linker。

With some。And。With some possible L flags。And we w to take the input file。And create an output file。

Something like this。And。When we have the L file， we can create the final。嗯。Binary。

 which I'm going to call Bo dot Ig。As an image file。And this requires looks at health。

And I'm gonna use object copy。Which is a command that transforms between different。Exeable formats。

By the way， I wna remove。The executable flag on this。E file。So， I wna cook it。The source file。

To the output file like this。Or no， not to the output file。Let's take an intermediate step。

So let's say we have a look at bin。And I want to make sure it's 512。But。Or a multiple thereof。

 So I'm going to use the truncate command。Then say that this should be a multiple of 512。But。

we fill it out with zeros， if it's not。The correct size。嗯嗯嗯。And to the object copy command。

 we need to supply。

![](img/9764a1b27c27c31115c7b182ba11ec48_7.png)

The source and destination formats。SoLet's check the help file for this。 O Co hell。

I think it's I and O。Yes。I for the input format and O for the output format。So， we can do。

Oshdam Prash Heop to see the different formats。And。I'm gonna make it a 32 B。



![](img/9764a1b27c27c31115c7b182ba11ec48_9.png)

Elf binary。So this would be the input format for Lux do L。And the output formats。

Will just be a flat binary， so。Machine code instructions only。Alright， I think。This is okay。And then。

 I need to。Do some other stuff。 But I think we can wait a little bit with that。So， let's just。

Rename this。Looks the Ben。To the output format， boot them。Something like this。And I wna have a。Clean。

 directive。Which will delete all O files， all image files， or L files。Yeah。

And since this clean directive doesn't produce any output。We need to declare it as pho。And finally。

 we'll have the all， which we just create。Boot dot in。Allright， I think this is correct。Let's。

Put in some stuff here， just to test it out。嗯。Well， we can just do。Something like this。



![](img/9764a1b27c27c31115c7b182ba11ec48_11.png)

And let's see if it compiles。Yeah。

![](img/9764a1b27c27c31115c7b182ba11ec48_13.png)

嗯。Okay。We need to specify the output file for the。And some command， as well。



![](img/9764a1b27c27c31115c7b182ba11ec48_15.png)

雷生。😔，嗯。F not。

![](img/9764a1b27c27c31115c7b182ba11ec48_17.png)

Recognize。Maybe we need to add the。Flas and say that。Let's see。 Ana dash F。



![](img/9764a1b27c27c31115c7b182ba11ec48_19.png)

Elf， I think。

![](img/9764a1b27c27c31115c7b182ba11ec48_21.png)

And it complains that we didn't export the start label。嗯。Global。



![](img/9764a1b27c27c31115c7b182ba11ec48_23.png)

Now， I believe it should work。Yes， no errors。And we have this booth of Iig， which is 512。Bits。

 and I have created an alias Ob shaam。8 to6， which you can copy。It runs the object jump。

 which is a disassembler that takes a binary executable and shows all the binary machine instructions。

And I have configured it to run as I8086， which is the 16 bit。E platformlaform。

So I can just run obdm。86， B dot M。And I get。

![](img/9764a1b27c27c31115c7b182ba11ec48_25.png)

There isasse here。By the way， I don't want it to be green。So。See。s do。😔。



![](img/9764a1b27c27c31115c7b182ba11ec48_27.png)

Similar with this file。Alright， so now we have the basic set up， but we need to define how the。

How the image file should be organized。

![](img/9764a1b27c27c31115c7b182ba11ec48_29.png)

Because there are three different parts。We have the code part。And this， I will skip for now。

 so we will just leave it。As 0。But we have the boat code part。We have the partition table。

And I will just add some dumbmy stuff here。For the time being， then when we run this for real。

 we need to copy this from the primary hardest drive。 So we have the。Current partition table。

And then we need to have this two byte signature at the end。



![](img/9764a1b27c27c31115c7b182ba11ec48_31.png)

So the easiest way to organize this， I think， is to create an LD script file。

So I'm going to call this look dot LD。😔，And I'm gonna choose。Not a plain text， but a linker map file。

So， okay， so we need to define three different things。 First。

 we need to tell it what the output binary format should be。So， we can take that from。Here。😔，So。Oh。P。

Format should be。This。And then we need to define the different memory areas。

So the first thing is our booth loader。We need to define some flags for that。

 And this is gonna going to be read only。Excutable。嗯。Allocated， and。Initialized。So basically。

 this means that we are going to use this and we are going to fill it with zeros if we don't use up all the space。

O。So first， we need to define the origin。The origin is where this code will be in memory。

So it's gonna be 7 C，0，0。And then， we have the。Size， I believe。



![](img/9764a1b27c27c31115c7b182ba11ec48_33.png)

So。We need to。Go all the way down to。

![](img/9764a1b27c27c31115c7b182ba11ec48_35.png)

This。来声。And then we have the partition table， P table。 And this is going to be read。He I。

The origin is going to be。

![](img/9764a1b27c27c31115c7b182ba11ec48_37.png)

We start here。So， we need to take。This origin， M plus1 B， E。



![](img/9764a1b27c27c31115c7b182ba11ec48_39.png)

So， basically， it's going to be 7。D。😔，Be。Since this is 7 C， this would be 7 D。



![](img/9764a1b27c27c31115c7b182ba11ec48_41.png)

And the size of this。Is。16 times 4。

![](img/9764a1b27c27c31115c7b182ba11ec48_43.png)

So。😔，That's its that's 64， by the way。 So let's， I have some alias for。

Conversing between hex and decimal。So0 x 4 is 64 by。And this hex。

Is just the print death that turns it into hes。And I also have a deck alias to turn his back into。

Yeah。

![](img/9764a1b27c27c31115c7b182ba11ec48_45.png)

Deimal form。Right， so the size of this is 0 x 40。And finally， the last part， which is the signature。



![](img/9764a1b27c27c31115c7b182ba11ec48_47.png)

The origin of this。Yes。0 x at。0 x，1， F E。

![](img/9764a1b27c27c31115c7b182ba11ec48_49.png)

So。嗯。

![](img/9764a1b27c27c31115c7b182ba11ec48_51.png)

7。D。😔。

![](img/9764a1b27c27c31115c7b182ba11ec48_53.png)

F。And the size of this is just2 Bs。So this is the memory layout。

And then we're gonna have the sections as well。And the sections。嗯。

Is this usually when we code something like this， we do section dot text， for instance。

 And there we put all the code。so we need to take all these sections and map them to these memory locations。

So let's begin with the bookloader。And the boot loader should contain。All files。

That contains the booth loader sections。And this should be part of the boot loader memory location。

And then we take the partition table and do the same。All files， and。啲。Practition table。And finally。

 the signature。I don't think we should have called。 Yeah， wish。对，徐磊。Then we have the signature。

 and we do the same here。And that's basically。Now， we need to add this file to the make file。LD flag。



![](img/9764a1b27c27c31115c7b182ba11ec48_55.png)

And I don't remember how to specify script file。 So I'll do。This。Y。D tea。



![](img/9764a1b27c27c31115c7b182ba11ec48_57.png)

Something like this。 And we need to create those different sections inside of our code。So first。

 we will have the actual boot loader。Then we will have the partition table。Then， we will have。嗯。

The signature。And the signature will just be。This here。So， I'm going to。See。Lets say。

The label signature。And。😔，We define a word。0 x。A A 5，5。



![](img/9764a1b27c27c31115c7b182ba11ec48_59.png)

So here it's in the opposite direction， but here with specified bite by bite。



![](img/9764a1b27c27c31115c7b182ba11ec48_61.png)

When we specify it as a 16 bit integer like this， we need to flip those。And the partition table。

For now， I will just do。Something like this。And say that the this is。We will have 64。Sereros for now。

And the boot loader， let's just have our start label。And our no。



![](img/9764a1b27c27c31115c7b182ba11ec48_63.png)

Alright， let's see if this compiles。M syntax error number line number 6。



![](img/9764a1b27c27c31115c7b182ba11ec48_65.png)

Okay。😔，Let's go to the main page。It's always difficult to remember all this stuff。 So L D secret。



![](img/9764a1b27c27c31115c7b182ba11ec48_67.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_68.png)

Name。😔，Origin length， okay。So， let's do。This。

![](img/9764a1b27c27c31115c7b182ba11ec48_70.png)

let's try this again。TheMe region。

![](img/9764a1b27c27c31115c7b182ba11ec48_72.png)

loader。No。😔，Declre。I forgot。We need to assign this。To the memory region。This。And like。



![](img/9764a1b27c27c31115c7b182ba11ec48_74.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_75.png)

Bookload are not declared。

![](img/9764a1b27c27c31115c7b182ba11ec48_77.png)

嗯。

![](img/9764a1b27c27c31115c7b182ba11ec48_79.png)

哦。

![](img/9764a1b27c27c31115c7b182ba11ec48_81.png)

Boot loader。Sign will not fit in region。P table。

![](img/9764a1b27c27c31115c7b182ba11ec48_83.png)

Mm。Pable length。Is this。😔，Section P table，64。0al。And then we define a word。Then。F1。嗯。Yeah。0 D B E。



![](img/9764a1b27c27c31115c7b182ba11ec48_85.png)

C d。

![](img/9764a1b27c27c31115c7b182ba11ec48_87.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_88.png)

What does it say exactly。The section dot sign will not fit in regionent P table。



![](img/9764a1b27c27c31115c7b182ba11ec48_90.png)

We're trying to put it inside of the sign， right。Section sign。no no。



![](img/9764a1b27c27c31115c7b182ba11ec48_92.png)

He这。S。Orig and。你。

![](img/9764a1b27c27c31115c7b182ba11ec48_94.png)

What am I missing here。They the boot loader。At the P table， we have the sign。Goodloader。Goodloader。

P柴布。😔，PK。😔，Oh， I have aduct here。

![](img/9764a1b27c27c31115c7b182ba11ec48_96.png)

Small errors。 His hard fine， sometimes。Or locate。Okay， now it looks better。So now we have this file。

 And if we do an ob dump。We should see。That we have。The no up at the first position。

And then we have a lot of zeros。All the way to the signature。At the end。



![](img/9764a1b27c27c31115c7b182ba11ec48_98.png)

Okay， that's good。But in order to see that， it actually is。The correct format。

 we need to define this P table。

![](img/9764a1b27c27c31115c7b182ba11ec48_100.png)

Li a little better， better。So。I'm going create a structure。Which has this format。

 So it will be organized and easy to。呃，行。

![](img/9764a1b27c27c31115c7b182ba11ec48_102.png)

So， let's create。Inside of the include directory。I would create a looks do。8。

And I'm gonna define that this is an analysis file。And the structure format。

 for assembly is a little bit。

![](img/9764a1b27c27c31115c7b182ba11ec48_104.png)

Difficult to remember。 So I'm gonna。

![](img/9764a1b27c27c31115c7b182ba11ec48_106.png)

Mual。So， an。

![](img/9764a1b27c27c31115c7b182ba11ec48_108.png)

No， not this。Let's copy this。And use as a reference。



![](img/9764a1b27c27c31115c7b182ba11ec48_110.png)

So I want to create astruct。Which I'm gonna to call partition。



![](img/9764a1b27c27c31115c7b182ba11ec48_112.png)

Let's see what we're gonna have inside of that。First， we need these attributes。



![](img/9764a1b27c27c31115c7b182ba11ec48_114.png)

Attributes。Maybe just like this。And we wna reserve。By。1， but。



![](img/9764a1b27c27c31115c7b182ba11ec48_116.png)

Then we have three bites of the star thing。

![](img/9764a1b27c27c31115c7b182ba11ec48_118.png)

Pos， let's call this start。Resspite。3。Then we have one by Ti。



![](img/9764a1b27c27c31115c7b182ba11ec48_120.png)

嗯。Then， we have。3 bys of the last sector。

![](img/9764a1b27c27c31115c7b182ba11ec48_122.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_123.png)

And then we have the LBA。 The LBA is a different format。

That uses a linear scale instead of the CHS format。嗯。We are not going use this， though。

 but let's add it anyway。

![](img/9764a1b27c27c31115c7b182ba11ec48_125.png)

So this is going to be the LBA， and this is one。D word。



![](img/9764a1b27c27c31115c7b182ba11ec48_127.png)

Which is 4 Bs。And finally， another D word for the number of sectors。



![](img/9764a1b27c27c31115c7b182ba11ec48_129.png)

So， number of second。Another deal。strike。Okay。So now we have defined the actual format of this。

By the way， this is not 32。 This should be 16。So inside our main file。What we're gonna do is。

We want呢。Include our。age。And inside of this partition table， we want to create four different。



![](img/9764a1b27c27c31115c7b182ba11ec48_131.png)

Structure instances。And， in order to create。An instance。We use this eye struck directive。



![](img/9764a1b27c27c31115c7b182ba11ec48_133.png)

So， let's。Paste it in here。So we're gonna have our first partition。Which is an eyestr。Politician。

That's one we defined。And since we。Are only going to fill this with bogus values。

 We don't have to go through every different part of it here。Yeah， I will just say。Pition。

We wanna reserve。Let's see。Let's do it like this。Let's do 64。But。Where we have the。Nmeric value 1。

I am。So。Let's create。For this。This will be the second。And let's fill this with twos。So， we can。

Find it easily。And we do the third。嗯。And July July the fourth。So。😔，Something like this。Maybe we can。

Make it a little bit tighter。Alright， let's see if it works。



![](img/9764a1b27c27c31115c7b182ba11ec48_135.png)

H。Times value，-48 is negative。

![](img/9764a1b27c27c31115c7b182ba11ec48_137.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_138.png)

嗯。

![](img/9764a1b27c27c31115c7b182ba11ec48_140.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_141.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_142.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_143.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_144.png)

Maybe we cannot use times inside of a structure。Let's， instead， define。We can define。A of D words。

So age should be 6 by the way， not 64。Maybe that's the problem。64 is the total amount。

It should be 16。St去了。

![](img/9764a1b27c27c31115c7b182ba11ec48_146.png)

Okay。Still looks right。 and lets you an ob dump。So inside of our book loader。

 we still have the no up。And then， starting at1。B F。1。Bd。



![](img/9764a1b27c27c31115c7b182ba11ec48_148.png)

Let's look at this。

![](img/9764a1b27c27c31115c7b182ba11ec48_150.png)

one。😔，Be。Okay， I think it's the correct。 Probably we have a lot of zeros here。 and this starts with0。

So。Yeah， so this 0 is not part of this。 Actually， it's part of the rest here。

 So we should start at 0，1。At 1， B， E。1， B， okay， that's， that looks right。

And it goes all the way down here。 And at last， by it， we have the 55 and the A A。 We don't。

 This to the right here is just bogus because。It trying to interpret this。As machine instructions。

 But this is just data。What can do is a hex dump。Of this boot file。And here we can see。

Here we can see if you go to 1 B 0， this is the 0。1，2，3，4，5，6，7，8。9ine。😔，ABC D E。So， it looks right。

Okay， so now we're done with the partition table。 We are done with the signature。



![](img/9764a1b27c27c31115c7b182ba11ec48_152.png)

And no， we're just。Just。Need to code our boot loader。So。Let's see。m。I wna have some function。

 which writes to the screen。It will make。Debugging a little bit。Easier。So， let's start。There。

So let's say we have a main label。Where we want to start up。 So inside of the start。

 we jump to main the first thing we do。Then we can put our other functions。on top here。

So I wanna have a function， which。Take a string。And writes it to the screen。So， let's say。

Let's call this print。First， we want to initialize our stack frame as usual。So。We want to push。一皮。

Move into B P S P。As we usually do。Then we want to take the argument。

 which I'm gonna place on the stack。So， let's say we put it inside of。Our S I。

And this is going to be B P。Usually in a 32 B environment， it's EBP plus8 to get to the first。

A parametermeter。And if we run 64 bit。We have。呃R。B。Plus。16 to get to the first。

But when we run 16 bit like we do now， it's going to be the regular B P。And just plus。4。

That's the first。Argument。So we put that inside of S I。And then we're gonna have a loop。

There will load。Load 1 by。So what this does is it takes the current position of S I。

 which in this case points to our string。And it loads。This but into the。The A L register。

And it increases。This by one。So now inside of A L， we have the byte。

So one check if this is an null terminator。So。We， what we could do is we compare it to。

So we compare by AI to 0。But this is not the most optimal way。Or the most optimized way。And。

When we want to compare something to Siro， it's actually better to just do an orar operation。On AI。

 with itself。If this returns0。We know that。 It is0。So in that case， we can jump to some end。

Otherwise， we want to print this to the screen。So we need to use and by a bio interrupt for that。



![](img/9764a1b27c27c31115c7b182ba11ec48_154.png)

So， let's search for。

![](img/9764a1b27c27c31115c7b182ba11ec48_156.png)

Bs in。108。

![](img/9764a1b27c27c31115c7b182ba11ec48_158.png)

And I like this Stanla page。 and'm gonna link to this in the description。

 I'm also going to link to this page aboutstruct。And this page about the memory locations inside of the。

LED script file。And of course， this always that wki where we have the rest of the information。

Alright， so what we are interested in is。嗯嗯。I think it's this one， right。Write character at Kran。

Cursor position。Let me just double check。Text oh no， I think it's this one。 Actually。

 red text in teletype mode。 Teletype mode basically means right to the console。

One character at a time。So A H should be 0， E。 A L should have the ASI character and that we have already。

Put there right。Page number， we can have0 and if foreground。



![](img/9764a1b27c27c31115c7b182ba11ec48_160.png)

We don't need to care too much about。So。We can just。Initialize our。Let's see。😔。

Let's initialize our B， X to。0， so let's do an X or。It makes it zero and we can do the same with AX。

 actually。Then we load that by。Maybe呢。😔，B， X， we can0 like this。 but A X， I wanna。



![](img/9764a1b27c27c31115c7b182ba11ec48_162.png)

可。This stuff here。 So this should be the higher by。



![](img/9764a1b27c27c31115c7b182ba11ec48_164.png)

So。It should be 0， E， And then we can have 0，0 here。 And when we load， it will replace those。0 here。

So， at this point。

![](img/9764a1b27c27c31115c7b182ba11ec48_166.png)

We have all these different things。Correctly。

![](img/9764a1b27c27c31115c7b182ba11ec48_168.png)

So now we just need to do the interrupt。So would you end0 x 10。And then we jump up to the Lou。

Print in the next character。And when we encounter a0te。We jump to this end label。At which。

 at which point。We can just。嗯。Moving to S， P，B P。We pop back the B， P。We can also take care of the。

This。Yeah。This argument here or this parameter。It's a good way to。Yeah。Do this。So we。

Minus the SP with 4。So we're no， I'm not with42。 Their addresses are2。but in 16 bit mode。

And so then we have removed this argument from the stack。And then， we can return。So。

 something like this。And before we even。Call any of these functions。

We should initialize a few things。Let's。Move into A X。The value of C， S。

Which is the segment register for code。So we take whatever is inside of that and we copy that into a few registers。

So we cop it into SS。Copy it into。D yes。And we copy it into。Let's see， C， S， S， S，D， S， and E， S。

Let's also initial a stack。So I wna have the stack at the beginning of the code here。

So let's say we have a label on top， which is our stack。We can move into A X。That stack position。

And then we can decrement it by2。Yeah， I mean。Mine is it by two。Just in case， so we will have a room。

And then we move into S P， the A X。 So then we have initialized stack。Alright。

 let's also say that we have some label which we can try test this print function on。So。

 let's say we have a string。Hello。World。😔，And we need to have a new line like this。And， let's end。

Can we do this， I du't。Think so， actually。But we cant say0 x a。And 0 X D。

 which is the Windows style new line， which the bio uses。And then we add it by a zerobyte。

And how do we use this thing。Well。We move into some register， our stream。We push that。St。

We call our print function。And after that， let's jump to some halt label where we have an endless loo。

So。😔，This is our fault。We wna co use the halt instruction。 And if。Some interrupt or something。Yeah。

Messes with that。Can have a。Llue Pi， as well。Which has a no up。 And then， then it jumps to the Lou。

Something like this。And by the way， we don't want any interruptive mess when we do this stuff。So。

 let's clear the draft。And then。Restore the interrupt。



![](img/9764a1b27c27c31115c7b182ba11ec48_170.png)

Okay， I think thiss gonna work。Comma Koon， a decorator， blah， blah， blah， blah， Leman。



![](img/9764a1b27c27c31115c7b182ba11ec48_172.png)

Okay。Let's do this， instead。

![](img/9764a1b27c27c31115c7b182ba11ec48_174.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_175.png)

23。This should be A L。

![](img/9764a1b27c27c31115c7b182ba11ec48_177.png)

Okay。Let's do an Ab dump。So， here's。Our code。And how do we test this。Well。

 when this bootloader is finished， I'm going to create a proper Linux server and install this boot loader onto it。

 But during development。We need to make it a little bit simpler。So let's use the Q M mu。QMU。

And I'm gonna use the。I guess system， I 3，86。And let's do like this because I wanna find there is some no graphic。

Yeah， no graphic。

![](img/9764a1b27c27c31115c7b182ba11ec48_179.png)

Let's go to our make file。And create another phony thing， which will be the。Run directive。

R requires Bo M。To run around Q Mu。With in no graphics mode。

Which means that it will in output all the。嗯， stuff。To the council instead， which is very。Lifted。

Now we're going create a primary hardest drive based out of our U dot in。Maybe we can even do。This。

And then we need to specify the size of the memory。 I think it' dash dash S。



![](img/9764a1b27c27c31115c7b182ba11ec48_181.png)

No。😔，No。See。Memria。嗯嗯嗯。Size of guest memory。Here， configure guest Ramm。That是M。



![](img/9764a1b27c27c31115c7b182ba11ec48_183.png)

So this， I believe， should work。 Let's try it out。 And if you don't have Q M installed installed。

 you can do。

![](img/9764a1b27c27c31115c7b182ba11ec48_185.png)

。And。You need to。Install the package。 Q system。呃。Or other QU system， X 86。Then， you to get。

All necessary things， I think。Alright， and then we can just do make run。



![](img/9764a1b27c27c31115c7b182ba11ec48_187.png)

And maybe we can spell it better， no。

![](img/9764a1b27c27c31115c7b182ba11ec48_189.png)

Crrect。😔，对。Noographic， singularis。Hello， Er。Works perfectly。Alright， so now we need to exit this。

Virtilizer。So what we do is control A。X。So， you do control a。You release。And you press x。

That's how you exit。Com you。

![](img/9764a1b27c27c31115c7b182ba11ec48_191.png)

All right， So we have gotten a bit on our way。Now we have everything set up in the project。

And we can start coding the actual boot loader。Where the first step is the relocation where we want to copy ourselves to different memory location and restart everything。

And this will do。

![](img/9764a1b27c27c31115c7b182ba11ec48_193.png)

Just after this。Soup， guys， welcome back。So before the break， we were able to print a message。



![](img/9764a1b27c27c31115c7b182ba11ec48_195.png)

To the screen。And the next step is to take care of the relocation。So。

We need to copy the entire boot sector into another memial location。We need to launch。Our code。

 once again， from that location。And then we need to take care of the booting from the。Partition。

So let's begin by creating some messages so we know a little bit。About what's going on。So， let's say。

Let's create the message you won。And this is going to be。Relocating。Yeah。

And let's create a second message。So we know when the relocation has happened。Yeah。Let's do。

And these are just temporary messages during development。 so we know if the things work or not。

So relocation， successful， something like this。AndLet's add the new lines。And the character。

Line feed。And null terminator。So something like this。嗯。Right， so first of all。

 we need to have a way of knowing if we have。If we are running the code the first time or the second time。

 because we will only relocate our own code。The first time。And the easiest way。

I think is to use the DL register。Because the bios will put0 X A D inside of the DL if we are booting from the primary hardest drive。

And it will post， I think，0 or one or something。 if we are booting from a discat drive。

 which we most definitely won't。So we will only support building from the primary hardest drive。

We will support different partitions， but only one physical drive。

So when we launch our code the first time， DL is going to be 0 x80。

So we can basically check for that and then change it to something else like 90。

And then execute our record the second time。That's the general idea， anyway。So。Let's do something。

Like。Instead of this code that we have over here。Let's print。No， wait a second。Well。

 we can print the re relocating stuff。 But first， we need to check。The value of the DL。Yeah。So。

 let's call。Let's create a subrouting， called Re。L。开ation。And。We will compare。

The D L register to 0 x 80。And if it's equal to that， we won jump to。Relocation。诶。Otherwise。

We will do the other stuff。But for now。Let's just。Jump to hold。Otherwise。嗯嗯嗯。嗯。Let's see。 No。

 not to hold。Let's say we jump to successful or something。蛇。😔，Our successful。Sub routineoutine。Will。

We will want to move into A X' second message。We wna push it， and we wna call print。

And then we can jump to halt。And。Otherwise， we will do the actual realloc。

 starting by printing the message。That we are relocated， relocating。And how are we going to do this？

Well， we could do a loop which basically just starts at the beginning here and manually copies each byte up to 512 bytes。

But。😔，There is a better way。We can use a special instruction， which is called rep。move S B。

What this does is， is it takes the。Me address inside of the S I register。And this is the source。

 So it uses this as a source for the copy operation， and it uses DI as a destination。And inside of C。

 X， we put the number of bytes。 We want to copy。 And then we just。

Do this instruction without any arguments。So let's move into DI。Yeah。So。Well let's start with S I。

 So the destination should be 7，8，0，0， as I mentioned before。

And let's do the destination field at 7 C，0，0。 So that is。え。Let's see。 No， the other way around。

So we want to copy it from 7 c0，0。 That's where this code is located。And we want to copy 2， the 7，8。

0，0。And then we do a rep， move S B。And when we have done the copy operation。

 we will just jump into that code。 But before we do that， we need to。And move into our D L。

Some other value， like0 x90。 So we won't just repeat this over and over。

And then we can do a long jump。And we do that by specifying。And。Two parts of the address。This。And。

This。Yeah。This is the right thing。So this basically means that we will do a jump to。0。As the。我。

The segment， basically。And if we have a zero segment， we will jump to this address。

 which is what we want to do。嗯啊。And let's。And if this would fail somehow without crashing， we could。

And this by jumping to hold。So if this works。First， we're gonna to say the relocating。

Then we were going to copy everything to our new location。

Then we're going to re launch this whole program with the only difference being where we store it in memory and the value of the DL register。

嗯。And then we're going to print the relocation successful the second time around。Right。

 that's see idea Anyway。 Let's see if this compiles。



![](img/9764a1b27c27c31115c7b182ba11ec48_197.png)

We got a warning，72。

![](img/9764a1b27c27c31115c7b182ba11ec48_199.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_200.png)

Yeah， that's right。 This should be a colon on after。Alright， let's see if we have a。Boot dot in。Yes。

 we do， and it's 512。Let's run it， and see what happens。Relocation。And then。Nothing。嗯哼哼。

That's a little bit disappointing。

![](img/9764a1b27c27c31115c7b182ba11ec48_202.png)

Right， so let's see here。This prints a first message， which means that this was equal to 0 x80。

And maybe。If we execute the hold。Directly after the the print。It might actually hold before。

It's able to print。So let's do the the loop here， the endless loop， but let's not do the halt。



![](img/9764a1b27c27c31115c7b182ba11ec48_204.png)

And let's see if this makes a difference。嗯。

![](img/9764a1b27c27c31115c7b182ba11ec48_206.png)

嗯哼哼。W a second。 I set the S I and the D I Bar never set the C X。We also need to set CX。

And this should be 512。 So I think that's0 x200。

![](img/9764a1b27c27c31115c7b182ba11ec48_208.png)

I'm correct。 Let's see。That's the deck and。0。200， yes， that's512。 Allright。

 let's see if it works this time around。

![](img/9764a1b27c27c31115c7b182ba11ec48_210.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_211.png)

Hm。It's weird that it's only printing， too。

![](img/9764a1b27c27c31115c7b182ba11ec48_213.png)

Of the dos。Because I have three here。In the first message。嗯。Destination 7，8，0，0。



![](img/9764a1b27c27c31115c7b182ba11ec48_215.png)

![](img/9764a1b27c27c31115c7b182ba11ec48_216.png)

Mmhmm。Let's double check the syntax for rep Mo B。Let's search for。Re。Stars， Felix。



![](img/9764a1b27c27c31115c7b182ba11ec48_218.png)

Then we come to this Felix coier page， which is。Often， the best one。Right so。This one。No。😔，你说。😔。

So we move C X bytes。From S I to DI。

![](img/9764a1b27c27c31115c7b182ba11ec48_220.png)

And we move。😔，512。系。Wait a second。No， I see。嗯。Right。If we。



![](img/9764a1b27c27c31115c7b182ba11ec48_222.png)

Do an o dumpump。Of the boot dot in。 And we grab for。7 C。Oh。So， look at this。This is when we call the。

The string， the print function。So we specify the address hard coded a 7 C each time。

And we can't do that because we are at 7，8，0，0， right？



![](img/9764a1b27c27c31115c7b182ba11ec48_224.png)

So we need to be a little bit more clever。We need to have some kind of offset。So， let's say。

We have a。Word。Which is 0 by default。So when we grab the address inside of the print。Mhm。

So let's see we put it inside of S。😔，So what we want to do is we w to。Take that address。

 minus the offset。Which is0 by default， which means the address will start with 7 C。

So let's start there。嗯。Let's。Let's see here。Let's move into。Bx。Offes。But。嗯。

If we use the offset address， it will still。Be the same problem。嗯。h。little bit。re。😔，Well。

 we don't have to do an offset。We can。Use the。D L here， as well。So， let's do something like this。嗯嗯。

Let's compare。嗯。D L 2，0， x 80。And if it。Not得 girl。If it is equal， let's jump to。No。Of set。

Let's just do no。Of。Let's make the local label。So let's say we have it here。 No of。系啊。

And then we're not gonna do much else。But if we。Are in the second iteration。Then we want a deck。

 Then we want a。Sub。The S。By0 x。400。I think this should be enough。



![](img/9764a1b27c27c31115c7b182ba11ec48_226.png)

Let's try it out。Ca， this time we got。3 dots。

![](img/9764a1b27c27c31115c7b182ba11ec48_228.png)

But I noticed we， we have only how many calls do we have to the print。嗯。Or actually。

That doesn't really matter。But。

![](img/9764a1b27c27c31115c7b182ba11ec48_230.png)

I saw a lot of different seven Cs here。57，67。Let's do something like this。Move ax。Okay。

 so that's the step。It doesn't hurt that the stack is 7 C。Actually。What about this。

 this is probably one of the prints。

![](img/9764a1b27c27c31115c7b182ba11ec48_232.png)

7， co2。

![](img/9764a1b27c27c31115c7b182ba11ec48_234.png)

Ye。😔，What's this。Move S I。7 C。0al，0。That's the actual relocation code。

 So that will not run the second time。 So that shouldn't be a problem。What about this。7 C，12。

That's the second message， I guess。Think this should work。 Let's see if we have this address。

And we minus 0 x 400。Then we get the decimal value of this， and the hex value of that is 7，8，12。

So that should be the right， the right thing。

![](img/9764a1b27c27c31115c7b182ba11ec48_236.png)

嗯嗯嗯。Maybe it's the actual print that fails this。嗯。This thing should probably be after the call to print。

Because otherwise， the return address will fail。That's probably it。So let's see here。

 where do we print stuff。 Here is a called print。 So afterwards， we w to minus the stack pointer。😔。

And same here。

![](img/9764a1b27c27c31115c7b182ba11ec48_238.png)

Could it be so easy。There we go。 Relocation， successful ladies and gentlemen。

 We have successfully relocated。😊。

![](img/9764a1b27c27c31115c7b182ba11ec48_240.png)

Nice， so now the only thing left is to run the code for the second iteration。

Which goes through the partition table。And。Finds。The first partition， which is beautiful。

Reads from desk。And。Boot from that。So。So we'll be right back after this。All right， you guys。

 Welcome back。So before the break， we finally managed to get this relocation working。

So now the next step is to。Pase the partition table。But first。

 we need to have a professional table because this is just placeholders。So。I'm thinking。

I'm going code a bash script， which is in charge of that。So let's say we have a P table dot S H。

So the the use of this script is to。Take the partition table from the main hardest drive。

And put it into our。Put it somewhere。So let's say we have the first sector。

 the first 512 bys of the primary hard disk we have in a file called disk。

So we wanna check if that file exists。嗯。And， if not。Then we want。Let's see here。

Then we want to print an error message。So， something like。Disk， not phone。

And then it tells to run the following command。 So pseudo D D。

And the input file is the primary hard disk drive。Output file is our disk file。We want to have a。

Sector size of 512 bytes。 And we want to copy one sector。

 So this is what needs to be run before we execute this script。And if not。

 we get this error and we quit。Otherwise， we can。Start paring this day。

So I'm going to use two temporary files， TMP1 and TMP2。

So let's start by removing those if they already exist。And let's。Suppress any error messages。And。So。

 let's see。

![](img/9764a1b27c27c31115c7b182ba11ec48_242.png)

So the disk file contains all of this。But we want to replace the code part with our own。

In these parts， we don't care about。So， we can actually。Well， it doesn't matter。However。

 this we want to keep。And we can take this as well because it makes things a little bit easier to take from here and until the end of5。

So this we want to keep in one file， this， we want to keep in one file。

 and then we can assemble these into。

![](img/9764a1b27c27c31115c7b182ba11ec48_244.png)

Our binary。However， booth do the image。So let's see how we do this。 We want to take the input file。

Of our。嗯。Bot M。I we'm going to create one of the temporary files。Maybe I should be。Proper。嗯。And。

 let's set。Size invite。To one。And then， we want to take。We we can't specify hex values here。

 So we need to do it like this。

![](img/9764a1b27c27c31115c7b182ba11ec48_246.png)

系啊。So we one呢。Take。Let's see here。We want to take B， E number。



![](img/9764a1b27c27c31115c7b182ba11ec48_248.png)

Of bites。Let's put it inside of here。So this will copy the first thing。Secondly， we want to take the。

The disk file， as inputs。An output is going to be our second temporary file。

We still want the by size of one。

![](img/9764a1b27c27c31115c7b182ba11ec48_250.png)

And。And now， we want to ski。B。But。

![](img/9764a1b27c27c31115c7b182ba11ec48_252.png)

So。We'll say skip， and we'll do the same trick。Paste it inside of here。嗯呢。Do small letters。

Not that it matters。So at this point， we have the entire new image in two files。

 so we just need to combine them。So we can simply do cat。TM P 1， T MP 2。

And we can concatenate it into。Well， a new boot of ink。This should work， I think。So。



![](img/9764a1b27c27c31115c7b182ba11ec48_254.png)

Let's try running it。Ws。So what do we call it P table with S H。

 So now it should fail because we have not generated that disk。But then we can just copy this。

The whole thing。

![](img/9764a1b27c27c31115c7b182ba11ec48_256.png)

哦。Should be D space。And I F equals this。

![](img/9764a1b27c27c31115c7b182ba11ec48_258.png)

So let's try this again。Okay。So now we have this disk file。😔，So this is the current maskingbo record。

 and we want to replace it with our code， but we want to keep the partition table。

So now we can run our script。Okay。And we can check our boat dot M。😔，It's still 512。

That's a good sign。呃。And lit。Do an option。Jump to 50。And down。There。This looks like our code， right。

And if we go down to the partition table。Dont be。So here， starting with8。

We have the first partition table entry。The1，2，3。4，5。6，7。8 but。Looks right。

So the interesting thing for us is this first field。Which contains the beautifulable flag。



![](img/9764a1b27c27c31115c7b182ba11ec48_260.png)

This right here， bit number 7 inside of this bite is the beautifulable flag。

And then the next three bytes is the CHS address， which tells us where on the。



![](img/9764a1b27c27c31115c7b182ba11ec48_262.png)

Hardest tribe， physically， where the。Well， where the first partition's data is。Or。All right。

Looks right。

![](img/9764a1b27c27c31115c7b182ba11ec48_264.png)

So let's integrate this into our build system。So when we create the boot of ing。At the end here。

 we wan to set P table do S H executable。Because when we update that file using the method I'm using。

 we lose that flag， so let's put it in here。And。And then， we just run this thing。And then。

 we will have。The new file。With the correct partition table and our coat。比色皮如子。Maybe at the end。

 by the way。We can remove those temporary files。Like so。Alright。So， next step。

Is going through the partition table。Because even though we put our。Bgu stuff here。

Our end file with will contain the right partition table so we can write our code as if these values were the correct ones。

So， the first thing is。Iterating through these four partitions。Looking for the bootable flag。

And the first partition we find with the beautiful flag set。That is the one we want to build from。So。

This code right here where we currently have this relocation successful。Instead。

 we want to print something like。Looks。Loader。And instead of jumping to halt at this point。

We want to call some function for。Finding the right。thhing。I guess we could。

Write a function called get A H S， which。Looks for the boable flag。 And if you find it， we read in。

The CHs。Vals。The cylinder head。Sector from the hardest drive。And we can。

Say that we have an error if the carry flag is set。So afterwards， we can have。Jump， carry to error。

And if， so this is basically if we don't find any partition。And we can move into A X message 3。

 let's say。偶。Arror message 1。Push A X， called print。And decrease。This。And then we can jump to halt。

Let's create this error 1。Maybe we need to clean up a little bit。With those。

If we don't have enough room later on。 But let's cross that bridge when we get there。Yeah。No。O。

Pticitions。Something like this。However， if we don't get this carry flag。We want to do something else。

But let's create this get CHS function first。So。Let's put it up here。So get C H S。We want to。気ちい？😔。

Wanna push BP P。And move into BPSP。As usual， and we don't take any。

Arguments or parameters to this function。Let's see here。So we want to start at the first partition。

 which is called first。

![](img/9764a1b27c27c31115c7b182ba11ec48_266.png)

And if we look at this。Format here， we see that the first。The thing is。Did drive attributebutes。



![](img/9764a1b27c27c31115c7b182ba11ec48_268.png)

Which means this is the the we want to look at。Let's。Start by moving into。Let's move into B， X。嗯。

The address of。Pition。We clear out。AX。And then， we move into a。L。The address inside of Bx。So now。

 A L will contain our。对的。M B，X will contain。Where the address of that data。Alright。

 so how do we get the seventhth。Bit out of this。The easiest way is to do an end operation。So。

 we and A L。喂。Something which looks。Like this。So， this is bit 7。And this is0 x80。

 which we have seen before。So if we end it with0 x a。We can just。compareare it。To 0 x a afterwards。

And if it is， then we know that this is。And we should probably do this inside of a loop， though。Yeah。

Let's say this is a loop。Lguang。So， if it's equal to。A恋。Then we can move to the next step。

 Let's call it。嗯。Well， that's actual。C， H S part。 So let's call it that。So here somewhere。

 gonna have that stuff。However， if we。If this partition is not boable。

 then we want to go to the next one。So we want to add on2 B X。

We also need to keep track of how many we have gone through。So， let's。Move into Cx。Number 4， I guess。

So。It starts with 4。 Then it become 3，2，1。0。Okay， so we need to check it by the end。We decrement C X。

And if it goes to 0。InThat case， we want to jump to the error condition because then we have gone through all the different ones without finding what we're looking for。

So， the error condition。It's just that we。Would set the carry flag。And and then we。And move into S。

B P， we pop。诶。BP back into place， and we return。However， if we。Are not， by the end。That in that case。

 we want to add into B X。

![](img/9764a1b27c27c31115c7b182ba11ec48_270.png)

16。Because it's 16 by to the next one。

![](img/9764a1b27c27c31115c7b182ba11ec48_272.png)

And then we want to continue looping。 so we'll jump back up to the loop。So， this is the code for。

Finding the first partition with the bootha blue flag。And what do we do when we find that one？

Then we can copy into A X， the value of B， X， which currently points。



![](img/9764a1b27c27c31115c7b182ba11ec48_274.png)

Toward。The first thing in that partition。And then we want to go to the CHS。



![](img/9764a1b27c27c31115c7b182ba11ec48_276.png)

And maybe we don't need to do it this way。Let's just add on B X。The partition。



![](img/9764a1b27c27c31115c7b182ba11ec48_278.png)

Let's see how we do this。Pition of。

![](img/9764a1b27c27c31115c7b182ba11ec48_280.png)

Start。I think we called it。

![](img/9764a1b27c27c31115c7b182ba11ec48_282.png)

So now be exposed points to that。😔，And we want to read in one bitete at a time。



![](img/9764a1b27c27c31115c7b182ba11ec48_284.png)

And put it in the right place。

![](img/9764a1b27c27c31115c7b182ba11ec48_286.png)

And where is that？

![](img/9764a1b27c27c31115c7b182ba11ec48_288.png)

We wantna。Execute an in 13 age。

![](img/9764a1b27c27c31115c7b182ba11ec48_290.png)

So read disk sectors。 This is the function in the bios we want to use to read in from the disk。

So we want to put， as we can see， here we。putut in the drive number。Yeah。And the。Cylinder。The head。

And the sector。

![](img/9764a1b27c27c31115c7b182ba11ec48_292.png)

So， let's put it in。In those places。So first， we start with the。是。Let's see。 cylinder。So。



![](img/9764a1b27c27c31115c7b182ba11ec48_294.png)

We move into。Let's see where we're gonna put that。So， some stuff。We said into A X， some in C， X。And。

Some in the D。Register。So we need to clear out。

![](img/9764a1b27c27c31115c7b182ba11ec48_296.png)

C X， at least。

![](img/9764a1b27c27c31115c7b182ba11ec48_298.png)

So let's start with the cylinder， which we're gonna put inside of C， H。



![](img/9764a1b27c27c31115c7b182ba11ec48_300.png)

So we move by。Into the H。Thats position B X。

![](img/9764a1b27c27c31115c7b182ba11ec48_302.png)

Then we can increase the X。 So we go to the next bite。So that's the head number。

 which we're going to put inside of DH。😔。

![](img/9764a1b27c27c31115c7b182ba11ec48_304.png)

So we moved by DH。B x。And then we increase it again。And this time， we want the sector number。

 which is inside of A L and no number of sectors。 We want the。



![](img/9764a1b27c27c31115c7b182ba11ec48_306.png)

This one， sector number， C， L。

![](img/9764a1b27c27c31115c7b182ba11ec48_308.png)

And now we have everything that we need from here。So， we can just。Yeah。Moving to S P。b p。

We pop off B P， and we return。And before we return， by the way。We can。Also clear the carry。

Since we use it to。Signal and error。All right。So， something like this。When we have gotten the CHS。

We want to read in。And。The first 512 bys。From that location。So。Let's call something like this， read。

嗯。By the way。We need to do the arrow check first。 Then we can call this grid。

Then we can check the error again。😔，And how will this discrete work， Well。

 we already have most of its parameters already set up。So well just create a function， like。

B done before。We push the BP P。 We move B into S。

![](img/9764a1b27c27c31115c7b182ba11ec48_310.png)

So， we have the。Tue。😔，诶。The cylinder number， we have the sector number。 We have the head number。

 The drive number is already in side of DL。 you remember，0 x80。So the only thing we need to set。

Is the A X but。And we need set B， X to where we want to store this thing。



![](img/9764a1b27c27c31115c7b182ba11ec48_312.png)

So。Let's move into A X。

![](img/9764a1b27c27c31115c7b182ba11ec48_314.png)

Number of sectors is a low。

![](img/9764a1b27c27c31115c7b182ba11ec48_316.png)

But， so this is going to be 0 x 0，2。And then。1 sector。And B， X， well， where do we wna put this stuff。

Inside of F C 0，0。 So that's the whole point why we messed with a relocation。 So we can move， I mean。

7 c，0，0。So we can put it right here。And now we just do in00 x 13。



![](img/9764a1b27c27c31115c7b182ba11ec48_318.png)

And the carry flag is。

![](img/9764a1b27c27c31115c7b182ba11ec48_320.png)

We。If an error。 So that suits us perfectly。So let's clear the carry before we do this。

And then we can simply return from the function。 so move S PBP。扑 b屁。Return。Okay。

And when we have done all of this， the only thing left is to execute that code。

So inside of the main function。The only is thing left。Is to。Let's see。Is to jump。To the address of0。

Sment is 0， and the address is 70。0，0。And then if we fail， we can jump to halt。And that's it。

After the break， we're gonna check if this code works。 See in a bit。 Sub guyss， welcome back。

So before the break， we basically finished the whole thing。嗯。I'm just gonna take。

A moment to fix some error that。嗯。Not list。So， let's see our function for。G， C H， S。

I call this loop 1。And I jumped to loop here， so let's change this to loop。And。

One other thing I want to add， so。When weoo。I want the user to press enter。

So we can see a little bit more what's going on。 Otherwise， it could only。happened instantly。And。So。

Let's。Change this， too。No。Sthloader。And。Press。Eder。To boost。Lin。Maybe I should have prompt like this。

And how do we read from the keyboard。

![](img/9764a1b27c27c31115c7b182ba11ec48_322.png)

There should be some bios。Interrupt for that。

![](img/9764a1b27c27c31115c7b182ba11ec48_324.png)

嗯。

![](img/9764a1b27c27c31115c7b182ba11ec48_326.png)

嗯。Let's see。How we gets back to the main page。So， bioos keyboard services。This one is good。

 Wait for key press， and read character。So the only thing we need to do is set age to0 and call interrupt 16。

 then it's going to wait for a key press。Yeah。And I guess， any key press， so。



![](img/9764a1b27c27c31115c7b182ba11ec48_328.png)

Let's change enter to press any key。Let's see。Where do we print message to。

I guess it's inside of Maine， somewhere。Here。😔，So， get C， H S。So， at this point。

We have done the relocation。But， we haven't。We haven't。

Actually found any partition with a beautiful flag。So I think it's a better way to put it。Here。

 actually。Yeah。So， let's just add。Let's clear out A X。And call in 16。 And no， not 16。



![](img/9764a1b27c27c31115c7b182ba11ec48_330.png)

He，6。

![](img/9764a1b27c27c31115c7b182ba11ec48_332.png)

But maybe not， because this gets the HS function。It prints。This error。If it fails， so in that case。

 this error will be。Friend tell then waiting for a keystroke。 And that's not what we want。So。

 I guess。We can move this。Here。😔，Yeah， that's gonna be good enough。All right， something like this。

 Let's see if it compiles。 and let's see if it fits。



![](img/9764a1b27c27c31115c7b182ba11ec48_334.png)

We only have 440 bytes。For the code。

![](img/9764a1b27c27c31115c7b182ba11ec48_336.png)

Disgrareade， not defined。 Oh in never death discre way。Or maybe。Disreet， I think we it is， right。

Disute what I call it dis cute。Disreet， of course。

![](img/9764a1b27c27c31115c7b182ba11ec48_338.png)

Of cause。H。It compiled without any error。嗯，And it fit。That's pretty remarkable， now。

Let's see I be done。And see how much code there is。So we go all the way， all the way to 12 D。

And if we take the decimal of 12 D。301， we could actually add。At least another hundred0 bys。



![](img/9764a1b27c27c31115c7b182ba11ec48_340.png)

But okay， that's pretty nice。嗯。How do we test this thing， Maybe we can test this。



![](img/9764a1b27c27c31115c7b182ba11ec48_342.png)

At least the part of it by running may run。Press any key to build Linux。Ofbo partitions。Well。

 that makes sense because。We are running it in a virtual machine， right。

 And that virtual machine does only have this boot sector。

 It only has 512 B on the actual hardest drive。So in order to test this properly。

 we need to install a real Linux server， at least。Fuul。Fully equipped and installed virtual machine。

And then we can run this thing。诶啊。On that virtual machines。But I think this is。Good enough for today。

I really hope you like this episode。 It is one of the most advanced and low level episodes I've done。

 And if you want more like this， make sure to lie， can subscribe and maybe even hype。 Who knows。

And we will finish this bootloader。In the next episode。So thank you for watching， thanks for today。



![](img/9764a1b27c27c31115c7b182ba11ec48_344.png)