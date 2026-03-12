# SRE大会-2025-美洲-｜-srecon-｜-分布式-｜-缓存-｜-OpenTelemetry-｜-安全-｜-AIOps-p31-P31-Incident-Management-Metrics-That-Matter--BV1TmLDz7EZZ_p31-

。

![](img/19742db83fc4abddea060eab5408c8b2_1.png)

Hey everybody since it's relevant to our talk today。

 let's take a minute to introduce ourselves in a bit more detail。 I'm Jamie。

 I'm a senior S Datadog and I just finished six months as the interim manager of our incident management team。

 which is a team that's staffed up to define processes and practices for onca and instant management as well as measure the success of those programs across the company I'm also a huge vintage technology nerd if you want to come up to me and ask me about my Uni workstations and hi I'm Laura I'm a senior staff engineer at Datadog with a broad scope around the idea that perhaps we should be reliable and resilient which obviously includes making sure that our instant management process and tooling are working well keeping customer in fact from unforeseen events to a minimum all of that for this talk I get to play a role I'm going to be a new engineering manager at Datadog who's getting ready to make it an impact in the incident management space So you welcome to Datadog just to give you some context for the type of company that Datadog is while we're not a fame sized company we are pretty large。

We are pretty large and we have a bottom up engineering culture so this is important because it means that any engineer Datadog will be involved in an incident at some point and everyone is trained up to the point where they are comfortable being an instant responder or an instant commander for any arbitrary incident they're also expected to be involved in running the postmortem we have a dedicated team us staff to build sustainable incident processes and to continuously reevaluate our posture for instant management and on call。

Okay， so how do executives know that it's worth employing this incident management team。

 We obviously need to understand how we're doing at making sure our incidents are under control and that the work the teams doing to make them better at business is business dollars well spent。

 So we definitely want to see that there's a company level need for a major correction， Ily。

 before it gets really bad。 Also， I would really like my fat bonuses。

 So how do we prove we're doing a good job in executive speak。😊。

I know we should measure mean time to recovery from incidents。 If our incident response is effective。

 we'll recover from them better。 So M T T R going down means we have good incident response。😊，Well。

 that's an easy statistic to measure but what kind of value does it actually bring to our organization I don't know。

 I think it generates a picture of reliability that's inaccurate and overly simplistic right incident are constantly variable they're always changing and one measure isn't enough to capture that level of complexity but it's also just not a robust summary statistic Shaan devidovich has actually done the statistical analysis in this great paper for instance specifically the number of incidents in the variation in the standard deviation of the data of incidents meaning that changes your meantime to resolution are almost deterministically noise in your data and you're not actually measuring something that's useful or actionable for your organization but more than that it also creates perverse incentives right the easiest way to drive down MTtTR is they have the same incident over and over and over again getting better and better at responding to the same incident every time until you're closing it really quickly and that kind of。

isn't a useful thing for an instant management program。And before you say it， no。

 MTTM and the other similar causess of MTTTR aren't much better。

 they also come with their own set of perverse incentives as well as not being robust and having the same problems as MTTR。

Okay， okay。 So we don't want to have the same incident over and over again。

So what we should measure is incident count。 If we're doing our jobs， right， we have fewer incidents。

Over time， that makes sense。 we want things to break less。

 that we make that happen by having fewer incidents。

 There you got QD Okay yeah I can see some logic there。

 but also like while it's easy to measure the count of incidence。

 what does a change in incident count actually mean if we have an increase or decrease in incident count。

 that's oftentimes correlation instead of causation we're looking at you know periodicity in your business。

 maybe there was a holiday， maybe there was a code freeze that stopped instance from happening temporarily。

 but also more than that， it sets up some bad incentives right it encourages people to not file instance for things that actually require that kind of a response。

 it makes low severity incident just spicy bugs right and it gives you ultimately a loss of visibility into what's actually broken because it discourages people from engaging with your process。

Alright， al right。 How about change failure rate。 It's like incident count。

 But it's normalized to how big our systems are and how fast they change。 Yeah， okay。

 but what's a change and what's a failure， It's kind of difficult to define。

 And it also gives a bad representation of how problems you interrelated Change build up over time from unrelated commits and stuff。

