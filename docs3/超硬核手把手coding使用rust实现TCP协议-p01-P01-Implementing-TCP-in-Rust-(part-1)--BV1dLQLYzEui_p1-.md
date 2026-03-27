# 超硬核手把手coding使用rust实现TCP协议-p01-P01-Implementing-TCP-in-Rust-(part-1)--BV1dLQLYzEui_p1-

So welcome back today we're going to take on a relatively ambitious project we're going to implement TCP for those who you aren't aware TCP is basically one of the fundamental protocols of the internet。

 it's the way that basically enables two different hosts on the internet to talk to one another in a reliable way so that you can send data in such a way that you're guaranteed to not lose anything that you send and that the receiver receives things in the same order you sent them the internet does not generally guarantee this and so TCP is a protocol that that basically sequences data across the network and makes sure to do things like retransmissions if packets are lost。

There have been a couple of questions in chat just before we started about like how much of TCP are we trying to implement the goal is to implement basically something that can talk to a real server。

 Now， how we define real server we'll get to in a while。

 but the idea is that we want the ability to talk to a real host on the Internet。

 So talk to some TCP implementation that is not our own。

 This means that we're not gonna implement any of the sort of advanced extensions to TCP or any of the sort of any of the advanced congestion control algorithms。

 for example， we're just going implement sort of the basic。

 probably new reno And so what we're gonna to be working for is RF 7，9，3。



![](img/e709d71a082b45418e3b70befbd3ce3f_1.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_2.png)

If I remember correctly this one。Alright， I guess actually， I want this one。

So T so this one is the RF for TCP， the transmission control protocol。 as you saw from Twitter。

 I think I posted out here。There are a couple of other RFCs that are handy to follow。In particular。

Why is this being weird no。In particular there's sort of this tutorial I'm not going to read through it。

 this is just good background for people who want to understand how TCP works。

 I'll give a very brief overview sort of drawing some figures and such。

 but I'm sort of assuming that you roughly know what TCP is I don't expect you to know the protocol by heart or what all the headers are that you sort of know what it's doing so I will not go through this particular RFC。

This document we're probably going to refer to a lot。

 so RF 7414 is basically a list of other RFcs that you probably need to implement。

 We're not going to implement anywhere near all of them in particular。

 we're going to focus on the things that are listed as core functionality。

 which basically thinks that you must implement to be a TCP host on the on the internet and that is basically 793。

 which is the core TCP protocol 11，22 defines。couple of other things like additional extensions you need to support and from memory some like initial values you need to set for different bits。

 we're going to ignore this because we're not going to support IPV6。

 This I think is basically possible to ignore and this one is basic control congestion control So we need to set up like basically Reno which is。

Pretty much slow start would be my guess。And this's like some stuff on retransmission timers and segment sizes。

 So these things down here will be relatively short extensions to the core thing which we're gonna do in 7。

9，3。 So my guess is that for this particular stream。

 our hope is to get somewhere decently far with 7，9。

3 and whether we actually get there or not we'll have to see。 But the hope is that we get 7，9，3。

 and then we can do all the extensions， maybe in the next stream。

 and then hopefully at that point we can talk to other hosts。

 So hopefully that gives you some rough idea。嗯。There's also RF 2398。

 so 2398 gives a bunch of tools for testing TCP implementations。

 My hope is that we'll get to try some of these after a while but that's sufficiently far down the line that I'm just going close it for now because it's not terribly important this RF 2525 is just a really handy way to debug TCP implementations because it gives a number of sort of known problems with past implementations and what the problem probably is if if you experience one of these particular issues so we might end up referring back to this so I'll keep it open although the core thing is gonna be 793。

Before we dive into that， there are a couple of small things I want to talk about So first there's the live coding voting site。

 So this is how we ended up doing implement TCP this time there are a bunch of other proposals too for upcoming streams So here if you go to the site you just put in a unique username and then you just drag these ideas according to which one you would rather like to see me do and it basically runs a it runs a a now I can't even remember what is' called。

嗯。Ranked choice voting to determine which one is the next upcoming stream and then also to figure out things like run ups so that we can keep running。

 running， basically elections， even if people only vote onces。Why is this not following the chat？😔。

Okay， so that's the live coding stream voting site。

 The other thing I want to mention is the last sequence of streams we did was supporting Flagraph to rust and so we ended up with this tool called Inferno and Inferno has actually been doing really well thereve been a bunch of people contributing we now have full color support and so if you look here we already have nine different people contributing so we have Jason has been doing a lot of work for doing things like。

😊，Supporting additional features like name attributes and stuff。

 BC Myers has been doing some work on adding sort of cleaning up the interfaces。

 some performance hacking， Joordy has been doing a bunch of work and coloring and so this has just been a really cool project and there's still lots of open issues so if you want to try to contribute to something that is sort of simpler to where we're going to be working on today then Inferno is a really good place to start。

And all the past streams are of course， up on YouTube as always。



![](img/e709d71a082b45418e3b70befbd3ce3f_4.png)

嗯。All right， so let's get started with TCP。In the tweets where I announce this。

 I announce that we're going to use this crate。 So peanut is basically a way to do low level networking。

I so。Normally I don't do any research before I do my streams in this particular case I knew that there were some weird things we were going to have run to run into when we start dealing with low levell networking in particular once you want to do things like implement TCP yourself。

 you run into the issue of the kernel already implements TCP。

And you sort of need to steal packets from the kernel。

 but the kernel needs to know which packets you're going to steal from it so that you end up in this sort of weird position where the packets sort of go to the kernel and to you and it's just a little bit of a pain。

 And so we're actually not going to use the peanut because it uses as far as I can tell。

 it uses raw sockets and raw sockets are nice if you're implementing your own protocols but not so great if you're implementing TCP because the kernel is still going to send basically the kernel is still going to run its own TCP stack and that might interfere with the things that we're trying to do。

So instead we're going to use this Linux feature actually let's put this here。

 This Linux feature called ton tapap so ton tap are basically user space， so not in the kernel。

 but in the user space a way to write what essentially looks like a network to the kernel And so what you're going to do is you construct you tell the kernel to create a network interface for you actually let me draw this is's going be easier。



![](img/e709d71a082b45418e3b70befbd3ce3f_6.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_7.png)

And if you have any questions at any point during this。

 the getting sort of the basics of this is pretty important。

 So if you feel like there's something your' stuck on then like just give me a shout。

 why I want I want that one。Okay， so。In normal applications。

 what we usually do is we draw the kernel as a thing down here。嗯。

And then user space sort of on top of the kernel。Wow， this is one is not great for writing。

 Let's depend pen。 And then you can imagine the like down here is the big， scary Internet。

And they're going to be a bunch of packets， and they sort of arrive down here at a thing called the NickC。

 a network interface。Pro the link to that kernel patch。 It's， sorry， it's not a kernel patch。

 actually， it's a it's just a description of ton tap。



![](img/e709d71a082b45418e3b70befbd3ce3f_9.png)

So if you search for just to top dot text， you should find it， but I can post it to chat as well。

 I guess。

![](img/e709d71a082b45418e3b70befbd3ce3f_11.png)

呃。

![](img/e709d71a082b45418e3b70befbd3ce3f_13.png)

It is。My chat is on a different plane over there so I can't put anything there。That one。

So I don't know if you got that， but。

![](img/e709d71a082b45418e3b70befbd3ce3f_15.png)

Let's go back to this。 So there's sort of a network interface and that receives all the packets that come from the network and the kernel sort of internally has a bunch of data structures that it uses to run things like TCP and it's going to send responses here。

 if user space wants to talk over the network， they create a socket by calling into the kernel。

 the kernel allocates some kernel memory for that socket that represents that TCP connection and then the user space thing is really just a pointer to the thing in the kernel And so this is how normal networking works that if you want to say read or write from a network connection。

 then you just give this identifier that the kernel gave you that's normally just a number like a file descriptor and you say like write these bytes to that file descriptor that goes to the kernel。

 the kernel then knows how to talk TCP and send stuff back on the interface card。

So what's going to happen in our case is that we still have this sort of user space and kernel divide。

Like so。And what we're going to do is we're going to have the kernel create what is basically a virtual interface for us。

 I'm going to draw that here。嗯。So this is a ton interface。

 and it's going to treat that as if it's its own network card。

 So it's going to treat anything that comes out of this as something that sort of came from the network。

 right， It's going to treat this as a ni。As a network interface。However。

 any it basically is going to consider this sort of the wire of that network。

 So any time time it tries to send on this network interface。

 that's really just going to appear out of here into the userspace program。

 So the user has like a process running here and basically any send the kernel does turns into a receive in the userspace program。

 and similarly， anytime the userspace program write something that's going to sort of go through that and appear to the kernel as though that was a packet that came from the network。

 So it's basically lets us emulate a network inside of user space。

So that's what a ton device does and effectively what it gives you is so there's the command IP that lists all the interfaces on your machine IP。

 if we create a ton interface is going to show that there's an additional interface like ton0 that has like some IP who knows what it's going be and like a bunch of other information and if we try to send something on this。

 what's going to happen is that the kernel is going to look up which which process owns this tunnel。

or this ton， and then it's going to take whatever the kernel wrote into this interface。

 whatever raw bits of a packet it wrote into here， those are going to be redirected into user space and whatever user space writes back is going to be treated as if it came back onto this network socket。

And this allows us to implement TCP pretty nicely right because we on here all we have to do is just like implement our TCP stack and if we receive a packet。

 then what really happened was the kernel sent a packet to this address and we're just going to interpret it as a TCP packet and we're going to send responses back to the kernel and the kernel is going to think it's talking to some host on the internet。

Why is this not following chat？呃。Okay， so does that roughly make sense。

 we're going to get into a lot more detail about how exactly we end up using Tn。

 but does the rough idea make sense that the ton that we create is basically a user space network。

Yeah， the link posted by Wilkins is basically the same document。Okay。



![](img/e709d71a082b45418e3b70befbd3ce3f_17.png)

And that means that instead of using the peanut package。

 we're actually going to use this ton top crate。 So luckily， there's a rust crate for this。 hello。

So luckily there's a crate for this and it's pretty straightforward right what you do is you have a ton top interface。

 ignore top for now。😊，And you can create a new one， you can give it a name or you give it a name。

 it can be empty。 and then the kernel just generates one for you。 You can choose the mode for it。

 and we're going to ignore mode for now。 And that gives you an interface。

 And once you have an interface， you can call receive to receive a message and you can call send to send a message。

 which is sort of what you want。Why is this not following Chad。

 I have to scroll down any time someone sends a message which is not ideal， Lets try that instead。嗯。

Yeah， so so all this gives us is a receive and asend and what these receives and sends are are basically IP packets。

 So any time we receive anytime the kernel sends an IP packet to us。

 So any time the kernel base is at the network traffic our way。

 the receive is going to give us back the bytes contained in that packet and similarly。

 we can send bytes out and the kernel is going to receive those as an IP packet。What this means。

 unfortunately， is that we also need to implement the IP protocol because we need to be able to send packets to。

 to the internet。Luckily the IP protocol is is。A little bit simpler。

 It's basically just you name the remote machine。嗯。

Don't you risk freezing the entire system if you mess something up。

 Ask him because I would like to follow along without my PC crashing every attempt at running the thing。

 It's unlikely that the entire system is gonna to freeze like the kernel is not like you're not going to crash the kernel for using a ton interface。

 However， what you might do if you screw things up is you might set up the routing tables on your host machine so that you can't talk to the internet anymore。

 Usually all you have to do in that case is like reboot or restart your network interface。

I'm hoping that this will not happen to me because then the stream will be cut off。 but in theory。

 at least we should be fine。 But but the the biggest concern is that your network traffic is。

 it no can no longer be routed。 Like imagine that all of basically if your entire network connection started going over the ton interface。

 then nothing is gonna go to the internet。 Every everything every packet you send is just gonna go to the。

It's just gonna to go directly to the process you're writing。

 which doesn't know how to talk to the internet。 It might be better to work in a VM， although again。

 I don't think you can really break anything this way， and I don't particularly want to work in a VM。

 but I agree you you totally could。 and it might be better。 I just don't want to。But yeah。

 so this gives us basically the interface we need。 there's one thing that's un missing and that is the RF for the IP protocol。

 which is 791。

![](img/e709d71a082b45418e3b70befbd3ce3f_19.png)

And luckily， the IP protocol is very， very straightforward。I don't need all the description。

Basically， when you send an IP protocol message， it looks like this。嗯。

So there's like a bunch of fields that we basically can ignore。Well， we're going to have to set them。

 but they mostly have constants。嗯。And then there's a source address and a destination address。

The source address is going to be the I address of sort of us。

 as in who we're pretending to be on the。On the user network that we're creating and the destination address is going to be the remote host that we're talking to。

I don't think we're gonna need any options。 And then following this header is gonna to be the contents of the packet。

Do you need to be root， so generally you need to be root to create these things。

 but there is a capability specifically Capnet admin that you can see this is a basically a thing you can tell the kernel to give a particular process or binary。

 you can say that when this program runs， it's going to have this capability。

 which means that it's going to be able to do these things without having to be root。

So we should not need to be rude for this。 You do have to be rude to grant this capability。嗯。Okay。

 so let's get started。 I think is the way to go。 I think step 1 of this is going to be just being able。

 making sure that we're able to send and receive packets at all。 And so as before。



![](img/e709d71a082b45418e3b70befbd3ce3f_21.png)

We're gonna go into streams。 I'm gonna a cargo new Lib。 Actually， Is it gonna be a Lib or a bin。

 Let's make it a bin for now， start simple。We're going call it。 What are we going to call it。Thanks。

 what are we gonna call this user space TCP thing， It's gonna be。That's going to be trust， TCP rust。

All right， and we're， of course， going to depend on the ton top crate。0， one， two。

And source main is going to do an externalern crate on top。And then。

I guess what we're going to do here is something like。参加。

This is just to see that we can get anything working。Moode， where its the。

 we specifically want ton mode。Don't worry too much about the difference between to and tap。I mean。

 I can explain it if you want to， but I don't think it's relevant。Faiil to actually now。

 Maine is allowed to return a result， right？I think that's true。嗯。And。Thunder is pretty funny。

 actually。Although。Oh， you're sorry， you're right。 I don't need extra crate， thanks。T。

 I like thunder。Wait， that's a great。 Actually， I， I agree。 Let's switch up to thunderhunder。Well。

So the reason trust is nice is because TCP basically， it doesn't actually establish trust。

 but it doesn mean that you can trust the what you send is what the other person receives。Actually。

 let's keep it thrust for now。 and then we can， we can figure that out later。

I was planning on using stable， although who knows。I don't remember what my default is。

 my default is beta。 So we're on beta。Okay， so we're going to do now。

We're going to create a new interface and then we are going to do。Buff is gonna be a。1500。

 and I'll explain why soon。Actually。I don't think we need packet info。Yeah。

 let's do with that packet info。Now， this is your new find for for now。0， you8。Oh。

 it's the other way around， right， you ate this。 And then we're gonna do Nick dot receive。

Into bothuff。Then we're gonna do。Read this mini， actually。Yeah。And then， I guess we're gonna。Ex。

 this。How many bytes we read， I guess this is n bytes。And this is gonna be buff。1en bys。

Let's just like see whether that works at all。Just so we have a place to start。In fact。

 almost guaranteed will not。Tn tap， not found。Oh， it's。Oh， they've done it properly， nice。Oh yeah。

 tsunami was great， it was a good crate name too。嗯。Oh， I。Face。And what else we missing。Oh， what's。

 I guess like this？哦。Don't need both。And then because we're going to be able。

 we're going to be doing like networking things， we're also going to do pseudo set cap。

What was it capability called cabinet admin on。Target there， release trusts。嗯。

You don't need a use statement because all with uniform paths， any。

Any identifier identified to the left of all the colons considers anything that is in scope and all external crates。

嗯。So why can't I do this？Set cap。Thatash age。Dus R dash， what？Help。Man said K。嗯。H。Oh。

 is it like has to be lowercase or something， Cap Net Edmmin。What。😔。



![](img/e709d71a082b45418e3b70befbd3ce3f_23.png)

哎。Apparently not。

![](img/e709d71a082b45418e3b70befbd3ce3f_25.png)

Equals EIP。What is the equals for。Man， cap from text。哦。

Each clause consists is a list of a comm every capability names and actually consist flag okay。

 what do the flags mean？M嘟。Secret flags indicate the list capabilities of recording re be race。

 For example， exs lower every capability effective and inheritable。 Oh。

 we just want to set them for all of them， sure。Equals EIP。Great。😊，And now I think in theory。

 we should be able to run this thing。Wait， it didn't error。

So let's look at what IP addresses we have。 Okay， so we now have a ton zero interface。嗯。

It doesn't have an address or anything。 So we can't。

 We don't actually know how to send anything to it yet。嗯。So let's do IP adder set。6，8，0，1。Slash 24。

The to0。Oh， add。Alright， so this still hasn't received anything， at least as far as we can tell。

 But now then also。呃。Seet。Link。Set up dev to 0。Great， so here it got a packet。

 I have no idea what packet this is， but this is indeed a packet that it got。One thing we're gonna。

 so as you notice， this just got a bunch of bits now， right？ So clearly， it is receiving some stuff。

 Like when we brought this link up， it received an I P packet of some kind。

 I don't know what kind of I P packet， maybe a pinking packet or something。

But it did receive an IP packet， and so that's suggest that our sort of our basic setup is working and now you see tons zero is gone。

 right？What we're probably going to want because building running this thing is a little annoying is we're going to want to do something like have this in a script。

嗯。And that's going to do cargo B release。It's going do that。

Then it's going to do what we did over here。And also what we did appear to set the address。

This is basically so that we don't have to run this every time。ho。This is just weight Pi。

 I think it's weight pi。Oh， maybe it's just wait。Yeah， it's just wait。

So what the script is doing is it's building， setting the capability。

 running the binary in the background， keeping the process ID of that around， setting up the network。

 and then waiting on that process to finish。Which in this case， is gonna read the 52 bys。

 as you've observed， though， like， this is a little weird in the sense that we don't know what these bits are。

 So we're gonna want some kind of tool that can help us interpret what these are。

 And we will probably want our program to not just exit to， right， something like。6。

So now if we do runus H， then now it's going to continue。 So now the IP。

 this is still up and now let's try to do something like ping on interface ton0。

 we're going to ping some address on that subnet。So this now received a bunch of more bytes。Right。

 if we， you'll notice that it keeps receiving bys。 and these are， in this case， pink packets， right。

And so now we're gonna have to interpret these in our program so that we can like parseel them as TCP packets。

 for example， And so what we're gonna to do is use， there are a bunch of tools you can use here。

 I'm going to use one called T shark。 So this is a terminal version of of wire shark。

And notice that it gets to sort of watch this interface and see what's going on。And specifically。

See this  the 52 bytes thing was a IPD6 router solicitation。

 that sounds like something we should ignore。And then all of the other ones are requests。 And。

 of course， there are no responses because our program doesn't do anything。

 it's not responding to anything。Okay， so what we're going to want is basically our program needs to sort of parse out the packets and know what to look for。

So we're going to kill that program for a second， and so this means we're going to have to figure out how to parse these bits。



![](img/e709d71a082b45418e3b70befbd3ce3f_27.png)

If we go back to this， you'll notice that what receive says is you get the MTU。

 which is basically just the packet size in your network where you're going to assume it's 1500 and you get plus four for a header that packet info is propended。

 So this is what the difference between new and without packet info is。

 specifically in this case this is a description somewhere here， the frame format that you get。

 is you get two bytes of flags，2 byte of protocol and then you get the raw frame。



![](img/e709d71a082b45418e3b70befbd3ce3f_29.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_30.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_31.png)

So if we look at the bytes that we received， this is gonna be。Like flags this。 see。

 we can probably do flags is。嗯。Actually， probably one bite order here， but isn't there。

Didn't we recently get like Reed big Indian or something in Ru？Might not have landed。

 It might not only be nightly。嗯。This is going to be very handy， regardless， BE。Yeah， from B。

<|OTHER|>So we're going to have a U 16。From N E。You 16 from any Btes。Sorry， give me a second again。

You just need to make sure the chat doesn't turn it all。There go。嗯。Yeah。

 so this lets us basically parse out a U16 from bytes in oh native endness。That's not what I want。

 I want LE。

