# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p148 11_欢迎Roger Thornton第1部分：AlienVault首席技术官.zh_en -BV1TFLZzYE26_p148-

![](img/f0a652245a8c9a8a876cf9d5693d3005_0.png)

Hi folks at Ammarossa here and I'm sitting with my good friend Roger Thornton who serves as the chief technical officer for alienen Vault。

 which is one of the cooler names of a cybersecurity company there's a little story behind that name maybe we'll get to tell you today but thanks tell us we tell us where did that alienen  Vault there really is a cool image alien  Vault was started by a couple gentlemen in Madrid Spain and it was started theres a point in time I don't know exactly when it was probably in the mid-1990s and all the cool names were taken。

And so this is when you had kind of invent names and they decided they wanted their name to be serious and playful。

So they created a list of playful names alienen was in that list and they created a list of serious names Vault was in that list and they wrote a computer algorithm that went through and it got to alienen and it got all the way down to Vault in the algorithm would go search the trademark registrations。

 the corporation database， the internet registrations and that was the first one that's fantastic I wonder if people name their kids that way like first the your first in your middle name you stuck with your last name but it's a great idea there's a similar story how my son became Alexander。

 but I' going to believe that is we'll do that in a subsequent video so tell us about yourself how'd you get interested in computing and ultimately in computer security Great Well computers and I would say engineering more in general is easy I grew up you know on an Air Force base in the 1960s and the first time I saw takeoff and definitely remember。

First time seeing some of the NASA gear and the rockets and stuff。

 I had no I was probably three or four years old and I didn't know what an engineer was。

 but I knew I wanted to make that stuff， right？So fast forward to I went to school in the 1980s。

We weren't doing a lot with spacecraft anymore， and I lived at that time right in the middle of the Silicon Valley。

So the big thing was computers， kind of lucked into it was the local industry。

 and so I start off as a semiconductor manufacturing engineer。

How you go from that to security is a strange story。

 but one of the great things about the Silicon Valley is。

It constantly changes itself to meet the needs of whatever the next new thing is。

 so I like the place I lived in we went from semiconductors to computers to software and then internet became the big rangeH and I worked in that arena。

 but when I did I work in the internet I worked for online brokerage firm called ETade did a work for eBay and at that time was the first time that I'd ever experienced crime against the products that I made and I also made some egregious errors at that point I was a development manager。

Years later， I would learn that some of the mistakes that we made in the authentication system on system works would be used to be a compromised system。

When all of that hit me， a friend got me really interested in security and he got me there actually a friend that you know catchline we were having the venture capitalist yeah so we were having lunch and you know。

 talking about ideas for startups and have you and he doggedly，Over a period of time。

 pursued me on this issue and， and his perspective as a person that had spent most of his career in computer security。

 And then as an investor had invested numerous security companies， he felt this sense of。

Guys like you software people you' you're building this stuff and then guys like us the security guys are trying to protect it and you know we're talking in like 19992000 right and he was reaching the point where he was starting to think。

The stuff you're building just can't be protected， we've tried and tried and tried no matter what we do can't seem to do it so let's talk about what are you guys doing when you're building it and I didn't get him the first few times he brought that up but he asked me a question that he became obsessed with。

And he said。🤧Tell me， what is a firewall made out of。And I said，Well。

 use a software and he had this aha。Why is it that the firewall can be on the open internet and suffer the ravages of everything thrown against it。

 but heaven forbid of the word processor or the banking system or any other piece of software。

 why does this one software need to protect the other why can't the other be built in the same way and as technical guys often do I gave them some answer that was not correct with just to move them on？

And I started to think and think and think， and of course I learned that firewalls are compromised every so often。

 but that ultimately every break in to a computer system，For the most part。

 I qualify this can be driven back to either design。

or coding mistake in a piece of software and you might say， well wait a minute。

 there's end users and they do stupid things but we're designing software systems and users are part of the system software should compensate for that so my first foray into computer security was a company called Fortify So my first customer IT and in that company like any good engineer and this is some advice I would love to give to folks that are taking this class。

