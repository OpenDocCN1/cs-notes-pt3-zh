# KubeCon-+-CloudNativeCon-大会2025-｜-云原生计算-｜-可观测性-｜-Kubernetes-｜-Prometheus-p42-P42-Do-Your-Containers-Even-Lift-–-A-Hardening-Guide-for-K8s-Containers---Cailyn--BV1Cd32zDEBG_p42-

![](img/47d00a0f2023637691ce73aba18b4f84_0.png)

Good afternoon， Kukon， how we doing it？😊，🎼The cool we get started today。🎼Quick up with the audience。

🎼哎。Okay。Onre let's if you're up for it。Three。I maybe a little more。🎼뭐야 뭐요？Awe， all right。

 so I would not have worn this outfit if I knew how many people were going to show up。

But I'm here and I'm in it and I'm so happy to see you all。

 thank you so much for taking the time on the last day of Kopcon in the afternoon to come to our talk。

 it means the world to us。

![](img/47d00a0f2023637691ce73aba18b4f84_2.png)

So what are we talking about I assume this is why you're here it's the title it's funny and that's what we're gonna go over this is an entry level talk going over the risks of containers if you just make them and you don't necessarily know what you're making so we will kick off with our introduction we are your coaches my name is Kan Edwards I am a security engineer at O zeroro by Octa and also a cochair of Kubernetes Sig security a CNCF ambassador。

 a very enthusiastic dog mom and a sander fan， I've got my bridge for earrings on if that's a reference you appreciate then we should be friends。



![](img/47d00a0f2023637691ce73aba18b4f84_4.png)

And I will pass it over to Dan to introduce himself。 So my name is Daniel Muic。

 I am also a senior security engineer at Uro by Octa。 I am a lover of photography。

 coffee and outdoor adventures， and also a massive sounda fan。😊。



![](img/47d00a0f2023637691ce73aba18b4f84_6.png)

Okay so what are we going to go through today we will start off going over the lingo we're going to go over the what the how and the TLDR we all know that the Kubernetes landscape and the software landscape in general is full of overloaded terms so let's break them downs and make sure that we know what we're talking about Next we're going to go into the before we're going meet this soft and vulnerable container get to know what they've got going on under the hood finally we'll get into what you're all here for which is the montage we're going to take that container from squishy to strong and then we'll finish off with Co corner we're going to offer some tips to take forward to your company to your personal home project so that you can。



![](img/47d00a0f2023637691ce73aba18b4f84_8.png)

![](img/47d00a0f2023637691ce73aba18b4f84_9.png)

![](img/47d00a0f2023637691ce73aba18b4f84_10.png)

Secure your containers and have rock solid show worthy containers。Finally， I'll start with the lingo。

 as I said， we want to make sure that we're all jumping into this presentation with a shared understanding。

 if I say any words， I want to make sure that you are thinking of the same thing that I am thinking of。



![](img/47d00a0f2023637691ce73aba18b4f84_12.png)

Starting off because this is KupCon， we'll go through the Kubernetes components at the very top we've got the cluster。

 that's where everything lives， that's right there a collection of worker nodes。

 then we've got the node， these are your workers， they can be virtual or in the cloud and then we've got the pod。

 this is the smallest deployable resource in Kubernetes and this is where your applications live。

 and then finally we've got the container which is the lightweight unit that contains all the components needed to run an application such as the application code。

 runtime， libraries and configuration。😊，And a few terms that we're going to be using that are kind of container security specific。

 so starting with base images， images like onions are made of layers and almost all are based on some another image。

We have ad dependencies so these can be operating system or your programming language packages that are used by an app to do what it does and these can be direct or indirect and its dependencies all the way down dependencies supply chain is so hot right now I know right we've got vulnerabilities and exploits。

 these can sometimes get used interchangeably but when we say vulnerabilities we mean weaknesses and software that can be used to do something that we don't want to happen。

And exploits are essentially tools to take advantage of them。And lastly， scanners。 So these are just。

