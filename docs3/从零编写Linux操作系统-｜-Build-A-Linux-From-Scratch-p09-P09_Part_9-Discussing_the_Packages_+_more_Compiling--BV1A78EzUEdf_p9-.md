# 从零编写Linux操作系统-｜-Build-A-Linux-From-Scratch-p09-P09_Part_9-Discussing_the_Packages_+_more_Compiling--BV1A78EzUEdf_p9-

Hello， world。 welcome back to this tutorial on  building a Linux from scratch system。Now。

 in the last video， we've。Started。Really building the final system。And。Yeah。

 it took quite a while and we didn't get very far yet， but that was mainly because， well。

 the Glippsy library is so big。嗯。So， yeah， I really want to。系啊。

To install a bit more than six packages this。Time。So。Yeah， that's just。Jump right back in。嗯。Yeah。

 I want to pick up a bit steam， so。One thing that I will。Do now which I did in earlier videos also。

Is I just want to create all these files in batch。This is。These Sha script files。So we have already。

Hat。The package dress。Men pages。T CL。Expect。Deja Nu。Yeahや呢。Etsy。And Glip C。

And I've also already created the file for。Z lip。嗯。And now I will just create empty files。For。

These are the tool。X， Z。The STD。File。Readed line。And4。BC。Fleex， spin u tilts。GMP。MPFR。MPC。After。A N。

Lip cap。Sdle GC C。P， K， G contract。And cursesos。Seid P S Smith。Get text。Bison grip。该是。猪。GDBM。Sper。か。

Inet you。P。Xm。Pel。Inter tool。また感じ。How to make。K much。Oh。ルップ？I。SS L， python。Nja。你son。あユ tell。

Diff fu tilts。Ork。Find you tills。Grauff。Yes。T zip。IP root。KPD。For keyboard。Dip。Pipeline。Make pitch。

MDb。Tt info。And then。Now， there are more packages in here， but。Yeah。The remaining packages。

Specifically for system V in it， and。After we've done these packages here。

 I want to split this video series in two directions。 One where we use a。System V in it。

 and one where we use system D。 So that's why。嗯。I will only go this far for now。



![](img/7620c7e229704c2a7caa021fe15f39fe_1.png)

Okay。So now I have created all these files。The code for Zlip is already there。So。

I'll just do some of them。We had these problems with M4。And just to avoid that。

I'll just take the work around that I had before。Okay。



![](img/7620c7e229704c2a7caa021fe15f39fe_3.png)

And this is a useful list。 So I'm gonna。

![](img/7620c7e229704c2a7caa021fe15f39fe_5.png)

Copy that。Here。

![](img/7620c7e229704c2a7caa021fe15f39fe_7.png)

Okay。Okay， all of these things are installed already， so。I will just go into the train route again。

And。Try installing these seven packages。

![](img/7620c7e229704c2a7caa021fe15f39fe_9.png)

![](img/7620c7e229704c2a7caa021fe15f39fe_10.png)

![](img/7620c7e229704c2a7caa021fe15f39fe_11.png)

![](img/7620c7e229704c2a7caa021fe15f39fe_12.png)

Okay。So well this is still still running。Let's talk about the packages that we are installing。嗯。

Men Pageriots， well let's。Contains the main pages。 very surprisingly， what are main pages。

 They are like documentation or。Help files for。Over 2200。Things。I think including source codes。

Some heada files， and so。TclL， the tool command language that the script interpreter。嗯。

It's a relatively high level one， as far as I know， and。I'm not sure why we even have。

Such a high level thing in a low level system like。Linux from scratch。 but okay， they。A doing it。

 I think in the future， I might。Change my script and just throw a few of these things out that I don't think are really necessary。

And maybe I can get。The system even smaller like that， but。We will see。

 So TclL is definitely something that I think I might。Want to remove。

We need T C L for Exp the next package。Now呃。Expect is。嗯。Yeah， program。

