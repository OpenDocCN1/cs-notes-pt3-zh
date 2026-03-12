# YOWcon软件开发大会（2024）｜-架构设计-｜-分布式-｜-AI-｜-代码-｜-JAVA-｜-Github-｜-Spring-p15-P15-Getting-Buy-In---Overcoming-Larmans-Law--BV1G9dfYTEHR_p15-

![](img/a1c081558da33e2c4a4e83fd43d34be1_0.png)

Alright， so just as a preliminary， I'm going to do this whole talk on Moreau。

For the most part I'll be using it like a whiteboard， but this is the URL for the Merau board。

 and it will be up there more or less forever。So if you want to， these are our course notes。

 if you will， is that there aren't going to be any slides or anything to give you。

 so these are our course notes。Which makes my life much easier The other thing I'll say is that I've got all my contact information up there for a reason is that when you come to these kinds of talks。

 this fire hose of information is coming at you and then you go back to the office and you try and put some of it into play and it's hard and you need to ask questions and please ask questions I'm more than happy to ask questions you'll note that my Twitter handle isn't up there though you're welcome to try and use Twitter but Twitter has turned into this cesspool of hate and violence and totalitarianism and I don't really want to have anything to do with it anymore so。

There we go。So let's get started。Actually， before I even start with this， let me ask some questions。

 One of the comments for the last time I did this somebody said， you know。

 we don't need any of this because we have a great culture。

So how many of you work in places that have a great culture， raise your hand。All right。Now。

Of those people。How many of you have ever heard of mobbing or ensemble programming。All right。

 leave your hand up only if you have done it for at least a week and gotten some experience with it。

And how much resistance is there in your organization once you've done that。Pie， medium low。

Only a few hands went up with the last question。So the issue here is that。

You can have a great culture， but it's not a culture of learning。

 It's not a culture of experimentation。 It's not a culture that's open to adapting to new ways of working。

And good life of fork balance。 That's a good thing。 Everybody once， wants that。

 but that's not enough。And one of the things that you're trying to overcome them when you're talking about Larman's law is the problem of the culture of the organization。

So let's look at the individual laws here。Starting at the beginning And also， also。

 this is the URL for Craig's site。 I have this again at the end of the slides here。

 Let me make it a little bigger first just a second so you can。Take a picture of it if you want to。

I'm not supposed to be quiet。 but whenever people do this when I'm in the audience。

 it's never up there long enough。 So I'm going to wait for the cameras to disappear before。

And I've got it again at the end of the list， all right， the cameras are down。So。Let's look， look。

 look at Craig's observations here。He makes a point of saying on his page that these are not prescriptive laws。

 These are not things that you should do。 These are things that you shouldn't do。So。

Starting for the first one， organizations are implicitly optimized to avoid changing the status quo。

And that middle and first letter maggetance。Positions， power structures。

 they all want to stay in in the place that they are now。But Ras was just talked about Conway's law。

 this notion that the communication paths within the organization are directly reflected in the software that you produce。

 and I would add to that in the way that you produce software。

I was chatting with Mel the other day actually and I brought that up and he said that's a really good law。

 it's not Conway's law but it's a really good one， so I have his blessing so what we're trying to do here then is set up a culture where we don't have this constant pool of the status quo。

And middle management in particular is a problem because if you go to a new way of working。

 let's say you were really going to an agile way of working。

AndAnd Zed had this problem when they were doing their much， much。

I don't know what the proper adjective is， but they're transitioning to agile。

If you're going to have cross functional teams where the team has represented on it。

 every skill that you need to get an idea into the customer's hands。Including people like。

Testing in product， I can guarantee you that the director of Seing and the director of product is not going to be happy about that change。

Becauseuse he's now going to be in charge of a fiefdom with nobody in it。

So there's always going to be some kind of pushback。That's inevitable。

And what we need to do is deal as create a culture where that pushback doesn't happen。So。Corollary 2。

Is that。Always， at least often。When you try and introduce something new into the organization。

 what they do is take the existing thing。Put new labels on it and say， now we're doing the new thing。

Your managers are now scrum master。Right。Your product people are now product owners。Right。

 and the it doesn't work that way。 You can't just take your hat off and then put another hat on and suddenly know how to do a different job entirely。

But part of this maintaining the status quo involves locking yourself into the position that you're in now and you'll accept a change in title。

 but you don't want to do something different because that's hard。

This is hard stuff to do because you're learning。And learning is hard。The， the。

