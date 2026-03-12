# Gophercon-Uk-2025-p18-P18_释放_Go_工具链--BV1dCHTzQEdN_p18-

![](img/1f7f31b1bf2a900aefcf60c3fdb8ab4d_0.png)

🎼Next speaker we have today is a specialist in infrastructure。

 microservices and observability is a very broad contributor to open source and is currently working as a staff software engineer at Datadog also formerly of Red Hat so would you please give a big hand for unleashing the Go tool chain to Cammal Acoon。

😊，So hello everyone。 today we're going talk about Go toolchain and an open source tool that we are building。

 So who am I， I'm an open source software engineer。 I've been working on infrastructure tooling era。

 I think since 2017 when I joined Redheadt， I start working on CNCS based observability and distributed system tools。

 promeus， Kubernetes whatnot。I am also still a promeoruous maintainer。

 and Im contributing to the open telemetry。So。I work for a small startup called Datadope。

 At this point， I think we have 30 K users， and we have， I think。

Like 8 out of 10 most prominent AI companies， what not， so。I had to do that。

 The healinging time is over。 But do you know， this masco has a name。No， yeah。

 I learned when I joined Datadog。 It name is bits。 So Datadog bits， pun intended。

 They really like Dops inside。😊，Yeah， top pound meme is a thing。So but like before we maybe continue。

 like if you' are interested in working for Datadog。

 we are one of the most prophyic contributors to the goal runtime after Google。

 so we have a couple of people constantly try to improve the goal tooling system。

 but especially when it comes to tracer profiling， whatnot or the performance bits。So。

Let's talk about first， what makes Go great。For me， it's simplicity。 And when it comes to simplicity。

 why it's important， because most of the times we read the quote then。We write it， or like。

Compile it。 and then the machine is executed。 Ma doesn't care if the code is readable if you run the L format or whatnot。

 but it's all about the cognitive load that you have。 And that's why like Go is great。

 I used to work as a Ruyion rails engineer back in the day and。😊，Usually。It is。

Ruby is a really nice nice language to work with。 It's also simple to understand。

But it's not simple to troubleshoot， right。 So， but go has all like everything。 It's easy to read。

 understand， troubleshoot， simpleim to operate because you can just like build a single static binary and deploy it。

 So there is no magic。 We can like。Summarize it like that。Why this matters。

 magic seems great while coding， but troubleshooting time， it's a mess。 If any of you。

 if you ever like work with rails， you would understand this。So。There is always a but， right。

So let's roll back a little bit。 Let's talk about three pillar of observability。

 People like that phrase。 I think now we have the fourth one profiling。

 maybe we will continue adding more。 But what we mean by that to observe a process or service。

 we try to collect some signals They are basically events or aggregated events， so。😊，Logs， what。

 you know， it's the easiest thing that you can do。 Just log a line。 This happened。 that happened。

 then that happened。 This was the thing that at hand， whatnot。 And the metrics are some measurements。

 They are basically。Aggregations， so you measure something What's happening。 Yes。

 like the current CPU usage or like a histogram of the。

 of the durations of the request that your application is serving right now。 I'm a metrics guy。

 So even though I'm like working for tracing right now。

 I think the metrics is the best signals out there because it's like cheap。 It's easy to add。

 and you can take actions on top of that。 You can like build alert for your services and like you。😊。

If your service is down， you can pay someone。 you can do that based on the metrics in the cheapest way。

 But if you want to know more about your application， like。I don't know。

 Network apologies where you are spending most of the time and what's happening when you are spending that time in that service。

 like traces is your friend， basically。Traces give you the most of the things。

 but it's also the hardest to integrate into your systems， because you may have。

Different programming languages， different runtime。

 different sort of services and like context proagation is is a problem。

 So to see the full life cycle of a request， for example。

 if you have an online HTP or GRPC based system。It's hard。 still， like to this day。

 I think it's a cultural thing。That， like。Hinnders us to integrate with the traces。

So how do we do these sort of instrumentation， right， So the manual way， we just write some code。

 right， go away。 It's simplified。 This is an example of how we set up。Traccing systems。 So we。

 these called samples are based on open teletry。 So they are open source。So you create your provider。

 you create your exporter。 And then finally， you got your tracer。

 and then you pass around your tracer and start collecting traces。 This is the most simplified way。😊。

But in real life， it looks like this。 So you have oops。Can't I can't scroll。 Oh yeah okay， you。

 first of all， import a bunch of packages。 I don't know why they design go SD K like this。

 but it's hard to integrate。 and you do stuff。Like proagators， metrics providers， log pro。

 I don't know what most of the things are。So， and then， yeah， after all these things。

 you have a functioning。Facilities to export traces out of your application。

 And then you got your tracer。And you pass it around if you， you have an handler。

 and you would like to see the。life cycle of a request。 This is basically what you do。

 and rest is your business logic。So。This it was go。 It's quite simple， but let's see how it。

