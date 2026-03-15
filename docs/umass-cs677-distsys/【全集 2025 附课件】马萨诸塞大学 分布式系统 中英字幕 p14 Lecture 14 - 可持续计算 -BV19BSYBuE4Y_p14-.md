# 【全集 2025 附课件】马萨诸塞大学 分布式系统 中英字幕 p14 Lecture 14 - 可持续计算 -BV19BSYBuE4Y_p14-

![](img/53dc0230acfc0cff5e67c278254ee993_0.png)

Hi， my name is Walid， I am a PhD student in UMass， I'm working with Prussant。

 I'm a final year PhD student。And I'm going to talk to you today about。sustainableustain computing。

So I will give you an overview of what is meant by sustainable computing and some of the work that we and other groups have been doing in this domain。

So before I start my lecture， I would like to give you a quick brief about myself。

So I've been here almost five years， I've been working on machine learning systems。

 they've been working on sustainableic systems as well。😊。

And then that I've been working on machine learning for sustainable systems and sustainable machine learning systems。

 so anything that contains machine learning and sustainability， I kind of like it。😊。

So I've been lucky to work here in UMass， I've been published。😊，Many papers across many conferences。

And I want to ask a question before I start the lecture， what is sustainable system？

So when people mention sustainable systems， there is many。

 many aspects that you should be considering， you should be considering the supply chain that you have to get the products that you are using。

😊，How you are what is the energy efficiency of the products that you are currently using？

And what is the source of energy that are you are currently using。

 so are you using brown energy or are you using green energy？

And how you are disposing the the products are using。 This not only applies to computers。

 This applies to。The grid， how to how is the grid， how the data how the power generators are built。😊。

What is the。And how is the end of life of these generators？Buildings。

 what is the products that you are getting in your buildings in terms of appliances。

 what is the energy efficiency of these appliance that you are using in your home。

 what is the energy sources that you are using in your home。And this also applies to transport。

So if I have an EV。Yes， people say that an EV is better even based on the efficiency argument that the energy efficiencies from electric vehicles are better than the energy efficiency of regular vehicles。

 but still I want to make sure that my EV is being charged on clean energy or at least decrease the decrease amount of brown energy that I'm used throughout my EV。

 and of course this applies to compute。😊，So thinking about compute。

 how do I build the hardwares that I'm going to use。

 what is the energy efficiencies of the hardwares that I am using。

 what is the sources of energies that I am going to use。

 and how I dispose and recycle the electronic waste。😊，Today I will mostly focus on compute。

 but many of the things that I will talk about today applies to many， many other domains。

So when I'm considering carbon emissions of a service and specifically computing。

 I'm considering the extraction of the material， I'm considering the designs， the manufacturing。

 the transport and the usage of these devices。😊，So in computing usually people refer to the entire from the extraction till the end of life except for usage as embodied emissions。

 and they consider the usage emissions as operational emissions。😊，ok。

And when we discuss data centers。😊，We should understand that computing demand is growing。

 So there is computing now is everywhere。 So we have been using computing。

In all domains that you can think of， you have been using domains and social media。

 we have been using domains in chemistry， everything now is about computing AI of course key attribute is one key type of computing。

😊，嗯。As an industry， we should understand what is the carbon emissions of computing and our industry in general。

 So IC T is responsible for 1。5 to 4% of the global emissions。

 This is higher than the aviation industry。Aaviation industries that have no electrification。

 we are all with the all the electrifications and all the optimizations we have did。

 we are now more than the aviation industry。😊，And there is estimation that we will reach 6 to 14% of the global emissions by 2040。

😊，And data centers is a huge part of these emissions。

 so there is different estimates and it changes per country。

 so data centers estimates say that it's from 20% to 40% of the global emissions goes to data centers。

😊，And AI is not doing us any help。So AI is increasing the demands for data centers and for computers increasing。

 So a recent analysis states that。😊，The increase in AI have increased the data center power by 160% compared to analysis that was in 2020。

 so three years apart the reality and the estimates are differed by 160%。😊，So， this is huge。So again。

 carbon emissions of computing are classified into embodied emissions and operational emissions。

 if we look at a specific device like a TU。😊，We will find that most of its emissions are operational emissions。

 so in this case what we need to optimize is its operational emissions。

 we need to run it is in more green energy sources as much as possible。

And this also applies to data centers， so data centers are not only GPUs and GPUs。

 they have other things， but in general people say that 80% of the emissions of data centers are operational and 20% are embodied。

😊，If you consider it something like a phone， this is based on the LCCA analysis that Apple have produced。

