# SRE大会-2025-美洲-｜-srecon-｜-分布式-｜-缓存-｜-OpenTelemetry-｜-安全-｜-AIOps-p08-P08-Live,-Laugh,-Log--BV1TmLDz7EZZ_p8-

。

![](img/9c9a219dba5f4a654a350727e0199c47_1.png)

![](img/9c9a219dba5f4a654a350727e0199c47_2.png)

Hello。Hello SR E Khan， I am so happy to be here in community with fellow reliability nerds。

 I'm also loving all this California sunshine。 I am from Portland and we dearly。

 dearly do not have the sun and I'm very much soaking it up。😊，Welcome to Live， laugh， Lo。

We're going to start with story time really quick。 This is me as a young software engineer。

 I've just transferred onto my second team。 I am a few months into the role of software engineering。

😊，And part of the onboarding protocol for this team was on day one that you have pushed and merged your first PR。

So that meant I had my onboarding buddy， I was given some trivial little ticket。

 something easy bite sized to tackle and fired up one of our services locally。Now。

I was greeted with my terminal screen full of short log messages that were super helpful containing little tidbits about what the startup process was doing。

 And I really learned a lot about this service from the logs that I was putting at。😊。

And that is when I fell in love with logs。Except that's not actually what happened at all。

 was it that was the opposite of what happened because instead I was subjected to a parade。

 I believe this was Kolin quite verbose logs， some of them inscrutable。

 some of them had somewhat alarming messages about packages we were using that were deprecated packages that were about to be deprecated and yes sure。

 there probably was information about the startup process。

 but I couldn't find it amidst all that chaos。So I turned to my onboarding buddy and said， well。

 forget this ticket， right， Like， clearly， we've got some other work that's more important to do。

And he said， oh， those logs， that's just normal， except it。And so with a nod to the title live Lalo。

 There's a few different laughs that I went through in my mind。 The first was a bit incredulous。

 The second was。😊，Oh， really， I got to get used to this。

 just ignoring things that sound pretty scary。And I was pretty nervous about what the future held for me and understanding our system。

 if this was the type of data that I had to work with。Now。

 I was on a team that was building out tracing features to support distributed traces。

 And so I was very early in my career introduced to the beautiful。

 rich structured data type that is a distributed trace。 and I。

 as a young naive page said to too many people that are very smart that I highly respect logs are just totally gonna be over。

 We have traces。 Why would we use logs。 And I meant it。

 I really did mean that for the record since we're recording。 I can admit。😊。

That was not the right take。 Pretty uninformed。 I was only a few months into my career。 Yeah。

 and since then， I've matured， and I have really come to respect each type of telemetry's place。

 whether you use melt， temple， whatever acronym， Each of them plays an important role。

 and all together， they help you understand your systems。😊。

So there's three things that I've come to discover about logs。Logs today， they're everywhere。

 They are ubiquitous。 Almost every component in your stack is going to emit logs。

Why it's one of the oldest signals that actually totally predates computers。

 If you have not caught Alex Hialgo's logs are good， actually talk from Monama。

He winds through the history of logs。 and the little tidbit I'll leave you with as that rope there was one of the first log lines。

 That is how long we have had logs as humans。Now， what's tricky about having so many different components emitting their own logs is we didn't all really agree on a standard format or structure or protocol for sending those logs。

 So we've got a variety of sources， some of which we control like the applications we write。

 some of which we don't， which are like thirdpart apps that we're bringing in。

So it's a little bit challenging to get a cohesive。

 consistent and structured view so that we can actually use these logs for understanding。Now。

 the second thing that I learned that logs are growing。

 And I will say this is a little bit of a small survey，1 27 folks that my company did。

 But what we found was。😊，For all these different types of organizations。

 their log volume was growing 250% year over year。 That's wild。 That is a lot of logs。

 more and more logs all of the time。😊，Now， some organizations address this。

 and I think pretty drastic in extreme terms。And that is slashing retention and putting all of those logs as quick as possible into cold storage。

 which is very cumbersome to try to access and rehydrate and query。

 And so you have developers working with like four days of production long data。 Good luck。

 troubleshooting anything that's an intermittent issue。

 something that shows up over a longer period of time。

 That makes me pretty sad that that is the reality some of our developers are living with today。

Partially because it is costly to generate these logs， to send them， egress them out。

 costly to store them if you're paying a vendor， costly to store them if you're self hosting。

 So I understand why people go to slashing retention。 I just don't think that it is helping anything。