That is used in some auto tests。嗯。So you run something and you tell it to expect this or that output。

嗯。I think if we throw out， expect， well， we won't be able to do us several auto tests， but。

Maybe we can live without that。 and then we might be able to throw out T CL and expect。哦。Yeah。

 derau is。诶。Framework for running auto tests。嗯。哎呀呢。Edsy is， yeah， two files。

 services and protocols that are stored in Etsy。These are just lists of。Of TCP portds and protocols。

 so。For example if。I think in the UFW firewall。You can tell the firewall， hey。

 open the H TTP port and then。That firewall would look into one of these files and see， okay。

 T the H T TP port is 80， so I need to open port 80 now。Dip C is a very central。

Library what's used in many， many programs。嗯。For example， it handle the lowales。You know。

 stuff like which。Character is used for decimal separation。Or how to format。Daate and time strings。

It's a very， very important。Libraary。I think without a ju seat， basically nothing would work。

So that's something that I'm not throwing out in the future。Zlip is a library for compression。嗯。

Sip compression。Then B zip is a compression tool。 Xy is another compression tool。

Z STD is another compression。Library， I think。

![](img/7620c7e229704c2a7caa021fe15f39fe_14.png)

Okay， it also installs a few programs。File is an interesting program。



![](img/7620c7e229704c2a7caa021fe15f39fe_16.png)

嗯。You know， in Windows， when you open a file like a JPEC file。

 then Windows will just look at the file extension dot JPG and。Will then look up。 Okay。

 JPG files are opened with some image editor or image viewer。嗯。On Linux， I mean。

The systems tend to do that also in Linux systems these days， but。The file program。Allows you to。

Go a bit deeper because the file tool also looks at the metric numbers at the head at the head of files and。

So， even if you're。Even if your file extension is wrong， then the file utility may might be able to。

To fix that， so。A Linux system might say， O， this file is named whatever something dot MP3， but。

According to the header of the file， this is a JPg file。 so I'm opening it in a。And an image viewer。

Maybe。Soの。Let's see you Sir。For example。File。G C S H would tell me it's a sea sauce coat。 Well， Ka。

Casehor is wrong。嗯。But S key text， that's correct。Sometimes it's it just guesses something。

But S text， it also can。Determine the encoding of a file pretty well so。

That's also pretty good when you're having any trouble with encodings。Using file。

 you can usually determine。The encoding that's used and then maybe run your program or run your text file through icon to convert the encoding。

Okay， read line。 That's a library。For。Yeah， for interacting with。The shell。 So when you。

 when your programs read a line from user input that might use。嗯。The slip reline。然后。嗯。

It also features the history， which。Allows you to scroll through your history with the up key。



![](img/7620c7e229704c2a7caa021fe15f39fe_18.png)

Okay， M4， that is a macroprocess， so something like the C plus plus or C preproces。

 something that expands macros。

![](img/7620c7e229704c2a7caa021fe15f39fe_20.png)

好。Many projects。Don't write their make files explicitly， they。They write and for scripts。

And run them with， or maybe even create them with auto make and。Auttocon。And。

That then generates your make files。Okay， then B is。ATt based calculator。

So you could say something like one plus one。And it will tell you， too。 I think you can also。

Set variables。Yeah， so。As said Fua totu， and。Then2 plus 3 is 5。



![](img/7620c7e229704c2a7caa021fe15f39fe_22.png)

Okay， that's PC flex。

![](img/7620c7e229704c2a7caa021fe15f39fe_24.png)

Oh， I love flex。You， I write a lot of compilers when you look at my homepage。

 there are so many things that at least pass some stuff。And。Well。

 Fl and bison are basically the most useful tools out there。To help you create puzzles。So。

Fleex takes and。Input stream like a file and turns it into a token stream， an annotated token stream。

And。According to you， to the rules that you write。And then Bien creates a parer。

That uses these tokens。So， instead of。That that would lead too far。

