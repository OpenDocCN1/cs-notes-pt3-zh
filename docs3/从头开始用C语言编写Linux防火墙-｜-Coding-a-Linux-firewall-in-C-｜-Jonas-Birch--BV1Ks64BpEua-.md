# 从头开始用C语言编写Linux防火墙-｜-Coding-a-Linux-firewall-in-C-｜-Jonas-Birch--BV1Ks64BpEua-

![](img/d302164e99a9a5422b4bf203e5dc4302_0.png)

So， guys。Before we begin coding， which we'll do in a couple of minutes。

 I will just take a few minutes and go through a little bit about what a firewall is and how this project is going to be structured。

😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_2.png)

So in order to describe what a firewall is。We need to describe what a router is。

So let's say we have a simple network consisting of two different segments。So。

We can say that this is an office network。Connected to one port of this hardware firewall or router this far。

And then we have the internet connection on the other side。H。嚟首。

And the purpose of this router is to take all the packets coming from this。Network。🤧K。

And forward it to the Internet。 and same in the other direction。Like。

 so that is basically how a router works。 It will just forward all the packets between those two networks。

But let's say we instead have a firewall。 We still have this。Office network。To the left。

But this time we give it a name。 and let's call this inside。

 That's a traditional name for this kind of network。

And it's connected to the left portion of the firewall。 And the firewall， in this case。

 is a hardware device。Similar to a router in its physical design。

 But it can also be a a Linux server， for instance， So a regular computer with several network cards。

And that's the purpose of the program that we are going to write in this series。

It will turn any computer into a hardware variable。Alright。

 so let's say we have Internet here on the right。And I will draw this as a cloud like this。

And this will be our outside network。Okay， so the purpose in this case， is still to take the packets。

And forward them。To the Internet from the office network。 But in the other direction， it will block。

Most。Of the packet。Like so， except for connections that has been initialized。From the office network。

 that will be saved in a state database。Inside of the firewall。 So when the return packet。Comes back。

 It should also be let。Through。So that is the the difference between those two types of devices。

 the router will allow all different packets。But the firewall will allow。Only some of them。

And we will also have different security levels。 So let's say， for instance。

 that this office network has a security level of 9。I will abbreviate this sec level。

And Internet has zero。 So basically， this means how trusted is this network。

And traffic can always go from a high number to a low。And the return traffic may go back。

But traffic that originates from。The Internet， in this case or a lower security level network。

 it will be blocked。By the firewall。So that is basically how it works。

And now I'm going to talk a little bit about the project at hand。

So the firewall that I intend to write。Is called。Bird cage。And it is divided in two different。

To totally different projects。There is。Bird。Cage。Ker。Which is the core firewall。

 That's the part of the firewall， which will handle all the allowing and disallowing of different IP packets and。

And all that stuff。And that is what we're going to focus on in this series。

Then there is the other part。Which is called birds。Kage。Zhui。And bird cage G I is the user interface。

 and that is a command line user interface similar to how Linux or Uni systems work。

 So the user will log log in to birdage U I system， and then we will have communication between。

Those two systems。 but this will be a completely different project written in a completely different language。

We will be focusing on there。Interesting， cool stuff with regards to the real firewall。 I will。

 however， release the bird cage， you eye。Source code as well。 So that is basically how it works。S up。

 guys， welcome to today's show。 So let's code a firewall， shall we。

I have already started a little bit by creating a template。Consisting of three files。

 so I have a make file for compiling everything。 I have a basically an empty dot C file。

And then I have this dot H file， which is based on my。A template from my bash B， S。System。



![](img/d302164e99a9a5422b4bf203e5dc4302_4.png)

you don't not need to know anything about it， you can go to the rig bow and bash B， S and templates。



![](img/d302164e99a9a5422b4bf203e5dc4302_6.png)

And then， you can just。look at this H file here， for instance。嗯。And I have。

 I'm gonna do some slight changes。 I'm gonna change the name of these。

I'm going to change the name of these macros。So this is gonna be 1，2，4， and 3 Bs each。

And as you can see， I had just have a couple of includes， a couple of type definitions。

 and then the macros for converting from into these。Types。🤧嗯。Okay， and I also have birch ules。

 which is my library with a couple of utility functions。 It's also available in the rippo。

EAnd I created a project called a birdird cage Corps。EBut I am naming my binary， firewall D。

And that D stands for demon。 and that is a common convention when you create。Yeah。

Programs which runs in the background， like servers and stuff。And so this will be called Firewall D。

 That is why I name the files like that。And I'm going to change the C standard to C 23 because I'm running the latest GSCC version。

And I think it's 14 or something like that。But if you're running a slightly older version。

 you can do C2 x instead， and there will not be a difference in the project。All right。

 So how do you code a firewall， Well， I have never done anything remotely alike。

 and neither has anyone else， basically， except for a Steerals who， who wrote the。The Linux firewall。

But this will be a different approach。 This will be a completely user land ring 3 firewall。So。

It will basically。Sn， sniff for network traffic and handle those packets。And if we want to allow it。

 we will allow it。 And if we want drop the packet， we will talk the kernelel and tell the kernel to drop it。

But that functionality， we're gonna code a little bit later。 I w to start out by。

Doing the communication with bird K U I。Because as I mentioned， this is birdircage Co。

 which is the core firewall。 And then we have bird birdird cageage U I。

 which is a completely different project。In a completely different language， even。And。

So that's not something we're gonna worry about in this series。 We're gonna code the。

 the real firewall， so speak， not the user interface。

but we still need to interact with this user interface。And。

And we're going to do that through something called Unix domain socket。

 And that's basically like a regular TCP or UDP network socket only it communicates locally on the machine using files。

And why Uniixor gets well since。Both of this。Tools will be installed on the same system。

 I think it's good to communicate locally using domain sockets。 Plus， if we were to。

Use network traffic for communication， say。Then we would have to worry about。

Handling those packets inside of the fire wall and stuff like that。 Now。

 this would be a completely separate。Al right， that's all you need to know for now。

 So how do we begin this rather ambitious project？ Well， two things， communication。With U I SSL。

And also。The config file。Because there will be a configuration。

EWhich will be stored in memory in some data structure we need to define。

But it will also be say able to save it to a file。 So if， if the server reboots or anything。

 it should still be there。And we need to parse that config file。

And that also makes it easier with with the communication， with the U I， because when we。诶。

When we edit stuff and when we need to tell the U I about the configuration。

 we can just put that into a temporary file somewhere and。Trigger。A realload or something。Alright。

 so let's start by defining the data structure for the configuration。And， let's see。

The configuration will look something like this。And it's inspired by the Cisco ASA Firewall。

 which is a hardware firewall。And this is gonna be a software firewall。

 but it will turn your Linux server into a hardware firewall。 So it's kind of a little bit of both。

And we're gonna have a couple of interfaces。 So let's say we have two network interface cards on our server。

