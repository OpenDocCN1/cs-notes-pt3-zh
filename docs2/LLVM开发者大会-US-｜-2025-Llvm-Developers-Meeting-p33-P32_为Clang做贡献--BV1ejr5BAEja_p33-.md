# LLVM开发者大会-US-｜-2025-Llvm-Developers-Meeting-p33-P32_为Clang做贡献--BV1ejr5BAEja_p33-

![](img/f2c0cb9886f85b8b6d4f49e13227facd_0.png)

Welcome everybody， and thank you very much for coming to our panel talk。

 This is basically if talk for folks who are wondering， I want to contribute to Kang。

 I'm interested in contributing to Kang， how do I actually get started in doing that。

 It's a very large daunting program to get started in And so this is mostly a chance for us to kind of give an explanation as to a good ways to get started and then a chance for y'all to ask questions as to you know what can you do。

 How can you help， What do we think about this， that or the other thing。 I'm Aaron Bman。

 I'm Aaron Bman， I'm the lead maintainer for Kang This is Eric Keen。

 He's also he's our templates maintainer。😊，Shafi Amore。

 he's been doing a lot of our bug triage and he's been doing a lot of defect reports and Corinan Jabo。

 who's been doing he's our Leer maintainer。So， one of the things that you know。

 if you're interested in getting started and playingang。

 there's a whole lot of things that you can get started with。

 depending on what your interests are and where your comfort level is。 So， for example。

 we have a bug database， There's a lot of bugs in it。 even if you don't think I can solve these bugs。

 One of the super helpful things is just verifying the bug actually happens still。

 So you can get dive in just by helping the triage issues。Additionally we have documentation。

 our documentation is not stellar。But it is a good chance for you to go， you know。

 I know a little bit about this flag。 I'm going to go document this flag or this morning diagnostic or this built in that sort of stuff。

And then finally， there's also standards work。 Obviously， we do an awful lot with standards。

 but that one can be a little bit more challenging to get started in just because you now have a standard ease document that you have to read in plus a compiler that you have to understand。

 But the good news is is we also have a lot of resources to help new contributors kind of get onboarded。

 So， for example， I've got office hours。 I run four times a month for one hour an office hour。😊。

And you're welcome to come and just say， hey， I started on this and I don't understand where to go next。

 what are my next steps， how do you get help， we also Discord， discourse。

 asking questions on GitHub conversations and hallways and conference talks and that sort of stuff。

So with that？诶 yeah。Convey my own experiences。 Yes， I remember I think I've read the bit on。

Vanue initialization in the spec， probably once every year or two for the last 20 years。

 and I still don't understand it。But。Yeah， is anyone interested in speaking to the review backlog and the nature of addressing that or how people can。

Contribute somewhat。 So I have strong feelings on code review。 I think that。

We need more code reviewers， and I think。You don't need to be an expert to do code review。

 You don't need to be a C plus plus expert， a standards expert。 Oh。

 you don't even need to understand specifically the area you're working in。

 there is a lot that you can contribute， just doing。Looking for obvious basic things， right。

 So one one thing I see repeatedly right， is like， let's say somebodys implementing new diagnostics。

 right， and often diagnostics have a bunch of options， right？ And so you can simply just hey。

 look at the look at all the combinations。 Look at the tests。 Are they all tested there。 Very often。

 They're not。 Hey， can you please write a test to cover all these diagnostics， right。

 No expertise is required。 this has a big impact。 I'm going to say。

Maybe a third of a time I've asked someone to write a test they've come back and said， oh。

 you actually caught a bug and I fixed it and they have to go and fix it right and so catching these things early is really great because if you don't catch it。

 you land it now you have to go and do a follow up。

 you have to fix it it's a lot more work right so catching this stuff early really does have a large impact sitting you seeing are you testing you you have like a if else loopop or you have like switches lots of cases。

 you see okay you added five cases but you only have three additional tests。

Did you actually test all of these， Right， Okay， if not， please write tests to do that， right。

 summaries， right， I I'm going argue very strongly that summaries on PRs are one of the most important thing。

 right， they prevent。Switching test switching， right。 So I sit there。

 I really should be able to look at the summary and understand fully why you're doing it。

 what changes you're making and what results I should see。 And sometimes， you know， people。

 people are experts They sit there and they just assume， oh。

 this is just obvious right And it's not obvious to everybody And so sit there， I say， listen， okay。

 I see you've changed the algorithm。 You've made a massive change here。 Okay。

 can you explain why you're doing that， right， because that's kind of important to understand。

 right And so again， right， you can contribute to code review without being expert， right。

 you just have to sit there and just take the time and the patients and just。Ask good questions。

I'll say on that the last point on the topic， the summary view of the pull request。

U maintainers are very guilty of。Of。Not needing them as much as others。

 So I think we do a poor job of understanding when they are good descriptors。

 So that is something where someone with middle to low experience would probably be even better suited than us to review those sort of things。

 you know make sure that it answers everything that your fi mention and everything that you would want to know about the patch so that you would understand at least what you're looking at。

And then the handful of times I have been on top of it enough to do that。

 I have also found that that can also bring up new test cases for you to look into and and to suggest or or to ask about to make sure that they're well tested and and。

The handful of times I've seen people actually be going ahead and doing that by the time I can actually get to review it。

 the patchs kind of ready， the self review amongst the nonmaers is unbelievably effective to the point it almost makes us irrelevant。