Okay， but what about people need to follow up diligently on their postmortems So they need to have lots and lots of action items。

 so the more action items， the better。 Okay， well， if you have the more action items， the better。

 that encourages people to make low value action items， right。

 especially because it's usually paired with some kind of idea of let's measure the completeness of our action items。

 So if they're overly simple， they'll be easier to close but we can measure this at the team level。

 right， like week over week trends if for individual teams that are getting better。 Okay， yeah。

 but why not hour over hour。 Like' if it we're talking about a single team in their instance。

 there's so much variability in the data， week over week isn't going to be very useful to give you actionable data back granularity。

We want our incidents to be less bad。 Can we do incident severity。

 It'll help us reduce the number of severe outages for our customers。 Yeah， I agree， In less bad。

 good， love that。 But if we're talking about trying to count the number of high severity incident that we have that encourages people to lower their incident severity artificially right And to maybe not file instance for things that should be incidents。

 You're killing me here。 Why not team seniority levels。

 we know more senior engineers are better So they should only break things if it was really actually broken as a senior engineer。

 I don't think I'm necessarily better。 And also I think that this would be a great way to like pit teams against each other。

 maybe create a blameful culture。 I think the downstream effects could be pretty bad。Jamie， Jimmy me。

 you're killing me here like， okay， get， it's really hard to measure this incident success。

 You've made it clear to me。 Incidents are complicated。 They're variable。

 There's a lot of human interaction going on， and we really need to think hard about the incentives that we're building。

 But meet me halfway here。 The business does want to know if we're being effective。

 And we should want that as a team。 We want to know if we're doing something that's useful and important。

So it's not okay to just say trust us or to have no insight into whether our practices are working or making things better。

 Yeah， I definitely agree。 I mean， I think like let's take an engineering approach this right。

 let's try breaking the problem down to smaller problems and think about incident response and on call as goals in and of themselves。

 we can agree that no matter what we do， our systems will break right no matter how skilled our engineers are faults are going to happen。

 So if we're effective at responding to that。 And if our incident management program is effective as a result。

 What things would be true And how can we measure them to show that we're getting there Okay so effective incident management。

 that is a good question。 So what are my goals as an official busybody around people being on call。

 Well for on call specifically， I want to know that our engineers are good at it。

 I want to know that engineers who are on call show up。

 they know how to use their tools that their tools work well。

 I just want to know that they're being responsible about it and that the process is doing what we ask it to。

 which is get a person with the knowledge to fix it alerted and in the。As quickly as possible。

 I want to know that they're getting treated as this interrupt level priority。

 the absolute priority that they need to be for people。

Nobody spent their own callship being unreachable or unable to deal with incidents， stuff like that。

 Yeah， for sure。 So in terms of engineers taking on call seriously and being responsible at Datadog。

 we're confident that this is culturally true globally。

 this is something that we just don't really feel the need to measure。 It's also a measure of trust。

 you know that we trust that our engineers in our culture。

 that people will tell their peers or their manager or whatever when they're doing something that's not part of the processes that we've established for on call。

 So know we often share expectations and stuff。 and it's also important to remind ourselves that collecting data isn't free。

 And in this case， if it's something that we don't feel that we need to measure。

 then maybe we shouldn't spend the cost to measure。

But also to your point about you know how people interact with onca。

 I think onca tooling should be invisible you except when you need it toil and confusion is poisoned for onca right you don't want to introduce additional toil for people just in trying to use the systems that you've provided for them so you know in terms of quantifying that we can think about how intuitive the system is we can measure people's honest mistakes right if you have a variety of ways to page someone and someone uses one of the wrong ways to page someone that's a signal for you but also you know if someone is tracking pages using the wrong statistical analysis or tool that's helpful you can also track the number of pages that are going to slackck or never acknowledge if you do have a need to measure the kind of you know serious and responsibility thing you can also measure time to pager but like I said earlier that's not something that we feel we need to do at Datadog。