Then we are going to have an interface which is called easy row slash0。That is the first interface。

And the configuration。Will actually， the command will be interface， but it can be abbreviated as int。

And then we will have a couple of configuration lines， which are。

EConnected to this specific interface。So we can， for instance， have something like。Mac address。

 And then， I du't know。Something like this。And and we're gonna use this format。 Windows。

 for instance， uses a different format where you have。 well， it's the same characters。

 but it's a colon。And the groups of two instead of four。 But I think this is easier to read。

 So this is what we're going to use。Perhaps we will later on add some functionality to converse between them。

And we will also have something like I P address。 And then I don't know， something like this。え。

And I haven't yet decided if we're going use this format。With a slash 24， or if we're gonna have。

A net mask like this。This is the more modern approach。 So probably gonna use that。And。Then。

 we will also have。And ability to shut down this port。

And I w to be able to shut it down in two different levels。 So I haven't quite settled yet。

On what the commands are gonna be。 But I think。Maybe。Lay layerer 1 or layer 1 like this， perhaps。

Shu down。 And this will turn off the electricity。To the wire。And。

But we will also be able to shut it down on layer 3。And we could have layer 2 as well。

 but we don't want to overcomplicate things。 The important thing is that we can shut down the I。

Network interface and also the firewall functionality for that in interface。

 And that is what this layer 3 layer 3 shotdown will do。And。And if we。Don't want it to be shut down。

 We will have。Like this。But this will not be shown when we show the configuration。

 So it will just omit the line。Okay， so this is the， the regular IP configuration and stuff。

 But we will also have firewall specific things and all。嗯。All interfaces。Will need to have。

3 things configured before we can take it off the lay3 shutdown mode。first of all。

 it needs to have a。So。Defined。So something like sewn inside。And。

The zone is just a name for the interface。And we also need to have a security level。And I have gone。

Over a lot of things in my head。First， I was into levels。0 to 100。That is what Cisco uses。

 but I don't want to be。We don't need that many levels。So then I was thinking 0 to 10。

 but that's difficult to save in in a optd kind of way。 So I think we are going to Jews。

1 hex a decimal dig。So it can be either0，1，2，3， o the way up to 9， or it can be A， B， C， D， E。

So the A here basically means 10。And maybe the F should be reserved for。

Management interfaces or something like that。 So let's for now， think of this as up to E。And finally。

 we need to have。呃。No， that's all。The I address is the third， so we need to have an I address。

 We need to have a zone name， and we need to have a security level。And then， we can remove those。

Nose， I mean， we can have those nose。So now， the thing is active。So。We will， when we start。

 the I will， we will check how many。Ethernet interfaces we have on the system and will create interface E 0。

0， and then E 0，1。And all the way up to whatever。嗯。How many network interface cards do they have。

And why the 0， Well， this could either be used if we need to add like modules。 So let's say we can。

And。We can have other types of interfaces， perhaps。With a different series。

 or we can have more interfaces that can be added on later on。

Or a third option is this number is the number of the firewall。

 If we have several firewalls in a group， we might want to。Let this be on firewall number  two。

 interface number two， for instance。Sorry。Okay， so that， that's。The interface。

We're gonna have a couple of different other options， as well。

There are some options with regards to the user interface。 For instance。

 we will have users that can log into the system， and that basically means log into the user interface。

So we'll have something like， you， Sir。就呢。Password。Orange。

And then we either have root at the end or nothing at the end。

And Ruth means that with this user is an administrative user。

And we will also have something called a root key。E， by the way， not password。

We are gonna to use pins。So we log in with the user name and a four digit pin number and why that that must be insecure。

 right？ Well， if we just log in regularly， we will not be able to do anything。 Basically， we will。

Be able to check some the status of the firewall and stuff like that。

But in order to change the configuration or。Check some。More important stuff。

 we need to log in its root。And we do that by using a root key。Something like。Yeah。一次。

Something like this。And I'm not going go over this in great detail because it has more to do with the user interface。

 but basically， this is being used as an encryption。え。K。And we will have a specific client。

That we will use。This in combination with a pin number to be able to log in its roots。

But we still need to support this in the actual configuration。

And there are a couple of other stuff with regards to the U I。

 but those are the two important things that has to do with logins。And then we have the third thing。

Which we also need to support from day one， so speak。And and that is access lists。

Access control list。So， we'll do something like。And。Acces list 5。不me。And then， some network。

And maybe we'll have something like。Permit。Host， and then we have one I address。

 So either a complete network or just one I P address。And then we can also do something like。

Drop any。So it will work like this when a packet comes into the network。

It will go through these line by line， so。If it hits this， then it will permit。

If it does not hit this， but it hits this， it will permit。 And if it doesn't hit any of these two。

 it will drop any of the other ones。And this is。A numberered， so called standard access control list。

And there this can be from 0 to 99， and then they can be used for different things。

 perhaps different interfaces。 So maybe we have something like。And。I think we will do。This。Down here。

 actually。So something like， I haven't decided on the command in Cisco， you do access group。

 And then in this case， the number of the。Accs list and the direction in bound or outbound。呃。

And then， interface。E，0，1，0。So well have something similar to this。And by the way， we should。Jump in。

A little bit here， because this is not connected to this。

And we will have some kind of ending command as well。

 So it knows that we are done with this interface， and these are global。Directives。Alright。

So this is basically what we need to support。Then， of course。

 we will add a lot of different other stuff。But in order to have one a working。

E version of the firewall with at least some stuff。This needs to be supported。So。Let's use this as。

A template。And try to create the data structure capturing as much。Of this is possible。

Or everything of this， actually。And that would mean quite a lot of different。thingsings。So。

 let's see how we should。Structure this。All of this needs to be basically in every part of the firewall。

 So let's put。All of this stuff in here in firewall D dot H， the main H file。嗯。Okay。

 so we need to have a data structure for interfaces。 Let's start there。So we'll dostruct S interface。

And。And it's going to have a。历史。😔，It's gonna have two of these numbers right here。

And are we gonna support indefinitely。Many， probably not。Let's say， we support。A。Interfaces。

At least per module， but。For now，8。In total， I guess。Yeah， let's do that。

That means we need to have an8 bit data structure for that。So， let's create one of those。

Let's do a type definition。 And let's call this。Well， first of all， it's going to be an unsign sha。

Because that is the smallest thing we can have at this point。And。and as you know。

 an un signedign cha is。And。I。Let's see。I think a mixed stuff。呃。I didn't mean an8 bit data structure。

EI meant an Amazon char is8 bit， but we're gonna have a smaller than that。

But let's start with an answer in Cha。And what should we call this。Maybe I F number。

For interface number。Yeah。And let's see how much we need。 I think it's a 3 bit。Structure， because。

Let's see if we have 0，0，0，0， this line to the right。It's 1，2。4。诶。And if we count the0。

 we just need the three。So，3 bits。EW whichhich means we will do I F number。And。Let's call it I D。