😡，80% of the emissions from an iPhone is embodied emissions because it has very complex hardware。😊。

That consumes a lot of energy to produce and only 20% as operational because and this happens for two reasons first the lifetime of a phone is very little。

😊，Compared to a data center and servers， so servers usually have a three to five years cycle。

And however， a phone is typically much shorter and a phone usually consumes much。

 much less energy than a data center， so the embodied emissions is considered a major part。😊。

So to optimize carbon emissions in general， I should be able to think of how do I optimize the operational emissions and how do I optimize the operational emissions？

So I embodied and optimize operations。To optimize the。

emmbodied emissions I should be able to understand the relation between the designs that I'm using and the embodied emissions。

 usually more complex designs means more higher embodied emission because it's more complex to manufacture。

😊，So there is papers that have been analyzing the。😊，The embodied emissions。

 how does different design decisions。😊，Effect the overall embodied emissions of a hardware there is papers that appears usually this work is done by hardware architects where they analyze the different decisions and there is also worked by。

😡，Different groups that another way to optimize the embodied emission is to extend its lifetime。

So researchers have analyzed that the ewate from phones particulars is very high。

 people keep the phone for one or two years and then through so researchers have proposed ways to extend the lifetime by building clusters out of phones show and showed that in many cases they achieve very very high and good performance comparable to a server。

😊，And there are other ways to extend the lifetime of hardware so is this paper from Microsoft research have shown that by extending the lifetime of specific components you can basically reduce the embodied emissions highly and in particular he shows that memory SSDs and brandss have very high embodied emissions and by extending its lifetime you amortize these embodied emission over longer periods hence using less new hardware and still achieving good performance so in this again people care about performance people care about the cost of but also people should care about the embodied emissions and the cost of hardwares that they have。

😊，So to optimize operational emissions it's a little bit of a different story。

 so I need to optimize so the carbon footprint of a server is based on two components。

 I need to understand the amount of energies that I'm using and the source of energy and by multiplying the energies that I'm using times the carbon intensity I get what's called carbon footprint。

😊，So if I want to optimize the energy or decrease the amount of energy that I'm using。

 I have to always， I can use better algorithms， I can develop better algorithm。

 better ways optimize my code。So basically using less cycle to do the same task and they can also enhance my power efficiency。

 I need to be able to do more with less power。😊，The second approach is to optimize the carbon intensity。

 I need to be able to integrate more and more clean energy into my system and into my grid and also implement carbon over scheduling so basically following where carbon where clean energy is and try to use more of。

😊，So in the rest of the talk， I will focus more on operational emissions and I will show you a couple of research that we have did to optimize the carbon efficiency of compute。

😊，So if you consider energy efficiency in general， there is data center usual host hundreds and thousands of CPUs and GPUs。

So researchers have analyzed or basically there is a law called Kummi law diameter to Moore's law。

 that this law basically says the energy efficiency of hardware doubles every 18 month。So。

 basically if。I'm a data center and I need to optimize my energy efficiency。

 I basically should upgrade my hardware whenever a new hardware or whenever a new or a more energy efficient hardware is there so that I can benefit from these efficiencies that comes by the newer hardware that is appearing so this is what basically data centers have been doing they usually have an upgrade cycle every three to five years and change the hardware that using。

😊，So that it can be as more energy efficient as possible。

Energy efficiency in this case is is tied directly with cost efficiency because if you are using less power。

 you are basically paying less to use power and then you can have more。😊。

You can have more profit from the hardware that you currently own。

There is also 20 plus years of research on optimizing energy efficiency and designing resource management techniques。

 but I would not go through it。However， I want to highlight something that this approach was very successful。

😊，So compared to in this analysis， they show that between 2010 and 2018。😊。

The total energy demand have only increased by 5% this is the global energy demand of this is the US energy demand of data center or the global I。

 its either the US or the global， but it only increased by 5% however the compute demand measured in millions of compute instances increased by six times or 6。

4 times to be exact This shows that great improvement of the energy efficiency being I'm able to do much。

 much more for much， much less amount of energy。😊，And the estimate was that this is a trend that is going to stay for long。

 so this paper was published in late 2020 and they say that in 2023 well have just more 3% more energy and we will be able to get 14。

1 x more compute。😊，However， this does not include what happens with AI AI to flip everything around。

AI came with very high demand for energy。And it came ink very high demand and with very high energy。

 actually the estimates say that the amount of energy is now based on what I saw it's 160% more than what was predicted at this time。