I don't know if any of you have read Cananman's thinking fast and slow。But he talks a lot about that。

 He says there is fast thinking。 So if I say what is 2 and 2。

 the number 4 pops into your head without you even thinking about it。 It's painless。And when I say。

 what is 37 divided by 16？You go，Right， and if you， if you've got some。

 if you really want to solve the problem， you get out a pencil and piece of paper and solve it。

 But most people would just walk away from the problem at that point。

 They would rather not solve the problem than do a hard problem。

And any kind of change of culture or adaptation to a new way of working is going to be met with resistance for that reason because it's hard and people don't like to do hard stuff。

The third one。This is my favorite one， is that every time come， you start talking about this。

 people start deriding you and they say， you're a theoretical purist some talking in some ivory tower and this can't possibly happen in the real world。

So I'm going to use mob programming as an example of some of the things that I'm talking about here。

 but。You can't do mob programming in the real world and I'm going well， let's see， Alaska Airlines。

 Spotify， Salesforce。Who else I was just working with the college board。

 2000 programmers in that shop。 They are all doing mob programming 100% of the time。

So if it doesn't work in the real world， how do you explain that。

 And often they just puff and puff and say， well， it doesn't work here。

So then we have to get to the question of why doesn't it work here。

How can we get around this issue of it， It doesn't work here。

The one that I like the most is the prove that it works to me。First of all。

 when it comes to new ways of working， there is no proof。Right。

It takes 20 years for an academic study to be done。 And by the time that's done。

 whatever they're studying is obsolete。And there are very， very few。

 if any double blindind studies on any of the things that we try to do that are innovative。

 So they said， well， it's just anecdotal。 Well， I'm going， okay， we've got salesfor。

 They've got what 5000 programmers in their in their shop。 and they're all doing mob programming。

 and they'll go， that's just anecdotal。And again， it's a kind of resistance。

 It's a way of resisting particular ways of working and a way of pushing back。 And again。

 the point is to。Dlect。Blame， if you will， away from the managers and the specialists。

Because if you think about it most consultants， if they come in from someplace like Deloitte。

 their job is to tell the sea levels what they want to hear。You're paying them $1，500 an hour or $2。

000 an hour to come in and be Smen。And that's not going to work。In this kind of situation。

The next one is that once you make a change。People that are displaced will then start representing themselves as experts。

And they'll be brought in as consultants to other companies who then take their advice seriously because they're the expert。

But they don't actually know what they're talking about。Right， so finding a good consultant。

 if you will， in this area can be very difficult。And then the last one I think， is in some ways。

 the most important one。In a large organization， culture follows structure。

And what that means is that when you start having the teams do things in a new way。

 eventually the culture of the organization will be pulled into that way into ways of thinking that will support the way the teams are work。

In a small organization， culture can come first because you've got four people in a startup and they are creating a good culture and they can choose to create a good culture or a not so good culture。

The ones that think that a startup has to operate the way an enterprise does are the ones that have the bad culture。

 And there are a few of those。 I've been a CTO a couple times for early stage startups。

 and we did not start with a culture like that。So。The big resistance， then。

 most of the resistance comes from the larger organizations。

 And those are the ones that I'm going to be addressing here。

And it's very rare that you've got something like ANZ that even has the will to make the changes。

Is that you just don't see it very often。And I should say also before I really get into the details here that。

It might not work。Everybody has heard the analogy of the culture is a big ship and it's got a huge turning radius。

 Well， some of them， the turning radius is so large that they're going to hit Japan before they get all the way around。

I that they can't turn。And again， that's usually driven by the upper management in the organization。

 so what we're trying to do here in terms of getting a culture in place in a large organization is to first of all demonstrate this how works。

 but also we want upper management to be driving it。Because if ever management is resisting。

 I can guarantee that it's going to be harder than it should be。

So we have to get upper management on board at some point。Right now。

 if you have a bunch of teams doing things in a new way。And it works。People will pay attention。

So I worked with one organization where one of the teams。

They carved off a little office in the corner of the building。

 this is a building that was almost a quarter mile long。And it， it wasn't nearly that wide。

 It was a long， skinny building， and they went all the way to the end of the building as far away from the corporate side as they could。

And they found an office and to get to this office， you had to walk along the third floor。

 take an elevator down to the second floor， walk over to another set of elevators and take it up to the third floor。

 and then you got to their office and within the office there were two groups working so they got a bunch of roll around whiteboards and they literally built a wall around their workspace。

And they made the rule that management is not allowed in here。Nobody is allowed in here unless。

 unless you're invited。And they started doing stuff in really innovative ways。

 right this whole company was one of those fake scrum companies。

 I'm sure we've all seen them where you've done the Laman's law thing。

 is that they've just taken what they're doing now and putting new labels on it and thinking that they've changed something in some kind of fundamental way。

 and that's rarely the case。You could even think about right there in the Scrum guide。

 it says that scrum teams are self managing。Well， how many people here who are working in what they say or scrum shops have a manager？