I might actually make a video series about writing a compiler in the future， so if I do that。

Then we will be talking about flex adviseson。Definitely， absolutely， certainly。



![](img/7620c7e229704c2a7caa021fe15f39fe_26.png)

Okay， bend your tails。

![](img/7620c7e229704c2a7caa021fe15f39fe_28.png)

Binuts contains。Well， for our purposes， at least the very important tools。LD， which was a linker。

 an asemler。AS。And some other stuff， like。Like read L or an M， which allow you to look into。

Object files or binary files。

![](img/7620c7e229704c2a7caa021fe15f39fe_30.png)

然后。Okay， GMM is a library for math。

![](img/7620c7e229704c2a7caa021fe15f39fe_32.png)

That's used by GCC。Possibly， also the。Stuff GC generates。MPFR。

 another library for multiple precision math， also used by GCC and the stuff GCC generates。MPC。

 arithmetic of complex numbers， with arbitrary high precision and。Correct rounding of the result。

Another mass library used by GCC and programs pay。Create。嗯。Aature。

Contains utilities to administer the extended attributes on fire system objects。

 So it gives you the utter program that allows you to set。Attributes on files。A C， L， O， Im A C。

 L is for access control lists。嗯。When you run on your machine only， it's。

Probably not something so important if you have just your user and the root user。

But AC Ls can be used to。Set different access rights for different users。Right， so。

 And if you only have one user such as me， usually。Then you don't really care about ACL， but。

In a larger environment。That's very important to be able to give people different levels of access to different files。

Lip cap。Well， the description in the Linux from scratchbook is pretty。Vague。

 it says the lip cap package implements the user space interfaces to the Poss capabilities available in Linux kernel。

 These capabilities are a partitioning of the all powerful route privilege。

Into a set of distinct privileges。嗯。Yeah， I'm not sure what they mean by that and。

The Google search didn't turn up much more， so。It seems to have something to do with access rights。

知道吗？In particular， with allowing normal users to do stuff that would normally only be allowed to。

R user。Shadow， well。Shadow is for the。For logging in， managing users， groups， passwords。I think。

Having lip cap between A， C， L and shadow。I guess that tells us a bit about。L cap。

Shadow and then G C， of course， is the glue compiler collection， the C compiler。

 the C plus plus compiler。That's one of the most central packages in。In the Linux world。And。

How far have we gotten NPC a。Okay。Then let's install these。f。O， shadow seems to have accepted my。

ARoot password。 Okay， I didn't expect that necessarily。Okay。It was pretty quick。Now， it's already。

 We are already at Gcc。

![](img/7620c7e229704c2a7caa021fe15f39fe_34.png)

There were a lot of。Messages when I built Gcc that said， fail this， fail that。I'm not sure。

 it looked like something。Related to auto tests， and maybe these were auto tests that were supposed to fail。

Anyhow， I will just continue for now。Because I just want to get through this chapter， and。Yeah， so。



![](img/7620c7e229704c2a7caa021fe15f39fe_36.png)

Now， I've copied everything。

![](img/7620c7e229704c2a7caa021fe15f39fe_38.png)

Up to， and including。834， which is abash， and I think that's a good point。For little break here。So。



![](img/7620c7e229704c2a7caa021fe15f39fe_40.png)

嗯。Package config。Well the book says。The package conflict package contains a tool for passing the include path and or library paths to build tools during the configure and make phases of package installations。

嗯。Yeah， I don't know。 That sounds a bit。Extensive to me， to have。To have an extra program for that。嗯。

I'd say that's something part of the whole auto auto make。Aal toolss。Ecosystem。Okay， end cursors。

 that's a pretty big library。嗯。It's there to control。Their coloring and positioning of。Offi Ksza in。

In a text window。 So if you remember the old days。The old ball and C plus plus。あ。

You might remember the con I O header file。 and yeah， and curses is。Similar， it does similar things。

