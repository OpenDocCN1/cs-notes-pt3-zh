# 【全集 春季版】伊利诺伊大学 计算机编程：从Bash到Rust 中英字幕 p01 Lecture 1 - Bash part1 -BV188rDBFEUY_p1-.f30280

Everyone can hear me now right， thumbs up。Perfect， all right， so at 7 PM。

 we'll go ahead and start lecture。 If you weren't here for lecture 0， you probably haven't seen me。

 My name is Sammy。 You can call me Sammy。You're curious， 196 is a class by students， four students。

So。I'm not a professor， neither is Rohan。Just call buy names。So， yeah so。

The reason why I wasn't here last Thursday is because I was out for an onsite。

 but I will be here for every lecture along with Rohan。

 and we can go ahead and go through some course obligations， so next slide。So yeah。

 so the way that it's gonna be split up is Piazza is going to be for all questions。

 just very general questions about assignments or anything you're curious about for the class。

 don't directly email us for these kind of questions because if you have a question。

 oftentimes someone else will have the same exact question as you so don't spam our emails posted on the Piazza。

 Discord， we're gonna to give out Discord links if we haven't already once projects are assembled。

 projects are going to be assembled sometime next week， start of next week or late next week。

And yeah， again， so for email， these are going to be for emergencies。

 like if you cannot complete course obligations for whatever reason。

 then go ahead and shoot us an email。 me and Rojahan's emails are on the sllvis。And homework。

 we're going assign these on Perle。 so the Perie learn is currently being set up。

 we'll have a homework released on Friday for Bsh。 So today we're going to go through Bsh Rohan won't introduce himself。

 but that's it for me for today。 My name is Sammy。 If if you have any questions。

 just go ahead and reach out to me。All right， can it hear me， okay。Everyone hear me。 Okay， cool。

 So today going go through bash。 So for bash， I want to sit on my computer for most of it because I want to do live demo because I think the best way to learn bash is to see it happening in front of you and they're practicing it afterwards。

 So for right now， I appreciate if you didn't practice it and just like watch me so that you can learn the commands and the content they're teaching。

 And then afterwards， I want to post the files that we use。

 And you guys try exactly we didn't lecture but back at home or wherever。 All， cool。😊。

So what is bash。 So bash is a text only interface which is used for controlling Uni system。

 So what does that mean， It means you have， instead of having your goi interface。

 your graphical user interface to click and open files and folders and look at all your stuff。

 you do everything from。The window on the left， that's called bash。

 It's a command C I command line interface。 And you only interface with it through text。

It's an acronym for Born Again Shell， which is a pun on Stephen Bourne。

 who is the author of the a direct ancestor of the Euch Shell。 It's called S H。

And it's using many Linux machines， almost all Linux machines。

 And it was used on all Mac systems up until Catalina。 And we swapped as Z S H。

 which I'll talk about in a second。So why do we want to learn ba？

 What's the point if we can just click on stuff， and it's so much easier。

 Why do we learn all this hard stuff。 Well， bash is the standardized way of manipulating the operating system。

 And because it's standardized， it's very easy to automate processes and manipulate how you work with。

Your operating system， because let's say， for instance。

 you want to repeatedly open this folder and open up this file。To do this autonomously。

 you have to train like computer vision to go in there and click on stuff。

 find what you're looking for。 It's very difficult， whereas using。The batchsh。

 you can just use text inputs to control everything。So。

Standardization for easy automation and manipulation of many different tasks。

 And for some serverside tasks， if you're working on a server or if you're working on a virtual machine。

 a lot of that will have to be done through a terminal。 They might You get a Gui interface。

So if you're on Linux， your setup is super easy。 You have to do nothing at all。

 You're probably already using bash。 If you're not。

 you can come to office hours and we will help you set something up。

If you're on a Mac and you're pre Catalina， you're fine。

 you're on bash and there's no need to set up anything。 If you're post Catalina。

 you also kind of have to do nothing。 You are on bash。 You're on something called Z， S H， which is。