Okay， so almost like product success metrics for our onca tools All right。

 I also do want to know that we're not burning out engineers with being on call when we page people。

 they have less time and energy to write new features。

 which again features are the things that I'm getting the fat bonuses for so I want that I do also believe it or not think that managers are human and want to do right by their people So probably I'd like to not burn out my people just for that reason I want to know that the demands that we make of engineers being on call are the minimum reasonable demands that the business really needs that that those are within the bounds of what humans can realistically sustain over time being on call is a continuous cost to a team。

 we should know that we're minimizing that cost and thinking about preventing burnout I really want to know that we're not letting that burden be unfair for being on call when you ask a team something like is your onca rotation fair they're going to answer yes because people who feel that work is unjust are going to burn out a lot faster So in terms of you know making onca suck the minimum amount。

Possible， I think that we can measure how much onca sucks。

 especially in terms of whether it's going to impact someone's personal life and kind of lead towards burnout。

 One thing we all know is that being woken up by a pager sucks So how many overnight shifts does someone have both raw and consecutive overnight shifts and how many overnight pages are they receiving on those overnight shifts do we find that there is an uneven distribution of them speaking of actually getting paged。

 how many pages does a person get in the average shift what's the maximum number of pages that an engineer on the rotation gets in an hour that gives you kind of a measure for how bad a shift is normally and how bad it can get But in terms of impact on someone's personal life。

 you how many consecutive days are they on call how long are those shifts and what's the total amount of time that they're on call within any given period of time Like Corey said on Tuesday this impact can vary from person to person and it's really important to consider within our teams and within the teams that we work within what that impact looks like and how we can。

Minimize that for the different responsibilities that people have within their personal lives in terms of rotations being fair and not burning people out。

 not everything is numeric， especially in terms of how things feel but we can quantify some amount of this right we can do the distribution of weekend and overnight shift for example。

 we know that a weekend shift or an overnight shift is going to impact someone's personal life and because of that we can think about are those shifts distributed evenly within a rotation。

 are they distributed evenly within teams if they share a rotation etc。Okay。

 I think we can work with that。 I can bring that data to execs。

 and I can point to lines that get better over time。 dollar times。 I love dollar times so。😊，Next up。

 we have what you might think of as really the central team mission right after engineers get paged sometimes they have a real incident。

 What makes that incident good， no incident is good， but what makes one better than another。

 I actually saw this really neat talk at S Econ and Dublin6 months ago called In Groundhog Day they did studies of incident response with AI So as a manager I love it and the takeaway there was that the best responders are the ones who are good at coordination and communication。

  building on your point about the best on call tooling being invisible Our incident process and the tooling should be invisible too。

 can we measure that Jamie measure whether our engineers are communicating effectively pulling in the people they need and then maintaining that coordination across those people。

 We can measure that。 Yes， So in terms of communicating effectively。

 we can think about the adoption of the newest features and processes for how you deal with incidents at Datadog。

 we're kind of privileged in this regard because we use our own incident management platform So we can check on our people using the newest features that we've developed and that are available。

m to use such as incident work screens， which helped us manage a sub0ro incident a couple years ago。

 we can also measure how often people from specialized rotations that are set up to help people who are on call get paged into high severity incidents for example。

 people who deal with security incident specifically people who deal with coordination for largescale incidents。

 we can measure how often they're pulled in to your point about instant tooling being invisible if you have a paved path。

 this is actually pretty straightforward to measure So since our team defines the tooling and process for the whole company。

 we can think about coverage in terms of are people making their own incident automation to cover the gaps that we're leaving or are our tools sufficient for what their needs are in terms of Invisibility do people know the name of your service that provides incident automation they probably shouldn't or are they surprised that it's built by your company at all because it's so seamlessly integrated into the workflows that they already use Consider you know like also the sentiment dimension to this。

a lot of how incidents are is based upon how people feel and how comfortable they are in responding to those incidents。

 so even if your're tooling and process super effective。

 there still may be other factors that are frustrating people and leading to poor incident experiences so we all know that people will fill out a survey and anger so make a survey that people can fill out in anger make an opportunity for people to give you that feedback when they're at their most frustrated with the incident process so that you can understand not only the average experience but also the outliers in the experience as well。

 but this feedback can also come from things like doing LLM sentiment analysis on the chat happening during an incident or on the postmortem we've had some success with that too。