嗯。And。You possibly don't remember that old compiler and。I'm getting old。Okay， set SD yeah。

That's a great program。 one of my favorite programs。I will just show you a little bit。

Of what you can do with it。So。You know， Linux streams， I hope。And。Well， with the echo command。

 you can write something to a stream。And then you can pipe that。

 but it doesn't have to come from echo， it can be any stream。And SD is a stream editor。嗯。

Which is probably one of the three programs that I use the most on Linux systems。嗯。And。

SED is used to edit the stream， as the name suggests。 So， for example。

I have the word fu bar here and。S is a replacement command。What do I replace。Let's say，2 o's。

And let's replace it with two A's。Okay， so then you get F R and。嗯。Where's the G here。

Just means if you don't have that G。You will only replace the first occurrence of the thing you're searching for。

 and with the G。You're looking for globally global replacement， so then you replace。All occurrences。

 like here， I am only looking for10。So only the first O is replaced by an A。 And here。

 both are replaced by an A because。I've used the G here。嗯。And SD is extremely useful。

 because you can。Search for anything， any regular expression。

You can have capture groups and reference them in the。Resulting thing。It's really， really useful。

One thing I want to mention， most people use slashes to。

To separate the search term from its replacement。But that's actually not necessary。

 You can use any character you want just the next after the S is what will be used here， so。

I can use columns， for example， and it will also work。

That's something that apparently many people don't know。 but yeah， that's。嗯。And of course， you can。

You can change these things， like。So。That's the stream editor， as I said， extremely useful in script。

PS M。嗯。Well， it's for。Management of processes， you know， P S is。Shows you the。Running processes。

And PS M， some other stuff related to PS like PS3。That shows your processes as a tree。嗯。

Where something is apparent of a note。That process has spawned that other no process。So。

That's in P S Smith， for example， kill all us in there。Which you use to terminate programs。Get text。

 has。To do with internationalization。 So translations of programs。Two different languages。Bson。

 as I've already mentioned， when I talked about flex is。Psar generator。

 So when youre writing a programming language， you， you are definitely using flex and bison。Well。

 not， not definitely， but。They are as a。Pser generators out there。

 Some people actually insist on writing their pars by hand。

Absolutely don't understand these people because bison and Fl are so good at what they are doing。

Yeah。Okay， grip。Well要。I just mentioned GrP already when I talked about set。嗯。No。あ。来吃一啊。Now。

 Gr is a bit similar to that。And that it reads its standard input。And manipulates it。 And then。

Writes the result to stand it out， so。嗯。But Gr really only makes sense when you have。Multiple。Lines。

 so that's why I'm。嗯。IUing this echo command here which generates three lines。And grip。嗯。

Just like Z also accepts a regular expression。And。For example， let's say。B a。

And an arbitrary character。 So that would match power and puts。 And that's。

Really a filter for what comes through。 You know， we have food bar and buts。

Pipper through this scrap。 B A something。And B， A。Our mattress， B， A something and B A Z。

 also mattress B A something。And。Yeah， again， regular expressions are a very powerful tool and。

I don't want to talk about regular expressions too much here， but。

You really should know regular expressions。 and if I actually make another video series about compilers。

Chapter 1 is going to be about regular expressions， so。You really need to know this。Yeah， one thing。

A grabdes V inverts。嗯。The results， so。Grep V。As says。Just remove everything that matches the term。So。

Here， we only get the first line full because that is the only one that doesn't match。So these are。

This is script。Again， very useful tool。And the last package that I'm doing right now is bash。Yeah。

 what should I tell you， bash is the Bna again shell。And。Yeah， pretty much the absolute basis of。

A Linux system。So it's your command interpreter。 When you boot a Linux system。

 at least without a desktop， you're gonna see a bash， Pre certain。Pretty certainly。 I mean。

 some people like to。Change their configuration so that they get something like Z shell or。

seahell or whatever， but。I think the overwhelming majority of Linux systems。呃。