Okay，The last thing I learned about logs is that they've really varied uses and applications。

 lots of different roles rely on logs like us and SreE， our software developer friends。

 customer and tech support， as well as security for detecting threats and intrusions。

 So we have all of these different roles who have slightly different perspectives。

 needs and motivations to interact with logs。😊，They sometimes need different tools。

 so the three things that we're kind of contending with everything emits logs。

 we're only emitting more and more logs， it's almost inherent to cloud native architectures that we're building。

 like just Kubernetes alone emits so many logs and we have multiple people with multiple uses that need those same logs to go to different places。

 sometimes with slight transformations。So it's kind of a perfect storm。And I'll say。

 just as a side note， I will never forget the time I was investigating an issue。

I had hit a dead end with the application logs and thought， okay。

 I'll look at the proxy logs that was sitting in front of the application。

Looking everywhere in our observability vendor。 I'm querying。 I had admin access。

 I could see everything， could not find the proxy logs knew they existed。

 finally asked in the team slack， and they go， oh。Those are in our elks stackack。I'm like， excuse me。

 I've been here like six months now， Did not know we were running our own El Zac。

 Also didn't know we were putting all our infrar logs there。 like， whoa we。Logs are mess。

 They are not a beautiful。 They are not as beautiful as traces， but they do have value。

 And that's what we're here to talk about today。 How you can make sure your logs reliably get from ABC to D。

 E， F，G， H， all the way to Z。😊，Also， in the most performant way possible。

 so we're respecting our use of resources。So this is where fluent bit comes into the picture。

 this is the sibling project of fluluent D， if you are a fan of or have used fluent D in the past。

And this is the technology we'll be focusing on today。 However， quick side note。

 It's called Live La Lo。 That was a very catchy title。 I have to admit。

 but I do want you to know that fluent bit handles more than logs。

 It also handles metrics and coming soon with every new release。

 We are building more and more support for traces。 So if you are interested in using fluent bit for traces。

 Come talk to me afterwards because I would love to pick your brain。😊，确。

What are we going talk about today， Quick agenda slide。 We're going to do high level viewluent bit。

 We're going to look at the life of a cloud native log。

And then I'm going to show some configuration options and features you may not know about fluent bit that will really help you make it reliable and performant。

 Of course， we're going to talk about meta monitoring。

 what telemetry fluident bit emits about its own processing。

 some diagnostic tools and ways that you can connect with the community。😊，确。

So we are in our 10th year celebrating 10 years of fluent bit， and I think it's fair to ask。

 what exactly is fluent bit。😊，Because if you look across our various docs， web pages， tutorials。

 my team writes， you will find fluent that referred to many， many different names。

 observability pipeline， Telemetry pipeline， data processor and forwarder， Telemetry agent。

 And I have also heard logging agent and logging pipeline in the wild。Why so many names。

 old fluent bit is quite flexible。 It can be deployed in different roles and， of course。

 started out supporting logs first。 So there's a lot of。

Maybe overcoming the what food but is known for with logs and saying， hey。

 telemetry agent observability pipeline， we do more than logs。

 So that's where some of those name changes are coming from。

I think it's always helpful to clarify terms in observability we just。

We do not make it easy for anyone to keep up with that space。 So back to what is fluent bit。

 My favorite definition as of this recording is that fluent bit enables you to collect event data。

 Yes， this is another term for log from any source。

 enrich it with filters and send to any destination。 It is an open pipeline。

 We support lots of different inputs and lots of different outputs。😊。

An event just side note is what fluent bit refers to the data that it brings in。

But you can just kind of substitute log for the rest of this talk。

This is like a high level overview of what affluent bit pipeline phases look like。

 We've got data sources sending data into the inputs。 We've got parsing， We filter buffer。

 buffering is happening throughout， but it just looked better fit better over there。

 and then routing to our outputs。So let's look at this a little bit closer in life of a cloud native log。

And before we go into the details， the three different modes or ways that you can deploy fluent bit typically are as an agent。

 so you can see here， perhaps you can see here have if we're running Kubernetes。

 we have our application container in a pod， you can run fluent bit as a logging agent inside of that pod where it'll be responsible for gathering that application containers logs processing and sending to wherever you're hurt or business desires。

