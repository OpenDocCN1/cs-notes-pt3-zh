# 【Jonas-Birch】使用C语言从零编写Ping-｜-Ping-From-Scratch-p07-P07_以太网与局域网通信讲座--BV1rwBTBUETy_p7-

![](img/9a9dc6b2c9f21648ab3f95fac41b650f_0.png)

So guyss， welcome to today's show。So today， we're going to talk about8。

And how computers communicate on a local network。So you have probably heard about IP。

 the Internet protocol。But today， we are going even lower level than I。

Because IP is on level3 or layer3 of the OSI model。The higher the level。

The closer we are to the application。And the lower the lab row， the closer we are to the hardware。

And Ethernet is primarily on。理。2， but also layer  one。

But we are going to focus primarily on layer 2 to day。So， when complete when。

You communicate through regular mail。Let's say we have。And below。Something like this。

So this is the back side of the envelope。 and this is。你说。So the staff will be up here for。

In addition to the actual envelope， we do also have。His paper。

Let the letter with some information on it。And in order to be able to sound this。Anywhere。

We need to write the message。On this piece of paper， on the letter。

And put it inside of this envelope。And on the envelopes front。We will。太悲。The address。就 the。

And on the backside， we will usually put him the source address of the people who sent that letter。

If we are only going to communicate one way， this is not necessary。

Because if we put this piece of paper inside of the envelope。

 write the recipient address and mail it， it will reach。The end。Useer。

But if the user wishes to respond to this lettertter。We need this。Source address， as well。

And why do I talk about。This snail manual system。Isn't that a little bit outdated， well， perhaps。

But then。It's a good metaphor for how this stuff works。So to right here。I have a network。And。

3 different personal computers， PC 1， PC 2， PC3， and above， I have written them。

So called Mac address or a short version of the Mac dress。An actual Mac address。

Looks something like this。So， we have。Total of six different fields。

Often depicted with a colon in between。And each。Fiel contains of two heads of estimate digits。

And if you're not familiar with a headeimmal number format。It's like 0 to 9。 And then we have a to F。

So we can represent。15 different numbers plus the0。And。No， including the zero。哎，你好。嗯。So， this。

Is the contents of a Mac address。And the Mac address is designed。

 so it's globally unique in the world。 Every new PC， which is manufactured or network card。

 will have one of these addresses burned into the circuit。对。

And you can't physically change the Mac address， you can change it theologically like how your computer represents itself on the network。

The Mac address is unique。And it needs to be unique because if you connect to computers。

With the same Mac address on the same local network， it will not work。So how do we？

And managed to create a globally unique address like this。Well， the first three fields。Is and。

Decided by a organization， a global organization。 So if you start a new company which produces network equipment。

 you will be assigned one of these and those other three fields， you can pick as you wish。

As long as they don't collide the。In your own organizations， you know， So it to be usually some。

Usually maybe the first network card produced will have all zeros like this。

 and then you count up to one， two and so on， or you have some other way of doing it。

 but it needs to be globally unique。So a Mac address is like an IP address。

 but the IP address is for transporting。Packets globally。Around the world， on the Internet。

Whereas the Mac addresses are used for communicating on our local network。

So these two standards coincide them。え。Cooperate a little bit。

But without Mac addresseses and a protocol like Ethernet。

 you will not be able to send packets locally on a local network。

And the Internet consists of a lot of different local networks like this。

And they are connected through routers and。All of these local networks create the internet together。

嗯。So to my right here， I have this sample network。And I have shortened the mac dresses。

 as you can say to only two fields。 And that's only because it's easier for me to， to write。But。

When I say like A A A A。I mean， a real。Mac address， 48 it long。All right， so if we have this network。

 how do we connect these computers？You might think through a router， perhaps。But。

 that's not really true。Because a router operates at layer 3， and we are on layer 2 at the moment。

 So if we have a router here。Which might be connected to this local network。

And this is the edge of the network。So this port on the router is part of this local network。

On the other side of the router， there's another local network。

So the limit of the local network goes where the router is。

So how do you connect this one way is through an older piece of network equipment that you might have heard about。

It's called a hub。They are rarely used nowadays， but they are a good way to start thinking about this stuff。

So a hub is like an extension cord for electricity。

Everything which is sent into one of the ports on this hub。

Is being sent out to the entire local network like this。And this me。

Makes it very easy to produce one of these network devices， and very cheap。Yeah。

And it's quite simple。Not very complex system。However， there are a couple of downsides。

One is security。Yeah。Since every frame。Which is。It's a network packet on layer  two。

 it's called a frame， each frame is sent to all the different node in the network。

 which is not very safe。Because it will be very easy for one of these computers to list an end of network communication when it's sent everywhere。

So that's one thing and the other thing is。Let's go speed。