![](img/e709d71a082b45418e3b70befbd3ce3f_33.png)

Because network， what is network I can never remember。



![](img/e709d71a082b45418e3b70befbd3ce3f_35.png)

Big N DN is network。 Okay， right。 So what we want is from B bytes。

So flags is going be a is going to be U 16 from B E bytes。 I this on beta。Probably isn't is it？

Oh yes。From the Bs。And this is gonna be above 0， above 1。And then what was the next thing？



![](img/e709d71a082b45418e3b70befbd3ce3f_37.png)

嗯。Where are we here。

![](img/e709d71a082b45418e3b70befbd3ce3f_39.png)

Proto。This is gonna be 2 and 3。 and this is gonna be。For and onwards。2。All right。

 we need to do some cleanup here。What's the bash term。



![](img/e709d71a082b45418e3b70befbd3ce3f_41.png)

The inline warnings is something that recently landed in Russ in the。Neovim language client。

 it's actually a little bit annoying because the default styling is pretty terrible。Nture term。

Capture kill。Sの。Trap， that's what I want。Specifically， I want。Chi。T。I basically want the。

 I want to terminate the program normally when you do a control C。um。

Can never remember what the syntax is for this。

![](img/e709d71a082b45418e3b70befbd3ce3f_43.png)

Gonna be killed。And we're going to kill this， so it turns down this。

 and then we're going to run it again。Inval signal specification。That's interesting。Oh。That's right。

Oh man， didn't tear it down。嗯。Well， that's obviously not working。



![](img/e709d71a082b45418e3b70befbd3ce3f_45.png)

Isn't there a way to like， do nicer traps， I can never remember how this actually works。Sig term。



![](img/e709d71a082b45418e3b70befbd3ce3f_47.png)

I thought it was just kill Pi。 I thought that was all you needed。Oh。

 maybe I need this needs to be bashed， doesn't it？Yeah， okay。Great。Okay。

 so now runs H is gonna when we kill it， it's also gonna to kill the underlying program。

 And crucially， in theory， now we're going get， we're gonna parse out flags and proto and we're going print them here。

 flags。Proto。Bs proto。Okay， so proto 8，6 D D。

![](img/e709d71a082b45418e3b70befbd3ce3f_49.png)

嗯。So I guess we're going to have to figure out what these different protocols are。Where is the。これが。

That's unhelpful。I think it's from the IP frame。

![](img/e709d71a082b45418e3b70befbd3ce3f_51.png)

IP protocol numbers。

![](img/e709d71a082b45418e3b70befbd3ce3f_53.png)

Hm。What did we get？Purtos 8，6 DD。Either type。So 86 DD is an IPV6 packet， right？



![](img/e709d71a082b45418e3b70befbd3ce3f_55.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_56.png)

And my guess is， if we start doing pings。Then now we're getting things that have protocol 0。

 this is 0，8，0，0 and 0，80，0 is IPV4。 And so the first thing we're going to do is ignore any packet that is not an IP before packet。



![](img/e709d71a082b45418e3b70befbd3ce3f_58.png)

Right， so that's gonna just tidy up our stream a little so。嗯。If proto not equal to。This continue。

So at this point now， notice there's nothing printed when we first started because those packets went away。

And indeed， if we now start pinging， those packets do， in fact， show up。Okay。

 now we've parsed out the beginnings and what now follows is an IP V4 header and so what we're going to do is we basically have to encode this structure the IPV4 header in our rust code somehow。

 I wonder if someone has already done this to save us the work。



![](img/e709d71a082b45418e3b70befbd3ce3f_60.png)

呃。IPV4 networkstructs。Seems great。Mmhm。IV4 header。Great。That seems fine。 Let's use that。 The reason。

 the reason I'm using a package for parsing I P is because it's not really what we're focusing on。

 So there's no reason for us to really redo that work。 Ether parse is 0，8。



![](img/e709d71a082b45418e3b70befbd3ce3f_62.png)

And in Maine， here， we're going do。呃。This is going to be ether parse。IPV 4 header slice。From slice。嗯。

offff。

![](img/e709d71a082b45418e3b70befbd3ce3f_64.png)

4our to n bys。And if this errors in some way， then we don't really care， right。

 That just means we're going to skip the packet。 And so we're going to do a match on this。



![](img/e709d71a082b45418e3b70befbd3ce3f_66.png)

And if it's a packet， then we do whatever we want with a packet， and if it's an error。

 then we're just going to ignore that packet。Ignoring packet。We already packet it。And then here。

 what we're going to do is print out the packet instead of the buffer。

And now let's see what that gives us。All right， let's see what now happens if we do some pinging。

Okay， so now we're getting， oh I guess the slice isn't really helpful。

 but it at least it parsed it correctly， right， So that's pretty promising。

 So let's now have it instead of just do that， let's try to actually print out some stuff。

 particular， what we probably care about from the I packet are things like the total length of the payload So instead of all of the stuff we've done so far。

 we're gonna do。

![](img/e709d71a082b45418e3b70befbd3ce3f_68.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_69.png)

Got IPV4 packet。Bys of IP4 packet payload。And that's going to be what P dot payload lend。



![](img/e709d71a082b45418e3b70befbd3ce3f_71.png)

嗯。What else do we want？I think we're probably going to ignore all these other fields。

But protocol we're going to care about， we're probably also going to care about source and destination。

So we're going to do source is going to be P dot source adder。



![](img/e709d71a082b45418e3b70befbd3ce3f_73.png)

嗯。And destination is going to P destination at her， and what else do we have？



![](img/e709d71a082b45418e3b70befbd3ce3f_75.png)

呃。

![](img/e709d71a082b45418e3b70befbd3ce3f_77.png)

Protocol。And notice that this protocol is different from the other protocol。

 so the protocol we get up here， these are for the ethernet frame that we got and so this is sort of set by the link level protocol。

And that we're not really going to care about down here。Oops， radio。This on the other end。

 is the IP level protocol which should be set to TCP。嗯。So in fact。

 let's print this out in a similar format to this， right？Just so we。

So this is going to be the source。The destination。Protocol。So I guess this is going to be。By it's。

Protocol this。This is going to be source， destination， Proto， and that。

So let's see what this gives us。Is there a way to deb that N and plugin。

 So it isn't checking after every new character。 I don't know。 I really want that。 And I。

 I haven't looked into it enough。 It's a fairly new feature， but it， it's really annoying。

You probably need time to live。 Yeah， I'm just going to assume that it's fine。 Like。

 there are things that we should do that we're not going to do。嗯。Yeah， it's really。

 really distracting while typing。The macroos we don't actually need because we're at the the data link layer。

 sort of the IP layer。 we so we don't need anything like ethernet frames。

 all we need to know is where to like respond to the packets。This is failing for some reason， though。

Why is it failing？Don't think it should be failing。Great， so now if we've ping， what's going to do。

 Great。 So we got one by of protocol 64。 Okay， so time to look up the protocol。 So 64。😊。



![](img/e709d71a082b45418e3b70befbd3ce3f_79.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_80.png)

Ooh， that doesn't look great。Protoical。😔，Oh， are we printing this in Hex。

We're not printing this in Hex。😔，But how about we print it in Hex instead。

Also let's get rid of these warnings。Don't need this。And don't need this。



![](img/e709d71a082b45418e3b70befbd3ce3f_82.png)

Protocol 0 x 40。 So IP protocols。

![](img/e709d71a082b45418e3b70befbd3ce3f_84.png)

Oh， am I printing these in reverse order？Oh， you're right。 Wow， yes。That is the pale of length。

 this is the protocol， okay， better。

![](img/e709d71a082b45418e3b70befbd3ce3f_86.png)

So now if you ping protocol 1 and Pro1 is indeed the ping protocol， Okay， great。

 thanks for catching that。

![](img/e709d71a082b45418e3b70befbd3ce3f_88.png)

Yeah， so now at least we know that we're getting our IP packets and we know that whatever is left the sort of TCP。

 So the question now is what happens if I try to connect using a TCP client to whatever port is not important。

 So I'm gonna try to do that。 Okay， so it' got 40 Bs of protocol 6。 Pro 6 is TCP。 Okay。

 so we got a TCP packet of some kind。 and we got 40 Bte of it。

 So this is where we really need to start getting into what are we going to do at this level。

 one thing we also have to decide is whether we are going to implement the the。

Pack it parsing ourselves or whether we're not。嗯。So this is actually sort of up to you。



![](img/e709d71a082b45418e3b70befbd3ce3f_90.png)

There's a lot of stuff in TCP。 and most of it is not about parsing， right， Like parsing。

 the TCP header is not particularly。Is not the core part of the TCB protocol。

 but it is a bunch of like bit fidling。 Ether， I think the ether pars。

Thing also supports TCP headers。So we can use this to do the parsing for us that way we don't have to spend a bunch of time doing the bit fiddling。

 but I'm also happy to do that So would you prefer to see me start working on like the TCP protocol side or do you want to also do the TCP header parsing。

😊，What would you prefer to see？

![](img/e709d71a082b45418e3b70befbd3ce3f_92.png)

To give an idea。If I stop this for a second。If proto not equal to006。呃。Just while you're thinking。

 I'll write up the the one that uses ether parts。

![](img/e709d71a082b45418e3b70befbd3ce3f_94.png)

呃。Is。 He Ly here， I wonder？

![](img/e709d71a082b45418e3b70befbd3ce3f_96.png)

So this parsing is just the same as the IP parsing I did above。



![](img/e709d71a082b45418e3b70befbd3ce3f_98.png)

I guess。

![](img/e709d71a082b45418e3b70befbd3ce3f_100.png)

You should be to port this。I I guess that's gonna be。



![](img/e709d71a082b45418e3b70befbd3ce3f_102.png)

P do。S way for me to get the length from this， I wonder。好。



![](img/e709d71a082b45418e3b70befbd3ce3f_104.png)

It's interesting。I guess starts。It's gonna be P。slices dot L and P dot Dsin。Destination。嗯。Letxii。😔。

Protocol， I think， I'd prefer to not see parsing just a protocol， parse protocol protocol。

Skip parsing， parsing might be interesting protocol。Skip parsing。 Okay。

 so it sounds like protocol then great。 So we'll just do the protocol。 So I've now done the parsing。

 This is why the parsing is nice to skip， basically because Ether parsel is the parsing for you。😊。

If you're curious about like low level parsing， I would look at the source of ether parse。

 it's mostly just like reading out so you have you have a byte string right and then you do things like this sort of U 16 from B bytes U8 from B bytes you just like read out the different fields according to what the specification says that the header formatting is you get out the fields and then you sort of parse them in the appropriate way。

And my guess is， if you read the EtherR source code。

 that is all it does when you use this from slice business。Why has this stopped falling very？

All right。So if I now run this， what happens Oh， I need to type my password apparently。Cin。😔。

All right， so now this is running。Oh， eventually we're gonna to need all the fields of the TCP header。

 I just didn't particularly care about printing it right now。

 So let's now try to first let try to ping。 You'll notice that nothing gets printed because we notice that it's not a TCP packet。

And then if we try to send a TCP connection， you'll say we get 40 B of TCP to port 80。 right。

 If I stop this and say 4，4，3 instead， it's going to say 40 B of TCP to port 4，4，3。Okay。

 so at this point， we are receiving TCP packets。And so now the question is， what do we do with them。

 right？ So at this point， now we sort of need know that there's some。

 there's something going on here。 And so now we need to figure out what we're going to do sort of in order to implement the protocol。

The thing to keep in mind is that in TCP， a connection is or in in well， everywhere。

 a connection is basically a a quad of。Source IP。Source port。

Destination IP P and destinationation port。Oh man， these warnings are so annoying。

 What's the thing for turning them on again？Sorry， I just need to。

Didn't I have fix this at some point。Thought I did。Apparently， not。All right， well。

New of M language client。

![](img/e709d71a082b45418e3b70befbd3ce3f_106.png)

I could write it as comments， I just don't want this feature to be on like ever。

 it's far too annoying the way it currently is。Vual text。This how do I turn this off。



![](img/e709d71a082b45418e3b70befbd3ce3f_108.png)

This。Excellent。It's gone。Beautiful， I can still put in in comment， though。

 So we basically want this quad like this。 This identifies a single connection。

 And any time you run sort of the TCP protocol， you basically want to run it on this quad。

 Like all the state is associated with that quad。😊，And so what we're， what we sort of need is。

 is almost like a map from this quad to the state for that connection。 right。

 So we're gonna end up constructing something like。TCP state。

And that's going to contain a bunch of fields。 And then we're gonna have something like connections。

 which is gonna be a hash map。嗯。Well， actually， let's make it default。

This is going to be a hash map from a quad to a TCP state。And a quad is going to be。A source IP。

I guess actually we could。呃。Oh， I will。 I'm not gonna。

 I don't think you should generally use this for anything。 No。

 this is building more because it's interesting， not because we're gonna use it for anything。

 So the source is gonna be a， I guess this， at this point。

 we need to figure out what this return type is for the。



![](img/e709d71a082b45418e3b70befbd3ce3f_110.png)

It's a TC。 it's what。Where's the source seter， IPV4 adder， which comes from standard net。



![](img/e709d71a082b45418e3b70befbd3ce3f_112.png)

So， we're going to use。Standard net IP PV4 adder。IPV4 adder and EUU 16 right so this is source IP and port and destination IP import port。

This， of course， we're going to derive like all the things for。 So the hash， eek and partialial leak。

And probably also debug。And probably also clone and copy。嗯。

So we're going to keep this sort of connection state and that's going to be from one of these to whatever we end up putting in the TCP state。

And just to make our lives easier， we're probably going to do a mod TCP。TCP。t RRS。

 and that's going to have this。So this is going to be a。TCP state。And so the question is。

 what do we do when we get a TCP packet Well， in all likelihood。

 what we're going to do is we're going to do connections， do entry， quad。

which is going to be the source is going to be the source address and the P source port。

And the destination is going to be the destination address and the destination port。嗯。

And the question is， what do we do if there is no connection well？We probably want or default。

 like there's gonna be some， it's gonna to be some default state that every connection starts up in。

um。And then。What this， so the dot entry API is really nice because what it will do is basically if there's already something with that quad is going to give us a reference to that thing to the the corresponding state。

 And if not， it's going to create one for us and then give us a reference to that。

 So what we end up with after this or default is basically。Is basically a。always。

 what we end up with is a mutable reference to a state。 And so at this point。

 we're going to say something like。On packet。And we're going to give it the P。

And we're going to give it。Actually， that's a good question。



![](img/e709d71a082b45418e3b70befbd3ce3f_114.png)

Why is there no way for me on this？To get out。

![](img/e709d71a082b45418e3b70befbd3ce3f_116.png)

Right， data offset is the one。So P is the header and then in addition we want where does the data start Well。

 the data starts at4 plus how far the number of 32 bit words in the TCP header， right？



![](img/e709d71a082b45418e3b70befbd3ce3f_118.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_119.png)

So actually， that's not even true。So the I header size is P dotslic dot L。



![](img/e709d71a082b45418e3b70befbd3ce3f_121.png)

Ooh， actually， this slice。

![](img/e709d71a082b45418e3b70befbd3ce3f_123.png)

That's even better。So the data starts at the IP hetero size。Plus the TCP hetero size。

TCP heterosyis is that last value。Actually， how about we don't overwrite these and say this is I。呃。

This is the I header。And this， we can just inline just to make the code easier to read。

That way here we can use IPh。slice。len。I P H dot slice dot L。

 this is give us going to give us a TCP header。Instead of just P， TCP header。TCP header。

It should just support。Alright， so on packet， we're going to give it the I header。

 the TCP header and also the， the slice of the payload， which in our case， is then buff from。

Let's give this a helpful name。 data I from data I to the rest of Buff， right。

 So from the point where the headers stop and the rest of the buffer is the contents of the packet。

And that's sort of the end of what mainine has to do， right。

 there's going be there's going to have to be some way to like send responses and who knows how that's going to work there's going to be timers and stuff involved。

 but at sort of the heart of it， this is the way packets get into the TCP state。Okay。

 so now we need to actually implement that， right， So we're gonna have to implement default for state。

And we don't quite know what that looks like yet。We're also going to have to impulse state and have something like a。

On packet， that takes。A an I P header， which is going to be was an ether parse IPV4 header。

 a TCP header， which is going to be an ether parse TC P。These are actually。

 this is IPV4 header slice。 This is TCP header slice and data。

Which is going to be just a bunch of bytes。And we don't really know what we're gonna do in there。

 But for the time being， we're sort of just gonna。Print this out。I dot。Source outer。IPH。

Destination ater。呃。Now we're going to， I guess just show the ports numbers directly in here。嗯。

And so it's going to be source adder than TCP header source port。And then the same but destination。

And then finally， we're going to give data do lend。This is mostly just a tidy up our interface。

 right， I probably did something stupid didn't。嗯。An inner。 Oh， I have messed up， don't I。

This should not be that。And this should be pub。Well， crate， but whatever， they're the same。Actually。

 I also want my run script to。If compilation fails， I don't want it to run anything。呃。What。

Why does compiling。This makes no sense。Oh， that's not what I wanted。This is what I wanted。Great。嗯。

All right， let's see what else no method on packet found， that's because this has to take me itself。

Right， and the， the lifetime ticket here is the lifetime of the， basically of the packet itself。嗯。

Which is basically the lifetime of this buffer， right？Alright， so now this runs and again。

 if we ping， nothing shows up because we're filtering those， if we try to connect to a given port。

 it's going to say，ooh， we gotta buttonooh， that looks wrong。No， actually that might be right。

So this is saying that the body of that request is。1440 B。 That doesn't seem right。Oh。

 the data is until n bytes， of course。嗯。This also is and bys。Becauseuse remember。

 when we fill up buff， we only actually like Buff is this long， but we only read this many bytes。

 So we should only be looking at that many bytes。 So let's try that again。 Now， if we do this0 bytes。

 right， So the first packet we get is basically a header only packet。 It contains no payload。Great。

 but this at least means that the math sort of worked out。So what this first packet is， in fact。

 if we lets start this again， if we start our our T shark and then do this。

 you'll notice that that message if I can kill them again is and let's also kill this and also kill this this packet that got sent is a sin packet and it has a bunch of like header fields And so the question is what do we do in response to that。

 Well， this is basically the first part of the TCP handshake and there's a pretty decent description of that in。



![](img/e709d71a082b45418e3b70befbd3ce3f_125.png)

don't want this， don't want this， don't want this。These go away。This goes away。

So this is when it starts to be time for the RFC。There's a。Operation is not what they do it。

 It's a diagram somewhere in this document， but I can never remember where it is。啊。

I think it's down here。😔，Arguably， I could just scroll through。Yeah。

 so this is the stuff that we no longer have to parse because Ether parson does it for you。嗯。

But where's the thing that shows the state。Oh yeah， there's a。

 there's a lot of stuff we're going to have to get to here。 Okay。

 so this is the diagram I'm thinking about。 So this is the TCP connection state diagram。

 And so we're basically going have to implement all of these states。 initially。

 when you start out a new。嗯。没有。So there are two states。 A socket can sort of。

 or a TCP connection can start out it It can even start in the here。

 I think they specify further up too。Yeah， so there are a bunch of different states that a connection can be in。

 There are these states。And TCB here is sort of the TCP state。And so that is。

 there is no connection currently。So that's what this closed here is。

And so the idea here is that if you're closed。 So if you're not expecting to get any connections。

 like there's no state for a given connection， then like， even if someone tries to connect to you。

 you're not gonna reply， right， If you're not listening on a given port， you're not going to reply。

Whereas if you're in a listen state and someone tries to connect you， then you are going to reply。

 So what we're doing here， actually， if you look at the the code up here。

 this sort of on packet here， we're saying that if someone senses a packet。

 if we haven't talked to them before， we're just always going to answer them， right。

 or we're always going to deal with that packet。 Now， that might not be the thing that we want to do。



![](img/e709d71a082b45418e3b70befbd3ce3f_127.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_128.png)

In particular， this means that basically every port is listening and this might not be reasonable going down the line。

 but for now let's just like stick with us like if someone tries to connect with us。

 we're just going to respond， yep， we're here and so we're going to ignore this close state and basically assume that every every port is going to be listening。

嗯。So if you notice that listen， there are a couple of different things we can do。

 We can either receive a sin。IfSo this is you should read this as if this happens， then we do this。

