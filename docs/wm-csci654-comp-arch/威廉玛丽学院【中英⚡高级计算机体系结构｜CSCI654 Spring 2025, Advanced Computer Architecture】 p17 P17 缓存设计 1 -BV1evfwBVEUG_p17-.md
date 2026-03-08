# 威廉玛丽学院【中英⚡高级计算机体系结构｜CSCI654 Spring 2025, Advanced Computer Architecture】 p17 P17 缓存设计 1 -BV1evfwBVEUG_p17-

Okay， so in today's lecture， we're going to talk about cash。 then cache is part of the memory system。

 So it starts a new unit。 Then in a memory system， we store data。

 then the data needs to bring back to the core so that the core can compute。

 Then at the very beginning when in W Neman design。

 the Wom architecture we start to have the memory and the core to be separated。

 And one one most important definition in W in Woman architecture is the instruction and the data are stored both in the memory。

 So instruction are nothing special， but the part of data that describes your computer's behavior。

 And remember when when when Neman design this。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_1.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_2.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_3.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_4.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_5.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_6.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_7.png)

By the time when when Neman designed this system， he predicted that the memory system development cannot catch up with the core this development so the core can run very fast by bringing the data to the。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_9.png)

Bringing data to the core and storing the data back will take a lot of time will become a performance bottleneck。

 so that part is known as the Venuyman bottleneck。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_11.png)

So we started by talking about the general structure of a processor and memory system then in the general。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_13.png)

The description， we start with a processor and the processor will have a few。

Connections connects to the memory system。 So， for example， we have a memory ride。

 We have a address bus when it's wide。 it's a bus。 Now， when we say a bus， it's a。

A bundle of wires that can send multiple bits at the same time。

 then the processor also have a wire that is for the right data or there's a wire going back for the read data。

 Now is many design they just simply combine this right data and read data as one bus。

 they just call it data bus it really depends on some control signal to determine if the reader transaction or right transaction。

 So on which side you can pass data on this this set of wires。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_15.png)

Then we know we have talked about this before， so technologies for memory we have many different technologies that we can implement to store memory from asram flip flops all the way to those like prebuiled fabric and that can that goes to the moon right so we mainly look at these two technologies and they are rather fast that is suitable for store some frequently used data to pass to the core and there are other technologies as like the the magnetic disk or the tape。

 those technologies are not suitable for memory because they are too slow and they're not suitable for random location access so asRM are typically designed with flipflop then we know flip flops are likely to have 20 registers about 20 registers per flip flop but at this time when we talk about asRM we remove。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_17.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_18.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_19.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_20.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_21.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_22.png)

lots of read and write logic so that we have a set of read and write logic to be shared by a whole array of sRs so in this case we typically consider an sRM has six transistors that's the minimum transistor required for SRM unit on the D Ram is basically a capacitor and a transistor but the capacitor is just。

The transistor itself。 So we only need one transistor to store a piece of1 bit data。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_24.png)

So data retention it can host data as long as it's powered。

 but the Dm requires period refreshing and in terms of speed， SRM is very fast， the D is slower。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_26.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_27.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_28.png)

嗯。So when we talk about faster， it can be as fast as one cycle or sometimes can be tens of cycles at most。

 And D can be。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_30.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_31.png)

Upper tens of cycles to hundreds of cycles， so it's slower。

But the the density of S Ram is slow right is the sorry， the density of S RamM is low。

 so it takes more transistors， so it requires more area。

 So we cannot really build really large SRM storage， but for D Ram， we can build much larger ones。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_33.png)

Power consumption， it takes a lot of power than as D is consume only a little bit power。

 Then cost per bit is more expensive on this side is less expensive。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_35.png)

Right so this is another comparison that is from the textbook that we have this asM cost per bit comparison access time in terms of nanosecond then the bandwidth in terms of like gigabytes per second then D bandwidth you see it's here。

 this is typically we say for one memory controller or something then if we can paralyze the memory access then we can actually have a lot of bandwidth right now today if you buy a GPU Now what's the typical GPUs Dra bandwidth can be several terabytes per second So that's very easy to achieve this level。

 it's mainly by achieved by parallel so that you have lot of devices that can pump data at the same time to the core。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_37.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_38.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_39.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_40.png)

Now， SD are and H DD are even slower than it's less expensive， but its even slower。

 So there's no really the best。The best system， the best technology solution that works for everything。

 there is always a tradeoff and we need to select the most suitable one at the right location。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_42.png)

RightSo how typically a memory system works then in early stage in even before 1980s。

 probably we only need a core and memory a D and the D is not that slow if or clock frequency is super high。

 The D is fasts enough to keep up with the execution of the core。

 but as today we know the core runs at several gightz time and it requires a lot of data to pump into the core to keep the core busy in that case memory cannot be D is not suitable but S is not suitable either because it we want。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_44.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_45.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_46.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_47.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_48.png)

