# 【全集 秋季版】普林斯顿大学 C语言系统编程 中英字幕 p02 Lecture 2 - Bash -BV1u1feBoEsK_p2-

Welcome back to lecture 1， Part B。 It has long been our experience in this class that people are apprehensive about using the command line。

 at least at the start。 I know a lot of people come into 217 straight out of 1，26。

 where the command line is left mysterious at best。😊，When 26 students learn a few shell commands。

 such as more and about input and output redirection。 But every time it's used。

 they can just copy it off the assignment check list by rot In this course。

 we're going to be using the shell command line interface a lot more。

 So the best thing you can do early in this course is to experiment。

 The earlier you play around and get up to speed。Using Linux。

 the less time you'll waste later on in the course trying to work through Linux confusion and inefficiency when you could be spending the time on topics more germane to the assignments themselves。

So the rest of this part of lecture is going to be a walk through of some simple execution in the Linux command command line shell with a few more advanced things。

 Admittedly， this is going to be a whirlwind of information that's probably too much to take in all in one sitting。

 particularly if you're particularly new to Linux。But you might return to watch this again after you've gone to the first precept and gotten the precept handout。

 givingiv you a different form of a whirlwind tour of all the Linux commands you could ever imagine。

Or even still， as you continue to experiment， you can come back and see， Wait， did I get everything。

 Do I now feel that this is less of a whirlwind and more just yet， I know this。

I'll also give a little bit more time in this week's second lecture so that that way。

 if you follow along with it again， you'll get more time to practicerac。

 And also that will give me some chances to give you a few tips and tricks for idiomatic usage or more advanced features and configuring some niceties that make it a bit friendlier and more modern feeling place to work and develop。

If you're already comfortable with bash， great， I do encourage you to still watch the rest of this。

 but you can do it on super speed。But I know that any time I sit down and watch somebody else working on the command line。

Invariably there were a few times ago， Wait， what did you just do， That was cool。

 I'll need to remember that。 So hopefully you'll get at least as many of those in in this lecture and。

 and the bit of the next as you do。 Oh， that was awful。

 He should totally know a better way to do that。😊，Two more thoughts， before we dive in。First。

 as you've already heard me say and you'll hear me say repeatedly throughout the course。

 the way to get better at programming is to program。 In this case， that applies here too。

The way to get better and more comfortable at using the Linux environment is to immerse yourself in that environment and try to do things in that environment。

 as opposed to working just as hard or harder， trying to find ways to avoid doing that。

My second thought， and I hope it's a calming one。Is that if you play around now。

 if you experiment now。There's almost nothing you can mess up。

Because you're starting from an almost completely empty account。

 Any mistakes that would wipe out anything on your account would just be wiping out products of your own experimentation。

 So the opportunity for learning and developing competence and comfort at effectively no risk is a pretty great bargain。

😊，All right。 So we have our terminal terminal emulator here。 It's already logged into arm lab。

 and we're ready to run commands in our shell。 Now what。😊，The first thing we can do is。

Look at our shell prompt and see that it actually tells us a bit of information right now。

It tells us what machine we're on。 arm Lab 0，2。 recall that arm labb is just a front door to two different machines。

0，1 and 0，2。 And what directory we're in Tilda， which I'll explain in just a second。

Note that the shell prompt is highly configurable。 though this is the default that we have when。

 when you configure your account， according to how we tell you to do it in precept。

 and in the lecture notes and the other materials well often just put a dollar sign because by custom。

 typically shell prompts end with dollar sign or percent sign。

The prompt sits here apparently doing nothing， but what it's really doing is just waiting to take the command。

So if you enter the command and press return， it will begin the shell's loop of trying to interpret the command。

If I just say， junk。Well， it's a junk command。 It isn't a command on the system。

 So the shell immediately processes it attempts to run it and reports back to me with an error that this command doesn't exist。

