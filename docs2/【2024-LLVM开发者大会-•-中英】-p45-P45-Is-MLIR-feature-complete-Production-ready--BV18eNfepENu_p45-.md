# 【2024-LLVM开发者大会-•-中英】-p45-P45-Is-MLIR-feature-complete-Production-ready--BV18eNfepENu_p45-

![](img/adefa64086067e77378dec1b04b8bc8b_0.png)

Okay， welcome back from lunch， everyone。 This is our session that starts with the panel on MLAR and is MLAR feature ready or feature ready featureture complete and production ready or feature ready is a good title as well。

 I'm Alexenco。 I'm moderating the panel。 and we have a great set of panelists here with Medi from Nvidia。

 But worked on MLAR a lot and on very practice before。 Renato from Intel。😊。

Ol school L M I guest also harm my our interests Stella from A M D。

 who has a big team working on ML AR in the Erie project。 Tobias was our first academic partner。

 I would guess and now has the biggest academic group using ML AR and doing ML AR。😊。

don't want to mis。 And Chris， I I know it just random guy hanging around to end conferences。

 We needed certain people。 Yeah， we， we needed more people。 So nice。 I was in town。 Yeah。

 he was in town。 So like yeah， I hope Chris needs no introduction in this venue。 but otherwise。

 Chris created LBM MR and many other things。😊，So welcome。And while I have this slide。

This is actually a not working title for the panel I had。 I knew。

I was just get it out of the way at the beginning。Okay。Yeah that's a nice panel。

I was thinking what is there something I haven't talked about at a JLBM conference about MLR and I really wanted to come？

And I decided to look at things like， what have I done in the past years that I can come and talk about。

 And I decided to go look at my commits， and I didn't do much。

 And then I decided to look at what other people have done at the GR。

 And it turns out people haven't done much easier this year。 So when I submitted this in August。

 I made it stats。 and we had like around 2000 commits with MLr tech in 2023 until August。

And around 10 commits sold half of that in 2094。I made the stas for ODM just this morning。

 and we had three MLR open meetings this year until today。 And we had 14 in the last year。

 and we had like 20s a year before。 So the working title for this panel was。Isam are kind of dying。

 Why are people not contributing， So that's my first question to the panel。 Is are kind of dying。はい。

I mean， look in the crowd。 Go。 Yeah， oh， I think they just came to hear a bunch of unated people。

 the funeral。 I think yeah， the funeral， right， It' thank you for attending。

 it's super fun because people ask me all the time is LVM did M is taking all the now the M is the thing。

 So yeah， but I think in the context of different open source project。

 I think I like the terminology of like kind of cathedral style development model and kind of a more federalistic development model。

 And I think from my perspective， what we see with M。

 I think they plenty of features that I'd like to have in the M。 but I think we also like。😊。

As an Ldium community， which was a relatively more towards like a uniform cathedral style development model。

 I think ML is very much the other thing。 We created the most federalistic compiler organization。😊。

That I've seen so far。 And I think that's something that's very uncommon for us as a community。

 So so it poses a lot of challenges。 I mean， in our research group。

 we both kind of copy ML built something like X TSl， which is also really unusual。

 it's I was a core LDM developer。 I was all my code was in LVM。 And then suddenly。

 we kind of ripped this ecosystem into pieces。 And I think this has a lot of problems。

 But I think it also really new opportunities for us as a community。 And maybe， yeah。

 that's kind of my take on what we are seeing。😊，I mean， my take， you're being awesomely provocative。

 So please keep doing this。Is there's more of a graduation thing going on。 right。

 So another interesting chart， I don't know about the data is if you look over the last six years。

 and MR has been a thing。 what percentage of the talks at L meetings are about MR。

And its users I actually looked at that and the set number was not going my way。

 So I did not put on this slide。'm sorry I didn't serve your purpose。

 right yeah but okay I did the number I can give last year this event。

 we had 10 talksR10 long talks isR is a title this year。

 we have 9 So 910 It kind if you't module isR， we actually have 13。

 So it's more if you count't DSL more。 but it's also all the users like the there's tons of people doing workshop and and all the others it's allr but so whatever look at is like to just like interpret your data。

 So when you look at the OD。 it's becauserrs graduated from let's teach each other what Mr is until a lot of people being able to use it and get value I think that that to me is a very good sign of success。

 It's not about is it interesting from a science perspective is it practical and is it useful getting built and deployed。

😊，Maybe you wanted to say something。Well， first， I wanted to thank Tobias to qualify MIR as a federalist system when many people would qualify as a nanoarchist system。

 And so that feels so much better to think of it this way。

 and I was about to say same thing as Chris said， you know。

 the open meaning that we had have been a lot about solving problems in MIR itself。

 the infrastructure understanding the needs of the user and outrage。

 in the first years of the lifetime of MIR。 maybe that's a sign of maturity now also that we have less problem with the core of MIR infrastructure。

 we have less to explain new things and new concept。 but。Also。

 the system gets used much more by users。 And so that's why we don't see a decline in the number of talks using ML IR at the conference。

 And we even have the workshop the day before the conference was very successful with more participant than than ever。

 I don't even have the final count。 I'm still waiting on the numbers， but but it was very。

 very attended and talks of pretty high quality。 I found that very， very good conduct。

And so that's another side of the the where we are is the project。 To be honest。

 it was kind of challenging to find those folks to start with。