Tens of gigabyte sides of memory， but SraM can only be a few kilobyte inside a few mebyte at most。

 So in this case， we can only build in this way that we enter a cache in between the memory and the core。

 It's like we have like you rent storage outside。 and we also have a small storage room at home So we put those part of those things that are not frequently used in the storage in the bigger rented storage。

 but we put the most frequently used at our home so that we can keep using this part of data So we enter this cache here。

 then this cache is in there here， but because when you learn first to learn programming， you know。

 like when you access data。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_50.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_51.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_52.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_53.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_54.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_55.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_56.png)

You access from some address right when you access some from some address。

 you are actually accessing from the memory。 so early time program is written in a way that you read the data and write data into addresses you don't want to have two system of addresses So one system address for the catch one system address for the D so you don't want to change your program in that case you want to be architecture transparent or programmer transparent。

 So the program that you have written today。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_58.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_59.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_60.png)

Without cash should work still in a system with cash in that design。In that philosophy。

 in that principle， we keep this cache to be architecture transparent so that they do not have address on their own。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_62.png)

They only have the part that we can。Like improve speed。 but it still， if we access this data。

 it's still that piece of data， right， So it's only a method of performance improvement。

 So stores frequently use data and they can boost the effective bandwidth that going into a core if we have most of them are cache hits can find the data within the cache and it can also reduce the average laency reduced from hundreds of cycles back to a few cycles。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_64.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_65.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_66.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_67.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_68.png)

人诶。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_70.png)

Now even that the caches or asRs are not built in the same way。

 there are different ways that we can build a cache in some way the cache can provide more bandwidth in some way the cache can provide fewer cycles latency。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_72.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_73.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_74.png)

So in general， if we have different ways to build it， we want to build different level of caches。

So the closer to the core we have smaller caches and storing the most frequently use the data。

 it has low latency high bandwidth that are connected to the core okay a high bandwidth is typically means the high bandwidth within the whole chip is then if you only consider one cache unit here。

 there may be multiple cores right， then if you only consider one L1 cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_76.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_77.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_78.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_79.png)

Its typically have smaller bandwidth as compared to all the L3 caches combined。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_81.png)

Okay， so the closer to the core， the smaller and the faster， but the closer to the Dm。

 the memory side， then we have longer latency， but larger cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_83.png)

Now we use multiple caches to bring down the average latency and L3 cache。

 which is the level that is close the closest to D。

 iss also typically named as last level cache or LLC。

 So it serves as a proxy for the Dm So every data， every piece of every read and write request needs to go through the L3 cache And also from the perspective of a Dm。

 they also call it a bandwidth booster because every request goes to the L3 cache and L3 cache is a D you can pump data faster out Now if you have a good hit rate。

 you can boost the。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_85.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_86.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_87.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_88.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_89.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_90.png)

嗯。You can boost the bandwidth。 You can increase the effective bandwidth that are going out of L 3 as compared to the Dm and。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_92.png)

佢。And there's actually a tradeoff in terms of the layer of caches and the if you want more layers of caches or you want to reduce the layer of caches。

So the more level of caches since if you add one layer layer of cache then you need to look up in this cache now it a means it need to organize something and send another request to the bottom level so lookup takes time right so then going back you need to store back and then send the response up so every extra layer of cash you add will add some latency。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_94.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_95.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_96.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_97.png)

right。But it will also provide you some chance to。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_99.png)

Reduce the potential latency。 If there's a good hit rate。 So there's no good answer for。

Like how many cache， how many level of cache is the right answer。

 Then remember last time when talk about AMD GPPU architecture in GCN architecture。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_101.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_102.png)

In GCN 5， the last generation of GCN， AM D has two layer caches， L1， L2。

Then they start to have CN and R DNA， right。 So R DNA1 is the next generation as compared to GCN 5。

RD1 adds one extra layer of cache makes three layer caches R dN2 add another layer of cache makes it the four layer of cache so in barely two generation about three years time。

 three to four years time AMD transited from two layers of cache to four layers of cache and there's definitely some internal reasons and one player reason why they add the fourth layer of cache is because AMD has divide some really。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_104.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_105.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_106.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_107.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_108.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_109.png)

F technology that can build super large caches， several tens of mebytes or hundreds of hundreds of mebytes L4 cash。

 Now before that， they don't really have the last level cash like pure last level cash。

 that purely serve as the bandwidth booster。 then in in R in2。

 they add L 4 cash as the last level cash。 that's。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_111.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_112.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_113.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_114.png)

It's always every transaction needs to go through the the last level cash as proxy for the Dm。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_116.png)

Okay， so before talk about how caches are implemented I want to talk about this terminology called locality and locality is a terminology that we describe the memory access pattern that when we access a piece of data。

 it's very likely that we will access adjacent like exactly the same data later。

 or we may access adjacent data。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_118.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_119.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_120.png)

So since I described two parts， right， we may either access the same piece of data later that is described by this term called temporal locality。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_122.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_123.png)

