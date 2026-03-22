# 谷歌《IT支持（计算机网络⧸操作系统，第2、3课⧸共5课）｜Google IT Support》中英字幕deepseek p44 42_各层协同工作.zh_en -BV1uyqcYpExr_p44-

![](img/f25e5c5b0d13d47955d0405972e87b8a_0.png)

。Now that you know the basics of how every layer of our network model works。

 let's go through an exercise to look at how everything works at every step of the way。Spoiler alert。

 things are about to get a little geeky in a good way。

Imagine three networks Network A will contain address space 10。1。1。0/24。



![](img/f25e5c5b0d13d47955d0405972e87b8a_2.png)

Network B will contain addressSp 192。168。1。0/24， and network C will be 172。16。1。0/24。

Rooututer A sits between network A and network B with an interface configured with an IP of 10。1。1。

1 on network A and an interface at 192。168。1。254 on network B。There's a second router router B。

 which connects networks B and C， It has an interface on network B with an IP address of 192。168。1。

1 and an interface on network C with an IP address of 172。16。1。1。



![](img/f25e5c5b0d13d47955d0405972e87b8a_4.png)

Now let's put a computer on one of the networks， imagine it's a desktop sitting on someone's desk at their workplace。



![](img/f25e5c5b0d13d47955d0405972e87b8a_6.png)

It'll be our client in this scenario and we'll refer to it as Comp one。

It's part of network A and has been assigned an IP address of 10。1。1。100。

 Now let's put another computer on one of our other networks。This one is a server in a data center。

It'll act as our server in this scenario and will refer to it as Comp 2。

 It's part of Network C and has been assigned an IP address of 172。 16。1。

 100 and has a web server listening on port 80。

![](img/f25e5c5b0d13d47955d0405972e87b8a_8.png)

An end user sitting at Comp One opens up a web browser and enters 172。16。1。100 into the address bar。

 let's see what happens。The web browser running on Comp One knows it's been ordered to retrieve a web page from 172。

16。1。100。The web browser communicates with the local networking stack。

 which is the part of the operating system responsible for handling networking functions。

 The web browser explains that it's going to want to establish a TCP connection to 172。16。1。

100 port 80。The networking stack will now examine its own subnet。

 it sees that it lives on the network 10。1。1。0/24， which means that the destination 172。16。1。

100 is on another network。

![](img/f25e5c5b0d13d47955d0405972e87b8a_10.png)

At this point， computer1 knows that it'll have to send any data to its gateway for routing to a remote network。

 and it's been configured with a gateway of 10。1。1。1。Next。

 Comp1 looks at its Arc table to determine what Mac address of 10。1。1。1 is。

 but it doesn't find any corresponding entry。Oh， it's okay。

 Comp A crafts an Arc request for an IP address of 10。1。1。1。

 which it sends to the hardware broadcast address of all Fs。

This ARP discovery request is sent to every node on the local network。



![](img/f25e5c5b0d13d47955d0405972e87b8a_12.png)

When router A receives this art message， it sees that it's the computer currently assigned the IP address of 10。

1。1。1， so it responds to computer1 to let it know about its own Mac address of 001122334455。

Computer1 receives this response and now knows the hardware address of its gateway。

This means that it's ready to start constructing the outbound packet。

Computer1 knows that it's being asked by the web browser to form an outbound TCP connection。

 which means it'll need an outbound TCP port。 The operating system identifies the ephemeral port of 50。

000 as being available and opens a socket connecting the web browser to this port。



![](img/f25e5c5b0d13d47955d0405972e87b8a_14.png)

Since this is a TCP connection， the networking stack knows that before it can actually transmit any of the data the web browser wants it to。

 it'll need to establish a connection。

![](img/f25e5c5b0d13d47955d0405972e87b8a_16.png)

The networking stack starts to build a TCP segment。

 It fills in all the appropriate fields in the header， including a source port of 50。

000 and a destination port of 80。A sequence number is chosen and is used to fill in the sequence number field。

Finally， the S flag is set and a checkum for the segment is calculated and written to the checkum field。



![](img/f25e5c5b0d13d47955d0405972e87b8a_18.png)

![](img/f25e5c5b0d13d47955d0405972e87b8a_19.png)

Our newly constructed TCP segment is now passed along to the IP layer of the networking stack。



![](img/f25e5c5b0d13d47955d0405972e87b8a_21.png)

This layer constructs an IP header。This header is filled in with the source IP， the destination IP。

 and a TTL of 64， which is a pretty standard value for this field。Next。

 the TCP segment is inserted as the data payload for the IP datagram。

 and a checkup is calculated for the whole thing。

![](img/f25e5c5b0d13d47955d0405972e87b8a_23.png)

Now that the IP datagram has been constructed， Comp1。Needs to get this to its gateway。

Which it now knows has a Mac address of 0011，22334455。 so an ethernet frame is constructed。

 All the relevant fields are filled in with the appropriate data。

 most notably the source and destination Mac addresses。



![](img/f25e5c5b0d13d47955d0405972e87b8a_25.png)

![](img/f25e5c5b0d13d47955d0405972e87b8a_26.png)

Finally， the IP datagram is inserted as the data payload of the Ethernet frame。

 and another checkum is calculated。Now we have an entire ethernet frame ready to be set across the physical layer。