😊，So which is huge， so the data centers between in the last five years almost doubled。

Which is huge and all the recent studies mentioned that it will actually increase more。😊。

Another aspect of the energy efficiency of data centers is which is called POEs。

 the power usage efficiency， which is basically the total amount of energy that a data center use。😊。

Over the compute energy where an optimal P where all your energy goes towards compute is one。

So usually data centers so if I am saying that the P of these data center is 1。2。

 this means that it has a 20% overhead and and this overhead basically comes from the cooling overhead and the power efficiency overhead from the grid and transformant and losses in power efficiency this usually contributes almost 10% based on Google's data center。

😊，And again， for many reasons， including aco one。😊。

Data centers are able to optimize carbon their POE over the last almost 15 years。

 so at 2018 Google had a POE of 1。2 now they have a PE of 1。

8 which changes across season because of different cooling techniques that depends on MBA temperatures that changes across season。

So the other way to optimize the carbon efficiency or minimize the carbon footprint of computing is to add renewable。

So basically the idea is very simple， let's replace the fossil fuels that we are using with more green energy sources。

😊，So in the recent years， carbon intensity have been increasing because many people have been trying to adopt or many countries have been trying to adopt this strategy。

 so all the countries are decreasing their carbon their carbon intensity， so for instance。

 China is going from almost 800 to less than 600 grams for each kilowatt of our produce in energy and China is one of the most the countries that have highest ratio of increase in solar energy。

Other countries。I also had been investing in this United States sorry United Kingdom shows a huge decrease so it goes from 500 grams in 2000 to almost half of it in 2023 and almost all countries have been trying to optimize their carbon intensity There are some countries that are outliers。

 for instance， Sweden highly depends on hydroelectricity。😊。

With some nuclear as well so that they have very low carbon intensity profiles。

So adding renewables was good for the environment but it was mostly but it's now also a cost efficient approach。

 so according the localized cost of energy， which is a measure that okay how much I pay for each kilowatt oromegatt of energy that I'm producing solar is actually right now the most cost efficient and of course it's very highly carbon efficient source of energy。

😊，However。I think more renewables do not solve a problem because renewables are intermittent。😡。

So renewables are， for instance， like a solar is only available during the day。😊。

Solar is highly affected by weather， so if there is a cloud if it became a little bit hot。

 the amount of solar produced is much less。😊，So the solution that companies and researchers have realized is that。

 okay， I need to add renewables， but I need to bind or I need to augment the renewables that I'm adding with load shifting。

So based on this article from 2020 by Google， they say that our data center now work harder when the sun shines and the wind glows。

😊，In translation， this means that where there is more renewable energy， we should be doing compute。

And when and where to be exact。So I didn't say this before， but what is carbon intensity。

 I keep saying carbon intensity carbon intensity， so carbon intensity is basically a measure of how clean the energy is。

😊，So because carbon because the grid depends on many sources of energy。

 usually is a carbon intensity as a signal that represents a weighted average the carbon of the energy sources that I have right now。

😊，So if I am considering these three sources， if I am considering like coal that have 760 gram emitted of CO2 equivalent per each kilowatt hour of energy produced。

 if I am considering something like solar or wind that basically more or less have zero grams emitted per each kilowatt of hour produced。

😊，I can compute what is called the carbon intensity signal。

 so the carbon intensity signal in this way if I have 50% of my energy comes from brown sources and 50% comes from green sources。

 I will have the weighted average which is 300 gram per CO2 per kilowatt out。😊。

So because the energy demand changes across time， so as the carbon intensity so the supply changes across time the demand changes across time so as the carbon intensity changes。

 so if you consider a grid like the California grid or they have a lot of solar energy，😊。

The carbon intensity becomes lower during the day because there is more solar energy and higher during theai。

So the change can be up to2 x difference between the low carbon intensity and the high carbon intensity period。

And also the grid and different states have different grids。😊，So each state has its local grid。

 actually， each state has many local energy sources。 So for instance， there is a。😊，In Florida。

 I think they have eight or nine different utility companies。

 each of their own energy mixture so that they have different carbon intensities。😊，So the again。

 the energy demand supply change across state across space。 So that's the carbon intensity。

 So if you think about it， I should be able to use the spatial and I should be able to。

So that temporal and spatial variability underscores the need for carbon a resource management。

 so I should be able to put my compute where the energy and where the energy is more green。😊。

So luckily enough。😊，Computing is equipped with many flexibility mechanisms。