And we need 3 Bs for it。And I think I have shown this syntax once or twice。Basically。

 you do a colon and you tell it how many bits we want。 And that only works inside of a truck。

And the similar structures。Okay， so that's the first。 Perhaps we should。Mark that， in some way。

Let's see。 Let's put two like this。So we know that we are done with that。😔。

Then we need to store a Mac address and a Mac address is a 48 bit。Thing。Which is。

Right in the middle of。All the difference。Stuff。Because we have。Yeah。We have an int 32。

 and we have an in 64， but we can't create an int 48 that way。And so we need to use this same syntax。

So let's do that。 Let's type this。Unignigned。Yeah。Maybe we should do like this instead。

 It's a little bit easier to read， I think。So we have in8 for this。And we'll have an。In 64 of this。

Maybe。Even like。So。And this will be a Mac address。And then we'll have Mac address Mac with 48。

And then we need to have an I P address， but not just an I P address an I P network with both the I address and this cider。

 as it's called classless entered main routing。but we will also need to have support for IP addresses。

 So let's create both。Let's type de in。32。And this will be an I P address。And。Let's see。

 We need to create a structure。For the network。 But first， we need something for the。Cder as well。

And cider goes from 0， to。32， but the zero is rarely used on its own。

 so we can probably get away with。是。So we have 0， we have one and 2 and 4 and 8。We have。16。

 and we have 32。So， we need。5。5 bit。For the cider。So。The thing that is closest to this。

The closest above。Is in it。And this will be a cider。And then we'll do astruct S。嗯呢。Or network。

And this will contain an。I P address， I P。And a。Sidder。Size me。And let's type if。Is direct。Yes。

 network to。那。And then we can put in the network。No。🤢，来 so。And we have support for this line。

 as well。Then we have those shutdown states that can just be a simple booleion。So， let's do。

Maybe you can do this。If we were to put in a。Anonymous struck here。

And then we have a bull at layer 1。And we have a bowl at layer。3。

And then we justify these as shutdown。This way， we will be able to reach these youth saying， yeah。

So if we have one of these and we've call it end。We will go to in and then shut down， and then。Lay 3。

Alright。AndAnd this should be zone。And this will just be。A regular string。We don't have to create。

Its own data structure， I think。那。So， we'll have an end a。Soon。Or maybe we should do it like this。

Let's say， we allow 16 bys。For this。And security level。There we， will have 16 different combinations。

So we have 1，2，4，8。16， so a four bit structure。By the way， this should be one bit。

And this should be 2 bits。I'm not sure if you can do that。Well see。Where where are we。Right。

 security level。I wanna have one of these for that。 type de。And。The closest isn in 8。This will be。

Level。Or maybe。S level。So we will have a sec level level。4 bits。Alright。

 we're making fast headway here。And。Let's weigh a little bit with this 1。 I wna put it on the bottom。

 actually。So how do we represent these users。Well， it needs to be some structure with an in8 as the username。

And then， we have to。Ha a pin number。Which goes how far。10000。Let's do a small script。



![](img/d302164e99a9a5422b4bf203e5dc4302_8.png)

So。Let's see。For I in。I will do a。Sequence from。1，2， let's say，16。At each location。

 we are going to echo。The number。To the power of 2。Is equal to。え。Then， we take。Don eye。Times， times。

2。That。And we need to add dash。E， I think。That's more like。O。So let's。不。This doesn't look quite。

Right， does it。七臣。😔，31。嗯，你的爱。😔，Yes。It took the wrong order。It should be2 to the power of this。

This looks more like it。Al right， so we w to have something with about 10000。And the closest thing。

Above is this。 So 14 B。

![](img/d302164e99a9a5422b4bf203e5dc4302_10.png)

14 B for the pin number lets。Type that down So don't forget it。

And then we need to have a bulloleion if it's root or not。So， let's type De。え。Let's see。

What did I say，14。So an in 16 should be the closest。And this is a pin code。And we will type。 No。

 well strike。Strt as user。We'll have an in8。Use your name。And let's say， we have 16 us。Limit here。

 as well。And then we'll have the pin， so。Pin code， pin 14 vi。And then， a bullion for the root。So。不。

Ru。1 bit。This is a user structure。Tyd F。Struck。As user。就 Sir。I will put it right here， user。

I don't know if we can do this。 I don't think so。Account， perhaps。Okay。And the root key。

Let's see if I remember this first thing goes from 0 to。1023。



![](img/d302164e99a9a5422b4bf203e5dc4302_12.png)

So。

![](img/d302164e99a9a5422b4bf203e5dc4302_14.png)

So we need a 10 bit for that。And this goes from 50。From 500 K。2。1 and a half million。



![](img/d302164e99a9a5422b4bf203e5dc4302_16.png)

Which means we need to run this a little bit longer。1 and a5 million。😔，1，2，3。Here， we have 1 million。

😔，And 2 million。So，21。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_18.png)

And it's not really necessary to be this kind of granular and optimized， but I like it to be。

Pretty neat。So let's see。 How do we define that。Rot key。Well， the first part is the actual key。

And the second is。The number of。Yeah， the number of round。So。Let's call this。

Just so we don't get a conflict， we'll call this a sub key， which is not hundred percent accurate。

 but。Let's say it is。And the other thing should be。Not in the8s， but in 32。This will be wrong。

So let's create a structure for this。Stt S。嗯。Rot king。And we will have。A。Subit type。

And we'll call this。The key。This will be 10 bit。And we will have a number of rounds。So。

 let's call it an。For n number of rounds。And this would be 21 bit。Typed of struck。Yes。Root key。

As a root key。And we add this as a。K。😔，K。Okay， we are。Almost done。With this part。Fun， as it is。

And this。Is another story and。No， it's not so difficult， actually。😔，Not at this point。

 it will be much more difficult when we allow for extended access list。

 but that will probably be in the next version。 So for now， this is all we need。

 and we already have and the network part。So we basically only need to add something for this action。

And the number。Of the access list。So let's say the action I think I want to define as an enum。

And we're gonna start with just two different。Actions。We will have a permit action。

 which is number one。And we will have a drop action， which is number 2。 But later on。

 we might increase these。So， we will do time。De。Eum E action。Fction。will go from 0 to。99。

So we have 1，2，4，8，16。32，64。1，20。So，7 bit。So we'll do structure for this。 and let's call it。u。

Standard access control list。And it has a number。So this will be an in day。

And what shall we call this。Yes。Identifier， perhaps。7分。And then， we have。The action。

 And I'm not really sure how big these are。Actually， let's find out。



![](img/d302164e99a9a5422b4bf203e5dc4302_20.png)

So， if we create。T andP dot C。Paste this in。

![](img/d302164e99a9a5422b4bf203e5dc4302_22.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_23.png)

Let's just do this。Maybe we should have an include， as well。And will print。Person低。

