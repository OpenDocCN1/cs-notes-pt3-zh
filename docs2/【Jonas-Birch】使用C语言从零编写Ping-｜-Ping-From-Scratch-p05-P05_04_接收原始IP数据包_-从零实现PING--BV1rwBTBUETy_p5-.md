# 【Jonas-Birch】使用C语言从零编写Ping-｜-Ping-From-Scratch-p05-P05_04_接收原始IP数据包_-从零实现PING--BV1rwBTBUETy_p5-

In this digigal jungle。Where packets vanished like damees in the fog。

 One man's got of chasete the truth。Names Doctor Jonas， I ain no hero。

 just a programmer with a grudge against unresponsive hopes。Yeah， you know the type。

They're ones that ghost you fasterted than a bad day。Tonight's case， the elusive pain。

That sneaky utility， The shouts， hay you alive into the void。

But the stock one got baggage bugs limitations like a snitch with a loose lip。

So I'm building my own from scratch。 Ra sockets， I C closed the works， no short cuts， no libraries。

 just me the code。And a bottle of coffee。Stick around， Ki。

 where diving into the shadows of networking might get messy。 might get funny。 But hey。

 in this line of work， if you can't laugh at a time out error， you're probably of line。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_1.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_2.png)

So guys， welcome to today's show。So today we are going to try to finish our ping。

We have been written from scratch and we're going to take care of the function that receives an IP packet last time we created the send IP function。

And we managed to be able to send a proper ICMP packet。But。I discovered a bug。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_4.png)

And here I am load into my books。Ending in dot 6。So this is what I want to ping。2。

So I'll start T P dump where check for ICP and the host address of 10。Like this。

 this is the IP address over my coding machine。嗯。I need to say S&。So first。

 let's try to send one packet using the regular。Ping software。And as you can see。

 we get this pink packet， ICMB echo request。And we get a response as the MP echo reply。

So this is what this is the result we are looking for。But when we run our code。ね。As we can see。

 it's from this to this。We do get the proper ping， and it looks right， every field。

But we don't get the ping reply。So that means that this packet must be malformed somehow。 Otherwise。

 my Linux machine would have responded with a ping reply。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_6.png)

And after some troubleshooting， I figured out what the problem was。Yeah 응。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_8.png)

So。Do you remember this。Check some thing that we code her。

Which goes through every part of the packet， 16 bits at a time and sums it all up。Well， at the end。

 I return the reverse ending of what it currently is。So it becomes a big Indian from Little Indian。

But since everything of this is already calculated。Best of big India。We should not。Reverse it again。

So here we should just return the return value。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_10.png)

And if we do it like this。And recomple this thing。And we rerun it。Now we get the proper response。

So now we know that our ping works。 It it sends a correct packet。But。

What's left is receiving the ping reply， making sure that。Well， the connection goes。

In both directions。So this is the task of today。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_12.png)

We are going to implement。A function which is going to receive。And I pay back it。So， basically。

 we wna do。Something like， do you remember the data structures we have。 So， for instance， we have an。

Let's see where it is here。 We have a ping packet which has all the fields that we find interesting like the kind of the source and the destination。

 I P addresses and stuff like stuff like that。And then we use an eval function to evaluate this into a string containing all of these fields necessary for actually sending an IP packet on the network。

Well， now we want to do the reverse。So we want to receive a packet and it's going to be delivered in this format。

Then we need to run the check some algorithm and make sure that it's correct。

And then we need to transform this into this data structure so we can present it to us and compare and stuff like that。

So let's get on with it。All right， guys， let's do this thing。😔，Yeah。So let's create the function。

 which receives one。I P packet。So， let's see。Where we should put。Yi。Here is our Sundayai piece， so。

嗯嗯 응。嗯。I guess。We w to return and I back yet。This is going to be called。It's sand I really。teve。

And what do we need， Let's see this in 32 is this。must check， send I。 Okay， so that is the。

There is a raw socket right。嗯。Well， we do need the。So。

This is a raw socket and do we need anything else？😔，I don't。Think so。Let's start there， anyway。So。

Let's go。Appearear。This function。I P receive。IP。32 S。And we're going to need a buffer。So。

How big does this buffer need to be。Well， we are not going to support jumbo frames。

 which are IP packets on the size of 9000。byイ。So the regular M U。

 as it's called maximum transmission unit， is 1500。 and then theres some headers and stuff。

 so maybe 1540 or something。And。Which means that our buffer can be 1600。

 and we should have enough room。And we need to have an eye pointer， let's call this。え。嗯。I p。Get。I p。

Like this。嗯。And we also need to have one for the raw IP packet， I guess。😔，嗯。Yeah， let's do that。So。

I'm not sure what I call it is it raw I P or。Yeah， I guess。So this is no， let me double check that。

Stuck struck S Ro I P。 O， I never made。Giveate the type from it， so。Let's say， we have it struck。

The raw I， and we can call this。B like this。嗯。And we need to check that。 We have。Otherwise。

 we can read。0 like this。 to indicate an error。Okay， so now we want to receive this packet。

