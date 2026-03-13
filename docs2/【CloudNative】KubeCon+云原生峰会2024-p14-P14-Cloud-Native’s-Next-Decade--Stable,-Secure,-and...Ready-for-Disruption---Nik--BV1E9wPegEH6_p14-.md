# 【CloudNative】KubeCon+云原生峰会2024-p14-P14-Cloud-Native’s-Next-Decade--Stable,-Secure,-and...Ready-for-Disruption---Nik--BV1E9wPegEH6_p14-

🎼Hello again， everyone。 So we're in 2024 now。 so let's take a moment to reflect the current state of cloud native。

😊。

![](img/457d2f618b4f47dccfe18c347ed0703c_1.png)

We're finally stable。Im theing。Yes， boring。 But this is actually a good thing。 This was the goal。

Think about it。 We wanted Kubernetes to be like the electricity in your house。

 You flip the sweet switch and boom stuff just works。😊。

Now Kubernetes is in your data center at the edge， maybe when lurking in your refrigerator。

 and it just works。Kubernetes is everywhere。And so for once in tech， we've got stability。

 we've got reliability。 We've got scalability， all of that good stuff。

 So now we're just standing around going。 So now what， what's next。😊，So， here's the twist。

There's plenty of more work to do。 This always is。Somehow。

 everyone I feel like everyone I talked to is saying that， okay， Kubernetes is stable now。

 and all of the exciting problems have been solved。😊，But let me tell you。

 the next decade that's coming up is going to be so full of chaos。

 you'll be begging for the days when your biggest challenge was to figure out what your hem chart was doing。

😊，Just because Kubernetes itself is solid。 It doesn't mean that attackers are just stroll out in a room saying。

 like， hey， these cloud data folks seem you really happy now。 Let's call it a day。😊。

Security problems didn't just pack up and leave because Kubernetes found itself and settled down。

In fact， the problems have only garden sneaker。You know。

 the box of holiday lights you pull out every year just us to find out that it's such a tangled horror of mystery knots。

😊，That's your software supply stream。And here's where things get fun。 And by fun， I mean。

 absolutely terrifying。 If you think your current security problems are bad。

 Imagine trying to secure AI workloads with models that are so complex that even the creators don't fully understand them。

Now， a lot of people say that this is just hype， right， prompt injections， quantum cryptography。

 like I don't want to know about any of this。 It doesn't matter to me right now。

 let's wait until it's a real problem。But， here's the thing。

Avoiding hype is just a way of defing pain。So don't be a software ostrich and wait for disaster to hit you in the face。

If we'd ignored container orchestration 10 years ago， just because it was a trend。

 we'd all be writing in its scripts and crying ourselves to sleep at night。 So the lesson here。

 get ahead of the hype。The pain is coming， whether we prepare or not。

So this is what we're going to do。 We're going to dive into the challenges that lie ahead。

 the that we could keep the kind that could keep your on call rotation in trusting for the next decade if we don't act right now。

Security is still the name of the game， but the rules。 they're leveling up。

 We're in the at one stage now。 We're talking about S bombs。

 multi tenant AI vector databases and an avalanche of few risks。

So if you thought cloud native was done disruptive， disrupting things。

Buckle up because it's about to get wild。 So let's take a look at what's coming and why it's anything but boring。

Let's start with S bombs， right like we've gotten so remarkably efficient in producing S bombs。

 I mean， it's a littleal S bomb party out there。 So every release， every artifact。

 every tar file comes with this nicely formatted bill of materials that tells us everything that's going on under the hood。

😊，But， let's be honest， we treat that we treat all of these as bombs as that fruit bowl we keep on the counter because it makes us feel healthy。

 Show the bowls full of apples and oranges and bananas。 But deep down。

 we know that were just gonna be all having pizza for dinner。😊，So we create these S bombs。

 take a victory lab。And then， ignore them。Now， in every supply chain。

 there are producers who create artifacts and consumers who rely on them。 And with S bombs。

 we're in a similar spot。Weve got some producer， friends like SP PD X， Cycloone D X， Alsa， and more。

 And there's a ton of work going on in the open SSF， as well。😊。