Happens in the Python， for example。Similar， maybe less code， because they have default。

Theyade to get their tracers， and they have like， fancy syntax， and then。They have exceptions。

 They like easy to integrate。Let's see the same thing with go， yeah。It's not that bad， right。

 You have all the facilities。 Maybe you record your errors， whatnot。So when you compare like this。

 that's okay。 Yeah， we have a bootstrap code we need to do。 But there's other ways to do that。

 Like we call it semi automatic race， which is like using annotations and decorators in Python terms。

 which is this is。Not open telemetry， but in you can have tracers like that。

 but it's just an annotation and instrument this application。 and boom， you have everything。

 similar thing you can do with Java， Java allows annotations so you can add an annotation and you can start collecting your data they even have like things like span attribute to the arguments that you have and you can put those into your spans or like instrumentation code。

Forgo， it's still manual。Yeah， it's。Feedlines， of course。 But the thing is。

 you need to do it everywhere。 Like， that's the problematic for every function that you would like to。

Instrument， you need to put this boiler plate。 but there is。Another way to do this， not in goal。

In Python and Java and Ruby。Basically， zero code changes and you got everything for Python。

 you install a package that comes with a bootstper， you do that。 and then you just say okay。

 open telemeary instrument， my Python application， and you got everything。

Even like the function calls in between So the in processcess function calls。

 not just HPU case that you have。For Java。They have a jar。You install it。ARun your Java。

 probably you have a container at this point， and you just like modify your container。

 and your application is instrumented。Works with all the popular frameworks and libraries。

 but with go。They don't have anything special。 We still write the code。No agent， No magic。

Just boiler plates。So some reality check。 So the developer experience gap is real。

 especially for a company like Datadog。Because like， we have a lot of customers。

 They have like different environments， different languages and。

They want to see everything in the same U I。 or like， they want to collect everything。

In the same bucket， basically。 So the pain is real。

So manual instrumentation means you need to write all those boilable E code。

 remember to add the spans to the EV code like maybe you have some team or component。

 are they haven't started instrumenting their code and then you have these gaps in your spans。

 You don't know what's going on there， but you technically know there is a service in there。

 but haven't started instrumenting their code。 you can you have the egress point an ingress point and the egress points。

 and you know like okay this is the amount of time has passed between these requests。

 but what happens in between。 It's hard to keep track of and there's always the maintenance burden。

 something changes especially open Telemetertry SDK。 It changes a lot。

 So you need to whenever you would like to upgrade。 You need to change the code。

 it always breaks I don't remember an upgrade of open Telemetry SDK。

That I haven't broken my bills yet。So， what。Like， we assume what go developers want。 I don't know。

 They have， They want the same experience， zero friction。

 automatic instrumentation without any runtime overhead or manual code changes。So the question， like。

 how can we compete with all these runtime， The goal run time is by design， simple。And。They don't。

 we don't have Jit。 We don't have like a way to rewrite the byte code。

 We don't have even the byte code。 It's just compile binary， right， So you。

 it's hard to get support from the runtime itself。So the challenge， we don't have annotations。

 no on time cord injection， we need to compile everything， so we need to find a way。Soution。

Goal has a hidden power。Which is the key part of the talk。 The tool chain is another go program。

 So if you can modify any program， you can change things。 So Go puts its magic in the tools。

 not the language runtime itself。😊，So let's see some show fence。 I don't know。 I don't see you。

 Maybe you can shout as well。 Have you ever heard of To as egg or used it。

You can see a couple of hands， okay？So let's introduce Tuula Z。 It's a flag in Go built。

And it basically one of the best kept secrets of go。 I don't think it's a secret at this point。

 but you can do funky stuff by hooking into Tuulaac。

 There were some other previous talks in the golfffer cons。One was from Daniel Marti。

 He tried to obfuscate some code Another talk from last year's Go for US。

 They tried to build their own code coverage tool， for example。 So how we do this。

We can intercept all the build phases of a go program。 So let's see。

 let's try just simple wrapper and see ourselves。😊，It is just consume some command line arguments。

 and the first argument is the tool name and the rest the arcs that it passeses。

 and we're just going to like print them out and only also let's forsake of like doing something real and let's capture the time and see what happens。

So you built that binary past that flag to the goal Bill。Go wheelchin using tool as Xfl。

And you see lines like this。 So there's a compile time， and it took 023 milliseconds。

 And theres a link command that is executed。 And you can see what's going on like how go on time it behaves。

So technically， we can。Intercept all these goals， so。And we can see， observe what's going on。

So intercept every tool call。 Let's try to wrap。Each of these and see what we can do。By like。