By the way， let's zero out our buffer。So， this is going to be。The address of both。And。Size。

And we also need to take care of return value。 So let's say we have signed。

The red is going to be equal to。Receive。From is the function we。你对。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_14.png)

I'm not entirely sure about it。Parameter， so let's check。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_16.png)

啊。So the FD buff。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_18.png)

Size， let's start there。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_20.png)

The FD is going to be this S。AndThe buffer。Did it show a specific data type for it。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_22.png)

Vid。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_24.png)

Maybe we should kiss。Anyway。So， let's say。Let's do this。Let's not。

 Let's try this first and see what it says。And let's say，1599 as size。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_26.png)

And what else is there？We have。Flus。And source address。

 And this we don't need because we get all of this from the packet address。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_28.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_29.png)

Maybe we need some flags。 We'll see about that。Otherwise，0。0，0， I guess。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_31.png)

What is the return value。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_33.png)

Number of bytes received， or-1。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_35.png)

There。So。😔，Let's see here。嗯。Maybe we should have some。Counter something。Let's say this is the。So。

 we can。So we can calculate the size of the payload。 I don't think that will be specified。嗯。

Maybey it will， though。So， if。Its less than 0。Return anarrow。Otherwise， we can set。E to。Thank you。

So now we have the size of the entire thing。And the raw I P packet is going to be this payload。

 so we can set our。Bad pointer。Equal to a。🎼Raw IP star。Oh。嗯。Add of the buffer， I guess。

And if we want to create one of the these。IPA structures that we have or that we want to have。

This one。I think we have a constructor for the art。Yes， make I P。Let's check。Need。エッピ？

We need the kind。嗯。We need the source and destination addresses。We need an I D。Id。 What's that I D。

嗯嗯嗯嗯。Okay， so that's。A global thing。 We have a counter， which we increase。

Do we put that inside of the。Pack it somewhere。But we put it here。😔，嗯嗯。嗯嗯。

What about when we evaluate this thing？Do we propagate that I D somewhere。Yeah。

 we set it inside here， k。😔，Okay， but then we can easily extract it， that's no problem。

And what was last。嗯。嗯。Okay， so although we specify。A specific I。Or。

We give it a pointer to this global thing， right。嗯。Let's see how we did it here。

It was a little while ago I made this thing。So let's see。 okay， we'll give it a random。Value here。😔。

But we can set this to zero。😔，It use this that and that is what we want to this case， right？Yeah。

 it is。Okay。So let's try to create this thing。嗯。Maybe we can。

Create variables to make this a little bit more explicit。So， let's say we have an in。8。So。

Destination。And。69。Now we need to have a kind as well。What is a kind， really。Is it this thing。Yeah。

 it's a type。So。Alright， we need to extract what kind of packet it is， right。Good left。太。

With the name。Likeで。And that's probably all we need， right？😔。

And we have access to the raw packet here， so let's start by extracting this ID field。😔。

So I D is going to be equal to， and we need to。The Indian， this thing。

And it's going to be the raw eye be back yet。Id， right。That is our I D。Easy as pizza。嗯。

And our source。See。It's going to be equal to。 We need to make this a string。

 So we're going to call the virtue this to doctor it。

Which takes an IP address as an integer in network by order。

And it reverses it and makes us string out of it。So we need to provide the raw packet， and then the。

source field， I guess it's called。 Let's see。嗯嗯。Yes， sources。And we had the I。And we have the dust。

And we need to do the check some calculation as well， right。嗯。We call the no。friend。

When we call the checkum function。我。Do we give it。So in this case， we have。Eval I。

So we give it the red and the length。😔，Little Indian。嗯。Where do we get the red from。R is equal to P。

 P is equal to。Okay， yeah， okay。 So this is the packet that the string。

Containing the packet that we are dealing with。嗯。What about the length in the alien。

So if we have a payload。It takes the。The header sized。And it adds the payload size。And。

The IP headers， okay。So it's all of these。Let's also create。して。3。Alright， so I D， we have source。

 and we want to。N should。Yeah。Nation right here。And I guess the check some can just be calculated by。

Calling the check some function。On our。Theer。What's the first argument to check some。

An inate star and then aside。 so we can give it the buff。The size。We can give it and。

Which was returned because we want to calculate it based on the entire thing。Does， but if it is a。

If the size is not divisible by2。Then we're in trouble。 I don't remember if the checkum。

Check it for that。No， it does not take that into account。😔。

I know that we have checked in other cases， so it still works， but。In this case， we need to do。

A check， as well。So， let's see。The size。Dvisible by two。ItRather。知。If it's not divisable by two。

We want to increase。It won't be a problem since we have。One extra bite here。Plus。

 we have zero it out。So this will be a 0 in that case， and the checksum will。Check out。Allright。

 and then we want to compare this thing。So。Let's also have a check on prime。

Whether to check some prime is equal to the raw I。To the Indian。Steel of the。Raw IP packet。

And then we w to compare these two。All right， welcome back you guys。

So now that we have the check sum in the correct format。We can compare the two。So， let's see if。