A specific type of tool that are designed to examine your container in some way to detect things like insecure configuration。

 things that look like they might be secret， it's vulnerable packages， that sort of thing。

And so why does this matter so。I did a bit of a lit review in preparation for this talk and found that a study from 2021 found that nearly half of the official darkcker hub library images that they studied contained at least one vulnerability that had a proof of concept exploit。

 So by that， I mean an exploit that can demonstrate that this thing is actually usable。

But has not been built to do something actively malicious。

X filling all of your credentials or starting up a crypto minorr。And in a different study from 2023。

 they found that about 30% of popular Doca hubub images were based on a parent image that was outdated by over a month by the time the child was built。

And 70% of the latest versions of those images were built from an outdated parent with a median staleness of more than five and a half months。

So probably we should just use latest all the time。About that so in yet another study from 2020。

 so all of these have got links at the bottom for sources that will be on sharedd after the show there's nothing actually all that special about latest。

 It's only created if you don't specify a tag when you're building the image。😊。

And it only gets updated if the maintainer of that image remembers to point latest at the version that they've just built。

So when you try latest， you're relying on someone else to dictate which image version you're actually running。

 So this study found that nearly 12% of images that they looked at had a latest tag that doesn't point to the latest version。

And about 4% had a gap。Between latest and actual latest of more than five versions。

There is kind of a problem here。In yet， more data from 2023。Ses， turns out they show up everywhere。

 So of the roughly 340000 images that were studied from both Docker hub and。

Quite a number of allegedly private but unsecured registries on the public internet。

 they found more than 28，000 of those images had at least one valid secret。

 and they found a total of 55，000 secrets So most of these were TLS and SSH private keys。

Couple thousand cloud API keys。 Hello crypto mining。And a couple thousand compromised certificates。

And those secrets， they stay in use。So a couple hundred of those certs from public CAs and nearly 5000 of them from private CAs were still valid when the image was pulled for the study。

And more worryingly。Like 275，000 hosts were still actively using these keys to secure services。

 and these were like HPS servers， SSH or Postgs， LDap， MTT。Woof， those are some big numbers。

You haven't seen anything yet。

![](img/47d00a0f2023637691ce73aba18b4f84_14.png)

How about a million？1 million exposed container components on the public Internet。

 data from 2024 found。More than a million of these exposed components。

 and by this they meant RE APIs like the Kubt， the Kubernetes API server， image registries。

 Docker runtime Socket， or etcD clusters。

![](img/47d00a0f2023637691ce73aba18b4f84_16.png)

Of those， the majority were running outdated versions and using default configs。

 which is a recipe for disaster when it comes to vulnerabilities。

About three quarters of a million of them were coup API servers。A quarter of a million kublets。

 And these are things that， by their design are supposed to give you remote code execution as a service。

And 86% of them were， sorry，86% of the exposed cube API servers allowed anonymous off。

 And this is because。From version 1。6， the default has been that if you have an authorization mode other than always allow。

 configured。Then anonymous author is also enabled by default， you can turn this off。

 but because Kubernetes is a declarative， it's going to take some liberties if you've not specified certain pieces of configuration。

It doesn't default to the most secure option instead it's going to sometimes pick a more usable option so that you're not pulling your hair out trying to work out where something isn't working。

So we need to be very intentional about ensuring we secure our applications properly。

Of these million components that they found。About 1000 of them are on public Ip blocklists from threat Intel providers。

 which means we've got a pretty good indication that。

F actors are taking advantage of these services to do bad things。



![](img/47d00a0f2023637691ce73aba18b4f84_18.png)

So now Kan is going to introduce our lucky example container。 So if we could have a drum roll。

 please。More， more， more， more， come on。

![](img/47d00a0f2023637691ce73aba18b4f84_20.png)

All right， this container love sharing secrets， It takes candy from strangers。

 gives its onetime password over the phone， has sent Amazon gift cards to princes in faraway lands and has the same password on all its accounts kept in plain text on its phone。

 It's soft， it's fuzzy and it's going to compromise your applications， introducing squishy bin。😊。

