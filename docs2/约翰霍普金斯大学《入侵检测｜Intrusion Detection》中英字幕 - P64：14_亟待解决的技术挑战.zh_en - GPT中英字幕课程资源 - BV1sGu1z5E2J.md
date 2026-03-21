# 约翰霍普金斯大学《入侵检测｜Intrusion Detection》中英字幕 - P64：14_亟待解决的技术挑战.zh_en - GPT中英字幕课程资源 - BV1sGu1z5E2J

![](img/7135582bf3ff9894f3a78769201f36de_0.png)

So in this video， we're going to talk about the IDS IPS technical challenges that still have yet to be resolved within this technology for it to do everything that we would hope an IDS system would do Now you're going to have seen a lot of these technical challenges brought up in previous modules as we talked about the various problems in the classifier as we talked about problems and sensors and coordination and in response。

 but this puts it together in one place to say here are a series of technical challenges that were these technical challenges resolved。

 the IDS would have much more potential at actually detecting a lot of the kinds of threats and problems that we've seen over time。



![](img/7135582bf3ff9894f3a78769201f36de_2.png)

![](img/7135582bf3ff9894f3a78769201f36de_3.png)

![](img/7135582bf3ff9894f3a78769201f36de_4.png)

And as you might expect， these challenges range from highly distributed coordination of multiple different kinds of IDSs to very localized problems of what do we do with mobile computing and the internet of things。

 but this does bring together both sort of the large and the small in terms of areas that are still active in research today and active in commercial tool development。



![](img/7135582bf3ff9894f3a78769201f36de_6.png)

So first， as we've talked about， there's a lot of difficulties out there with taking heterogeneous and widely distributed IS and IPS systems and putting them together in some sort of a cooperative structure so that we can use the IS I sensors and the different kinds of classifiers in concert so there is some work underway in sort of trying to do loose coupling between IS IPS systems so what do we mean by loose coupling。

 loose coupling is rather than try to make a monolithic single IS IPS systems that does everything。

 How do you get a number of different types of IS I systems to work together so that their common data set can be used together。

 the hope here is that you can have very detailed and specialized IS IPS close to the target。

 And then as you get farther and farther away。

![](img/7135582bf3ff9894f3a78769201f36de_8.png)

![](img/7135582bf3ff9894f3a78769201f36de_9.png)

![](img/7135582bf3ff9894f3a78769201f36de_10.png)

![](img/7135582bf3ff9894f3a78769201f36de_11.png)

![](img/7135582bf3ff9894f3a78769201f36de_12.png)

![](img/7135582bf3ff9894f3a78769201f36de_13.png)

All of the different targets be able to consolidate these together into a consolidated system that would together be able to understand the full range and breadth and scope of any particular attack that might be going on。



![](img/7135582bf3ff9894f3a78769201f36de_15.png)

![](img/7135582bf3ff9894f3a78769201f36de_16.png)

So the goal in sort of this coordination is to create sort of a neighborhood watch approach where any given home in a neighborhood might be like an individual IDS or IPS and the global neighborhood watch where everybody calls in with their indicators has to do with tracking a threat all the way through a very a much larger domain。

 understanding the scope of a larger threat by putting together a lot of smaller indicators that would be able to not only track the threats but perhaps even coordinate their response in the idea of coordinating a multiple IPS kind of a function。



![](img/7135582bf3ff9894f3a78769201f36de_18.png)

![](img/7135582bf3ff9894f3a78769201f36de_19.png)

![](img/7135582bf3ff9894f3a78769201f36de_20.png)

So what do we need to solve in order to create something like this， What's the challenge。

 The challenge here is to create compatible I S and Ips standards so that we can use heterogeneous and different approaches in I S and Ips together to both put together indicators to get better Is over large situations or perhaps even more importantly。

 How do we put together responses distributedly over a large number of technologies to coordinate an intrusion prevention system that's more than just detection and prevention in any one place。

 This dynamic approach to prevention will hopefully be able to increase the resilience of systems by。



![](img/7135582bf3ff9894f3a78769201f36de_22.png)