But naturally， we want to focus on commands that do exist。

 So Let's start off with how to get the lay of the land。

 I mentioned above that the shell already tells us some things It tells us the machine name。

 but we know that's not the entire machine name。 We can get the entire machine name。

With the host name command， which tells us that it is Arlabo 2 dotss at Princetonnetti view。

Note that this is case sensitive。 If I do host name， it doesn't tell me anything。

This is a Linux thing， not a bash thing。 If I come back over here onto still bash。In my。

 on my Mac book。 And I do host name。That one actually works perfectly well。 So it is a Linux thing。

 not a bash thing that it's case sensitive， but that will be the case for。

All of the commands that were going to run and all the files were going to create。是。

We've learned how to verify our host name。 We can figure out who we are with the command， Who am I。

But none of this was surprising。 I know how I logged in。

 I know what machine I logged into and what account name I used。The next thing then is。

 where am I on the file system？The prompt says Tilda， but that's weird。

 That's not entirely meaningful。What you have to realize is that the Linux file system is a tree。

 It starts at the root， which is a directory that doesn't actually have any name。

And then it has a series of subjecties。Demarcateated with slashes。

 So you can think of these slashes just as if you were to draw a tree in a data structuress course。

 And so if we do something like this， if we do you seem ready。



![](img/f058e9e345e76f5c3c704b5304fd26b1_1.png)

We get somewhere， and that， in fact， is the director I'm in。Every Linux system。

 when they set up user accounts typically gives each user their own directory。 in this case。

 it's slash you slash the result of who am I， the login name。Your login name is your net， I D。

So here I am in the directory slash U s Cer readyti。

 oftentimes we don't pronounce the slashes and we'll just say in you Seeer readyti。

But that's not what it said。 It said Tilda， Well Tilda is just a a short cut an alias for the user's home directory。

It's convenient because we often want to interact with our home directory。

 And so it saves us a little bit of typing to do Tilde as opposed to slash use slash your net I。

So that's where we are。 And when I did in L。 S， it actually shows us what's here。 L。

 S for the list will list the contents of a directory。 If you don't give it an argument。



![](img/f058e9e345e76f5c3c704b5304fd26b1_3.png)

It will just list the current directory， but as you saw before。

 we can give it an argument and it will list the contents of that directory。



![](img/f058e9e345e76f5c3c704b5304fd26b1_5.png)

You can give arguments that are directory names in any of several ways。

 You can give a full path name。 So before I did slash you slash See ready。If I was sitting in you。

Where in sitting in C， I could do a relative or non absolute directory。

 so I can do LS U slash See ready with no slash because I'm already there。



![](img/f058e9e345e76f5c3c704b5304fd26b1_7.png)

All right。 So now you've seen how I can move around as well。 C， D will move to a directory。 Again。

 you can give it an absolute path or a relative path。 You can also do what I just did and do C。

 D with no argument， which will take you back to your home directory。 This is a nice。

 natural default case， because we often want to do that。😊。



![](img/f058e9e345e76f5c3c704b5304fd26b1_9.png)

One more nice city with C D。 We can do C D dash， and that will move us back to whatever our previous。

Directorory was。If you ever want to see your directory and you don't want to just trust what the shell prompt says。

 again， the shell prompt is configurable。 Also， Tilda doesn't really tell us a whole lot。

 we can use the PW D command for print working directory。



![](img/f058e9e345e76f5c3c704b5304fd26b1_11.png)

If I see back to what I think should be my home directory， it tells me it is。

 but I can again confirm that with Pw D。

![](img/f058e9e345e76f5c3c704b5304fd26b1_13.png)

So in my directory， when I do L S， I see a number of different types of things。

 The blueluish purple things here are directories。 These are subdirectories of my home directory。

 And then there's also。

![](img/f058e9e345e76f5c3c704b5304fd26b1_15.png)