I。A lot of you， right？So that's not scrum。那真不。And if you go through the scrum ride。

 if you read through the scrum guide， there will be thing after thing after thing。

That demonstrates that problem to you。So there are two ways that we can approach this problem。

First of all， there's bottom up thinking。And bottom up thinking is the example that I just gave you。

Where you have one team that basically works as a so calledled skunk works。

 I don't know if anybody's heard that term before， but it's worth looking up。

Lockheed Martin created the Skunk Work back in World War II in order to have real innovation in aircraft design with something that they were not getting out of their normal engineering department。

 Java was created by a separate company， a son spawned off a separate company called Java that created Java。

And at one point， Sun realized， oh， these guys are a cash cow and they pulled them down back into some sun microsystems。

 and that is the beginning of the decline of Java。All of the crazy， horrible garbage。

 that enterprise Java beans。 if you can remember about that back， back that far。

 that was all sun engineering。 That was not Java。 The Java people were disgusted by the whole thing。

 About half of them left。So the the。Skunk works then as a way of separating yourself from the organization so that you can experiment so you can be in a safe place。

Right safe， of course， means that nobody's going to penalize you。For experimenting。

 Sa also means something else is this is people have been talking。 well， not that kind of safe。

 but people。People have been talking on and off about psychological safety。

Let's talk about that for just a second。A lot of people hear that term and they don't and they don't actually know what it means。

 so I think it's worth talking about it。 psychologicalychological safety does not mean that you are in a room with people who agree with you。

Psychological safety is being in a room where people are arguing。And you're not afraid to speak up。

If you have ever SAT in a meeting and decided not to say something。

 even though you had something to say， you are not in a psychologically safe environment。

 It has nothing to do with conflict。 There's a lot of conflict in a psychological safe environment。

 but the conflict is safe。Right， iss that anybody can have an opinion。And that。

 that whole concept came out of nursing。Is that the nurses were treated as second class citizens by the doctors and they knew things。

That would help the patients that the doctors would not pay attention to。

 The big one is the doctors were not washing their hands。

So the nurses came along and they forced the doctors to dip their hands in this liquid。

And then washing their hands and see what was left。 And most of them were shocked by that。

But the point is， is that that was input from the nursing staff who were in a psychologically safe environment so they could get away with making the suggestion。

And they were also in an experimental environment where the doctors were willing to run the experiment。

And that's the other side of this is that we need an experimental environment in order to make this work。

Where everything is treated as an experiment。Now。Thinking about that for a moment。

 that's one of the levers that we can use to try and get adoption。Is that。

If you go up to somebody some， some higher upper level manager and say。

 we're all going to do mob programming。They're going to say， no， you're not。They say。

 I'm not going to pay four people around for four people to sit around and watch somebody work。

Which is what they think my programming is， but it's not。

Ensemble programming is an ensemble of four people working while one person takes notes in code。

And since taking notes and code is boring， they rotate through that position every 10 or 15 minutes。

But it's four people working。So they don't know what they're objecting to。

 but they're objecting to it。Well， how can you bring them around？ Well。

 if we're doing a bottom up thing， you can say， let's just run an experiment for a couple weeks。

 Let's just try it。It doesn't work。 We won't do it。 And if it works， then we'll keep doing it。

And that goes pretty well， usually。Where it goes wrong is that it does work。

 and then then the manager says， well， use it when it's appropriate。Right。

 and so the way that usually plays out is that the team uses it for some things。

 and then they scatter off to the four wins to do things that they see as trivial work。

But then that all has to be checked into trunk at some point。

So there's going to be a code review process。And in the process of doing the code review。

 you're going to find things that are wrong。And at that point。

 what a lot of organizations will do is scatter back out to the four winds in order to fix the problems。

 but usually if an organization is mobbing a little bit， they'll say。

 let's just do our code reviews as a mob and if we find something wrong， we'll fix it。

And eventually it will occur to everybody， you know， if we had written this code as a mob。

 we wouldn't have to be sitting here doing this。So that's a kind of loose Laman's law problem。

 We'll do it when it's appropriate。Even when it's always appropriate。And as I said。

 there are a lot of really big companies that are mobbing 100% of the time on everything。

And it's because it's an effective way to work。 And they know that because they're comparing what's happening now with what they used to have。

 and they see a change for the better。So。The final thing I'll say about bottom up that's useful is unfortunately。

 we don't work in an office anymore mostly。We're either working remotely or we're working hybrid。

 So if you're working hybrid， that's O， that's good。

