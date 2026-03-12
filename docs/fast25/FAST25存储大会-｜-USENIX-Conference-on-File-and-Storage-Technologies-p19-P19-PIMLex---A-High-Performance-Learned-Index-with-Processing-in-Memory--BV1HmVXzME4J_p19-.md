# FAST25存储大会-｜-USENIX-Conference-on-File-and-Storage-Technologies-p19-P19-PIMLex---A-High-Performance-Learned-Index-with-Processing-in-Memory--BV1HmVXzME4J_p19-

。

![](img/433817884b5550a665f8b2e6bcaa7994_1.png)

Hello， Ver， I'm Li Xiao from Nka University。 Today， I will present on paper。

 P like Hy performance learning index with a processing memory。😊。

So the index structure is an important component in storage system。 The classical indexes。

 such as B plus3 is proposed decades ago。 and the B plus tree looks up key level by level and the time complexity is O log。

 the recent studies on learning indexes， use the machine learning models to adapt the distribution of data and showing it shows the advantages over the traditional indexes。

 So if the model is prices enough， we can find the data directly。 So therefore。

 the learnex is much faster than the traditional B plus3。So to perform a data lookup。

 a learn index predicts the and search step by step in the model level。

 once it predicts where the data might be， it does the last mail search in the data level。

 So both model search and the last mail search require a lot of memory assesses。

 but in the traditional computer architecture， we face the big problem。 what we call the memory wall。

 the memory wall， the reason the reason behind the memory wall is simple。 The CPU is fast。

 but the memory just cannot keep up with with the CPU。

 So this gap leads to the costly memory assesses and which end up introducing a lot of overhead for learn。

 So from our test， we find that most of the execution time in learnex is dominated by memory bond。

The processing memory of p offers a promising solution to the memory problem。

 So by integrating the processing capability directly into the memory devices。

 P can reduce the need to move data between memory and CPU and this motivate us to use the powerful p to overcome the memory bond of learns。

😊，However， when we try to apply learn death to P， we encounter some challenges。

 So the first challenge is the mismatch between the large space required by learnds and the limited capacity of p。

 The learn death needs a lot of space to handle massive amount of data。

 but the capacity of P devices is small， for example。

 commercial p div up man only offer 8 gig per in。The second challenge is the mismatch between the model structure of learn desks and the features of P。

 The model prediction of learn decks require multiple floating point operations。

 but P div struggle with the floating point calculation。 For example。

 the up man p only the it only support native integer operation due to the hardware limitations。

 The floating point operation have to rely rely on the software emulation， which is much slow。

 When we test a simple learn decks in on P， we find that about 18% of time is spent on the model prediction。

So finally， there is the challenge of a load imbalance caused by skilled workloads。

 The pin based index usually divide the data into partitions and distribute them across multiple pin modules。

 However， in the real world environment， the skilled workloads are very common。

 Some how data get access much more frequently than others。

 So this lead to some pin module being overloaded while others remain idle。 So in our test。

 we find that the performance of learn and skilled workload is only about 010% of what it chips and the uniform workload。

So to address the three challenges， we propose the high performance P based learn indexs。

 the pin index。 then we will introduce the design details。So in general。

 P employs a decoup structure， it contains a search layer on pimp side and data layer on D side。

 The search layer is built using anchor case， anchor case is by samplingling the data layer through the range partitioning the search layer is divided into some small partitions and distributed across multiple p modules。

Within each partition， we create some machine learning models to improve the search efficiency。

 and we， we also maintain a partition table that recalls where the partition of。

 of the search layer are located in on the data layer。

 a primary data raised or key value pairs in order。

 and and it will handle the read and value updates。

 we and we use the buffer pages in the data layer to handle the insertion of new data。😊。

So pininglet follows three step execution procedure to handle read and write。 So First。

 the pinlet checks the position table to identify where the pin module to which the request key belongs。

Then Team performed lookups on the search layer to obtain the approximate position of the request key。

Finally， P locate the actual position of the request key in the data layer， and it it。

 it will performs reading and writing on the primary data and buffer pages。

The two layer deco structure can minimize the p p space usage。

 Pimp likes select the anchor case at the interior of datata from the primary。

 and it ensured the the search layer the size of search layer remains small。Meanwhile。

 P handles a lot of memory accesses on P for example。

 to look up K 6 we first searched the search layer to find the largest anchor case smaller than K6 that say that is K 5。

 This step is based on the model prediction with a fixed error bound Epsilon and the search search range is two epsilon。

 After that， P like check the data layer searching for keys within the anchor interval datata。

So this deco structure can address the first challenge。

