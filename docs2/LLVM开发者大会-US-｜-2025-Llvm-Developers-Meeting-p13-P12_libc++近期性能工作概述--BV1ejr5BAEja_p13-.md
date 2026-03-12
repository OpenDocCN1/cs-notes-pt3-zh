# LLVM开发者大会-US-｜-2025-Llvm-Developers-Meeting-p13-P12_libc++近期性能工作概述--BV1ejr5BAEja_p13-

![](img/1ba2f5891f1cd1f8eaea7a26ed2b0e62_0.png)

Yeah， so my name is Zi， I work at Apple and we're going to be talking about the performance and performance at Jason For。

So first of all， we're going to start with looking at the。

Micro benchmarkchs infrastructure in Li C++， then we'll move on to showing a new benchmark benchmarking workflow that improves the ergonomics for third party contributors when they want to run benchmarks。

 then we'll look at a few recent optimization examples in Li++ when well then dive into tracking LiC+ performance through time and we'll finish with talking a little bit about L&T。

 its current status and its future。So first of all。

 theipososis has had benchmarks for a very long time， actually， so this is not something。

It had benchmarks but they were not integrated into the test suite so they were basically built via normal CMake that you used to build a library。

 they had to be run manually which was kind of a little bit awkward and what we did last year is that we integrated these benchmarks into the Lipsy success sweep。

And you the number of benchmarks in a group。Pretty drastically in the past year。

 so we now have about 11，000 micro benchmarkchs and each benchmark basically tests a specific API and a specific usage pattern with a specific size。

 so for example， inserting elements into a map with 8。

000 elements would be like one benchmark right so we don't actually have 11。

000 individual tests that we wrote。嗯。These benchmarks are written using Google benchmarks。

 so I'm not going to go into the details here in the interest of time。

 but basically you write an benchmark just like you write a normal Google benchmark and so here for example this is benchmarking St hash for 32 bit integers。

 we generate a bunch。you know random integers and then we hash them all you know in sequence and then there's a lot of sort of gymnastics to make sure that the compile does not just completely all everything that's why Google Denmark is great at doing。

And so you just try to benchmark like that know as a normal test in the lips plus test directory and you name it。

 know you give it an extension that bench at CPP and that's where like the magic happens Basically the test re then figures out that hey this must be something that you know this must be like a Google benchmark thing So it's going to make sure basically a lit setup is going to make sure that you have the Google benchmark available for you it includes。

 It's going to make sure that you link can set。And then when you run it。

 you can just run it like you would run any other test in the CQL slot so if you're a contributor。

 you make patches before， you know how to run your test。

 obviously now you know how to run benchmarks as well。And so know if you just run this。

 it's going to execute a bunch of stuff under the hood and then Google benchmarkchmark for those who are not familiar with that。

 it runs your code a bunch of times to make sure that you sort of converge to a。

A measurement that makes sense。And the other thing that we do under hood is that we produce what I call LNT compatible output。

 so L&T is a tool for performance tracking that we'll talk about later。

 but basically it supports a really simple input format。

 the input format where basically you have the name of the benchmark followed by depth followed by the metric that you're measuring so there could be other metrics like code size。

 memory usage， whatever， and then the value for that metric。So we actually like the lit。

 our lit that suite generate that property。And so when you have these files。

 we introduce a very simple script that basically compares two L&T files。

 so if you have like any two measurements in this simple format。

 you can compare them it's going to give you。You know， interesting in information。

 including the genome mean different of change。So this can be helpful if you're like iterating locally。

 this is a super person。But can we how to make this crisis for？嗯。Of course you can。

 I wouldn't be asking the question otherwise。 So it cant be partially automated。

 So something that we added recently is a Giub action of workflow that is triggered on comments。

 And so you basically go like lips Xx but benchmark and then you pass the like you give it the name of the benchmark you'd like to run and then。

In the background， a Github option is going to start and is going to basically run an A D comparison on your PR and then come back and edit the。

The comment with the benchmark results。Right and so this is just the output basically of the Comp benchmark script that we is so that basically this process just gets automated for you。

 so we the baseline is going to be a merge phase which is basically main if you're doing a PR against name and then the candidate is going to be like the head of UR。

