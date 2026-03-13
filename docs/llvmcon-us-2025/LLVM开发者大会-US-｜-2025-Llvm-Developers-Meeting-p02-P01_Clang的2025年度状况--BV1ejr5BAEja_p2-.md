# LLVM开发者大会-US-｜-2025-Llvm-Developers-Meeting-p02-P01_Clang的2025年度状况--BV1ejr5BAEja_p2-

![](img/bf75cd350857cefc068d245cffc26020_0.png)

Welcome， everybody。 My name is Aaron Balman， and I'm going to give a little bit of an update on what's going on with Kang and the Klang community since the last time I gave this talk。

 which was October of 2024。 So this is basically what's been going on over the past year。

 And I would like to give a big thank you to Vlad Ser Bnikov for his assistance with gathering a lot of the data that I have in this talk。

 I like graphs。 You'll find that out。😊，So dive them right in。

 what kind of things have we been working on on the C side of things is we've largely been working on C23 and C2Y support。

 so in Kang 20 we improved enumeration support， so now you can have the C23 feature allowing fixed underlying types like they had in C++。

as well as enumerations that are typed long， long as opposed to have typed int。

 which is an extension that everybody has supported for decades。😊，In KAG 21。

 we worked on some of the C2I features like count of which allows you to determine what the extent of an array is。

 we also added another C++ feature for octtoiterals where you have00 to prefix them like you used to have for 0 x and 0 B and that sort of thing。

And another one of the Kang 21 features that we worked on。Was improved tag compatibility。

 This one's a little bit of an oddity And C your structure types。

 We don't have a one definition rule like C plus plus does。 Instead。

 it's based off of type compatibility。 And so the committee decided if you have two types that are compatible across translation units。

 Sure they should also be compatible within the same translation unit。

 which means you could actually redefine structures in the same translation unit。

 as long as all of the members are the same， the alignments the same and that sort of stuff。😊。

This turned out to be a little bit of a bug factory。

 I expect there's going to be a long tail of bugs on this one that we're going to be fixing for years to come。

 but it does mean that you can actually make better use of anonymous structures in your code。

 which is really interesting。😊，And in Kang 22， we've been continuing on， we worked on named loops。

 which allows you to break from multiple nested loops。

 you could break to a label or you can continue to a label to make it more easy to determine what the control flow is。

And one of the other things in K 22 that we're working on is the defer technical specification。

 So this is not actually a published T S yet。 It's in the process of going through the publication process。

 but there's so much user interest in this feature because it basically brings to you the same kind of things that you had in C++ with our AII。

 This is more of a C feature of this where it doesn't have constructors and destructors instead。

 you're basically saying I'd like to defer execution of this until the end of the scope。😊。

And then across all of the different clang releases。

The C committee has been working on this series of papers called Earththly Demons Papers。Basically。

 there's undefined behavior that is made sense 40 years ago， but it doesn't make sense anymore today。

 nobody's used it as an extension point， it just didn't pan out。

 and so the C committee has basically been turning those things into constraint violations。

So you get a diagnostic for it。 And so across all of Kang 2021 and 22。

 that's one of the things we' were doing is removing those undefined behaviors。

So in terms of where we are with completeness for C。

 the pie charts are showing you the data as of 2025。

 the text is telling you what the data was in 2024 when I pulled it so we can kind of see how we've been progressing C 99 is exactly the same weve done nothing with it for the last year。

 not too much of a surprise on the C 11 side of things we took that 21% unknowns and got rid of all of them。

 so now we know that we are 82% of the way done with C 11。C23， similarly。

 we improved from 76% complete to 79% complete， that was mostly turning those into yeses。

And then C 2 Y， this one's a bit。 Take it with a grain of salt。 C 2 Y isn't finalized。

 So what it was in 2024 is very different than what it is in 2025。

 but we have been continuing to progress it。 And as of now。

 we're currently about 81% of the way done with C 2 Y。So on the C++ side of things。

 we've also been doing plenty of work there in Kang 20。

 we worked on C++ 23's range lifetime extension and rangebased for loops。

 This is a really nice feature feature in that it removes an undefined behavior that was really easy for people to run into with references。

 And so this just removes an entire class of failure modes， which is great。

 We've also been working on our constant expression support。

 So we added unknown pointers and references for cont as well as contx replacement new。😊。

And then we also have been working on C++ 26 with its very addict friend and support in Kang 20。

 and in Kang 21， we've continued the C++ 26 trend， we worked on structured bindings and PACs。

 we worked on structured bindings and conditions like in if statements。