![](img/7135582bf3ff9894f3a78769201f36de_23.png)

![](img/7135582bf3ff9894f3a78769201f36de_24.png)

![](img/7135582bf3ff9894f3a78769201f36de_25.png)

![](img/7135582bf3ff9894f3a78769201f36de_26.png)

![](img/7135582bf3ff9894f3a78769201f36de_27.png)

![](img/7135582bf3ff9894f3a78769201f36de_28.png)

Ratcheting up the prevention， as we understand better and better from a distributed system。

 what all of the individual attacks are and how they're coming to be。

 So this is a very active area of research within Is and Ips。 And to solve this technical challenge。

 It's not only a definition of the standards。 What should the standards be。

 But it's also the idea of。

![](img/7135582bf3ff9894f3a78769201f36de_30.png)

![](img/7135582bf3ff9894f3a78769201f36de_31.png)

![](img/7135582bf3ff9894f3a78769201f36de_32.png)

not just syntactic， but what are the most important things to standardize versus what should we have as individual to the endpoint Is and I systems。



![](img/7135582bf3ff9894f3a78769201f36de_34.png)

Now， beyond the coordination of lots of different heterogeneous Is and Is。

 there's the idea of the individual IS IPS systems are starting to get more and more tied into nontradition advice。

 This really began with the convergence of telecon and I。

 as the first example of sort of a nontraditional I device。 This is， as you might expect。

 cell phones and the use of cell phone technology and LTE to merge that together with what was traditionally internet technology。



![](img/7135582bf3ff9894f3a78769201f36de_36.png)

![](img/7135582bf3ff9894f3a78769201f36de_37.png)

![](img/7135582bf3ff9894f3a78769201f36de_38.png)

By merging various kinds of things down into small endpoint devices。

 we not only change the transport mechanism， but we change the fundamental nature of the applications and the operating systems that are involved with these sort of nontraditional devices。

 So imagine with all the entertainment now being delivered over IP networks。

 investigating anomalies across these networks where you don't just have standard internetbased services anymore。

 but a lot of other things that are being delivered over IP and over TCPI to try to understand whether you have normal traffic or not。

 So take your even your traditional home， if you have an internet connection in your home initially you might have just had an internet connection that went just to your Windows machine or your Mac or perhaps a Linux machine where normal behavior was browsing the Internet。

 getting your email doing all the traditional things that you would do on a standard computer。



![](img/7135582bf3ff9894f3a78769201f36de_40.png)

![](img/7135582bf3ff9894f3a78769201f36de_41.png)

![](img/7135582bf3ff9894f3a78769201f36de_42.png)

![](img/7135582bf3ff9894f3a78769201f36de_43.png)

But now， if you've got， you know， Fios or if you have Comcast or one of these more advanced TV providers who's also doing your internet。

 you're getting a lot of your entertainment content over the same lines also delivered as I P。 plus。

 all of the other information going to different elements and items in your home are now。



![](img/7135582bf3ff9894f3a78769201f36de_45.png)

Changing the nature of what it means to have normal behavior in your home。 you may， in fact。

 not even know that you're supporting IPV 6 if you've got devices in your home that are set top boxes that have IPV 6 addresses when your own laptops and systems may not。



![](img/7135582bf3ff9894f3a78769201f36de_47.png)

![](img/7135582bf3ff9894f3a78769201f36de_48.png)

![](img/7135582bf3ff9894f3a78769201f36de_49.png)

So this is likely to be much more prevalent moving forward and trying to resolve these non-traditional devices at all levels in home in business and in the infrastructure is going to be an area of research for IDS systems for some time to come。

 it's making anomaly detection systems even more problematic than they were when we were just dealing with traditional TCPI kinds of connections。



![](img/7135582bf3ff9894f3a78769201f36de_51.png)

![](img/7135582bf3ff9894f3a78769201f36de_52.png)

![](img/7135582bf3ff9894f3a78769201f36de_53.png)

