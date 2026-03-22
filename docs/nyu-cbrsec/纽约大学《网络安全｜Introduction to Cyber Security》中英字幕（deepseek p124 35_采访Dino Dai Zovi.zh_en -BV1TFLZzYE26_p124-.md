# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p124 35_采访Dino Dai Zovi.zh_en -BV1TFLZzYE26_p124-

![](img/f400fa6312d03edb2a69dfb9f428793b_0.png)

Hi， folks， I'm sitting here with my friend Dino Daovi， the chief technical officer of capsuleite。

 how's goingino good great Hey， so you work for company that focuses on Linux security。

 seems like that's a big area particularly data center how you guys get into Linux security to see the problem or what sort of was the driver We saw the problem and we also saw this shift in technology stack as bigger companies。

 especially companies in Silicon Valley were building their production environments。

 they went naturally with Linux because it allows them to have a deeper level of control where everything becomes software defined and this became the architecture of their production environments and we saw this actually shifting to everyone else with the cloud and with containers and going to more traditional more security oriented enterprises and we saw that a lot of the tools that they had been used to and at their disposal were just not a good fit for this new technological wave being ushered in by their engineers by ops people and kind of by the market。

in itself。 And so we wanted to create better tools for them。 That's awesome。

 Now you're an example of somebody who comes to cybersecurity with a background in development and in hacking you have some background there Tell us a little bit about what kind of got you interested in cybersecurity in the first place。

 Sure first， I want to tell people what I think hacking means So hacking means finding the creative solutions to things。

 I mean， solving puzzles it doesn't mean trespassing right So when I say hacking that's what I mean and I've been obsessed with the kind of the chess game and the puzzles of computer security since that was like 14。

 So that's been my background and growing up with the internet。

 the best thing about it is that all this information is at your fingertips。

 you know the security community back then was very open with information So they published zines with how tos and how this worked。

 how these things failed and you could really learn everything you wanted from open mailing lists and all this all these resources and that's really how I got into it。

 and when I got started there wasn't。Really a career path。 But I knew who my heroes were。

 I knew was like I can get paid to legally hack into companies like that's awesome like that is so cool like you know I don't have to worry about stressing out like this is cool and that's what I don't want to do at that age Can you be a competent hacker without having some understanding of Uniixbased systems like Linux and Android and so on。

 you think that that's kind of a prerequisite I think it's a prerequisite because what I always saw hacking as is understanding a system better than everyone else。

 So if you are looking at technological systems， you have to understand it better than the people that built it。

 And when you can do that then you can work your way around it and navigate it。

 you can essentially surf。😊，And you know， there's always an element of social engineering as well。

 but that's not just understanding people， you know。

 and how to kind of navigate that system if someone came to you and said the following。

 tell me what you would say in response if they said， hey。

 Dina the way I'm going to protect my Linux system is I'm going to scan for all the vulnerabilities on it。

 what would be your what would be your response to that I say that's necessary but not sufficient。

It's a good start。I think I'm prodding you here I think we have an obsession with vulnerabilities in the industry because they're very concrete and we can feel like we're making motion without progress because what's really important are is defending against attacks and vulnerability is just the first stage in the attack first there's a vulnerability than someone has to figure out how to exploit it they have to be able to find the target acceptable to it。

 they have to be able to know choose that target and once they're in they have to be able to find the information they want and they have that information has to be value to them if we think about this entire chain from the side of an attacker。

 whether regardless of what their motivations are we can design better defenses。

 we can make our data inaccessible to them or not useful to them。

 we can make our systems more expensive for them to attack or we can just become better at identifying their attacks and taking evasive corrective action when we think about all these things and it just becomes very easy to count vulnerabilities and to assume that we can find and fix them all。

But I think that is just not a tenable strategy No I've heard you say before that improving development。

 improving the development process is really the correct thing is that your thought that need to prevent vulnerabilities in the first place if that's really the way to do it I actually focus these days more on kind of the deployment environment I think of it holistically because it's really difficult to write bugfr code and if it's almost impossible and attackers can analyze the code offline and find that one that one weakness possibly using an entire cluster full of fers and just you know they get to spend all that time and the attacker has no or the defender has no idea when the attack is coming bugfr code I think as a poor strategy for that and I like figuring out how to shift things in the defenders advantage by putting a lot of the information they have to learn online now so now whenever the attacker tries to attack the system。

And they make their activities known and that when they're trying to figure out how the system works that is a heads up to the defender and that actually I think really makes better defensible systems more of a reality when you have better visibility into what's going on in your environment and what should be happening and what shouldn't be happening you think Linux is a good operating system absolutely you do Yeah what makes it good what I think its core strength is is its malleability because one of the things I like to think about is how do we get better at getting better and that means decreasing the latency of our iteration cycle and our learning cycle and with with Linux because everything is open source you can make the change you can deploy the change and the community moves a lot faster and the way that people are deploying Linux now in the cloud means they can update their kernel almost seamlessly which was previously a very difficult operation it just happens behind the scenes when their AMI on their auto scaling job is rebooted and。

As we move closer to that approach， we can learn from attacks and have the fixed deployed much quicker。

 we can make our environment a moving target so that attackers can't learn it and so that defenders are attackers have to keep pace with defenders versus the other way around Intering。

 you know， question we love to ask。Our guests as part of the series here is their level of optimism around cybersecurity kind of as it unfolds what do you think do you are you more worried and more optimistic about kind of the near and longterm future cybersecur Overall I'm optimistic because what I've seen over my career is yes I've seen a lot of breaches。

 yes I've seen a lot of systems that are hackable or compromable but I've seen us get better and I've seen us build popular largescale systems like my favorite is ios favorite example of this there is a strong amount of security in this system that we used to think that a few things one no secure system will ever be popular among consumers prove that false you know once you have physical access to a system it's always game over it also proved that false and so we're making progress and as we keep making larger pieces of our technological infrastructure defensible enough so that we are safe and I put a big difference between safety and security because。

Security means that no attack is possible safety is means that for the attacks that you care about。

 they're not going they're most likely not going to happen and that's what we really care about in making more parts of our infrastructure defensible and so that our digital communications are safe so that our personal information online is safe and our businesses are safe that's what internet security is really all about interesting。

 you know one last question I want to ask on behalf of the community here if people watching want to learn more about Linux in general what kind of advice would you have。

 should they be downloading it to a PC should they be reading something online what would your advice be。

What my advice now would be one download it to your machine。

 but get into the cloud as soon as you can you know there are free tiers on most of the cloud cloud infrastructure companies and for where people's careers are headed it's absolutely gonna be based on the cloud over the next five to 1 years and so in the old days it would be get a shell account get a shell account Yeah now let's get an AWS account launch Kubernetes start playing around the clusters because the computer is now the data center right it's not just a single node and the operating system that matters is the framework that you used to manage that whether it's a large scale on-prem cluster and a big company or it's a mix of you cloud cloud infrastructure because what in order to tackle the jobs that we're going to be tackling and kind of in computing over the next 10 years we're gonna need to scale the amount of computers way faster than we can scale the number of people and that count for security as well we need to amplify the expertise of the people we have。

Not just keep throwing more people at the problem so that we can scale our expertise to the problem we have and we can scale our human capital to the computational size of the problems we want to tackle that's great advice and good marching orders for our whole community here Hey thanks so much for taking some time and sharing with us thanks for having me you bet and we'll see on the next video。



![](img/f400fa6312d03edb2a69dfb9f428793b_2.png)

![](img/f400fa6312d03edb2a69dfb9f428793b_3.png)