Doing these， like running and checking the logs， we can see that this is very simplified。

 go build time compile to runtime， comp bunch of packages。

 all the dependencies that you have to have that program。

 there is this phase of parsing the source code figuring out what it imports like building a dependency graph and compiling everything and in the end linking everything together。

I don't want to like focus on these part of the talk like the process， how go process works。

 But theres a really great talk from， I think Go UK 2022。Yeah。

 I learned a lot by like watching this talk。 So if you want to dive deep， you can have a look。

So let's say we want to target the compile step， right， It's just some。Mtching the string。

 we know that that's what's get called to the tool as like。 and then we can say， okay。

 handle compile time with the arcs and do something about it。

 Let's say we just want to carry about like the go files and from the go files。

 we would like to do some analysis or some modification to those files。 we can do that。So。

The next phase。 now， we have all the source code that like funneling true。 And we can hook into that。

 Let's talk about。How what we can do about it。Who here has ever written alin or similar things。

Couple of friends。 All right。 So Go has amazing facilities for。😊，Pasing。

 transforming and reasoning about the source code itself。 Basically， it you can do a lot of ASD。

 asymptootic what syntaxtry manipulations。 So and yes， you cannot see。Well， did like。

Go has some intermediate representation as well。 You can actually like see what it is generated as well。

 you have facilities in the core runtime with the packages you can see what the SSA output。

 you can see what is the A T output。 especially when you want to do like really advanced things like okay I would like to check around what's going on with the locks。

 for example， where do I acquire the lock， do I actually like release that lock the best place to absorb those things is in the SSA for example。

 and then there is a way to actually check that。 there is a really nice Li called check locks in the Gvisor tool repo。

 It's not a standalone thing， but I've been playing with that and I was amazed we can actually statically check the locks。

 and we can see if we want to。😊，We have already acquired this law， okay。It was a sidet。

 but let's see what it gives， right， We can parse the source code into a syntax tree。

 We can walk and analyze。 This is what Lints does。 right， They see a pattern， okay。😊。

Let's say you forgotten the handle an error， right， And they check， okay。

 theres a function that returns an error type interface， Inter value。

 And you are assigning that to an underscore。 And you are not like doing any comparison to that。

 right， You can just like check the link。 Find that pattern and just like yell at the user。

 Don't do that。 right。But moreover， you can actually modify the ch itself on the fly， right。

 You can match those patterns and then change the chor。And then you can generate valid code。

 generate packages， and feed that into the GoB tool chain again。So。Let's check how it looks。

Basically parsing the go tree。 This is a very simplified example。

 So you remember our analyze go function from the。Previous tool chain hook comment， like。

 we are checking that。Converting that to a token set， parsing the file， if it fails， we return error。

 oops。And then we try to find， for example， this is。

My tool is yeah all the declarations in this file， right。This is how you do it。Okay。

We have a A2 parse， gather some statistic， maybe just like the high level studs and we can just print them。

 but what if we want to do something more involved， we can actuallyva the tree。

 There is a function called ASD inspect。You can give there is a function called like you can implement an interface called visitor。

 there is a function called like Volt， for example， you can walk the ASG tree。

 you can have a little bit more int but you can also have the inspect pass closure and check the notes itself。

 so here we will try to add annotations to GoCd right。You don't have annotations in go。

 but let's say these are。 but we have something equivalent to that。 We call them directives， right。

 slash slash go link name， for example， or the build text that we have in the file。 These。

 These are called directives like the goal itself。 It uses that。 Maybe you can say that， okay。

 don't inline this function。 It exists， right， Let's follow the same pattern and try to have something like。

 okay， we would like to inject some log lines。 Let's call it D D。😊，Datadoox， sorry， and then log。

 And then whenever we see that。Anotation or like a directive in the function。

 Let's try to add log states in that。 So for that， we need to find all the function declarations and then check if it has the log command。

And then like remove it， let's immediately clean it up， and we are going to inject logging， right。

And his low comment file looks like， okay。There's file。 You can extract the command itself。

 find the comment group， like， do some string checks， oops。即。

Didn't highlight that part and check if the text contains D D dot low， right。

 This is our investigation stage。One of the shortcomings of the standard library packages air on to comments。

You don't actually store the positions of the comments。 So if you change the tree a bunch of lines。

 you lose track of the comments and you can easily mess up the comments。

 not the code itself because it's the AST， but the comments that are associated to the correct note。

 you lose that information。 there is already an open issue， and the team。

 they already acknowledge that。 they would like to improve the standard library。

 but there is an open source version called DST， which stands for Dave syntax tree。

 which helps you to keep track of the comments itself。

 So it's like preferable but for sake of simplicity。 I didn't use that package。