There are some other challenges that are under underway that are certainly worth mentioning the whole idea that we're getting cryptography everywhere where all of the connections are being。

 you know， whether it's your mail， your web， they should be asked or whatever it is， cryptographic。

Protocols are being used in lieu of straightforward plain text communication。

 almost every playworking the network。 Now， why does that matter for Is。

 Because if your Is is depending at all in deep packet inspection or looking at a network Is where you're trying to look at the traffic and it's encrypted。

 You're not going to get that information within your Is。 that's going to do two things。

 it's going to drive the Is into the endpoint， So into hostbased Is and downed into the various devices or it's going to make the Is much more concerned with metadata across the network so that doesn't need to have payloads。

 These are the two chat ways that this particular challenge is being addressed within the Is community today。

 then we have the whole problem of embedded protocols， The idea that。



![](img/7135582bf3ff9894f3a78769201f36de_55.png)

![](img/7135582bf3ff9894f3a78769201f36de_56.png)

![](img/7135582bf3ff9894f3a78769201f36de_57.png)

![](img/7135582bf3ff9894f3a78769201f36de_58.png)

![](img/7135582bf3ff9894f3a78769201f36de_59.png)

![](img/7135582bf3ff9894f3a78769201f36de_60.png)

Essentially， you're taking everything over report。 Everything is becoming a web service or everything is embedded in some other type of service that's there。

 So initially， your Is could look at the service type and get a good idea of what normal behavior in that service might be。

 but with embedded protocols， you don't have that same ability。

 if you see the outer envelope of the protocol。 That doesn't say much at all to what the protocol and what the standard and normal behavior would be internal to that to those packets。



![](img/7135582bf3ff9894f3a78769201f36de_62.png)

![](img/7135582bf3ff9894f3a78769201f36de_63.png)

![](img/7135582bf3ff9894f3a78769201f36de_64.png)

![](img/7135582bf3ff9894f3a78769201f36de_65.png)

If it's on the network， the same thing is true on the host。

 but it's more in the case of dynamic virtual machines。

 where instead of having a host where you can look across the entire internal structure of an operating system you now have multiple operating systems that are encapsulated just like in the embedded protocol case So if I'm trying to do an Is or a host-based IS and that host is actually hosting many other virtual machines then do I go into each virtual machine in order to do hostbased IS do I treat the outermost host Ibs host IS as a networkbased Is looking at traffic in and out of the VMs。

 there are lots of different technical approaches to this that are currently being addressed today But the challenge is in all of this world of embedded protocols and embedded virtual machines and this whole idea of making additional complexity with regard to the where computation and where。



![](img/7135582bf3ff9894f3a78769201f36de_67.png)

![](img/7135582bf3ff9894f3a78769201f36de_68.png)

![](img/7135582bf3ff9894f3a78769201f36de_69.png)

![](img/7135582bf3ff9894f3a78769201f36de_70.png)

![](img/7135582bf3ff9894f3a78769201f36de_71.png)

![](img/7135582bf3ff9894f3a78769201f36de_72.png)

![](img/7135582bf3ff9894f3a78769201f36de_73.png)

![](img/7135582bf3ff9894f3a78769201f36de_74.png)

I actually moving around， it's driving the IS research to try to become more and more complex with the way sensors。

 the communication between sensors and where the analytic structures are in the IDS。

Another completely different type of challenge is the whole idea of when you have sort of the free IP ranges available without any accountability。

 This is the open access access to the Internet。 So when I start having Ymax and areas within cities and airports and beyond coffee shops where you don't have any accountability to the user connecting to the Internet。

 You could potentially have a lot of malicious activity coming from those areas with no way to track it back to any place where an individual could be held accountable。

 So what does an I do in looking at the source of an intrusion when the source of that intrusion is a dynamic IP address that resolves into an airport that's providing free wfi or within a public space that's providing free wfi。

 I there any way for the Is itself to gather enough information to do additional accountability。



![](img/7135582bf3ff9894f3a78769201f36de_76.png)

![](img/7135582bf3ff9894f3a78769201f36de_77.png)

![](img/7135582bf3ff9894f3a78769201f36de_78.png)