This applied。The calculated checks is equal to。嗯。嗯。😊。

But we need to calculate the checks some without。Let me see。Right， what we want to do。うんふん。

Is not comparing the two。So let's remove this one。What we w to do is check if the supplied。你。

Our calculation of the check sum， if that is equal to0 X， F F， F F。Then we know it's right。

So if it's not equal to that。Yeah。In that case。是。Print some error message。Something like received。

Okay。M form。行。And then we can provide that check sum。So，0 x。Person。不你。We'll get it in four decimals。

Or four digits。And then we provide the integer of。ject。Brother。The integer of。The raw pas。唔清。

Let's also return an error。Ex。Otherwise， it's okay。 And now we have all the different parts。

 so we should be able to create an eye packet。By calling， make I P。And， let's see。By the way。

What was the first argument。メ？The kind。 That's right。And we have the source destination Id and this。

😔，The kind is。One of these enums。Echo， echo reply。No， it's one of these。

 So if the packet contains an ICMP， a TCP or a UDP。Pilload。😔，Let's see which one is it。Mmhm。This one。

 the protocol。So if that is equal to。ICP。Then， we can。Deeduce the enum。So how did we do that？😔。

If we go to the。Make a P function here。嗯。Where do is that the kind。Okay。

 we'll just take it like this。So let's see， where do we use make P。 So here we say L 4 ICMP。O。

And when we。Evaluate。P， how do we do with this。Protocol field。 I will set it to one if it's L4 I。

 okay。Let's do the same here。🤧。嗯。That's the kind equal to。If the row up packet。

And its protocol field is equal to one。In that case， we set this to L 4。P。Otherwise， we said it to。

What do you call it？Unassigned with a small。So， and now we can create this thing。

 So we give it the kind。We give it the source。Destination。你 idea。And a0。

If we don't get an I packet back。We can return。Aro。But we don't need to do that。

We can propagate the error。 So we just return the I peak。Kinli。嗯。What about the payload。

Source destination， I D and this。Where do you have the payload。😔，Packet payload。Is 0。嗯。

Do the payload。Because here we create the I packet。Okay， then we set the pay load。Afterwards。

 all right。And what is the type of the payload？An ICM。綺麗。😔，To do something like。This we。

 I guess one should make a copy of。Of the payload。So。Maybe we should do something like。

Something like this。And。If the kind is not equal to。Of。L 4 IC P。Then we can say something like him。呃。

So。Or。系。And then we can specify the protocol specifically。So we can do that as。

For did you text the dustimal left before。And this time， we take the I。肥了吗？An error。

 because this is the only thing we support at this point。Otherwise。

 we need to make a copy of the payload。 And in order to do that， we need to calculate。Size。And。

 basically。The size。Of the payload is going to be this an。Minus the size of the header。

So maybe we can do something like。Let's do this。N is。Mus equal。The size of。true。Raw I。

And if this is serial， so there is no payload。Then we can be explicit about that。

And say that the I P pack give。Payload。Is。I think。0。And then， we return。But if we have a payload。

 we need to make a copy of that， right。And that needs to be this。I simply structure。

So we need to extract that as well。😔，Let's create is。R。IC p。We can call this。Or。阿片。

And we also need to have a regularizing。So， iPad。So we need to start with a raw packet。So that。嗯。

What do I call。O尔SNP。So the R， I think P。It's going to be equal to。Well， let's just set it to。ICP。

And we'll take。Letzi。Will take the address of the buffer。Plus。Size of。不。えピ？

Then we should be at the right position。And now we need to do basically the same as we did here。

For the I think。So we need to extract the kind。嗯。The size and the date。So， let's say that we have a。

In 16。ICMP size。嗯。TypeI think病。And let's say that。 we have。嗯。Say that we have a。ラキ？平ing。

Which is a paper。And that is the payload。Of this I P。 So basically this stuff right here。And the day。

 the field。Da the field we need to allocate。So let's say in。A lot of moving parts， e。

We also need to check some for this thing。So， let's say that we have an。16。i是 p。😔，All right。

 so let's try to extract those different things。And let's start with the tie。And the code。So。The R。台。

Is equal to。诶。RICP。Cold is 0。In that case， we have an echo packet。Don because it I think it kind。

Equal to。一个。Lets doubleub check the。Yes echo and echo reply。Otherwise。They are。CRICP。Type is 0。D RSP。

So also0。I think these are the right ones， but let's double check。The echo is 8，0。 E apply 0，0。

And in all other cases， I seem be kind。toあ呢。All right。So， that is the。Td thing。And the size。

The size we need to calculate。😔，So currently， what is n equal to n is equal to the entire。

Layer4 pack kit。So， we need to remove the。We need to remove the ICMP header from it， as well。

But maybe we can wait a little bit with that。If we check the make ICMP function， it all。 okay。

 it takes both the kind， the data and the size。And the size is just the size of the payload。Okay。

Let's do this then。怎色。うんまいに。Qual size of。若。嗯。We don't have anything。Ping板。😔，The lose that pink。0 of。

De castted us。其实。Otherwise， we need to allocate。For this thing。In that case， it's going。いくト。No。あの。