I want to add one more point that whenever you do a cold review， you should always be thinking。

What tests can I add to this right？ and I have to say right that this really can have a big impact right like I sit there。

 I say。I can find new tests to add， right。 And 50% of the time when I've asked somebody to add more tests。

 it's caught a problem， right， They've realized they didn't do something， or they've caught a bug。

 and so。Always think about that。 How what more can I test here。

One thing that I would also like to add is code review isn't super formal。

 You don't have to go and add yourself as a reviewer， you don't have to worry like， oh。

 if I hit accept are they going to land this and it's terrible。

 Why are you landing it on my acceptance。 like it's fine。

 You don't have to add yourself as a reviewer， you can just pop into anything that looks of interest to you and provide comments and that's really beneficial because the more eyes we get on the patches。

 the less likely it is， we're going to introduce bugs that we're going to have to pay to go and fix later。

Yeah， one thing with that is that it's very important to get review fairly quickly。

 So I think more people doing review and be able to do review quickly is' very very important because if it's your first time contributing plan。

 You did to bad and you don't get， you don't hear anything from anyone from like three weeks。

 You are never coming back。 Yeah， and we are losing contributor because of that。

 right people do work and they don't get feedback on their work， They work never get mad。

 they don't come back it's a very bad experience。 So we are we are trying to do review as fast as we can。

 but we， we need more people doing that， right。😊，That I think that's something we are trying to improve。

 Otherwise， I think we saw talk yesterday that we are getting better。Yeah， we're getting better。

 but it's the volume of changes is going up over time。 and when the volume of new code is coming in。

 we'd also need to increase the volume of reviews and that's traditionally been a real bottleneck for the entire community is getting the code reviewer attention and so the more often you just step in and help out with reviews。

 the more it helps the community as a whole but the more it also teaches you about parts of the compiler that are of interest。

 So it's a really good way to introduce yourself to what's the architecture of the compiler how is it pieced together。

 what pieces and parts work together and code reviews， even if you don't say anything。

 even if you're just reading the code and looking at it。

 that's still beneficial for you and that will end up being beneficial for the community as a whole if you stick around。

😊，If you， if you didn't make a pi and you don't hear from from anyone for like a week。

 feel free to go on on Disc code the centers appearing on Github because we don't we。

 we are going to miss things。 Why like there was like a you appear。 And sometimes we miss things。

 we feel really bad about it。 But like， feel free to tell us。

 you didn't look at my peer for like a week what's happening。 And we， we try to look at it。 yes。😊。

I will also say if anyone has questions， feel free to come to the two mics in the center。

 we're going to keep seat conversation here， but happy to throw this mostly to the audience if folks want to be involved we have。

So I wanted to applaud the effort。 I think Klang was one of the first sub projects in El to add。

 was it like code owners or you know some like something that led to like the area Les kind of system。

 I think that was super helpful， Can you reflect on how that's gone has remained up today and have there been changes to that kind of thing as a new contributor。

 who do I ask for review know the clang I talk， they actually graph like contributors。

 contributions over time And you know you are all maintaining a whole lot of code where maybe someone else wrote that kind of thing。

 And so you know knowing do I CC them， Do I CC you。

 like who do I CC for any open source project is always a huge。

 huge question that new contributors have Yeah， thank you。

One of the challenges that we have is is our code reviews through Gitthub don't automatically add reviewers based on what files are being changed。

 and so it is a challenge sometimes to know。We do have a codeown's file。

 a maintainers's file that's at the root directory of the Klang Repo that tells you you for these areas of the compiler you should contact these folks that list is something that we keep up to date throughout the year basically try to encourage people if you want to step up and be a maintainer if you've got the experience to do so then great we list you and if you decide I don't have the time to maintain anymore that's fine we just delist you you can come and go as you would like to go and so it is the maintainer file is really the first place you should look for help for these sort of things。

One thing kind of bounce off of our last topic。If as you're looking through a review and you see that it's not getting enough attention。

 one of the things you can contribute with is figuring out reviewers for that person。

 A lot of the newbies don't know new contributors don't have a good idea on that。

As to get back to the original question， we did start with code owners， right。

 which was a little bit more formal and everybody had a single spot of ownership。

Which was a great improvement over what we had previously， which。

 you know was a little bit wild west。But what we found is that it was a little too much pressure on an individual basis。

 each individual code owner was having to do too much and feeling responsible for too much。

 so Aaron pushed for us to move toward the maintainers right which is a less formal。

 less unique the multiple maintainers can exist for every individual thing and in fact when we see people who are doing a lot of。

Code reviews and doing a lot of patches are active and knowledgeable in the area and you show themselves as responsible and you know。

 doing lots of code reviews and showing that they g what's going on there。

 we kind of pull them into the maintainers as well because having that amount of knowledge spread out along a number of people is both good for the community and good for us individually。

And I think what I've also tried to do is especially on issues。

 right if I know somebodys visit this area。 If I fail in the bugger report， I taggged them。

 I very often tag them。 So often you kind of need to lead by example。

 So when issues when you triage issues， you know， like one of the things I started doing what crashes right is like making sure stack traces are there。

 making sure assertions were there looking at this a regression。

 added now a project for tracking regressions and stuff like that。

 And so sometimes you kind of need to take initiative and when you do things and and you do them repeatedly。

 then people kind of learn， okay， well this is this is the way to kind of be responsible right And so when you see people being responsible right。

 you kind of know， these are people to kind of go to So yeah one thing I want to say that I think is kind of implicit that we haven't explicitly told you is you can't screw up。

