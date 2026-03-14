# 【Jonas-Birch】使用C语言从零编写Ping-｜-Ping-From-Scratch-p08-P08_02_数据包套接字_-实现以太网库--BV1rwBTBUETy_p8-

![](img/c2659e9ea806b288914cf08aedf7a4e0_0.png)

So guys， welcome to today's show。In the last episode， we started a new project called Esther。

And Esther is an ethernet implementation， a library that we can use to send anything we want when it comes to networking。

 which we will basically send the data directly to the network card。 so we will be able to。

Spoof IP packets by sending packets with a different IP address than our own。

 You should not use it for that。 but that's one way of using it。Another thing is。

We will be able to monitor traffic on the network， for instance。

And we can do a whole lot of different other stuff。

So basically we set up the project the last time and added some utility functions for printing Mac addresses and converting between Mac addresses and our Ethernet date structure and so on and so forth。

So today we are going to create our Eval function。Which is going to take one of these。

Een the data structures。And turn it， I mean， this one。 No， where is it。嗯。Here it is。

So this is our ethernet data structure。And we're gonna turn it into。Something like this。But also。

 with the。Some data的。So I think I'm gonna do it like。Now， let's。Do you like this for now。Alright， so。

First off， I w to make our lives a little bit easier。Currently。If we， for instance。

 evaluate our I P packet。Or our I data structure。It' going to return an in8th star。Which is just。

A number of bites。Yeah。But。It would be easier if it could return something which。Return the bites。

 but also the size。So we don't have to calculate manually each time。

So that's where I'm going to start。 I'm going to create a very simple new data structure。

Which I'm going to call a bite string。And it's going to look something like this。

So we're gonna have an in 16 size。And then we're gonna have an ink8。诶。Well， Dave。

And it's going to be packed， and we will type the。Drg this bite string into a bite string like this。

So this will。Makes stuff a little bit easier。And let's create a constructive function for this thing。

是。Let's see here。It's going return a by string pointer。And by the way， let's not do it like this。

Let's just use the pointer。 we have。是嘞。Let's do it like this， instead。嗯。So， we're gonna have a make。

B string。Which is going to take。An inate star。And a size。 So and in 16。是。to drink。In a。They done。

In 16 size。So， let's first check。 that we。If we don't have data or if we don't have a size。😔。

Will return腊人。Otherwise， we're gonna calculate how big this needs to be。Which is just size of stock。

That by string。We got a malloc。The size。Let's assert that we have a B S。Let's zero it out。

And fill in the contents。Something like this。So。Let's。

Take this Eval ICMP and let it return a by string instead。Same with the one for I P。

And same for evil， either， either。So， let's start with。Eval爱 him。Actually， we don't need a variable。

So let's see which one contains the size of the thing。别错了。😔，We gonna return。Make bite string。

Provide red。嗯。Size。Take E IP and do the same。So let's see here。We have a rest， which is equal to P。

We have the length。Little Indian。A quiet string of breath。嗯。Length， little ending。1外。一子。女S。

Did actually do this one。SoWe are returning this P。And we are currently only。Evaluating the。Header。

Maybe we should take the rest， as well。Something like this。Mm。AndI wonder if。

We need to update some other stuff， as well。Let's see if anything is calling Ebal I P。No。😔。

What about。But it's calling the eval function， I guess。Let's check E， I S。Okay， here we call it。

C pointer。Is equal to this。Let's create。Bite string pointer instead。いいが？We have a。Yes。And。Well。

This is enough。You can set the ICMP point or2 B， S。对的。

AndIt shouldn't be necessary to do this calculation。Instead， we can just use by strength size。

Thank this is R。All right。So。I think I'm gonna create a function， which merges too。Of this。

Things as well。不的。😔，By。Tre。Section。So let's say， we have a。B， S。Merge。

It takes two by string pointers。Then merges them into one。Let's also create。AF pointer。

Where we have bite string。Let's call this。PS， S function。And it takes two bite its strengths。

And then we can do a little bit of object orientation to make stuff even easier。And add。

About string function。Which we call。H。Something like this。Let's make this dust。

When we create one of those with a make by strain。Andces B yes。M具。Equal to the address of。

I would B a mergege function。嗯。It's first check that we have those two。

That not both of them are empty。Because then it's an error。However， if one of them is empty。So。😔。

Let's say， if a is。对。Then we can just return B。And if。Be。😔，Is empty。 We can return a。Otherwise。

 we need to be a little bit。Clever。So。The size is going to be equal to。Well。

 let's start with the size of the day duck。So that's the A size plus B size。And then we allocate。

It's clear out。And then， we cop it。Into。Pi。From a days。A size。We increase P。By a size。

Then we cup into pea。俾你。Besides。So now we have a new data area。We can free the a。デた？Can free the be。

对。And we can free a。3ree。😔，Let's Sir。That we have a pay。Now we can create the new one。

So we need to have one more size variable。Let's assert that we have a B， S。Then with08 out。

And now we just need to suck the fields。Actually， we don't need to do。

The allocation and stuff in here。Xulei。😔，When we have the size and its content。We can just。Return。

Make bite string。And we provide the。LetSee， we need to have another pointer。

So when we have allocated， we can set red to P。We can return rest， and。嗯。Well。

 we don't need this end either。Because this size calculation will happen inside of the make the constructive function。

We can remove this。And we can just say size here。So now we can merge。Two of these。

So let's test this out。Let's create。It main3。Where we have。2 by strengths， B is1， B is 2。嗯。

Need to have two days fields as well。 So do you want。Did子。Let's say， the1 is equal to。Hello。

D2 is equal to world。I guess we need to cast。So let's create some bite strings。So B。

 S1 is going to be back by string。 D1。And hello is 1，2，3，4，5。Experts。Itsten。1，34 5。Its do some error。

Reporting， so if we。Let's do this， instead。So， V S1 is equal to。V S1。Merge。B S1 and B S2。

Think we can do it like this。If we don't have a be one。Otherwise， let's print some stuff。

I'm not sure if this is going to be no terminated， though。Maybe we can。Include。

And all terminated by defense。Expir here。Then we can free B S1。AndWe can return。E。

And our main is main 3。All right。

![](img/c2659e9ea806b288914cf08aedf7a4e0_2.png)

Let's see if we can get this work。By the way， Im annoyed by this。So let's remove this if you。

Know that the warning is not correct。And。😔，You are disturbed by it。

 You can just copy this thing right here。

![](img/c2659e9ea806b288914cf08aedf7a4e0_4.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_5.png)

And then you go into the make file。add flag。Where you pace this in。And after the W， you add no。Dash。

😔，And then the warning should go away。

![](img/c2659e9ea806b288914cf08aedf7a4e0_7.png)

SoLet's see。 Exp the declaration specifiers。

![](img/c2659e9ea806b288914cf08aedf7a4e0_9.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_10.png)

安叉。Think you need to move it down a little bit。

![](img/c2659e9ea806b288914cf08aedf7a4e0_12.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_13.png)

Anon type name is F。

![](img/c2659e9ea806b288914cf08aedf7a4e0_15.png)

1，43。That's right。 We have a little bit of hen and the egg situation here。In order to create this。

We need to have this。And the vice versa。So。Maybe we just need to do something like this。

Let me try something。 if we take this。Type definition。And put it above here。And first。

 we just declare that we want to have something which is called by string。

 but we're not telling what it is。Then， we can。Type f。Then we can do this。And then， like， guess we。で。

Here。Think this is going to work。

![](img/c2659e9ea806b288914cf08aedf7a4e0_17.png)

That's more like it。Oh。I call it B， S here。

![](img/c2659e9ea806b288914cf08aedf7a4e0_19.png)

But I think I called it the right thing inside of the C file。



![](img/c2659e9ea806b288914cf08aedf7a4e0_21.png)

Alright。Conflicting types for E I P。In8 E like P。嗯。



![](img/c2659e9ea806b288914cf08aedf7a4e0_23.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_24.png)

So let's try this again。Returning， blah， blah， blah。

From a function with incompatible return type by string。In8 evil I think。



![](img/c2659e9ea806b288914cf08aedf7a4e0_26.png)

Should gotて。先有小路的意思。😔，email IC p。Should be a bite string。Evenmail I。It's okay。E will。Eer。

Allsome change。

![](img/c2659e9ea806b288914cf08aedf7a4e0_28.png)

And what's this about the macros。What are they referring to。function E I P。Let's go from the top。

In function E I P。

