# 超硬核手把手coding使用rust实现TCP协议-p03-P03-Implementing-TCP-in-Rust-(part-3)--BV1dLQLYzEui_p3-

Hello everyone， welcome back。 It's been a little while since last time， hopefully。

Hopefully you haven't all been longing for this for so long that you're now desperate for some more just before we dive back into where we were first there was a interview with me on the co-recursive podcast about my research about Rust about doing live streams and a bunch of other sort of things related to what I do so if you want to give that Alyssa and I highly recommend it it was a lot of fun to do I will also be at Ruscon this year later in August so if you are at Ruskf and you enjoy these videos and feel free to stop by and talk to me even if you don't enjoy the videos you should still feel free to stop by and talk to me。



![](img/49347db1b6244c3ae42b589040f18ec5_1.png)

We're going to continue this time with the TCP stream we've been doing for the past two streams。

 we might not finish all of TCP because it's a pretty large protocol。

 but I think well at least have gone through the interesting design challenges that we had and I want to make sure that we switch up what topics we talk about and so I don't want to do more than three on TCP because this is not going to be a final usable stack in the end regardless。

 of course if someone wants to take it further they should feel free to。

 but I think we're going to switch to another topic after this stream。



![](img/49347db1b6244c3ae42b589040f18ec5_3.png)

And when it comes to another stream， you may or may not remember that there's a page that is essentially a way where you can vote for what stream topic we're going to do next。

 I know that the last time a bunch of people voted。

 some of these options were not here and so I recommend that you log into the site you just go to this URL I can put it in the chat too give me a second。

There we go I've also put it in the video description if you're not watching live and here the idea is that you can vote on what streams you would like to see。

 you can also put them in order and it will basically run a ranked choice voting algorithm to figure out what people overall prefer Currently it looks like the next stream will do is a second open source contribution stream which will be really fun but there are lots of other interesting ideas here that it would be interesting to hear your input on and sort of discuss what it is that you want to see if you have other ideas that aren't listed here then feel free to reach out to me on Twitter or email or some other way and I'll consider adding them into the list。

All right， with that all said， I think it's time to continue with TCP。

It's been a while since last time， so let's do a little bit of a recap of where we are both for your sake and for my sake。

 of sort of where the implementation is at and what we were thinking of doing next。



![](img/49347db1b6244c3ae42b589040f18ec5_5.png)

Post a link to the interview too。 Yes， I can。 I'll put that in the show description， as well。

Here we go。Twiitch Twitch chat can't see YouTube chat if that's supposed to work。

 That is supposed to work。 But there is something weird about Restream and chat sync。

 I think they're preparing an update。 So hopefully they'll fix it for next time。

 but it's something that I sadly can't do much about。Right， so let's recap where we were。

 We have this Ru TCP library that we've been building and。



![](img/49347db1b6244c3ae42b589040f18ec5_7.png)

If you remember， it basically sets up a sort of artificial network link using ton tapap drivers in Linux。

 if you go back and watch the very first stream， you remember that we sort of use this Linux mechanism to give us a way to essentially write our own networking stack on top of just IP and we've written。

 essentially if you look here， we have source lib which implements both the stuff needed to handle packets and send packets。

 so this is this packet loop business that just handles all the incoming packets and decides how they affect the underlying TCP streams that we are maintaining。

So we have an interface which is just a network interface。

 you can create a new one that's going to create a new to tap link。

 you can bind to get a TCP listener just like a standard net TCP listener and you can also accept to get a new TCP stream and when you have a TCP stream。

 the idea is that you can read and write from that TCP stream。

So these are very similar to the standard types you would find in the standardNe。Currently of course。

 we don't support handling actual data all we do is we open up the connection and then we close the connection again。

 there's no exchange of data that's not something we've added。

 and so that's going to be the main topic for today is we're going to implement the necessary stuff in order to read and write data over TCP rather than just handling connection set up and tear down。

嗯。We also don't have a connect method， I think on interface。

 So currently all you can do is set up a server Ily。

 of course you should be able to connect to a server that's running elsewhere。

 This would be if you want to make an HtP connection or something。

 and so adding a connect method would also be good， I think。嗯So。We have this main dot RRS。

 which is what uses our library and what we use to test it。

 and if you recall from last time it really just like creates an interface。

 binds to a port and then accepts a packet。Reads basically no data from it right。

 so it asserts that it read zero bytes because our connections are always immediately terminated。

 And so this server， if we try to just run one。

![](img/49347db1b6244c3ae42b589040f18ec5_9.png)

So if I run the server， there's now a TCP server running on port 8000 on my machine。 and if I run。

Where is my。I adder。Yeah， so my ton interfaces is the one that's generated by our server when we start it is running at local port this。

It's not even true？I guess we'll find out。 and if I try to connect to it。

 you'll see that the server says it got a packet。Esablished a connection and then in theory it should just be terminating that connection so when I terminate the input here。

 say that I'm going to send no more bytes， then the server prints no more data and the connection is going to be terminated and I can do this again。

I guess let's do this。 So this echo is essentially saying send no bytes。

 So dash n means no new line either。 So this is sending an empty string to the server so the connection should be terminated straight away and you'll see that here indeed the server got another or accepted in another connection established that connection read no bytes from the connection because we didn't send any bytes and then terminated to the connection。

 And so in theory， we could keep doing this and luckily our server does not crash And the interface is。

 as I showed you。Just something that looks very much like what you would use with standardnet。

So the real challenge today is going to be to make read。

 actually be able to read data that the other side sent and for us to be able to do stream dot right in order to write data back to the client right。

 So I should be able to do something like E F。 actually， let's see what happens if we do this。

So if I run this and I try to echo Fo， what happens， Yes。

 so currently it crashes with we assert that data is empty because we don't handle data and so this assertion is something we're going to have to deal with and similarly。

 a similar assertion would fail if we tried to write data on the server side because that's also something we haven't added support for yet。

So that's what's going to be our challenge today is to implement those features。

 So let's take a look at where that happens。So if you remember。

 we've sort of split the library into the source Lib。

 which is the thing that runs the main packet loop。

 the thing that receives packets from the network interface。

It pares out things like the port and whatnot， and ultimately it calls into TCP connection。

So if we switch to the TCP packet， you'll remember that we have this connection struct that contains all the various things that are defined in the TCP RFC。



![](img/49347db1b6244c3ae42b589040f18ec5_11.png)

So remember that we are following RF 793， which is the TCP RFC， and it defines where is it？嗯。

うんうんうんうんう。down here。Further， further， further， further， further。

 closing a connection and where is our diagram？The diagram is further up， isn't it？It defines。

Where are you。Where is the giant TCP state diagram？嗯嗯嗯嗯嗯。Should well。

 so certainly here here defines a bunch of variables。 So we need to keep for the state。

 This is things like the sequence numbers for data we've sent。

 the latest sequence numbers we've received from the other side so that we can acknowledge the sequence numbers or the packets that they send us。

But there's also this diagram which keeps track of all the possible states that the connection can be in right so initially you start in the closed state when you decide to listen for connection。

 you're in the listen state， when you then receive a sin which is essentially a connection request from someone else。

 you then go to this state， etc， and all of these states have various things you need to keep track of such as the current sequence numbers。



![](img/49347db1b6244c3ae42b589040f18ec5_13.png)

And so this is why our connection has a state and the state is seeing basically all of these states map to these states。

We also keep track of the。The sequence number space of the stuff we've sent and stuff we've received and information about the other side。

 and currently we also have this， this is sort of one of the last things that we added in the last stream。

 which is incoming bytes and unact bytes。So incoming is going to be bytes that we have received from the other side。

 but that we haven't returned to our call to like TCP Stream read and unact are things that we have sent to the other side。

 but the other side has not yet said that they have received it。

RightSo the reason we have to keep this around is in case we need to retransmit it。

 we can we can't just like send bytes out of the wire and then just sort of forget about them because it could be that that packet gets dropped and this is。

 of course， what TCP is all about is giving you reliable transmissions。 So if a packet gets dropped。

 you need to resend those bytes so the receiver actually receives them and in the right order and that's what anact is for here。

嗯。And you'll notice there are a bunch of Tu's here that these may or may not be important to us。Yeah。

 so the send sequence space， what we did last time was essentially abstract out all the states that's needed to keep track of how much you've sent and all the states that's necessary to keep track of all the state you've received。

 we might want to add some methods to this to make managing these variables easier。

 but for now I think we can leave it alone。Connection has a bunch of methods that are that basically corresponds to outside events。

 so this would be things like receiving a sin on the network interface。

And you'll see except is the thing that gets called when we receive a packet for a connection we have not yet established right so imagine that a TCP stream or imagine that the network interface is sort of in the listening state on a given port and you receive a packet from a peer that you've never seen before。

 then except would be the thing that gets called so that you can establish that connection so except does the TCP handshake。

And sets up basically all of the initial state that's needed。嗯。So right， I think what is right？

W is just if you want to write a byte out like you want to write out a TCP packet。

 right takes care of that， it sort of sets up all the IP and TCP headers that you need and then sends out that packet。

So we use this to send out things like resets， Acts。

 any kind of package we want to send to the other side goes through right。嗯。

Onpack is the main event handler。 So essentially， our， our。

Our network interface whenever it receives a packet it's going to call this on packet so it basically turns into an event loop and it's going to call on packet on the appropriate connection so remember there can be many connections open at any given point in time So if we remember back to Libbars Libbars keeps track of this this map from Quad which is a local IP import and a remote IP import to a connection so it is going to use the packet headers to determine which connection the packet is for and then it will call on packet on that connection。

And this handles all of the TCP state transitions that we've talked about in past streams。See。Right。

 so here you see is the the assertion that we failed earlier when the other side is sent us data right。

 so this is we are in one of these one of the states where the other side is allowed to send us data。

 but currently we just require that that data is empty， whereas in reality what we should do here is。

Like accept that data and then push it into our or make it available to read calls。嗯。Yeah。Right， and。

 and also currently， we have no mechanism here for dealing with writing out bytes that we want the other end to receive。

 right， So， so that's also something we're gonna have to add。 So if we go back to our lib。

So on TCP streamam， we implement RE which looks up the appropriate connection。

 so remember we take this lock to make sure that we only have one thing operating on a connection at a given time。

And then we check whether this data， this code in theory supports there being data for us to read。

So that's good。Yeah， this basically just looks at the cu of incoming bytes。

 so of bytes that we have received and then reads out as many bytes as it can。And down here。

 we have the， this is the condition variable that we added last time so that if there aren't any bytes to read。

 we have a way to block， right， so our。Our code down here。

 what it's going to have to do is stick bytes into the the incoming byte。The incoming byer array。

 it's a V DQ of U8S， I think， and then it's also going to have to wake up any readers that are waiting to tell them that there's now data for you to read。

A right currently just adds bytes to unact， but of course it's also going to have to wake up。

 it's going to have to do something in order to make our packet processing code actually send out that packet right just adding bytes to this is not sufficient。

I we're going to have to figure out a way to do that。呃。Yeah。

 we're going to have to figure out what to do there too not sure how to do that。All right。Oh。

 and shut down， we'll need shutdown too。Okay， I think what we're going to do is we're going to start by implementing Read because I think we have most of the stuff that's necessary to read and it'll sort of get us into the flow of things。

 and then we'll implement right later because that also requires dealing with wakeups and retransmissions。

So let's see where we're at for reads。 So for reads we already have all the stuff that's necessary to get at the。

To get at the incoming data array， right， all of this is done。 So if there is。

 if there are bytes to read， then we。Copy out the bytes that we can read if you remember from last time the double copy here is because we're using a VDQ right so it has a VDQ is like a ring buffer right so the bytes that you can read might be in two separate locations in memory。

 you should go back and watch the previous stream if you don't remember exactly how that worked。

But this is us reading out as many bytes as we can into the buffer provided by the user and then basically erasing those from the ring buffer so that that space is available for later packets that we received and then we returned the bytes that we actually read and if we ended up not reading any bytes。

 specifically if this is empty， then we block。All right。

 so the thing we really need to support here is this assertion we need to deal with right。

 so this is there's an established connection and data where does data come from here。嗯。

So data here is the body of the TCP packet， which is what's going to contain the data that the other side wanted to send us。

So what do we have to do when this happens well？There are a couple of things that have to happen。

When we receive data， we need to stick it into incoming， right， so that part is easy。 that is just。

What was it called incoming？Incoming dot extend data。So that part is easy enough。

 but now we also need to wake up waiting readers。So if someone tried to read in the past but went into this condition。

 then we need to wake them up。呃。In addition。嗯。We also need to make sure that we。啊。

The bites that we received。So remember in TCP， we always let the other side know that we have received bytes that they sent us。

Let's turn。So this， if here。That is just us saying that if we ever get anything from the other side and we are in the established state。

 we're immediately going to shut down the connection。 and in reality， of course。

 we don't really want to do that anymore。We don't want to shut down the connection immediately because we want to be able to accept data from the other side。

So this business， we don't want to do anymore。This business is really going happen only when。

Only when the user calls shutdown。So shutdown as a command you can call on TCP streams to say I have no more data to send right think of this as like when you drop the TCP stream。

 the other side has to know that you did that， but you can also say I'm done sending you data but you can still send me data and so we're going to have to figure out what to do about this business。

But here， clearly， we also need to make sure that we acknowledge to the other side that we indeed received that data。

So currently what we do is when we receive the packet。

 we sort of check that it's a valid packet and check which of the bytes we should really adopt。

In fact， I don't think it's even all of data here。嗯。Read stuff we haven't read。 So， for example。

 I think I need my drawing program here to。

![](img/49347db1b6244c3ae42b589040f18ec5_15.png)

Show what's going on。嗯。So let's see。嗯。Imagine that so we have this is our machine。

 this is the remote machine， and there's a channel between us right， this is the TCP channel。

 imagine that in the past we have received bytes one，2 and three。Right。

 those we've received in the past。 and then we get a packet from the other side。

That contains the bytes。2，3， and 4。Now， when we receive this。

 we have to make sure that we recognize that where's my。 this is the one。

 We have to make sure that we recognize that we don't want to read these bites again。

 because we've already read them over here， right？ Instead。

 we want to make sure that we only adopt this bite， right。

 This bite we do actually need to receive and add to our buffer。Rightai， this needs to go here。

Out that I did something stupid tonight。I meant here。嗯。So we might actually in TCP。

 we might get a data segment where only parts of the segment contains data that we haven't seen before。

So if we just currently what we did was dot incoming dot extend all of data， but that's not okay。

 it has to be only the stuff that we haven't read already。So let's look at how we might do that。



![](img/49347db1b6244c3ae42b589040f18ec5_17.png)

U。Let me see。It's been a while since I looked at this code， too。

So the received sequence base is the stuff we received from the other side。嗯。And。

Let's see so receive next is the remember that the the sequence numbers are naming bytes in the byte stream right so this is essentially this is going to be one for the first byte two for the second byte three for the third byte etc and so we only want to read。

呃。The bites from next and onwards。

![](img/49347db1b6244c3ae42b589040f18ec5_19.png)

Right， so。If we go back to the drawing。Yeah。If。

![](img/49347db1b6244c3ae42b589040f18ec5_21.png)

Let's imagine that like this is sequence number 703。This is sequence number 704， etc。Right。

Because remember sequence numbers start at a random offset。Okay， this packet from the other side。

 we're going to be told that the first bite of this is 704 because2 was 704。And our next。

 our next pointer。Is going to be pointing to here。 Our next pointer is going to be 706。Right。Because。

In order for this to be the state of the system， we must have previously received all of these。

 right， we previously received all of these。And when we receive them， we set next next equal to 706。

And that is how we can recognize that here， when we receive this packet， we only want this bite。

And so then the question is， how many bytes do we skip off of the packet we receive？ Well。

 this is the。Sequence number of that packet。 And so we have to skip。Next， minus sequence number。

 bytes。

![](img/49347db1b6244c3ae42b589040f18ec5_23.png)

Does that make sense？And my guess is in fact， remember how the TCB spec at the bottom has this really convenient overview of what do you have to do on all possible events and so for us we're going to have the segment arrive state。

So this is a new packet arrives。So what do you do if？It's down here somewhere。嗯。

<|OTHER|>We already do all of this。You can ignore the reset bit for now， ignore the S bit。呃。

The abitt we can ignore。Ding。Now we also need to update the windows。And then down here somewhere。

 process the segment text， right？

![](img/49347db1b6244c3ae42b589040f18ec5_25.png)

So let's go back to here。And see what it is we currently do。



![](img/49347db1b6244c3ae42b589040f18ec5_27.png)

So。It's actually pretty important to do these actually in order。

 as we have learned from messing things up in previous streams。嗯。

So let's see we what stage we're at here， so check the reset bit that oh sorry even further up。嗯。