So we do get to use AI tools。 Okay， so I know you told me that people treat their pagers seriously。

 do tweets。Do teams treat incidents with the appropriate seriousness as defined by me。

 So do we see things like teams getting to the point where the problem is mitigated。

 And then they just walk away， Do we get updates that aren't making out to stakeholders as often as they should or maybe uses of the incident process for things that aren't actually emergencies。

 maybe something like teams using incidents because they can't get their problems on some other teams O Rs。

Yeah， I think we could measure seriousness to a certain extent。

 you know so I guess to think about this conceptually we can think about instance as a state machine。

 so the beginning state for that state machine would be when impact begins and the terminal state is when we have followed up on all action items fully mitigated all impact and the incident is closed。

So if we think given that mindset， we can think about where incidents linger in the state machine to your point。

 we do not want incidents to typically linger in the mitigated state without resolution right unless there is continuous updates happening in the Slack channel that can be measured given that idea of the state machine and as you move on through the state machine and get into the later stages it's also important to consider measuring the completeness of the data that you need to follow up on incident as SEs so for example。

 is all the track metadata that you want people to fill out in your instance actually recorded is that recorded more consistently from more severe or higher impact incidents that probably should be。

Also consider whether teams are choosing to write postmortems even when it's not required。

So if a team has an incident that they think is interesting locally to their scope。

 they're going to be interested in writing a postmortem if they have the right enablement there as well。

 so that's a sign of instant seriousness that we are in fact reflecting on things even when there isn't a corporate requirement to reflect on those things but in terms of using instance for things that don't require that kind of incident response you know like getting a problem on some other teams's OKRs there's oftentimes organizational fault lines that go behind those kinds of things too and this gets a little more fuzzy it's hard to quantify or do a change point detection for an organizational fault line right but it's useful to follow up on postmortems to read the post-mormems that are coming out of your organization and to look for red flag。

Because somewhere in there， the organizational fault line will be hinted at Eventually someone's going to be frustrated enough to say that team did it or whatever。

 you know， and looking for blamefulness， looking for those kinds of red flags in your postmortems can help to point out where those organizational fault lines lie so that you can invest time and energy into addressing those structurally。

Okay， and I do want us to be good at incidents to solve customer problems quickly and completely。

 So you've told me that measuring time doesn't tell us that。 no matter how much I wish it did。

So I guess we do a proxy that does work for， are we doing incident response that is good， well。

I guess I could sell the assumption that engineers who feel prepared and good about their response is a good proxy for we did the best that we could or we solve our incidents well that is an assumption but it's when I could stand in front of higher management and kind of defend so for engineers responding to incidents do they feel comfortable and prepared and ready to respond after the fact how's their self-critique do they mention having a hard time following or focusing on the technical challenges because they're not skilled up they're not prepared because they're worried about the fact that things might be down or they might be getting blamed Yeah it's a good question and like other folks pointed out in other presentations the feeling of going into an incident is really important if people are comfortable and prepared then it's going to be that much easier for them to respond and you can do some amount of that via quantification but like a lot of the other things I'm saying here you also need to qualify that with context so you could quantify。

 for example， the usage of roles within your process you should have a way to track this given that you're using roles in your process if。

Using Datadog， you get that for free with the incident app and you can measure that and then check whether roles are in place for things where they should be in place。

 For example， our high severity incidents commanded by an incident commander are highest severity instance commanded by a specialized incident commander that kind of thing again you can also read postmortems who read flags of confusion if people are confused and are not ready to respond。

 they'll write that end to their postmortem， especially if the person who was responding is the person also writing the postmtem right but again this is kind of fuzzy and you want to do some qualitative analysis of this you know this is really helpful to do before and after your training on how to run instance and beyond call。

 which you all do have trainings on how to run your instance and beyond call right but also you through surveys and after the first end instance you can check in with someone again and see how things are going So there's a lot of ways that you can do that but I think that idea about self-briitique afterwards is also really important know you touched on that point saying that people can have a hard time focused。

Are the technical challenges when they're worried about being blamed。

So blamelessness starts at the policy level， but it really requires the buy in of lots of different leaders in order to make a blameless organization and it's useful to do checks to make sure that there's not a pocket of blameful practices building up in some section of the organization and for that it's really handy to have a team whos staffed up to keep the pulse of incidents。

 either directly or indirectly and start looking for those red flags。

 if something doesn't smell right， follow up on it and the infinite wisdom of Pico if you smell us tell us。