![](img/c2659e9ea806b288914cf08aedf7a4e0_30.png)

Line，51。

![](img/c2659e9ea806b288914cf08aedf7a4e0_32.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_33.png)

Inside of the H5。51。

![](img/c2659e9ea806b288914cf08aedf7a4e0_35.png)

But that the macro where。都是。Happen。😔，Ether do sea。One for， oh， it's the zeros。



![](img/c2659e9ea806b288914cf08aedf7a4e0_37.png)

All right。So。😔，Let's go into this。Let's go to Eval， IC P。When we return errors， we need to。

Return the right thing， as well。Then we go to E IP。Couple of those， as well。Youわい。Same here。



![](img/c2659e9ea806b288914cf08aedf7a4e0_39.png)

Okay， now I think those errors should be gone。1，52。



![](img/c2659e9ea806b288914cf08aedf7a4e0_41.png)

Oh， I forgot。

![](img/c2659e9ea806b288914cf08aedf7a4e0_43.png)

And now I believe we should be down to one screen of errors。Almost， there's still one of those。



![](img/c2659e9ea806b288914cf08aedf7a4e0_45.png)

2，34。

![](img/c2659e9ea806b288914cf08aedf7a4e0_47.png)

It's always a lot of work to change return types of a couple of functions。ok。😔，That's better。Okay。

 that's the warning that we had before。 Did't I remove this？In2 pointer。



![](img/c2659e9ea806b288914cf08aedf7a4e0_49.png)

No point。 O。 so point to， theres both directions。So， there's。To pointer and pointer to in。



![](img/c2659e9ea806b288914cf08aedf7a4e0_51.png)

Implic the Decation of make。String， that's right。

![](img/c2659e9ea806b288914cf08aedf7a4e0_53.png)

Fphy。5。This should， of course， be make by string。

![](img/c2659e9ea806b288914cf08aedf7a4e0_55.png)

Nothing else。Incomp types， when assigning type by string star。Some type bite string。



![](img/c2659e9ea806b288914cf08aedf7a4e0_57.png)

So I guess that was right。 the first time。

![](img/c2659e9ea806b288914cf08aedf7a4e0_59.png)

Clled object is not。A function or function boiler。Simon Dubai string， Do star。



![](img/c2659e9ea806b288914cf08aedf7a4e0_61.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_62.png)

Struck as white Str star。Sruck bite， St。 Str bite。B strange。Star。St。



![](img/c2659e9ea806b288914cf08aedf7a4e0_64.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_65.png)

It like this。Always a little bit tricky with us。F planners。Error field merge declared as a function。

 okay。

![](img/c2659e9ea806b288914cf08aedf7a4e0_67.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_68.png)

Now， it's compared。Let'sTry this out。Inval pointer。Interesting。Are we freeing too much。



![](img/c2659e9ea806b288914cf08aedf7a4e0_70.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_71.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_72.png)

All right， we're trying to free。Those。系啊。And they are。Read only。Let's do something like this。

 just for the sake of test。The string cat is a concatenation function。



![](img/c2659e9ea806b288914cf08aedf7a4e0_74.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_75.png)

哦， I门。String do。Which just duplicates a string。

![](img/c2659e9ea806b288914cf08aedf7a4e0_77.png)

， it works。So now we are able to merge。Two of these， which will make stuff。



![](img/c2659e9ea806b288914cf08aedf7a4e0_79.png)

Quite a bit easier。So。Let's。Our date the structures。Move those closer together。So， we have。This。

And then， the raw version。Then we have the two ICMPs。😔，2 I piece。Qianq。

So this goes before the raw version。Alright， so let's see。 So we have。你呢。Then we have a payload。

Which is an I packet。And we have the I P， and we have a payload which currently is only ICMP。

 but it's going be exported TP and UP as well。So I want to make it so when we evaluate。

Ethernet is going to evaluate。The header， but also the payload。

So it's going to evaluate the next thing and the next thing。

And I think the IP version does that already， So evil I。Yes， we don't just need to add that to our。

Ethernet so。Eval Ether。So when we have done all of this。Create a by string pointer。Let's call this。

This one。So， if our etherer。Does not contain a payload。

Then we are done and we can just return B what。Otherwise， we can set b is2 equal to。Youval。

And we provide the E pay load。We don't have one of these， we can return the first one。Or。

I guess it's better in this case， to return an error。So we can free。It be。One day的。Free， B1。

And we can return an arrow。Otherwise， we have。Two by strings， which we wantna emerge。So。

Let's just return。He is one。B S 1， PS S 2。Espec。No need to calculate all different things。Let's see。

 Did I update the macro for Eval。No， we don't have the ethernet。Easer star。We want to do evil Ether。

So。And。😔，We should have a show function， as well。Something like this。See here。

So the show I P takes an int8th and an I and returns void。We need a void。So一嘴。😔，They star。

And Ether star。And I think we can just cope with the IP function。And added to what we need。

 So E show。IP。嗯，说的起。Pyload。Why do we do these calculations。And。What do we just aim for。Here。😔。

Bs total。We have the right be。Plus。😔，Paload。P。Maybe we should call this E instead。Let's say。

 we have an I P。你回海边了。😔，哦。Let's add instead， if we have an E payload。We wanna set。Packet equal。

The payload。So then we can still run all of these calculations。But we'll do an。Plus， equals， instead。

这个。EnCose。This。So let's see here。Packets， payload。Size。Needs to be equal to size of struck。Easer。

And we add。异议。😔，Payload。S。Isal size。Maybe this。Perhaps。m。If we don't have。payload。

And will only be equal to the size of。This is drag。R， either。

AndWe also need to take care of the Mac addresses。M1 is equal to。S。😔，Yi。Destination。2。😔，Source。So。

 we have a size。Kind， I think。We should add， as well。Or maybe not。There's no I D。We will have sos。

 though。Which is M2。Exestination。M1。What else do we have inside of the structure。Protical。

And this is a 16 bit。Did you。For。去。So以。To call something like this。All right。Think this is right。

So let's try this out。Let's say， we have another main。Or actually， maybe we can reuse one of these。

Cause I think we have done something similar already。So， here we create a map。No， let's。こ you。

All right， so what do we need here。We need to have one ethernet thing。So。嗯。And we need to have。

To my addresses。So， let's say we have。No。A source destination。LetSa the。Source is equal to May。咩。

Any like this。And let's say the destination is。The broadcast address of all Fs。

Then we can create an E using May。Yer。The first， we need the eitherther tie。周为还有T。😔，I皮。

Then we have the destination。And the source。And now we can try to show this thing。 So we show E。

That be free。We return。And maybe we should also free。Likeet addresses。So。Okay， so in this case。

 we're going have an empty ethernet。

![](img/c2659e9ea806b288914cf08aedf7a4e0_81.png)

Frae。Let's see if we can show that thing。Unknown type name， I P。



![](img/c2659e9ea806b288914cf08aedf7a4e0_83.png)

Maybe the reshuffle inside of hair wasn't too good。No。Take this。プレダプト。And we'll do the same trick。

Stuck this。

![](img/c2659e9ea806b288914cf08aedf7a4e0_85.png)

Iテ。Conflicting types for show， either。Have void into its star。Vid。案side。Sorry。😔，Struck as。There。这玩。

Previous declaration of show， either。

![](img/c2659e9ea806b288914cf08aedf7a4e0_87.png)

With another type。Is that so。S。😔，Eer。Sure。😔，Show is。



![](img/c2659e9ea806b288914cf08aedf7a4e0_89.png)

Previous declaration， I don't have any more declaration。69。73。



![](img/c2659e9ea806b288914cf08aedf7a4e0_91.png)

Oh， I boyed star。That's right。

![](img/c2659e9ea806b288914cf08aedf7a4e0_93.png)

Easy mistake。Cannot convert。ThePoer type M1 is equal to show。Can not convert。A point to time。



![](img/c2659e9ea806b288914cf08aedf7a4e0_95.png)

74。So是。😔，The show。Mei。You a star。In对。E destination。Insource。Mkey star， O。This needs to be point。



![](img/c2659e9ea806b288914cf08aedf7a4e0_97.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_98.png)

5，4，9。

![](img/c2659e9ea806b288914cf08aedf7a4e0_100.png)

Now， I believe it should work。Allright， so。Ether E is equald this 14 by total。We have a protocol。

 She this。 We have a source and destination。 It looks。Quite nice with the tabs and all。Somehow。

 it became right the line， which is kind of cool。

