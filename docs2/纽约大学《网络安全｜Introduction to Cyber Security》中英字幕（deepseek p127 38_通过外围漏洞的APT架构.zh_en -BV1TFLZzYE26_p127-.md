# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p127 38_通过外围漏洞的APT架构.zh_en -BV1TFLZzYE26_p127-

![](img/524a863faf910b8fb6c200ea7c5e3955_0.png)

Hi， everybody at Emmarosso here。 And in this video。

 I want to dig into and highlight the way an advance persistent threat or AP works in the context of the perimeter model that we've shown you that has all these breaks in it because we've got so many different types of services that a typical enterprise needs to support to operate。

 So let's put a little diagram here that shows the different steps or stages of an AP。

 and really the mistakes that are made at each stage。

 So the first thing is that most companies except email。 and it can kind of come from wherever。

 let me give you a little example。 embedded in your email is something called a from line So you can see who sent you the email where did it come from。

 And it's usually something that is at the application level。

 You know you put the information there about who this thing is coming from。

 The problem is that that's not typically connected to the under。😊，lying infrastructure。

 meaning if I say I'm sending email to you from big giantcompany co and it comes across and the problem is that the mail server for big giant company co is 192。

1。2。3， but the email is actually being sent from some other crazy IP address。

 you wouldn't know it in the email protocol because you don't check the email protocol does not look for that kind of thing Now turns out there's an interesting standard called Dmar。

That does sort of connect the two things together。 It's kind of an interesting protocol。

 probably worth maybe as a separate study。 if you want to go and dig a little bit deeper， you can。

 It's not really all that fundamental to the discussion here。

 But the point is that kind of sloppy handling of email。

 maybe not filtering email for malicious attachments， not doing Dmar。

 which would connect the IP address of a sending email server to the from information。

 It's kind of cool。 that Dmar would actually check to make sure， hey。

 here's the IP address it should be coming from。 And everybody has to sort of keep track of that。

 So that's mistake1 of sloppy email handling。 mistake 2。 somebody clicks on the email。

Why do they click Because you're probably being spearfish。

 They sent you something that's intended to make you click。

 I want you to you interested in what's coming through。 You see some enticing content。

 something that you're interested in。 How in the world would they figure out what you're interested in。

 Well， welcome to social media，'s not that difficult to do a little research on somebody who works like in the marketing department of a company。

 See that they're interested in water skiing or something。 And then I send you an email saying， hey。

 look at all this interesting water skiing equipment。 click on these links for free coupons。

 and you click， and the malware comes in。 that's fishing。

 So second mistake is somebody clicks without really knowing what it is that they're doing and doing it in an unsafe environment。

 The third mistake is that we set up an environment we've got trust across an enterprise。

 meaning if I connect to this computer Well， then I can probably see all these others。

 I just trust everything on。Enterprise think about where you may work or the school you're in the systems that are embedded in your network。

 your enterprise probably all in line and don't have firewalls between them。

 and if you connect onto the same network you can probably see other students or other workers or whatever So that's the next mistake a very easy lateral traversal so if somebody's clicked on something gets malware the malware is probably a remote access tool that lets a third party a malicious intruder log on that system now they've got control of that system。

Belonging to the person in marketing who clicked Now from there， they can laterally traverse。 again。

 it's this idea of a big perimeter and everybody can kind of go wherever they want to go。

 They go wherever they want to go and they connect， say to some records management tool。

 That's a third mistake。 The fourth is that outbound Internet access。

Is very controversial in a lot of companies。 Most people want to be able to click on any URL that they'd like to。

 Now， within reason， you know， a typical company is going to have acceptable use policies。

 that It want you going to gambling or inappropriate sites unless maybe a news organization and you really need to be going there。

 But for the most part， there'll be a thin swath of sites that a company would consider inappropriate。

 And then everything else would be allowed。 And the problem with that is that if there are malware drop sites or there's sites where I'm going to exfil trade out to as the bad guy。

 And you're not really caring when some system in your network wants to connect to place on the Internet you've never heard of and don't know anything about。

 then that's the next mistake。 the fourth mistake。 we call that web egress being allowed essentially to something we call an uncategorized website Now。

 a lot of tools exist that will sit on an outbound。

Proxy okay so probably be a forward proxy protecting all the clients in the enterprise。

 And before those clients can go out to internet services。

 it's going to hit the proxy and the proxy might keep track of a list of so-called categorized sites。

 meaning your vendor is keeping track and it's a site that we're pretty comfortable with。

 you go to it if it's an uncategorized site you probably get blocked and interrogated and there'd be a question like what are you doing and that's where most information gets exfiltrated。

 It gets exfiltrated to some dynamic site on the Internet that's probably uncategorized。

 and I say probably because it could be the case that a known categorized website has been compromised and the malware is going to exfiltrate to that。

 So it's not perfect， but it'd be a big mistake， I think not to be doing some sort of outbound or egress filtering on web connectivity。

So you put all these mistakes together。It's no big surprise that so many companies are experiencing advanced persistent threats。

 It shouldn't be a surprise to you。 Certainly not a surprise to me。

 and now that you have some understanding， we in the cybersecurity community really need to do some things about it。

 And that's sort of the essence or the challenge that we have in modern cyber。

 Hope this has been useful for you。 Talk the end the next one。



![](img/524a863faf910b8fb6c200ea7c5e3955_2.png)

![](img/524a863faf910b8fb6c200ea7c5e3955_3.png)