Another shell interface similar to bash。 But there are some slight differences。

 And for the purposes for this class， bash and the S H can be。Tre it interchangeably。

 almost the differences are negligible。And for Windows， if you're on Windows 10。

 you can follow a tutorial to set up something called vagrant， which is a virtual machine。

 And you can run a Linux shell there。 And if you're using earlier version of Windows。

 come to office hours and will'll help you set up a Linux shell。So for the purposes of this demo。

 we're gonna use this kind of file structure。 So if we look at the window on the right here。

 we come from the user to the desktop to intro to bash。Which is a folder。

 And we can see all the different folders here。 Are there any questions about this structure or about bash so far。

Okay， great。So let's start with our first command， L S。

So a lot of the commands are really easy to remember because they're basically just formed versions of words。

 So L S is short of list。 and L S will list all the files in the current directory。

 So the way you you use L S is you just go into a folder。 So right now。

 I'm in the intro to bash folder， and you type L S。And you'll see your other directories。

 which are in different color。 and then your files。Pretty basic stuff。

 Any questions about that at the moment。O케이， cool。Next， we have PWD or print working directory。

 So as the title suggests， this function will just print the， the path to your current directory。

 So the way we do this is we go into terminal and we type。 Can everyone see the terminal screen fine。

Yeah， okay， you type PW D。And hit enter。 And you'll see the path from your home directory all the way to the current directory that you're in。

 So if we look at the diagram here， we see that we started users。Which is here。

Go onto Rohansh desktop。 And then we're in the in intro to bash folder。

Which we can see in this path here。Our next command is C D change directory。

 So C D allows you to change the current directory that you're in。So C。

 D is not like the other plans we learned in that you can just type C， D and expect to get anywhere。

 You have to type C， D and follow that with an argument。

 which will be in the directory that you want to move to。So let's go into a new directory。

 So we're currently in the intro to batch directory。 Let's try to go to directory 1。

So to move from the current directory to something that is relative to where you are， it's very easy。

 You just type， let's list the files right now。We can see the directory  one is here inside intro to bash。

 the photo that we're using。 So we go C， D， directory 1。

And that doesn't look like anything's changed。 But when we type PWD to see the directory that we're working in。

 we can see that we're now， instead of being intro a bash， we're in directory 1。

So we moved from the insert of batchsh folder into directory 1。As I list the files here。

We see that we're not looking at these files anymore over here。We're looking at。

These files on the side。The next sense。こ。So there's some things that extra they can do with C D。 So。

 oh， sorry， yes。Is a space in it， Okay， so if you have a space， the way you want to do it is。嗯。

You so type in the first， the first word and then press a tab， and thatll autocomplete for you。

 And you'll see there's like a backward slash to fill up the space。DoesThat work。Okay。

 that I can do from here。 So let's make a file here。 So you went on this command a second。

I'll do my desktop。 That's easier。I want to make a new folder。

 It's gonna be called some space folder。Alright， so now。I go here。呃。

We can see that there's some folder here， right， That makes sense。 So now if I want to go here。

 I can press C D sum and hit tab。 And for this space， you'll have a backslash followed by space。

And now I can go into this folder。 And if I put in the working directory。

 we can see that the space is here， but we can't put space into into our arguments。

 You have put a backward slash and then a space。 Make sense。Okay， great。Okay， cool。

So with the C command， there's other things you can do， because normally when you， let's say。

 you're trying to go from directory  one all the way back to users。How do you go， Firstly。

 How do you go backwards。 So if you want to go backwards up through your directories， you do dot dot。

 So you press。 So let's go into directory 1。If we print the working directory。

We see that we're in directory  one right now and not enter the bash。

 If we want to move up to in the bash， we do C D space dot dot。If I hit enter。

 our new directory is Incho debaash。And if we wanted to go back all the up to users。

 there's two things we can do。 We firstly do C D dot dot slash dot dot slash dot dot slash。

Repeatedly， until we're there。Which is really tiring。 Or if I go back to where we were。We can use C。

 D and then start the argument with a forward slash。So if we do this， we have。

 now it's called an absolute path。 That means we're not going from relative to where we are anymore。

 We're going directly from our home directory， which will be users。 So I do C D slash and hit enter。

嗯。If I print the working directory， there is none because we're back in home。

 So now if I want to go back to where we were， I have to go back to users。