![](img/c2659e9ea806b288914cf08aedf7a4e0_102.png)

But it works。So let's create an I packet and see if we can add that to this thing。Yes。

How do we create an IP packet。Do we need。没爱啲。So we need to have a kind。I guess that is L 4。SMP。

And source as an。And8。 So let's just do this then。Let's say， we're standing from。わい中う。12。😔，To啊。

To a destination lift。Send to the broadcast。So 1，92，1，68 to 12 or2，5，5。And we need and。Id。

Think we can leave this a0。But we need to have this counter。そです。Well。

 I think we can just do something like this。How big was that count。In 16。

So let's say we haven' an in 16。Counender。And we have an in 16 counter pointer。嗯。

That's set the counter， too。5。😔，Counterpointer 2。Address of。And we can provide it here。

And I guess that's it。no only to色的意。😔，Pload。😔。

![](img/c2659e9ea806b288914cf08aedf7a4e0_104.png)

Equal to the idea that。

![](img/c2659e9ea806b288914cf08aedf7a4e0_106.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_107.png)

Comparth。look at this。

![](img/c2659e9ea806b288914cf08aedf7a4e0_109.png)

So we are still just showing the E。

![](img/c2659e9ea806b288914cf08aedf7a4e0_111.png)

But it。Shows all of this as well。So everything is starting to work as expected。



![](img/c2659e9ea806b288914cf08aedf7a4e0_113.png)

And if we were to create a white string， B， S。And said it equal to evil。异议。

So if we are able to evaluate this thing。Let's print。It's。Content。So。Priintic。Now， what do I call it。

啊。

![](img/c2659e9ea806b288914cf08aedf7a4e0_115.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_116.png)

It's called printex。Aprinttic。

![](img/c2659e9ea806b288914cf08aedf7a4e0_118.png)

In 8 in 16。

![](img/c2659e9ea806b288914cf08aedf7a4e0_120.png)

So， we take the beerard。We take the BS data。TheB， S size。Let's have a。Space as the limiter。



![](img/c2659e9ea806b288914cf08aedf7a4e0_122.png)

Something like this。嗯。

![](img/c2659e9ea806b288914cf08aedf7a4e0_124.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_125.png)

This should be I。

![](img/c2659e9ea806b288914cf08aedf7a4e0_127.png)

5，6，7。我系。That's not this。

![](img/c2659e9ea806b288914cf08aedf7a4e0_129.png)

Where。Okay， so this is the day done。First， we have the destination Mac， then we have the source Mac。

And we have some stuff。注意了 know。But it looks right。

So now we have successfully been able to evaluate the ethernet and everything within。And。Yeah。

 and that's all the preparations we need。 The next stuff we're going do。Is。Take care of the sockets。

The pack gets sucked。So we'll be right back after。Yeah。🤧All right， welcome back， you guys。

So before the break， we managed to get this stuff to work。

We are now able to create an ethernet packet and evaluate it down to the actual bytes that we want to send over the wire。

So the next logical step is setting up all the socket stuff。

And creating a function for sending an ethernet right。



![](img/c2659e9ea806b288914cf08aedf7a4e0_131.png)

With the containing IP packet and so forth。So， let's first see。What we currently have。

 we have some kind of setup function。 Here it is。And currently。

 we are creating a regular raw I P socket。 So we need to change this setup function。So， it becomes。

a packet socket instead。So let's check the manual page， man。



![](img/c2659e9ea806b288914cf08aedf7a4e0_133.png)

Packet。

![](img/c2659e9ea806b288914cf08aedf7a4e0_135.png)

And。We need a couple of includes。嗯嗯嗯。

![](img/c2659e9ea806b288914cf08aedf7a4e0_137.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_138.png)

There we go。So let's see， si soet at age。 we have already Linux I F packet we need。

Ethannet adult age， I don't think we need。But let's keep it for now。All right， so packet off get。

Uses this AF packet。 We need to define a socket type。And protocol。

So let's take this thing and go to our setup function and change。A I not in2。A packet。



![](img/c2659e9ea806b288914cf08aedf7a4e0_140.png)

And what about the socket type， either sora or soet datatgram？😔。



![](img/c2659e9ea806b288914cf08aedf7a4e0_142.png)

And we need the silk rule。Which we have。And then we come to the protocol field when we were dealing with the regular raw socks before。

We need to specify a protocol， and it will only catch that protocol。

But now we have the possibility of doing。This stuff。 So we grab all the packets。

 And that's what I want to do。Because I want to differentiate between them myself。

And I want to have the。Ability。Tun。😔，嗯。Well， to capture all packets on the whole network if we wish this to。

So this is good， and what about this headering load， do we still need that stuff？😔。



![](img/c2659e9ea806b288914cf08aedf7a4e0_144.png)

Let's go to the socket option。

![](img/c2659e9ea806b288914cf08aedf7a4e0_146.png)

F lost reserve。No， I don't think we need this。Let's keep it in a comment， just in case。And。

I'm not sure if this stuff is compatible， but let's keep it for now。 So this is。

The timeouts currently we have a timeout of， well， whatever we define the timeout to be。

 I think it's two seconds or something。 and I think I want to keep that perhaps。

We should lower the time out， but let's not care about that for now。

Let's see if we can still use this stuff。So let's define yet another main function。And this time。

 let's say。We have it in main。And let's。Use the。Arguments， as well。

And I believe this is going to be a main number 5 or something。Yes。So we're gonna have an ink and。

Char， double star。So we can give it some command line arguments。So， let's call main。牌子。

And provide the R C and R V parameters。And inside of here。I wanna have a。うん。

Let's check if R C is less than something。 I don't know how much at the moment。And in that case。

 we want to。Print。An error message or a usage message。

So let's print it to standard error and the usage is going to be the name of the file。😔。

And this version is going to send one single ethernet frame。So， let's provide。Yeah。

The source Mac address。Destination， my address。嗯。The source， I P。Destination， I P。And。The message。

Yeah， let's do it like this。And then well return minus-1。Allright， so we have 1，2，3，4，5。Arguments。

 which means that we want to check if this is less。Then。口？If we had one argument。

We would put a two here， so a six I guess。Because it's going to be 1，2，3，4，5。Maybe even7。

So let's create some variables to hold these things。😔，So we need to have a math。Let's call this。

Max worse。And my this。And I don't remember if our functions return pointers or the actual thing。

They return pointers。And similarly， we need to have the I P addresses。And。Those we can。Keep in the。

Yeah。32s。So I P source， IP P desk。I'm let the message be an in pointer。

And I will not add a lot of error correction and stuff here。So， max source is going to be equal to。

Make make。Based off of the first argument。Same with destination。It's the second。

And the I P address is。I'm going use the Inet address function to convert the string into a。Interger。

Same with the destination。To。3，4。And then the message we can just do。An in the8 cast。From Arv。Fuck。

And if any of these are0， we can。Quit。😔，I will not do anything more advanced than that。And。See。

Let's do a macro out of this。So we're gonna define a usage。This。Wild folks。We need to give。

I forgot that。3趣日。Us in this way， we need to provide the。And argument。So。Will be the x， in this case。

AndThen we can just do something like。Use search。😔，耳鱼。Sa here。Pretty clean。All right。

 so we need to keep。And in 32， for the。Sucket file the script。So， let's call this F D。

50 is going to be equal to the setup function。Something like this。So， at this point。

We should have everything。So let's just print an O message。And let's free up some stuff。

You can close the F D。We can free Mac source。Free Mac desk。The return Si。

Just to say that everything works as。

![](img/c2659e9ea806b288914cf08aedf7a4e0_148.png)

きて。我是 didn。

![](img/c2659e9ea806b288914cf08aedf7a4e0_150.png)

うm。Usual， I forgot all of these slashes。

![](img/c2659e9ea806b288914cf08aedf7a4e0_152.png)

For our macro magic。

![](img/c2659e9ea806b288914cf08aedf7a4e0_154.png)

And， yes， these are unusualus。So。Let's， for now， just do something like。Vvoid max source。

And make this。This is just a trick to。Do something with his variables。And silence those messages。

It will work。

![](img/c2659e9ea806b288914cf08aedf7a4e0_156.png)

When we used them later on。Still some errors。

![](img/c2659e9ea806b288914cf08aedf7a4e0_158.png)

嗯。

![](img/c2659e9ea806b288914cf08aedf7a4e0_160.png)

