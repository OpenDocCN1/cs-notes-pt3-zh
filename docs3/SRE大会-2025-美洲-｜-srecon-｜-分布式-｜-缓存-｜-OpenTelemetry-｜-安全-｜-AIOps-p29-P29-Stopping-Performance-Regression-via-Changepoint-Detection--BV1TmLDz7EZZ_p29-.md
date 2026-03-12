# SRE大会-2025-美洲-｜-srecon-｜-分布式-｜-缓存-｜-OpenTelemetry-｜-安全-｜-AIOps-p29-P29-Stopping-Performance-Regression-via-Changepoint-Detection--BV1TmLDz7EZZ_p29-

。

![](img/4f3f1e726407f98183f8f7370cff3aa0_1.png)

![](img/4f3f1e726407f98183f8f7370cff3aa0_2.png)

Good morning， everybody。 I'm Shany。 I lead the capacity and performance team for Tickupplant at Bloomberg Today。

 I'll be talking to you a little bit about who we are and why changepoint detection came to be relevant to us。

 Yeah， and I'm Joseph。 I've been on the capacity and performance team for about four years。

 And for the project we talk about， I helped lead it from the start up until now。

 and I'll talk about a bit more of the technical and product details later on。😊，Alright。

 so before we go any further， I think it's important to establish a baseline definition of change points that we' work off of。

 So if you have a metric or a time series that's describing your system's behavior。

 A change point is essentially an instance where that time series changes abruptly and persistently。

 So you probably care about it。 You want to investigate it and know what about your system has changed。

So with that out of the way， let's talk about our experience building a change point detection product。

In order for us to tell you why change point detection was relevant to us。

 it's important to understand what the tickle plant is and where we actually fit into Bloomberg's market data organization。

 As you can see over here， the tickle plant is responsible for feeding market data realtime and otherwise to downstream applications at Bloomberg。

 So if you're a Bloomberg customer that's looking at market data on the terminal。

 through our enterprise API services or bulk data products。

 you are likely a customer of the Tle plant。Being the sort of common ancestor for market data at Bloomberg really means that Tcoon's performance is going to reflect in Bloomberg's overall market data products performance。

You know， sometimes there is a sentiment amongst Ss that outages get a lot of attention。

 They're spoken about。 But when things are going well， we're generally doing our job Well。

 it just gets swept under business as usual。 It's slightly different for us when it comes to latency。

 especially because low latency is a feature of our product。

 Our clients care deeply about low latency， because ultimately， it's crucial to their success。

 So having established that clients care about it。 And that Ton's latency affects Bloomberg's latency。

At any given point in time， it's important for our team to know whether the work that we're doing is making Bloomberg's performance better or worse。

So what is it about latency， especially for us and our product that makes it a challenging problem？

 Well， it's really the diversity of factors that end up contributing to latency in a large scale distributed system like ours。

 As you can see from the visual over here， we're dealing with high volumes of extremely volatile data。

 What makes it even more fun。 is that we can't necessarily control or even reliably predict the factors that end up contributing to this latency。

 It could be news events across the world。 client interests and subsets of markets that constantly change。

 And to add to all of that， these periods of high volatility are typically also the times that our clients care even more deeply about latency。

 And to kind of illustrate the volatility and the volumes in the two weeks since we made the slide got it approved The peak is no longer at 400 billion。

 We're now looking at 490 billion messages in any given day as our current peak。😊，Ultimately， for us。

 all of these factors mean that not all latency is avoidable。 We do have to live with some latency。

So what do we actually choose to do about that。 Well。

 we instead choose to get much better at preventing the ones that we can control from impacting our clients。

 things that you see over here， like the core rollouts and everything else， we're in control of that。

 So if we flag a regression early enough。 then we are in control of being able to roll it back before it ends up impacting。

😊，Clients and their performance， ultimately。When we start thinking about how we actually approach this problem。

 the challenges come back to the breadth and scale of the system that we're talking about。

It's impossible for us that， you know， we can rely on understanding every little nuance of the client behavior and their interest in the markets and。

 you know， design perfect performance tests that are reflective of this。

 So what we in statute to do is we rely on statistical methods that allow us to take this fairly complex system that we're dealing with and treat it as a much simpler black box。

So there we go all right， so what do we actually do about this for a while， not much tangibly。

 we thought about the issue a lot， we recognized the need for it。

 but we were sort of forced to take action when the issue came to us。We saw。

We saw decreases in performance sweeping across many machines in the data center。

 it was obvious to all of our engineers that this was a problem， but despite many。

 many eyes looking at it， no one could actually pinpoint exactly when this started。

 it didn't seem to have any correlation with code rollout or feature flags and no one made any progress。

It was only when we rolled out a very rudimentary changepoint algorithm and we were able to take the metadata before and after each point for every machine that we were able to solve the problem and what that looks like is this a bit of background here。

 work time is this is the work time of machine over time。

Workaktime is the time it takes us to process one unit of data like that market message graph that you saw earlier。

 each of those is a tick and this is the time it takes to process those。

Work time is interesting for two reasons。One， it sort of acts as an activation function to an activation to like a cliff function。

 So if our work time gets too high， our latency can explode upwards without bound and may not recover。

The second reason it's interesting is。It is mostly load independent。

 so regardless of whether the market is extremely volatile。

 we're getting lots of data or it's in a more typical state。Work times about the same。

What we see here is that there was a certain configuration file that this machine was added to。

But nothing actually happened until several days later when the machine restarted for maintenance。

 then for completely separate reasons， this change was rolled back and forth。

And each of those also had their own several day offset。Now this looks simple。

 partially because I chose the most simple draft for this part。

