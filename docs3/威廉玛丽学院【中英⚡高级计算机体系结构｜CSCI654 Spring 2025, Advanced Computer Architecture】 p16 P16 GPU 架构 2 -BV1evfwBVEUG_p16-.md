# 威廉玛丽学院【中英⚡高级计算机体系结构｜CSCI654 Spring 2025, Advanced Computer Architecture】 p16 P16 GPU 架构 2 -BV1evfwBVEUG_p16-

Last time we have talk about the GPU。Software， how to write a program for GPUus and how the GPU assembly works。

 Then today， we're going to talk about how the hardware can support that type of assembly。

 that type of software and how， and if you look at the constraint on the hardware。

 you probably will better understand why the software is designed that way。

 And the software definitely makes some sacrifice to fit the requirement of the hardware。

 So before we talk about GPU architecture， I want to want you to。

Review the history of development of GPSUus and what GPSUs are there。

I think you must heard of many news articles saying something like the release of R T X 40，90。

5090 or B 100， B 200。 So what are those things and how you can compare one machine with another then。

We can do you， you need to have a sensitive sensitivity that catches this news and understand how this industry is producing these products and why and。

What is being improved from generation to generation。 So just using AM D term as a。Understanding。

 and so we can see their release date and the GPU， the product name and their internal name that you understand which chips are actually the same。

 like which products actually share the same chip。 Okay， so yes I want to draw a table then。

Start with release date。Then release date。 and we have the product name。After that。

 we have the chip name。And another thing is called family。ok。😊，Family。

 yeah or family or architecture。 So when did AMD start to first make GPUs？能。

How did AMD starts to first make GPUus， Its by acquiring another GPU manufacturer or designer that is called ATI。

 right， So by the time AMD acquired ATI， it was in 2008。 AMD start to produce GPUus。

 Now by that time， they were using the old ATI architecture。 But a few years after that。

 AMD started to。Come up with their new GPU architecture。 And this is the fundamental of the G， the。

GPU architecture， you see in AM D today。 So the real estate of this first product is in 2011。

 So basically three years after acquiring AI。 And they published this one called Radium。HD7，9，70。

So this name is not important， but or。7，9，7，7，9，8，7，9，90。 Now you can from this number。

 you can tell if it's a low end。 This is 70 is a mid range。9。

80 is already a high end 90 is probably the best in the product line。 Then by that time， the chip。

 the chip name is called G F X。600。Okay， so how to read this number。

 how to understand this number is the first number is the family。 It's the big version。

 So you can read it as 6。0。0。 Okay， so this is a minor number， and this is a patch number。So 60。

0 is Nf big family， and they call it GCM。It's called Gras core Next。The next is， in terms of。

The next generation after acquiring AI。 Okay， so this is 2011， then in 2013。

So I don't want to write down this name。 It's not that important It's very old。

 Then they start to have a new version called this 2。Okay， and in GN 2， this version is。Going to 7，0。

1。 I'm just using the most famous one as the name。 So one here is probably not that important。

 but you should look at this one as the seventh most the biggest generation of their GPUs。

What before what's before 6 is basically the AI generation GPUus， okay then。

Gson 2 and one are not super different Then a bigger different comes in 2015。 In 2015。

 we started to have this GPU called R 9， not Fuy。Ax or Fuing nano。

And the RNA flu in nano is a very important GPU to me personally because or simulator。Was。

Or simulator MG S was built on this one based on R nano。

 So R9 nano is keptped being used again and again。Why we select this one is because our lab happens to have that one at that time。

 and we all keep introducing this one。 You will find analyzing this one is super easy because it runs just at 1 gigHz。

 So makes every calculation super easy。 And you will find everything is 64 or 32。

 Then it's like all the configuration is a power of two。 So it's very easy to analyze。

The performance of this one。 So today， I'm basically going to use this one as the fundamental。

Architecture that we introduce today。 Okay， now this one is G FX。803。Okay， and this is G 3。

I will also give a commercial name。Okay， so they don't have really have commercial name。

 They only have product name here。 So the commercial name for their family。 Okay， so this is Gian 3。

 right， then it's interesting that in 2017， then they start to build this chip called R X。480。

So what's the cheap generation by that time？And interestingly， is G FX 803。Okay。

 so that's basically saying。It's roughly the same chip。But it's。

Produced is packaged in another product， and they call it GC3， GN 4。And by that time。

 they start to have this product name called Polis。Before that。

 they don't really have this commercial name。ok。Then G4， and there's another one called55，80。

And it's also GFX 803 and it's just a slightly more powerful one。

And they still like sell it as another product。Then。After that， let me look at this one。Okay。

 this is not 17。 This is 16。Then in 2017， they start to build new chips。By the way。

 what's a big difference here is this one is a 28 nanometer technology。

 but this one starts from this one， they start use 14 nanometer technology。

 So the chip is actually getting much smaller and saves energy。Also。

 you can tell R9 series is their higher end GPU， but on this level it's not that higher end。Oh。Okay。

 so in 2017， they start a newer generation， and they start to call it Vega。64 and Vega 56。

And start this version， they start to have nine。0，0。Okay， and start to have 900 series。

 you can tell this is a new theories， and although they never really say it's a GCN series。

 but typically we call it GN5。 It's the fifth version of GCN and they have， of course。

 it's called Vega and they ditched this naming S and the commercial name is Vega。