Like we really had to push people to come and present。

 And that's one thing that I kind of observe as a trend is it is indeed being used more and more。

 and we kind of diverge from the I'm not sure it was really a charter in the beginning。

 but part of it was like I remember Chris on stage saying I don't want to do yet another commizer or yet another bus infrastructure And for canonizer and structure。

 we kind of did that Yeah， but for the rest of the thing。

 do we really want to do yet another arithmetic do we really want to write x plus like x plus0 equals x again。

 and it looks like people are increasingly turning to downstreams and that to me diverges from the original idea of let's not revent things and we are kind of back to the mode where people with especially big groups groups tend to reinvent things in their own let me ask can I jump Jeff you。

how long it would be until canonicalizers got brought up less than five minutes。

I was just gonna say to continue being provocative or to make it a pro way， again。

 try to be friendly and try to help answer questions。 People ask me things like， hey， Chris。

 you said six years ago that you hope that MLR would help unify all these compilers。

Why is everything so fragment And so me being the optimist， the way I look at this， I say， well。

 can you imagine what all these domain problems people are talking about solving and using MLR for today。

 What these teams and what these people would be doing if MR didn't exist。Like， think about that。

 Think about just like the ML workshop or as something like all these domain problems or all these fancy chips。

 all these different domain problems like。They probably the chips that exist， right。

 But what happened is you'd have even more fragmented sub communities of individual companies。

 like not able to speak the same language。Right， and I think the MR first charter。

 which I thinkre it's a great framing ox is like it didn't have to unify everything。

 That's impractical。 people do have different problems， right， But。

 but unification isn't a binary question， right And so even if you just unify past managers and canonize and OD S and。

The concept of the dialect。 and like， even if you just do that。 And you don't even have dialects。

 like that's still significant progress in terms of， I don't have to reinvent SSA again， right。

 But then if you say， yeah， R， actually， Rth is widely used。 Linux was widely used。

 Like a lot of these things are widely used and， and very practically useful。

 That's actually a huge contribution for those domains。course， to to tell you， like。

 that doesn't help a lot for hardware design。 But then you go look at circuit。 And it's like， okay。

 well， actually， there's some prequel stuff happening here。 And it's do you attribute that to M IR。

 Well， it wouldn't exist without it。 And so there's like these different ways to look at fractically the contribution over time。

 I'm just not sure it's the same language they were speaking。We might be talking about arithmetic。

 but arithmetic is different depending on the hardware。 So one person says this works。

 The other person says this doesn't exist。 So even though we are all talking in the MLR area。

 So you get a lot of questions。 I subscribe to all of the new。Topics in the ML IR theme。

 but only the first one， right， I don't want to follow the whole thing。

 And there's a lot of people coming in say， oh， I see that there's this dial like this and there's this operation。

 which I think does this。 Why doesn't it work， And then an answer comes along and says， oh。

 it's because it was not designed this way。 This is what he means do it this other way confusing。

So I think and the person says， thank you goes away。

 And it' like when I started with L VM is like why my EDG pattern doesn't match the I because this is what Kang does So do what Kang does right it worked。

 There is an answer exactly at least that was an answer。

 But I think the design of IR happened since VR and especially Nikkita's rust presentation that was awesome。

 this is what we need like okay， we have needs and people have different needs。

 And what do we actually mean by these things It's not just we are talking MR is we need to talk what MR is and how we interpret it and how we get to the solution that different people need without solving every compile the problem under the earth。

 That's the question don't have answer for。 I think what I find like relating back to the topic is done or not。

 think is actually interesting to see what is， which done or not basic。Data structure。

 block data structure。I guess it's mostly something we agree on， right？

 I think we really transition from like like defining these core data structures to， I mean。

 maybe the last four years is kind of building AI compilers。

 And some of you say this is still a difficult problem。

 But that's also like where you have major industrial teams building these compilers， right？

 So so they are the problems of how do we finalize them， how make them nice。

 maybe how to to share more of our technology。 But even that its a relatively mature ecosystem。

 I think， But I think the other thing that I almost would say like we actually at the very beginning is is if you look at the really the breadth of M IR across communities that have never been working together。

 Collaborating together。 I think we probably over the last years， created one of the。Least organized。

 most diverse， most controversial communities in the kind of P space。And some will say， okay。

 that is really deeply annoying。 It's unarchistic。 it's crazy。

 but kind of if you look at like some of the recent dales or whatever。

 where we really want to build like compiler technology that crosses way beyond the CPU model。

 I I think step number one is to kind of create this mess。😊，And， and。

 and I think we are like on day two of。Fraiging out what we do with that mess。 Yeah。

 I think progress is super funny。 if you zoom out and you look at progress， right？

You can always see that the world and technology and things are progressing。

 And it feels like there's a linear improvement in technology or GDP or whatever it is that you're looking at over time。

 But if you zoom into one of these things， what you realize is it is in a straight light at all。

 what it is is actually a gigantic freaking mess and two step forward， one step back。

 like things that work and don't work And then the question is like。

 do you have a consistent value system， do， do you have a shared notion of what success looks like。

And if you don't， then what happens is you do this and you get pulled all over the place。

 But if you're making progress and you're just disagreeing about how to do it， then。

 then you're still getting somewhere。But plus one you， like whereas MR for biochemistry， Where。

 you know， the unification of SQL and query optimizes， Where you。

 I think there's plenty of work to be done。 I think French law， I found that really interesting。

 There you go。 So yeah， yeah， yeah， why is Lang chainin not using MR。😊，I mean。

 part of that question or the thing that I think of just because my brain has to work through ordered lists is that。