Up here。Right right。So state， listen， this we've already dealt with。



![](img/49347db1b6244c3ae42b589040f18ec5_29.png)

If the state is sincecent。

![](img/49347db1b6244c3ae42b589040f18ec5_31.png)

That apparently， we just like ignore。Oh， so sincecent we can only be in if we've done a connect。

 which is not something we've implemented yet， so we can ignore this bit。嗯。Otherwise。

 first check the sequence number， okay， so checking the sequence number is what we're doing here。



![](img/49347db1b6244c3ae42b589040f18ec5_33.png)

![](img/49347db1b6244c3ae42b589040f18ec5_34.png)

We should arguably label these to keep track of where we are in the protocol spec right so this is implementing all of these checks。



![](img/49347db1b6244c3ae42b589040f18ec5_36.png)

Second， you check the reset bit。Which I don't think we currently do anywhere。

 like we don't tend resets。

![](img/49347db1b6244c3ae42b589040f18ec5_38.png)

Which is fine。 Then check the Simbit。呃。

![](img/49347db1b6244c3ae42b589040f18ec5_40.png)

So checking the Sbit in theory， we should do up here somewhere， yeah， up here。



![](img/49347db1b6244c3ae42b589040f18ec5_42.png)

Okay， so we basically just don't handle the Sbit at all currently。 So this business。

 we also don't do because getting this is an error and we just basically don't have error any error handling currently。

 right like here is basically saying you send a reset to let the other side know that you weren't expecting that。

 Check the a field， though， that we do do。Down here。Right if the abit is off。

 drop the segment and return。 Okay， so no a， great， So we just return。



![](img/49347db1b6244c3ae42b589040f18ec5_44.png)

If the apit is on， which is what happens in the remaining bit down here， if we are in sin received。

 say if we're in sin received， then we do this business。嗯。



![](img/49347db1b6244c3ae42b589040f18ec5_46.png)

If we are in the established state。うん。Interesting， yeah， so this is。

We're still in the business of checking the a field。

 the abit is on because otherwise we returned if we're in the established state or if when we're in Fin weight 1 or Finway 2 because they say in addition two right so all of these three are doing this business。



![](img/49347db1b6244c3ae42b589040f18ec5_48.png)

Right。

![](img/49347db1b6244c3ae42b589040f18ec5_50.png)

So that's this。Any segments on the retransmission queue。

 which are thereby entirely acknowledged are removed， right so here。



![](img/49347db1b6244c3ae42b589040f18ec5_52.png)

We're going to end up doing some pruning of self unacted。Right。

Because if the other side send us as for bytes that are still in our retransmission buffer。

 then we can now safely remove them because the other side has said that it's received them。

 so this is going to be relevant for rights。

![](img/49347db1b6244c3ae42b589040f18ec5_54.png)

嗯。Users should receive positive acknowledgecment for buffers which have been sent and fully acknowledged。

嗯。That's fine。 This is basically telling the when people did a write。

 you can now say that it's been written。 so this would be relevant for things like flush。



![](img/49347db1b6244c3ae42b589040f18ec5_56.png)

So like， oop。嗯。If no， if unacted empty。And waiting。Fluush。Notify right。

 So if the if the call has called flush， then at this point， if there's nothing in un act。

 then we can say that the flush is completed。

![](img/49347db1b6244c3ae42b589040f18ec5_58.png)

嗯。If the act is a duplicate， it can be ignored。

![](img/49347db1b6244c3ae42b589040f18ec5_60.png)

Okay， so this， I don't think is something we currently do， so I think。



![](img/49347db1b6244c3ae42b589040f18ec5_62.png)

Here we're going to say。

![](img/49347db1b6244c3ae42b589040f18ec5_64.png)

呃。u。Second n。Is less than。Self send U A。 this is probably not actually a less than， is it？嗯。

Feel like this check is also broken because of wrapping。

I think what we want here is actually wrapping less than。



![](img/49347db1b6244c3ae42b589040f18ec5_66.png)

So if this， then we can ignore the act。How， interesting。Yeah。

 so this is basically more error handling than we can pretty much ignore。嗯。



![](img/49347db1b6244c3ae42b589040f18ec5_68.png)

Let's leave that up for now。

![](img/49347db1b6244c3ae42b589040f18ec5_70.png)

This is related to updating the send window。 So if you remember from the earlier streams。

 one thing that TCP does is it limits how many bys you can have outstanding。

 Like if I've sent1 thousand00 bytes to the other side and the other side hasn't send that it said that it's received them yet。

 there's a limit to how many more bytes I can send like I'm not allowed to have more than a certain number of bytes in transit。

 Of course， when the other side acknowledges something。

 then now my window can grow again as in I'm allowed to send more bys。

 And so this is also something we're gonna have to。



![](img/49347db1b6244c3ae42b589040f18ec5_72.png)

De with for rights。嗯。Update to window。This is the Grooove box dark， hard color scheme。



![](img/49347db1b6244c3ae42b589040f18ec5_74.png)

嗯。Okay， that's fine。And then if we're in Fin weight 1 or F weight 2。So that's the checkdown here。

 if we're in F weight1， if our fin is acknowledged。

Then our Fness bin Act so enters state 2 and continue processing。



![](img/49347db1b6244c3ae42b589040f18ec5_76.png)

If we're in Fin weight。

![](img/49347db1b6244c3ae42b589040f18ec5_78.png)

Qu。😔。

![](img/49347db1b6244c3ae42b589040f18ec5_80.png)

<|OTHER|>N for the processing for established state。

So we don't actually want to adopt the data here quite yet。So this is still handling the a。

 Fin weight。

![](img/49347db1b6244c3ae42b589040f18ec5_82.png)

If the。Retransmission Q is empty。 The user's clothes can be acknowledged。



![](img/49347db1b6244c3ae42b589040f18ec5_84.png)

![](img/49347db1b6244c3ae42b589040f18ec5_85.png)

Okay， so here。So that's also not something we really need to worry about。



![](img/49347db1b6244c3ae42b589040f18ec5_87.png)

Close weight were supposed to do the same as for established。 So this should also include state。

Do we even have close weight yet？ No， we do not great。



![](img/49347db1b6244c3ae42b589040f18ec5_89.png)

So there's a bunch of states that we don't currently deal with。

 I'm just going to ignore those for now。 We ignore the urgent bit。

So now we get to process the segment text and the thing after that is checking the fin bit right so here we check the fin bit that's the next bit so here what we want to do is process the segment text。



![](img/49347db1b6244c3ae42b589040f18ec5_91.png)

And so here we're going to bring back this if right。

 because we only handle the segment text if we're in one of these states。

The drawing software is called My paint。

![](img/49347db1b6244c3ae42b589040f18ec5_93.png)

Right， so what do we do？Right， so it's just saying that when we're in the state。

 we're allowed to receive data， right because the connection has actually been established。

And we can adopt text from the packet into the buffers。

 either we can put a limit on how many bytes we allow to buffer or we can just adopt all of them。

 like read all of the bitetes out of the packet。嗯。We're just going to ignore push。Once the TCP takes。

Responsibility for the data， it advances。Receive next over the data accepted and adjust the receive window。



![](img/49347db1b6244c3ae42b589040f18ec5_95.png)

Righti。

![](img/49347db1b6244c3ae42b589040f18ec5_97.png)

So。Bring the oops。

![](img/49347db1b6244c3ae42b589040f18ec5_99.png)

Spring that in here， becauseuse it'll be handy to have the。



![](img/49347db1b6244c3ae42b589040f18ec5_101.png)

Doocks here， for our own reference。嗯。Right， so here we need to send an acknowledgement of this form。



![](img/49347db1b6244c3ae42b589040f18ec5_103.png)

Is the requirement。

![](img/49347db1b6244c3ae42b589040f18ec5_105.png)

And notice so this is something that keeps coming up in TCP that。

You don't necessarily want to just like send an act immediately because if you're about to send some data。

 you might as well include the acts， which are just changes to the header with any data that you're already about to send。



![](img/49347db1b6244c3ae42b589040f18ec5_107.png)

In our case， though， that's not actually something we're going to do。



![](img/49347db1b6244c3ae42b589040f18ec5_109.png)

![](img/49347db1b6244c3ae42b589040f18ec5_110.png)

ce nextSo this is already， I think， what right does。 Let's double check that。So。

 our right function sets。呃。Or is it。

![](img/49347db1b6244c3ae42b589040f18ec5_112.png)

TCP sequence number is set to send next and acknowledgement number is sent to receive next right。

 so send next， receive next and set the act flag， so all of that is already handled by right。



![](img/49347db1b6244c3ae42b589040f18ec5_114.png)

So Wright will take care of that for us。So if we just call self dot right， Nick。This。

 that will send that acknowledgement。That will automatically set the right acknowledgement。

 we will however， have to do this business， which is update received out next to match the data that we just received。

 and of course we're going to have to actually adopt the appropriate bytes。So how do we do that Well。

 Re dot next is the next byte we're supposed to receive。

 So recall that this was going to be what did we say self dot Where。Receive。Dot next。Minus。

The sequence number。 So minus the start of the packet。If I'm reading that right。

 I think that's right。Now， maybeU size。M be necessary。

We also still have to wake up the waiting readers。 Now from memory。

 we already set up a way to do this， right， so on packet returns available to indicate what is now available。

 So if we go back to Lib，On where's our call to on packet。嗯。

Right so this already has the required mechanisms for waking things up。

 so really all we have to do is make sure that the returned A。

 the returned availability contains the read flag， and then the packet loop。

 the main event loop is going to make sure to notify the necessary readers。So here。

Self thought availability。 and self thought availability。Already checks incoming right。

 so it will already set the right thing。 So we actually don't need to do anything here。

As long as we extend to this， it is now， no longer empty。 So when we get to this return。

 this availability is going to contain the read flag。

 and then the packet loop is going to wake up the any waiting readers。So in theory。

 this should now already let us do that。 And， of course， now that we have read those bytes。

 we now set。Let's see self dot received dot next to be equal to the sequence number plus the length of the data。

 right， so it now includes any by the received next is now bumped by how many bytes we received。嗯。

And so here there are a couple of ways to do this， we could either just add the number of bytes that we read or we can just set it to the appropriate value。

And we're going to do this by saying。Second N plus。Oh， question。Oh， keyboard。

 this is the Fiilco Majeto touch ninja。So this is going to be self dot。It's going to be second。

Wrapping a。嗯。The length of the data。嗯。And。Wrapping a， keep in mind that here if the if it includes。

 so remember that f and sin are both extra bites。嗯。

So if the packet includes a fin by then we need to add one， so if TCPH do f， then one else0。So。

Expected U32 found the U size。Sounds not right。To check。

How long have you been specializing in networking to know such so much about it。

 I don't think I've really been specializing in networking。

But it does help that I've written a TCP stack before， although a simplified one like this one。

 but it really just comes down to learning how the protocol works。

The size for values of type U8 cannot be known。At compile time。呃有。This has to be a reference。3，41。

As U 32。Great。😊，Alright， so in theory， we can now receive data correctly。 We do， however。

 want to make sure that the connection is shut down once the other side doesn't have any more stuff to send。

Like we basically want to make sure that the other side knows that we're done。嗯。So the question is。

 how do we do that well， what does right do？So does right set the fin flag。Hm。That's a good question。

 If you terminate a connection， do you have to keep sending the thinin flag。I don't think so。



![](img/49347db1b6244c3ae42b589040f18ec5_116.png)

![](img/49347db1b6244c3ae42b589040f18ec5_117.png)

I think what we actually want to do here is。We still want a peer。To。嗯。Yeah， so the first。

 the moment the connection has been established， we want to set the fin flag and write out the fact that we've set the fin flag。

嗯。Although do we want to do？This。Probably not。This is something we we're going to have to。

Deal with later。 So this to do that we need to make sure that we resend the f if the other side doesn't receive it is definitely something we're going to have to deal with。

 but not something we quite need to deal with yet。 But this， these two lines are essentially。

We're going to send a shutdown the moment a connection has been established right。

 because because we don't support right yet。 So we might as well do this。We don't support。Right。

 yeah。 So immediately send and a file。Of course， ultimately， this will not be here。So we'll do this。

But in theory， we should now be able to receive data， I think， I guess let's find out。No。

If I run this。呃。Actually， no， we also need to modify main。So， we're going to do。嗯。Buff is gonna be。

Something like this。If n is0。Then， we break。嗯。Otherwise。We print out the data that we got。In fact。

 we could print this as a string if we really wanted to， technically it's binary data。By。Right。

 so we read into the buffer if we got no bys， then that means the other side is hung up。

 otherwise we print out the bytes that we got and then we try to read again。Alright。

 so let's try that。Yes， I did do a masters in networking， although that was in wireless networking。

 So it wasn't quite this， although it's just if if you end up dealing a lot with networks。

 like TCP is so ingrained in all of the networking stuff that it just becomes sort of second nature to know at least at a high level how it works like how how the various bits and transitions work。

 like people study TCP a lot for things like congestion control and how it behaves in various settings and that I know a lot less about but I do know sort of how mechanically the protocol works。

Okay， so let's try now to echo F to。To our server。I crushed。Question is， why did it crash？

Slice index starts at one， but ends at 0。 Oh， I know why this is。So remember this business。

So remember how the sin flag is considered a bite in and of itself。Right。

Imagine that we received the very first packet from the other side。

That packet has say the content's fo， but it also has the S flag set。So at that point。

Self received next is going to be zero right， or it's going to be the first sequence number。

 which is prior to the sin。And the sequence number is going to be that same value。

Although that shouldn't actually matter。H。Slice index starts at one。Where is this， So this is at。

On packet。 Oh， that's unhelpful。 Why do I not get the line number in on packet。嗯。H。Reading data。From。

This。Good old print debugging。Receivedt next sequence number and data。

LetSee what we get when we do this。So this crashed and it says。😔，Reading data at there。 Okay。

 so it got an empty sequence of bytes。And received next。Is one， Oh， interesting。Interesting。

 so this would be the sequence number of the packet is this。那。Don't do that。

 The sequence number of the packet is。嗯。Da哒哒哒哒。Is this。The s。

 the next bite we're going to receive is this one。 But if this bite。Is the the sin bit。

 Then this is telling us read one B from this。 like skip the first by in data。

 But there is no first by in data because that first by is the sin bit， which isn't a part of data。

So how are we going to deal with that Well， I think what we're going to do is。

If the TCP header has since set。I get we're gonna do。Unread。Data at。And that's going to be equal to。

This。呃。And we're going decrease it by one。And now we can do this。Let's see how that works。

still crashed。 What does it crash with now？Same thing，From。H。So why is this misbehaving。

Let's try that again。Al right， so we got。Reading data from index 1。Oh， it's the thin。 It's not the。

 it's not the sin that's throwing us off。The sin actually we don't even need to deal with special because we always read to the end of the packet。

 if there's a sin there， we'll just end the unra datata at will' start at zero and that is just correct that what we need to deal with is the case where there's a f because that's saying you should read one byte for data but there isn't actually a byte in data。

So， instead。Oh。How do we want to do this This is This is only a problem if the fin bite is the first bite。

As in the Finb is the only bite。 If the fin bite is at the end here， let's draw this again。



![](img/49347db1b6244c3ae42b589040f18ec5_119.png)

It's gonna be helpful。

![](img/49347db1b6244c3ae42b589040f18ec5_121.png)

。Let's go over here。All right， so。嗯。How do I explain this？There's a data stream。She has some bites。

Let's make them not very。Interesting bytes，1，2。3， four， and then logically in TCP。

 there's also this like virtual zero byte。Which is the sin。And there's a virtual last bite。

 which is the fin。Right。And。Now， imagine that we receive a packet such that this is the sequence number of the packet and also next also this is received up next。

So at that point， and let's say that that packet spans these spikes。Okay。

 so we received this packet and what we're going to end up computing is。That。Next， minus c。Is zero。

Right， so we're going to read0 dot dot。 Now data starts here， right。

 Data is going to be this because that first byte is sort of a virtual byte。

 But because we are starting from0， starting from0 is fine because that's still going to get us all of the bytes。

So the sin is not actually a problem， even if we don't do any special casing of the sin bit。

The thininbit is also not normally a problem because let's imagine now that we get another packet over here that contains these bites right so it contains three and four and the Finbit is set。

And let's say that this is next and also seek。Okay， so at this point， we would do the same thing。

 we would say next minus sec， which is0。 okay so we're going to do 0 dot dot and0 dot dot is going to be from0 of data。

To the end of data， right， because data only spans these because Fin is virtual。

 So that's still going to give us the right bys where this is a problem。

 You might have spotted this already is if this。Is Sih。And next， so data is actually empty， right。

 Data is entirely empty。Because the Finbte is virtual。So what are we going to do， Well。

 we're going to do。Sorry。This would be， if next is here。The actual problem。So next points here。

 because we've already received the finbitte。So imagine that this is like the other side resending the fin。