But before all left， we also need to check。Unassigned。So， if our I think big。なさ。

We need to mention that this is the wrong kind of tire package。P。And then we can print the tie。Yeah。

And the code。Soly。嗯。阿尔安。P。然后。C we can return error， I guess。Otherwise， we check for these。😔，Here。

You can。Oh。うかップ？Into。Inけ。Then we want to copy it from the R ICMP。That's the name， right。Yes。

We we want to copy your and bytes。So now we have a copy of this。Plow right here。嗯。

So now we can take the I packet。Andcer。😔，Hello。嗯嗯。This is a payload of the ICMP packet。Mmhm。

We still need to have。Still need a other raw S MP packet header as well， right。Or maybe not。

It's enough to have this thing。That's right。 We can create this with our。Constructor function， now。

So。😔，Sway with this thing。And let's set to what you recall call the。Poiner。😔，嗯。

Don't we have an ICMP and now。这个谁。😔，I this should be I。No。😔，Maybe I should have a different name。

ICMP。And the I packet is I。 Ok， now I see。So the IMP packet is going to be equal to make。P。

And we take our I CMP kind。We take our。Ping packet。Okay， this is an in8， and this is the。Back in。

And the sizes。We don't get enough。Heed back is。不能。Let's just return the eye feedback。

Without the payload in that case。Otherwise， we can set the I packets。Heload。Do our。可可。

And I think that's all we need in order to receive an IP packet。Because now we have it in this form。

The payload points to a structure of this form。The date the points to either this pink packet。

Or it's empty。Think this。Should do it。嗯。So how can we test this。Well， we have a main where we。

Send a packet。So let's create an I structure for the received packet。It's called it。来。

And after we have sent this thing。Actually clean。as well。Then we can set our reply equal to。

Receive I。That we provide our。Yes。Don't have a reply。Print thearrow。So么。Otherwise， we can do show。

Reply。And then， we can free。嗯。We should also free the day direct。So， let's check。If we have。He。They。

3ree。This is called payload。It would have a reply。能。And then we can free the actual reply。And went。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_37.png)

All right， a lot of moving parts。 Something tells me that we're going to need。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_39.png)

Some troubleshooting right there。<|OTHER|>Argument one of zero incompat pointer tie 25。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_41.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_42.png)

で。Like。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_44.png)

Expected expression before。I听。The work。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_46.png)

Okay， so IP P is not the name of this thing。你别他。几。The raw， it should be。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_48.png)

Statement with no effect。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_50.png)

Okay。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_52.png)

So if this is a。And this is 0。Or。This is 0。And。This is Sarah。

How can that be a statement of no effect。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_54.png)

Oh， should be else。プラ？

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_56.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_57.png)

Expect expression 78。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_59.png)

Ping back嘅。That's right。 this。You人。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_61.png)

Conversion to non scaler type requested 78。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_63.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_64.png)

本对。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_66.png)

0 makes point from in theger。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_68.png)

82。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_70.png)

Do zero the pink back。Oh， this should be。The same here。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_72.png)

Unused variable， right， We forgot about this one。Data is in size。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_74.png)

So that， I guess we。Move IP size。As well。嗯。What about to check some。

We should actually do the check some check。On the I and paper kit， as well。Lets do it。So。

 the ICM see sum。s equalqu to。Check some。哦。Well， it's the roar。 I simply pack yet。And we need。

like this。But what about the size。Well， we haven't deducted the。Haers yet。

So I guess we can just propagate down here。And what if it's not a multiple of two。😔，Let's do this。

Guess I don't when I copy this stuff。From all different directions。So， if。你爱 c p。

Check sum is not equal to 0 x。嗯。L。AndHere we can give the raw as in pay。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_76.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_77.png)

Aray subscript，8000 it。Outside。B。At offset 32000。In the吧。嗯。That can't be right。Allrry。

 I think P time。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_79.png)

Because the R I&P is a raw ICP packet。Which we have right here。And it doesn't seem to be。B。

So it's a struck。S raw I andP。You take the bath。The address of the buffer。And we add。The size。

Otherwise， I see otherwise， I。Well， that's right， too， and that should only be 20 bys。嗯。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_81.png)

What if we were to remove this。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_83.png)

It compiled all the errors。Disappeared。Coollyo。 alright， let's。Test this out。

Received packet with mail form check some，90，25。你穿你看。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_85.png)

Let's。Don't do the check some for now。Or at least， temporarily。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_87.png)

This。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_89.png)

And now， the other checkum fails。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_91.png)

Okay， let's see what happened。Okay， something happened。袜袜。Okay。

 so here we sent the packet and this is what we received。😔，32 by， kind 3。Id。81。

Source and destination。Well， the destination is correct。Soce， not so much。

And the payload kind echo reply。 That is correct。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_93.png)

But why do we have the same here。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_95.png)

See。😔，The source is equal to the raw。Source， the destination， the raw destination。

And where do we call the constructor。Here， source destination。That's weird。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_97.png)

It's rare that some of it seems to be okay， like that。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_99.png)