And this will be size of。Yinan。Ection。4。H。So， it usess an entire。



![](img/d302164e99a9a5422b4bf203e5dc4302_25.png)

Integer。Well， we're not gonna do that for sure， but we're not just going to use。Tubbits， either。

Or one， even。Because we wan to have room for a little bit more。

 So let's say we have three bits for this。So， we'll have an action。Okay。3 bits。😔，And then。

 there's just。Network。So。Next。No。Then we type F struck。S standard ACL， standard ACL。

We put it inside of here。And this needs to be an。Aray。I suppose。Or link list。Let's see。

 We need to have。Several lines。And several。It sell。So maybe we could call this something else。

 Let's call this an A C， E， an access cultural entry。So， this is for just one。

Then we probably don't need this identifier。So， it's an action。At this。😔，And this is。S一。And an ACE。

And then we can do something like type death。If we have。SGDSE。99。So，99。No， that's not it。

That's the number of。Excellf。But let's do the same。

 Let's say we have a maximum of hundred0 entries per。Ael， I think that is reasonable。

So 99 S A Es is an A L。And then we need to have room for。Standard A L。Let's just call this。Aself now。

And we need to have 99 different。He sales。That's not very optimized， though。

 If we don't only use one， we still have room for a lot of days。

So it's good that we saved a couple of bits here and there so we could waste them here。

But I don't w to go the path of link lists I。Dontless I need to。Maybe。

I can have this in the back of my head， and then we can。Then I can probably write this。

 so it will be easy to change later on。So now we have support for all of these。😔。

And the antibody way will be the same as。0ero I P address and 0 here。So we don't need to have any。

Extra thing for that。And then we just need to enable it， as well。And maybe the easiest way。

It's just putting it inside of the interface data structure。Did we create one of those。Wai a second。

 We put everything on the interface here。That's not really what we want。

Those three lines we wna put on its own。So， let's。Create。Something for this else。So。

We'll have an A sale。Oh no。We might not have an ail here。So， maybe we'll do this pointer。So。

 let's say。An inbound。Ifill。And oh。Bound。谢谢。It's too long。Ael in。你时候。😔，So the number。mhm。

So we have a number since we have a reference to， and。I they with that number。We had the direction。

 and it's link to the interface。 And if this is。Poining to 0。 Then we don't have it。Activated。

That's good。Today are all the different A C。Interface options。So， will type death struck。S interface。

As interface。And now we can create our final thing。Which is the config。And here， we will have。

A couple of interfaces。So。Interface， and how many did we say， a， right。So。I F。himt name it。 I F。

because if。I是。Keyword。I face， perhaps。And we need to have。2，8 so 7 here。Or let's make this point。

 instead。Maybe even。An array of pointers。Then， we can allocate。One at a time when we enumerate these。

interfaceters。And that's pretty much it， I think。 So we'll type de as config to config。

So now we can keep the entire config in this structure and just pass it around to the different parts of the program。

 or perhaps maybe even have a global variable or something。We'll see how。Yes。Play so。

We can also pass it around as。Self pointer。Pas it as a reference to the functions。

 that I gonna need it。All right， we'll take a short break。



![](img/d302164e99a9a5422b4bf203e5dc4302_27.png)

。S guys。I'm going to take a few minutes and show you how this UI is supposed to be。So。

When you log in， it looks like this， this is a problem where you can type。And you can。

Move through your different commands。So if for an instance， to show version to see the version。

 I can press app app arrow， and I can modify the command。And I can cycle through all other commands。

 exactly like modern Linux。Pro。But quite difficult to get right。 actually。

 if you code it from scratch， like a deal。And。Alright。

 so you can also do if you don't know the command， you can， for instance。

 or maybe you know part of the command， you can do。Let's say show and you press tab。

And you get a list。Of the difference。Possible。ComYou can at any point， also press question mark。

And you get the more detailed list with a little bit of description for the different commands。

But if I want to do。Sohow run， for instance， that's short for running config to check the configuration。

 This command will fail because at the moment I am logged in as a regular user and you need to be route for that to be possible。

Same if you want to do like。Configure and stuff like that。And。Allright。

 so in order to elevate your privileges， you type elevate。And then， you get。One of this challenge。

Numbers， so you copy those， and then you go to a different。TheDifferent window。And you run the。BC。

 login program。Which looks like this。Yeah， you can add a key for。Different firewall。

 So you can have a list of those。 I will not go through how that works with kids and stuff。

But in my case， I just typed the ba login firewall。It will ask me for the challenge。

 and I placed in those numbers。It will ask me for a pin code which is personal to my user。So。

 I am there。For numbers。And now it encrypts this。Challenge with this pin code， and。

A so called root key。And this is the result，38，19 in this case。 And this is different every time。So。

38，19。I just type it in。And now you see that it's a hash symbol instead of this。诶。Re than symbol。

This means that now I have access to all the commands so I can do show run to check the configuration just the example。

And at the moment， there are not so many options。 It's for the host name。It's this name right here。

 And I can change it by going into the configuration and just take the typing in host。

 and then the name of the device。 Let's say， router5 or something。And as you can see。

 it instantly changes this probe。And this is an example of a root key。

And you can generate one of those。I type in January。Some random number。

But I haven't yet implemented that feature。AndBut the most important as of right now。

In order to make this word together with what we are going to code today。E I'm gonna show you。

 Let's just first。あべ。Take those new numbers。And those are randomized， so。Different each time。

And we do the same again。You only need to do this once per。Okay， I sat in the wrong。

You only need to do this once for every。Lo in， you do。 But since I got logged out。

 I need to do this again。とれる。クスもスやとりてきて。Allright， so let's see。嗯。

Let's say I wna create an access list。 That's。Dfining what I addresses and so forth that should be allowed。

So I I just do access list and we can do the question mark to see。The synt。So well give it a number。

And we can。And we can。Permit， for instance， the network 10 1，0，0， slash。See。And perhaps， women。

2なで sixty8。Not1， thats 24。And maybe we won't want to drop the IP address of 212，16，1624 or 23。

And then maybe we want to permit everything else。So permit only at the end。And if we do。S。

 H run access list。We see any commentss。With regard to access lists。

We can also do just show access list without the run。

And we will get this table describing the different parts of it。So in this case， we will。Allow this。

Networks。嗯。No， we will allow these two networks， and we will draw。S A P address。And permit the rest。

So that's basically how it works。 Let's see if I。F格。Thing。嗯。Yeah。

 and here is how we can add a root key for authorization。And we can also add a user。

 So we say userr and the user name and then pin and the pin code。

 And if we should allow route access or not from this user。And this is basic quite basic function。

 I like this far。But there will be more features and more advanced access lists。

But this is so we have something to work with。And you haven't missed any video because this I have done on my own。

 And this will be a separate project。 We will focus on the core firewall， which is the cool thing。

So let's continue with the code。

