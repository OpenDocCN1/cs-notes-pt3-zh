# 谷歌《IT支持（计算机网络⧸操作系统，第2、3课⧸共5课）｜Google IT Support》中英字幕deepseek p37 35_TCP段的剖析.zh_en -BV1uyqcYpExr_p37-

![](img/14ed24605fdb269e6ed5024a115cd245_0.png)

Heads up in this video， we're going to dissect a TCP segment。In IT support。

 if network traffic isn't behaving as users expected it to。

 you might have to analyze it closely to troubleshoot。

So get ready to take a peek at all the inner workings。

Just like how an ethernet frame encapsulates an IP datagram。

 an IP datagram encapsulates a TCP segment。

![](img/14ed24605fdb269e6ed5024a115cd245_2.png)

Remember that an Ethernet frame has a payload section。

 which is really just the entire contents of an IP datagram。

Remember also that an IP datagram has a payload section。

 and this is made up of what's known as a TCP segment。

A TCP segment is made up of a TCP header and a data section。



![](img/14ed24605fdb269e6ed5024a115cd245_4.png)

This data section， as you might guess， is just another payload area for where the application layer places its data。

A TCP header itself is split into lots of fields containing lots of information。First。

 we have the source port and the destination port fields。



![](img/14ed24605fdb269e6ed5024a115cd245_6.png)

The destination port is the port of the service the traffic is intended for。

 which we talked about in the last video。A source port is a high numbered port chosen from a special section of ports known as ephemeral ports。



![](img/14ed24605fdb269e6ed5024a115cd245_8.png)

We'll cover our ephemal reports in more detail in a little bit。

For now it's enough to know that a source port is required to keep lots of outgoing connections separate。

 you know how a destination port， say port 80 is needed to make sure traffic reaches a web server running on a certain IP Similarlyly。

 a source port is needed so that when the web server replies。

 the computer making the original request can send this data to the program that was actually requesting it。

 it is in this way that when a web server responds to your request to view a web page。

 that this response gets received by your web browser and not your word processor。



![](img/14ed24605fdb269e6ed5024a115cd245_10.png)

![](img/14ed24605fdb269e6ed5024a115cd245_11.png)

Next up is a field known as the sequence number。

![](img/14ed24605fdb269e6ed5024a115cd245_13.png)

This is a 32 bit number that's used to keep track of where in a sequence of TCP segments。

 this one is expected to be。

![](img/14ed24605fdb269e6ed5024a115cd245_15.png)

You might remember that lower on our protocol stack。

 there are limits to the total size of what we send across the wire。



![](img/14ed24605fdb269e6ed5024a115cd245_17.png)

An etherNe frame is usually limited in size to 1，518 bytes。

But we usually need to send way more data than that。At the transport layer。

 TCP splits all of this data up into many segments。



![](img/14ed24605fdb269e6ed5024a115cd245_19.png)

The sequence number in a header is used to keep track of which segment out of many this particular segment might be。

The next field， the acknowledgeledment number。Is a lot like the sequence number。



![](img/14ed24605fdb269e6ed5024a115cd245_21.png)

The acknowledgecment number is the number of the next expected segment in very simple language。

 a sequence number of one and an acknowledgegment number of two。



![](img/14ed24605fdb269e6ed5024a115cd245_23.png)

Could be read as this is segment 1， expect segment 2 next。



![](img/14ed24605fdb269e6ed5024a115cd245_25.png)

The data offset field comes next。This field is a four bit number that communicates how long the TCP header for this segment is。



![](img/14ed24605fdb269e6ed5024a115cd245_27.png)

This is so that the receiving network device understands where the actual data payload begins。

 then we have six bits that are reserved for the six TCP control flags。

 we'll cover the control flags and what they each mean in the next video， so flag this for later。

The next field is a 16 bit number known as the TCP window。



![](img/14ed24605fdb269e6ed5024a115cd245_29.png)

A TCP window specifies the range of sequence numbers that might be sent before an acknowledgement is required。



![](img/14ed24605fdb269e6ed5024a115cd245_31.png)

As we'll cover in more detail soon， TCP is a protocol that's super reliant on acknowledgegments。

This is done in order to make sure that all expected data is actually being received and that the sending device doesn't waste time sending data that isn't being received。

 The next field is a 16 bit checkum。It operates just like the checkum fields at the IP and Ethernet level。

Once all of a segment has been ingested by a recipient。

 the checkum is calculated across the entire segment and is compared with the checkum in the header to make sure that there was no data lost or corrupted along the way。



![](img/14ed24605fdb269e6ed5024a115cd245_33.png)

![](img/14ed24605fdb269e6ed5024a115cd245_34.png)

The urgent pointer field is used in conjunction with one of the TCP control flags to point out particular segments that might be more important than others。



![](img/14ed24605fdb269e6ed5024a115cd245_36.png)

![](img/14ed24605fdb269e6ed5024a115cd245_37.png)

This is a feature of TCP that hasn't really ever seen adoption。

 and you'll probably never find it in modern networking。

 even so it's important to know what all sections of the TCP header are。Next up。

 we have the optionstion field。Like the urgent pointer field， this is rarely used in the real world。

 but it's sometimes used for more complicated flow control protocols。



![](img/14ed24605fdb269e6ed5024a115cd245_39.png)

![](img/14ed24605fdb269e6ed5024a115cd245_40.png)

Finally， we have some padding， which is just a sequence of zeros to ensure that the data payload section begins at the expected location。



![](img/14ed24605fdb269e6ed5024a115cd245_42.png)