Fileles that are in just the default text color。If I want to go somewhere else。

 let's continue with the C D example。If I just type D， E here and then hit tabab。

 it will autocomp to the best of its ability。This isn't perfect。

 So if if I cancel that out and do C D S and hit tab， it blinks at me。 It says。

 I can't fill that in any farther because you have string pro and survey pro and Sim table pro。



![](img/f058e9e345e76f5c3c704b5304fd26b1_17.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_18.png)

And shellpdge。But if I give it enough information。I just type the U， I can now again hit tab。

 and that will give me a full a full tab completion。



![](img/f058e9e345e76f5c3c704b5304fd26b1_20.png)

And then I can enter and go。Another nice thing you can do。



![](img/f058e9e345e76f5c3c704b5304fd26b1_22.png)

If I come back here。Imagine that you don't want to go back and remember， Wait。

 what was in that directory that does begin with that， You can hit tab twice。

 and it will print all of the options that are fitting that， that prefix。

 And now I can see which 1 I want。

![](img/f058e9e345e76f5c3c704b5304fd26b1_24.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_25.png)

I thoroughly encourage you to use T completion， if only because the lab Ts will go nuts if you sit there trying to type out really long path names or really long command names without tab completing。



![](img/f058e9e345e76f5c3c704b5304fd26b1_27.png)

All right。 So now we're in survey Pra。 And when I do an L S here。



![](img/f058e9e345e76f5c3c704b5304fd26b1_29.png)

You'll see that there's actually something slightly different。 You can't quite tell from。

 from my text， but there is actually a green that is different from my text green for a conduct survey。

 so that green color indicates that it's anexecutable。



![](img/f058e9e345e76f5c3c704b5304fd26b1_31.png)

Let's see how we can run the executable。 One might think that just like the other commands were doing like L S and C。

 D， we could just say conduct survey。 But when I T completed， it doesn't do anything。And indeed。

 if I try to type it out completely， I think I spelled it right。 It still doesn't do anything。

The reason here is that the system， as we have it set up。

 is configured not to attempt to run things from the current directory unless you explicitly tell it to do so。

 We'll talk more about this in the more advanced topics in the next lecture。 But for now。

 you can just think that I have to give it a relative path。

 starting with the directory it belongs in。 So in this case， where here。Now。

 we haven't seen this before， but dot is just an alias for here。

 It just means the current directory that I'm in right now， wherever that might be。

So now if I say here。Conduct survey。 That will work。 That tab completed。

 I also could have given it a。

![](img/f058e9e345e76f5c3c704b5304fd26b1_33.png)

Absolute path。If I actually gave it the correct。

![](img/f058e9e345e76f5c3c704b5304fd26b1_35.png)

Path。And that would work as well。But again， typing all of that out is much less nice than dot s conduct survey。

 And as proof， this actually does work。 This is the program for assignment 0。



![](img/f058e9e345e76f5c3c704b5304fd26b1_37.png)

You've seen me do this a few times。 Control C。 You learn this in 1，26。

 Control C will cancel out an execution。 This is useful if you have something like an infinite loop。

 but it's also useful when you just start saying， na， I've thought I wanted to run that。

 but never mind。 I don't。

![](img/f058e9e345e76f5c3c704b5304fd26b1_39.png)

All right。So let's go back to the previous directory。How can I do that， I have several options。1。

 I could use the absolute path。 I could do C， D， slash U， slash C Mer ready。That's cumbersome。

I could do a relative path。Dot's cousin， remember， Dot is the current directory。Dot's cousin is dot。

 dot， which indicates the parent of this directory， so we could do。



![](img/f058e9e345e76f5c3c704b5304fd26b1_41.png)

That， and that would be fine。

![](img/f058e9e345e76f5c3c704b5304fd26b1_43.png)

We've already seen C the dash that will move us too。The previous place we were。

 which I think was my home directory， but I'm not entirely sure。Again。

 since the parent of this directory is my home directory， I could do C D Tilda or just C D。

 and all of those would work。

![](img/f058e9e345e76f5c3c704b5304fd26b1_45.png)