So I can run in my workload using a supend and resume manner， I can run my workload or my batch job。

 for example， a machine learning training job during during the day and stop it during the night。😊。

I can also do resource scaling， I can use more resources when carbon intensity is low and slow that and do not use any resources when carbon intensity is high。

I can do some sort of approaches that allow me to change the rate of computing。

 so I would not feed the same amount of data， or I can use something like DVFS that allows me to change the speed of my computations。

And they can definitely do patient shift。😊，So because computing is well equipped with resources。

Unlike other domains， so for instance， I cannot do spatial shifting with home loads because I cannot basically shift my house。

 but I can do some sort of temporal shifting for EV charging I I should not be charging at this time。

 but I can charge at another time。😊，So a recent domain have appeared which is called carbonbon A resource management。

 and the key idea of this domain is that we should use carbon intensity variation and computation flexibility to optimize the carbon efficiency。

😊，And this domain and I will continue the rest of this lecture on this domain。そう。

If I want to implement carbon aware resource management， I need three things。

 the first one is I need visibility。I need to understand what is the current energy sources that is powering my computation right now。

 I need to understand how the carbon intensity， for example。

 changes across time or the across locations， usually the。

The grids provide a very high reliability abstraction where when you plug your computer to the socket。

 you don't know which which source of energy is feeding your computing and it's physically impossible。

😊，But by understanding the different energy sources that is currently powers the entire grid right now。

 you can compute something like a carbon intensity signal that you can use to and make decisions about。

😊，And second I need policies， I need algorithms and I need techniques that allows me to leverage the computing flexibility with visibilityiities I get from the grid and understanding how does this affect。

😊，The workloads that I'm currently running， if there is any other constraints I should be considering and they should be able to provide algorithms that allows me to do this job。

And third， I need incentives。Because I need to understand the trade offs that I when I do carbon a resource management。

 there is many， many trade offs， so I need to understand that trade offs I need to understand and I need to incentivise people。

To use it。In this lecture， I will talk about the trade offs， but I will not talk about incentives。

So one of the fundamental techniques in so before I go to the techniques。😊。

So anyone has any questions？Okay。So one of the fundamental techniques of carbon A resource management is called importmed shifting。

And the key idea of temporal chiping is to match the availability of flow carbon energy with a computing demand to basically run where is when the carbon intensity is low。

 so if I consider a job that instead of running it in a carbon agnostic manner。

 I can defer its execution to another period of time where carbon intensity is lower。😊。

And if the job is very long and defing it might not give me lots of benefits。

 I can do it in a suspendedspend and resume manner so basically I will start my job and when carbon intensity gets high over a threshold for instance。

 I can stop my job and continue it later。😊，So I will give you an example of a recent work that uses carbon a and portalal shifting。

 so the policy is called let's wait a while so this paper appeared in a couple of years back。

So here I will show you four different workloads and I assume the power concern so this was profiled based on a machine learning training job that uses 0。

2 kilowatt hours of energy each hours as it runs and I'm using here the carbon intensive from California between 2020 and 2022 to demonstrate the benefits temporal shift。

So here I'm going， the x axis shows the waiting time。

So here I have four jobs the X axis shows the waiting time whereas the waiting time changes from0 to 60 so the waiting time or the slack is the amount of flexibility that I can delay the job for So for instance。

 if I have a one hour job and I have a 60 hour slack this means that I need to pick one hour out of。

61 hours to run my job， so pick the best hours that you can run and just run your job during this hour。

Of course， this assumes that I can predict a future carbon intensity。

 but there is many approaches that allow you to do so in very high accuracy。😊。

So here I'm considering four jobs， I am considering a job that would run for one hour and I am considering a job that runs for six hours。

 12 hours and 24 hours。😊，The first thing is that you would realize that was extending the waiting time。

😊，I get more carbon savings because you have better options to choose from so instead of having one option that you need to run the job right now。

 you have 61 option 61 different options if you have a one hour job。

Another important thing is that there is a diminishing Richard so usually and you will see and that I will mention this word diminishing Richard multiple times throughout the lecture。

😊，There is a point where extending the deadline do not add much benefit so for instance。

 if you're considering a one hour job usually you are either in the lowest carbon intensity period and defring it do not make a difference or you just missed it and you need almost 18 hours to be again in the same good period。

😊，So at 18 hours they chose that okay if I have a one hour job extending it beyond 18 hours usual do not give me much benefits。

 and this applies to almost all of them， however there is the way that the knee of the curve is different per the job blend。

😊，There is a trick in this graph。😊，So this graph shows you that short the jobs can save more carbon。