When you open a command interpreter， it's gonna be the bash。Okay， this is still not done， but。



![](img/7620c7e229704c2a7caa021fe15f39fe_42.png)

I don't want to wait forever， so。I want to get through this chapter really。

I'll just at least continue copying these scripts。

![](img/7620c7e229704c2a7caa021fe15f39fe_44.png)

So。Another batch of scripts。

![](img/7620c7e229704c2a7caa021fe15f39fe_46.png)

Andantrum but right back into it。

![](img/7620c7e229704c2a7caa021fe15f39fe_48.png)

![](img/7620c7e229704c2a7caa021fe15f39fe_49.png)

So this is getting as exhausting。 I'm doing this all day already。



![](img/7620c7e229704c2a7caa021fe15f39fe_51.png)

嗯。Here we go again。Okay， well， this is still running。

 Let's talk about these tools that we are installing now。 Are these packages。



![](img/7620c7e229704c2a7caa021fe15f39fe_53.png)

Yeah， lip tool is。

![](img/7620c7e229704c2a7caa021fe15f39fe_55.png)

A package that。Contains a good generic library support script。

 It wraps the complexity of using shared libraries in a consistent， portable interface。

 So that's basically。What you need to dynamically load shared objects， you know。

 the equivalent of DLL files。GDBM is a new database manager。嗯。

The library provides primitives for storing key data pairs， searching and retrieving the data。So。

Yeah， something like。A library for。For hashing and stuff。



![](img/7620c7e229704c2a7caa021fe15f39fe_57.png)

To store data。G Perf generates a perfect hash function from a keyet。



![](img/7620c7e229704c2a7caa021fe15f39fe_59.png)

嗯。Okay， a perfect hash function。It's pretty hard to explain， so。

It's a tool that you use in some programming projects， I think it。嗯。

It gives you an optimal way of checking。So like when you do something like a switch statement。

 but over us strings。嗯。Of course， in C and C plus plus， you cannot switch over strings。

But I think GPf generates something like that。And in an。

Optimal ways such that you will get to your selection in the shortest possible way。

Given the strengths。Expat sea library for X， M L。

![](img/7620c7e229704c2a7caa021fe15f39fe_61.png)

I need you。 Okay， that's。

![](img/7620c7e229704c2a7caa021fe15f39fe_63.png)

Some regular stuff like Ping and Tnet FTP。Trace route。I have conflict host name。

Pearl is a practical extraction and report language is a programming language。Relatively high level。

 also。Again， something that I don't think should be in a low level system like a Linux from scratch。



![](img/7620c7e229704c2a7caa021fe15f39fe_65.png)

X， M， L Pser。Okay， let's。

![](img/7620c7e229704c2a7caa021fe15f39fe_67.png)

唉。Pearl interface for passingsing X and L files。Well， oh， I。

 I just see it's actually an interface to expert。So。



![](img/7620c7e229704c2a7caa021fe15f39fe_69.png)

That explains why we have expert。Inter tool。

![](img/7620c7e229704c2a7caa021fe15f39fe_71.png)

I for internationalization。So。I think that's used to。

 it looks to me like this is used for actually automating internationalization stuff。



![](img/7620c7e229704c2a7caa021fe15f39fe_73.png)

Autocon and auto make。 Well， these are the so called auto tools。



![](img/7620c7e229704c2a7caa021fe15f39fe_75.png)

あ。A。Well create these con groups that we've been using all the time here and the make files that we are using all the time。

So。

![](img/7620c7e229704c2a7caa021fe15f39fe_77.png)

That set。Kmo。Is。

![](img/7620c7e229704c2a7caa021fe15f39fe_79.png)

For communication with the。Colonel for。For loading kernel modules， unloading kernel modules。

 So you have mud probe。Inmo， or M Mo。Lip e fo。 No lip elf。



![](img/7620c7e229704c2a7caa021fe15f39fe_81.png)

