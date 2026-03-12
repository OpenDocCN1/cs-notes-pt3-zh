# LLVM开发者大会-US-｜-2025-Llvm-Developers-Meeting-p12-P11_关于AArch64上BOLT的教程及其与PGO的竞争或互补关系--BV1ejr5BAEja_p12-

![](img/ec46fba408a5595c2ce7f3f0e279e2ae_0.png)

Hi everyone， I'm Pasalis， our Q。Welcome to this tutorial。

 there's going to be some extraordinarytroductory talk on B。

With some emphasis on Air 64 and some comparison with some other PGs。

PGO or profile guide optimizations is any technique that uses profile data to optimize some code。

Which essentially makes。PGO sorry， B the P Tech as well。

So both and these other IPGOs can deliver great speedups。However， they are not so polished。

They may require some excess steps to apply them， some of those steps， for example。

 as we see letter with bolt and profiling， have different ways of doing them。And on top of that。

 there is some overlap lag between what Bolt does and what these other PGOs do。

 which creates some confusion。So today I'll add some background to try and help a little bit with that。

So I'll start with a modrating example and the solution around code layout。

 which is the main thing that Bolt does。Then I'll go into bolt。

Explain it and explain also and compare it with a few other PLs or post optimizers。

Then I'm going to LBMGs。And with some background， I'll try to answer some questions like what's the difference between the two。

 which one should we pick， given that LLVM can do code layout， then why bolt even exists。

And towards the end， there'll be a demo。So try not to fall asleep。

 So this will be like a packed talk and as we said we Q& A at the end around 4045 minutes。

So let's get started。So we'll see what is a problem of code layout， how we know we have this problem。

 and why compilers need some help to deal with this。

So say you have a binary that we want to exc in our processor。And we start our execution。

So well load some instructions from the binary into our instruction cache。

And then there comes a branch， so we move to a new location and we have to load the instructionss from that new location into our IC。

And then there comes another brand。 So again， we have to load direct cash。 and then another one and。

This can't keep happening。Which is normal， like called us branches。However。

 you have to keep in mind that not all code is executed uniformly， some functions are hot。

 meaning they run more often or they run for longer。While some others are cold。

 they may not run at all or they may run for a little bit of time。 and the same for basic blocks。

 just a few of them are good。So when our hot path travels long distances。

 it is when we have bad spatial locality。So essentially， our hotness is spread all over the boundary。

So how we know we have this problem， the answer is of course to use some hardware metrics。

And one way to do so is to do the top down methodology So when our workload is front and bound。

 then we kind say that this may be a good candidate for optimization。But on the sun for the boldness。

 I brought up a pipeline of the CPU。So the front end fetches instructions。

 decodes them and then dispatch them for execution。

 and then the backend is going to execute those instructions and write back some results， etc。

 So the problem is when the front end cannot fit the backend quick enough with instructions so it stalls waiting for things to execute。

And when it's more than 10%， we can say that this is a good candidate for。Leal optimizationization。

 is a。This could be due to eyeage misses， eyeTby misses or branch mispredictions。

 which may need some rollbacks。And when it comes to bolt。

 the rule of thumb from the bolt authorities is when we have more than 10 meus per instructionss。

And more than 30 is a stronger indication。But again。

 these are rulesrs of thumb we can use a top down tool。

 which is linked there on Air 64 and I'm going to try to demo later today。

Or we could use per to this ourselves？We should be soon able to use ATP or Ar performance。

Is a brand new tool。So I'm not going to try to demo this today。

 so here you have like a front end bound workload with some eye catch misses it has some nice extra things。

 we can do top towns per function， can do hit mapps。And its listed somewhere publicly。

 but not officially public yet。 So keep an eye out。只管了标志。Now let's see why compilers need some help。

I will bring on a flow of of clang。 You're going to see this throughout this talk。

So we start with our source code， then the front Engine MIR。

 then go into different optimization passes on the IR， then we continue on the MIR。

 then we get some machine codes， some object files， will link those together and get our binary。

And the problem is that at each of those points， all the compiler had with some heuristics。

 So what we need is some intelligence on the call graph and the control graph。To figure out hotness。

 which it's impossible to use a risk for this。And when it comes to LTO。

 I'm going to define LTO because it's often used with PGO and it should be used by PGO。