So if we receive a sin， so as sin as this is the first part of the handshake。

 then what we send is an act， which is an acknowledgement of the sin and a sin because we want to establish a connection the other way。

 So the handshake establishes a two way connection in TCP So this is the other person reaching out saying。

 hey， I want to talk to you do you want to talk to me and this is saying yes。

 I want to talk to you do you want to talk to me？At this point。

 we sort of note that we're in the state of we have received the sin from the other side。

 And at this point， one of two things can happen。 Either the connection can be closed。

 in which case we just like terminate the connection or we receive a。No， here。

 or we receive an act of the sin that we sent， in which case we don't send anything。

 but now the connection has been established。 So this is sort of the initial TCP handshake。

And so getting through the flow from here to here to here is basically how you do a server right So this is how you receive connections。

 On the other hand， if we wanted our library to establish a connection。

 it would start out encloed and then it would do an open。Which creates the state for the connection。

 And then it sends a sin。So this is sort of the opposite end of this receiving a sin。

Confession is fun。 Yeah， so， so if you're a client。

 you're going go through this path of sending a sin to the server and then being in the state S sent。

 at that point， hopefully you're going to So if you receive a sin from the server。

 it means the server was trying to connect to you at the same time。 in which case， you can just act。

 and then everything proceeds normal。 But in the common case， you send the sin。

 and you receive a syn act。 This is the syn act that the server sent here。

 at that point you're gonna to send an act to the server saying is。

 I do indeed want to talk to you at which point the connection is established。

 You might wonder why you need this like twoway acknowledgecment。

 and there are many reasons for that。 The primary one is to make sure that the hosts are actually talking to one another that does not。

😊，Sort of some other host in between that's trying to do weird things。

 We're not gonna get too much into the weeds of exactly why the protocol works the way we are。

 We're sort of gonna naively implement this as if it were the what，19。81。Sound good。

We're going to assume that the internet is a safe place。And so as you can see。

 there are sort of two different paths here for whether you're a server or a client。

 but as far as TCP is concerned， it doesn't really matter。

 All that matters is how you end up using that state。

 So I think what we're going to do is we're going do the sort of TCP server part first。

 and then we can implement the client part later。 The client part is what we're gonna end up using for talking to other servers online。



![](img/e709d71a082b45418e3b70befbd3ce3f_130.png)

What happens if the final act from the client has dropped somewhere a so there are all sorts of ways for this protocol to be weird。

 basically there are a lot of timeouts in this protocol of things like you try to resend if you don't hear back we'll get into all of that sort of dealing with retransmissions as we get later。



![](img/e709d71a082b45418e3b70befbd3ce3f_132.png)

嗯。But in general， TCP assumes that either you will receive an act eventually or the connection is eventually going to time out and close or it just stays open forever。



![](img/e709d71a082b45418e3b70befbd3ce3f_134.png)

Okay， so in this case， all we're doing is receiving a packet and this。

 this diagram gives us a pretty good idea of what we probably want to do。

 specifically what we probably want to do is have this be an enum。



![](img/e709d71a082b45418e3b70befbd3ce3f_136.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_137.png)

Right， we we sort of want to encode the state diagram， and the default state is going to be closed。

Now， this does mean that we're still going to sort of create an entry here for things that are closed。

 and we might want to sort of prune those like there's no reason to keep this around if it's closed。

 but it's it's a good way to start to approximate the diagram。 when we're closed。

 we're also going to be able to go into listen mode。 and in fact。

 what we're going to do for the time being。 So this is going to be state closed。 but。Starting out。

 we're going to say that we're always going to listen on all ports。

The other things we're going to need are。

![](img/e709d71a082b45418e3b70befbd3ce3f_139.png)

嗯。Soon received。

![](img/e709d71a082b45418e3b70befbd3ce3f_141.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_142.png)

I guess name these the same as in there。And we're also going to need established。



![](img/e709d71a082b45418e3b70befbd3ce3f_144.png)

And let's just like stick with those for now。 There's a bunch of state we're gonna have to keep for these two。

 But let's sort of start out in the very simple case of if we receive a packet。If。

It sort of depends what state we're in。嗯。So if we are in state closed。

Then all we're going to do is return。It's nothing more for us to do。If for in state， listen。



![](img/e709d71a082b45418e3b70befbd3ce3f_146.png)

Then the only packets we expect to get in state Listen is a packet that has a sin set。



![](img/e709d71a082b45418e3b70befbd3ce3f_148.png)

That is the only thing we're expecting to get。And so if TCPH dot sin。So if the sin bit is set。Sorry。

 or the other way around。 if sin is not set。Then。I guess here we could do some logging and stuff。

 but here got unexpected。Sin only expected sin packet。So in this case， two， we just return。Right。



![](img/e709d71a082b45418e3b70befbd3ce3f_150.png)

Otherwise， though， if we go down here， we got a sin。

 And now we need to start establishing a connection。



![](img/e709d71a082b45418e3b70befbd3ce3f_152.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_153.png)

And so what that means is we're going to have to parse out the stuff from that syn packet and then we're going to have to send this S act。



![](img/e709d71a082b45418e3b70befbd3ce3f_155.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_156.png)

Okay， so we need to cook up a message that's going to be the response we send。 And here， too。

 like we're basically cooking up a TCP header。 And so for that。

 we can we might as well just sort of reuse this the ether parts because they also have。

Sort of the opposite of a TCP header。Now， here。

![](img/e709d71a082b45418e3b70befbd3ce3f_158.png)

It's a little awkward。 This is going to need some way to send a message。 So I think on packet。

There's going to have to be some way for it to know how to send packets again。

 But let's just construct the packet in the first place。 Okay。

 so we're going to have to create one of these。So we're going to send a synac。



![](img/e709d71a082b45418e3b70befbd3ce3f_160.png)

And in order to do that， we're going to have to set all of these question is how can we create one？



![](img/e709d71a082b45418e3b70befbd3ce3f_162.png)

Newu， great。So we're going to do new。And it's going to go in the opposite direction right So we received a synAC from someone else and now we need to respond to them。

 So when it says source port， that's going to be the destination port of the packet we received。

That's where we're sending from， the destination port is going to be the source port of the packet we received。

The sequence number we don't know yet， and the window size we don't know yet。

 we'll have to figure out what those are。

![](img/e709d71a082b45418e3b70befbd3ce3f_164.png)

Then we're going to have to specifically， again， we're going to read the RF more closely。

 but specifically we're going to have to set sin and set act。



![](img/e709d71a082b45418e3b70befbd3ce3f_166.png)

Because we're sin is going to be true。

![](img/e709d71a082b45418e3b70befbd3ce3f_168.png)

An act is going to be true。

![](img/e709d71a082b45418e3b70befbd3ce3f_170.png)

So we're acting their sin and we're also sending our own sin。



![](img/e709d71a082b45418e3b70befbd3ce3f_172.png)

And then we're going to have to wrap that in IP packet because we're sending it back to them right。

 and so in order to do that。We're going to end up creating an IPV4 header。



![](img/e709d71a082b45418e3b70befbd3ce3f_174.png)

So。Thiss going to be either pars， IPV4 header new payload L is going to be。



![](img/e709d71a082b45418e3b70befbd3ce3f_176.png)

Sunak dot slice dot L。Time to live。64。Protocol，oo。It's going to be TCP。What else do we need？



![](img/e709d71a082b45418e3b70befbd3ce3f_178.png)

Source and destination。Okay， so the source is going to be the IP PH dot。



![](img/e709d71a082b45418e3b70befbd3ce3f_180.png)

Destination， right， so we're responding， so we have to invert them， so if we're giving source。

 then that has to be destination address。

![](img/e709d71a082b45418e3b70befbd3ce3f_182.png)

And similarly。The destination is going to be the source address。So that。



![](img/e709d71a082b45418e3b70befbd3ce3f_184.png)

And then ultimately， we're going to have to send these packets out。



![](img/e709d71a082b45418e3b70befbd3ce3f_186.png)

Ohh， that's a lot of things。Shouldn't be one for syn act。Yeah， so okay。

 so there are a couple of questions in chat。 The first one is shouldn't it be one。 Oh yeah。

 these parameters are going to be set to something， they're not just going to be zero。

 I just haven't done it yet。 And it is totally true that as you've already observed we're keeping state for every connection And so in theory。

 you can make the server do a lot of work with doing very little work yourself and this is often known as a sin floodoo attack and it's something that's modern kernels are actually pretty defended against because what they'll do is they won't actually set up any state locally。

 they won't allocate any state locally until the connection is actually established。

And so there are defenses against this。 we're just not going to care about them right now because they complicate the implementation。

嗯。So you're totally right that this is a problem in sort of real implementations。Okay， so we've。

 we've constructed this packet。 Theres still some things that we don't know， like。

What is this going to be， What is this going to be。And also。

 how are you going to write out this packet， right， Like， there has to be some way for。

For us to sort of send a reply here where this is going to get particularly tricky as was。

 as when it comes to being able to send。U beinging able to send packets， like if there's a timeout。

 for example， that we're waiting for。And I don't have a good idea for how to do that。

 I think what we're going to do for the time being。



![](img/e709d71a082b45418e3b70befbd3ce3f_188.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_189.png)

Is just to give this guy a writer。Specifically， it's going to end up with something like an eye face。

Now， of course， this is its own kind of stupid because ultimately we're gonna want to， for example。

 have， we're gonna want to be able to send packets even if this is not active。 But let's just。

 for now， we're just gonna give it a mutable reference to the I phase。

 which is we're gonna call Nick。And what this means that is that we can send packets ourselves。

 right， just by writing out this ni。呃。Buff is going to be a。1500 U 8。I guess zero， you eight。と。嗯。Now。

 this is also not not what is referred to as zero copy。

 Often you want the kernel to not you don't want to not have to write things into memory more than once。

 We're gonna ignore that as a concern。 So this will not be highly performant。 but it should be fine。

 So at this point， what we want to do is sort of write in the IP header。

 then the TCP header and then any payload that we have。 I guess here we're gonna do something like。

Written is zero。So we're going to do。I P dot right。Ooh。

 what's the difference between right and right raw？



![](img/e709d71a082b45418e3b70befbd3ce3f_191.png)

I wonder。

![](img/e709d71a082b45418e3b70befbd3ce3f_193.png)

Interesting。I think right is what we want。

![](img/e709d71a082b45418e3b70befbd3ce3f_195.png)

What is it that implements right again for like things that are slices。嗯。

For mutable references to you 8。The writing update is nice to point to the yet unwritten part。



![](img/e709d71a082b45418e3b70befbd3ce3f_197.png)

Yeah， so。Here， we're going to have。H。呃。Unwritten。Is gonna be a mute to buff to the entire buff。

And then we're going to write into unwritten。

![](img/e709d71a082b45418e3b70befbd3ce3f_199.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_200.png)

嗯。And then yeah， and then when also the S act is going to be written to unwritten。



![](img/e709d71a082b45418e3b70befbd3ce3f_202.png)

And the payload is going to be empty。And then at this point。

 we're going to write out the actual packet using sendend。



![](img/e709d71a082b45418e3b70befbd3ce3f_204.png)

Right so we're going to do。Nick dot send。 And that takes basically a buffer。

 And that buffer is going to be buff。Oh， I don't know how that's gonna work。to be this， I think。嗯。

Written is gonna be。Let's see how much have you rewritten， We've written。呃。Well。

Unwritten is going to be this。And so we're going to write up until unwritten。Right。

 so this might seem a little weird， but。Out the headers， we construct the headers。

 then we write those headers into Buff。 and what this trick is going to do is basically we create a slice the point to the entire buffer and every time the a header gets written。

 the start of that buffer gets moved。 And so this line down here is how much is remaining in that buffer。

 how much space is remaining and however much space is remaining is how much we haven't written。

which means that the stuff we have written is everything up to that point。

 which is what this is doing。And I guess this means that on packet is going to have to return an IO results。

um。I guess maybe u size。I'm clear that it matters。And I guess we're going to have to use standard Io。

Let's see whether this makes any sense。We're going to need prelude。Probably。I right is not。

Implemented for you，8。Where is it saying that？Okay， there are a couple of issues。 First。

 this expects a U8 of size 4。

![](img/e709d71a082b45418e3b70befbd3ce3f_206.png)

Which is not worth we're giving it。

![](img/e709d71a082b45418e3b70befbd3ce3f_208.png)

I guess this is going to have to be destination and this is going to have to be source。

It's probably still going to complain about that。嗯。Specifically。

 I wonder whether we're going to have to do like。This。It is a little awkward。But， maybe。

And this is going to be。Source， source， source。

![](img/e709d71a082b45418e3b70befbd3ce3f_210.png)

Nothing found for IPV4 header。This， we're going to have to use。



![](img/e709d71a082b45418e3b70befbd3ce3f_212.png)

Hotal。稳。All right， what else was this complaining about？This and also this。Now。

 what is he complaining about？I complain in Maine about this， that's fine。It's now a question mark。

It takes four parameters， but three were supplied， that's because we also need to give it now the network interface so that I can send additional things。

Okay， what else do we have？呃。Spected， mutable reference。Oh， this should come first。

You could use inner chunks to get that slice from destination source。Is that true？Oh。

 cause there's like a fixed size chunks thing now，Chunks。Chunk's， exact。I think is the one。

 but I don't know if it gives you that， I think it just gives you an iterator。U。

Where is the implementation of。Implementation of bitter。 Yeah， it still gives you a slice。

So it doesn't give you a Uuphor。W is what we need。TCP line 29。Oh， this is okay，0。This is okay，0。



![](img/e709d71a082b45418e3b70befbd3ce3f_214.png)

No total lens found for TCP header。

![](img/e709d71a082b45418e3b70befbd3ce3f_216.png)

ItBecause it's just。Tedtter Le is what we want。Because there's no payload。

What else is it complaining about？The size for values of type U8 cannot be found。嗯。Maybe it's this。

We don't need。These we haven't done anything with yet， so they're unused。Alright。

 so now we have something that's sort of running。 And in theory。

 it's going to write back the appropriate act。 So let's start up our T shark。

And then let's try to connect on a port and see what happens。 Well， something crashed， not yet。 Oh。

 it'sca。It's not terribly surprising。 Okay， so we haven't actually figured out what we want to set these for。

 This is why unimplemented is nice。 So when we try to create this， we need to set a sequence number。

 we need to set a window size。 And in order to understand what these are。

 we need to actually read the RF。

![](img/e709d71a082b45418e3b70befbd3ce3f_218.png)

嗯。So the place to start for this。I。u。Where do we want to start for this？No， no。No。Nope， no， no， no。

 nope， no。No。Here， okay， so header format， that's fine。

 Here is where we're going to need to actually start reading and talk about what some of these fields mean。

 Just give me a second。 I need to get some water。Okay， so。

Let's look at what actually is in a TCP header。 There's a source and destination Port Weaiver already talked about。

 and there's a sequence number an acknowledgement number。And there's a bunch of stuff down here。

 let's talk about these two because they're relatively important for how the protocol works。

And the protocol is pretty good at describing how they work。

So the sequence number is the first dataoced in this segment。So specifically。

 it is sort of the index in the data stream。Of the first data part of that segment。

 and you can sort of think of a sin as a bite of its own。RightSo if sin is present。

 the sequence number is the initial sequence number， which we're going get back to。

 and the first dataoct as one beyond that。 So the sin sort of counts as the first byte。And the。

 the acknowledgeknowgment number is the value of the next sequence number that the sender is expecting to receive。

So there's a diagram further down that makes this a little bit easier to follow。Where is it？Here。😔。

Yes， so this， the， this statement is basically entirely correct in order to understand TP。

 like you just need to understand sequence numbers of acknowledgement。 There are。

 there are a bunch of variables that need to be stored and。They're sort of stored。

Almost no matter what state you're in。

![](img/e709d71a082b45418e3b70befbd3ce3f_220.png)

And so what we're going to probably have to do is basically have a struck TCB。

 So this is what they call a transmission control block。

 This is sort the state that has to be kept for every connection。



![](img/e709d71a082b45418e3b70befbd3ce3f_222.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_223.png)

嗯。And TCB is going to contain the fields that we give down here。

 And my guess is that we actually want。Here's probably what we want State。

 that's going to have to contain these fields。And in addition， it's gonna contain something like。

Well， I sort of want to call it stated， but。Let's make this connection。

So instead of calling me the state， it's going to be connection。嗯。And this is going to hold a state。

So this is the state that that connection is in。嗯。So， this is going to be。



![](img/e709d71a082b45418e3b70befbd3ce3f_225.png)

For now， we're just keeping that。But let's look at what is in the TC B。

 Among them are things like soccercket numbers。 we can ignore that。

Precintence and security we can ignore for now and then pointers to receive buffers we don't particularly care about yet。

 retransmit cues in the current segment。 This basically has to do with TCPs intended to provide reliable transports or reliable sends and receives across an unreliable connection so the internet is prone to just like randomly dropping your packets or rearranging them。

 which means that sometimes TCP is told like hey， I never receive that packet and it needs to send them again。

 which means that TCP actually needs to keep a queue of things that it has tried to send in the past so that it can remember to send them again。

嗯。And this is what's known as the TCP。This is what's known as the TCP Retransmit queue。嗯。

And so the way to sort of think about this is we're going to keep all the bytes that the user wants us to write。

 and then we're sort of going to remove them as needed。

 so we're sort of going to keep a buffer of everything we've tried to write。U。In addition。

 there are a bunch of variables that are related to the send and receive sequence numbers that are stored in the TCP。

There's a diagram down here that we're probably going to spend a bunch of time looking at。

 so it's useful to spend some time。The send sequence space is basically the bytes of data that we have sent。

嗯。And there are a couple of points in that data stream。 So send dot U A is what we have sent。

 but that has not been acknowledged。Send next is where we're going to send from the next time we send。

Send dot window is how much we're allowed to send so TCP has this notion of as a receiver you can sort of limit how much your sender is allowed to send so that they don't overwhelm you with traffic and so the how much we're allowed to send is the last point that was acknowledged plus the size of that window so sendenddot next can never go beyond sorry we can never send bys beyond this boundary even though we might have them locally we're not allowed to send them yet。

呃。And these are used for updating windows which are going to change in all sorts of ways。

 There's also a notion of an initial sequence number。

 The initial sequence number is what we choose when we started the connection that doesn't have to be zero。

 So basically you can think of this as we don't have to name the very first byte as one。Right。

Like we don't have to start counting at one as long as both sides of the stream know。

 know what we call 0， right， And similarly， we keep a similar sort of values for the receive buffer。

 specifically， we keep track of。Where。What we are expecting to be the next byte we receive and the window for receiving and also the sequence number that the other side has counting as zero。

RightSo this is why these segments are labeled， so everything that's in once so everything before this line is data that has old sequence numbers that have been acknowledged。

 two is sequence numbers that we have sent， but that the other side is not yet said that they have。

3 is so everything between here and here is sequence numbers that we're allowed to use in some sense。

 right， because this is the first bit of data we haven't sent and we're allowed to send up to this much right。

 like a window more than where we got acknowledged and so all of this werere allowed to send if we if the user gives us data and four is stuff we're not yet allowed to send。

嗯。And so three is referred to as the send window， this is where we're allowed to send。

And the receive space is sort of similar in that everything before received dot next is stuff that we have received from the other side。

And we like we were're sort of done with that。 We've passed it to the user space。

 hopefully or we're about to， but it's like nothing。 this is just data that we have received。

2 is sequence numbers that the other side is still allowed to send us。

 So it's within the window that we have announced to them。

 And three is stuff that they're not allowed to use those sequence numbers yet。



![](img/e709d71a082b45418e3b70befbd3ce3f_227.png)

And so we're going to have to keep all of this state for every for every connection。

 And so we might as well just sort of keep it already。 So we're going have astruct。

 which is going be a send sequence。

![](img/e709d71a082b45418e3b70befbd3ce3f_229.png)

And that's going to have。This， which I guess is going to be a U size next。

 which is going to be a U size window， which is going to be a U size， urgent pointer。



![](img/e709d71a082b45418e3b70befbd3ce3f_231.png)

Which I think is like a bull。I think the urgent pointer has even been like deprecated。

 So I think we can probably just ignore it。 But let's keep it just in and conform us with the spec。

 W1， In fact， let's also just for our own sake。