You can try things and we're not gonna jump down your throat if something is not correct。

 whether it's code or a comment on a review。 as long as it's following the code of conduct and is done in good faith。

 we're gonna work with you to try and help you through these things。

 And so it's perfectly fine for you to just jump into an issue and try and figure it out。

 If you got it wrong。 Some will notice。 we'll correct it。 and we move on。 Yeah However。

 I feel doing a good job。 We happen to try to give you more responsibility。 You don't have to accept。

 but we always thank you find you Mon know new people to。😊。

Most people to work on Kang and Mon and Kang long term。

 so if you like willing to do the work we are going to give you work。

 we will reward you with more work。So I have a question this is kind of related to the comments you just made there。

 say I've put up a pull request and somebody， you know I added the maintainers as reviewers。

 somebody else comes in and gives me a review， if I'm satisfied， you know。

 I get the sense that that person did a thorough review and I've addressed their comments and it passed CI。

Is there a policy or a process where can I go ahead and just say， okay。

 I think this is good enough and merge？This is a little bit of one of those squishy comments， right。

 like when you're ready to click the merge button。You'd have to feel that the person did do a thorough review with a reasonable amount of knowledge。

 You'd probably want to give the the other reviewers a reasonable chance to review you know。

 it's unfortunate when。 you get a review 20 minutes after you submitted it。 Youre like， oh， great。

 And then you've submitted it you know， immediately after CI passes and others haven't really had that chance。

 but。We have in the project a fairly active and aggressive revert policy， which is another thing。

 by the way， if your new contributor is kind of jarring。

We revert pretty aggressively right if it breaks a buildbot or something that's just part of the process right like it's nothing against you。

 it's nothing against your patch other than maybe it broke a thing。

 but we revert often we would rather err on this project LBM at large on the side of having too much work done and too much work in rather than the overly conservative mechanism that other projects use。

So。If you're kind of on the fence and you feel like it's been well reviewed。

 but you're not sure the veracity of the review， you're probably okay to click go and deal with the fallout。

one thing you can do is if you're ever in question you're like somebody accepted this is that good enough。

 you can just say I'm going to land the patch tomorrow if anybody else has further comments。

 please bring him up and we do post review commit as well。

 post commitm review as well And so you know it's fine if things get in on someone's acceptance even if they're not a maintainer that's perfectly fine it's a judgment call though and that makes people who are newer contributors a little scared because they don't know theyll trust their own judgment yet。

 but it's fine you can either choose we' land it and see how it goes or you can poke a maintainer and just say hey。

 Id like another set of eyes on this it's perfectly reasonable to do that。

And that's also not a negative towards the person who did that initial review。

I have a lot of people like all except things， and people will come along and say。

 I have additional comments on things in Aaron and mist。 It happens。

 None of us are going to catch everything。One thing I will point out， though， I， know。

 I mentioned making sure I've had enough time for people， you know。

 for it to bake and for people to take a look。 Remember an Aaron's。Presentation the other day。

 I had the graph of when we do work。 Remember how Saturday and Sunday were like。

Sing single point lines and everything else was nice and wide。 Keep that in mind， right。

 Don't do like a Friday night and be like， well， you've had 48 hours。Give me a workday， maybe。Yeah。

 yeah， I personally， when I review something outside of my area， right。

 I will often explicitly tell the person， listen， I gave you an exception。

 but please wait for one of the maintainers in the area to kind of go over it first right because。

I'm just not。 It's not my area， right， Like if I review static analysis overview， I'm not。

 I'm not going to tell a person。 I'm going to say， listen， please let somebody else from that area。

 kind of just give a。look at it first when I do that I'll often just say give the other reviewers 48 hours。

 you know give them till Tuesday kind of thing to try and make that easier and maybe we as a group could be better better about that to make it easier for folks to judge。

On the flip side， if someone approved your PR。A week ago。

 and no one mailed it because you don't have mail right。 Please let us know。

 because we have like to of P L that got approved and review。 and theyre like ready to learn。

 And then sit on guitar because nobody noticed that someone should press the mail button， so。😊。

Tell us when you peer is ready tell someone and we'll make it for you。 Yes。

 We should probably get ourselves a but that Yeah does something like that， yeah。😊，But I mean。

 I think more to the point that everybody's kind of basically dancing around。

 which is it's all about communication， so if you're at all confused about anything。

 just communicate， you can't over communicate really。Hi。

 I tried to submit clamA patches before and I discovered that plan is such a big project and I personally would like to develop some expertise on ideally like all of them。

 but due to bandwidth reasons， maybe I can only develop one of them be what would be in the area in Klan that is where new contributors to start developing expertise and that currently isn't seeing much care or that's a good extra caveat there so Aaron was talking about this DRs defect reports if you feel comfortable enough with standard language right you can look at defect reports and understand enough of it。

We really are behind in verifying C plus defect reports。 So that is a perfect area。 I mean。

 there must be other areas， but I just remember you talked about this yesterday and。Yeah。

 I think at a lot of times， it depends on what's of interest to you。 So if you're like。

 I really am excited about constant expressions， then we can find ways like there's。😊。

There's so much work to be done at a production compiler。

 we can find something in pretty much any area you're interested in for things for you to do in it。

