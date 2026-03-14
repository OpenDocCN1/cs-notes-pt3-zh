# 【Jonas-Birch】使用C语言从零编写Ping-｜-Ping-From-Scratch-p02-P02_02_互联网协议_-从零实现PING--BV1rwBTBUETy_p2-

So guys， welcome to today's show。So today we are going to continue our ping。

That we started with a couple of days ago。

![](img/8cda9f826e20109b2365751545d5a8a0_1.png)

And before I continue， I just want to mention a little bit how it works on the packet level。



![](img/8cda9f826e20109b2365751545d5a8a0_3.png)

All right， you guys。 So Internet protocols are divided in a seven level gale。So at the bottom。

 we have layer 1。And at the top， we have layer 7。And what does this mean。So， the lower level。

The closer， Sir。To the hardware。It is。And the higher level， the closer to the application。

And during this project， we are primarily interested。In two protocols at level level 3 and level 4。

So。We have already talked a little bit about i c m p。And today， we are gonna。cold。I p。

So what does this mean the IP protocol looks something like this。So we have a type field。

And a cold field。We you also have a check on。And we have a data field。So something like this。

 And if we are sending a pink packet。That means that the type field is going to be 8。If go。

The user sends an echo packet and receives an echo reply。And that's how the pain process works。

So the code field would be0 in this case， and the date the field。We can decide that for ourselves。

 Usually， there is some kind of I D number here。So we can differentiate between the different packets。

And then the check sum is a number。We follow some mathematical formula that we're getting into。And。

This is just an example。Okay， so that's the ICMP when the reply goes back instead of an8 here。

 we have a0 and that is the echo reply or the echo response。Okay。

 but we cannot just send the iCM packet。 We also need to include stuff like the addressing information。

And that's where I P comes into play。So an IP packet looks something like this。😔，Okay， so。

And I have not included every feel here， only the things。Think is most important。 So first of all。

 we need to specify the version。 You've probably heard about I version 4。

Which is the current protocol and IP version 6， which we are currently migrating to on the Internet。

But we are dealing with IPV4 in this case， so we put a four in this field。The TTLs。

 it stands for time to live and usually we put something like 250 or 255 or something high number from the beginning and each time a router will forward this packet。

It will decrease this detail field。And the reason is if you were to have a switch network。

 so these are network switches。And switches operate。Layer 2。So it can be etherness， for instance。

 and you have a computer here。And a computer here。 And the network is built like a ring。

If this left computer here will send a broadcast packet to this。Network switch。It will forward it。

To everyone like this。And keep doing that。So this will rotate and rotate and rotate and it will take up every last CPU in the whole network and the whole network will probably go down。

So you cannot build an ethernet network like that。 however。

 on the internet we use routers and style switches。And。So。The last network。

 that's a low glare network using switches， but this is more like internet with routers。

And when they designed the IP network protocol， they wanted to have some protection against these loops。

So。If this computer sends。A similar packet to the router here。It will have 250 as a TL。

Then this router will move this to the next one， and it will decrease it to2。

49 and so on and so forth。 So if there will be a network loop to to a misconfiguration。

 it will loop a little while， But when this gets down to 0 the detail。

 then it will delete that packet， So it will stop the loop after 2504s。

So that's what the detail field is。The source is the source IP address。

And the destination is the destination， I， P address。And these I addresses are regular integers。

 which are in so called network by to order。Which basically means that if you have an I P address。

 A dot B dot C dot D， it will become D dot C dot。B do a。And I will show that in code later on but。

Yeah， you need to know that kind of stuff。Then we have the checkum。

 which works the same way as in ICMP。It's the same formula。

And then we have the data field with the actual payload of this packet。

 which in our case will be this ICmpP packet。 So we are going to take this whole ICMP packet and put inside the data field of this。

IP packet and then we will send this IP packet。And then we will receive a similar packet pack。

So this was a little bit of networking one on one， one0 one。But hopefully， you know。

 enough to be able to write the code， so let's start。Coding the I part of this code。Alright。

 so before we continue the coding， I just want to fix one thing that one of my viewers pointed out。

 and that is when we send the data。And when we receive it， it is in the。Big Indianian format。

 And what does that mean。Well， the numbers， if we want to represent an8 bit number。え。

It can be something like A A， A A， I mean， A A。And。And this is no problem。

But what if we have a number。That is2 bytes。We can represent that as A， A， BB。Or S B， B A A。

And Inb computers use little Indian， which means that the least significant bits。Or to the right。

But big Indian does the opposite。The least significant bit is here。So。Basically。

 we just need to deal with all that are 16 bits，32 bits，64 bits and so on and turn them inside out。

Most of our things in the raw ICMP packet。Is just 8 bits。

 But this check some we need to take care of and same with the well。

 when we get to IP Internet protocol， then we need to deal with a couple of more fields。

 So let's create a function。 We can call it engineion。And since were only dealing with 16 bits。

 we'll start there。So we will have a 16 bit integer。And we'll have a function called Indian。