So in terms of time right so we access right now we may access the same data later then so one example is if a loop repeat access the same variable process needs a variable。

 add one， add one， add one now we can put it in a register if the register size is not big enough we put it in a memory in that case。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_125.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_126.png)

It's an example for temporal locality that we don't want this data to go to the。Memory。

 we wanted to stay in the I1 cache。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_128.png)

Right on the other side， we have spatial locality。 and spatial locality describes if a program access or memory location。

 it likely。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_130.png)

It's likely to access nearby locations very quick， very soon。 For example。

 if you are iterating over an array in order， you access one piece of data in the next iteration。

 you access next piece of data， next piece of data， right so。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_132.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_133.png)

So those are common patterns for program then everyone who writes a program would typically follow these type of patterns so we can exploit these patterns or leverage these type of patterns to make our program run faster。

 And that's the motivation of building caches right Cas want to。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_135.png)

We do not expect pure random memory access， but we expect some patterns and what are the implications of the existence of temporal locality and spatial locality like temporal locality。

 we want to we want to keep the recently accessed the data in the cache for spatial locality we want to keep the nearby data if we have access one piece of data。

 we want to store some group of data around it so that later on we may access the same piece of data。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_137.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_138.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_139.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_140.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_141.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_142.png)

So this is spatial locality and temporal locality。Okay， then we always。

 every time we want to analyze a system， we want to describe。 Does it have spatial locality。

 What is the exact pattern that describes the temporal locality or special locality。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_144.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_145.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_146.png)

ok， then。That's a general introduction of the cache。

 Then we first look at the cache in terms of its interface and behavior。

 And then we go to see how it's internally implemented。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_148.png)

Now a cache， just think it as a black box， right， So when we send a read request。

 then read request a particular address， a then。We need to consider two cases。 One case is 0 x 4，0。

 Another case is 0 x 4，4。So why these two cases？Because typically，4。

0 is the unit that we're considering。 So this is a。

Because data caches are designed with some data buses to the top and some data buses to the bottom。

 right？

![](img/92d85e15a1465e52e0e23e65c4ef91cd_150.png)

Databaes means when there's a read request， no matter what we read。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_152.png)

Even if the。Core wants to read 4 by of data。 Sometimes a core may want to write， read4 by of data。

 sometimes we want to read 8 byte of data。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_154.png)

We don't want it to differentiate to provide one type of solution for4 B of data。

 Another solution for 8 by of data。 We always want to provide。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_156.png)

Like sufficient data so that every time it will send the same unknown amount of data to the core。

 the core can select which part it wants In this case， our data bus is 64 byte。O。

624 byte is quite common in today's CPU and GPU。嗯。At the bottom， we also have 64 byte。

 It doesn't have to agree with each other， but at least it's multiple， like it's very。

 very likely to be a multiple of two。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_158.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_159.png)

Like a a power of two。 Okay， so those are data buses。

 That means if we want to access just 4 B of data， we're actually accessing 64 B of data。

 And if we request this amount of data， it always goes come back with this amount of data。 Okay。

 so in that case， we don't really need to have a。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_161.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_162.png)

Like a wire， a set of wires to tell like how many bytes we want to write， we want to read or write。

 every time we send， we read or write is not amount of data。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_164.png)

So this is also called a cache line。 That means the cache。

 the unit that is stored in the cache as a whole。 So， for example， if we have4 byte within the cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_166.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_167.png)

If we have a4 byte within the cache， we actually have the whole 64 byte。

 a 32 byte or 64 byte or 128 byte。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_169.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_170.png)

Adjacent。The number of byte that is stored in the cache， and this is called a cache line。Okay。

 so a cache line is the unit's smallest unit that are stored there。

 and we want our cache line to be aligned with the boundary of these cacheline sizes。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_172.png)

So 64。I。0 x 4，0。 okay， in this case， when we want to access 40 or we on to4。

0 when or when we on want to access 4，4， we have two different cases。

 One is accessing at the beginning of this cache line。

1 is accessing and in the middle of this cache line and actually。F4 should never happen。

 then we should always add access at the beginning of the cacheline。If you look at this。

 if you look at hackx number， you don't feel why it's 40 or 4，4 or 4，4 here，400 or4。

4 here is just like run down to some like granularity。 But if you look at binary then。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_174.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_175.png)

Its basically， we don't need to send the last a few bit。 say if 30， if 32 equals 2 to the power of 5。

 in this case， the last five digit。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_177.png)

It's not necessary。 In that case， if we only send。Like， say 32 a bit address， right。

 If only 1037 bit， then we're good enough to describe a cacheline。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_179.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_180.png)

Okay， so let's say in this case， we have our cache misses or cache is not like we have an empty cache and we have some cache slot we can store some data there and in this case the cache misses data is not in the cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_182.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_183.png)

