# 约翰霍普金斯大学《信息保障分析｜Information Assurance Analysis》中英字幕 p43 23_TCP-IP协议分析 IV：TCP协议入门.zh_en -BV1Qz8EzYENX_p43-

This is 695741， Oule 2， Le 4 and this module will be covering TCD。



![](img/910a37d33ade943714bab18be13f04ad_1.png)

At the end of this module you'll be able to explain the basic mechanisms involved in a TCP session。

 including the TCP flags， what the sequence numbering is for。

 and also be able to describe the TCP state machine。

You'll be able to describe the structure of a TCP packet。

 including what the various fields mean and what their uses are。

And also be able to describe relevant features of TCP。



![](img/910a37d33ade943714bab18be13f04ad_3.png)

We pay special attention to TP in this module because of its dominance in modern network traffic。

TCP is byte for byte the most common protocol used on the internet， hundreds of services use it。

So many of the applications that you use on a regular basic basis。Are made possible by this protocol。

For instance， when you check your mail， look at web pages or transfer files over FTP。

 you're using TCP。So it's worth spending a considerable amount of time understanding what this traffic is and what the quirks of it are。

Granted it is an expensive protocol， there's a lot of packet retransmission。

 but with that cost comes a guarantee that every bit of payload sent will end up at the other end of a connection Ral Scre bloody murder。



![](img/910a37d33ade943714bab18be13f04ad_5.png)

So。TCP is imposing a model of on IP that IP doesn't use natively。It builds an illusion。

If you remember back to our discussion about the IP suite。

 you'll remember that it is a packet switchy protocol。

So it does not have a dedicated circuit by which it transmits data TCP allows us to have the illusion of a circuit by maintaining state in the session。



![](img/910a37d33ade943714bab18be13f04ad_7.png)

In this model， we have two parties trying to speak the client。

The initiator at the communication and the server。The entity that's listening for clients who are trying to connect。

What this really means is that we only haven that。One of them sets up starts the connection and the other actually is listening for the cache。

 it doesn't have any bearing on the actual transmission of data once the session is established。



![](img/910a37d33ade943714bab18be13f04ad_9.png)

These two roles are a little bit fuzzy in that regard。So here's the TCP header。

We start off with two 16 bit numbers， those are the port numbers。

We're going to get into those a little bit， but just think of them like your standard web port numbers and your web port number like 80 or SMmTP。

 which is 425， these numbers are present there。We also have a sequence number and acknowledgement number。

 which are2 32 bit numbers that allow us to represent what's going on in the session。

We have an offset which tells us how large the actual header here is。

And we have flags flags are going to be the most one of the most important one of the most important fields。

 because this is where the state is actually maintained and it tells you a lot about what the packet's intent actually is we also have the window size checks some and urgent。

And of course， just like with the IP suite， we've got the options at the end。



![](img/910a37d33ade943714bab18be13f04ad_11.png)

And following all of that comes the payload， which is the actual data being transmitted。



![](img/910a37d33ade943714bab18be13f04ad_13.png)

Let's spend a little bit of time talking about the the really important parts。

State is maintained in the flag field， like I said before。

The flag field is eight bits where each bit represents a flag。

You will often hear people refer to packets based on what combination of bits are set in this field。

 The send bit indicates synchronization， and that's commonly referred to as the send packets。



![](img/910a37d33ade943714bab18be13f04ad_15.png)

![](img/910a37d33ade943714bab18be13f04ad_16.png)

The Fin bit indicates closing of sessions of the reset that that the connection is to be reset Finally we've got the act that that can mean multiple things really depending on what's going on and where it is in the actual stream of packet that have and sent between the two。

 but we're going to get to that in a second。There's also this push urgent and ECE bits which don't relate to state necessarily。

 so we're going to kind of gloss over them for the time being。



![](img/910a37d33ade943714bab18be13f04ad_18.png)

And get directly into these。More important session based bits。Okay。

Excuse me so a client a client initiates the connection by sending a send packet to the server that's listening。



![](img/910a37d33ade943714bab18be13f04ad_20.png)

Where a server listens and hears that， it responds back with a Senac。



![](img/910a37d33ade943714bab18be13f04ad_22.png)

Now the S Act basically says，" yeah， I hear you and let's establish a connection。



![](img/910a37d33ade943714bab18be13f04ad_24.png)

Finally， the client will send back its own acknowledgement and thus data transfering can occur。

I'm pretty sure that everybody here has already heard about threeaway handshake， if not。

 that was it just described it in a play by play， then we also have how to tear down a session。

Once we got an established session， everybody down the threeaway handshake that transferred all the data that they need。

 either side can actually send a f。

![](img/910a37d33ade943714bab18be13f04ad_26.png)

And the other side wars spa back with an acknowment of that and then send their own f。Wech。

Will then be acknowledged and the session is completely terminated。This is how it's supposed to go。

 This is not how it always goes。 In fact， many servers implement servers implement it to day。 Well。

 just instead of going through this process of sending fs and axe and waiting for you to send a f back。

 They'll just send。A couple of resets like eight resets。

 assume that one of them is going to make it to you and just throw away the connection。

It's not elegant， but that's how it works， doesn' matter to any users because they don't see it。

 it will matter to you since you're going to be looking at packet data。

So just be aware that this does exist and it does affect our data collection。

 but it does not necessarily mean that any maliciousness is present。



![](img/910a37d33ade943714bab18be13f04ad_28.png)

![](img/910a37d33ade943714bab18be13f04ad_29.png)