Is a library for handling。Elf files， executable and linkable format。



![](img/7620c7e229704c2a7caa021fe15f39fe_83.png)

Okay， lip FFI。The LFFI Library provides a portable high level programming interface to various calling conventions。

Open SSL well。I guess you know this already。SSL is。The secure socket layer。

 That's a very important library for。Enccrypted network connections。And then Python， well， Python is。

A scripting language， a pretty popular one。Widely used these days。Again， it's pretty high level。

Would actually rather prefer not to have it in here。嗯。But I think you need that。

For a compilation of some parts， I think in。I think for system D。

 you need Python if I'm not mistaken here， but。Again。As a purist， I would say。

If we could avoid having it， I would prefer to avoid it。



![](img/7620c7e229704c2a7caa021fe15f39fe_85.png)

Okay， here I need to set a paper size in Germany。A 4 is the。Standard size of paper。

In the United States， you might have letter。So you can configure that in Esy paper size。

So I'm going to set this to a4。Interestingly， here we have a pre。Determined J 1。Because， well。

Apparently， this has problems if。You would run multiple compile。Steps in parallel。So。

This really forces us to leave it at one。We can not say it up。And F， S， make drops。



![](img/7620c7e229704c2a7caa021fe15f39fe_87.png)

Okay。Great， so。Okay， so now we've。Run the last batch for today。Let's stop this。And， let's talk about。

These last packages。

![](img/7620c7e229704c2a7caa021fe15f39fe_89.png)

Okay， so Ninja。

![](img/7620c7e229704c2a7caa021fe15f39fe_91.png)

Ninja is a built tool， like make。嗯。It's a more modern built tool。I know that it's， for example。

 used in the。Chrome project。So。That is a testament to its quality， of course。



![](img/7620c7e229704c2a7caa021fe15f39fe_93.png)

Me sound amazing。 I'm not sure how to pronounce it is it。



![](img/7620c7e229704c2a7caa021fe15f39fe_95.png)

Another built system。嗯。Which I think is only needed for system D， but I don't know。



![](img/7620c7e229704c2a7caa021fe15f39fe_97.png)

Caaught your tilts， oh boy。

![](img/7620c7e229704c2a7caa021fe15f39fe_99.png)

嗯。What is not inuteruter is the better question。嗯。

![](img/7620c7e229704c2a7caa021fe15f39fe_101.png)

So let me just show you。Almost， I would say half the system is in core u tilt so what do we have？

Baase 64， encoding the。Open bracket tool， which is。Yes。A link to the test commanders， but。Well。

 in bash script whenever you see if。Open bracket， something close bracket， that open bracket。

 that's this tool here。嗯。Everything is in the base name， cat。Change group， change mode， change owner。

 change route。 check some copy。Cuts。Ddi。嗯。Their name， disk usage， echo environment setting。是。

Just look at it， it's everything， everything is in here。The I D tool。嗯。

Install is something that copies files with some more。Options。嗯。

Link shows the tool for making hard or soft links。Directory listing， M5 sum。Make directory， make。

Types， notes。嗯。Move， nice。Just look at it。 It's so much in here。print if。Print， working directory。

Read link， remove， remove directory。Different， some tools for different。Shan numbers。Sleep salt。

A be unique is also in here yet， thats unique。呃。S， T， T Y。TTY S in here。Sk。

Which fleshes system buffer us。嗯。Tee。So many of these that have already used in the script， you know。

So。Timeout translate， which can be used to。Turn uppercase to lowercase and lower case to uppercase。嗯。

You name is also in here。W C。Although I think wet count or what is it。Who， who am I。Yeah。

 so much stuff in coyuts。Okay， check is a testing framework for C。



![](img/7620c7e229704c2a7caa021fe15f39fe_103.png)

可以。D you tilts。

![](img/7620c7e229704c2a7caa021fe15f39fe_105.png)