Then we've also got agent mode。 If you are running fluent bit as a Da set across all your nodes。

 it can also collect like CPU and host metrics。 It can collect logs from all of the app containers for the pods running there。

 as well as collect Kubernetes worker components like Kubt logs， very powerful。 and then， of course。

 have it to all of these lovely destinations。😊，And then the last kind of main mode that it's deployed in is as a collector。

 aggregator， forwarder， whatever you want to call that central fluent bit that's responsible for taking in logs from multiple different。

Applications， multiple different servers， multiple different nodes。

 you can have tiers of fluent bit sending data to each other。 there's a lot that you can do。

 but this is the basics。Here we go。 Life of a log。We're going to imagine flu bits running as a da set in our imaginary Kubernetes cluster。

And we're gonna to imagine that a particular node we're looking at is running a pod with engine X that's handling web requests。

And our journey begins when someone makes a request。

 En X responds and the container logs to standard out that stream。 This is what it might look like。

 It is a typical Nng X logs while it is not necessarily superstructured。

There's still a lot of helpful information about the request， the status， bodyby scent。

 so on and so forth。Now， the second thing that happens is the container runtime。

 whatever you are using CRIO or container D is going to redirect standard out to a file。

 but not before it converts that application log or that containers log into the CRI logging format I actually thought it was pretty interesting that the first log transformation happens before fluent bit and what this logging format is in a nutshell。

 it adds in a timestamp it has what stream it has picked up this log from。

 and then it's called a flag for completion。It is gonna be P。 P is I am one of many logs。

 I'm a multiline log。 I'm just one one of the first few。 And then F is I'm the final。

 I the final log of a multiline log， Or I'm just a solo dolo log， treat me as I am。

So this kind of gets converted into C I logging format and written to a file。Okay， then fluent bit。

 If you're going to use the fluent bit operator or kind of the standard out of the box deployment methods。

 it is going to be set up with the tail input plugin。 that is going to tail the file。

 kind of a familiar command for some of us。And the important part to know is that you are going to specify the path。

 We're looking at everything that's in v log containers for that node。

 and we're setting a multilined parsor， both Docker and then CRI。嗯。Go。

Next stage we go to is fluluent bit needs to parse that。

 So this is our second transformation that's going to happen。 It's not one that we've decided。

 but it's one that the system's doing。 Fluent bit needs to create its own internal representation of a piece of data it's going to work on。

And so it turns it into the fluent bit event format， which is a timestamp。

 a different timestamp than CRI。 It is Uniix epoch secondsconds nanoseconds。 Then we've got metadata。

 Now， you can kind of get confused and think， okay， well。

 isn't metadata kind of in the body of the message like of our law like is there not metadata there。

 Yes， but this metadata isn't for you。 It is forluent bit to understand how to handle this record or event。

 whether it's a metric， a log， a spam， and some helpful things about the time that it came in。😊，Okay。

 and if we look at the log at this point， we still just have this sort of like naked N X log。

 We actually could not tell what applications sent it， what instance of what application sent it。

 what namespace it was running， a pod I D， anything that would help us narrow down if this was a particularly pesky request we needed to follow up on nothing would actually at this point help us figure that out or narrow down the scope。

Which is why oh。This one always gets me okay， side note on parsing。 It is not magic。 It is just rex。

 I went on a really fun rabbit hole answering what is the life of a log to my own satisfaction。

 way more slides than I'm presenting here。 And one of the things I discovered is the built-in parsers do com。

 Oh my gosh， it's just a rex。 And we give you this helpful rubular do com。

 So you can test out some different log lines。 make sure that rexx is gonna to work for you。😊。

And now， now that brings us to the most powerful and exciting part of fluent bit， which is filters。😊。

This is going be the last kind of built in piece of a fluent bit pipeline for Kubernetes logs。

 and it is the Kubernetes filter， which is going to fetch all that metadata that we wanted。

 that makes this log more actionable because we can understand who sent it specifically who sent it where they were。

 And so that will call out to the Kubernetes API。 If this has already been running for a while。

 it'll have cache some of those values。 So it it'll grab some stuff from the cache。

 And then it will add it to that log message。 does not add it to the metadata metadata for fluent bit。

 This is metadata for us humans， it gets appended to the log。I'm not going to read all of this。

 but these are the typical suspects， pod name， namespace name， pod I D， labels， host。

 that sort of thing。Now， from here， the sky is the limit when it comes to further processing。

 There's a rich set of already existing plugins that can help you transform this data。

 Maybe we're like， oh， don't need that Docker I。 Let's drop that sucker。 you can totally。

 totally do that。 you can mask or remove PI from the logs。

 and almost anything is possible if you can't make it work with the built in plugins。

 you can customize with Lewiscr Wam。 go， you can customize inputs and outputs。

 and I don't know if I can say what's coming next， but stay tuned for the for launchun at cubeubecon next week。

 There is another exciting way to customize fluent bit coming soon。😊，And from here。

 Fluent bit is going to route and send the events。 and yes。

 this is a little bit hand waving about the last part of the data。

 but we're going to talk a lot about what happens when Fluent bit is ready to send these log messages out later。

