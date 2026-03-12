# Gophercon-Uk-2025-p02-P02_Go_1.25_版本即将到来--BV1dCHTzQEdN_p2-

![](img/c06ef113ce62dcb458bb3c9c467c1a5a_0.png)

Its about ready to begin the second talk of the day here in the Port Saton。😊。

So the next speaker we have is a regular contributor to the go language and is currently working on the data validation language Q language which is entirely written in Go Every now and then Daniel Marty very kindly and obligingly comes out into the community to give us a bit of an appraisal of some of the features coming up in the next release of the language before it's out that's exactly what he's going to be doing here today so for his talk what's coming in go 1。

25 please give a big hand to Daniel Marty。😊，Hello。So。Before we begin。

 I should note that go does two releases per year， meaning one every six months。

 And you can see that the release plan overlaps a little bit。 starts such that for example。

 right now we're in the middle of August。 So work for 126 has already begun。

 And even though this talk is called。 What's coming in Go125。

 the release actually happened about 30 hours ago。 So maybe we should say what came in Go125。

 but let's pretend that didn't happen。 Let's pretend that something happened with a release and it was delayed by a week。

 And then the title is still correct。So a big caveat is that these are my personal picks and they mostly focus on features。

 so I've omitted fixes because they tend to be not as interesting and main the main purpose of this talk is to get you excited about the latest release so that you test it early and you help with the testing and development of go itself。

And I will share the slide with the links later， so don't worry about writing down anything it will be shared。

And here we'll only skimmed the surface because we've only got about like 50 minutes。

 But because of the links， you can always go and read more if you want。

So the first section is the language。There's actually no significant language changes this time。

 And I was wondering to myself， when was the last time that even happened because it used to be the norm。

 and the answer is it hasn't happened for almost five years because I believe it it was go118 that came out with generics。

And then we got a bunch of more generic changes afterwards。 and then we got iterators。 So really。

 there hasn't been one release with zero significant language changes for a long time。

Except that we have the spec has removed the concept of core types。

 but that's purely just a conceptual change。 The semantics of the language are exactly the same。

 It's just that if you read the spec， you used to have to learn what a core type was。

 but I'm willing to bet that most of you don't even know what that is because ultimately doesn't affect anything。

 It was just a concept。The next section is tools。 and by this， I mean the tool chain。

 command go and so on。The first one， and this was a big ask for many years。

 is an ignore directive in your GoO files。And the reason for this is basically the node modules directory。

 If any of you have written， for example， websites with Go and ja and you've experienced the fact that。

 for example， if you do go test dot slash dot dot dot it takes like 10 seconds to even start doing anything。

 it's because it went into node modules searching for go packages and it's spending you know it's burning your laptop trying to search for go files in there。

So what you can do now as of G 125， and what's important to note here is that you can only do this if you require G 125 or later。

 because G 124 will not know how to parse and understand this。So what you can do is say。

 ignore these paths。If you do dot slash， it's going to be at the root of the module and if you emitmit the dot slash prefix。

 it's going to be at any depth， so for example， fo slash static would also be ignored in this case。

And then this will be applied basically whenever you do that dot dot， dot matching。

 then those directories will be skipped entirely。Another change is go Doc slash HP。

 And one use case for this is suppose that you're flying to a conference， for example， in London。

And they offer you paid wfi and you say， I can't afford $10。Or rather， I would not pay $10 for wfi。

What you can do is use the go dot command to read documentation about， for example。

 a standard library package in this case， but also your own packages。

 you can do go dot/lashfo and that will still work for your module。

But the problem with this is that it's text， so you'll probably get spammed with pages and pages on your terminal。

And you also don't get nice things like sections， linkification of links and references and things like that。

 or for example， being able to like click on types to find out what a type is。

So what you can do now is with Go Doox s HtP， it starts a local version of package。

go do dev that basically does the same sort of rendering that you would get on the real website but locally and you can see that's local host at the top。

And this will mostly work the same way， but just with a caveat that this will work off of your local standard library。

 go version and so on。And you can see that the links in blue， they would actually work。

 as well as the examples。You can also run this on your go module。

 so if you run that command inside our go module that you maintain。

 all the packages for that module will also be available。