Is， you know， M IR is a lot of things。 And what isn't is it done or is it alive or is it dead。

 But what parts of it are done and what parts of it are alive and what parts of it are maybe experiments that。

You know， we， you know， maybe it's time to move on。And。I， you know。

 just looking over the last five years， which I mean， we've been building this thing for five years。

 it's，20 Yeah， it's you know， I think that ML Air core is is done in a good way， you know。

s there' there's always things to do， there's always always more to do。

 but like I'm not going out saying， hey， you know what you should use what's really cool。

 M I Air core， people already know about it。 Like if you've got this job you use it。And。

A lot of the core stuff。 And， and， you know， so part of me wants to say， while we're doing this。

 walk through the woods， how do we walk that in， How do we， how do we make that production ready。

 How do we， How do we make that useful and all the things that needs to needs to be used for that aren't just。

 you know。It's being used a little bit under duress sometimes because it is it needs some finishing。

 But that's where my mind goes。 You know， someone asked me how do you， how do you use MLR unify AI。

 I'm like， well start by by securing the foundation， get ML I core locked in。

 let's get it layered right。 you know this is this is at the good kind of done。

 get the core software abstractions locked in， get， get them layered right， you know。

 get them get people who who are。You know， have described that inspected out。 And， you know， there's。

 there's a charter for it。 And， you know， that creates the space to then， to then say， okay。

 these things are done。 Like now let's， let's focus on some of the other stuff。

 And all compilers are still are still staggering around。 You know， we've got。

 that's kind of where this， this whole thing started。 and then。It， it could could still go anywhere。

 You know， you've got， you've got lots of bets being taken from language language based stuff like Mojo and Triyton to to more classic M O compilers that are。

 you know， op soup op soup distillation is I don't think I've called it that before。

 I've called it many things， usually swear words， but。The， you know， let's。

 let's give some space for that to go。 But let's lock in。 what's good。 Let's， let's， let's do that。

 Let's make it better。 Let's make it， you know， So it's not part of the。

 part of the rest of the soup。 I think that's， that's how I would answer the the question let's。

 let's say we agree。 This is core。 This is nonco。You might take some time， but let's say we agree。

 which means this is now graduated， and this is undergrad。Do we when things here graduate？

They don't need to graduate into MLra coreps or they can graduate to something else。

 I think we should treat those things as project like they don't need to inherit the original mission and like they should be projects and they should and they don't necessarily need to follow the same rules either of you know the highlander rules if there can be only one you know and that sort of thing shouldn't be that's whole points right and you know if they need to do things differently so be it but no I don't think I don't think everything graduates to MLR you you've got all of MLI's children at this point and they're going grand they're going to different schools it's fine。

To me that Oh sorry。 to me， that phrase is more the question of。Like if。

 if you describe things that separate projects， then you know。

 it's like where what is the community around them and what is the mission around them。

 Because we are talking about debatting from the mission of MIR and MIR is in L VM to to fulfill a given mission。

 So there are components that， you know， starts needing their own space and their own mission and their own roles。

Like the the graduate， like that becomes incubator project or， or just separate projects。

 separate organization。 I think there are tons of successful M I R based projects outside of。

not everything has to be inside the L VM to be successful。That's probably as I think it's more。

Reflecting what already happened rather than trying to create something。 So people already， as。

 as I said before， people already talk different languages， even though we all talk ML IR。

 they're worried about different things。So we're just basically saying these people flocked together。

 those people flock together。 and there's an intersection， right， So if we encode group set。

 set intersection， then it's not divide in the communities。

 It's just making it clear which subsection of the intersection you belong to。

 We're gonna need to DSL for that。How should we do that second， second， DSL and commization。

 There you go。 We've done it under 30 minutes。 I was talking to Steve earlier， and he was。

 he gave a nice analogy， which I think is really worth to think about is it's when Emeller came into existence。

 Like conquering a new planet。 The first thing you have to do is go terraform the planet。

 go figure out what the laws of nature are go。Figure out what this thing is。

 And it's a very messy process。 And now I think that we've conquered Planet M IR。

 but we need to make it livable。And so as we're， as we're getting into this next phase of evolution。

 I think that it's not about， So your numbers， for example， it's not about MLR are done。

 It's about more of how do we structure the community。

 how do we figure out the tribes and get them factored the right way。

 How do we make so the infrastructure is more clearly explainable。 How do we make it。

 So somebody new walking into the community and say， okay， that's ML the good parts。 this is MR。

 the other stuff。RightYeah， and I guess in the spirit of being provocative。

 I think that like one way to to， to petition the kind of communities between kind of good and bad。

 right， what is good and bad。 And I mean， And obviously， like we are scientists。

 we are typically the black sheep。 right， like like not delivering a product。

 not delivering production quality stuff。 And yeah， I think。😊。

Maybe also like thinking about like what is still to be done。And I think maybe maybe one。

 one kind of technology that hasn't been built a lot in the M I community to。

 to the level I think that could have been built or should build be built over the future is do we actually have community management tools。

That scale to to what we've built。 What you mean， Yeah， that's what I'm wondering。 What what。

 what do we actually need， Do we need more compiler technology to manage our ecosystem。

 Do we need something entirely different， right， How do we。

How do we enable efficient communication at a level that that maybe doesn't scale to the LDM mailing list。

 right， I mean， historically， like when I wanted to contribute something to LVM， I posted a patch。

 I have a conversation like 10 people answered。 and they say that's how you need to evolve scale evolution。