Back to my desktop and back to into the bash。Does that make sense with the absolute melt path。

So relative is without the forward slash， and that'll be from moving from where you are to a new new file。

 new directory。 sorry， And the absolute path is you start with the forward slash。

 and it'll take you all the way back to the home directory and you put the whole path back to where you want to be。

Cool。The next command we're gonna learn is concatenate， or simply cat。

And cat is used to display the contents of a file。 And this also takes an argument。

 So you type in cat space， the file that you want to look at， and you'll be able to read that file。

I read， the terminal will print the content of the file for you。So， let's go into。

So right now we're intotro to batch。 You see there's two files here。 So if I list that。

There is file 1 dot T X T and a Python filet P Y。And you can see that here on the right hand side。

 too。If I do cat file 1 dot T X T。We can see that this is the only thing in the file。

 just some random data or a string that says this is a file with some random data。

And then if I want to read the Python file。I can do cat Python file。

And there's a function in there that prints a bunch of triangles。Alright。

 so now we want to use touch。 Touch is a command that you use for creating a file in the current directory。

 So the type of file that you created depends on extension。

 So you can make any type of file that you want。 It could be a dot T X T。 It could be a Python file。

 It could be a random extension， which will not open because your computer went to handle it。

 but you can make any type of file here。 Again， this takes an argument。 So you say。Touch also。

 clear is a great way of clearing up your。Terminal， if it gets super messy and a lot of text。

 press clear and youll have a fresh。 Well， it doesn't delete it。 It just scrolls you down。

 but it makes it look you have a fresh terminal open up。So let's say we want to create a new file。

 Let's say we want to call touch new file。That Tx。I see on the side here， a file was created。

And if I list the files。There is certainly a new file here。So over here， we take a look。We had。啊。

No file here。 And then we have， well， it was an intro to bash， but we'll have a new file there。Great。

 now we're gonna。I'll take a quick break and do a cahoot。

So if you guys can sign in here with your net I Ds。

 we can give you attendance and extra credit points if you got the questions correct。

Before I start the quiz or another the quiz， the question there any pressing questions right now。

About anything we've learned so far。Or is anyone refresher on any of the commands we've learned。Okay。

 okay。We'll give it another minute。Is everyone in the Kahoot？ Are we waiting on anybody。O。

And fire music。I just wanted to mention。As long as this okay， just wanted to mention。

 don't worry about the points of this。 Just focus on the accuracy and getting it in on time。

 There's no special prize for finishing top five other than like， you know， your personal pride。Also。

 if song called， if you're just putting your full name in。

 please put your net I D because we can't give you points if it's not your net I D。Like。Over here。Oh。

 sorry， yeah。我就。Rise your hand if you're not in the cooo yet。No problem。We'll give it。

 like another minute。嗯。I can come help if you need it。对。

You raiseise your hand if you're on the cahoot。You go have， cool。Alright， so the first question。

You'll， you'll get points this regardless， there's no correct answer here。哦。哎 cool。

So the answer that one was cat filed a T XD， so。But I can do that over here。Cat for concatenate。

 which just means they're gonna I'm not why do use concatenate for viewing the file。 but do cat。

P 1 T X T。 You can see everything inside there。Cool。

 we'll come back to the Kaooot later once we learn more commands。Right。So we learn touch。

 that's how you create files。 Now we want to learn RM or remove。Remove will delete the file。

 It doesn't move it to the trash。 It permanently deletes the file。 It's gone forever。

 You can't get it back。So the way you do it， it's similar to touch。 You just write RM。

Followed by the file that you wanted to delete。 So let's say for the new file that we created over here。

 we do RM， new file that T X T like this。And that file was gone。 It's not in my trash trash。

 I can't get it back。 It's permanently deleted。Just know RM can be used on directories that have。

 You can use RM to delete the directory， but you can't use RM to delete a directory that has a content in it。

 so。If I list the files in here， you can see the directory  one。Has stuff in it。

 So if I do R M directory 1。I can't leak the directory。 And also， cause that's content in it。

The makes sense。哦。So we have the new file here。 We use RM new file， and the file is gone。Right。So M。

 K D I R or make directory。 See this is kind of easy to remember because it's almost。