Something I have discovered is that if you try to follow through any link to， for example。

 a type from a dependency that will not work。I wonder if they will work on that in the future。

 there might be a bug for that， an issue for that。Another change is fewer prebuilt tool binaries。

 and by that I mean that Go 124 came with a bunch of different tool commands that you can run with GoTo。

 so as for example， GoTool compile。And these are basically just binaries， right。

 because when you install go， it comes with a go binary， but it also comes with these binaries。

 These binaries don't end up in your path， so you can run them directly。

 but you can run them with go tool。And some of these you might know about， like for example。

 compile and link are the compiler and Lier and that you run with via Go build transparently。

 but they exist。And then， for example， cover is what you might use after running Gootesque cover profile to view the coverage information。

And test to Jason is what runs under the hood when you do go test That Jason。

 It basically pares the test output and produces Jason out of that。So G 125 says。

 let's only include and release archives the binaries that we know everybody will use all the time。

Such as for example， the compiler and linker。But the others。

 we will not include us pre built binries， and they will be built as needed。So for example。

 in Go 124。6， via which I'm doing via Go tool chain as a way to quickly switch between versions。

If I do go to all dash N， meaning just show me the binary， but don't actually run it。With Prov。

 which is one of the binaries that is no longer shipped by default。You can see that in Go124。6。

 this is part of the Go install as part of Go toololcha， but in Go125。

 what's happening is that it's building it behind the scenes and it's just shoving the binary in my go cache。

 meaning they go build cache。So same result， I don't even see any difference in practice。

But the nice thing about this is that the release archives。

 which usually weighed between like 60 and 80 mebytes depending on the platform。

 they've now gone down by about 20 to 25% in size。 and we all know that go binaryaries go is a great language for many reasons。

 but binary size is not one of them。 So if you can shave off you know 10aries10 binary files are of the release。

That is quite a significant win。Another change is Go version M Jason。

I'm willing to bet that not many of you are aware of this。But go version。

 the commander tells you what version of Go you're running。With the M flag。

 you can point it at a go binary， and it's going to tell you the embedded information in the binary that says。

What go version built this binary， What module did it come from， What version of that module。

 What dependencies did it have and at what versions， as well as the built parameters such for。

 such as， for example。Gorge or what operating system， what VCS and revision it came from and so on。

But this is just plain text right so as usual with with many other commands。

 they've added a JSO form of this and this is not a funky new type that they came up with。

 This is just the same type that you can access via the standard library to access the same information i。

e。 runtime debug build info。Another change。 And this is more like a module's ecosystem change rather than a command go change。

 but it's both。Is that you can now serve a go module at a VCS subdirecty now this is a bit complicated to understand。

 especially if you've never served go modules from a custom domain， so I'll explain an example。

Suppose that I've got the Github。com account MD， and then I've got a reer called GC UK。

And I want to publish a package under there， right。

 So if I name the module the same URL as the Github repo。This will work out of the box。

 I can import this from another module。After pushing it to get， of course。

 but this will work out of the box I don't have to do anything else。Now。

 what if I want to host that module on my own domain in this case， mN。cc/ gcuuk。

 I might want to do this because I might want to change kit hosting providers in the future。

 or maybe because I like a shorter URL or maybe because you're a company and you want your module URLs to look more professional。

 right？So you can do this， you've always been able to do this by serving an HTMLl at thaturl。

That says metadata go import and the content is a string that says。

 I want to serve the module M done docc slash G UK at at the getripo at that URL。

 So it's basically just an indirect。 It's a pointer。

Something else you've always been able to do is sub modules or rather nested modules。

 So in this case， if I have a another go module at submodt with another package called package 2。

And I want to serve submod at that module URL。I can actually serve exactly the same meta tagag at that URL without changing anything and it will still work。

The reason for this is because the logic can tell oh。

You're telling me that MV1T C slash GC UK is at that repo and I'm looking for a module that's underneath that in submod。

 so I will look for the directory submod in that repo， so it does basically like a prefix match。

 right。But here's the pro the case that doesn't work today。

 What if GC U is a demo repo that contains code for many languages。 So in this case， Ro。

 javascript and go。And I want to serve this as a go module on my domain。Now， if I did this。

 this is not going to work right away。I could serve the module。Under source slash go。

 But then the module paths or rather the package import paths are gonna be a bit funky。

 What if I just w to remove that source slash go suffix， I just wanna say to the modules ecosystem。

 the source for go is in that directory， but pretend that's sub directory。Is not part of the path。

 right？So what they've done now is that the go importport meta tagag。

 you can add one more element at the end that says same logic as before。

 but instead of using the root of the repo as your go source， use that subdirecty。

So it's basically the same idea as before。 It's just that now my module path is is cleaner。

 It doesn't have to include source go。Another change that's kind of related is that now you have a work package pattern。