And then we also implemented the trivial relocatability traits for the Lib C+ plus side of things This one is a little bit in flux。

 there's a C+ plus meeting happening next week and they're going to be going through National body comment review on things and there are comments about trivial relocatability。

 we implemented what the paper currently says， but if things change in the committee we'll go ahead and figure out what to do with it from there。

😊，In Kang 22， we've largely been doing bug fixing as is probably no surprise to anybody here。

 C++ is an incredibly complicated language to support。

 And so this is kind of a chance for us to take a little breather and try and fix up a bunch of bugs。

 It's not that we're not working on newer features or things like that。

 It's mostly just that this is the way it's shaken out。

 The two big things that I expect us see us working on for Kang 22 though。

 from C++ as contracts and reflection。 And again， these are going to be discussed at next week。

 C++ meetings。 So things might change。 But the good news is here is we have two different forks that have the experimental versions of these。

 And there are people from those forks that are working on bringing those upstream。

 So it's not going to be a big code dump they're going to have to do the same thing that like CR folks did with regards to bringing it in piecemeal。

😊，But we do have plans for supporting contracts and reflection。

 There is almost no chance those will be done for Kang 22。

 just so we're clear these are multi year efforts。 These are big projects。

So in terms of our C++ conformance， again， pie charts are showing you what's going on right now。

 Tex is telling you what's going on in 2024。So on the C++ 20。

 we went from 92% complete to 95% complete。 This was largely due to folks working on C++ 20 modules that's basically the only thing we have left for completing C++ 20。

And C++ 23 support improved a little bit from 89% to 91%。And then C plus plus 26。

 just like with C 2 Y， it's a moving target。 It didn't become feature complete until fairly recently。

 So the fact that we were 83% complete before and 58% complete。

 that's just because more features have been added and they've been larger features。

So it is something we are actively working on。So switching gears a little bit into defect reports。

 So these are basically bugs in the standard， and I don't have the pretty pie charts from 2024 for this。

 but I did spot check the data， and we're basically exactly the same in 2025 as we were in 2024 on the sea side of things。

 We are 50% complete of implementing our defect reports。

 We have about 9% that we don't know whether we do or don't implement the defect report。

And on the C plus plus side of things， we've got 21% complete for the for being done with the defect reports。

 but 54% is unknown。 And so there is a lot of unknowns that we really need some assistance getting testing test cases is written for to figure out whether we do or don't support the defect reports。

 And this is actually really critical for us to do because the standards committees assume we have all implemented every single defect report。

 So every new feature they add assumes every defect report has been fixed in every implementation。

The good news here on the takeaway is if you look at the nose， it's 2% for C and 2% for C plus plus。

 So there's not a whole lot of things where we've just said， no， we haven't done this。

 and we don't expect to。😊，So。This is kind of our trend line as to how we've been doing with fixing defect reports。

 And you'll notice Kang 18，19 and 20。 we were doing really good。

 That was trending in exactly the right direction we wanted to see。 Kang 21， it dropped off。

 And as of Kang 22， we haven't fixed a single defect report。

 So it's starting to look like in the future， we're going to be adding to defects as opposed to actually fixing any of them because that trend line is starting to go negative。

😊，We could really use help with regards to working on defect reports。

 It's not the most glamorous of things to work on。 sometimes really frustrating。

 but it's really important work。So now a little bit about our community。

I thought this was kind of interesting。 I wanted to know when do we do our work。

 So the bottom is Monday， and then it goes Monday， Tuesday。

 Wednesday all the way up through Saturday and Sunday on the very top。😊。

And one thing you'll notice on here is there's a dip somewhere。

 Can anybody guess where Christmas happened in 2024？Right around month 18。

 These are four week blocks， not actual months。 but 2023 is actually on here as well。

 It's right around week 4。 And that's where there's a little dip going on there。

 And I thought it was really interesting that there was such a stark difference between the two。

 So I dug into the data a little bit。 And it looks like in 2023。

 we basically just did business as usual through most of December and people took off kind of the week of Christmas。

 And in 2024， it seems that people just took all of December off。 which is really interesting。😊。

But another thing that's kind of interesting about this is if you look at the weekend work。

 we don't do much on the weekends。 We're a Monday through Friday kind of community。

 which is probably not much of a surprise to folks。 But the weekend work is increasing over time。

 So the left hand side of the graph is all narrower bands。 the right hand side of the graph。

 So we are starting to pick up steam basically across the board。😊，We now have a dashboard。

 by the way， to help track this kind of data。 there was an announcement on discourse last week for a dash Grfaa dashboard showing this sort of data。

 So if you're interested in these things， we're starting to gather this more and have it more publicly available。