At the moment this is still experimental， we don't have dedicated hardware to run this so you know there is quite a bit of noise。

 we are basically reusing the precommit CI that we use for testing which is not at all optimized for making benchmark measurements。

 but the infrastructure is there， so I think these other improvements can be made as follows。Okay。

 so let's take a look at a few optimizations that we did recently。

 and that way we can also see how these tools basically work in practice。So since Elggan 20。

 we landed a bunch of optimizations， I went over the release notess。

We landed over 25 release noted optimizations， those are just the ones that I could easily find in the release notes but there's actually more than that it's been a primary focus in the 22 release cycle I would say if you've been paying attention to the work we've been doing elliptical stress it's almost all per related now。

And so what we did is basically we investigated a bunch of APIs that we thought were impactful and one of the way that we did that was by looking at like workloads。

 you know either external internal workloads and we basically looked at which APIs term let+S were called more than others and then we did some sort of prioritization and we also took into account。

 basically what we thought was the room for improvement in these APIs and one of the things that came out of this investigation was the Asciative containers。

 so the As containers， I was not expecting that actually I thought that other things would show up a lot more but we saw a lot of usage of the Associative containers and we know for having work in lets+S for a while。

 we know that the As containers are not exactly there is room for improvement。

And so Nicholas Fazer has been working really hard on improving these containers。

Pretty great success。So let's take a look at patronizing St mapap a little bit。 first of all。

 what you need to know is that St mapap is basically a red blacky， you know， essentially。

The nodes on the left hand side， the left children are smaller than the current node。

 rank contain a value that is smaller on the right hand side greater。

And then there's some rebalancing going on， but we don't really need to think about that。

And so one of the things that we did was optimize map copying so previously the way we copied a map was actually pretty naive。

 we would take an empty map and then we would build it up by inserting successively inserting things into into the destination map right however when you do that you finally new insertion point from scratch from the root every time so that's really inefficient。

And in reality， you already have a valid tree， you know。

 you already have a valid red tree that you are copying from。😡，So。In that sense， you know。

 now you're using the。Now we're using that structure is kind of wasteful right you are making a bunch of comparisons。

 try to find the insertion points again and you don't really need to so what we did is you know just copy the tree itself like we don't need to perform any comparison it's pretty simple right。

And these results are a little bit small， but you can see here basically that we got some results from anywhere from like 10 to 90% of an improvement for copy assignment and copy construction。

 which is pretty significant， right？So it's surprising sometimes how even a standard artery implementation。

 which you would think has being like， you know， the Holyly Gil optimization actually has， know。

 some pretty obvious things that you can do to improve it。

Another thing that we did was optimizing map search。And this one actually I think is an amazing idea。

 again， Nicholas's father had the idea and implemented it， I think it's pretty cool。😊。

I think you' like it， so when you search for a value inside a map youre walking down the tree and you're basically you have a key that you're looking for and you check the current node key。

 is it greater than or smaller than the thing that I'm looking for？If it's smaller， well。

 if the key that you're looking for is smaller than what you have in the node。

 then you go to the left tile， otherwise you go to the right tile。

 and if they are neither less than or greater than then I guess you just found the key that you were looking for。

And that's really how this works because standard map is specified with what we call the three week ordering compator。

 which is just like it's a less than comparison literally so at the core of the algorithm we really have to do like if you the key is less than the notes key。

😊，Otherwise， if the notes key is less than the key。

 which is equivalent to saying that the key is greater than the notes key， right？And that otherwise。

 we found the match， so the important part here is that we're performing two comparisons。

We're calling the convert twice for every node。But so there are some types which and some pretty important types actually。

 which can do better better， so for example， standard spring。

Any spring out there provides a three way or rich or like however you want to call it。

 but it provides a three way comparison that can tell you whether it's less than equal to or greater than in essentially as much time as you need to just say that you're a less than and so if you could。

Use that rich comparison there inside the map implementation。

 you would have the number of comparisons，And so that's what we did。

 We implemented this for a small set of types and there was a lot of restrictions that we need to。

To satisfy in order to be standards transform， because well。

 you can only do that when you have standard less， for example。

 if you pass a custom comparator to the map like we don't know what it does， so we can't do anything。