Because what that lets you do is set yourself up as an example for the rest of the organization。

So one of the teams I was working with， I told all the teams I work with when I come in as a coach to help them learn how to mob I say。

 do it in a public place。So they dug up some giant monitor somewhere and they ploned it down。

 not up in the air where they usually are， but down on the floor。

And then they went out to the local target， and they bought a bunch of beanb chairs and put them on the floor。

So here's the entire team sitting on beanbag chairs on the floor。

 staring at this monitor while one person has a keyboard in their lap and they're typing。

And people would walk by and they'd say， what are you guys doing？And they said， well。

 we're mom programming， come join us。Sit down with us for an hour and see what it's like。

And people would do that。 And then they would walk off to their teams。 And often。

 though they would bring their entire team back and say， look at what they're doing here。

 This is interesting， right， And gradually， the practice infused out to the other teams。

 There was no upper management involvement with this。So it strictly by。

 I'm doing something interesting， take a look at this。

And there are lots of ways that you can set up cultures where that can happen。

 it's best if people are observing like mobbing， but you can have regular sessions within the organization where people。

 the whole point is for everybody to get together and for the teams that are trying something new and interesting to explain what they're doing to everybody else so they can try it。

But it's always experimental。You always want to do this with an experimental mindset。

 Let's try it for a couple weeks and see if it works out。Because if you just say， oh。

 we're going to do this from here on out， everybody's going to push back against that。

But if you cast it in terms of a class or a experiment。

 then it's much easier to absorb when you're doing that sort of thing。

So the next issue is we need to be thinking about。Top down instead of bottom up。

And this is where things get kind of interesting。The first of all， never utter this word。

Don't say it。It used to mean something good， but not anymore。

So you want to present things not as we are going to adopt this process because that's a big。

 scary thing to do。Right， if people are afraid。I can guarantee that's going。

 going to bring out the fear of people， the upper manager in particular are going。

 this is really high risk。 There's no way we're going to risk the whole company on this new way of work。

Right，And at this point， things like safe， right， the vast majority of safe installations are abandoned within the within two years of being installed。

 right， And the companies are spending millions of dollars on companies on on consultants like Deloitte and McKinsey and all that grab。

 that crowd。I have I hold in pretty much utter contempt。

 They have no idea what they're talking about。I have sat down with those consultants too often。

Where I was trying to teach something to a team and they would just pop up with this weird。

 crazy stuff。 I don't know where it came from， suggesting they do this crazy thing or that crazy thing。

 At one point this was IBM。 I said， will you guys just shut up。And they took me aside and they said。

 no， we can't shut up。 And I said， why not， you don't know what you're talking about， and they said。

 yeah， that's true， but if we shut up。If we shut up。

 then the customer will think we're not providing value， and I'm going， you're not providing value。😡。

Why are you doing this？But the point here is that。Those big consulting agencies are doing a lot of damage。

 and often it's because they're trying to do this big bang thing， this big bang thing。

 Let's bring in an army of scrum trainers。And we're going to teach everybody to a March lock step in Scrum。

 the same group that I was talking about earlier， the same company， that fake scrum they were doing。

 literally everybody in the company started their sprint on the same minute。

They did their sprint reviews all starting on the same minute。And even that wasn't working out。

 and it was obvious， right， They say some manager wants to go to three separate sprint reviews and they're all happening at the same time。

 Can we do something about that。 And no， they couldn't do anything about that。

 Everybody has to start on the same minute。 That's because some crazy consultant came in and told them to do that。

So clearly， that's not going to work。We need a way to talk to management in a way that makes sense to them。

So the important thing here is we want to speak their language。What is the language of business， Now。

 this is a big deal because programmers as a class had know nothing about how businesses work。

Which is a huge problem。 I would strongly recommend that if you're going to try and convince upper management to do something that at minimum。

 you go buy a a good book on how to run a business。And understand what's important to them。

And MBA is not necessary， but you need to know how they think。Well， they think about。3 things。

 two things， depending on how you want to look at it。 First of all， they think about money。Again。

 one of these comment that went back on the last one is we have such a great culture that we thank God。

 we don't have to be thinking about money all the time。 And I'm going， well。

 you programmers not might not think about money all the time， but I can guarantee your bosses are。

Does anybody who's running a company that's not thinking about money is not going to have a company much longer？

It's all about making money。So money is the main language that they're talking about。Now。

 there are some things associated with money。 Time， for example， is a side effect of that。

 at least in programming。Is that if your processes are good， it will take less time。

And managers are always saying the most important thing is we've got to get things out the door faster。

