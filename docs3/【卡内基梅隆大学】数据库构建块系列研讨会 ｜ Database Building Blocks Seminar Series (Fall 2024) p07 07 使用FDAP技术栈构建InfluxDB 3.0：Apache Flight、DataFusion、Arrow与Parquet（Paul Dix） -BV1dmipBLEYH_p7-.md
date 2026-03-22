# 【卡内基梅隆大学】数据库构建块系列研讨会 ｜ Database Building Blocks Seminar Series (Fall 2024) p07 07 使用FDAP技术栈构建InfluxDB 3.0：Apache Flight、DataFusion、Arrow与Parquet（Paul Dix） -BV1dmipBLEYH_p7-

🎼Yeah， down。They ready for。And y'all at the speed of sound where we're now wax worst top perhaps or gather around and witness something。

🎼The database Building Block seminar series is filmed in front of a live studio audience。😊。

🎼This program is made possible by Google。

![](img/43d41d11438ff8a292e69a5017bd8cfd_1.png)

🎼This is a big deal right So let's get started。 Rive's a big deal。

 It's because Paul is the only speaker。 we've had these data seminars this is his third talk And not only this is his third talk。

 the first time he came in person like 2016，2017。 And he sometimes listened to us and then he didn't listen to us and came back。

 taught us how he did it was a mistake。 He should listen to us。 So this is his latest talk about。

 hopefully saying why he listened to us and they have a new system with infl TV that's super exciting。

 and Paul has read Shepherd。 So again， as always， if you have any question for Paul。

 please feel free to interrupt him any time that way he's talking to an audience and not to himself。

 and feel free to do this any time。 Paul， again， third time， thank you for being here。

 The floor is yours。😊，Thank you for having me I can address the listening to you bit later and whether or not it's wise I can I can give you my。

Reports from the field lesson lessons from the from the battleground M is a bad idea that was that was my main one may or may not be。

 but that still outperforms a lot of stuff on our new versions keep going okay so thank you for having me so this talk is about building influx Db3 Auto with the FDap stack Ftap being flight data fusion arrow and PartK I'm Paul Dix I'm the founder and CT of influx data which is the company behind influxDb。

So influxDB for those who don't know is a time series database basically from metrics and events so when you think about that you know screens like this this is a dashboard for one of our production clusters of3Dto where you can see a bunch of time series data everybody's favorite time series recently NviIdia stock price why are we building databases let's just go do AI stuff come on Andy let's do it。

Time series use cases， so server network monitoring， obviously application performance monitoring。

 custom metrics， sensor data is a very big one right factories， power， mining， water and waste。

 rockets， agriculture， satellites， vehicles。😊，Any machine you can think of that runs out there in the world outputs sensor data。

 and generally you want to monitor on that and report on that as a time series。

And structured event data of all kinds， you can basically produce time series from that which leads us to tracing perhaps maybe logs。

 you can pull time series data out of those things so I think there are two ways to think about time series databases the first which is usually what people think about when you mention a time series database which is storing computed or sampled values along with some metadata right so basically CPU measurements average response time to an API or you know those different things。

But the other way to think about it is essentially time series is a way to analyze data so you can compute time series data on the fly from any sort of raw data that has a timestamp on it events。

 like I said， logs， you can。Pull up time series from it。

 but when you think about a time series and you have one to work with generally it's something like this right you have。

Colllection of time value pairs in time order and you have a set of metadata that describes you know this collection of data right the metadata could be a sensor ID。

 a host name， building region， customer， whatever it's anything you can think of that would basically describe a single set of observations over time。

So the trick about building a time series database generally is this the data arrives like this timestamp T1。

 T2 each one is new data arriving with different timestamps and then the columns the colored boxes are basically different individual time series so the data arrives like this。

But。You want to query the data like this。😡，And optimizing this is basically the entire game。

 how do you make that fast， how do you make it efficient and how do you do it with fewer CPUs。

 less RA and less hard drive space。So inflxDB has a couple of things around it that are important for our users in our use cases schema on right is a big one so they don't have to define their schema ahead of time。

 they can just write data into the database， high volume deormalized in justest most of the value in the data that people send in inflXDB is actually in the recent data that's data within the last 24 hours right because they're building real- time monitoring alerting systems where they're alerting on very recent things or they're building like dashboards for humans to look at。

 which is again all focused on very recent stuff。Because of the use cases。

 there's performance sensitivity around the query workload right people don't want to wait seconds or even hundreds of milliseconds in many cases for the results to come back。

 they want it to be from a user perspective， they want it to look instantaneous and then from a systems perspective in the background。

 they want to be running a bunch of monitoring in quiries and they want that to be fast。

And in our case， which I think is kind of like。Weird in the database community。

 which is like most people who use influxDb actually use the automatic data eviction capabilities of it right so they'll keep data around for whether it's seven days。

30 days， six months or a year or two years eventually they want to evict the data and they want the database to just do that for them。

Quickly and efficiently。So。This talk is about 3。0 in the F top stack。

 but I did want to touch on the evolution of influxDb as a way to highlight。

 I think some of the important properties。Of like the F abstract stack and how we arrived where we are now So version 1。

0 of influxdb came out in 2016 Andy and I were just talking before we started this recording and he mentioned that he emailed me right after we announced our early prototype of the first thing in November of 2013 and the key things about the early version of influxdb 1。

0 version is influxql， which is the query language that we built from scratch and the query engine around it and the storage engine that we built which is basically an inverted index paired with an L entrytry that was designed specifically for time series data right so those those things together kind of made influxDb1 like really good for metrics use cases up to a certain scale now with version 2。

0 we wanted to do a couple of things we wanted to add a bunch of capabilities to the database so that people could push down more processing and more query。

Complexity into the database itself。 So we created。