If you need to send each network packet to every node on the network。Maybe in an network like this。

 where we only have like four different nodes， including the router， it's still viable。

 But what if you had like。突然的。50 devices on this network。The paint will go down very rapidly。

As new and echo devices devices gets added。So that's why this type。Hps。Are no longer used。

But during the9 day。This was the primary。え？Way of connecting local computers。

 at least on home network。So what do we use instead？I think you know the answer。This is a switch。

A network switch is more。Advanced hub。In a way， it's still connecting computers at。と？

But it has some intelligence。When one of these computers setss a network frame。

 it will look at the envelope， so to speak。And learn the different mac addresseses on the network。

And using that knowledge， it can send if this， this Py one wants to send a network gear frame to PC 2。

 for instance。It can do so。Without it going to the router or 233。

 since this network switch knows all the Mac addresseses on the network。

Let's take a closer look at how。We are。Create one of this frame。Oh。So。When we。

Stand a frame on the network。We need to package it in some kind of way， which all of these。

Noes can agree on。So there is something called P D。一页。And it stands for protocol data units。

And it's a way of packaging。Information， which works on all of these different layers。

 So the exact P format will be different on layer 3 and layer 2， as et cetera。 But it has。

 as the general P format is still。Similar so to speak， it's always consisting of two different。

Fields。We have。开der。啊。And we have good day。So the header is the envelope， so to speak。

 and the date the field is the letter inside。The header contains all the addressing information on layer 3。

 for instance， it might contain IP address。And although too。

 it might contain mac addresses of the tourists and the destination。So。

Using this P format with a header and data， we have some consistent way of talking about these things among the different protocols on the different layers。

And。So。不人。I think we're talking about EtherF。I'm going to show you how one of these frames look。So。

 we have a。Soar said。Field。We have a destination field。And we have a day。

And there are different versions of Ethernet and different ways representing it。

But these are the general。Pa。Usually we can include one more field， which is。Yeah。

 it can be called the type field。Or the proable field。

And this contains some information like a value such as 0 x00800。

If this data field contains an IP packet first。Or it might contain something like eight or eight if it are。

And that way we know how big this data field is and we know what to expect。Yeah。



![](img/9a9dc6b2c9f21648ab3f95fac41b650f_2.png)

All right， you guys， welcome back。So if we remove this， type build and focus on the other part。

Oh that's practical。Let's and now I'm talking about only Ethernet。 no， I or anything else。

So let's say PC1 here wishes to communicate with PC2。And we need to take one thing into account。

 And that is that PC1 knows its own market。But it does not know anyone one else's， not piece 2。

 not 53， not the router。And let's say these two have not communicated。previousビ？

So let's say busy who wife wants to say hello to busy too。So the day the field。为了看。The hello message。

And the source address is， of course， P1ang's Mac address。So let's book AA。AA here。

But before we can this， we need to put something into the destination and what do we put there？

Remember that this one does not know the Mac address of Bea tip。So in this case， we put all fs。

Right the forest here， but。It's a full Mac address of Fs。So what is it  12 fs or something？

And this is called a broadcast。😊，Great。And PC1 will send this to the switch。

And the switch will send it to every。Single device。On theね。Like this。And that's。

The purpose of a broadcast。 So if it does not know the destination Mac address， it's going to。

Send it to a broadcast。And。P c one诶 p c two有。Receive this whole frame。

 the message as well as the source and destination addresses。

Which means that PC2 now knows the Mac address。Or piece one。

 so it's going to save that inside of a table。write down A A A A。啊。

And this is called the Mac dress table， where some sometimes it's called cab。Often。

 we talk about routers， because routers have a memory chip， which is called it cab。

 where it stores this kind of stuff。 So it's a term， which is widely used。All right。

 so let's now say that PC1。I mean， it two wishes to。Response。就别催我。Let's say， we want to say。Hi there。

And。In this case， Pi2 is just going to put its own Mac address as the source， which is CC。食屎。

But at this time， PC2 knows the Mac address。嗯。If1。 So this time we can cover it。

Inside of the destination he like this。And when we have the Mac address in the destination of field。

Of an end device， this is called a juniorcast。对。And what will happen is this is going to be sent to the switch。

 and the switch is going to send this frame to P 1， but not to any one else。

And this is the most optimal way of communication。Alright。

 so this was a little crash course into the Ether protocol。

 And now you know enough to code this stuff in C。But if you feel that something is not clear or if you want to。

Learn more about this stuff。I recommend my book。The foundation of network technology。

Because in chapter two。You will learn all of this。And this is the Swedish version of the book。

 by the way， but I will provide a link to the English one。

And here you will know everything about Mac addresses， how the communication is from the network。嗯。

哦的是的。And if you continue on to chapter 3 about Internet protocol。

 you will also learn how these two protocols。Work together。So thanks for watching today。



![](img/9a9dc6b2c9f21648ab3f95fac41b650f_4.png)