Today， when I want to do something in MLya， I mean。

 how do I even reach out into all the different communities。

 How do I understand how far do I need to reach， right， I mean， there's this entire。

 like I call it kind of secret social engineering in the LdM community。

 Like if I want to get something done， I talk with the right people。 I kind of get things organized。

 I historically knew how to realize like。I think it's the same thing right。

 It's still the same tactic， but it's just more people larger thing。

 I think it doesn't you don't know who the people are right So in the case of all ofM right。

 there's clearly delineated subproject And so if you want to go asked above questions。

 you want to go ask cogen questions if you want to go ask lip equalQ plus plus questions。

 ask whatever like you can know where to go， but MLr is two monolithic。Like， as it has grown。

 what that means is the community has grown， which is a good thing。 But then M is still one thing。

And so because it's still one thing， right， The problem is that any of the individual stakeholders or participants or whatever gets awa Let speak for myself。

 gets awa with all the stuff going on。 And most of it， to your point， is not interesting。

 And so if you， if we provide more scaffolding and more。Like there's an AI subsection。

 There's a software subsection， I think circuitatory， the hardware subsection， right。

 then it could out more focused community and discussion and more cohesion。

 but MR is is much harder to split than L of V M。 because if you talk about M L。

 you involve what tensor memory， line knowledge vector or whatever。

 you talk about you got some clumps。 you do do， But these clamumps are not necessarily mutual exclusive。

 So if if somebody really cares about lineage from M point of view or from HBC point of view or something then they're going be overlapping groups caring about different things。

 I think it's possible to have too much of an ontology and this group might be prone to that。

 Yes the。I I've described this before as， you know we're currently asking people to walk into a stadium and kind of self findd row 36 F。

 you know， that's where Low lives。 and then like want to maintain row 36 F。 And you know。

 that's just not how social communities work， you know， there needs to be。

 there needs to be homes for this stuff。 you need to create， you know。

 create a sense where people can。Can， you know， want to improve an area because there's， you know。

 people know who， know who the， the main decision makers are， You know。

 the main people with the experience there that。And， you know， can have conversations， you know， and。

 and and happen。 I think that that's that we just need to start fostering more of that in Emier itself。

 We， you know， part of it is getting the， is getting the technical。The technical dependencies。

 you know， I would say， more encoded into the project before。

 before the core contributors stop caring and and enforcing that。 You know。

 get the project needs to be more of a dag and less of a。lessss of a circle。

 but the but more important to me for the health of a project is the social dependencies， you know。

 which is part of what Chris is saying， part of what Tobias is saying， part of what Renao is saying。

And， you know， for that， you need， you need structure。 You need charters。

 You need people to understand what the component is， not just the the entire thing。

 And that that helps helps sort it。 And it creates some optionality， too。

 The whole thing doesn't need to succeed or fail。 or not everything is the rock star situation。

 And some of it is。It just， you know， it's all the different phases， but we need more， we need。

We need to let this thing grow into some some standing cls and the technical decisions may the technical background may change over time because you see。

 I created this with this intention。 But now it's used for all different thing。

 And this is part of it。 you don't throw away because you said originally intended for this one。

 So go create something else。 evolve it evolves I think it's the lineage has evolved from you know。

 mainly one core thing to multiple things。 And now part of it is my fault。 and its like， okay。

 that was the wrong way to go。 let's try to simplify now。 And I think it's a valid exercise。

 of course， I would prefer to have been right a year ago。 but sorry。

 So progress is messy yeah exactly yeah， I guess one thing I'm wondering about like I mean there's social challenges。

 And I think that will be really interesting process as a community to manage them。 But for me。

 I think one of the things from like the LBM days， but I learned that。

Communities kind of we use technical tools to organize our communities， right。

 So I think one one summary of what LDM is for me is it's like like line based deform that is driven by P check。

That that is pretty much what LBM， the LBM community is as a whole。

 We are writing fire check test case。 We know how to use it well。 and。

 and in a way that that obviously it's just a small part of what LBM is。 But。

 but that organizes the community。 And so I'm wondering a little bit in LBM， what。

 what are this kind of what what's like。😊，Are there additional tools like F check for MLlaya in the like most abstract sense that would be really。

 really beneficial to organize ourselves as a community。 For example， I gave Alex。

We should fix tableboin。 We should fix tablegen。 No， tablegen is good broke。 Okay。

 this is the most don't We had too much agreement on the panel。 I had to throw something in。

I thought you're going to suggest we'd replace this course with Git。Now。

 he was saying that we should replace tablegen of Cma。'd be fantastic。

Table gym doesn't have enough streams。 we can obviously plug IRDL。

 but then Chris will say that's just a research project that should be deleted。😊。

To make a little bit more controversial。 I think that's interesting， right Yeah。

 I would try to turn this a bit because I think we seem to all agree that there needs to be some work on like structuring the community。

 and we might disagree on how specifically it is。 And like it it's kind of technical。

 What's interesting to me here is who is going to do it work。

 who is like willing to do the effort and who has credibility and maybe authority to do it work。

 I cannot like just go and pick random person you were there。

 You are now in charge of defining what are the difference some I mean this is where it's I think。