Our own query language and scripting engine called flux。

 which is a multiyear difficult thing that I could tell you about on another talk。

 and we also embarked on an effort to create a multi tenant cloud offering that was usage based。

 which I can also I could also create a whole other talk on，😊，Mululttiten of databases in the cloud。

 which totally suck。But。All of this led to3D， we had the first release of a3D version in it last year。

 which was the part of this talk will cover the architecture of that version。

And the key things around that were the FT stack using object store for all the data and then。

Something that I'll talk for the future， which is bringing pipe。And before I get to that。

 let me just show influxQl so you get a sense for what we were dealing with and what drove us to the FTAP stack so this is what the query language looks like as you can see it looks kind of familiar it looks like it might be SQL。

 but it's actually not SQL in meaningful ways like one this kind of query would be very difficult to express in SQL but also if you're a SQL person。

Seeing this probably hurts you because it doesn't look like regular SQL。

 but basically you're getting the， you know average response time for the last 10 for the last hour in 10 second intervals。

Fillling the gaps for both the CPU and the disk measurements。

Fluux our query language and scripting engine was very。

 very different so we wanted basically like a functional style language This is what one query might look like I wanted to show another more complex example of flux where we can show like importing functionality from a different live from from from an external library so we had things in flux where you could like connect to third party data sources connect to APIs send data out to other places。

Basically create all sorts of complex logic that was executed inside the database itself。

All of this version one version two was written in go so we basically like we started version you know the initial parts of influxDB in 2013 just for reference go hit 1。

0 in March of 2012 so basically like these early versions of influxDB kind of like grew up with the go community and we created a lot of libraries along the way。

 we there wasn't there weren't like libraries we could just like pick up and use off the shelf right and there were a lot of people creating stuff around the same time。

So after we released 2。0 there were a number of needs that we realized that we needed to hit that people had been asking us for for a while and we just like in 2。

0 we didn't focus on those things right in 2。0 we focused on this like cloud database and the new language but we didn't focus on like the core underlying database technology。

 we essentially like just。Puulled over the exact same database technology that we had built for1do0 into 2。

0 So the things that we needed were infinite cardinality for time series data people wanted they wanted cheap historical storage as Andy mentioned one0 and 2。

0 used locally attached disk we told everybody to use SSDs and there were memory map files which meant it was actually really really fast for a number of things but moving that over to use like。

Object storage for cheap historical storage seemed like it would be very very difficult We wanted to achieve quote unquote unlimitedlimited scalability and the design of that system just didn't lend itself to like horizontal scale and most importantly we wanted broader ecosystem compatibility right what we learned when we developed the flux language and released it out into the world was there was a very small group of people who were big fans of what it did and what they could do with the language but a much larger group of people who said I don't want to learn your stupid language I already know SQL and I want to use that and I already know like JavaScriptscript or Python and I want to use those for my scripting needs so we took this be back to heart and we thought okay we want to be able to we want to bring in a SQL engines so that you can actually execute SQL against the time series data right because the other thing is like we had influxQL and people loved and still do love inflQL for doing a number。

Of thingsing but。It's our own custom like query engine and there's tons of capabilities that just doesn't have that a mature SQL engine has like joins and like window functions and partitioning and like all this crazy stuff right so while influxQL was good for you know really easy time series queries when people wanted to do much more complicated things there was just no escape hatch and what we wanted for the next version of influxDB was to give them SQL as an additional option and basically like a fully capable engine。

So。Enter into 2020 obviously we had a global pandemic people dealt with this in a bunch of different ways I had my own journey which was。

Thinking about the database and thinking about whether or not I wanted to rewrite the database。

 which is a foolish thing to do and there was stuff leading up to this so basically I wrote this blog post in 2018 as you can see about my my enthusiasm for rust and how I thought it was actually super interesting。

😊，F problems like building databases and then。Closer in in 2020 this is April of 2020 so this is like right in the meaty section of the lockdown and you know we're all isolated and i'm thinking。

Why not？Let's rewrite this database in rust that would be a good idea and my thought at the time was essentially like the changes that we needed to make。

To bring those capabilities into influxDb were so dramatic that basically they amount to a full rewrite of the database anyway and my thought at the time was I mean obviously like I love a bunch of this stuff that rust has like memory safety and fearless congruancy and like crates and error handling and all this other stuff but my thought was that I don't want to write a query engine again。

 like we've already written too， we wrote one for influxQL。

 we wrote one for flux I don't want to rewrite a third like I just want to take something off the shelf and my expectation at that time was that we would be using something something written in C++ from some other project and doing that in rust would be cleaner and easier I thought than doing it in go and having to deal with the seago bridge and whatever so。

In 2020 we landed on data fusion as the project for the query engine and this was in so obviously Andrew and Andy both gave talks the first two talks in this series and Andrew works with us I work with Andrew Infl data he started in May of 2020 so in early April 2020 I actually reached out to Andy because I was looking at data fusion as a potential like thing to use and he was helpful enough to get on a zoom call with me and talk to me about project but the other two projects we evaluated that time and this was basically like Andrew's first assignment when he started with us was basically like go look at these。

You projects and determine which one would be best for us to use as like the query engine backend for our new version of the database right and the three projects were ClickhouseductdB and data fusion and mind you at that time Clickhouse was not a company is basically just some open source projectandex DDb was not a company there was no mother duck there was no duck labs it was basically just you know some project Cwi with I think a couple of postdocs working on it So we looked at all the three of these projects and what we realized was any one of them was going to take a significant amount of effort to add the capabilities in that we felt we would need to make like firstclass time series database on top of them So we thought okay if we're going to do that it means we're going to be heavy commits to whatever project we adopt and we already know this thing is going to be in rust and data fusion is in rust and the other advantage was data fusion was already a part of the。