Okay， allright。 So one last kind of piece of the incident handling。

How's our communication with customers， Usually we find that having an incident does less harm to your reputation and customer trust than having one and not communicating well about it。

 So do we inform customers about problems in a timely way in language that makes sense to them。

Yeah and thankfully this is something that's pretty easy to quantify because you already know where you communicate with your customers。

 right， there are dedicated public and private channels for communicating with your customers。

 hopefully and so you can measure the time to post communications in any one of those channels Also look out for customer feedback about what's been posted because you will likely hear some feedback about the updates that you're giving while you're analyzing an instant trying to communicate as effectively as possible if you have a dedicated customer communications team get some qualitative feedback from them as well。

😊，Okay， okay， so that's one one more piece， I guess。 So we have this volunteer escalation rotation。

 right， It's not actually members of the SR team。 It's engineers from across the company。

 They get escalated to far more severe incidents to run coordination and help drive resolution。

Is that rotation in good shape， I it well staffed is it struggling to find volunteers do the people on that rotation feel ready to respond。

 they're only going to get paged for really scary incidents right are they comfortable with the incident tooling and tech can they step into that instant command role and then conversely does that rotation have trust from the rest of the company when they show up to help is that a good thing or a bad one yeah I think that perception is really important。

 especially for rotations that are positioned as experts。

 it's really hard to build trust during an emergency you can build trust that you have already established during an emergency but starting from zero with a team that isn't familiar with your team that's positioned as experts is not a good idea so it's good to build those bridges proactively and also to socialize this via trainings and that kind of thing so that everyone is aware of who' is positioned as experts and knows how to engage with them in a way that's not difficult but in terms of quantifying the health of that rotation。

 I think we can do that too so you can think about the count of people on that rotation？

Their average tenure， weve found that for this particular rotation。

 12 to 18 months is a pretty sweet spot there， but also look for consistency of handoffs within that rotation if they are experts and if they're dealing with high severity incidents。

 we need to make sure that all that context is properly transferred from ship to ship etc。

 but also look out for direct feedback from engineers on the value of that coordination rotation because engineers will provide feedback if something feels amiss。

All right， so let's move on after our incident。 If I think about an incident as friend once sent to me as an investment where you've involuntarily paid most of the cost upfront。

 I do want to know that I'm getting that maximum return from this investment I've been forced to make。

 So do we properly analyze what happened and fix the things that we find。

 Do we do that quickly enough to prevent repeats that's gonna to mean that we have real engineering investment in doing that analysis right。

 not just ticking a box and that we see progress on actions instead of churn。

 So like I don't see an action upscale in one incident and then downscale in the very next one。Yeah。

 and action items like we were talking about are really important there's lots of ways to measure that hopefully it doesn't require writing structural engineering equations on an orange。

 but you know whatever works for your engineering organization making sure that that analysis is adequate is something that's really helpful when you have postmortems because you can measure the completeness and the length of your postmortems to figure out whether a full analysis was performed and make sure that that analysis is in your career ladder this is critically important if writing postmortems and being on call is not a part of your career ladder it needs to be yesterday postmortems also should be written for all severe incidents and if they aren't you should really know why you didn't reflect on that severe incident as well as starting those postmortems quickly regardless of whether you complete them quickly internally we have a process of starting postmortems within a certain amount of time after an incident is closed would highly recommend you to do a similar thing so you can measure deviation from that standard as well。

But also it's helpful to think about whether teams are using an in team review process for their postmortems and for their incidents as a team we provide a structured process for other groups of the company to do their own decentralized postmortem reviews is that process in use if that process isnt use do teams report that's valuable。

But you also mentioned this idea of like low churn and like investing in high quality fixes and action items right so we don't measure the number of actions on the post more than for the reasons we touched on earlier。

 but we do track how quickly actions are finished there's no static target for that because some fixes are really deep in our system。

 some fixes are more shallow but tracking how long it takes is really important。

And we look for teams to define both short and longterm action items to make sure that the analysis is not just focusing on quick fixes and is instead focusing on things that can happen over the long term as well We also monitor for repeat incident and we track contributing factor categories for each of those incidents to see their usage over time and see how our patterns are changing this analysis for repeat instance in my experience is best done manually。

 This is engineering work and it's helpful to have engineers that are looking for a pattern they have seen before。

 especially if you have a central group that is reading a whole lot of postmortems all the time like we do。