We start similar initially。WWe has run a lighter pipeline on the IR。

And then we bring all the bitco together。And then we run a second pass on the IR that can do better IPinpo optimization。

 it's going to be more heavyweight and more capable， and then we willll continue as before。

But this suffers from the same problem is still going to use heuristic。

 so it cannot help with code layout。So it'll be clear that what we need is to reor the code。

And to do so， we need some profile data。So now I'll jump into the solution。

 which essentially is going to be some background that around these two areas。

There are three things we could do the first one is to reor the functions。

 as we saw not all functions are hot， so we could just reor based on hotness。

And once we do some of those expensive jumps that cause disruptions in our CPU pipelines are going to be eliminated。

But there is more we could do， we could do this on the basic blocks because just a few of them are hot。

So once we do， we essentially optimize for the fall through case。

Which means that once we enter such a chain of blocks。

 the chances are were going to stay on this chain until we are done before we have to jump to another one。

And this is a TP problem travelling system problem per per function。

But there are still more things we could do because when jumping between different traces。

 different chains of those host blocks， we have to cover some distance that include some cold code which might again cause some disruption in our CPU so the last thing we could do is to split the code。

Into a thin hot section and the bigger cult one。 And we are kind of lucky when it comes to cold layout。

 because。Usually， just a small section of the banner is going to dominate execution。

 So think of like hot loops on one end and on the other extreme and things like， I don't know。

 exceptional handling blocks that should be there， but never on the on the hot。

Now to the second part on profiling， I already defined a PGO。

 we also have the FDO term pit driven or direct optimization。This is similar term。 It may have some。

Suppletheical differences。But want what I want to note on this slide is that PGOs are way more than just layout。

So I'm going to search on provide summaries in LLVM。

We can find all these matches and from all of this， just the highlighted ones。

Are more closely related to what Bolt tries to do。And if I continue on this small exercise with trying to look on block frequencies and branch probabilities and I restrict this for registers。

 something unrelated to layout。And something that is quite specific。

 So it this like a small slice of the profile data， we can find even more matches。

 So the point is that， you know， PGO is way more than just code layout。

And now quick link to the profiling methods， those are three， of course， different instrumentation。

Is when we modify our binary to get some accurate accounts。 We come to per function or per block。

 This is going to be super slow， which might be a problem on a production environment。

And it's going to increase the binary size， which might be a problem on a mobile device。

But at least we get the best the highest quality profile。

 which means we have the highest optimization potential as this is quite intrusive。

 we have sample based approaches。The idea here is simple。

We get some approximate counts and we hope that we're going to reach these same conclusions。

Only are 64， we can use units like BRB。With tools like PEth， and this should be faster。

 but the quality may vary， so we'll have to check whether we captured enough information。Otherwise。

 we can limit our optimization potential。And the last approach is called tracing is when I'm using units like ETM or Eta on Air 64。

 and those generates huge volumes of data， which means overheads， but I can tricks to limit those。

And onto to some challenges。As I explained， the environment might impose some restrictions。

 for example， instrumentation on a production environment might be prohibitive。

Or the binary size on a mobile phone might be a problem。ItAlso may have restrictions on the hardware。

 like I mentioned BRB， but it's kind of difficult to find an Air 64 machine with BRB today。

We also have the trade off between profile quality and the overheads。Again。

 experimentation is the best profile， but it has the highest overheads。And sample base approaches。

 we can play around this overheadhead this trade off， sorry。We can increase the sampling frequency。

 which means higher overheads and may mean higher profile quality。

So we have to make sure that we are happy with both the profile time overhead and the optimization for。

And of course， our workload might change。 so if I take a profile today， maybe in the month。

 maybe it's not good enough， or the code might change。

 which may mean I have to repeat the profiling step。诶。And all these are to to。

To the challenges and the last one， which I'm going to dive deeper because is related to this comparisons between B and L MPPGs。

Is a problem of correlation and maintenance？So if we consider this flow， I showed you earlier。

 say we use Kang to compile some binary and then pair to get some Perth data。

So those perf data were captured by sampling a binary， so they are at the binary level。

 when we start using PGOs， we start compiling with the sources right so we have to go through the process of correlation。

From the banner level into the source I。And this is a process that can lead to some profile quality loss。

 which means we might limit our optimization potential。