Right， so the sequence number of the packet is the start of the fin。

And our next is beyond the fin because we already received the fin in the past。 Well。

 if this is the case， we're going to compute next minus C。And that's going to be equal to one。

And so we're going to do one dot dot。But data starts at 0。

 So there is no like one is going to point to here。

Which is outside the bounds of the empty data array。

And so this will only happen if we see a retransmission of fin where f is at the start of the packet。

So with that in mind。

![](img/49347db1b6244c3ae42b589040f18ec5_123.png)

U。What we really want to do here is。If。Uread data at。Is。😔，Wang， actually。



![](img/49347db1b6244c3ae42b589040f18ec5_125.png)

IThis might be a problem for even if Sik is here。The problem is if the next is at the end， right。



![](img/49347db1b6244c3ae42b589040f18ec5_127.png)

So I think what we actually want here is。If unread data at is more than。Ou。

We can't actually use more that。 No， we can。Is。Greater than or equal to data dot L。

That is the only case in which it's a problem。 so here sort of as a note to ourselves。

I think we want to assert。That unread data at is data dotlen。Because this can only be the case if。

Must be that。We must have。Receive a re transmittedit fin that we have already seen。嗯。

Next points to beyond the thin， but the f is not in data。So in this case。

 unread data at should be set to0。Let's try that。And thats still crashed， where did it crash now？

Ced at this assertion。呃。Plus one。Y。So unread data at is where we should start reading。

 and that should be after the f。 and the fin is located logically at the end of data， which is。呃。

Data dot L is the start of the fin。 plus one is the end of the fin。

 which is where we would start reading。 so this should be true。No那我。嗯。0。Oh， sorry， greater than。

Is the problem。They could both be zero， which is fine。Like in the case of sin， for example。So。

 that's fine。ho。Let's see。😔，No a got connection read 0 by of data， no more data。Okay， so clearly。

Something weird happened。出了。We'll， we'll bring back our。Our friend TCP dump， wire。Oh。

 I don't remember what command we used。T shark。Alright。So we're going to start the server。

And start T shark。We're going to do this and see what happens。Moi。😔，So。

First thing that happened is the。Connection attempt to the server。 The server responds。

 So the connection attempt is a sin。 The server responds with an act for the sin and a sin， right。

 So it acts 1。The other side acts。It then sends。Four bytes of data。

We respond saying we're done sending data， right， so this is the point where we like immediately send that we're not going to send any more data。

呃。They send us。U。Were done after five bys， right？ So this is or6， I guess。

 sin plus 4 B of data plus the fin。And the act is two， because they acknowledge our fin， then we act。

Then we act their data， then we act their fIN。The real question is。

 so this does imply that we're receiving all of their data。So the question becomes。

 why does it say that we read zero bytes of data， that doesn't seem right？So， let's hear say。

Reading from。呃。And see where those bites go。Reading from4。Well。That doesn't seem right。

So reading from four implies that we're just reading from the end， which is not what we want to do。

 we want to read from the start。So this four seems unfortunate。嗯。Cause this should really wa。

 what just happened。In theory， this should be zero。

 instead it's saying how many bytes we should read。Which implies that we have， for some reason。

 already updated received next。I that。B though。Ah， we do that there。



![](img/49347db1b6244c3ae42b589040f18ec5_129.png)

Why do we do that there？Does the specs say to do that there。



![](img/49347db1b6244c3ae42b589040f18ec5_131.png)

Where is this， this is。

![](img/49347db1b6244c3ae42b589040f18ec5_133.png)

After checking。Up here somewhere。Not the reset bit， but probably first check the sequence number。

That's fine。嗯。I don't think that line should be there。Check the a field。

 None of this sets to update received next， because received next shouldn't be updated until here。



![](img/49347db1b6244c3ae42b589040f18ec5_135.png)

So。😔，I don't think that's true。嗯。Specifically。I think this should only happen。Oh。

When should this happen？I think this should only happen after we have received that data。m。Yeah。

 this line is definitely not right。U。

![](img/49347db1b6244c3ae42b589040f18ec5_137.png)

Oh， I guess。When we receive the sin， we do want to say that we should skip the sin bit。Fourth。

 check the S。I don't think that's true。

![](img/49347db1b6244c3ae42b589040f18ec5_139.png)

I think this happens further down。 I think that。It is only at this point where we actually。

Decide to read some data。That we're going to add to it。

Cause now received dot next is going be equal to。Oh yeah， it's this business。嗯。And also， of course。

 if。Although there is a question here of。When we get the initial C from the server。

 we need to make sure that we set next to be one。嗯。

LikeI'm thinking of when the connection is first set up， then we get a packet that contains the seek。

At that point， our next should be one。Yeah， this is not going to be quite right。

 we're going to have to deal with that here too。Onpack。嗯。ASo the initial seek packet。I see。呃。

FTCPH dot sin。Then， self thought。Receive dot next。呃。Should be equal to the s number。Wrapping add one。

This is。So， this is。Got sin part of initial handshake。So here we want to assert the data is empty。

Because it should be the sin should contain no data from memory。Well， I don't think that's necessary。



![](img/49347db1b6244c3ae42b589040f18ec5_141.png)

Take the Sbit。The accupant is off。See， this line makes me think that you can't send bytes in the first packet of the handshake。



![](img/49347db1b6244c3ae42b589040f18ec5_143.png)

Which is unfortunate。嗯。Right， so let's try that。 Although now。

 now this is going be wrong because now received dot next is going to be。Oh。

 I see in the subsequent segment and in the next packet。

 receive next is going to be one right immediately after the sin and sec n is going to be one。

 which is going to be the first data byte， so that should still be right。And this。Oh。

 this should be same。嗯。And we should never get here with S set。So this should still be right。

LetSt that。嗯。Seron failed left Eagle's right。Destination and so slices have different length。

Wait where did this happen？In TCP stream， read。Well， that's progress。

But why is it not giving me the line number？ That's kind of annoying。

 So this is happening in the implementation of read。

 So that suggests that it actually got some bytes to read。 So that's good。

It would be useful to know what line it was on， though。But apparently， he doesn't want to do that。

So it's one of these that are failing。Interesting。Oh yeah。 This is definitely wrong。

 So this code is where we are reading， we're reading bytes out of incoming and into Buff。Right。

And we're going to copy。yeah， it not definitely not right。And we want to copy stuff into Buff。



![](img/49347db1b6244c3ae42b589040f18ec5_145.png)

And we're going to have to copy from， remember， here， let me draw this again。



![](img/49347db1b6244c3ae42b589040f18ec5_147.png)

It's useful for reference。So we're using a V DQ， which is a ring buffer。

 and a ring buffer is essentially just a list like this。Victor。It has a。Head pointer。

And a tail pointer。And。All of the bytes that we have stored are stored between the head and the tail like so when you read from it。

 you erase the old head pointer and you stick it to where you're now reading from。

 when you write to it， you write at the tail and then you get rid of the old tail and you update the tail pointer。

Of course， what can happen when you have a ring buffer like this is you can have。The head。Be here。

 And the tale。Be here。So now you have byte one here and byte two here。

And so if we're now going to copy， we can only copy from contiguous memory， right。

 so we actually need to do two copies。 We need to do one copy from here to here。

 and we need to do one copy from here to here。If we're copying into Buff， which is here。

We want to make sure that this bit goes to。Here， and we want to make sure that it's going be goes to there。

 And we want to make sure that this bit goes to。Here。Currently， though。

 that's not really what the code does。

![](img/49347db1b6244c3ae42b589040f18ec5_149.png)

So currently the code decides how many bytes is going to read out from the head right so the head is the from the head to the end of the list or end of the ring buffer。

Like end as in rightmost part of memory。 And that's going to be either as much data as is in head or as much space as is in Buff。

 right， so imagine that the ring buffer has like 1000 bys in it， but buff is only 20 bys long。

 Then we can't copy 100 bys into Buff。 It has to be the min of the two。

And so Buff is going to copy from slice。As many bytes as we allow it to read。

And then this is where it。Right， and so the question now becomes， how much should we read from the。

From the tail。Oh， does it require these to be equal？That's silly。 Okay， so this is gonna be buff。

Dot dot H read。So we're going to copy H read bytes from head into Buff。

And then we're going to see how many bytes are left。

 so this is the length of buff minus the number of bytes we read from head， the minimum of that。

 which is how many bytes we have left to read into Buff and how many bytes we can read into Buff。

And then we're going to copy oops， nope。And this is going to be， I guess， H read。Qu。

H read plus T read。Is going to copy stuff from the tail。So let's see if that works better。Oh。

Red four bytes of data got bytes。 Okay， so our main program now actually got some bytes out。

That's good。 It doesn't look like it terminated to the connection， though。

 So remember back when this used to work， or is that。Much further up， apparently。哦。why can't I find。

 Oh，cause it's in this buffer。It used to say no more data right。

 So the the server still needs to realize that the connection went away。

 which it's not currently doing。 In fact， we can do this here。

 like this no more data is no longer printed， even though the client clearly went away。

 right like it terminated， So this means that we're now missing the signal that there's no more data to get。

Which seems unfortunate， right， There's no， no more data here。 It does get the4 bys。

 but this suggests that the second time it tries to read， it doesn't get to hear。

This suggests that is received closed is not returning true。So why is that？😔，And。While， in theory。

Actually， let's look at what the packets we get are。Let's pull up our trustee T shark again。

 Run this。嗯。So。It sends to us f， and we act that f。Right， so this suggests that。

Over here we are probably entering this。🤢，So now the question becomes。W。Is the reader。Not。Like。

 why does it block So my guess is it it ends up down here in the second call。

 although we could figure that out， right， so here。嗯。Trying to read。嗯。Connection has gone away。

And this is connection still active。What。没有。Connection is still active。Oh。Why does it say。

That's weird。So it says red some amount of data， print this。Oh， it's cause I'm stupid。

We want to keep reading， we don't want to keep accepting。Let's try that。Great。

 connection is selectiveive， red bites。Don't know why Prince got connection again。Oh。

 that's also because I'm stupid。Let's try that one more time。Run this。

 print this and now we'll see we got a connection。 We're trying to read connection is deocive。

 we're at four bys of data， and this， of course， is fo and a new line， then it tries to read again。

 and it notices that the connection has gone away because the other side hung up we read zero bytes of data which indicates end of file and then we recognize there's no more data Great。

 and the other side seems to be totally happy with that。So with this。

 I think we actually have reads right， Like now clearly it works to just read。

 We can try this if we want to be a little bit fancier。 Here's what we're going to do。

This is going to get real fancy。Let's have this print out。What it got from the other side？

So this is going to be。St。UTF 8。And we're going to unwrap。It's fine。

So this is just interpreting the bytes we get as a string。

I kind of want these ignoring weird packet things to go away。I also want。Used to go a。

Ignoorring weird packet。Alright， let's try this。So let's clear out the screen a little bit。

Now what we're going to do isre going to connect great， so we're connected。 I got zero bytes。

 I do hello， enter。God packet reading。 hello。 great。 Okay。

 so it actually got the string that we sent。 Now， what happens if we try to send another string like bar。

W， Zubbar。O and then I'm going to terminate the input so C D sends an end of file。And indeed。

 it says no more data than the connection has been terminated。 Right。

 So reads now work even across multiple packets。Yay。Excellent， of course， here。

 there's no pocket loss。 So it's kind of hard to。It's hard for us to check whether all the logic is right。

 but it does mean that like we can actually now receive data that's sent over TCP。In fact， here。

 let's try something real cool。So curl sends HDP requests， right， like web requests。

 So let's see what it sends。Clear the screen and let's see what curl does。Well。

 it does nothing Could I type the wrong IP address， but let's see。不。Readed 80 B of data。

 Get slash HDP hose user agent， except no more data。 And curl says empty reply。 Great。

 So this now actually works with real TCP clients。 right？

 This is the kernelel sending like real HDP requests to our server。 We can't I respond with anything。

 but at least we got the data that we wanted。😊，Sweet， so we now have working reads。

Let's go ahead and commit this。Implement reads。's to。Great。Right。

So now it's time for rights and rights are a little bit more problematic because you also have this notion of retransmissions。

Because we don't really emulate a faulty link。 we might have an easier time than you otherwise would。

 And there will almost definitely be bugs in what we implement。

 but we at least want the basic thing to work。I think what we're going to do is。First， implement。

AhDo I want to implement shutdown first？😔，H。No。Yes。Maybe。Yes。

So remember how we have this like ugly little hack up here， this can probably go away。呃。Kll that。

So we have this ugly little hack where we immediately send， essentially a shutdown， right Do。

 we send a fin bite to the， to the client immediately because we know that we don't support rights。

 Well， let's do a little bit better than that。 Let's make it so that in Maine。

We can do stream dot shutdown net。Oh， that's a good question。St down。This。Net shut down， right。咁嘛。呃。

So instead of us doing this internally in the library。

 we're now going to have this happen externally， right like you should be able to shut down the right side of your pipe。

 basically saying to the client I'm not going to send you any bytes。

This means that this is going to go away and this has to be something that the client can actually trigger。

 Do you implement time weight。Depends how you define implement。Time wait is here。

Unclear that it does the right thing。 Like we don't have any timers yet。 So I'm going to go with no。

 but the， the state is represented。嗯。Right， so this business， which we currently do immediately。

 the moment any connection is established， we're instead going to have the client be able to issue this command。

 basically。嗯。So how are we going to do that， Well， F is a little weird because it's not an actual bite。

 right， We can't stick at it unacted because it's not， it's not a bite。

 but it is something that we sort of have to retransmit。Now。



![](img/49347db1b6244c3ae42b589040f18ec5_151.png)

If we go back to our state diagram。Appear somewhere。Should have just kept it open。

 It's pretty handy to have。嗯。is it。Here we go。嗯。So close is the operation that a client can make when it says it wants to send no more data。

So that's when we send our fin。嗯。And so what we do know is that if we're ever in a state where。

If we're ever in a state like Fin weight 1， Fin weight 2， or closing。

 although can we even be in closing。

![](img/49347db1b6244c3ae42b589040f18ec5_153.png)

Yes， it is possible for us to be in closing。

![](img/49347db1b6244c3ae42b589040f18ec5_155.png)

No， I don't know。 We， I don't think we implement closing currently。

 is probably its own kind of broken。 but certainly if we're in。Ooh。

 that will actually be possible now。Which we're going to have to be careful about。

 but if you're in Fin weight 1 or Fin weight2， then you know that you've already that the client has requested that you close the connection。



![](img/49347db1b6244c3ae42b589040f18ec5_157.png)

嗯。So the question really becomes down here and shut down。 what do we do？ Well， certainly。

 we're going to have to get access to down here。We're going to have to sort of open up the connection。

 right， get the lock for the connection， and then we're going to have to do something on that connection。

Right， like C dot finish， something。 How do you get inline compiler complaints in BM。Oh。

 this is using neooing language server。Which gives you this。Or you can just use Ale。

 which is also fantastic。Yeah， so the question becomes， what do we really want to do here。

 like how do we want the client to signal that they want to shut down？Well。

 we could have a close function， right， So it's called close in the spec。

 So we could just say that there's a close function。

 And then what we want to do with close we can do in here。



![](img/49347db1b6244c3ae42b589040f18ec5_159.png)

![](img/49347db1b6244c3ae42b589040f18ec5_160.png)

So the question because， what do we want to do on close well。呃。

We certainly want to indicate that the connection should now be closed。

 we might even want to send another packet。So here let's add in pubb Cate。Closed rule。

So this closed is really the fin by， which is this virtual byte at the end of the send stream， right？

So down here。I guess， on here。On connection。We're going to have we have two of these， I forget。Close。

嗯。What is close going to do well？Cloose is certainly going to say self dot close equals true。喂。



![](img/49347db1b6244c3ae42b589040f18ec5_162.png)

And in fact， we can again， look at the spec and see what it tells us to do。So when you get a close。

Or nope， to for that。Segment arrive， segment arrive， status call， abort call， close call。

So if you're in the close weight state， actually， there are more here。If you're close。

 like if you're trying to close a connection that doesn't exist， that can't happen to us right。

 because you have a TCP stream item And so you can't like you wouldn't be able to call shutdown in the first place。

 if you're in listen。We probably want to deal with this at some point， but let's ignore it for now。呃。

That's interesting。 So sin sent。 This is if you try to shut down a connection that has not yet been established。

 So in that case， you can just like ignore the fact that you sent a sin。

 You don't need to send anything。 And when the other side replies， itll they'll just get an error。嗯。