As an engineer， when you first approach security， you're going to think about solving the problem the problem。

 if I understand the requirements and can interact with the problem enough。

 I'll fix it and if you're fortunate like myself to early in that endeavor。

 meet somebody with a law enforcement background，They will tell you and teach you that computer security is not a problem like most engineering problems。

 it's crime。And。For the most part， no place on earth have we solved the problem of crime。

 crime exists， where human beings endeavor to commit crime and they apply their their intellect and their vigor and energy they'll prevail to some degree。

 So crime is something we manage， We manage it to an acceptable level。

 We never really solve it because the cost of solving is。

Infinite right so when I first went into computer security I didn't know that and so I went about how do we solve this and the idea at fortify was well if we simply just built the software better。

From a design and coding point of view， we would anticipate the behavior of bad actors。

 we would build code that didn't have things like buffer overflows insQl injections and all these very common patterns that allow people intrusion。

And so we set off to do that。We made an impact。But as you can imagine。

 not every piece of code in the world is built to be resilient from a security point of view。

Even though it may end up being critical in what it's deployed to do。

 so we're at a state today where。Every major bank in the world is building code that's pretty well tested and rigorously designed and built the telephone infrastructure is that way。

 a lot of DOD systems are that way， but that might be 10% of all the systems on earth。

And a company like I you know， don't want to pick on somebody。

 but you know the next social networking company to come out of the Silicon Valley or virtual gaming company to come out of Silicon Valley will build something that doesn't seem to need the rigor that a banking system or communications infrastructure needs。

And it probably won't be built to be to withstand every form of attack that we can envision and then it'll become critical once it becomes critical we have the same problems。

 so once I really got my head around that， which was we could build software better。

 but we're never going to build it perfect。And a preponderance of the software is just simply not going to be built with an eye towards security I moved my interest in the security problem in managing that problem to the area of detection and response and'm。

I don't know if you guys have covered， but I'm sure you have or we will。

 the NIST framework protection， try to protect your systems。

But NISist is the US National Institute of Standards and Technology and the framework you references a set of requirements to help companies improve their security right right so sorry to interrupt oh no thanks thanks for clarifying that and the model that they have this protection detection response's it's I think one of the most important models out there to get your head around if you're really and building a great security program and so spend that time in protection and。

Proved to myself that things that people like yourself knew for the years before I got involved in security there was no way we're going to protect these systems completely Okay if that's the case。

 then what's another model that we can apply to security and frankly it's the same one banks have used for years So if you think about your favorite bank and the branch in your neighborhood。

You don't try this at home， but you could rob that bank and the chances are you're going to get away with。

The act of going in and taking money， in fact， the bank's going to help you do it。

 they're going to facilitate you get you out of there。

Now the probability that three weeks later you're enjoying that money at home is pretty close to zero and the reason for that is the banks have looked at that and concluded it is impossible for me to protect the branch to the point where it can't be robbed and when they describe this to you they said that could be done。

 it would no longer be a bank branch， the primary function of a bank branch is to move money in and out to the local community that it serves and if you really secure if you protected to the point where it couldn be robbed。

 it would no longer be serving that function so as crazy as it sounds。

 the better approach is to put the protections in place so that it's not being robbed on a regular basis。

But the detection capabilities employed by the banks and law enforcement with the help of telephone companies and computer makers。

Everybody else involved is such that were you to commit that crime？

The detection capabilities of knowing who you are where you went afterwards are such that that's adequate in terms of keeping the bank safe And so you know it's funny that that model's right there in front of all of us it's one of the oldest ones there was person explained all that to me was an executive at a bank who told me banks have been around for about 3000 years that been being robbed for 295 some odd years and this is really a group that we can learn a lot from in terms of combating crime So this idea of fine you' you're gonna to get in but if I can detect you。

And respond before any real damages happened。 I meant， you know， I basically， That's。

 that's really fascinating。 Hey， we're going let everyone take a little break here。

 We come back and do a second video with us and continue on those themes。 That's great。

 I hope you've enjoyed Part 1 with my friend Roger Thornton。

 and hope you'll come back and watch our second part， enjoy。😊。



![](img/f0a652245a8c9a8a876cf9d5693d3005_2.png)

![](img/f0a652245a8c9a8a876cf9d5693d3005_3.png)