Actually， show off hands。 How many of you know what go workspaces are。Okay， about 20 people。

 so maybe like about a quarter of the people here。 So a go workspace is basically a way to say。

 I have a bunch of modules in this repo or in many reos。

I'm going to collect them all in a go dot work file which is called a workspace and what this means is that all of their dependencies between them or with external modules。

 they will be synced up so that they all agree with each other so it basically lets you work in this case these modules for example。

 OCI server depends on OCI registry so I want them all to always be in sync and I want when I work in the first one I want the dependency to be the the same module that I've gone locally instead of the remote one that's track。

So a go workspace let you do that。But the problem is that once a go workspace grows pretty large。

 being able to work on the whole workspace at once is actually kind of tricky because the dot dot dot prefix only works within one module。

It doesn't allow you to sort of get past a workspace。

So with G125 what you can do is use the work pattern and that is basically an alias for all the packages contained by all the modules in my current workspace。

 but not the external dependencies， it's only the packages directly inside each of those modules So in this case if I do a go list you can see I get the package for the command。

 but also all the packages for OCI registergitry and everything else。And this will work with go test。

 it will work with Go installst。 So for example， if you've got a CI on a mono reer with a workspace。

 you could do go test work instead of having to C module 1 and then go test CD module2 and then go test and so on。

Another change is checking for finalizers。 So go has had。

F rununtime finalizers for objects for a while， meaning that when an object gets garbage collected。

It is almost guaranteed that a function will run for you and you can do this， for example。

 to I I believe it's used by a dot file to check that a file is closed in the operating system before you release it to the garbage collector so that you don't leak file descriptors。

And now we have runtime do dot at cleanup， which is a more modern and less hard to misuse version of finalizers。

 But there's still ways to mess it up that are kind of common。

 So this godi back flag tells the runtime。嗯。Spend a little bit of extra time。

At each garbage collection step， but basically run some extra checks to catch common mistakes such as for example。

 do I have a cycle in my pointers that will mean that my cleanup never runs or does my cleanup function point back to the object that I'm trying to clean up meaning that it's going to be broken。

Another change that is actually pretty dumb small， but I've run into this before a bunch of times。

 and it was pretty annoying。And that is， if you do a panic and then recover the panic and then rethrow or repan that same value。

 it used to look like this so you would basically get a stack of panic with a message recovered and then a panic message recovered and then a final panic for the top level panic。

 if you will。And now what it will do is it will basically collapse all of them and it will say panic how many times it was recovered and reppaked。

 but it will not repeat the message and duplicate the lines。

And the last change I will mention about the tool chain is that Go 125 requires Mac OS 12。

And it is also the last release to support 32 B windows arm。

Hopefully that shouldn't be an issue for any of you。嗯。

But I believe there's an issue that tracks this。 So if any of you do have an issue with that。

 please raise it as soon as possible。TheThe next section is performance。

 Usually there's a good chunk of performance changes， and this is no different。

The biggest change is a change to Gmex prox。Now， another show of hands。

 How many of you know what Gomax prox is。Yeah， so about half of you。

So Gmax Pros tells the go runtime how many CPUs it can use at once。

 meaning how many goouts can actively be using a real CPU at a time。

 so you can have1 thousand0 go routineines that are alive， but if you only have8 real CPUs。

 it doesn't make sense to try to run all of them at once， right。So by default， up to this point。

 Gmax prox was equal to the total number of CPUus on your machinery。

 That's usually fine for a laptop or a server that only does one thing。

But you can you can imagine that for example， if you deploy to Kubernetes and you have a Kubernetes node with like 80 CPUs。

 but you only want to allocate two of those CPUs to one service。

 It doesn't make sense for that service to try to run 80s to run on 80 CPUs at once or run 80 guoutines eating CPU at once。

 because that's just not going to be efficient it will still work。 It will still run。

But it will do weird things like just cause extra overhead or cause extra memory to be retained and allocated because it's trying to do too much。

So you could set Goome Xbox manually to the right thing。

 but many people didn't do that and it's also kind of tricky to do the right thing。

So they've changed the default， such that。On Linux， it obeys either the CPU limit of the C group。

 meaning the container。Or the available number of logical CPUus。 And don't ask me what that means。

 It's just a thing。And this default also gets updated periodically in case the OS changes either of those parameters。

And like I mentioned， this is especially important for containers。

 Kubernetes and basically any sort of， any sort of virtualization that's not like a that doesn't expose a different number of real CPUus。

 but rather tries to say。The limit or the logical number of CPUs that you have available。