So what's the difference between 64 and 56。Is the number of cores right This one is higher end has 64 cores。

 and this one has 56 cores。 And remember in the first time in the first lecture we're talking when we're talking about bining。

 this is basically the same product， but some defect happening here。

 So they they sold it as a lower end product。Okay， it's 2017。 Then after this。

 something interesting happened， actually in。Still in 2006。17。

 like because Nvidia has another product line called Tesla product line， right。

 This is their higher end。Data center only chip。 So M D is following the same product line。

 and they start to have their instinct。They call it a radium。Instinct。Product。

 and they call it machine intelligence。 M I， M I 50 or M I 100， M I 50 by that time。

 am I 25 M I 6 or several product of GPUs。 And what's their product line and is nothing special。

 but just G F X 900。Okay， it's the same。It's the same chip， but it is sold in a different product。

 Then this is only the chip， right， This is a chip name。 So 8900 and 900 are using the same design。

But the memory around it may be different。 Okay， and the。Cooling system may be different。

 and they may even remove some， say video encoder from it。

 that is not the essential part to make it a pure data center product。 Okay。

1 one chip can be used for different things。Then starting from this point。

 then they still using 5 14 nanometer， then they。By that time。

 T SMC start to have 7 nm technology from 14 nm to 7 nm is a very big jump。

 Its probably jump bigger jump than anything else。 So they start to have a chip called。

I think this is in 2019， right？Yeah， this is called Radium 7。I reading V I I。Read on 7。

 So this is the first 7 nanometer tag7 nanometer chip in the world。 Okay， it's actually super small。

 The chip is super small， much， much smaller than this one。 but the version is still G F X。900。Okay。

 by that time， they its， it's basically still G and 5， but they don't say G and 5 anymore。ok。

就 reading 7。You can see it's not going following any。Like numbering system， like 8 or 9 here。

 And you call 7 because it's a 7 nmeter technology。 And it's actually a solo G。Only GPU by that time。

In this family。 So it's a very weird position that the chip， if you know， the die size。

 is actually very， very small。That's because they're still producing the same chip。

RightBut using a new technology， making the chip really small I mean the AMD still want to make big chips。

But they find problems。 The scalability is not working anymore。

 so they cannot really squeeze in a lot of resources in a larger chip。If I remember correctly。

 this is 300 millim square or something but highest end is 600 millim square about size to 800 millim square。

 so they cannot really make large GPUs like if they make large chips like the communication latency will be too high。

 we' see why the communication will be too high in that time then they start to say okay。

 we cannot really use one product line for the two different market right so one market is the gaming market and one market is the data center market So they start to have different product lines。

 So that time GN5 and continue is the last generation for GCL。Now by that time。GC。

Start to split into two product。Start to split into two product。 One is called R DNA。

And the R here stands for Rdium is mainly for。Gaming graphics market。 And on the other side。

 they have C DNA。Which stands for compute。 Okay， they start to use different architectures to work on two different markets。

人。2019 is not too far away from us。 then what's the generation after that？

Then they start to have this R first R that's in 202020。And the first generation of R DNA。

And the chip name is called GfX。10。1 is。This product is。The10 generation， with ones minor is。10。1。0。

 That's their version number。 Okay， and this is the generation called 5，700。XT。Or X T or X T X。

 By that time， this is the product。 Then the1 series， this GPU is only a。

Me to range or low lower end GPUs then。Starting from there， they start to have something like 6。

900 X T。 And this is G F X。1030。It's not a big generation， but there's something definitely changed。

 and they call it R DNA2。So today， I think we're waiting for the release of R DNA 4。

 then and actually， MD is talking about meing them together back to have a U DNA。

Architecture and what， what is exactly UDN architecture， We don't know。

But this is only on the gaming side。 On the other side， we have the。AComputer side， right？

 So by that time， it's still in 2020。The computer side， they start to have this GPU called MI I 100。

 This is a rather important chip。 that is a kind of competing with A A 100 way A1 the media A 100 GPU。

 And if you look at the architecture name， you will understand what is going on。 So the name。

 the chip name is called G F X 9，0，8。So what's going on。对 this is cDN， this cDN one。嗯。

So what is happening is。CDA is rather a patch。On top of the。GCN architecture。Okay。

 so it's not very different。 They just in terms of product name， they change it to C DI。

 It's basically stM。Telling from is still the nice generation of neuro GPU。Then。

Something actually more important is， am I 200？S is 2，10。And 2，50。This is in 2021。And this is GfX。

908， not 908， so they are running out of numbers， so they are starting to use hackx numbers because they already have 10。

 they can now go towards another major number， so they are starting to change this number。

