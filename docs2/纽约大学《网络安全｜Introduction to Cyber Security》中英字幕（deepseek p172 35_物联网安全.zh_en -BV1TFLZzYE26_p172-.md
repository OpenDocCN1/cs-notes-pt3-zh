# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p172 35_物联网安全.zh_en -BV1TFLZzYE26_p172-

![](img/c6c57ca0671a881f17a3ffefd5a93ff3_0.png)

Hi， everyone， Ed' Miroso here， and I want to talk to you a little bit about and provide an introduction to the topic of Internet of things IoT security。

 Now IoT devices are things that for the most part， are connected to networks。

 but are not your computer， not your smartphone，'s kind of everything else。

 might include like a big aircraft engine might be connected in some sense to the public internet or wind turbines out in a field somewhere might be connected to the internet。

 providing telemetry back to a research center or accepting commands。

 say from some control center or connected cars eventually becoming autonomous。

 These are all connected up to networks and all of them to some degree are vulnerable to malicious hacking Now today we count something like 6 billion of these things connected across the Internet here as I speak to you。

 but it might say 2020 the projection is that this。Will growrow dramatically。

 potentially like 20 billion of these things connected up just an aircraft engine alone might have1 thousand different parts that are beaening out information about temperature and position and sensing and velocity and on and on and on So these very interesting problems from perspective of cybersecurity engineer。

 So the first let's kind of go through these things I'll take the first thing is just the Io devices themselves they can be categorized into a couple of different classes。

 first we would say there call them industrial control devices。

 things that have consequence if hacked to some critical infrastructure component tend to use the term industrial control for that but it's not just about industrial control。

 It's more critical infrastructure like a heat pump at a power plant or you know mentioned an aircraft engine or say some really。

Important safety device in a transportation system。 you don't want these things to be hacked。

 You don't want the integrity of them to be affected or modified because people could lose their lives。

 The second class is kind of everything else like we joke about connected refrigerators and entertainment systems and video recorders and children's toys and appliances in our home。

 These are certainly connected to the internet。 they are clearly Iot devices。

 your wearables and other things would be in that category and yeah。

 you don't want them to be hacked， but for the most part。

 would probably not produce some significant consequence。

 and then you can say that there's kind of a category that lives in the middle of those too there's clearly critical infrastructure affecting。

 They're clearly not。 and then things in the middle would be like， for example， medical devices。

 Now you'd say， gosh， you know an insulin pump shouldn't be hacked and kill somebody but it doesn't cascade right。

The most part， if I attack an insulin pump and cause someone to become ill， it's an isolated。

 it's a nefarious， disgusting sort of attack， but it's not the same thing as a power plant that could be attacked and kill all sorts of things so a lot of engineers tend to categorize things in those sort of buckets。

 it's really two buckets and then a combination， industrial control。

 IoT sort of consumer and then things that are in the middle。Now， what are the problems here。

 The first is that none of these devices that exist today。

 legacy versions of these were designed with security in mind。

 They probably have an operating system， but it's probably no good way to patch them。

 No good way to do vulnerability management on them。

 No good way to update systems with security that needs to be done。

 They just want to design like that。 A heat pump in a factory that connects up to the Internet。

 was not designed for cybersecurity。 It just wasn't。 That wasn't the consideration。

 was a mechanical engineer who saw a heat pump could be control with a computer。 Hey。

 let's put it on a network。 Hey， let's build a monitoring system。 Wow。

 I can control the heat pumps from this one room。 not thinking about cyber。

 but thinking about utility。 So the first problem we have an Io security is this issue of legacy。

 The second is a problem of protocol。 So， yes， some of them do run I。

 but a lot of them are running proprietary protocols。 There's one very popular one called Modbus。

There's others that are running analog signaling like voltages， 28 voltage。

 2 volts or zero or things in between， you know turning things on and turning things off and so it's all over the map in terms of the way a control system and a controlled device would operate it's the vigarities of the mechanical engineer who designed it you know will determine the specifics of how the interaction works so putting like a firewall in between them is just not simple。

 it's just not an easy sort of thing to do so you put these things together you know this issue of a dramatic growth of number of devices that themselves are not well protected the systems were not designed for that。

And then you put protocols in place where they're connecting to control systems。

 where the protocols are all over the map。 it becomes extremely difficult to retrofit security onto this So what I think is happening is that we do the best we can with retrofit。

 We build appliances and things in certain cases that do the best they can with existing legacy。

 but a next generation IoT is going to have to be in place over the next 20 years where we design security into them from the beginning。

 we build the devices that are hardened， we make it easy to update and patch them。

 we build native encryption into these things。 we have them natively able to produce or support encrypted protocols that have authentication digital signing all the things you learn about in cybersecurity in the Io infrastructure they're not there now they have to be there。

 So either overlay them or you design them in natively and they've got a bunch of old heat pumps in a factory。

Luck doing something overlaid， you're going to have to rethink that and that's going to be a societal cost that we'll have to just deal with because if we don't then we're going to see some pretty massive attacks on IoT and in a subsequent video I'll give you an example of one。

 but for now I hope this has been a good introduction sort of the landscape of security in the context of IoT and industrial control thanks。



![](img/c6c57ca0671a881f17a3ffefd5a93ff3_2.png)