And then。做。We we need to tell if the cache is amiss or not right the data is there or not。

 how can we tell So that means we're not storing all the data within this cache。

 we're only storing part of data。 We need to know which part of data we're storing。

 So how can we know which part of data we're storing。We store our data。Okay， how large is the data。

 That's， for example， if the data。If the data is3 64 byte。Okay， then how large is the tag。

Let's just make it simple for now， let's say it's 64 feet address。Right。Just make it simple。

 Don Don't consider how how we can reduce the overhead。 So the overhead is one a。Overhead is one，8。

 right。 That means for every 64 B of data。That's 5，1，12 bit of data。

 We need to store some extra tag information。That is the address of the data that is being stored there。

So it's about one eighth of the overhead that we have to store in extra so that we can make it the useful cash。

Okay， so then we need for every unit， we need to store both of data and cache。 So now we， we know。

What is actually storing for that data。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_185.png)

And by looking into the tag， we know if the data is there or not。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_187.png)

If it's not there， we send another read re request to the bottom。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_189.png)

To the bottom unit， when we describe a cache， we describe the bottom unit as a memory。

 But if you consider multilayer caches， then it can be another level of cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_191.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_192.png)

ok。Then we wait for some time。 Then the data returns。 Data A returns， right。 Then data A returns。

 We on one side， we stored a here and put the data here。 We marked the。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_194.png)

Properly marked the tag with A address and send the data to the top so that top can know。 Okay。

 this is the。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_196.png)

This is the data I requested。ok。So。能。So this is how basically it works。

 then if we read the data again。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_198.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_199.png)

Now， I should have another slide。 The next time if I read the data again， this is a cache hit。

 In this case， if it's a cache hit， we know the data is already here。

 we directly return the data to the top。 Then it's much faster than。

It's much faster than reading data from the bottom。Okay， so then if there's a cacheline B。

 catchline C， catchline D， E F， then we eventually can store all of them in this tag until when we access some the cache。

 some pages， some addresses like G。 okay， if access G， then it's full， then we need to find a victim。

 find something。 and we kick it out。 Then this is a term called a victim block。 and。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_201.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_202.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_203.png)

And evicting the。And evicting that cashline block and evicting that cashline were evicting that victim block。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_205.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_206.png)

Okay， so then we are going to focus on how internally， in terms of circuit。

 how this mechanism is implemented and what are some tradeoff of different methods。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_208.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_209.png)

By the way。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_211.png)

Want to talk about this thing， the catchline size is 32，64，128。

What are the advantages of smaller cash liness。And what are the disadvantages。你 say。走。

Let's talk about large cash lines。C， L， what's the pro。And come。Yeah。

You can store more like sequential data。有。That's the advantage， right， I would say better。

Better utilize special locality。Right。人。What just name account。Proably store less。😔，Yeah。就。Fewer。

Nice， right。So you store fewer lines in there。嗯。So then there's a tradeoff， right， and another pro。

It's smaller overhead。Right。Like the tag is always one addressed。Now。

 when you double the cacheline size， you are hing the overhead。

So those are some of pros and accountss if we go deeper there are more pros and accounts。

 but you see there's a tradeoff right then it's always you need to be smart on selecting which type of what size then if you have strong spatial locality you' are very likely to access adjacent data in that case you want to use larger cacheline and if you have smaller cache lines if you don't do not have a strong spatial locality。

 you want to use smaller cacheline question architecture that have。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_213.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_214.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_215.png)

They're usually all of the same。诶。Yes， there are architectures with different levels that use different cache sizes。

And。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_217.png)

Here I'm also saying the bus data bus and the cacheline sizes are。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_219.png)

The same size。It's actually not always the same。 The data bus can be smaller than a cache line。

 I don't think there's any point of larger than a cacheline size， but it can be smaller。

 So for example， the cache line is 64 byte， but I can only have I have say 32 byte but I can have cache line as 64 byte or 128 by that is we can。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_221.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_222.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_223.png)

嗯喂。We have fewer overhead。Now we were more in that case。

 we are more flexible in terms of what data that we need to fetch there， okay。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_225.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_226.png)

Also， I have to say there's another con。That is banned with utilization。

So if you every time you load 128 byte right every time you load a lot of data。

 you either increase the latency or increase the energy consumption。

 Now if you need that part of data， that's definitely a good thing， it's worth the effort。

 but if you do not need the data it's not worth the effort， right。

 So if you still have something like 128 byte。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_228.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_229.png)

ACache line， but 32 B data bus。 that is called sector cache。

In the sector cash there many different variations， in that case。

We both have low overhead and better bandwidth utilization。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_231.png)

ok。So different cacheline sizes are okay and the bundle data buses on the top and the bottom doesn't have to be the same thing。

 Cacheline size can be a different number， so they are all independent parameters。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_233.png)

Our simulator do not support that， thats something that we can add。

We support different cache lines as at different levels， but the lower level must be bigger。ok。能呃。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_235.png)