Those sneaky little backslashes， a。1 set。Use。Sts。

![](img/c2659e9ea806b288914cf08aedf7a4e0_162.png)

So。😔，Let's see here。We need to convert this to an in the a。Like so。This， we need to convert。To a。

Sure儿。

![](img/c2659e9ea806b288914cf08aedf7a4e0_164.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_165.png)

AndLet's also fix this one variable。

![](img/c2659e9ea806b288914cf08aedf7a4e0_167.png)

And now， I believe it will compiled。Almost。D man。Unclared。



![](img/c2659e9ea806b288914cf08aedf7a4e0_169.png)

This file is getting a little too big， I think。So let's see。 De Mark， what did I call it。Mdes。

Maybe we need a semicolon here。

![](img/c2659e9ea806b288914cf08aedf7a4e0_171.png)

And now， I believe it will compile without any warnings。Yes。嗯。That's interesting。



![](img/c2659e9ea806b288914cf08aedf7a4e0_173.png)

哦。Lix。😔，Do。This should be or0。Sa here。

![](img/c2659e9ea806b288914cf08aedf7a4e0_175.png)

Okay， that's better。So let's see， let's say we have a source map。哦，不。Well， let's check。

The network card。We don't necessarily need to use the real Mac， but let's anyway。是。Let's see here。

Yeah， this is the one。We need to convert it into our format。LikeThis。

Let's say the destination is something like this。Some I P addresses。



![](img/c2659e9ea806b288914cf08aedf7a4e0_177.png)

Okay。Maybe I was right， the first time。

![](img/c2659e9ea806b288914cf08aedf7a4e0_179.png)

All， it's so sucky pale。 And that's probably because we're not rude。嗯。



![](img/c2659e9ea806b288914cf08aedf7a4e0_181.png)

Okay， that sounds good。 Let's do a check from the beginning。To say that。 We are real。Before。

 or maybe inside of the setup。Yeah。So let's make our lives easy。And just do。S。😔，Yeah。UI。

It's equal to 0。To be。嗯。Specific about our intent。

![](img/c2659e9ea806b288914cf08aedf7a4e0_183.png)

And maybe we need some include for that。 I'm not sure。Nan。😔，Yeah， looks right。Alright。

 so we were successful in。

![](img/c2659e9ea806b288914cf08aedf7a4e0_185.png)

Yeah。In creating the actual stock。So now we need to have a function。

Which sounds one of these packets。And I think we can create that function， rather easily。

Because of all the hard work we did during。😔，The creation of all of these valuation functions。So。

 let's see here。Let's create something like。Bll sun frame。And what do we need to give as arguments。

 We need to provide the socket file descriptor。我俩。😔，How are we gonna do this。

I guess we could just provide。诶。An ethernet。Structure。And put everything in there。No。

 I think that's good。Because all the day then everything will be inside of that thing。So。

 in our main function。May number 5。Instead of printing， okay。

We are going to set up one of these things， So we need an。Ethernet structure。Which will create。

Using the may。Ether。And we need to provide in。Either type。 So let's say type I P。

A destination Me address。We do have one of those。So。This。Nax source。But what about the data。Right。

 that would be inside of the I。Which means we need one of those too。So we'll make IP。

And what kind is this going to be。I think we have a kind for ICMP。Only。At the moment。

Let's see if we go to the I。We have a tie。Kind。It's one of these here。And since we are at layer 3。

 the thing we are describing are the layer 4。 So we have I and P。TCP and UDP。

 maybe we should have one for。I don't know。 A ro version。

Which is just a message without anything else。Yeah。That's good。Problem is。How does。Our。

Make a P handle that kind of stuff。Okay， it just takes the kind。Like this。The得。That suits us fine。

So our packet is going to be L4。Ruo。嗯。The source address。Okay， it takes the sort of address。

As a string。So we can't do it like this。We will just do。Something。Yes是。😔。

We can just provide IP source。I does。Right， we need to have those I Ds and counters and stuff。是。

In 6 counter。In 16。Counterpointer。Start count0。 account pointer is going to be our counter。

Provide a counter point。No。😔，First I D， right。And set it to 0。

 And we set this to the counter pointer， and we could。Generate the I for us。

Let's make sure that we have。Ether。P。😔，Not the best user friendly。Arow message， but。Never mind。

Allright。So now we w to take our ethernet packet。嗯 said。Payload equal to our I P。take our I payload。

能。😔，It's called Ipacky。Our I packet。Payload is going to be。LetSee how we define this。To do， to do。

 Okay， it only takes ICMP at the moment。It's not good。Let's create。A union。See。Let's do Union U。

You can call this layer 4。We will type depth our union you layer4 into just layer 4。And instead of。

Instead of saying ICMP payload， we will say。Layer。F尔。回了。Like this， I guess。Let's define our union。

 you layer for。As either。IC p。橡皮 packet。Or。Ro。Ro back。

Which means we need to define what a raw packet is。And we can do that pretty easily， by just T。对。In8。

To。Something like this。So， let's see when we evaluate。The I make I。No， not make happy evil， happy。

How does it handle this， Okay， it has a case for L 4 IC P。And this is hard coded for。Rose and P。

Let's see。 Where else do we。Do anything with the payload。Yeah。And we e。The payload。

So we need to have an evaluation function for the raw version as well。

Calling this an ICMP pointer is not the best way， either。嗯。Maybe we should rewrite this function。

 It's not going to be very pretty now， but。Not much we can do for now， L 4 Ro。

I guess the protocol will be zero in this case。And instead of plus this， we can do ternary。So。

So if packet kind is L 4 ICMP。In that case， we will do。This。Otherwise。We will not。A。

And what about this stuff。We will evaluate this and get a by string back。Please stay。认识。

Skip this part。And just copy the by string。对的。And we can remove this ICMP pointer entirely。嚟首。😔。

And now we not just need to write a very simple evaluation function。Let's make this very simple。

So it's going to return a bike。It's going to return a by strain。Eval raw。And it's going to take。呃如。

Packet。And we will just return May。By its string。Provide。Go packet。And we need to have the size。

Do we have some string length function。Yes， we do。So， let's use it。And。Just take the length。

Of the in8 version of the row packet。Like this。Pretty nice。

And now we just need to add one line to our evaluation function。So， if we have a raw。

We want to run Eval Ro。Raw pointer。Okay哎。Lai。So no。My touchpa is getting a little bit annoying。

 to be honest。I think this is going to work。WeGo to our main 5。So， the i packet payload。

It's going to be equal to。Let's see here。I guess we will just the raw star。And provide。The message。

Think that would be good enough。So now we have the ethernet。 we have the I。

 We have the layer4 packets。Now we can call our functions。 Let's have some return variable。

Something like red。Perhaps。Let's say it's equal。Let's do this first。Then we suggest equal to。Senfri。

😔，We have our final scripture， and we have our etherna。Thatsい。

We have a positive return value we wan to provide。Chun。😔，Otherwiseway falses。Something like this。

And I would just need to create this function for sending the frame。

 And it's going to be pretty easy， I think。I hope。So it's going to return a bull sun frame。

We need an in 32 FD and。AndEther。比。If we don't have one of those arguments。Return false。

And we need to have a bite string。Which we get from just evaluating the ethernet packet。

 And then we have。All the series of bites。Ne have a signed integer for the return value。So let's see。

 which system color are we gonna use for sending this thing。 I think we should use a sand。

 but I'm not。

![](img/c2659e9ea806b288914cf08aedf7a4e0_187.png)

Sure。Let's see here Philscriptor buffer。leength。And possibly， flags。



![](img/c2659e9ea806b288914cf08aedf7a4e0_189.png)

Let's see if this is compatible with the ethernet packet socket。Because in that case。

 we can just do red is equal to。So。We provide the filescriptor。You provide the by string。 day done。

S圈。嗯。And then。Integer will provide the by string。啥意思？None0 as flags。We return red。

I don't think there's much more to it， actually。

![](img/c2659e9ea806b288914cf08aedf7a4e0_191.png)

Let's see if this thing compiles。Payload has incomplete。Ti。



![](img/c2659e9ea806b288914cf08aedf7a4e0_193.png)

嗯。Sure enough， it does。But with structures， we can do that。But apparently， not with this stuff。

So we need to be a little bit more clever， I guess。Let's remove this。And will do the type de。Union。

You。4 in layer，4。And this is one，2，3，4，5 lines。And we need to put this above。Here。

And do we have the ICM P S， we do。