Soft Foundation so it was already it was inarrow， it had been contributed in the fall of 2019 so。

At that point， we're just like， okay， let's base everything around data fusion and really the bet was。

You know just like the summer of 2020， the bet was like if we contribute to it。

 we'll be able to add to it and ideally hopefully over time what we'll see is that it will pick up momentum and other people will pick it up right because really like。

The query engine for us is a dependency it's a dependency that we have and basically one of the classic like open source models like why would you contribute to open source a do open source because you want to commoditize your dependencies you want your dependencies to be as cheap as possible and with this we figured well it's in Apache it's free and ideally other people will contribute to it adding functionality performance and basically battle hardening it and we will hopefully benefit from that I mean obviously we're contributing back but in 2020 wasn't obvious that that would be the case I feel like given that I don't know 80 70% of the talks in this talk series talk about data fusion I think it's kind of been playing out pretty well so far yeah so this is the architecture of the3。

 database the distributed version of the database so I'm actually going to be talking about two different architectures for the database。

This is the one i'll talk about first and foremost and then later i'll talk about a single server one so it's broken up into a collection of different services this is probably a familiar architecture or two people been paying attention databases for a while we have an ingestion tier we have a catalog as a service we have object storage obviously we have a compaction tier that will rewrite data and write indexes and stuff and then we have a query tier。

So we'll talk about each of these different pieces and how we use the F stack in all of these。

So query processing in inflectuxb30 so one of the interesting things is we actually have a number of different front ends that we have for doing query processing right so we have the sQL front end which is obviously the data fusion included one。

 but we also have。On the far left you can see the storage GRPC front end right so basically our version two cloud platform has this GRPC API to communicate to the storage engine and we had to implement that for the version3 backend so that it can be plugged into that cloud system we also wanted to create influxql as a front end we didn't start out this way in 2020 but that's where we arrived and i'll talk a little bit more about that。

And then the other is the reorg runed， which is really just like compaction and persistence。

 which we'll talk about that。So。We do planning， execution。

 all of this is data fusion and outputs record batches， and we send that either to G PC out。

 arrow of flight or parquet rid to object storage。So。

We use a lot of different extensions within data fusion in influx B3。

 and we'll talk about some of these right so we use you know table providers。

 we use different front ends， we use different logical plans execution plans streaming extensions。

 so let's dig into some of these so the ingeter。It's job essentially is to what do the check marks mean in the last figure？

Basically these are all points where we use like extensions in data fusion。

 we hook into the data fusion API to create custom extensions Go okay thanks。

So the ingeter takes in line protocol that you see on the left。

It buffers it in memory in arrow format， that's in arrow compatible format。

And the point of this is to， you know we can't write the data as it's coming in straight into objectject store we have to buffer all this data up in memory。

 but we also have to have it bequeable。And then periodically。

 it writes this data as parquet files into object storage。So。

Where we use data fusion here one way one place we use data fusion is we use it to sort and deduplicate the data before we write it as parquet files。

 so when when people are writing data into influxDB every individual row is basically identified by the tag set。

 which is like metadata that describes the set of like measurements。

And the timestamp right so you have the tag set and the timestamp and the whole thing is designed so that they can write the exact same data if there's some sort of failure in the middle they can post the exact same data again and they won't get duplicates right we'll de duplicateuplicate the data so they're not getting dus of everything So we do this on on persist so basically we do a scan sort dedoop and then we write it as parquet files and that's one of the important things is we do this sort and we we keep track of the sort within the catalog right so in the。

In one in the previous like。Bigger architecture slide。

 you can see there's this like catalog service So when we do the right into object storage。

After that， we update the catalog and we say， hey， we wrote this file for this table and it has this sort order and it has。

 we keep a couple of other bits of information like the min and the max time in the catalog so we can use that later when we're doing query planning。

So one of the other places we use data fusion in the ingeter specifically is using the pruning predicate for query processing right so I mentioned that。

One of the purposes of the ingester is to basically buffer data and memory so that it's queryable before it gets persisted to parquet files in object store。

So the query tier can ask the ingester like， hey I have this query。

 give me data for this table and we use the pruning predicates within data fusion to like prune partitions of data out from the ingess that we only send the relevant partitions of data back to the query。

So we look at the mini time， we look at the stats and send the relevant stuff back。So the the Ddo。

 so the compactor piece， so the goal of the compactor。

 I guess one of the things I didn't mention on the ingeter is。As data is ingested in。

 we actually create two copies of it basically because we want the ingestion ti to be like disconnected from each other。

 we don't want them to have to coordinate or anything like that。

 so we create two copies of the data and each ingeor is responsible for persisting the data to object storage so we create two copies and later the compactor will pick up those copies and pick up these set of files and rewrite them and deduplicate them into larger chunks of files so the compactor does this so it merges everything and deduplicates and writes it。

So we have a data fusion plan that does this like job。

 and we use the parquet rider to write it all out to object storage。

So obviously the queryier uses data fusion extensively， we use flightsQL。For the queries to come in。

 it does query planning， it immediately sends a request over to the ingestion here to say like hey。

 send me the data for for this query for this table and it asks the catalog service for。

The relevant partitions for this table based on the query based on the timestamps。

 timestamps are the only pieces that that get that get used to filter are used to filter data before things arrive into the actual like data fusion planning。

Section。Right so the execution plan runs， we also have a data cache in the query right because we in our use case like。

Most of the queries， the operational queries where they're querying very recent data。

 they don't want to have to wait or request to object storage to get a result back right because their expectation is。

That they're going to get a response in， you know， ideally sub00 milliseconds。

 but usually sub 200 milliseconds and。If that's your performance envelope like you've already blown your budget if you have to go out to object store or at least if it's not S3 express where do you do you。

Use the knowledge that it's a times series database in optimization in that flow in that you we currently see here。