![](img/e709d71a082b45418e3b70befbd3ce3f_233.png)

Do this。I like it when documentation like。It keeps data keeps comments from the protocol specs because it makes it really easy to refer back and forth to them to someone trying to read the code and trying to understand it later。



![](img/e709d71a082b45418e3b70befbd3ce3f_235.png)

And in fact， for own sake。So this is a u size， this is going to be a u size。

And I S S is going to be a U size。

![](img/e709d71a082b45418e3b70befbd3ce3f_237.png)

嗯。And then， in fact， this。

![](img/e709d71a082b45418e3b70befbd3ce3f_239.png)

Is probably useful to include as documentation on thisstruct。呃。So this is something like。

State of the send sequence space。

![](img/e709d71a082b45418e3b70befbd3ce3f_241.png)

B。And then I guess we can also refer to 3。2。

![](img/e709d71a082b45418e3b70befbd3ce3f_243.png)

This is RF 7，9，3。Section 3。2。And just。For our own sanity， we probably don't need this too。B。So。😔。

And this is figure4。So this might help us later when we're like looking back back at documentation things。

 In fact， these can arguably be。Proper documentation， so to speak。And similarly。

 we're going to have a receive sequence。Actually， we could maybe call this send sequence space。



![](img/e709d71a082b45418e3b70befbd3ce3f_245.png)

And this is the receive sequence space and the receive sequence space is a little simpler， it's next。

 which is a U size window， which is a U size up， which is a bo and IRS， which is a U size。



![](img/e709d71a082b45418e3b70befbd3ce3f_247.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_248.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_249.png)

And here， too， will sort of keep the docks。 One reason this is nice is because it means that we're going to have to switch back and forth a little less。

 at least。

![](img/e709d71a082b45418e3b70befbd3ce3f_251.png)

One might hope。嗯。So， this is the。Receve sequence space。



![](img/e709d71a082b45418e3b70befbd3ce3f_253.png)

So do the same here。This is RFC 793， S32， figure 5。嗯。And similarly， here。You don't need that。

 This can be this。And this will be this。

![](img/e709d71a082b45418e3b70befbd3ce3f_255.png)

Okay， so now we have the those set up。 and in addition。

 there are a bunch of variables that are that are used。

sort of as we discuss the protocol further down。They'll talk about segments and we'll get back to that later。

U。So the idea basically for us as sort of a TCP client。

Is that we're going to make sure that or we're going to want acknowledgegments for these。

So these are things that we have sent but have not been acknowledged。

 and if we have to send more data， we're going to use the space of sequence numbers。Right？



![](img/e709d71a082b45418e3b70befbd3ce3f_257.png)

So now the question becomes like what are going to be defaults for these， right？

 So a connection is certainly going to have a send sequence space and a receive sequence space。



![](img/e709d71a082b45418e3b70befbd3ce3f_259.png)

But we don't really know what's going to go in them。And so down here。

 I guess we have the diagram and so this is where it goes into sort of discussion of the sequence numbers and this is also something we sort of need to walk through。

So everyoctet， so every byte of data that's been sent has a sequence number。

And because we want to make sure that the receiver receives all of them in the right order。

 because every by is sequenced， every one of them sort of can be and should be acknowledged。

And the idea is that it's cumulative， so if I say basically if I send you an act 8。

 it means I have received all the bytes up to eight。And notice that it's not inclusive。

So I if I act 8， it means everything up to but not including8 has been received。

 of the first numbered bytes。嗯。Numbering within a segment as the first dataoced immediately following the header is the lowest numbered Yeah so if you receive a packet that has a bunch of bytes in them。

 then the first byte after the packet has the sequence number of that packet。

So this is when they talk about segment， a segment is basically just one packet。

 So this is the sequence number from the header of a packet that we received。

And that gives the sequence number of the first byte of the data in that packet。呃。

And the sequence number space is finite， which is important to remember。

 so specifically it's 32 bits long。And this means that。

Like the sequence numbers are going to wrap around if you send enough data。嗯。Ahu。Okay。Fact。

In response to sending data that tea people receive acknowledgecments。

 the following comparisons are needed to process the acknowledgecknowments。Let's see。Yeah。

 so the idea is that we as a sender， we're going to send data to the other side and it's going to send us as back。

And in order to do that。Yeah， so this is going to be the last sequence number we have sent。

 but that has not been acknowledged right so this is the values from before。

This is the acknowledgement field in the header when we get a packet from the other side。

No I from the received。Yeah， so this is the so again， this is up to but not including right。

 so they are expecting to get something with the sequence number next。

And these are on segments right so these are headers of the current packet。

 so this is saying that the first byte of the current packet has the sequence number。

And L is the number of bytes。Contained within this packet。

And so necessarily the if you add these two and subtract one。

 that is the sequence number of the last byte in a packet。And so here。

 they sort of define this notion of what an acceptable act is。 And if you look at it。

 it's actually not that surprising， right， It's saying that if the。嗯。

As long as the value they are acknowledging is one that we're expecting an acknowledgecment from right so we believe we have not received an acknowledgement yet。

 we receive an acknowledgement and that acknowledgement is something that we have actually sent right so next is what we're gonna the sequence number we're going to assign to the next byte we send。

 which means that if they try to act something that is greater than this。

 it means we' trying to act a byte we haven't sent。If they try to act something that is before。

Before this， it means we've already received an acknowledgement for it。

 so we don't really care about it。呃。And。If you have a packet that's like on the retransmission cues is something you might have to say again。

 you should consider it acknowledge if basically if the last byte。

 the sequence number of the last byte in that packet。Has been acknowledged。Yeah。

 so these sort of checks here are things we're going to have to add later。

 they're not important for the setup， but they are important to do。

So we're going to end up having to look at these。 I'm going to ignore them for now。

 So because the very first thing we have to do is the henshake， which is this part so。Sorry。我。No。

Yeah， so part the part of the problem is that TCP allows you to like establish many connections right。

 so we have these quads and there's nothing stopping you from like starting another connection with the same quad。

 but TCP sort of has to detect that this has happened。

And the way it does that is by basically randomizing what you call the first byte of a stream because that means that if someone because you randomize it every time。

 when you start randomly you're unlikely to start on something that's valid for the other for some connection the other side is still remembering from before right like they're remembering this part of the sort of sequence number space you pick randomly you're going to pick like somewhere out here because it's a very large space and that is far outside their window so they're just going to go no。

 this is not a part of my stream and they're sort of going to detect that something went wrong and probably terminate the connection。

嗯。Specifically， they want to assure this even if TCP crashes and loses all knowledge of sequence numbers。

And so this is why when you create a new connection， you choose a random initial sequence number。

And imagine that it's just like actually random， in reality。

 they sort of want it to be not quite just random， but so that it increases over time to makes it sort of maximally unlikely that you end up in the same sequence space as someone else。

嗯。There's a bunch of assumptions here that probably theyre unclear whether hold on the internet today。

 but we're just going to start with this being。I think actually random is probably what the current recommendation is。

 but it's not important。Yeah， so there's the initial send sequence number that's chosen by the sender and the initial receive sequence number。

 which is learned during connection establishment， So this is going to be in our case because we're first implementing the server we're going to receive a sequence number from the other side。

 this is the sequence number of their S packet so that is going to be where they're going to start transmitting right and in response we have to send them a sequence number。

 which is the sequence number that we are going to start transmitting from。So at the beginning。

 the two TCP hosts are going to have to synchronize。

 and this is done in the sort of handshake protocol they uses a S for synchronize。

 and that includes the initial sequence numbers。嗯。Right so this is the actual handshake protocol and so A tells B that they started this and then B respond。

 okay， I got your message like I got your sin and then it sends my I'm starting at this location and A says okay I've heard that and these two can be combined because they're both being sent from B to A and that's how you end up with this handshake。

RightSo this is the three way handshake。

![](img/e709d71a082b45418e3b70befbd3ce3f_261.png)

So now that we have that， before we start digging into sort of actually sending data。

 let's try to now figure out how you're going to start a connection。嗯。

I feel like these we sort of want to be。We're going to have to figure out what to do about this on I don't think this can be default。

But let's figure that out a little bit later。Let's not do this highlighting。

 So the question then becomes what goes in this unimplemented part， right。

 So this is where we're writing a TCP header。 We need to give the sequence number and the window size。



![](img/e709d71a082b45418e3b70befbd3ce3f_263.png)

Well， the sequence number， so because we're receiving a syn and sending a syn Act， right。

 So the sequence number we choose really just has to be random。



![](img/e709d71a082b45418e3b70befbd3ce3f_265.png)

We have to pick some number， which is where we're going to start transmitting from。

 And that number we have to give to the other side。 So we're gonna match on self do state， I guess。

And zero is random。 So we're going to start at 0。 Ultimately。

 we're going to change this value to be something that is actually random the way the spec says。

 But for now， we're just going to say0。

![](img/e709d71a082b45418e3b70befbd3ce3f_267.png)

This other thing is the window size， right， And this is how many bytes are we allowed to have outstanding。

 And if we look further down。A quiet time， there's a lot of stuff in TCP。Yeah， where's the。

There's like a suggested window of size somewhere， but I don't remember。

So the TCP spec is actually pretty easy to read if you sit down and read through it。

 and it is pretty interesting， they talk about a lot of different interesting challenges that can come up。

Where's the place where it says？Window size。Window management suggestions。对。

Let's start with a window size of。

![](img/e709d71a082b45418e3b70befbd3ce3f_269.png)

好停。嗯有。

![](img/e709d71a082b45418e3b70befbd3ce3f_271.png)

Seems fine。Again， like there are protocols for that basically determine how you're supposed to set this。

 but for us， it doesn't really matter in this initial setup phase。



![](img/e709d71a082b45418e3b70befbd3ce3f_273.png)

This is more for us to understand what's going on。What we could do here is something like have a function that determines where to start Now the other thing is keep in mind that they just sent the other sites just sent us a sin that we're acting right which means that we need to acknowledge their sin and the way we're going to do that is by setting the acknowledgement number。

Right， and remember that the acknowledgement number is the next bite we are expecting to get from them。

Right， and so that's going to be。Where's the sequence number。

So the sequence number they sent us is the sequence number of the sin。 We have now received the sin。

 And so therefore， the next thing we're expecting is the next bite。

So that's the next thing we're expecting。 In addition， oops。

The other thing we're going to have to do is set the。嗯。It's called。So our sequence number。

 we already set to0 above， but now we're going to have to establish a bunch of state for ourselves right so specifically for the send state。

 we're going to have to set a bunch of stuff and for the C stuff we're going to set a bunch of stuff。

So first， we need to keep track of。Sender。Info。So this is the receive window the other side sent so in this case let's call us the server and then the client the client sent us information about their sequence number and like their initial sequence number and also send us stuff about their window size and we need to keep track of that in order to keep track of their window right so in self dot receive we have a receive sequence base so that's next window this urgent pointer and IRS and so the IRS is just the sequence number that they just send us。

Right， because that is the sequence number of the sin， which is the first thing they sent us。

 The other thing is the， the next by we're expecting from them。 Well。

 I guess let's do these in order。 The next byte we're expecting from them is the。P。

H sequence number plus one， right， because we've received the sin。The window。😮，Window。Wellow。

 window size。

![](img/e709d71a082b45418e3b70befbd3ce3f_275.png)

And the window。The number of data are beginning with the one indicating the acknowledgement field。

 which the sender is willing to accept right， so that is their window size。

 the urgent pointer we don't actually care about， which means that here we have all of this sender info。



![](img/e709d71a082b45418e3b70befbd3ce3f_277.png)

RightSo this is all the stuff that they sent us that we need to keep track of。 And now， of course。

 you'll notice that the acknowledgement number is really just the next， right。So in fact。

 we can just do this。 In fact， we can we can take advantage of this further。

 further down in the protocol in that it will always be the case that the acknowledgement number is just the next thing we're expecting to get from them。

 and so this might be something we can sort of factor out later on。In addition。

 we need to decide on stuff worth're sending them。So we have to establish our send sequence base。

Right。In particular， we're going to have to do something like the last thing we sent them that is unacknowledged is whatever the sequence number we choose for our sin is。

 right that is the thing that we've sent them that they have not acknowledged。

The next one we should send， os， the next sequence number we should use。Is this one？Right。

 so is one past the sin。The window size we're going to use is， I guess， 10 right。

 That's what we chose further down。 The urgent pointer we don't care about the。



![](img/e709d71a082b45418e3b70befbd3ce3f_279.png)

WL1， I don't know what we initialize to。 It's used to basically compute how aggressive we should be about sending things。

 So I think we're just going to not set it for now。



![](img/e709d71a082b45418e3b70befbd3ce3f_281.png)

呃。And the ISS is zero。So the reason I set IS S here first is because the IS S is the sequence number of the sin。

 right？ So this is why arguably this should go here。As well。And so now of course， we can use here。

 the sequence number here is going to be the ISS。And then 10， this is going to be our window size。

And at this point。We now sort of have，ooh， these are in， these are in send。All right。

 what am I missing？Secequance number is probably a function。No field receive on state。Oh， right。

 this should all be on connection。呃。The sequence number， let's do as you size。Well。

 it's going to be all sorts of painful。Right， let's stick to the。Types they use。

 which is the sequence numbers are U 32s， the windows are U16s。So this is u30， this is U 32。

 this is U 32， this is U 16。This is U 32。The reason I use the UI is because there are TCP extensions that basically increase the size of these values to accommodate for having more data in flight。

 but probably not something we care about right now。Seft do send oops， send。And this is send dot。

 and this is send dot。All right， how's that？呃。Right， so this is for the defaults。Yeah。

 so this is why it's a little weird actually to。Set up a connection in the first place。嗯。Yeah。

 specifically what makes this weird is if a connection is closed。H。嗯。So here's where this is weird。

If we're in the closed state， we have no state for any connection， if we're in the listen state。

 we also don't have any state for a connection， all that means is that we're sort of willing to accept connections。

Which means that connection doesn't really have a default because if youre not if you're listening。

 you don't have a connection。So it's a little weird for this to even have a default。

Which is why I wonder whether。嗯。We should not have default。And instead， have something like。U。Except。

Which gives you a self。嗯。And what that will do。Is actually this。So we're going to have an accept。

 which is how you accept new connections so that assumes that you have no current state that's going to produce a state。

Right。I guess， maybe option。So this is gonna to be okay， none。呃。

So here we're going to create a new connection。

![](img/e709d71a082b45418e3b70befbd3ce3f_283.png)

Its state is going to be。Well， presumably we receive the sin， so according to the diagram。

 we're going to be in the sin received state。

![](img/e709d71a082b45418e3b70befbd3ce3f_285.png)

S received。Receive is going to be。不し。Sve sequence space。

And send is going to be a send sequence space。Yeah， this is actually probably nicer。Like， so。

What else do we want Great， so that then gives an okay sum C？What am I missing。

 So send has some other fields， specifically up W L 1 and W L 2。 So I guess up is false。 W L 1 is。0。

 WL2 is0。I don't actually know what these should be and what does receive sequence base have up which is false？

呃。So， let。ISS is 0。I is this plus one。Beautiful。And this is a comma。Right。

 so this is here we're creating the entire state for a new connection because we received the sin。

 which is represented by the state and then we send the act。Allright， let's see。 So in main now。

 this changes the setup a little。 Basically， what we're going to do is we're going to match on entry。

So yes here we're going to use collections， hash moap。Entry， and if we get an entry occupied。嗯。

Then that is an existing connection。And if we get an vacant。Then we do something。Right。

 so if we get an occupied one。Then we call on packet。If we get a vacant one。Then we're going to do。

 if let some。Connection is equal to TP connection， except。N IP PHT。These things。um。

And if that is some， then we're going to insert that connection。So we still want an on packet， right。

 because there are going to be cases where we actually receive a packet and we have some current state。

In which case， this will probably do something like u size， actually you probably won't even do that。

 I'll return nothing。And currently， that function does nothing。Unimlomented。嗯。

What this means is that initially if we get a connection from a quad that we don't yet know about。

 then we try to accept that connection。Wouldn't random but decreasing be better， though。

As the sequ numbers increases as you send bytes。呃。So this part of the RFC for choosing initial sequence numbers has been like obsoleted by later RFCs。



![](img/e709d71a082b45418e3b70befbd3ce3f_287.png)

So I would just like sort of ignore what it says because if you look at the 7414。

Some of the other thing， I think it's  1122 already goes into a bunch of details of like all of the ways in which that is broken。



![](img/e709d71a082b45418e3b70befbd3ce3f_289.png)

And what you should do instead。诶。是。See get mute all packet it。This has to be mute。

 This probably also has to be mute。All right， all right， let's see what happens now。Send a packet。

Well， that doesn't look great。The packet went to us， and we sent。Something in response。

Not entirely clear what？And then we panicked it not yet implemented。At 1，4。At 149。Okay。

 so I think what that means is we got the first packet。And then it tried to connect to us again。

 And then we crashed。嗯。But this， though， is not very promising。

 That suggests that whatever it is we're writing back is not correct。Also， how is it？1，4，5，6。

And something is not right here。Let's take a look at what the responding with。Le bites。呃， about。

Unwritten。

![](img/e709d71a082b45418e3b70befbd3ce3f_291.png)

So it's responding with。A ton of bites， at least。Why are they weird。😔。

Let's look at- so what we're supposed to respond with is an IP header。So， the IPRC。It's like RRC 791。

Since this one。呃。Let's see。

![](img/e709d71a082b45418e3b70befbd3ce3f_293.png)

Hitter format。Version。Actually， that's another good question。 Let's compare that to what we received。

So。Up here， let's do。Got header。呃。Senttetter。Just so we can sort of compare the stuff we got in and what we sent out。

So this is gonna be IP PH and I P。

![](img/e709d71a082b45418e3b70befbd3ce3f_295.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_296.png)

Ooh， is there even a way to get this out？Probably not。So let's just do that。 Oops， what I do。

TCP header。What is it complaining about？😔，I don't think it's complaining about anything good。Oh。

 TCPH。

![](img/e709d71a082b45418e3b70befbd3ce3f_298.png)

All right， so let's see what happens now。So。What it got in for the IP header was 45，0，0。

And then so the question what becomes， what are these bys。Back to this。So， these bytes are。

Versin is the first。 So version is 4， which is what we also what we respond with。So 4，5 is correct。

Then， it's 0。0， and then this is length。So that's fine。Identification is 24。 What is identification。

Okay， that's fine。It's fine for that to not be helpful。Flas。We are not setting any flags， are we。

Total length。Okay， so this is this。

![](img/e709d71a082b45418e3b70befbd3ce3f_300.png)

Then， total length is the next。

![](img/e709d71a082b45418e3b70befbd3ce3f_302.png)

Oh man， the scrollings can be annoying is 003 c， and we give 0028， so that's fine。



![](img/e709d71a082b45418e3b70befbd3ce3f_304.png)

Identification is next。So this is oh， man。

![](img/e709d71a082b45418e3b70befbd3ce3f_306.png)

呃。24 C D， and we give。Nothing。😔，So what are the flags。😔，Flas down here。Okay， that's fine。

Time to live in protocol。Flas and fragment offset。Time to live。 We do set。Specifically。

 I think it would set it to what was already there。Protocol follows that。 So protocol。

<|OTHER|>So they send 40，0，4，0，6。Okay。40。😔，0，0。40，6。That doesn't seem right。Lets try again。45，0，0。



![](img/e709d71a082b45418e3b70befbd3ce3f_308.png)

0，0，3， c。24 CD。40，0。40，0，6。 So there we give it the same。 And then their header checks some as 94，9。

 B。And R is B97C， the checksum is sort of unimportant。Source address。

So we're setting our source address。We're not reversing them。Or maybe we are。

 So their source address is these four bytes。Our source address is these four bytes。 Okay。

 so we are reversing them。So rs is 02， theirs is 01， so that's inverted。

So that looks like the IPV4 header is correct。So I wonder why。I wonder why That's not。Looking right。

😔，Let's see what this says for send。Unsuccessful send。

 the number of bytes sent in the packet is returned。Ha。Okay， what about our TCP header。

 So ours start with 0，1。That seems maybe problematic。

But the weird thing is this couldn't even parse out the IP addresses。I' just saying raw packet data。