And so you can also ask these sort of things on discord， for example。

 or in office hours and just say， know， here's the thing I'm interested in。

 can you help me find a place for it？And speaking of constant expressions。

 the new constant Bcode interpreter is kind of been on the back of one very， very awesome guy， Tim。

 who I don't think made it this week。He could use help and that's an area that would。

TheThe faster we can move to the new bit code interpreter for Cont experter。

 particularly now that we have reflection coming。 The faster our compiler is gonna to be the better our user experience。

 That's going to be， you know， a big highlight in when that when that gets released。

 it's going to be the biggest thing that's happened to clang in in releases。 So I would。😊。

Anything you could do to help him accelerate that， he's also very active on discord。

So you can ask him what he needs help with。And how you could help， but。

And and that a lot of the times is fairly general， right， like his bit code is interesting。

 but it's really well documented， so it it's a little。

bit of a reading into it to figure out how it works。But it's sort of a general C plus plus knowledge。

 You don't have to know the nity gritty of the internals of the compiler。

 you just have to know know small sections at a time。 It's a really good place to start。

 He started with kind of very little compiler knowledge and has done an amazing job so far。

 but we need more work on that。We also have a lot of bug parts。

We have a lot of bug reports and some of them are not hard fixes right we often put good first issues they kind of get grabbed rather quickly。

 but not always right so I mean， if you want to kind of dive in you know I mean you know sometimes I try to when I have a chance to kind of put a little bit of analysis in there right' maybe sometimes I'm off but I do try so bugger reports is also a place to kind of look for good places to contribute sometimes Yeah we have a label specifically good first issue that you can search for on Github and it will give you the list of things that somebody has thought might be a good first issue and as Jafi said we usually try to like。

Explain， we think it's a good first issue because you should go here and change this and then make sure to write this test。

Kind of thing。So we you you are mentioningque shoes， I think in C press， we may might have 3000。

2000 openque shoes。 And if you， if you look at them， right。

 they are like curry shoes for the prepocessor， Leing， cooteine。

And each category has like hundreds of courages， so you can pick whatever category you like。😊。

And what on that just fighting tests。 Most of them not the implemented。

 And we just don't know about it。 So just fighting tests and commit that was our we might have to debu a bit。

 Yeah， yeah， you might be noticing a theme of we need help with tests。 We need help with tests。

 We need help with tests。 that that is something that always helps if you're interested in getting started you don't even feel comfortable touching the compiler just looking through the test directory and noticing。

 you know， I don't see a lot of tests around this attribute。 Great， write those tests you。

 put up a patch for that。 It's a really good way to help out and learn and different from。😊。

QA on normal projects， normal programming projects， this is actually programming you're doing。

 right that this is writing examples and stress tests of the language itself on the compiler。And。

 you know， you do need a good understanding of the language itself。 But yeah， new more code coverage。

 one of the。Weaknesses to how Kang was started is it was very undertested initially。

 and we have been better since， but not great since。

That that amount of coverage as particularly for older features， a lot of the times， like they said。

 for the C plus plus language and C language defect reports are things where a lot of them work right and a lot of them are already implemented。

 but we have no idea because nobody's had the time to write the test Aaron showed we have what not even 50% that we know whether it's been done or not。

 So defect reports are a fantastic spot to improve。The compiler a whole bunch at once。

 even if it doesn't change the compiler itself。And I think you said that sorry but also。

 documentation is always something that we need。 Yes。

 it's really hard to find good technical documentation， technical writer。 So if you are good with。😊。

English， you can submit documentation and that guy used。Yeah， to the document。

 like just to help you try and find things as a good example， we have a file called Adderdox。

td that has got all of the documentation for all of our attributes。

We have a whole bunch that are just listed as undocumented。

 and so you could literally just look in a file for undocumented and go oh。

 I know something about the cleanup attribute or I know something about Goodoo mode or whatever it happens to be and write those docs because users will appreciate it very。

 very much。Maintainers will also appreciate you。Yeah， I think this has now already been touched on。

 but I was going to come back to the point Sch made was about verifying defect reports。

 It's not just about writing the code to fix the defect report。 in many cases， they're already。

Functional， but we need tests。 I we need someone who have actually S down。And said， this is good。

 I'll show a。 Oh， no， we have a question。 Let's do this。

So it looks like many of the bigger features end up being implemented in a fork first and getting upstreamed later on。

 And I was wondering what is your perspective on that is this abago feature。So。

As a production compiler， we have to be very careful about what we produce and what we release。

 because once we've released it， people will use it， and then we have to maintain it forever。And so。

 if it's an experiment。If it's a small experiment， sometimes that's fine to do inside of the compiler。

 but if it's a feature like say contracts from C++。

 that's an expansive feature that you really want to explore the whole design space and not feel locked into just because of a release schedule and so I think it's a feature to do a lot of that work in a fork。

The the downside to that is is we don't want a large code dump of here's 100。

000 lines and now you have contracts because we can't review that。

 And so when you do that work at a fork， you do have to realize that bringing it upstream basically means redoing it。

But as we heard during the keynote yesterday， that's a benefit， not a cost that a。

 it spreads the knowledge around to more people， which is something we really need because there is a bus factor problem where we don't want one person to be the only one to know something about a critical component。

But it also is going to be just very beneficial to help no， I'll let you go with this one actually。

Sorry， yeah。We find that the process for going from a fork to an upstream。Has two huge benefits。

 right， One is that the person who originally wrote it has already learned everything that they were going to learn in their fork。