😊，If I'm computing carbon savings and percentages， this is true because if I have a one hour job。

 I can move it anywhere and they can get huge amount of benefits。

However if I'm considering the actual saved carbon， it's a totally different story。

 it actually a complete opposite。😊，Because a longer job means a more compute time。

And any amount of saving can actually save much， much more carbon。So in this case。

 by extending the waiting time， the 24 hour gets huge benefit and again。

 this is where the knee of the curve is actually apparent for the 24 hour jobs。😊。

So temporal shifting， in summary， temporal shifting depends on the flexibility。😊，And completion time。

AndBut extending the completion time or extending the slackla comes with diminishing returns。

Where longer jobs have lower relative。Savings， but higher absolute savings。

Any question regarding to portal shifting？So temporalal shifting is nice。

 but there is a fundamental issue with temporal shifting。😊，So if I want to run temporal shifting。

 I basically need to extend my completion time as I was accepting earlier。

 so instead of finishing my job within 24 hours， I needed to finish it。😊，Overall。

48 hours or 72 hours。そ。So extending the completion time is one of the fundamental problems of temporal poor shifting。

😊，Another approach or another issue with temporal shifting is that it fails to exploit the differences in carbon intensity I would run the same rate at this period where carbon intensity is moderate and at the same rate when carbon when carbon intensity is extremely low。

😊，Soと。Avoid these issues。We have proposed the usage of resource scaling。

So instead of running the ro in a suspension resume manner。

 I will basically stack the compute across different times。

 so when carbon intensity is very low I basically not use one server that like I was using in the portal shifting I will basically use three servers。

😊，And this allows me to decrease the completion time。

 and this allows me actually to get more carbon savings because I can run at different ratess based on the variations of carbon intensity。

😊，So to do so， we propose an algorithm called carbon Scalar。

 which leverages the variability and of carbon intensity as well as the elasticity of foreclos。😊。

So to do this approach so in this approach we have shown that if I have throughput。

 so if I am considering that when I scale a job I should usually understand what is the benefits that I'm getting from using more resources so usually people try to represent this in terms of the relation between resources and throughput so more resources means more throughput。

However， a key insight that we have。😊，When we try to solve this problem is that we will not use the throughput as a measurement tunic。

 well use what we call a marginal capacity。😊，So marginal capacity is the extra throughput that I will get for every added resources。

😊，And the benefit of using this will will come later in improving the optimality of the algorithm but。

😊，But I will explain this as I go。So here， the relation between resources and the marginal capacity。

Tells me is what is the benefits I'm getting for every resource I am adding。

So I was able to use this marginal capacity with carbon intensity to compute what is what we have been calling the marginal capacity with pre unitit carbon。

So this allows me to understand what is the benefit I can get by running at each scale across times。

😊，Using this idea of marginal capacity and normalizing by unit carbon allows me。😊，5。

Compare decisions across scale and time at the same time。

So by being able to compare scale and time at the same by using one unit， I'm able to compare， okay。

 should I use one resource at this time slot should I add another resource at this time slot or should I use the first resource at this time slot？

So by building this on this idea we have proposed an algorithm and on a side note by using the marginal capacity we were able to map this problem towards other sets of problems called marginal resource allocation where optimal greedy algorithms exist so if you took something like 611 you know that in some cases greedy algorithm can be optimal。

😊，And this is one of these instances。 So we showed that this algorithm is optimal， and we have。And。

Which allows to optimize the carbon efficiency as possible as it can be done。

So this is one experiment that I want to share with you about the benefits of using carbon scalar or using scaling in general。

 so here this graph shows me the carbon emissions。😊，And gram of CO2 equivalent where lower is better。

So here it shows that our approach compares to a carbon agnostic we are generally able to save between 51 and 55% without extending the deadline。

 so if I have a 24 hour job in this case I have a 24 hour jobs and I need to finish the job within 24 hours so this will not increase the completion time as per temporal shifting for instance。

One thing also we note is that usually in this case。The GPUs that we are using consume much。

 much more power so that it has much more carbon and again this is related to the increase。

 the huge increase in global energy consumption by using more and more GPUs for AI because GPUs generally have much more energy consumption。

😊，So the carbon scar， so using this approach scaling or carbon scar in specific can reduce the carbon emissions without increasing the completion time。

So another approach that people usually try to optimize carbon efficiency with is to use space shift。

So I showed you this map earlier where different states have different carbon intensities and this also applies to a great extent。

