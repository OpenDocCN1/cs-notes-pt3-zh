# 从零编写Linux操作系统-｜-Build-A-Linux-From-Scratch-p14-P14_Part_D-10-systemd__Network--BV1A78EzUEdf_p14-

Hello world， welcome back to this tutorial on  buildinging a Linux from Sctch System。Yeah。

 in the last video we have。Buil。All the packages from chapter 8。Up to and including them。And yeah。

 now I want to finish。Chapter 8， and。Then go through the system configuration in chapterpt 9。

 So yeah， let's jump right back in。By creating。

![](img/c2c4b16d856edd337379bb6f72e89a15_1.png)

。Scrip files。

![](img/c2c4b16d856edd337379bb6f72e89a15_3.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_4.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_5.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_6.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_7.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_8.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_9.png)

嗯，O。O。Now。Let's doubleub check the。The download locations。

Because I started building this with the system V version of the。Linux from scratch， book and。

So these last packages might not be in there。And my package is CSV。



![](img/c2c4b16d856edd337379bb6f72e89a15_11.png)

System D and Dpers seem to be the only ones that I needed to add。



![](img/c2c4b16d856edd337379bb6f72e89a15_13.png)

All right， then。Let us run。The installation for these。



![](img/c2c4b16d856edd337379bb6f72e89a15_15.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_16.png)

Okay。Mo to the。Drive again。And I will also mount the boot drive might need it later。



![](img/c2c4b16d856edd337379bb6f72e89a15_18.png)

![](img/c2c4b16d856edd337379bb6f72e89a15_19.png)

啊。

![](img/c2c4b16d856edd337379bb6f72e89a15_21.png)

O。I can try。That says here it couldn't unpack the documentation of system D。😔，嗯。Yeah。

 the documentation isn't really necessary。This might not be critical。 I will just let it run anyways。



![](img/c2c4b16d856edd337379bb6f72e89a15_23.png)

Well， this log file looks terrible， it's much too short and it only says。😔。

That it couldn't find things， so。Yeah， I think I will have to download。



![](img/c2c4b16d856edd337379bb6f72e89a15_25.png)

The main pages。 And yeah， I will just put them in the packages here as we。



![](img/c2c4b16d856edd337379bb6f72e89a15_27.png)

All right， now let's run this again。Okay， now everything has run through again。

And I've already looked into the。

![](img/c2c4b16d856edd337379bb6f72e89a15_29.png)

Loock files and yeah this looks much better here。See it says it installing this and that。

And heal this。嗯。This build process here where you have these 1833。Parts and。

They are compiled one after the other。Yeah， that looks much better。Okay。

 so let's continue with chapter  nine。嗯。Yeah， in the system B videos。

 we would have configured system V and gone through these boot scripts。

 but in system D you don't have these boot scripts because。Yeah， system D has more of a。

Of a wholesome concept behind it， so。嗯。You don't have to give it all the scripts for it to know what it's supposed to do。

 it already has some idea of what it is supposed to do。So you don't have to write your own network。呃。

Scrips and stuff。 You just tell system D， hey， do this with a network and system D will do that and。

呃。It's not that much our problem。So。Now that we are through with chapter 8。

 I think it's appropriate to。Have another script。I should come up with more creative names here。

But okay。Okay， I prefer。Setting my own names for。The network devices this here would。I think。

Use default。Way of naming things。Okay， I need to put a mega address here。So using IP space A。

 I've printed this list of。My current network settings， and。Yeah， this is my Me address。For the。

Why at Ethernet port。 So that's why I put that there。嗯。Okay， I could configure。

The network was aesthetic。Address， but yeah， I personally think that using DHCP is a better way of。

At least doing things out of the box。Because， I mean。

 everybody has a DHCP server in their home router today。So。

We need to set the name for the network device that we are using here。

 and that's the one we've set here。Either zero。We'll be using IPV4。It's not used domains。Okay。

 system D even creates its own resolve con。Which is a list of DNS servers and Ya compatibility。

Reasons。It's a good idea to。Make a zoo link。To that generated file and put that where。

Other programs might be looking for it under Etsy Resolve conv。Yeah。

 the entries in there should be taken from them。DHC P server on。Let's set the host name。

By putting the host name in a text file。In Etsy， named host name。Itsy hosts is， yeah， something like。

Oh。A local cache for DN S entries。But you。These days， he wouldn't do much more than put。In a 127，0，0。

1 local host here to tell it， well， if I'm talking to local host， and I'm talking to myself。

We have for IPV 6， also。Chapter 9。3。Overview of device and module handling。 This was actually。

The most interesting part of the whole process for me， because。

I've always assumed that K handed the deaf directory。And。Yeah， as you can read and hear。

 that's not true。 The kernel handles the this directory。And then there's a service named Udff。

Which reads stuff from the Zus directory， which is for communication with the kernel。And。

UDef then creates all the device nodes in the dev directory， so。

Then you can have configuration files for U Dev to。To manipulate。来嗯。You could give。

The same device name to the same device all the time because。Yeah。

 the thing is that depending on how fast a device answers and。In the boot sequence。

Things can just be。Renamed after a reboot。 so you have device A B。

 and then let's say two ethernet devices。And。Sometimes you boot and A answers first。To the request。

 hey， what devices do I have？Then A would be EthH0 and B would become ETH1。

But in the configuration for UD， you'd be able to say no， no， no， A should always be EthH0。

 B should always be EthH1 because otherwise。It just could happen that next time you boot B answers first。

 and then B will be E the H0， and A will be E the H1 and。That would not be so nice。😔。

