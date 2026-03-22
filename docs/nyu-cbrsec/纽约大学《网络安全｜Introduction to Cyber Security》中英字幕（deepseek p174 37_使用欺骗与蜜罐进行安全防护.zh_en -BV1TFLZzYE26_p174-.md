# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p174 37_使用欺骗与蜜罐进行安全防护.zh_en -BV1TFLZzYE26_p174-

![](img/85cea1417bc26d3a5bea7d8cac5cf74e_0.png)

Hi， everybody at Amorosso here。 and I want to talk to you in this video about something called deception in the context of cybersecurity。

 deception meaning fake lures， honeypots， a lying trickery to try and catch bad guys。

 one of my favorite stories here about a cable company kind of in the New York City area that I had some involvement with some number of years ago I'ved been speaking with them wasn't a place where I was working。

 but watch what they were doing， thought it was clever。

 The idea was that in those days maybe 20 years ago。

 you could take the set top box off a you a cable company provided end user appliance to get analog broadcast。

And you could find the CPU of the set top box and read the number， pop it out。

 go on the Internet and buy the same number。 But they always gave you the option of buying the same number with a T after it a test version。

 It mail to， you put the test version in， put the top back on and it decrypted deccrambd everything。

 You got all the paperview channels， all the sports events， you know， everything for free。

 So the question that this company was thinking through。 And again。

 I remember sort of being involved in looking at this and think of what how would you solve something like this。

 But what they came up with was an idea it was very clever during a heavyweight boxing event。

 They came up with the idea to put a banner message across the event。 but to scrambled it。

 so that if you were buying the event， you'd see a scrambled message。 It's no damage。

 you'd just you're watching the event and you see scrambled gobbledyg， you'd just shrug no big deal。

 But if you had the chip， it decrypted everything and you'd read the。And what the message said was。

 hey， welcome to this big prize fight。 Thanks for buying it。 Hey， we're giving out free t-shirts。

 If you give us your name， phone number， address， blah， blah， blah。

 we'll mail a t-shirt and they got something like 8000 people mailed in for the t-shirt and they caught them。

 know，s isn't that cool。 they're using deception。 They're using trickery。

 they're using this idea that operationally it's not just a matter of putting cryptography in place。

 But if you're dealing with an active attacker， why not be an active defender。

 So the architecture kind of in support of these things for the most part is that you have authorizedized and unauthorized users。

 hackers。😊，Going through your normal security stuff attack detection prevention。

 and if there's a suspicion that there may be something funny going on。

 Po might be that you would take that hacker if you're accurate and divert them to fake content we often refer to as。

Honeypot content。 It's a duplicate of your system， but it's not it's not real and it's there to kind of trick them into sticking around and trying to hack and you're watching and you sound alarm bells。

 you like to think of it as sort of a jail。 This is a really powerful concept and virtualization really helps with this like the example。

 that for example， a hacker running a scanner if you detect the scan and you say this is not reasonable。

 You could use a virtual network to open up a fake network into which the scanner emerges and never returns。

 you know， you just keep building more and more and more。

 and more and more fake network and the scanner just keeps chasing it。

 we call that a tarpit because in some sense you've caught the scanner and something that it'll never get out from。

 These are fun， interesting techniques。 I think this is a really wonderful and vibrant area of cybersecurity it's something that if you're watching and you're considering a master's program or。

HD or you're doing research。 We don't have anywhere near enough work in this area。

 And this is how you catch bad guys， like the way we catch people on the Internet。

 doing you know inappropriate things with young people， for example， is on the other end。

 they think they're talking to a youngster， it's actually some FBI agents faking to be that youngster and they usually trick and nab the perpetrator。

 it's a very effective means for catching bad people。

 and I think it's way too underattended in cybersecurity。

 So I hope that as you consider architectures and designs and implementations and anything you're doing in and around cybersecurity。

 I hope you'll try and factor in some level of deception， deceptive use。

 this attack kind of detection via lures and honeypots as a component of your strategy in reducing risk and whatever it is that you're trying to protect and certainly if you're doing critical infrastructure protection。

 This is a useful measure。 I hope this has been。Introduction for you。

 and I'll see you in the next video。

![](img/85cea1417bc26d3a5bea7d8cac5cf74e_2.png)

![](img/85cea1417bc26d3a5bea7d8cac5cf74e_3.png)