Soon received， right。 So here the question becomes， what do we do well。Really。

 this comes down to essentially the established state。

 which is you cu the fin as if it were a normal bite。

 right you queue it as if it were at the end of the send queue。And。And only when only essentially。

 only when we're allowed to send more bytes and we've reached the end where the fin would be。

 then do we send a fin segment， right so。So remember how there's a window of where we're allowed to transmit。



![](img/49347db1b6244c3ae42b589040f18ec5_164.png)

Let's go down here somewhere。嗯。So imagine that these are the bytes we're trying to send。1，2。

And then logically， we also want to send here right， so when close is called。

 we're going to add a fin to the end here。But imagine that the other side only lets us send one byte at a time or let's say two bytes at a time。

So we send these two， so even the close has been called。

 we can't send the fignette because we're only allowed to have this is the window。Right。

We're only allowed to have two bytes outstanding。Now， when the other side acts this bite。

 for example， let's say that this bite is act。 Well， at that point， our window extends to。These two。

So at this point， we can， like this bitete we can now ignore this has already been received， right？

And we can now send2 and 3， but we still can't send the fin。Then at some point， it's going to act。2。

 and now the window is three and thin。And two can be ignored。And so now we can send three。

 although we've already sent three because it was already in the previous window。

 but only at this point are we allowed to send the fin because it's within the window。

 So even though clothes was called much earlier， we can't send the fin on until we're allowed to。呃。

Is that the reason you're trying to make TCP module development for rust。

 even though already have it on C++ to be more secure。 No。

 so the reason we're implementing TCP and rust is just because it's an interesting use case in writing low level code。

It's。Not actually。Like the intention is not for this to be like a production ready TCP stack。

 It is more because it's interesting to develop。But but hopefully this makes sense right。

 so we're only allowed to keep a certain amount of bytes in transit to the other side。

 so even though we want to send a f， we might not be able to do so yet。



![](img/49347db1b6244c3ae42b589040f18ec5_166.png)

This is also why we have this the I don't have it open。

 but the the unact bite list is like basically bytes like these， right。

 So when we're only allowed to send one and2 but the client like TCP stream has already written three。

 we need to keep this around somewhere right until the time when the window extends to here and we're allowed to send。



![](img/49347db1b6244c3ae42b589040f18ec5_168.png)

Right。And so that is unact。 And the f is sort of logically in that same unact。

 but it's not a real bite。

![](img/49347db1b6244c3ae42b589040f18ec5_170.png)

So。The question becomes， what do we want to do on clothes。 Well。

 we sort of want to send stuff if we can。 Of course， the problem is this。



![](img/49347db1b6244c3ae42b589040f18ec5_172.png)

What we've introduced here is this notion of time that we didn't really have before。

 We might not be allowed to send anything else。 So we need there to be a timer running that like decides that。

 hey， now is probably a good time to send something。



![](img/49347db1b6244c3ae42b589040f18ec5_174.png)

![](img/49347db1b6244c3ae42b589040f18ec5_175.png)

um。Like we can't just do self right here， right， I would not be okay。So instead。

 what are we going to do？We can just， we can imagine that there's just like always a timer running and so we're going to set self to close to true and then we're going to wake that sort of timer up to let it know that there are bys to write out that would be one way to deal with this。

How do we want to do that， though？嗯。Hm。It's a good question。 So at this point。

 we have to decide what our timers are going to look like。 right， So with this notion of time。



![](img/49347db1b6244c3ae42b589040f18ec5_177.png)

![](img/49347db1b6244c3ae42b589040f18ec5_178.png)

It sort of means that there always has to be， there has to be something that deals with time and that schedules when we're going to send stuff or resend stuff。

But where do we want that timer to be， The the problem we have is that this timer also needs to。

Access the the connection states。 it needs to take the lock on the connection so you can't like。

Do a write while the timer is also writing stuff out as an example。😡。



![](img/49347db1b6244c3ae42b589040f18ec5_180.png)

The easiest way to do this is probably to have the。Packet Lou。So we have this like on packet loop。

 right？So the packet loop just spins trying to receive things from the ni。Ideally。

 so this is a to do we have from earlier right， is we want this received to have a timeout so that we can like block on receiving a packet or a timer expiring。

From memory when we looked at this， there wasn't actually a way to set a timeout on receive here。

 so this receive is just going to block forever， which means that we can't do the timer management in the packet loop。

 we actually need to have a separate thread that manages timers。嗯。So let's do that。Where is it， we。

Let's see。 what does interface new do？Interface new。Spawns a thread that does the packet loop。

And I think we're going to need。Timer handle。Timely。And I need a。Thread to handle here for interface。

So this is going to be the timer handle。嗯。哎。So。Ooh， actually， that's going to be a problem。

That's not going to work。The timer loop needs to also have access to the interface because it needs to be able to send packets。

嗯。Ha。I don't know how we're doing this。嗯，嗯。So let me try to explain what the problem is。

When we open a ton top interface， we only get one handle to it。

And that is the handle we need to use whenever we receive packets。

 but it's also the handle we need to use whenever we write packets out to the network。嗯。And。

The timer thread sort of also needs to have this because the timer thread could totally decide that it needs to send a packet。

But the the packet loop is the thing that owns that interface right， and in fact。

 it's blocking on it right the main loop is going to use Nick dot receive and it's going to be blocking on receive。

 so it is using that interface and we can't have the timer the timer thread also try to use this at the same time。

At least not safely， probably。So the question is， how do we set a timeout for that well？



![](img/49347db1b6244c3ae42b589040f18ec5_182.png)

I guess we're going to look at to top， see what we get， oh， ton dash top。



![](img/49347db1b6244c3ae42b589040f18ec5_184.png)

呃。Interface。So there's receive here。And let's look at what receive does receive。So， receive。

Just as a read on the underlying file descriptor。And what is the underlying file descriptor， In fact。

 the real question is， can I get the underlying file descriptor？ Yes， indeed， I can。

So a fall descriptor， if you're not sort of well versed in Linux and Uni， fall descriptor semantics。

Basically， everything that you can interact with like files， network sockets。

 pipes have this notion of a file descriptor。 So this is a number that the program keeps track of that is mapped to the file the network socket or whatnot in the kernel So whenever you do a read or a write you're really just doing a read you send a read system call to the kernel you tell it I want to read from this file descriptor and you just give it a number and then internally the kernel translates that to oh that is this TCP socket。

A ton top interface apparently is the same thing。 it's underlying， it's just a raw file descriptor。嗯。

And we can， in fact， extract that raw file descriptor。 And if we want， if we look at here。

 let's look at。

![](img/49347db1b6244c3ae42b589040f18ec5_186.png)

Look at the rust source code because that's fun。Oh。Why is my internet slow。That's。

Somewhat disturbing。Really？😮。

![](img/49347db1b6244c3ae42b589040f18ec5_188.png)

![](img/49347db1b6244c3ae42b589040f18ec5_189.png)

Why。Okay， that was weird。Alright， let's look here， Lib。might be it should be lip standard。Ss。Uix。Ne。

Time out。We find here。So these are operations you can。

 this is sort of how rust implements various operations on sockets like TCP streamam， for example。

 So there's a there should be a read。Set time out， right。

 So there's a set time out function that basically when you call things like receive time out on。



![](img/49347db1b6244c3ae42b589040f18ec5_191.png)

In fact， I can show you。Let's look at TCP streamre。So TCP streamam has at know where is it？Oh man。

 I want this。You can do set read time out and set right time out on TCP streams。

 This is the same for any kind of file operation and you'll see that。Self dot 0。 What is 0 here。

TCP stream is really a net I No well it's going to be the same for TCP stream， it's a net Imp。

 which is the implementation of TCP for this platform and ultimately this ends up calling the set timeout function。



![](img/49347db1b6244c3ae42b589040f18ec5_193.png)

For the given operating system。 So on Uniix， this is basically what that does it。嗯。

Pas the duration into an appropriate like。Structure that the kernel expects。

 And then it does a Uni system called to set options， set a timeout on that。On that socket。

 And so the question is， how can we do this a similar operation。

 like what is the system call we need to make， giving the file descriptor of the to top interface。



![](img/49347db1b6244c3ae42b589040f18ec5_195.png)

![](img/49347db1b6244c3ae42b589040f18ec5_196.png)

嗯。

![](img/49347db1b6244c3ae42b589040f18ec5_198.png)

So that we end up setting a timeout for it， well。That is a good question。

 Let's go here and do man read。 No， man to read。System call。

Because remember looking at the source for this， we saw that receive。

Is really just calling read on the underlying file descriptor。Right。Where was the？F oh。

 FD is in fact a file。That's even better。So a way for me to get at the file right so if FD is actually just a file。

 all we need to do is figure out how rust sets a timeout when it does reads on files。

So instead of looking at TCP stream， we'll look at file。

 I don't know if there's a chimeout for file actually， this might be the problem we run into。嗯。Yeah。

 this probably doesn't have a read timeout。Let's see what Reed here does。嗯。Oh。

 that is a very good question on whether it's possible to set。A timeout for Re。On Linux。嗯。

It should be。Probably an ocyl。To be honest。But documentation for those are terrible。



![](img/49347db1b6244c3ae42b589040f18ec5_200.png)

Set timeout， read。H I guess I could select over it。I was hoping that was a nicer way。



![](img/49347db1b6244c3ae42b589040f18ec5_202.png)

嗯。That's awkward。Okay， that's fine。 We don't actually need this to be a high performance version。

 So what we're going to do is use Ns Nix is a great a great crate that wraps various like low level kernel features in particular what we want to use here is the。

 I guess it would be under cis probably。😊，Slect。嗯。This one。So select is a system call on Linux that。

Lets you。Essentially， it notifies you when a given file descriptor is ready to do an operation on。

 it does not actually do the operation， but what you can do is give in in this case like。

A file descriptor that you want to read from， and it will return when you would be able to read from it without blocking。

 but it also lets you give a timeout。So this is saying。

Let me know when I can read from this or when this timeout has expired。

I was sort of hoping there was a nicer way to wrap this， but it doesn't really look like it。嗯。

So that is what we will end up doing。嗯。So cargo Tamel， let's add in here， Nick。0ero 13。And here。

We're going to have to issue this call。We want to read from Nick。But we want to not block。呃。

But we want to make sure that。We'll wake up when the next timer。Has to be triggered。Yeah。

 it's very similar to selecting over channels where one of the channels is a timer channel there are many ways to do this。

 So Epo is the the other way that you often use on Linux on Mac OS。

 I think you would end up using K Qs select is。Not what you want to use in very performance sensitive cases because it has some issues。

It also has the downside that we're now going to end up doing two system calls right。

 we do one for the select and then we have to do the receive。

 but we're just going to ignore that for now。So what does select take？In file descriptors。

The highest file descriptor set。Oh man， this is awful。 I don't want to use it。

 but I think we may have to。Actually， is there a nicer one？That I can easily use。😔，Probably not， oh。

 maybe poll。Oh， yes。Great， let's just use poll instead。Great， even better。

Because we don't actually care which of the the so when you're implementing like heavy duty network IO。

 for example， you probably really care whether you use select or Po or EPolL or KQs or any of these mechanisms。

 in our case we don't actually care because it's not super performance critical but we do we just want whatever has the easiest interface to use。



![](img/49347db1b6244c3ae42b589040f18ec5_204.png)

![](img/49347db1b6244c3ae42b589040f18ec5_205.png)

And so poll is going to take。呃。Okay use all the pole FDs。What does？People do。Oh that's fine。

 don't care about that。Timeout is the number of milliseconds that pole should block。

It's another good question of whether milliseconds is good enough。But， we'll see。So。Poll FD。

All right， how do I make one of these？Great。So we're going to say PFD is going to be mix pole。



![](img/49347db1b6244c3ae42b589040f18ec5_207.png)

Caul of the new。Right， and we're going give we're going to need to give a raft D。

 which we can get from Nick。As rawftD。喂。And we also need to give it event flags。Just probably just。

Yeah， we want， is there data to read？Right， so we want next poll。Event flags。Pull in。

That gives us a pole of D now that we have a pole of D。We can pass that to poll。

So this gives us a pull of T。 And now we want to call that on。I guess。This。

 and we want to give a timeout。 And what is that timeout going to be， Well， in theory。

 it'll be whatever the next timer is。 I think what we're going to do here is we're going to do something a little bit stupid。

 Instead of trying to cleverly manage timers， there are lots of ways to like manage a set of timers and wake up when the next one is due to expire。

 But instead what we're going to do here。It's a little stupid。

 but we're going to do the stupid thing is we're just going to wake up every we're going to wake up every millisecond。

呃。

![](img/49347db1b6244c3ae42b589040f18ec5_209.png)

And then decide what to do。This could totally be more clever， but we're just not going to be clever。



![](img/49347db1b6244c3ae42b589040f18ec5_211.png)

And as you see， the call to poll will block either until the filescripter becomes ready。

 so this would be that we're allowed to read， or there's a signal handler being called。

 we can ignore that for now or until the timeout expires。And of course。

 there's also you can give a time out of zero and a time out of zero makes it so that it's going to return immediately and basically tell you whether or not you would be able to read。



![](img/49347db1b6244c3ae42b589040f18ec5_213.png)

Okay， so we're going to wait for only one millisecond， it's going to return a N result。

That's kind of awkward。嗯。And I think。It's awkward。Remember that this function is supposed to return an IO result。

 what Paul gives us back is not an IO result， it's a NI result。

And I don't think this implements into IO error。嗯。So what we're going to do is do。Map error E。嗯。

We're gonna do。Okay， what can I do with an  Erno？Can I turn it into an IO error。

 That's all I really want to know。嗯。That's anl。Implement from Eno for Iowa， great。So in theory。

 I should be able to do E dot。What was it called ass？As Erno。Unwrappped。

 we don't expect there to be any other type of N errors。

And then we're going to question mark so as Erno Unw is going to give us a N Erno one of these that implements into IO error。

 and so therefore we can use question mark。So that， I think should work fine。呃。Great， and now。

Depending on what the return value of this is， so poll。



![](img/49347db1b6244c3ae42b589040f18ec5_215.png)

The function will return as soon as any event occurs。Allright。

 so the question is what is this return value should really be documented here。

 maybe we should submit a pull request， but for now。



![](img/49347db1b6244c3ae42b589040f18ec5_217.png)

What does Paul return。Oh， the field R events as an output parameter。So what do we get back？😔，Oh。

 it's going to modify the pull FD。I see。So this is gonna be really。This。And we're gonna give in。This。

It's going to be some n there。 and I don't exactly know what the n is。 The N is。呃。Okay， that's fine。

So what are the return values on success of positive numbers returned。

 this is the number of structures which have non zero R events fields。

A value of0 indicates that the call timed out and no file descriptors were ready。Great。Here if n is0。

Time up。Or I guess， timed out。Do something with timers。呃。

I guess we should assert that n is not equal to -1。 that shouldn't be possible， right。

 minus-1 would be an error which should already be handled by NIs。If n is zero， something timed out。

Currently， we're just going to have that do a continue。Which means that if we get down here。

 that means that the file descriptor is now ready， and so therefore we can do this。So pull of D。

 essentially what this means is。When the poll returns， if n is1。

 that means that this pole if the changed， which basically implies that this event happened。

 we could double check that by checking the events that happened for the file descriptor。

 which in theory should return a thing saying that， yeah， you can now read。



![](img/49347db1b6244c3ae42b589040f18ec5_219.png)

。But here， because we know that the only way that we can get to here is if it is now pollable。

 we don't really need to is readable like there's data available that that basically means that we don't have to make this check at all because there's only one possible way you could get here with。

 I guess we could。Assert E N1。We could also assert that Poland in is that we were just going to ignore it。

嗯。Great，If I do， like。Timers。If I do this， that's not what I'm meant to do。If I knew this。

 what happened。Why is it fetching the in alchsns。呃。You don't have to set non blocking on the F D。 No。

 you don't。 So this is one of the reasons why poll is nice is because you just tell it I want to read from this file descriptor and let me know if it's not available for reading。

 So keep in mind that poll is not I'm polling this file descriptor。It's not like， do a read。

 It is tell me when I can read， just a little different。呃。cannotnot find the value of PDF。

 That is because it is P F。啊PFD。Somehow PFD is a lot harder to type than PDFf。And of course。

 we need to assume that we're on Uni so that we can use asR FD。呃。Right。This。So this really just set。

嗯。Clloose equals true， right， closed equals true。And in theory， it should also reexamine some timers。

To but we don't actually need to deal with that at all currently。

Because the timers should just take care of that， which means we don't need this function anymore。

And shutdown can return。Okay， immediately。And now this needs to include。Closed is false。Yeah。

 so now you see they're just like timers firing so often。

 which implies that our thing is actually working。If we want to make sure that the other stuff is still working。

 we can just not do the not print timers and then check that this command invites the works。

 which it does。Right， so this is imping that this is all working the way it is， because the。

