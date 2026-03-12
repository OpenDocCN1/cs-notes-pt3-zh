# FAST25存储大会-｜-USENIX-Conference-on-File-and-Storage-Technologies-p13-P13-IMPRESS---An-Importance-Informed-Multi-Tier-Prefix-KV-Storage-System-for-Lar--BV1HmVXzME4J_p13-

。

![](img/6df43157f62355e5897ea743ece4884d_1.png)

![](img/6df43157f62355e5897ea743ece4884d_2.png)

Good afternoon， everyone。 This is Wei Jianchhen。 My advisor is Xhui Binghe from Georgia University。

 It's an honor to introduce our work in press， which stands for an importance informed multiter prefix K storage system for larger language model inference。

 This is a joint work with Huawei Cloud。😊，The larger language model has gained a lot of attention and has been widely applied in various fields。

 such as chatbos and search engines。 Modern LLM applications often pre information rich contact prefixes to user queries before sending them to the LM for inference。

 Many requests share the same prefix tokens， such as system prompts in GT plugins or similar questions retrieving the same documents in R E G systems。

Since the shared prefix tokens have the same K cash generated in the previous stage。

 recentcent work has proposed storing this shared prefix K cache in GPU or CPU memory。😊。

When new requests with the same prefix tokens arrive。

 the KV cache can be asynchronizely loaded and reused， reducing redundant computation time。

 The right figure illustrates the time to first token of a simple3 layer year Lm inference。

 It shows that this approach significantly reduce the TTFT compared to recomputation。

As shown in the bottom left figure， this advantage exists across various prefix lengths。

 ranging from 128 tokens to 8000 tokens in our tests。😊，However， as the number of requests increases。

 GPU and CPU memory become insufficient， and KV cachees must be stored on disk such as SSDs。

 Unfortunately， loading KV cash from SSD introduce significant I latency。

 which can now be fully hidden by asynchronized loading and are exposed on the critical paths。

Our tests show that the I O tie accounts for over 50% of TDFT。

 making K loading from SSD to GPpU a new performance bottleneck。😊，To address this issue。

 previous work can be divided into categories。 The first relies solely on GPU CPU。

 which is limited by cache size and still require substantial recomp in large scale scenarios。

 The second one uses scheduling information to prefi unnecessary prefix kvs from SSD to CPU memory before task arrival。

 However， this approach is inefficient under high request loads or preemptive scheduling。

 We consider whether it is possible to reduce the amount of reus Kv data that needs to be loaded thereby reducing all time。

Recent recent research has shown that retaining only important Kvs during the decoding phase can achieve similar in accuracy。

 as demonstrated by H2 O and ingen。This inspires us to load only important Kvs during the peripheral phase to mitigate the I bottleneck and reduce T TFT。

😊，However， this approach faces challenges。 First， identifying important kvs introduce significant IO overhead。

 For example， given a request with N tokens and three heads in one model layer Here is the prefix K and V stored in SSD we need to load all pre keys into GPU memory to generate the attention matrix then we identified the most important kvs in each head marked in orange here。

 Finally， only the important values are loaded from SSD。

 we found that the reduction in kvs is limited only in step 2。

 because identifying the important kv in each head request substantial IO。

 One might think that since kvs are shared could statically predetermine which kvs are important based on historical information and load only those。

 However， our tests on two OP models show that。While this static method reduces I data。

 it leads to up to a 5% accuracy loss compared to dynamic identification of important Kvs。

 which is unacceptable。The second challenge is that existing storage and caching systems are suboptimal。

 as they do not account for importance of token's Kvs。Specifically。

 storage systems suffer from read andplification because a tokens kvs are packed into the same data trunk。

 mixing important and unimportant Kvs。 The left figure shows the proportion of important kvs in each data trunk。

 when only important kvs are loaded。 unimportant ks are also loaded into memory。 On the other hand。

 caching system are based on reason or frequency。 The right figure shows that there is no direct correlation between importance and frequency。

 One data trunk with high access frequency may have a low proportion of important ks。Next。

 we will introduce our observation and design to overcome the above two mentioned challenges。

Here is the overall architecture of I。 It includes an important token identification module to tackle challenge one and KV reordering and cache replacement to optimize storage and caching for challenge2。