The the fundamental architecture is still C architecture。

 but starting from this point is they start to have chipt technology。

 Chit means they have different chips， several chips that is packaged in one product。 So they have。

 they made very big chips and。They have smaller chips。 that is packaged as if it's one GPU。Okay。

 then。Also， they start to have I my 300 theories that is the most advanced today。

 and they start to have tensor core。Now media has tensor cores。

 and AMD also has tensor cores in our GPU。 And that changed a lot in the architecture。

 There are a lot of fine tunes at these generations。

 but the main architecture is still following the G GCN architecture design。Okay。

 and we're looking for what RDA will be。 And it's still not there。

 But probably that's a big time that when UDN is released。

 we can make another newer version of a GPU simulator to support new architecture。 Still today。

 we are doing G F X。8，03。And that's released in 2015。 So 10 years ago。

 then it's definitely or simulator needs to ramp up with a new architecture。Okay。

 so just a quick review about the AMD family。 Now， I think Nvidia family is much。It's simpler。

 Now if you do a some online search， you know， those generations like Hopper， other Lovelace。

 Blackwell， those are all big generations for NviD GPUs。

 and they also start they also from the very beginning， they have two product lines。O。So。Today。

 we're going to use the G F X X 80，3 chip as the fundamental chip and start to introduce。

The main component and how how it works。Remember， last time we're talking about some API calls。

 right， runtime API calls。 So how it works is the host the program。The host program runs on the CPU。

 right？Nan cause runtime API。Then。It runs on CPU and is implemented by the user。

Now runtime also runs on the CPU， but is implemented by NVdia。Right， a media provides a library。

 and the runtime calls driver。It still runs on the CPU。

 but it runs in the OS S domain privilegeleg mode， and is also provided by a media。 Also。

 there are some open source alternatives， but it's mainly provided by a media， right。

 starting from this point， the driver needs to run the kernel。That is on the GPU side。 right。

 So this run on the GPPU side and is also implemented mostly by the user。Right， so starting so there。

The most critical point here is at this point， if we're starting to transit from the driver side to the kernel side。

 and other than launching a kernel， the driver can also initiate memory copy。Right。

 so kernel and memory copy are the most important tasks for the GPU to run。Now。

 I'm going to draw a very。I'm going to break it down into two pictures。

 I think the space is not good enough。No matter what this code is run， running on the CPU， right。

 This part of code runs on the CPU。 Now eventually， when we want to launch something， we want to say。

 oh， we want to do a memory copy and we want to start a kernel。

 We need to send a message or send a command to the GPU side。 and the GPU side will take care of the。

We run the command。 And this communication is mostly done by PC I。e。Network and it's on PCIE。

 So the CPUU use PCCIE to send command to the GPPU。And this is the GPU。On the GPU， the entry point。

Is where this PCI is connecting to other than a network interface。

 its something called a command processor。I don't know the term for am media here， but on AMD side。

 this thing is called command processoror。Okay， this is a command processor。

 Now command processor is actually a small CPU within the GP。

 It actually even has its own instruction set and is controlling the rest of GPU。 What it can do。

 right， They start with the memory copy part。 The memory copy part is the simpler part。 And。

The memory copy part is the simpler part。 So we start with this one。

 So when the command processor knows， okay， it's a memory copy command， right。

How what it does is it goes to give another engine that is called DMA engine。

DMA stands for direct memory access。 Okay， so DMM engine。

 the DMMA engine will take care of the memory access。 and typically GPU contains two DMA engines。

 So because one can take care of host to the device and one can take care of device to host。

 these two can happen at the same time and their。If they're using PCIe， they have no interference。

 now you can you can double the bandwidth。Then the DMMA engine is directly memory access， right。

 so it can directly access the CPU's memory。AndTpically implement in DDR technology。

It can directly access the GPU CPUU memory and to directly talk with the GPU memory。Okay。

 so the DMMA engine is basically a data mover， data buffer that can take data from one side to and right data to the other side。

 Then both side works。 And they there can there can be another DM engine is doing another stream that is accessing the data。

Okay， at the same time。So for memory copy， that's pretty much it。

 right that's the only thing that we want to talk about。 No need to understand too much detail。

 We just know， oh， there's something that can help us copy the memory is good enough。

On the other side， the command processor， if it's a kernel。

 the command processor will start to execute this kernel， right？So remember。

 when we talk about a kernel， the kernel can go down a few layers deep， right。

 And that's the probably the most important thing that you need to remember that a kernel was the next level after a kernel。

一车。Block right。So I also want to introduce some alternative names that are used in different。Contex。

 So a great。Is a kernel that is launched or another way to say it。 When we launch a kernel。

 the GPU forms a grid of threads。 Okay， it can be one dimensional grid， two dimensional grid。

3 dimensional grid。Only terminologies。 if you use kernel is totally O。 It's just another name。

 A media called things block A And D called things wave。work group。

No reason just they want to call into word group， okay。Then block on the next level。Is work。

It's typically 64。Or。64 or 32 threads， right， So a warp on AM D terminology sometimes is called a wave front。

我。Sometimes it's just as simple as a wave。A ver is also called a wave in AM D GP。Again below verb。

 we have threat。Now， a thread on AM M D side is sometimes called a。Work item。No。

 you may also hear this term called Le。ok。Now， think about lane and wave。 Just think。

 just imagine there's a swimming pool， right， and there are lanes。And what is a wave。

 A wave goes nowhere way。Right， and the wave always is at the same。Location in terms of the lanes。

 But the wave goes in this way。 So there are parallel lanes going towards that direction。

 And so this thing is called a wave。Okay， they go parallel towards the end of the program execution。

They call it wave and they call it lay。 So in different contexts， you may use different。Names。