I think you need to just approach it incrementally and from the top， which is that， you know。

 the the process of sorting a list of things， you know。

 it's the easiest to take them take the biggest and you know， move that。 I think that， that you know。

 we， we don't do a service to the community either by assuming that there's like this has to be completely organized。

 We are an anarch as collective after all。 and。The Federalist anarch is collective， I guess now。

 But the I， I think that， you know， if， if we start， if we start minding the house a little bit and。

 you know， boiling out projects thing， this is done we。You know。

 it's five year anniversary of Mgar core。 Here's what the software tier is。 You know。

 here's all this stuff。 Then that's gonna get， that's going to p people people's attention。 You know。

 people， it's it's a time for self selectionction。 It's a time for for some of this。

 And we let that organize a little bit。 We created this over five years。

 We're not gonna like do a sort next month And， and suddenly be in a good place。 so I agree with you。

 I mean， it's not nothing going be fixed overnight。's， that's certainly true。

 But I think what the and maybe your point is community wants guidance on what success look like。

If we can't identify as a team what success looks like， then people continue to pull against。

Let me challenge you， Alex， I love you。 There actually is a new way to make decisions around here。

 It's the new governance so one of the things that will happen。

 I think it was in January ish is the new committee is going to be formed to help guide and direct M error。

 And so that could help。 But doesn't， It doesn't eliminate the fundamental question of like。

 how do we actually solve the problem， even if we can make decisions。

So one of the things many of us had a conversation on Monday about， which I think is。

Would be fantastic。 And actually， before you even go there。

 let me tell you one of the things that bugs me。😊，As a longtime LVM person that has certainly fond of it and wanted to be successful。

 when MLR came in， it was a very innovative， new， crazy thing。 We were all trying to figure it out。

 It was in his teenage years。 It hadn't grown up yet。

 And so when I joined it had a lot of energy and things going on， we wanted to move fast。

But LVM has a number of projects。 There are a number of aspects of the way we all function in the LM community that forces things to move a little bit slower because we want a higher quality result。

 And you get a tragedy of the commons when somebody drop something in the tree and now rest to maintain it。

 The one example of this is if you want add to code generator to LV。 Of course， you can't just say。

 hey， I a new micro architect or some new processor。 boom。 Here's the first third of a target。

 I'm gonna to drop into L。 Now everybody gets to maintain it。 Now I don't have to merge it anymore。

 Instead what we have is we have。You know， short， but a written list of， hey， well。

 here are the rules to put an experimental target in tree and it has to have like some test cases。

 It doesn't have to be。Like it doesn't have to be perfect。

 but there's a criteria And then here are the rules for to graduate into a built by default target right it's pretty simple and you know lots of people have argued about it and the consequence of this approach is it means that the things that get into the L ofVM tree and therefore have to be maintained by the world there's like more energy required to reach each of these states and so it means that the stuff that gets there is more serious。

M IR， in contrast has allowed lots of stuff to just enter the tree。 There's no real oversight。

 And so coming back to conversation we had on Monday。

 something I think would be extremely awesome for both the existing code。

 but also for particularly for new contributors is if we came up with some kind of schema and said。😊。

Here's a stable feature， like canonicalized。 I think canized like fine。 Maybe it's not done。

 but it's pretty stable。 Like， you know， I think we， we know what that thing is。

Here's an experimental feature。 It's still moving It's still changing in various ways。

 and it's a different category of expectations where like building on this means you may have to do some work and may be changing。

 Exp debate， whatever， like the expectations are quite different。 And here's。

 I don't know what the label is， a science project。Like you want to put it at the top。

 No clearly science project that science project abandoned where or like。

 I think we still have the unrolling Ja pass。 just mentioned science project and abandoned where the same thing what I mean by that is I love research right。

 So a lot of innovation So isolate you guys came from research But but what I mean by that like unrolling Ja pass from 19 or2018。

😊，Well， it hasn't been maintained。 then it being in the tree is actually harmful。 Y， And if we do。

 if we think about that， and we just came up with the。I hear a hierarchy and a set of criteria。

 Then what we could do is we could go around and label things。

 And what it would do is it force some questions like who maintains this code。

 And if nobody raises their hand and if it's not fully working and stuff like this。

 then we have a separate question of like does it belong in tree。 And I think we get to a healthier。

Bate for the project， because lucky enough， we already have a policy for that。 for the targets。

 So we can just repeat the process。 Yeah， again， this is where， again， N came into the tree。

 And I think it was good that it was able to move really fast， because。😊，Getting figured out。

 And it was innovative。 And we didn't know what the outcome and the answers were。

 But now it's in a different state。 Lots of people are built coming back to the title。 Yes。

 Mre is in production。 lots of people are building on top of it I it ready to be in production。

 So it is but but the part definition， It is in production， therefore， it's ready， but。😊，Well。

 but the problem with the question is it's formed because MLLR is not one thing。And so actually。

 the reality of the world is that。Parts of MR production， Part are not。

 And particularly if you're a newcomer coming into the community， you have no idea。

 And so you pick up something that's attractive。 You're like， oh， cool。

 this's gonna to solve my problems。And then you're like。

 oh MLR sucks doesn't work and you get the self selection where you ask is this dialect ready。

 the owner or whoever contributes， yes， it is， but no it is according their opinion and there's no the one guy exactly because I mean what I hear is you're raising kind of like a science quest。

I think we like like talked about tools for organizing our community。

 I think we are seriously lacking tools that help us with like this process。

 And I think the Ld processes in a way are really sensible to apply to M IR。

 But I think there's also really like in a way， we want to scale these processes。 we want。

 I think we really want tooling。 Like I think Alex M IR chart is the best example。

 like like it's it's one of the first kind of。Pohools we have to， to， to， to。