But there's an issue They want to address that。So let's modify the A SD itself and inject some log statements。

 right， How do we do that， This is the。A little bit ugly part because we are building that actual A SD。

 Okay， we want to add。The start， and it needs to be an expiration from the time now。

 you represent that。And then let's say we would like to add the S log info。 and we do that。

 And we add the tokens。 This is the thing that I would like to add。 So it's。

Intense labor intensive code。 And then you want to add that the first statement because you would like to record the function exit duration。

 and then did Yeah， then I forgot to highlight that part。

 and then you add that function body list append all these statements to the function that we are modifying and what happens that okay this is a valid syntax tree and then you just like speedit out the code。

 run the go format in the code and you get something predictable。So from L to a modifying code， like。

We now can generate more stuff， right， like that was about the modifying the code。

 Maybe we would like to import some packages， generate some packages add some files。 There is also。

Another open source package， This is from Golan thatx report called AST U。

 It is the interface that I previously mentioned， the visitor interface or the inspect interface。

 They don't let you to modify the node in place。 You can just like modify the children of the node。

 and because it's not a pointer。 and its like they realize that they made a mistake in the API。

 but this is gos backwards compatible So that's why there is this AST U package exists。

 It's cleaner to modify the node。 So we use that。 Yeah the named import。 We don't need that。

 but I just wanted to demonstrate theres a function of that because S log is as log。But then。

Rerite and generate a file。 Now we have a file that all the log lines are injected。

Let's see that an action。So。I'm not doing the live demo part。 It's hard。 Things go wrong。

 So that's why I will just show you that。 But everything is， theres a link at the end。

 You can observe the code and run it yourself。Even the simple application。

 So we annotate the function， D de log。It's just doing something sleeping to demonstrate。

 And the end result， we get all these parts are injected。 Now。

 we in injected our instrumentation code。Now， basically。We have。 and this is the end result of that。

 Now， when you function， basically executes， you got your。Instrumentation， this is logs in that size。

 So now go has annotations。I don't know。 This would make Java， old Java people happy or sad。

 Oh my God， I just like got rid of these things and they strike back。

 I don't know if you are an old Java person that write go。 Please find me。 I would like to know。So。

 the grand plan。Compile transform compile time transformation。 Now， we have a way to hook。

In togo build time， it tool is X。 We know how to analyze the code。

And then we know how to transform the AST。 Yes， this is not run time。 so compile time。

And we can modify and modify the source code and put that back into the goal build process。

 And the end binary review will have our instrumented code。So， this is0 overhead。But in runtime。

So because we are actually budding compile time。 So there is an overhead in runtime because we are adding some code in place。

 right？So， one more thing。Who doesn't like Yamals。Please be honest， Like， this is so few。 Really。

 don't you use Kubernetes。No， okay， I hate the animals。Okay， but。Those directives。

Is theyre also not easy to add， right， You need to know where to add them。 And there are some。

P prerequi。 Maybe you need a context。 If this is a tracing code。

 you need to have the context that context because like。Context provocationation。

 You need to have a span I D， Tracing I D。There are some limitations as well。 And still。

 like we are dealing with some type of persona in global community。 They don't want to do anything。

 Yeah， I don't want to instrument my code。 Like even adding that comment line。

 I don't want to do that。 So how do we do that。Apect oriented programming。

 Have you ever heard about this term。Really。😮，Okay。No one， Okay， I was expecting Brian。

That shows your age， Brian， sorry。So this is also very popular in Java。

 and it's about like cross- cuttingtting concerns， something that makes Java people happy again。

 like what are those cross- cuttingtting concerns， like observability， security reliability。

 So anything is not your business logic， but you need to maintain and write and make sure it works in your code。

Those are cross cutting concerns。We all like gave examples from observability。

 but we can do the same thing for security， reliability of platforms。 Like， you can inject anything。

 right， This is the goal source code like we have。😊，I。I I will talk about it some integration。 And。

 for example， it's for us。Enabling profiling on your like production services。 it's easy， just like。

Let our compile time tool inject a boilerplate code。

There are a lot of AO P solutions out there in Java， Python decorators， meta classes， annotations。

 I don't like this stuff。😊，Sorry， I don't even like the genetics。 So I am that guy， and I really。

core routines like what are core routines and iterators now we have。 like。

 have you ever seen a iterator code。It's ugly。 It's hard to read。 hard to reason about。But。

 apparently，They love it。 Coeen。 Okay， that's another discussion， so。

So our answer is like compile time transformation， no runtime over at。

 We don't use any deflections and like0 cognitive load for developers。

Let's see some real word examples。 Of course， they are not real word， but yes。

Let's say we have a process order。 We have some authentication things。

 We have some tracing logging injection， like we decided to have a circuit breaker。😊。

