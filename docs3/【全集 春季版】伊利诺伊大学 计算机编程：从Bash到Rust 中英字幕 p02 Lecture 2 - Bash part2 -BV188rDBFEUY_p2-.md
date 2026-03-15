# 【全集 春季版】伊利诺伊大学 计算机编程：从Bash到Rust 中英字幕 p02 Lecture 2 - Bash part2 -BV188rDBFEUY_p2-

Will be album。But aside from that， no other logistical announcements for today。

 we can just go ahead and get started with the lecture。can everyone hear me。



![](img/980cd4b18c5b1a14d5de6db97818aefd_1.png)

Yes， okay。 cool。 So start off， let's get the Kaahhoot started up right away， so。😊。

We're going to Kahoot again for questions and attendance， so。🎼Joining that right now。🎼The。🎼，Oh yeah。

 don't put a nickname， Quaer Ne ID as during day， so we can keep track of whou。🎼，🎼，🎼。🎼Yeah。🎼。🎼，🎼哎。🎼。

🎼The。🎼，🎼，🎼Yeah。🎼。Okay， is everyone in？Raise your hand if you're not in the caooot yet。O。Oh。

 people just join。 Okay， raise your hand if you're not in the caahooot yet。Is everyone in the cahoot。



![](img/980cd4b18c5b1a14d5de6db97818aefd_3.png)

Okay， cool。

![](img/980cd4b18c5b1a14d5de6db97818aefd_5.png)

So welcome to Bsh part two。We're gonna build off what we learned last time。

 teach a few more commands， and then move beyond commands to do cool stuff like batch scripting and text editing files inside the terminal。

😊，So here's objectives for today， we want to go over。If two commands。We're not going to do piping。

 We're going to do text editors。OfV Emax and nanono。

 and they we're going to do an intro to batch scripting。And we have time we also do alias thing。

So our first command for the day is pseudo。 So Su is super user do。

 So that gives you root access to your computer。 So what does root access mean。

 Root access the same as admin privileges， You can think of the root user as being the supreme overload of your computer。

 root can do whatever he or she wants to。 So if you want to delete drivers that control your screen or your keyboard。

 you can do that。But let's say you want to do something like install a new program to the root directory and you need permission for that if you write pseudo and in the command。

You will do that regardless。 we punched for password。

 and you' will do that regardless of what that command is。An important thing with Ruto with Su。

 sorry， is that with great power comes great responsibility with pseudo。

 you can do whatever you want in the terminal。 So be very careful because you can。

Break things that you didn't want to break。 you know， delete core files。

 So if you're using pseudo would be very careful。 And you might wonder。

 like if I want to always have control in terminal， why didn't I do pseudo before every command。

 Well， firstly， it's annoying to type pseudo for every command。 And secondly。

 you don't need to have root access for most things you're doing Like if you just want to list the files in director。

 You don't need to have root access， things like that。



![](img/980cd4b18c5b1a14d5de6db97818aefd_7.png)

And the way you use pseudodo is let's put this together。



![](img/980cd4b18c5b1a14d5de6db97818aefd_9.png)

Okay。You basically take any command you want。 So Let's say we want to。

Let's go to the Intro to Ba directory。Let's do wantan to delete a file。 We can do pseudo R M。

 Let's say the file is like。Protect the file you can use pseudo R M， and then put the file name。

And we hit enter， you'll be prompted for your password。

 An important thing here is when I type my password。You might hear my typing。

 but nothing is doesn't look like anything we typed in。 That's to protect you。

 So no one can see the length of your password。 I can type my password in now。

And that file got deleted。

![](img/980cd4b18c5b1a14d5de6db97818aefd_11.png)

Yeah， very important。 Be careful in using pseudo because you don't wantan to。



![](img/980cd4b18c5b1a14d5de6db97818aefd_13.png)

Damage things that you shouldn't be touching。

![](img/980cd4b18c5b1a14d5de6db97818aefd_15.png)

Alright， so now we're going to talk about find。 Find is true for find。 There's no acronym there。

 It's a really powerful tool for locating files。 And once you find a file。

 you can then run commands on those files。So the way you use it is you type file， give it a path。

 and then you hit enter， and all the files in that directory will be listed。

 and it's not just the files in our current directory。

 It'll recursively go through all the directories in there and then continually print that out。



![](img/980cd4b18c5b1a14d5de6db97818aefd_17.png)

So， for instance。Also for clarification， this window on the left side is just my。Findder。

 you're gonna see my files in here。 So I know this is a bit of confusion last time。

 This is just to see what's going on in a more gooey based way， something we're more used to。

