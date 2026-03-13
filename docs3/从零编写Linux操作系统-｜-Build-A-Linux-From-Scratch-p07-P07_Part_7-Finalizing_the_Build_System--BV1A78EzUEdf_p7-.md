# 从零编写Linux操作系统-｜-Build-A-Linux-From-Scratch-p07-P07_Part_7-Finalizing_the_Build_System--BV1A78EzUEdf_p7-

Hello， weld。Welcome back to this tutorial on building a Linux from scratch system。Now。

 in the last video， we have talked about。Yeah， building the system， so。

So far that we have all these directories， and we've created。All these。All these users and groups。

And how we want to proceed， compiling more stuff。Tpter7。嗯。Yeah， so。

So what the Linux from scratch book。Now， assess is。Before we've。So。

So we are running this LF S script， right。 And here we。Go into the change route environment。And then。

That change root environment。Does all that stuff。嗯。And then， they say。They want to run another bash。

On top of that。Change root environment like this。嗯。

So the reason for that is that the first batch that we are running。

In that train route has some problems， for example， because we are running this as route。

But inside that change root environment， this Etsy password file didn't even exist。

 So from inside that。Adam。You would have some problems because you are running as a user I D that doesn't that doesn't have any user attached to it。

At least at the start of the script。 So after we've created that。Then， we。Make another bash。

 and that doesn't have these problems anymore at that point。嗯。😊，If you ask me。

I'm really not sure why they do this stuff inside the change root environment in the first place。嗯。

Because。From my understanding， I don't think that there is a good reason why you shouldn't do that。

Already in the L F S script before。Going into the change route environment。嗯。I mean。

 also these creating all these directories， you could do that outside of the change route， you know。

Simlings， I'm not sure if that would work outside the change route， but。Yeah。

 Etsy hosts could be created outside the train wood。

I'm really not sure why they do that inside a trained route， but。

I guess I have some good reason for that， so I will just accept that。嗯。

But I don't think there is really， it's really necessary to put。The L S script。

 a bash on top of the a broken bash on top of the bash script。

 and then a working bash on top of that。嗯。I think it would make sense。 I think it makes more sense。

To just。嗯。Exit the change route at that point and then just enter the change route again。So。

We might do this this inside a loop。We will just have another。Scrt。Okay。So we need another script。😔。

So what do we do in here？Well， we want to continue installing packages。So I will just copy this。

Package install check 7。Which pes do we need now？We need。Lip SD， C plus plus。Good text。By some。台称。

Text info。You。Linux。Okay， so these are the packages that we want to install。



![](img/77264a30aa8a858ec63338e684f04aba_1.png)

![](img/77264a30aa8a858ec63338e684f04aba_2.png)

So， now， I've created。All these files here。And now， I will just。Again。Copy these。

Compile instructions here。Okay。So inside train routes too。😔，We will try to。Stall these。

We might want to set LF S to nothing because I don't know。

 Maybe some script could try to use the variable。 And since we are in the change route。嗯。

There's actually， there's really no prefix to our slashs， whatever。

So I think it makes sense to set this to。An empty string。And also when we start this。

We start this as root， and root has。The home director is slash route。And when we run at bash。

Normally， the。The directory that you start in is your home directory， so。

I think we might be in the wrong directory here。So I'm gonna C D2 sources。Okay。Okay。

 so the Linux from scratchbook Now， I don't know why they do this here。Create a few more。

Fileles for logging。And give them。Certain permissions。嗯。So。

I think they need to be there for the kernelel to write its locks。

I don't know why they put the creation of these files here and but。Yeah， whatever。

 I will just leave them there。Yes， I think。So we have inside change route 2， L F dot S， H。

Prepare change route。Then we are running these scripts in a loop。Maybe put。

Quotation marks around them。

![](img/77264a30aa8a858ec63338e684f04aba_4.png)

ok。Yeah。Doesn't look too bad。 So let's run this。Okay， now we are running change route，2。

We've created these files。And this does not look good。Okay， extracting X C file。

X E cannot not exc no such file or directory。嗯。

![](img/77264a30aa8a858ec63338e684f04aba_6.png)

That's weird。Let's see。Okay， something that immediately jumps at me is that there is no X Z。

Direy here。Which I think， should be there。Lets look at the log files。There is no X Z dot lock。

That's weird。

![](img/77264a30aa8a858ec63338e684f04aba_8.png)

Co。Look at that，The package in the package of CSV wasn't named XZ。Okay。

 that explains what's going on。So when I tried to install X Z。

 it would just not have found it because of this。So。How do I go on from here。Okay， so。Of course。

 we have the problem that。These virtual file systems are。Mounted at this point， so。Well， am I。