What's that？because you have time series database， you have some optimization that you can do right。

Yeah， so we all of the data is basically ordered by time basically like each parquet file we have we keep the min and max time of the parquet file and we try what the compactor does ideally is it creates parquet files that are non overlapping in time right so basically the first thing that we do when a query comes in is we look at the time bound for the query and we eliminate all parquet files from consideration that don't match that time boundary and then we yield that to data fusion and it uses the metadata cache where the metadata cache is like the statistics for the parquet file right so we keep stats on every single column like the minm values and we let the data fusion。

Pier planner use that to do further pruning if it can。O对。Yeah。

 so I imagine lot of the queries especially the couple of dashboards like it'll be the exact same query you're seeing here like like it's it's just being pulled every say minute。

 for example， does data fusion or do you guys have their own custom like query plan cache that you rely on so that like you see the exact same string showing up you know need to execute it because you have new data but like you don't have to go through the whole planning process all over again。

 we don't right now but we definitely want to do that because that 100% happens like。

People have the same dashboard and the same query gets executed all the time and it's not just like one person it's common for like 10 people to have the exact same dashboard up So you get like that same query so many times the only tricky bit is like。

The time boundaries of the query change， obviously they're shifting constantly。

 so figuring out how to cash。Do intermediate caching is one of the problems that we want to solve。

 but it's not something we've gotten to right now all of our caching efforts are focused on。

Just the metadata for the parquet files and separately from the actual data data of the parquet files so because the S3 S3 calls cost you money so you obviously want to avoid those yeah it's honestly I don't I don't know that the cost of S3 gets has been a problem so much as like the time it takes like time to first bite it on S3 kind of sucks if。

The expectation is that your query is going to return in， you know。

100 milliseconds to 100 milliseconds。 So essentially like for that kind of system。

 even though object storage is the historical store。

 you have to design something where everything is either in memory everywhere or it's on a locally attached SSD that's super fast。

 but the problem is。Our execution environment is Kubernetes which is a total freaking nightmare to deal with disks。

 also cloud disks， cloud disk performance is just complete garbage or completely unreliable even for locally attached like SSDs MBmbmeE drives。

 I think there's been a number of posts recently that talk about like how bad。

MmbME drive performances in the cloud relative to what's available just in like commodity hardware right now so。

It's。It's not a problem that we have solved like right now essentially like we have to have things in RA。

 otherwise like our queries are too slow for the set of queries where people have that expectation like。

I would say there's kind of like。This bimodal workload distribution where there's this whole set of queries that people expect to be super。

 super fast and these other ones where they're like if it takes a second that's fine。

 but those are usually like。A lot less in terms of the number of queries that get executed right those are basically like ad hoc queries where they're like okay with it。

So and then another part of this I mean you're going talk this later like go back to the last slide like you're relying on aero flight SQL so that means that there's existing client drivers that you don't have to build that speak flight SQL you just rely on whereas in case of influx the previous versions did you have to maintain your own like programmingb language different libraries or different programming languages yourself because you had to write your own wire protocol Yes so yes we did。

 but I mean the thing is like before it was just HP and JSON which anybody and everybody can deal with so that actually like I'll just blow up my spot for like one of my conclusions at the end of the talk which is flight SQL I don't think is actually a usability win。

 particularly like for when we adopted it because。The libraries。

 the libraries in the different languages aren't that good for it and even if they are like there's a bunch of confusion in terms of how to use it like in my experience it's a better user experience for most people if you just say here's an HTBMpoint and it returns like JSON that looks like this and it's like JO lines then they could just deal with it and it's way easier for most people。

but yeah， that's like。I， I， I。I'm a believer in the dream of flightsQL。

 I just don't believe that it's been achieved。Because of that。The different levels of like。

Implementation across the different languages。U。So。

Partition and file pruning right so file pruning happens at two different levels。

 as I mentioned there's one which is basically before we get to data fusion where essentially we just use times to prune out whole swaths of data and then there's the actual pruning predicate logic and data fusion that we use because we have a thing where people can specify within a table like custom partitioning rules so they can say partition by this column with this many like partition buckets and whatever。

 and it can use we use the pruning predicate to prune out partitions which can actually be really good for our use cases where a lot of queries like they'll narrow down to like essentially like one time series or one essentially partition of data so if we have even 100 buckets of data we end up eliminating a lot through this process right so。

We evaluate the SQLs plan， we evaluate it using the partition information， the metadata cache。

 and then we only return the relevant stuff。So。One of the。

One of the other things we did in data fusion is we created like a custom SQL operator。

 so in this case。If you're doing like this time query and you want to have， you know。

 you're doing you're bining everything into like these different bins on the right hand side and you want a bin to occur for each block of time。

How do you express that in SQL right so there's no data points for that block of time so what you want to do is you want to fill in an empty block right so it would have no row with this timestamp so the trick is like how do you do that so we built a date bin gap fill function modeled after timescales time bucket gap fill but again like we had this in influx Db1 is a totally different thing but obviously that was in our own custom query engine so。

We use a custom data fusion operator and an optimizer pass to do this， right。

Here standard group I can't do it， so what we do is we do an optimizer rule to rewrite it to this where we put in the gap bill so you can scan filter group I and then the gap bill。

And you can see here that we actually have the custom stream operator， the gapill execec。

 to do that and actually inject empty records in。So。

So that's the that bit of like data fusion extension logic that we're using and the interesting thing is like so I don't when when did we create this piece I think the D in gap bill thing we'd created in like。

Early 2023， so essentially like。It's been interesting like it's because Andrews like， you know。

 on our team and he's the PMC for Data fusion  Ar， as we've developed the database along the way。

 we've had these different extension points where we're like oh。

 we need to add this piece in and usually what we've done is。