When you try and implement something fresh。嗯。In the compiler， under an experimental flag。

You don't know what you don't know yet right so having you come in and explain to the reviewers。

 I'm doing this and I need to because of all of this versus having to go back and fix things up that you've messed up and like Aaron said。

 that you might be locked into because we've done a release in the meantime so we find that very effective we've done it with KangiR。

 which I think is probably the best success story of massive project upstreaming so far。

We are learning。A lot about it， we are revving it， changing the implementation as it's being upstreamed because we are learning this and seeing new perspectives and。

I think we've all seen a project right where you get to the very end and you put a bow on it and you're ready to release it and you go。

 I wish I had done this different on day two， right and。When you're doing upstreaming。

 you get to do day two the second time， so you get to fix all of those as you come back and we've seen that that has improved code quality a bunch and hopefully it will show a much more production ready product much sooner than otherwise。

Yeah， I mean， it's， it's， it's a challenge because so when you go to the Sea of C process Committee。

 they want an implementation most of the time， right， Like。

 we prefer having an implementation before putting something in standard。

 But from the compiler perspective， we don't want to put something things that the committee might change。

Before I don out die， right， So there are like a chicken and aquam that is very up to third。

 And I think I think refer is。There's somewhat reasonableable solution to that。

Most of this prototype implementation of like and reflection。 They are exactly that。 I prototype。

 The goal is to show that we can implement it。 We know it can work。

 but usually they are like not meant to be production already， right， the probability。😊，Like it's。

 it's 90% of the way there， but it's nowhere anywhere to to be able to put in a production competitor。

 And so I think that's slow up process。The letters having a good quality of implementation of strain。

 which ultimately it's what better。And I think every company that has been doing prototype is very happy to have that circumstence。

 Thats a opportunity to get things， right， And having more people look at it， right。

 Because when there is like a prototype of contact or reflection， it's usually one person。

 And so they don't they do what they can， right， But having more people look at it is always beneficial。

😊，Great yeah， concretely， for example， we had reflection。

There was a prototype implementation of reflection that was happening in December of last year。

 having that prototype meant that people got to play with it。

 And now the reflection that's actually going into C++ 26 is significantly different than what we had from that original prototype because we were learning from it。

 And so that's where the benefit of these forks a lot of times comes in is it gives you the chance to experiment。

And really figure out the correct shape of the feature before you're locked into it。Classic。

 throw the first one away kind of situation。 Y， let's， let's do something interesting。

 So Klang has grown and gotten a lot more different facets from Windows support to kuda to everything else。

 And all of these have their own extensions and。😊，Hrac recall。Ear in the days。

 John McCall or maybe Doug wrote the like。Extensions。Bar for climbing Elium。

 which I think is still roughly the same as what was written 10 plus years ago。

How are folks feeling about the extension ecosystem that exists within and without。Cang。So。

Extensions are actually what make the programming language useful。

 And it's weird to think about that because you think well， surely C++ is useful on its own。

 But when you go and you dig into like system headers and everything else。

 it's a pile of extensions that makes it work。And so extensions really are a benefit to the compiler。

 but they're also a major cost because every time we add a new extension。

 you have to figure out how does that interact with all of the standards features and how does that interact with every other extension the compiler has and so its I think our bar is set pretty well currently。

 but it it's difficult because as。As we've been doing this for 10 plus years。

 we've accrued a whole lot of extensions， and this can actually be hard on the standards Committee side of things。

 because some of our extensions will conflict with what the Standards Committee wants to do。

 And so we just have to be careful with our extensions and make really sure that they're worth the cost of implementing them。

 But also worth the cost of taking that design space away。😊。

I think we do a fairly solid job of deciding when things should go in。

The one area I wish we were better at was the other side is when they should come out。

Extensions live in clang for a very， very long time。Despite never being used。

 I'll tell a story because this is。We're all familiar with precompiled headers before my time on Kang。

 there was this feature Pretokenized headers， which was in the compiler and I came across it because there was a bug and it was actually slowing down our parsing a whole bunch。

And I started looking around trying to find someone who had used it， and I found one use in the wild。

 and it was in boost， and they were using it because they misspelled precompiled headers。

ThatThey had this big if El tree in their make file that was always doing do precompiled headers buy everything。

 except they did PTH instead of PCH inc for some reason。And so I changed that in boost and。

And removed that， but it was one of those features that hadn't been touched or thought about when I hit it in 10。

 15 years， since early in the project。And I think what we don't do well is go back and revisit our extensions decisions and say this was an extension。

 It was a great experiment， but its time is over， and I think the compilers full of them and we occasionally go back when they caused problems We had one recently with that affected the module sizes an optimization that actually improved sizes but was a maintenance headache and we didn't have anybody around to maintain it anymore we removed that because it was a headache I think we need to be more aggressive at deciding。