And so that's where we're going to end the life of a log for today。 Obviously。

 the log life will continue as it gets ingested to different destinations， stored， indexed， queried。

 charted， graft， alert， analyzed。 there are many， there's a rich life after a fluent bit。

 but for our purposes， this is going to suffice。😊，Okay。That's a happy path。

 That was everybody doing its job。 We had enough resources。 Things were moving along。

 but this is S R E Con。 We know that doesn't always happen。 You can't count on the happy path。

 So what， what could go wrong with fluent bits in sending these logs。

 I have come up with the four dreadful Ds。 The first is dropped。😊，Obviously。

 we've covered why logs are so important。 So we really want to make sure they get out of our system and to their destination。

 So if we drop or lose logs， that's going to be pretty impactful to us。

 I'd say that's kind of the worst case scenario。The second thing that can happen is that logs can be delayed。

 Now， if you're using logs for alerting， maybe you're turning a log into a metric and alerting on that or alerting on some certain keys or fields that you see in a log。

When that log is delayed， that can actually cause problems and cause you to draw incorrect conclusions about what's happening。

So if you have anywhere near real time requirements or super low latency。

 delayed logs can actually be maybe your biggest problem。Logs can be duplicated。

 We'll talk about how fluent bit manages batches of logs or records called chunks。

 And the chunk is the unit of operation。 It is the pod of fluent bit， if you will。

 And that means when it has a problem sending。 if only one of those records fails to be successfully ingested by an output。

 Fluent bit is going to retry that entire chunk。 So depending on how your destination is handled。

 getting duplicate data， that could cause a lot of problems for you downstream。😊。

And the final one is distorted。 Your logs could get distorted。

 We looked at that beautiful Rajax in the parsers dot com。

 We know that you can write your own custom parsers。

 but sometimes things happen and log formats change and the parser didn't keep up。

 Maybe some non Json somehow got snuck in there。 But whatever the case is。

Sometimes logs can go through fluent bit and not actually end up being nicely structured or understandable。

 They can not。 They could look like not what like you expect。Okay。So。

What can cause situations that result in those horrible things that we do not want to happen to our lovely。

 cherished logs。A big culprit is something called back pressure。

 This can come from a variety of sources， like having too few resources， not enough memory。

 not enough CPU， not enough bandwidth。It can come from data sources sending way too much logs。

 like overwhelming the ingestion。It can come from processing bottlenecks。

 Maybe you went a little filter mad， and you have 20 filters chained in a row。 They run sequentially。

 that can cause congestion right in the middle of your pipeline。 And finally。

 at the end of our pipeline， we could experience delivery issues。 And if we cannot。

 if we're going to continue to retry to retry， sending logs to somewhere they didn't end up getting successfully。

 we're not only going to have to hold the logs， we're trying to retry。

 But we're also going to have to continue to hold the logs that are coming in and being actively processed。

 So backcrer is a big problem。Great， so we covered the life of a log。

 We've covered the horrible things we do not want to happen to our logs。

 And now I'm going to share what you can do about it with some configuration options。

 both to improve the reliability of fluid bit， as well as to make it more performant to great things。

😊，And I'll just say for basic scenarios， when you're getting started。

 the default setting per fluent bit will work。As。To really ringring the most performance out of fluent bit。

 And like we showed before with the Swiss Army knife， it can do so many different things。

 It can operate on Io T devices on the edge， can run on your beefy Kubernetes clusters。

 Let's not rely on the defaults。 I'd say double check and really understand your data your context in your system and then use that to tailor fluent bit to be exactly what your system needs。

😊，So I can't directly do that for you， so today I'm going to share the tools and features at your disposal。