The basic sequence of events is this。At session Open， each side sends a S packet。

Establishes an initial sequence number which we're about to get to and the response include in every response。



![](img/910a37d33ade943714bab18be13f04ad_31.png)

Includes an act which confirms how much data has been received。

Then we actually gather it through and try and terminate the connection with a fin。

Once we've transmitted all of our data， or of course we've got the reset capability。



![](img/910a37d33ade943714bab18be13f04ad_33.png)

Yeah。So now back to the sequence number and acknowledgement number。

This is how each side keeps track of what the other has seen。



![](img/910a37d33ade943714bab18be13f04ad_35.png)

The way it works is simple， a sequence number。Is randomly selected by the client who sends。

Who sends it and its initial S packet， The server acknowledges by sending back the number in the acknowledgeknowment field and chooses its own sequence number。

 The client sends back a packet where the acknowledgecknowledment number is the sequence number sent by the server and increments the sequence number that it' sent before by the size of the data it sends。



![](img/910a37d33ade943714bab18be13f04ad_37.png)

From this point， each side just acknowledges up to the sequence number it receives。

 and the sequence number tells the receiver where the packet goes in the sequence。

This is very important in detecting when packets are missing。

 Each side will only fill the acknowledgeledment field with the sequence number to which it has all data transmitted。

 For example， if a server has all of the data from client from the client up to the sequence number 10。

 and it receives a packet with a sequence number of 400 without receiving the packets that gave it the data in between。

 the server will respond to ament will respond with an acknowledgement of 10。



![](img/910a37d33ade943714bab18be13f04ad_39.png)

![](img/910a37d33ade943714bab18be13f04ad_40.png)

![](img/910a37d33ade943714bab18be13f04ad_41.png)

This is where it gets kind of。Um messssy。And this is where you start seeing a lot of packet retreat missions。

Because it's only going to because each side's only going to acknowledge up to the point that it has all of the data。

Even if it's just missing one packet。One packet didn't make it。

The other side eventually is going to say， okay， well。

 I need to retransmit data and start retransmiting all of the data。

And that's going to include that one packet that it needs and also all the packets that it doesn't necessarily。

Good part is that if you're only missing one packet and you know， in this particular case。

 we're missing one packet for the sequence between 10 and 400。



![](img/910a37d33ade943714bab18be13f04ad_43.png)

That means that once it receives that packet， it's going to acknowledge all the way up to 400。

 so hopefully not everything's going to have to be ray trans。



![](img/910a37d33ade943714bab18be13f04ad_45.png)

But this is where the messiness actually occurs。So here's the machine here's the state machine describing how TCP converts packets into the illusion of a session and it's hard the mechanism of the state for state enforcement is relatively simple。

 I mean we've just gone over most of it right there。

 but there's a lot of corner cases which look flying an airplane the harder it' it's。

Really hard to get started and end。The middle part's pretty simple。And at this point。

 you know the basics of how how the beginning and end works， so we're going to move on from here。

 but this is a nice little state data diagram that you can walk through and actually describe everything in。



![](img/910a37d33ade943714bab18be13f04ad_47.png)

Now。Let's get to the port numbers， port numbers are completeless。

They're really just recommendations of what applications should run on each port。

There's absolutely nothing that makes you run a particular service on a particular port other than the fact that everyone generally expects you to。

One thing is very certain though， user level activity occurs above port 24。

 If you are a client without privilege， you are likely going to pull an address or a port number from a pool of ports above 1034。

That's why whenever you start looking at traffic， you're going to see a well known port number like port 80 connected to some sort of strange number that's between 1024 and 65535。



![](img/910a37d33ade943714bab18be13f04ad_49.png)

![](img/910a37d33ade943714bab18be13f04ad_50.png)

Because the client pulled a port from that pool of user port numbers。Now off to the right here。

 we do have a list of some of the more common ports that you'll see and generally speaking， you know。

 when you see these a majority of that traffic is probably going to be these guys。

 it's it's it's possible that you could be setting up a web server on something that's not port 80。

But。It's and that's some malicious activity does that because it's a wonderful way of setting up a service on some sort of strange port and have people not look at it as。

 web traffic。But it's online for that you're going to have an SMTP server set up once it's on strange board that's not 25。

But。I strongly recommend that everybody at least learn the general port numbers that people have to use。



![](img/910a37d33ade943714bab18be13f04ad_52.png)

Are that people use？Now a little bit on the options。The offset field is just like in the IP suite。

 works on words， not on bytes， so generally speaking we have five words。

 20 bytes native TCP header size by default。If it is higher。

 that means we've got some options and some of the more common options are listed here where we can actually adjust the maximum segment size。

 how big the data can be at any given time。The selective acknowledgement。

 which allows us to actually not acknowledge every single thing。

 but do specific things on how we determine how many bytes we received。Also。

 you can do some timetamps and they have some quote， unqued security。嗯。

Mechanisms tied into an M5 check sum， which will allow you to indicate。What are。

Indigate actually determine whether or not somebody has modified the data in transit。



![](img/910a37d33ade943714bab18be13f04ad_54.png)

In conclusion， TCP is a common protocol on the IP suite so used for session based activities provides an illusion of a circuit。

And packets can arrive out of order。And put back and and be put back into order。

And several fields are used to set up and maintain state。



![](img/910a37d33ade943714bab18be13f04ad_56.png)

Port gives an indication of the services running， but not a guarantee。



![](img/910a37d33ade943714bab18be13f04ad_58.png)

Of what that service actually is。