What that headache level is before we remove stuff。I'm going to make the argument。 So， I mean。

 both Aaron and Eric made really great points。 I'm going to make the argument that actually we。

 we should be doing more extensions。 I feel like。Being part of the standardization process， right。

 the standardization process。Works well in some cases， but it can be slow， right。

 And I feel like as implementations， we can do a better job of being。Iterating over features。

 especially let's say around safety and extensions and then going back to the committee and saying。

 hey， listen， we did this， this't work well， this didn't work well right and I feel like that some things just are harder in a committee because there's nobody there who's done it。

 people have great ideas but。Nobody's actually implemented the space so I feel like we actually can do more in the extension space。

 but I mean there's a chicken egg there right， I mean we need people to actually put the time into it。

 but I'm going to argue that actually。We have more。 I feel like extensions allows us to do more。

 right， And I think that if we， we did more， right。

 we could feed that into the standardization process。

 I think we could push it better into the right direction。

 Sometimes I feel like sometimes the process can go all over the place。

 And that's because we don't have strong signal about what。Actually works， right。

 We just have lots of ideas and well， well， we can do this， we could do this。 Okay， yeah， sure。

 but has anybody actually done it。Right， and that I think is something that， yeah。

 the danger with that is there's a tension。Because we do the extension and we're the early adopters of it and we're the ones learning and the standards committees always want to go。

 oh but we don't want those bad things， we want the good stuff that you learned from and then we want to take the bad stuff away and so they change the features。

And that's where it becomes difficult with extensions because we want to help the standards committees。

 but we also have to support our users because those are the people that pay the bills。

And so we have to be very careful about the extensions we're adding。 So as an example。

 adding a new attribute， ones it is an extension， but no one's gonna go， oh， wow。

 that's a big maintenance burden。 we're gonna be locked into that attribute forever。

 that usually isn't a problem。 But if it's an extension like reflection。

 I think that's a much bigger surface area。 and there's much more risk that the standards committee is going change it in ways that are difficult for us to respond to。

 But I take your point。 we should be working more hand in hand with the committees on the design of the features that go into the standard。

 and that often starts as an extension。 I think about doing be drugs we did 20 ago not choosing sametctic space。

 So Kang to be likes that something it's going to be just something It used be 20 years ago that would use like tokens that pay that could be very cheap by could be a company。

😊，Like b， for examples， that complete effect。We， we used to do that。

 We don't do that now because we know that like the committee are going to invent future of Go there。

 right。 So we are like more conservative with that sort of。 What I found is that going when。

 one of the。Limits of external trend are usually they are designed to work in。

To to serve a specifics problem in a specific scenario。 And so they don't work in the general case。

 And so going to the committee is useful because someone is going to say， okay。

 how does your extension work with template in a context And then we realize that we。

 we don't have themselves with this question， right？

 And so it's useful to both the committee and implementation work together to make sure the extension become something that we can use anywhere。

 right。😊，Sure， maybe a brainstorming question with the move to GitHub。

 people are adding all kinds of slick kind of automation and automations to the code review process and things like that。

 other language frontends to LOVM， also have some really slick integration， brainstorming question。

 you know， if you had the resources to help you automate certain tasks。

 what kind of automation could we be building to be improving the contribution pipeline。

Well that's a good question，So。One thing that would be helpful is during the code review process。

 there's kind of a checklist of things that we have to go through as reviewers。

 and a lot of that feels automatable to me like， does this actually meet the coding standard kind of stuff。

 And we added clang format to our CI pipeline to help people go， oh， this is not formatted properly。

 There are other things that I think we could do like I noticed you've added these four new diagnostics。

 but I don't see any tests that have that diagnostic text in it。 Or you've added a new feature。

 There's no documentation for it， And so I think we could add some more of those kinds of things to really help catch stuff that us as reviewers miss continually。

 but are just mostly checklist kind of items。😊，One thing that takes a lot of time。

 and I don't know if we could automate it， when is trying to do B。

And the one is trying to do head churn。And if you have time to do that actually。

 something you could also failqui is doing reduction to find like a minimal test case for like5 or something。

😊，If there was a way to automate。So we have to do addiction， for example。

 that would be incredibly useful， very， very very useful。 But one thing I would love。

Kind of on the same topic is for us to somebody to come up with a。

The suite of tests for all the bugs we have we haven't fixed。We get Shafiq can tell me better。

 a billion。Bug reports per day， it feels like。Yeah， so it's something like an expha test。

 but an automated IH system that when a bug is submitted。

 it's reduced and it's put somewhere that we know when we fixed it。I。

Have occasionally looked for you know， bugs on a topic and tried to figure stuff out and then gone and realized that we had closed the mall with something unrelatedated。

 It would have been awesome to have been alerted to that along the way， or。😊。

When someone commits puts a review up that those get run and we as reviewers get told。

 did you know this also fixes this because of how often I didn't realize when reviewing one thing that it touches something else it's really easy to get。

Over concentrated and over focusedcus on the one problem they're solving。

 not realize it's a little more generic and things getting fixed along the way with that or changed along the way with that would be really helpful。

I think it's a little more than just Xhals， but it's the whole automation process to PR with multiple fixes Yeah yeah。

 and it comes up and it just gives you the list of fixes that it somehow managed to do。

 and then I can check and make sure that those are right and make sure it covers those right and I think that that would vastly improve a lot of our processes So this is not PRs but I think we could do some better automation on our issues bug reports。

 especially with crash bugg reports So he's talking about about reductions and bisecting right but also just automated generation of fact traces assertions finding duplicates that would be awesome right because very often the bug has been sometimes it's not right but I mean。