😊，To every place in the world。That in Europe， there is different carbon intensity across different neighboring countries。

 even in more differences than here in the US because at the end of the day。

 they are different countries with totally different grid systems。😊。

But here there is many grids that shares great components of their grids。

So if I'm considering spatial shifting， I need to consider。😊，One key aspect。

 so into important shifting earlier， I can delay the job because I am considering a bad job。😊。

Over here in spatial shifting people usually consider this with interactive workloads。

 so I need to consider the latency limits that I have so for instance if I have a latency limits of 10 milliseconds then this is where I should be searching。

😊，So this is the options that I have， I have one， two， three or maybe six options to choose from。

If I have more relatancy budget or I can extend my response time by a greater amount。

 I can have better options and these go on until I get like to the extent of reaching or running my workload anywhere on not。

😊，Of course there are other constraints and latency， for instance。

 there are lawss that do not permit people to put like GDPR in Europe。

 I cannot host my things in the US and in the US I cannot hold things outside。

 but this is a general idea。So， one key。A componentonent of the internet in general is called CDNs。

 so you will have towards the end of the class a lecture about CNs。

 but CDNs are our content delivery networks are basically services that allows you to host media closest to the user in a way that it will and will have performance because you will host the media that you are watching。

A YouTube video or whatever closer to the user， it has cost and energy benefits because I'm moving the data for shorter distances。

So the idea that we were trying to achieve here is that we need to redistribute CDN workload in a carbonware manner。

So I need to move and this paper was published in SoC 2024， so where we use CDN traces from AkaMmai。

 we use different traces to build an extensive analysis of what is the possible。

Caribbon savings that TDNs can implement。So the results shows that by extending the latency limits for a service like CDNs。

 I can have higher carbon savings and again there is a diminishing return。😊。

So by extending the latency beyond 60 milliseconds。I should be able to。I should be able to。

Like extending that latency limit beyond 60 minutes， second usually do not bring me much benefits。

And here， the graph shows that。By extending the deadline on average the latency is not increased by the same rate。

 so usually by increasing the latency by 30 milliseconds。

 I can achieve very high carbon saving so almost 40% reduce carbon efficiency of a CDN because CDNs consume a lot of energy because they are global services by by 40%。

😊，And I again， I can do the same in Europe， so we showed that because usually Cdns are not that global。

 they are global， but they are usually。😊，There is no much benefit of moving things across US and Europe。

 so in Europe we have did the same analysis and shows that TdNs can reduce their carbon efficiency by 80%。

😊，Considering the same like 70 or 60 milliseconds latency watch。And， lastly。

I would like to highlight that the savings in Europe is higher because the differences between countries is much higher。

So in average。So in Europe there is many countries like Poland have very brown grid。

 but there is also many grounds like Norway， Sweden have very low carbon have very green grids because it rely lot on nuclear energy and renewable Europe and the hydroelectricity。

😊，So again， higher latency lead to higher saving， but again with diminishing greater earnings。ok，我。嗯。

呃。Like C end is that like。Yes我。So CDN deliver streaming videos， they deliver all kinds of content。

 they deliver websites， they deliver， CDN deliver everything。Thats more。啊。Yes。

 compared to ML training， yes it's much less。But at the scale of CDNs whereas the scale。

 cdNs are very high scale services and they consume a lot of energy。

So basically most of the content that is delivered over Btuub or Facebook or any social media are mostly delivered by see theNs runs by this company。

There is other companies like Akamise that has provide CD and content delivery services and this when we use their data and it's it's。

And it's a well known fact that it consume because it's a global service and helps a lot of customers。

😊，So that they have high energy footprint and of course， high carbon footprint。Okay。

 Nick more questions。I expected more questions。😊，But we're going to have questions at the end if I finish early。

😊，So one big thing that we have been writing more and more in our recent papers。

That in carbon hour scheduling， there is no free lunch， only trade offs。

So we have discussed or you may be guessing one of the tradeoffs that we have been seeing is a carbon performance trade off。

But there is also carbon cost trade offs and there is carbon energy trade offs。So again。

 carbon a resource management brings many trade offs and it's obvious by now that there is a performance trade off。

😊，So should I run my workload now or run it later， so increase my my delay So usually for math metrics like like response time it can be in millisecond。

 but there is also。😊，In batch workloads， there are performance metrics like waiting time that can go for hours。

So by deciding whether you run your workload close versus running it far。

 running it now or running it later， this brings a carbon and performance tradeoff。

There is also an energy tradeoff， which was not really obvious to us or any people who are started working on these domain。

