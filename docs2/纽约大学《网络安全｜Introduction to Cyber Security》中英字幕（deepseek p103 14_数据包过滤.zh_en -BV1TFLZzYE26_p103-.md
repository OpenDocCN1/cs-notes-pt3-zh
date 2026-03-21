# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p103 14_数据包过滤.zh_en -BV1TFLZzYE26_p103-

![](img/5f358a11478344e9ab32897e00414f64_0.png)

Hi everyone Ed Amarosso here， and I want to take this time on this video to introduce you to something called packet filtering。

 which is absolutely fundamental to real time cybersecurity。Turns out that for many years。

 companies and homes and businesses and everybody would connect to the internet through a device called a router。

 you'd have one given to you by your ISP or you'd go buy one whatever made sense。And the router。

Really was designed to move packets， I mean， routers are devices that were invented， to move packets。

 to move TCPIP packets from one place to another， they come designed with rules and what happens is packets hit and on an inbound interface to a router and the router generally has rules that are put in place around what to do with the packet。

 meaning where you route it so you can think of it as the workhorse that makes the internet run and there's companies Cisco systemss。

 juniper systems， some others became very popular and became very powerful and successful and the late 80s and into the 90s and 2000s to the present time building wonderfully powerful and feature rich routing equipment。

 but it turned out that everybody kind of noticed that if you had a device。

 a router that's sitting there doing what。I just said。You went。

If I'm going to make a security decision。Why not do it there。 I mean， there， right。

 If it's already doing rules， Could't I add some rules there that just say， hey， you know。

 is this allowed or not allowed？ Now， there's design decisions that come with that I mean。

One is if the main purpose for that router is to be fast。

 like if you're an Internet service provider and it's a core router that's moving lots of stuff。

 maybe you're not going to be okay with that。 you might say， hey， listen。

 Anything that slows this thing up， forgett it。 you're not going to put any stupid additional rules in this this thing has to move。

 this has to smoke。 this has to be pushing packets fast。

 but there might be others where it's not as big a deal， for example。

 the router that's sitting on your desk connecting to your ISP。

You know is it really important that you preserve every microsecond of processing on that thing。

 Probably not， even if you're a gamer， it's probably not going to be a big deal。

 So kind of in the 90s we started realizing its a little earlier。

 but could commercially started realizing that you could write some very simple code to a router called a packet filtering。

 I'll pop up a picture here， it shows Alice and Bob with a little firewall。

 there's typically to show firewall we show the large vertical tower there with the supposed bricks that are in the icon and you can see a syn packet going from Alice to Bob and the code that would be on that firewall router。

 that big tower would be a big if then else， and you can see the code if the packet header has the abit set to zero。

 then that's the beginning of a session then look and see what's going on is what's the source IP。

 what's destination IP with sourceport and then。Decide whether allow a block and that would be just you decide as the coder if it's port 8 and you don't want people hitting your web server then you drop it if it's port 80 and you're okay with people hitting your web server you allow you get the point that would be the rule and then you say if the packet the aPt is one let it through or you could drop it or something else you're the designer you figure out what kind of rules make sense but generally in a packet filter。

The only options you're going to have are to allow our block。

You can let the packet go through or you can kick the packet off into the garbage， A or B。

And you have to have some sort of condition that drives that。

 so these are logical conditions that are examined in sequence。

And it's just sort of an artifact of the way these things were originally developed。

 that you'll develop a first rule， a second rule， a third rule， all the way down to an end rule。

 which we call the default rule。Meaning you got to put something that matches something。

 you can't have a device that just never matches and you can write these rules， nothing matches。

 so every router will have a default that will always match and either a lower block will get to that。

But that's packet filtering and you can see that。Designing what you'd like to be these rules can be a little tricky。

Making sure that you don't impose some kind of performance penalty on the router can be tricky。嗯。

Kind of connecting your intent of what you want the policy to be with the real implementation can be tricky。

 Do you follow having multiple routers， maybe from different vendors。

 and imposing the same implementation， same policy can be tricky。 This is not easy。

 I remember the Cisco systems telling all of us back in the 90s that if you wanted to learn to configure routers and to do packet filtering and so on。

 They said， you should take our beginner's course， which I did was a one weekek course。

 And they said， then go back and work for two， three months， full time with a router。

 then take our intermediate course。 then go back and work for about six months of a router。

 And now you can call yourself a beginner。 remember it sounds like a lot of work to get to be a beginner。

 but you get the idea this is not simple snap stuff。

 and I do understand that some of you may write some rules for your home router。For a business。

 it might be a slightly more complicated， but the bottom line is that this。

 this idea of putting the rules into the router was a good idea。

 So let's do a little quiz to test our understanding。 Now， the answer is D。

 And some of you may be saying that's not fair。 You didn't tell us about forwarding。

 but this is my way of introducing the concept to you。

 It turns out that there really are three options here。 I can allow it。 I can block it or。

I can send it somewhere and say， I'm not sure that's what makes this interesting。

 if a router can only pass or block， we've got problems， but if I can program the router to say。

 I need more information than all of real-time cybersecurity is enabled。

 this is how we have cybersecurity you know intrusion detection and prevention and surveillance and data leakage prevention。

 all these different types of capabilities are enabled by the fact。

That sometimes we're not entirely sure we can forward packets and sessions to intermediaries that you'll see pretty soon we're going to call proxies。

 but for now we're going to stick with packet filtering on our next video I'll teach a little bit more about how you do it I'll see you on the next one。



![](img/5f358a11478344e9ab32897e00414f64_2.png)

![](img/5f358a11478344e9ab32897e00414f64_3.png)