![](img/77264a30aa8a858ec63338e684f04aba_10.png)

Yeah， I think I will just reboot here。Doesn't make sense like this。



![](img/77264a30aa8a858ec63338e684f04aba_12.png)

Okay， so I have rebooted now。First thing。We need to do。After rebooting。Mount the。USB key。Okay。



![](img/77264a30aa8a858ec63338e684f04aba_14.png)

So。But。

![](img/77264a30aa8a858ec63338e684f04aba_16.png)

Ok， so x3 was not compiled before。So。I will do this here。But to be sure。

I will put an exit behind that， because。Yeah， this。

Because we are changing the owner of everything here and。

I don't want to do that unless I'm sure that X Z has successfully compiled， so。



![](img/77264a30aa8a858ec63338e684f04aba_18.png)

So now you have the problem that all your directory belong to root。So。I will。Yeah。

 just take the ownership back。好难哦。Okay， it just going to take a while because we already have a lot of files there。

O。So if we hadn't done that， then the compilation of Xz might have failed because we are compiling as user。

And if it tries to install that on bin or wherever。And bin as owned by routes。 that wouldn't work so。

That's why I。Took the ownership back。Okay。Yes， now it's extracting X Z。



![](img/77264a30aa8a858ec63338e684f04aba_20.png)

O。This looks fine。So， now I'm。Move that again here。And now， we can run。



![](img/77264a30aa8a858ec63338e684f04aba_22.png)

The tractor 7 quotes， again。That looks better， so far。Okay， I wrote two。That doesn't look good。

And you cannot not find。Liip and curses double you。Okay。



![](img/77264a30aa8a858ec63338e684f04aba_24.png)

But maybe that's not the first thing that。Has failed， so。Let's look at the log files， first。

Maybe there was an error before， and so。Let's see。What are we installing。

So the first thing we installed the slip STD C plus plus。Go down to the end of the log file。

Make leaving directory。 That sounds reasonable。That doesn't sound like anything。Had cleareded down。

Get text。So long look， as you can see here on the right。6。The long lock file。Sounds like most of it。

Worked well。Okay， some warnings here。Make leaving directory。 make leaving directory。

 make leaving directory。Sounds good， normally。Baicong。Make leaving directory。啊。啊。Okay。

That doesn't look good。14 lines of code does not sound like a 14 lines of log file does not sound like a successful build。

Okay， let's make sure your kit is complete checking。Okay， it seems to look for。For fails。

 and they aren't there。Okay？But I notice these files all start with a， with a dot。So。

These are hidden files。Going on here。Pay， I'm telling it to show hidden files。Yes， okay。

These files are actually not here。

![](img/77264a30aa8a858ec63338e684f04aba_26.png)

Let's see。 Are they somewhere else。

![](img/77264a30aa8a858ec63338e684f04aba_28.png)

![](img/77264a30aa8a858ec63338e684f04aba_29.png)

？

![](img/77264a30aa8a858ec63338e684f04aba_31.png)

32 R。Here they are。啊。唉。Okay。I know what's going on。Here in our。Package installer， right， We have。

We create this。This target directory， right？And。AndThen， we extract the。Tobo。Go into that directory。

And then we move everything。So， if。Okay， so。We unpack this tar。

 and then we have this director pearl 5，32， slash pearl 5，32。And。

This was this whole thing where I said if everything is in one directory。

 we just pull everything out of that directory。And that has not worked for these。4 here。

So I could just move them manually now， but。Actually， that wouldn't work because。

When I run this again， the directory is just gonna be removed and recreated so that we will have the same problem again。

So。Instead of moving。Star， I will move star comm。Dot star。 So we。Explicitly， include hidden files。



![](img/77264a30aa8a858ec63338e684f04aba_33.png)

Wait， wait。 Who wait。

![](img/77264a30aa8a858ec63338e684f04aba_35.png)

I almost ran this。That would be a waste of time。Because。Liips standard C plus plus。

Get text and buy and rent through properly。And， let's see。Python。Yeah， that doesn't look suspicious。

 It looks okay。As do we have text info。It's complaining that Pearl isn't there， Pearl wasn't there。

This one is correct to complain。And you till the next head。



![](img/77264a30aa8a858ec63338e684f04aba_37.png)

Theres problem that it couldn't find incursors， but。



![](img/77264a30aa8a858ec63338e684f04aba_39.png)

I will run this。Now， and then well see。So， Python。Looked like it went through also。

 So I'm going to run it like this。

![](img/77264a30aa8a858ec63338e684f04aba_41.png)

Okay， this is it。Already more output than we had in met。Loock file， so。It looks like its。

Doing better now。Okay， well that's running。