To reduce the loading of prefix K， we observed that there is high similarity in the set of important token indexices across different heads within the same layer of N M。

😊，Here is an example。 Suppose the important K indexicees for two heads are 0，2 and 01。 respectively。

 we use the ja inside to index to measure the similarity， which is one third In this case。

 The second figure shows the real similarity between every two heads in a layer of OP T 30 billion model or above 0。

9。The right figure demonstrate that this similarity exists across different IM scales and important K ratios。

Based on this observation， we propose similarity guided important token identification。

 The key idea is to use the important token index set from a few selected heads to approximate the important token index sets for the remaining heads。

 Let's take an example， the left figure shows the the process without our method and right figure shows the process after enabling our method。

 it first loads the prefix keys of only a few heads。 say one head。

 then identifying the important token distribution in this head。 Next。

 we approximate the important K distribution in the other heads and loads only these important keys and values compared to the left existing method。

 Our approach significantly reduce the amount of prefix keys loading in step one Since not all years have sufficiently high similarity。

 we selectively applied。This method only to high similarity layers for low similarity layers。

 we still use existing methods on the left to ensure inference accuracy remains at the similar level。

To address the storage read amplification challenge。F reorder kvs based on token importance。

 separating important and unimportant kvs into different data chunks。

 This reduce the number of chunks needed to load mitigating read amplification。 However。

 reordering affect the structure。 The figure a shows an example with two requests。

 one has token t 0 to t 7 and the other has to t 0 to t 3 followed with T8 to t 11 Among them the orange the orange tokens T 0 t 3 T4 and t 9 are important tokens。

 We cannot directly reorder them to gather these four orange tokens into one node。

 because it was disrupt the structure as t 4 and t 9 are not shared tokens Therefore。

 we avoid cross node redering and add mapping list in each node the mapping list like m0 are used。

To recall the mapping relationship between token inices before and after reordering。

 So said the original token sequence can be restored during inference for the caching challenge。

 we introduce a score based cash cash admission and replace method。

Instead of relying solely on excess frequency， we consider the proportion of important tokens in each chunk。

 For example， assume chunk 1 trunk to have excess frequency results of 1。

5 to 1 and important K results of 50% and 100% respectively LF prioritize chunk1 for the faster cash while our methods prioritize chunk 2 for the faster cash because trunk 2 has a higher score than chunk 1。

 This reduces the number of cash means from 20 to 15。

Our experiments were conducted on the server equipped with an a 100 GPU with 80 GB memory。

128 Gb CPUU memory and a 2 T B SSD We tested for publicly available data sets with prefix size ranging from 55 G B to 65 g B。

 We compared in with four systems recomp， which does not use prefix K caching As like。

 which performs aynchronized K loading without schedule information to fit a more general scenario and the other two systems which add H2 O on top of as like and use L R U or L for cache management。

To prevent runtime auto memory， we set the cache space to 10 G B of GPU HBM and 32 G B of CPUU derived。

 By default， each chunk contains keys or values of safety4 tokens。

Since our first technique uses an approximation method to identify important Kvs。

 we conducted accuracy tests， the results show that I achieves comparable accuracy to H2 O and with an average accuracy job of less than 0。

2% compared to re。😊，We also tested the TDF results in press outperform the alternatives with a。1。

2 times to 2。8 times improvement over state of the art solutions。

 This is mainly due to the reduction in I O time， as shown in the bottom left figure。

 The bottom right figure illustrates the changes in T TF T after enabling each technique。

 it shows that each technique further reduce TD f T。Additionally。

 we tested impress on different chunk sizes， data set scales and the popular Lama models results indicate that in consistently outperforms state of the R system under various conditions For more experimental results。

 Please refer to our paper。To summarize， we identify that IO becomes a bottletanneck when loading shared prefix keyvs from SSD for LM inference。

 our key idea is to load only important Kvs during the previous stage。 However。

 identifying important Kvs introduce IO overheads and existing storage and caching systems are suboptimal to address this in employees3 techniques。

 similarly guided important token identification。 Kv reordering and score based cache management Exp results show that I achieves the same level of inference accuracy while outperform the alternatives。

Thank you for your attention。 I'd be happy to take any questions and comments。



![](img/6df43157f62355e5897ea743ece4884d_4.png)

![](img/6df43157f62355e5897ea743ece4884d_5.png)