![](img/c2659e9ea806b288914cf08aedf7a4e0_195.png)

Yeah， I don't think we need to change anything else。Incomp types， when assigning the type layer 4。

From I C star。

![](img/c2659e9ea806b288914cf08aedf7a4e0_197.png)

Thats right，63。So， this should be。Layer 4， instead。The guess should be point。



![](img/c2659e9ea806b288914cf08aedf7a4e0_199.png)

Csty union type from T。 not present in union。That's a little bit annoying。

 So how do we zero this thing out。

![](img/c2659e9ea806b288914cf08aedf7a4e0_201.png)

Can we do。Just this， perhaps。

![](img/c2659e9ea806b288914cf08aedf7a4e0_203.png)

Nope。

![](img/c2659e9ea806b288914cf08aedf7a4e0_205.png)

So let's do something like this。 We set it to false。And we add some bogus value。

 It will not create any real oil。え。What is called overhead。SoLet's just say， bogus。嗯。Booone。Bgus。

Or something。

![](img/c2659e9ea806b288914cf08aedf7a4e0_207.png)

Let。

![](img/c2659e9ea806b288914cf08aedf7a4e0_209.png)

Maybe we can do something like this then。So let's call cast this into a row。

And we'll say this is the packet payload。都。Ro back。



![](img/c2659e9ea806b288914cf08aedf7a4e0_211.png)

That should be the same result。Alright。就是。😔，Union type。Val worth scalar is required。



![](img/c2659e9ea806b288914cf08aedf7a4e0_213.png)

リエ？So， if packet。配篓。😔，Go packet， let's say。Same here。Raw packet。

But the row packet does not have a size。This is the problem when we rewrite some software to do。

Something not the same。How do we do this。Well， I guess we need to do a turn right here as well。

So we're gonna plus。 And if we have a。Ping。So let's see the packet is the I P packet。

Kind equal to L 4 IM。In that case， we want a plus。Yes。But this is going to be the ICMP。It sized。

And otherwise， we will do the string length。Of。Packet。Pyload。对。Rober。Nothing声年。Not very beautiful。

 but。It's gonna do the trick。

![](img/c2659e9ea806b288914cf08aedf7a4e0_215.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_216.png)

1，24 has the same problem。Heload。の packet。And。To be specific about this， when I do this check here。

 I'm not checking。If this is a raw packet， per se。I am checking， if。This pointer is0 or not。

 so it can refer to。An ICMP pointer。As well。Just so you understand that。Alright， so。

Let's do a ternary here， as well。If our packet。Kind is。L4 I P。Then， we want a plus。This thing。

Otherwise， the。Stngland。哦。Backin。Hello。Rope again。Doest in days。Like so。

But why do I have this check here as well。Here I add the， okay， I add the handleer。



![](img/c2659e9ea806b288914cf08aedf7a4e0_218.png)

That's sensible， actually。嗯嗯。嗯嗯。Same problem here。

![](img/c2659e9ea806b288914cf08aedf7a4e0_220.png)

1，27。This needs to be the。就。

![](img/c2659e9ea806b288914cf08aedf7a4e0_222.png)

I think people。

![](img/c2659e9ea806b288914cf08aedf7a4e0_224.png)

The same problem at 1，43。到。Well，Maybe we can actually do IP packet here just to communicate our intent a little bit better。

Let see。😔。

![](img/c2659e9ea806b288914cf08aedf7a4e0_226.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_227.png)

To。Tin。😔，It payload needs to be if packet payload raw pack。And here we do a check for L 4 ICMP。

And we add。Heer。So let's move this into this ternary， as well。So， we're gonna plus the packet。

Heyload。Do't I think people get size。Otherwise。Will just take。The string length。哦。F good。Youello。

Robot。

![](img/c2659e9ea806b288914cf08aedf7a4e0_229.png)

And this all affects that stuff。Hopefully， there's not much more of this。But it is。



![](img/c2659e9ea806b288914cf08aedf7a4e0_231.png)

To 20。Right， this should be removed。

![](img/c2659e9ea806b288914cf08aedf7a4e0_233.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_234.png)

To 48， this is getting old。Backet payload。あき。

![](img/c2659e9ea806b288914cf08aedf7a4e0_236.png)

Cannot convert to a pointer type 2，51。

![](img/c2659e9ea806b288914cf08aedf7a4e0_238.png)

Guess we need to do a turn here as well。So if the packet kind is L 4 IC P。

We wna eval the packet payload as an i and packet。Otherwise， we wantt evaluate it does。嗯。Heello。

Ro back。

![](img/c2659e9ea806b288914cf08aedf7a4e0_240.png)

Love terrorists。Alright， so let's see here，34。 I guess were missing a comma。



![](img/c2659e9ea806b288914cf08aedf7a4e0_242.png)

Yes， we do。

![](img/c2659e9ea806b288914cf08aedf7a4e0_244.png)

一个若。Implicit declaration。

![](img/c2659e9ea806b288914cf08aedf7a4e0_246.png)

K。😔，て call。一个。Okay， I never created one of the signatures。So。😔，B string。Eval room。And it takes。

The rule。知top了。

![](img/c2659e9ea806b288914cf08aedf7a4e0_248.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_249.png)

4，6，5。 Okay， now we're down with the main function。Or阿 San f。Even will。And this is just E。



![](img/c2659e9ea806b288914cf08aedf7a4e0_251.png)

Lot of small typos。AndNow we're down to one line。嗯。Expected。Specifier qualifier list before。



![](img/c2659e9ea806b288914cf08aedf7a4e0_253.png)

34。嗯嗯。I've never seen that。

![](img/c2659e9ea806b288914cf08aedf7a4e0_255.png)

Specify qualifier list before raw。

![](img/c2659e9ea806b288914cf08aedf7a4e0_257.png)

Let me。Think a little bit about that。 And were。We'll be right back after this。Sup， guys。

 welcome back。So before the break， we managed to create our。Fun for sending a frame。

On the Ethernet network。

![](img/c2659e9ea806b288914cf08aedf7a4e0_259.png)

So， now， we're gonna。Do the troubleshooting。So let's see here where we're at。Right。

 were having some problems with this raw thing。

![](img/c2659e9ea806b288914cf08aedf7a4e0_261.png)

嗯。嗯。So let's see if we can figure this out。So what we wna。

Do with this code is if we call this eval function or macro。

And we provide something of the type of rawar。 Then we want to call the evil raw evil raw function。

Same as we have done with the other ones here。And it seems like。We have。😔，Don pretty much the same。

Synt。One thing I wanna try， though， since this is a regular。In the8 pointer， actually。

 maybe we can do this。And we can let this。Default。To the evil rule。Maybe that。Could。Actually， work。

Let's see what happens。

![](img/c2659e9ea806b288914cf08aedf7a4e0_263.png)

Okay。That's nice。6，21。

![](img/c2659e9ea806b288914cf08aedf7a4e0_265.png)

Right， this should point to the address of the calendar。



![](img/c2659e9ea806b288914cf08aedf7a4e0_267.png)

Assignment to in 32。Make integer from pointer。

![](img/c2659e9ea806b288914cf08aedf7a4e0_269.png)

That's correct。We changed the type of this thing。Because before we。Had the IP source and IPD。As。

Apointers。 we need to。Let's see here。We need to change these into into the8 pointers， instead。



![](img/c2659e9ea806b288914cf08aedf7a4e0_271.png)

So。😔，And what about this Exp identifier or blah， blah， blah， blah， blah。



![](img/c2659e9ea806b288914cf08aedf7a4e0_273.png)

6，39。This shouldn't be I P equals。 It should be I packet equals。Same here。 I the pack kids。



![](img/c2659e9ea806b288914cf08aedf7a4e0_275.png)

What about this。In compatible types， when assigning。TheT layer 4。Tyral star。



![](img/c2659e9ea806b288914cf08aedf7a4e0_277.png)

Okay， it's the same thing here。This needs to be the payload do。Roaw packet。



![](img/c2659e9ea806b288914cf08aedf7a4e0_279.png)

And now I believe it will compile。And it did。Okay， so how do we test this out。i think感 gonna你。😔。

Let's see here。Let's log out from this server。Attached to this screen。

Let's connect back to this server。And into the directory。 And let's reset this。To our home。

And then I'm gonna connect to another server。系。A gas server。And here， we can。Listen for the packets。

And then， we can know。Use the other one to send。So， let's see。11。😔，To say。Let。Grab this Mac address。