And then as we start optimizing and go through all these passes。

 we have to maintain the profile quality， the previous talk mentioned some issues on the the info as well。

 so that we go into those transformations， they higher the chances some might distort or ske a little bit our profile data。

 which may mean that we might limit our optimization potential。And its will also mentioned that。

 you know we are humans in the previous talk， and we can make mistakes。 so in this case。

 the code was swap the successors。But the profile data themselves were un swapped。 So as a result。

 any pass after this one was going to make some wrong assumptions。So this is tricky。

 that's what I'm trying to say。And this was some background。I will now dive into both。

We stands for binary optimization and layout tool。It was created by Me and more than a decade ago and they've used it this many years in production。

And it is a PLO or a postling optimizer。So from this flow， all we care about is just the binary。

Actuallyly， we don't mind whether Jesus or Kang was used to。Generate this boundary。

So all we need to fit to both is a binary and a profile。And that's all。

So boltol can then disassemble and understand this binary and do the process of correlation to attach the profile data into the Bs IR and the benefit of bolt is that this IR is on the assembly level。

 it uses machine instructions。For which we can say that bolt is a kind of like a low level PGO。

Because it makes this process of correlation and maintenance way more flat。

So it can have high quality profile， even with sample based approaches。

 when and where it needs to use those。It support layout， which is roting functions， blocks。

 and splitting the code。And once we do that， we can get our bolted binary。

It supports all profiling methods I you read earlier。

 I'm going to try to demo most of those today and some variations except tracing。

And now I'm going to do some comparisons with some other PLs。So here I put up a code locality。

 which is essentially a simple set of scripts。That are tied to a particular processor。

 and technically， it's a kind of a PLO。 So I put it up for comparison。And propeller， which is。

 I would say， the main competitor of both。When it comes to the input binary。

 bolt does not require a compilation so we can。Take a banner from the white， and just recompile it。

Reored it， however， we need to run the full layout， including function reoring。

 we need to have the locations preserved in that binary。

The good news is that those locations just take a little bit of extra space。

 so it's not going to be a bit of a problem to add this into our optimization pipeline。

The rest of the tools code locality。For example， we willll need some objects that have sections per function and propeller will need sections per block。

When it comes to reing， this simple locality tool can reor just functions and the rest of the tools can do the full thing。

And on the compiler support， both and the locality support both LLVM and Gno。But to be fair。

 the locality tool again， is a bit simple， so it was not so hard to like invoke a different link here with maybe slightly different commands。

Also bolt officially supports CC++ binaries， but we have partners that use bulk to optimize goal and binaries as well。

Proeller requires the LVM tool chain。And maybe a bit more tricky to integrate a little bit more effort to integrate into the build system of the programs you want to relay out。

When it comes to binaryarywriting。We can say that bold is awriting tool because it disassembles the binary。

 understands it。And then re linksx it， and this extra knowledge gives an advantage to both。

So it can run some extra optimizations。But it runs on on the binary level。

 so the source area is still some assembly for me say。

 so it's not like that we can replace what we can do at the LVM level and do at post still it's nice that it has this advantage。

 The rest of the tools do not have this。But the fact that they are not rewriting could be seen as an advantage by some。

Because someone could trust some software call a linker to do the original layout and the original link here。

Original linking， and then they have to trust this same linker to relay and relink this binary。

When it comes to bolt， someone has to trust bolt to do this relinking。

So this was bolt and PGs some Ps in an nutshell。Now let's see how things are done on the ELium site。

So Kang on its own uses heuristics and with PGs uses profile data。With Lt on top。

 well have this extra pass for better IPO。Onto the providing techniques。

We have a sample baseGO or SPGO or auto to have the other many names here。For the same thing。

 and for that， you could use branch stacks。OnR 64， this will be BRB。

 which is a buffer of branch records。That allows us to effectively sample the control flow in the call graphs。

It's kind of optimized because it captures just the branches。

And that is because we can't infer any forth truths in post processing。It of course。

 supports instrumentation as well， we can do this on the front end level。And on the IR。

And also have a contact sensitive variant。And to see what context sensitive it is。

 I'll put up an example。So you have a that calls P bar 20 times and all of the time it's calling P。