Destination is the correct IP P address。But the kind。Its type 3。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_101.png)

Where does that even come from。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_103.png)

Kind。😔，Maybe that's correct， though。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_105.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_106.png)

What does it say when you send the。First拍。Kind 3。 Okay， so that's right。

And there's 8 bys of payload on the。Ping packet。And there's 8 bys of payload on the received packet。

So that all seems right。 Everything seems pretty much right besides the source IP address。

Why is that。The same as the destination。Prety weird。😔，嗯。Well， at least we are closing in， right。

 we are pretty close to getting this to work， as you can see。Only some small details。😔。

Left to figure out。Which we'll do after the break。 So see in a bit。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_108.png)

All right， you guys， welcome back。I think I have might have。Figure this out。

Both the checksum and this。problemble that we have。The source。And destination。 So let's do like this。

 Let we practice this。that。And。We are comparing the checkum to this F F FF。

And if we go to the check some function。That is generally the way to do it。

 to compare it to those Fs。 But usually you have one checkum function。

For creating a checkum and another one for verifying it。Because when you verify。

 you don't do this inverse operation here。So basically， at this point in the code， I think。

The result is FF， FF。But when we do this， we flip all the wbits to zeroes。

Which means that the result is going to be 0。And。So that is what we should check for， not the FFFF。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_110.png)

So I have put back both of these。Check sums。 Let's just verify that it。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_112.png)

Doesn't work。Right， so this is to check some。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_114.png)

So let's see what happens。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_116.png)

If we。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_118.png)

mm，mm。嗯。Let's see。Re packet with mail phone check。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_120.png)

Right， so it's the IP packet。That it complains about now。 So instead of this line right here。

 we should have an if statement which just checks if sees some， is。え0。Like this。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_122.png)

So if we do this instead， what happens then？

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_124.png)

Is it still the same or is it other one now。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_126.png)

Ci。😔，No， this says ICMP， annoying， I thought I had figured it all out。But let's add one thing here。

 We are currently only check printing the check some from the IP packet。

 It would be interesting to print Wait a second。If it's。0。We give an error。 I， I meant the opposite。

 of course，0 means that it's okay。So this is how we should do。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_128.png)

I'm glad I didn't change anything else， because I thought it didn。Nice。

So now it fails at the ICMP instead。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_130.png)

And now we can just do the same there。So instead of this right here， we just check that ICM P。たさ。

Is positive。And now， it should all just work。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_132.png)

And it does correct in nice。 alright。 So let's dig into this problem right here。

 And I think I have the solution to that that as well。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_134.png)

Because I wrote this two dotted function quite a long time ago。

 but I suspect that this does not use Malo to allocate the pointer it returns here。So。Basically。

 both of these function callss refer to the same distance to the same。Place in memories， so to speak。

So when we do this， we overwride the first result。So what we should do instead is don't declare these as pointers。

 But let's say we have a source with size 16， and we have a destination。Of size 16。And y 16。

 Because if we have an I P address at the maximum length。With the three。Digits。P。え。Per groo。

Or peroct。So then we have three times4。Which is 12。 And we have 1，2，3 dots， which makes it 15。

 And then we want to have then。no terminator at the end。 So 16 is perfect。Alright， so let's see here。

Before we do this right here， let's zero out our。Source。And the size is 16。

And let's do the same with the destination。And instead of just doing it like this。Now， we can。え。

Let's do one more step， by the way。Let's create a。L。For the length of the string。

And maybe we should have a point to。Call this T for temporary。

So let's say we we set this TM P equal to to Doton， and then we provide the rawar。source。

Then we calculate the length of the string。So， we set our land equal to。Bring long。Of the。

Character encoded。I don't know。Silian death， I think。So， we can just provide。TMP like this。

So now we have the length。 So now we can do a memory copy。So we copy into our source variable。

We copy from our。Our Tmp。And we can copy 1 bytes。And since this is not a string copy。

 This is a memory copy。 So it does not add an alterinator， however。

We have already zeroed out the whole thing。 so it will have an old terminator。

And when we have done all of this。We do the same once again。

 but this time we take the destination here。D stillill the。And then we copy into the destination。

So now we can remove these two lines and we can treat those string arrays as。We have done with the。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_136.png)

Poiners before。Because they will fall。What's the word for it， They will。Degenerate into pointers。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_138.png)

そレ' see。So。Do that so。It was a lot of errors， a lot of errors。 maybe we should not define it twice。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_140.png)

So， let me see。 yes， this。九。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_142.png)

It should be go。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_144.png)

Alright， we need to have a string length function。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_146.png)

Let's write one。It's quite simple。So。Let's say we have a in 16。

And it takes it into a star as an argument。Let's go up here。6ス？这。It takes an in star。

 which is the source， let's say。We need to heaven。We need have a pointer。嗯。

We need to keep track of the length。 So let's say we have an in 16。

We have four loops at m to0 with at P to source。And。We're gonna loop as long as P is not。

The old terminator。And at each it， we're going to increase both N。And that's it。

Then at the end of the loop， this。And will contain the length。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_148.png)