![](img/d302164e99a9a5422b4bf203e5dc4302_29.png)

So guys， welcome back。So before the break， we started out with our firewall project。

And defined different data types for the different。Part of the configuration。And。

I did one thing after。During the break。And I just selected this thing。 the user account。So。

 I wouldn't forget。Because。We don't just have one user account， right。

 We need to have several of these。M。😊，So。Lets。See how we can best do this。

I don't really like the way we did with the access lists。😔，That we created100。

Of of those in an array。We could do the same for the user accounts。But it's not really a good way。😔。

To go。 So what alternatives do we have。We could just make this pointer， and then allocate。

As many as we need， but I think。I think we need to decide how to do this in a more general kind of way。

And either we do like this。 So we make it a pointer and then we allocate， and then we can reallocate。

When we need more， but that's not very effective。 So a better solution is creating either a linked list。

But that's also kind of slow。So。I was thinking why if we create a general type of。And。

A dynamic array。So a d dynamic array has the following structure。Let's say， we create。

Something like this。And。Then we。Will have。And first of all。A size of this thing。

So let's say we have an in 16 size。And then we need to have a capacity。

So let's say we're having an in 16 capacity。And I wonder if in 16 is the best。 Yeah， it is。

 We're not gonna use more than 65 k， anyway。So basically。

 the size is how many entries do we have in this list。The capacity is。

 how many entries can we fit in this list。So let's say it by default， allocate space for 50 entries。

 Then the size will be 0 from beginning。And the capacity will be 50。And when we reach that capacity。

 So the size is equal to 50， and we need to have more then we will allocate an additional 50。

And so on and so forth。And。And we need to have a third thing。

 And that is the actual data that we need to store in here。 And since we want to make this a general。

Type， which will be able to handle different kinds of structures。And。

We have a couple of different possibilities， I suppose。But。I think。In this case。

The easiest way would just be to make them void。And then have something of the sword。Let's see。

Let's call it data。And then we create a type definition for our structure as dynamic。

And let's call this。嗯。What if we were to call this。Just。Alright。

 so we need to have something which creates one of those and handles the size and so forth。

The allocations。So let's start with a a constructor function。

 And we need to decide how many should we have。え。And since some of the structures might be kinda big。

I think。20。Or 10。Let's see。10 access list。Yeah， I think that's okay。So。

 let's make a definition for that。嗯。Something like。Define， and then。D。Block size。It's too big。

 Let's just call this block size。Maybe we can have like this。So let's say block size is 10。And then。

 we need to have。The constructor function。So it will return a dynamic array pointer。Let's call it。

Mei。😔，在那咩。嗯。What do we want to have in here。😔，And。Nothing， I think。

Because we want to create an empty。An empty one。And then we wanna， wanna have。Other functions。

 as well。Something。Which will。Let's see。That will add something into one of these。So， let's call it。

Din earth。And。Then， it will return。The you say。So then or maybe not， actually。Let's do it， as a void。

So。AndDt add。And it's gonna take a dynamic。也。Aray， and it's going to take an entry。Of type void star。

So we can add to it。And we can create1。 I don't think there's any point in deleting。Or is it。

How would we delete something from it。We would have to create。And new one and copy over stuff。

I think it's better to just。0 out。In that case。嗯。I guess。Let me just think a little bit。

Let's cross that river when we need to。And so let's say put this in code。So， we need to create the。

Cstructor。Make dynamic。No argument。We need to have a pointer for this。嗯。And what do we need to do。

 We need to have a size， as well。And the size。Should probably need to be in 32， in this case。😔，No。

 what is the size。Well， its。Will be。嗯。That basically depends on。See。嗯。

Ps on how we're gonna store stuff inside of this。Do we want store just a pointer to another allocation。

Or do we want to store the actual thing。嗯。Maybe we could actually store the actual thing。

In that case。We will give it。The size of that thing。So。The size would be。Like this。我。No okay。

 so let's see。 we need to have。A， maybe we could do this instead。We create a count。

 So the count is the number of things we have in it。 The size is the size of each thing。

The capacity is。How many entries do we currently support。And the day， the is。The actual。Da的。

With all of these。And trace， I think that's the best solution， actually。Maybe we could even do。

Better。What if we were to call this dynamic prime。I'm going show you why， in a second。And。Alright。

 so now we will have a。嗯。This would be make dynamic prime。And this will be an in 16。And。Entry size。

And then we have it in 32 for the whole thing。嗯。And I w to make one smaller。

Additional change instead of just doing void data like this。Let's do in8 data， and make it an。

Empticized array， which we can increase by doing the actual allocation。 And why indeed date。

 Because then we can just copy the bytes into here。This is a rather elegant solution。

 I'm going to show you in a just a sec。Alright， so。How do we calculate the size。Let's do it in。

In one step， like this。So the size is going to be the size of。诶。The size of the actual structure， so。

Destruct S。Dynamic。And then we need to plus。Enterize。Times the number of entries。

 which is our block size。Because we want to create10 of these。From the beginning。

 or at least space for1 of these。So， now， we have the。Size， then we can make the allocation。

 So P is going to be a dynamic。And we man了。S bys。And we're also going to clean them out。So。

 we will 0。Yeah亮。O屁。And。Size bites。Let's also assert that we have a P。

 because if the allocation fails， then something is seriously wrong。 and we should just quit。出気？呃。

And just to make stuff explicit。We can do like this。😔，AndWe can set the count。Does Si like so。

And we also need to set a capacity to the block sides， which is 10 in this case。

And what else do we have， We have。The size of the whole。Thing or the size of the。Of the data。

So how much is that。That is the entry size times block size。So size is equal to entry size times。

Block size。And then we just return P。And why did I call this make dynamic prime。Because now。

 we can create。A macro， a function based the macro， which we call make dynamic without the prime。

 And then we are not going take the size of the thing。 We're gonna take the data type。

So this will be something like。What is it called。Not a higher order。Fengxiing。But a。

Higher candidate type， actually， or something of the like。And so， let's see。

So if we have our definitions here， we can have our macros here， or we have macros somewhere。

 don't we。Yeah， here。No。😔，Here。So let's create the macro for me。嗯，等了め。

Then we're going to take an X as an argument。And what are we gonna do。

 we are gonna call our make dynamic。Prime。And we're gonna pass。The size of。哎。

So now we can call this function by doing something like。🤧。For instance， if we wanna do it for and。

A standard access list， we can create。Something like this。We can do A C， L is equal to make dynamic。

Dynamic。And we give it a data type。Standard A C， L。And then， it should create。10 of those。

Kin of lifted to her。Have you seen that in sea before。I don't think so。Alright。

 so now we have created this thing。 Next step is2。え。Add something to it。

And are we still gonna use void here。😔，Yeah， I guess that is the best way。So。Let's create。いん。Avoid。

Dner。And what are we gonna give it， We're gonna give it a dynamic array。So， dynamic。啊，而。Laura。而。And。