And then a B that callss fu bar 10 times， and all the time it's calling bar。So without sensitivity。

 we can know that4 is called 20 out of 30 times。But with sensitivity。

 we can make an assumption that for example， A ends up calling F for all of those times。

 and this could be powerful with some particular workloads。Now let's see how LLVM does code layout。

Functuaaling， it happens at the linker level。When we use PGO， this is Tu alone automatically for us。

 but we will also use author files and do this ourselves， for example。

 the propeller and the locality tool this is what they are doing。When it comes to block reoring。

 this happens at the various stages of the MR pipeline。

And it has to run anyway because you have to emit those blocks， even without pro data， of course。

But when we do have profile data， it runs TSP with an approximation anyway。

 with those data to do a better job。When it comes to splitting。

It happens at the very last point that is still feasible on the MR pipeline。And by default is off。

 regardless whether we use PGOs or not。And to my understanding with CSPGO plus LT or plus sp。

We could get to the closest to the effect that boltt does if we do not want to use B。呃。

Bold would then refuse to。Re layout out such a binary， which also means that without splitting。

 we can apply board on top of those LLVMPGs。Now some comparisons between LLVMGs and B。

So on the LLGM level， we are on a higher level。And there are many， many more things we could do。

 So this is like way more powerful than than both， of course。

But this creates the problem of correlation and maintenance， which I noted earlier。

Especially the sample based approaches can suffer from correlation。

Because we capture a profile at the binary level， and then we have to start compiling with the source I。

And。Any approaches， including instrumentation based approaches will have to go through maintenance。

 which may lose some of the profile quality。And the deeper better we go into those pipelines。

 the higher the chances are to increase some of this skewness or distortion。

 and if you remember it is at the lowest late stages of the pipeline where code layout happens。

So this is the benefit of both is that it has high quality profile at the point that it needs to use it。

So when people ask when which one is better， I think we have like two different levels。

 two different tools to solve different problems， high level and low level PGs。

So when people ask which one should we use， I think the answer should be both。

Given that theres a Qta allow， for example， one could go with IrRPG pluselo and then bolt it on top。

 that's one combination。In this slide， I will go through a few more PGs， because we have。Mippios。

 some of those are more。Are tied to some particular workloads。

And may not have support for most of the targets。Starting with CSSPGO。

 we have an anex as here is contact sensitive sampling。

It combines the branch stacks which saw earlier with call stacks to bring contact sensitivity。

 that's the first of the two features， and the second one， which I think is more generalized。

 it uses pseudo probes， which cause minimal runtime overheadat。呃。

To essentially attach some unique ideas to each basic block。

 which helps a lot with the process of correlation。 So with like a pseudo instrumentation。

 we can like increase the quality of our profile。We also have a hardware PGO。

Which is an extension to SGO to use data for more hardware units。

When the authors of this RSC have introduced it， they've used branch prediction information。

To figure out whether and branch is truly unpredictable。

 And theres some information that may be tricky to get with， even with this instrumentation。

So when a branch was truly unpredictable， they took alone if conver。A more recent that I've seen。

 which I think still falls under this harder picture umbrella。

Used memory profiles to optimize Vi loads。Out of the hot pass。And we could do data locality as well。

 We don't have to do just code locality。 for example， we can split the data sections。

And we can do temporal locality too， not just spatial locality。For example， mobile appss。

 though those apps might not even be CPU bound。So what we care is to load an application faster。

So we try to lay out an author in which we will need the least amount of memory pages before we are our rabbs have been running。

 which will mean less page faults and less time seeing these splash screens on phones。

So this was LLVMPGs。诶。Now let's jump into the last part， which is going to be quick demo on Air 64。

So I started with a pathological case。Initially， we had a binary where the quote coat was like spread all over this binary。

And it caused some disruptions into the CPU pipelines。

This will most likely be the case with many data center workloads。Or with。

Some more complex bin because the compile by default cannot you know do good layout。

 but for this demo I wanted to come with a simple program that trans fastt has no header files。

Can of even use instrumentation with it， no dependencies。So I pick bubble salt。

Which is an example that GCC uses as well。But on its own。

 it was not good enough or maybe bad enough for both。

So I did a few changes to make it more interesting。

 so I took the swapping part and wrap it into function。

Then I've added some control flow with some knobs， which never run。诶。

So bulk has to figure that out and push them to the side。 I made a few copies。

 and then I've added a few more functions in between those。