Which is a little odd。Also， we're sending on an awful lot of zeroes。Which doesn't seem right。嗯。Oh。

 wait， this isn't right。This is how many bytes we didn't write。Which is this is not what we want。

We want。Buff thought Le Minas unwritten。I think。I mean， it still still crashes。

 but at least now we're writing out fewer bytes。嗯。So the first part we still have。

So that goes up to there。And then， we're sending。It looks like an extra 0，1。0001。

 this is the end of the IP packet， and then we're sending 01 BB。And then， B， A 86。

So we're inverting these values。 Oh， so these are the TCP ports。Okay， so that is correct。

 we are supposed to invert the TCP ports。嗯。Then we're sending。😔，All zeros。😔。

Which is our sequence number， is that right？

![](img/e709d71a082b45418e3b70befbd3ce3f_310.png)

嗯。Which is。R sequence number Yeah， so our sequence number is all zeros。



![](img/e709d71a082b45418e3b70befbd3ce3f_312.png)

And then we send our acknowledgement number， which is this part。I don't want it to scroll。

So starting at0 F， which should be the same thing as they sent us their sequence number。Rightai。

And what they sent us is their sequence number。Was this value。0 F60， D172，0 F60 D173， right。

 so plus 1。 So that's correct。And there's a bunch of other stuff that didn't matter。



![](img/e709d71a082b45418e3b70befbd3ce3f_314.png)

And I think our length is the same as theirs。

![](img/e709d71a082b45418e3b70befbd3ce3f_316.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_317.png)

Hello。

![](img/e709d71a082b45418e3b70befbd3ce3f_319.png)

They're also， oh， I see and then check some an urgent pointer。It's like the last bit that they're。

Including here。😔，Specifically， following the。So they sent that， then their acknowledgement number。

 which is all zeros then。1，2，3，4 by of stuff。Where the last one is their window。

So these are their window FAAF0。Then。Check some。😔，An urgent pointer。So they urgent point to zero。

 and they're sending a bunch of TCP headers。So why is ours differing from that？



![](img/e709d71a082b45418e3b70befbd3ce3f_321.png)

So， we're sending。This is the sequence number。Then no， this is the ament number。

 Then these are the data office and reserved。 This is the window。 So 0 a there is our 10。



![](img/e709d71a082b45418e3b70befbd3ce3f_323.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_324.png)

呃。And then we send check some， and then we send an urgent pointer。 That check some is wrong， though。



![](img/e709d71a082b45418e3b70befbd3ce3f_326.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_327.png)

I don't think we're allowed to send a check sum of 0。certainly， I think it's。

 I think it's not true that the tum is zero more， more importantly。Oh， interesting。



![](img/e709d71a082b45418e3b70befbd3ce3f_329.png)

Okay， so I think we， yeah， we need to manually compute this checksup as my guess as well。

 So specifically。

![](img/e709d71a082b45418e3b70befbd3ce3f_331.png)

Down here。We're going to have to do。

![](img/e709d71a082b45418e3b70befbd3ce3f_333.png)

Check sum is going to be the S act。Dot calculate check some for IPV 4。 We're gonna give the I header。

 the one we're using to send。And the payload is going to be empty。And that。Should give us。嗯。

Fail to compute。Check song。Okay， so that should give us the checkum。

 which should be set on the synac。Check some， it's going to be equal to that。

Let's see if that makes a difference。W。Its going on here。 What did I miss， Oh。

 this should be a semicolon。可以。Now， shark。And then， try again。Raw packet data is still what it says。

Actually， let's have it Stop trying to。Crash herecause it's a little annoying。Interesting。

Why does it just say raw packet data， though， This packet looks entirely fine。Specifically。

 why does it not think it's a valid I1。Send。😔，Must be a valid representation of a packet。

I wonder whether there's a here。on tap dot texts。

![](img/e709d71a082b45418e3b70befbd3ce3f_335.png)

Maybe we need to include these as well。 actually， that's probably true。嗯。



![](img/e709d71a082b45418e3b70befbd3ce3f_337.png)

So we need to set flags and proto。And I think we're going to do there is。Yes。

 so remember that will we get in here？Oh， I wonder whether I can just turn that off。No。

 I don't really want to do that。

![](img/e709d71a082b45418e3b70befbd3ce3f_339.png)

H。Specifically， this is like if no PI。嗯。

![](img/e709d71a082b45418e3b70befbd3ce3f_341.png)

Which the question is whether we have to put those four headers at the beginning。



![](img/e709d71a082b45418e3b70befbd3ce3f_343.png)

呃。When we send as well。

![](img/e709d71a082b45418e3b70befbd3ce3f_345.png)

中。Yeah， I don't think we care about that。 Okay， so let's make this。

 let's make this without packet info。And now these are going to go away。

There's no longer going to be these four bytes at the beginning。And in theory。

 we shouldn't have to write them when we write back either。ignoringgno weird packet。 I P， Okay。

 that's fine。And now， if I do this， what's it gonna do。Ooh， how about that？Okay， so now。

Look what happened。Our client。Yeah， so it's basically why not monolith is state machine with transition between states。

 So the okay， so that's how I started it out right， with connection being an enum。

 The reason I didn't do it this way was because there's a bunch of states that's shared between almost all of the states。

嗯。In fact， the things related to sequence numbers and acknowledgecment are actually associated with all of the states that are where there is a connection。

 and so that's why we have the state enum， but there are some fields that are not a part of that enum because they would be in every variant。

So we will still use any them for the actual state machine。嗯。Yeah。

 so here what happened was this program， Okay， so for what is worth Necat is a program that just like connects to here and then just whatever bytes you give it to standard in。

 it's going to send over the network。And so it's connecting to 02。 And indeed。

 we see that connection here。 And then we see that we sent a response here。Right。

 and it looks to be sent to the right port。 right， So this was the source port。

 This is a destination port。 It has syninac。 It has a sequence of 0。It has an act of one。

Which is correct because the sequence number they used was also zero。And we have a window of 10。

 They have a window of 64000 and a lens of 0 because we're sending no bytes。

And then they sent us an act。So， this act。Is supposed to be。Well， basically。

 this act is saying I got your sin。 and at that point the connection is established so that is the next packet we now have to handle right。

 So this means that now actually our initial part of the handshake worked out correctly。嗯。

I suspect that we might not even need this。 I think the colonel does this for us。

But let's double check。Yeah， the colonel does that for us。呃。Colonel is nice and does this for us。Now。

 we don't actually need to print these bytes anymore。

 which is gonna be make the stream a little nicer。 Let's also do。

Let's also do this because we don't care about it。嗯。All right， so now at this point。

We're going to do C dot state。We already set the CD state right so down here。

 this is where the state machine comes into play。 We're going to match on self dot state。And。

If the state is。Well， so let's just imagine that state closed doesn't exist， right。

 if if it's closed， then like we have no state。 Listen as well as a little weird because if you're in the listening state。

 you also don't have any state， right you don't have any connection yet。And so in some sense。

 it's a little weird to think of it as。As a state that you can be in。

 So let's ignore that and rather think about established， because in theory。

 what we're going to do is move from this to this。So if we're in sin received。

That's where we're sort of。Expecting to be right now。How do you feel about the rust mascot。

 I like the crab。嗯。If we're established， then this is something that we haven't。

 we don't know what to do with yet。 But if we're in sin received now the question becomes。

 now what do we do。

![](img/e709d71a082b45418e3b70befbd3ce3f_347.png)

Well。It will tell us。So specifically， if we're in the received。



![](img/e709d71a082b45418e3b70befbd3ce3f_349.png)

If we're in this state， expect to get an a。For our sin。That's what we're expecting right now。嗯。

I think one thing we're going to want here is almost to keep track of this IP header。嗯。

Just we don't have to repeat it every time。Yeah， I。

 I wonder whether this is something we actually want to stick into the。

Into the state of the connection。Well， actually， I guess here is going be an ether pars。I PV4 header。

They were just going to。Keep around there。In such a way that。Here。😔，呃。

Because we're going to be using basically the same IP header every time。 There's no reason for us to。

嗯。There's no reason for us to have to go through the steps of like parsing out the source and destination fields each time。

 The one thing we will have to be careful about， though， is。IP dot。嗯。



![](img/e709d71a082b45418e3b70befbd3ce3f_351.png)

What's that field？The payload lens， How do we set。

![](img/e709d71a082b45418e3b70befbd3ce3f_353.png)

Payload lend to be Sak。Dodge。What do we have it said to， Heerland。Plus zero bytes for the data。

On receiving， you strip the first bite from the ton slice into to the boom back。 Yeah， so。

 so we no longer need to do that now， because I added this without packet info。

 because we're now constructing with without packet info。 We don't have those four bytes anymore。um。

If no。And also， include on send。So because we're ignoring the packet info， we don't have to do that。

嗯。Right， so we need to set the payload lend of the I I P every time we're going to use it。

 But apart from that， we're probably fine。 There are probably some other things like we could have a convenient method on here。

 on connection。 that's something like send。does this trick down here for us。

But we're probably not going to be able to actually use this most of the time because the retransmit cu is gonna。

 well， the re transmitmit cu means that we might have to send things later。

 So we actually have to keep track of the bytes。C点I。And this is also C of A P。

What is he complain about now。Expected U size。Found you 16。Allright。

 so what do we do when we get us in act well。If the。

So here there are a couple of things we need to do， right， So if you remember from from the RFC。

 they talked about this or is it down here somewhere。



![](img/e709d71a082b45418e3b70befbd3ce3f_355.png)

。This acceptable act check。

![](img/e709d71a082b45418e3b70befbd3ce3f_357.png)

Which we basically have to do for any package we receive。嗯。Jackie， Jack。

W whichch is to make sure that this is an act that we shouldn't be ignoring because it sort of is something that's unrelated to us or was sent incorrectly by the sender。

And so we need to do that basically regardless of what state we're in。

 So we're going to do if TCPH dot acknowledgement number。嗯。So here。

 one thing that's tricky is all of this is rapping。 It's rapping arithmetic。 So specifically if。

TCP acknowledgement number。Is。Right so remember that because we can wrap around， right。

 this is 32 Bs。 you like it it doesn't really help to just do to do this sort of stupidly， right。

 of self dot send dot n a minus this and TP H dot act number。

Less than equal to self dot send dot next。If we did this。This would not actually do what you want。

What。呃。What's it complaining about。How。Unemployment。aitWhat am I missing？Not happy with me。Oh。

Double exclamation mark。嗯。So this check writing it out like this will not actually work because of wrapping arithmetic。

 right Both of these need to consider wrapping。 so the check really is that this is between those when considering rapping arithmetic。

呃。I I'm not creating a socket server per se。 this is implementing TCP。

 It might let you write sockets， but it's not a socket server。

I don't really know what you mean by socket server。

Was is implementing the ways that sockets work sort of under the hood in some sense。 There a really。

 what we want here is sort of a comparison that。Checks， let's see if。So let's first do ACN is TCPH。

 acknowledgement number just because。嗯。If AN is more than self send UNA。But， remember wrapping。Okay。

 so if AN is more than UNA， then we require that it is less than or equal to next。Or rather。

 actually， if， if it's less than U A， it might still be fine， right because。

How do I even visualize this？ Let's try it here。

![](img/e709d71a082b45418e3b70befbd3ce3f_359.png)

So。嗯。We have the space where。There's there's UA。And then there's the act we got。

And then there's next。And we want to check that act is greater than UA and that it's less than or equal to next。

It's very unimpleed， yeah， but of course， because the 32 B space wraps around。So at some point， like。

 imagine that this is zero。 it sort of goes like。This way and then comes back around here。

 So this is also a very large number。 So imagine that there are a couple of cases that we sort of need to think about so。

For example， we might have that。Like， so the simple case is that you have。This。U A and。

This case is simple because you can just do straight comparisons where it gets harder。嗯。

Is when you have something like。Here is you。😔，Here is a。😔，And。😔，Well， that was a stupid example。

 I should have done wrapping the other way。 let me。Oh man。

 erasing of this program is really annoying， but I think there's a。Yeah。No， race。That's awful。

 Can I get a bigger thing？Like brush。はです。Yeah。All right。Pen。😔，嗯。So let's draw that again， shall we？

So zeros here。And then the numbers go this way， but here， of course， we wrap around to zero。

So now the simple case is。You have you。You have N， you have A， you compare them straight。

 Everything is fine。Where he gets weird is if you have。You。😔，And。Ai。😔，BhM， this should be。 sorry。

 should be。 let me clarify。 I wrote the letters in the wrong order。So specifically。嗯。

Give me back my thing， pen。So， if。This is a， and this is N similarly。This is A， and this is N。Right。

 so the red case is trivial。 The green case is harder because here， if you just compared U and A。

 you're that's not good enough， right， because U is greater than a， which is not what this requires。

This requires that U is less than a， but in a wrapping space they are。And the same。

 you have the same problem， of course， between。Between here， right。

 like if there's a rap between here， then you would have the same problem with that comparison。

And so this is the trick that we're going to have to overcome for this check。

This check is not just going to be。

![](img/e709d71a082b45418e3b70befbd3ce3f_361.png)

This check is not just going to be a straight comparison。Specifically。

 I think the trick here is going to be to compare them pair wise。 So specifically if。



![](img/e709d71a082b45418e3b70befbd3ce3f_363.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_364.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_365.png)

UA is less than a N。Right， if。So if U is less than a。

 then either were in this case or we in this case， or there's an error right？ So here if。



![](img/e709d71a082b45418e3b70befbd3ce3f_367.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_368.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_369.png)

Sorry， it means we can't be in this wrapping case correctly， because U is greater than a。

 So for this to now be correct， we now need to do the comparison of a to N。So if。

Ac n is less than self dot send dot， next。

![](img/e709d71a082b45418e3b70befbd3ce3f_371.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_372.png)

Less than or equal。Right， so this is this first case is the trivial case， no wrapping。Right。

 so we're all good。So it's U less than a， less than or equal to n。So all good。In this case， we have。

U is less than a， and a is greater than n。

![](img/e709d71a082b45418e3b70befbd3ce3f_374.png)

So can that happen with rapping？Well， you， so let's think about it。U is less than a。

 so we have U A and a is greater than n。 so n is somewhere over here。Well， that's。Fine。As long。

 actually， is that always fine？Isn't this check just broken。So， specifically。

When would this ever not be true。Right， like。I'm imagining here， for example。Like you。

So currently we have used lesson A， right？Isn't this true for NN？Like if n is here， then N is。

Greater than or equal to both of them。 I think the requirement is that。N is less than you。

I think the requirement is that a is between U and N and U and N are not overlapping。

Because if N was here， that just seems wrong。I think specifically the case we're looking for is we want a to be between U and N。

 which means that we can't do all the way around the wrapping。So I think what we want to do is this。

 right， that is the case we're trying to guard against。 We're trying to do the the knot of this。

 right。

![](img/e709d71a082b45418e3b70befbd3ce3f_376.png)

嗯。No wrapping。呃。So in this case， n may have wrapped。Check that。So in this case， U is less than a。

 and we now need to make sure that n isn't between A and U。



![](img/e709d71a082b45418e3b70befbd3ce3f_378.png)

Right looking at our picture here， we have that use less than a。

 So what we're really checking is that n isn't between these two。 as long as that's not the case。

 then everything is fine。

![](img/e709d71a082b45418e3b70befbd3ce3f_380.png)

So actually， we can write this as。Check is violated。 if and only if N is between U and a。So， if。

Self dot send dot next is greater than self dot send dot U A。

 and self dot send dot next is less than A n。嗯。And we're specifically allowing。

We're specifically allowing act to be equal to next。Right。



![](img/e709d71a082b45418e3b70befbd3ce3f_382.png)

So。A is allowed to be equal to next， so if n is here， then we're all good。If n is here。

 then that's obviously who actually is that fine？

![](img/e709d71a082b45418e3b70befbd3ce3f_384.png)

I don't know。 that needs to be strictly greater。呃。We need next to be。This is an error。

 even if next is equal to UNA。Great。If you compare U to N， don't you know if you are rapping or not。

 The problem is you can have wrapping in both directions。 You can have rapping between U and A。

 You can also have rapping between A and N。Right， and so specifically。

 what we're dividing this into is two cases， either if u is less than a。

 then the if U is less than a。

![](img/e709d71a082b45418e3b70befbd3ce3f_386.png)

Right。Then the invariant is violated。 if and only if and is between the two of them。

If n is anywhere else， either to the right or to the left， then it's fine。

Because if it's still the right， then it's more than A。 And ifs still the left。

 it's just wrapped around and is more than a。So that part is fine。

Promoting to a bigger type wouldn't help because you still you can't do the unwrapping right is the problem。



![](img/e709d71a082b45418e3b70befbd3ce3f_388.png)

In this case， so let's draw this other case out。

![](img/e709d71a082b45418e3b70befbd3ce3f_390.png)

我认为。There。嗯。So let's draw the other case out with。Pretty blue colors。U。

So this other case is that we have。We have A and U， right， A is less than U。



![](img/e709d71a082b45418e3b70befbd3ce3f_392.png)

Right， that was。

![](img/e709d71a082b45418e3b70befbd3ce3f_394.png)

This is if is less than U is less than a， right， so this is a is less than u or they're equal。

This check is violated， if。And only if。呃。If n is in between here。Now。

 this is okay only if n is between here。Otherwise， it's not okay， right， if n was here。

If this was end。对。mIf this was N， then we would have a problem， right。

 because now a is not between U and N。So if a is less than u。

 this is a problem if n is between A and U。

![](img/e709d71a082b45418e3b70befbd3ce3f_396.png)

。Okay， if。Check is okay。 if and only if n is between U and A。 So that is a nice symmetry to it。



![](img/e709d71a082b45418e3b70befbd3ce3f_398.png)

嗯。

![](img/e709d71a082b45418e3b70befbd3ce3f_400.png)

Again， and。Self dot send dot next is less than this。Else this。



![](img/e709d71a082b45418e3b70befbd3ce3f_402.png)

And for the equal， the requirement is that N is allowed to be equal。

 so the check is okay if n is equal to a。 so if self dot next is greater than or equal to a。

 that's fine。

![](img/e709d71a082b45418e3b70befbd3ce3f_404.png)

And it has to be strictly less than you， which this check is here。

 As long as those who are both true， then were fine。 So we're not returning。

 Otherwise we are returning。Okay， so when we get to this point。

 we now know that we what we have is an acceptable act。



![](img/e709d71a082b45418e3b70befbd3ce3f_406.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_407.png)

Who。Great。This is for。This is when you receive data， which we're not really doing， well。

 I guess technically we received data。呃。When data is received， the following comparisons are needed。



![](img/e709d71a082b45418e3b70befbd3ce3f_409.png)

Oh， this is for right。 So this was checking the act。 And now check that。 so this is the。



![](img/e709d71a082b45418e3b70befbd3ce3f_411.png)

呃。

![](img/e709d71a082b45418e3b70befbd3ce3f_413.png)

Valid segment check。This is to check that the bys that are in this packet， including the sin。

 the sin counts as a byte， to check that those are within the range of things we're willing to accept。



![](img/e709d71a082b45418e3b70befbd3ce3f_415.png)

So I guess let's actually give a 3。3 referencing here。



![](img/e709d71a082b45418e3b70befbd3ce3f_417.png)

呃。First， check that。呃。Sequence numbers are valid。3。3。So this is RFC 793， section 3。3。



![](img/e709d71a082b45418e3b70befbd3ce3f_419.png)

Right， so the valid segment check。Is similar， right？ It's very similar to what we did above。

 specifically， it's that。嗯。

![](img/e709d71a082b45418e3b70befbd3ce3f_421.png)

That it's not what this is。

![](img/e709d71a082b45418e3b70befbd3ce3f_423.png)

嗯。So going back to our picture here， they're really just swapping out the。These values for。



![](img/e709d71a082b45418e3b70befbd3ce3f_425.png)

Instead of U and A， it's going to be。

![](img/e709d71a082b45418e3b70befbd3ce3f_427.png)

They want next， oh， why is this pen different？W， pen。They want next。To be less than or equal。

To the sequence number from the packet。

![](img/e709d71a082b45418e3b70befbd3ce3f_429.png)

Which should be less than。呃。

![](img/e709d71a082b45418e3b70befbd3ce3f_431.png)

Next， so this is next， in case that was unclear， next plus window。

So what we could probably do is just have a function that does this kind of rapping arithmetic right。

 because we're going to need this check in multiple places。