偶尔。No， actually。Since this is on another network。We can't just。

We can't just send an ethernet frame to it without using I P， because。

It needs to go through a router。It would be better， if。Both of these servers were on the same。

Local network。嗯嗯。But that can be arranged。We need to set up。Temporary network， just for these two。



![](img/c2659e9ea806b288914cf08aedf7a4e0_281.png)

So let's see how we can do that。We need to put them on the same local network， basically。So。

 let me log in to my。Virtualization server。Where I have all my virtual machines。

It's a quite cool Sir this。 Actually， I have it in a data centre outside of Stockholm。And。

I have 192 GB of rom in this。So it has potential for a lot of different virtual machines。Allright。

 so let's see here。We need to set up a new network。So what are we going to call this one。你咪事嗯。😔，嗯嗯。

Let's call it， Esther。Same as the project。And let's just pick the Van I D for it。 I don' know。590。😔。

Maybe that's still high。8。Okay。So now we need to create network cards。On these two servers。

 and I think I can do it while they are still running。 I'm not100% sure。I think so。So， let's go into。

The Intel 32 machine。Settings。A network adapter。And this new should be on the ethernet。Like this。

And then， we go into the。Aero gap machine， which is this one。We do the same thing。

 We add a new network adapter。And make sure that it's on the Ether network。



![](img/c2659e9ea806b288914cf08aedf7a4e0_283.png)

嚟声。And if everything has worked， we should see a new network adapter here。 So currently， we have 1。

92 and 2，24。And now we have 256 as well。That's good。So let's。Give it some kind of I P address。So。

 this。2，56。Should be。1，72。25，0，1， let's say。Let's make it。Slash 24 network。Let's activate it。

And then we go to the Intel 32 machine。Log in as the route。And。This is the interface， so。2，24。

And we have1，72。25，0。5， let's say。Alright， so if this network works。

 we should be able to ping the other side of the link。Let's start by pinging ourselves。 So 172，25，0。

5。That works。 And what about just one。That works， too。Let's just for the sake of it， tried。

Pinging the other side from this one。0。25。All right， that looks good。So how do we。And。

How do we monitor if we are able to send the ethernet frames。Not really sure。 We're gonna use TP now。

 That's for sure。And we want to see ethernet frames。 Can we just type Ethernet。意思。And Cla replied。

In the wrong contact。Because sniffing for a pay packet is quite simple。

 but how do we sniff for ether。

![](img/c2659e9ea806b288914cf08aedf7a4e0_285.png)

Maybe we can give it。じつく。So， TC P dumb。Be色呢。The problem is， this is going to。Listen for。

Fter by Mac address。 That's good。Tisipear damp Ether hostst。 And then the Macre。 That's good。

 That's very good。

![](img/c2659e9ea806b288914cf08aedf7a4e0_287.png)

So。😔，Let's go into our。Other machine。And let's use the real back addresses for now。

So our brand new network card has the following Mac address。Anticip Peter wants it in this format。So。

 let's see。Have to see。Sren participate dash and dash I。EN S 2，56。Ether host this one。Alright。

 it's listening。So let's see if we can do this thing。By the way。

 we need to grab this machine's mac dress as well。Okay。So the source Mac， that is our worst。

 Let's save this here。So this is our Mac address。Alright， so our source is this one。

 and we need to format it properly。And our destination。Is this one。And our source I P is once72，25，0。

25。Destination is 1，72。25，0，1。 And the message is， hello。And we need to run this as root。Okay。

 return equal close through。But I don't see anything here。我我我。H why is that。

Let's see if we can get some information by running ats。嗯，哼。No such device。

 I think we need to specify what。What interface we're gonna send this thing over。Okay。

So how do we do that， I guess we need to do a bind operation。So let's prepare for that。

soifti S's address。Suckling tea。Eland。Wonder if this is the right thing， though。

Let's check the package manual， once again。Use buying in specifying an address。And okay L L。

Right it down。So addresss， L， L。

![](img/c2659e9ea806b288914cf08aedf7a4e0_289.png)

Let's create one of those。 So this we can do inside of the setup function。So。

 we need to have a stroke。是。Addres， L， L。call itそ。

![](img/c2659e9ea806b288914cf08aedf7a4e0_291.png)

And what do we need to put in here？

![](img/c2659e9ea806b288914cf08aedf7a4e0_293.png)

S， L， L family， always A F packet。S L L firmly。

![](img/c2659e9ea806b288914cf08aedf7a4e0_295.png)

This。Protoical。That's0。

![](img/c2659e9ea806b288914cf08aedf7a4e0_297.png)

I guess it's。This thing。so。Sello。Prostoical。Is it a ton。嗯。Ether呢。Pi。😔，哦。



![](img/c2659e9ea806b288914cf08aedf7a4e0_299.png)

Ive index。Right， we need to figure out。What number the interface has。Let's wait with this one。

H a tie。Our hardware type， What is that。When you send packets， it's enough to specify， blah， blah。

 blah， blah。And this is for receive。Okay， so let's wait a little bit with this stuff then so。



![](img/c2659e9ea806b288914cf08aedf7a4e0_301.png)

This is equal to something。

![](img/c2659e9ea806b288914cf08aedf7a4e0_303.png)

And。一体。😔。

![](img/c2659e9ea806b288914cf08aedf7a4e0_305.png)

We can also wait。

![](img/c2659e9ea806b288914cf08aedf7a4e0_307.png)

What else we got。

![](img/c2659e9ea806b288914cf08aedf7a4e0_309.png)

Yes， we don't。 We can。Forget this one。 We need to set this one， but。For now， I will just。Do this。

Because this， we need to do some other lookups and stuff。



![](img/c2659e9ea806b288914cf08aedf7a4e0_311.png)

The H A type packet type is done。 H A lamb。Length of address。Is that in， Sir。I guess it's in bad。

Well， and my address is 6 by。48。

![](img/c2659e9ea806b288914cf08aedf7a4e0_313.png)

L the address。

![](img/c2659e9ea806b288914cf08aedf7a4e0_315.png)

6。And then， we need to specify it。The address。您的笑儿。😔，Weird for man。To save a market yourself。



![](img/c2659e9ea806b288914cf08aedf7a4e0_317.png)

Well。😔。

![](img/c2659e9ea806b288914cf08aedf7a4e0_319.png)

No SL address。

![](img/c2659e9ea806b288914cf08aedf7a4e0_321.png)

So I guess we will need to string copy then。Do we have a string copy function。Hello。Well。

 we can use the regular copy。Let's copy into。The。In the8 version of so。S L L。Addres。

It needs to be the address of this。And we wan to copy the source Mac。Which we need to define。

And the size is going to be 6 bys。So we need to take two arguments here。

We need to take an in age with the。Interface name。And。A new day。Well， let's do this。咩。Soer。So。

 I guess we need to。I'm not really sure how we gonna do this， but let's。Let's do this。

Let's clean out this structure before we do anything else。 So we0。Overso。再一首。😔，Stke。Sock address。

 L O。All right。And this right here。The ifF index。We need to create some function which turns an interface name such as E。

 T， H1 or E， N S 2。56。Into an index number that the operating system can understand。So。

 let's call this。I F2 index。And we need to provide the。Alright， something like this。

So now we need to do a couple of things。 First， we need to modify the signature， so it matches this。

 and then we need to modify the call sites。As well。Let's see here。Let's go down to。

Our setup function。Which is now going to take an in star。And。A meulous pointer。

And at our main function， we need to modify the usage first。

Because now we need to provide an interface as well。And in our main function。We need oh。

 now we need to move everything。Well， it's not。So this will be two。 This will be three。

This would be 4。 This will be 5， and this will be 6。We are going to need。An interface。

And the mac address we have already。Let's set the interface equal to。The one like song。And let's。

This validity， as well。And down。Se up function。See here。We need to provide the interface。

 and the source method。Alright， let's go back to the setup function。What did we have。

 We wanted to create。And I have to index， we can create our。Signature for now。

Maybe we can let it here。So， it's going to return。In the。Let's say， in 16。뭘 이제。Actually。32。

And before I forget。Let's also convert this。And in theger。Let's do in 16。

 We're not gonna have more than 65000 interfaces， I hope。

So we have an interface and we want the index。And we provide an intake pointer to the interface。

We are talking about。And when we have all those things。And we have a socket。

 We w to bind this to that socket。So。Our T。Is going to be equal to bind。And we provide our。Our S。