And then boilplate instrumentation called with that， we can just like reduce everything to this。

 okay。Process my order。That's just the business logic。 All of the things。

 I'm going to inject that in the compile side。 So you don't need to do that。How do we do that。

 Ya Yes， this is the Yamel part of that。 So we have these definitions now。

 this is the thing like I want to put an example， real life example we have the join points。

 This jargon is coming from AOP and Java as well。 So they call it a join point and we have a directive like an annotation。

 So it means like find all these like annotations and put this code in there。

 we still support that with this production tool which I'm gonna mention soon but you can also do some other things right okay。

😊，So you have a drawing point about like trying to catch any open pile。

 and then you have a security library that checks。Whether if you can open that file， whether like。

Yes， basically sanitization and just like you don't need to go in there， change everything。

 so you just basically say that any call to the open file。

 I would like to just inject this and change that。Cross cutting security concern。

So I've been referring to this tool。 It's called Orchestra。 It's a weird name。

 I know I didn't know anything about this word before。

 So I call it the Yamal vision realized in production。 Yamal strikes again。 its like。Apparently。

 this is orchestra， right， It's some sort of an organ。 like it's an old thing。

 I don't know who named the prob。 Yeah， it will become so。So we named our two from orchestra。

And what orchestration does， it's compile time auto instrumentation for go applications。

 So0 code changes required， open telemetry， compatible supports bunch of go frameworks。

 not just the standard library。It's production ready。

 You can use it with all these magics that we use。 It's an open source project。 How it works。😊。

You installed that。There is a binary， and there are two modes， right， The first mode， we have the。

The thing that we've been talking about， we can just like hook into this as a laser。 Okay doesnt。

 Okay， so you can just say that， okay， run this comment with this mode and I will do all the magic for you。

 the other way is， okay， you can just like pass it along to the binary。😊，Yeah。

 its whatever you would like to use the most like the practical use case that I have。

 there is also a tool as like environment variable and you can just set that and basically you can build a base image where you set those environment variables install orchestraone and then just like use that as a base container image and all your go images automatically gut。

Instrumented， right， seamless。 So if you are a platform engineer， you would love this， right， Ok。

 I don't need to deal with any of the developers。 Okay， I'm just going update the base image boom。

 I got the instrumentation。 That's our use case， like。😊，So。All these were like， simple examples。

 This is the。Sequent the diagram of like orchestra。 It's a bit more involved， right？

 Theres this tandem between go compiler itself and orchestraone。

 I know like don't try to even read that。 It's just I just want to show that it's like complicated right。

 We have a job server。 Theres a dance going on between like go compiler tool chain and the orchestra。

 Okay， I have this file。 Okay， I'm gonna manipulate。 I manipulated it。 Okay。

 it's part of that package。 Let's compile that package again。 Okay， here the N package。

 and then you can link it right。 there's constant back and forth。 It's the compile stage。

 And the link link stage is the same。 Now we have Nve packages。 because we injected some code。

 And they have some dependencies。 So here are the dependencies put that in your compile list or like the linkless when you are getting everything together。

 No we have dependencies。So by that what we are doing， like we roll a bunch of integrations。

 what we mean by those integrations， Yammal files， we basically rolled all those Yam files for you and put them in public go packages modules and we have orchestra that tool that go file and this is basically a go mod file。

 you say that okay I'm going integrate with that because I'm using G I have some GRP sitting I would like that integration。

 and then you have that file or orchestra finds that。

 finds the integration pull just go module system， pulls that file knows what to do and inject every record。

We already support。Like goilla Jean E probably more。 didn't put everything。

 But if you have an HTP application， you can just like use it and start like if you have a service。

 start instrumenting everything。 If you have a database like same。

 If you have an R M we can instrument that as well。 Now you can see that。 okay。

 my application gets a request， I make a query to some SQL database。

 this is the amount of time that I actually spend in the querying and these are the attributes what not we do that as well。

 R PC same and many， many more。 So but it's not just instrumentation， right。

 we have security product that like we use this to enable our customers because like， yeah。

 they want auto instrumentation， automatically everything。 I would like to use your security product。

 and yeah this is。😊，How you use it Aerospace capturing。

This is what I've been working on for a couple of months。

 This is an interesting thing to actually think about。 So we even with the like error changes。

 we don't have a way to capture the stack in place for the errors， right。

 So that would be nice to have them。 Okay， this happened when this error happened。

 these were the calls。 And then if we can put them in a span。 And if you see that in the U I。 Okay。

 these are the actual like stack traces。 You can say that， okay， I'm wrapping my errors everywhere。

 but the rapping is not the same with the capturing the actual stack trace。 So。

 but then this is an actual shotgun surgery。 Let's say you you've been using the standard goal package。

 But there are libraries out there that supports capturing the stack traces and proagating that。

 now you need to change everything everywhere。 like all the error things。 So we actually。😊。