Yeah， if you are。If you write programs， you probably know di。So， when you have。Two files。

 then diff will create。A so called diff file。Which basically describes the difference between these two files。

From file A and B， you create a divff file， something dot div。And。With patch。

 you can apply that def file to file A to make file B out of it。 So that's very useful， for example。

 in Git。 This is used for。When you submit your changes， you don't submit your whole new files。

 you only。Git just makes the the diff from your old version to your new version and then only uploads the diff。

 And if you pull。嗯。If you pull the changes。It actually only pulls the di files， and then patches。

Your old files with these di files to get the new files。

 So that's how you how you distribute your changes in a Git repository， for example。Okay。



![](img/7620c7e229704c2a7caa021fe15f39fe_107.png)

That's stiff。Gnu A。

![](img/7620c7e229704c2a7caa021fe15f39fe_109.png)

How do you describe Arc， It's very powerful tool。I would describe it like a bit like a spreadsheet application。

 you can write small scripts。And run them on CSV files。Not only CSV files。

 but that's a very common use case for Arc。And it's actually quite similar to C in its syntax。Okay。

 find， find another very useful tool。So with find， you can well。Find files。 So， for example。

 if I say find in the current directory， something。With's the name。Something dot S age， it will find。

All the。Shed scripts in here。You know， the ones directly in the。Dirctory， but also in subdirecties。

 you can limit the number of subdirecties so the depths you can set a minimum depth， a maximum depth。

嗯。You can limit the creation date or the owner。All sorts of things that you can。

That you can use to to specify what you are looking for。嗯。Actually， for the longest time。

 I've had problems remembering the order in which。You have to pass the parameters because。

It's a bit unusual that。嗯。You would。Put the directory where you are searching as a first parameter。

 and then。Have the。The different conditions that you are looking for。After that。

 that's a bit uncommon for Linux programme， but it actually makes sense when you think about it。

In the way that。With。The directory must be the first parameter， because you can have multiple。

Conditions here。Like I don't know something that contains an E。



![](img/7620c7e229704c2a7caa021fe15f39fe_111.png)

G。Processing and formatting text。

![](img/7620c7e229704c2a7caa021fe15f39fe_113.png)

I think it can produce。PD F files。嗯。Yeah， you have to set a default paper size here that you can。

Also。Change in Epssy paper size。Yeah are， not something that I will。Regularly use， but。By G。

 the Grand unified bootloaddown。Well， that's， of course， the thing that we will。A use in the end。

 too。To boot our system。So that's gonna be the bootloader that we will put。On。Oh。

Into the boot partition， but only later， so。Here we basically compiled the tools that we will then use to install the bootloader。

Like your gr and， for example， is used there。

![](img/7620c7e229704c2a7caa021fe15f39fe_115.png)

Less is a small。

![](img/7620c7e229704c2a7caa021fe15f39fe_117.png)

Text file viewer。嗯。

![](img/7620c7e229704c2a7caa021fe15f39fe_119.png)

Jesep another compression tool。I P route is for。

![](img/7620c7e229704c2a7caa021fe15f39fe_121.png)

Well。In networking， you have this notion of a default router。 So when。

You sent something that's outside your own subnet。Then it is sent to the default router。

 and I P route is necessary， if you。If you have more complex rules than that。 So， for example。

Where I work， we have multiple routers。 And depending on the I P address that we want to communicate with。

 it has to go to different routers。So。Then， we would need。Static roots。

Which would be configurable with IP root。KBD is something a tool with which you can select your keyboard layout。

So。You need to call this with。A certain keyboard layout， So that。

The Linux system will then recognize your keys correctly。You load keys。

 That's the tool I'm talking about。

![](img/7620c7e229704c2a7caa021fe15f39fe_123.png)

Lip pipeline， the lip pipeline package contains a library for manipulating pipelines of subprocessors in a flexible and convenient way。



![](img/7620c7e229704c2a7caa021fe15f39fe_125.png)