That's a socket file descriptor。And then I guess we need to cast this into astruct。Sock address。

And we provide this so。The size of。Yeah。It true。Soet address。Hello。Something like this。



![](img/c2659e9ea806b288914cf08aedf7a4e0_323.png)

And。Let's check for buying return value。 I think it's supposed to be 0。



![](img/c2659e9ea806b288914cf08aedf7a4e0_325.png)

On success，0 is returned， otherwise，-1。And if we have an error at the bind， we will。

Close down our socket。That's the S。Well， if soet fails， we should。Should return an error， right。Well。

Something like this。And。😔，Same here。0。Okay， so that's just。 now we only need to。Do this day。

Figure out how we can turn。And it name into an interface index。

And I guess we need to linearly search through all the indexes and come and compare the index name。

So this is going to be an in 16。I。Inindex。And we'll have an in the day。Toerface。Like so。

And how do we do this？

![](img/c2659e9ea806b288914cf08aedf7a4e0_327.png)

Hm。How can we figure out。How to do this thing。Turning an interface name。我。We know that I have config。

Com。Needs to do this。Because it prints all the interfaces。So if we were to run this in atrays。

Pipiepe it into a file。Then， we may be。Be able to find something， which makes sense。m。I have come。

This might be。So I O C T L is the system call。 And let's remember this。C，G， I F con。C，G I Fcom。

Maybe this。No。😔，Is there an I O C， T， L， I F。Com。😔，How do we search in the man table。Yeah。

There must be a command to list everything which contains the search word。What about a。

I will sit down。No。A regular expression。That sounds good。So we should be able to do I O， C， T L。

Do plus。Look at this。Alright， do you have something appropriate here。Not really。

What if we were to search the contents。Of the man page for C G I F con。How do we search the contents。

Okay the manual pages are stored at this location。Maybe we can just search this then。

If we do something like。Grith dash or。C， G I F Kf in this directory。Nothing。

What about just I have gone。We don't get anything for I've con either。 Maybe that's not。Correct。

Location。User chairman。哦，已经。Zhixi。That explains it。So， let's add。Let's use see， Grin。Our option。

 not supported。I wonder， I think I have done something like this before。Let's see here。If I go into。

My re。My。What did I call this。知道。😔，umbrella。Think I did something like this here。

This is an old project， which。We're trying to。It was trying to block denial of service at。

This is the right thing， I think。Get I address。Okay。Get I F address。H， here we are。

So it was a specific system called just for this purpose。Get interface addresses。

Create a linked list of structures describing the network interfaces。The link list。So。

 this iPhone name is then。String name of the interface。Do we get that。Id or the index。

Or do we need to just count them， perhaps。Okay， so now I see this does the opposite， basically。

This compares the I P address。So we give it an IP address and you get back the interface name。

But what do we do with that interface name。Because that's in。Well， let's try。

 let's go through that list。And just count the interfaces， and that。

And let's try if that becomes the index。I think that's the best idea。



![](img/c2659e9ea806b288914cf08aedf7a4e0_329.png)

So。Let's add the headers。So we need to have one of these structures。



![](img/c2659e9ea806b288914cf08aedf7a4e0_331.png)

Let's see， struck。I have。Addresses。

![](img/c2659e9ea806b288914cf08aedf7a4e0_333.png)

We also need to have one for each。Individual。Address。



![](img/c2659e9ea806b288914cf08aedf7a4e0_335.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_336.png)

And something for the return value。Something for the end。

So red is going to be equal to get I F addresses。

![](img/c2659e9ea806b288914cf08aedf7a4e0_338.png)

this is not a system call。 This is a library call。

![](img/c2659e9ea806b288914cf08aedf7a4e0_340.png)

Maybe we can try to go deeper when we get this to work。



![](img/c2659e9ea806b288914cf08aedf7a4e0_342.png)

Does it not mentionally。System call for this， no。

![](img/c2659e9ea806b288914cf08aedf7a4e0_344.png)

Well， well， let' see。

![](img/c2659e9ea806b288914cf08aedf7a4e0_346.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_347.png)

We need to provide the address of。

![](img/c2659e9ea806b288914cf08aedf7a4e0_349.png)

The head of the list。What's the return values。On success，0， okay。h。



![](img/c2659e9ea806b288914cf08aedf7a4e0_351.png)

Hm。So how can we signal an error here。Let's do something like this。嗯。All right。

 so now we have the have now we have the head of the list。We need to do a four loop， where we set。

P equal to。嗯。Head to begin with。

![](img/c2659e9ea806b288914cf08aedf7a4e0_353.png)

And and we're gonna to iterate as long as。我的爱。

![](img/c2659e9ea806b288914cf08aedf7a4e0_355.png)

Okay， until it's。0。So as long as we。Have a pee。And at each iteration。P is going to be equal to P。



![](img/c2659e9ea806b288914cf08aedf7a4e0_357.png)

Something。

![](img/c2659e9ea806b288914cf08aedf7a4e0_359.png)

I thought Nick。So collect this。And what do we want to do？At each of this。

 we need to compare the interface address， and we need to。Keep count， as well。So。

Let's initialize our index to 0。And increase is by。Wen。😔，Every time。😔，And if this P。



![](img/c2659e9ea806b288914cf08aedf7a4e0_361.png)

I name I yes。

![](img/c2659e9ea806b288914cf08aedf7a4e0_363.png)

Yes。Well， we need to compare this。 Do we have a string compare function or something like it。

We have cooked。Let's write one。 very fast。So。Bll string。Compare。And we have an inth a。

A and indeed date B。Bll string， compare。Indeed A， indeed B。So we need to point。The two pointers。

An a pointer and a big pointer。A bo for the return value。It's in to true。A for loop， where we said。A。

2 equald a。B pointer衣裤。B。And we're gonna loop as long as。Well。😔，We need to have both and a。And。😔，B。

And at each iteration， we want to increase a pointer。And the B pointer。Something like this。

I check if。The current position of a pointer。Is equal to the current precision of B pointer。

And if they are not equal。Then we wan to set red equal to false。Embre。And then， we can just return。

That should go through。The these two strengths and compare them one by one。So， if。String compare。

Of this thing here。If this is equal to the interface。We need to signal somehow that it actually。

Completed。But let's do the same here。 We'll do a bull rest。Or。Bokay。Let's say。Are okay to。False。😔。

But if this happens， we wna。Said it to truth。Great。So by the end of this day。If。We didn't find it。

do this。If we didn't find it。We wont return。I。Well， we can't return an  error here。

 So let's do this instead。Let's assert。Yeah。嗯。It will not look very good。Let's rename this， too。

Bound。Interface。And I rename this variable just so this assert message， if it fails。

 will be more understandable。So let's assert that found interface is equal to true。And， if not。

It will exit。Otherwise， we will return。The end。And I guess we need to free this structure。



![](img/c2659e9ea806b288914cf08aedf7a4e0_365.png)

At this point， as well。Free I F addresses。刘文。I thought we need to free every single one of them。

Do they do it in an example。Okay， there this。Free the whole thing。Or no， they can't really do that。

 can' they。It's a linked list。

![](img/c2659e9ea806b288914cf08aedf7a4e0_367.png)

Well， maybe they can。嗯。So。Free I F addresses。Ha。I guess this should work。



![](img/c2659e9ea806b288914cf08aedf7a4e0_369.png)

Let's see if it compiles。From incompatible pointer tie。Maybe we shouldn't do this。😔。



![](img/c2659e9ea806b288914cf08aedf7a4e0_371.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_372.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_373.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_374.png)

Cannot convert to a pointer tie。

![](img/c2659e9ea806b288914cf08aedf7a4e0_376.png)

Well， it is a pointer。 So I guess we just。2。😔，思ませ。Yeah。Guess we can just do this。

Im not sure if this is going to work， though。Well， well， we will see。We will say。



![](img/c2659e9ea806b288914cf08aedf7a4e0_378.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_379.png)

6，89。This should be map。So。

![](img/c2659e9ea806b288914cf08aedf7a4e0_381.png)

What is this Head is used， uninitialized。

![](img/c2659e9ea806b288914cf08aedf7a4e0_383.png)

Okay。Let's see here。We could make。This。Like this as well。 So let's do head and。P。And let's。

Put the address here。Before。Do this。嗯。

![](img/c2659e9ea806b288914cf08aedf7a4e0_385.png)

To。Okay， to compose。That is good。Let's see。嗯。First， let's check what the name of the interface is。对。