There's the one we haven't seen and again， gets back to our home directory。

So now that we know something about directories， how do we get them in the first place？

All of the commands we've seen thus far are abbreviations。 let's say L S is short for list。

 and C D is short for change directory。That's a recurring theme。

 So here we're going to do make directory， but we're going to arbitrarily cut off some letters。 So M。

 K for make D I R for directory。Don't ask me。 I didn't do it。



![](img/f058e9e345e76f5c3c704b5304fd26b1_47.png)

So make D， if I just try and do that， it will tell me missing up R， And this is typical。Normally。

 when you do something wrong， it will print out some information about how to use that command。



![](img/f058e9e345e76f5c3c704b5304fd26b1_49.png)

In this case， it tells me there's a missing upand， but it doesn't really tell me what it should be。

 What it does do as many programs will。 Many standard commands will have a minus minus help command line option that you can give that will give more information。



![](img/f058e9e345e76f5c3c704b5304fd26b1_51.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_52.png)

If we do that。The standard here is that the usage will have all caps。

 things are the arguments and with hopefully some meaningful name。

 and things in brackets are arguments that are optional。So in this case。

 makector takes various options， and the thing that absolutely has to have is a directory。

We could have learned more about this with not just the help page。

 but there's actually for almost any given command and also many library functions。

We have the manual pagess。 I mentioned this slightly in the first part of this lecture。

 we can do man。 and in this case， maketer。And this gives you a little bit more verbose description。

The main page interface is a bit clunky， you use Return or enter to go one line at a time and space bar to go a screen at a time。

It does tell you how to use it。 you can use H， and then to get out of here， you do Q forqui。

So we learned a little bit about this， we learned that we can make her and just give a directory name。

 so let's do it。Make D A， everything looks good。Makector X， Y， Z。No complaints。

 Hopefully those actually exist。And indeed， we see that we have A and X， Y。

 Z that were created right about now。So we can do each of those separately。

 What we can also do is make a directory hierarchy all at once。 So I can do make D B C。

But it doesn't actually work quite yet because B doesn't exist。I could do maketer B。

 and then maketer B， C， but maketer actually provides a minus P option to make all of the parents in the。

 in the hierarchy。 So maketer B， C will do it。We have L S。 We now have a B， L S， B， we have a C。



![](img/f058e9e345e76f5c3c704b5304fd26b1_54.png)

So that's all about maketer。

![](img/f058e9e345e76f5c3c704b5304fd26b1_56.png)

If we tried to the one last thing is we tried to make a directory that already exists。



![](img/f058e9e345e76f5c3c704b5304fd26b1_58.png)

It won't let us。 It will fail with a meaningful error message that says we can't do it because it already exists。



![](img/f058e9e345e76f5c3c704b5304fd26b1_60.png)

All right。So now we've created a whole bunch of useless directories， let me clean them up。



![](img/f058e9e345e76f5c3c704b5304fd26b1_62.png)

I can do so with the R M D IR command。 Again， we're going to have random letters there and not。

 But R M for remove D IR for directory。 So R M D IR。



![](img/f058e9e345e76f5c3c704b5304fd26b1_64.png)

I can do a bunch at once。

![](img/f058e9e345e76f5c3c704b5304fd26b1_66.png)

But not all of them， because B is not empty。 So R M I R will only let you remove an empty directory。

 This is for your own benefit。 so you don't remove something and go， oh。

 I just deleted everything in the world。So here it won't let you。

We have a number of different ways we could do this。 We could remove。B， slash C。

 we could remove using the same。Command the same option minus P that we did for maker。

 We can do remove B slash C。 that would also work。

![](img/f058e9e345e76f5c3c704b5304fd26b1_68.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_69.png)

So now， if I do an LS， I have proof that all of those directories went away。



![](img/f058e9e345e76f5c3c704b5304fd26b1_71.png)

Allright， so let's get one new directory again and we'll talk about files。