Characterize what the community really is。 There are many aspects。

 like the number of cons to like a subpro the quality of test coverage， all of these things。

 which I think all exist kind of in our heads help make things quantitative but we need tooling to make a quantitative。

 we need tooling to communicate the knowledge that we have， I mean， if I ask you Chris。

 which dialect do you think is production ready。 probably know that good for some dialects others someone else will know And others is just I mean。

 I would have， I mean， if you me that， I would have to give you these hearsay answers to your be like lots of people use a。

 It's a useful thing。 lots of people use Linux。 It's brain And so it's useful thing doesn't。

There's no criteria for that。 It's just what I hear people eat。

 but what I'd also say I just add color to this is that。嗯。How should I say this？

MLL is a top level directory in L VM。 Like there can be other top level directories。

 We also have incubator projects like circuits。 circuit's awesome。 Like I love it。

 and it's done tons of really cool stuff， right， And so there's lots of ways of structuring things other than just everything in MLR。

 And the flip side of saying MLL is production is to say， no。

 not everything under the MLR tree is production。😊，Be you wanted to say something。Yeah。

 just introduce some nuance earlier or someone maybe Ranato you were saying like we look at whether dialect is production and the author may say yes。

 some other people know that raises multiple question to me first what does it mean to be production is an interesting question itself。

 So that one person， it is in production。 But for others and then being in production is also very contextual。

 like if if I take some example，FF is used by many production tool out there open triton。

 for example， useF4。It doesn't miss a little。Anything about the SF dialect as the wall。

 because SF dialect is more than SF 4 and SF F， which are the main construct used。

 There' is also a4 or and parallel 4 with reduction。

 And even if we look at the parallel4 at some point， it've got the addition of reduction。

 which may not be supported， in all cases。 And so it's very nuance and subtle when we start talking about this kind of thing。

 and it's difficult to identify what we mean。 and even even if we take just a single up in a single dialect。

 it might be。Yeah， there is the the， the definition。 A dialect is first。

 the definition of a semantic that allows you to represent the program。

 And then there is the incarnation of this up through lowering for specific targets and。

The fact that there is an LLVM Roing for that workss well on CPU and that is robust for SF4 doesn't mean much about our GP implementation or about in other context。

 so that's why we have to escape the， I it production question because it's still form right。

 And that's， that's not something that anybody can answer。 but you let me answer。

 you can answer questions like。Does it need its specification， right。

 So let me give you an example of this。 I would claim。

I believe many people would hopefully agree that arith is a pretty stable and useful thing， right。

 But on the other hand， to many exactly your point。

 Arith is mostly production and stable for scrs and vectors。 It also works with tensor。

RightAnd so if there was a discussion about， is this saying stable， what you'd say is you'd say。

 well， two third of it is。And then we'd say， are we going to finish the last third or should that be moved out？

Right，And I think that is really the question that should be asked。 And so if you have this criteria。

 And your point， the question isn't， does somebody use in production。

 Because somebody with's an experimental target might say yes， like I use in production。

 it's really important to me。 That's not the question。 The question is， does have strong maintainers。

 I it test。 I it satisfying it the invariance that the verifiers produce。

 Does it meet theman like these things are objective And so I thinksor athon tensor is a good example because there a particular group of people who use arython tensor。

 And it's very important for then。 But is not well defined。

So for the other people who want to use either they use in the same way of this group of people or it doesn't work。

 So is this well if it's not well defined， then it we either make it well defined or we move it out。

 And， and just from my old school， I care about L be more success and long term perspective， like。

 I have no。No stake on like what answer you take， but either make it work or get rid of it。

 either way it's fine。 But， but doing neither is actually really not fine， right。

 because that's actually the problem。 And that's the state that we're in today， which is no problem。

And so anyways， if we push forward some of the project。Governance。

 some of the how we think about things saying I think it would force some of these conversations。

 And then I think that would be very healthy for the project。

 I think that what that would do is would force us all to have those conversations。

 have those debates。 It would be messy。 It would be challenging in some ways， right。

 But that's how progress is。I guess one question and sort of come back to my previous question。

 we sort of diverged。I think everybody or I hope everybody is happy to have a conversation and adapt things。

 but it's， it's all just work。And then， and how， I guess how do we make sure people。

 all people who contributed， don't just say， you know， it's just kind of too much work for me。 I。

 I'm not going to do it。 And nobody else is going to the thing just disappearly。Well。

 so that comes back to incentives。 And so as an open source project。You can't tell people what to do。

Like， I can't say， like， have one of your students go do this thing that goes and re this code。

 like that that never works。 nor can you say even somebody in good faith， like， you know。

You know they want to do that， but it turns out they have a really important P1 project that gets dropped on them like and they disappear for a year。

 right。But from a project perspective， you can say if you don't do this by this date。

 we're deleting your code。And so if you do that， then what you're doing is you're empowering the stakeholders who care about it。

Go back until their management。 I need to allocate time to this thing or else our codes getting deleted。

 That's bad for us。 We need to invest in this。 And now there's a really good reason to get the people who care about it to invest time in it。

 And so if you invert the questions from， hey， who wants to make the world be less yucky。

 who wants these features to exist。 Then you get progress。

 That's how you can actually get people not not not because everybody has good intentions。

 It's not about good intentions。 It's about convincing your boss it's worth you spending time on it。

 right And And then what you get is I think you would look at the distribution of the code basease。

 And you'd say some people care a heck of a lot about parts of the code base。😊。