Find a way using these tools， Find a join point， Find all the methods that actually returns an error interface。

 Find that error value and wrap that with this function。

 the package that we have called this rep function。

 And if there is no stack tracing that we will just capture。 Now， your application， all of a sudden。

 like all the functions that returns errors， which is a lot of functions， probably。😊。

Can have these aerostic traces。So the sky is limit。 If you。

 you can visualize that pattern in an A SD form。 And if you like， do you know what to change。

 you can do it， right we have。Already predefined a lot of drawing points。

 like aspects to change to manipulate the code。 It's Yamala engineering。 It's ugly。

 but you can do that。 So the performance impact。We expect 10% to 20% more time spending a compile time。

There are some N cases， but it's one time cost。 You。

 it only happens when you're compiling your program。 I show you the like the complex。 oops， okay。

 it's， it's not like the complex diagram。 We do a lot of stuff in the compile time。 So compiles time。

 compile times are a little bit slower。But compile times are not that expensive compared to developer time。

 So maybe that is acceptable。 There is no runtime overhead。 There is no magic involved。

 If you manually instrument your code base， it's the same result。

And the binary size depends on the injected packages。It could be。

Increased because you were like not instrumenting anything。 You just like edit another module。

 It's the same thing。But you get automatic distributed tracing， metric， logging all over your fleet。

 all the go processes that you have。 You don't need to maintain anything。

Con consistent instrumentation across the team， Product ready observability。

 whatever you would like to call that business things like。This is the value of observability。

 right We are not discussing that。 That's it's about like how we put that in there。

 And the orchestra is agnostic to the library that it injects， right。

 If you have the correct ammal files， you can inject anything。

 if you have your favorite instrumentation library that you've been。Building in a company internally。

 you can use orchestra to inject all these things， or you can just use open telemetry SD D K。

 whatever。 like the orchestra doesn't know anything about the injected thing。So， we aim for。

0 developer friction， production ready solutions。 You can just use this。By hooking To Le， basically。

I am sure。Go runtime team or compile team。 They are not happy with what we are doing。

 Well all the comments are doing。 They are really abusing something they put there for maybe introspection purposes。

 right， maybe you will have a time function。 Okay， use it you would like to profile what's going on in between steps。

 Actually， like， that's one of the best use cases。 I think they are using it for that as well。 Like。

 okay， how much。😊，How much time it takes to build that file file and track that， right。

 for it's useful for that。 But it gives you a lot of information in those calls。 like。

 what is the source code。 And okay， youve got ideas。 And this is the end result of it。

So this way is different from the other languages， runtime magics， proxies， whatnot。 First of all。

 it's predictable。 There is a mode。😊，You can actually say that， okay， orchestra。

 I don't want your magic。 I want everything explicit。 Just spit out what you generated。

 and you can check it in。 That's E。 It's doable。😊，So it's performant because there is no runtime reflection。

 whatnot involved。It got like access to the full ASD can do a lot of stuff。

 like sky is the limit like this is imagination you are writing whatever you can write。

 you can make this tool to write that code piece。EIt works with all the existing bill system。 Go。

 if you are using basil， I'm sorry for you。But it works。 We also use that。 So， but it supports like。

 theres nothing wrong with that。 So the feature， like， what do we do from now on， so。

Couple of months ago， or Datadog decided to donate orchestra to the。Open telemetry。

 This is a community project。 This is already open source。

 So we don't we just want to make this way more ubiquitous so that community gets an adapt。

 they like。😊，They can use open telemetry they can use any library they would like to inject。

 We just want to have there。 But there are other people also came to same conclusion。

 There was a small project started in the open Telemetry countryrepo called Insgen doing similar stuff。

 but in a very premature form。 and were there was another tool from Alibaba called Open Telemetry go instrumentation。

 It works with the same way。 So and then this started。

 They also decided to donate to project and open telemetry being no Kingmaker。 Okay。

 we are going to form a C And you bought parties。😊，Builds the new tool。 So this is what we are doing。

 So there is an open telemetry O C working on auto instrumentation， compile time instrumentation。

 This is the first tool that I mentioned it's retired。 now we are learning from orchestra。

 our experience， the tools of like Alibaba already built and we are merging them together and we will have and like a neutral tool that does the same thing in open telemetry depo。

 and CNNC have gone on that。😊，And it will be injecting the like。Open teletry SD SDK itself。