We've experimented with LLMs for this， but haven't had good results yet。

 you mean they can't do everything。 Okay， so we're getting there。

 I can see how I can use those metrics again to tell us tell exactly a story that our incident management is good and effective。

 but I do want to be measuring that the things we build for customers are getting better too right we work on them and we're not just running in place。

 you know based on what you've been telling me Jamie， it seems like if we're doing it right。

 MTtTR should go up over time because our incidents get more complex and more things have to fail in new and interesting ways to have an incident I know we can't measure the meantime that it still doesn't work to do that。

 but could we maybe measure incident complexity。 Yeah。

 you know I think we've talked about a couple of measures so far today that get at different aspects of incident complexity。

 but we can measure some things a bit more directly too So one is the length of the postmortem。

 More reflection typically indicates there was a lot of complexity to unravel there。

 You can also check on the number of engineers that we're involved in an incident responding to it。

Also the number of roles that were involved in an incident and a role-based incident response process。

 the more roles that are involved in an incident， the more complex that incident is because it requires more specialized individuals with certain types of skills to join those incidents you can also check to see if incident are requiring more than one member from an escalation too this also gets into the length of an incident so normalize this if you are going to measure it。

 but if an incident requires someone to hand off from a specialized rotation to someone else in that rotation or pull in multiple members of that specialized rotation。

 that's a good indicator that you're working with a very complex incident。

You can also use LOMs for this， which is very exciting。

 this is a great place for sentiment analysis from LOMs based on either the chat channel。

 the postmortem， whatever artifacts were produced by your incident。

 you can do some analysis to determine how complex those incidents are。😊，All right。

 and I've really already implied this with the questions I'm asking here。

 But to a significant degree， the customer for all these metrics we're building is our internal executives。

 So is that customer happy， Do they have the information they need from us。

 presumably that's visibility into things like the reliability state of the systems that they're responsible for places where problems are emerging so that they can get involved if they see a need to do that。

 Are we giving that to them。😊，Yeah， well since executives are customers too。

 we can think about like what the existing touch points we have with executives are and how to optimize those to make sure we also get feedback because executive time is really limited and if you already have things like quarterly reviews of incidents or feedback sessions about incident management。

 it's great to leverage those something that we do at Datadog is we publish summaries of incidents for our executives to consume and that happens on a monthly basis it might happen on a different basis for your organization but it's helpful to check the view counts for those summaries if you're using confluence it's right there on the little eyeball thing and that's helpful to see our people actually reading those summaries and digesting them and understanding the information or do you require like some additional checkin with executives in one of those meetings。

All right， so that gives us lots of metrics to show executives that our incident management process is successful and working well。

 But what am I going to tell those executives who notice that that's really not the same thing as measuring customer reliability。

 Like our satisfaction with our incident management process is a proxy for us to say we fix customer problems effectively。

 but assess a problem pipe and I'm sorry about my French。

 we've covered a lot of ways to measure if the incident process is working based on our belief that that process is letting us recover well。

 but that is not the same thing as the product is reliable for customers。 Abute， yeah， so you know。

 how do we think about measuring the customer experience， say it with me， everyone。😊，SLOs。

 yeah so see other talks at this conference， the same conference for the last several years。

 if you want to measure reliability for your customers， do that directly right。

 don't use incidents which are your own internal process for handling outliers and exception events as a proxy for the customer experience because the normal customer experience is not going to be captured by the worst case。

😊，Okay， so we've actually done this， the two of us have had this conversation as a team and with our management。

 both about the need to measure success and also how we think as a team we should measure our own progress and our company's progress。

 how has it been going。So。It varies。 It is generally effective over time。

 but it is a conversation you have to have more than once。

 You need to start by getting initial alignment on the values and metrics that you're going to be measuring with anyone who has decision making power。

 You do need to have management who believe that it is a good idea to be measuring the incident management process and people's happiness in it rather than directly trying to build a summary statistic。

 Some people will resist。 however many times you want to have this conversation。

 and new people join the organization。 So it works best to have an understanding conversation with them about what it is that they're trying to accomplish what they want to know about their organization。

 And then why the implementation that they've suggested doesn't meet their goals and try to build them one that does。

 It's never going to be simple。 Like I said， it's an ongoing conversation。

 You can keep that conversation open from your end。

 even in cases where you have to measure the wrong things for a while。 Think about marathons and。😊。

