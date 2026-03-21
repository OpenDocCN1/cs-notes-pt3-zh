# 约翰霍普金斯大学《信息保障分析｜Information Assurance Analysis》中英字幕 p19 18_路由协议滥用行为.zh_en -BV1Qz8EzYENX_p19-

![](img/ed9838bc3e7c56accd0716c22d0092d6_0.png)

Look class it a 6。5741 information assurance analysis as Professor Culin is talking and the topics of this module。

 which is 55 is routing abuse This is a bit of a grab bag topic actually I'm going to talk about an actual routing failure Now if you call from my lecture and from my lecture earlier of this module I talked about the idea that。



![](img/ed9838bc3e7c56accd0716c22d0092d6_2.png)

There's a very collegial relationship among the people who maintain these networks。

 That's an important thing to keep in mind， because when you see this no。

 what you're seeing these relationships start to fail is when you're starting to see these large disruptive events of the Internet。



![](img/ed9838bc3e7c56accd0716c22d0092d6_4.png)

And I'm going to talk about the incident involving Pakistan， which is a good。



![](img/ed9838bc3e7c56accd0716c22d0092d6_6.png)

Example because this is the kind of thing that historically the upstream providers of the people who did this sort of gone but。



![](img/ed9838bc3e7c56accd0716c22d0092d6_8.png)

They were not in communications with the greater community at the time。

 and that led to a keystone copereo。The other thing is to talk about what I'm going to inimistically call non optimal routing in this case this is really anonymous routing。

 And we're going to talk about the idea that， you know。

 there's this routing is intended to get you to your destination of fast。

 People have adopted the principles of routing to do other thingses of particular anonymity。



![](img/ed9838bc3e7c56accd0716c22d0092d6_10.png)

![](img/ed9838bc3e7c56accd0716c22d0092d6_11.png)

![](img/ed9838bc3e7c56accd0716c22d0092d6_12.png)

Bart， now。2。First thing to understand， EGP。Is very socially maintainedate does not have a lot of built in security。

 Part of this is B G Ps rare。 You don't run B G P。 Ors with routers run B， G P。

 And in order for you to have a meaningful B G P connection to another organization。

 you generally have to sign some kind of business agreement with them。Okay， this means。

There's effectively a paper trail。It can still be abused and the reason it can be abused is because the internets down on global mediumium and our paper truck gets a bit shoddy once you get outside of the limited area。



![](img/ed9838bc3e7c56accd0716c22d0092d6_14.png)

I want to talk about a particular example of this okay， in 2008。

 Pakistan decided to block YouTube content either Pakistan okay？So the the idea was you know。

 they in front of the content defensive， so they were going to block it at the routing level because if you try to block you know。

 easy for example， proxy service， people just we met that in proxy， they encrypted their channels。

 things like that， Pakistan's goal was okay。We're going to stop the YouTube communication of the rowutdy level。



![](img/ed9838bc3e7c56accd0716c22d0092d6_16.png)

So the way they did this。YouTube announces a partly empty block， 20865-152022。Three active Is。

Actually， at the 1530。S 24。What Pakistan did is it it announced that 24。

Ed redirected it to a black a hole， so this basically means that Pakistan announced that it had a more fine tuned connection。

The the slash 22 that YouTube announces， okay。And according to BGP。

 that is a that gives the route that gives the ans for prey， so how does this so what happens Well。

 if you take a look at this graph， what you'll see is that there are two red dots in the bottom。



![](img/ed9838bc3e7c56accd0716c22d0092d6_18.png)

One of us 36，5，61， which is YouTube tubes， and then 175，57。

 which is Pakistan's newly announced network。 You can see175，57 there。 Okay。

 every other autonoous system on the planet basically starts immediately rounding all traffic from YouTube into Pakistan。



![](img/ed9838bc3e7c56accd0716c22d0092d6_20.png)

![](img/ed9838bc3e7c56accd0716c22d0092d6_21.png)

![](img/ed9838bc3e7c56accd0716c22d0092d6_22.png)

Now。Why did this happen？This happened because the upstream routers from Pakistan Telecom did not filter the announce If Pakistan Telecom had blocked that particular BGP announcement。

 fine。

![](img/ed9838bc3e7c56accd0716c22d0092d6_24.png)

They didn't do that。Their upstream providers didn't block it either and as a result the as a result。

 the message got propagated when this kind of screw happens in the US and Europe。

 there are mechanisms in place for dealing with it because the upstream providers all talk to each other This is Asia which is a relatively new area when it comes to network connectivity they weren't really talking to the appropriate people and as a result they caused a global consequence for their own local action。