So at this time， we have a grade， right， and our command processor knows， okay， we have a。

We have a kernel that is running， and it can be break down into some blocks， a lot of blocks， right？

就呃。On the other side， what do we have？I'm going to remove this part。On one side。

 we have command processor and we have kernels to execute。 On the other side。

 we have a lot of cores for cores here in AMD terminology， they are called compute unit。

Ill just write C you。 Okay， Comp unit on。Ammediate terminology。

 And they called sometimes they just called it S M or S M X。Discus streaming multipocessors， N。

It's a complex name。 So let's just use C， but I'm still going to use blog word and thread。

 and those are Cs。 So C is a core for GPU， but its capability is much more complex。

 It's much more capable than a CPU core then。I just don't want you to get confused that a C。

 I say is equivalent to a core remember， Vega 64， Vega 56。

 there are quick numbers for number of compute unit or number of core。 but if you look online。

 you may hear about another term called KUa course。And that's totally different thing。

 We'll introduce what they are， but they are not a compute unit。

 You you what you can see is here is typically thousand。Of cola course in one GPU。

 but in at the C level or SMM level， there are typically like 60100 around this level， okay。

So code of course， is something else we'll introduce later So here。Just consider Vega 64 or Viva 656。

 Then below the command processor， we have many compute unit or many cores。So， we have the。

Lologgs that we want to execute。 Now， what is happening is this command processor will dispatch this。

Blocks to the compute unit， O。Then if we want to introduce a little bit more terminology here。

 just consider if you have two kernels that want to exclude at the same time。What's gonna。

 what gonna happen。 So it's basically the same theory， same method as the DM engine。

 we delegate to something else。 Then that's something else。

 If we can have multiple copies of that thing， then we can run multiple kernels at the same time。

 So what are those things in M D terminology。 they're called。aceイス。AC c e。There are several of them。

A C E is aynchronous。Compute。Eine。Okay， asynchronous compute engine is responsible for like this。

 The compute， the command processor tells this A CE， you are responsible for this task， this kernel。

 then AE will take that kernel and work on it until it's completed。 At the same time。

 the command processor can assign another kernel to another AE and this AE will take care。

 the execution of another kernel and dispatch and receive the response from another kernel。 Okay。

 so those are asynchronous compute engines。Then asynchronous compute engines。

 then we have a lot of compute unit， right？So this that's。Assume we only have one ACE。

 and this AE will dispatch those blocks to the compute unit。Okay， so imagine。In a kernel。

 if we have 1 million blocks。This is totally okay。 In theory， this is okay。

 There's no limitation on number of logs。Now， on the other side， we have 64 compute units。

And at this stage， let's just imagine once you can only exclude one block at the same time。So。

What's happening here。Yes。We cannot really let all the blocks to executeude at the same time。

And remember， GPU doesn't really want complex control logic。

 So they GPs do not like swiping or contact switching in CPU。

 what's happening is if we have 1 million threads， We just store them in a memory。

 Then the CPU will pick up this one， exclude for a while。

 story back pick up that one exclude for a while and story back。 That's how CPU works。

 GPU doesn't like that way。 GPU works in a way that we pick up 64 blocks。Excuse， we finish them。

Now we let them retire， We throw them away。 Then we pick up another 64 thread。Excuse them。

 finish them。 throw them away， okay。做。It's not exactly batches。

 Its just consider if I can exclude one。 If I'm a C you， I exclude this one。 I get one task。

 I exclude this one。 After that one， I get another one from the A E。

 Then I'm excluding that one after that one， I get another one。

 So that means if have 1 million blocks。We。If we have 1 million blocks。

 we only have a small number that is excluding at the same time。this makes one thing that in GPU。

 you should never expect。Global synchronization within。A kernelel。So， for example。

 if in one tie one thread， you write。4。A。Eal equal0。 or it's right while。YA equal口 equal口0。Wait。OK。

 then after that， do something。In one thread， if I want to do this on the other thread。

 I write a equal to 1。 I said a equal to1。On that thread， can this happen。Can this work？Then。

 the quick answer is。If they are within one block， they can work。

Because a block is always executed in one core。 And at least， there are some memory ordering。

Have memory or guarantee within one compute unit。However。If you are running。

 if you are running this one， if you are writing this one in one block and writing this one in another block。

You may be in bed lock。Why is it？ Because in one thread。One block， you may be executing this one。

 right。Then there are 63 other computer units executing something。 It probably also waiting。

So the block that is quo this one may not be even dispatched， may not be even executing。Right。

This one may never get executed because you are still executing this one。

 you have to wait until this one to complete so that you can start to execute this one。

But because of the hardware limitation， you can never run this one。

So this is an example of global synchronization。And this never happens。

 so you should never write this type of program in GPU。Synchronization。

 or the the quick thing that you should remember is in a GPU problem。

 synchronization can only safely happen within a block level。That's why we have blocks。Okay。

 block is the smallest is the largest unit。Or a group of thread that you can do save synchronization。

ok。This is the reason because you have limited hardware and the blocks may never execute at the same time。

O， any question。呢个さ。To learn from piece and。是是。For the GPU they have the。I what the work about the。

汗がせ。Sa myself sense say myself sense why this is just。番光。Yeah， we'll get there。

 I'm just making it simple simpler。 So in fact， is one computer unit can run multiple blocks at the same time。