Then we're gonna give it the thing we're gonna add。So， entry。So how are we gonna handle this。Well。

 let's。嗯。We have two cases， Either we have space to add it， and then we can simply add it。

Or we don't。So， let's make a case first。嗯。If。Our array。Let's see。If I were a raise。Cold。

Is more or equal to。 It should never be more。 But who knows。Better sur like this。And but if it's。

Equal to the arrays capacity。 So we don't have room for this thing。

Then we need to increase the capacity。And we're going to increase it by block size。

Which means that we need to have a。New size。うしい。Let's also create。Something called N。So。そい。😔。

Entra size。And we need to know the new number。😔，Or the new capacity。

So the new capacity should be the old。Cac。Plus， block size。 So we increase it by a block size。

And let's set n equal to entry size。Times the new capacity。

So this is our new size of the data portion。And we also need to have a new total size。

Maybe we should use a size here instead。 so we don't。没。Our different names for them。

So this is the size of the data。And then we set n equal to the new size of the whole structure。

Which is。The size of。h。Exstruct as dynamic。Plus。The size of the data。And now， we can make the。

New allocation。And we do that。😔，By saying。We need a new pointer for that， I suppose。Or probably not。

We can use our。So2。Is equal to dynamic， And then we use real all to change the size of the allocation。

And， and we give it the old。Poiner。And we give it the new size， which is。え。And in this case。

As an integer。Something like that。And we can once again， assert that we have an R。So now。

 we have successfully increased。The size of this。We also need to update。The capacity inside of。

The structure。So，2。Capacity is equal to care。Like so。And the rest won't change。So。

Now that we have increased or not。Perhaps we had room， as it was。嗯。By the way。一次。

All of these are in 6s。The capacity could be only 16。And count。

 But I think the size should be an in 32。Because it's quite， could be quite big。But it is the size。

 Wait a second。 It's the size of the。Individual things。So， let's。Do this all。溜溜溜乐。😔，Let's see。

So I didn't mix up stuff some stuff here。Size。His entry size。Times chat。Let's set all to 32， instead。

We don't really know at this point what we're going to use them for， so。We need a lot of room。😔。

So cap is equal to the current capacity plus block size。 That's a new cap。 The size is equal to the。

Yeah。To the entry。The entry size is。Our size。Times the capacity。

And then we'd just add the rest of the structure。We are located。😔，As Sir。

 that will update the capacity。Yeah， sounds good。AndLet's also。Just to make it clear。We create。

An index。Because the index， the new index of the new thing we are about to add。

Is going to be the old size。So。嗯。ItsThe R。12。他错了吗？😔，Because if you have three entries。

And the count will increase to 4。And if we wantna access the fourth element。That will be 3。

 counting the0。 So the index should be 3。🤧嗯。And now we need to copy in the new entry。

And we can just do a memory copy。And we need to define what that means。So， let's see。

We're gonna copy it into。A raise。Data。嗯。The index。And we're gonna copy it from。The entry。And。

And how much are we going to copy， Well， it's the size。Of the individual thing。

But we set the size to the entry size。Maybe it's better to call this entry。So we don't mix it up。

As I have done multiple times already。So this is the entry size。😔，And the entry side。

 we get from this。The entry size is equal to the。Entrase。I think this is the best way。

 Then we can just。Do like this。So we take the individual entry size and times it with a capacity。

Do we do the same here， We take the entry size times the block size。Here we take the。

with times its with energy。 I， I think。This is the right thing。So we memory copy this stuff。

And then we can just return， I guess。But what is memory copy， We need to define that， as well。

The memory copy is going to be。Avoid function。Memory， copy。It's going to take an innate source。Int。

 yeah， I mean， destination and an intake source。And it's gonna take。嗯。Ying。32。Exercise。So。

 we have void。Memory。河边。In a destination， in the8。Sours。And 32。Size。We need to have an in pointer。

And we need to have some。And for。Knowing when we're done。

And then we do a four loop where we set P equal to， by the way， we can't just have a P。

 We need to have one per。Source and destination。 So let's have a D and an S for destination and source。

And we set the D equal to destination， we said。Sos equal S equal to source。We set n equal to size。

And we're gonna loop as long as we have an N。And。What are we gonna do at each iteration。When we're。

 well， we're gonna increase the destination。And the source。And we're gonna decrease the end。And then。

At each。Iteration。What are we gonna do。We are gonna set。The destination， equal to。Source。And then。

 we're gonna return。So， this。Willll go through。And the number of times。So， size number of times。

And just copy。One bite at a time。And let's also create a function。 that will。And。That will。Prim。😔。

The content in some way， or at least。Information about it。So， let's say we have a。Avoid。D print。

And it just takes one of these dynamic things。It should be dynamic pointer there， and there。

And what will the print thing do， will then print。让你 take下美。😔，Or。

I will just print some information about it。So， let's say。嗯嗯嗯。嗯。

I wonder if it would be beneficial to save the type， as well。At least for the printing purposes。

We could actually do that。So let's just say we have a small in a。呃。系。And。

Shouldn't but need to be bigger than。16， and if it is， we will only。え。Put the first。

15 bites of it there。嗯。And how can we put something in there， Well， we need to use our。Micro。

We call make an。喂。😔，The size。The lesss also give。The string representation。Or， rather。

The innate representation of the string。Representation。And。I always seem to forget how to do this。

 but I think we use this。hash symbol like this。Which means we need to add an argument to the make dynamic。

And that is just a innate point representing the string。Will be cand of cool to save the date。

 the type as well。Or the name of the desktop type。So。Here， we will have。诶。In the。Da time。

And we are going to memory coffee。Into the P。疼。Yeah。And we take the data time。And we simply copy。😔。

历史。😔，We can use the。Min function or the macro。So。The thing we give it two arguments and the one that is the lowest。

Will prevail。So。Let's say the first being the string length of。The data type。And the second being15。

So that' way we will not copy too much。We need to define what min means。😔。

So we'll have a macro called min with an X and a Y。And。Let史。In case。X is less than。喂。😔，Then we will。

 well return e。Otherwise， we return why。Yeah。Okay。So， now we can do。A kind of if the print function。

Where we are going to print。呵不子。Let's do data time。And then we'll have the name of the data type。

And a new line。Let's jump out a little bit。And then， we will have。The capacity。Maybe we can just do。

Cirulate。mmm。嗯嗯。Maybe we can do it even better。😔，What if we were to do something like。Printing。

And then we do this。And then， we have。Da the type。雷骚。😔，And then， we have the。Psideive。Enterse。

And what else did we have here。So， enter capacity。😔，Did the type。Counts， that's the number of。彩斯。

And then， we have data。Let's。主这是。呃。扣子。Entry size。Then we do a double like this。😔。