And it takes a 16 bit in here as input。 and this will turn it inside out。 By the way， let's call it。

And then。16 Bs。 That's easier。And let's put it a little bit on its own so we can。Create more。

Later on。So how do we turn an integer inside out， It's pretty simple。

 actually using those bitwise operators。So let's say we have this andion function。

 and we're having a。Value called X。We need to divide it up into smaller numbers，An A and a B。

 which is one by each。And by the way， let's make this in8。And we need an N16 y。

 which is the return value。So。If we have a number such that。AA。

Let's first isolate the babies and we'll use it the same technique as we did with it。

 check some earlier。So， B is equal to。呃。And we take the input value and we end it with 0 x 0，0， F， F。

So， that。

![](img/8cda9f826e20109b2365751545d5a8a0_5.png)

Issoate。Despite。

![](img/8cda9f826e20109b2365751545d5a8a0_7.png)

。Al right。 Where were we so。We have be defined， and a will do basically the same。对。In this case。

 we're gonna earn this with 0 X， F， F 0，0。So， we isolate。The top。But。And we also need to push this。

And。Let's see，8 possessions。To the right。So。We don't have a lot of zeros to the right。Okay。

 so now we have defined。Those things。嗯。Now， we just need to assemble this stuff。In our y variable。

So why is it going to be， And let's see。 So we take this in the right。Order。

 so the B should be to the left。So， we take。The， the be。Variable。 And we push this。

As positions to the left。嗯。And then we end this with the alobe。Yeah， that's right。

And now we can save if you return。Wイ？O。So now when we call the checkum function or or rather before we return。

😔，AndLet's say， we have a。A resolve。Fing or red。Variable。So， instead of returning this。

We will set our。Rth equal to this。And then， we return。And then。16。好不瑞。



![](img/8cda9f826e20109b2365751545d5a8a0_9.png)

Something like this。 So let's see if it compiles and gives a different result。 So we had D4，2 D。

Last time。

![](img/8cda9f826e20109b2365751545d5a8a0_11.png)

So when Iclock。And， this should be Amb 16。

![](img/8cda9f826e20109b2365751545d5a8a0_13.png)

So。😔，D 4，2D。Did I check the right thing。So， this is the time。This is the code。

And then this check some D，4，2 d。Before for20。No， it。0，8。00。Maybe I'm not reading。Toly。0，1， D4。

So the D4 is right。And it's at the right position。 But why is there a one there。Instead of the 2D。

 that's weird。

![](img/8cda9f826e20109b2365751545d5a8a0_15.png)

嗯是起。We give this the same。Input as before， return， and then 16。Over。So， B is。嗯。And0， x 0，0， F， F。

And a。Is it。And。F， F 0，0。And push to the right。m。No why。Is being。Push。8 positions to the left。

And we or it with a。And the problem is。The A， right。



![](img/8cda9f826e20109b2365751545d5a8a0_17.png)

Or which was it。Tough to see here。 Let's isolate it a little bit。😔，So。😔，We have these two fields。

Then we have this。And then， the rest。And now， we have this。This is the same。And the D4 is the same。

 but instead of 2 d， we have 01。

![](img/8cda9f826e20109b2365751545d5a8a0_19.png)

mm。Let's try this function on its own。So let's say we havent in 16。Well。Where well is equal to 0 x。

A AB。Then we have Val prime。Which is equal to Nvi Andmbian 16 of Val。And then， we print this thing。

And willll print it as。Heod a small number。4 dig。嗯。16 bit。Well prime。And。Return这。



![](img/8cda9f826e20109b2365751545d5a8a0_21.png)

So now we should get B， B A A， right。Baby1。

![](img/8cda9f826e20109b2365751545d5a8a0_23.png)

Do I push it too far。mmm。So， we start out with。We ended with this。So we get the A A。Oh。

There should be two of those， right。Weird that I didn't saw that。

 You probably saw it two years ago and laughed at me， right。Alright， so。

Sometimes it's easy to miss what's right in front of you。



![](img/8cda9f826e20109b2365751545d5a8a0_25.png)

So， let's run this again。And now we have 2 d D for， okay。Good， so now， now we are done with。



![](img/8cda9f826e20109b2365751545d5a8a0_27.png)

![](img/8cda9f826e20109b2365751545d5a8a0_28.png)

。Close a few of these。Now we are done with ICMP。How would generate the package anyway。

So let's move on to I P。 And that's the only other particle we need to implement before we can。Well。

Caold the rest。So we will have similar functions for IP。And。

And let's start by defining the data types。And as before， I wanna have a truck。S， A P。

Where I only store the things that I find interesting to， to save。And。And what is that。Well。

 we want to have the I P addresses， at least the source and the destination。

And we can store them as a 32 bit integer。So， let's say。嗯。Let's say we have a source。Let's say。

 we have a destination。And乐s。Check how the packet format looks。 So Internet protocol week。



![](img/8cda9f826e20109b2365751545d5a8a0_30.png)