So right now， if I print the working directory， we're in intro to bash。But let's move up。 actually。

 let's do from here。 We' can do find。 And then dot。

 So dot is the home directory or sorry the directory that we're currently in。

 So I want to see all the files are in this directory。

 And you can see if you look in the side here in intro to bash is's only directory  one and this Python file。

 if I hit enter。😊，You can see lists all the files， including the hidden files。

 and it'll go into the directories and print all the files and the directories in there。

Any questions about the fine function so far， We're going do some more on it。



![](img/980cd4b18c5b1a14d5de6db97818aefd_19.png)

No， okay， cool。Okay， so we're gonna to use some flags with fine to change its behavior。 So firstly。

 we're gonna talk about the name flag。Basically， if you type a command and and a directory。

 you're just list all the files in a directory。 That's not particularly very useful unless you have some very specific purpose。

 But what you can do is you can do a find。Diectctory and then do the name flag and followed by the name of a file。

 and then you'll be able to find the paths to specific files in that directory。



![](img/980cd4b18c5b1a14d5de6db97818aefd_21.png)

So。Let's do。 Let's first go into directory 2 or directory 1。 Sorry。

 let's make a couple of files here。 Let's go the first one，1，96。File dot TXT。

And let's make a couple of these。Okay， and as you can see here， when I list the files。

 we have several files which have 196 at the start of them。Now， what we can do is we can do find。

 Let's do want to find one file。 First of all， let's do find。

In the home direct and the director we're currently in。1，96。File that T X T。 O， sorry。

 forgot the name flag。Hter。And we see we get the path to that flag， to that file， sorry。

But now we briefly spoke about wildcard's last lecture。

 So the wild card is essentially when you put a star in front of an extension。

But it's actually a little smarter than that， which you can also do is。

Let's say I only want to find files that start off with 1，96 and end in dot T X T。 I can do find。

Dot fur the current directory， 196 star do TXT。So does anyone to guess what this will do？Anybody。

Yeah。Exactly， so I hit enter。Oh， I forgot the name tag， name flag。Give me a second， oh。1，96。File。

 that takes you。嗯。One second， sorry。We're facing tactical difficulties。Alright。

 let's do the other way around。 So let's say we want to find。A file do T X T。

And we wanted to be prefixed with something。 but a star there。 hit enter what is going on。 Sorry。

 one second。

![](img/980cd4b18c5b1a14d5de6db97818aefd_23.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_24.png)

Okay， yeah we'll lose this for now。 We'll come back to you in a second。 Sorry about that。

 I think I'm just messing up one of the， the prefixes there。

 But we can also move on from the wild card and do I name。

 So let's say we have files which are case incentive。

 So let's say we make a file with a bunch of capital letters。 So we go touch。



![](img/980cd4b18c5b1a14d5de6db97818aefd_26.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_27.png)

Capital file that TX you。Now， we want to find this file， but we don't know， like。

 if it's k sensitive and sensitiveitive， we can do。Find。And do I name as the flag。

And do capital file。That TXt。And you can see it found this file。

 even though it's fully capitalized here。

![](img/980cd4b18c5b1a14d5de6db97818aefd_29.png)

That makes sense。概扩。

![](img/980cd4b18c5b1a14d5de6db97818aefd_31.png)

And finally， we use the delete flag， so the delete flag is different from the name flag because we don't pass it any arguments。

We basically just take whatever files are found by fine and then delete them straight away。So。

 for instance。

![](img/980cd4b18c5b1a14d5de6db97818aefd_33.png)

Let's make a new file in directory1。This file is going to be called delete me。Okay。

 amm not going to move up a bit。Now， my desktop。So first， let you find， you find。pass it。

A directory in a bash。namee。Delieteve me。ThatTXT。Okay， so now we have a path to this file。

And now if I do the same command， but I add the delete flag。

So you can keep track of it on this side here。They'll find it and delete it。That makes sense。

Similarly， let's say I want to delete oh， sorry。快什么。So the question was。

 how do you revokeke an action once you delete it， You can't if you delete something or do RM in terminal。

 it's gone forever， it doesn't go to the trash。 It's just fully deleted。

 So be careful when using delete files like that。Okay。And now。

 let's say I want to delete all the files of a specific type so I can go in here。 I can do。

Find intro toabash。 Let's say I'm gonna delete all these text files here。

 I can do file Intro toab directory 1， give the full relative path there。😊，嗯。Give it the name。

And then， say delete。Okay， this has been weird。 I'll come back to this。At some other point。

 but essentially you can delete all files with an initial prefix。



![](img/980cd4b18c5b1a14d5de6db97818aefd_35.png)

If you do that。Okay，And another really powerful tool called GrP。

 which is global regular expression print， and you use GrP to find text inside files。