Then we introduce the a ping friendly model structure。

 The Ping features a limited computing capability， but powerful memory capability。

 which is unfriendly for the original multilevel model structure。

 So we propose a ping friendly model structure from P less。

 The key ideas is to trade more memory access for less computation。

 And this can address the second challenge。😊，So the learn usually apply multilevel model structure。

 and it use a model based search approach。 search operation at each model level is based on the prediction from the upper level。

 then the learn less performs the binary search within the error bond range around the prediction position。

 So the total cost of the model based search is the sum of the prediction cost and the search code。

This method bring some sorry。so。😊，This， this method brings some computational overhead。诶。Sory。😔，Okay。

 we， we can all also perform another search method， the globe binary search。

 So the globe binary search will perform a binary search within， within the within the。

 the all models within a level。 and it treat more memory access for reduced competition overhead。😊。

So based on the above cost analysis above the two model search methods。

 P likes use the bottom up push to select the search method with the lower cost for each model level。

 So this will transfer the original multi level model structure into a pre friendly one。

 So in this example， the bottom level use the model based search will the level above it use the global binary search。

We also propose the lookup table based model for the floating point based model。

 each prediction needs the multiplication of the search keys with the slope of the linear regression model。

 So the lookup table based model reduce the floating floating point operations it will precalculate and store the results into an lookup table。

 for example， for the search key F 1，1 is correspond are F10 and F 20。

 and their calculation result are P1 and P2。 and we we can store the P1 and P2 into lookup table and and use the P1 P2 to represent the actually calculation result。

😊，So when using with using a lookup table based model。

 we can find the request key with with the search range between P1 minus epsilon and P2 plus epsilon so and for the floating point based model。

 the prediction result is more accurate。 So the search range is two epsilon based on the look lookup code and the prediction code of the two model types。

 we can select the model type with the lower cost for P。

So then we introduce the harmless severe replication mechanism。

 which so when using the same number of pin modules to handle the different search layer partitions。

 the skilled workload can cause some partition to become hotpots。

 So this cause some pin module to get overload it while others remain idle。

So since the uneven distribution of the workload decrease the overall performance。

 we we need to keep the load balance for the different pin module。

 So our key idea is to create additional replicas on more pin modules for hot partitions。

 So this can address the this the challenge3。Our replication mechanism need to determine the number of replicas for each partition。

 So the total number of replicas across all parts should match the total number of P modules。

 And we use a T I to represent the number of queries handled by partition I。

To based on the number of replicas R I and the number of queries T I。

 we can define a load factor for each partition， which represents the how basic that partition is。

 And the global load factor is the business degree of the biggest partition among all partitions。

 So our goal is to configure the R I to minimize the global load fact。So to achieve this。

 our load load balancing algorithm will calculate the number of queries processed by different parts。

 And by compare the average number of queries H P module should handle with T I。

 we can determine the number of reps。 and you can read more details in about this in our paper。

So when household distribution changes， P still need to maintain the load balance。

 So to achieve this， we use a rep replication adjustment method。

 It will relocate replicas for all partition， but it slow。

 So we also propose the fast repa adjustment method。

 It only relocate pin module from some idle partition to the belly one。

 So this method in enable quick adjustment， but the load balance is less effective。😊。

So now we will present the evaluation results。We implement a p based learn less baseline basic basic like directlys learn based learn as PGM index to P8 it don't don't have any automation like the model structure or load balancing。

 So we also compare p legs with other D based learn such as I like leap fan deck and study。

 So the evaluation use five river data sites and skilled workload。

We evaluate p based indexes with four D beams and four p dims but for the D based index to ensure a fair comparison。

 the platform is equipped with 8 D dims。So compared with the p the basic legs。

 P legs show a performance advantage。 So this improvement is due to the p friendly model structure and the load balancing method of pin legs。

Comped with the D based learn desk， Pimp like still outperforms others for both get only workload and the mixed workload。

 This is because Pmle leverages the powerful memory capability of p。

 and it can reduce the overhead of memory access。😊。

AndFor the insert only workload Ple auto performs likes and leap Fex。

 but it perform worse than S on some data size。 So this is because for Pax。

 the data rights in in the data layer are still processed on the D side。

 So this will bring some overhead and it can't beat the S in some data size。

So we also evaluate P with with the data size contain 800 million key value key values。

 the large data site。 the two layer deco structure of pin can reduce the space usage on P。

 making the better at handling large data side。 So we find that P out perform other indexes on in both get and insert performance。

 So， but here we exclude s and lip because there their index size exceed the total memory capacity。😊。

So in summary， we this paper introduce the ple， which takes the first step in exploring how P can address the memory bond issues in learn death。

 So our evaluation show that p like outperforms both p based baseline。

 the D based learn death with real world p hardware。😊，Currently。

 there are still some performance limitations of p hardware。

 and we look up to the future development of the p architecture。

 and we believe it will further improve the performance of Pilas。

So you can read more details about P in our paper。So that's all， thank you。



![](img/433817884b5550a665f8b2e6bcaa7994_3.png)

![](img/433817884b5550a665f8b2e6bcaa7994_4.png)