So B has to figure out that these yellow bits， which are the hot ones。

And stitch them together and push everything to some cult section。

And this is still like 100 kilobytes， so it's not a huge buyer。

But I want to note that this is not like a typical case for the size of these bin like terrible has terrible locality。

 so I'm just going to demo usage here， your Viage may vary in real life workloads of course。

So don't focus as much on number similar I'm going。Make some comps myself。All right。So。

You can use your favorite compiler to compile this program。

I was expecting that both works with both GCC and LLBM。Let's go minus over3。Because why not？

 And let's keep it locations because we want to do the full layout。

Here I'm saying to GCC to keep this order that I show you in the binary。In the source file。

 so it doesn't try to do anything to change it。But let's confirm this。Let's dump those objects。

Though simple。 sorry， Does itmangle them。Can this up a little bit。Ja the text segment and。Functions。

So， maybe not near that。So we have a swap function and C one， s cultt。

A smaller swab and a bigger cult function。 So it looks like this picture。But we hope before we start。

 we have to make sure that this is indeed a bad binary。 So let me run top down。S I go up。嗯。

Can see that we are 55% bound on the front end？And。This was due to 60 L and I catch Mrs。

 Perkilo instructions。And we also had quite a few branch misses。

Praccu instructions and both could help a with those as well。All right。

 so now we confirm that this is a binary， so let's try to optimize with bold。

I'm going to start with instrumentation， so let's instrument this binary。

My input binary and my output binary。Do instant。So once I run this。

 Bolt will place profile data into this location by default。

And it's going to be on the F data format， which is the format that bolt understands。

If I run the original binary。Just to see how how fast it runs。

And I'm going to run the ised one to generate this profile。And is way slower。

 which is what we expected。I'm going to move this into more comm location。

And I'm going to apply both with a full layout， my input binary。My provide data。My out binary。

Tot top dot inst， and the full layout。Reorta functions。With hot function sort。

What are your third blocks。With TP approximation。When a split functions。

And I'm going to keep knobs because bolt tries to remove those by default。

And I wanted to simulate you know cold code， so I don't want to cheat， keep them。

 but push them to the side。All right。So now if I run the original binary。Three times。

And the bolted one。It runs in around half time。But again， your mileage will vary。

 don't expect to see 2 x on each workload。Now， let's。

Ran the top down to confirm that we have improved。This binary， to see that the metrics reflect。

They on time。So from the boldness is down to 30% from 55%。And。On the L1 Ikaashmi says。

 we have wh less than 1%。Thenhan than one， sorry， particularly instructions。 this not percentage。

And the branches are down to 10， I think these were like 16 or something like this。

So we did a good job。Now I'll try some other profiling methods。I will start with B R B。

 So I'm going to use minus J for branch tags。 I'm going to capture any type of branch called three。

 conditional， conditional。On the user level， because we are on the user level。

And if you remember I told you that BRB is not widely available， I was not lying。

 I don't have this on this machine。But I've taken a BRB profile from another machine and I put this on this one that I could use on the demo。

And let will show you how that looks。So I'm going to print the B stack。My profile。这个 here。

So line 22 is a single branch stack。With all those branches。

 we can figure out which bes are hot and which are cold， and we have around 26000 of those。

Of those events。Because this is like a PE profile， we have to convert it into F data so both can't understand this。

Some'm going is per to bolt。One could use。Other other tools like ABPF or go through some other routes and in which case they could convert manually to this F data format in this case I'm going to go with pair to bold。

So I put my input binary， my profile。And my converted pro。All right。And now， I'm going to use。

Bald with。BRBE。Its the same command as before the full layout just using BRrb dot F data。

 which I just converted。And petm extension。And if I run the times。We get some good results here。

 as well。The next protocol we use PEf could be armP。We can capture just branches。On the user level。

 again。M이 good banner。And then we have to convert this with pair to bolt。My input binary， my profile。

My converted profile。Do us S P at the end。Because both has to know what type of profile that is。

And we can bolt with S P。Again， this， the same command as before， just using the S profile and。

Give her an extension name。So if we run this three times， we can get some good performance as well。

I'm gonna comment about all these approaches when I I'm done。 There is still one。Method we could use。

 which is called the basic sampling， we could use。Instructions or cycles。

 I'm going to go with instructions。On the user level again。