You know the upstream team that works in influx data that works on you know arrow and data fusion says like okay。

 what would we need as an extension point to be able to hook into the data fusion part where we can write custom code inside of influxDB to do that and in some cases we we do that custom code and then we keep it in other cases I'm trying to think of examples where we actually did that and then later that same functionality got mainlined into data fusion and then we had to update influxDb to use the now like。

The the data fusion native capability I can't think of a good example off the top of my head。

 but the thing is like we've been doing this now for like four years and data fusion has also like matured and developed along the way so there's a lot of stuff that we did early on that kind of just comes out of the box now with data fusion which is interesting。

So the。So influxqL as I mentioned like I showed this query earlier right so the from CPU and disk is not a cross join is basically just saying like I want data from this table and from this table but like put it all together group by time 10 seconds fill so it's doing gap bill interpolation。

So we wanted to be able to express this and essentially like when we started with 3。

0 we're like we're going to build it as a storage engine。

 we're going to have this SQL capability and we're going to use the GRPC。

API to have the other parts of the influxDb stack hook into this new storage engine right so that meant。

If you wanted influxQL or flux， you'd be doing those things， you'd be hitting a go processor。

 and then you'd be using the GP API to then hit the rust like engine。

And what we found was that grRPC API and that way of doing things was like like not performant at all it was like really really slow and essentially it became like a deal breaker for anybody who wanted to use influxQL or flux on this platform so at that point we realized we needed to figure out a way to bring influxQL in natively into like this new version of the database right so what we did was we said we'll create an influxqL front end on top of data fusion right so。

What that looks like is this right so we basically take with the influxQl text we built in rust in influxql parser which parses it into an Ast and then we translate that Ast into a data fusionological plan right so at that point then we're getting all the benefit of all the data fusion you know optimizations and you know functions and all that other stuff all we had to do is essentially build a parser and a thing that can translate the asT into logical plans which I think is。

Actually pretty cool so that when new optimizations and stuff land in data fusion。

 we just kind of get those on influxQL for free and essentially we have this like whole mountain of complexity that data fusion has that you know our frontend can sit on top of now unfortunately we were not able to do a flux front end for this because as I mentioned flux is like a scripting engine as well and it's like an interpreted scripting engine and like has all these functions and all this other stuff you know in my ideal scenario we would be able to build a flux front end on top of。

Data fusion， but the truth is like。There's just like we don't have the resources to do that and it would be incredibly like we could do something。

 but the problem is for anybody who's using flux。 they would want a bug for bug compatible version and delivering that is basically like a fools errand like it would just be way too hard to do So and the thing is like flux isn't so great where people are like。

 oh， you know banging down our door to be like I want to use flux to work with the database which I have a couple of thoughts on that later can you share probably like publicly percentage wise up for customers that like are using fluxQl versus。

😊，Bs versus whatever you're calling the new version of SQL here。So I mean。

 the thing is like we don't yet have an open source version of 3。

0 so the people using SQL are essentially only our commercial customers is on version 3。

 which you know we released the first versions last year so you know the bulk of our of our customer bases on version one and version two Amazon launched in March like a hosted version of version two and like they say like version two supports both influxQL and Fl and it sounds like what they've seen from you know the people who've talked to them that wanted them to run that service is they use influxQL for a lot of their basic query needs。

But they use flux because of tasks。 So tasks is a。Feature in version2 of influx to be open source and in our cloud platform where you can essentially like submit a bit of flux code that the database will run on a schedule inside the database and they use this for like。

 you know。Monitoring alerting for processing of the data for sending the data out to third party systems a variety of like things and what they found is that people are frequently using it for that。

 which I find surprising because again like。We heard from a lot of people that flux was a barrier to adopting 2。

0， but there are a lot of people who did adopt to 2。

0 and a number of them are using it specifically because of that， which。Yeah。

 is a bit surprising to me。There are other ways to do that same thing。

 but I think people liked the fact that it was fully integrated with the database。

 so it made it kind of like easier to get running。嗯。

So so there's one like time series specific optimization that I want to talk about that we built so basically like as I mentioned the。

The compactor outputs data in parquet files that are not overlapping in time and each one is sorted right so basically like。

If you want to if you want to execute this like you have to read the first batch from each stream before producing an output if you have like this limit 10 right but the thing is if each stream which is each parquet file is in time ordered basis like。

😡，Reading the first batch from every single parquet file for all of time it would be a complete waste of resources right so the idea here was to have an optimization that would basically do we call it progressive eval where it would evaluate like streams in time order and it wouldn't read from the stream until it was you know exhausted the first one right so it reads one then the other than the other and actually it reads。

Two streams at a time so that we minimize io stalls so that that was an interesting one。

 The fine thing is like when we were first talking about this one I had。You know， this is a new idea。

 obviously， like I had first encountered this idea from the elk stack back in like。

I must have been like 2014 or something like that Oh there's Elastic search。

 log stash and cabana and they had a thing where they created basically an index for each day of log data and the way the whole thing worked was like if you did a query。

 it wouldn't query every single index across time， it would do it。

In time order and then stop execution when you found the result you were looking for。

 so it's basically like same the same concept as that。

So as I mentioned a couple of times we released this as a managed service in 2023。

 I think so there's there are a number of things like so。

Some of these things might be obvious to people， but sometimes you just have to I don't know。

 make mistakes in real life and live through the pain to realize not to' touch a hot burner again。

 but there were because it was a complete rewrite there were a number of things that we like。

Didn't realize like we the thing is like all we all we were focused on at that time was like all the things that people were saying inlectB didn't do well right like we need infinite cardinality。

 we need cheaper storage we need all these other things we need SQL and we became so focused on like delivering those capabilities that we kind of like forgot what we did well in version1 and2 and it wasn't until we actually released version3 last year and started getting people using it and running it that we realized oh wait like these other capabilities are super super important right so。