![](img/7135582bf3ff9894f3a78769201f36de_79.png)

![](img/7135582bf3ff9894f3a78769201f36de_80.png)

![](img/7135582bf3ff9894f3a78769201f36de_81.png)

When there is no specifically offered information in those connections as they're being made。

This is putting together a series of threats with the entire mobile infrastructure。

 So when your infrastructure becomes mobile and your threats become mobile。

 not just your target points， then the Is has a much more difficult time trying to sort out Where are the sources where are the targets and how do I scope any particular intrusion that's going to be detected within my IDS system。

 this sort of combination of the idea of my embedded protocols， my dynamic Vms。

 my free access to the internet without accountability and my increasingly compact services over port 80。

 together form a tremendous IS challenge to try to create new technologies that don't rely on the assumption that my structure is very simple with regard to how do I get。



![](img/7135582bf3ff9894f3a78769201f36de_83.png)

![](img/7135582bf3ff9894f3a78769201f36de_84.png)

![](img/7135582bf3ff9894f3a78769201f36de_85.png)

![](img/7135582bf3ff9894f3a78769201f36de_86.png)

From a source to a destination in a fixed infrastructure。



![](img/7135582bf3ff9894f3a78769201f36de_88.png)

Finally， there's the whole aspect of privacy issues。

 The idea of an IS collecting information and manipulating metadata and resolving who the victims and who the perpetrators are of these incidents that are being detected may be exposing。



![](img/7135582bf3ff9894f3a78769201f36de_90.png)

![](img/7135582bf3ff9894f3a78769201f36de_91.png)

Too much personal information about what's actually going on in the communication protocols within the network in the days where we had very simple internet infrastructures。

 the privacy issues were pretty much resolved by the ownership of the fixed infrastructure where the Is was running。

 But now if the Is is distributed in a mobile environment with potentially unaccountable I structures and a number of the other issues that we've just talked about。

 these raised additional privacy concerns that we never had to worry about that much with regard to Is。

 So I would certainly expect to see much more of that come into the future。

 the reference I have here begins to bring up some of those privacy issues with regard to Is。



![](img/7135582bf3ff9894f3a78769201f36de_93.png)

![](img/7135582bf3ff9894f3a78769201f36de_94.png)

![](img/7135582bf3ff9894f3a78769201f36de_95.png)

![](img/7135582bf3ff9894f3a78769201f36de_96.png)

![](img/7135582bf3ff9894f3a78769201f36de_97.png)

![](img/7135582bf3ff9894f3a78769201f36de_98.png)

![](img/7135582bf3ff9894f3a78769201f36de_99.png)

![](img/7135582bf3ff9894f3a78769201f36de_100.png)

The next sort of technical problem that needs to be resolved with regard to our with regard to IDS is how do you really detect early indicators so as we've seen coming through the course。

 most IDS signatures really don't file fire until the attack is well underway IDSs and IPSSs have difficulty in sort of understanding what the precursors of attacks look like this really means that we need a better model and a set of classifiers that will really distinguish this kind of precursor activity from normal activity and it doesn't really matter whether this is signature or anomaly based in terms of the kind of detection the idea is the traditional model that we have for attacks。

 does not appear to be sufficient for really understanding and detecting these early indicators of attack something that's going to help us respond even earlier to an incident that after the incident has already。



![](img/7135582bf3ff9894f3a78769201f36de_102.png)

![](img/7135582bf3ff9894f3a78769201f36de_103.png)

![](img/7135582bf3ff9894f3a78769201f36de_104.png)

![](img/7135582bf3ff9894f3a78769201f36de_105.png)

![](img/7135582bf3ff9894f3a78769201f36de_106.png)

![](img/7135582bf3ff9894f3a78769201f36de_107.png)

![](img/7135582bf3ff9894f3a78769201f36de_108.png)

![](img/7135582bf3ff9894f3a78769201f36de_109.png)

