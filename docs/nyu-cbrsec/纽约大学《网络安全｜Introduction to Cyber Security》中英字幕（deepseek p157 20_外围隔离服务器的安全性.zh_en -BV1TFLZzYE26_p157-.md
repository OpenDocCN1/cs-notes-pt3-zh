# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p157 20_外围隔离服务器的安全性.zh_en -BV1TFLZzYE26_p157-

![](img/598ba8d3247f76f254131472c1898ee5_0.png)

Hi， folks at Amarosso here， and I want to talk to you a little bit about the implications of a big distributed kind of hybrid cloud security architecture and the idea that we'd have workloads scattered around different cloud infrastructure。

 potentially around the globe and coordinated and hyper- resilient。

 all the nice features that we want in a future enterprise security architecture when I show that concept to a lot of security teams。

Here's what they say。 They'll show me that their data center architecture is global。 They'll say。

 well， data center over here。Some headquarters building over there。

 and we're scattered around the globe， maybe your big bank。

 And they'll say we already are that we are distributed and we are global。

 But that's not what I'm talking about， a global perimeter is not secure。

 Here's a representation here that shows a little warning that global perimeter are not secure。

 If I have all these nodes scattered around lots of different countries。

 little blue nodes and red nodes denoting workloads and control nodes respectively。

 If all of them are protected by a common perimeter。

 meaning I've got one or two or three or however many gateways that are the entry point to which I can gain access to these systems across which there's layer 1 connectivity。

 there's network media that connects them and that they trust each other。

 So some an attack that happens in Australia might cascade laterally across the perimeter。

To a server in Seattle， they'll trust each other。 a global perimeter is not secure。 Now。

 if you have something like this， which a lot of people do， an interesting corollary emerges。

It may be I want you to look up in the top left of this diagram。

 You can see one of the little servers there。 If it's sitting there， again。

 let's assume I got an attack in Australia。 It traverses laterally through this trusted grid。

W is more secure for it to be sitting in the perimeter or the next chart shows I've now taken that server and moved its wayway up into Canada into an isolated server with its own microsmentation let's go back a chart look at what we had we had that dot that little server sitting inside the perimeter officially inside the perimeter and now boom I've isolated it out。

 which do you think is more secure I think the answer is that server is more secure outside that big monster perimeter Now here's the reason this is sort of interesting here in the United States we had an election recently where one of the big issues was that one of the candidates had isolated an email server outside the official government infrastructure。

 namely big perimeter happened to be run by the US state Department Now setting the politics aside。

 this is nothing to do with politics。 the implication a lot of people。

m and sort of the conclusion that was made was that by isolating that server outside the perimeter。

 this candidate made the server， the server less secure。

 I think you could make the case that the argument is wrong that in fact。

 by isolating the server by removing it from the perimeter。 it was actually more secure。

 I doubt that that political group had intended to do it for that reason that maybe 50 other reasons for moving it out but maybe an unintended consequence is that it actually led to a more secure service。

 So what we all need to take from this。 is that it's not necessarily the case that services are better off from a security perspective inside a big sort of official perimeter better to break the whole thing up。

 isolate， scatter， distribute， virtualize These are the words。

 these are the verbs that should be used synonymously with making。More secure。

 I hope you've enjoyed this。 I'll see you in the next one。



![](img/598ba8d3247f76f254131472c1898ee5_2.png)

![](img/598ba8d3247f76f254131472c1898ee5_3.png)