So the way you do this is you type in Gr， give it the search a term that you wantlook for and then the file。

 and then Gr will return the lines where this was found。



![](img/980cd4b18c5b1a14d5de6db97818aefd_37.png)

So let's first make a file。 So Im want to teach you this command later。

 but let's make a file called search Me。Let's go。Okay， and willll add a couple of words in here。

 So let's say。C， S 1，96。Rohan。Johan and Sammy is one word。And then， Rohan。And Sammy。A separate words。

 and finally， my name Lowcase。Okay。Now， if I do Gr， and let's say I want to search for my name。

 So first， let me， let's view the contents of this file。Search me。

So this is what's in the file right now。 If I do Gr。Rohan， and then do search Me TXT。

We can see it prints all the lines where。Any part of a word or the word Rohan appeared。

 So even though this part here， Rohan and Sammy's one full word。

 it still transitic because part of that was the search term。Any questions about that。

 how that works？

![](img/980cd4b18c5b1a14d5de6db97818aefd_39.png)

Okay。But now let's say we don't want to have just part of the word。 We want the exact word。

 We can use the W flag， and the W flag will return only exact the lines where only an exact match was found and not just the partial match。



![](img/980cd4b18c5b1a14d5de6db97818aefd_41.png)

So the way you do this， we do grab。Give it the W flag。Give it the search term again。

 and then the file。Now， in you enter， you see that。

Rohan and Sammy was not included because that was not an exact match。

 it's a partial match because only a section that word was a search them， not the whole word。

But what you probably notice is that the lowercase word is still not being included。

 And sometimes we want to include the lowercase search terms。

 And the way we include the lowercase terms is by using the i flag。

 So the i flag will make the search case insensitive。 That means it will find。



![](img/980cd4b18c5b1a14d5de6db97818aefd_43.png)

But it's fully capitalized， partially capitalized， if it's like。Like the spongeebob me。

 where it's one capital， one small like that。 They'll find all of these words if they're saying similar to the search term。

And you can also stack flags on top of each other。 So what I mean by that is。



![](img/980cd4b18c5b1a14d5de6db97818aefd_45.png)

If I do Gr。WI。Grep knows now I want an exact match that's case insensitive。And then I do brohan。

We see that。All the exact matches that are case insensitive have been found。Does that make sense。

 are there any questions about GrP？Okay。GP is a really powerful tool to search through huge files and find what you're looking for。



![](img/980cd4b18c5b1a14d5de6db97818aefd_47.png)

Okay， now we're onto diff or a difference。So what diF does is we'll compare two files line by line and then identify the lines whether they have any differences。

So the way you do this is by typing diff， file 1， file 2， and then hit enter。

 And then wherever there's a line where there's a difference， you'll see。



![](img/980cd4b18c5b1a14d5de6db97818aefd_49.png)

That being printed out into the terminal。So first， let's do this where we have two identical files。

 so we can use search Me T X T。Let's copy， search me into another file called copypy。If we list that。

 we see that we have search me and copy here。And also cat these files。 So we can see them。

We see that they are identical。Now， if I do di， search me out chist and then copy。There's no output。

 Nothing is printed because there's no differences between them。 They're exactly the same。

But now let's edit of the copy text。So。Let's first add an extra line。And move the in over here。嗯。

Differences。 and let's change this。To just say， and like that。Now I di these files。

We see that the lines where there differences were printed out。So here， the third line。

There's a difference here。Similar the fifth line is a difference， because。嗯。

Bhan and Ron is different。 And finally the last line is also different because。

We added an extra enter， therefore there is a blank line with no characters on it。

 but that's still part of the file。😡，That's the difference here。



![](img/980cd4b18c5b1a14d5de6db97818aefd_51.png)

That makes sense。对。Alright， now we're going to talk about logical operators。

 So logical operators are a way to string several commands together in bash。And。

 you do this by using like the ampersand Ampersand or and and key。

And it's quite simple to use you basically this type of command。

 do and end your next command and and next command。 And you can string。

As many commands you want together to create a huge monstrous command。

And you might think what's the use of this， Like why would I want to do this when I can just hit enter each time。

 Well， sometimes you have to repeat commands over and over again。 And as we know。

 if we're going to repeat a command because hit up on the key。



![](img/980cd4b18c5b1a14d5de6db97818aefd_53.png)

But let's say I want to repeat seven commands in a row。

 Then I have to keep hitting up like seven times to go all the way to where I want to be。

So let's demonstrate this。 So let's first do， let's make a directory。Let's call it。嗯。And， and。

And then we put the two m to go to the next command。 We want a C D into and end。