He started。Another significant problem that we have within the Is world and in the security world in general is this whole idea of detecting delayed attacks。

 This is where the malware or some kind of attack happens and a payload is hidden for some period of time before the next stage of the attack actually happens。

 So imagine if I am a a user that brings my laptop to and from the office。 and。



![](img/7135582bf3ff9894f3a78769201f36de_111.png)

![](img/7135582bf3ff9894f3a78769201f36de_112.png)

![](img/7135582bf3ff9894f3a78769201f36de_113.png)

![](img/7135582bf3ff9894f3a78769201f36de_114.png)

While I'm at home， I can browse the internet， I can go off and do whatever I want。

 and my system can get infected。

![](img/7135582bf3ff9894f3a78769201f36de_116.png)

But it doesn't do anything。 It just sort of sits there and watches until it sees that I've actually opened up some sort of a VPN connection or come back in internally to my organization。

 And now it launches the attack as an insider attack。 So in this way。

 the malware takes advantage of the fact that the same hardware and software is moving between different security domains。

 And it using delayed attack techniques in order to。



![](img/7135582bf3ff9894f3a78769201f36de_118.png)

![](img/7135582bf3ff9894f3a78769201f36de_119.png)

Prevent the standard IDS systems and the standard firewall detection systems from keeping that attack from launching。

 it allows the Maware to work its way into being an insider before additional attacks are launched。



![](img/7135582bf3ff9894f3a78769201f36de_121.png)

So how does an IS system have to deal with this？ Well。

 it's got to be able to deal with what happens when I'm connected or disconnected。

 So you may think this goes back to the hostbased Is or perhaps even networkbased Is but from a different perspective in terms of how I'm trying to detect the attacks that are temping to take advantage of the effect that I'm moving to different security realms。

 so the Is also has to move from different security realms。

 We might solve this by being local and do host-based Is。

 we could also solve this through IS communication where each different security realm might have a different Is imagine that my home infrastructure had an intrusion detection system on the network that could collect indicators which could pass along to the IS system in my work environment so that the two could compare activities and be able to better scope any kinds of detected malware or detected activity that would happen within the system。



![](img/7135582bf3ff9894f3a78769201f36de_123.png)

![](img/7135582bf3ff9894f3a78769201f36de_124.png)

![](img/7135582bf3ff9894f3a78769201f36de_125.png)

![](img/7135582bf3ff9894f3a78769201f36de_126.png)

![](img/7135582bf3ff9894f3a78769201f36de_127.png)

![](img/7135582bf3ff9894f3a78769201f36de_128.png)

![](img/7135582bf3ff9894f3a78769201f36de_129.png)

There's lots of requirements for improving the whole world of IPS。

 trying to understand what kind of actions we can take and what are effective actions that we can take from an IPS very。

 very active and open problem within the IS world today。

 So today we really only have limited actions that we can take with confidence in any kind of an IPS。

 mostly it's blocking connections once we've detected an attack。

Sometimes it's a little bit of reconfiguration， but it only in a very limited sense。

 Ips S scares people away， and it should， because we don't really understand well enough how to take actions that actually reduce the risk to our organization and don't increase the risk today。

 the risk is high。 even if there's only a modest type 1 error rate。

 because any type 1 errors would create some sort of a response function that's going to create more damage than benefit within my system。



![](img/7135582bf3ff9894f3a78769201f36de_131.png)

![](img/7135582bf3ff9894f3a78769201f36de_132.png)

![](img/7135582bf3ff9894f3a78769201f36de_133.png)

![](img/7135582bf3ff9894f3a78769201f36de_134.png)

So we need to find a way to link actions with sort of confidence in the detection and find ways that we can have low impact actions that lead to higher and higher impact as we gain confidence in the understanding of what the intruder is actually trying to do。

 So a lot of what we were trying to do manually in investigating what the intruders。

 objective might be based on Is alerts。 The Is should have that same level of confidence as more and more indicators are collected around a given set of attacks。

 and that can lead to actions that are potentially more and more dangerous or more and more risky as we know that the situation is more dire with regard to the attack。

 so that we don't have just a very simple detect react， you know， detect react， detect react。

 Instead， we have detection， gaining confidence， small reactions trying。