Let's see if we find。Nice。😔，Sure。😔，嗯。That's pretty weird that they don't show it。

At all along the first page。Right。Maybe we should say I before。😔，嗯嗯嗯嗯。They should are here。

 They should put this on top of the page。I can promise you that 90% of the people searching for IPV4 is looking for this。

But they never mind。 All right。 So the version is I P before。 That's not much to talk about， Ih L。

Let's see， the。IP is variable in size using to do do。 So this is just the size of the header。

DSP is the packet， the priority。Is the N is。诶。Is it。They do not fragment。No， explicit congestion。

This fit alone and then notification。 unless we can just link without talking。Well。

 this is not something that I have used a lot。A total length。Well， identification。

 I guess this is the protocol number， perhaps， or is it the。An I field does it and。

Identification field。Uniquely identifying a group of fragmented packets。 alright。

I don't think we need。But maybe it could be handy if we extend this。



![](img/8cda9f826e20109b2365751545d5a8a0_32.png)

Later on。And maybe use it in our firewall program or something。So let's， let's use this。



![](img/8cda9f826e20109b2365751545d5a8a0_34.png)

So16 Bs， I D and 16 I D。What else we got flags。嗯嗯。Fragment of at time to live。

Protocol could be interesting。 So this is the layer 4 protocol。

 So the protocol that's inside of the body of the of this。With an8 bit field。And it will probably be。

呃。One， in our case。And。But， I think。I wanna。Yes。Save this anyway， do I。



![](img/8cda9f826e20109b2365751545d5a8a0_36.png)

No。Let's， instead。Create an enum， like we did。Up there。So， let's say， we have a。

Let's say we have a tie。Kd。And we can combine。And。Those。え。AM p。Code type fields。With the protocols。

 I don't mind。Let's add ICMP， TC P and UDP。And when we add it like this。

 the program will or the compiler will assign numbers to this so we don't care about that。

 but let's make it packed。So that it doesn't take up a whole lot of memory。

So let's say if0 is probably maybe we can even define this。Explicitly。So， we have。1，2，3，4，5，6。

Different。So， if we were to。Make this some binary。This is one。2。😔，For。诶。

So those three bits will be enough for this field。So let's set that in both of these to optimize a little bit。

So the kind is going to be3 bits。And if we don't specify， it defaults to this in 16 or in days。

But since we only need three bits， why not。

![](img/8cda9f826e20109b2365751545d5a8a0_38.png)

Right， let's see if we can find anything else interesting here。 We have a。S some here as well， but。

I think I will use， just use the one in the raw packet。 So we will have two different kinds。

And then we have source and destination， and。Potentially， some options that we don't care about。



![](img/8cda9f826e20109b2365751545d5a8a0_40.png)

So， this is。呃Enough。And let's make this packed。 Let's type death。Astruct S。I P。

 and let's just call it I P。And we also need a stroke。Yes。A raw I。And here we need to put everything。



![](img/8cda9f826e20109b2365751545d5a8a0_42.png)

So， let's see。4 bits aversion。

![](img/8cda9f826e20109b2365751545d5a8a0_44.png)

To in8 version。

![](img/8cda9f826e20109b2365751545d5a8a0_46.png)

Forbi。And， and then we have this length。IHL forbid。



![](img/8cda9f826e20109b2365751545d5a8a0_48.png)

In8 IHL for bed。

![](img/8cda9f826e20109b2365751545d5a8a0_50.png)

Yeah then we have the DSSCP and。It goes up to 13。 What is that 7。S bit。



![](img/8cda9f826e20109b2365751545d5a8a0_52.png)

So。In 8 DSSC P，6 bit。

![](img/8cda9f826e20109b2365751545d5a8a0_54.png)

![](img/8cda9f826e20109b2365751545d5a8a0_55.png)

ECM， it's just2。It is。BCM。2。😔，嗯。Here we， we just made this as an optimization。

Here it's strictly necessary to define the bites and make it packed。 otherwise it will not work。



![](img/8cda9f826e20109b2365751545d5a8a0_57.png)

And then we have the total length。So that is probably the header and the data， right？



![](img/8cda9f826e20109b2365751545d5a8a0_59.png)

Yes，16 beds。In 16 length。

![](img/8cda9f826e20109b2365751545d5a8a0_61.png)

![](img/8cda9f826e20109b2365751545d5a8a0_62.png)

And then we have the I field， which is also 16。

![](img/8cda9f826e20109b2365751545d5a8a0_64.png)

![](img/8cda9f826e20109b2365751545d5a8a0_65.png)

Flas is 1，2，3， bit。

![](img/8cda9f826e20109b2365751545d5a8a0_67.png)

![](img/8cda9f826e20109b2365751545d5a8a0_68.png)

A fragment of set。Which is。13 with。Yeah。So， in 16。Of sir。



![](img/8cda9f826e20109b2365751545d5a8a0_70.png)

See。13。

![](img/8cda9f826e20109b2365751545d5a8a0_72.png)