We now have a sort of an entry point for where we can do stuff with timers。

And so what are we actually going to do？ Well， there are a couple of things we could do。Really。

 what we want to do here is when a timer expires， then like do what the timer tells us should happen when it expired。

 Instead， what we're going to do is something a little bit stupid。

And you're probably gonna dislike me for doing this。But we're going to do it anyway。

We are going to do。Where's my， yeah here。Bear with me because you're all going to hate me for this。嗯。

So we're just going to loop over all of the connections and we're going to call this on tick method。

 and ont is going to get to decide basically whether it wants to do something。

And so the idea here is that the。Dan。The connections are going to keep track of their own。

 like when stuff has to happen。 They can just check that in on tick。

 and they only really need to keep track internally of when they want something to happen。

 We'll see how we end up using that。So if we now go to TCP， we now we have on packet。

 and now we will also have。I guess here， we can now， finally given in。This。

I guess where is my on packet？い。It will get these。Yeah， that's not what I'm meant to do。On packet。So。

 this is going to be on tick。呃。And oh， you are right， this will also check for availability。嗯。嗯。Ha。😔。

Do we really need to， or we do， don't we？😔，We have to。Drop the lock before we notify。嗯。Okay， so。Like。

 this is going to return to availability。 So now it， for example。

 if tick means that we got to send some。That can never happen great。

 so the availability cannot change because of this。Thank you。呃。Did you don't die on errors？If。

I guess if one connection terminates， it doesn't because of what happens in On tick。

 we might not want to just exit， but I'm not sure。So the question is what do we do in onT Well what we really want to do is we want to retransmit if there's something to retransmit。

 we want to send new data if there is new data to send。

 Of course you could also imagine that we want to do this proactively right。

 like if we see that we have data that we're allowed to send， we can just send it。What this means is。

When you close the connection， you might as well just call on tick。 and you'll see why in a second。

 So what on tick is going to do is it is going to decide if。It needs to send something。

It's going to send it。Basically all we have to do like the most of what the timers are is that。

 and in fact， if we look at the R of C。

![](img/49347db1b6244c3ae42b589040f18ec5_221.png)

嗯。ち to。All right， we're also supposed to enter F。呃。



![](img/49347db1b6244c3ae42b589040f18ec5_223.png)

We also need to figure out what to do about this， but that's a separate issue。



![](img/49347db1b6244c3ae42b589040f18ec5_225.png)

If in enter。

![](img/49347db1b6244c3ae42b589040f18ec5_227.png)

。But that's a question for later。 But there should be。

 I think there's a timeout to see what they call it。



![](img/49347db1b6244c3ae42b589040f18ec5_229.png)

User timeout。No， that's not what I want。I think there's another timeout。

That's the wrong kind of timeout。嗯。U。User timeout。😔，Segment arrives。 segment arrives。

 segment arrives。 segment arrives。Status call abort， call。 close call。Receive call。Send call。😔，Yeah。

 so this is what do you do when you're asked to write data？That's fine。Open， that's fine。Even。ま。

I specifically want retransmission timeout， those are really the only timeouts that matter to us。



![](img/49347db1b6244c3ae42b589040f18ec5_231.png)

Yeah， okay。So in onT， what we're going to do is see whether we're allowed to send stuff and if we are。

 then we should send it， if we're not allowed to send stuff。

 then we should check whether there's more stuff whether there's stuff that needs to be retransmitted。

So here， what we'll do is keep track of when we last sent data。So this is going to be last send。

Or I guess， lost。呃。As too less scent。 Lasts cent is good。And that's going to be a。

 do we have time imported here？So last send is going to be an instant。

How do you set up unit tests for this project， So unit tests for this project shouldn't actually be that hard because you can just。

 you could imagine that you just set up the are our TCP stack as a server and then use a standard net TCP client and see that they can talk to each other and then you do the same in the reverse the the biggest problem here is that in order to start a server or client。

 you need to spin up a ton tap， which requires。AParticular capability or route to access。

 and you don't really want to run your unit test as root。

So the other way to do this would be to test just the TCP stack so not actually use Tn tap。

And basically make our library be generic over the underlying transport so that it doesn't have to be a ton tap。

Like you could， you could basically test unit test this by just unit testing connection and constructing the packets right so that would be the the unit testing you would write The integration testing is a little bit harder just because of permissions。

The title just says Russ livestream。 Yeah， it's pretty unfortunate。 YouTube。

 it's really annoying to be changing the YouTube title when I when I upload the video later。

 it will have a more descriptive title。嗯。Okay， so we're going to have a last send。

 which is going to be time instant now。The chat bot is partially broken in the sense that I think people from Twitch can't see comments from YouTube and people from YouTube。

 I don't know whether you can see comments from Twitch。 I can see comments from both so。

At least there's that。 This was a problem last time， too。 And I don't know。

 I don't know what's causing it。 but I did see that I'm using re stream dot I O so I can stream to multiple places。

 And apparently， they're planning like a giant。Redo of their chat bot。

 so hopefully that will fix some of these issues。嗯。Okay， so what do we want to do here？ Well。

 we want to make sure that。嗯。We need to start actually maintaining our window。

 because that's what determines whether or not we're allowed to send something。 And in addition。

 we need to make sure that the sin and the f are also included in。呃。Included in retransmissions。

 right， so we might need to resend our sin Now maybe we just ignore that just because it's easier and it's not all that interesting。

 but certainly for data packets， we may need to retransmit them and we certainly will have to wait for the for the window to grow。

All right， so。呃。Where is。If self T P thin。Why does it have to do that？Pyload by8s。

Unwritten dot right。嗯。So this is probably wrong because this is going to update sendend dot next。

 which means it won't work for retransmissions， so that's something worth keeping in mind。嗯。

And we're going to have to figure out fins and such。 But for the time being。

 let's first just deal with what happens in on tick。



![](img/49347db1b6244c3ae42b589040f18ec5_233.png)

And we can deal with the other stuff later so。Where's our send。

So basically to decide whether or not we're allowed to send stuff。

We basically have to see that there's space in the window。呃。Where is the。Mmhmhmmm。Sn。

Do they actually document this test。Think so。That's the interface managing the window。😔，Mhm。

Or so currently we don't manage our window size at all， which is probably fine for the time being。嗯。

This we will certainly have to update and here I think this the other RFC we had gave a better estimation for how you compute this。

I think the first thing we're going to do is。Where is the appear somewhere。 Actually。

 let's go to the top。And look for。Data communication。

Center of data keeps track of the next sequence number to use in the variable send dot next。

 the receiver of data keeps track of the next sequence number to expect。

 and they will receive dot next。The center of the data keeps track of the oldest unacknowledged sequence number in the variable。

 S on a， right， So this is。So we have this like unacknowledged bytes Vec D Q， right。

 U is going to be the sequence number of the first byte in that。 and send dot next is going to be。

The next， the bites we are going to send next， if any。呃。Yeah。Great。Wheres the part about the window。

 though？That's fine。That's fine。 so we'll have to send empty packets every now and again just to make sure to keep alive the connection。

It's guarantee that when either TCB has a zero window。

 the reopening of the window will reliably be reported。嗯。Yep， that's fine。

Like certainly setting the window size and managing the windows is pretty tricky here。



![](img/49347db1b6244c3ae42b589040f18ec5_235.png)

呃。Things that we've already sent are self do。Send dot neck， I guess。呃。So。

Data that we have not even sent once yet is all the stuff that is in。Unact。

And that is at or beyond send dot next。Right， so let's draw this again because it'll be easier。



![](img/49347db1b6244c3ae42b589040f18ec5_237.png)

downown here。LetsDo this color。So our unact buffer。Logically。

I guess let's label these because it's helpful。For。My。是。7even。This， and when I draw the arrow here。

 I mean this element is byte。The sequence number of this byte is sender dot next。Sorry， no。

 that's false。Oh。The one thing that's annoying about this tool is erasing。嗯。stop raising。

 This is U and A， right， So unact。 the first unact sequence number is this one。

 the moment that something is act， we're going to remove it from the beginning of this of this array so that this imvariant always remains true。

Somewhere in here， we're going to have a pointer oops。For next。Right。And。

Next is the next bytes we are allowed to send。Sorry。

 that not allowed to send next is the next byte we want to send。

 so the next byte that we haven't sent previously。Now， there's also going to be something like。嗯。

This is going to be the。Send dot window。We think we should double check this。

 but I think it's the center window。It could be the receiver window， actually。Not。 No。

 I think it's the center window。 So this is how many bytes we're allowed to have outstanding。

When ontick is called， this is basically the variables it's allowed to look at， right？In this case。

 it should observe that。Currently， we are allowed to send these bytes。Right。

We're allowed to send these bytes because that would still keep us within the window。

So if we do send these bytes， then the unacknowledged byte is still one。

 and now send dot next is going to be here instead of here。And at this point。

 we can't send7 because7 is still outside the window。At some point， if we get in， if we get。嗯。

Ac is equal to， let's say， on Act plus 2。 then now。This is going to be unact。

These are going to be deleted， right？The window now allows us to send two more things。

 and so now we're allowed to send this。 and so we're going to put sendend dot next here。

And send those。So there's like a sliding window of about what data we're allowed to send。



![](img/49347db1b6244c3ae42b589040f18ec5_239.png)

So here， how are we going to do this？Well。Uncent。Is。还是一。呃。

Number of bytes sent is self dot send dot next。Wrapping sub。Self dot send。Dat。Unacknowledged。

Is that true？Hm。Ves。😔，Yes， that should be true。So this is the number of bytes that we have sent。

 but that have not been acknowledged。呃。Uncent is self dot un Act dot L minus an Act。

So these are bytes that we have not sent yet。I guess， as use。

These are the number of bytes we have not sent yet。At this point。

 we sort of have an option to decide what we want to do。

And it's going to depend on whether we're allowed to retransmit yet。

 if we're not supposed to retransmit。Then， so here， let's see。 self do， last send。Dot。



![](img/49347db1b6244c3ae42b589040f18ec5_241.png)

Ellappsed。I'mTrying to remember what retren。ちちち。Two minutes is recommended for the retransmission interval when the window is 0。

I want to see where they recommend how to set。😔，retrans， so。嗯h。Send window。 Yeah， Okay。

 so it is the send window。 The sequence numbers， which of the remote is willing to receive。

The range of new sequenceque， which may be emitted by TCB L between send dot next and send。

Unacknowledged， plus the window minus1。Yeah， great。

So this is the same that I showed in the drawing on the other one。嗯。

When the TCP transmits a segment to data puts a copy on the retransmission queue and starts a timer when the acknowledgecledment for that data is received。

 the segment is delete from the queue if the acknowledgecledment is not received before the timer runs out。

 the segment is retransmitted。The question is， what is the retransmission timer？

What should it be set to？😔，<|OTHER|>Tuplicly detect impressive retransmissions。Tin。😔。

So TCP also technically says that you should keep track of retransmissions times per packet you've sent rather than per byte。

 it's like if I send five bytes and then five more bytes if the retransmission timer expires for the first five bytes。

 I should just resend those， I shouldn't resend 10， even though potentially I can。

 so this is also something we may have to keep track of。嗯。T transmitted。But what is the time？

Here we go， read transmission time up。Because of the variability of the networks that compose an network system and the wide range of uses that these being mentioned the retransmission timeout must be dynamically determined。

 one procedure for determining a retransmission time out for determining a retransmission timeout is given here as an illustration。

There is probably a better way to compute this。 I'm pretty sure I've seen this， in fact。

Measure the elapsed time between sending a dataoctet with a particular sequence number and receiving an acknowledgecgment that covers that sequence number。

The measure ellappse time is the round trip time。I see。

So the recommendation here is basically estimate what the R TT is the round trip time is。

 and then keep sort of a moving average of the estimated round trip time and then the round trip time is going to be。

Some multiple of that RTT。嗯。

![](img/49347db1b6244c3ae42b589040f18ec5_243.png)

Okay。

![](img/49347db1b6244c3ae42b589040f18ec5_245.png)

So they want that to be。

![](img/49347db1b6244c3ae42b589040f18ec5_247.png)

S， R TT。M。We're going to figure out。 So this means that we need to keep track of when we send each by and when that bite was acted。

Its basicallyically what they're telling us to do。 We probably don't want to keep track of every single byte。

 but instead every like every time we every， basically， every time we send something。

 we should keep track of the sequence number and when we sent it so that we can update the。

The time out appropriately。 So let's go up。 This means that we're not going have to keep a little bit more data here。

Specifically， on the connection。On the connection。Let's。Start another。A timers。

It going to be a timer st。St timers。It's going to have a last send。 It's going to have a。Ha。😔。

It's going to have something like。Since。Or send times。Which is going to be， let's say， a V Dq of。

A particular sequence number。And a particular。 And when that sequence number was sent。Right。

 so every time we send an send a sequence number， we stick it into send times。 And when it gets act。

 then we take the difference between。嗯。We take the difference between when we sent it and the current time。

 and that is an estimate of the R TD。And then we do SRTT is a time duration。



![](img/49347db1b6244c3ae42b589040f18ec5_249.png)

![](img/49347db1b6244c3ae42b589040f18ec5_250.png)

Great。😊，So。This is going to be timers， which is going to be a new timers with last cent equal to that with a send times is a empty one of these。

And where。S， RRTT is。Time， duration。From minutes。Qiu。Oh what is it then。From。I guess，6，2 times 60。

If self thought lasts send。

![](img/49347db1b6244c3ae42b589040f18ec5_252.png)

Dot elapsed is more than。And what did we want this to be， The retransmission timeout is。



![](img/49347db1b6244c3ae42b589040f18ec5_254.png)

Ubon is an upper bound on the timeud， for example， one minute。Okay， so not two minutes。One minute。



![](img/49347db1b6244c3ae42b589040f18ec5_256.png)

Theres more than。

![](img/49347db1b6244c3ae42b589040f18ec5_258.png)

I see they want a lower bound and an upper bound。So， this is。呃。Waied for， is this。If waiteded for。

Is greater than。One second。And waited for。Is less than。



![](img/49347db1b6244c3ae42b589040f18ec5_260.png)

啊。Self timers。The smoothed R TT。Times beta。

![](img/49347db1b6244c3ae42b589040f18ec5_262.png)

I guess。1。5。Because magic numbers are great。呃。So in this case。

 we've waited for what we believe the timeout should be。

 and so at this point we should retransmit things。Otherwise。

We should send new data if we have new data and space in the window。So here we really。

If we're going to retransmit things， the question becomes what do we retransmit Well， we retransmit。

 this is where technically the TCB protocol probably wants us to only retransmit the the the packet that has timed out rather than as much as we can。

 but instead what we're going to do is we're just going to send as much as we're allowed to retransmit。

嗯。So what that means is we're going to do something like。Self dot right， of course。

 self dot right is broken。 We know that it doesn't work for retransmits。

 but that's something we're going to have to fix。 And that takes the ni。 and it's going to take。

I guess。Allow is going to be self dot send dot window。



![](img/49347db1b6244c3ae42b589040f18ec5_264.png)

Right， what was the。What was the computation here for how much we were allowed to send。

🎼Managing the window。Send window， or is it。We're allowed to send from。



![](img/49347db1b6244c3ae42b589040f18ec5_266.png)

This。Self dot send dot window。hich means we don't really need it。

 So here we're going to write everything。From we're gonna retransmit everything from self dot unact。

That's also not going to work。😔，But let's look at that in a second， everything。This many bites。

RightSo we're going to send basically， we're going because we're retransmiting。

 we're just going to retransmit as much as we possibly can。And that might include some new data。

 right？ And then at this point， self dot send dot next is going to become self dot send dot。Un act。

Wappping a。Self dot send dot window。Sort of this code is still a little bit inaccurate。

 but does the rough idea make sense？We're supposed to， we're supposed to do retransmissions。

 We just send basically the full window again。 We could be more conservative here。 But instead。

 we're just gonna。We might actually hear when aend like only as much as willll fit in a TCP packet。

 for example， but that's not currently what we're doing。And then now self。tsend dot next。Will be。

Actually， that's not even true。Seelto sendal next should now point to the next byte that we want to send。

 although this might not actually be accurate， but we'll get， we'll get back to this code。

 Theres more to lay out the the rough structure。 what it's going to do here。If unent is zero。

 then we don't actually have anything to do。Right， if we don't have any bytes that haven't been sent and there's nothing to retransmit。

 there's nothing for us to do。 There's nothing for us to send here so we can just return okay。

Otherwise。We should just send out as many bytes as we are allowed to send。Right。

 so how many bytes are we allowed to send？ Well， we're allowed to send self dot send dot window minus。

嗯。那是以。Minus。😔，An un act。Right？And if a allowed equals 0。Then what do we do well。