We also have to know that the key type。You know， has a rich comparison and you have to know that the rich comparison and it doesn't do anything you know。

 completely weighted， so like we need we have some you know restrictions。

 but the important point is this basically applies to standard map string。

 which is a pretty important thing， right？And when you do that。

 we get some pretty amazing results so here we're seeing like from about 30， 40。

 50% improvement you for all of the like eras find count you contains all of these pretty fundamental APIs and so yeah I think this is pretty neat and we can also see on this comparison here that as we would expect it does not have any impact on standard map for ins。

 for example because。We don't gain for it most of。So these optimizations are great。

 but I'm sure most people have already optimized something or tried to optimize something and then realized that actually the introduce is a regression。

 which is why I'd like to talk a little bit about tracking loopical self performance through time。

So first of all， tracking performance through time is important for any software I think that really cares about performance because it allows you to detect and fix regressions in a timely fashion that's super important because more time you know is spent between the moment where you introduce a regression in the moment you figure out the regression like the harder it is to go and fix the code and understand what happened because there's a bunch of other things that can change in between and then you're just like you don't know anymore how to。

To face that。It also allows you to validate and quantify actual performance swings。

 which can be really difficult when you're talking about maybe like。

 oh we gained like 1% in this operation， it can be lessened the noise unless you're diligently tracking everything。

So this。A a great tool， I think， to sort of validate that what you think is in the improvement is actually an improvement which is especially relevant with modern hardware where the sort of common sense doesn not always apply like you need actual data to figure out that you really made things better。

嗯。And then one thing you can do if you have the ability to grow back in time is actually to detect previously introduce a regression because each previously introduced a regression that you find today is a free。

 it's basically a free lunch， it's basically a free performance win if you face a regression。

And we haven't been tracking so far you know the performance of LiC++ through time。

 but now we have the tools to do that so that's what we're going to talk about now basically we recently introduce a very simple script that allows you to basically build and test Li C++ at a given commit so you give the script the commit if you want to test that and then you give it the set of basically the arguments capacity pass the test suite and then it's going to check out LiLS at that commit not in your current Gi like it does not dirty your current Git state that does that in the temporary directory so it checks out Li at that commit builds it and then runs the test suite as of your current checkout。

Again， set build useful。So you can add a new test， add a new benchmark add do something。

 and then basically go and check the behavior of an historical like of an old kind oflig source against your current locally checked out state just pretty neat so this can be used to like cleanly bisect stuff you know and all kinds of things。

And if you combine that with the new improvements to the you know the way that you run benchmarks in the test suite。

 you can basically。You can basically perform historical performance measurements by doing back in time and running the current benchmarks against old conbil cells。

And so we have this other script that you pass a list of commits in this case I'm just getting all of the commits since January 2025 that by a5 lit you plus plus。

And I'm passing that into the script there I'm giving it an output directory。

I'm giving it the arguments I want。To ask to the test suite， right so in this case I'm saying， hey。

 please optimize and run the map benchmarks。And I actually ran that on my laptop and the next morning I had basically a bunch of L&T files。

 one for each image that corresponded to the performance measurements for the benchmarks I had run。

And this L&T files， this is the format that I presented at the beginning。

And then we have a little tool there that allows sort of visualizing that data。

 this happens locally it generates like a stand HTML file and each line is a single benchmark and you can see like we've had in the last year we've had several sort of improvements to the map operations so if we actually look at the map copy optimization it's kind of hard to see on the graph here but if you zoom enough basically you'll see that theres like this huge sort of drop and。

And if you hover over the graph there， you can see the commit information。

 which is really useful to sort of find regressions and attribute changes。And again。

 the map search optimization had similar behavior， and so it's really nice to go back。

 generate this data every time and be like， hey， like we thought this was going to be good。

 this was good hey， who， actually this one， we thought it was going to be good and it introduced a regression。

So now that we're talking about these graphs， anybody who knows L&T is like why。

 what is this I talking about， why aren't we talking about L&T？

Because L&P basically solves that problem， it's an amazing tool for tracking performance through time and it features a client server infrastructure。

 so it allows basically a centralize it has a server which centralizes the data visualization analysis the detection of regressions automatically and then it has a simple sort of client tool。

That allows you to basically run the benchmarks on any architecture， any configuration。

 and then just submit that stuff to the server and it's really easy。