And then， the T T L。8 bit。😔，Proractical 8 bit。

![](img/8cda9f826e20109b2365751545d5a8a0_74.png)

And we are soon done。

![](img/8cda9f826e20109b2365751545d5a8a0_76.png)

Sck song 16。And then， the source and destination。And that's 4 by 8。And 32 source in。



![](img/8cda9f826e20109b2365751545d5a8a0_78.png)

To destination， Did I put the right order now。Yes。And then， options。嗯。Do we need to keep those。



![](img/8cda9f826e20109b2365751545d5a8a0_80.png)

Let's define them as。And a。Of。Chs。And we define it like this。 So if we need it。

 we can allocate for it。And this is packed， and we don't need to type if this。Alright。

 so now we have the raw packet as well。Let's start， as we did before。

 by creating a constructor function。Which will create an I P packet with make I P。And。

What do we need to specify source， destination， I D and kind。So， let's take it in。That order。

Should we。😔，Maybe we can actually。Of this。A little bit。So。This will be a tie。

And then we have the source and destination IP P address。 And in the construct。

 I think I wanna specify them as。Regular strings。In8 star In the8 star。And what's the last one， I D。

戦そ？なんなつ。ItThis thing。So here we have the IMP functions。We seem to have them a little bit mixed， so。

Let's just put it up， top。Or so we wan to return an I pointer。This is make I P。

And we are going to pay。点。By the way， let's make those strings castt， as we did up there。

So we have a tight， kind。We will have an innate source， intnate destination。And an in 16 Id。

Make sure。That we have a kind。Kned or。Source or。Destination。And we fail。

And what do we do if the Id is not specified or if it's0， shall we randomize it。Gue， we could。

And then maybe use some counter or something。完了。😔，And since I'm lazy， I will just use。

The library functions for this。So I'm gonna see the random generator with S round。

And provide it with our p， as input。Then， I'm going to。Return the first。明ing。So。See。Let's call this。

Rund。😔，Rand is equal to our round function。But， let's。Mdulous dis with。65。5ve。3，6。

Since there is a maximum。And maybe we could actually make it a little smaller。 so we have enough。Re。

To increase it。Which means that we need to pass this value to our function as well。

Or a pointer to it， really。So let's also give it an in 16 star。So let's say this is N 6。Yeah。Counter。

Or rather。Counterpointer。And then inside of here， we will have one for the。Actual counter。Yeah。

你 could do。Or maybe we don't。We do， however， need some kind of I D。So let's say this is I D prime。

And will have an in 16 I D。And。If we have an I D which is positive， I mean， an I D prime。

 the parameter。Then we set I D equal to that。Otherwise， we set I D equal to。The counter pointer。

And then， we increase it。Something like this。Okay and。What else do we need to do。

 We need to allocate this， statement。So let's say we have an I P packing。Pack is equal to。

 And by the way， we need a size first。So the size is signs of。St。S， I P。嗯。Pect。I。I think of me。

The integer size。Yeah。If we don't have a packet。We can actually assert that we have a。

Like we did before。And then we can zero out this thing。たさ。And now we just need to fill in the blanks。

So。Let's create。Or， let's know。Let's just fill in all these fields here that we can。So。

We need to switch。On the can。So let's say we have some kind of variable for that。

And how big is the actual field。 that doesn' matter。 By the way， we don't need to do this here。

We'll do this later when we deal with the other packet type。So let's just set the packet。Kind to。

The kind。It set the packet yet。I D to。Id。And then we have the source and destination。

 which are I P addresses。 So we need to。Have some function， which turns。An I address into。But well。

 from a string。To a。In the year。Maybe we can cheat a little bit and use the standard C function。嗯 no。

Really in the mood of parsing that kind of stuff right now。

It would be an interesting exercise for another day， though。And let's say， we have a destination。

We do the same here。And if。Either of these are0。Or actually， the source can be 0。

Then the operating system filters it in automatically。

 but the destination can most definitely not be0。So， if。The destination is 0。

Then we free the whole packet。Return an error。Otherwise， I think we have all the fields， right。

 Ki source test， I D， yes。So now we just can return this thing。Easy busy。

Do we need to deal with those cons。Things in some way， Sometimes we need to cast。An additional time。

 because of that。Yeah。Let's see。The only place we'd use them。Here。And this takes a cost， too。

 So that shouldn't be a problem。All right。 I think this function is done。And。

So let's create the show function when we're at it。We would probably。Need debugging。So。

 well have a void。So。I p。Which takes an I star pack。If we don't have a packet， we just return。

Otherwise， we try to print this thing。Yeah。So， the kind。In this case， we can actually represent this。

As a number。So let's say we have a0 x。Percent。2 digits。Or actually， one digit should be enough。

Since this field is just。3 bits。So let's just make it one。Now， let's make it too。

 Its it looks better。And this is H H X for 8 bits。Yeah。So， this is the packet。I did。 No。

 the packet kind。And then， we have。Id。So this we can cast to a regular。A regulargular shower。I guess。