![](img/7135582bf3ff9894f3a78769201f36de_136.png)

![](img/7135582bf3ff9894f3a78769201f36de_137.png)

![](img/7135582bf3ff9894f3a78769201f36de_138.png)

![](img/7135582bf3ff9894f3a78769201f36de_139.png)

Give us more data using the IPS reactions themselves to give us data to add confidence that would eventually allow us to prevent the objective from the attack from being achieved。



![](img/7135582bf3ff9894f3a78769201f36de_141.png)

And speaking of you high error rates or type 1 error rates。



![](img/7135582bf3ff9894f3a78769201f36de_143.png)

Within anomaly detection， the type 1 error rate is still too high fromomaly detection systems to really be used with confidence in most real environments。

 There are lots of advances currently going on with machine learning techniques。

 some new domains that would have more limited functionality where anomalies can be more easily detected。

 but we've worked on anomaly detection for a long time。

 and we have yet to still have that breakthrough kind of system in anomaly detection that really makes it functional in a wide variety of environments。



![](img/7135582bf3ff9894f3a78769201f36de_145.png)

![](img/7135582bf3ff9894f3a78769201f36de_146.png)

![](img/7135582bf3ff9894f3a78769201f36de_147.png)

![](img/7135582bf3ff9894f3a78769201f36de_148.png)

But the research that we currently have in behavioral analysis and behavioral detection is beginning to point the way to potentially reducing this high type 1 error rate that we've had and helping us to create IDS systems or anomaly detection system that would have a manageable typey 1 error rate that's low enough that we could with confidence incorporate that directly with our CSE teams or with an IPS response。



![](img/7135582bf3ff9894f3a78769201f36de_150.png)

![](img/7135582bf3ff9894f3a78769201f36de_151.png)

![](img/7135582bf3ff9894f3a78769201f36de_152.png)

![](img/7135582bf3ff9894f3a78769201f36de_153.png)

![](img/7135582bf3ff9894f3a78769201f36de_154.png)

And there are lots of other advances that are not addressing any specific technical challenge that we've had in the IDS world。

 but it turns out that by addressing this research。

 it also gives us benefits in challenges in the Is world。 So a lot of the big data analytics。

 the graph analytics and streaming progress that we've been making has also helped improve classifiers in general。

 which is going to help us improve what we can do with regard to intrusion detection。

 the same in sort of this research regarding resilience the more we can create highly resilient systems。

 the more we understand what kind of responses are required to increase resilience。

 this can be incorporated directly into IPS as well。

 so that we can begin to link the advances in resilience to advances that we would have in IPS。



![](img/7135582bf3ff9894f3a78769201f36de_156.png)

![](img/7135582bf3ff9894f3a78769201f36de_157.png)

![](img/7135582bf3ff9894f3a78769201f36de_158.png)

Measurements and metrics， as we understand better， how to quantitatively measure risk。

 how to quantitatively measure the impact of threat。

 Then we should be able to better get our automated responses aligned with these metrics that are being done。

 not for I S directly but to benefit I S， the same with enhanced reverse engineering and signature generation。

If we can do more automated reverse engineering， if we can do more automated signature generation。

 then we have an ability within an I system to update our own signature based。



![](img/7135582bf3ff9894f3a78769201f36de_160.png)

![](img/7135582bf3ff9894f3a78769201f36de_161.png)

On malware that we might actually detect and reverse engineer。 So again。

 the advances that we're getting in reverse engineering， the advances in sandboxing。

 looking at functions like what Fire eyee can provide in exploding malware inside of an environment can help us do automated signature generation and thus give us an advance with regard to IS systems。

 So this was a series of technical challenges that we have with regard to IS in general。

 no one challenge is going to make Is， the fundamental technology that will solve all of our problems。

 But as you can see， the intertwined nature of the research that's happening throughout the security community and the analytics analytic community is going to benefit the world of IS and IPS moving forward。



![](img/7135582bf3ff9894f3a78769201f36de_163.png)