So if I want to optimize the carbon efficiency， I basically need to use some sort of a flexibility mechanism。

 flexibility mechanism like supen and resume， flexibility mechanism like using scaling。😊。

Flexibility mechanism likepend suspend and migrate my workloads from one place to the other。😊。

Every flexibility mechanism of this consumes more energy than just running the workload as is。😊。

So if I suspend a workload， if I have a batch job and I suspended it。

What will happen is that I will use more energy because I use energy to store the states that I have。

 I use the energy to get the states from memory to this。And if I'm doing migration。

 I' also have to have overhead from migrating my data from one location to the other。😊。

All of these are overheads and all of these bring a carbon energy trade off。😊。

So I will talk about one trade of maybe if there is another one I might mention if there is enough time。

About scaling。So scalinging is good。So I built my entire ceasesis around scaling。😊。

So but elastic scaling is not free。😊，So if I am running at a higher scale。😊。

It basically becomes less energy efficient because when I'm using more resources。

 I'm getting less out of these resources， I'm being less energy efficient。😊。

So basically resources have or basically jobs have different scaling profile。

 there are jobs that have ideal and linear scaling， usually called embarrassingly parallel jobs。😊。

By running these jobs at any scale， I usually get almost。😊。

DoubSo if I have one resource and I double amount resources， I will have double amount throughput。😊。

However， there is many jobs that do not have this behavior This behavior goes back to MD law if you remember what U law is。

😡，W states something about the issue betweenizable and nonparlyizable portions of your code。😊。

So all workloads when you scale them over multiple sources usually have a communication barrier for instance。

 if you consider a machine learning training。😊，At the end of each iteration or a mini batch。

 usually have a synchronization period where you actually change the weights of your model with others。

😊，This is a communication barrier and you will be using。😊。

And this will decrease the throughput compared to a linear throughput。😊。

So these different scaling profiles is what we have been seeing all along in all our analysis and all the profiles that we have captured。

So if you if you consider here there is this example where we have three workloads we have two machine learning training jobs。

 one is using resnet 18， the other is using a smaller model which is mobileNe V2 and they have an MPI workload that is based on the embody simulation problem so this embody is a。

😊，Is a problem used to analyze moving objects in a space and how the gravitational forces affect each other。

 it usually comes as one of as a type of scientific computing that people use。😊。

So if you consider this job， you have three different scaling profiles， actually。

 we have profile workloads that go across all the scales。

 we have profile workloads that are almost linear and we have profile jobs that do not scale beyond the single node at all。

😊，So by considering these three workloads I am able to understand what is the benefits and what is the limitation of adding more resources so we use here speedup and this is the ratio between number of servers and speedup and of course speedups is normalized to using one resource as you can see there are jobs that scales almost linearly and there are jobs that have very very poor scalability。

😊，So if I'm considering these workloads。Based on the carbon scator approach。We have seen that。

By using different workloads are able to achieve different amounts of carbon savings。So here。

 if you consider these workloads that is very scalable， it can go almost a 50% carbon savings。

 there are some instances。😊，That goes to 50% carbon savings。If you consider the Mo net。

 there is some instance that goes to 50% karaate。If you consider the embody there is the maximum it gets is among 30% what is more important in this graph is that it shows a relation between carbon savings and energy overhead。

😊，So， the more scalable the job is。😊，The more I can get by with the amount of carbon savings that I get。

The energy overhead is included in the carbon saving so it is not a different metric and they have to analyze it but here I'm just analyzing the carbon saving and the energy overhead the same within the same workload so as you see a workload that is very scalable usually gets very high carbon saving with very little overhead。

😊，And if the more the less scalable the job is the overhead increases。

 so if you consider the embody 1 k。😊，I have I was able to get 30% carbon saving。

 I almost get 30% energy overhead。In some cases， energy is not the limiting factor because there is energy curtailment。

 there is solar energy that I may be willing as a user to sacrifice 1 or 2% more energy to save carbon saving by 50%。

 but I don't think anyone will agree that I want to get 30% carbon savings。

 I should be able to get 30% and I will have 30% energy overhead。😊。

So scaling increases carbon efficiency， but it decreases energy efficiency based on our workload elasticity profiles。

😊，嗯。So another work that we did is that we wanted to analyze the performance carbon and energy trade offs。

So， this paper was。the objective of this paper to do DNA placement on heterogeneous aid resources。

Across Europe， so in this graph， I'm showing that so the purpose of this。O。都。

The purpose so we were doing some analysis regarding how to optimize the carbon efficiency of model serving services。