Please don't hack。

![](img/47d00a0f2023637691ce73aba18b4f84_22.png)

So let's take a quick look at what makes this Qie so squishy， starting with our dockerophil now。😊。



![](img/47d00a0f2023637691ce73aba18b4f84_24.png)

The application that we've containerized here doesn't really matter。 In this case。

 it's a flask API that returns a string， but。We're trying to demonstrate how we've containerized it and how we're deploying it。

So we're starting from a fairly slim Python based image using Alpine from the Docker hubub Library。

We're setting up our workd， we're copying across a PIP config so that we've got access to our private registry。

 installing our dependencies， get rid of that PIP config。

 copy across the rest of our app source code， set up our entry point。

 and we're off to the races It's pretty small， can't be much wrong with that right。😊，It's me。Right。

 yeah， so it's a little little baby application it's not doing too much we're going to look right now again Coopcon at the Kubernetes deployment here you can see we've got a pretty standard deployment。

 it's got a namespace label， great job， it's got all kinds of basic settings and this could have come from anywhere this could come from the Kubernetes。

 docs this could come from your favorite AIcom， whatever it is。

 this is a really normal configuration and there's nothing wrong with using it。😊。



![](img/47d00a0f2023637691ce73aba18b4f84_26.png)

Before we get our little friend into fighting form， we need to get an idea of where we're starting。

 so for the sake of the metaphor， this is equivalent to getting a read on our body composition or doing those awful before pictures。

 doing our one rep maxes， Dan's going to take us through the results and give us a good look at where this squishy bin is starting。



![](img/47d00a0f2023637691ce73aba18b4f84_28.png)

Thanks， Ka。So first， we are using a tool from a tool called Trivi。

 which is an open source tool from Aqua Security。 and we're using this to scan our images for any known vulnerabilities or misconfigurations。

And as we can see here， we have got a couple of vs that we need to take care of， including。

A pretty high severity one there that we will come back to in just a minute。

We are also going to point a tool called Tffle hog which is another open source tool from Tffle security to scan our images for any secrets that might be lurking there。

 it can find all kinds of secrets in all kinds of locations。

 even though we're just looking at an image today， but I'm not sure if it supports signal group chats just yet。

And。As you can see here， so much for our super secret password a right there in our Pp config。😊。

So trivia can also be deployed as an operator to your cluster and in this case it is scanning for the cluster components itself。

 the workloads that you're running on it， the infrastructure that sits underneath your cluster。

 the RVac configuration and it creates custom resources in ECD。

 which means you can consume this programmatically in any way you choose。So。

I realize this is a little bit hard to see， but this is a sort of overview of some of the findings that we've got from the Tvi Config report。

 And in this case， we've got。A mutable route file system。

 we've got things like no security configs configured， we can escalate our own privileges。

 and we're running as the root user， we've got an ID for the check。

 we've got a little description of what's going on here and a message giving you a bit more details of exactly what you should do to try and remediate this。

😊。

![](img/47d00a0f2023637691ce73aba18b4f84_30.png)

And。

![](img/47d00a0f2023637691ce73aba18b4f84_32.png)

These are just some of those zoomed in a bit so that you can read them a little bit easier。

So that volume that we looked at earlier。😊，Who doesn't love a CBSS 8。

8 remote code exec in their package management library。

 so CBSS for anyone who's not familiar is the common vulnerability scoring system。

 it takes a number of factors about vulnerability such as what network conditions it needs。

 whether it compromises confidentiality， integrity or availability。

 that sort of thing and gives you a score from0 to 10 to give you a rough indication of how severe a problem is So our demoO app is pretty small and has a nice shallow dependency tree。

 but who here remembers the log for She V and the pain of responding to that incident。😊。



![](img/47d00a0f2023637691ce73aba18b4f84_34.png)

So。Time for montage， it's lifts and water jokes and get this container in a better place。