When you consider the millions of metrics we had and the weird rollouts and the vast。

Sort of strangeness of this。 It was basically intractable for a human to handle this problem just through looking through like Grfana。

So unfortunately， a lot of our data is not as clean as that is， a lot of it looks more like this。

 what you see here is the same event in three different environments that I'm going to go over just to show you guys what I mean so。

Here， this is latency， lower is better， you see it's relatively consistent， there's a few spikes。

 one large one， and while that's not good， we don't like that。

 it's not something that represents an existential risk if we were to rule out this code。

Here it's the opposite scenario， you do have that large spike。

 but the latency remains elevated and it never properly recovers to a baseline level， this。

 if it represented the performance of software and this rolled out to all of our machines could be existential threat。

Unfortunately， algorithm unfortunate for an algorithm。

 this is the much more common case where it's a lot more ambiguous。

 so depending on the number of data points you get， the time scale。

 the magnitude and with the knowledge of your system。

 you might say maybe this is a change point or this is or maybe here or here or here。

 and when you look at the research comparing change point detection methods。

There's a significant amount of interannotator disagreement， even among experts。

So when we were choosing an algorithm to base our product off of initially。

 we wanted to choose something that， aside from having。Good perform evaluation metrics。

We we wanted what it flagged to match our expectations of what a change point should be for this。

 we went with Bayesian online changepoint detection very simply， simplifying a lot here。

 how it works is as it reads over your series， it forms an idea of what the distribution of your data should be。

Then when it sees enough points that seem to have come from a different distribution。

 it calls that a change point。I want to spend a little bit more talking about the challenges of actually bringing this to our team as a product。

I'm mostly going skip over the expected challenges。 A lot of these were。Frankly。

 what you would expect of a team doing a data scienceency project for the first time。

 So tracking inter annotator agreements， versioning experiments and data。

 I want to spend a lot more time talking about the unexpected challenges。Ironically。

 the first of these is expected changes。 So our algorithm here was really good at detecting the market opening and closing。

 machine maintenance periods。😊，If your calendar wasn't working。

 it could tell the weekend's really great。The problem with this is that while these are all change points and the algorithm is right。

 it's not really something that's interesting to us or stuff that we care about。And in my experience。

 when I look at teams that calculate whether they're meeting their SLOs or internal anomaly detection systems。

 and I've seen it in a few external projects as well。

A lot of the ways that people deal with these sort of expected anomalies or expected change points is to create one or more configuration files。

 and they basically say， hey， I want to ignore this span of time and ultimately ends up extremely toil intensive。

 I think people。It works， I'm not saying never to use this， it does work as a temporary measure。

 but people really underestimate how much work is actually required to keep these up to date and usable so for instance。

 we have hundreds of markets we care about they all have their own markets open and close they all have holidays that might not occur it on the same day every year。

Time zones is another thing。 we did something very similar for an internal SLO。

 There's many times where we broke due to various DSST situations and time zones and it ends up being like a game of Wackamel essentially。

What we did here instead is we deliberately went out of our way to avoid having these sort of configuration files almost on principle。

 we focused a lot more on post processing and preprocessing our data to make sure that we were a bit more resilient to these sort of expected changes so rather than have configuration files per market per series that we read and exclude point in time。

 well push a lot of that to the query layer for in our case graphite to get series that we know are clean。

 let's say。The the other issue I want to talk about is from a triage perspective。

 this is our initial UI， and I think it looks okay， good for an SRE team。

The unfortunate part is that there are 12，000 rows here， and this is shortly after we launched。Now。

 yeah， some of these are false positives， but a lot of these are also stuff that。

Let's say user experience that we didn't really。We didn't really think too much about and we sort of took for granted。

 so things like you run the same analysis， but with slightly different parameters and so now you've duplicated or near duplicate a lot of change points you run the same analysis but on a different day and so because we have a rolling retention window window then we have slightly different change points。

And also like very simple stuff like in these bottom two rows， they are very similar。

 there are two changed points which are very similar。 They happen on the same cluster。

 they're just four hours apart。The main difference is that it happened on two different nodes。

Is that important diagnostically， yeah， but from a triagegers perspective。

 doing this each week as a team， this just compounded with everything else I mentioned to be very overwhelming。

啊。Ultimately， our solution for this was to put in much more work into having a good experience and product than people would expect for something that sounds very algorithmic and data scienceency。

 So， for instance， we added tags to our run so we can look up certain。Bits of analysis we care about。

 we added an ability to mark a change point as either a true positive or false positive to have a better feedback loop and improve。

 as well as a bunch of filtering options that aren't depicted here。In total。

I'd recommend using a statistical system like this。

 whether for anomaly detection or changepoint detection， if your system。

 it has a lot of ways it could change， it's very noisy So simple rule- based systems won't work。

 And then particularly if your system is very large。 you have distributed responsibility。

 and it's not the SR ideal。 It's not， hey， everything as instrumented exactly as I want。

 everyone tests exactly as I want。When you have to live with what you have。嗯。

And I'd really stress that you'll probably spend a lot more time working on the usability of your product rather than the actual algorithmic stuff。

 at least compared to to what I've seen people expect。

 I'd also recommend this talk from Ivan happen it happened last year。

 he approached as a similar problem from a different angle。

 I just think it's nice to have another perspective。

 So if you want to make a market open or closed detector。 please reach out。

 we'd love to answer your questions。 And if you want to work at Bloomberg， we have a QR code。

 Thank you。

![](img/4f3f1e726407f98183f8f7370cff3aa0_4.png)

![](img/4f3f1e726407f98183f8f7370cff3aa0_5.png)