Right， it can run multiple but not unlimited， probably 10， probably 40。Different numbers。

 I'm just making it simple。 Okay， we'll go there。Well， that's naturally the next question。

 That next problem就。As we're saying that。A compute unit。Can run more than one。Block at the same time。

 So what's the limitation， So how the A E can dispatch the right number of compute units。

 number of blocks to the compute unit。 Okay， now in that case。

 we need to go another layer deeper and look at the work level and see what is exactly the communication between these two。

Now， what's are the limitation， So let's go back。 that then in this case， we need to。

Enlarge the compute unit， which is the most important unit here and see how it works。ok。So， here。

In computer unit。 and this is the front end。Of a compute unit， it has four of these things。

And we call it v front pool。O， those are way from pool 1， way from pool 2。

And wave front Po is or terminology。 It's a simulator terminal we just。

Think it's a proper terminology。 Now， we use it in M plusim and also multituim。

 You can learn from multituum。 If you look at the AMD terminology， AMD document。

 you will never see this terminology。 They， They just simply call it C D。

But this is not descriptive descriptive enough， I've just call it way front pull， okay。Now。

 with wave front pool， there are some wave front slot。Okay， those are wave front slots。Sorry。

 I cannot use the verp anymore because how do AMD hardware they just call it away from slot， okay。

So those are away from slot。 So what are in way from slot。

 iss basically it contains some registers like PC execution mask， VCC， and those。

Neer registers to represent the state of execution of a verb or a wavefront。ok。

So if there are four of them， that means this way front pool can hold four verbs at the same time。

Then in most of the design， in most of the chips， AMD chips， this number is 10。ok。

So 10 way front slot in one way front pool。10 way from slot in onepo and 10 way from slot in onepo。

 Okay， so that comes to。The number of how many ver that1 S M 1 C U can handle at the same time。

That's 4， multiply by 10。 That's 40。喂。4 multi double by 10 is 40。Vy front。Then。

You need to do this calculation。How many blocks can this computer unit execute。

And the quick answer is， it really depends on how large it is's a block。 right。

 Let's say a typical block。That're equals to 256。Thread。2，56 threat in M D。Terminology， that's。4。

V front。ok。There's four wave fronts because each wavefront is 64 thread in GCN or CDNA architecture。

In EM mediadia and in RDN it is' 32。O，4 way front。 that means。40 way front and 4 way front。

 now means 10 block。Each compute unit can handle。 So each compute unit can execute 10 blocks at the same time。

If you have smaller blocks， you can exclude more。 So for example， if you have a 64 thread。

 in that case， that's one way front。Then in that case， you can have 40 blocks， right？

You cannot have more， even you have 32 T。It still it's still a warp， and you still have 40 blocks。

 Ex me in one compute unit。O。And that's a theoretical upper limit。

We have to have these resources to hold those bayfronts。What are other resources？Next。哼。

There are three other resources。Remember last time we're talking about asset registers。

And the last time we're also called saying there are vector registers。Right。

 and there's also another thing called LDS local data share。O，D， is。Sra。

 it's addressable asram in GPU architecture。 Okay， so it's a local storage that you can use for like low data to the compute unit and process the data。

 process， process process。 and for many step， and eventually story back。

 So LD S is another resources。 So when we compile a program or a launcher kernel， we need to tell。

That how many S registers that are required， how many vector register required and how many。

 how much LD S is required by that time。The1 A AE S dispatch a kernel to the compute unit。

We will also allocate some SRAM space， V rack space and LDUS space。 if there's no space。

 then that block cannot now execute。Okay， in some cases， if you have a really large kernel， like say。

 highly optimized matrix multi， you only have one kernel to run if you only have one if you one verb can use all the vector registers in that case。

 you can only execute。1 block。In in your program。In one computer unit， Okay， so。So basically， you。

 I a summary。What's the limiting factor for number of verbs that can be executed in each compute unit？

There are four limiting factors。We放 slot。S register， vector register and LD S。Okay。

 so how large is the vector register。能。The vector register is。1024。Multiply by 64。

So we can allow 1024 registers。That to be used by each。嗯。By each verp， by each thread， or we can say。

Right， earlier version can have 2，5，6。Now GCM probably is still 256， then newer version is 1024。Now。

64 is the number of length because each lane， each thread will have its own vector registers， right。

 They have to have physical registers to memorize the number。 So what's the size here。64 K。Right。

那 consider each。Registertry is 4 by long。So the total size is 256 kilobyte。Only in the registers。

 that's a huge value as compared to when we talk about risk 5， theres 32 register to use。

This is a huge number。 So that's why I say32 is a。Really small number for for for an architecture。

 This is a massive。Okay， but anyway， we need to， the most important thing is when we launch a verb or a block。

 we need to allocate spaces in vector register， Scalar register and LDS。Okay。

 then when we're executing multiple kernels， because there are multiple As there。

 we can even have fragmentation problem。Let say we have， we have one part of register allocated。

 one part of register allocated。 and the right of space combined may have enough space for one verp。

 but they're not connected。 If they're not connected， there's no way to execute that verp。 Okay。

 so it's a rather complex process here。To find the vector which part of the vector register or to allocate to that block。