Sppelling it out。It's very similar to touch。 You just write M， K D IR space。

The name of your directory。So。Here， we're gonna go into directory 2。 So C D directory 1。

So if I list our working directory， we're now in directory 2， which is over here。

And let's make a directory inside this directory。 So let's call it， O， not that。New directory。

And we see if I list it。There's a new directory here。 And if you look on the side here in my folders。

 there's a new folder that has no content in it。Yeah， question。Right， yeah。 So if I。

 I can show you now， if I do like touch and I make a a random， like， let's call directory。

You see that you don't have a folder here。 You just have a file with no extension， and it won't be。

 You can't release a file like this， generally。Right。And then R M DIR。

 So no price for guess what this does。 This removes your directory。

 but you can delete a directory that has files in it。 So if we tried。Doing that， let's。Try deleting。

 So if we go， you know directly to have stuff in it， you can see that over here。

By try doing R andDIR on directory 2。We get error message。 It's not empty。

So it's kind of a safety measure because you don't accidentally delete something that has a lot of useful files in there。

But if I go into directory to， to our new directory， which is over here。And I do RMDIR。

 new directory。That directory is gone。 again， using remove directory from your command line will not move to trash。

 It just gets later permanently。So we were here。 We had a new directory in here， and it was gone。

Okay， so we'll take another break and we'll do another question。Is everyone onhoot。

Does anyone need a second。嗯。哦。Alright， so the answer to this one was。This here。

 So let's try that in the demo。 So we go into。So I did PWD。

 And this is where what our path is right now。 We're in directory  one at the moment。

But you C space start。Thatll move us upper directory。 So we'll move from directory  one。

To the intro to Bas directory， so。This is what we get now。Are there any questions about that。

 why that happened。Okay， because the red one is wrong。 I'll explain how we get to users。

 If We want to get there， We do C D and then follow that with a forward slash。

 We use the absolute path， yeah。Which ones are it？Oh here。

It just separates us from the file right now。 And then this is a git repo。

So it's it just shows you what you're typing， where your typing starts。That makes sense。O。Okay。

The next command we're going to learn is M V or move。 And move has two main purposes。

 It's either to rename a file or to move a file into a new location。 So you's gonna rename the file。

 you put two commands in。 So firstly， well put the file whose name you want to change and follow that by the name that you want to change it to。

If the file already exists， you will erase that file's content and replace it with original file content。

 But if the file doesn't exist， you will just rename the file and delete the original。

Wrry about that。It's going down disturb。Alright。So let's go into Drory1。And let's make a new file。I。

So if I cat the new file。We see there's nothing in there。 There's no content in there， at the moment。

But there's already file in here。 It's called file and D directory。 So I do cat file and D。

So this is the text file inside another directory。 So that's the content in there。

And now I'm going move the content from our current file into the new file。So if I do envy。

File and then follow it up with new file。So the first argument is the file whose content we want to move。

 And the second is the file that we want to move the content to。

We see that file and doesn't exist anymore。But new file is still here。And if I cat the new file。

We have the original content in there。But let's say we give it a file name of a file that doesn't exist。

 So if I say。And let's say， file doesn't exist。Dot Txt。It looks as though it just renamed the file。

 What it actually did was copy its content into a new file called file doesn existt T X T and deleted new file T X T。

供。Egle to use move to move a group of files or a single file from one location to another。So。

Let's go up into intro to bash。So this default we're in right now。We can see that there's one file。

 one text file in here。 It's called file 1 dot T X T。And let's say I want to move this this file。

From directory  one， sorry， from intro to bash to。Directory 2。So I'll do M V file 1 dot T X T。

And I'll give it。 I can give it either the relative path or the absolute path。 In this case。

 I'm gonna give it the relative path。And now you can see that the file has moved from intro to bash。

And is now in。Directory， to。Any questions about that？Okay。

And something cool you can do is' I gonna to make a couple of random files right now。😊。

If you do Mvy and you put a star。And then followed up with an extension。

 You'll move all files with this extension to wherever you want to move it to。

So let's try doing that。We can see that all the files that were text files have moved from intro to bash。