So if that's their goal， that's what you've got to focus on。 Not we're going to be agile。

 but we're going to get stuff out the door faster。And there are a lot of ways that you can accomplish that。

So。You have to make。A business case。In order to get your weight。

And a business case is always about what it's going to cost one way or another。嗯。

How much money will it cost to do this new thing， How much money does it cost to do what we're doing now。

And are those two numbers greater or lesser than each other？

That's what's going to get their attention。There isn't a high level manager on the planet。

Who could care less about sprints and backlogs and backlog grooming and all of that junk。

They couldn't care less。 They hire you so that they don't have to think about that stuff。

So when you say we're going to do this agile thing。

 and that means we have this backlog and we're going to have sprint reviews and they're going。

 what is this noise I'm hearing coming out of this person's mouth。

Because it has nothing to do with money。Money is at the center。Of all this。

So you want to be thinking about money then。 The other thing that I'll talk about， I'm gonna。

 I'm going continue that。 But let me just kind of finish the basic things here。

 The other thing that is is an issue is fear。What are they afraid of。So again。

 when I go in as a consultant， the first thing I ask the upper managers is I say。

 what keeps you up at night？What problem is so horrific？That you're just worried about it constantly。

And often they'll come up with three or four， which is kind of scary。And then I'll say， well。

 which of those is the worst and that requires a bit of discussion because they say， well。

 they're all equally bad and I'm going to know it's not possible。

 one of them is more of a problem than the others。And they eventually will settle on one thing that scares them the most。

And then you say， let's work on that。And a lot of times， the let's work on that is something simple。

 might be non intuitivetuitive to them， but it's something simple。

So consider the notion of work in progress， WIP。So work in progress are the number of things that you're working on simultaneously。

Okay。Simimpplest， lowest hanging fruit with we needed to get it out the door faster is to reduce your work in progress to one。

It's a very simple thing to do。And you can say to the manager。Let's just try it for a few weeks。

Because if you're working on multiple things。here I am working on thing one。And then， I get blocked。

I need to talk to the。UX people or something like that。So I'll stop working on it。

And then what's this doing？The Internet connection is kind of iffy， and Mi is。

Dubbious about internet connections that are iffy。You stop working on it， and meanwhile。

 let's say you need a UX change or a database change。

The database group is busy working on something already。

 so they're not working as far as you're concerned。

And eventually they'll get some time in their schedule and they'll start working on your problem。So。

All of this all of this space in here。I don't erase， I don't want to erase all this space in here。

Is waste。This is time when nothing is happening。At least if your goal is to get something that is revenue producing out to the customers so they'll start paying you for it。

Lan has this concept of， of。Waste， which is an important concept here， right。

 what we're talking about here basically is waste。 It also has an interesting concept called inventory。

 So inventory is work that has been done that is not bringing in revenue。

Every line of code that you write that is not delivered is waste。

Because it is money that the company has spent and it's not bringing any。

 any revenue for the company。So when we're talking to our managers， we have to say。

Let's figure out how to get revenue sooner。We're not talking about developing code faster because we're not。

Is we get stuff out the door sooner by working in more effective ways。

But what would be working at the same speed within the new process？

Or by simply not building things that nobody wants or cares about。

The vast majority of work that we do as programmers is writing code that nobody could care less about。

And that's completely waste。 It's just utterly wasted time。So you have the whole agile thing， right。

 where they say， you need to build small two day chunks。Release it to customers。Get feedback。

And then adjust based on what you're doing。 They call that the inspect and adapt cycle。Right。

Ill stop it。The inspect and adapt cycle。Where you build small。You release。You get feedback。

And you adjust。And I have the arrow pointing in the wrong direction。All right now， by S I。Well。

 again， another， I don't want to regale you with too many reward war stories。

 but one of the most agile shops that I have ever worked with was a bunch of programmers that were working inside a hospital producing software for the doctors to use。

And one day， a friend of mine was sitting there typing away， doing his programmer thing。

And a doctor comes up and he said， you know that thing that you released to us last week？It's great。

 but if we could just move this over to here， it would save me two hours a day。

And my friend who is sitting there with a code in front of him， types away for a minute。 and he says。

 you mean like this。And the doctor says yes， that's great。 When can we have that， and my friend says。

 you've got it。He hits the commit button。 It goes into Jenkins。 Jenkins runs the tests。

 The tests then deliver after the test passes automatically deployed into the working system。

This is what Devopps is。This is what agility is。And this is a very short inspection and adapt loop。