I spend a lot of my time just just doing it。 I mean。

 people have gotten better actually because I do it all the time and people have actually the regulars have learned。

 okay， I need to do a stack trace。 I need to add the assertion。

 I need to by figuring out if it's a regression， doing all these things。

 these things should be run easily automatable right， I mean。

 and they seem like pretty big wins because then a lot of these bugs will just be。Right。

 so I mean this isn't necessarily automation。 but if I could wave a magic wand to get something that would be really beneficial to the cllang community。

 one thing that comes up as related to extensions is is this gonna break code what are what's the fallout from this change going to be And so if I could wave a magic wand。

 I would love if there was some very easy way for downstream consumers of clang to try out patches to see that it's going to impact them before we land because after we landed it。

 it's expensive and it's frustrating because you have reverts and it's just not as clean And so it'd be really handy to be like I ran this through all of Intel's 30000 test cases or whatever and these are the ones that broke just having the conversation with somebody at lunch it's just a bad experience for everybody right it's a bad experience for the person who wrote the PR because they they're just trying to fix something or something and it's bad。

😊，Berms for the people it broke right and it just sucks and nobody did anything wrong just you know it just just。

It's just a bad experience I would love a large conformance type test suite of just。

A trillion open source projects that I could all just make run when I was unsure。

 I've done a couple of the template patches over time that I've had pushed in， reverted， pushed in。

 reverted because first it breaks Lib C+ plus which I didn't really have an easy way to test back then。

 which Louis you in his defense came along and like fixed all that for us because that was back in the fab days。

But then like oh， it broke chromium， and then I fixed that and then I broke this。

 and I had to revert and I fixed that， right？And it was years of cycles on a couple of these of people finding。

 oh， did you know you broke my little edge case and me having to go back。

 that it would have been wonderful if it had run a ton of them all at once and not for every pull request。

 not for everything， just the ones that we know are high risk and we want to see how they are。

 we definitely accept patches that are this might break a bunch of people。

 But the only way to find out is to press go。 And so we do and having a way to not have to press go。

😊，Unless without more assurance， I think we go a long way because we don't have any automation for issues today。

 we rely very heavily on compile ice bloodla he did the work to put every clangception since like 2。

7，2。7 with a on Comp ice， and I don't think we could even like pay issue with compile ice so。

If Matt is watching this Thank you， but yeah so it's computer exploring the only tool that we have to try to find if factor theberg is a regression or something。

 And if we could have a way that' more automated than that， it would be very useful。😊。

We even call this out in our release notes because you'll notice at the top of the clang release notes。

 we have potentially breaking changes because we don't even know who it's going to break。

 So this is something that has been kind of a long standinging issue and the reason why it matters so much is。

😊，Anytime it's difficult for a user to upgrade from clang version N to clang version n plus1。

 That's really a bad situation for us to be in because we're at risk of losing them as a user。

 They may just decide that's the last clang I'm going to use And from the C plus plus perspective。

 it's also bad because it means that it slows down their adoption of later features right， And so。

 I mean， it's bad in offfront， right。H， yeah， sort of related to what you guys were talking about with the some of the issue automation stuff。

 I wonder if there's not some common language that you could put the burden on the issuer。

To describe how to reproduce the problem， I'm thinking like a sea vice interestingness test。

Like give me some common language and then my bot can run your thing。

And then put a fixes tag on it when it does solve。 But I guess the balance is not pushing away people who are trying to issue bugs and。

Too much work。The expertise level of the people filing issues is all over the map。

 but I Shafiq Rabbi has more data about this。I feel like most of the people who interact with a compiler project are usually on the upper end of the skill level usually not the lower the recent college grads that are doing it。

 so we might be able to raise the bar on it a bit and then it seems like with a lot of these。

The expression you use magicic wand， sort of dancing around the LLM land。Any you。

Any thoughts on having the LOM look at your tests or consider all permutations of your diagnostic rather than some rule based approach。

 I think we've had bad experience so far。 Yeah they're not。 This is a very expert area。

 and I think our experience so far has been rather negative。

 Yeah we have had issues that have been just hallucinated flags， for example， and so its it's。

It's hit or miss， but I do think there could be potential as LLMs improve over time， maybe not today。

 but maybe five years from now or whatever， as things have improved。

 we might find more ways in which to help with these sort of automating these sort of tasks。

 with the current technology I don't know how much I would trust it and then a lot to unpack that you guys are talking about。

 but with the testing or evaluating downstream users for a particular PR。

 This is something that like new of them does with nightly releases where they auto merge every PR that passes tests and they put into a nightly release and then they hash the thing and then downstream users can choose to。

Run their tests against these nightly latest or whatever。

And then it gets reported back up somehow saying your PR breaks someone who uses this。We。

We actually are better than nightly， I think we're just harder to find。Harder to get to them。

 All of our build bots run every couple of patches and have their artifacts available。

 but we don't do a good job of publishing it。 nor encouraging our users to。Yeah， to play with them。

 and maybe that's because it's drinking from a fire hose because it's 30 a day。

Probably more than that on some of the bots。Yeah， and I mean。

 the usual advice is for our downstreams is to live at head and so a lot of times we'll get notifications about breakages like a half hour an hour after we've landed it from some company that said。

 we've pulled this down and this has caused these problems within our， you know。

 and that's fantastic feedback for us。But but。It would be。

 I think what would worry me about auto merging stuff is。You really have to trust the compiler。

 And if we're auto merg things that just happen to pass our test suite。

 we're relying super heavily on a test suite that we know is deficient in the number of tests it has。

 and that's what worries me。 So if we had much better testing。

 then maybe that would be more viable but I don't know what would qualify as better testing enough to be comfortable with that。