ok。It's a discussion on catchline sizes。 So by the way， on AMD GPUs。

 they extended from 64 byte to 128 byte because they think oh today's application have better locality。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_237.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_238.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_239.png)

When we talk about rights， the right writing process， then。There are some。

Some pros for smaller sizes。 Now we can talk about later。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_241.png)

Cashmalanem， how it's designed internal of circuit and how internally it works。

So this is a circuit that describes how a cache works， let's describe it together。So on top。

 we have a address bus。Okay， let's just say6 for a bit。 and send the address here。

 Now we have tags stored there。 I want to write eight of them， but accidentally make seven of them。

 not a big problem。 Okay， so there's a comparator to compare this address with each of them。

 So then apparently， you don't want them to store the same value。 In that case。

 you always only have one tag one comparator enabled。 Okay， to have one output。

 Then you have an encoder。 encoder is basically you convert this this each bit into some。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_243.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_244.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_245.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_246.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_247.png)

Like coding， encoding， right， then if you have 8， then you need 3。Output， so in this case。

 it's 8 to 3 encoder。8，2，3 encoder， right，8 options。 Then you have only need3 bit。

And this one goes to a multixer。So think about this data， this data are pretty much registers， right。

 they can always provide the data。So these data will are connected to a multiplexer。

 and the encoded data will control which。Outcome， which。

Data can be connected to the outcome in this case， here is this wire is connected to the data output。

 then this data goes out。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_249.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_250.png)

ok。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_252.png)

Pretty simple design。 then in some smaller scale caches， then caches are really designed in this way。

 in some larger caches， caches are not designed that way。

 Now give you think several hundred kilobytes that is definitely not designed in this way。

 but that's just keepbit at taxable level。 Just make it simple for you to understand。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_254.png)

ok 诶。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_256.png)

And this is also a very simplified design because I do not have the right logic。

 I do not have the part， like how we handle cache misses。 We assume there's a cache kit， right。

 So it's just a simplified design。 Just understand the general mechanism is good enough。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_258.png)

We're not going down to the circuit level anymore。那。The data offer will get the data。

 The data goes back。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_260.png)

So we can talk about what is attack and what is actually need to be stored within attack then for 64 bit addresses。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_262.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_263.png)

Today， pretty much all the machines， CPUUus and GP PUus are 64 bit machines。

64 bit machines use 64 bit addresses as。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_265.png)

As addresses， right，6，4 bit as addresses。 but do we really need that many bit。 the answer is， no。

 we do not， right， because。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_267.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_268.png)

It's a huge amount of data size and we don't really have memory in this large and our CPUs are not designed to suppose to support lead large memory。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_270.png)

2 total the power of 30 is1 gig。2 or 40 is1  TB。2 total a power of 50 is one petabte。

Then60 is something I don't even know。其他 about or something then。

Pyabbyte memory is do not exist today， so in today's system we don't really need that larger address so we can have some smaller addresses。

 so typically in X86 or in GPUus， we use 48 bit address system to reduce some sizes then for the highest level we simply either feel0 or just use some extension。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_272.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_273.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_274.png)

We do not really send it so that we can reduce some data transfer， some wires。

 reduce some die size and reduce some energy consumption。On the other side。

 we don't really need a cache line offset right We don't need a part that within the cache line。

 So in that case， we reduce 8 B。 then make that a 42 B tag。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_276.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_277.png)

Okay， that's the actually number of bit number of bit within the attack。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_279.png)

OK就呃。But there is one problem with this design， So this is a8 entry。AndCash is okay。

 It's not a big problem。 But if you consider overhead， we already have 32 B as an overhead。 Now。

 here， we also need a comparator。And this comparator。嗯。Can take a few bits or a few some gates。

 right， Now if we really have a lot of entries， this overhead is not negligible。 Now。

 we really don't want do not want so many comparators to occupy the space and consume energy。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_281.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_282.png)

RightSo we want to reduce the comparators。 Do we really need that many comparators。

Then the quick answer is， we do not probably。We cant even make it work to have only one comparator。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_284.png)

So how can we make it to work with only one comparator。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_286.png)

We do this。Only only one comparator。 We do this。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_288.png)

If this is the address。And think about this address in three parts。

The lower a few bit are do not take， say the lower a few bit。 and say we take 3 B out of this。

Address， right。If it's 0，0，0， we define it can only be 0， be here。If it's 0，0，1， it can only be here。

02 can only be here and so on。Right， is 1，1，1 can only be at the end at the last slot。So if it's8。

 if it's 8 bit。So if it's there 8 entries， we have three bit。 if there are 16 entries。

 we have four bit and so on。Right so it's a very simple consideration。 We just。

 we define a particular address or particular cache line can only reside at one location。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_290.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_291.png)

ok。If another address that arrives at。Aris at a discussion and only also have 0，0，0 at this location。

 We have。 we cannot evict another one， even if this one is empty， we cannot fill in here。

 We have to fill in the first place。 This is by definition。 This is the cost we pay。