All the way up to directory 2。Any questions about that。꼭。N CP or copy。

Co will copy a file into a new location， and its usage is very similar to move。

 except when you use move， you lose the original file。 When copy， you will keep the original file。

 so。I'll show you guys that here。I to make a file。Let's call a copy。And I want to move this file。

 which is here right now into。Directory 1。I can use C P。Copyme T XT and move it into directory 1。

And we can see that we have the same file over here。But the original one also exists。

 We didn't move it。 We copied it。Similarly， if you wanted to copy the contents of this file into a new file。

 you can just do C P。So let's add some text in there。I'll teach you guys them soon。So now。

 if I read this file， we have some content in there。I'm going to use C， copypy me TXT。

And put into a copied file。And now when we read the content and copied file。

We see its the same as the original file， but we didn't lose the original file that's still there in the directory。

That makes sense。 It's very similar to move， except you don't lose the original。对。And finally。

 I want to teach you all the man command。 It's short for manual。

 And it's a very useful command that youll probably use throughout your programming career。 Again。

 it takes an argument。 So you'll type man and follow it up with any。😊。

Any command you want to learn more about。 So you type man。L， S， for instance。

You will get the the manual for L S。And you might think you're stuck because you don't have your terminal anymore。

 with the way to get out of this， It's in a Vm file。 you press escape。And then you do W， sorry。

 just Q。And good thing about man is that you don't need wfi to access the man pages They are already on in batchsh。

 So you can just， even if you're like on the road， you can just type in man。

It some random command that you haven't heard about。 And youll get the manual for that。Alright。

 so I want to go over some tips and tricks that I think are super useful for being efficient in bash。

 because typing a lot can be。A bad use of your time。

 So we're gonna try to speed that up as much as we can。So in typing and terminal。

 the first thing that I think is super useful is the tab key。Let's say you're typing。

That's say you make a really long file name， for instance， So let's say。Our file has a really。

Long file name。It's really long。Okay， and now I realize I hate this file。 I hate the file name。

I want to delete it。Now， I could do RM。Has a really， that's gonna take me ages。 That's super long。

 Another thing you can do is just type in the first defining characters。

 So the first characters will separate this file from the other files and just hit tab and you automatically get the rest of the file。

😊，And you can get rid of that file。But let's say you have a file。 Let's say you press tab in your。

 So let's go into directory 2。So you can see in directory 2， we have a bunch of files。That。

 that starts the same。 So if we do。RM F I L。 So now terminal doesn't know whether we mean file 1 or file 2。

 So if hit tab， it'll prompt you to choose which one you want。

And then itll you can choose which one you are from there。Another really useful tip is。

Use up down arrow keys to find previous commands you just entered。 So I just deleted R file to。

I just this， this this command， sorry， you can see it's there。

 And you can see my previous commands by me pressing the up key。

And you can scroll that up and down key。So it's a good away if you're like using a command repeatedly instead of typing it over and over again。

 you can just press up and hit enter。And let's say you want to find a specific file。

 I want to see the last time I made a directory。 I can type M K D I R and then press up。

 and I can see all the previous times I made a directory。

Itll only give me the history of the naturey command。And control seal end the current program。

 So let's say you run some code。And it's running forever。 And you don't know what to do。

 It's like slowing on your computer。 Things are catching fire。 If you just press control C。

Your command or process will end， sorry。That's a good way of， if something is going wrong。

 you can quickly end that process without having to close the terminal completely。Finally。

 the command exclamation mark exclamation mark will bring out the previous command entered up。

 So I do print working directory。 I get this。 I do exclamation mark exclamation mark， and I enter。😊。

We can see its's back。 and I can。Do that command again。

Any questions about any of the tips and tricks that I mentioned。要O。We have one more question。

 So let's go into that one。Alright， great。 Yeah。 So if you do RMDIR on MP directory。

You will just delete it unless there's files in the directory。You will get an error message， so。

Let's make a random directory in here。Make directorctory。嗯。Deate me。By I listed。

 we can see this is a delete me directory in here。 And as you saw。

 there's no files in there right now。 and we can check that。There's no files in there。And now。

 if I do remove directory。Deleelete me。You can get rid of it。 And it's gone now。Ex senses。Okay。