So you can change that with UDF ruless。嗯。But I have to say， I've been a bit stuck on this。

Chapter here， because it explains several things of how to configure。Several。Things in youde。

 like how do you force something to be loaded， how you can prevent something from below from being loaded。

嗯。But。Yeah， the reason why I was stuck was because I just didn't see。What does that mean for me？

Is it telling me to do， So what should I do， I mean。When I install。

A Linux system from a distribution。Then I don't have to write my own UF rules， right。Yeah。

 in the end， I just decided。To live with a problem that devices may be named differently。

In different reboots。So I'm basically just skipping this directory and doing nothing。嗯。Yeah。

 you see that's what I mean。Here you could。Deal with having duplicate devices。

That's stuff for the configuration of Udef。O。Let's go into the。啊。Configuration of the clock。And。Yeah。

 you have a few。Things here。Things that you could set or not set and how to set。

 I don't care much about this question。I just want to move forward。嗯。Yeah。

 having time synchronization， I think， is not a bad idea。So， let's come to the console。嗯。

So I could set the keyboard layout here， but。Yeah， I would have to look into the lists of models and variants and options。

I will just accept having a wrong keyboard layout like on my German keyboard。

 the Y and the Z will be。Flipped。So。Yeah， I'll just ignore that for now。Okay。Now， L sea。All the los。

So with local dash A， you can list your locals。D， E underscoreco， capital D， capital E dot U T F 8。

 That's on my German system。What I would use that， for example， I think。

 sets the currency symbol to a euroign and。诶。Yeah， a decimal separator to a comma or stuff like that。

Okay， now we have this input Rrc。嗯。Yeah， I think that's something that。This。

Executed at the system start to set several。嗯。Configus for the year。For the terminal。

Like it defines here， the key codes fob。For the home key and。嗯。The end key and。The delete key。So。

 that。When you press a key， it actually happens what you expect to happen。

Like when you press a back space， you expect the last character to disappear and not some gibberish appear on the screen。

Okay， now the Etsy shells file。That's， again， something relatively interesting。With this。I mean。

 every user can select his own shell， like when he logs in， he wants to use a bash。

 or he could also use a regular bond shell。And you could also have other shells like there's a seahell and a Z shell。

And there's。Many of more shells。嗯。But yeah with Etsy Schtz。

 you can limit which selections are legal for the user to say this is。

 I want this to be Michel because if the user says， hey， I want Michel to be bin false。

 then he cannot be， then he cannot log into his account anymore because every time he logs in。

Been false immediately terminates again， so he wouldn't be able to log in any more。

 And by not having been false in here， you can prevent that problem。So this is basically in。

Aow a list of things that are allowed to be shell。Oh。Okay。Isabling screen clearing at boot time。

 The normal behaviour for system D is to clear the screen at the end of the boot sequence。If desired。

 this behavior may be changed by running the following command。Yeah。

 I think that's a good thing because。Because。We are interested in the boot sequence， right， so。嗯。

It I think it makes sense to keep the some information about the boot on the screen and not remove it just because you are through it a boot sequence。

By default， temp is created as a temp F S。 If this is not desired。

 it can be overridden by executing the following command。I don't care。 I'll leave it like that。

Automatic file creation。Yeah。I don't see anything we need to create。

At the system start automatically， so。Let's skip that also。Can default behavior for system services。

System services should always be restarted after 30 seconds。I think that's a good setting。 I mean。

 if you compare that to system V， yeah， the R C script would just start some system services。

 and if they crashed well。System V didn't care。 So if you wanted things to restart。

 then you would have to write some script around。These services that would take care of that and。

Yeah， I think that's not a good design for from， from a user friendliness perspective， so。I think。

 system D。系。Is much friendlier in that regard。K M。But this would have to be set for each service individually。

 so。I'll just comment it out， but leave it in there。Okay， now it gives us some。Commands， too。嗯。

Look into kernel in like journal control， which is a system D version of。D maskask。the message。

That we used to look into the ring buffer of the corner。嗯。Yeah， quas。So， if something precious。

You can limit the size of a quad dump。嗯。Yeah， I think that's a good idea。 We don't want to fill our。

Hart drive。I think one gigabyte should be enough。😔，Maybe 640 kB，640 K should be enough， anyone。O。

Okay， that was all for Chapter 9， Chapter 10。 I want to do in the next video， so。Yeah。

 I think this should be all we need to do right now。



![](img/c2c4b16d856edd337379bb6f72e89a15_31.png)

Have I saved。系啊。

![](img/c2c4b16d856edd337379bb6f72e89a15_33.png)

Wait a minute。I don't want to rebuild。

![](img/c2c4b16d856edd337379bb6f72e89a15_35.png)

All this stuff， okay。哦。Yeah， that doesn't look bad。So， it set the。Link to the of conf。

This here looks like it has something to do with。The locates， yeah。嗯。



![](img/c2c4b16d856edd337379bb6f72e89a15_37.png)

Okay， yeah， this all looks like it went through fine。 So yeah。

 I think I'll leave it at that and next time we will go into chapter 10 and yeah that's gonna be really interesting。

 You definitely don't want to miss that。 We will compile the kernel we will install a gr and hopefully we will already be booting the kernel。

 So definitely don't miss that it will be really interesting So yeah。

 if you like this video like a shared subscribe and see you next time。



![](img/c2c4b16d856edd337379bb6f72e89a15_39.png)