And on the server you're going to have a graph， this is the same graph that I showed by my locally generated lit output basically right this is what lit would give you there。

 it tries to detect regressions automatically and so on。

So the current status at LNT is we used to have an instance of LNT running at lNT。L。org。

 we could submit stuff to stuff to it。 unfortunately it's not working anymore。

 the codebase is kind of a live support it hasn't we maintained for a few years so it was not in the best of shapes however it's becoming active at the moment。

 so we fixed many of the unit test we're like almost ready to deploy it again so I think within a couple of weeks if we're lucky like we should have basically LNT instance active again that we can submit like everybody can basically submit our core data to。

And obviously there's going to be some improvements we want to make， we'll want to， as I said。

 redeploy NTl elegantorg， then I'll basically want to merge some of these local comparison tools back into N&T。

 you know I needed them earlier to make rapid progress。

 but theres really no reason why anybody in the elegant community shouldn't be able to easily do these local comparisons。

And there's other UI improvements that will increase the value of LT for everyone such as displaying the commit information on charge which is not currently supported。

 there's a few fixes we want to do to the regression detection。You know sell on that。

Theres also obviously some more future lipsical plus performance work that we want to do so first of all。

 once we have the NNT sense running will want to generate the historical data that I showed for as many benchmarks as possible and To into in theorg we'll want to be tracking a few configurations and we're actually looking for community feedback on that so first of all we know that we want to track hardened lipspsical+ because this is a relevant configuration。

For other users。We also want to have tracking for the stable and the unstable API because we also know that this is relevant to a lot people。

 and then we'd like to be tracking curve on various architectures。And once we have。

 you know this setup， then obviously we'll want to you know investigate past regressions in a principled way because this is like you know those are low hanging fruits basically waiting to。

We need to be implemented。So in summary， we talked about the improved micro benchmarkchs infrastructure in Li+。

We talked about some of the organic improvements to run。

To run benchmarking to run benchmarks from the Github pull request interface which currently only applies to the C++ but could be easily generalized to the rest of the Monte Ripo as well we saw a couple of optimizations of concrete optimizations that we did in the C++ but there's also a lot more that we were able to make in the past releases and then we glance over some of the new tools that we have in theCL+ to perform historical data collection and visualization and finally we talked about some of the the current status of LNT its revival and some of the upcoming improvements I must say I'm really excited for actually for what's come in this area。

 I think that LNT is an amazing tool that unfortunately has not been due to it being on sort of live support。

 it hasn't been delivering as much value as it can it's really an amazing tool you can actually annotate regressions and have common。

You say like yes， I've already investigated this regression， linked it to a above report。

 there's like a lot of stuff you know that has already been implemented and is's just like nobody knows about that。

 you know you have to just really take to know it so I'm really excited for the sort of benefits that this tool can deliver in terms of the performance tracking。

So with this， I think our goal here is to make CS faster than it is today。

 but I would even go as far as to say that I think with the proper tools we might be able to make it like the fastest。

 the most performing SL sustainable standard library implementation out there I'm pretty confident that we worked hard enough we can make it work Thank you。



![](img/1ba2f5891f1cd1f8eaea7a26ed2b0e62_2.png)

E question。Hi， great talk。 I was wondering。 So you talk a lot about measuring runtime performance。

 Have you put any thought into measuring performance of like。😊。

How long it takes to compile various headers？We do not do that at the moment。

 It would be easy It would actually be pretty easy to gather that information。 What we do have。

 though， Nichos did set up a we measure the size of headers which is less noise basically than the compilation time。

 it's easier if you don't have a great setup for with a dig machine it's easier to measure the size of the headers。

 we are trackinging that。 buts not like this is the sort of stuff that once we have a server of running。

 know， we'll set up a custom schema for the C plus plus which includes basically which could include the header size。

 basically So so basically we are gathering that information。

 but we're not really be doing much with it because it's not it's not visible to most。

That'sThank you。Hey， so this figured the threeway comparisons really neat and I'm wondering。

 is there any collaboration between the different standard library implementers to share some of these tricks with each other so everyone can benefit from all of these insights？

Not at the moment， I mean， at the moment， not greed。If they want to know what we're doing。

 they can ask us， no but really there's like no coordination， I would say at the moment。😊，Yeah。

 but I guess they'll be soon enough they'll be aware of。I think that we're doing。Okay， thank you。