OkayNow we can't always be working like that。 It's nice to have an onsite customer。

 It's nice to have somebody who's giving you feedback as quickly as you can。

 but we don't always have that。 And often we don't have that。

 So it's going take a little bit longer to get feedback。

 there are many ways to get feedback other than talking to directly to customers。

 One of my friends has What he did is he made。😊，A mailing list for Lavov a better word。

 but used text and any other way that he could use to get older people that automatically broadcasts the commit message out to everybody who volunteered。

Because they were interested in the product。 They they had real skin in the game。

 They were using this thing on a daily basis。 They needed to have it work。

 They wanted changes to happen in order to make their lives easier。

 So they were really interested in seeing those changes when they came out。

So as a side effect of hitting commit， the commit message went out to all of them。

 and then usually three or four or five would log on in。Send some feedback in。Tech support。

 it's a great way to get feedback。Texupport is is dysfunctional in most companies because you。

 what the techupport are doing is they have this big book， this binder， right。

 And it's all full of workarounds for problems that come in so often that they want to script the solution。

 And I'm going， no， you want to fix the problem， not script some workaround。

But the problem is is that that problem， that customer problem， is never making it up to engineering。

RightBecause tech support has been outsourced to the Philippines or something。

 And the company is here in the states or somewhere where you don't have direct content。

Communication is too hard。So that's a way to get feedback。 But the point is。

 is that you're delivering small。And you were。Getting it into your customers's hands as soon as possible。

 Now， going back to this graph here。Right。Let's start over from scratch。 right。

 Here you are doing something。 You get blocked because you need UX。 Here's the UX people。

They finally get around to doing it to helping。They do it and give it back to you。Meanwhile。

 you're off doing something else so you can't get to it immediately。 so finally。

 you get to it and you release it to the customers。And then you get some feedback and they say。

 I can't figure out how to do this。So it goes back down to UX。Eventually。Now。

 the work to waist ratio here is pretty high。The only time I'm working is when that curve is up。Now。

 the problem is that they'll come along。 the programmers are not going to sit there idle。

 though you could argue that that would be the better choice。

And they start working on something else。Until that has a UX problem。

Which just gets us into the curve， probably over here， symbols。

Doess everyone see what I'm saying here？Jerry Weinberg。Who was one of the greats。

 He passed away a few years ago。Okay。Made the observation that you lose。20% productivity。For every。

Additional thing。That you're working on。All right， so we have the situation then where if I'm working on three things at once。

Between the context swaps and the delays and the blocks and all of this other stuff。

 I will be working at 20，40，60% less。Effectiveists， than I should be。

Which means instead of something taking 10 weeks to get out the door。

 It's now taking 20 plus or minus。Which means that you're not making money。

Because you haven't gotten into your customers' hands。

 There's it's inventory up until the point you release it till it's actually done。Right。

 and of course。Things are never done， done， but at least it' done as you can make them right now。

So the point here is that。As soon as you get into this kind of。Graph situation。

This is called a value stream map。 If you want to read up on it。

 It's that was developed by Mike Rather。Who is a manufacturing guy who was working with Toyota mostly。

But the basic idea here is， you want to。Ploot out when you're working， when you're not。

 when are you waiting。Those are important statistics to have。

Especially when you're trying to convince your boss to do something。Now ultimately。

 this comes down to something very concrete。Ops。Oh great， I've lost the internet connection。Hello。

Well， we're going to have to continue in red because Miro will only let me change color if the internet is working and it's not working right now。

So。The， the。That was， that was。Mind boggling。 what what was I talking about。

 value stream mapping and， and trying to。Generally， make this concrete。All right。

 so let's say for the sake of argument that you are making 100，000 a year。I looked it up。

 and that's par for some regions as Australia at least。All right， now。

 if you're making 100000 a year， it is costing the company roughly 200000 a year to support you。

This is called load。In software， the load factor is usually between 1。5 and 2%。1 point right。

 or not percent times other is a multiplier。So generally speaking。

 if you're doing a back of the napkin computation， just double it。Alright。

 so if you are costing the company 200 gay a year。And if there are 2，000 workdays in a year。

 which they are， take my word for it。That means you're paying everybody $100 an hour。

Or at least everyone costs you $100 an hour。 You're only paying the 50 of it。

So we just had a meeting。 It went on for four hours。 It had 10 people in it。That's $40 times 100。

 right，$4000 for that meeting。Did we accomplish enough in that time to justify spending that money。

Usually not， right， His meetings are usually not very productive。

So when you start being able to put everything in terms of money。

Then it starts making sense to upper management。So let's think for a bit。As I said。

 about my programming。I'm using this as an example deliberately because it's for some reason amongst the most controversial things that people can suggest。

And often this is called ensemble programming because that's more acceptable in some cultures。