![](img/47d00a0f2023637691ce73aba18b4f84_36.png)

Starting with some quick wins， we're going to patch almost all the things。

So taking recommendations from any scanners that you've used and updating your image version。

 But some things to bear in mind when you're running these updates。

 if the thing that you're updating adheres to December or the semantic voting standards。

 that's like major minor patch。that can be a really good way of trying to get an indication if what you're updating to is going to have breaking changes in it if that major version number has changed。

Also worth having a look at release notes for any of your sort of critical dependencies because they can or something yeah。

 they can also highlight when things that aren't necessarily breaking changes but will affect you are going to be in the release updating too。

😊，Make sure you don't accidentally run Alpha in prod if you do， you are a braver person than I am。

And just because it should just work。Please test your application。

 I can't tell you how many things I've been told should just work that didn't。

B shout out here to end oflife dot date， which is a really great online reference for a bunch of projects。

 their supported versions and like support dates for。😊，When those versions are going out of support。

As well as Renovate from Men， which is an open source tool that will help automate a whole bunch of different types of dependency updates。

Not just security relevant ones，Yeah， and fun shout out。

 I actually mupped this up when we were preparing the demo and went ahead and pulled a alpha version that was not latest。

 so just because you're in the field doesn't mean that you're just going to do things correctly all the time。

 I think more even than bad actors we need to watch out for not having paved paths and guardrails because we all make mistakes we're all tired。

 overworked and excitable。

![](img/47d00a0f2023637691ce73aba18b4f84_38.png)

So let's get into some of the changes we made to our Kubernetes components to ensure that squishy bin gets nice and secure The first thing we did is another quick win we just chucked squishy bin in its own namespace this is a really common strategy in Kubernetes to ensure that these multitenant applications that are sharing resource space are not actually accessible to one another so this allows us to have bespoke security policies for each of the workloads that we're running and you can see right here it's as simple as adding a line to the deployment。



![](img/47d00a0f2023637691ce73aba18b4f84_40.png)

We can see this in action right away with our next step that we took for security in the namespace we can go ahead and add some labels through the pod security admission controller this is a native Kubernetes feature it's been available since 1。

25 you can also configure the security admission controller in the Yaml we all love Yaml and want to be there all day I love YamL but we don't have time for everything today so I've just done a really basic example you can see the top labels there say enforce and I think that's pretty self-explanatory that's going to go ahead and enforce the pod security level and this is baseline this is just kind of your okay you've met the minimum security requirements and then below we have two other levels set to audit and warn and so Warren is going to warn the user when they create resources and audit is going to add it to the event logs so we'll go ahead and take a peek at what this looks like。



![](img/47d00a0f2023637691ce73aba18b4f84_42.png)

![](img/47d00a0f2023637691ce73aba18b4f84_43.png)

So first we will look at the nameme space itself， we see those labels。

 we've already talked about them， so there they are。😊。

And then we will move on to looking at our pod definition。For these examples。

 I've made just some kind of risky business pods， bad pod， you can see it's got a security context。

 but it's commented out， it's not really doing much lifting at the moment。



![](img/47d00a0f2023637691ce73aba18b4f84_45.png)

![](img/47d00a0f2023637691ce73aba18b4f84_46.png)

The security context that is set there is unconfined， which is the most risky one， but it's not。

 it's commented out。 So we'll go ahead， We'll create the pod。

We get a warning because it has no defined。Security context that it would violate the more advanced restrictions。

 So we'll delete that pod。And then we will go ahead and uncomment that security context。

 I think maybe we'll see。

![](img/47d00a0f2023637691ce73aba18b4f84_48.png)

Could be a surprise。

![](img/47d00a0f2023637691ce73aba18b4f84_50.png)

Oh yeah。I know me。And then we will go back in。

![](img/47d00a0f2023637691ce73aba18b4f84_52.png)

See if we can create the pot again。A no luck could not create it。 So this is really nice。

 If you have very risky workloads and you want to ensure that your security policies are being met。

 you would do something like this that enforces。