I've never used that， but it sounds useful。 I think I should look into that。Because I。

 when I write programs， sometimes I want to communicate with other programs and。It's a bit。



![](img/7620c7e229704c2a7caa021fe15f39fe_127.png)

Inconvenient， the way I usually do it。Make， well， the。



![](img/7620c7e229704c2a7caa021fe15f39fe_129.png)

Big， big。Built tool that we are also using all the time here。Here we。We use make all the time。

 here in there。In this。Scrips here。I've just seen another。Make car that I haven't。That， I haven't。

Sped up。Okay。第二。Very powerful tool。 I don't know。 If you know what you're doing， it's。

You can do a lot of things with it to。To really explain your whole idea of the connections between your source files。

嗯。I've used that to generate， to automatically generate a lot of stuff。So。

If you know what you're doing with it it's a really powerful tool that if you ask me。

There is just no other tool out there that even comes close to its feature completeness， so。

I really don't know why， why there are any other built tools out there whoever thought。

We need a new bill who just didn't know how powerful make is， if you know what you're doing。



![](img/7620c7e229704c2a7caa021fe15f39fe_131.png)

Okay， patch， I've already explained to apply diff files。



![](img/7620c7e229704c2a7caa021fe15f39fe_133.png)

MenD B。Contains programs for finding and viewing main pages。嗯。Okay，This is where a man lives。

 I thought that would be in。I thought it would be somewhere else， but okay。Okay， then that。

 of course， makes sense， because。Man is the tool。Used to view men pages。

I thought that this would have been part of man pages， but。Apparently， it isn't。



![](img/7620c7e229704c2a7caa021fe15f39fe_135.png)

T another。

![](img/7620c7e229704c2a7caa021fe15f39fe_137.png)

Powerful。Compression tool also used all over the place in the Linux from scratch。To set。

Text info contains programs for reading， writing and converting info pages。Sounds like some form of。

Of mark up。Translator or markdown translator， maybe。Okay， and Vm， yeah， very powerful。And also。

 very popular。Text editor。嗯。It's hard to get used to， really， because。

Normally youd assume that you start a text editor you start editing your text， not in V。呃。In then。

It's more that you will load a text file， and then you kind of program the changes that you make to it。

Okay， was I started here。 and now I was by pressing I I。Went to the editing mode。Okay。

Then with S I've。I've left the editing mode again， and now I am in the normal mode again。

Where I could use colon W to save the file。Coon queue to end the program。

Since I've done changes to it， it wouldn't let me so。I would have to say Q exclamation point to say。

 I don't care。 I want to。嗯。I want to leave。Anyways， but。Just an example。

 colon D3 would delete the next three lines。Like this。Okay。So。Colon， dear just deletes one line。You。

Donation pride， that's been。Nice tool。Very popular among programmers。But， of course。

By praising them here， I've of course， initiated another holy wall because。

A lot of people prefer Eax。And。I don't even have it installed。



![](img/7620c7e229704c2a7caa021fe15f39fe_139.png)

From what I've seen， it was just too complicated for me。Okay， so that's all the packages that。

We are currently installing。And。It only took me about。About 10 hours to go through all this。

The Linux from scratchbook says the compilation takes or。

Would take about five hours on a system like this， but as I said。With the auto tests。

 I guess that's why it's taking so much longer now。And again， because I'm running it on now。

On our USB key instead of SSD hard drive。 So yeah。Okay， so this is everything I want to do for today。

As I said， about 10 hours， I think that's enough for today。So yeah， if you like this video， like it。

 share it， subscribe。嗯。Maybe just like it for the sheer effort of doing this for 10 hours today。

 So I actually took a day off from work for just for this。And， yeah。Tune in next time when we will。

Go into the。The init system and probably also already in the system configuration。

 so then we will really go to the really interesting stuff。I'm really looking forward to that。

See you next time。By。

![](img/7620c7e229704c2a7caa021fe15f39fe_141.png)