上次了。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_150.png)

Comp。And when you look at that。 now we have the correct source。 This is my other server。

 the one we are pinging and。It has this IP address as the source。

 because this is a packet that we are receiving after we have sent ours。

And the destinationation is this machine。So it all looks good， right， The check some checks out。

 everything is。F嫩的的。I want to change the show function a little bit， though。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_152.png)

Because we do not show the details of the。Ping pack。 So let's say， let's see， show I Z P。嗯。

So we are printing it as hecks。 we don't need to do that。But if we have data and one more condition。

If we have data。And。The packet。Kin。Is equal to。Let's see here。Is it equal to echo or echo apply。

Maybe we can do this。If。So。一。We have data。Then we do a if statement where we check。The packet kind。

Equal to。Go。Or。The packet time。Is equal to equal with。In that case。

 we have a pink packet and we want to print out some extra details from that body is out to be this stuff that we have right here。

Okay， so let's see。 we need to define a pointer for that。So it'll be struck as pink。

Let's call this P P pointer。So we set the pin point or equal to。嗯。It can be packed day。嗯。

That day is an array。So， I guess we should take。As like this。诶。All right。So now we should be able to。

Print the I D and the C from that pack。So let's say we have an Id。嗯。It like this。

To see we have this and then a tab and then this。 and then a new。 And okay， let's follow the same。我门。

This will be a new line。And then。Two spaces and。Provide the sea。Okay， so。We need to。

 these are 16 bit values， so we need to take care of the endion。

And what we're going to provide is the pin pointer。And it's I。And we' are gonna run the end， and on。

啲。四。そでま。Something like this。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_154.png)

Its that。All right， the idea is this。And the sick is this， and it should vary。我 it does。Nice。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_156.png)

Very nice。 Very， very nice。 How do we decide the seek， though， I don't remember how we。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_158.png)

电子啊。Let's see。 Where do we create。The pink bag。Here we calculate the size of it， at least。You we买咯。

We that the idea， O， to 5000。It was at6 to one。嗯。That's a little bit weird。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_160.png)

How can we get so large numbers back。What is。TCPWC。I D 500061， I D 500061。Okay。

 so it sounds the right thing。 We are printing it wrong， though， So perhaps we shouldn't。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_162.png)

Do this。嗯。This endness。Maybe it's。Already being done somewhere else。这乐子修。So I。

So let's not do this And。But we take this idea as face value， but we need to cast this into inte。

Maybe that has。That might be it actually that we are not treating it as an uns signign。

 but let's see what it says。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_164.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_165.png)

I think I was right here。 Let's sip put back this。 And then the thing is。But， let's test。

Let's test this。Like this。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_167.png)

H。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_169.png)

Maybe we need to。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_171.png)

It's man。So let's say this is an unsign。嗯。A regulargular on。We can try that。down and we do。Heres。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_173.png)

Because it's， it is obviously the correct value。 We just need to present it in the correct。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_175.png)

うん。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_177.png)

玫背V儿。😔，Getting the wrong data when we point this thing like we do now。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_179.png)

That might be it。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_181.png)

Let's see exactly what we have here。😔，8 bys of payload。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_183.png)

If we look at this8 bite， So this is。To by。We are now， I see。

 We are pointing it to this data is that。What did I do here。诶是。

The ping pointer equal to the packet kit date。 and what is packet kit。Well， let's say IP packet yet。

It's this one。And this has a date。 But this is a pointer。 This is not an array。 O， kiddo。Now。

 it's starting to make sun。So。All right。Did I leave this now。I'm sorry。Think this is right now。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_185.png)

There we go。So the ID is 5000 and the C is one for the first pack。Splendid。

So now we can successfully send IP ICMP packets， we can receive them， we can interpret the results。

Even to check some calculations。Check out。So that's nice。 So the next step is。Well。

 it's adding some additional things so we can， for instance。

Type on the command line what we want to ping。 And we also need to show。

Show it a little bit better than than this rat。So。We we'll do all of that after the break。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_187.png)

All right， welcome back to you guys。So currently we are doing a lot of the heavy lifting inside of our main function。

And we still。Are gonna do some of it there， but。I want to break out the things that has to do with sending an actual ping to its own function。

So， let's see here。All of this。えジで？What do I do now。So let's see it's pretty much all of this。

All the way down here。So we'll break this out and lets。Let's just put it here。And let's say。

 we have a new function。Which is called。不。or something。And what do we need？We need to have。No。

We need to have the addresses， right？So。Let's say， we have an。In 32。嗯。Source。整理中。In 32 destination。嗯。

The ID number， I mean， the yeah， the ID number。We need to， also。Provide。How do we do it here。

 We created a random。So， let's say with heaven。How big is it in 16， right？

So we have the the I D have。S number。And I guess that's all we need。We do also need。

All of these variables， almost。This one。Re。I here。Let's just temporarily do something like this。那个不嘞。

I want to try this out so I know that it still works。So I'll set the red equal to our new function。点。

What's their IP addresses？These， right。So the source is going to be the ion。Addre。Oh。Strering。😔。