![](img/47d00a0f2023637691ce73aba18b4f84_54.png)

![](img/47d00a0f2023637691ce73aba18b4f84_55.png)

If you want to get even further you can use tools like gateatekeeper or Caberno or Kuboring to do the same thing。

 the examples I'm using are gatekeeper but there's lots more that you can use all of these examples come from the gateatekeeper policy library and there are loads there that would probably work in your job and also again for your home lab。



![](img/47d00a0f2023637691ce73aba18b4f84_57.png)

And so the two main types of admission controller are validating and mutating。

 we'll start with validating this just means that it's going to perform a check when there's a change on a resource and validate that it meets whatever policies that you have set we've started out with a very basic one with the Se comp secure computing mode profile。

 runtime default is kind of again the default basic profile and then local hosts would mean that you're grabbing the local hostt profile and it has to be available on the node disk we've allowed all local host files because we don't give a hoot。



![](img/47d00a0f2023637691ce73aba18b4f84_59.png)

And now again， we will go ahead and watch this in action。



![](img/47d00a0f2023637691ce73aba18b4f84_61.png)

And so I will apply the policy， this is all made to run like all of the Kubernetes。

 we've got a Yaml file， we're going to apply it， the constraint is created and we will take a look at it oh no we'll take a look at our bad pod。

 same bad pod as before。Got that unconfined profile， which means no holds barred。

 it can do whatever it wants。Within reason。And then we will go ahead and try and create it。

 you can see that it is denied because of the Se comp policy that we just added。

 now we will go and we'll add this exemption， and so I wanted to highlight that you're able to make exemptions because not all your workloads have the same security requirements and it's very likely that you're going to have some things that need a little bit more of a permissive security policy。



![](img/47d00a0f2023637691ce73aba18b4f84_63.png)

![](img/47d00a0f2023637691ce73aba18b4f84_64.png)

![](img/47d00a0f2023637691ce73aba18b4f84_65.png)

And this allows us to secure by default and start very secure and then open up where we need。

 rather than lock up and then secure where we can。 And you can see now that we were able to successfully create the pod。

 w。😊。

![](img/47d00a0f2023637691ce73aba18b4f84_67.png)

Next we will look at the mutating so same sort of thing we have a policy and in this case the policy will make changes based on a set of criteria。

 this is a very simple one it's going to look and see what the SeCO profile is set to if it does not exist。

 it will set it to runtime default and we will watch that in action as well and this is really powerful because it means that you are taking some of the burden off your developers and ensuring that your minimum security requirements are being met。



![](img/47d00a0f2023637691ce73aba18b4f84_69.png)

We're going to look at the pods， we made the pod， it was able to be created。

 now we'll delete or we'll look it into the details of it and see that it does not have a set comp profile set。

Which is what we expect。Now we'll delete the pod。And we will add。Our policy。Applied or policy。

 so now it should pick up that the pod does not have that setcom profile set and set it， maybe。

I'm just kidding。 I know what's going to happen。I did this。And then we scroll up。

 and there it is magic， very， very， very powerful。

![](img/47d00a0f2023637691ce73aba18b4f84_71.png)

And so we've already touched on updating the image that we're using。

 but we've also made some other changes to our Docker file， starting with that pesky Pp Config。

 so instead of copying a file into our container build and then trying to take it out and leaving it behind in another layer。

 we're instead taking advantage of the ability to mount a secret at build time and it will then be available at the path that we were previously copying it to but not get added to a layer in the final image。

We've also added a user so that we are no longer running。

And we've set up a health check so that our container runtime can tell if we are still alive or not。

It's not shown here， but a quick shout out to the Docker ignore file to make sure that you don't accidentally copy your virtual environment on node modules if you're going to be。

installing them in a container boat anyway， or more importantly， things like an ENVRC file。

 which some of us use to manage different environment barrels and project settings as we're moving around different projects on our disk。