There is also a project that I would like to mention。It's called open Telemetry Weer。

 It's about setting the semantic conventions， basically。Another Yao project。

 So you define your observability standards， semantic conventions， whatnot。

 And it generate the documentation， All the SDK that you would need for Python， rust， like go。

 you name it， like for the all languages。 Then you grab those libraries。😊，Incorectly。

 like by semantic conventions and you instrument your application。

 So you can combine these bold approaches， right， You can use the weer。

 generate all these things in a semantic convention。 It's just an application to inject。 get that。

 Use this tool。 inject to your application。It's a couple of days of work probably to decipher all these things and put everything together for a platform engineer。

 but then like your whole services can have instrumentation and up to date instrumentation or like some security protocol that you would like to check。

 you can have it， the error tracking that I mentioned。So if you want to go into into this， like。

 start small， like。Pick a service， pick a demo application， compile that。 See the result we have a。

 for example， orchestra D command that shows you what it actually injects。

Try to find some A SD patterns that you would like to。

 if you want to do something custom like and try to inject that one as well。

If you are like super hyped for whatever reason， O， that was the thing that I was waiting for。 I。

 I want to contribute。 We are like。You can find us in the public calendar of open Telemetry。

 We meet every Thursday morning If Im not mistaken and we are at the beginning of the project。

 So you can there's a。ItLike really tremendous amount of things to contribute back。

 So if you want to do something in open source， if you're like one under or more。

 join the meetings and try to contribute。So this talk was theres a precu to this talk。

 We've been building this tool for apparently four years。 I only joined Datadoox six months ago。

 So I wasn't there。 So this talk from John Butner， it actually shows a primitive version of this tool。

 And if you want to learn more about it。 check it out。 it's a great tool。 a great talk。

 you would learn a lot about it。😊，So thank you， everyone。

 This was the all the content that I would like to share。I mean。

 it's your turn to unash to tool chainin。These are the slides。If you wanna learn more。嗯。I also。

 it's in a gi Github report。There are also some links。

So the resources that if you would like to discover more。And if you want to keep in touch。

 these are my handles。 A， font awesome。😊，5 doesn't have a blue sky icon。 So sorry about that。

 I need to upgrade my tooling to Fo awesomeom 7。My front end skills are limited。

 So probably I will ask cloud code or something。 Okay， how do we do this。But yeah。One more thing。

 since we have time。Dark magic。 Do you want to see some dark magic。

 All these things were magical for a go developer。 If you don't feel like it。😊，I don't know。

 The first time I've seen this tool。Before starting working on that。

 like all my gopher senses were like tingled。 What is this， Like， why do we do this？

 But the technical challenges are like really nice。So。Ptching to go on time。We can， actually。

To whatever we want， including the Go runtime， right。Because then you say， okay， go build dash A。

 It builds everything。 When it tries to build everything， it includes the go runtime itself。

 So that means。We can reach out to the goal runtime source code and do whatever we want。

 So this is the dark magic park。😊，AndIn， in。The code that I'm going to show you。

 we are trying to modify around time G， like one of the core components。 and it's creepy， right。

 We can just like， break。😊，Anything， the whole thing， it could be unpredictable。 Apparently。

 it's not， so。But why we wanted to do that。 So I show you that some of the functions they don't have the context。

 right， And you would like to instrument that called， How do you do that。

 You need to propagate the context， You need to find the context。

 So we come up with a thing called coal local storage。

 Dolly inspired by Tread local storage and what it does like。if we have a context in a go routine。

 we capture that， put it in there。 and then like we read it from there when we are executing the code because it's not properly pest lot。

 So to do that， we patch runtime itself。 runtime G struck， we add another pointer field in there。

There are some， like。Functions that we add with go link name。 Okay， add these things。

 And there will be a package that you're gonna be linking and you can jump onto that and do the cleanup after goal routine exits and the Yammal part。

 okay。😊，So with all those like join points as like you are reaching out your own code。

 we say that okay， find the go wrong G time。 Yeah， it just finds that track definition and at this track field that special name track type any。

 Oh yeah， please import unsafe because we are doing something really unsafe。

And then we put the linkname to link against that， add these functions to that tract。

 and now they are available。 and then now we can use those functions to clean our mess。

 We also hook into the go exit and then like call a function。To basically make it ned， right。

 because it's not ex exiting。 Or whenever we we will call it again， we will inject something else。

So this is the funk。 Like， these are details。 But if you are interested there in the slides。

 how we do that By that， we implement a stack， basically。We can push things on the stack。

 anything related to the context。 and then we can， for example， put a tracing Id。

 put a span I in there and then if a function that we are trying to instrument。

 if it doesn't have a context， it can reach out to the go local T GLS basically and read that value like this right It's the GLS context。

 We put something in there and probably it's the tracing I span I。Andvoola， some dark magic。So， yes。

 this time， I' am really。Pan， thank you for listening。All right。

 I think we have time for a couple of questions before the break， if anyone's got any。Hi。

 that was great， really interested to use this tool I it the case that you can see the generated code I wasn't clear on that so is it go directly to binary like can you see the effective result of as it were as source Yes yes so you can。