And so you get a lot of people willing to step up and say。

 for a variety of reasons I'm willing to invest in fixing these issues like Earth。

 I think a lot of people care about that， right， for example。Other people， you know。

 not to pick on an unroll jam。 But like， you know， and it's not dialect level。 It's， it's。

 it's much finer grain than that or maybe parallel for you know， or whatever it is。 Like if you。

 if you go and ask these questions and you say， okay， well。

 then let's motivate the stakeholders who care to invest in it。

And that's how you get something that's great rather than something that's attractive。

And this works much easier if it's bottom up， right， You have a real problem。I solve this way。

 You solve the other way we discuss。 and we add this and then starts building up。

 if you try to come top down like lineage is this。 And then you don't even know what this is when you try to lower to harder。

 then your discussion is voido there's no no end to it。 So you need to say， okay。

 I really for instance，f parallel。 I want to hoist configuration file to the thread level。

 but I don't know if my parallel is one thread per parallel。

 or if there's more or if's more than one parallel per thread， So I can't do the hoisting。

 I have to have something。 Okay， this parallel is guaranteed to be one per thread。

 And then I can takes a month， I this a thing that other people want， I don't know。

 So we need to talk about the actual implementation。

 So how do we do things just just talking about oh， this dialect use this tensor。 Therefore now。

How does he use Tensor， Right， Is it just a tensor type， Tensor operations well。

 and this is something that's not obvious。 And its， again。

 me as an old old dog in this world like LVM doesn't have to make everybody happy。Right。

 and so we've gone through this so many times over the decades now， where somebody's like， you know。

 I'm the Windows maintainer。I'm the only person that cares about this target。

 but I want to do X and Y and Z and W。 and like。Maybe you they're jerk about it or whatever。 And。

 And like unless you do this， like whatever。 And you're like， well， that's incomp with our goals。

 long the leave。 It's like， well。Leave， and they did。 right。 And， and that's very hard。

 And similarly， when you talk about， another great example， this is there was a hardware company who。

 very early adopter of L VM went and built a really amazing proprietary thing。

 created a huge number of auditory patches and did all kinds of cool stuff for their users。

 came back 3， four years later。 And they're like， wow， L VM changed a lot。

 Now I have to rebase all this stuff。 We should have stable APIs。😊，Right， and the answer is like， no。

 that's not good for the project。 And so there。Very grumpy in all these things。 But it's like， well。

 the North Star has to be what is good for long termm success and scalability of the project。

 It's not about somebody grumpy because they're always grumpy We're engineers， right。

 but you have to think about that from a long termm perspective。 And this is where I think that。

 again， L M is kind of in the N error is kind of ins past the adolescent phase。

 It's now lots of people want it to be in production。

 And so I think that the criteria has change from what it was like when it first entered the Monte Repo。

But I guess one thing I'm wondering is， like people say， like we need to define what things are。

 right， So， I mean， we， we can think about Webassembly。

 like several people from the AlBM community started to develop or could develop Webassembly。

 and Webassemb is super strict。 right， There's no Webasse assemblyly feature that doesn't have formal semantics。

Weassembly knows what everything mean。 It's also a lot slower and kind of getting like more feature。

 especially from semantics for like。I mean， non， non arithmetic starts to become quite complex。

 So I'm kind of just wanting to throw that in the round what， what。What do we think about this。

 Do we， I mean， how chrom is one of the most extreme ways to。I mean。Test and。

 and and clarify what something means， right， in theory。

 like nuon Lopez and Don started with like like。Pmalizing algaium Fanggra。

Do we need that for MLL to which degree do we want it， I have to answer what MLR is for that。

 Like maybe for some parts。 But I know， if if you're just saying what MLL is now。

 subdivide it and say what what what you what MLL。I think I'll go even deeper。

 I this what John was saying is。Their formal semantics is one type of verification of description。

 You can have multiple types of description and verification。 For instance。

 the example of iteration space in the Mamal versus the floating point precision that you get by reordering things you don't need to care about floating points when you just going back to F4 or F2 or whatever。

 So it's harder to talk about formal semantics in there because there's just too many variations that you can't prove them all。

 if you just say， look， I don't want to formally verify fine。

 I just want to make sure that the induction space is the same。

 And then this is a valid transformation because this is a high level thing。

 And some people care about the very low level stuff。

 other people want to care about the very high level stuff。 But you have to be flexible in there。

 you can't just say， oh， the lineage has this semantics。

 And I need to prove for every single FP type to every single input type and whatever。

 It just doesn't。 It's not the purpose of lineage。To be verifiable， at least in my view。

 right it may be the purpose of a reith or some Nvidia Intel X 86 are fine but then they already done this the no but anyway。

 they should have already done this at the IA level for instance I don't know。

 So I think there is a place for some verification I really want to see like verify to be actually useful。

 but I don't think formal verification throughout the entire space of a floating point or something would achieve that。

 Well， I think one of the things you're identifying is that their show should be or makes sense for there to be different criteria applied to different things。

 So I think one of the previous amazing talks that was given by some of these folks are like what are the different dialects。

 there's border dialects or lowering things。 there's like these kinds of things。

 And so if you have a border dialect that's just about ingress from an external community or egress out to another community。

We can define that fairly precisely。 like we know the allium dialect should implement the same things。

That al does for example， And so that would be a place where maybe formal methods could be helpful right I would be a little bit concerned about saying like something has to have a formal spec in order to be accepted because then it becomes less inclusive we probably。

 And you can only and have a spec like all these things that work well seem to be saying ease spec。

 it's kind of technical solution。 Maybe you need to have a spec for what components are or for what like spec for people。

 I mean going back to what the bias was saying about structure in the community we need the way to specify who is interested in what describe what you're currently interested in what is your company willing to invest into and that kind of stuff。

 That becomes like a money by I mean be honest one empirical thing be to do is like take every file and say。