And I believe actually， Bill Kennedy has a talk tomorrow about what a CPU limit means in Kubernetes。

 So if you want to learn more about that definitely go to his talk tomorrow。Another change。

 and this is a big one is Go is getting a new garbage collector called green tea。

And we shouldn't actually say it's a new garbage collector。

 it's more like a tweak on the existing garbage collector because it basically works the same way。

 it blocks your program for as little as possible， it does a lot of work concurrently。

 you don't have to configure anything， all of those all of those qualities still remain。

The main difference is that the green tea garbage collector is optimizes better for really small objects。

 meaning， for example， suppose that you allocate a struct with just one string or a struct with just one integer or a slice with just two elements。

The overhead for tracking those small objects can now be up to about 40% better， less overhead。

And you can use it with Go 125 already by setting this go experiment flag add build time。

 meaning when you run Go build。And for example， the way I would test this is if you have a service and you've measured via Provf that the garbage collector is about。

 say 10， 15， 20% of the CPU cost of your service。Try building and deploying with this flag and then see what the new numbers look like。

Depending how on what kind of objects you allocate， you might see a small drop in the CPU cost。

At least in my experience， small objects are kind of common just because you tend to not when you。

 for example， allocate2 gigabytes of memory， it's not in， for example， 20，100 mebyte objects。

 it tends to be on many thousands of small objects right。

 so this should bring some improvement to Mo go programs。And the issue， which is 3，7，3，5，81。

 That is the full proposal documented with details。 It's only about a 15 minute read。

 So I highly encourage you to go look at it because it's really interesting。

Another change is to the runtime tracer。How many of you know what the runtime tray packages show of hands。

So three people， which is about what I expected。 and one of them is Brian Boorham， of course。

 I can just about see him with the lights。So the runtime tracer basically gives you is a debugging a low level debugging tool for what the what a go program is doing。

 and it gives you lots of information about what the go runtime is doing as well。

The problem with the runtime trace package up to this point is that continuously riding a trace was kind of expensive because you basically gave it give it an a your rid。

 So he was constantly collecting data， encoding it and writing it。

 So even if you gave it a buffer or even if you gave it a pipe。

 it was still wasting a lot of time most of the time。

 when actually what you care about is you want to be recording that data。

 but you only want to actually store it when something interesting happens， such as， for example。

 suppose that suddenly there's a memory spike， or suppose that something panics。

 and you want to see actually what were Gooutine's doing at that time。So the new flight tracer。

 what it does is that it continuously records into a ring buffer。And then you can tell it， okay。

 now something interesting happened， take a snapshot of that bring buffer and write it to a file or to a network socket or whatever you prefer。

And just like before， issue635，663185。It's about a 10 minute read。 It's really interesting。

 and it will also show you the kinds of use cases that people use this for。

Another change is the way go binaries include debug info。

 and this means what happens when you use a debugger to， for example， step through your program。

This has always been done via dwarf information， at least on Uniix and Uniix C systems， sorry。

 Linux and Uniix C systems。And there's a new version of Dwarf called Dwarf5。

And this results in slightly smaller bin and also slightly shorter build times because it's just a better format。

I'm not going to go into more detail than that as before。

 you can always go look at the issue if you want to learn more。😊，Another change。

 which is also likely only to affect about four of you in this room。

Is that if you deploy go to an absolutely massive server and you give it all of the CPUs and you do a lot of network work。

 such as， for example， an HTP server。The scaling actually used to be not great in certain scenarios。

Such as for example， if you have almost 200 CPUs and you have thousands of open sockets or connections that are already ready。

 meaning like users waiting for data or users trying to send you data。

The runtime actually spent a significant amount of time just burning CPUU， not doing useful work。

I'm not going to go into details about why this was happening。

 It's something about Eal that I don't understand。 you can go read that issue。

 It's really interesting。But if this is you or this use case sounds similar to what you do。

 try go1 125 and say if it's better。And if it's not better。

 go to that issue and respond because they。They want to hear from users that do this sort of large deployments and how it's working for them。

Another change that's pretty small is that when you do a make call to make a slice。

It used to be that only constant sizes would get allocated in the stack as opposed to the he。

 and the stack is usually better because it doesn't cause GC overhead。

 it's more local to the rest of your memory and so on。But if you didn't make with a variable length。

 such as an input parameter。It used to never go to the stack。

 so they've taught the compiler to be a bit better about that and now it tries to put it on the stack。