Or actually， it takes the。嗯。It actually takes the strings as in， but so let's do it like that。😔，Star。

うじ。Then we don't do the I address stuff。We were just。谁？Something like this。嗯。5。S it to。ンだトンドトラセ。

Let's say， the I D is 500。And the sick is。Thous。Print。オッケー。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_189.png)

四つな？

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_191.png)

Inlic duration。Forgot to add the new function here。We are having a pool。平你。And the intake star。

 another intake。The二。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_193.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_194.png)

嗯。R And D， we don't have right。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_196.png)

So this R And D right here is actually the。The idea。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_198.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_199.png)

嗯 응 응。Makes。Pointer from into the right。 It should be a pointer here。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_201.png)

So。Maybe we can do。Let's taste。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_203.png)

Main is normally a nont function。嗯。ok。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_205.png)

嗯 maybe we should this。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_207.png)

Very good。Alright， let's try this out。And we get an okay back。 That's good。The idea is 5006 is one。

 though， so we don't control that。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_209.png)

Where does the seal come from。I never seem to figure that out。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_211.png)

We are。Creating the body right here， okay。That makes sense。Here， we should provide。And here。

 we should provide。え地。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_213.png)

All right， now it works。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_215.png)

That's good。 Now that we have this function， which does all the heavy lifting for us。

We can just deal with the command line arguments and stuff like that。So let's say we have an in8。

For the。Destination， and I'm not sure if we need to specify。A real source。

 I think we can just give all zeros， and it will figure it out automatically。

So I think that's what I'll do， so we don't have to worry about figuring out our own IP address。

Which can be a little bit difficult at times。Okay， so let's check if our sea is less。2。

And will say something like you search。fi name of。Program。嗯。And return went as well。Otherwise。

 we will set。内。2。啊。Well care。但是你。Okay， so now we know the destination。

We also need to keep track of the sequence numbers。So let's say we have an in。一。See。succeed。2，1。

So we can do that in the loop。So。🎼フとは。Gna loop as long as seek is less than。1，2，3，4，5， less 6。诶。

Inquiし。Let's add some。ー。And I want to mo this after。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_217.png)

How Cisco does this stuff。 So let's log into。Thisく。P。Something。嗯。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_219.png)

C this right here。Tpe escape sequence to the board。And changed this to。Control。嗯。人么太笨。你不能。

It's not going to be hundred by。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_221.png)

LetsSee how big they were。I guess they are counting this right here。So，8 buts。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_223.png)

Need to replace。Add。Timeout is 2 seconds。 sure why not。And we will provide。S version of。N。Alright。

 that's good enough。And then， in the Lou。What we are going to do is we will set our。こ。Turn variable。

Equal to。平。We are going to provide。Let's try the old zeros。 I think that will work。

And the other one is our destination。Our I D。Is。啲。How did you do this。R and D is an N 16。Well。

Just do this stuff。And here we the third see。By the way， this is a variable declarationation。

 so let's。Please。And now we have two different。possibilities。Either。Rt is。Positive。

 which means these were successful。In that case。诶。An exclamation point。That means it was okay。

Otherwise。I gone。えと。And we want to flush this。😔，And see it on the screen。Immediately。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_225.png)

And afterwards， we would actually like to print something like this。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_227.png)

Maybe we can。For the first version， we can make it a little bit simpler。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_229.png)

Let's see。 success rate is。Some percent。 And we have this。Round trip。I don't want to have round trip。

Calculations at this point。We'll do it in the later version， though。So， this is fine。Okay。

 so we need to calculate the percent and we need to know how many we send and how many we received。😔。

So。See here。You can have it in the。Sound we don't have to worry about any decimals。And。

We need to count how many were successful。So when we run this low。Initialize。0。Is successful。

We can increase that。😔，And the percent can easily be calculated by taking。うさ。Equal to。The。Succes。

Divided by。Let's see divided by。See。And then we want to times this by 10。So， we get the right。Ding。

Maybe we can do something like。I don't know if it is possible， but it should be。So， we say that this。

Expression is a double， temporarily。We convert success to double。看的。Seek to a double。 We divide them。

And this is too it double。Then we times it by 100。 and when we have it in there。8%。We can go back to。

I'm not sure if this works， but I I don't see why it shouldn't。Alright。

 so now we can give the argument here。The first one is the percent。Second one is。The。是。

And the third is。Like so。Yeah。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_231.png)

Let see what it says。Compiled without anything。That's pretty nice。Okay， so we give this the。

ロッワンド twoロ6。嗯。Only run。嗯嗯。Or maybe it didn't success rate 83%。 It seems that our double。Stuff worked。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_233.png)

But we did the wrong calculations a little bit， at least。Because C equal will be six when this loop。

😔，Ens。So， let's。Minus minus this。First。And there' is a lot of noise from the other functions。I of。

Okay inside the show functions， that'ss it。The calls to show。Okay， this we don't need。Let's remove。

And the。St。And this， we don't get to print。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_235.png)

I think that's it。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_237.png)

500。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_239.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_240.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_241.png)