Also， ACE went launch away front。Or a verp。 is's not only， say。

 it's not only a process of assigning the task。 It's a it's a little bit like operating system prepared the memory state for the CPU to exclude the AE will also say。

 oh， your register。 This register should set to this value。 that register should set to that value。

 So it will also be responsible for register initialization process。 Okay so this ACE。

 if you only have one kernel。 This ACE， when its dispatch。

 it may take a few cycles to dispatch each work。ok。It may take a few cycles。

 Then it goes to the next one， goes to the next one， goes to the next one。 Consider in more than。

AMD chips。 There can be 120 in MI 100。 It can be even more in MI 200，300。The ACE can be really slow。

 Just think about four cycles in each C， then。4our cycles for each cop unit。

 that's a really small number， then four cycles here， four cycles here。

 four cycles here going around is 2，56 cycles， right。To phase six cycles。

 we may be able to complete a warp already。So if you write really， really small kernels。

 ACE can be a performance bottleneck。Okay， it can be a performanceable。 It's not issuing。

It's not giving the。Ws fast enough。And we did measure that if proper optimization of A C E can improve the performance。

 like not really A C E just。Aware of the limitation of AE so that intentionally right the kernel to be larger to do more work。

The each thread to do more work so that the total number of thread is fewer。

Now we can improve the performance by a few times。Okay， so highly optimized。

Colonel always need to consider the limitation at A C E。Okay， so that is the execution。

 that is how the blocks and verbs are dispatched。So think about this after the dispatching。

 we have everything dispatched here， right， so。No。Each way front pool and each way front slot are packed with。

A。Each way front pool， each thought are packed with wave fronts to exclude。

 Now' see how these wave fronts are executed or how the instructions are executed。 Okay。

 I'm going to reach out this one because this is gonna be a big graph。For the compute unit structure。

So let's start draw this big figure。Is this a computer unit？And we start with four way front puts。

So we have the wave fronts here waiting for to be executed。 right。 So remember。

 in the first pipeline stage， what would we do。What's the first of pipeline， typical pipeline stage。

We need to fetch， right， We don't know the instruction to exclude， so we don't know what to do。

 So we have to get the instruction to execute。O，小。Let me draw this here。They should be here。

 but I'm going to draw something else there。 So that's me right fetch here。

And this is the fact stage。 And there's a。Abitter。啊。Okay， right in this way。

This is a fetch orbitbiter。 So what does fetch abiter， Because you have 40 ver there。

40 wave fronts there waiting to be executed， right。So which one can fetch？They。

 they all have different PC。Which one can fetch， The fetch orbit will determine which one can fetch。

Okay， so it's really a design decision that what's the arbitration。Policy。And also。

 we have clear evidence that it's changed。By the driver。 So once。

 one time we're doing some micro benchmarkching to test what's the fetching and issue。

Something we'll talk later， the issue policy。 And after upgrading the driver version。

 things are changed。Okay， so this is something driver can control。And what's the typical？

What's the typical algorithm that we can use， For example， the one that fetched。

That is for the longest time that haven't fetch any instruction。 We fetch for that workp。 Okay。

 that's a typical fetch。Methodd， anyway。So the fetch Orer will select verp to fetch and send a memory request to the instruction cache。

Now when it's cash， I just use the dollar sign and cash has the same pronunciation as cash。

So it goes to the instruction cache。 We talk about instruction cache later。

 when we talk about the memory hierarchy。呢。So let's assume that we have something that is fetched。

 Okay， and what is actually fetched into the compute unit for each way from slot。

 There is actually a L0 cache or。L0 instruction cache， or sometimes it's called instruction buffer。

 So there's a for each。For each wavefront slot， there's a like certain sites that can store some instructions there as the instruction buffer。

 So instruction buffer are there to be executed。Okay。

 so let's assume all of them have something to to execute。 Now the next level。

 next stage is to get them to be executed。So what's the next level？I。艺术。I the issue a bitter。ok。

Then on one side， issue abiter has this input that is。40 words waiting to be executed， right， then。

On the other side， we need to know where they can be executed。 Okay。

 so I'm going to draw this next stage as this。ItMaybes slightly different from the real architecture AMD architecture。

 but I'm just showing there。Just showing in a way that is easier to understand。 Okay， remember。

 last time we're talking about superscalealar， right， The GPU is also superscalear。

 How it's superscalealar。It's。Here， the first unit is branch unit。 Okay， then there's a scalar unit。

Remember， we have S instructions to scalar unit， right？Then， we have。Vectctor。

 the vector memory unit。We have。V L U unit。Vectctor A O U， or sometimes this is also called S D unit。

But that's just called the vector L U unit。 Now we have a LD， S unit。Okay。

 consider this stage as decod stage。In this case， issue happens before decode because by just looking at a few bit。

 we know if it's what type of instruction they are。ok。

And there's actually another unit called Global GS， and GS is never used， I rarely。

 rarely see GS instructions。For so many times， the only thing once is in a random generator program。

 and even in newer version of GPS PUus， the GDS unit is removed， so。Let's see， we have 1，2，3，4，5。

5 units， right， That means this is a five issue pipeline。ok。

Which means the issue or bitter can issue five instructions at most in each cycle。