Then we want to create a file here。Let's call it。S file。And then， we want to。Leave。

The direction that we made and moved back up to enter of bash。So now when I hit enter。

We can see here。On this side， there's a new directory made。 and there's a file called some file。

And also， if I print the working directory， I'm back in in the bash。 I didn't stay in that file。

And now if I want to repeat that command， I can just hit up and there it is。

 I keep doing that over and over and over again。 Obviously I can because they have the same name and same the files exist。

 But if it was a different command， like running a Python script， for instance。

 I can do that over and over again。

![](img/980cd4b18c5b1a14d5de6db97818aefd_55.png)

And I want to talk about SSH or secure shell or secure a socket shell。

So secure shell SH is the way to access another remote terminal and control a computer from it。

This is really useful when you're working on a virtual machine or you to connect to a server because you can't always be there in person。

 So having SSH is a secure secure way to access， start to control that operating system。

And the way you do this you do S H， you give the username at the the host URL。

 And when you hit entry， we prompted for a password， and then you'll enter that VM in your terminal。

 So I'll demonstrate that here。

![](img/980cd4b18c5b1a14d5de6db97818aefd_57.png)

So right now， we can see if I put the working directory。 I'm in。 this is my local machine。

This is director right now。 And when S S H into A VM。You can see like， this is my you are my。

Username， followed by the hostt URL。When I hit enter， I mean prompted for a password。Okay。

 and now it looks like nothing has changed。 It looks like， okay， cool。 Some string was printed。

 but nothing's changed。 Well， actually， I'm in a totally different machine right now。

 I'm totaling a virtual machine on the U IU network。 So I list the files here。😊。

We can see that these files are totally different to what we had before。

 If I print the working directory， it's also different to what we had before。

And now I can control a separate terminal the difference when I have my local machine。

It's exit to leave。And now I'm back in my local machine。



![](img/980cd4b18c5b1a14d5de6db97818aefd_59.png)

All right， any questions about any of the commands we've covered so far。Okay， oh， yes。Oh， sure。

 So when you SSH， you can control any other terminal that's online in the world as long as you have the correct URL。

 So the one that I log into right now was one that's on the UIU network。So it's， it's just a。Of V M。

 a virtual machine that's running somewhere in the OIU network。

 And I was able to access that from my local machine。Any other questions？All right。

 let's go to the Kahoot。

![](img/980cd4b18c5b1a14d5de6db97818aefd_61.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_62.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_63.png)

🎼嗯。🎼，🎼。🎼，Okay， so a big mix here。 So let me explain that。 So firstly。

 a lot of you press WI WI is for we want exact match as a W flag and case in sensitivity。

I for insensitivity， we want case sensitivity here。嗯。I'm not sure why I was picked。

 I just means insensitive， case in sensitiveitive。And finally。

 the correct answer is orangeient or the circle， yellow。

 and W because W will give you an exact match and itll be case sensitive。

 It will take account of case。Are there any questions about this question？O。Okay。

 we're now going move away from commands and talk about text editors and bash。 So let's say。

 for instance， we S H into another machine。 How do we edit the files there。 We can't just open up。

Sublime text and start adding the code there。We can if we made a couple changes， but generally no。

 we can't。 So that's why we have text editors in bash。

 They let you edit files just like a regular ID， but they are different because you can't click on stuff and you can't work with how you work with a regular I the special commands。

 And although it might be difficult to learn initially。

 they can be very powerful and increase your productivity。

 So we're going to learn three of them today。 Vi and Es the most popular。

 but Na is the one that' is super easy if you have to edit a few lines of code。

 it's real easy to pick up nano and work with it straight away。

 but Vi and Es is super powerful if you want to put the time into them。ToStart with themm。

 So VIm is a really popular terminal editor of released in 1991。 And to start with them。

 you just type in themm file name。 VmMS should be installed in most Linux machines。😡。

So if the file exists， then we'll open the file and you can edit it， but if the file doesn't exist。

 if you save after you close them， that file will be created。😡。



![](img/980cd4b18c5b1a14d5de6db97818aefd_65.png)

So， for instance。Let's go to search me at TXT。 If I cat the file， you see there's content in there。

Now， let's do vim。 If I do vim， search me now T X T。I can see it like this。

And we see the contents there。

![](img/980cd4b18c5b1a14d5de6db97818aefd_67.png)

So VIm opens in command mode。 So V has several modes for doing different things。

 So I'm just going to talk about command and insert mode because those are the two most important ones。



![](img/980cd4b18c5b1a14d5de6db97818aefd_69.png)

And the the way you can identify command mode is that there's nothing in the bottom here。 There's no。

 nothing saying a specific mode。 So you know， you're in command mode。