And this wake cast to an integer。And then， we。Have the source and destination。

And we just have them in an I format。But we are using virtue till if I remember correctly。



![](img/8cda9f826e20109b2365751545d5a8a0_82.png)

I do have some function for that。So， let's see。To doctor。



![](img/8cda9f826e20109b2365751545d5a8a0_84.png)

This does exactly that printed in doctor decimal form。So why not use it。

So here we will just have a string instead。Same here。This is。Soce。

 this is the packet the destination。But we need to call the two doctor。

And since I have written this function on my own， I don't consider this cheat thing。And。

And we need to cast this to。A regular。String。And let's print。Ittra new line at the end。And return。

Then I would just add the signature for this。So avoid show I P。And this takes in。Like P star。

 Maybe we should。We could， actually。We could actually give this。An int a star， as well。

With the name of the identifier， that would be pretty cool。So， we'll do this。

In both of these functions。So。We'll just add。In a。系灯。And。LetMove this out two steps。

And we'll give it a kind of a headline。So。This is the。Yeah。IP。Star。And then， the name is equal to。

Maybe。Something like this。And here we just put the identifier as a string。

Then we do the same with the other show function。Andfin it。😔，Yeah。So isnin't it， I done。

And we have a little bit different。Syntoaxia but。Let's move this O。And this。This， I think。

 I will put outside。So， if we do this。And this。And then we do the payload。

And then we add the headline here as well。 So this is a。An ICMP star。Identifier is equal to this。

This is the identifier。And no。To the cool part， let's create a。A macro， which is just called show。

 And it takes one argument。So either an I seen feedback yet。Or尔。嗯。嗯。An IP packet， and it will。

Rec the type that we give it and print used through。Right function for that。So。Let's define it。

 something like this。 to define。So， and it just takes an egg。And we will call。Generary。

Which is a built in Mac。And I never really seem to remember the syntax。

 But I guess the first thing we must give it is the。Tai。😔，Or they identifier rather。To do this。

And then。If this is an I P star。We want to call。So。I p。And we want to provide。And。The name of it。

As a string。And。😔，x。No。Like this。And if we have， maybe we can line this up a little bit better。

If we have an ICMP star。W called。Show aC。The same thing。 we give it the x and the x。

Something like this。 I think this is how it's done。

Try it out We already have a little bit of cold here。So instead of doing show ICM。

Let's just see what happens if we just do show packet。



![](img/8cda9f826e20109b2365751545d5a8a0_86.png)

Okay some error。I think you really declared。

![](img/8cda9f826e20109b2365751545d5a8a0_88.png)

Maybe I call I P I。Ca I talked too much about now。notで。Rp。



![](img/8cda9f826e20109b2365751545d5a8a0_90.png)

Which line is this。

![](img/8cda9f826e20109b2365751545d5a8a0_92.png)

3。Ty Fstruct S， IC， IC。Oh。It collides。 This is the same name space。Mm。So， let's call this。嗯。

L 4 ICM for layer4 in the o Si model。Doesn't look us。Nice， but。Never mind。



![](img/8cda9f826e20109b2365751545d5a8a0_94.png)

13。

![](img/8cda9f826e20109b2365751545d5a8a0_96.png)

![](img/8cda9f826e20109b2365751545d5a8a0_97.png)

Yes。It's true。It's a lot of lines of errors， but。I think we will。Fix this rather quickly。

Warning pointer targets in passing。Argument， one of another's different signness that is true。

 as well。

![](img/8cda9f826e20109b2365751545d5a8a0_99.png)

So，24。嗯。So what type does this take。Cons。No， that's。😔，I guess it takes a regular string。



![](img/8cda9f826e20109b2365751545d5a8a0_101.png)

This。😔，Pasting b and packet does not give a valid pre processingcesing to。



![](img/8cda9f826e20109b2365751545d5a8a0_103.png)

Maybe it should be one。 I always mix those up。So。😔，Let's just do one。



![](img/8cda9f826e20109b2365751545d5a8a0_105.png)

Sness， again，1，91。

![](img/8cda9f826e20109b2365751545d5a8a0_107.png)

Xope。How can that。Differ in sin and differ against what。Maybe this should。A the size。

But that shouldn't really matter she。学温笔。😔，Show I think P。Well， let's try。



![](img/8cda9f826e20109b2365751545d5a8a0_109.png)

Hhm。No。😔，Expected specifier qualifier less。

![](img/8cda9f826e20109b2365751545d5a8a0_111.png)

Okay， so that's not it。嗯嗯。Der in。And they。IOh， it's the first argument。No I get。We need to。Cas this。



![](img/8cda9f826e20109b2365751545d5a8a0_113.png)

So。Yeah。Passing argument 2 of show I。From incompatible point of time。Well。😔。

It should never be ICMP when it's I P， right。That's a weird thing。 That's a。Ide with this whole。Feng。

😔，Or。Construct。I prepared。Good I star。That argument is of type I in piece。In function main。m。