As I mentioned， there are a couple of like kindss of queries where the query performance was absolutely critical and version one and two of the database would delivery query results in you know like sub 50 millisecond response times and people came to rely on those response times and basically。

I mean。We knew we knew like you know like the car brute forcing stuff wouldn't be as fast as like the heavily indexed method that we had before。

 but the thesis at the time was that you know like 3400 milliseconds response time isn't going to be a deal breaker and what we found is that there is actually like a tipping point where it becomes super。

 super important for for those people for our use case where like the difference between a 50 millisecond response time and say a 200 milliseconds response time is enough to essentially like get somebody to buy the database or not which is again like。

I just like wouldn't have expected that without like you know getting it out there in the world operational simplicity。

 version1 and version2 of open source had this completely right basically you could install the thing and be up and running in seconds it was super easy to use and operate with our version 3。

0 that we currently run like I showed you the architecture it's a very complicated thing and like we run it as a managed service but we don't have a way to you know deliver that easily on premise to people want it and at this point you know half of our business is still onprem so a lot of people want to run this database themselves even if it's not in their own data center they want to run it in their own cloud environment so getting to operational simplicity is important usability as well。

As I mentioned， I don't think LightSQL is really nearly as usable as a simple HB API with JSON。

 people find that much more， much easier to work with。

 and I do think that some influxQL had some real advantages in terms of a couple of things that made really easy。

So you can tell me like if I don't know if I can run over Andy E。Keep going at time， this is gold。

 keep going， okay。That you always talk about real stuff， it's good。Okay。

 so now I'm going to get into so I haven't actually talked publicly about this before。

 but essentially， you know we're obviously still working on the distributed version。

 the database and there's tons of things like we're still doing that I could talk about but I'm going to talk about this because this is what I've personallyve been focused on for a little while。

Wwhichch is the single server version of 3。0 which internally we're calling monolith and this is going to be you know available early next year and that will actually form the basis of there'll be an open source version and a commercial version。

 but the goals with like the single server version is we want it to be operationally simple so diskless as an option so that you can use only object storage or the whole thing you don't even have to have a locally attached disk or。

Use local disk but with no dependencies whatsoever right you don't have to run it as this complicated thing of services and whatever。

Last and the last value cache so basically within an individual time series saying like I want to keep the last end values in Ram and quickly available where the response time for an individual series or a group of series is under 10 milliseconds right that's the performance target metadata cache and index so this is。

It's specific to use cases that people have with us。

 which is like they want to build a UI where there's like a selector and you'd like you know select like some piece of metadata or they're in Grfana and they have a dashboard builder and they need they want the selectors to be super super fast so metadata cache and index sub 10 milliseconds response times is another target。

Single series queries optimizations where we actually don't have to do some massive bru or scan to return single series data with a target response time of 50 to 200 milliseconds at the most。

 depending on the length of time that you're going back。And an embedded Python virtual machine。

 which。In my mind like the so in version one of InflB we had a thing called capacitor which is a separate process with its own custom language that you could use to do processing and that project has actually been even though we had it in maintenance mode for God I don't know like seven years now or six years it has been surprisingly durable for our customers that use it we still support customers that use this project and they use it extensively with version one of our database but it has a custom language in version two there's tasks which is provides that same kind of functionality and again with a custom language so。

Our thesis is that you people actually don't want to learn a custom language。

 they want to use something they know， most people know Python and if they don't know Python。

 every LLM knows Python， so basically everybody in the world knows Python now so basically have it in the database so you can do on right in batches on parquet persists so you could like transform the data or send it somewhere else on a schedule like Chron or ad hoc which is like submit a query to the database with Python as part of it and have it executed。

And then this is in our commercial versions， but like HA and isolated query and virtual machine processors and stuff like that。

The a couple of things I wanted to highlight about the architecture of this thing so basically like here we have post a which has like wall a catalog and parquet files that sends off to object storage right so。

The way it works is you know as you can see from the the directory structure it has its own area so the design is essentially like host A owns this area and object storage under host A that only it can write to。

And it writes wall files， it writes catalog files， which is just Json snapshots of what data it has persisted in periodic intervals and then the parquet files themselves。

So the right path looks something like this。A client writes data first it checks that the data is valid right it validates it against the schema that has if it is then it buffers the right into in memoryory。

 you know holding pen and every second that buffer gets flushed as a file into object storage right this is configurable but by default it's once a second right so and then when it flushes it it puts it into an arrow buffer in memory so that it is queryable and a response is sent to the client。

Every 10 minutes the arrow buffer for every table is flushed into object storage as parquet files right so what that means is for clients that are writing data the average response time across all those rights is going to be 500 milliseconds we also have like an end point where you can write data and not wait for a wall persist you know confirmation which means you could have potentially data loss。

But this whole thing is designed so that essentially like every second wall file gets flushed right every 10 minutes all the data gets persisted and with that 10 minute persist the wall files that were flushed in that interval of time are purged right so at any given time and what we actually do is we shift this by a window because。

We want to ideally we want to write data into object storage that in parquet files that are non overlapping in time to begin with。

 so we keep in between five and 15 minutes。The wall files is basically。

5 to 15 minute window of time essentially so we flush 10 minutes of wall every you know every 10 minutes。

So that is that piece。Then the idea here is that you can have many。

 many of these servers writing data into object storage and ideally you can have other servers pick up that data right Any can read from this file structure。

 but only these individual servers can write to their so our compactor that we have in this architecture will pull the data。

Here we have like a query host which is pulling the data from the individual hosts。

 essentially it keeps an in memorymory catalog that is the union of the two catalogs from host A and host B and then you can query across data from both hosts and because it can actually pick up the wall files as they're persisted。