My profile going to be PM u datata after the name of the unitity near I 64， but it's just naming。

Okay， so I captured the profile and I could convert this。My input banner， my profile。

My output profile。That just BA because it's a basic sample。Not cutting bolt with the PM U。

Same command as before just using the event prop data。 And if I run this new binary。

We can get some decent speed up， as well。So with PMU， we have like a single IP for example。With SP。

 we have like a pair of branches。Those could not be expanded unlike BRrb。

 which those could be expanded。 and what this means is that in in theory。

And most likely in real life， we're going to need way more overhead to capture during sampling。

 a profile that will have the same quality as with Brb， so Brb will be your best bet。

If you don't have VRB and you don't mind experimentation， you could use it。You could also try ETM。

Orette， maybe with some strtroobing to manage the overheads， but I'm not going on demo this today。

And alternative， you can use S or or PM use。 But in theory。

 you can even use PM U and increase something this much that could。

Much instrumentation numbers in terms of optimization outcome， but this is dependent on workloads。

Right， so this was some usage because I said that the quality may vary and you have to play around。

Bolt has some stats to guide you a bit on this。And I'm going show some。

 I'm going to share some insights behind those tabs。

We have the code density added by meta based on some pro implementation。So essentially。

 when we want to optimize with。Withvol， we expect that some bits of the cold are going to be hot。

 and if we don't find some dense regions in that binary。

 we assume that we need to capture some more profiles。

We also have some continuity metrics that try to。Tell whether our profits are making sense。

And those are based on three observations。The first one is continued on the control flow。

 So you have a blog that accepts some samples。Then there has to be some path from the entry point that is capable of passing those samples。

Of course we may lose some along the way， but there has to be such a valid path。

On the callgraph conservation， say we are calling fo 10 times， then the entry points of fo。

Should proagate these samples further into the function。And the last one。

Conservation on the controller flow。Say we have a block， not an entry block。

 not an exit block that receive some samples。Then those samples should proagate further in in in that function。

 And these numbers are like perfect numbers。 So some heuristic are combined to。Show some。

 some stats to， to the user。And the last tool that I'm going to show is called Hi map。

It helps us to visualize a profile to see where some samples are like in a binary。

 So what we need is a binary just a per profile。So you don't have to combine this with both。

But I'm going to show before and after bolting a banner to to visualize how things are。

On the left hand side， you see some range of addresseses。Per per line of。

Of this hitm on Toby some representation to figure out where we lie on that line。

 Don't focus that much on this one。 and that's the main hitm。Un empty line means a gap of。

Any size could be of any size。And。A character is a block of code。

 We can configure the size size of the block by default is is the cache line。

This is hardware dependent， of course，诶。And a letter means we have a sample which also points to from which function it came from。

And the color can tell the hotness。If there is no color。

 then we have the least amount of samples and when the letter is lower case。

 we have even less samples。And also meet some other starts， like。

How much hotness comes from which which function。From which sex， I'm sorry。

So I'm going to demo hit mouse as well。I'm going to try this on the input binary。

And I'm going to use the last profile I've taken。Again， with BRB data。

 this is going to be more accurate。Because it's going to be more a better profile。But here。

 I'm going with a basic example。So if we see how those samples look like。

You can see that the hotness is spread， essentially the same as the picture I've shown you at the start of the demo。

And if I take another profile just like this one。Sttractions。We could try any binary。

ICould go with the instrumented one。PM U dot of install data。And my intervention。谁他 kidnapn。

Minine food battery。呃。Do， my profile。PM U do do Ins， my output hitm。Pm u of the instance。

basicic simple。So we see this new hitm。We can visually see that we did a quite good job。

 So all samples fall into justice。Area of code。It's an extra verification that。How the profile data。

알 touch to the banner。But if we try in real life here， have a zoomed out example of a database。

And if I'm going to scroll through this bigger binary。

 you can see some colors and some samples that are spread。All over the place on this bigger binary。

And if' just stopped if I go to the the after picture after bolting， you can see many colors。

 many samples， all these。Being compact on on on a small。Hot section。And this， I scroll。

You will see weightless samples， no colors， maybe lowercase letters I cannot tell。

 but probably and lines bigger empty lines， bigger gaps so we can say that we did a good job。