By reducing the comparator， but we can put the multiplxer at this location。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_293.png)

And use this 3 bit to control。 So which one can actually go through this。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_295.png)

Miper and can go on to the comparator。Now， in this case， we only have one comparator， right？

We only have one equal equal sign here。 Now， if it's equal， then we know it's a heat。

 If it's not an equal， we know it's a miss。Okay， in that case。

 we also use these three bit to control the data bus here。 Okay， assuming if it's a hit。

 then we let this data to go out。In a miss then we need to do something else。

 but that's not something that we show in this figure。Okay， so so this is a much simpler design。

 We only take one comparator and it's still a cache and still works。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_297.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_298.png)

Okay， so we split， we call this thing a set。 So we split the cache into8 sets。

A certain address can only go to one address。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_300.png)

How we can know which address it goes to we select 3 bit out of the address then use this 3 bit to determine which side it goes to。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_302.png)

Okay， then in this case， remember， if you notice here， we're reducing from 30。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_304.png)

We're reducing from 42 down to 39 bit tag because the set information。This three bit。

 we don't really need to store the three bit there。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_306.png)

Okay， we don't need to store this three bidder。難聴。Then the question is， which bit。

We should select in theory， we can select any bit。we can select any bit within the address。

But which addresses are the best。They say， can we select the most significant three bit？

What happens if we select the most significant three bit。The memory is always matter。Yeah。

 so if we select， if， if we consider， we select the most significant 3 bit and we only use 1 MB of data。

 then that 1 MB of data goes to。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_308.png)

All goes to。One set， right。 So you are only utilizing one eighth over cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_310.png)

So that's how bad design。Right， so we wanted to be even。

So we wanted to have the same opportunity to go to every cacheline。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_312.png)

In that case， the most reasonable selection is。Its the least significant bits right above the offset。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_314.png)

ok。I can tell you in one particular reason why we do not want to use this a little bit。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_316.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_317.png)

In AMD GPU architecture。They reserve one1 extra bit beneath this。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_319.png)

Offside bit。So they have this thing。 This is the。Sa most significant bit。And this is the offset。

And they reserve one bit here and select the list of you as their L2 caches。I don't call it a set。

 and it's a bank。Selectctor。Why they do that？Why reserve one here？

Is because there's another layer done。 So this is an O2 cache。

Then each L2 cache is connected to two memory controllers。

So there's another level down here that is to cacheline level interling。

But so this one is doing an inter livingaving at a granularity of two cache lines。Okay。

 this is just one very particular reason why you do not want to select this a few bits as the inter living unit。

 But here we're saying this term called interl， that means。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_321.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_322.png)

Catchline 1 goes here。 One goes here。2 goes here，3 goes here， and 7 goes to the last。 The A goes to。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_324.png)

So I should start from 0，0 goes here。7 goes less A goes to the top，9，10，11， and so on。

 Then5 16 goes to the top， right， So this is called interl。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_326.png)

Then if you consider if this is a concept。Concept of time， temporal concept。

 you would call this is around Robbin。 right Now in spatial concept。

 you would call this concept interling。ok。Then okay， so the problem with this design。

 as we talked before， is very， very likely to have。Conflict， right。

Just consider if you have eight cache lines。If you have8 cash lines。Sorry，8 sets。

Right then eight sets with each size to be 64 byte。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_328.png)

Then that means 8 by 64 is。5，12。Right。Then， just consider this。If you have a matrix。

They has like single precision floating point。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_330.png)

I have 32 type each。Is each unit。Okay， each unit is F 32。If you have 1，28。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_332.png)

아 미죠。If you have 128 unit in each row。ok。And you happen to want to access the data in this way。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_334.png)

What gonna happen。いいです。This unit goes to。Set 1。This unit goes to set one again。

This unit goes to set one again。ok。Then you have no temporal locality。 You have no spatial locality。

 and you keep evicting data out of the same cacheline， and you are not using the rest of the。Cash。

Okay， this is a very specific problem。Related to this type of cache design。

 This set based cache design。O。So we want to mitigate this problem。

But we don't really want to pay the cost of so many comparators。

So can we find some mid ground between these two design。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_336.png)

Somewhere between。More than one comparators。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_338.png)

More than one comp， for example， if we have two comparators， how can we design this cache？



![](img/92d85e15a1465e52e0e23e65c4ef91cd_340.png)

This is confusing that every time， although I'm very very familiar with this topic。

 but every time I need to consider， oh， this data comes， where it stores。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_342.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_343.png)

Like even just preparing this slide， that I was considering this problem。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_345.png)

ok。We say。In this case。We have two comparators， right？

Two comparators means we can compare two piece two addresses for every arriving address。

 for every transaction， we can compare two addresses。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_347.png)

Now if we compare two addresses， that means we have two different locations that we can store this data。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_349.png)