😊，And those usually have secrets in them。 And that trusted host stuff。

 you can ignore that for general use。 That's just an artifact of how we've set up our demo environment。

 It's just telling。The container runs on to just ignore any TLS warnings while we're doing our build。



![](img/47d00a0f2023637691ce73aba18b4f84_73.png)

We are also making some improvements to deployment。

 so we are now pinning our image to a specific digest to avoid any risks associated with mutable tags。

 so if a threat actor somehow got push access to your image registry。

 they would be able to potentially push poisoned versions of images over writing existing tags and then when you spin up your workload you're pulling not the image you think it is。

By pining to a Sha 256 digest， if anything at all in that image changes。

 we get a completely different digest。Adlo will fail。

We also make use of very high user and group IDs to avoid any overlap with the host host range。

 we are running on a readon root file system， we're blocking known Privesk。

 we are dropping capabilities where we can， we're applying a S comp profile and we're applying some resource limits to prevent things like ReddoOS or cryptocurrency monitor from exhausting our cluster resources and generally wasting electricity。



![](img/47d00a0f2023637691ce73aba18b4f84_75.png)

So introducing catch and container， this container background checks its friends and family。

 It has a ubiki in a safety deposit box in case it's death。

 it doesn't hone a single Io device and it sleeps in a farraday cage。 It's tough。

 It's unapproachable， and we might have actually compromised reliability to get it this rock solid meat。

😊，Cat and container。

![](img/47d00a0f2023637691ce73aba18b4f84_77.png)

あ。在。Time for before and after。 Everyone loves it before and after。 And by this， we still means scans。

 And we're going to see how squishy bin has made its transition to catching container。 So before。

 we had a bunch of vulnerabilities that we needed to take care of。 And now。😊。



![](img/47d00a0f2023637691ce73aba18b4f84_79.png)

No more known vulnerable packages are installed。

![](img/47d00a0f2023637691ce73aba18b4f84_81.png)

We have。A cis benchmark of Kate's cluster and our workload deployed on it。 And now。It is clean。

 it is fresh， it is all passing Now this is just our namespace your control plane or a multi tenantant cluster is probably going to have requirements that mean that you're not going to perfectly be able to meet every requirement on a benchmark so you're going to need to do some risk analysis and some bespoke enforcement based on the workloads that you are trying to run in your environment。

😊，But don't let perfectly the enemy of good here， applying some of these controls is still going to put you in a much better place than doing nothing at all。



![](img/47d00a0f2023637691ce73aba18b4f84_83.png)

Awesome。So now we are going to hop into the coaches corner for those of you that work in security。

 how do you do this on the scale that you need to across multiple teams， multiple stacks。

 multiple needs， we're going to give you some tips to ensure that your container security program gets you the results you've always dreamed of。



![](img/47d00a0f2023637691ce73aba18b4f84_85.png)

So tip number one， just like when you're trying to get that rock solid bo you want to make sure that the healthy choices are the easy choices and in the case of container security or any security for that matter。

 we want to make sure that these secure choices are the default choices in practice we be security engineers and security teams don't have the time to go through every single Docker file or every Kubernetes YamL or run scanners in our terminals like we just did。

 what we really need to do as security professionals is ensure that we are paving the roads and putting up guardrails we should have a private registry of blessed images but also ensure that we're making sure that we want and are getting the images that we depend on we should ensure that we're patching and upgrading our images regularly that we're enforcing the use of slim and minimal images。

 ensuring that dependencies are only included as needed and they're vetted when they are included finally have scanning in your pipeline and alert when containers need to be patched and upgrade。

Trust that a security review on the creation of a service is going to be reflective of what that service looks like in a week。

 three months， three years。Next， it's important to make sure that you understand the use cases and goals of your customers。

 And by this， I mean the developers that you work with。

Ensuring that you are fully aware of the processes that you're trying to secure and reducing friction in any way you can。

 meeting teams where they are and adding on to any existing workflows they might already have。

By communicating early and often and involving users in the process。

 you can avoid the nightmare scenario of deploying a control and then disrupting everybody's ability to do their job。

 There is no faster way to upset a company than doing that。