![](img/f058e9e345e76f5c3c704b5304fd26b1_73.png)

Note that when I make a directory， it doesn't actually go there。

 It just makes it and leaves the location the same as it was。

 So maketerss are very often followed by C。 One of the most common short cuts I've seen in people's advanced configurations is actually to have a new command for maketer That's a maketer and follow thats some short keyboard sequence to say。

 make a directory and then go there。

![](img/f058e9e345e76f5c3c704b5304fd26b1_75.png)

All right， so we went to file test and we need some files。

 I know of one file that we saw in the previous directory。 So let's use it。 We will use C to copy。

Again， with the， these are the right letters， but not all of them。We can give the path。

 using the tilda for variety。

![](img/f058e9e345e76f5c3c704b5304fd26b1_77.png)

And we will copy it to dot。 What does dot mean Dot。 Remember， is this current directory。

 If we give it a directory name， it will keep the same file name as it already has。

 If we give it a file name。

![](img/f058e9e345e76f5c3c704b5304fd26b1_79.png)

It will give that file names。 Now， we have a bashhar C and a bahar C， too。

 I forgot the dot in the second one。 It doesn't actually matter in the sense that。

 unlike in some operating systems， fileile names are pretty arbitrary。

 You'll notice that we're not dealing with things that have suffixes。 None of these is dot text。

 I have or don't have a dot at the beginning of it doesn't matter。

 We can name things almost whatever we want。All right。So we saw L S before。

 but now that we know about man pages， we can do a little bit more with， with L。 S。

 So if we do man L S。

![](img/f058e9e345e76f5c3c704b5304fd26b1_81.png)

You'll see that there are a lot of options。 I mean， a lot， a lot of options。



![](img/f058e9e345e76f5c3c704b5304fd26b1_83.png)

So many options。So many options。Let's use L S minus L。 That's the most common useful one。

 And that gives us a long listing of what's here。So here there's some confusing stuff。

We've got dot and dot dot that's been appearing。 And now we see information about them。 So we're。

 we're listing our directories。 We also have the two files。Over on the left， we have permissions。

These are permissions for the files。 They look cryptic。 We'll talk about them in another session。

 but basically it's the second， third and fourth digits there are the read。

 write and execute permissions for me as the owner of the file。

A read means I have permission to open the file。 A write means I have permission to to edit the file and execute means I have the ability to call it as a command。

 In this case， these are just text files so I can read them。 I can write them。

 but execute wouldn't do much。All right。 you'll also notice that the directories have slightly different permissions。

 They are Byzantine， and I will again， we'll talk about them in a different， a different lesson。

 but I will also leave them to you to learn about by doing man page on the C H Mod command， C H Mo。



![](img/f058e9e345e76f5c3c704b5304fd26b1_85.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_86.png)

Changes the permissions in a file， or as they call them the file mode bits。

The other information about the files we have in addition to the permission。

 some stuff about how it is stored in the file system。The owner of it。

 you can see my username seem already there。 The size of the file， in this case， 1，9，8。

8 is the number of bys in the file and the modification time。 This is the last time it was updated。

So now we can look at several file commands。 The first is cat， which is short for concatenate。

 which means。Append that file to something else by default， the terminal。Added at the end， so。



![](img/f058e9e345e76f5c3c704b5304fd26b1_88.png)

Bachelor C，2。It prints out the entirety of it。

![](img/f058e9e345e76f5c3c704b5304fd26b1_90.png)

That's useful in lots of cases， but it's not so useful for reviewing it。

 because then I'm requiring to。

![](img/f058e9e345e76f5c3c704b5304fd26b1_92.png)

Scroll up a whole bunch。 And that's just not the best way。



![](img/f058e9e345e76f5c3c704b5304fd26b1_94.png)

A way to see it progressively is more， which perhaps you saw in win 26。Here we can do more。

 It shows us one screen。 We can again hit enter a few times and go one at a time。

 or we can do the space bar to go a screen at a time。