a question related to that。 Could you do that optimization for any type with a spaceship operator。

Foring的。Okay， so basically， we now have a built in。 Okay。

 so Nila implemented a built in that allows you to check whether your。

Your less than operator is sympathized from the spaceship operator。

 which is the case for many types in C+ plus， I guess2 later。

 and so we do have a building so it will apply to any type。

Where there's this syntheization happening。Ins supposed to swing with a recent claim。Thank you。

 two questions。Arguably a lot of people that care about performance will be using alternative assist containers。

 Do you have any other areas of focus other than assist containers for this work Yes。

 absolutely this is as I said， this is where we required because we found those candidates we were this will have impact and bid so right now we're thinking about looking into the inlining properties of string and vector。

 we think there's a lot of potential gain to be had there。

 It's going to be trickier because those are not algorithmic improvements you know we have to make sure it's basically making sure that we generate the code in a way that is frankly to the compiler that like the slow path。

 for example， it' outlined but like we know that there is large gains to be had there。

But it's trickier and than just sort of improving algorithm So there's that there's， yeah。

 we have a list of I basically。Co thank you。 and microbechs are of course a great data point。

 but theyre also very limited in representing performance of a whole application Have you looked at alternative ways to measure performance other than just looking at microbechs。

Yes， so we are looking at larger benchmarks。 for example， the spec benchmarks。

 It's closer to real world code。 I guess we've also had discussions with some of the Google folks they have there I think it's called fleetbench and that's something that they say is representative of their workloads。

 So we're really interested in like expanding the set of benchmarks that we're tracking in Liy+ for it to represent as well as possible。

 basically what people care about。 at the end of the day。

 you have to set know the metrics that you're that you're gonna gather。

 and sort of the set of programs that you're going to gather them on。

 You need to set that and then you're atimizing for that。 So yeah we're this is still working。😊。

Awesome， thank you。 very work。Com the next speaker。I guess the。Hello。

 I was just wondering the micro benchmarkch infrastructure that you're talking about is that upstream or is that is that a private Everything that I presented today is upstream Okay all of the commentss that that were on the slides are things that you can run pretty much as is and it should work amazing then I have another question what's the timeline on the LNT revival that you're working on。

I mean， you know， the unit tests are working now， we have data dependencies。

 We have a doctorcker image that's working。 It's like we need to deploy the thing on terraform on AWs with terraform。

 I think it's probably a few weeks max it's mostly about getting the right people in the right room at the same time getting the right sort of。

诶。Getting access to like the admin account and A US from the foundation， you know。

 these sort of things， but technical speaking like the most of the technical work。

 almost all of it has been done Okay， awesome， yeah。

 I think we'll be wanting to submit that to that server as well， great。Do you track。

Keepive track code size as you go about implementing these performance improvements for the workloads you're testing for performance for。

That's a good question。 At the moment， we do not track code size。

 We do have like most of the optimizations that we've done so far are not things where the cos is going to go up very much。

 We do have some vectorization optimizations where we check basically that you're not optimizing for size if you are optimizing for size we don't like we use a more naive algorithm that's going be slower but that's basically the amount of it。

 This is all still sort of work in progress。 code size is absolutely something that we will start tracking for for the micro benchmarkchs。

 we just have to sort of figure out does it make sense to just take the size of the executable allow micro benchmarkchs。

 we have to play around the。Thank you， you may have already mentioned this。

 but I probably have missed it， is there a way that you can see the graph that you presented like the historic data？

performance benchmarks， is it availablestream at the moment it's not available。

 but once we have the LNT instance， we're basically going to be submitting the data that we've already generated into the upstream LNT instance and then everybody is going to be able to see it。

 iss that a place where we can continue to kind of monitor what you're like doing in the most of performance or applying to have some dashboard thing。

Do you mean sorry， do you mean monitoring sort of the optimizations that we're doing or just your performance data over time。

In case in if you code size。 Yeah， I think LNT is going to be the place where you'll want to track that basically you'll want to I think theres even a way to subscribe know for emails but basically LNT。

 we're going to eventually set up stuff that submits the automatically into LNT so you were going to be able to track we are going to be able to track performance and you could also track it that way by using the up LT since I don't know if that answers your question think。

Thank you。