![](img/8cda9f826e20109b2365751545d5a8a0_115.png)

Should we omit the parentheses， perhaps。

![](img/8cda9f826e20109b2365751545d5a8a0_117.png)

![](img/8cda9f826e20109b2365751545d5a8a0_118.png)

Do you need to cast it somehow。

![](img/8cda9f826e20109b2365751545d5a8a0_120.png)

Okay， there we go。Variable， R And D， no。

![](img/8cda9f826e20109b2365751545d5a8a0_122.png)

Well， that's correct， because we don't。We don't call this make function， yet。So， let's just tie this。

对。

![](img/8cda9f826e20109b2365751545d5a8a0_124.png)

mm。And we should be al right。Allright， let's see if this still works。I send payp It is equal to this。



![](img/8cda9f826e20109b2365751545d5a8a0_126.png)

Yes。Pretty nice。So now we can just add more types if we want to。Alright。

 so what's the logical next step。Well， we have three out of。2 out of three functions。

 We just need the Eval I Eval I P。Where we turn。And our I P。Structure。Into a raw structure。

As a series of bites。Alright。So。See。In对。El， I think。And this is going to take。IP star。

And what does the evil function do specifically。Well， you just construct this。Well。

 let's do something similar。So in it E I P， we take an I P。Again。You need some stretch。😔。

We also need a pointer。Poer。The check some。When need。Besides。We basically need the same stuff。

If we don't have a pack。And we don't need to check for the day in this。Cs。Since在玩呢。😔，Well， it might。

Sly。😔，Be Sunday的。And let's see。The ICMP packet is the date。m。I think。Inside。

 I don't w to mess with this， really。But inside of this， our own IP packet structure。

We can actually give an ICMP pointer。As the payload。So。Yeah。And does that， in turn。

Contain everything。Yeah， Canadada does。All right。So let's update our show function first so we don't forget it。

😔，Can do this。No， but we can do something similar。O， I P。mmm。Zif。Our pack yet。Has ever lived。Hello。

Pyload。And then， we can just call。So recursively。And provide this payload instead。

 That's pretty nice。O。Where where are we。😔，Yeah， so。When we do this， make I P。From the start。

 I think we should just set this。Yeah。We will just set this。Payload。To 0 for now。And then， when we。

Have a nice MP package。 We can。Just point this manually。Alright。Let's see。I guess we need to switch。

Good pack。And。Because we need to set this。What did we call it。ThePro field。So let's say， we have。

And8。To go。No， no were in the room。In the。To go。Se it is0， first。Then with swear。The packet。Kd。

If we have。L 4。I想 pain。We set the protocol to one。And that's the only thing we should support at this point。

😔，So here we'll just return an error instead。Okay， so that's that part。

And then we just fill in the rest。Let's start with a check some zeroing it out。So。This is our。

I guess。No。Ex。ze。😔，P 0。Destination。And this is already in the right。Big Indian format。So。

You can just。Take it。Okay。你时慰你。Llas。

![](img/8cda9f826e20109b2365751545d5a8a0_128.png)

Don't think we need that， either。Let's just double check。どこれ。Fg。We serve。

 we don't fragment more fragment。 No， we don't。

![](img/8cda9f826e20109b2365751545d5a8a0_130.png)

What else that I。We just copy。And let's see。 the I D field is 16 bits。

So we need to run this through our alien。ク？ and this is。The length of。



![](img/8cda9f826e20109b2365751545d5a8a0_132.png)

The header， right。Internet headerline。Since we don't have any options。This will always be the same。

WhiShe is 20 bys。 if I remember correctly。Or is that the entire。

The minimum value for this field is 5。

![](img/8cda9f826e20109b2365751545d5a8a0_134.png)

Well， let's just do this。搜一首。😔，Sted us ro。by the way， how big is this field。



![](img/8cda9f826e20109b2365751545d5a8a0_136.png)

![](img/8cda9f826e20109b2365751545d5a8a0_137.png)

It's just 4 bits， okay。Nothing to worry about them。



![](img/8cda9f826e20109b2365751545d5a8a0_139.png)

Then we have the length field。 That's the entire pack。冷死冷死冷。Here，16 Bs entire pack yet。Invites。

 including Heather and Deta。

![](img/8cda9f826e20109b2365751545d5a8a0_141.png)

So now we need to check if there is some ICMP packet inside of here。So。Let's see。 Let's create。ling。

😔，Little Indian。The length。李亮亮。So， if。The pack yet。Contains a payload。

And we need to figure out the size of that payload。The length。😔，In the little ending。Is going to be。

The rope packet。IHL。Plus。The pack yeah。Do you want to have。So， always， this is the I P bag。

Don't really have a size for that。Well。Okay。Can do this。 So the pack get。Heload。

And this is the length that we are interested in。So size。 And this is just the size of。The I see。

ICM packets， payload。So。😔，We also。Near to plus the size of a struck S ro， I see Peter。