😡，Another change is unique dot make， which is used usually to intern strings。 And that means。

 for example， if you're decoding J and you keep getting the same keys all the time over and over again。

 it doesn't make sense to allocate the same string over and over again for the same key， right？

 So people will try to in turn that string， meaning that meaning basically reuse the allocation for the same string。

 So unique dot make allows you to do that。But it used to be not super efficient because any string or by slice。

 actually that you passed a unit dot make would escape itself so it would it would allocate anyway that has now been fixed。

And a related change to the same API is that the runtime now does a better job at reclaiming inter values via Uni dot make。

 and this was spotted because I believe it was Brad Fitzpatrick。

 he has a long running service in tailscale， and he was noticing that by using Uni dot make。

When a flurry of input requests came in from users and they were in turning strings。

 the memory usage would suddenly spike， and it would take a while to come back down。

And this was basically the logic for reclaiming the memory， not being very well balanced。

 So it would basically hold onto the memory a bit too long， which could cause lot of memory issues。

 so that has now been fixed。The last section is the standard library。

 This is where most of the changes are， but I'm only going to cover about a third。

 The rest of them are on the go125 release notes。The first one is the sync test package。Now。

 the reason this package is amazing is because suppose that you have a function that says。

I will start a routine that does a regular cleanup of files or entriess in a map。

 whatever you want every two seconds and I want to write a test that's real and checks if it did the job right so really the only way you can do this today that doesn't touch the API is by doing a time done sleep of a little bit more than that and hoping that it's enough。

But that's， of course， a race and the emoji on the top was meant to be a man running so you can see the emoji didn't cooperate。

 but that's basically a race between the two sleeps right。

 or in this case a ticker for two seconds and a sleep for three seconds。If the machine is really。

 really， really busy running lots of tests， it could be that those sleeps end in the opposite order。

Or just basically that you're just wasting time。 This test takes more than three seconds to finish。

 which is horrible。Something that you might do today。Is use a fake clock。Which works。

 but then you have to be really careful about replacing every use of the time package with this fake clock。

 and then you have to pass it everywhere as well。So it's kind of a funky， weird solution。

 And this will not work with a standard library。 So， for example， if you want to use。

The Outh package， which does retries every few seconds。

 those retries will not use your fake clock because your fake clock is done in the standard library。

So what happens now is that you can run your test body inside S test do test。

 and they call this a S test bubble。And basically， the runtime tracks this groutine。

And it basically says everything that you do inside this gr routine will use a fake clock internally in the run time。

 So any time you run time at sleep， there will be a fake sleep。

 It will advance the fake clock by3 seconds。And anything else that was waiting for a sleep or a time after or a time dot ticker。

 anything like that will also run if it goes if your sleep went't past that。

 So basically the time is stopped in time。Until you run sleep or you do something like that。

 And the only primitive that you get is a samet as dot wait， which says， okay， I've slept。

 Now wait for all the egoutins that have been triggered by the change in time to finish their job and get blocked by something else or finish。

So this way， when we run insure cleanup happened， we know for sure that the ticker run at least once because it's been more than two seconds and we've waited for it to start and finish whatever it had to do。

Another change is including Jason V2 is finally arriving。Now。

 there's many reasons why encoding Jason as it was up to this point kind of stinked。

And I'll cover some reasons why。It misses many functionalities that people want， such as for example。

 you cannot configure formatting of fields via field tags。

You can't omit or filter values based on the value itself， such as， for example。

 omit any list that has no elements。Marshalling nail slices and maps always produces no。

 which is fun。And you can only in line Jason objects by doing go embedding ofstructs。

 which has its own pitfalls。 So it wasn't the best idea。It also has a number of API deficiencies。

Jason dot decoder has a few traps， such as if you do J do decoder with a reader and then you call deco once。

There's a bug in that， and that is that you're not checking whether there's any trailing data in that reader。

So that is potentially a security issue if somebody is sending you data， that's the JO bb。

 and at the end， there's malicious data。 You're not checking if that's the case or not。

Marshall and Unmarshall don't take options because the options are part of the encodeder and decoder。

And a bunch of other API take buffers， which is horrible。

It also has a number of performance limitations， which I bet is the typical biggest problem for most people。

The marshall adjacent method that you can implement on your own types returns a bite slice。

 which is horrible， you have to allocate the bite slice。

 then the encoder has to take that byte size and copy it over and so on it's really bad。On Marshall。

 Jason takes a bite slice， but that bite slice has to be exactly the bit of Jason that it needs on Marshall。