It doesn't really matter if I write it set one， set1， set two， set two， or set 1，2，3， 1，2，3。

 it doesn't really matter it's just independent some locations okay。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_351.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_352.png)

So set one still here。 But when a comes here， when a comes in here， then if the set has。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_354.png)

0，0。 Now we know 0，0 goes to set 1 or set 0。 It can either stay at here or here。

Its two locations now we can sort this。This cacheline。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_356.png)

난。Within each way， then we can know of which side， which sets that we're selecting。

 then this set bit will be controlling way1 and way2 multiplexer。

 So only set one addresses can go through this multiplexer and go can go on the comparator。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_358.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_359.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_360.png)

Then the tag part will be controlling， will also be fed into this comparator and determine if it's equal or not。

啊。ok。determineter if it is equal or not。 then they are feeding into the encoder。 in this time。

 this is a2 by2 to one encoder。2 to one encoder。 There's only one bit。

 but we still need a set bit to be combined with this encoded bit。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_362.png)

So that we know which one we were eventually selected。Or I call， I call this way selector。Okay。

 these are a set selector and way selector so that we know which one can generate the output。

In this case， we are still selecting this one。오케이 내 say 내 say 얘기야。From the interface。If a comes in。

 we know it's empty， a stores here。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_364.png)

Okay， now if B comes in and B also occupies S 1。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_366.png)

Then we store it inside one again， store it here because we know this one is empty， if they're empty。

 we definitely don't want to evict a。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_368.png)

It can store here。 Now， if C arrives again。If sea arrives。Again。Then， we。No， okay。

 A and B are occupying that one。In this case， we need to decide either to evict A or evict B。

 but that suppose we evict A， then C is written here。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_370.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_371.png)

Okay， so in this case， this is called a two way associative cash。Okay， because it has two ways that。

You can understand this term of way in this。Two different ways。 Two different methods。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_373.png)

A number of ways describes how many comparator are there in the cache。If it's two way。

 then there are two comparators or you can understand in a way that how many locations that a piece of a dress can store into。

Okay， if it's too way。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_375.png)

If it's two way associative， then we can store this piece of address discussion line in two different locations within this。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_377.png)

O。This is this is how we can understand this way of saivity。Okay， then it comes to design decision。

In what case we want to have higher number of ways In what case we want to have lower number of ways。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_379.png)

Now， we can。Understand in this way， you can definitely see this is a spectrum， right。From on one。

Exreme， we call this like， we put compare one comparator to every cacheline。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_381.png)

In this case， we call it fully associative that means a piece of a address。

 a cache line can store in anywhere within the cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_383.png)

Okay， this is called fully associative。 in this case， we say。The way equals to n。

 and we only have one set。Okay， one side then that means 0 bit。嗯。0 bit for the set bit。Okay。

 then y equals the N n。 That means we have n different location that we can store this data。

Second the original one you share was fully。Sa this one if you have8 entries。

 and there are8 comparators， they are fully associative。Now， in the middle。

 we have this idea called way associative， we can either have two ways asciative。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_385.png)

Wway out of8 way，16 way，32 away。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_387.png)

64 away。anthing。But at least this number is smaller than the total number of slots within this cache the cacheline slot within this cache。

 So then set equals to n is the number of slots divided by w。

 The W is the number of ways and y is defined by the parameter。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_389.png)

Now on the other side， we have this thing called direct mapped。Direct them map means。

There's only one way， there's only one location for each each piece of data can reside。

 and we can directly calculate where that this piece of data can be stored。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_391.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_392.png)

In this case， we have the most number of set bit。嗯。We have done most a number of set bit。

But we have the least。Possible location that each cacheline has be stored into。

So what is the advantage of each design。Or on this side of the spectrum and on that side of the spectrum。

And I think the quick answer is。The more ways， the better the performance。The better the heat rate。

 the more likely that our data can hit there。But the disadvantage。It's not fully associative。

The fully associative will have more hardware cost， okay。

Then you really need a lot of energy and die size。就。A question is。If the cost。

If the penalty for a cashms is very high。Which one we want to go to？Which one we want to use。

So go on that way， right， Go on the fully assertive way。If the penalty of a cashshms is very high。

 we want the heat rate to be as fast， as high as possible。 in that case， we use fully asive。Now。

 if we have tight budget， then we use direct map， okay。

So direct the map today we can almost never we can almost not see it even two way asive is very rare for L1 caches is more likely we have four way asive today。

And only four comparators，2 to4 is a small change。4 to 8 is a large change， right。

 every time we double away sensitivityivity， we probably only increase the heat rate by a little bit。

 but we pay a lot of extra cost。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_394.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_395.png)

Then in lower level caches， we can see something like 16 way， 32 way。

 but I rarely see more than that。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_397.png)

Now， another thing we also rarely see fully asative because the cost is very high in one exception then。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_399.png)