E and not about winning the argument or sprinting through it right and it's really important as you go through this process of continually iterating to get feedback on these metrics early and often once you've defined success metrics for a team。

 especially if you have a team that's running instant management whose success is defined by these metrics。

 it's really hard to change and move those success metrics so it's really important to make sure that you have strong alignment from everyone who's involved and everyone whose job is going to be affected by this before making changes official otherwise you can be seen as an Ssary team imposing things on development teams which just builds the wall right back up。

So it's also helpful to have a structured feedback process like I was saying earlier and make a survey for people to fill out in anger。

 but also make sure that people can give you feedback throughout the entire process of you working with them to build these metrics that's really important especially in a larger organization that has a bottom up culture but I think one thing that's challenging in this whole thing is getting visibility into trends that you need to correct based on these incident metrics because there is so many of them and we're capturing a very complex picture of organizational reliability here it's tricky we really haven't figured this out fully yet。

 we regularly check our dashboards to get an understanding for what the trends look like and to understand what normal is so that we can spot deviation from the normal build that mental model so that we have an idea of what we're looking at and what impact it can have what each of these metrics actually mean in terms of people's day-to-day lives before you take an action。

And just like an actual software system， in reality。

 you can't necessarily predict everything that's going to go wrong ahead of time and so a lot of our ongoing tracking and awareness for emerging problems is just done by sort of keeping our hands in。

 being aware of what's happening， joining incidents as they happen， talking to people。

 being available for people to come rant at on a regular basis。

We can see some emerging concerning patterns that way。 and we bring those to the team。

 And we say we think we want to follow up on that。 We design some follow up。

 We do a little bit of conversation。Stop seeing that pattern done。 It's really。

 really important in this question of is your incident process working to remember that metadata and summary statistics。

 especially if you're collecting them cheaply by， for example。

 asking every team to fill out a bunch of checkboxes is not a substitute for analysis。

 I know you've probably already heard that this conference。

 But analysis where you dig in and you understand the patterns and the problems in the context。

 there is no substitute for it and summary statistics are not going to help you。

 if it is worth understanding what is happening is worth really understanding。

 it is not worth just doing a summary。For sure So we've covered a lot while your org probably shouldn't be measuring exactly the same things that we have since your org is definitely different than ours here's a summary of some of the things that we heat tabs on internally to measure the success of our instant management team gladla that we made the slide cell phone friendly There's of course a whole RFC behind this slide with tons more information context details and stuff that we couldn't possibly fit in 35 minutes so please consider the challenges that your organization is facing and think about this as an engineering problem to solve for the constraints you're facing。

And I know you always all took pictures， but please don't take away that list as this is the answers。

 like most things engineering， the right thing to build is going to depend on your org， your needs。

 your requirements， your context， your culture what we want to emphasize here is that it makes sense to think of your incident as an internal coordination process and measure directly whether that coordination is succeeding separate from what does that look like on the customer end measuring whether we handle incident well involves defining what it means to handle an incident well and understanding that every incident is going to be a unique and special snowflake averages of good things won't help。

Working with stakeholders， especially your executives to build a shared vision around that complexity and their goals in understanding the incident management process is key to building metrics that really make things better or at least give you real insight and visibility instead of generating shallow optimization behaviors and gaming and meaningless work across your organization which is a real risk care for sure。

 and speaking of executives， if you like Laura's character are looking for something to give your executives to show them that we're doing the right things and we're continuously improving。

 here is an executive friendly flowchar。You can check this to build measurements for your own instant management process and just draw attention to the fact that this is a cycle once you get through this whole process。

 you're going to do it again and again and again because your organization is going to be continuously changing and improving right to the talk from yesterday's point。

 this is a verb， you need to continuously be re-evaluating your instant management process to have the best posture here。

Thanks， everyone。

![](img/19742db83fc4abddea060eab5408c8b2_3.png)

![](img/19742db83fc4abddea060eab5408c8b2_4.png)