Alright， when you're working on ensemble， you've got the whole team。

The ideal team size is4 plus or minus1。And the。All working on the same thing at the same time。Right。

 so you have to be working on the same code base。 There's lots of ways to do that now， right。

 Intel J has all this teaming stuff is V S code。 I use V S code a lot when I do classes because it's on the web。

 and it's so easy。But anything that let you to have multiple people working in the same code base at the same time is useful here。

 and you can even do things that are a little clunkier is that you can stage all the code through Git。

And there's a shell script that you can get called mob。tsh。 that's also the URL。

That takes care of all of the nastiness of gett for you。

Gid has got like the worst user experience of any program I've ever used。And it's like。

 it's horrific that it's that important。 And I still have to every time I need to do something other than。

 than pull or push or commit， I'm completely lost。 I don't know what to do。

 And I've got to spend an hour looking it up。 That hour， by the way， is more waste。So。

What they'll say is， I don't want to have。4 people sitting around watching someone work。

 So the first thing we have to do is invite them in to a mobbing session so they can see that it's not that。

Demonsstrated。The second thing you have to do is just part start putting numbers on stuff。

 so let's think about what's going on in mob programming and what's going on in the normal。

 what's called a scatter gather situation。And the scatter gather world。

Everybody gets together at the beginning of the day， and they have a daily standup。

And in the course of that daily standup， they figure out what they're going to do over the day。

 and then they all disperse to their caves， which are scattered all over the valley that they live in。

 And they go inside those caves， and they roll a boulder over the front of it。

 And they don't come out till the end of the day。And then at the end of the day。

 they all go back to the central meeting place。And they say， well， I just did this。

 And somebody else said， well， I just did that。 And those aret going to work together。

 and you have this horrific integration problem， which might spill into the entire next day。

That's scatter gather。So you have。The whole team， and there is a standup。

And then they disperse to do the work。 This dispersal in here costs money。Right。

 as they say to stand up， it's only 15 minutes。 But when you start factoring the context swaps。

 And if your work happen to be working in an office。

 you walk by the coffee machine and you get a cup of coffee and start up a conversation with somebody about skiing last weekend。

 and it's easily a half an hour。Most of the time。So your 15 minute stand up meeting is going to take anywhere between 45 minutes or an hour before you start getting functional again。

 You recover from this context swap and start working again。So。Here we have work for 15 minutes。

 That was $25。And here we have $75 of waste。And then everybody does their work off on the side。

 and then they come together。And。More waste while they're doing the contact swap。

And then they try and integrate。They're integrating as a group。Which is an awful lot like mobbing。

 right， It is that everybody's working together。But the integration then discovers problems。

So now you have to go back and rewrite some of the code， might and maybe all of it。

Rewrite waste is very expensive。You pay for writing the code。stop it。You pay for writing it again。

And then there's the opportunity cost。Which， again。

 is something the programmers often don't think about。

Opportunity cost is the time that you could have spent working on something useful instead of doing all this flaiing around。

So it's a three times hit here。Because the original work was didn't， didn't give you anything useful。

 The rewrite may or may not。 We can'。 We won't know that until we try and integrate again。

And the opportunity cost is always lost。 so you've always lost 2 x。And sometimes longer。

Is everyone seeing how this is working？So here we've got another， let's say this is $100。

And this is another 100 down here。As you saw from the graph that I just wrote。

 the down is usually much larger than the up。 Now， the thing is， is， you can measure this。

This is not something you have to guess。You can take a notebook and write down what you're spending your time on during the course of a day。

And real hard numbers。Real hard numbers。Here's how much this this is costing。

 And here's what these various processes that we're in are costing。

 And then then we can look at mob programming。In mom programming， you don't need a stand up。

Because you're working together throughout the day。 You don't need to plan。For not working together。

 you do need to plan a little bit， but it's a much simpler plan because they're all there。Right。

 if you need to change what you're doing right now， you can do it。

 There's no integration because everybody's working at the same time。There's there are。

A lot of other advantages， though， you lose the rework。Which again， something you can measure。

You lose your slash dot time。Or your Google time。Because if you don't know how to do something。

 odds are somebody else in the ensemble does。So you don't have to spend a lot of time looking stuff up because there's somebody there that knows how to do it。

Which means that you gain。Learning time。For free。Because you're constantly learning in small bits and bits and drabs right。

 as you are working。And that's free。It's just part of the conversation。

So if you're talking about a way to onboard people。

 you can't get better than this as you bring the new people and you just put them in the mob and they don't know much to begin with。

 but I can guarantee that they will be learning gradually as you're working and they will gradually get more and more effective。