And let's see if we find the last time we ran this。Here。😔，So now we need to add it。

To face an name here in the beginning。Okay。Still don't see anything， though。😔。

So let's see the bind operation as a cell protocol。Ieth index。I have name to in。呃。E N S 1，92。不。

What is this。Mappings between network interface， names and indexes。Inice is。

So there is a function for this。

![](img/c2659e9ea806b288914cf08aedf7a4e0_387.png)

Ne I F dot H， shoe have this。

![](img/c2659e9ea806b288914cf08aedf7a4e0_389.png)

I want to test this function and see if it returns the same thing as ours do。



![](img/c2659e9ea806b288914cf08aedf7a4e0_391.png)

Let's create a temporary main function。嗯。

![](img/c2659e9ea806b288914cf08aedf7a4e0_393.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_394.png)

Onside in。

![](img/c2659e9ea806b288914cf08aedf7a4e0_396.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_397.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_398.png)

So how do we call this？I have name to index， and just provide。



![](img/c2659e9ea806b288914cf08aedf7a4e0_400.png)

Streight。K。😔。

![](img/c2659e9ea806b288914cf08aedf7a4e0_402.png)

On the error，0 is returned。 Ok， so the index cannot be 0。 That's interesting。



![](img/c2659e9ea806b288914cf08aedf7a4e0_404.png)

Alright， So something like this。And let's create a signature and。Here。



![](img/c2659e9ea806b288914cf08aedf7a4e0_406.png)

ha， that makes sense， actually。Because our starts at 0 and。



![](img/c2659e9ea806b288914cf08aedf7a4e0_408.png)

Theirs can't return 0， because that would be an error。Right， right， right。That's good。 actually。

 That means that we can actually return an error without doing the assert。So， I have to。

So instead of asserting this here。You can just do this。The same down here。So if we haven't found in。

 the F will return 0， otherwise， we return in。And we will start our index， at1。Okay。Exciting stuff。



![](img/c2659e9ea806b288914cf08aedf7a4e0_410.png)

嗯。So let's try this again。嗯。

![](img/c2659e9ea806b288914cf08aedf7a4e0_412.png)

Okay， this time， it uses the right。Interface， at least。And our source Mac address is this。0，0。0 C。

Okay， it does not look right。No wait。 It is actually，0，0。Cerious c。2 nine nine来。It worked。But why。

Doesn't it。Ser packet。Message too long。 And why doesn't it。Return an error。 Why does it return。

Rt is equal to true。That is the first thing you want to。If we have a rat， we return true is false。So。

 the sound frame must。Not work properly。The return value。Which is a signed integer。Is it good to son。

Okay。We need to do something like。If the return value is more than 0。Then we w to return true。

Otherwise， false。

![](img/c2659e9ea806b288914cf08aedf7a4e0_414.png)

Okay， that makes sense。So our problem is message too long。😔，mmm。Message。うラ。

The socket type requires that message。Be sent atomically。And the size of the message。

To be sent made this impossible。

![](img/c2659e9ea806b288914cf08aedf7a4e0_416.png)

That's。Let's see if we can print this。Well， let's print the size first。



![](img/c2659e9ea806b288914cf08aedf7a4e0_418.png)

2000。27000 B。Yeah， that sounds a little bit too much。Because our message is just， hello。😊。



![](img/c2659e9ea806b288914cf08aedf7a4e0_420.png)

How is that possible。

![](img/c2659e9ea806b288914cf08aedf7a4e0_422.png)

哦，喂的在。😔，呵呵呵。😊，Payload。Itself is very much too big。 I guess it has to do with us。



![](img/c2659e9ea806b288914cf08aedf7a4e0_424.png)

That would never。And Ill terminated it。That be。Let's see。 How does our main look。Ro back again。

Is equal to the mess。He。Let's try Use some temporary buffer。In8 above。16。

And instead of setting this pointer here。Or we can set it， but。Let's do a。sco the。Let's see here。

Let's copy into our。Laer。This argument。Something like this。

And then we can set our message pointing towards the buffer instead。Will this make a difference。

Let's also go to our sand frame。Let's quit after we have done。



![](img/c2659e9ea806b288914cf08aedf7a4e0_426.png)

得路。😔，Sa thing。

![](img/c2659e9ea806b288914cf08aedf7a4e0_428.png)

So that's not it。I have an idea。 We have a couple of main functions。😔，And our main 4。

Or made four used to work。So let's see if it still works now。This is a good way。嗯。嗯。

Saving all the main functions previously is good in occasions like this。



![](img/c2659e9ea806b288914cf08aedf7a4e0_430.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_431.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_432.png)

Okay， so here it works。What is this exactly We have。Either it packet in an I P packet。



![](img/c2659e9ea806b288914cf08aedf7a4e0_434.png)

But。Does it still work if we have an ICMP packet。我です子が。How do we create the one of those。Make I。

We need a time。😔，I think we need to look at the actual function， make ICMP。Okay， so we need a kind。

 We need some。Da的。And the size。In this date， there needs to be a pointer， which we already have。Okay。

So， let's go to our。Min for。Let's add one of those。 So ICMP and ICMP。

Let's say our ICMP packet is equal to make ICMP。And we need a kind。 Let's say this is echo。你 some得。😔。

ABC。The size of this is 4， including the null bites。This needs to be。16。嗯。Our I P packet。Pyload。

It's going to be。Or payload。Dot ICMP packet is going to be the ICMP packet， like so。



![](img/c2659e9ea806b288914cf08aedf7a4e0_436.png)

Crupt corrupted top size。Okay， because the。IC packet in turn， does not have a payload。



![](img/c2659e9ea806b288914cf08aedf7a4e0_438.png)

嗯。Okay， so we need to create a pink packet。Let's do that， then。We need to have a strap。嗯。

Did we call this S。Yeah，B。This is the。So this is the pink packet。And what is it contained。IC。对。

Let's say the pink packet is equal to。Stuck this。拼。😔，Below。And we want to mal look the size of str。

Struck a p。Plus。For by自车。嗯。And then， we'll set the。Fields。So。The idea。Will be something。

The seek will be something else。two。😔，And the day。And this is an array。

 So we need to take the address of this。Let's copy ABC。Size 4。嗯。3， in this case， I guess。嗯。Okay。

 so now we have a ping packet。So we can set the IMP packet to。热外贴儿。When we create the S& packet。

 we need to refer to the pink packet as its data。So。This is going to be the。The p。

And we need to calculate the size， once again。Thepin。Plus。For。



![](img/c2659e9ea806b288914cf08aedf7a4e0_440.png)

Right。K。I simply packet payload。Kind echo size 8 B of Pa。 That makes sense。This does not look right。

 though。

![](img/c2659e9ea806b288914cf08aedf7a4e0_442.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_443.png)

Corrupect the top size。So， we are basically overring。And。The heap so low。



![](img/c2659e9ea806b288914cf08aedf7a4e0_445.png)

I wonder what would happen if we just wna descend。hel。AnM the。

So we have an ethernet header an IP header， but then an empty payload to this。

Something like this would this work。

![](img/c2659e9ea806b288914cf08aedf7a4e0_447.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_448.png)

Okay， at least it doesn't crash。So， let's go to our。3。Fe。😔，And remove this。



![](img/c2659e9ea806b288914cf08aedf7a4e0_450.png)

Okay， red is equal to true。And we got something， didn we。Let's see。 if you send it again。Yes， we。

We get something。From this Mac address。To our correct market。

 So we are able to send an ethanneterate。And it interpret this program interprets this as。

A DS A P packet。Maybe that's because if we check。Et cea， protocols。The protocol 0。

 which we are currently using IV 6 hop by hop option。But， we are able to send。

An actual etherist frame。 And that was our primary intention at this point。So this is pretty cool。

Can we spoof our Mac address。Let's see if we can。If we wanted to create an artificial one。

 let's say 0，0，0，1。38， a 4，99。0，0。It didn't like that。We did not get an error， though。I wonder if。

It has to do with our。See here。美女。Became the wrong interface or something。Well。

We can figure that out later。But this is pretty cool， actually。

So I think this will be enough for today。 We have successfully been able to send an even。

I hope you like this episode。So please like and subscribe， and I'll see you soon。

 Thanks for watching。 Thanks for today。

![](img/c2659e9ea806b288914cf08aedf7a4e0_452.png)

![](img/c2659e9ea806b288914cf08aedf7a4e0_453.png)