We can't send any data， can't we？嗯。Right like if if the window allows us to send like if the number of unacted bytes we have are the full window that we're not allowed to send any more bytes。

 we need to wait for the window to open up。 and so in that case。

 we can't do anything and we are not supposed to retransmit， so we do nothing。

Only in this final case are we allowed to send some bites。

 So here we're allowed to write out to the ni。呃。Self dot unact。呃。From。From an un act。Qiu。😔。

And an act。Plus。All。Now， the observant among you might notice that like there are some out of bound conditions here that are going to be annoying to deal with。

 but that we will actually have to deal with。Oh， we just got a lot of people claiming。

That there's PhP。 none of this is PhHP。 If you are saying PhP， you're in the wrong channel。嗯。Right。

 so in this case， we are allowed to send stuff and we do have some stuff to send。

 And so in that case， we just write out as much as we're allowed to send。And at this point。

 self dot send dot next is。Self dot， sand dot。Unact plus sort of。Plus。Actually， know。

 it's not even that it is self to send out next plus alo。Sort of。um。My VRC is public。 There' is。

 in fact， a previous stream where I go through my entire like editor setup and stuff。

 So if you search for that， you'll find it。O。And we have to do with fins that's sort of separate。

So let's actually now tidy this up a little if we need to retransmit。

 what do we actually get to retransmit well？We get to retransmit up to the window。

 We might want to have a lower limit， but because this is a we're only going to be sending small things regardless。

 it might not matter all that much， and we might get like IP segmentation and stuff， which is nice。嗯。

So， here。Right， remember， unact might not have enough stuff to fill a window。 So send is gonna be。

 or I guess。Resend is going to be。The min of self do unact dot L and the self send window。

And that's how much we're going to send。Let's also fix right while we're at it。So， right。

What is unwritten here。1500。A great。So it will only write out at most 1，500 bytes， so that's great。

This is not quite right， the updating of send dot next。Is not actually right。

Because it might be a retransmission， right？Now， how do we want to deal with that， though。H。We could。

 of course， update self sendend out next in every call。嗯。

But we do call right in a decent number of places。Right。嗯。😊，The sequence number， of course。

 is also not necessarily send out next。Inner retransmission。

Maybe the trick here is going to be giving in the sequence number of the first thing。🤢。

Then I think we can write properly。So the sequence number is not going be self dot send dot next。

The sequence number is going to be whatever the initial sequence number is。

The acknowledgegment number is correct。呃。And now this can actually update self sent next。

Because self send next is going to be。嗯。Let's see。 Let。Last sec is。Second。Wrapping a。Well， this。

 really。Minus1。Next segment。If next sec。啊。Not quite。And， of course， if it includes a。

If it includes a sin， then we wrote one more byte， if it includes a f， we wrote one more byte。um。

This， this is going to come back to bite us because these aren't actually true。うん。😊。

Actually you know that is true。It just resets the flag at the end。Probably fine。

I think what we want here is。Okay， let's ignore that for now。

 but we only want to update send dot next if we actually have bumped send dot next。 So in this case。

 if next sec is I guess if。Wrapping less than。Self send next。So if that's less than next sec。Then。

Next is next sec。So this means that in the case of a retransmission。

 we won't update send dot next to be less to be like whatever the last thing we retransmit was。

 we would just leave it alone。 So the idea here is that sex is the sequence number of the first thing in payload or potentially in sin really。

嗯。Like including counting the sin is a different way to phrase it。嗯。Yes。Gui。Okay。

 so now this is going to have to decide。What to do。 So here， this is going to be self send next。

That's false。See send next， right， so when we send the initial sin to establish the connection。

Our first sequence number is going to be whatever we decided the initial sequence number was going to be。

Where else do we call right here？Same thing。Self and next。

 but for all of the all of the ones that were there already。

 they already assumed this to be the case。And they send no bites， so that's fine。呃。Where else。

So this is sending an act， in theory， this could like also include sending data。嗯。

So we could make this just be tick。For example。Maybe just tick to。Pigyback act on data。呃。

This is well， self send next。Because it's sending the sequence number here is the sequence number of。

Just past the fin。This does mean that we don't have a way to retransmit the fins。

 so we'll have to deal with that later。What this doesard and let us do though is in the case of our retransmission。

 this is self dot send dot on a right， that is the sequence number of the first thing in an act。

How this interacts with sins we'll have to look at and down here is's the same thing。No。

 that's not true。Here it is， in fact。Send next。Yeah， so the。

It should be the case that self send next points to the first bite in an act that we have not sent yet。

And here， the bytes we want to send is。The min of。Uncent and allowed。

How do you like rust compared to PhHP， They are very different languages， I highly prefer rust。

PHP is a very dynamic language。Which is and it's nice for simple web setups。

I used to program aoting PhP， I don't think I would use it for anything anymore。嗯。嗯。Right， so here。

right， so this should now work for retransmissions。That's great。On a right。

 So when we first start sticking stuff in， oh， right， we haven't added anything to write yet。Great。

So now if we look at Lib， what actually happens when we try to do it right？What do we do here， Oh。

 I guess we're not actually dealing with rights yet。 We're mostly just looking at shutdown。

 At least that was our initial intention。嗯。So for now， we're actually going to assume that。

We're going to assume that there are never any bytes tocent。

 We just want to get shut down to work first。Which means that the only thing we could be asked to retransmit is the f。

Or asked to transmit is the fin。嗯。The question is， how are we going to deal with retransmiing the f because it's not in an act？

So we need to keep track of whether or not we have sent the fin。Which we know， because。Oh。

 interesting。嗯。爸叭叭叭爸。So。We have a couple of pieces of information here， right。

 We have self dot closed， which is。Has shut down been called。But we also have self dot state。嗯。

And self do state can be one of these。Which indicate that we have sent the f。



![](img/49347db1b6244c3ae42b589040f18ec5_268.png)

So if we go back to our diagram。嗯。When we send a fin， we end up in Fin weight 1。

If we have sent a fin， we're in Fin weight2 or closing or time weight。

 So in any of the states from Fin weight1 and down， in all of those cases， we have sent the fin。



![](img/49347db1b6244c3ae42b589040f18ec5_270.png)

Right。And so we actually know whether or not， I guess，oo。Let's add a thing here。Have sent Finnin。



![](img/49347db1b6244c3ae42b589040f18ec5_272.png)

![](img/49347db1b6244c3ae42b589040f18ec5_273.png)

So that is。Andうん。Let's see。 in state soon received or established。

 we have not sent it yet in Finway 1， Finway 2 and time weight， we have sent it。



![](img/49347db1b6244c3ae42b589040f18ec5_275.png)

![](img/49347db1b6244c3ae42b589040f18ec5_276.png)

So。In theory， we should be able to use that to determine whether we're resending a fin or not。Yeah。

So let's see。So these are the bytes we're going to resend。And。



![](img/49347db1b6244c3ae42b589040f18ec5_278.png)

Oh， wait， did it say。actually， I don't think that's true。Thinking back to。

Thinking back to what it said on clothes， I think it said enter Fin weight 1， regardless。Like。

 no matter whether or not you can send the fin。Close。So close and established。😔，Yeah， in any case。

 enter Finw  one。

![](img/49347db1b6244c3ae42b589040f18ec5_280.png)

So， it's actually not sufficient。We need to have a separate mechanism for determining whether we have or have not said the Finn。

嗯。Because there also has to be like an if here， right of。Like if。Need to resend。Fin。

Or I guess this is really just。Is the f within the window。 That's really all we care about here。So。

 if。嗯。If weend。Is less than， I guess this is a。No， this is not that if weend。Is less than the window。

And self closed。Then。We also set the fin。Inc the fin。Or I guess can we include the fin？

RightSo resend is how many bytes we're going to send out。 that might be0。 In fact， in our case。

 it will always be0。And if， if the window has space for us sending the fin。

And we're supposed to send the fin。 Then we send the fin。And。If un sent。0， right， So this is tricky。

 So here we need to know。Whether we have already sent the f。Because if we haven't。

 we should send the packet if we can。Specifically， we should send the fin if we can。嗯。Interesting。So。

 so one way to do this would be and nod itself closed。嗯。But unfortunately。

 the downside of doing this is that。This will send the fin again， each time。

Which is not actually true because it's not correct because the f should not get like there aren't multiple fins。

 which this would imply。嗯。So I think we may actually need。To keep track of。

Essentially the last sequence number， like the， here's what we could do。

 We could keep track of what the sequence number of the fin is。

So that would be up here in connection。I guess we could do。Cl。It's a little awkward。

 but we can do it this way。Right， so。Close to add is going to keep track of the sequence number we used for the Fin if we have sent it。

So here this is going to be closed at is none。Because initially we haven't closed it at all。呃。

So if there's no data to send and we have close the connection。OrAnd we've sent the f。

 then we have nothing to do。呃， if。Send is less than allowed， and self dot closed。

And self closed at is none。 So this is， if we're allowed to send more than what we're already sending。

And we're supposed to send the fin。 And we have not yet sent the fin。 Then we send the fin。嗯。

And in this case， closed at is going to be set to。Self do。Send dot next。Wrapping ads。A。Unent。

That's where we ended up sending the fin。Because no more data is allowed to be written once we've closed right so the actual structure of this is the bytes in uncent are followed by the f and so self send dot next is before these things are un sent so plus uncent is after those and that's where the sequence number of the fin will be。

Great。I think that's right。Think that's right。I mean， it's probably broken， but you know。嗯。

There's also moving to Finw one。So the old hockey code that we had was this business。

So this set Finn to true。嗯。Hm。It moved us to Finw 1。So that means that that is something that。

Shut down is going have to do。Right， it's gonna do this。



![](img/49347db1b6244c3ae42b589040f18ec5_282.png)

Close true state Finway 1。 And from memory， this was what closest was supposed to do， right？



![](img/49347db1b6244c3ae42b589040f18ec5_284.png)

Technically， we should check here for。嗯。Check for it。That。



![](img/49347db1b6244c3ae42b589040f18ec5_286.png)

呃嗯。As long as the second Finn is not omitted， nope， thats not， we don't do that。



![](img/49347db1b6244c3ae42b589040f18ec5_288.png)

I guess this should really just be if COt state。Is equal to state established or established。

 I guess。If。嗯。

![](img/49347db1b6244c3ae42b589040f18ec5_290.png)

State。

![](img/49347db1b6244c3ae42b589040f18ec5_292.png)

嗯。Do we even have that state？Yeah， soon received。

![](img/49347db1b6244c3ae42b589040f18ec5_294.png)

If no send has been issued， there is no pending data to send the form of segment and send it。



![](img/49347db1b6244c3ae42b589040f18ec5_296.png)

Oh， actually， no， we don't even， that's also fine。We actually I think we probably just want to do this。

 So if we're in state soon received。Or were in state established。Then we move to Finwa。呃。

And if we're in any other state。

![](img/49347db1b6244c3ae42b589040f18ec5_298.png)

What other states could we be in。

![](img/49347db1b6244c3ae42b589040f18ec5_300.png)

Close weight and close weight is also fine， but also we don't support that state。



![](img/49347db1b6244c3ae42b589040f18ec5_302.png)

So soon received and established Fin weight1。Is also fine for us to do this and time weight would be an error。



![](img/49347db1b6244c3ae42b589040f18ec5_304.png)

So F weight 1 and Fin weight 2 are both fine。 In all cases， we move to。Well。Actually， in the others。

 it doesn't matter。If we're in these， nothing needs to happen。 and if you're in any other state。

 then we really want to return。An error。On the form of。New。



![](img/49347db1b6244c3ae42b589040f18ec5_306.png)

Our kind， who knows？

![](img/49347db1b6244c3ae42b589040f18ec5_308.png)

Error closing。Is that an error kind I can use。嗯。Unclear， actually。😔，Still connection of。Pored。

Might not be the right one， but。嗯。Closing。Actually， maybe this is already documented in shutdown。

What does DCCP streamream shutdown say？嗯。The second call， not connected。 Okay， that's fine。

So shutdown is just going to set up the state to be right。

 and then the tick is going to take care of actually sending out the fin。

Is the goal to create as an exercise part of a TCP stack that you will use instead of the inbut kernel one sort of。

 So， I mean， what we're doing is really just。Building a TCP stack because it's an interesting way to learn low level programming and because you learn TCP in the process。

 I don't my goal is not to use this for anything。 It is more as sort of an educational experience。U。

But of course， the goal is that it actually works。 and in fact。

 it does work for reads now and hopefully with this change， it should work for rights soon too。

We'll see whether that turns out to be true or not。That is a lot of errors。

And they're probably all because of my stupidity。嗯。M should be。Hims。Of。

 there's a bunch of stuff we don't maintain here， either。嗯。Not add。嗯。

Conversion between numeric types。Ignore back off getpe， That's not quite how it works。So this is。

This is the third video in a series so if you want to learn about the underlying like setup for how how we're doing this in the first place。

 you should go back to you should go watch the first video in the series which is on YouTube so I would watch these actually in sequence I won't actually go back to explain how the earlier parts work in this video because it's already explained in the earlier video。

嗯。Expected slice found you。that's a separate issue。Alright， let's see here。Oh。

 it doesn't have the state， does it？I think this is going to have to do the C close。

And then we're going to have to in here。Add in a close。I result this。It's gonna do。So。Solf， self。

Great。68。Why。Don't manage。Connections。嗯。2，68。Hm。I guess。RTO is going to be。Duration from。No。Yeah。

 from nanoos。Actually。That's annoying problem we have to do arithmetic on time。

 which is kind of awkward。um。P U 32， found U 16。Yeah。Oh， that's a good point。

 I can add stuff to my twitch。 It's a good use。 I add links to the other things。 It's a good point。嗯。

Expected U size found range 2。 so here's the other problem we have， which is。

 remember how un unact is a ring buffer。You can't index a ring buffer like this because the ring buffer is really two。

 two segments， right？The sort of head segment and the tail segment potentially。

So the real question is， how do we want to do this？嗯。Oh， this should say resend。嗯。This also asked。

Sid。Clse that。So the question is， how do we want to break up this right？嗯。

I think actually what we're going to do here is have right。Support taking。😔，Two buffers and a length。

Yeah， that's what we're going to do so there's going to be。Paload1。Pload 2。And Ly。And then。

 we're going do。Unwritten right。Paload。Payload。Wen。Da dot Le。Wells。僕？嗯。

We want to make sure it doesn't write more than we're allowed to write because of the window。

 for example， right？So here， what we want to do is we want to write。From payload1。

 as many biases we're allowed to or that's there。 And then we want to continue writing from payload2 if we're allowed to。

嗯。Which I think means that we're going to have to do something along the lines of。First。

 write as much as we can from payload1。呃。嗯。Which is going to be。Min。Of。Len and payload 1 dot L plus。

Paload。2 dot L。And then， we're gonna do。Pwenlin。And to feed the men of these。

We're going to write out。written。So， written plus equals this。Dot， dot P1 L。And then。

Len minus equals。He wantna know。Sorry， I'm going to explain this once I've written it just to make sure I actually。

Understand it， myself。呃。去。Yeah。Okay。Then， write。OrIf we can。2。All right， so the idea here is。

We can write out。Whichever is less of how much data there is and how much we're allowed to write。

So that's now going to be lead。So the question first becomes。

 how much can we write out of payload one while we can write？

Whichever is less of how long paled one is and what our limit is。

So maybe we should call this limit instead of L。It's to limit。It's a better name for it anyway。嗯。

Okay， so we write out some stuff from payload1 as much as we can basically。

 now the limit is decreased by however much we ended up reading from payload one right So if we wrote。

So it can't even be that this has to be written。So now。U。Once we write some stuff from Ped 1。Now。

 the limit has been reduced by however much we wrote to payload1。Right。

Now we try to write more from payload2。So there are sort of three cases here。

 either we exhausted payload one or other two cases。

 either we exhausted payload one and there's more room or we did not exhaust payload one because we used up the limit。

If we used up the limit， then the limit here is going to be zero。And so this is going to be zero。

 and so we're going to read zero bytes from payload2。If we read some bytes from Paload 2。

 and now we're going to continue writing。sorry from payload 1。

 Now we're going to continue reading from payload 2。

 The amount we're going to read from payload 2 is however much of the remaining limit is or payload 2's length。

 whichever is smaller。 So we write that out as well。

 And the result is we wrote this many bytes out from the two payloads。Okay。Great。What is this？Right。

I guess this is like。Max data。So what is size here size is。😔，How many bitetes are there in a packet？

It certainly can't be more。Then the length of the packet。But it could be less。

 in which case it's the TCP header， the I P header and。As much data as we can write as we have。Yes。嗯。

Let's see。 it can unwritten dot right end up writing fewer bytes。 than you ask it。 Yes。

 this is why I do limit minus equals written。Rather than limit minus equals P1 L。

