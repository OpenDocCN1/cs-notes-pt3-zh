# SRE大会-2025-美洲-｜-srecon-｜-分布式-｜-缓存-｜-OpenTelemetry-｜-安全-｜-AIOps-p42-P42-Network-Flow-Data-in-the-Cloud--BV1TmLDz7EZZ_p42-

![](img/7f9736476d139ab841252da4b171e7a5_0.png)

Thanks， y'all appreciate you being here after lunch。

 We'll try to keep it lively and not put anyone to sleep。 But just from the agenda。

 there is gonna to be a little math， I apologize。Yeah， so we'll start off with kind of a motivation。

 so here's a quote from Mark McBbri， who was a former principal engineer and he was investigating a service migration at Slack to a new network environment。

And。You know it's a very valid question and if it's hard to tell the answer to this question of like if we move services。

 like how much traffic do we have， where is our traffic going and is our ability to deliver this traffic at risk？

So how services communicate， that's that's pretty important to understand。

 and it's a hard question at the time for Slack because we have this very non uniform set of ways to deliver our services。

 So we have a mix of。Workloads at run on EC2， EKS and Cu。

 services talk to each other both through a service mesh like via envoy。

 but we also have hosts that don't use envoy， don't participate in the mesh at all。

 they use console or DNS， so it's kind of a bit of a mess to kind of find some sort of common denominator for how these services talk to each other。

And this extends beyond just the services themselves。

 the network primitives in the environment that we run in also have finite constraints。

 so if you consider like low balancers and gateways。

 those also are constrained on things like packets per second or bandwidth。

 and you don't want to overwhelm those either。And so here's an example of kind of where the state of the art was at for our network monitoring。

 we had individual host stats that were exposed via you know kind of the defaults available from Promeus network or node Exper and those network stats are kind of undifferentiated。

 they'll capture the magnitude of host traffic but they don't tell you where it's going。

 there's no directionality， it doesn't tell you what service this host is talking to or services and at Slack we really rarely care about。

The traffic of just a single host。 So we need some additional attributes for grouping。

And so what happened was this reminded me of a very classic。

Graph theory problem and so we have to go back to our college days and we have this definition of what's called a flow network and so we have a graph graphs are made up the vertices and edges。

 flow networks is a special case of this so we have a directed graph and that's Scott vertices and edges again and there's a capacity function that describes each edge and a flow is a mapping that satisfies the constraints on these edges so we have two conditions we need to meet there's a feasibility condition and so a flow along an edge can't be negative and it can't be larger than a capacity of an edge so let's use the analogy here of like this is a road network between cities all the roads are one way。

😊，And then there's another conservation or excuse me another condition that needs to be met and that's the flow conservation condition。

 so basically what this says is the sum of flows going into a vertex has to equal the sum of the flows going out unless it's the source or the sink of the flow。

And if I just put you all asleep after lunch， I apologize。

 we're gonna have picture time now so you can again imagine this is like the width of the road here。

 let's add a red flow， this flow has roughly half the magnitude or the magnitude of the flow is roughly half of the capacity。

 we go from this source A to C to D to the sink G sometimes we refer to this as the path and again its the magnitude is consuming half the flow。

 so half the lanes are used up。Now we're going to add another blue flow here。

 so we've consumed all the capacity along this particular path。And so now， if I want to get from。

 say， B to G。I can't take the path through C And D because it's already consumed fully。

So I have to take this alternate path。And this is the basis of the flow network definition。

 so let's look at this in maybe more familiar terms。So we have a a。

Roughly kind of standard AWS infrastructure diagram here。So let's， let's start from left to right。

 The left side， we can think of this as like edge regions。

 maybe we have traffic or requests ingressing from the Internet。

 They're going to hit this load balancing stack。Pass through an auto scaling group。

 land on some EC2 instances that are running a proxy function。

If the request can't be handled locally by that proxy or that caching layer in the edge region。

 it continues on to a traffic or transit gateway， gets passed back to our central processing region。

 we have another similar stack of processing of load balancers and instances。

 and maybe this is like our web app stack that finally handles the request。

So we can take this very kind of high level architecture model。

And we can convert this to a graph and this is calling out all the same dependencies。

 so you can think of you have an availability zone that depends on its upstream region from that infrastructure diagram。

 we know that the NLBs were constrained to a single availability zone。

Those ASGs downstream depend on the NLB and so on so forth， passing on to the EC2 instances。

So now we've described that topology in a graph， we have some other questions to answer right so for our traffic flows。

 what are the magnitudes of them， what are the sources and sinks。

 what's the topology of the given infrastructure that you're interested in。

 this could be your cloud infrastructure could be physical as well。

 and then the question is can or the capacity of the graph that topology。

 can it satisfy our flow demands。So we went。Way back to a super exciting new technology now。

 this is SF， it's old it's been around forever。 there's an RFC you can go read the definition on if you need a little light bedtime reading。

 but essentially uses a classic network 5 tuupple for a hash。

 so we match on source and destination IP address， source and destination port。

 and then the protocol type。And so that could be like TCP or UDP。And using that hash。

 we maintain a couple set of counters over a time interval。

 So we look for the number of sampled packets that match that hash。In in the given interval。

 and then we also keep an aggregate sum of the payload from those packets essentially and that gives us the ability to describe the source and the sinks of those flows。

 So that's the source and the destination IP address。

 And then the sum of the payload becomes our magnitude for the flow。

Now we're still missing the overall flow path from this data because we don't have any understanding of the network topology based on this export。