I's everyone following me here？I left anything out。嗯。Code review and PRs。

You don't need to do them because every line of code is being reviewed by four other people as you're writing。

PoPo requests are a huge source of delay。RightYou put in the pull request and somebody might get around to it eventually。

 And when they get around to it， usually they don't look at anything useful。

 They're looking at formatting and stupid stuff like that。

 And then you have to make the changes nonetheless。 So it goes back down and you'd make changes。

 And then there's another pull request。 and it comes back up again and you go around and around that loop forever。

 it seems sometimes。Well， if there's four people reviewing as you're working， none of that happens。

The problems do not occur。What else that I write down here， there are no bottlenecks anymore。

There are no scrum masters。Because you don't need them。And there' are certainly no managers。

Because again， you don't need them。So the salary of the manager， that's a cost saving。

Bottlenecks delays， dependencies， there aren't any dependencies here。Which is， again。

 a source of waste while you're waiting for the thing you're dependent on。Pidency。

That's a good question， you don't need a product owner。I think a product owner。

 the concept of product owner is an abomination。It's a single point of failure in making decisions about the product。

And product owners often don't talk to customers nearly as often as they should。

 They spend all their time sitting at their desk， pounding out requirements inside Jra。

 making line after line after line of ridiculous requirements。

 which we are not going to implement anyway， because as soon as we do the first one。

 the rest will be rendered moot。Huge waste of time。We don't need to backlog either， I should say。

We don't need Jra。So that'll go。Now， we do need the internet a little bit。

Oh now my the Internet is gone again。Which means I， go come on。い。We don't need Jra。

We don't Jared as a bug tracking system。 Why are we even thinking that this is a good idea to use a bug tracking system for managing our work。

So every one of these things can have a concrete number attached to it。

You can sit down when you're working now and you can measure the amount of time that you spend doing this stuff and you can make a spreadsheet。

And you can go to your manager now and you can say， you know。If we were doing ensemble programming。

 we would save this much money。And we would also get it into our customers' hands this many weeks sooner so we could start making revenue immediately。

That's a good business argument。That's a business case for ensemble program。

If you just try and put it in terms of， well， this is nicer， It's better。

 I'm happier when I'm doing this。 The managers are going to look at you like you're crazy。

But if you say。We've got 10 teams。 They're all working like this。

 You can save $10 million a year by doing this instead of working in the way we're working now。

 they're going to sit up and pay attention to that。

So it's hard to have this Larman's law push back in upper management if you are presenting them with a real business case。

This is what it costs to do what we're doing， and this is what the new thing would cost。Now。

 of course， they'll say， well， you're just about that。 So do an experiment， right。

 mob for a couple of weeks and pay attention， write it down， write all the numbers down。

 So you have real numbers again。You know， and this， this is very much of。

You're asking for forgiveness here， not permission。

Because you might have to go off and do your experiment on your own。Right。

But it's only again a couple weeks we're talking about。 And you can。

 you can push the whiteboards into a circle and nobody can see what you're doing， right。All right。

 so business cases， this is a way to do it when you're talking to upper manager。

Push back on from members of your own team。 That's commonplace。 People sitting around going。

 I can't work here is to is to， again， formulate an experiment。

 Let's just try this for a couple weeks and see。That way。

 we've got some real data to use inside the system。And。The the。

That notion of an experimental mindset is really important。

And that's the cultural change we really need to get rid of Iran's law。

It's to get a cultural change where people are willing to try stuff。

And they have permission for the stuff to fail。So if it doesn't work， that's fine。

 We'll just do something else。So you have to try stuff。I those people who were saying， I want proof。

 Well， here it is。 Here's proof。 We've got hard numbers for you。All right。

So Laman's law is a real thing。People are pushing back all the time。

I can guarantee as I was talking about mob programming。

 there were at least a dozen or two of you in here saying we can't possibly do that。

Which is proof of what I'm talking about。But until you experiment。

 you don't know whether you can do it or not， you're just guessing。

 and I'm not a big fan of guessing。I want something concrete in front of me that I can use to make a decision。

So work from the bottom up in terms of experimenting things on the ask for forgiveness。

's not permission。Work from the top of down in terms of producing real business cases for the changes that you want to make。

Work specifically on problems that management finds difficult。So getting back to the。

 we've got to get stuff out the door faster and you can say， well。

 let's try reducing our work in progress for two weeks and see what happens。RightForte an experiment。

Keep track， right， write down the numbers as you're doing it。 So you know whether it works or not。

So it's all about experimenting。Whether you do it from the top down or the bottom up。

 it's all about experiment。All right。So that's all I've got to say， thank you。

