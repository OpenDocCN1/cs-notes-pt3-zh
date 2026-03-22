# 谷歌《IT支持（计算机网络⧸操作系统，第2、3课⧸共5课）｜Google IT Support》中英字幕deepseek p20 18_IP数据报与封装.zh_en -BV1uyqcYpExr_p20-

![](img/e202f37a04557bd1c3365865b723659a_0.png)

Just like call the data packets at the Ethernet layer have a specific name ethernet frames。

 so do packets at the network layer under the IP protocol。

 a packet is usually referred to as an IP datagram。Just like any ethernet frame。

 an IP Datagram is a highly structured series of fields that are strictly defined。



![](img/e202f37a04557bd1c3365865b723659a_2.png)

The two primary sections of an IP datagram are the header and the payload。

You'll notice that an IP Datagram header contains a lot more data than an ethernet frame header does。

The very first field is4 bits and indicates what version of internet protocol is being used。



![](img/e202f37a04557bd1c3365865b723659a_4.png)

The most common version of IP is version 4 or IPV4。



![](img/e202f37a04557bd1c3365865b723659a_6.png)

Version 6 or IPV6 is rapidly seeing more widespread adoption， but we'll cover that in a later module。

After the version field， we have the header length field。

This is also a four bit field that declares how long the entire header is。



![](img/e202f37a04557bd1c3365865b723659a_8.png)

This is almost always 20 bytes in length when dealing with IPV4。



![](img/e202f37a04557bd1c3365865b723659a_10.png)

In fact， 20 bytes is the minimum length of an IP header。

 you couldn't fit all the data you need for a properly formatted IP header in any less space。Next。

 we have the service type field。

![](img/e202f37a04557bd1c3365865b723659a_12.png)

These eight bits can be used to specify details about quality of service or QOS technologies。

 the important takeaway about QOS is that there are services that allow routers to make decisions about which IP datagram may be more important than others。



![](img/e202f37a04557bd1c3365865b723659a_14.png)

The next field is a 16 bit field known as the total length field。



![](img/e202f37a04557bd1c3365865b723659a_16.png)

It's used for exactly what it sounds like to indicate the total length of the IP datagram it's attached to。



![](img/e202f37a04557bd1c3365865b723659a_18.png)

The identification field is a 16 bit number that's used to group messages together。



![](img/e202f37a04557bd1c3365865b723659a_20.png)

IP datagrams have a maximum size and you might already be able to figure out what that is since the total length field is 16 bits and this field indicates the size of an individual datagram。

 the maximum size of a single datagram is the largest number you can represent with 16 bits， 65，535。

If the total amount of data that needs to be sent is larger than what can fit in a single datagram。

 the IP layer needs to split this data up into many individual packets。When this happens。

 the identification field is used so that the receiving end understands that every packet with the same value in that field is part of the same transmission Next up。

 we have two closely related fields， the flag field and the fragmentation offset field。



![](img/e202f37a04557bd1c3365865b723659a_22.png)

![](img/e202f37a04557bd1c3365865b723659a_23.png)

![](img/e202f37a04557bd1c3365865b723659a_24.png)

![](img/e202f37a04557bd1c3365865b723659a_25.png)

The flag field is used to indicate if a datagram is allowed to be fragmented or to indicate that the datagram has already been fragmented fragmentmentation is the process of taking a single IP datagram and splitting it up into several smaller datagrams。

 while most networks operate with similar settings in terms of what size and IP datagram is allowed to be。

 sometimes this could be configured differently。

![](img/e202f37a04557bd1c3365865b723659a_27.png)

![](img/e202f37a04557bd1c3365865b723659a_28.png)

If a datagram has to cross from a network allowing a larger datagram size to one with a smaller datagram size。

 the datagram would have to be fragmented into smaller ones。

 The fragmentation offset field contains values used by the receiving end to take all the parts of a fragmented packet and put them back together in the correct order。

 Let's move along to the time to live or TTL field。



![](img/e202f37a04557bd1c3365865b723659a_30.png)

![](img/e202f37a04557bd1c3365865b723659a_31.png)

![](img/e202f37a04557bd1c3365865b723659a_32.png)

This field is an eight bit field that indicates how many router hops a datagram can traverse before it's thrown away。



![](img/e202f37a04557bd1c3365865b723659a_34.png)

Every time a data reaches a new router， that router decrements the TTL field by one。

Once this value reaches zero， a router knows it doesn't have to forward the datagram any further。



![](img/e202f37a04557bd1c3365865b723659a_36.png)

The main purpose of this field is to make sure that when there's a misconfiguration in routing that causes an endless loop。

 datagrams don't spend all eternity trying to reach their destination。

And then the slo could be when router A thinks router B is the next hop and router B thinks router A is the next hop spoiler alert in an upcoming module。

 you'll learn that the TTL field has valuable troubleshooting qualities but secrets like these are only released to those who keep going。



![](img/e202f37a04557bd1c3365865b723659a_38.png)

![](img/e202f37a04557bd1c3365865b723659a_39.png)

After the TTL field， you'll find the protocol field。

This is another eight bit field that contains data about what transport layer protocol is being used。

 the most common transport layer protocols are TCP and UDP。

 and we'll cover both of those in detail in the next few lessons。



![](img/e202f37a04557bd1c3365865b723659a_41.png)

So next。We find the header checkum field。

![](img/e202f37a04557bd1c3365865b723659a_43.png)

This field is a checkum of the contents of the entire IP Datagram header。



![](img/e202f37a04557bd1c3365865b723659a_45.png)

It functions very much like the ethernet checkum field we discussed in the last module。

Since the TTL field has to be recomputed at every router that a datagram touches。

The checkum field necessarily changes too。After all of that。

 we finally get to two very important fields， the source and destination IP address fields。

 remember that an IP address is a 32 bit number， so it should come as no surprise that these fields are each 32 bits long。

Up next， we have the IP optionss field。

![](img/e202f37a04557bd1c3365865b723659a_47.png)

This is an optional field and is used to set special characteristics for datagrams primarily used for testing purposes。



![](img/e202f37a04557bd1c3365865b723659a_49.png)

The IP options field is usually followed by a padding field。

 since the IP options field is both optional and variable in length。

 the padding field is just a series of zeros used to ensure the header is the correct total size。



![](img/e202f37a04557bd1c3365865b723659a_51.png)

Now that you know about all of the parts of an IP datagram。

 you might wonder how this relates to what we've learned so far。

You might remember that in our breakdown of an ethernet frame。

 we mentioned a section we described as the data payload section。

This is exactly what the IP Datagram is。And this process is known as encapsulation。

The entire contents of an IP datagram are encapsulated as the payload of an ethernet frame。



![](img/e202f37a04557bd1c3365865b723659a_53.png)

You might have picked up on the fact that our IP Datagram also has a payload section。

The contents of this payload are the entirety of a TCP or UDP packet， which we'll cover later。



![](img/e202f37a04557bd1c3365865b723659a_55.png)

Hopefully， this helps you better understand why we talk about networking in terms of layers。

 each layer is needed for the one above it。