So I think this is still correct， like unwritten upright can end up writing fewer than P1L bytes。

 right because it could be hitting the limit of buff， which is of limited size or limit of unwritten。

 which is buff。嗯。So that is why the limit is decreased by how many bytes were actually written out。

And if we then try to write on more bytes here， unwritten would still then say I wrote zero more bytes。

 so I still think this ends up being right。嗯。Okay。What now fails？Lots of things， great。1，9，3。Right。

 so now this is going to be。Yes。Of course， now all of these have to。Include more stuff in them。

 which is a little annoying。But。It's worth the cost， because。Now。Where is it？Here。We can now do。呃。

Headtail is self unaced。Dot who。Where is the place where we get the head H tail？As slices。Ass slices。

And then we can do H T reend。So this will write first from H then from T and no more than resend。

Which was what we wanted in the first place。嗯。And the same is going to be the case here where this is going to be。

后来。H T。Self unact as slices。Oh。Except here， we have to skip forward by an un act。

Which is also going to be a bit of a pain。We want self dot unact。And unact。So。

So we actually need to mutate these to skip。Which is。if。呃。It's writing to， yeah。

 it's in it's writing to an in memorymory buffer。That will only later write to the actual output。

 yep。That's right。So that's why I think it's okay。If， if it wrote directly to the output。

 you're right， then it could write too much。嗯。All right， so。Here we need to。Basically。

 remove stuff from the beginning of H and T all the way up to N unact。 So if。Hdot L。

Is greater than or equal to N unact。No。呃。Well， actually， let's write out the verbose version first。

 then H is equal to。H。呃。And un act dot， dot。 And T is T remains the same because we just trimmed off that many things from H otherwise。

呃。Skipped is equal to H dot L。H is equal to an empty1。And T should be equal to T。An un act。

Minus ski dot dot。And this can probably be。Simplified somehow。But I'm not going to bother。

 right so here。Let's draw again。

![](img/49347db1b6244c3ae42b589040f18ec5_310.png)

Because this is a little bit weird。So。All right， so we have our ring buffer again。Actually， that。

 I don't want。one。So we have a ring buffer。And let's say that the。This is the head。And this is the。

Tail。Let's actually write these out。嗯。So this is  one，2。3 and 4。So with this setup， let's say that N。

Un act。Is。3e。RightSo what that means is we really want this slice because we want to skip three if we're going to send only the stuff that's new。

 only the four here is new。All the other stuff is stuff that we've sent in the past。

 so we only want to send for。So the question becomes， how do we get a like when we do dot as slices？

Right， then what we get back is。A reference to1，2。And a reference to 3，4。

Where this is H and this is T。And we want to turn that into。H is nothing。And T is4。

That's what we want to end up with， right？

![](img/49347db1b6244c3ae42b589040f18ec5_312.png)

And so the way we do that， if we， if we look at the code we just wrote is if Ht L is greater than equal to unact。

 So if。

![](img/49347db1b6244c3ae42b589040f18ec5_314.png)

Is let's say un Act was one， right？ So if un act was one。If an act was one。

 then all we have to do is skip the first one elements from head， right。

 and leave tail the way it was， which is what this does， right？

 H is just set to be skipping and un act from H。 and T is left unknown otherwise。



![](img/49347db1b6244c3ae42b589040f18ec5_316.png)

![](img/49347db1b6244c3ae42b589040f18ec5_317.png)

Head is going to be empty， right， So if N on act is greater than the length of head。

 then head is going to be empty， no matter what we always need to skip these。And so in that case。

 we're going to set。Skpped is equal to 2。So we skipped these two。



![](img/49347db1b6244c3ae42b589040f18ec5_319.png)

Right。So that's here。 Head is going to be empty， and T is going to be。Skipping， however。

 we have left that we need to skip。 So N and act was 3， Spped was2。

 So sort of left like how many are left is one。 So that is this one。

 So we're going to skip this one as well。 And so T is going to be。



![](img/49347db1b6244c3ae42b589040f18ec5_321.png)

![](img/49347db1b6244c3ae42b589040f18ec5_322.png)

![](img/49347db1b6244c3ae42b589040f18ec5_323.png)

Starting from one and onwards， which is starting from here and onwards， which is4。



![](img/49347db1b6244c3ae42b589040f18ec5_325.png)

All right。And with that， it should be possible for us to pass H T and send。

Because send is sort of how many bytes we are allowed to send。嗯。Yes， I think that's right。

289 is the multiplying time which we're going to ignore for now。298。Recent expected U size found U32。

呃。It's probably fine for this to be a U 32， to be honest。But it'll be easier if it's a use size。嗯。

So let's just make it B aU size。This should。Not need to do any of that anymore。

Because the first bitete here。Is the first bite of unact whose。

Sequence number is the unact sequence number。呃。289。 That's still the timer。

Mismatch type expected results。😔，呃。Hm。We're certainly going to need to。

We're going to need to maintain these like last send stuff as well。

 and those are going to have to be updated here。🤢，That's not what I'm meant to do。

So here this has to return OK in the end。We， we have to figure out what to do about these timers， so。

When do we it might be the last sentence is not sufficient。Because we might have to keep track of。

Last send for yeah， it's going to be a little awkward。

I think we have to keep track of every send because imagine that you do asend and then later on it gets act。

 what is now your last send？Right， so I think you actually need to keep track of。

When you send every packet。嗯。Does that and that has to be updated when you when you retransmit。Hm。

Yes， I think the trick， I know what we going to have to do we're going to have to make。啊。是。

I think what this is going to end up being is a B tree map。From sequence number。To when it was sent。

Because we can use the B tree map to look for all the sequence numbers before or after。Of course。

 this gets weird with rapping arithmetic， but we can figure that out。

We're also going to have to figure out what to do here in order to estimate the RTT because we don't want to use retransmissions to estimate the RTT only the original sends right。

 otherwise like if I resend a thing five times that doesn't mean that the RTT is5 times as high。

 so I only really want to count RTTs for。From the。From things I didn't have to retransmit。

Because I also don't want to do it。 have it be the last send because imagine that I send something。

 The retransmit timeout expires， so I send again。 but the first one actually arrived。

 It just arrived a little bit late。 So the other side sends me an act that I receive immediately after the second send。

 If I use the second send is when I send the thing that was now act。

 then my estimate of the R TT is going to be very small， which is also wrong。

I don't know how real implementations handle this。What do they use for the estimation。

 It's probably a lot of my guess would be there's a lot of research in estimating R TDs。

 I think it's just hard。W whichhich means it's fine if we do a bad job of it。In fact。

 we're probably going to do something stupid， which is great。Okay。

 so we really need to maintain this send times business。It says seven times。

And I think what we're going to do there is。呃。Is down here。Whenever we write something out。

 we're going to do self sometimes。In search。呃。The first sequence number。And time instant now。

So every time we send any packet， we store the sequence number we sent in that packet。

 the first sequence number we sent in that packet， and the time when we sent it。

And then what we'll do later is in the code that deals with when things have been act， there。

 we can then sort of walk， send times and use that to update the R TT。

And now because we do this in right， it means we don't have to update all the places that call that send packets。

 we can just do it here。Of course， this might have some problem when we send resets and such。

 but we can probably just ignore that。呃。It does mean that waiteded for is a little weird。U。

I think this is going to be like the minimum。Yeah。This is going to be。Send dot values dot min dot。Y。

Right， so this is。actually no。M。Thanks for that。妈。Ti Gpsed。And we want a max。So this is what is the。

What is the longest we've waited for anything that we've sent？Although that's weird， too。

I think it should only be for the currently un Act。I think what we're really going to do here is。um。

What's the interface on B3 map for like next higher value。 It's like a range thing。

What do they call it。It not never what I want。There's a range， that's what I want。😔。

So I want send times range。And I want self send unact dot dot。Dot next。The map。Time instant elapsed。

So that is， how long is it since。We sent。The last thing that is not an act。

It's a little bit weird of a sentence， but this is like， find the。呃。

Find when we sent the earliest unacted things and see how long it is since we sent that。Yes。

And if the time that has expired there is more than the timeout then retransmit。

And if I guess this is like。How do we want to do this conditional， though？

This is like lead should retransmit。So we should retransmit if。Waited for。Is some。

I guess we could even do。If let some。Or is waited for。呃。If。If there is no such timer。

 like if we have no running retransmission timers， then of course we shouldn't retransmit。

Because there shouldn't be anything to retransit。 Otherwise， we should do it if。

Waied for is greater than one second。Right， so this is the lower bound。And。Waited for。嗯。

Dot as float sex。So asphpho X gives you the duration in floating point seconds。So this like seconds。

 but with decimal points。Is more than 1。5 times self timers S T T as float seconds。

If should retransmit。Then we should retransmit things。And here。Can we include the fin。

 then self closed at。 is it going to be sum， What is it going to be。

 What is the sequence number of the fin， Well， it is self dot。呃。It is the start of。

The unacknowledged buffer plus the length of the unacted buffer。Yeah。

 that is the sequence number of the pin。Which I think is the same as down here， I hope， maybe。

It is not， but that's not terribly me。Surprising。Sort of want an assertion here to check that these are the same。

I feel like this should actually be the same。So let's down here do like。She， no。

 we can just make it be this， right， because the fin just should always be that。

The start of the unacknowledged window。PlusPlus the length of bytes that are in that window should just always be the f。

 down to fewer errors。We need to import BreM that is luckily pretty easy。Timers。Sometimes。82。

Not fine。TT eappsed。Really。Oh， as sex float。Now， what's it called？Duration。What is it called。

 it is called。Oh man， stop with that。啊。Nly。Or am I on， I don't if you remember what I'm on here？啊。

Pson。背的。So I guess some beta。And on beta， it is called what exactly？It's called。As sex F64。

Which means it's not going to compile because it's a feature， right？Probably。Yeah。

Override said Knightly。 That's too bad。Pretty annoying。So we're going to have to do feature。Right。

292。O。Sure。306， more numeric conversion。This， of course， needs to be。Wrapping ads。As does this。

Which also means it has to be SU 32。Probably。3，1，6。That's fine。321。

Nummerical conversions are the most fun。嗯。So。Oh， getting pretty close。Expected U size found U 32。

Great。Now we just need to fix the borrow checker。72。So why is this complaining。

 this is complaining because。Can a connection is mutable。Values， mute。Try that。

Variable does not need to be mutable，107。Okay。2，52。44。That does get reassigned， That is true。309。Oh。

 that's awkward。I'm borrowing into self unacted。Whi means that I can't call self right。

That's pretty annoying。That we can't actually fix that easily。嗯。It could be that。That self dot right。

Should just always read from self。 an act。Rather than us like passing it in everywhere。

Like we give we give a start and an end。Instead of giving those slices。Because currently here， right。

 like H and T are borrowing self unact， but self out right needs to borrow self mutably。

 which it can't do。I think we're just going to do here zero。And then down here， we're going to do。

And unact。As you size。And now right is going to change a little bit。It's going to change to be。

Instead of taking payload1 and payload2， it's going to take。Start use size， limit use size。

 I guess offset。嗯。And we're going to say let mute H。T is self unacted as slices。Offset。Then， offset。

Offet， let skip。And then now this is gonna be H。T。These are all going to be H。Qi。Oops。

All right see how that works。And now anywhere the calls right。It's now just going to do this。

Although。Of course， now we have a。Problem here。 Oh， no， as long as you at limit to 0。

 is's not going to send any bytes anyway。 Great， even better。

So it doesn't matter that it's using an act behind the scenes。0ero。

 zero is always send no data anyway。Hey， how about now？Great。

How much faith do we have that this will actually work on the first try。I'm skeptical。Let's see。

 Oh I just rebuildbuilt off。Well， it didn't crash immediately。It still got data。

AndThen it crashed an on tick， which called right。Well。

 that's better than I thought it was going to be。I guess actually。We sort of， we might as well have。

Close call， self dot on take。It can't do that， doesn't have the in。That's fine。呃。Okay。

So right is failing somewhere。Slice index starts at one but ends at zero。

It sounds an awful lot like Finn。嗯。In fact。Because right knows the sequence number。

 in theory it can compute the offset。I don't think it needs to take the offset。Right， because。Here。😔。

Self dot send dot next should just be pointing to。The end of an act。Here。😔。

We want to send from the start of an Act。Which is0。Here we want to send from。Next。Which is。

Unact plus number of un Act。Here we want to send from next。From next， from next， okay， great。

So we don't actually need to take the offset。Instead， the offset is going to be。Self dot， send dot。

Next。Wping of self。Right。No， sorry。See。Because that is the starting。

 so the sequence number of the starting byte。And we subtract the unacknowledged index。

 which means if you're starting to send from the start of one Act。

 this will turn0 and the offset is 0， otherwise its going to be some larger value。

Which means that anywhere that calls right does not need to give this argument。

This starts to to unact。Which wrapping sub。An act is just the same。Yep。This。Starts from。Next。嗯。

Although。Next here could be pointing to after the fin。These could both be pointing to after the fin。

In which case right would crash because it's trying to look up past the end of an act。

This does not need this。This does not need this。I need this and this。Does not need that。

So here we're going to have to look at。If。呃。嗯。I mean， what do we want to do here。

 we sort of want to observe that。we need to handle the f somehow。

This will also have a problem with the。With the sin， I think。We need to special case。

The two virtual bites。Sin and fit。So。Let's make the。Offset and the limit， both be mutable。Actuallyly。

 the limit doesn't need to be， but the offset does。

Because we never read past the end of the input stream regardless。But we do need to return it。

Just leaving it to do for myself for later。Z。If the sequence number is。

If the sequence number is the sequence number of。嗯。It's a good question。

So we have two sort of special cases， we have the sequence number is equal to the sequence number of the sin。

 in which case we need to like shift it one right。Although I don't think that can ever happen。🤢，No。😔。

That would only happen if you retransmit a sin， which should not happen。

So the real issue here is if the sequence number is equal to the sequence number of f because it'll be off by one。

And so therefore。If。嗯。If we have the。Sequence number。Of the fin。And if。This sequence number。

Is that sequence number？呃。Plus one。Then c minus equals one。No， then。Offset minus equals one， no then。

Equs 0。Right so this is。If we're， if we're being asked to send bys starting at after the thin。

Then we need to set the offset to zero， where we should not be reading any data。

Or another way to say this is。Here。😔，Although that's also just annoying。嗯。

I to see whether that does the right thing now， of course， it doesn't。If I do this。

 what happens so it crashes where。It's so unhelpful that I don't get the line number here。All right。

 it's time for some print debugging。Right from。I guess， C。Limit。From。So seek。Limit。呃。Yourself。On。

As slices。And then I also want to print out here。嗯。Using offset。But。All right， so what do we get？

Right， sequence zero， limit zero。From there， that's fine。So that's writing out the initial sin。

Write sequence1 limit 0 from there。This is writing out the fin。 let's print some more stats like。嗯。

This is sell TCP Finn。Yes。S。And then let's not do that here， but do that here instead。Inで。All right。

 what do we get？So first， we write out the sin at sequence number 0。 Great。

 Then we write out the thin at sequence number one。And the question becomes。

 what happens at sequence 2？Where sinness falls and sinness falses。So when that happens。

 it's using offset one。H。Oh， so we're correcting subtracting one， but the sin。Is the sin unacted。

 Is that why the wrapping sub is not picking this up。呃。Bace this。Theself send on a。Yeah。

 I think RNA is not being updated correctly。Base 0， See offset0 base。 No， base 1。So one base one。嗯。

So what sends this fin？Or rather， why is this not being picked up？可。Let's see。

Fhinko is none for all of these。 How is this fin being sent though？That's the real question。 Oh。

 do we still have our hack in place。Is that why？ we do， don't we？Yeah， that should not be there。

Let's see how that turns out。Oh。All looks promising。So let's see。So first we write out the sin。Then。

 rewrite out。呃。Just an empty packet。Unclear why。Oh， this is an act to the other sides。Something。

Unclear。I think this is just an act we decide to send。Yeah。

 this is just us deciding to act something unclear why。Here we do that again。

Just seems like we're just sending X without needing to。嗯。Then。we're acting， no， no no。

 this is us acting the bytes that they send us。Right， because then we get the bites right after her。

Then our shutdown happens。And so we send our fin。And then， it tries to send。我我我我我。What is going on。

Oh， this is the retransmission timer kicking in。That's also problematic。Right。

 so we don't actually reset our redress mission timer anywhere。嗯。So whenever something is act。

Must to act our sins。Right， so here we want to make sure that we remove anything from。



![](img/49347db1b6244c3ae42b589040f18ec5_327.png)

Right， so this is we got。 and actually， let's look at the RF again down here。

 This is when we receive。 Where is it。Check the acccuant。Sin bit， check the act field。Yeah。

 any segments on the retransmission cu， which are thereby entirely acknowledged， are removed。



