# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p95 6_TCP序列号攻击.zh_en -BV1TFLZzYE26_p95-

![](img/837a246705adf9481aed2b9ec0140307_0.png)

Hi everyone Ed Emmarosso here， and I want to talk to you about an internet protocol attack。

That kind of doesn't work anymore。But it illustrates some properties of TCPIP that I think are useful to exercise in our mind now where a lot of this came from the 1990s。

 very fertile time for internet protocol attacks and there was actually a hacker who was kind of notorious。

 interesting guy at the time named Kevin Mitnick who launched an attack that a lot of a studied it was kind of interesting。

 not sure that he invented it， but he certainly made a famous called a sequence number attack。

 here's the way it works and here's what it's predicated on back at the time。

 certainly in the '80 when I first started doing internet work。

It was this concept you're going to think this is crazy。

 but you would actually keep track of computers that you'd have a trust relationship with the internet was a lot smaller then and you were perfectly willing to say I trust that machine essentially trusting their source IP address。

 you can see probably not the greatest idea but you'd have a name and again it might be domain。

 but the main thing is you'd have a trust relationship so that if for example。

 if you're Alice and you want to connect to Bob but you know Bob's not going to let you connect but you know Bob has a trust relationship with Bill。

Then if you could somehow convince Bob that you are Bill。

 then you'd be able to set up a connection and lob a command like hey， you know。

 give me a root shell or something okay so you get the idea I'm Alice。

 I want to connect to Bob Bob has this trust relationship so if I can get a session set up where Bob thinks he's connected to Bill then that's great now there's one other problem here that existed years ago that this attack would take advantage of and that's that S sequence numbers and synax sequence numbers we're not always random like sometimes the protocol stack would go e。

1 thousand0， 2000，3000，400 is the sequence numbers。

And the assumption was there's so much traffic and a lot of things going on。

 people connecting all the time and it's essentially random because I'm just incrementing some number。

 it was just an easy， convenient way to implement now if you had a very quiet system and you were connecting then there wouldn't be a lot of sequence numbers for a lot of different users you'd be the only user so what Kevin Mitnick did was he was attacking I think the San Diego supercomputer center server。

But he did it here in the United States on on a holiday And it's the Christmas Eve。

 So the idea it was its not gonna be a lot of traffic into the server。 And he knew that that server。

 how to trust relationship with a particular machine。 Let's call it Bill。

 and we'll call Kevin Mitnick Alice。 So what he would do is as Alice throw a sin packet over and watch the S Act come back。

 Now， keep in mind。 TCP does not do security when it sees a syn packet。 Now。

 maybe there'll be a firewall in between at the time there wasn't。

 So you throw a sin it's thrown a S act。 once you establish a session， it might say， well。

 I need to pass word， all this other stuff。 But to just get a packet。

 a packet respond you basically anybody。 So Alice Miniick would go。😊，Here's a sin。 Watch the S act。

 and let's say it's 100。 Okay，100。 Then here's a sin S act 200。 again， Christmas Eve。

 there's not thousands of others doing this。 You're the only one。 write that damn。 Then here's a sin。

 Watch the syn Act 300。 You get the idea 100，20，300。 fortunate， Let's see you did that to 1000。

You did it 10 times you're pretty convinced you know what's coming back now what you do is you send a packet as bill Bill's source IP。

You send it。But the S Act goes to Bill。But it doesn't matter because you know the S accent 1，100。

 so you now act。With 1100。 and you've got a session set up。 Isn't that clever。

 It's a sequence number text now yeah， it doesn't work anyway。 You don't have trust relationships。

 Pro stack developers don't do things not randomly anymore the better better software。

 There's firewalls in between you know you and most servers。

 but it's a very illustrative attack to think about simply because it gives you the idea that when you make a mistake。

 you do a bad implementation， some hacker somewhere is going to notice they're going to take advantage of that。

 they're going to come up with something clever and you're going to be stuck with a situation where you can hardly believe that someone was able to take advantage of a situation that you created that resulted in a security compromise。

 So I hope it's been sort of useful little example for you。

 think these things through try and think through as you ponder your understanding of TCpiIP。😊。

What sorts of things you would attack and what sorts of protocol weaknesses exist a lot of the interaction that we have。

 not just in computing， but also in your personal life， so I hope you enjoyed it。

 we'll see you in the next video。

![](img/837a246705adf9481aed2b9ec0140307_2.png)

![](img/837a246705adf9481aed2b9ec0140307_3.png)