![](img/980cd4b18c5b1a14d5de6db97818aefd_71.png)

And there's a bunch of different commands here you can take a look at。

 and I'll go through some of them。Right now， so firstly。

 you don't have to use your arrow keys to move around the text。



![](img/980cd4b18c5b1a14d5de6db97818aefd_73.png)

All the keys that are either are on the hop bar。 So H， J， K O。It' move。To the left。

 Alice moved to the right， J down and K up。So this is good。

 If yout want to keep moving your hand around a lot， it's right there when you need it。



![](img/980cd4b18c5b1a14d5de6db97818aefd_75.png)

If you press the dollar sign， you move your cursor to the end of the line。😡，And underscore。

 move your cursor to the beginning of the line。 W and B from moving forward by one word。



![](img/980cd4b18c5b1a14d5de6db97818aefd_77.png)

If you do slash somewhere， this is really powerful。 If you do slash。And then let's say， C， 96。

We'll move the first occurrence to that word， or the curse will move the first occurrence of that word。

Both if I want slash。Sammy。

![](img/980cd4b18c5b1a14d5de6db97818aefd_79.png)

It's a really great way of moving around your file quickly without having to click on things。

And to move between line numbers， you can just type in the line number and G G and use to undo。



![](img/980cd4b18c5b1a14d5de6db97818aefd_81.png)

But now you're probably wondering， how do I do anything if I type with my keys。嗯。

 let me leave insert mode。 If you type with your keys， you can't actually do anything just yet。

You're just scrolling through。 So how do I enter stuff to enter。

 you press I to you go to insert mode。And you can see this this insert at the bottom there。 And now。

 when I type。

![](img/980cd4b18c5b1a14d5de6db97818aefd_83.png)

Text appears on the editor。And here you can use， if you want to move around。

 you can use your arrow case to move around。

![](img/980cd4b18c5b1a14d5de6db97818aefd_85.png)

And finally， you go back to command mode， you press escape and you're now in command mode again。

Any questions so far that I know there's a lot of content。

The slides will be out if you want to look at the commands afterwards。

 But any questions about what we've covered so far。



![](img/980cd4b18c5b1a14d5de6db97818aefd_87.png)

Okay。And finally， how do we leave them。 This is a pretty common problem， actually。

 for a lot of people using them， there's no X at the top and you can do control C like how you normally need to end a process。

 You would are just stuck in here。 So what you leave them is you go back into command mode。

 and there's several different options。 But these are the most useful， I think。 So firstly。

 you can do colon and quit Col and quit， well just let you quit。 If you've edit the file。

 there'll be a warning。But otherwise it'll let you quit or so you don't add the file be a warning。

If you do Q exclamation mark， there'll be no warning and you'll just quit without saving。

 And finally， if you do Col in WQ， you can write and quit。



![](img/980cd4b18c5b1a14d5de6db97818aefd_89.png)

So let's say I just do colon exclamation mark。 The file closes， if I can it。

The content hasn't changed。 but if I did WQ， the content would have changed。Any questions about them？



![](img/980cd4b18c5b1a14d5de6db97818aefd_91.png)

Okay， great。Now let's talk about Emax。 Eax is another popular terminal editor of released in 1985。

 It's similar to Vim in many ways， except there's not not any mode。 The way you use Vim。 Eax， sorry。

 is you use。Different prefixes。 So plus control and the meta key。

 which on your machine is either an alternate options key。



![](img/980cd4b18c5b1a14d5de6db97818aefd_93.png)

So let's go into EmX。If you're on a Mac， you might have difficulty with Ems because。

The option key isn't set to the me key unless you've set it to that。 So let's go to the desktop。

And let's go ahead into of bash。Let's make a new file so we can do emax。New file。That text。

And now what's great with Emax is that you don't have to go in different mode of type。

 Youre going just start typing stuff。But now if you want to do different things。

 like jump around or leave， you have to use the prefixes。 So let's talk about that。



![](img/980cd4b18c5b1a14d5de6db97818aefd_95.png)

So if you hold control， you can do different things。 So if you press A。

 you'll move to the beginning or the end of the line respectively， you press V。

 you'll move down a page。 So page is just what you're seeing right now。 So the text here。



![](img/980cd4b18c5b1a14d5de6db97818aefd_97.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_98.png)

Is one page。 Let's say you've written a huge program。 If you're going to jump down quickly。

 you can do a control V to jump down。

![](img/980cd4b18c5b1a14d5de6db97818aefd_100.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_101.png)

And if you do underscore， you'll undo any changes that you make。



