# FAST25存储大会-｜-USENIX-Conference-on-File-and-Storage-Technologies-p18-P18-HiDPU---A-DPU-Oriented-Hybrid-Indexing-Scheme-for-Disaggregated-Storage-Syst--BV1HmVXzME4J_p18-

。

![](img/13968c0a1f18abb4a73453fe8ecca8fe_1.png)

Hello， everyone。 This is Zhu Wenbin from Shandong University。 Today， I'm going to introduce our work。

 Hi， D P U， A D PU originated hybrid indexing schema for disd storage systems。In modern data centers。

 the data processing unit is replacing the traditional network interface card to handle communication with computing servers。

By integrating computing。Networking and storage capabilities。

 The DPO acts as a smart and programmable processor on the data pass。

With the potential to accelerate data processing and reduce CPU load。For example。

 upon receiving an our request。The D PU can further retrieve the physical device address from the storage controller in the CPU said。

Its line construct the PC IE command to directly access storage devices。In this way。

 redundant data copy between CPU memory is removed。And the data efficiency is improved。However。

 in this procedure， the CPU is still involved to translator addresses。

In the storage server of distributed storage system， CPU resources are limited。

 and involving CPU computing also brings associated overhead。

When processing massive concurrent oil requests。The latency of this ccentric address translation can be high。

So our motivation is to offload the index of mapping table and do address translation in the D P U。

However， there are several challenges for indexing in DU。First。

 the D memory is extremely limited compared to the size of mapping table。On this stage。

 P PO must store most of data in the own memory， but interaction overhead through PC IE DM A could also be high。

Besides， so has many calls for processing concurrent work。

 Each core of DPU only has a limited computation power。To address these challenges。

 an efficient index structure is essential。We start our work by exploring current index structures for storage mapping table。

Multtile page table is fast， but better at space efficiency due to its inherent horse in each level of subts。

Learner table constructs learned indexes or making table to achieve better space efficiency。

But it requires extra local search due to the prediction in accuracy。

Perfect hush table offers both good lookup and space efficiency。

But it doesn't support real time index update and incurs high reconstruction overhead。

So unfortunately， there is no current index designed for D PU and could effectively address these challenges。

In this work， we propose high DU。It is composed of three main components。First。

 a hybrid index includes a inner index that fits into D P's limited memory。

While the auto index is optimized for efficient searching。

A DPU of loaded cash is employed to further reduce unnecessary interactions with CPU memory。At least。

 at last， asynchronous index update strategy support processing complex index update operations。

In了 CPUPU。And ensure D P focuses on simple， but frequent index query。

We start introducing the detail of the high D PU by hybrid index。

The hybrid index is composed of a learned index， and continuity based segments。First。

 a segmentation algorithm divides the mapping table into fixed segments。

H D P will create different indexes for segments， with different levels of continuity。

Except of accurate segments。Perfect hh table based segments have secondary hhing parameters called pilots as alter index。

Next， a learned index is built with the first key of each segment。Segmentation and learned index。

Make sure the size of inner index can adjust to the constrained D P U memory space。

To find the corresponding mapping entry of a logical address。

I DP first determines which segment it belongs， using learned indexes。

If it belongs to an accurate segment。The target position is get with the base address， and an offset。

If the logical address belongs to a P T Hsh segment。

 high D P will first retrieve the pilot value through a hush and D MA operation。

Then perform a second hasush with the pilot value to find the complete free target position in the mapping table。

The linear based P T H segment works similarly with P， T H segment。Except that the pilot value。

The pilott position is determined through a division operation， instead of harshush。

For aggregate segments， one DMA is already sufficient to fetch the mapping entry。

 but for P T hsh and LP T hsh segments， an extra DMA is needed to get the pilot value。

To address this， high D PU introduce a pilot cash in D P U。It uses optimistic locking。

Which loads the entire cash group into thread's private space and compare the Is to find the right pal value。

Before updating cash。It will check the group counter to find the next right ball position in the cash group。

 which helps preventing right conflicts。Besides LP T hassh utilize the segments with considerable continuity to group adjacent keys into a bucket and share the same pad value。

Experimental result shows this code effectively improve the heat ratio。In high D PU。

 D PU handles simple and frequent read operations， where complex and practical index update caused by right operation is handled by CPU。

W operation may require mapping tables， update， delete or insert。

The first two can be done in place within the meeting table。

But inion might lead to the index reconstruction。To address this。

New insertions are stored in a cook hush based bubble。

Which also allows D P U to check the latest key with the one round of D MA。When the buffer fills up。

 local reconstruction is triggered to rebuild the segment index。