![](img/e709d71a082b45418e3b70befbd3ce3f_433.png)

Because the check is pretty much the same。 So let's down here do。Do something like。FN。

Is between wrapped。So we're going to have a U size。B u。C U size。And this is going to be start。

It's going be end。I is going to be x。And it's going to return a bull。And we sort of want this to be。

So the question is， should this be inclusive or not inclusive？Let's write it as non inclusive。嗯。Okay。

 so。We can read this as。呃。If the star does less than x。If end is between。Start and X。

 So I think this is going actually make this a lot clearer， right？

 So if we in because these cases are sort of weird， we're just going to call this start。

 this end and this X。

![](img/e709d71a082b45418e3b70befbd3ce3f_435.png)

RightSo now it becomes a lot more intuitive。 So if we find that the start is less than x。

Then it's wrong if the end is between them。Otherwise， if we find that the start is after X。

 then it's correct if the end is between them。Right。

 to you see how this is I've just re labeled the markers。

 but now it's a lot clearer why this is correct。

![](img/e709d71a082b45418e3b70befbd3ce3f_437.png)

嗯。So， this is end。The start。This is N。 This is X。So if there's probably like a way you can do this without all this branching。

 but I find this easier to reason about。Yes， if start is x。

 then it's violated if and only if the n is between start and x。呃。



![](img/e709d71a082b45418e3b70befbd3ce3f_439.png)

And specifically。If we want this to be non inclusive。For both sides。Then we require， in this case。

 we require that n is not in between here。And is it allowed to be equal to start？呃。

So what we're doing is S less than x less than E。嗯m。Not sure。嗯。If starting less than next。And。

We're doing non inclusive。Then， n has to be。Greater than X。Which means that it's not okay。

For it to be equal to x。

![](img/e709d71a082b45418e3b70befbd3ce3f_441.png)

Yes。It's not okay for it to be equal to x。 great。 and that's indeed what we have here， similarly。



![](img/e709d71a082b45418e3b70befbd3ce3f_443.png)

If the end， so we want this still be true， we know that this is less。If X was。



![](img/e709d71a082b45418e3b70befbd3ce3f_445.png)

So what I don't think the comparison with start matters， actually。

 I think all that matters is the comparison with end， although it might matter for this case。



![](img/e709d71a082b45418e3b70befbd3ce3f_447.png)

If the start。We want to check this， right， so we're writing the non inclusive version。

If it is the case， start is less than x。Then， we require that。Are we？Then， I think。It。It should fail。

Even if the end is equal to start。Because if the end is equal to start。Then this is not true。Yes。

 if the end is equal to start， this is not true。小。

![](img/e709d71a082b45418e3b70befbd3ce3f_449.png)

If the end is equal to start。

![](img/e709d71a082b45418e3b70befbd3ce3f_451.png)

Yeah， so if the end is here or up to， but not including x。

 then we're going to say that x is not between start and end。If end is。Equal to x。



![](img/e709d71a082b45418e3b70befbd3ce3f_453.png)

No， that's also not okay， yeah， so these are both equal。



![](img/e709d71a082b45418e3b70befbd3ce3f_455.png)

So if N， if the end has any of these values， including start an end， then it's not okay。

 Otherwise it is。 So if n is here， then we're fine， right， start is there。 E is here。 X is here。

 And so x is indeed between start and end。 if n is here， then we're also okay。

 because x is indeed between start and end。 If n is here， E is not between start and end。

 and if E is here it's not between。 Okay。

![](img/e709d71a082b45418e3b70befbd3ce3f_457.png)

Otherwise， so this is if start is greater than or equal to x， so this is this case， right？



![](img/e709d71a082b45418e3b70befbd3ce3f_459.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_460.png)

呃。I guess this is going to be。If star is equal to X。そし。Then we give false。Right。If。Oh。

 we could even hear do。Match。Start dot。嗯。Visit compare the thing that gives me an ordering is what I want。

wardard。😔，Gives me an order。ing great。 So match。嘻。Don't compare X。 that way。

 we don't have to do it multiple times。 So we're gonna use。Compare or and ordering。

If we get ordering equal。Then false， right， If start is equal to x。

 there is no way in which x lies between start and end。嗯。If start is less than x。Than this。

If start is greater than X。Then this case。And otherwise。出。Okay， so let's look at the greater case。

It might actually help for us to draw this out here。We have。Okay， so we have some timeline。

 timeline number line。Where start is somewhere。And X is there。呃。If， let's see。X is between S and E。

If and only if。呃。End。If it's not the case。That。This holds。Oh， I don't need word， yeah。

 you're probably right。Right。So I think this drawing makes a lot of sense in the sense that。

In these cases。Let's make it really explicit for ourselves。So， that's fine。This is also fine。呃。

But not in these cases。That's funny。I don't know how to。Mark the snow。

I guess this is going to be like。X plus E。Or， in other words。Great。So comments help。

Hopefully these diagrams explain a little better what's going on。We have。So， in this case。

We have the opposite。Of above。So I guess， here we want。Rraps。Wrap around。I sort of want this to say。

0。So， here。We have this where we have X， and this is S。嗯。X is between S and E in these cases， right。

 So here we have X S。And Yi。And in fact， it's only between them in those。As been。Only in this case。

But not in these cases。I guess that would be this case， for example。Because in this case。Oh。

 did I remove the case that I was kind of stupid？Where did I put。There。

X is between S and E only in this case， not if E is more than s， not if e is less than s than x。

 then x is not in between， and if x and E are both there or as S and E are both there。

 then it's also not the case that x is between S and E。Or in other words， if and only if。呃。I， this。

 I don't think that's right。Yes， or in other words， if and only is if。呃。This case。S。So， so next。

Was end。Start。嗯。No， this is x。This is end。This a starch。Or， in other words。If。

So only in the case where end is less than start and end is greater than x。Great。

 and now we can use this here， specifically。If not。Is between wrapped self。UA。Send dot U and A。

 self a N， self dot send dot next。 And we want this to be inclusive。 So this is wrapping sub。

Wping add1。Right， because if we want it to be is between， but it's allowed to be equal to the end。

 we're just going to increment the end by one， and it needs to be wrapping because we want it to go around。

啊。So it's not between then we're going to return， okay。The valid segment check， which we can now do。

The valid segment check。Is this。So we're going to do the same thing。But。是。

CN is TCPH dot sequence number。And if。Receive dot next。

Dot wrapping sub because we want to allow equality， seek n。To。

Self dot received dot next wrapping add， self receive window。If it's not between those。

 then we have a problem。Expected。I see 32。Who。

![](img/e709d71a082b45418e3b70befbd3ce3f_462.png)

Great， and also or what does this mean？Why did they give this？Oh， I see。



![](img/e709d71a082b45418e3b70befbd3ce3f_464.png)

So this one's kind of tricky okay， if it acts at least one byte。Which means that。

At least one of the following is true。呃。Specifically notice that the reason that we use these both checks is we're basically checking the first byte of the segment and the last bite of the segment and if any if one of them contains something that was within the window。

 we want to accept those bytes so the sender doesn't have to send them again。So in this case。

 this is still wrapping sub。 This is going to be not second， but。Well， second plus TCPH dot。嗯。



![](img/e709d71a082b45418e3b70befbd3ce3f_466.png)

What， what was the name of the TCP header payload length again。Oh man， really。



![](img/e709d71a082b45418e3b70befbd3ce3f_468.png)

Oh， it's just data dot L。M-1。u。Window end is going to be that。So that's going be this。

Why is this not formatting my file？Oh， I did something stupid。196。哦。Expected U size found U 32。

Oh yeah， these have to be U 32， of course。Because that's what we're operating on。嗯。Cannot add。

As you 32， I guess。

![](img/e709d71a082b45418e3b70befbd3ce3f_470.png)

All right， so now that we've made both of those checks in accordance with this。Yeah， exactly。

Do zero in those length savings we have four cases。Oh， man。So there's actually more than this。

It's also。For the accessceptibility。Hm。What is the receive window here？



![](img/e709d71a082b45418e3b70befbd3ce3f_472.png)

H。I see。 So there's basically special rules for。Oh， man。If。Both of these are for if data dot L is 0。



![](img/e709d71a082b45418e3b70befbd3ce3f_474.png)

And。

![](img/e709d71a082b45418e3b70befbd3ce3f_476.png)

Not TPH dot A。S and not TCPH dot thinin。Becauseuse these also counted as bytes，0 length。Segment。

Has its own has separate rules for acceptance。

![](img/e709d71a082b45418e3b70befbd3ce3f_478.png)

Yeah， exactly。 So this is acceptable if。Sec n is equal to self dot receive dot next。



![](img/e709d71a082b45418e3b70befbd3ce3f_480.png)

If。F self dot receive。Actually， this is if。啊。It's like。Okay is equal to this， but。So it's if。

The receive window。

![](img/e709d71a082b45418e3b70befbd3ce3f_482.png)

Is equal to 0。Then。If。嗯。Second and。

![](img/e709d71a082b45418e3b70befbd3ce3f_484.png)

Is not equal to self dot received dot next。 Then it's not acceptable。Ese。



![](img/e709d71a082b45418e3b70befbd3ce3f_486.png)

Then it's this check， which is basically just this check。



![](img/e709d71a082b45418e3b70befbd3ce3f_488.png)

So we still want this up here。Else。If self dot received dot window is equal to zero。

 then it's never acceptable。According to the speck， Els。This business。And of course。

 this can become an Elsif。And this can becomeul。Who。哎。And now I have a syntax error somewhere。There。

And also there。Okay。So we did the thing。This is also not true because the Seg dot L。



![](img/e709d71a082b45418e3b70befbd3ce3f_490.png)

Also counts S and Finnten。

![](img/e709d71a082b45418e3b70befbd3ce3f_492.png)

So。Let S L is data dot L。呃。If。TC P， H dot fin， then S L plus equals1。And oops。And if it has a sin。

 then S then plus equals  one。And now， anything that looks at。That。This is a U 32。Fu。FS。Slain。

Zal to 0。

![](img/e709d71a082b45418e3b70befbd3ce3f_494.png)

Great。Okay， so now so this was just the check we have to do for whether or not we are even willing to look at this packet。



![](img/e709d71a082b45418e3b70befbd3ce3f_496.png)

So to take a step back for how we got here， this is we have。The other plays。

 the other host sent us a sin。 We accepted it。 That was the function we wrote before。

 And in response， we sent an act for the thing that it sent us and a sin for it to send its part of the handshake。

 And now。And now what we want to do is。Take the act that it sends to arson and parse that。 and。

 hopefully we should get into here。

![](img/e709d71a082b45418e3b70befbd3ce3f_498.png)

So at this point， hopefully we should now be receiving a。呃。

And I'm going to ignore all of this for now， establishing a connection。Right。

 so we are at the point where。So we're basically be in this case， right， we were in listen。

 we got a sin， so we entered S received， we sent this and now we're about to receive this packet。

And now if all the checks work out in theory， well， so first of all， we should check that tcP。

ac is set。

![](img/e709d71a082b45418e3b70befbd3ce3f_500.png)

嗯。If that's not true， then like something was weird。 We didn't get an act or sin。

 So that doesn't really help as much。嗯。Yeah， this seems like a really weird packet to get。Okay。

 so if this is an a packet。嗯。It must have acted at least one unacted bite。

 which means that this must have acted our sin because it's the only thing that we have sent。

 And so therefore， we're going to say that our state is now established。Must have。嗯。Must have。呃。

Act our sin。Since。We detected at least one act bite， and we have only sent one bite。



![](img/e709d71a082b45418e3b70befbd3ce3f_502.png)

The same。So at this point we're in the established stage， and at this point in theory。

 we can start sending and receiving data。 instead what we're going to do is we're just going to immediately try to terminate the connection。



![](img/e709d71a082b45418e3b70befbd3ce3f_504.png)

嗯。Now let's terminate the connection。RightSo TCP has a feel returning okay when something is wrong。

 I agree。Although in this case， it's like a little weird to return an error， too。

 the reason for that， though， is the wave that main is written。If it errors。

 it's just going to error out entirely， although like maybe we actually do want to do that。

mBut this is like these errors are like the client sent us something weird。嗯。But yeah。

 I guess you are right。I mean， we could do like。Iio air。New I Air kind。um。This is like。嗯。Well。

 there are many reasons but。IYes。What do we even want to give here？sake。😔，let's do broken pipe。

And call this。Ak had。Try to act。Uns bite。Okay so the reason it's a little weird to error here too。

 is that this could just be like a delayed act。 So just because it doesn't delay any relevant bytes doesn't really mean there was an error。

 It just means that the act was delayed for a bunch of time And so there is nothing useful for us to do with it。

 It might be an error too， but it's more likely that it's just not something that's worthwhile for us to deal with。

So it is a little weird to return error。Yeah， exactlys。

We're accepting that the client did something wrong。But it's not really bad for us。So yeah。

 I think we're gonna， I think we should keep that as okay。 I agree with you， though。

 It is a little weird。 In some sense， like what we should probably do there is like log that something went wrong。

So down here right now we're in the established phase and the client。

 the other side is also going to know that we're in that phase， at least once they get our AC。

 they might send us an additional synac though， but we're just going to ignore that case for now。嗯。

Okay， so at this point， what we're going to do is this。Tear down the connection again。嗯。For now。

The one thing that's weird here is we sort of want to。嗯。Yeah。

 there's certainly a lot more stuff to do with timers herere that we're going to have to come back to。

 like， for example。Well。Well， actually， no， this is fine。 Okay。

 so we're going terminate the connection。 And so what we're going to look at then is two down here somewhere。

😊。

![](img/e709d71a082b45418e3b70befbd3ce3f_506.png)

Half of my connections， reset generation。Yeah， so this is where so to get to your point where。

About like what do we do in these cases， this is where you're supposed to generate a reset。

Whenever a segment arrives， that is not intended for the current connection。And that is so this。

 of course， in the in the closed case right where we're not listening。

 so that doesn't matter to us if we're in a non state。

 so if we're in like one of these initial stages，And it tries to acknowledge something not yet sent。

 So that would be。

![](img/e709d71a082b45418e3b70befbd3ce3f_508.png)

Uear。

![](img/e709d71a082b45418e3b70befbd3ce3f_510.png)

。

![](img/e709d71a082b45418e3b70befbd3ce3f_512.png)

Let's add here to。

![](img/e709d71a082b45418e3b70befbd3ce3f_514.png)

Imple state。

![](img/e709d71a082b45418e3b70befbd3ce3f_516.png)

嗯。Is。Non synchronized。And that's going to be true for state sin received is non synchronized。

And state established。As。Actually， I guess this is synchronized。



![](img/e709d71a082b45418e3b70befbd3ce3f_518.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_519.png)

Is nicer。False。Because that way down here， we can say if not self dot state dot is synchronized。



![](img/e709d71a082b45418e3b70befbd3ce3f_521.png)

If we're not synchronized， then according to reset generation。



![](img/e709d71a082b45418e3b70befbd3ce3f_523.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_524.png)

Send a reset。嗯。So specifically this case， so it acknowledges something that has not yet been sent。

 right， that's when this check fails。

![](img/e709d71a082b45418e3b70befbd3ce3f_526.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_527.png)

嗯。Or in a security level of compartment， which is not now I don't know what these compartments are。

 then we should send a reset。If for sin。

![](img/e709d71a082b45418e3b70befbd3ce3f_529.png)

Okay， so in this case， we should send out a reset packet， send。Reset。嗯。AndThat's gonna be。

It's really just going to be the name。So we're going to have this。

Sort of helper function that is just going to send a reset packet。Sli。Think think we want to buffer。

TCP head her here too。Because like the port numbers aren't going to change either。Right。

 so wherever we made this。So this is going to be ISS， and this is going to be window。

So now we're going to be able to in send reset， we're going to do。Self dot TCP dot。呃。Sa。Oh。

 it's another good， I think it's just RST。This is true。And what else like。

There's probably some like some rules for。What these should be。

Like these should probably all be zeros。Oh， you're right。

 Sendryset does not need a lifetime parameter。呃。Set payload L， it's going be self on TCP dot。嗯。This。

 and then we're going to have。Actually， here's what we probably want。

 We're going to have something like aend， which is， in fact， going to take a lifetime。

It's going to take a。Nick。嗯。Actually， it doesn't need a lifetime。 That's fine。

 It's going to take a payload。Of bytes。And that's gonna do。Specifically。

Self dot TCP dot sequence number。 So the sequence number is going to be self dot send dot next。

The acknowledgement number is going to be self dot receive dot next。嗯。

And the I P set payload L is gonna be self dot TCP dot。Heerlen plus Palo dotlin。

Is there anything else it needs to set， I don't think so。嗯。This is as U size。And then。

 it's gonna do this。And I guess whenever you call send， we sort of want。This。

And we're going to do u size。Because we're going to tell you。How much we wrote。嗯。So specifically。

 send， I guess this is really right。嗯。This is really we're implementing right。

It's a little sad that this buffer has to be separate。 Basically。

 this is where our program is no longer zero copy， right， because what we're gonna do is。😔，嗯。Wait。

 didn't we change this？Fe like we ended up changing this。Didn't we find that this was wrong。

 that it wasn't unwritten， but it was Buff dot L minus。That change like， get lost somewhere。

So this is going to sort of send the things we're always going to have to send whenever we send data。

呃。And then。It's going to create。嗯。Well， this isn't right。 This will be self dot IP P， self dot TCP。

 and then self dot buff。No。呃。And I guess this will be。Unwritten dot。Ri。😔。

I don't know if that's going to work， but。Right。嗯。So， let's see。We're writing out the headers。

 And then we're writing out as much of the payload as we can into Buff。 right。

 That might not be all of the payload。嗯。And then。嗯。Unwritten is going to be unwritten dot L。

And then what we're going to send out is。However， much we did do。 Yes， I think that's about right。

And now， up here。This no longer needs to do that。And self dot send dot next。Is already the I S S。

シししし。Yes。Actually， that's not quite right。😔，We haven't written the Sb yet。Yeah。And then the hope。

 of course， is that this is now going to be just C dot right。To the neck with no extra bites。

And then， this。Is going to be。There's one thing that's missing here and this is。We're missing。

The incrementing or sequence number。So self dot send dot next is now going be plus equals。

Paload bites。And if。TCP dot act。If。Self dot TP dot act。 No dot sin。Then。Then we also have to add one。

And f， we also have to add one。This should be。いい question？Though I don't see how it would ever fail。

I guess these should also be question work。It's like ether parse right error。

It's not really what I want this to be， but。No， we're just going to un do that and then just ignore this for now。

嗯。As U 32。And this is going to have to be a wrapping ad。Same with this。And same with this。

I feel like this has bitten me in the past。ThatThat does not assign。So in other words， here。Yeah。

 great。And if this is the case， then self dot TCP dot sin is gonna be。False。And then。D falsese。

And act is basically always true。Wapping ad is really convenient， it's true。嗯。Okay。

 so now we have right， which means that send reset can probably also do that。Specifically。

 it just sets these does not have to set。Paload anymore， probably。Oh， this is kind of awkward。

 We don't know how much of that we can。Actually， we do。Fit is self。

Size is going to be TCP header L plus I P dot header L。呃。

This is going to be standard min of Buff dot L。And this plus this plus Pao dotlin。

Because we can't write out more than the size of the buffer， basically。嗯。Iairment。

You 16 plus USA service。So that's going to be the size。That's going to write however much it can。

That's gonna be。Yep。And this， of course， is just going to call self dot right with nothing。And then。

 okay。Go in with Nick， I guess。So now we have a function for just sending data out self。t TCP，tP。

For sending just data out， we have one for sending resets。 and in this case。

 we have to send a reset before we return， there's also some like precedence level stuff。



![](img/e709d71a082b45418e3b70befbd3ce3f_531.png)

If the incoming segment has an AC field。The reset takes its sequence number from the a field of the segment。



![](img/e709d71a082b45418e3b70befbd3ce3f_533.png)

Its TCPH do。

![](img/e709d71a082b45418e3b70befbd3ce3f_535.png)

Okay。Number。Otherwise， the research sequence number is zero。😔。



![](img/e709d71a082b45418e3b70befbd3ce3f_537.png)

Take its sequence number。Which is really just self send next is equal to this。No， actually。

 that's not what we want。Sending this gets really quite weird。呃。It's going to be some to do。