So the last thing I to talk about is flags。 So flags are way of having different behavior from your command。

 So a lot of the commands I just showed you， don't just do one thing。

 they can do many different things based on the flag you give them。

 And you can see that in your man pages。 So if I do man L S， for instance。

You can scroll down to flags， and we can see a bunch of different flags here。

And this will create different instances of the command that's using right now。嗯。

And you put the flag at the end of your command。 So I'm gonna to show you two flags that are really。

 really useful versus LA。 So you might have noticed。In the files。That I listed。

 there's a hidden file here。And there's a hidden directory here。

So if you have a file that starts with a dot， that file is hidden。 You can't see it。

 So if I go to intro to bash， for instance。You can't see it there。

 There's no hidden file at the moment。 It looks like those are all the files there。

And if I go into there my terminal， and I do。L， S， there's no hidden file in here right now。

What if I do L S， and I'd use the flag dash A or all。I can see all the hidden filess in there。

 as well。And if I read that， and now you don't have to do anything else to read the file。

 If I want to read the file。We can see this content in that file。

Similarly with the directory over here， if I go into。Directy 2 or directory 1。 sorry， if I do L S。

Let's clear that， first。I do L S or list。 You can see there's nothing else。 No hidden files in here。

 but if I do L SA。Does it head directory。That makes sense。

 Any questions about hidden files or how to view them， yeah。No， so。

 so the dot indicates your home directory and the dot dot indicates the above directory。

It's just letting you know how you can move in between these files， yeah。

Any other questions about that。2。And I also want to teach you RM RF。

 So this will delete a file directory and all its underlying components。So。We。

 we said that if we use RMDIR on a directory and there are files， you know， we can delete it。

So for this file， directory 1， for instance。There're stuff in there。

 We can delete it because they're stuff in there。But if I do R M。Directory1。 and then。70 RM。R F。

 directorory 1。I'll drive you too。 We'll do draft you2。We can fully delete the directory。

 even though there's content in there。And you see that director doesn't exist anymore。

It basically recursively goes into your file or directory。

 So it deletes everything in there and it will delete the directory itself。It's a good way。

 if you have like a bunch of junk in a folder， a good good way of deleting that permanently。

 But be careful with the R function， because if you have important stuff。

 you will permanently delete it。 So I would advise against using RF， because unless you know。

 for sure what's in that file。Any questions about that。Right， great。

That was everything we had to cover today。Are there any questions， you come here and ask us。 if not。

 you guys are free to go。O yeah。So from my understanding。

 Piazza should be like joining any other class， I believe if you look on piazza and go for， you know。

 join class and you put CS196， it should be there if it isn't， let me know。

Because we can't join the piazza， so。嗯。Just a few things I want to throw in there about Bash Thursday's lecture is also going to be on Bash。

 that's gonna to be a little more involved。 make sure you're comfortable with the material that we did today and overall try to get comfortable with using the terminal just like normally and in your other classes because we're going to be using terminal the entire class。

 you're going to be using terminal in your whole career and in school so。

We're going to release a homework on Bash on Friday so that way you guys can get some application with it and you're kind of forced to understand all the concepts next week is going to be git。

 I'll be teaching those lectures。We'll be doing get all of next week。

 and it'll dip into the next week as well。 And then we're gonna to start after that doing the Ru programming language and both of us will be working on the material for that。

Does anyone have questions about the course， because I know not all of you were here for lecture0。

Any pressing concerns。第二个字。So if you go on the CS196 website， it should be up now。

 it went down randomly yesterday and you go to resources and scroll down。

You should see under lecture one， if you click on the slides button。

 you'll be able to see these slides。Yeah， what's up。Yeah。

 so office hours are not decided yet they're to be announced。As of right now。

 they will likely be two times a week， but we will release the information pretty soon。

 We just need to sort a few more things out。Also， the files that we're using today。

 I'm going to upload the original folder。 We'll upload it the course website。

 So if you guys wantan to mess around with that and follow along with the lecture， you can do that。

Any more questions， Anything you guys wantna ask us you can come down after the lecture。

 but I'm pretty sure that's good for today。