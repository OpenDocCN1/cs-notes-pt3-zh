# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p111 22_应用代理过滤.zh_en -BV1TFLZzYE26_p111-

![](img/4214e001d8229ff742ddad4b58001a9c_0.png)

Hi， folks at MROso here， now let's talk about a concept in real time network security called a proxy。

So what's the idea of a proxy It's kind of a go between in attack parlance we would use that there're a man in the middle but the man in the middle usually implies something nefarious or bad proxy is the same thing。

 but it usually implies good， does that makes sense like if I'm arbitrating between A and B and I'm benevolent。

 I'm doing something good then I'm a proxy So A thinks it's talking to B。

 but it's really darking you and you're somehow operating on behalf of B， maybe even invisibly。

 but if you know you're a hacker， then it's a man in the middle attack。

 but for the most part it's the same kind of thing。But look， I mean， when we design firewalls。

 we do this intentionally and you'd never think of it in some senses of any kind of man in the middle becomes a device that's implementing policy。

 So here's the idea。 you remember when we talked about packet filtering。

 we came to the conclusion that there's really three options for a packet filter。

 the first thing you can do is block。The second thing it can do is allow The third and most interesting thing it can do is forward。

 So what that means is I can actually create an arrangement。 I show it on the screen here。

 where Alice and Bober connected through a packet filter， probably a router。😊。

And that packet filter itself is connected to something called an application proxy。

When a packetca comes through。And the packet filter sees that I don't know。

 whatever is going on that it just doesn't want to make a decision about。

 let's say it's remote access or it's some it's just going to see a destination port and it might see a destination port that has something to do with remotely accessing or our login telling that these are old examples of how you do it they're more modern versions as well。

 sees that。And says， I can't make a decision。I need you to type a password to something now can a router read a password no。

 but what it can do is it can forward a packet to a program that's running on a computer at the application level that can serve as a proxy for B。

 so A thinks it's hit B， but it hasn't， it's hit a man in the middle that goes A。Type a password。

Here's a number， what's F of this number， What is your do a little puzzle for me whatever any crazy thing you could imagine or it might be just doing a log of what's happening and then passing it through that the possibilities are endless around what you might do。

There are a couple of different ways you can do this。

 one is I can instrument a with special client software that can connect to the proxy。

 everybody hates that， you know that's an agent。Full or an agent based or a client affecting or client changing implementation。

 What we like and said is something that doesn't affect the client in some sense。

 allows you to have an agent list or a client change free environment with client just thinks it's doing what it's doing and it hits that proxy。

 So think of those two things together， packet a filter in the application proxy， in some sense。

 as a firewall and a lot of products that are out today that really are very much that that just have at the lower layer。

 making some packet of filtering decisions about whatever it can make， for example， if I see。

Something that I just know is okay， I've decided it's okay。

 maybe it's the network time protocol or something。

 and I know that I always allow network time protocol packets in and out。

I don't need to pass it along to a proxy。 I've already decided ahead of time that we're gonna to just go ahead and let that through。

 but everything else forward up to the proxy， In fact。

 maybe everything gets forwarded to the proxy or maybe I make the decision that certain source Is。

 I'm going to somehow trust and let's say you outsource something to the Albanian country of whatever which you know does call center operation for you and they tell you that this is their source IP addresses。

 you don't really trust that， but you're going to say， well， all right。

 you better stay on those source IPs because the router is only going to accept packets from there I'm going to forward you to a proxy。

 you're going to do something before you get the network but if I get stuff from any other part of the Internet。

 any other source IP， the routers just going to drop it。

 Does't that rock like it gives you all kinds of cool building blocks that you can use to implement policy。

 it's powerful and it's kind of。Sing。All of a sudden these tools you're using allow you to design secure networks。

 you implement policy， make you get wrong， right if you get it wrong， you have a big problem。

 let things leak in and out， that's a disaster。 you can't allow that but the design of sort of layer1。

2 packet filtering， layer 3。That's really， really powerful when it's combined。

With the application logic that you'll get in a typical firewall there's a whole industry that's emerged in the last 20 years selling this kind of thing with this idea of pack and filtering and proxy together。

 extremely powerful companies like checkpoint and Cisco and Juniper and on and on and on and on have developed capabilities that are just amazing and they're even more powerful ones that are called next generation firewalls from companies like Fortignt and Palo Alto networks and so on really。

 really exciting that have lots of capability and things we haven't talked about in our videos yet。

 hopefully you'll stay with us and you'll see some additional capability but when you pack into that application proxy。

 a lot of interesting capability， some really， really really useful cybersecurity。

 defensive mechanisms are enabled and I hope that's been useful for you and I'll see in the next video。



![](img/4214e001d8229ff742ddad4b58001a9c_2.png)

![](img/4214e001d8229ff742ddad4b58001a9c_3.png)