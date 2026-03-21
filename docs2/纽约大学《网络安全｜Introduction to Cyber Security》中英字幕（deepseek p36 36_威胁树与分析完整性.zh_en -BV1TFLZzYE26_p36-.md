# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p36 36_威胁树与分析完整性.zh_en -BV1TFLZzYE26_p36-

![](img/04eed4cda71b0c0cb0c92785d83761ea_0.png)

Hi， folks。For this video， I want to talk to you about something called a threat tree。 Now。

 here's the motivation behind this。 If I were to ask you。

To tell me what you think the security issues are in some system。

 let's say we're walking in a data center together。 You first down the job。

 You're the security expert。 And then once you look at the data center and list out what you think all the issues are。

 That's pretty typical sort of request that you might get。 a lot of you。

 I'm sure are're kind of mulling over the possibility of a career in cybersecurity。

 I would say it's probably a 5050 shot that if you go into cyber at some point。

 you're going to be dragged into some situation。 and someone's going to say， hey。

 what are the security issues here， You're the expert， tell me it happens all the time。

 What generally follows。 is a process that I call structured brainstorming。

 That's where you and a colleague， you go， well maybe it's a problem over here。Problem over there。

What else problem over here。 And then as time progresses。

 you start running out of things that you can find。 So you have problem。

 problem then problem then another problem that you can't think of anymore。

 So you say this is what we found and it's this brainstorming that in my mind。

 gives a lot of security assessments a bad reputation。

 Here's why you have no idea if you got them all， you don't know if you did。

 if you had three other smart people with you。 then maybe you find more。

 So how does that methodology find issues。 And again， issues might be vulnerabilities。

 places for fix， you get the point， just this idea of trying in an unstructured way to come up with these brainstormed ideas of what you think the security issues are around a system。

 that's a terrible way to do the engineering。 It's not something that you've seen in any other branch of engineering。

 other branches， you're building models， you're using quantitative。to derive things。

 you don't build a bridge by brainstorming。 which doesn doesn't work that way。

 So a technique that security engineers have come up with that's admittedly not perfect。

 but it improves that structured brainstorming process somewhat Here's the technique The technique is called the threat tree where what we try to do is categorize issues in a complete or provably complete manner for as many hierarchical decompositions as is possible so for example if we were looking for potential threats to a system would you agree and you probably do because I'm sure you saw in an earlier video we introduced the CIA model So would you agree that if I said all possible threats are either confidentiality integrity availability with the caveat of course that we said that in some cases fraud set aside fraud。

 let's use the CIA model we could say the first level of our threat tree is that the issues are either going to be。

Confidentiality， integrity， or denial of service now。If I can make that claim。Then I can。

 I can posit that that's complete， right， I've I've got a complete understanding that they fall into three categories。

 that cool。 Now， if I could do it again， if you say， hm for each of those three。😊。

I could say potentially that if my assets are， say， hardware， software and information， well， then。

I've got three possibilities for the first three possibilities。

 so it's either a confidentiality of hardware software info or its integrity of hardware software Info or it's denial final service to hardware software In。

 and now I've got nine categories of things that are much more specific。It's not this broad a。

 What are the threats And you just everybody brainstorms。 Now I've got some guidance。

 I can take it another level。 like say let's say I say maybe I'm looking for problems that involve insiders。

 outsiders or combined。So now I've got ninele nodes with three possibilities。

 I now have 27 categories of things that guide me through a more structured process。

 like integrity threats to hardware by insiders。 Oh， okay。

 now I can do structured brainstorming on that。 And maybe I can take a 10 levels deep。

 And I maybe the thousand nodes that I'm actually looking at。 You decide you're the engineer。

 And you figure out what makes sense。 This is an improved way of trying to make sense of cybersecurity issues。

 Look。Cybersecur is about lists and groups and sets and categories。 That's what it's about。

 It's about coming up with a set of potential problems and then having solutions to those problems。

 That's what we do all the time。 I'm sure a lot of you who maybe have dabbled a little bit in cyber hacking and so on and so forth。

 You understand the power of keeping track of vulnerabilities。

 tracking lists and having categories of vulnerabilities and knowing what the different attributes are。

 you know what systems they apply to and how long they've been in place and which patches apply。

 it's a very taxonomyoriented kind of discipline this business of doing cybersecurity in a practical setting。

 So you can see how a threat tree can provide some hierarchical ordering and some structure through that decomposition to maintaining completeness as we try and keep track of issues on a system。

 So think through that。know， maybe for sort of additional thinking as you go off and ponder this lecture。

Think through how you might categorize or virtually anything in your life in terms of a stepwise decomposition where you maintain completeness as long as you possibly can。

 And then you can do some sort of brainstorming at the bottom。

 So I hope this has been a helpful introduction to one of the tools that we find very useful in doing system security engineering。

 thanks。😊。

![](img/04eed4cda71b0c0cb0c92785d83761ea_2.png)