The buffer will be first divided into each segment， according to the segment's first key。

And each segment's reconstruction is independent with others。

The version number in segment metadata help to identify the expired cache entries。

Note that local reconstruction doesn't require updating the learned models and won't affect queries for other segments。

IDP will only update learned models during global reconstruction。And it is in fact during the season。

 I。We have implemented a high CPU PU prototype on a Huawei D PU。It has  four MB of internal memory。

 shared by all threats。And each D P threat is also equipped with 4 kB of private memory。😊。

We have also implemented several optimizations in the D PU to increase the efficiency of processing learning indexes。

They include fixed point model calculation， High plan based local search and data use。B compression。

We implemented two baseline indexes， D page and Dle。

D page is a three level page table with the first level of loaded to the D PU。

Deland builds learned indexes on the mapping table and addressed the error bond to try to make sure that the learned indexes can be uploaded into D P memory。

Above optimizations of learned index are also applied to the D。

Workloads used in the experiment are from two sources。

The first is Microsoft Research Cambridge block I traces。

 and the second comes from the real time oil requests captured from a female based server。

Running various， real world applications。This table shows the scale of traces。

We have also open sourced a functional CPU version of high DPU。

It doesn't rely on DPU and simulate all operations of high DU with only CPU instructions and o memory。

Overall， performance shows the throughput and average latency with different number of clients。😊。

D page always needs two random DNAMA operations for each query， making it less efficient。

Body learned1 address continuity is high。It only requires one single DA to fetch the predicted mapping entries into the DPU。

Which makes it more efficient than D page。However， when the address continuity is low。

It needs to fetch more data into the D P memory and perform the local search to find the correct position of the target mapping entry。

Which also reduces its efficiency。With the help of pilot cash。

 high D P has more than  net 2% probability to obtain the target mapping entry with only one DMA operation。

Which gives it the best performance， among all traces。😊，As a result， I DP can achieve a minimum of 1。

5 times to a maximum of 6。3 times performance improvement。

The D P memory usage of all indexes are already constrained to within 4 MBB。Here。

 we present the CPU memory overhead of different indexes。

The memory overhead of the D page comes from its house in each table。

And Dland has to store the logical address， along with its mapping entry for local search。

Space overhead of high CPU mainly comes from its perfect hash table。

It traces of the complexity of index construction by allowing acceptable holes in the mapping table。

As showing the figure， high D P shows stable and lowest memory overhead across all test traces。😊。

One exception is trees's project。Well， D page has lower memory overhead。

Because this trees is mainly composed of large fields。Leaving few holes in the page table。

We then expanded the test site to the pet better scale storage。

To test the scalability of all indexes。With the extended trees。

Both D page and high D PU successfully construct and off their indexes into D PU。However。

 the number of holes in D page also increases as the data set grows。

 leading to significant CPU memory waste。On the other hand， as the data set expands。

 De learned quickly fails to construct learned indexes that could be uploaded into the D P U。

We then evaluate how index reconstruction impacts the performance of high D P。

Since the local reconstruction is conducted in the background， it won't block the index queries。

The only effect is that it may cause cash expiration。As shown the figure。

When local reconstruction occurs， the pilot cash may experience expiration and misses。😊。

But thanks to the LPT harsh segments， the the reduction in cash hit ratio caused by exp is no more than 10%。

And the overall performance degradation is negligible。

We also comparedd high D with the recent learned app。

 which accelerates queries using a cached mapping table and learned indexes。Unfortunately。

 learned FTL struggles to be uploaded to the DPU。Because of its fixed size speed map。

Which requires one bit for each possible mapping entry。Therefore， for fair comparison。

 we also implemented a I DP version that runs entirely in CPU and also memory。

Which is referred to as high DP H。We also make sure the high D B H has the same old memory usage with learned A。

Since the high W H and London F TR run on the CPU， they both incur the overhead of involving CPU for each query。

Which significantly degrade their performance。English work。

 we explore the use of D PU to accelerate the data pass in distributed storage systems。

Without indexing， the D PU still relies on the CPU for address translation。Which is extra overhead。

And uploading the index to the D PU facing challenges such as limited space。

 interaction overhead and low computation power。To address these challenges， we propose high DU。

 which integrates techniques to overcome each of these issues。

We have also implemented a high D PU prototype on a real DPU， and evaluated its effectiveness。

This is all about my presentation。 Thank you for listening。For more details about this work。

 please contact me by the underlying email address。

 I will be happy to answer any questions you may have。😊。



![](img/13968c0a1f18abb4a73453fe8ecca8fe_3.png)

![](img/13968c0a1f18abb4a73453fe8ecca8fe_4.png)