So in terms of how long does it take to get polar requests closed。

 This is both merging pull requests， as well as just closing them because we've decided we're abandoning that work。

 Most of it ends up being merges。But the top graph is showing us under a week versus over a week in terms of how long the PR stays open for。

 and the bottom graph is the same data just showing it one day versus more than one day。

And really nice thing to notice about this is on the over a week line on that top graph。

 that trend line is going down， which is great。 We want to see people being able to have good velocity on getting their merge their PRs merged。

😊，But I am a little bit concerned about how rapidly the one day is rising。

 It's impossible to say exactly why that's happening。

 It could be because we're doing more for supply chain security。

 And so people are pushing up more trivial patches。It could be that we're doing more。

Reviewing of one another's work and not doing a very good job of it。 It could be more self accepts。

 So this could be a demonstration of poor code review practice。

 but we don't have enough data or insight to know exactly why it is。

 It's mostly just something that we should pay attention to as we're gathering this sort of data。

But the nice thing is， is the trend is really for closing stuff is going in the right direction。

 We seem to close most stuff between one day and one week， which is pretty good。😊。

This probably comes as very little surprise to anybody here。 But who is doing the work。On GitHub。

 if you are listed as an LLVM member or a contributor。

 that's basically almost 100% of the people doing the work。

 but our first time contributors are starting to pick up steam。

 we're starting to see more people do firsttime contributions。

 which is great because those are the folks that build up the future for our product。

 which is something we really need to do。But。One thing that's a little worrying to me is when you look at the number of still open pull requests。

 the ones for first time contributors， almost every one of their pull requests remains open indefinitely。

 they're not getting reviewed， and I think that what's happening here is because when you are a first time contributor。

 you don't get to put anybody down as a reviewer on your PR。 you're not allowed to via the UI。

 and no one is auto added。And so it's really easy for a lot of the first time contributors to have their PRs go under the radar because nobodys being added to them。

 So it's something we need to be more proactive about until we get better authorization on the Github side of things to be able to allow people to add their own reviewers or automatically add them for you。

not really worried about how the trend line is going straight up in the last couple months。

 that's basically just active work that people are still working on that that data makes a lot of sense。

But there is an overall trend in the in that we are increasing the number of still open PRs over time。

 And this， to me， says we need more focus on dedicated reviewers。

 That's the bandwidth is the bottleneck with clang a lot of times is getting code review attention。

And doing quality code reviews。 So if you have the opportunity to help out with code reviews。

 please jump in。 You don't have to be an expert。 You could just come in and say， hey。

 this doesn't match the style guide。 That's still helpful。

 So anything you'd like to do with helping out with code reviews would be fantastic。😊。

And then switching gears a little bit to our users。 What language modes do our users use。 Now。

 one caveat to this is this data is all gathered from source graph。

 So it is skewed massively towards open source projects。

 We obviously don't have any insight into what people are doing with their proprietary code bases。😊。

And the other thing is， is we have no way to know what people are doing if they don't pass an STD flag or they use。

 for example， from visual Studio C plus plus latest。

 we don't know what language mode those correspond to。 So we this data is kind of incomplete。

But the really interesting thing to notice about this is 90% of C plus plus code is C plus plus 17 and earlier。

95% of C code is C 11 and earlier。😊，So this is demonstrating that we really need to make sure to keep existing code working。

 That is a very important thing for our users。 That is not to say we should just ignore all the new language standards。

 though， because the baseline expectation of users is we're going to support every language standards。

 So we're going to have to do that work at some point。

This is more just a reminder to folks that if it's going to take a little bit longer to land for a C plus plus 26 feature。

 that's fine。 It's not going to get in anybody's hands for years anyways。

 And so don't sacrifice the quality of older language modes just to rush to get something out for a newer language mode。

😊，Because you'll notice C+ plus 23，2%， C 23，1%， the latest standards like C2 Y and C++ 26 don't even have enough data to show up on the graph。

So what kind of things am I seeing people talking about online。

 This is gathered from places like hacker New and hallway conversations and standards meetings and that sort of stuff。

One thing that's really interesting is the Defer T S has 300， over 300 Abojis on that pull request。

 I've never seen anything like this in the Klang community before。

 There's a lot of excitement around that feature， which is really interesting。😊。