😊，So in this graph here I am showing that we have a problem and the problem in this case we want to do optimize DNA placement across heterogeneous resources that is placed across different cities in Europe。

😊，So we have three policies。😡，We have the carbon A policy that optimizes the carbon footprint of this deployment。

 we have an energy aware policy that tries to optimize the energy that is used by all these resources and we have a latency aware。

😊，So。We are using three metrics to analyze the the the benefits of these three policies。

 The first one is。We want to see how much carbon that this service is using。

Second is that we want to analyze the amount of energy that we are trying to use。And third。

 it's the amount of latencies these services exhibit because again。

 we have multiple services across different edge data centers。😊，So， what is。

Noticeably here is that every policy kind of optimizes objective。

 This is no surprise if I'm a carbon A policy should be able to optimize the carbon other than other policies。

😊，But what is not？But what is interesting here is that。

A carbon an energy aware policy is usually so compared to a carbon energy A policy。

 carbon A policy entthruses 50% carbon savings。😊，However， it has more than 6。

5 more energy compared to the energy aware。😊，So here if I'm considering this energy where it uses 6。

 wt megawatt hour， the carbon aware， yes it has half the amount of carbon， but it has more than 6。

5 more than 6 times the amount of energy。So in this case the tradeoffs are not only fundamental they need different approaches to optimize them to at least be more realistic and the reason for for this differences is basically the hardware it's very highly heterogeneous in our scenarios。

 which is kind of reflects the state of the art right now because most of the hardware in edge environments are very heterogeneous there's many。

 many types of GPUs and people have been analyzing the effect of these different types of GPUs on their total energy energy consumption and also carbon footprint。

So the carbon energy tradeoffs is very， very pronounced in heterogeneous settings。So in summary。

 I want to leave you with three things。One is that carbon footprint of computing is rising。

 this is something that you should now be aware of if you have not been aware of it before。😊。

Second is that if I want to consider the carbon efficiency of a service or computing or computing in particular。

 I should be able to analyze the entire lifecycle emissions so yes usage is very huge for data centers。

 but for other devices that you are using for example your own。

 other things are much more maybe much more important。😊。

And lastly is that there is no free launch in carbon over scheduling， there is always a cost。

And speaking， of course。The the。The movement in the US regarding recycling was also claiming the same things。

😊，30 years ago， there is papers from H reviews that they analyze the benefits of whether companies should should should。

houl adopt more sustainable decisions and their procurement or in their things and to be honest there is many。

 many innovations that will happen to try to seize this trade offs but for now it there and not I don't think it's going away anytime soon。

So thank you if you have any questions。啊明聊天。So I took less than an hour， so you have。不ning minute。

Okays that。Of course。通话的。然后意思。Using what。哦们。So usually so usually at the scale of our data center。😊。

The is so there is many approaches that propose by。Data centers itself， for instance。

 there is a war by Google。That appears like two three years ago or something or maybe a little bit more that shows that okay。

 how do optimize the carbon efficiency by doing low shifting at a scale？

So to do low shifting and scale they use something called a virtual capacity where they can limit a usable amount of resources at different times at different periods of time so for instance。

 if I have 100 servers maybe during noon I can allow the batch workloads or the entire data centers use the 100 data servers over during night because carbon intensity is high I will I I will only limit my capacity to 50% so I'm using 50% of this workloads or two companies use other approaches to augment their carbon intensity to use something like PPpas to use。

😊，Where where you kind of invest in a local energy in a local solar farm， for instance。

 and you can claim the generated green energy as yours so both approaches are kind of used in data centers but in the case of open AI I don't know specifically that they are doing something that will help but。

Many companies are moving now into nuclear energy。Nuclear energy is almost as green as energy can get。

So nuclear energy are stable， you have other types of problems。

 but as far as the output energy that comes out of a nuclear power plant， it's green and it's stable。

 which is something that data centers will definitely love。😊，都会。到时。Yes。多诉你点系。Okay。

 so so data center usually hosts two types of workloads。

 they host interactive workloads where latency is critical。

And the results you are getting is also critical so they would not really touch this。

 but what they do is that they want to shift batch work clothes for instance。

 if they have some sort of a data processing service like like the overnight data processing of YouTube videos。

😊，This can be delayed for a couple of hours and no one will really notice。

Machine learning workload is another type of。 I can I don't need to train it anytime。 I can specific。

 I can be more or less。Selective was with the times that they train job for the job app。

So I think we conclude， thank you。And。

![](img/53dc0230acfc0cff5e67c278254ee993_2.png)