So that should be the entire length in little Indian。AndThe length in big Indian。

Will simply be the Indian16。Of the length。And。Littleland。And this is if we have a payload。

If we don't have a payout。The length will just be equal too。Yeah。The length of the headers。

You need an else close。All right。Nice， what else we got raw packet though。Offer。

We don't really need to。Bather with us。And we deal with this kind of IC feedback package， at least。O。

The。Opportuns。😔，We don't need， either。Protocol， we have already。No， we haven't。

 We have just defined a local variable for there。So， here we said it。How big is this field。Indeed。

That's good。嗯。And then we just have one more， right。Source， no， we have a few more。

So the source here we do the same as before。We just said it to the pack guest。It's the worse。我 else。

😔，Time to live。This is 8 bit， right。Yeah。And I think the standard is to set it to2。

But it doesn't matter all that much if。It differs with a few。这样。hope， I mean。To the TTL。 and finally。

 the version。 And that is an8 of4 bit field。Something like that。 And this should just be a4。

This is the entire thing。And。So now we need to take the。Then。Robitts。Likefe we did here。

Let's see you back check。Yeah， we just need to allocate a string buffer。Which is big enough。

And how big is that。It still。😔，leength。😔，嗯。Let's also set the length alley like this。Here。

 we need to set the rope packet yet。le。To late， sillyally。Let's initialize length a to 0。

 from the beginning。So this contains the entire length。こなくて。😔，Let's do the same here。 if the length。

Elie。And2。Is。Even。It's odd， I mean。Then we increase this by one。Now， we can do something like。CP。Mlo。

😔，Thely。Oh we zero this thing oh。嗯。E lean。A copy into。Into P。So being the raw packet。Length， Alibits。

And by the way， let's set red。To P。Sir。We have a pain。And let's。Increase。By length， El。

Then we need to check if we have a payload again。So。We have a payload。We need to。Copy that thing。

 as well。Do something like this。And， this is the。爱想屁。Pointer。😔，So we set that equal to E。I想片。

And we give it the path kit。You楼。And if we get a result。We will copy that thing into。This。So。

 copy and P。The source， this time being。ICMP pointer。And we want to copy packet。Heello。😔，Size。

And when we have done this copy operation。We can free the ICMP into。And then， we can return re。Okay。

Now， I think we have everything。And then， we can just start。嗯。Creating the real stuff。

Where we initialize so getss and the like。

![](img/8cda9f826e20109b2365751545d5a8a0_143.png)

Let's just see that。 this compiles first。Sizeize of。Conversion from unsigned and。To un shore。4。

Change its value from 200。To4。Roper。HH2。😔，Is equal to stroke。So。Wい。



![](img/8cda9f826e20109b2365751545d5a8a0_145.png)

Is that really four bits。 So how can that hold everything。The first headerfield。In an I pack。

Its a version field。Oh， no， that's not it。The IPV4 header is variable in size。

The IHL field contains a size。Of the IPV4er。It had 4 bit that specified the number of 32 bit words in the header。

 okay。

![](img/8cda9f826e20109b2365751545d5a8a0_147.png)

ガつ。Quite different。So， instead of size of this。We need to。Divide this by4。

And we use this in a couple of places。Which means we need the times it will 4。



![](img/8cda9f826e20109b2365751545d5a8a0_149.png)

Let's see。 row packet Op with the0 and values of flexible array member。That's right。That is right。



![](img/8cda9f826e20109b2365751545d5a8a0_151.png)

1，29。This is an array。 It's not a pointer or anything else。So。We can just leave it out。

Since we don't dial a case for it anyway。

![](img/8cda9f826e20109b2365751545d5a8a0_153.png)

What else。Variable length be， E set， but not used。

![](img/8cda9f826e20109b2365751545d5a8a0_155.png)

嗯。That's right。 This should be length B。

![](img/8cda9f826e20109b2365751545d5a8a0_157.png)

S ist another。

![](img/8cda9f826e20109b2365751545d5a8a0_159.png)

Useed very well。Okay。Check is a very。That， I actually forgot。Before we return here， we need to。

Create the right shake zone。So欠。Should be equal to。是。😔，Some。See。

I think we actually want that size variable。Because we're dealing with a couple of different sizes。

 and we can't mix them。However would like。So here， for instance。I think were better off。Let's see。

Length L E。I think we need to have a size struck us。L I。We can allocate best。なんです。And we do all this。

But when we copy， we just want to copy size by。😔，From here。And we want to increase this by size。And。

What about here， We w to provide our packet。谢谢。And the size。嗯。😊，This needs to be length。Elie。

And then， we can set。Raw pointer equal to。It is raw。I p。And we can point this to。Right。

And then we set the row pointer。Check some。To chef。And return。



![](img/8cda9f826e20109b2365751545d5a8a0_161.png)

Now， I think it's good。

![](img/8cda9f826e20109b2365751545d5a8a0_163.png)

No。We shouldn't do it first。

![](img/8cda9f826e20109b2365751545d5a8a0_165.png)

