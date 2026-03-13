# 【EDUCBA】Azure网络基础 ｜ Azure Networking Fundamentals p12 04_02_01_Azure 防火墙 -BV1twFSzNE5z_p12-

![](img/bf063ae74290c1af7fc0da778efd7599_0.png)

Hello， learners in this lesson， we'll be discussing about azure fireball。



![](img/bf063ae74290c1af7fc0da778efd7599_2.png)

Let's first understand what is a firewall。 If you are not aware about it。

 Let's understand what is firewall first。

![](img/bf063ae74290c1af7fc0da778efd7599_4.png)

In the computer world， firewall protects unwanted software from getting into your system。



![](img/bf063ae74290c1af7fc0da778efd7599_6.png)

![](img/bf063ae74290c1af7fc0da778efd7599_7.png)

While you are surfing the Internet， it creates a wall around your system。 And with that wall。

 only legitimate files or sources will be allowed to enter into your system。

 That's what the firewall is。 What is is your firewall。

 as your firewall is stateful firewall as a service。 And it provides you network。

 intelligent network firewall security。 And that is a cloud native firewall。

 And it also provides you built in high availability。 You don't need to create 2，3 firewalls。

 Availability will be there。 Don't have to worry about。😊，Manual availability of your firewalls。

 It has built in high availability。 It works on layer 3 to 7 filtering。

 It provides you is a layer 3 to 7 filtering。 That's what also it provides you。 Also。

 it has one more feature called threat intelligence based filtering。😊。

What is threat intelligence based filtering If you want to alert or you want to deny the traffic from any non malicious I addresses。

 maybe any fully qualified domain name or maybe some URL。 that also it provides you。

 So this is what your asz your firewall is。Let's see。 what are the different rules of azure farwell。

 We have three types of rules here。Any rule。Network rule and application rule。

 What is N rule If you want to allow incoming internet connections by configuring destination network address translation rules。

 that is your N rules。 Second is your network rules。 Network rules。

 if you want to configure the rules that include source addresses， protocols。

 destination ports and destination addresses。 then you need to have network rules。

 Third one is application rules。 If you want to configure fully qualified domain name like ABc dot com w do Google dot com。

 you want to allow or these sort of rules， then from a particular subnet。

 then you need to configure application rules。

![](img/bf063ae74290c1af7fc0da778efd7599_9.png)

![](img/bf063ae74290c1af7fc0da778efd7599_10.png)

I I show you with the help of a diagram because we understood about NSGs as well。

 network security groups。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_12.png)

As your firewall provides you one additional layer as well。 That is a fully managed service as well。

 That is one layer of another security as well。 It works on hub and spoke technology as well。

 So let me show you with the help of an example。 Let's say you have2，3 virtual networks。

 and let's call them spoke network， S P O K T spoke。😊，Network， you can call it。Here at one layer。

 let's say you have this aszure firewall， which is。Fully managed by us your as your。Fre one。

This is your spoke network。 Let's say one traffic is coming from ABC dot com or whatever it is。

 So first of all， it will go to this firewall if the firewall rules， either it is network rules。

 network rule or application rule， whatever it is。 if it is allowing the it will go into the spoke network。

Definitely， you'll be having with these V Ms。 you'll be having NS SGs as well。

 If it is allowed from NSG as well， then it will be able to enter into your machines， right。

 then you'll be able to hit it。 So two layer of security somehowhow。

 That's how also it will provide you。 Thank you very much。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_14.png)

![](img/bf063ae74290c1af7fc0da778efd7599_15.png)

![](img/bf063ae74290c1af7fc0da778efd7599_16.png)

Hello， learners in this lesson， will see usz your firewall in action。😊。

Some of the part I have done it already for this particular video because it takes time to actually deploy all those things。

 So some part have already created。😊，What I'm about to do here。

 I'm about to give you walk through off as your firewall and the users of。 What I've done already。

 Firstst of all， I have created one virtual network。



![](img/bf063ae74290c1af7fc0da778efd7599_18.png)

If you see， this is the virtual network I have created。



![](img/bf063ae74290c1af7fc0da778efd7599_20.png)

As of now， you might know like how to create the virtual network。 That's why Also。

 I'm not showing you。 I've created one virtual network with this settings，10 dot 0 dot 0 dot 0。

 slash 16。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_22.png)

If you notice here one more thing， the DNS servers， which we use in virtual network， mostly。

 these are the asure provided DNS server I'm using。 If you want to use external DNS servers as well。

 that also you can do。

![](img/bf063ae74290c1af7fc0da778efd7599_24.png)

After that， inside this virtual network， if I show you here。

 there are two sub networks I have created。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_26.png)