So this was the demo， essentially。And that's the we recently bonus slide， so we are a team at arm。

 we are working on B I'm a maintainer of the Air 64 backend， we try to help with patches。

 reviews and testing。We are very thankful to have a very active community on LLVM。And of course。

 by the I called tometa for this great tool， this is their work。And both workss。

You can get some really nice numbersers。Try with top down see if you have some good candidates and then apply both。

And if you then help， reach out on Discor on this course。

 on LinkedIn whenever we also have office hours every second Wednesday。



![](img/ec46fba408a5595c2ce7f3f0e279e2ae_2.png)

And we will hit the roundtable later today， 415。So that's mostly lead。诶。

A tutorial version will be uploaded on this link。I just have to write it based on these slides。

And that also。Thank you very much。Great， thank you so much， I guess we have。😊。

Around 15 minutes of questions， so plenty of time for questions。

Thank you for the lovely tutorial I had a question about the requirements for using board So if you said that LLVM okay basically I'm using Swift。

And it has an LVM backend and it also has PGO flags， at least I have not used them yet。

Can I expect it for both both to work out of the box or is there going to be some work required so officially support CNncC plus bin and。

Ep piers as well。So if that banner itself， you can give it a log and see what will happen。

But it won't be officially supported。I cannot tell I haven't tried this。

 I don't know if Meta has more information on this。Okay。

 but what I know is that some people have used。Have you seen with goldland pine。

 which are not officially supported？All right， okay。

 I'll say this is one more thing so what is the typical speed up expected。

 say if I have a program that is just within the rules of thumb that you described for wanting to use bold like what does the typical improvement look like？

So it depends。 We had cases where we had like 40% speed ups。And this was a particular program。

 I'm not going to name it that。Inlined some functions many， many times。

 a few functions well in line like thousands of times。 something went wrong。 I'm not sure。

 And for those particular binaries， it was able to do quite good job。

And this was binaries like published by someone。For their uses to use。So for those cases。

 it did some wonders when those issues are like improved。This will go down， of course。

 And when you apply on top of PGO， then。I's going to go down as well， right， because。

You you have to use PGO to get an initial good layout。

 You need LLVM to do some nice in lining and all those optimization passes and then apply bolt on top to get those extra。

Few percentages that maybe be mis due to。Correlation and maintenance。Because in theory。

 we shouldn't be need both， but in practice we。We have that some extra percentage to gain。对嗯。Okay。

 thank you。嗯。In your experience， how is the effect of B on its binarywriting on debug info。

 Do you need to maintain it or update it in bolt or。And like。Yeah， so， yes。

 it needs to be maintained。诶。Actually， we have a a container specifically just for the data。

but it has to be。Has been supported。In your experience。

 does it work well to preserve the debug info because I think the scariest thing that I've heard people say about using Bol is that they don't want to lose the ability to debug there。

Yeah， I haven't focused that much personally on the information。We had some issues with。

 I think with door5 recently。诶不。Now there is work to to support。 But I think that is。Basic support。

Thank you。So in our experience， some of the most painful front end big jumps that。

the cost front and bad performance is across DSOs in a large app， that has multiple DSOs。

 but from when I understand bold optimizes a single DSO individually。

 is there any scope to kind of get it to address these more software architecture composite problems？

Cross multipleaus。So。I think if you capture a single profile when you run your program， you can get。

Prorovide that pair like for all。 And then you have to apply both individually for each DS so and then use those。

You mean to improve the process or you don't have like manually apply this for each DSO。

Or I guess in the extreme case， you would kind of merge DSOs together or you put reorder code within DSO so they're close to their colleagues。

 but well probably that's impractical for various reasons Yeah。

 but even the process of optimizing H DSO individually would be an interesting use case。Yeah。

 so I think for DS themselves to be placed into memory is going to be up to most likely ASLR。

But when it comes to a cash， I think that won't matter that much because we。I guess like the last。

Parts of the address is going to be used for mappinging。呃。But yeah， I don't know。

There can do some improvements not to have like many collisions or。Yeah。

But we could improve maybe in the case of multiple DS source to， like bolt all of them in a single。

Command line， yeah instead to come to this manually。Hi， to your left。

I tried bold and my binary was perf neutral and top down said I have 10% bad speculation。

 20% front end bound on X86， so I was wondering like how I can check my binary like whether it's buggy or maybe I can like give a repro to you do you have any advice on that？