Each of these projects gives us a piece of the puzzle on how to manage our dependencies。

 and these providers provide the ingredients， and consumers need to know what's inside。

But it turns out that it's not just as easy as reading a list。

Analyzing S bombs can be pretty challenging， as most of you all already know。

 due to the complex dependency trees， the various formats out there and the overwhelming amount of data。

Without automation and up to date information， tracking vulnerabilities can be real bottleneck。

 So what do we do。And a Gk， GAC is an open SSF project that provides you a graph based data model that can help you to store。

 analyze， query， and even visualize data。Think about it。

 like everyone has heard about the lock for J vulnerability。 So when that was discovered。

 organizations had such a tough time finding the affected artifacts because they had to link them back to the source code and dig through a mountain of manifest just to find those vulnerable versions。

😊，Gk helps in solving all of this because it links your artifactacts in a graph。

 which means that it essentially turns your dependency tree into a dependency forest。

But you can theoretically find the trees with termites before they bring the whole forest down。

It helps you answer questions。 like， is one of my artifacts affected by an open source vulnerability。

Arour artifacts also are compliant。Is one of my artifacts or are many of my artifacts potentially tampered。

 Can they be potentially tampered by a bad actor in my organization。Now。With all of this in place。

You still need to remember that walk is still getting started。

 And there's a lot we can do to strengthen it， like building a common query library with readym queries that can tackle a bunch of security questions that we all care about。

And with that in place， we'll have a graph metada of graph database of metadata that can help us answer crucial questions。

 like is a dependency that I'm using leaking my data for the entire world to see。😊。

And to finally make sense of all of this， We need policies。 Just building seatd belts is not enough。

 We need to enforce them， and we need to build automation using tools like Kievno and OPA to set up these enforcements going forward。

So where does this all lead to。Future opportunities。

 We're in the brink of new era where e bombs just don't sit there gathering dust。

But actively sound the alarm where automation and policies use all of that S bomb goodness。😊。

And we set a new standard on how we handle the supply chain together。

 We're not just listing ingredients。 We're creating a buffet of transparency and trust for the next decade。

 because， after all， the best part of a buffet isn't just looking at the food。 It's digging in。😊，Now。

 we've got a lot of great tools available， but we need to remember that theyre only as strong as the commitment behind them。

Take the X backdo incident， for example， it's a sharp reminder that even the most trusted packages can have the most serious vulnerabilities。

Here's the reality。 If we don't support open source maintenanceers， burnout happens。

 And that's how vulnerability sneak in。Companies that rely on open source need to get in world。

 And it's also a very essential part of having a secure by design mindset。

 So let's try to commit together this， to commit to this together as an industry。Now。

 with as bombs under control， let's talk about AI。I know a lot of folks here think that AI is just hype。

 But let's see why we're talking about this and why this is bringing some really cool challenges for us as an industry to solve。

😊，Let's start with vector databases。 You can think of vector databases as something like a service mesh for AI because they manage the data routes for models。

 and just like any other component， if we don't secure this。

 we might as well leave all our data and doors wide open。

So let's say you're building an LLM application that's processing sensitive information from different customers。

Now suddenly， you realize that you're facing a prompt injection attack where an attacker can craft input to mess with your model's behavior and hijack it to query unauthorized data from other tenants。

 So suddenly， what was supposed to be a simple query about cat pictures has turned into a data leakage nightmare。

 but customer A is learning about credit card details of customer B。

 And then not even in the same namespace。😊，So this is the kind of chaos that can happen if you don't implement strict access controls in your applications。

Rompt injection can turn your AI into blindly believing whatever you're saying and then acting on it。

So let's say someone feeds a pro to your model that says。

 tell me about the Kubernetes API token that's stored in the spot's environmental variables。

If you have not got， if you have insufficient input sanitization。