So let it open Two subjects I have created。

![](img/bf063ae74290c1af7fc0da778efd7599_28.png)

One name is Azure firewall Subnet and another one is workload submitnet in Azure firewall Subnet。

 I'll deploy my Azure firewall， and in workload subnet， I'll be creating one virtual machine。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_30.png)

The address space I have taken for Azure farwell submit is 10 dot0 dot 1 dot 0 slash 26 and for workload submit 10 dot0 do2 do 0 slash 24。

😊。

![](img/bf063ae74290c1af7fc0da778efd7599_32.png)

![](img/bf063ae74290c1af7fc0da778efd7599_33.png)

In the workload subject， I have deployed one virtual machine。 Let me show you this as well。

 This is my virtual machine， so I have deployed this virtual machine inside my workload subject。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_35.png)

![](img/bf063ae74290c1af7fc0da778efd7599_36.png)

As you can see here， this is my virtual machine。 One more thing I would like to show here by default in this virtual network subnet。

😊，I haven't addeded any inbound porch。 Nothing is allowed in here。 If I show you its networking。

That I have disabled。 Anything inbound is disabled here。 These are only the default rules。

 Even RDP is not allowed from here。 That's what I have blocked。



![](img/bf063ae74290c1af7fc0da778efd7599_38.png)

![](img/bf063ae74290c1af7fc0da778efd7599_39.png)

That's what I have done。 This is my virtual machine。Apart from that。



![](img/bf063ae74290c1af7fc0da778efd7599_41.png)

I have created。One firewall， that setting， I'll show you what I have done。

 this1 I have already created。 But if you want to create a new one。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_43.png)

![](img/bf063ae74290c1af7fc0da778efd7599_44.png)

What settings I have done， I have selected the subscription， same resource group。

 which I have used for my virtual networks and all。 some name I have given。



![](img/bf063ae74290c1af7fc0da778efd7599_46.png)

From here， I have selected standard plan。

![](img/bf063ae74290c1af7fc0da778efd7599_48.png)

From here， standard plan， I have selected the same region availability zone。 I have put none only。



![](img/bf063ae74290c1af7fc0da778efd7599_50.png)

From here， I used the classic。Option to select this one。



![](img/bf063ae74290c1af7fc0da778efd7599_52.png)

I have selected the existing virtual network， which it is showing here VNe one and I have added one IP address public IP address for this farewell as well and I simply created it with those settings only so these are the settings I just want to show you again name anything you can have standard I have used and I have used classic option to do that。

😊。

![](img/bf063ae74290c1af7fc0da778efd7599_54.png)

![](img/bf063ae74290c1af7fc0da778efd7599_55.png)

Existing firewall and one I P address。 I have you。

![](img/bf063ae74290c1af7fc0da778efd7599_57.png)

That's how it got。Created。This is the test farwall。 that's the name I have added。 Also。

 one more thing I have done。 I have created one route table。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_59.png)

Because as you can see， I just want every traffic， either a trend coming or outgoing。

 It should go via this spiralwall。 That's what I want。 I need to change the routing as well。

 That's what I have done。 I have created one route table。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_61.png)

![](img/bf063ae74290c1af7fc0da778efd7599_62.png)

![](img/bf063ae74290c1af7fc0da778efd7599_63.png)

And this route table， I have associated to workload submit the second one， not the firewall submit。

 but the second one， the workload submit。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_65.png)

For that， I have added one route here， as you can see here if。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_67.png)

Address prefixes， if I show you here。Next for I P address， I have entered。

 this is the farwell's private IP address I have put。Your prefixes any prefix for Internet。

 I have added this one。 Next stop type， I have entered virtual plans and next for I P addresses。

 this one， the private I address of your。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_69.png)

Fireable。 So as let me show you here as well。

![](img/bf063ae74290c1af7fc0da778efd7599_71.png)

Firewall， if I go。This is my firewall。And。

![](img/bf063ae74290c1af7fc0da778efd7599_73.png)

This is the par Pri 10。0。 1。4。

![](img/bf063ae74290c1af7fc0da778efd7599_75.png)

This is what I have entered here。 If traffic， if address prefix is whatever any traffic internet it is。

 then it should go via this next four pipe P addresses this 10 do0 do1 dot4。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_77.png)

![](img/bf063ae74290c1af7fc0da778efd7599_78.png)

The type I have added us virtual appliance。

![](img/bf063ae74290c1af7fc0da778efd7599_80.png)

Then if I go to firewall， let me show you what rules I have entered here。

 what I have allowed and what I have denied。 will continue remaining part of the topic in the next video。

 Thank you。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_82.png)