So what was the second question like how do I ensure my binary is optimizable by bold because right now it's perf neutral on benchmarks and so I want to get gains out of it but I don't know if it's actually valid use case for bold。

So I think if we take a top down before and after trying both。

 then you click get an insight if change some things。Bothold has some other stats， as well， that。

C Dino startss， I didn't have time to show those。That tries to show what he tried to do。闭。

Combining what it had on the profile data and what it was able to to do。Can tell you， for example。

 that had all these taken branches and now have this few these ways taken branches because I optimized for the fall through。

So that could be another indication that， you know that binary was。A good candidate。But again。

 some of these are like a rule of thumbs。So some of these things could be like trial and error。

Correct， please to reach out on this code with more specific examples and。Someone will try to help。

Sounds good thank you one extension maybe you mentioned taken branches where are you getting your PMU events on my Amazon instances I don't find PMU events PMU events like near branch taken PMU event for Perf record the BB1 I will expect PMU to be widely available everywhere。

Even AW S with。Visualization。For ape youll need a metalist。诶不。I don't know。

 are you referring to BRB or。I'll continue offline yeah， okay， all right， okay。Any other questions？

2哎呀。The binary salt program you showed is rather small but when the executable is quite large。

 say gigabytes while introducing boats。Affect the compiling time heavily， because from your slides。

 I see both has its own IR， its own pipeline。 and it， it will do some part。 will it。嗯。

Add much more compelling high。You mean on the these assembled part and and the。

The bulk processing part。Whether that will increase。Yeah， I mean， when the code sites become large。

 will the size that both consumes increase， Yes， it is going to increase because it has like way more code to go through。

But if you try to PG， that binary is going to take way more time。

Both that it is going to be like here， it's going to like go through that coat。

Wars whether with PG will have to go through all this。Passses and。But this is like coat size。

Call specific text。Very fell to write。O。All right。Is there any tolerance in terms of program differences between the profile collection and the optimization phases。

 meaning do I have to collect a profile and optimize it every time that I change my program or can I collect a profile like weekly and use it throughout every time you change your program usage or yes？

Yes， so the things that。I omit some things， this one of those things that I have augment。诶。

Meada has added support for sta profile。Which means that if you have a binary and receive some minor updates。

Then it might be able to like， match from with。With the same profile you took previously and compile this binary without profiling again。

But again， depends how much that binary has changed and how， how well the。Of will work。 but yeah。

 you may have to repeat。If the battery changes when the workload changes。

 the battery might be the same， but the workload might change， at least for minor program changes。

 I would not be able we be required to reprole it。It's going to be per use case you have to figure。

 unfortunately。You may also have to， in extreme cases。B a binary per input。

With all these mal more at boa。啊。Extreme， or maybe。One thing that is often applied is that。

People take different， different profiles and then merge it， both can merge different bin。And then。

 you have one。Profile that should be good enough。For for all those inputs。But in theory。

 you could have like different。Optimization per input。Right， thank you。All right。

 we still would have time for questions。Ii I had a question so we've had some experience using bolt and propeller and I guess we found that bolt is very hard to bootstrap on a custom target and propeller at the same time has like very few optimizations that it support like baseball block reordering and function and function ordering right and bolt has significantly more optimizations like partial linelining all a significant and larger stack。

And I guess the examples you showed seem to show optimizations that are common to both to propeller and to both。

 can you comment on the benefit of both specific optimizations？

Or have you seen any benefit or plausible like use cases for data layout optimizations because everything here kind of focused on code layout optimizations。

So I will say that the main thing of both is code layout， that's what you're going to use it for。

But again， depending on your workload， there might be some things that you could try with bold。

The fact that it does some of those optimization might be， in some cases， a bit of like a。

 you don't have to go through again， so。For example， recently。

 there was like an addition that maybe could be implemented in LLVM as well。呃。

But I haven't tried individually to see the effect of each of those。Each of those passes。

 So in our 64， our main focus was to。Get on par with x 36。诶。But recently。

 we've said that we're gonna try and。At a least， on under me with things at work and some numbers。

 we are in process of。Collecting some information， adding。Some more guides， so users will know。

Which options are available in？Maybe some starts to back them。That'll be interesting。All right。

 then let's thank our speaker once more。