I think definitely we later on， we want to talk about address translation。 So T， O B。

 especially L1 T， O B， are very likely to have。诶。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_401.png)

Fully assuciative design， T LB is the data that is stored for translation。ok。

They're stored for translation。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_403.png)

So if you miss at TLB， you go to something called MMmU， you page， you do a page table work。

 a page table work is several hundred to thousands of cycle latency。

 so the miss latency is very high and your cache is actually very small in that case。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_405.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_406.png)

They tend to use a fully assuciive design， okay。But even L2 or TLB， L3 TLB， if there are L2 L3 TLBs。

 then they are likely to use something like 16 way or 32 wayusivity。

 they don't use fully asusative design。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_408.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_409.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_410.png)

Okay， then five more minutes。 Let's talk about replacement。 So who should be the victim。

 Then when the cash is full， we need to find a victim。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_412.png)

So if we have access A and access B and access C， then which one we want to evict。

 We have several options。 the most commonly in design is least recently used。

 That means if we access AB C， that in this case， A is the least recently used。

 we evict A right if we access A B A in this case， B is the least recently used， we evict B okay。

 this least recently used。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_414.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_415.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_416.png)

What else？With the problem with LR U is is generally not actually not that easy to implement。

 if you consider a very large cache， but with only a few ways， we need to keep a queue for every。

For every set， right， there can be many set where each site can be quite large。

And this a random access， right， If you say， oh， we access this one， we first need to find it。

 move some part of data forward and put it to the back。 So it's actually very annoying。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_418.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_419.png)

Not very easy to implement， but it' still even its not easy to implement is still some common design。

 or there may be some tricks that these vendors play。

 these companies play to make it almost least the recent use。

 but with some possibility of making an error。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_421.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_422.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_423.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_424.png)

But。Let's say some other solutions first in first out， what is first in first out， that means ABC。

 ABC A in both ABAC， in both case， we evict a because a is arrived first no matter if access later or not we evict a in that case were simplifying the least reason to use the Q management so we don't really need to shift everything and in this back。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_426.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_427.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_428.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_429.png)

Simpr design and in terms of performance。Not that bad。Okay， I should split it into two slides。Random。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_431.png)

So every time we find one， we want to randomly ector something。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_433.png)

ok。And most recently used。That means do we have another slide。 No， okay， if we access ABC， A。

 we evict B If we access， So ABC， we evict B， If we access AB， A， we evict a。

 which one is most recently used， we evict it。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_435.png)

Now you may feel random and most most recent used are quite weird， right？



![](img/92d85e15a1465e52e0e23e65c4ef91cd_437.png)

It's actually not that weird and it's useful in some particular cases。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_439.png)

I say， yeah， compute once， that's a good example， for example。They say we have a convolution， like。

 you know convolution， how convolution works， right， You have a matrix。

 then you have something called a kernel。The three by three。

 then you apply this kernel and you swab across the whole matrix， right？



![](img/92d85e15a1465e52e0e23e65c4ef91cd_441.png)

This kernel data。It's used again and again， again again。 Every time you are using this piece of data。

 right。But this part of data is not that that commonly used， right。

But you'll keep loading new data here。 So if you are using something like a54 design。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_443.png)

You evicted after sometime evicted again， after some time evicted again， right。

 but you actually need it a lot。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_445.png)

Now， in this case， a random will perform better than54。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_447.png)

ok。And in another case。If you have a。Matrix， I make case smaller。Only this large。And it's 1。

1 times larger than your cash。 just making some interesting example here。

 just slightly larger than your cash。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_449.png)

What happens is you're accessing the whole cacheline， you're accessing the whole。

 you're accessing the whole matrix。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_451.png)

At the end。呃。Okay， let's make it。Changes slightly， two times larger， O。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_453.png)

At the second half， you start to evict。youvicked the the first half。Right。

 now you need to process this matrix several times。The next time you come back。

 you find that it's a cashshms。Mis miss miss miss， you start to evict the second half when you arrive at this point。

 it start to miss miss miss again。 it's always missing， comeback， it's missing。Go here is mission， O。

These is a terminology called cash threashing。That means you keep evicting data。

 then require this data again， evicting some data and requiring this data again。

 so because you are accessing too much data， your cache can then handle。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_455.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_456.png)

Right， your cache cannot handle then you cost stretching。

 That means you're evicting the data you actually need。No， in that case。

 think about most are recently used。At least。You always have this partner。Right。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_458.png)

You always have some part of like your earliest to access data， or if there's a convolution kernel。

 that you access that part of data and commonly use the kernel， you commonly use the data。

 you are likely to store it in the cache， then you are likely to make its stay for the longest amount of time。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_460.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_461.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_462.png)

So most recent used cash is actually。Sometimes a quite effective design。Okay。

 that's the end of today's lecture。 Then next time， let's talk about writing into a cache。



![](img/92d85e15a1465e52e0e23e65c4ef91cd_464.png)