The network interface connected to Comp1 sends its binary data as modulations of the voltage of an electrical current running across a CAt6 cable that's connected between it and a network switch。



![](img/f25e5c5b0d13d47955d0405972e87b8a_28.png)

This switch receives the frame and inspects the destination Mac address。

The switch knows which of its interfaces this Mac address is attached to and forwards the frame across only the cable connected to this interface。



![](img/f25e5c5b0d13d47955d0405972e87b8a_30.png)

At the other end of this link is router A， which receives the frame and recognizes its own hardware address as the destination。

Rooututer A knows that this frame is intended for itself。

 So it now takes the entirety of the frame and calculates a checkum against it。

 Ror A compares this checkum with the one in the ethernet frame header and sees that they match。

 meaning all of the data has made it in one piece。Next， router A strips away the ethernet frame。

 leaving it with just the IP datagram again， it performs a checkum calculation against the entire datagram and again it finds that it matches。

 meaning all the data is correct。

![](img/f25e5c5b0d13d47955d0405972e87b8a_32.png)

It inspects the destination IP address and performs a lookup of this destination in its routing table router A sees that in order to get data to the 172。

16。1。0/24 network， the quickest path is 1 hop away via router B， which has an IP of 192。168。1。1。

Ruter A looks at all the data in the IP datagram， decrements the TTL by one。

 calculates a new checkum reflecting the new TTL value and makes a new IP datagram with this data。



![](img/f25e5c5b0d13d47955d0405972e87b8a_34.png)

![](img/f25e5c5b0d13d47955d0405972e87b8a_35.png)

Rooututer A knows that it needs to get this datagram to router B， which has an IP address of 192。168。

1。1， it looks at its arc table and sees that it has an entry for 192。168。1。1。Now。

 router A can begin to construct an ethernet frame with the Mac address of its interface on network B as the source and the Mac address of router B's interface on network B as the destination Once the values for all fields in this frame have been filled out router A places the newly constructed IP datagram into the data payload field calculates a checksum and places this checksum into place and sends the frame out to network B。



![](img/f25e5c5b0d13d47955d0405972e87b8a_37.png)

![](img/f25e5c5b0d13d47955d0405972e87b8a_38.png)

Just like before， this frame makes it across network B and is received by router B。



![](img/f25e5c5b0d13d47955d0405972e87b8a_40.png)

Rooututer B performs all the same checks， removes the ethernet frame encapsulation。

 and performs a checksum against the IP datagram。

![](img/f25e5c5b0d13d47955d0405972e87b8a_42.png)

It then examines the destination IP address。Looking at its router table。

 router B sees that the destination address of Comp 2 or 172。16。1。

 100 is on a locally connected network， So it decrements the TTL by one again。

 calculates a new checkup and creates a new IP datagram。



![](img/f25e5c5b0d13d47955d0405972e87b8a_44.png)

This new IP datagram is again encapsulated by a new ethernet frame。

 this one with the source and destination Mac address of router B and Computer2。



![](img/f25e5c5b0d13d47955d0405972e87b8a_46.png)

And the whole process is repeated one last time。The frame is sent out onto network C。

 A switch ensures it gets sent out of the interface that Comp 2 is connected to。

 Computer 2 receives the frame， identifies its own Mac address as the destination and knows that it's intended for itself。



![](img/f25e5c5b0d13d47955d0405972e87b8a_48.png)

![](img/f25e5c5b0d13d47955d0405972e87b8a_49.png)

Computer 2 then strips away the etherM frame， leaving it with the IP datagram。



![](img/f25e5c5b0d13d47955d0405972e87b8a_51.png)

It performs a CRC and recognizes that the data has been delivered intact。

It then examines the destination IP address and recognizes that as its own。Next。

 Comp 2 strips away the IP Datagram， leaving it with just the TCP segment。



![](img/f25e5c5b0d13d47955d0405972e87b8a_53.png)

Again， the checksum for this layer is examined and everything checks out。Next。

 computer 2 examines the destination port， which is 80。

The networking stack on Comp 2 checks to ensure that there's an open socket on port 80。

 which there is。It's in the listen state and held open by a running Apache web server。

Computer2 then sees that this packet has the S flag set。



![](img/f25e5c5b0d13d47955d0405972e87b8a_55.png)

So it examines the sequence number and stores that。

 since it'll need to put the sequence number in the acknowledgement field once it crafts the response。



![](img/f25e5c5b0d13d47955d0405972e87b8a_57.png)

After all of that， all we've done is get a single TCP segment containing a S flag from one computer to a second one。

Everything would have to happen all over again for Comp2 to send a Sin act response to Comp1。

Then everything would have to happen all over again for Comp one to send an app back to computer2 and so on and so on。

Looking at all of this end to end hopefully helps show how all the different layers of our networking model have to work together to get the job done。

 I hope it also gives you some perspective in understanding how remarkable computer networking truly is。

😊，Even more remarkable than that， you for making it through this module。

 now it's time to apply your new knowledge to the next assessment When you're done。

 I'll see you in the next video。But first， another quiz， you got this。But even if you don't。

 just review the material until you get more comfortable with this stuff。