And longro there's not much of a solution， SBGP， despite my statement here。

 is not a viable protocol as far as I can tell。

![](img/ed9838bc3e7c56accd0716c22d0092d6_26.png)

All right， so that's how he screw up routing globally， let's talk about anonymity now okay。

That an we're going to talk about because it's example of people using routing for something it was never intended for。

So first thing we need a vocabulary to talk about and the cornerstone of anonity is what we call an anonymity set。

 an anonymity set is a group of people who are indistinguishable and I said I said。

 you're a member of the college students at Hopkins。



![](img/ed9838bc3e7c56accd0716c22d0092d6_28.png)

That's the number of the 100。 That's the number of the thousand。 if you're in 6，9，5，74，1 class。

 that's the number maybe about 20 or so。Okay， so being a college student is more anonymous than being a657 for one student。



![](img/ed9838bc3e7c56accd0716c22d0092d6_30.png)

Okay。😊，Now。There has been a lot of work over the past 20 years in creating anonymous messaging。

The reason for this。Is traditionally to protect against state sponsored observation generally。

and this is generally centered on groups like the Cy unmailling and things like that。

 but the cornerstone of all of these things is what's called a mixed network that the mixed network is a routed network。

Except instead of foreign ring for efficiency， you forward to confuse the observer。



![](img/ed9838bc3e7c56accd0716c22d0092d6_32.png)

Now the classic Wi networks were defined by Alan Sham in the email and traceable electronic mail return addresses with digital pseudonyms。

The idea is that these networks basically on a node by node basis。

 encrypt and signed messages that can then be progressively decrypted and signed by hosts at the far end。

 Okay， Now， why email and then routing because email and routing are both routing protocols。

 and consequently they're fairly similar in that respect。 broadly speaking。

 the difference between mixes and email is latency。

 mixes are broadly divided into high and low latencies。 Nxes email is high latency。

 low latency means that you could expect some sort of within your life Times F and the most noble example being a system called Tore shorthand for the onion router Its the most popular network It makes network in history is developed call Cys native and research lab was actual implementation by Roger Dle died into a group of people called imaginatively enough the tour route。



![](img/ed9838bc3e7c56accd0716c22d0092d6_34.png)

![](img/ed9838bc3e7c56accd0716c22d0092d6_35.png)

![](img/ed9838bc3e7c56accd0716c22d0092d6_36.png)

![](img/ed9838bc3e7c56accd0716c22d0092d6_37.png)

It is a low latency anonym system that places routing with arap。Now， when I say in places routing。

 I don't mean it places BGP and other routing。 It still does route traffic， but within the TCP layer。

 it does the additional layer of additional we of routing。



![](img/ed9838bc3e7c56accd0716c22d0092d6_39.png)

Those's route it， then you route it divide by 4 and dec crypial， okay？

The simplest version is you take your message， you encrypt it with your destination's info and your destination key at that point only your destination can be crypted。

However， what you can do is for every step on the way， you can add in their encryption as well。

 so what they have to do is they progressively decrypt the message until it reaches the destination and until unless you can break open that layer。

 you never know what the next stop is going to be。

![](img/ed9838bc3e7c56accd0716c22d0092d6_41.png)

，Does it work？Kい的。Now as some weak points it his exit nodes。

 it also requires guts to run an exit node。The problem with Tore in my mind is that Torre promises anonymity。

Poor tried switching his anonynuity。Without people acting anonymously。So if you use Tor。

 you've got to pretty much stop using the way this you know it Okay。

 don't visit sites you usually use， don't use cookies， be aware that DNS resolution is a problem。

 don't do anything to reveal your identity。 Do not log on to a site using To。

 or're not live a Facebook using Tor that's just giving your identity away Tom。

And there are other behaviors that users engage in that male also sort heart if you look at the Panoptic click project。

 you can find examples in browser for configuration。



![](img/ed9838bc3e7c56accd0716c22d0092d6_43.png)

Tours are the only mix。There's a called FreeNe， which is developed as an escrow system。

 very high latency， very， I don't even know if it's being used anymore。Crowds。

 which Ive legally obliged to dimension because my thesis advisor wrote it and then mixedmaster。

 these are alternatives as of Dp by free。 So in this class。

 we talked about routing abuse and certain and we talked about anonymity。

 Now the key thing to understand about anonymity here is that it is not optimal routing routing is about getting from point A to point B as efficiently as possible andonymities is about confusing people so they can't figure out where you were going。

 All right。

![](img/ed9838bc3e7c56accd0716c22d0092d6_45.png)

En。