😊，Yeah， but it gets back to like writing test is useful because the test we have the Mohuto machine we can do。

 So that's sort of a benefit of writing test software issues and stuff like that。Yeah。

 speaking of tests， this is just something that I think a lot of folks in the community aren't quite aware of。

 but we actually have multiple test suites。So we have the tests that live with Kang in the clang test directory。

 but we also have LLVM test suite as a completely separate repository for tests that don't have licenses which are compatible with our own。

 So， for example， we're not compatible with a GPL， but we have GPL code in LLVM test suite because we have the Gcc torture test suite in there。

 And so if you have code where you're like， I don't think this would be appropriate。

 it'll take too long to run the tests and it might cause CI problems like if you have things like that。

 we actually do have other buckets you can put that test into so we still get the benefit out of it because we do have bots that run LLVM test suite。

 they just don't do it on every single patch。There is one other issue with the auto meing of patches。

 it is super easy to make malicious code that passes all tests yep you don't want that compile compiler。

I'm just going to throw it aside on the question of like if I had a magic wand。Mutation testing。

 Sure， like I don't want to have to go and think， did you test all your code pods。

 A robot can do that for me。 Yep， I would like a robot to do that。

 so we do have a fair number of people fuzzing。Declying front end right and it's been a struggle because we've had to kind of work with them and educate them about what the bar is for quality bug reports。

 right And I think it has gotten actually a lot better So the people who are regularly doing it。

 I think they kind of got， okay， this is the bar。 and this is what we expect。

 and I'm gonna be honest， they actually like the stuff that's going on today。

 they actually catch a lot of recent regressions。 So so you know and we actually are doing a pretty decent job of fixing regressions on a timely manner。

 So they are useful right And so I mean， more the problem is just。

We already have more bugs than we could fix。 That's why would mutation testing on。

 on the proposed patch。 right， Like frame me the bugs just in this patch because sure。

 there's a huge legacy。 Yeah， even as less than that code coverage。😊，Yeah。

 that would be the bar below I'm pretty sure we actually have a code coverage thing somewhere have one that's not been updated in a while and can it tie into the patch again。

 like getting code coverage for the whole project and all the tests is one thing。

 but if you can tell me that this patch doesn't cover its own code exactly I'd be super covers itself makes sure it improves code coverage。

 all those heistics that we all used in the late 2000s when code coverage was a huge thing。

 I'd love to have that。😊，For users watching on this recording on YouTube in the future。

 what video would you recommend they watch next to learn more about this topic？

I kaleidoscope as a tutorial， you know where else can we what do you have videos that you recommend or a talk someone's given about the architecture of Kang or how to get started。

 something you'd I'm unar of a video but our internal reference and this goes back to documentation we have our internals reference documentation where anytime someone has acquired。

A certain level of knowledge of a section of our internals。

 we kind of try and convince them to write us some documentation。嗯。Sorry。

 I forgot your name in the yellow earlier you asked a question where you could help。

Learn a spot of the compiler that is not listed in the internals reference and write me one。

Help the next guy around those， we we have some really good ones。

 we do not have enough of the compiler covered， the more of it that's covered。

 I think the better we're going to be and you know。You don't have to be perfect either on those。

 get me to like 75%， we'll fix it in review， but we would love to see that part of our documentation improved。

 even for our own reference， I go back to that all the time to reteach myself the stuff I forgot last week。

Yeah， that I'm not aware of videos that are really necessarily explaining the architecture of clang as a whole。

 but the internals manual is where we tell folks to go when they get started and playingang。

 we do have a getting started page， but it mostly is telling you go look at the internals manual because that's telling you how the compiler is constructed。

 What are the pieces and parts and the major components。

We have some doxgen documentation also somewhere you can find on the client websites y and we try Tra。

Extensive do documentation。So it's also not be perfect and also Paty is welcome to improve that。

 but we have something。Probably last one。Related to that。

 maybe some LVM sponsored clang internals video， I think how Google has some great Tensorflow videos on public YouTube。

If you want to learn the internals of Tensorflowlow。

 it's like five minutes long and it's very brief but just to get newcomers into the project。

 we love short form content the kids into these days is the video content it's a really good idea。

I mean， it's an interesting idea ins so much as anybody who's got kind of a maintainer level of experience could really put together a five minute video on what they maintain and even if we did that and just stuck it up on the LLVM blog and YouTube that would be beneficial but the downside to it is is the project moves so quickly that that information becomes stale really。

 really quickly high level want to start with we should discuss that let's do that maybe we can。

Speaking of videos， I actually watched one of those Anastasia's past videos in LV and Dev meeting。

 It was from a couple of years ago， but I think the information is still more or less。Relevant。

Although not up to date， maybe sure all the。Yeah。So we've got about two minutes left。

 One thing that I'm wondering is。Are there things that you would like to see the Klang community doing that we're not doing。

 like are there things that are preventing you from contributing to Klang that we can help remove those barriers for you？

Just as a sort of thing to think about， if you have anything where you're like， boy。

 if the community could do X， then I could convince my management to let me work on this project。

 feel free to contact me because I will happily try to build a case to get you to come to work and playingang any day of the week so except Saturday Sunday Well yeah those two we don't really work。

哎。Well thank you everybody， We really appreciate you guys coming to hang out with us for this hour and we hope。

You learned something and we really appreciate all the questions。

Like Barren said we hope you come back and talk to us and ask us questions and tell us how we can improve your lives Yeah feel free to come grab us right after the talk too Yep absolutely Thank you Thank you。