![](img/f058e9e345e76f5c3c704b5304fd26b1_96.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_97.png)

You don't have to understand what any of this says。

 Bsh or C is actually a configuration file that is a bunch of bash commands that gets run when you begin your shell。

 So it's basically if when you start your shell， you always want to do something。

 you can have it done automatically。 In this case， it's a whole bunch of set up。



![](img/f058e9e345e76f5c3c704b5304fd26b1_99.png)

Getting a baache or C is one of the pieces of the setup that we'll ask you to do with configuring your environment in precept 1。



![](img/f058e9e345e76f5c3c704b5304fd26b1_101.png)

So along with more， more isn't that great because if I do this again and now I say， oh。

 I went too far， I want to back up and it doesn't let me。



![](img/f058e9e345e76f5c3c704b5304fd26b1_103.png)

So as a terrible pun， less is a command that is more than more。



![](img/f058e9e345e76f5c3c704b5304fd26b1_105.png)

Because it can do more things。If you user it， less。



![](img/f058e9e345e76f5c3c704b5304fd26b1_107.png)

That Ba or sea。

![](img/f058e9e345e76f5c3c704b5304fd26b1_109.png)

You will see that you can go down just like before， and you can also go back up。

 which is perhaps useful。The weird pagination over there on the left is just that I have a comment that is wider than my terminal。

 And so it wraps around。 This is why when every style guide you ever see says。

 don't make your lines too long。 This is why。

![](img/f058e9e345e76f5c3c704b5304fd26b1_111.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_112.png)

As an aside， those line numbers are something that's actually set up in my baachelor C that won't come in the default configuration。

 but less is still more than more in that you can move up and down。

Other commands to see what's in the file， you might want to look at only the top or only the bottom of the file。



![](img/f058e9e345e76f5c3c704b5304fd26b1_114.png)

First， let's do clear。 Cl just says， I'm getting frazzled by how many things are on my terminal right now。

Move them all up and give me a fresh screen。So I can do just the first bunch of lines。

I can control how many of those there are with head minus n in some number。And the。

 the opposite of head is tail。 So I can again do tail minus N 5 E C。



![](img/f058e9e345e76f5c3c704b5304fd26b1_116.png)

And it will give me the last five lines， so head gives you the first end lines。

 tail gives you the last end lines。Another thing we might want to know is how big a file is。

We saw that we can give some options to Ls and get this。

 But another tool that you'll find useful is WC， which prints out the number of lines。

 number of words and number of characters。You might ask whyWC。

 well it's an extension of the old word count program。

 which tells you how many words it just in this case tells you a whole bunch more than that。

In this case， word just means a series of non white space characters delimited by white space。

 It's not actual English language words or anything like that。So we can do WC。



![](img/f058e9e345e76f5c3c704b5304fd26b1_118.png)

And we see again that 1988 is the number of bites it apparently has 66 lines and 249 words。



![](img/f058e9e345e76f5c3c704b5304fd26b1_120.png)

One got you with several of these commands like Cat and W。 C。 And les。

 like you already saw me make the mistake， is that。If not given any arguments。

 they compute on standard input。 So if you just say W C minus L to give it the word count。

 show me only the number of lines， it will appear like its's hanging。



![](img/f058e9e345e76f5c3c704b5304fd26b1_122.png)

Looks like it's not doing anything。

![](img/f058e9e345e76f5c3c704b5304fd26b1_124.png)

Not doing anything， but it's not。 It's actually waiting for input。

 And so if we say I'm done with input， never mind， will actually tell me that I wrote three lines。

 You might recall from， from 1，26 that control D will say I'm done with input。 Send it E O F。

 so to speak。

![](img/f058e9e345e76f5c3c704b5304fd26b1_126.png)

![](img/f058e9e345e76f5c3c704b5304fd26b1_127.png)

So you might ask， why would they do this， Why would they have this hang up that seems to be naturally confusing。