Okay， the first is dry run。 We're gonna start pretty simple here。

 Dr run is a command that will partially validate your fluent bit configuration。

 If your fluent bit configuration file is got some bad syntax or something。

 Fent bit's not gonna start。 It's going be in a crash loop。 No one's gonna be happy。

 So you can run this very simple command as a git hook like C or PR check。

 dash dash dry run and it will let you know the configuration test was successful or not， I mean。

 I don't know your config， but like let's assume that it is successful。😊，And if you're like， pay。

 you said partially validate， like， why can't just do all of it， What's the point？ Well。

 if your status quo is doing zero config checks， I'm pretty sure partial validation is gonna to be like a big step up。

 It's very quick， very cheap to run。 Just do it。Okay。

Then we're going to talk about validating our custom parsing。If it's。

 if you're dealing with logs that are maybe coming from like an arcane system or like a third party component。

 you don't control that emits its own wacky log formats， you are going need to write your own redex。

 fun， not my idea， fun， but somebody's。We influence bit， use rubular。

 which is just this very nice simple website that lets you drop in some test strings。

 maybe you copy paste some logs from your system， don't copy paste them with PII。

 just get like staging logs or something， pop them in there， hack on your reexx。

 make sure that everything's matching as you expect before you deploy this in production。So rubular。

 we highly， highly recommend。I think my favorite part about config validation。

 or I guess data processing validation comes from the expect plugin。

 It is literally a test that you or a plugin that you can drop in between every stage of the pipeline from parsing to filtering to the other filter that you wanted to processing and the outputs to make sure that the data transformations you expect are actually happening。

 This is very helpful if you are tweaking flu bit confi。 you're tweaking data pipelines。

 You really want to make sure that everything is all buttoned up before taking mat to production。

 And that is what the expect plugin is for。 do not run it in production。

 run it in one of your like CI pipelines， run it locally。 use the expect plugin。😊，Cool。

So those were all tools for proactively validating your setup before we're taking fluent bit to production。

 Now， we're going to examine options with buffering。So。From our Kubernetes life of a log example。

 we were using the tail input。 The tail input has some special config options I wanted to highlight。

 because likely， folks are running Kubernetes here。

 So you can configure the chunk size because we can also configure the max size。

 The max size of the buffer is going to be the largest file that you could that could be read into fluent bit。

 It is by default，32 k。😊，We will get to it on another slide。 I do yes。

32 kiloB And if you have super chatty logs， if you have those cotlin logs like I had a while ago。

 you might want to bump up that max size so that fluent bit can be efficiently ingesting your data。

 You can also set the size of the chunk that is going to be the batch size of how many records or how much memory the records will take that flu bit can operate on across the pipeline。

You can set the offset key， this will actually put the offset of where fluid bit was last in the file when it ingested that log into the log record itself。

 very helpful for troubleshooting。And finally， some other tail input things you should be aware of is skip long lines。

 If you do not have skip long lines turned on。 and fluent bit encounters a log line that is larger than the chunk size that it's configured with。

 It is not gonna be happy。 It is actually gonna prevent some other logs from getting through。

 So if you turn on skip long lines。 Fent bit is gonna say， oh， that's too long of a line for me。 No。

 thank you， Sir， moving on to the next。 And it will be able to continue ingesting logs。

 which is what we want。 I mean， ideally， we'd want that long log line in there。

 but we don't want one or two errant log lines to hold up the whole queue。😊，And finally。

 the database setting， which is where it'll be just a little file that will track the offsets in the files that Simpet is tailing and monitoring。

And it is backed by SQL light 3。 So especially for。Running in Kubernetes。

 you're going to want to tune these the chunk size and the max size for your system in your logs。

 different text stacks， different languages have varying levels of verbosity。

 And so make sure that your fluluent bit can be pretty performant at the ingestion part。Now。

 if you're not using the tail input plugin， but one of the many other plugins is worth mentioning the way that two ways that you can。

Speed up or make sure that fluentbit's reliable at ingestion。

 And it really comes down to the memory buffer limit。

 This sets a limit for how much data can be processed by a particular input plugin。

 These are scope to particular input plugins because Fent bit could be gathering from many different sources。

 So it's very helpful。Now， this addresses only the in memory buffering that fluent bit is doing。