So then what the decoder has to do is parse those bytes from the input to find the end。

 give them to you。 You need to parse them again。 And then when you go back to the decoder。

 the decoder has to go take what you did and go advance to the next step。

 right So there's a lot of overhead。 a lot a lot of double parsing。It also doesn't support streaming。

 such as， you know， if you want to encode of lots of go objects or decode of JO objects。

 it's actually really hard to do in an efficient way without buffering lots of things。

Andken the token type is an interface， meaning it always allocates， so that's always bad。

And many other behavioral flaws， which I'm not even going to get into。

 but I'm sure many of you know of at least a couple of these。Now。

 this has been cooking for a long time。We first started thinking about a go JNV2 back in 2020 because we were all at home doing nothing better。

The first GitHub discussion with the first draft implementation and draft design came out in 2023。

There was lots of feedback， lots of it angry， but lots of it also really helpful。

And the final proposal with， I shouldn't say final。

 but the proper proposal with a well rounded API and implementation。Came out in early 2025。

So now it's available in 125 behind the go experiment that I showed you before。

 and most of the credit goes to Jo Tsi， who did most of this work here。Because really。

 he's done like 90% of it。If you want to learn more about how J V2 is better and the tradeoffs that were at play and what features we chose to include or exclude。

 there's a really good talk that he did at Gophercon in the US a couple of years back。

 so definitely go watch that because that goes into lots of detail。

And if you enable the experiment in Go125， you actually get three things。You get the new packages。

 J V2， which is the better including Jason。An name of JO text package。

 which is the lower level bits and APIs。 These things allow you to， for example。

 tokenize incoming J or encode JO that token at a time。 So it's a lower level API。

And then what it also does is it replaces the implementation of V1。In terms of V2。

 So the idea is that long term we can delete the V1 implementation。

 keep the same APIs with exactly the same behavior。 but underneath they just call the V2 APIpis。

 So then we don't have to maintain two J implementations anymore。

Another change is safer file open functions。And I'll explain this with an example again。

Suppose that you have a function that serves assets under our directory to users。

 so the user gives you the name of an asset。They might say full slash barge or JPEG。And that's fine。

 But what if they say slash ETC password or the same thing with dot dot？

They could basically read any file on your server， which is not great。

You can fix that already today by inspecting the incoming name stream， such as for example。

 there's a file path that localize function。That basically forbids things like absolute paths or dot。

 dot。And that does handle the case that I showed you before。

But what if you happen to have a sibling in the assets directory that points to a file that you should never be sharing Now。

 you might say this will never happen to me， but the reality is that you don't know there's no reason for you to allow that possibility。

 right。So the new API that you have is called instead of OS that open file。

 it's called OS that open file in。And the first argument is apparent director bath。 In this case。

 the asset director。And this tells the Os， whatever you do。

 you're not allowed to open any file that's outside of that directory。

 So this is basically the Os assisting you， right， It's not just looking at the string。

 So this will work with slinks。 This will not let a slink point out of the directory。

On Uni C is like Linux， this uses the open at system call instead of the open call。

 which is basically the same idea。And on Windows， there's an attribute that you can pass to open file called root directory。

 And it's basically the same idea。 This open call has to be underneath this root directory。

Another change is an interface。We' we've had Io DataF for a long time。

 which is read only file system abstraction as an interface。

But it only has pretty basic operations on it like open file。 It also has read file。

 It also has read directory， things like that。 It allows you to basically like walk a set of files and open them and read them。

But it it doesn't have support for Ss because Ss don't exist in all operating systems and file systems。

 right？But now there's a new Read link F interface that extends IOFs with two methods， Read link。

 meaning take this， take the same link and tell me what it points to。And Ltt。

 which is like stat to get the information about a file， but without following siblinglink。

And Read linknk F already comes out with support from DF。

 which gives you an AOFS for my directory on your system， so that includes some link support now。

 as well as a bunch of other APIs in the sound library that take IF。Another change is Wadegroup。

go in the sync package。Now， thankfully， this one is much simpler。 So with weight group。

 you might do something like this。 Start 5 go routines， have them do some work。

 and then wait for all of them to finish。😊，So what you can do is replace the ad and done with a single call to Wgroup。

go。Pretty simple， but pretty useful。Run under to that cleanup now runs cleanup functions concurrently。

And that basically means like I mentioned before， if you add cleanup functions that run when an object is garbage collected。

 it used to be that they all run sequentially， but there's really no reason to do that now they run concurrently。

And the reason this was sequential was because the old set finalizer API was sequential。

 So this copied the same detail。But there's really no need to keep the same restriction that's just historical for no reason。