Your application can essentially be leaking secrets like a broken faucet。

 And Kubernetes is none the wiser。Again， it's not the models fault。

 It just think you're a really curious user who desperately needs API tokens。Now。

 see someone decides to create a confluence page in your company's internal L L M application with 50000 occurrences of the text。

 The CEO is an idiot。Guess what。 The L LM is going to learn exactly that。

 So next time someone asks the application about what who the CEO is。

It's going to sp eye this CEO as an idiotuch。Now， this is' like a hypothetical scenario。

It highlights how attackers can easily exploit weaknesses if we don't use best practices to secure our vector databases。

 And here's where things get find， because this means access granular access controls。

 not at the vectors and the indexes levels。 And these are really hard problems to solve。😊。

But it's not just about defense。 We also need to be able to challenge the output of an LLM。

 to improve them。Cube flows supports this through its model registry feature。

 This gives us data lineage， which basically means that we can track data as in how it flows through the models to ensure that it's being used properly。

We've also got a ton of work to do when it comes to AI bills of materials or AI bombs。

 It's time that we make these models transparent and don't leave them as black boxes。

 This transparency will help us understand the data sources。

 reproduce the results and actually hold ourselves accountable when it comes to biases and ethical concerns。

😊，So looking ahead， this decade is poised for major disruption in this area。

But let's take a current moment to step back and look at the future。Now。

 as we've talked about evolving AI workloads， there's another frontier that we can't ignore。

Quantum computing， again， maybe a hype term。 But let's see why it is。

 This is something that we need to think about。Now。

 quantum computing has an unsettling impact on security。

 A topic that's a bit like realizing that your house keys could soon open all the doors on the block。

Now， quantum computers， as everyone knows， are super fast。They use something called qubits。

 which can be ones and zeros at the same time。 This means that they can explore many possibilities simultaneously。

Classical computers are slower， and they move through each step one at a time。Kind of patient。

 something like patiently flipping through pages in a manual。

 While quantum computers can drive straight to the answer like they've got the cheat sheet memorized。

😊，And for encryption， that's a serious problem。According to National Institute of Standard and Technology or Ns recent analysis。

 algorithms like RSA and ECC fall into 0 bit security against quantum adversary。

 which essentially means that they offer no security。

This also means that data that was previously considered secure is now exposed to quantum decryption。

 almost instantly。So the implication is clear。 We're looking at a full scale migration to quantum safe algorithms。

 and we need to act sooner rather than later。And heres some good news， yes。

 theres some in August 2024 just a few months ago， NIS released the first three finalized standards for post quantumum encryption。

 Phs 203，204 and 205， and they are meant be to survive this quantum storm。😊。



![](img/457d2f618b4f47dccfe18c347ed0703c_3.png)

But here's the urgency factor。 By 2035， the US federal government says that it's only going to buy solutions from vendors that support this sort of encryption method。

So in tech terms，2035 is basically tomorrow。 So if your infrastructure doesn't support rapid。

 doesn't support these quantum safe algorithms， you might be looking at some rapid reskiing and rewiring right now。

For those of us who live in breathe Kubernetes， you might be wondering。

 why does all of this apply to us。 Oh， yes， Kubernetes and the whole cloud native ecosystem is on the front line。

😊，Service mass certificates， ebo atestations， all of the container signing and all of those cryptographic pieces that keep our cloud native ecosystem secure。

 all of them will need quantum safe updates。😊，Another thing to keep in mind is that these new algorithms often come with larger key sizes。

 and this means higher computational demands。 So there's a lot of challenges here that we need to start looking at。

 And there's a ton of work to do。The 2035 deadline isn't just a suggestion。 It's coming fast。

 and we need to prepare right now。We need to move to quantum safe， stay safe standards now。

We're talking about an industry wide shift here。 And to facilitate this。

 the Linuxox Foundation has launched the post quantum cryptographic allianceiance。

 So let's start preparing Kubernetes to make it quantum safe。😊，Cloud native is evolving fast。

 and we've got big challenges across the horizon as we tackle AI， quantum computing。

 software supply chain and more， we need security built into every layer。

This is a chance to truly disrupt cloud native and make it future ready for the next decade。

So let's push boundaries and redefine what is possible in cloud native together。 Thank you very much。