![](img/980cd4b18c5b1a14d5de6db97818aefd_103.png)

So let's say we accident delete this。 If I do control and then underscore， it'll bring that back。



![](img/980cd4b18c5b1a14d5de6db97818aefd_105.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_106.png)

And now we're going to talk about the Me key， which is so if you're on a Windows。

 it would probably be alt and if you're on a Mac， it's options， but as I said before。

 you'll have to set that in your terminal because it's not automatically set depending on your OS。😡。

And basically， you do cool stuff like moving between words。 So I want to move to my words。

 I can use the F and B。

![](img/980cd4b18c5b1a14d5de6db97818aefd_108.png)

He's ob beast move backwards。 F is to move forwards。



![](img/980cd4b18c5b1a14d5de6db97818aefd_110.png)

If I want to move through sentences， I can use ARE。And again， di delete changes。 Actually。

 I don't think that's， that's not the case for， yes or will， sorry。Okay。Thatll leave an Emax。

It's different from them again。 but you just hold。

![](img/980cd4b18c5b1a14d5de6db97818aefd_112.png)

Control。And then press X。And see at the bottom of his control X。

And now if you wanted to save the file， you'll do control S， but if you just want to leave。

 you'll do control C。And now we can see there's no file here because I didn't save it。

There's a temporary one here。Any questions about EAC so far or anything。



![](img/980cd4b18c5b1a14d5de6db97818aefd_114.png)

From the text editor section。No， okay。

![](img/980cd4b18c5b1a14d5de6db97818aefd_116.png)

And finally going do nano so。The other two tech editor we learned have been around for a very long time。

 They're very， very powerful。 You can actually， although they look pretty bare bones at the moment。

 you can， it's been out for so long that people have made modifications that you can download and use or scripts that you can download and use to make them very useful。

 So you can actually make Vi and Emax。😊。

![](img/980cd4b18c5b1a14d5de6db97818aefd_118.png)

Very intuitive。 They can have like line numbers。 Like， for instance， I go to them here。



![](img/980cd4b18c5b1a14d5de6db97818aefd_120.png)

And I open up a file。You see there's not there's no line number。 There's no pretty printing。

 Pre printing is one keywords or highlight different colors。 It looks pretty dull to look at。

 but you can download and set up scripts to do things like that。

 So if you want to do that in your own time， we're just showing you these tools in case you're interested。



![](img/980cd4b18c5b1a14d5de6db97818aefd_122.png)

But nano is a great tool。 if you just want to have very easy access to doing stuff。 So nano is 2000。

 and I believe has the smallest learning curve out of all editors we looked at today。

 So if you want to open up a file in nano， it's similar to the other two。

 you do Nano and the file name， file exists。 you'll just open up the file if it doesn't。

 you'll create that file。😊。

![](img/980cd4b18c5b1a14d5de6db97818aefd_124.png)

But with nano， it's very nice because you're gonna open up a file。

And you're gonna start typing stuff。 All the commands that you really need are。At the bottom here。

And it's good for just if you to make a few small changes to a file on your server。

 you're gonna just do the changes here。And if I want to leave control X， I get prompted， plus's Y。

 and I can leave。That was definitely the easiest out of all the text editor that we've learned about。



![](img/980cd4b18c5b1a14d5de6db97818aefd_126.png)

Any questions。About that。Okay， cool。

![](img/980cd4b18c5b1a14d5de6db97818aefd_128.png)

All right， forget to ask people， let's do one more question。



![](img/980cd4b18c5b1a14d5de6db97818aefd_130.png)

🎼嗯。🎼，🎼The。🎼The。🎼ふふふ。🎼た。Alright， so I'm sorry。 This one is actually really， really hard。

 So if you got a write， great job unless you guessed it， then you' are lucky。

 So find will only delete things that。😊，Appear。 So if you don't specify。A name it won't delete stuff。

 It'll just like throw an error message。All right。So now let's go to batchsh scripting。

 So you can actually， instead of writing commands manually， you also write scripts to run commands。

 and these can even take input。 So Bsh scripts have the dot S extension and you can run these scripts by typing bash and then finally the extension。

😊，So。😊，Let's do variables first。 So you can declare variables by just choosing a variable name and then assigning a value to it。

 You don't have to declare the type or anything like that。 You can just do。Variable or x equals this。

And you want to use the variable later， you put a dollar sign in front of it。But quick note is。

 don't， when you're signing。Your variable don't put spaces around the equals operator。

 So here's an example of that。

![](img/980cd4b18c5b1a14d5de6db97818aefd_132.png)

嗯。Around the Es operator， make sure there's no spaces。 Otherwise your code will crash。

 They'll be in our message zone。Does anyone want to guess what this will do。As a quick preface echo。

 we'll just print back whatever is there。Poer guess what this function does。