Kin。It's sack， but not。Used5。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_243.png)

3。So， it's here。Let's put this。And let's only print something， if it fails。Or no。

 we don't want to do that either， actually。However， if it fails。We want to return an error。

Maybe we can。I allocate this。AndFs。Something like this。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_245.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_246.png)

It still burns all this。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_248.png)

Where else do we have。可对で。engngsh。😔，This is inside of another show function。Shall reply。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_250.png)

Let's。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_252.png)

Almost。Perfect， we need to add a new line as well。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_254.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_255.png)

Is there any additional nu as we need。 No， theres no here。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_257.png)

Let's see。嗯。Well， we can add it。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_259.png)

Look at that00%。By the way， what happens if we try to ping something which is not gonna respond。嗯。嗯。

That's a little bit disappointing。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_261.png)

Pretty weird， that。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_263.png)

So where do I have this reply thing。Let's put this back， show。来。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_265.png)

Lets say what we get。Okay， so these other packets that we get back。嗯。嗯。😊，This is not the I P。

 I tried to pay。Where does it get get this from。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_267.png)

Oh， did I change this。没。This should， obviously， be。Okay， maybe this does work after all。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_269.png)

Let's start with something that does respond。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_271.png)

Let's remove。😔，Those。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_273.png)

So this should be able to respond。And it does。This should not respond。Okay。Now， we're talking。

Receive I P return error。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_275.png)

We should not print that， actually。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_277.png)

Rely。😔，哦。普通。This is。A more serious errors。 So here we can actually print it。嗯。Here we should both。

False。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_279.png)

Alright， let's try it。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_281.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_282.png)

Page receipt。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_284.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_285.png)

嗯嗯。嗯う。If we receive an unknown packet， we wan a。We want to recurse。Because we wonder。

Check for the next。Packet in that case。So let's just。テはい。You that word best。Do not。😔，St。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_287.png)

Okay， let's see what happens。As I suspected， the timeout。Is very。B。mm。Very， very big。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_289.png)

So how do we change that？There's probably some socket option。嗯。个。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_291.png)

Receive timeill S O send time Socket options is a timeout for any socket operations。😔，That's nice。看ま。

That's really cool。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_293.png)

Okay， so。We can do that in our setup function。So， let's set our。Wasuss cold。Yes。It's called Se。

So there are a number of seconds， let's say we have a constant dealing with that。

So let's say we call it T mount like this。The microse。Se to 0。So。Let's see。 first。

 we initialized the socket。 Then we say。This。Soet option。

We don't actually need to import everything just because this fails。So， let's remove。No， we can。😔。

But we don't need。Do this or。So now we can just do all three circuitcket options。

So what was the other one。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_295.png)

Receive。Time out。And send。睇。And these we called TV set。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_297.png)

い。Okay， I think。So， this is this。This sense。発 songアイピーバ song。And we need to provide our argument。你呢。

应。And we called them。So。嗯。Mo is called TV。テビ？

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_299.png)

I think it was。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_301.png)

遅け。Do this。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_303.png)

嗯。I think I got it wrong。N， I don't want a copy paste more than I really have to。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_305.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_306.png)

We need to define that constant， though。So。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_308.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_309.png)

Once。あてい。Oh， that's right。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_311.png)

Accidentally。Remove that part， as well。This should be。32，1。等会。This should be the size of。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_313.png)

Alright， let's see what it says。Now it times out after two seconds， isnsn't that great？

Success rate is 0。And if we p our built 6。嗯唔会唔畏。🎼因为。Why would that stop working。😔。

Is this still responsive。で、す。Why does that fail。What if we were to do？嗯有。To this。Fer。Proractical。

 not available。The call， not available。If we run the regular thing the same。我喺度。修身。😔，嗯哼。😊，So。

Here we have So IP， oh， I changed all of them。😔。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_315.png)

嗯。This is。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_317.png)

HeSo like him。Maybe it still works， after all。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_319.png)

Fingers crossed。All right， let's start by p。Thinking the thing that does not work。

E does not they respond。Alright， that seems to be working like before。

And what about the thing that should respond。Would you look at that ladies and gentlemen， It works。

 It all works。 Every little thing works。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_321.png)

Isn't it beautiful， beautiful。So let me just add one little tea you anything。And timeout is。です。

Second。And then， we can provide the。

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_323.png)

Should change anything。But。It's better this way。 Now， we can actually modify the。

They head of file if we want to increase or decrease the timeout。All right， you guys。

 we have successfully created Ping from scratch。And we have made it in a nice enough way that we can turn this into a library and use it to deal with all kinds of IP operations。

 maybe at Ethernet and R and stuff like that。But I hope you have liked this entire series and especially this episode。

 which I think is one of my better ones actually， I hope you do too。

 and that you want to like and subscribe and hype the new feature don't forget to hyp。

And please tell me what you about what you thought of the new intro。Or the intro sequence。诶。

Tell in the comments below。Thanks for watching you guys。 And thanks for the。



![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_325.png)

![](img/a43ce7f9cab56ff018c7ab10c2b04ae1_326.png)