You can essentially query data， there is like TTBR time to be readable between like when it's written and when you can query it on the downstream host。

 but that's you know probably around the， you know anywhere from 200 600 milliseconds range。

 which for our use cases I think is mostly mostly okay。

So compaction I want to talk about this really quickly essentially like the way we look at compaction or the way we look at our data is you know we have this time advancing and we're persisting data in these 10 minute blocks and what we want compaction to do is we want it to combine these blocks into larger blocks and here i'm just showing like you know a factor or two combination down the down the tree we actually will have it will be much more aggressive about compacting older time blocks than this but so you can get a feel for it and the idea here is that when you're querying back in time。

You'll only have to query those individual blocks， right？😡，The goal here is。

Really like we want to reorganize the fiscal layout of the data。Right because。And if we're。

The naive way to do this is to have the parquet filess just land in object storage and you have one parquet file per 10 minute window of time and then if you want to run a query against it。

If you want to look back for a full day you're going to process against 144 files and if you want to do 30 days it's going to be 30 times 144 and whatever and eventually like it's going be a lot of files and a lot of data to churn through so our goal is to reorganize that data in ways so that it's optimized for how we expect people to query the data。

And we do this in basically each block of time we process row level deletes at the same time and we also write file indexes when we're doing this so I'll talk about that really quickly so the idea is you have this host which is pulling data from you know these two different hosts that are landing data and object storage it pulls it in it doesn't actually pull the walls in this case it only pulls the snapshots because it doesn't care about the walls it only cares about the parquet files that are persisted and then it writes compacted data in right so it writes one it writes its own catalog。

 which is a union of the two catalogs that it's compacting data from and it writes the different generation data and in a generation you see you have an index file and you have the individual parquet files right so this block here is a generation of data and within a generation you can have many。

 many part files so the idea is that as we get larger and larger blocks of time right。

We go 10 minutes into 20 minutes into hour four hours， 24 hours。

 five days at some point there's going to be some limit where we don't want to rewrite the data anymore because it'd be too expensive we're going to have to do a bunch of testing to see what that when that would be and how that looks。

And there's also probably going to be some sort of drop off in terms of like the actual performance gain we get out of it。

 but the idea is that within these larger blocks of time we'd have either many， many files or many。

 many row groups inside like larger files right and the point is that data within a generation is sorted by whatever your sort order defined right user can define the sort order so they say like oh I'm going to sort by region and then host and then time right so what that means is if you have 1 thousand0 part k files there。

The data for an individual host is only going to exist in one of those parquet files in that region right so our trick is basically how do we lay out the data so that it looks like that and it's an object storage and then how do we look it up very very quickly right so we have a file index that allows us to do that so。

Here， say we have you know Gene five， which is 24 hours worth of data and one way to do this would be like you said。

 these non overlapping blocks of time， right， T1， T2， T3， whatever。

We want to instead arrange it so that it's basically like this right it's it's the sword order and essentially what we want to be able to do is say we know that column A is in the sword order for this data and we want to create essentially an inverted index that says for each unique value of column a what files or row groups it maps to right so essentially what we're doing is the file index is an inverted index that maps unique column values into a posting list where that posting list either represents a specific row group or a specific file right now we're just doing files but there was over the summer data fusion actually had the capability added to it where you could。

Tell it to you can tell it the offsets for row groups for execution so basically it would know if you actually have like row group row group information for like the offsets in the files you can hand that to data fusion so that when it makes request to object storage or when it reads it from you know in Ram cache it will only read the ranges that it needs so。

We haven't taken advantage of that yet， but that's the plan and that capability was added because we had this intention。

 which is not there yet。So， so the last value cash this is。

I think this is kind of interesting I mean it's a really basic thing its basically like you know we want we want to have an inRAM structure of essentially like you know just a hash mapap where you can look up where the last value is for this series right we're using this is what the API looks like to like query it right so essentially you're selecting temp which is a column and time from last cache which is this function we give it the table name and we give it the cache name previously like we would have had created this we would have said like four table create this this last cache。

And keep whatever number of values and it does this for each individual series within that table and you can we can specify like。

What constitutes a series you can basically specify a set of columns right so you can say like oh keep the last value for that you've seen for each unique region or keep the last value that you've seen for each unique region and host and you can actually it's hierarchical so you could get last cash values based on either an individual series or based on that hierarchy so here you can see we're using a data fusion table provider and a data fusion table function implementation。

The the thing that like the reason why we wanted to do this is like this last cache thing versus just saying like oh well it's just SQL database you can just like create you know have the last cache thing in memory and you can just have a regular SQL query but the problem is like the semantics of this I think are very specific which is like this cache gets populated as you write data into the database and it doesn't right now at least it doesn't like fall back into some slow path query execution pathway if it doesn't find anything in the last cache it checks the last cache and then it returns back right which。

Is I think useful because like so。When you think about like people query the last value for something。

 what they could do is they could construct a SQL query where they say give me the last value for this。

 but only look back for the last like an hour right and basically because of the way data is organized in infl UB here。

 it would reinforce that period for the last hour and that's great and it could probably do that pretty quickly。

But the problem is in a lot of cases。R use cases people don't know whether or not an individual series has reported a value in that period of time right so what we've seen is we have users who say I want to be able to report the last value。

 but in a like 30 day look back window or a 90 day look back window and the thing is like actually computing that using。

Real like sQs like bru forcing that entire set of data because we don't know a priori what the actual individual series are like we need to keep a record of what the individual series are and what those values are so this is basically a way to do it so that we essentially can guarantee very。

 very fast response times as I mentioned like sub 10 milliseconds and。

We're going to have a similar thing with with the metadata cache。

 I don't have an example for this talk， but。We have it as a specific separate thing。

Because this is just kind of like my philosophy here on this， which is。