And the first should be the。Vor。I'll come back to what that is。And then we'll have the data type。

 which is the Rs。タイプ。Then we have the capacity。And count。And the entry size。哦。Like so。

 And let's also add this。EVar， which should be an in8 pointer。

This should be the name of the variable。嗯。All right。And then， we do。We show some of the date。

 that let's say we。Do a hex dump。Of the first， say。32。But。So， we do print。Let's see if I remember。

The argument list for this。We wantna print our。Da的。And。😔，嗯嗯。See。😔，And we wanna print the minimum。

 the minimum。Of either。Count times。Yeah。TheEn size。 so we don't overflow this thing。Or 32。

 if that's the less。Leer one。Literary cool。I think that's good。And we also。

Might have some kind of separator。😔，Oh， let's just。Do without。

And then it would end adjust adjust to an extra new line。And return。O， so how can we。Get the v here。

 Well， we do the same trick as before we call this thin print prime。Dn print prime， and we add。Ying。

8 pointer。And then， appear。We define。Yeah。D print。And we haven't。We just take one argument here。

 So we have an egg。And we called in print。Pride。And we give this。诶。But we do also give it。😔，你哎。

Like so。Like we did down here。And this dollar 1。That's just a type cast from string to in。

 in this case。All right。 kinda cool solution。 if you ask me。Let's see if it works。So。What do we need。

We need to have a dynamic array， by the way。😔，We need to。A Sir。That we have。An array。

And let's also assert。That the array。Has a。Cold。Which reminds me。We forgot to increase the count。

When we add things to it。Like so。So， R should be equal to make。Dynamic。

And what is the date type we wna add here。Let'。Sa。Let's say we add intes。So， we just。Give it。In。嚟首。

Just see that。Totle this right。So， make dynamic of X。Size of。呀那识别。😔，ToMake dynamic in。

So now we should have 10。 Yeah， we should have room for 10 integers。So let。Add something to it， so。

Dinard。And we wna add。To our。And what do we w to add。Well。We wna add some numbers， right。1，2，3，4，5。

 say。And then we run print， no。D print。And we give it the array。Then we free the array， and return。

Alright， so let's see if this works， we probably need to fix a couple of errors。



![](img/d302164e99a9a5422b4bf203e5dc4302_31.png)

嗯。Let's。Start。F into the egg。It's not followed by a macro parameter。 Okay。

 it doesn't like the parentheses。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_33.png)

So let's just remove those。

![](img/d302164e99a9a5422b4bf203e5dc4302_35.png)

The width of key exceeds its tie。

![](img/d302164e99a9a5422b4bf203e5dc4302_37.png)

So how did we define the sub key。So key as an end8。 It should be in 16。



![](img/d302164e99a9a5422b4bf203e5dc4302_39.png)

Expected identifier right the line 93。

![](img/d302164e99a9a5422b4bf203e5dc4302_41.png)

I made the wrong syntax。So where do we put the99， do we put it。Here， perhaps。



![](img/d302164e99a9a5422b4bf203e5dc4302_43.png)

bitfield shut down， has invalid。Hi。H。

![](img/d302164e99a9a5422b4bf203e5dc4302_45.png)

Hd02。没有。Maybe we can do that。Can't define。你别。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_47.png)

零。Like that。Type F S config， config， andon type name S config。 Yes， that's right。



![](img/d302164e99a9a5422b4bf203e5dc4302_49.png)

Because。Where do we have conflictfig。Right。This should be struck as conflict。



![](img/d302164e99a9a5422b4bf203e5dc4302_51.png)

Let's see。 memory copy string line。 We haven't defined the string line function。 Let's do that。

 as well。

![](img/d302164e99a9a5422b4bf203e5dc4302_53.png)

是。we are going to have a void。 No， nothing void。Let's see。Let's do it in 16， in this case。So。

 string land。And we would give this。Let's see how we use it。String them。We give it。We give it an in。

So， let's do that in a star。And how do we create a string language function， Well。

 it's pretty simple， actually。嗯h。😊，In 16 string length。 And we give this an in。え？呃S9。And。

What do we need， Well， we need an in a。皮。😔，And we'll do a for loop where we said P is equal to。

We need to have a counter， as well。We said P equal to S d R。 We said n equal to 0。

We're gonna loop as long as we have P。And we will increase P， and we will increase M。

And then we' just return and。

![](img/d302164e99a9a5422b4bf203e5dc4302_55.png)

Cst point there from integer， different size。Meory科 be。😔，到了晚。😔，2。Data。嗯。Dyna is no number。Name， size。

 not。Ttty pointer。From inger。Or they the。ADA。嗯嗯。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_57.png)

It， it is the correct size。But it's。An empty de。Which we have allocated for。嗯。

Let's see how we did this。Memory copy in the8 and8 in date and8。This是 good子。で视。And how do we call it。

Memeric。😔，Memerical of the time。The time is in the so。



![](img/d302164e99a9a5422b4bf203e5dc4302_59.png)

Is this a line。Complaining about。No。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_61.png)

53。All day the。At idea。Maybe we should do some pointer arithmetics instead。So let起。😔。

If you haven an in8 P。And we said P equal to R。Data。So， that's the first。我。And then， we plus it by。

They are。Entry size。Times。The end。And we put P here， instead。That should be right， I think。



![](img/d302164e99a9a5422b4bf203e5dc4302_63.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_64.png)

Has no name， member， name， size。自際？Okay， so this should be。The interest is。



![](img/d302164e99a9a5422b4bf203e5dc4302_66.png)

Expected， blah， blah， blah before。

![](img/d302164e99a9a5422b4bf203e5dc4302_68.png)

63。Did I forget。App parenthees， perhaps。There we have this。人家。This。Min。😔，Here is one。Herelish one。

Here's one。App here， okay。Maybe we don't need to assert that it has a calm。😔。

Let's just do an if statement down here， instead。So， if our。Has can。Then we do this。



![](img/d302164e99a9a5422b4bf203e5dc4302_70.png)

Let's己。In expansionsion， blah， blah， blah， make dynamic in。Incomparable type for argument。

 One of the a。😔，你2。😔，He。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_72.png)

But did we say that the a had for first argument。睇到未。😔，2。点爱点哪米。😔，Star。We forgot to make it a point。



![](img/d302164e99a9a5422b4bf203e5dc4302_74.png)

Okay， we're down to just one error， basically。In expansion， blah， blah。

 blah expected expression before this parentheesis。Or they could make dynamic in。Size of。In。



![](img/d302164e99a9a5422b4bf203e5dc4302_76.png)

Maybe we shouldn't put it in parents。W was事。😔，Make the love me。😔，Maybe we should just do that。Here。

 though。We should do this。And why do I put this。Arguments。Inside of parentheses。Well。

 that's because we might want to given expression。There什 no argument。And we want to capture。

That possibility as well。

![](img/d302164e99a9a5422b4bf203e5dc4302_78.png)