Of the last like the data you're producing， looks like over the last year。

 how many commits were changing that thing versus how many commits were just large scale factors that touch that thing。

Like just look at that distribution percentage。 And what that is。

 is that's kind of an overly simplified metric that could give you a distribution says like how much maintenance burden versus how much evolutions happening Now。

 some things like canonicalize or I don't know， whatever are probably done。

 And so you'd expect that the number of like functional enhancements to it would be low， right。

 but but other things。That are less mature， right， You could look at and say， okay， well。

 nobody's actually working on this thing。So we started， we started with a simple question and。

Got to formal verification。 So I think the talk is probably done， but the。It's。哦。

I didn't we cover canonicalization in the middle， but so we're good。 we should。

 everything has been done properly。 you know I do think that if just to make it super practical。

 I know everyone has a day job， whatever it is。 And I know from my day job what I care about immensely is that MLIR core itself is an asset I can depend on for the long time the long term that the software abstractions。

 the control flow SCF， LVM integrations the GPU dialects。

 a hardware dialects are well maintained and have good owners， those are top of my priority list。

 right below that is that that you know the classic tensor programming dialects that you know kind of evolve from Xla Tensorflow into a lot of different different shapes and forms。

 you know this is part of my day job and I want to make sure that that that has a center of mass and an owner and you know formally verified or not。

I， I'd like those clubs to exist at some point soon。

 and be able to be dependent on for the long term and have good maintenance and all that stuff。 He。

 thank you， Stella， I think we are at time。 and it's kind of good conclusion。

 I would really actually love everybody Boston panel and here。

 like to kind of self identify what parts of the Malayri care about and ready to commit time and effort to maintain and contribute to。

😊，So we have time for a couple of questions from the audience。 There are mics。reIn the。Orriors。

No questions。No， we ended form of verification。 I think people were tired。 Yeah， sorry I that。嗯。はい。

Yeah， awesome discussion， yeah。So I write the MLIR Newle monthly。 I took over from Medi。

 and hopefully you all read it。😊，One problem。 Thank you。What I find is like what Alex show， right。

 the number of comments lowering。 but also the number of people。

 So every time I'm trying to write it on on Sunday， okay， I say， I'm gonna write a newsletter。😊，Okay。

 what has Mattia done okay。So the number of people contributing has reduced a lot。

And when these people。Get moved on to the day job。 The improvements to MR is going to reduce。

 And this is， I， I don't know。 industrydutry problem。

 Everybody working on MLR has a day job doing something else。

So they don't may not have time to fix the bugs， identify the bug， etcter。

 maybe I'm just exricolulating。 but you see the problem。 Yeah， I mean。

 thes of people here are managers of teams。 Yeah are you folks ready to tell somebody your day job is to fix So so I answered this in a recent thing of I've got broad discretion to ask people to do things I can't why not tell them to do things。

 the main thing I can't tell them to do is do something that's going be painful or illdefined or you know of go into a quagmire And you know I think that part of part of the succession planning for the project and getting it past the first tier of contributors that all have kind of privileged root access to the project。

 what you're seeing is that those contributors are hitting hitting their hiatus points。

 know and we need to we need there's a lot of other engineers who are the day jobs And you know if we organize this a little bit better before before the root access people。

lose， lose attention。 I think that we're going to be a lot， a lot better at getting， you know。

 those of us who who have a big investment in making this successful in， you know。

 using all of the enticements at our disposal to， to， you know， ensure succession。

 But right now it's too disorganized， just too disorganized。Yeah。

 quick concerts because we are running。 Yeah okay， most of the quick answer is everybody， the the。

 the。A large majority of the patches that were coming in were coming from Googlers。But then all left。

Clearlying myself。of the people more than half of the people here are excoubrs。 Yeah。

 so if you go and run the data and say， how many those patches came for people who were at Google at Google research。

 right， that that is a change。Yeah， I want you to provide the counterpoints because I have a different perspective from what I saying。

 I think that we gain in diversity a lot。 And so in in the early days。

 the team was very small and very Google focused。 And， of course， now。

 many of those people spread out to various companies， but even beyond those companies。

 there are many contributors who have affiliation， I don't know。 How many students。

 many academics who are actually fixing bugs own future。And， and。

 and so I see a larger diversity of people contributing these days than there are used to to be。

 other aspect is that you may see less people， but it also that those people， as M matured。

 are busy building project downstream， as we discussed a bit earlier in the。YeahOkay， thank you。

 Thank you， Me。 And that kind of answers my question。 Sorry。

 we don't have time for my initial question ismalayar dying know it's kind of live kicking and getting better it was a provocative question。

 I had to start a panel to be entertaining。 I see there are questions we couldn't answer。

 We actually have a roundtable in half an hour and I think 245 big challenges in Malayar。

 We kind of thought about this problem before And we see like I think we all collective。

 We see two big issues with Malayar one is discoverability。 How do you know what's there。

 what it does， how good it is， what it is good for， who do you talk to about it。

 and another evaluation。 when you come and want to contribute something is what it is a good thing And I'm like what is the overall goal that you can say。

 I it even worse contributing this thing because some of the people wouldn't even come and say like maybe it's worthless。

 and might end up be super useful for any people。 So come to the roundtable as well and thank you everyone。

 Thank you the panelists。😊。