Hello， learners。Now let's explore the next topic in our discussion。If you go here， rules classic。

Like we discuss， we have three types of rules， application rule， network rule and NAT rules。

 So if I show you application rule first， that's what I have added。If I edit this。

 that's how you add a rule as well。 Let me show you。



![](img/bf063ae74290c1af7fc0da778efd7599_84.png)

Name any name you can have priority number I have added 200 allow。

 So what I have allowed here in application rule， I want to allow from my virtual machine。

 Google dot com。 That's what I want to allow。 name。

 allow Google type is I P address sources 10 dot 0 dot 2 dot0 slash 24。

 That is the address range of your sub network。 So from that sub network。



![](img/bf063ae74290c1af7fc0da778efd7599_86.png)

![](img/bf063ae74290c1af7fc0da778efd7599_87.png)

If you are hitting。Definitely from the machine only you' will be hitting Google dot com。

 that is allowed。 S T P， as well as S T P， S。 I have allowed。

 This is what your application rule I have said。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_89.png)

Second rule I have set is network rule。 if I show you this rule as well here what I'm doing here。

 I am allowing DNS servers。 Okay， so I'm basically using external DNS servers for that。

 you can use virtual networks as well， but I'm using particularly。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_91.png)

External DN S， so I'll do this setting to the network interface of your virtual machine as well。

 that also I'll show you， But I'm doing a loud DNS for UDP protocol that is source is of sub network of your workload sub。

😊。

![](img/bf063ae74290c1af7fc0da778efd7599_93.png)

![](img/bf063ae74290c1af7fc0da778efd7599_94.png)

And this is what I'm allowing。2，0，9 dot 2，4，4 dot 0 dot 3 and dot 0 dot 4。

 These are the external DN S servers。Po destination port 53。 That is also I am allowing third rule。

 which I have added is N T rule。😊，So if you see here， if you go to RDP， RDP as well。

 I am allowing from here。

![](img/bf063ae74290c1af7fc0da778efd7599_96.png)

If you see here what I have done so that says natural connection parity is 200。

 So what I'm doing here name is IDP protocol is TCP from any source。

 if destination is this is the public IP address of your firewall if from any source if traffic is coming to your firewall on port 3。

38，9， then it should be transferred to your virtual machine。 That is the IP of your virtual machine。

 That's what I'm allowing from any source。To your virtual machine 3，3，8，9。 then that is also allowed。

 Thats what I have done。

![](img/bf063ae74290c1af7fc0da778efd7599_98.png)

Also， one more thing I have done， if I show you。What settings I have done to my network interface card of the virtual machine。



![](img/bf063ae74290c1af7fc0da778efd7599_100.png)

So that's what I have done if I go to various N I see， this is your work triple line。



![](img/bf063ae74290c1af7fc0da778efd7599_102.png)

I have added custom DNS server here。 I went here。So I went to DNANS servers。

 So if I go to custom DNANS servers。 So these are the ones which I have added external which I was showing。

 which settings I have given to your as your firewall。 So these are the same I。

 external DNAN servers also Im using。

![](img/bf063ae74290c1af7fc0da778efd7599_104.png)

![](img/bf063ae74290c1af7fc0da778efd7599_105.png)

Now I need to test whether it's working or not。So if I go to virtual machines。

This is my virtual machine。 Me to connect to this。Virtual machine。 So the public I P， I P。

 I be using of firewalls。 So firewall， public I P I be using。



![](img/bf063ae74290c1af7fc0da778efd7599_107.png)

I go to firewalls。And the credentials are use of the Vm。So this is my5 one。

And if you go to public IP configuration， this is the public IP。😊，This is my RP file。

 which I have downloaded earlier， and I need to connect to this IP because I'm using the public I of the fire。

 Let's connect with that。😊。

![](img/bf063ae74290c1af7fc0da778efd7599_109.png)

I need to enter the password。 This is the username I have added。 Now I need to enter the password。😊。

Yes。

![](img/bf063ae74290c1af7fc0da778efd7599_111.png)

What I have allowed here， that is Google dot com。 So if I hit Google dot com。



![](img/bf063ae74290c1af7fc0da778efd7599_113.png)

This warning， it will show。Cls this。I'm able to see Google dot com， because that is what is allowed。

 If I see Microsoft dot com that fully qualified domain name， we haven't added。😊。



![](img/bf063ae74290c1af7fc0da778efd7599_115.png)

If I try to hit that， yes， do that as well。This is denied。That's the use of as your firework。

 Thank you very much。

![](img/bf063ae74290c1af7fc0da778efd7599_117.png)