Fix sequence numbers here。Because we already have right already uses like the state of the connection to fill in that。

 which is not what we want。

![](img/e709d71a082b45418e3b70befbd3ce3f_539.png)

嗯。

![](img/e709d71a082b45418e3b70befbd3ce3f_541.png)

So let's just leave this as a note for ourselves for the future。



![](img/e709d71a082b45418e3b70befbd3ce3f_543.png)

嗯。Any unacceptable segment。

![](img/e709d71a082b45418e3b70befbd3ce3f_545.png)

So this is something that we're going to have to deal with down here， probably。This is going to be。

Another to do。Handle。Synchronized reset。This business。Which I'm also going to leave for later。

Because so resets are basically。Reess are basically for if something goes wrong。

 And we're going to just assume that that it does not go wrong。 Unwritten is not the same as Buff。

 Unwritten is a mutable slice pointer to all of buff。 This means that when you write into it。

 it shrinks it。Removes us from the start so that the next ri will only write to parts that we haven't written to yet。

嗯。So it's actually not the same。

![](img/e709d71a082b45418e3b70befbd3ce3f_547.png)

Okay。This should be stated。Closing a connection， right， So this is what we want to do now。

 We want to close the operation close the connection to the。To the other side。

 which is basically saying like I have nothing more to send。 if you close a connection。

 you might still receive more data， you just can't send any more data。嗯。有。Yeah。

 so close is simplex as opposed to duplex。嗯。Yep。

![](img/e709d71a082b45418e3b70befbd3ce3f_549.png)

Okay， so。Also keep in mind currently we're not dealing with retransmissions at all。

 like retransmissions is something that will also have to be done here。



![](img/e709d71a082b45418e3b70befbd3ce3f_551.png)

But currently we're not doing them in the slightest。So specifically。

 because we want to terminate the connection， what we do is we send a packet that has a fin segment。

 so it just has the fin bit set。And we enter fin weight。



![](img/e709d71a082b45418e3b70befbd3ce3f_553.png)

Okay， so that's going to be self。ttCp。 fin。Is true。

We're probably so well we're currently sort of abusing the stored TCP header here a little bit because it also stores information about like whether we're in a F state bullets。

 I guess， to do。Needs to be stored。In the retransmission queue。

The reason why this is important is imagine that we have a bunch of data that we haven't sent yet。

When you send that data， the Finbit should not be set。

 it should only be set for the very last data packet you're sending out。

 whereas here we're just like setting it on the header for all subsequent TCP packets。

 which is not okay。

![](img/e709d71a082b45418e3b70befbd3ce3f_555.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_556.png)

And then we want to write to the ni， no bites。嗯。And then self do state is going to become F weight 1。

Which is a synchronized state。Of course， currently this looks a little stupid right we're setting established and then immediately moving on。

 but that's still what we like normally you would not do this right。

 normally this operation to close would be user triggered iss just that in this case we're choosing to trigger it immediately。



![](img/e709d71a082b45418e3b70befbd3ce3f_558.png)

All signals proceeding and including ven will re transmittedmit。



![](img/e709d71a082b45418e3b70befbd3ce3f_560.png)

呃。Yep， there's also a question of what happens if we receive a f。

So this is sort of in the established case， if not TCPh。 fin。呃。T， unemped。Or TPH dot。

 I guess actually or data dot。Or so if there's any data in the packet and it's not a final packet。

 we're just going throw up our hands and go。

![](img/e709d71a082b45418e3b70befbd3ce3f_562.png)

So if we， an unsolicited fin arrives。

![](img/e709d71a082b45418e3b70befbd3ce3f_564.png)

Then what that means is that we want to， basically， we want to act their f。

 and then we want to terminate ourselves。 But we've already sent a fin。

 So like this is unlikely to happen。

![](img/e709d71a082b45418e3b70befbd3ce3f_566.png)

This is going to end up being a simultaneous close。



![](img/e709d71a082b45418e3b70befbd3ce3f_568.png)

嗯。But in either case。So I guess in this case， this is the same as state being thin。

Being Fin rate  one。 Okay， but in this case， we receive that we can act it until the user connection is closing。

 Okay， so we're gonna do self dot right。

![](img/e709d71a082b45418e3b70befbd3ce3f_570.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_571.png)

To the ni。So this is gonna act that act that fin。

![](img/e709d71a082b45418e3b70befbd3ce3f_573.png)

Right。呃。Receiving a fin。Yeah， the we'll respond with a close upon which the TCP can send a f to the。



![](img/e709d71a082b45418e3b70befbd3ce3f_575.png)

Okay， so in this case， all we really do is we just like act that they wanted to f。嗯。



![](img/e709d71a082b45418e3b70befbd3ce3f_577.png)

So the question is， what happens here。 Okay， so in this case， were B。嗯。Oh， what's close weight。

 though。So this doesn't mentioned that， but it looks like。If you receive a f。

 you should enter close weight。Oh， this is RLs。 Rs works totally fine for me。Sometimes a little slow。

 but that's about it。

![](img/e709d71a082b45418e3b70befbd3ce3f_579.png)

Okay， so in this case， we do want to go state is。Close weight。Okay， so close weight is another state。

嗯。And it is also synchroned。So this is going to be stayed to close weight。



![](img/e709d71a082b45418e3b70befbd3ce3f_581.png)

嗯。And in this case。

![](img/e709d71a082b45418e3b70befbd3ce3f_583.png)

Oh， I see。See， this is where we're sort of hijacking the setup a little。Specifically。

We're sort of we're cheating a little here right because because of this， you're going to enter。

 we know that you'll be in thin weight like this cannot happen because you must you must get this first to get the connection to be established。

 so we're just going to do this and say this is unimplemented。



![](img/e709d71a082b45418e3b70befbd3ce3f_585.png)

Because currently it can't happen。 And then if we're in F weight 1。And so that's this case。 We close。

 We're in Fin weight 1。 we send。We send our fin。And now we're waiting for them to act。

 and at some point， they're going to act our fin。

![](img/e709d71a082b45418e3b70befbd3ce3f_587.png)

A。And we're not going to let them send us any data。 That's not something we support yet。

 when we eventually get that。

![](img/e709d71a082b45418e3b70befbd3ce3f_589.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_590.png)

Then， we enter closing。Okay， so we're going to ignore close weight， but we are going to have closing。



![](img/e709d71a082b45418e3b70befbd3ce3f_592.png)

So this is。So， here。Sequence number 100。😔，Sorry， sequence number 300 is where we sent our fin。

 which means that our fin is 301 because the fin is its own bite。 So when they hear act 301。

 that means that now we know that we should be closing。



![](img/e709d71a082b45418e3b70befbd3ce3f_594.png)

Right， so down here， actually let's。This should be closing。So down here， when we get Fin weight。

 and this turned out to if this check was true， that means that the only thing they can possibly have act is our fin。

Right， because there's no other data they。This is the same argument as here that they must have acted our fin since we detected at least one act byte。

 and we have only sent one bite， which is the fin。Let's make these wrap the same。嗯。

How did I double exclamation mark this again？And so in this case。

 what are we supposed to do we're supposed to。

![](img/e709d71a082b45418e3b70befbd3ce3f_596.png)

Ak their fin， which we do with this。 Do we include fin in that。

 We're not supposed to include fin in that？ That's going to be awkward。



![](img/e709d71a082b45418e3b70befbd3ce3f_598.png)

I guess that means self TCP F Finn is false。

![](img/e709d71a082b45418e3b70befbd3ce3f_600.png)

嗯。And now we enter closing。And now。What is this， though。Why are we receiving anything here？Like。

 why are they。One is this act of the end that seems really odd。嗯。

I was found a clothes in which can send a f to the L TCP。

The TC P then waits until its own fitness acknowledged whereupon its deletes the connection。Okay。

 so at this point we now enter time weight。

![](img/e709d71a082b45418e3b70befbd3ce3f_602.png)

So there's also not a closing， that's just a lie。

![](img/e709d71a082b45418e3b70befbd3ce3f_604.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_605.png)

Well， I guess sort of。

![](img/e709d71a082b45418e3b70befbd3ce3f_607.png)

It's like if is closing even in the diagram。The like giant diagram。Yeah， then you send an act。

 And if you receive anything， you go to time weight， I see。 So if we're in closing。



![](img/e709d71a082b45418e3b70befbd3ce3f_609.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_610.png)

呃。How did this work， so we were in established？We sent a Finnin， and then we entered Finw 1。Yes， yes。

 In Fin weight 1， we receive an act of fin。

![](img/e709d71a082b45418e3b70befbd3ce3f_612.png)

Yep， so it has fin set， right， otherwise unimplemented。

 and it is actinging at least one byte because of our checkup there。



![](img/e709d71a082b45418e3b70befbd3ce3f_614.png)

嗯。 then。I see， that's if we receive a fin， which is not we're going to receive。



![](img/e709d71a082b45418e3b70befbd3ce3f_616.png)

We're going to enter then I C。 So in this case。We're gonna go。😔，Self thought state is thin。Finway 2。

These are excellently named， but thats what they're called in the spec， so you know。Sted F weight 2。



![](img/e709d71a082b45418e3b70befbd3ce3f_618.png)

Okay， so all we really do is when we get that a because we go to Finway2。



![](img/e709d71a082b45418e3b70befbd3ce3f_620.png)

嗯。And then if we're in Finway 2。Then at some point， we're going to receive a fin from them。Oh， I see。

I don't think this check necessarily means that they must have act at least one by。

I think it means that they act a valid by。They could still。No， if they act no bys。

 we would not get here。I think that's true。 but that makes it a little weird because it means that。



![](img/e709d71a082b45418e3b70befbd3ce3f_622.png)

That f that we get here is not going to act anything that we have。



![](img/e709d71a082b45418e3b70befbd3ce3f_624.png)

Send， so it's not going to act any bytes。 So let's think about this， right so。呃， if。

What are we requiring up here， We're requiring that。They act。Yeah。

 they have to be acting at least one bite because of this check。Also。

 doesn't right have to increment that？Oh， I see。So here we should also update。



![](img/e709d71a082b45418e3b70befbd3ce3f_626.png)

Does it say right here that how we update these？嗯哼。Yeah， that's fine。That's fine。Yeah。

 so my guess is they go through this in more detail here。嗯。Once a connection is established。

 data is communicated by the exchange of segments。Retransmissions center data keeps track of the next sequence number to using in the variable send next。

 yes， we already have that in our right function that makes sure to modify send next。呃。

The receiver of data keeps track for the next sequence number to expect in the variable received dot next。



![](img/e709d71a082b45418e3b70befbd3ce3f_628.png)

Okay， so here。We're going do something like。

![](img/e709d71a082b45418e3b70befbd3ce3f_630.png)

One item going to be self received next。呃。

![](img/e709d71a082b45418e3b70befbd3ce3f_632.png)

Is going to be。I think， W end。No， that's the end of the window。 It's going to be。Seek an oh。

 I see an Er this。Should be wrapping a of that。嗯。And I think， in fact。This is what the next。

This is the next so if we get through this check， that means that we received at least one by。

 and now the。Next thing we're expecting to receive is whatever follows that， right？

 So the sequence number of the first byte plus the length of the segment。

 which is going to be the first index that we haven't seen。 Okay， so that's this sentence。

 the sender of data keeps track of the oldest unacknowledged sequence number， right。

 So up here at this point， we know that something got acknowledged。

 And so therefore our unacknowledged is going to be。



![](img/e709d71a082b45418e3b70befbd3ce3f_634.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_635.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_636.png)

Again。If the data flow is momentarily idle and all。The data sent has been acknowledged。

 and the three variables will be equal。

![](img/e709d71a082b45418e3b70befbd3ce3f_638.png)

That's probably true， okay， so is this true？Ac， so the act value is the。啊。The next bite。

 they're expecting。Which means it's the first bite that is unacknowledged。 Yes， so this is true。



![](img/e709d71a082b45418e3b70befbd3ce3f_640.png)

嗯。All right。😔，When the sender creates a segment and transmits it， the sender advances send dot next。



![](img/e709d71a082b45418e3b70befbd3ce3f_642.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_643.png)

Yep， so that's here。

![](img/e709d71a082b45418e3b70befbd3ce3f_645.png)

When the receiver accepts the segment， it advances receive dot next。 That's here。



![](img/e709d71a082b45418e3b70befbd3ce3f_647.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_648.png)

And sends an acknowledgement， right， So in theory here， we should also acknowledge that， right。嗯。

But we don't currently have a process for sending data or for doing things like timeouts like we don't know that we need to act this。

 but we happen to act it because we write right here。



![](img/e709d71a082b45418e3b70befbd3ce3f_650.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_651.png)

嗯。So I guess like here。

![](img/e709d71a082b45418e3b70befbd3ce3f_653.png)

Make sure this gets back。呃。When the。Data sender receives an acknowledgement it advances UNA。

ItDs in measure of delay。The amount by which the variables are advanced is the length of the data in the segment。

Shi。😔，Why is a push。Okay， so retransmissions， communication of urgent。

 managing the window is not currently so that we're doing it all。That's fine。

Interfaces we're going to ignore for now。呃。That's fine is talking about how send receiving clothes should work。

 so that's something we'll end up implementing as a sort of higher level interface after a while。

Vent processing。Yeah， so this is like a possible way to structure your implementation of TCP。

That's fine。 This doesn't seem particularly important。I mean， this is probably useful。

 but it's just not what we want。 So this， this does give us all of the。

All of the state transitions are explained here， right。

 like if you are given an open call and you're in the closed state， then do the following。

Which is pretty nice。

![](img/e709d71a082b45418e3b70befbd3ce3f_655.png)

And so in our case here。

![](img/e709d71a082b45418e3b70befbd3ce3f_657.png)

Were in。We're in these like accept， I guess。But if receive in this， that's fine。



![](img/e709d71a082b45418e3b70befbd3ce3f_659.png)

This is not what I want。In fact， what is it we want， or what are we missing？



![](img/e709d71a082b45418e3b70befbd3ce3f_661.png)

Here。Finway 2。 I think that's the last part we were at。So where's our big diagram。

Of all the things here。

![](img/e709d71a082b45418e3b70befbd3ce3f_663.png)

So Finway2 here at this point， we now have to make sure that our f has been acted。No， sorry。

Fin wait one as we wait for a fin to be act。 And so the observation is that we will never get to hear because up here。

We're going to get a message that isn't acting anything。Which is a little weird。Wait。

 if A is send out next， no， that's fine。Yes， it's not necessarily acknowledging。 okay。

 it's not necessarily acknowledging it by because it's allowed to be equal to next。But。

What if these values are equal？They can't be， I see。They're going to be actinging， this is weird。

Okay， so what I'm trying to figure out is in this case， what we want is for。嗯。If we get an act。

 it should be acceptable for that act to not be acting any data because we might not have sent any data。

 right， which I think this check allows for。Assuming that。Unacknowledged is always less than next。

Becauseuse if unacknowledged is equal to next， then there's no value you can give to act that would be O because it wouldn't be greater than unacknowledged。

So the question becomes， what is unacknowledged set to if all your bites are acknowledged？



![](img/e709d71a082b45418e3b70befbd3ce3f_665.png)

嗯。The oldest unacknowledged sequence number。嗯。Actually， maybe this specifies what we should do。

 So specifically I want what happens。On。Segment arrives。If the state is listen。Xin。That's fine。



![](img/e709d71a082b45418e3b70befbd3ce3f_667.png)

Yeah， so this is all the stuff that should be happening in our accept。 Okay。

 so this is actually kind of handy to read through。



![](img/e709d71a082b45418e3b70befbd3ce3f_669.png)

Um。Se okay， so this is someone who's trying to connect to us basically。Said received out next。

To be the sequence number plus one， that's what we have。IRS is at to， that's what we have。

Any other controller text should be cud for pressing later。 I S S should be selected。

 and a sin segment should be sent of the form。

![](img/e709d71a082b45418e3b70befbd3ce3f_671.png)

呃。

![](img/e709d71a082b45418e3b70befbd3ce3f_673.png)

Se is ISS Act is received dot next， which our right takes care of。



![](img/e709d71a082b45418e3b70befbd3ce3f_675.png)

呃。Sequence numbers should be ISS， which is our sequence number is set to send dot next and send dot next is send to ISS。



![](img/e709d71a082b45418e3b70befbd3ce3f_677.png)

And we set both sin and act in the fields。嗯。

![](img/e709d71a082b45418e3b70befbd3ce3f_679.png)

Then send dot next is send set plus equals 1， which will be true for us because the payload is 0 bytes and sin is set。

 so we add one。UA to ISS。And then， okay， so self thought。Send dot。Oh。

 U and A is already set up here for the sender to ISS， great。



![](img/e709d71a082b45418e3b70befbd3ce3f_681.png)

Pctions say it should be sin received。Great。So now we are receiving stuff in the sin received state。

First， check sequence number。

![](img/e709d71a082b45418e3b70befbd3ce3f_683.png)

Okay。Oh， interesting。 First， check the sequence number。So not check actx first。



![](img/e709d71a082b45418e3b70befbd3ce3f_685.png)

Even though the acceptable act check comes first。Initial test and arrival。

There are four cases for acceptability。

![](img/e709d71a082b45418e3b70befbd3ce3f_687.png)

Okay。So。This is okay。😔，If。Yeah， it's fine。So I think what we really need to do is is move。

This check down。 So the first thing that should happen。Is do。



![](img/e709d71a082b45418e3b70befbd3ce3f_689.png)

A sequence number check。 So that's the check we already have。 It just。

 that should happen before that check。If the income can be segment is not。



![](img/e709d71a082b45418e3b70befbd3ce3f_691.png)

Acceptable， an acknowledgment should be sent in response。Oh， that's interesting。So to do。

 if not acceptable。Send。

![](img/e709d71a082b45418e3b70befbd3ce3f_693.png)

呃AQ。

![](img/e709d71a082b45418e3b70befbd3ce3f_695.png)

Allright。

![](img/e709d71a082b45418e3b70befbd3ce3f_697.png)

After syndi act， drop it and return。So this idealized segment pan X does not exceed the window。

That's fine。Second， check the reset bit。That week。Nor it's not set。 then security in presence。

 which we ignore。 Then check the S bit。Oh， interesting， so the order here is really weird。



![](img/e709d71a082b45418e3b70befbd3ce3f_699.png)

嗯。

![](img/e709d71a082b45418e3b70befbd3ce3f_701.png)

Yeah， that's an error fine。So now check the a field。 If the act bit is off。

 drop the segment and return。

![](img/e709d71a082b45418e3b70befbd3ce3f_703.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_704.png)

What is how do you look for that bit even？Oh， I see。So down here， we're going to do。

According to this。

![](img/e709d71a082b45418e3b70befbd3ce3f_706.png)

Not tcph。ac。Then return， okay。

![](img/e709d71a082b45418e3b70befbd3ce3f_708.png)

Otherwise， if we're inson received。So this check is not even going to happen。Yeah see here。

 So these states don't check for the don't do the act number check。



![](img/e709d71a082b45418e3b70befbd3ce3f_710.png)

That's when I thought sneaky。 Okay， so if we're in sin received。呃。

So this is going to be iflet this or。State。Established。Is self do state。

 Then we're going run the act check。

![](img/e709d71a082b45418e3b70befbd3ce3f_712.png)

Right， because this is done for。Both of these。Oh， and soon received。The check is actually different。



![](img/e709d71a082b45418e3b70befbd3ce3f_714.png)

Interesting。Okay， fine。So in soon received。We're gonna do。



![](img/e709d71a082b45418e3b70befbd3ce3f_716.png)

This。If not is between here， we're going to allow this to be wrapping sub 1。



![](img/e709d71a082b45418e3b70befbd3ce3f_718.png)

嗯。If let this。Self do state， so。If this， then。で。Great。



![](img/e709d71a082b45418e3b70befbd3ce3f_720.png)

ok。啊。The same gentlemen is not acceptable from a reset。



![](img/e709d71a082b45418e3b70befbd3ce3f_722.png)

Else。

![](img/e709d71a082b45418e3b70befbd3ce3f_724.png)

To do reset。

![](img/e709d71a082b45418e3b70befbd3ce3f_726.png)

哎。So that means this check is actually just like。Not what we should do。嗯。Alright。

 so we'll leave that up there and now。