So what are a five units？And so the initial abiter always works in this way。In cycle 1。

 is select from wavefront pull 1 in cycle 2， it selects 5 out of 10 from wavefront pull 2 right in cycle 3。

 selects from here in cycle 4， is select from here in cycle 5， is select from here and so on。 Okay。

 this is round Robin。So you have five of them to be excludedd there。

Then there comes a critical question。 You say， even if this one， we have 10， right。

 We have 10 out of 5。So which file we need to select？10 out of five。 Which five to select。

Then there are some rules that at least we can get rid of that we don't consider， right。

 the first rule。Is if this way front。Has instruction。In pipeline。No， we don't select this one。ok。

If the wavefront is currently excluding some instruction in the rest of the pipeline。

 we don't exclude it。This may not be true in very modern GPU， and it's not true in media GPU。 Okay。

 this is only an AMD style。 Now you can see later on how how much it can simplify the header handling。

Then the second rule is no。2 wave front can occupy。Can use one unit。This is easy to understand。

 right？No two way front can use one unit that's a structural hazard。I think there's only two rules。

 only these two rules。O。And then。Third one is not necessarily a rule。 It's a policy。

 It's a design policy。 And this thing can still us change。 So even even if filtering out。

The waves by these two rules， there may be still some rules that there may be more than five that we can select from。

So which one we can select？Specifically to end。We we try issue as much as possible from one ver where we try to keep them fair or try to say。

 last time we issued this one and this time we show that one。

We have different policies that I can select。And very likely。Is more than to select the one that is。

Most recently issued。喂。It's because we want the ver to execute as fast as possible。So it can retire。

 can make the space for new works。ok。However， this is not always true。

 And even in different the same hardware， different driver version。

 we detect that this thing can change。 Okay， they may use different policies。

 Sometimes they want to get like a round Robbin style to be fair。 sometimes they select this method。

 Okay， so there's no certain rule for the third one。 But the first to are。Sure。ok。Okay。

 then we have deco stage。 We have6 decoder。F decoder， and there's another type of instruction。

So we call it special instructions。 What are special instructions。 Those are wait count。Brier。

We haven't never type talked a barrier。 It's not that important for micro architecture here。

 than an end program。Some these type of instructions。

 they call it special it's a synchronization only instructions， right。

 Those instructions doesn't need to be executed the issue。Unit will determine or if wait count。

 if the counter is narrow or not。 Then if the， if find the counter is smaller than the value。

 then we don't need to issue issue that instruction。

 It will just discard and explain next instruction。 Okay， so at most， it can issue 6 instructions。

 I do one cycle。 Let's do。That's in theory。Okay， so starting from this point， the BR is rather easy。

 So you can consider there's a。啊。Read。Excuse。And right back。Pipeline。

 okay for scalar is also similar。Vctor Manm， will talk about it in the next lecture。

 we'll talk about the GPPU memory system。But let's talk about VLU。

 What is connecting behind VLU is a group of four S D unit。And that's the powerhouse of the GPU。

Those are all day unit， okay。For in the unit， the limitation is。Wve front， pool，1。

Can only go to this empty unit。 way from pool 2。Can only go to this one， and so on。

And four can only go here and actually right before here， that is the huge。We registers。Stage， right。

 because we need to read。 Okay， but I don't want to draw in this way。 So because I want to tell you。

Better about what exactly is happening in the S unit。

 Just consider the sameD unit as the AO U for the GP。 and also vector registers for the GPU。

So what are CMD unit and how CMD unit is implemented？So it's implemented in this way。

 a assembly unit， each assembly unit has 16 lane。It right here。 it is the same D unit。In SD unit。

 the AO U。Has 16 lengths。I don't know how many I draw， but just imagine is 16， okay。How many thread。

It's one warp。64， right？64 thread per warp。Or per bayfront。So if there are 16 lanes here。

 how many cycles it requires。To finish one workp。4， right？4 cycles。By the way。

 when we talk about GPU architecture， when we talk about instructions。

 especially issuing instructions， we always need to be clarity be sure that what we are issue。

 are we issuing thread level or work item level instructions。

 or are we issuing work level instructions。RightSo sometimes we talk about IPC instruction per。

 we also need to specify what instruction you are talking about。For CPUU is the same thing。

 for GPU is。It can be， it can mean different things， right， So for example here。

Everything here we're issuing are。Work are way front level instructions， work level instructions。

 So when we issue， we issue one work。Instruction from a work， not a not a thread。 Okay。

 that means when we issue once， we're excluding 64 copy of the same instruction。That means。

It takes four cycles。To exclude one instruction。The y4 Sd unit and y4 cycles， iss not a coincidence。

 it's carefully designed。Right in one cycle， in cycle one， we issue here， right。

In cycle 5 word in cycle， let' say， in cycle 4， were done。In cycle 5， we start another instruction。

 In cycle 8， we're done。Right so here issue in cycle 2， we start in cycle 5。 we end 6 to 9。

It's another instruction similar here in step cycle 3， we start in cycle。6 then。We finish in cycle 7。

 we run in cycle 10。 We finish here， also in cycle。4our， we start in cycle 7， we end 8 to 11。Okay。

 so in theory， if you only have ALU instructions and everything is working perfectly and you fetch fastly enough。