What snippet of code does。

![](img/980cd4b18c5b1a14d5de6db97818aefd_134.png)

Okay， cool。 If I to ask， that's fine， I can do a demo。😊，Okay， so let's。

 let's first take a look at the file。So this is the file that we have right now。 Let's run it。

 So to run， we just do bash。And then， var。Dot S H。So， just printed。The variable。

 and then printed the same message twice。 So let me explain that。

 What this cost of it did was we firstly took a variable called secret variable。

 and we signed the value password 1，2，3，4 to it。

![](img/980cd4b18c5b1a14d5de6db97818aefd_136.png)

Then we'd echo a secret variable because the dollar sign we're addressing the variable and not just a string all secret bar。

 We printed the value password 1，2，3，4。And then the next two lines， the exact thing happened。

 We printed the message， the secret message says， and the variable content。Any questions about this？

Yeah二。Right， so let's just specify that。 So the question is why does second line have brackets。

 Essential， is because if you wanted to have multiple variables， you could do that。

 but you can just have a single variable in between the brackets for now。



![](img/980cd4b18c5b1a14d5de6db97818aefd_138.png)

Y。And now conditional。 So conditional is just if else， if else。If L， L，F， LF， so。

Conditionals are in this form。 So you'll have if。You have these square brackets， two square brackets。

 the condition， and then then do something L if it just short for else if。Another condition。

 you do something， Otherwise， if all the conditions are false。

 you go to else and that'll do something。And finally， to end your conditional。

 you put Fi to like if backwards。So then note is。And a common bug that I had a lot of trouble with is you need to have a space between the condition of the brackets。

So。If you look here， there's a space because you don't have that space， the code will not run。

And for like comparators。 So normally when you write a scripture， write， if x equals equals this。

In batch script， you write EQ or dash EQ as your equals equals operator and dash N as you're not equals operator。

Any questions about conditionals？

![](img/980cd4b18c5b1a14d5de6db97818aefd_140.png)

Nope， okay。So let's look at this code here。Take a second to look at that。

Does anyone want to be brave and tell me what they think the snippet of code does。いやス。Almost correct。

Because。Actually， you're right。 That's， that's exactly who it's gonna to do。Exactly， sorry， Yeah。

 the demo is a little different， but yes， exactly。 it's gonna look。

 So first I' going look at nu 20 and say， does numb not equal 20。It does equal 20。

 So we go to the next Elsif。Does string equal a word。String does not equal word。And finally。

 we go to the else condition。 That's the only thing we have left， Well I'm confused。And know。

Echo the where to the start。

![](img/980cd4b18c5b1a14d5de6db97818aefd_142.png)

And so the demo that we have here is。If I do cat variable dot T X T， a variable。Conditional。First。

 run this。O。Alright， sos a bug in this， but you're right。 It should just print。



![](img/980cd4b18c5b1a14d5de6db97818aefd_144.png)

It， should just print。 Well I'm confused then。Echo what's up here。 There's a bug in that script。

 I'll fix that for later。I finally we' going to do loops。 sorry。 We're going to do loops next。

 So loops are in the form of4 I N。 and we have the brackets here。You put a starting number of range。

 So you go from the first variable all the way to the end。You had to do something。

And then you'll do something in the loop， and you'll end the code there。So。

Let's say we have this four loop here。 So4 I in1 to 10 do echo we are on loop。I。

Does anyone to a guess of what this does？Yeah， again。



![](img/980cd4b18c5b1a14d5de6db97818aefd_146.png)

Yep， that's correct。 So now let's run that。 So let's do bash。That slash loops。And it's gonna print。

Exactly that run these different loops。That makes sense。

It's similar to another coding language you might have used like Java or Python。

 There are a few syn difference。 but for the most part， it's pretty similar。



![](img/980cd4b18c5b1a14d5de6db97818aefd_148.png)

I finally going to talk about functions。 So function declaration is in the forum。Function name。

 you put two brackets。 Yes， sorry， question。呃。For now。

 we're going to do four loops because the course the other wireless with bash。

 for now we're going to stick to four loops， because it easy to stick with that because variables can be confusing with bash。

But also， we're not gonna， We sort gonna in to batch。 We're not gonna test you extensively on this。

 So don't worry about learning this content super well because。

Unless you really want to use batchsh scripts， we're not really gonna。

Have you do it a whole lot for rest the semester。Right， so function。

 so function declarations in this form where we'll have a function name， brackets。

 and we'll have stuff the function does in between。Important to note here is if you pass a function。

 a variable sign into the function， the function will save this into variable 1。 So dollar sign1。