So let's see if it compares now。It does。 correct。 Do you think it works。No。It's sful thing。Okay。

 let's see what it says。SDR lamb。M。Yhy S lamp。😔，Maybe it calls my string length function， as the。

Probably so。But what does it pass。That's a bit weird。And why does it crash。So， we may look with0。



![](img/d302164e99a9a5422b4bf203e5dc4302_80.png)

We do string length。So are we still inside of that function。😔，The construct function。Make the name。😔。

We allocate with 0。To do this in this。Is the。You gave it the time。

When to copy it into the type field。And how does the type feel。No。Well， it's just an array like this。

And give the day time。It should be in。The string length of。In to be3。3 is less than 15， so，3。

But is what we should cope with。

![](img/d302164e99a9a5422b4bf203e5dc4302_82.png)

And it returns to。From。

![](img/d302164e99a9a5422b4bf203e5dc4302_84.png)

That sh real matter， too， should be okay， too。So did I miss something here。We have a destination。

 a source。The size。The N is equal to the size。This destination is its source。😔。

Stngs we have an L wave。Go on with loop。Then we increase the day。We increase。The S。

Were coffee into the tide。Maybe it has to do with。No termination， perhaps。

But we are zero out the whole thing。Before her。Let's add some thebu message， for now。So， let's。

Let's do this。Supetai。Be printed。

![](img/d302164e99a9a5422b4bf203e5dc4302_86.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_87.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_88.png)

Okay， let's see what it says。P type is equal to8。 Okay， so that's no problem。



![](img/d302164e99a9a5422b4bf203e5dc4302_90.png)

This is not where it crashes。😔，Is it designer of the Dun add， perhaps。If I come。Is。More。

Or equal to the R。Capacity。我去去乐比。😔，So， the idea。Its equal to 0。And the R data。Plus。Our entry。Times 0。

So P should be equal to r datata。And into that， we copy。Our entry。And the entry side。

It will increase cold。Let's add some debu thing here， as well。So if we see this debug one。

 then we know that the add function also were。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_92.png)

But， we do not。And this time， we didn't get the first one either。



![](img/d302164e99a9a5422b4bf203e5dc4302_94.png)

Did you removed。也色聊聊天。😔，So， the add function。We have some problem here。😔。



![](img/d302164e99a9a5422b4bf203e5dc4302_96.png)

thisす。

![](img/d302164e99a9a5422b4bf203e5dc4302_98.png)

Okay， so it's our memory copy。嗯嗯嗯嗯嗯。Let's try this。

If we just comment out these lines and we try to print the empty array。



![](img/d302164e99a9a5422b4bf203e5dc4302_100.png)

What happens then。Data type is in。 That's pretty nifty。Printing R。 that's the name of the variable。

 Also printlift。Capacities1 count is 0。 entrytry size is 4， because one integer is 4。But。So。

 it looks okay。

![](img/d302164e99a9a5422b4bf203e5dc4302_102.png)

而V。A we allocate them。车轮日牌。😔，Let's add some back message。



![](img/d302164e99a9a5422b4bf203e5dc4302_104.png)

Allocated60 by。68 birds。Because four times 10 is 40。😔，And the rest of this。This 28 bys them。So。

 we have room。

![](img/d302164e99a9a5422b4bf203e5dc4302_106.png)

And there's no problem with this memory copy。😔，But there are obviously， problems with。This one。嗯。

Let's just double check that we don't reach this point。



![](img/d302164e99a9a5422b4bf203e5dc4302_108.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_109.png)

And we need。Those both。

![](img/d302164e99a9a5422b4bf203e5dc4302_111.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_112.png)

Okay， so we don't。Come here。Which。Is。Right。So what if we were to。Print what we are。

Giving this function。So。Were calling memory of。😔，And we are giving it。P。😔，Very convenient in in a。

Version of the entry。And then， the entry size。So what do we have here。You后 the屁。嗯。DN3。And then。

 the entry size。

![](img/d302164e99a9a5422b4bf203e5dc4302_114.png)

喂。Let's see what it says。

![](img/d302164e99a9a5422b4bf203e5dc4302_116.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_117.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_118.png)

H。Sfuls before this。

![](img/d302164e99a9a5422b4bf203e5dc4302_120.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_121.png)

Okay， so。This is no problem。Let's print the address instead。



![](img/d302164e99a9a5422b4bf203e5dc4302_123.png)

No we should get some useful information， I suppose。哦。Hey。So we try to memory copy into this address。

😔，But。😔，We are using this。TheArgument， the integer。S。The an address and。A reference。



![](img/d302164e99a9a5422b4bf203e5dc4302_125.png)

Okay。No， this。I guess we need to send the reference to this。😔，Is it even possible to do。

Something like this。

![](img/d302164e99a9a5422b4bf203e5dc4302_127.png)

M熊2。😔，No。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_129.png)

Well。I guess we need to do something like this， now。Create the variable X。And we want to set。

一 to thisす。<|OTHER|>And no， I suppose we should be able to do this， right。

Let's see see the accept that。Okay， let's do this instead。So。X is equal to1。Then we。嗯。We don do and。

We have an array。Will send the reference to X。

![](img/d302164e99a9a5422b4bf203e5dc4302_131.png)

And well just change this， like so。

![](img/d302164e99a9a5422b4bf203e5dc4302_133.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_134.png)

Okay， so now we turned the right thing here。😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_136.png)

![](img/d302164e99a9a5422b4bf203e5dc4302_137.png)

And now， I believe it might just work。Oh， look at this。So。We have。A variable R。

 which is a dynamic array。With a data type of type in。Capacity 10， count 5。Enracsize it。

 So there are four bytes each。And here is a dump for them。😔，So， basically， we have。This is the first。

This is the second， and so on and so forth。And we have added our one or 2 or 3 our4 our5。Okay。

 so that works。 But what if we were to add more than 10 to it。



![](img/d302164e99a9a5422b4bf203e5dc4302_139.png)

Something like this。

![](img/d302164e99a9a5422b4bf203e5dc4302_141.png)

What happens then。No， we have a capacity of 40。Coun of 35。And this is the first 32 bys or so。Alright。

 So we have successfully created a very cool dynamic array， which not only stores。😊，Data type。

And calculates its size。 It does a all， also。Print the name of the variable。



![](img/d302164e99a9a5422b4bf203e5dc4302_143.png)

Alright， so I think this is enough for one day， actually。We have covered a lot of ground。

 with the preparations。And next time， we are going to。

Continue on by creating the network sockets for the Uni domain sockets and communication with the user interface。

And I hope you like this episode in this series。 It's gonna be a very cool and unique project when you are done。

 so like and subscribe and hit the bell button so you get notified when I release the next episode in this series。

😔。

![](img/d302164e99a9a5422b4bf203e5dc4302_145.png)

Thanks for watching。 and thanks for today。

![](img/d302164e99a9a5422b4bf203e5dc4302_147.png)