You can have 100% utilization of the same unit。ok。Lets sustain same the unit。 And here。

You also need to consider a read。Um。So although it takes four cycles， right， so we cannot。

We cannot really say it's taking four cycles。InI can say in four cycles。

 the first pipeline stage is completed。 So what's the pipeline stages here。

 You need to consider there are some vector AOU register banks。The register banks。 So in cycle1。

 I say in cycle 1， what do we do， We do read。We read from the register。 How many register we read。

We read from， we read  for 16 lengths， right。Then， in cycle。In cycle 2。

I will write this is0 to 15 lane， okay， now 15，16 to 31 and so on。In cycle 2， we execute。

 Let's assume we can execute in one cycle time。In cycle2， we read。For the seconds like。 Okay。

 then here we execute， and this one will write back。And here we write back。Thenread。Excuse。

Write and read。Excuse。Right。This three，4 after cycle 4， this rate stage is freed up。

 then you can take another instruction。Okay， so that's why I don't want to write a vector register here is actually what's happening is like this。

O。就。Let's do some quick calculation。What's the computing power of R 9 nano GPU。

So in terms of computing power， we use this terminology。Or this unit called flops。Then flops。

 just be careful。 There are two ways The right flops。 is one flops， one is。Flops。Okay。

 what's the difference is this S is capitalized or lowercase， okay。

Our case is floating point operation。Operation per second。

This is floating point operations as a pluural reform。Okay， this is a common convention。

 but some paper or some article may use different ways。 Okay， look at their definition。

Were are when we're talking about computing power， we talk about floating point operation per second。

 That's the most important number that describe the capability of a GPU。So let's calculate R9 nano。

How many days？P D。16， right。How many CD per U？4our，4 same de unit per C。How many C per GPU？64。 Yeah。

 I I， I don't think I talked in this number before，64。 So it's just easy to calculate。

 So how many instruction it can complete in each cycle。Just multiply these three numbers together。

 right。So 64 multily 64， that's 6，0，96 inst。Per cycle。That's the theoretical limit。那IC。

And just careful， this instruction is thread level instruction or work level instruction。O。4。

096 instruction per cycle。ok。Then。The best number comes。 It works at 1 gigHz。So， that's 1 billion。

Cycle per second。 So how many instruction per second。for。0。G。Not， it's not common。 It's a dot， O。400。

400，4096 G instant。Per second。ok。How many operation is each instruction。It's too up。Per instruction。

 why。Because of work。This is confusing， right， It takes me a very long time to match this number with the official number of the official advertiser number。

 What is two ox。 It's basically the。And Mac， multiply an accumulation。Multiply and accumulation。

 this instruction can be completed in one cycle time and is considered two operations。

And that goes to。8。196。Os。P。Billionops， G ops。Per second。Or we say is8。Wait， it's a comma here。

It's not the。It's not a。 it's not a。Rememberote， right this one by this one， right。It's a comma here。

 It's not a dot。 So if I change it to dot is 8。196。T flops。O。It's basically 8。2terralops。

That's the performance character。4再 play一个 GPU。ok。And here， we're talking about。

Single precision numbers， single precision。 Sir F 32， Now F32 is。A few years ago。

 F32 is the most important caricmetric the property。And today。Which one is the most important？

Like even at the beginning of this semester， I would say it's probably F16 or F8。

Today is probably at four。Floating  point4，4 B floating point numbers Op performance is probably the most important in magics。

 Why， Because machine learning is LL models today。Especially deep sick。Us F4。

 so that describes how fast a program can run。O， thiss your computing power。And so。超。

Just to answer that question， what is a coac core。Cut a core is a lane。Okay。

 so how many length are there in the total。GPU。This number，4096 could course。Per GPU。

 although that's only a Nvidia terminology， AMMD never use that terminology。

 but it makes sense that how many thread can be excluded at the same time， right。Right。

How many thread， if on CPU side， the number of cores equals to the number of thread that are excluded at the same time。

So that's cool。 Another concept。 Have you heard of hyperthing。嗯。Like。A few years ago。

 it's a super popular terminology for Intel CPU。Hyper threading。

It's a super important terminology for Intel。C票。And。Recently。

 AM M D Intel stopped working on it and AMD started working on it。But it's still。

 AMD never say is a hyperthing they don't have a commercial。They don't have a commercial name。

What is hyperthing？This is hypersing。What hyper thread is here。 You have a lot of threads， just。

Sitting there。Waiting to be exhored。And there's an issuer to detect which thread can issue instructions。

ok。人。Earlier year， Intel hyperthing， we have 2 H T。 That means there are two。

Threads waiting there to be excluded。 So if one one thread cannot be excluded。

 we exclude from another thread。ok。And I don't know if there are four hyperthring in AMD GPUs today。

 but what are the number of hyperthring in GPUs？Is 40， at least a 40 if we don't count the threat。

 the thread level， we're even counting at a work level， it's a 40 hyperthreading machine。Okay。

 threads that are sitting there and waiting to be executedd。Okay。

 then I know I haven't answered the question about hiding the latency of memory。

 But next time when we talk about VM unit and the cache system。

 let's talk about how memory system works together with the compute。

 with the instruction issue process。Okay， there are some some interesting design in AMD GPPUus。