But users are also still super excited about the security improvements that we work on。

 I still see a lot of people talking about how excited they are for bound safety。

 I'm seeing more conversations around lifetime safety。 sanitizers continue to be super popular。

 So work that we're doing to help users secure their code is still very much appreciated。😊。

And then as I mentioned before， we do have people who are tire kicking the newer standards。

 So we have folks who are trying out C23 and C plus plus 233 and reporting issues to us。

 It's good for us to work on those， but by far， most folks are still stuck on old standards。

 C 99 and C plus plus 11 are the lion's share of what people's code is。😊，So within our own community。

 we are looking for some help with completing C++ 20 modules。

 This is something the modules maintainers have gone on discourse and asked for help with。

 and that help has not materialized So I would would this is the one thing that's holding us back for saying we're done with C++ 20 is modules。

 So if you're interested in language support， helping out with modules would be really fantastic。

 I hear there's a round table that's going to be going on today or tomorrow about modules。

 And so if you're interested in that， I would highly recommend going to the round table for it。😊。

We are continuing to work on new C+ plus features like contracts in reflection。

 but those require a massive amount of investment。 Those are going to require lots of test cases。

 lots of documentation， and these are just really， really big features。

 And so these are things that I think our community is going to wind up investing a lot of effort in in terms of code review。

But the one thing that I saw over and over and over and over again。Build times are terrible。

 and documentation manages to be worse。 And so this is something that really frustrates a lot of people。

 especially on the C plus plus side of things。 The compile times for C plus plus have been going way up with every release of clang。

 And so we really do need to start paying down some of that technical debt to keep our build times low enough to remain competitive。

And we really need to work on our documentation story。 It's our docs are all over the place。

 there's a lot there that we could really use some help with working on。

 So if you're interested in getting started working on， playingang。

 working on things like documentation is actually really a great way to get involved because it's pretty easy。

 it's very， I wouldn't say low effort， but it's pretty easy bar for you to clear in terms of getting your patch accepted。

😊，But it really has an outsized impact on our users。 It may not seem that way。

 but it is something that our users would really appreciate。With that， thank you。

 I'm curious to hear what questions you might have。

This is just a minor question about the def blocks。

 How does it interact with the attribute that I think of the name of that functionally acts as a deferred。

Sorry， I'm having a hard time hearing in youall over。

There have an attribute that does something similar to。

 I'm just wondering how that's expected to interact。 Yes。

 so there is a cleanup attribute that exists and differ is basically syntax around the cleanup attribute。

 In fact， the the， if you look at the implementation of it。

 it is using the exact same machinery as the cleanup attribute does。

So they will interact with one another。 And it all just falls out naturally。

How do you feel about the sustainability of adopting the next 10。

 20 years of C and C++ language features for clang？Oh boy。So。

I think that the committees almost think that we're waiting for something to do and twidling our thumbs。

 And if they don't give us work， we're going to just all be out of a job。 And so I。

 I am actually worried about the sustainability of， of new features。

 and especially as they become larger and larger。 So like modules was huge。

 Ref and contracts are huge。 Cons were huge。These sort of features in C++ anyways。

 those are really expensive and hard for us to maintain and support。

 But on the flip side of it is not that we can really do。

 the committee is gonna to do what the committee does and the problem is once the committee goes and adds a feature。

 then people start doing conference talks about it。

 Everybody starts getting excited users starts saying why are you supporting it。

 And so we just have to bite the bullet。 One way that we can help with this is if you join one of the standards committees。

 If you join the C committee or you join the C+ committee。

 you can then have your voice heard on the committee with regards to how expensive certain features are in terms of like their feature set and what the design of it is。

 And that's really the best way to have any sort of influence on this sort of thing is through the standards committees。

😊，But it kind of is one of the situations where it is what it is。 But yeah， it's。

 it's definitely a concern。Everyoneone， thanks for the talk。 did I read with it with the grape。

 right that the PR turnaround time got improved。Yeah。Oops， let me back up a little bit。Yes。

 so this is data that's coming back from September of 2023 through to September of 2025。 And yeah。

 the throughput is definitely improved on getting patches accepted。 Yeah。

 do you have insights what contributed to that。I don't。

 it seems like it might be just growth of the community and so we have more people submitting PRs。

 therefore we're accepting more PRs， but I don't have enough granularity in the data to really be able to dug into it that much。

Thank you。 That's good to hear， though， yeah。Well， if there's nothing else。

 thank you all very much for coming。 App it。