😊，So whenever go build things， right， it creates a temporary directory。

 and you can actually see those generated code。Maybe not the source code directly。

 but the artifacts the archive files they are generated。

 but we have a mode that you can actually observe them right and it's called orchestra di Nely added if you there is a flag that you said okay orchestra and whatever you are doing。

 give me all the information you have basically debug mode and it gives you that while I'm building this binary。

 I generated this director and everything is in there and you grab that directory in your source code and do the orchestra diff and you see what were the results right so you could then just build that and you get the same effect it's already built if you see like this is just for debugging right it's just for transparency if you want to change something you go back to the Yama file change stuff it is the source code that would produce everything is on source source code。

Thanks。I think my my question might be slightly similar in that regard。

 So you're putting the code you're going to inject in the Yamal file， right。

 But then how you go about testing that code。 Yeah， so make because I mean， I don't know you。

 but I very rarely get the code right the first try。 So So we have some testing facilities。

 basically there are snapshot tests right， again， Yamal files you say that， okay， this is the。

Aspects that wantna have in the Yamal file。 And this is the called template that I would like to inject。

 And this is what I'm expecting to see。 We create those like golden files， snapshot files。

 whatever you would like to call them。 And this is also necessary for the regression testing， right。

 And it they get run whenever we change something。 That's how we test。😊。

In terms of being able to debug after you've run this sort of thing。

 so if the changes that have been made by tool Ex or whatever， are they altering the file names。

 the line numbers of what you might cover up in your stack traces？

Can you repeat it really having hard times also here？

Question about whether when you're debugging is when you're doing toolex stuff。

 is that affecting the line numbers， the file names correct everything。 we also like。

So we have a mode。Now， we actually。I。Everything happens in the compile time and all the line numbers are changing and accordingly we change everything right but let's say that you don't want to do this implicitly。

 you want to have something explicit right and there's a mod for that。

 I want to run the orchestra and I want to see all the outputs in my code base and if I want I would like to clean everything up right for those things we inject some comments in place This is where we started like the line number。

 this is where we ended and then when orchestra want to clean your source code， find those blocks。

 remove the source code so you can go back So everything is automated。Any other questions？

Go on over here。Yeah， thank you very much。 It was very interesting technically。

 You said yourself that you don't like things like annotations and， you know。

 I don't like what like Java annotations and like that sort of thing。

 right it seems to me that what what you've kind of ended up with in terms of like the end result is something that looks very similar to the black magic that annotations do except they are very exactly Yeah the difference between these ones are a invisible and B like everywhere Yeah。

 and I just kind of。😊，Like as a new developer to a repo using this， like。

 how do I like even discover that this black magic is happening and start to like reason with it。Yep。

 I agree。So first of all， we started the talk by saying like we despise these things。 And at the end。

 we just like ended up doing the same thing。 That's the irony of the talk right but like there are people out there there are users customers。

 they would like to have this they don't care about it。 me personally。

 maybe I am working in the instrumentation space for too long。

 I would like to see what's going on I would like to see and change everything。

 So being explicit is more important for me personally， but it's not same。

 And I understand Ive seen called like companies， they have thousands of services and too many teams and microservices right。

 it was the hype topic and if you want to change something in there it's a lot of the developmentment time。

 and I understand the reasoning they need it。はい。My question is about security。

Like my questions about security。 Okay， and did the go team see this or are we heading into an era We have open issues already。

 We talk about our journey explicitly。 We we have meetings regularly and they know what we are doing。

 and we also demanded some improvement in the tool as like because some some of the things like hard。

 especially when it comes to build caching Whatnot。They didn't say anything。 The issue is open。

 So maybe we will have it someday。 at this they didn't close it。

 So it's a good sign on on the client side or like on the implementation side， my question is。

 how can we are we heading into an era where coding agents inject stuff into our code Monicious stuff into our code doing the wheel time。

 and we won't even notice it， How can we prevent that from like happening。Can fear， really。

How can we keep it secure at the like real time when AI coding agents inject stuff into。

 But it's like， you can always have the diff。 like， you can basically enable。C I step if you want。

 and， and you can just like render all the changes that you have and do something about it。 but。

 It's like there is。I mean， you know， if you are developing this， there is no like。

 it doesn't give additional attacks text。 It gives an additional ax service。 Theres this if you。

 if they know you are using this and if you， if they change the Yamal file that you are injecting。

 they can do stuff。 but yeah。Okay， I'm afraid I think we're about out of time there。

 So could we have another big hand for Ka Akoyun。 Thank you。😊。



![](img/1f7f31b1bf2a900aefcf60c3fdb8ab4d_2.png)