The next one is in net HTP。The cross origin forgery handler for modern CS RFf protection。Now。

 I could stand here and pretend I understand how that works or what it means。But instead。

 I will do you one better。The person that wrote this feature is at this conference， it's Fipo。

 and you will spot him releasing because he's the only engineer with a laptop that's wearing a suit so。

😊，If， if you see him， definitely go ask him about this because I cannot for the life of me。

 understand what's modern about it or what it's meant to protect against。Another change。

 this is technically an AAPPI， but it exists purely because of the performance aspect of it。

Instead of with a reflect value， instead of calling interface to get an empty interface and then type asserting that to a type to get like a real go type value。

That allocate and it's pretty slow， you can now directly use the type assert。Method on value。

 So that that first line at the top is not entirely correct to directly type us sort into a type。

Same idea。 much faster。Another change is in the testing package。

 you can now attach attributes to a test or a subtest。

And these will be also shown by gotation in a structured way。

 so they're basically a way to add extra metadata to a running test。And here's one example。

 suppose that you're testing a feature and you want to say this is interacting with a remote service。

 so I want to record what request I I'm using in this test because later if something fails or goes wrong。

 I can always connect that to the server site。😡，So what you can do now is set that as a naturalcut when you run go test。

 you will see that line in plain text， but most importantly with Jason。

 this is not just plain text that you have to parse with Jason this shows up as a separate J object that you can easily understand。

Another change pretty simple in testing， you've always been able to log messages as part of the test。

Now you also get an output rid that you can pass to other logging libraries， for example。

 because many APIs in terms of logging， they take they sometimes take an IO rider。

 which is a bit lower level。 So it was a bit difficult to shove that into testing to ti log。

 you have to sort of write your own rid that made costal log。

 So now you have an output writer directly。Another change， again。

 pretty small is that the regular expression package now supports Unicode category Al Aaseis like backslash P letter。

Most of you probably don't know what that means， it's just another way of saying a category of characters or letters。

Another change， and it's again， a convenience。It's in the goA ST package right now we have a preor iterator to basically walk a tree of ghost syntax nodes。

And it does a callback for every note in preorder that you're walking over。

So pre stack is exactly the same thing， but it gives you also the stack of parent nodes as a slice。

 so if you want to do anything as part of the iteration that depends on what point of the tree you're in。

 this is actually pretty useful。And finally， and this is getting pretty niche at this point。😊。

In the Go types package， there's a type called var。

 and that represents the type checker any variable。

But the problem is that Go has many kinds of variables， you've got globals and locals。

 but you've also got parameters， you've also got fields， you've got quite a few of them。

 and it was always a bit tricky to be able to differentiate them as you wrote， for example。

 a static analysis tool。So now what you can do is use the new kink no， that's meant to say kind。

That's meant to say kind。 So that basically just gives you an enum with what kind of variable you're dealing with。

Now， if you want to test， if youre want to try， go 125。Because it released about 30 hours ago。

 you might already have it as part of your package manager or a OS， but if you don't。

 you can either export that first line above， and I will tell your current go version to download this newer version and replace it。

 replace yours with it。😡，And you can also set that on a per module basis。

 So whenever anybody works on your module， they're also told to at least use G 125。

 And if they're on older version， it will transparently do this tool chain upgrade。

So that is all I have。 and before we take some questions。

 here's a QR code to the slides in case you want to Thank you。Yeah， great talk。

 Thanks very much for that。 It was a really good overview of what's coming。

 I know this has been a bit of a hot topic on the community。

 But you think that we're going to start to see more V2 packages。 And if so， what。😊。

That is possibly the most dangerous question I could get asked。But the answer is yes。

 these answer is that including Json V2 is actually not the first one because we had math Rand V2 already。

 because math Rand already had a bunch of issues and， and。And downsides。

 So mathth Rand V2 was the one that basically set the path for everybody else。

And the path is basically the V1 package stays where it is， we don't break anybody。

We try to do the V2 as best we can， and we try to rewrite as much of V1 in terms of V2 as we can。

So it's basically don't break anybody， do the best job you can， but at the same time。

 try to not maintain two versions at the same time。With V2。

 we've done that as best as we've been able to。There's a bunch of other contenders for sure。

I would say log was another one that was done。 you can think of log's log as kind of log V2。

Because it's structured logging， right？There's a bunch of others that could potentially see similar treatments。

 I think one that keeps coming up is net HP because net HP works really well to be fair。

 it's used by a lot of people， it supports HP2， it will support HP3 as well。

