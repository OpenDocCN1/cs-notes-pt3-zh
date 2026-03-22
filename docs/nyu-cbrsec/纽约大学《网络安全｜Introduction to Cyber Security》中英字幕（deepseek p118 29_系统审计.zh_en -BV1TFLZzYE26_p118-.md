# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p118 29_系统审计.zh_en -BV1TFLZzYE26_p118-

![](img/650baf3421ac9d89a6b39b6ddb231843_0.png)

Hi everyone at MRmarosso here， and I want to talk to you in this video。

About a concept in cybersecurity that we refer to as auditing。

 and and I don't mean human beings coming in and doing an audit。

 I mean computing processes that are collecting data and building log files as the basis。

 One of the things that we saw in the earliest computer systems。

 big mainframes would generate log files， and it's been a foundational item in cybersecurity ever since。

 the idea that we collect data。 We take it for granted， right， a lot of you probably talk about。

Big data analytics and big data lakes of information and doing analysis and analytics and AI and machine learning and all this data。

 Well， where's the data come from， Where's it all coming from。

 Turns out that there's a pretty effective taxonomy that you can build up。

 Let me tell you where this came from before I sort of explain it to you。

 I had a boss once who came to me and said， oh， you know，s cybersecurity stuff。

 Isn't that really just kind of keeping track of stuff that's happening， And I remember thinking。

That really is kind of an interesting view， because I'd always thought of cybersecurity in the context of the old reference monitor concept。

 which is taking action based on policy。 Alice wants to connect to Bob。

 Security sits in the middle decides if it's okay。 it's okay， Let it through if it's not okay， don't。

 But this idea that maybe another view of security is。That I'm not going to worry so much about that。

 but I'm just going to keep track of everything is an interesting concept like here。

 I'll give you an example， I why I think this is so foundational。

There's two ways that security or any sort of thing in the middle。

 some sort of an additional component middle can impose policy  One is can arbitrate。

 which means Alice connects through this security piece to Bob。

 It sits actively in the middle of Alice and Bob plays an active role。 That's one。

 A second is security sits off and just keeps track of what happens。

 Does't affect what Alice and Bob do。 But if either of them have a beef。 They bring it to me。

 And I'm the judge， this is how courts work， right， where a court basically looks at evidence。

 The evidence comes in。And the judge decides， is the judge out being the traffic cop making sure there's no traffic accidents。

 No， absolutely not。 but having a court and having judges and having evidence might make people drive a little bit more carefully because they know they might get judged and' thrown in jail or something。

 you follow It's an interesting way of thinking about cybersecurity Now。

 the taxonomy that I want you to learn and have in your mind and I almost something that you memorize is auditing can come one of two different ways。

 it can either be based on something that's internal that's generating information out natively。

 it's embedded in the system and it pushes out log files。 It's embedded in the code。

 It was designed in from the beginning to be emanating out information about what is happening。

 That's one。 And a second is I have this mechanism I've built or network I'm using or computer I'm using or gizmo I've built。

And from the outside I latch on， I connect with alligator clips， I put a tap on。

 I watch from the outside， I hang a camera to watch。

 I'm collecting data external to the native behavior of that system。

 Those are your two options now you can do both be great。

 but if you buy something that doesn't have audit embedded。

 then you got to do it externally if it comes with it native， then you're in good shape。

 Most operating systems generate log files right I mean。

 you don't have to go into the kernel and create log information you know generators。

 it's already there。 So if you think of those as kind of two rows。 then for the most part。

 there's three levels at which we do auditing generally as computer scientists we think of these three levels。

 One is something we call the application level。 that's where a kind of consistent with user interfaces and sort of highlel functionality。

 we can generate things your browser， for example， generates a browsing history。

 that's an application level internally。Component that gives some indication about behavior on your system。

So application levels one second is system level and usually we think of that as operating system or the kernel or the code that kind of drives the core functionality of some computer or device or whatever and again an OS will have internally generated log files if it doesn't then you're going to have to find something that sits around the operating system in the runtime system providing some kind of a log of the behavior so obviously you're better off with something internal than external but the advantage of external is that if you bought something that just doesn't have what you need。

 then you can latch on and then the third is network and that's where at the network level you want to have a good understanding what's happening。

 it turns out generally the external observation that comes with say putting a tap on a network or putting on a span port some way of collecting out data in many cases。

More common than a network sort of natively generating audit logs and networks were always designed to move packets not to expose a lot of information about what's going on。

 although clearly a lot of network devices do do that。 so think about that taxonomy。

 internal external app system network gives you six possibilities。

 And as you're doing your design work， depending on what it is that you're building as a system engineer a developer as a designer。

 which I know that a lot of you you either do now or will do at some point in your career。

 These are important cases to keep in mind， as you design something that will complement the firewalls and reference monitor type mitigation behavior。

 the arbitration it will complement that by having the ability potentially to judge or adjudicate based on evidence。

 And turns out that's really what security analytics is all about。 It's about collecting evidence。

Making some determination and judging， so I hope this has been a useful insight for you in the way auditing and log files complement the way we do cybersecurity I'll see you on the next one。



![](img/650baf3421ac9d89a6b39b6ddb231843_2.png)

![](img/650baf3421ac9d89a6b39b6ddb231843_3.png)