![](img/49347db1b6244c3ae42b589040f18ec5_329.png)

So this is the trick here。We want to basically remove so self unact。Drain。

And we want to drain everything up to act N。Wrapping sub， self send an a。Right。So， this is。

So this is， we got an act for something， and now we want to remove anything from the unA queuee that has now been act。

And then we also want to deal with any of our timers。U。So。I guess here what I want is。

We want to walk the B tree map so that we want to make sure that we keep track of or remove any of the timers that are relevant。

 right？H。So。Self timers。Send times。I guess， retain。嗯。That's gonna be a sequence number。And a scent。

And if is between wrapped。嗯。Self send。On a。Seek again。So for all the timers。

 if the sequence number for that timer is in the list that has now been acted。Then。

Then we want to remove the timer。However， we also want to make sure that we update our RTT。Estimate。

which was self S RRTT。 So R TT is sent e lappsed。And self the smooth R TT is。

Actuallyly I think what we want is SRTT should just be an F64。As6 of 64。Then， this should be。



![](img/49347db1b6244c3ae42b589040f18ec5_331.png)

嗯。I don't know what they recommended as the alpha。t8， sure。



![](img/49347db1b6244c3ae42b589040f18ec5_333.png)

0。8 times the SrRTT。Plus 1 minus 0。8。

![](img/49347db1b6244c3ae42b589040f18ec5_335.png)

![](img/49347db1b6244c3ae42b589040f18ec5_336.png)

Times。R TT as as6 F 64。Now what。Cannot find value that sc has to be itself。

I guess this might as well just be sent elapsed。5ve。😔，4，3，7。Really。



![](img/49347db1b6244c3ae42b589040f18ec5_338.png)

There isn't a retain on Beare map。

![](img/49347db1b6244c3ae42b589040f18ec5_340.png)

That's interesting。Bet map。Ha。That's awkward。嗯。嗯。Why is there not a retain on Beare map？H。

I guess we will do it the stupid way。B tree map， new。Actually， let。Old is standard member place。

Self timers send times。B tree map new。And then， we're gonna do。All dot extend。嗯。No， self timers。

Send times extend old into iter。Ffiter map。Seek consent。

Which is essentially implementing our own really inefficient retain。Then， none else some。6。Ts。

 S R TT。And this has to be 1。0。Or3，9。So here， this closure borrows self。

But we're also using self here， so we need to。Do some sad stuff like。UA is self send UA。

So this is going to be unA， and this is going to be S RRTT。Otherwise， the closure would not work。

How about now how much is it going to break，ooh， that broke a lot？Drain upper bound was too large。

Really。😔，This one， huh。嗯。How is that possible？So。Ack for that。呃。Last was that。Prune in。This。

Again self send an A and self an act。Ac for one。 last was the， Oh， it's the。

It's when we get the act for the sin。嗯。If。A have self un act。We only wanna do this Excel。Great。

Ak for one， so ignores that。And then somewhere down here。For two great。

 So we still haven't sent any data， but now shutdown works increase font， sure。Better。嗯。Great。

 so now the trick， now the real question is's going be。Can we implement right？

This doesn't actually she need to do anything。Flash。

Because we don't actually have to have a way to do flush yet。But， that's fine。Let's change our main。

To try to do。Stream dot right。Hello。How terribly wrong do we think this is going to go？Mo crashed。

All right。嗯。It's all fine。 So all of this is establishing the connection。

 We receive the data from the other side first， that's fine。And then， we send。Right。

 with a limit of 5。So that would be our hello。And also fins set the true。

And this bull thing closes 6， which is。Zero is the sin。1 is the H and hello。2 is the E，3 is the L。

4 is the L。5 is the O。6 is the f that follows the O。 So that's right。We try to write seven。

Which uses offset。0。😔，This should also set limit to zero。嗯。If we try to write。Trying to write。呃。

Following thin。Alright， let's try that again。Alright， so it still did something weird。

Fact is printing。Doing the same thing a lot。Why。Oh。Why is it deciding to is the real question。

 So it is certainly writing out the data。 It's just doing it a lot。

Let's make our lives a little bit easier and have the timeout thing be like a second instead。Okay。

 so what actually happens here？呃。Because this is all the received stuff so that we already have dealt with。

Here's when the timer first fires after the right。And it wants to write out five bytes that includes the f。

Why is limit5 All right yep。So it's using offset 0 base one in that。 and it's supposed to write out。

5， so 1，2，3，4，5。 This is the hello。Then it tries to write out from seven。

 and then it's just writing nothing。That's all fine。嗯。

Although the fact that this stays full means that we never get an act from the other side， so let's。

Pull up our trusted T shark。Start this again。Start this。Run the client。Right。

 so what actually happened there？Suwei。😔，Weixin。😔，Sequence1 and act their5。

 So this is the food that they sent us plus their sin and their f。No， just put their in。Then。

We send our fin with a length of  five。So clearly it got the data。But。Also， why are we sending these？

We're sending those because we never get the a for this。

Why are they not acting the data we're sending them。That's certainly what's missing。嗯。H。

Because our packets look well formed。I guess let's try pulling up wire shark。嗯。



![](img/49347db1b6244c3ae42b589040f18ec5_342.png)

![](img/49347db1b6244c3ae42b589040f18ec5_343.png)

And then， run。This。

![](img/49347db1b6244c3ae42b589040f18ec5_345.png)

So what does this get？Right， so this is the food that we get from them。Then， we。

this is us actinging their sin again， this is us actinging their foo。

Then we send a thinin a that contains solo。Data5 bytes。But why oh why？

Do we not hear anything from the other side？Isn't that a problem coming from Nsy， Well。

 it does certainly look like Netcat is not doing the right thing。

 but why is it not doing the right thing。

![](img/49347db1b6244c3ae42b589040f18ec5_347.png)

嗯。I mean， we could certainly do dash N。嗯。I don't see why that should matter。Not yet implemented。

 great。Why。Oh7。Oh， I don't think we want that。Oh， I wonder。I wonder whether。嗯。いや。F no of TP。s。

Let me just try a little hack here。And see whether that makes a difference。Just not。嗯。

I have no idea why。It's not。Why is it not printing the。It's clearly getting the data。

 that's what's weird。嗯。I mean， we do， we could enable debugging and see whether that makes a difference。

Sure。I guess debug and verbose it is。呃。I guess not， give me more of herposts。

It's just not printing the contents。What happens if we do curl instead， let's see if curl is better。

Behaved here。No。Now， it shouldn't be farwall rules because the the packets are going through like we see that in T shark。

嗯。Let's see what happens in the case of。嗯。Like if I do。This is really weird because the。Very clearly。

 the packet is going through。Right。Teachhar here， when I run this。Oh。

 we are getting a retransmission from them。Why。Right。This is their sin act。

 this is our act of their sin。This is them sending。And what are they even said。

 weren't they just sent oh foo and a new line？Food in a new line。

This is us maing their sin again because our implementation is stupid is。U。Acknowledging their foe。

This is us。Sending our hello。And also terminating the。Connection。This is us just sending acts。

 This is them。Retransmitting。The f。That doesn't seem right。There is no finignette。

I think this is the kernel from a previous run or something。But why are these just being ignored？Hm。

That is very weird， indeed。Let's try to just like， leave this running for a bit and see if that changes anything。

Certainly at some point we should try to resend the data as well when the timer expires。

Liuccent theory。But our code there could be broken。Muu。😔，I don't see anything。Ha。Fascinating。I mean。

 it could be it doesn't like that we send the fin along with the data。

 but I don't think that should matter。嗯。So remind me why this doesn't work again。

 this crashes us because。Not yet implemented on 5，10。This is， we got a fin early。

 so this is something like。

![](img/49347db1b6244c3ae42b589040f18ec5_349.png)

Were in the established state， and got a fin。In which case we have to glue to close weight， okay。

 fine。

![](img/49347db1b6244c3ae42b589040f18ec5_351.png)

Don't really want to implement that。Shouldn't matter， though。Ha。I don't know why this is happening。嗯。

Let's do ah， here's what we'll do。Let's do an Sce of that process。Let see what it gets。All right。

 so it's loading a bunch of stuff， that's fine， where does it start doing networking things？

So it connects。It reads Fo。 it writes food to the network socket。

 and then it just pulls on the network socket。So this indicates that the kernel never thinks that it's getting data to read。

So it's not Netcat， so it is the kernel。So why is the colonel not delivering that data。😔。

Why is the colonel not delivering that。It's certainly like the protocol interactions all look right。

And the data that they send here， we are receiving。

And the data we're sending here looks totally fine。

 The only thing I can imagine is that it's not okay for us to include the fin with the data。嗯。

So something mean we could try not doing that， I suppose。So in our right。No， in our on tick。um。

So this is just if。Oncent。I 0。So now we should only send the fin after everything else has been acknowledged。

诶。5，10。 Oh that I。Run it with the wrong flags。No。Oh， forgot to run the。T shark。So if we run this now。

With this， what happens？😔，No。So here。This is them sending data to us， this is us acknowledging that。

This is us sending data to them。 notice there's no fin。And then， we send the f。😔，That is so weird。Hm。

I don't have a good answer for you。嗯。Oh， hi。Ha。It looks like all the。

 let's pull up wire shark again because Im oh， that's not what I wanted。Her sha。Apparently not。Mm。

Let's try。Because that did not make a difference。And I don't think push should be necessary。

So why are we getting no axe from the kernel？Here's one thing we could try。If we do this。Then， this。

And then， SS S dash T。21，68。2。😔，Yeah。What's the thing for choosing an interface？呃。啊。

S says show only one interface。

![](img/49347db1b6244c3ae42b589040f18ec5_353.png)

![](img/49347db1b6244c3ae42b589040f18ec5_354.png)

え。Alright， S， S， what is the。哦。I specifically want to know。Oh fine。STI destination。0，1。24。Let's see。

 so it says。It is Act 5 bys。No， it is sent4 bys， and five bys have been act。

Are we yaing too minibytes。Lasts send， lasts receive。 losts I。To deliver。So it is receiving segments。

 it just not adopting them。Why。Hm。So it's just ignoring all the incoming segments because it's saying there's nothing new in them。

 or it's deciding that they're not valid。Okay， that's the only thing I can think of that the is's deciding that the segments we're sending here are invalid。

Why is it deciding that is the real question？啊。Hm。I wish there was a good way to just， like， log。

The kernels。Linux kernelel log dropped packets。

![](img/49347db1b6244c3ae42b589040f18ec5_356.png)

Reasons why the network is dropping packets。

![](img/49347db1b6244c3ae42b589040f18ec5_358.png)

What's in here？Start this。Start that。😔，呃。Rx packets。Because it is getting packets。

There are no Ax errors。There are no C or C errors。No packets dropped。R X bytes。Rx packets。😔。

So it's getting all of them。 This is what's bizarre。And it's getting more and more bites。

But it's just kind of ignoring them。Why is it ignoring them？Let's look more carefully at these。

They send us a sin， sequence number zero。We send them an act。

Saying that the next thing we expect is one。And including our sin with secret zone for zero。

They respond， acting our sin。Giving sequence number one is the contents of this packet。

 but there are no contents。 lengthng is0， and there are no flags and act equals one because the next thing they expect from us is one。

They then send us。With sequence number one。Length of four。We respond。With sequence number one。

 acknowledging five。So the next thing we should receive is five because we were expecting to receive one。

 then we got one，2， three， and four。Because four more。

 so our next expected sequence number from them is 5。So that act is correct。

 which is also why they're not doing any retransmissions。Then， we send。Sequence number equals1。

 which is still correct from our side。Length 5。And that they just stop responding to。嗯。

So those are weird that they're not sending any。I guess the keep alive interval is like two minutes。

 so it'd be surprising if they did。Why are they ignoring our bites？And crucially。

 it seems like it's not dropping any packets。But if you look at the output from SS。Or is it up here。

 the receipt queue is also empty。是。The receive window。

Is large enough to hold This initial window is 10， and we're not sending that many bytes。

 so we should be fine。There's just like nothing here that looks weird。Oh， unless they think our。

Window is too large。嗯。I don't know。

![](img/49347db1b6244c3ae42b589040f18ec5_360.png)

I also don't know how to make progress without more insight into how the kernel。

Is deciding to drop our packets。Which this is not giving me。啊。Are there other。GP。



![](img/49347db1b6244c3ae42b589040f18ec5_362.png)

Except none of them are being dropped， and there is no reset being sent back。And there。

I think there is also。嗯。If we look at I L。Is there an I piece stats， I wonder。嗯。On to tap。So。Monitor。

It seems not helpful。I guess we could try sending， I mean， it would be kind of stupid if this helped。

But what happens if we send。More bites。I mean， this is clearly somewhat。Somewhat of a desperate move。

No。嗯。I don't know， I think what we're going to do then。Is I'm going to commit this。嗯。

Because this looking at the traces it looks like we're doing the right thing。

 which makes me think that what's actually going on is that there's a TSCP extension of some kind that we basically need to support and we don't。

And that's causing the kernel to drop。 What is TCP metrics？TCP的这す。



![](img/49347db1b6244c3ae42b589040f18ec5_364.png)

Allright。I don't think that's going to help us。

![](img/49347db1b6244c3ae42b589040f18ec5_366.png)

Sadly。Because really what we need insight into here is like the。The Linux kernels， TCP stacks。

Like internal steps。U。And I don't think that's something we're easily going to get。

I might end up debugging this sort of separately， but I think。

I think we're at a point where me debugging this any further is not going to be interesting and we also got like basically most of the way we want it right so we know the reads work。

 we have shutdown working on its own and we have rights at least producing what looks like the correct protocol messages。

So I think we're actually going to end it there， even though it is a little bit unsatisfactory。

Because in theory， I think we covered all of the。All of the sort of interesting aspects of this。

 I think the only thing we're really missing is the implementation of flush。

 but flush is also pretty straightforward。So the only thing we're missing for flush is the ability to block until there's nothing left。

 And really， all we'd have to do there is add a。Is my TCP available？

We would just add another available flag that would be like flush。

 and we would set that flag in availability only if。Unact is empty。

 and then we would have a condition variable wake up just like we have elsewhere。嗯。

Come to think of it。 We don't do wake ups for rights here。

 but that is because rights in our system currently just cannot block in a real system。

 you would have a limit to how large you allow your buffers to grow and currently we don't do that。

 So here there's definitely currently our rights do not block and our flush does not block。

 which is not realistic right。Oh I don't think IP metrics。Like IP TCP metrics。

I don't think that's going to make a difference。It doesn't print anything more than what we have from the other stats。

嗯。Yeah， so I think it's really bounding the size of the buffer for right and implementing blocking for rights and blocking for flush。

 which are basically going to be the same thing as we did for read， right。

 like implementing the appropriate availability flags here and adding a condition variable for flush and a condition variable for write。

 both of which are。Essentially the same as what we did for read。And of course。

 that we didn't actually get around to implement and connect， my plan was to do connect。

 but given the issue we're currently seeing， I don't think we're gonna to get past what we're currently seeing without some like deeper level network exact debugging。

 which I think is going to be mostly orthogonal to rust than more like digging into kernel things。

 which I don't want to spend a bunch of time on now，So I think we're going to end it there。

We have now a TCP stack that can do reads and write。

 The rights don't work for some relatively weird reason， but。

The fact that Wireshark and T shark both show like a valid TCP session with data going both directions means that we're like。

If not there， very close。 and I think we have all of the components we believe we're going to need。

 including the timers and stuff for now managing all of this like segmented TCP retransmission。

 it's definitely not the most efficient implementation you're going to get but but I do think we're in a point where the。

The basic structure lends itself to writing a totally correct TCP implementation。

This is likely going to be the very last TCP stream。

 I might do one like much later if there's a lot of requests for it and if we can get past this the kernel dropping our packets。

 in the meantime， what I would like to ask is first of all， if someone wants to dig into this more。



![](img/49347db1b6244c3ae42b589040f18ec5_368.png)

I'll push all the code to the rust TP repository。 So feel free to like。Check it out on your machine。

 try to run it， try to figure out why this is happening。Separately from that。

 please do go to the live coding page and vote for what stream you would like to see next There are a lot of ideas here they would all be interesting to work on like just drag them in the priority order you would like to vote for them and then we'll see what ends up being the next stream my guess is the next stream will be in about two weeks but I will announce it when we get closer。

And with that， thank you everyone， do you have any questions before we like finish then I can take them。

 they don't have to be about TCP or this project at all。

 but like anything at all that I can that you want to like talk about before I sign off。

Need to wait for the delay on the stream。Doesn't look like it。Great， well。

 thanks everyone for coming out， and I will see you on the next stream。

So long farewell of viers and goodbye。

![](img/49347db1b6244c3ae42b589040f18ec5_370.png)