I don't want people to have to like construct the SQL query and like send it to the database and in some cases it's fast and in some cases it's slow but it's slow because it doesn't happen to have that index there I would rather have it just return no data so that they see that versus having to run and explain plan。

To be like or have it return an error right versus having the query take I don't know。

 five seconds and then being like， oh man this totally sucks。

 why is it slow Well now I have to run an explain plan to see what the hell is going on and again like so many of our users don't have I mean they don't have the knowledge to to do that playing people do and that's fine。

 but like one of the things we're trying to optimize for is like。あ。

Like user expectations right like so they can do something in they either it works or it doesn't。

 but if it works it's always going to be fast。嗯。So okay we're rounding we're rounding your home plate here or third base or whatever。

 so some I think some things which may be hot picks on the FD stack I don't know this I already mentioned flight I don't think is actually a win for usability I think for our users most of the time like it's just easier for them if you have an HM point the returns like JSson lines。

 it's like super easy for everybody to work with。The the implementations and all the different languages of flight have varying degrees of。

User friendliness and capabilities and stuff like that。

 So we haven't found flight to be a big win for usability Now it is a win for performance。

 but in our use cases， people generally aren't pulling back millions of records for a query they're actually like they want the database to process million millions of records and they want the result to be more like00 records and you don't need the performance that flight gives you to serialize 10 records of data。

AK standard like SQL standard。Its so we use nanosecond timestamps in parquet which I don't I still don't think Databricks can actually read so our parquet files are not necessarily readable by a variety of thirdpart systems which is ultimately one of the reasons why we adopted parquet is because we wanted people to be able to just take those files and read them anywhere they want and we're not using a bunch of crazy parquet things。

 but they're just a couple of points where it's seen we haven't quite gotten the wind that we would have hoped for I mean it's improving over time but it's it's not there。

 but would I would say for anybody who's using parquet in their system because they're hoping for a lot of like you know interoperability with thirdpart systems like you have to really look for like the lowest common denominator of parquet functionality and only support that if that's your goal。

😊，Arrows memory hungry， thats probably obvious， but if you're working on systems where you know you can get。

Much more efficient representations and compressed formats and executing against a compressed data directly and all this other stuff likeductDB and a variety of things do like can they can do optimizations that' obviously that you can't yet do an arrow。

So Andrew calls Data fusion LLVM， but for databases。

I also say I wanted to say that data fusion is visual basic for databases。

 so this I'm dating myself here visual basic is a programming environment that Microsoft created in the 90s to create Windows applications and there was this absolute explosion of you know boring corporate application like just internal applications that companies built all over the place for Windows for you small groups of users and stuff like that。

 but it basically made an entire group of people， programmers that never otherwise would have been programmers right because it was easy to create a Windows application that had a database in it you know with visual basic。

😊，And my my thesis here is that data fusion is like this but for databases right so you know it used to be that you need to you know go to the high priests of databases like Andy or Stonebreaker a few wants to like get something created for you。

 but I do think you know Andrew has his goal of like1 thousand projects using data fusion and that may already be the case。

 but I have a complete confidence that that will be the case if it's not already and there will be much more than that and basically be this like。

Explosion of database projects and data systems and stuff like that that data fusion will enable because。

People can use data fusion without actually having to understand how do I actually create the really complex inner machinery of a database and。

The thing I think that is really exciting is I believe that data fusion enables innovation at the edges。

 right when we created influx B1 and then version two， we created our own languages。

 we created our own create planner our optimize our process our execution engine， blah blah， blah。

And the thing is like because we did those things， it meant that we didn't have a SQL engine right it meant that we had to make a case for people using influxDB。

 even though it didn't have the you know familiar functionality and you decades of database work that came before it and the nice thing about data fusion is if you adopted it。

You know you're going to get SQL for free and you can actually come up with ideas for new language stuff and you could create that and put that in your project but still have SQL capabilities and still have this fully functional engine and you know for the people who want to try your new language great they can and they have this easy escape hatch to use SQL and I think it's also the same at the persistence layer I think you know right now parquet is obviously the file format that's being you know adopted broadly in OLAP systems but obviously like I think there's room for。

Innovation for specific workloads and specific use cases for different file formats and the thing is like you could do that and have a custom table provider for that file format。

 but still have know the data fusion table providers for parquet， JSON CSV， whatever。

 and you just kind of get that out of the box， which I think is really great。So this is my。

My closing thoughts on basically finding an edge in databases， yeah。

 if you're you know if you're addicted to pain in you're masochist and you want to create a database of some kind I would say consider the workload in use cases it's really。

 really hard to create a general purpose database that does anything interesting for people whereas it's much easier if you think about very specific things for the problem you're trying to tackle how does the data arrive。

 how will it be queried and the difference is usually the way it's queried is different than the way it's arrived than it arrives and that becomes an opportunity for you to do interesting things and basically really how can you provide one or more of you performance win for a specific workload where people think it's important enough to pay for and adopt a new system a reduction in cost that is significant。

Operational simplicity， right at this point。Most of the time when people look at operational simplicity。

That's enabled through like oh， we we have it as a cloud service right。

 but a lot of people don't want to adopt a cloud service。

 They actually want to run the software themselves。 So I think there is。

There's interesting opportunities for databases that people run themselves that are targeted at operational simplicity。

And then really you know I think the biggest thing is an increase in developer productivity can people build an application for whatever this use case is in less time with less configuration with less headache faster with your solution they can with others and this is。

These are all things that we're thinking about at infl as we're trying to build these new versions of 3。

0 and continue to improve the existing version of 3。

0 that we have so ultimately I think the bar is incredibly high for all of these things and you need to have significant improvement to justify getting people to use your solution。



![](img/43d41d11438ff8a292e69a5017bd8cfd_3.png)

That is all I have。🎼你。