So when it reaches this configured limit， fluent bit is going to pause and say， up， no more。

 no more logs are getting in until I have freed up some more memory。

 And that trade off means you're gonna to need to understand how your instrumentation SDKs or those sources are going to handle。

 are they going to retry。 How often that's a interaction that I leave as an exercise to you。

 De audience。But you may be thinking in memory， a little risky。

 Don't we want to store that somewhere safe。 What if we lose our place and we have a ungraceful termination。

 Are we going have duplicate logs if I just start tailing the file again。 Yeah。

 so that is why we also offer file system buffering。😊，What I want to highlight here。

 you can read the docs for the full details。 But what's most important for you to configure is storage max chunks up。

 up refers to chunks that are held in memory down， refers to chunks that are stored in the file system。

 and they also can be busy， which means I'm a chunk that's being processed。 You know。

 you can't let me just be processed。 I'll deal with you when I'm done。

So this says what the limit is in memory for how much。

 how much in memory how much memory for the inmeory buffer you're allocating when it hits that limit fluent bit is not going to pause ingestion。

 it is going to start routing those incoming logs to this file and pick up and read from them when the memory is freed up。

 that is a lot more robust in something that we recommend。Great。

 we're moving along the pipeline phases。When we get to the end of our pipeline。

 what are our controls for making sure data can flow through。Ultimately。

 it comes down to the throttle filter， which lets you control the rate at which log events are sent to destinations。

 It is a pretty straightforward config。 And this is very good for times。

 It is defining the number of events per period and it tracks the number of events being released and a minimum interval in between。

 And again， this is going to require you to understand how your destinations。

 what they can handle in terms of throughput of data and kind of fine tune per output how you would throttle。

All right。Finally， not finally， there's a lot more。

 There's a scheduler which coordinates data ingestion from the input plugins。

 and it's gonna to flush data at a fixed number of seconds。

 And when we're sending this data out to destinations， the responses we can give back are okay。

 Everything's good。 retry or unrecoverable error slash we ran， we exhausted or retry attempts。😊。

The retryries， again， not as straightforward， which is why I recommend you check out the docs page。

 If you're not familiar with exponential backoff in jitter。

 There are some very helpful couple scenarios that they walk you through flu bit config and how it would result in what amount of retries are sent in out what time。

 But the things you the three things to know the cap， the base and the retry limit。

 the retry limit is the max number of attempts to retry that you've got。

 and the cap in the base are going to be your range for that weight time in T。Okay。

So we've learned a little bit about buffering and making fluent bit reliable。

 Let's talk about performance。The biggest bang for your buck here is going to be multi threadreading。

 This is a diagram showing fluent bit。 It's got one main event loop that runs in the main thread。

 When you turn on multithreading that affects the inputs who will get run in their own self containedtained threads。

 as well as any processors， and the outputs actually are configured with the number of workers that will be allowed to。

Distribute the tasks that you can distribute the tasks among。Oh， and it's important to note here。

 if your destination expects exact temporal ordering of logs。

 you're not going to have a good time with multi threading your outputs because we cannot guarantee that they are going get there in order。

 So something to consider。So I mentioned processors。

 and you may be thinking page that was totally not on that pipeline phase diagram。

 You showed me what the heck。 Well， that's because processors are a little bit new， and they're not。

They are their own thing， but they're attached to an input plugin。

 So what processors solve is if you need to do a lot of complex data transformations。

 like maybe you need all five of these filters because those run sequentially。

 that risks becoming a source of contention。 And so processors are just the data transformation logic that can be attached to the input plugin。

The difference between a filter and a processor， filters are also used for data routing。

 So whatever that tag is in that metadata， the metadata fluent bit cares about。

 it uses that to decide what output plugins a particular record or chunk should go to。

 Proors don't do that。 But they， they do show up at the beginning of the pipeline。And finally。

 stream processing， which is totally its own talk。 So the high level things are it lets you query data。

 a continuous data stream as it's coming in， lets you manipulate things。

 It is a streaming SQL engine。 We love SQL so friendly。

 And this is a little diagram that shows you can grab that the stream processor processor can actually also put data back into the inputs as you're going。

😊，Helpful for real time and complex analysis needs to be able to process data while still in motion。