And one common workflow in Linux is to use pipelines。 You learned about this in 126。

 I know it comes up on exam 1 frequently， and you had to use it in the atomic assignment。

If we want to run a command and then see statistics about the output。

 we can run the command and then pipe the result into W。 C。 So consider， for example， if instead。

 instead of wanting to know how many characters there were in the entire file。

 we only cared about the first line。That's how we get the first line。

 that head command that gives it the minus n to say， how many。Fashhar sea。 And we piped that into。

 Let's see all of them。 It indeed， has one。

![](img/f058e9e345e76f5c3c704b5304fd26b1_129.png)

Line weirdly enough， it has one word and it has 73 characters。 Why does it have one line， Well。

 if we cat。

![](img/f058e9e345e76f5c3c704b5304fd26b1_131.png)

Dot bash R C， you will recall that。That doesn't do anything because it shows us all of it。

If we do head minus n1， depth batch or C。You'll recall that it has a comment at the top That is just this one big long line of dashes。

 So there is only one word in the entirety of the line。All right。 So while we're on the topic。

 other re directions， In addition to pipelines are super useful。 You learned about them in 126。

 So if I wanted to copy a file， we saw I could do a C P。 I can also cat the file。



![](img/f058e9e345e76f5c3c704b5304fd26b1_133.png)

And then redirect the output， cat writes under standard output， so redirecting the output to Bas C3。

 and that works great。You'll see that it has exactly the same contents， it is newer。



![](img/f058e9e345e76f5c3c704b5304fd26b1_135.png)

So we can do that。We I will note here that more realistically that would just be a copy would be using it with something like header tail。

 So if we only wanted a portion of the file， we could do head minus-1 do ba C output to header line。

And now we have header line that's only those 73 characters on the first line。

So just now we saw one way to create a new file by redirecting output from a command。

 There are numerous other ways。If we want to create an empty file， we can do touch。

Touch will create an empty file。Touch is actually， that's a side benefit of it。

 Touch's real purpose is to update a file to be its modification time more recent。

 So if I touch bahar C 2。And I check。It is now 10 minutes newer than it was before。

 So that's what Te really does。 But it has this nice benefit of youtetraophil that doesn't exist。

 It creates it。We just saw output redirection。 We can actually output redirect the null command。

So this says run no command。And then output its standard output to this file。 Well。

 no command has no standard output。 So that works great。 The null command is actually a thing as。

 as a bash syntax token， but it doesn't do anything。 It's just there for purposes like this。

One thing to note， many of the commands we've seen thus far copy move overwrite are cautious。

 The way that we have it set up is that it won't clobber。 It won't overwrite without asking you。

 So in the case of copy if I try to copy header line to header line  too， it will ask。

 do you want to overwrite this， And I can say yes or no。Similarly， if I want to move。

 I can move header line to header line 3。 It will ask， do you want to do this， yes。嗯。

The overr is similar if I cat Baashhar C 2 to headerline 2， It will tell me ye can't do it。

 There's a way around this， though， because it's not prompting。 it's just saying y can't。

 If I overrite and put a bar that says， no， really， I want to overwrite it。

 And so that will actually do it。 And as proof， headtterline 2 now has 1988， not 73。Finally。

 of course we could use a text editor to create a file and that's probably the most common。

 but I will leave EmX and other text editing goodness to precept。

So we've seen copy saw I just showed you move， which says move a file from one location to another。

 This is also good for renaming it。The last thing to talk about is we saw removeer RMDIR。

 We can remove a file with just RM。R M up Baashhar C， it again， is cautious。 It will ask you。

 are you sure you want to do this。That's the basics of how to move around directories。

 how to work with files in simple manner。 There's lots more to Linux。

 I encourage you to play around with it。 Take the precept hand out， play with all the things。

 See what you can find out。 And next time for Thursday's lecture。

 I will give just a little bit more about how to configure bash to do some cool things。

 and how to get an environment that feels a little bit more， more robust。😊。