![](img/77264a30aa8a858ec63338e684f04aba_43.png)

Let's see。啊。U Linux had complained。About。And curses。 So it was not able to find。



![](img/77264a30aa8a858ec63338e684f04aba_45.png)

Dash L N Cursors W。Now。Just from my experience as programmer， I can just tell you。Not finding D L。

 something means that it is looking for。啊。It's looking for a file， named。Lip。And。Cus W。Dot S， o。

Shared object。 So something like a DLL file under Windows。嗯。So。Why does it not find this file。

I will just put a wild card here behind the name。Okay， it's。That's。

Let's just redirect these error messages。Okay， sources is not what we are looking for。So we have lip。

Lip and cursesors， W S0，6 and S 0，6，2。And we have user lip， lip andcursors， S O。So。

For whatever reason。嗯。It seems like。The linker is looking in。This directory。

 but not in this directory， because if it looked into this directory， use a lip。

It would find a lip and curses dot S O。So。So， it seems like it's really。嗯。

Seems like it's really looking in this lip directory。I will just make a swim link。

I had no not assuming I will do a hard link。So， I would just。So呃。

A hard link is basically like a copy of the file。Except that。You don't have。 You're not using the。

Twice as much disk space。So。A hard link really means that you have two different entries in your。

In your file system， for the same location on the hard drive。So。触っちす。😔，No。Okay。

 so if it's looking at lip at the lip directory， now it should find lip andcursors WO。

And it's still compiling pearls， so。I think this might have been early enough。😊，That。

Maybe this u Linux compilation。Will， later。Run through， maybe。But okay， so yeah。

 I will just let this run。For now again。

![](img/77264a30aa8a858ec63338e684f04aba_47.png)

Okay， it has finished。I'm not sure if I should be happy or suspicious。

 because this was relatively fast。Let's see。Okay， this was as far as it had gotten before。

 I think so。Seems like it's gotten further， at least。Leivaving directory。 leaving directory。

 leaving directory that。It's something that you see in recursive code from the make program。

Text info。A lot of。Loock file here。Leaving directory， leaving directory。 leaving directory。And per。

That's a lot of look file。Wornings。Okay， it's complaining a bit about locales， but。

Since this is still just a temporary system， you know。

 B is not the final system that we are building。I think it's okay。Setting locale failedette。

Falling back to standard look here。Okay， so it didn't end with a warning with an error message。

I mean， we have an error message here。But it says it was able to do do with that， so。I think。That。

Looks like。It looks fine。I look at that It。25，000 lines of lock fire。😊，Okay， whatever， so yeah。

 anyhow。This video took a bit longer than I expected。But。Hey， at least was。With some。

Fixing errors that at least teaches you some interesting things and lighting is bad。嗯。

I'm just seeing that on that little display on my camera。Okay， so。Yeah， it took a bit longer。

 so I think I will just stop it here， I wanted to go into Cha 8。Today， but so。Okay。

 at least weve finished chapter7。嗯。The Linux from scratch book。At the end of chapterpt 7。Actually。

 does a little bit more。So。They tell you to delete a few things， and。Some documentation， for example。

 for。For the programs， because they are only temporary programs。

 so you don't need the documentation for them。And remove the。

Remove the debug symbols from the binaries。But。90 megabytes， that's not so much。How。Yeah， I mean。

 the system is at is around 5 GB now and。We would be saving 120 megabytes roundabout， so。

That's not worth it if you ask me。 So， yeah。I will just。Stop it here， and。Yeah， maybe we should。



![](img/77264a30aa8a858ec63338e684f04aba_49.png)

Still， try to unmount this。So this should unmount F P T， S and depth。



![](img/77264a30aa8a858ec63338e684f04aba_51.png)

Okay， this time it worked。 less time an mounting death didn't work， so。That's why I had to reboot。



![](img/77264a30aa8a858ec63338e684f04aba_53.png)

![](img/77264a30aa8a858ec63338e684f04aba_54.png)

Okay， so now we've unmounted these things。The thing about。The backup that I had tried before。嗯。

This doesn't work when。When these mounts， these directories are mounted。That's why it。

It was completely futile to try and make a。Make a backup when I tried last time。 So， but now。

 now I could make a backup。Because this time。

![](img/77264a30aa8a858ec63338e684f04aba_56.png)

These directories are not mounted。And yeah， as you've seen。

 you can really have some trouble when you。When these directories mounted， for example。

 my my Google Chrome crashes when that happens and you cannot start it again， so。

I'm not sure what's going on there， but yeah。If you can not unmountund， just reboot。And yeah。Okay。

 so again， this is enough for today。 So'll see you next time and。If you liked the video， like， share。

 subscribe and see you next time， bye。