Ha， a passing argument， one of checks some from incompatible。Po0 time。Ied。😔，嗯。



![](img/8cda9f826e20109b2365751545d5a8a0_167.png)

Okay， so。Here， I suppose we should。给日字。Raw pointer。Yes。



![](img/8cda9f826e20109b2365751545d5a8a0_169.png)

Check some red yeah。Alright， it compiled。嗯。And its still works。This far。

So when we come back after the break， we're gonna test this out。

 and then we can start coding the raw socket kind of stuff。So we'll be right back after this。



![](img/8cda9f826e20109b2365751545d5a8a0_171.png)

All right， you guys。 We come back。So the next thing we're going to do is we're going to test this IP packet constructor so we know that everything works。

So we already have an example ICMP package right here。 So all we'll do is create one for IP as well。

Yeah。Yo。😔，So。Here we create everything I seem related。We will not show it， though。

And not do the printing。So。Here somewhere， I'm gonna do I P is equal to。Make改 p。

And we need to have a kind。So， let's say。This is。No。Yeah。例如。😔，For S and P。

We need to have a source address。Let's say。1，92，1，681 do。5。And the destination address。

Let's just pick something。2，12，1616。2，40。And we need。So have an I D。

 or we can put a0 here to auto to generate it。And we need to have a pointer to the counter。

And that is our R And D。Okay， so now we should have an I packet if we don't。

We can actually as serve to when we test stuff。So let's assert we have an IP。嗯。And let's set the I。

That's one thing we do not account for when we set the payload。We should recalculate。The sizes。

 right。And the check。きさ？So I think we need a function for this。Sheli。😔，So。

 let's say we have something like。Add payload。So。嗯。Well， let's make it a bulloleion。And。Its add。😔。

Beload。And it's going to take an I P pointer。And it's going to take an ICMP pointer。

And that should be enough， I guess。And then it should add the payload and recalculate what needs to be recalculated。

So。😔，We have a boolean ad。load。😔，Takes an eye。I。I P packet。And it takes an ICMP， ICM。Like so。

Let's check that We have both of these。 So I P packet or。I think皮。Return false。Okay。

 so we will take our I P packet。And we will set。诶。Actually。

 I don't think we need to recalculate anything doing。😔，Kind source desk。 I no， we don't， because。

The only time we need to do stuff like that。Is when we e。VIP packet。

And that function we already have。So。We don't need this， actually。So， let's remove this。いんですよ。

So the only thing we need to do。Is take the I P packet。No， we can't name this I P。

Let's call call it I P packet instead。AndLet's。This raw package right here。うつ？

Change the name of packet， to。I see MP pack。See where we have just packed。系先。ICMP packet。

Let's sir that we have an ICMP package。Then we make the IP back in。Which is now called that。P can。So。

 willll set its payload。To our ICMP package。Just like that。don't need to do this。Think we do。

Do we have a size field inside the I。😔，We have kind source。Destination。Id。😔，Payload。

Do we need to know the size of this thing。No， I don't think we do， actually。

So we can remove this size right here。When we have。Prepare the packetant。

We will set our raw equal to。Email。I p。And。Give it the。Pa。But how do we know how， how much to print。

Well， we never really do need that， except。Now， when we're debugging。Well。

 we know the size of the I P header。Maybe we should put this size thing back。

 We don't really need it later when were actually going to use this for real。 But now。

 when we debug it。It's good to have a。So the size is going to be the size of。struck。Yes。诶皮。能。😔。

Raw IP。So， the actual header。Plus。The size of。The raw ICMP packet。Yeah， et ce。And finally。

 we add the I packet。Payload。Size。I think that's right。So， let's first。Pri。😔，Yeah。Let's show。

The I be packet。And then， we can。Print。The raw。And we need to specify。The number of。Bs。

 which is size。And the delimiter。 Maybe we should have a delimiter here。Let's just make it a space。

And when we have printed this thing， we can。Free the package。This is， this is the。I think he。Py data。

And the ICMP packet。ND爱迪达。Like so。

![](img/8cda9f826e20109b2365751545d5a8a0_173.png)

I think this is the right。Way to do stuff。可以。May。It's compiled without any warnings or errors the first time。

Alright， so we haven't Ipack yet。And this is the kind and the I D， which is auto generated， remember。

Yeah。嗯。Soce。Destination。And this is the payload to the ICMP packet。

And this is the contents or the payload。And here， down at the bottom。We have the entire。Thing。

And I can't know for sure if this is correct。 We will know better when we。Try to use this thing。Fist。

Doesn't look wrong， at least。

![](img/8cda9f826e20109b2365751545d5a8a0_175.png)

Okay， so now we can start doing the real socket stuff。

But this will be all for today if you like this episode。

 please like subscribe and we will continue this project in a later episode Thanks for watching Thanks for today。



![](img/8cda9f826e20109b2365751545d5a8a0_177.png)

![](img/8cda9f826e20109b2365751545d5a8a0_178.png)