So at Slack to build this， we run an HSFD agent， this is open sourced and readily available。

 anybody can go grab this and this is on every host at Slack。

 we sample from this tunnel interface that we'll talk about a little more later and then we gather those statistics up and we send those to a centralized service that's based off PAC。

 PAC again is a open source service readily available， anybody can do this。

 it's got a SF listener so it's got this SF accounting Damon。

 collects all those SF logs from our fleet，Basically writes that to disk and then on an ongoing five minute interval basis we'll parse the logs that are local to disk and do some annotation based on the grouping that we're interested in so we can use the IP addresses of。

From the SF logs and do look ups against our other data sources like our Che infrastructure or our cube infrastructure。

 and we can use that to map the flows and account them based on on like a per service basis now or a per availability zone or per region。

 and we can annotate this in groups that are actually interesting from a failure domain perspective。

嗯。Once we've done that log annotation， we write that out as a set of parquet files to S3。

 they have this exact same file format that you'd find as an AWS VPC flow log so if you're familiar with that it's the same spec and then we actually pass this on to a thirdparty tool called Kenentch for some more analysis we'll talk about in a little bit。

 but you could run your own data warehouse and do your own queries against this data as well。

Some quick stats on setting this up， This was like a halftime project for me over one quarter。

 The majority of the time was actually spent waiting to roll the agent out to the fleet。

 We were a little conservative about wanting to run something。Every it's reasonable。

 it's been running since January 24 and this is very low touch。

 like I think there's been approximately1 PR a month and one actual page in anger for the whole system。

 so it's very mature， very stable。Not sexy。嗯。For the implementation piece to understand the topology。

 we kind of punted on this。 again， we're talking about the kintyick product。Basically under the hood。

 this uses a bunch of。A S describe calls to the E C2 and networking API endpoints to build that topology graphs and understand all the dependencies。

 You could do this yourself。诶。I didn't have to。And a brief aside， you you might ask。

 why not just use the the VPC flow logs。 So at Slack， we have a。

A few different things that kind of make that challenging。One， we run a full mesh。

 that ton1 interface。 That's a full mesh encryption interface。 So we send all traffic。

And encrypted in transit。 So from the vendor's perspective on any cloud。

 they're just going to see encrypted traffic going to the port of the VPN listener service。

 It's pretty boring to get better attribution。 We actually need to capture that traffic prior to encryption。

嗯。Now， you might say， you know， you're not gathering any of the network primitive flows that might be available with AWS。

For us， we run dedicated。Ingress and egress proxy stacks。

 so like having that boundary at for internet in egress and Ingress is fine。

 like we're willing to give up that traffic granularity。And the big thing is cost。

The system I just described runs。It's 1000% less per month。Or three orders of magnitude， it's wild。

And we get to do our own annotations。 So again， breaking those logs down by the failure domains that we're actually interested in。

Allows us to do a lot more useful analysis of the photo domains。

 So let's jump into some of those use cases real quick。 One of the big ones was。

Our infrastructure organization wanted to push costs back on service owners。

And so here we have like a network load balancer where service A and B， you're talking to service C。

 Service A sends twice as much traffic because we now understand the flows across our topology。

 We can have a chargeback mechanism for service A and say you're going to pay two thirdds of the cost for this load balancer and service B can pay the remaining third。

嗯。If you've ever had to track down intra versus intratraAZ costs。

 you know there's a difference in cost for sending that traffic。

 you can now have an actual empirical conversation with a service owner and say these are the tradeoffs because you send traffic via more expensive manner and maybe they have a very valid reason as a service owner to have that traffic pattern but you can at least discuss the tradeoffs in actual material costs now。

 and maybe they can redesign their application or their service to have more economical traffic flow。

Another use case was traffic migrations， so here we have like a ring of VPCs pairing that went to TGW mesh。

 so you can imagine for each intermediate step of this migration process。

 you might be concerned about dropping traffic or not having valid paths。

You can examine based on the demands and use some pretty because we transform this into a graph theory problem。

 there's a lot of algorithms available to do the traffic analysis piece to determine if the that feasibility condition that we talked about earlier can be met。

And you can actually take this one step further than just migrations。So。

Let's go back to our our large graph。 And， you know， maybe this is too verbose。

 Maybe it's not verbose enough for your environment。 but you。

 you use this graph to describe things with enough detail that you can then do a similar analysis where。

We can remove a node and then apply the flows that still exist and see if our feasibility our ability to meet that demand is still still possible。

 So in this case， like we've taken out an entire availability zone right。

 So we can clearly see that we've split the graph into two parts。But maybe this is fine。

 maybe we're over provisionvised enough in the remaining regions or excuse me。

 the remaining availability zones on the right side， that it doesn't matter。

 but we want to make sure that we're not too over provisionvised because otherwise we're just setting money on fire to serve requests that don't exist。

And you can take this even further and you could iterate if you wanted to be totally exhaustive and do this check for every node and every edge in that graph。

 removing one at a time。嗯。So yeah， just to recap。To enable the network flow data。

 you want to generate the logs that gives you your source in sync， model your network topology。

 You need to have some understanding of the forwarding rules within your topology that allows you to determine where the flows go。

And then that in the end， you can make informed business decisions and really bound the risk without having to empirically shift traffic around。

It's I've got， if anyone's got questions， happy to take them。



![](img/7f9736476d139ab841252da4b171e7a5_2.png)

![](img/7f9736476d139ab841252da4b171e7a5_3.png)