Okay。Metta monitoringitor。This is fluent bit。 The Teleary fluid bit is going to admitm about what it's doing with all of your logs or traces or metrics。

 There are a lot of things that you've got at your disposal。 But first。

 please take a moment to admire this beautiful buffer overflow。 So many， so many slashes。

 This I caused inadvertently on a local Kubernetes cluster where I said， hey， fluent bit。

 just grab all the logs that are in the default namespace。 Oh。

 that's the namespace you're running in every time I make a request。

 You're like going in this infinite loop of logging and logging and logging and logging that request。

 and it made this beautiful art。 that I had to share。😊，Okay。Oh，10 minutes。

The F cut docs have a very long， comprehensive table of the metrics that it emits。

 It emits them in the Prometheus format。 I based on the questions that I see get asked in our Slack channel。

 I think people struggle to。Fill the gap between what this metric does in its description and the types of questions that we can ask about fluent bit and what we can learn about it based on these metrics。

 And especially if you just like pull up the community Grfaa dashboard， you're like， whoa。

 this is a lot。 This is overwhelming。 So I broke down a few of the high level metrics that are important。

 And based on the questions that you can ask how many seconds has it been running， When did it start。

 How many hot reload， super helpful if there was a。😊，A hot reload。

 and then a bunch of ingestion issues。 The hot reload might help you there。

And for each major phase of your data flow， from input to filter to routing an output。

You can ask basically two camps of questions。 We're going go through these next slides a little bit quick because I think you can get to the docs page。

 But really the questions or what the metrics measure are how many records， How many chunks。

 How many bytes of memory are they taking up through for the inputs for the filters and for the outputs。

Okay。And then， of course， we've also got a lot of metrics about storage， what chunks are up。

 what chunks are down， what chunks are busy， how many connections are there per output plug。

 how many of those connections are busy， Lots and lots of wonderful questions that you can ask fluent bit about itself。

And a small note on fluent bits own logs。 you are going need to handle those。

 We saw fluent bit cannot handle its own logs。 And I really wanted to call out that the metrics are going be the most reliable source for you to find out if data is dropped。

 That is because each retry attempt， it's going to have this little warning message that says， oh。

 we failed。 And if you are just counting the failures based on the error logs you see。

 And you don't follow the story all the way to the end of either an ultimate failure。 or， hey。

 actually， that fourth time， we were able to send that log out。

 you could be getting some like false positives there。Okay。3 diagnostic tools。Health check。

 you have to configure this。 It is based on the number of errors that you are going allow errors sending to destinations。

 And it is also going to count on how many retriries you're going to allow。We'll go to D internal。

 This is sending a Sig cont to the pit of fluent bit。

 And it gives you this really beautiful report that I could not fit on one slide or on one row。

 And it goes for each input plug。 whether it was over the limit talks about the status of the tasks。

 the status of the chunks， as well as the storage layer。 This is very。

 very helpful for figuring out what could be going wrong and where or how busy you're asking fluent bit to be。

😊，And finally， tap， which is like tracing。 It is the life of a log as it gets traced through all of the different phases inluent bit。

 It is also quite verbose。 This is just one example showing a start and stop time。

 It's basically like a span， but it's just not an hoteltel span。😊，Okay。So with all of this。

 I will leave you with a few things。 as I was preparing for this， Braddon Keynes from Google。

 who's superstar in the fluent bit community， A K， A Brad Donong。

 He sent me some notes about his thoughts on the hoteltel collector and fluent bit。

 How did they coexist。 What are the strengths。😊，And what stood out to me is that he said the means to configure fluent bit to its most powerful capabilities necessitates an understanding of fluent bits architecture。

 that is as of this writing， not easy to grasp from the documentation and does require a deeper understanding of the internals that folks need to seek out for themselves。

😊，And so my hope with this talk was that I planted some seeds。

 I maybe showed you one cong option you didn't know about or a diagnostic tool that you're gonna to go take back to work and try out and learn more about your logging system and how to make fluent bit work for you。

You can join our community。 We've got a fluent bit slackla。

 You can see we're under the fluent D umbrella。 We've got a newsletter。😊。

And a big thank you to everybody who has used， contributed or just joined the fluent bit community。

 It's been a great 10 years。 And I'm really excited for the next 10。😊。

You can get a ebook copy of fluent bit for Kubernetes。

 or I have five physical copies here that you can come grab。



![](img/9c9a219dba5f4a654a350727e0199c47_4.png)

And thank you very much。 You can find me at Pagerduty dot com or on Macstodon in Blue Sky。

 Please ignore the X。 I will be deleting that。😊，Thank you。



![](img/9c9a219dba5f4a654a350727e0199c47_6.png)