A really great way of doing this is by running threat modeling sessions with your teams。

 It gives you a great opportunity to really understand what these teams are building。

 And at the same time， it gives teams an opportunity to think like the baddies。

 which can be both enjoyable and quite eye opening。😊，And building off of threat modeling。

 that's a great way to educate teams and encourage buy-in if you take time to learn about their application。

 which presumably you will do when you're building a threat model， getting them to dataflow。

 they're getting them to work through the data flow of their application you're going to learn a lot about their application and then when you present the threat model you're able to offer relevant and valuable insight and hopefully they're going to be really enthusiastic to action those items because you came up with them together。

 we all know that the most secure application is one that's turned off but how can you use the turnedoff application and when we make assumptions about developers and the teams and the tools they use not only do we damage relationships but we also risk impacting our customers which at the end of the day none of us want to do we want to create a culture at our companies that value security we're both really lucky that we work at a security company and security is in our blood in our bones but that's not always true you might build something and not think that security is necessarily the priority and when security is successful。

 it's silent。Never hear。 oh， man。 it's been six months， and we haven't been hacked。

 but you hear the day that there's a compromise。 Everyone knows about it。

 So we need to make people know that we're doing stuff。 We're doing stuff all the time。

 Please keep employing us。 We need it。And then a way to do this in a mature level is to create a security advocate or champion program be。

As formal as you want， it can be pretty casual， but you bring members of various teams in。

 educate them about security， and then you have like this mold。

 your person on the inside who's going to be able to represent the security interests and also come to you and be like。

 hey， we're doing this。 I'd love here if you're gonna to be mad at us in six months which helps us to stop showing up at launch day being like hey。

 no， sorry and gets us involved early run security educational sessions， do cybersecurity Mon。

 That's so fine。 every single person loves the CTF。

 You just have to make sure they know they're welcome to try and then completely unrelated to the talk。

 Annie Murphy was on my train here in Canada， which is very cool okay。😊。

And so we' can start wrapping up now so these are some of the tools and resources that we found really useful during this。

 big shout again to endoflifeve。date that I use that all the time at work， Shill。

 which is a CI tool for scanning for End oflife software or software that's about to become End oflife。

 the gatekeeper， Trivi from Aqua Tfflehog， Tfflehog。

 and Helm which made it so easy to get started with the trivi operator in our cluster。😊。

Saavve us so much time。 and Docker and Kubernetes， the Docker desktop integration with Kubernetes gave us a really easy demo environment。

 But there are plenty of other tools， Kerno， confidential containers。



![](img/47d00a0f2023637691ce73aba18b4f84_87.png)

And all of our so the slides are already available on sheds and we've got some of the resources in our repo。

 but we'll be adding some more when we have a chance to recover。

 Caden has to get back to Canada personally， I'm probably going to need a couple days of hibernation to recover but。

Everything will be on shed and on GitthHub。

![](img/47d00a0f2023637691ce73aba18b4f84_89.png)

Perfect， so if you're really amped up about security， which I hope you are。 I am un pumped。

 during the conversation。 You don't have to just do security at your company。

 You don't have to do security at all to help with security。

 You can join me and my cochairs at6 security。 That is the goose QR code where you could come to the Kubernetes S and talk to us about the security。

 come to our meetings， H out and help improve the security landscape。

 You could do it at the Cncf level through tag security， but we would really love to have you。

Honestly， we would love to hear your opinions。 We would love to hear your problems。

 please come join us and and make security better。 No， make Kubernetes more secure。

 security is the best。 So thank you so much for attending。 This is the QR code for feedback。

 if you've got comments concerns。 We have tiny little bit of time for questions。

 Maybe if you have them otherwise， you can find us。

 I think we'll be easy to spot and we'll be around。😊。



![](img/47d00a0f2023637691ce73aba18b4f84_91.png)

![](img/47d00a0f2023637691ce73aba18b4f84_92.png)