And when you make a function call， you give the function name and then the value to pass to it。

So we have this here。 It's called a Greek person。So it's going to echo high there and then variable1。

So this code here will just take group person， it'll pass to the value Rohan and say hi there after saving Rohan to variable 1。

 print hi there Rohan。

![](img/980cd4b18c5b1a14d5de6db97818aefd_150.png)

Let me see add action here。Exact same thing here。 And if I do bash。嗯。当时。It says hi there brohan。

 you can change the variable here。Quし。So the question， if you change one overall。

 how we do the same thing。 Yes， it definitely will。 Itll just ignore the variable。

 I you use the variable So we can do that right now， actually。嗯。Is what you meant like this？Oh， do。

 okay， we can do that。So now if we run this。It just blanks out because we didn't initialize。

 so if I look at that file here。The reason nothing comes out is because we didn't initialize a variable called Rohan。

But let's， so， but let's say want to print the actual dollar sign。 Like。

 can we ever print a dollar sign in a ba。 Yeah， we can。 if We want to print。嗯。Like high there。

 dollar sign Rohan， we could do high there and put single brackets around this。

Around the dollar sign。Like this。And now when I run it。It'll print。

 It'll include the dollar sign in the print statement。Yeah， question。More variable。Yes。

 it'll go one to up until like how many variables you have。



![](img/980cd4b18c5b1a14d5de6db97818aefd_152.png)

Okay。And last thing I want to talk about is aliasing， there's not a slide in that here。



![](img/980cd4b18c5b1a14d5de6db97818aefd_154.png)

But let's say you have a command you frequently。 So a frequent thing that people do a lot is Python over Python 3。

 So as some of you might know， Python， if you just type Python normally in your terminal is't 2。7。

 and Python 2。7 is totally redacted。 You cant do that anymore。

 So it's annoying to always have type Python 3 when you want to run a script。😊。

Something you can do is called aliasing。 You just write alias。And you write a command。

 So I'll write Python here。And then do Python 3。When you enter。Doesn't look get anything happen。

 but now every time you type Python， Python 3 will be typed instead。And this matter for any command。

 you're giving a string commands， you can aliaase that to a single word or a shorter word。

And that's just useful if you have to type something like if you're pushing to get a lot。

 you might be doing a huge command， you can just alias it to a shorter thing。

So that's everything we had， are there any questions about any content we had so far？



![](img/980cd4b18c5b1a14d5de6db97818aefd_156.png)

Yep， okay， one more question。

![](img/980cd4b18c5b1a14d5de6db97818aefd_158.png)

Okay。🎼。🎼，🎼Yeah。🎼，🎼，🎼清楚。🎼，🎼Yeah。

![](img/980cd4b18c5b1a14d5de6db97818aefd_160.png)

that's totally correct。 So Eddie showed in the demo if you have two files。

Let's just make two files that are empty。If I di them。Nothing is printed。Great， so that's everything。

We just covered it there。So I just want to throw a few more things in。

 so just throw another reminder about what I said at the start of lecture。

 don't forget to join Piazza because that is how we are going to be able to communicate with you tomorrow when the homework is released。



![](img/980cd4b18c5b1a14d5de6db97818aefd_162.png)

![](img/980cd4b18c5b1a14d5de6db97818aefd_163.png)

We went through a lot of things today。 it went very fast。

 we don't expect you to be able to like immediately retain everything that we did today。

 a lot of what you're gonna learn when you're doing bash and terminal stuff is going to be learned through application so what we gave you today is just basically an overview of various text editors and various commands you'll learn them better once you actually apply them throughout you know your assignments or whatever it is that you use your terminal for right so just get familiar with it for now and as you apply them more and more you'll be more comfortable with it don't be worried if we went through it really fast today with text editors figure out which one you like most and get most comfortable with it but aside from that that was all we're going to do for bash next week we're gonna to start get and that's it for today so you guys are free to go if any questions you can come down here and ask us。

Oh yes。Sorry。Yes， well， the all the presentation we uploaded to the website will also include the files that we use like the intro to bash files so you guys can test the stuff we're working on。

 They'll be up in like 10 minutes。Yeah question。No， this is actually a builtin function。

 It's called Cali。 You can， if you guys want to find out how to use this， you can Google Calse bash。

 and you can find the whole instructional for this。 There's a lot of cool fun stuff you can do。

 Like the other thing I did earlier was C matrixtrix。 That's another command you have to download。😊。



![](img/980cd4b18c5b1a14d5de6db97818aefd_165.png)

And they'll just have a cool like matrix theme coming down your screen。第。

Come down if you have any questions。