But it has a lot of food guns。So， and it's also not very efficient if you do very high throughput so。

I believe it's been in the talks for a long time， but because it's such a large package that used by so many people。

I think it's going to be a very delicate project。 I mean， just think about it Jason took five years。

 I think H TP2 might V2 might take like 7， right so。Thank you。

right hellello all right thanks for your talk enjoyed it Yeah， just a quick question。😊，So obviously。

 the J package being updated， that's really great。 And there was issues potentially with performance on the marshaing and un marshaling。

 Do you know of any benchmarking that's been done on。And also。

I noticed obviously that it's experimental， you know， theres a timeline to release it。

Properly or so I couldn't hear very well。 So I think you're asking mainly about benchmarks。

 is that right， Yeah， Jason Marshallling benchmarking between the new and the old and also the release timeline between like making non experimental。

 let's say。Yeah， so I'll answer the second one first because that's easier in G125。

 it's behind an experiment that the optimistic plan is for go126 to flip it so that the experiment is on by default。

 but that of course， depends on how many bugs and issues are reported in G125， If we were to find。

 for example。A big API flow or design flow and go125。

 that will probably push it back by onevol cycle just because it's too risky otherwise。

In terms of benchmarking。There are some high level benchmarks that V2 is doing to compare against V1。

The good news is that the decoding is way， way faster， like more than twice as fast。

 just by using the high level APIs。The marshalling。

 the encoding is only a slightly faster because V1 was already pretty dumb fast。

 So V1 was really slow with the decoding。It was actually reasonably fast with the encoding。

Where V1 became extremely slow was if you used the martial Jason and im martial Jason methods。

Because effectively， what happened。Is we we found this issue with the Coreres project。

 The Corernees project has its own way of encoding and decoding into Jason or Yao for that matter。

 So and they have multiple levels of these objects。 like， for example， a a bagg。

 potspeg and then container， whatever right。 So each one of these types had a marsial。

 an unmartial JasonO method。But because each one of those takess a bite slice。

Every time you call a martll Jason method， you're duplicating the work for everything that's inside of it。

Now， if you have three levels of that， you're basically。

 you've got an exponential problem because you double here， you double here， you double here。

 it's two to the power of three， right？So V1 was extremely slow for large projects because of because of this。

 basically， so V2 doesn't have this problem。 So the marshalling in V1 and V2。

 if you don't use that is only slightly faster， but if you use that。

 it could be thousands of times faster。 It depends on what you're doing。Okay， any other questions。

 anyone from this side？😊，my。So the the fake test clock is there been any considerations to making sure that there's not like any false ordering with regards to the race detector does does it do anything special to make sure that races are still。

Detected when run with the fake clock。It's a good question。

 I actually have no idea because you're asking about the race detector in the runtime， right。

So the race detector， I know that some of the things it does is basically add a bit of randomness to the scheduler and not a bit of randomness to other bits over their one time。

I would imagine that some of that randomness goes against what sync test is meant to do。

 so I don't know if you can use both at the same time， maybe try。I'll do that。😊，Any other questions？

Actually， now that I think about it， you probably can use both because otherwise it would be a breaking change。

 but I guess the better question is， is it just as effective with a synt' bubble that I don't know。

Yeah， as someone， obviously， with the finger on the pulse of all these changes coming up。

 is there anything in the next couple of years or of the next four versions that you're looking forward to seeing like any big changes coming up。

So that would be an amazing question to ask to the only person on the go team at this conference。

 you can you need to get a group of people and corner him somewhere so they can run away and then question him。

😊，But more seriously。I'm not aware of any language changes that are upcoming。

 at least nothing that they've shared。I know there's a bunch of plans for the runtime and the standard library。

 such as for example， finishing the green tea garbage collector。嗯。Nothing else large comes to mind。

 I think we've gone through a cycle with generics and。We had generics then we had iterators。

 and that was a lot of work for the team on new features for the language。

And I think now we might slowly transition into a quiet period where they work on more like internal details and performance。

 That would be， my guess。嗯。At least personally， I would like to see them work a little bit more on certain aspects of the compiler。

 Like it's still not great at inlining function calls。

So if if if the function colon in liner was better， that could give like a 5。

10% improvement for many go programs， for example， but it's a lot of work。Yeah。Yeah。Next question。

All right， no one else tempted it。All right， big hand for Daniel Marty， everyone。 Thank you。😊。



![](img/c06ef113ce62dcb458bb3c9c467c1a5a_2.png)