![](img/e709d71a082b45418e3b70befbd3ce3f_728.png)

呃。Continue processing。Okay。What does continue processing mean， though， I guess， here。

 So now we're gonna match onse on state。

![](img/e709d71a082b45418e3b70befbd3ce3f_730.png)

And if， forre in state established。

![](img/e709d71a082b45418e3b70befbd3ce3f_732.png)

呃。

![](img/e709d71a082b45418e3b70befbd3ce3f_734.png)

Rui。Great， so that means that this， let' let's deal with this a little bit later。

 So this is the part where we want to close the connection right specifically this means that here it shouldn't be possible for us to be in this state。



![](img/e709d71a082b45418e3b70befbd3ce3f_736.png)

If we're in established， then we're going to make sure that this was a valid thing for us to get act。



![](img/e709d71a082b45418e3b70befbd3ce3f_738.png)

And then we're going to set that equal to AN， great。



![](img/e709d71a082b45418e3b70befbd3ce3f_740.png)

And then。

![](img/e709d71a082b45418e3b70befbd3ce3f_742.png)

There's a bunch of stuff we have to do here that we're not going to do。For now。

 except we are going to assert that。Data is empty。

![](img/e709d71a082b45418e3b70befbd3ce3f_744.png)

Have sent。Swin is an offset， Yeah， this is recomputing the window sizes。



![](img/e709d71a082b45418e3b70befbd3ce3f_746.png)

And。I guess actually here is where we want to do this。Then we're going to fin and enter Fin weight。



![](img/e709d71a082b45418e3b70befbd3ce3f_748.png)

If we're in F weight。

![](img/e709d71a082b45418e3b70befbd3ce3f_750.png)

In addition to the processing for the established state。Oh， interesting。



![](img/e709d71a082b45418e3b70befbd3ce3f_752.png)

Okay， so this。

![](img/e709d71a082b45418e3b70befbd3ce3f_754.png)

So I guess this is actually just。If。It's interesting that these are actually sequential as opposed to。

As opposed to doing all of them at once。Okay， and now。嗯。

We're going to match self dot state if we're in fin1。For Finn is now acknowledged。 So if self do。

Send dot E an a。Is equal to self and I S S plus 2。Yeah。

 so the reason this check has to be like this is。We want to check that we have an acknowledgement for both the sin that we initially sent and the f that we sent following it。

hich means that the unacknowledged should be the by following that。Our f has been act。

And in that case。This is also if let。Is equal to self dot state。Then self do state is state Finway 2。

And then up here。It's。If。Finway 2。

![](img/e709d71a082b45418e3b70befbd3ce3f_756.png)

Oh， weird。嗯。Then， in this state。If the retransmission queue is empty。

 the user's clothes can be acknowledged， but do not delete the TCB。



![](img/e709d71a082b45418e3b70befbd3ce3f_758.png)

Okay， that's fine。 so we won't to actually do anything in the。



![](img/e709d71a082b45418e3b70befbd3ce3f_760.png)

In this case， what we will look for is presumably down here。Yeah。Process segment text。😔。

So somewhere down here， it's going to be like if TCPH dot fin。



![](img/e709d71a082b45418e3b70befbd3ce3f_762.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_763.png)

嗯。Then。

![](img/e709d71a082b45418e3b70befbd3ce3f_765.png)

Here， it really depends on on state。 but we're only going to deal with the case where。



![](img/e709d71a082b45418e3b70befbd3ce3f_767.png)

State is Finway 2。And in that case。

![](img/e709d71a082b45418e3b70befbd3ce3f_769.png)

We're done with the connection。

![](img/e709d71a082b45418e3b70befbd3ce3f_771.png)

Herecent theory。And we shouldn't need to send anything more。



![](img/e709d71a082b45418e3b70befbd3ce3f_773.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_774.png)

There is the question， though， of when we send our a。So I think is going to be basically on timeout。



![](img/e709d71a082b45418e3b70befbd3ce3f_776.png)

Instead， I think we're gonna。Eagerly act that right here。By doing this。Whereas our right。

 this resets fin， great。So this is going to put us into time weight。

Which is a thing that we don't have yet。嗯。Okay， so in theory， we now have like a full。

I think we have a full circle now of being able to basically set up and tear down a connection。

 It's no data being sent， but it does do the entire sort of handshake protocol。

 including both set up and close。So let's see what happens if we try to， oh， that's not too bad。

Compare。Wai哦。2，86。嗯。Anything else we're gonna。Says un implemented。う。I mean。

 I have no idea whether this actually works， but let's see what happens if we try to start this。Ha。

Okay， so we're going to need some logging here。But。It did get the sin act。Oh， interesting。

Why is it rescending the sin。That's very interesting。That makes it seem as though。

We're like doing something wrong。Specifically， I wonder whether the。

I'm pretty sure that act should be won。😔，M。

![](img/e709d71a082b45418e3b70befbd3ce3f_778.png)

That's interesting。I wonder if we should try to fire up wire shark here and see what it gives us。

 So if we start this up on。

![](img/e709d71a082b45418e3b70befbd3ce3f_780.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_781.png)

Tn0。

![](img/e709d71a082b45418e3b70befbd3ce3f_783.png)

Okay， and see what。This gives us。

![](img/e709d71a082b45418e3b70befbd3ce3f_785.png)

So。GCP aha sequence number 0。<|OTHER|>Acknowledgement number zero。

IPV4 total length exceeds packet length。😔。

![](img/e709d71a082b45418e3b70befbd3ce3f_787.png)

Oh okay， well， that's the first mistake。It looks like。

the payload size should not include the IP header。That is totally true。嗯。But it sort of has。

 that's awkward。呃。Minus self I P headerland。As you size So the reason this is awkward is the the size of the packages cannot exceed buff。

 including the IP header， but when we set how large the payload of the IP is。

 we should obviously not include the header。

![](img/e709d71a082b45418e3b70befbd3ce3f_789.png)

That's fine。 So let's run that again。And then restart this。Oh。



![](img/e709d71a082b45418e3b70befbd3ce3f_791.png)

Why does Sre shark not let me？No。This no。

![](img/e709d71a082b45418e3b70befbd3ce3f_793.png)

I think it's confused。Not what I wanted it to do。Well， apparently， that's not helpful。哈。

That is very weird。

![](img/e709d71a082b45418e3b70befbd3ce3f_795.png)

Why is， why does starting wirereshark bring me to this。



![](img/e709d71a082b45418e3b70befbd3ce3f_797.png)

Why isarch is not running here。

![](img/e709d71a082b45418e3b70befbd3ce3f_799.png)

Very weird。Okay， let's try that again so starting this。Watch ton0。😔，And then send a packet。And then。

 kill this。Okay， so now this is right。 And here this sent。Sequence number 0， Act number 0。😔，Here。😔。

We act number one。And send number 0 with our sin。😔，Ha。It could be the windows too small， but。

Theres an act of the segment of frame 2。Yeah。So that makes it seem like。This act is correct。

But why is it not acting back。H。Let's see oh， we have might be that this document can help us here。嗯。

<|OTHER|>No， no， that doesn't seem helpful。

![](img/e709d71a082b45418e3b70befbd3ce3f_801.png)

嗯。Hm。😊，All the values seem right。 I mean， I guess it could be that the windows is like too small。

 but。I don't think that should make a difference。H。Also。

 why is our program not responding to that act， like when it gets the sinrytransmission？

I think it should really just respond to that， which it's not。So that suggests that in here。

It's do good old print bugging。Wait， what。So it never gets there。So when we get a packet。Oh。

 we probably throw it away because we think it's。Yeah。Okay， so。We throw it away。

 So this is the case where。If it's not acceptable when the word is supposed to act。嗯。So here。

 I guess what we could do is。What we really want is like， okay。Is。True， no， false。This is false。

 This is false。This is false。This is true。And。Yes。This can probably be simplified。

 this is more because I want to see what happens here。呃。If not， okay。Then， we wna act。

And then we w to return。呃。What do we want to do here， We want to do。Send out next。😔，See you not next。

 so I think this is just a right。Where I do right。So let's see if we now start sending those acts。

Yeah， like it's even recognized them as duplicate acts。So why is it not accepting our？

So like a message for this。 I don't think so。哈。I don't know what's going on。

 I don't know why It's doing that。I don't know why it's doing that either。嗯。😊。

It's a very good question。Like。Surely， let's do， let's try this first。Instead of doing this。

Do you like。Yeah， that's gonna。The back。嗯。So，8000。 That seems fine。

And now we're going to do this to 8000 on。On tos。1，2，7。0，0，1。And let's look what that looks like。

Okay， so that's what it looks like when you have a real one。And this is what it looks like。

When you're trying to do it to us。So what's the difference between these here？Oh。

 it's the sequence number of the。I see。That's what's wrong。Right。

 like that this needs to point to the first bite that we are sending and the sequence number of the。

First， bite we are Cindy。 Why is that not0， though。Oh， the first bite in the payload。Oh。

 that's awful。 So that doesn't include the sin。I see that's where we're wrong。

 So specifically what should happen is。When we initially do this。

The sequence number we should include。Is actually this。Plus1。 So next up here is this plus1。Yeah。

 let's try that。Oh， man。Let's try there again。So watch that。 and then this。No。Okay。

 how's it different this time。Seek a still 0。😔，Did I like not save the file？

The sequence number is sent to。Self dot send dot， next。Self， send next。IS S S plus one。

What am I missing。😔，Hm。Why is that still zero？Self。tcp。 sequence number。😔，It's equal to self dot。

 send dot next。😔，Check that again。Also， why is there seek zero？Like why up here？Oh wait no。No。

 even in the Luai case。It's 0，01。Wenwen。So the old behavior was the correct one。

Question just is like， why is this not working？I wonder if this is like the Linux kernel。

 because we are interacting with Linux here， right， like the。The kernel is probably。

Like requiring you to include some of this business。 And because we're not specifically。

 it's just like secret value， whatever the secret value is。



![](img/e709d71a082b45418e3b70befbd3ce3f_803.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_804.png)

嗯，Pent dinnerina。Yeah， there's something， something weird going on it。

 what we're comparing is like this packet。Which is what the real server sends。To。

All this packet number two。 So， of course， there's a bunch of like more。

TCP headers that are being said in the other one， but the fundamentals seem to be right。

 Specifically， we replied to the correct port。To the correct IP address。嗯。We set c equals0。

 act equals1， we set our own window， length is 0。So what are we missing？

Like there are other values here， but they shouldn't matter。嗯。Oh， it's window scaling。

Like almost positive it's window scaling。嗯。

![](img/e709d71a082b45418e3b70befbd3ce3f_806.png)

Specifically。Just thinking back to this， right， which says things you must implement。

RFCC 1122 talks about where is it？呃，I。Transport protocols， TCP。嗯。One imports push。Window size。

Urgent pointer TCP options。😔，Must implement both sending and receiving the maximum segment option。

Should sentinmesis segment。😔，Must implement both sending and receiving。Yeah。Oh interesting。

 there are also errors in the state diagram。Yes， this is indeed using RLS。嗯。Closing a connection。

D communication。Its like congestion control stuff， retransmissions， managing the window。Okay。

 that's fine。<|OTHER|>Okay， that's probing， this is all。None of this is stuff。 that matters。Okay。

 so it seems like the only thing we're not supporting that this says that we must support it is。

Maximum segment sizes。

![](img/e709d71a082b45418e3b70befbd3ce3f_808.png)

Okay， there's an alternative explanation here， which is very stupid。呃。

Which is that we need to compute this。I don't think that's the case。I mean。If that were all。

 that'd be great。 But I don't think that's enough。That was all。What。

Why did this not give me an error saying the checksum doesn't match？Okay。So。In theory。Oh。

 I forgot to。We start the server。We monitor it。We send this。And now。Okay。

 now we correctly get the act。So we act them。 They act us。 We send a thin act。No。

 they send a fin neck。Oh， interesting。 Why did they send a fin neck。

Why aren't we the ones sending the Finac。Oh， wait， no， this just means that。Did we send it first。

 I thought we send it first。They send an act。Then they send a Finck， okay。

 so that's not actually something that we implemented。

 which is specifically if we are in the established state。And they send a fin。呃。We're established。

And Gods stuff。And then I sort of want to do something like debug self TCP Fin。And probably。Also。

 TCP，H dot fin。So we never get to that，huh？Why do we not get to that。Wait， this shouldn't be a yes。

 This shouldn't be a no。That's why。Great。Try that again。Okay。So if we try to listen again， not what？

So。Oh。Okay， they sent a sin to connect。 We sent a syn act。 They sent an act。

 We sent a fin and an a of nothing。 They a are f。They act are thin， and in theory。Wait， why is this？

Why is anything running on that right now？Let's try that again。They send a sin。 We send a sin act。

 They send an act。 Now， the handshake is done。 We send a thin a。 They send an a。And then。

 they send a。Fhin a that， in theory， we should respond to。But it looks like we do not。

Or we probably just don't print anything。 actually， is what's going on。Specifically， in this case。

 we enter f weight。 and in this case here。They've closed。No， they've act our fin。 And this is。They。

Let's help ourselves with a little bit of。Stuff。Okay， let's see what happens。

Establishing God's stuff。So， there's something。Still something we're missing。 specifically。

 werere not handling their fin。Right， so here。Is where we end here is where they act that we finished。

 here' is where they tell us that they have finished。And now we're supposed to act them。

 and yet we're not。嗯。So the question is， why not？😔，呃。Go。So we do get a packet there。

 are we just like throwing it away？Because that would be unfortunate。We're not throwing it away。

Is the good old print bugging， right。Okay， so we got packet and then we did five ones。

We could add one。2，3，4，5。So the question is， do we go in here？Well， we didn't do this。

So this suggests that fin is not set。In the packet we got from them。

 Although that seems odd because wasn't that the whole point。Oh， that's that a。Oh， I see。

This is just dealing with their act。But then the question is， why are we not getting。

Why are we not getting this fin？And in fact， isn't this wrong。

 why shouldn't they be acknowledging too？But regardless。Why aren't we seeing the packet？I wonder。嗯。

Cause we're also not crashing。So。So what's going on here？Oh。哼。Okay， so here I just turned off。

Here I just like terminated。The sender， and then we did indeed get true。And then we panicked at 315。

Because we weren't in Finway too。How are we not in Finway 2， though。I sort of want to compare this。

And this。Cause it seems like we're not doing that correctly。Hot packet with false。So if we do this。

What do we get。We get we basically only receive two packets， okay， so what are those two packets？

Okay， the first packet we got。Was this one。No。😔，I don't think that's， wait。

 that's here is just confused， let's try that again。Okay， so we got two packets。

 We got this packet and then this packet。 Both of them do not have fin。

 So the first packet is this one。 The second packet is this one。

And it's true that this is not acting our fin。 but why are we not receiving this packet。

When we send this， we should still be receiving that。But it's as if we just never get that packet。

And in fact， it's sent again later， and we still don't receive it。Ha。Yeah。

 I don't know why we don't receive that one。I mean。

 the only thing I can think of is that main is dropping it。Like。I mean， we could try。

Seems a little odd。You see， there's no packets being ignored。And so we're just not getting。

 we're not getting this packet。And I don't know why。😔。

Like we're not receiving at all after we send this， we don't receive anything。Hm。

There's no error either。 Well， What does work， though， is if I。If I connect。

 and then I sort of terminate that connection intentionally。Then。嗯。Then we get a packet with true。

HmThat's very weird。I don't have a good answer for that。Here we do get a fin packet， though。 Okay。

 so here what I'm doing is I'm starting it， and then I'm pressing control D。

 which immediately terminates the input。And so at this point， you'll see。What。W。

 did I not start that， Thought I did。So if I do this。Do you bunch of stuff。terinate that。

 And then it crashes。Luck。This a we don't get and the thin a we don't get。Or rather。Yeah。

We don't get either of those， see， we get one。We get 1，2。

We get two packets before this unexpected one， which is the version6 packet。

 and then we get one packet。Which means we get one，2。And then we don't get either of these。

 but then we get this one。I don't know why we're not getting these in between， oh to 8，000。

So that's an old one。Oh， I wonder whether this is just like old leftover stuff。 Like。

 if I now do like 9001 just to show the ports are different。Why do this。Wait for one of those。

AndThen， exit this。No， there's still this packet really should be getting through。

Although it does sort of go through here， I guess。But。I don't know if that's the same。

Let's print out what it is the。嗯。A this。TCPH dot sequence number。No， that's suck。X， TCP，H dot。

Acknowowledgement number。Yeah， so we're expecting to see。Three packets，1，2，3 with Si 1，1，0，1，1。

 and act 1，2。What does it actually get？It gets。That's not a sequence number of zero。

I think this is like adjusting sequence numbers， which is not okay。This acts2， so that acts are sin。

No Xs1 nas are sin。X 2。Sak are Finn。So this seems like。Down here。Established。

Then UA should be set to2 at that point。So why is it not？We're establishing gods of that x1。

 So the question is this packet。This packet right here， Acts2。

 we're never keeping track of the fact that we act that packet。Even though。

We should be in the established state。Oh。I know why it's because we。

It's because we immediately try to terminate the connection right down here。

 we're immediately changing away from the established phase and we're not doing this processing。

 even if you are in the finalized stage。So this should be state。Fin weight 1 or state， F weight2。

 and then we sort of only want this if let state establishb itself。

Dot state because this is sort of hacky， this part down here。All right， try this all for size。Great。

 so now we realize that they've act our f。 And so now when this terminates。They've acted our f。 Okay。

 we didn't crash。 So that's good。 What happened here。 We sent the Finn Act。 They act that。

Then they sent us a f a。Which we eventually act。Nice。

So now that connection has gone away and we've gone full circle。

 we've sort of fully established a connection and torn it down。

Right there's a TCB retransmission in here， which I don't know why。

Things like for whatever reason we didn't act the first one。嗯。Now， okay。

 so I think we're going to stop there for today。Let me get rid of these， like E prints and stuff。嗯。

There's still a question of why we never got there， but okay。嗯。

I think we're gonna stop there because now we have like a thing that can talk to a TCP client。

 It doesn't actually exchange any data yet， which I assume then is going to be what we'll cover in the in the next stream。

 because then we'll need to do with deal with like。

Re transmitmit cues and and timeouts for sending acts will need to deal with congestion control and window sizing。

 but at least now we have sort of the basic setup working where we can we can at least talk the protocol and handle the handle the appropriate messages and send the appropriate messages and sort of see that everything goes through。

I will， I guess I'll push this。 There's no reason really not to。



![](img/e709d71a082b45418e3b70befbd3ce3f_810.png)

嗯。Still。まYeah。TCP。A learning experience in employment。PCB。Just。Like so。



![](img/e709d71a082b45418e3b70befbd3ce3f_812.png)

And then we'll do。I guess we will do。

![](img/e709d71a082b45418e3b70befbd3ce3f_814.png)

![](img/e709d71a082b45418e3b70befbd3ce3f_815.png)

嗯。So remote a origin， this。

![](img/e709d71a082b45418e3b70befbd3ce3f_817.png)

Nice， okay， so in theory， all the code should be up there if you want to take a look。Okay。

 so what we're going to do is end the stream here because it's sort of a good breaking point where we have we have sort of one cycle of a TCP connection working and then we can cover sort of data management and congestion control and all of that stuff in the next stream I think the next stream will be in about。

Maybe in about three weeks it's a little hard to say。

 but the plan is to keep going on this as as you can see from implementing as well。

 there's like a lot of stuff to cover here and a TCP stack is like a nontrivial effort that we're doing so my guess is this will end up being three streams before we get to something。

I already have the key as H added， but I have it auto expire。

 I don't like having key material in my memory。嗯。Yeah， there's a lot of cover。

 so my guess is that will go through probably three streams on this like unless either we get really far the next stream or people complained they don't want to see any more about it。

 but in either case， my guess would be about three streams and as always。

 if you want to vote on upcoming stream ideas， there's a site where you can vote this is how we ended up doing TCP in the first place。

 currently the sort of next comer is to do another open source contribution stream which is really fun and but that will then be not for quite some time because we still want to make some more headway on implementing TCP before we sort of leave that behind。

So in that case， I guess thanks for watching everyone and I will see you next time。Bye， everyone。

Thanks for watching。

![](img/e709d71a082b45418e3b70befbd3ce3f_819.png)