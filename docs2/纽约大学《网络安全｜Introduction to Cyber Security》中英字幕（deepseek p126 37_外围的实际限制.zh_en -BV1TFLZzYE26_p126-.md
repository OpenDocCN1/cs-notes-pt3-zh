# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p126 37_外围的实际限制.zh_en -BV1TFLZzYE26_p126-

![](img/a8f21c20cbe6d5b031fa8d867fa1980f_0.png)

Hi， everyone。 This Ze Ammarosso。 And I want to show you in this video kind of an interesting progression in the design and representation of an enterprise perimeter。

 Now， if you work in a business。 you probably have to deal with something called an auditor。

 It's a third party individual。 may they work in your company but it somebody's going to come take a look at what you're doing。

 provide oversight and make sure that， for example。

 you have the right controls in place to protect the business。

 turns out that that auditor is going to demand evidence that you're protecting things properly。

 And what every cybersecurity team does first， is they show a picture to the auditor that looks more or less like we've got on the screen here。

 It says enterprise perimeter， say perceived。 You can see that it's disallowing external access。

 This is the intention of every enterprise security team to have an enterprise perimeter that。😊。

littlettle malicious intruders that want to come in off the enterprise。 they bounce off。

 It's kind of a funny picture that we show theyre like almost like a little electron。

 And if we show activity going on inside the company。

 like trusted internal enterprise access and we' showing traveral and it's all internal。

 you can see that the clear circles represent trusted users in the enterprise and the filled in circle on the outside bounces off。

 I don't trust that this is what you show your auditor。

 This is what we all would like to be the case。 But there is a gigantic problem。

 something that I think we've alluded to in other videos if you've been with us for other videos。

 and it's something that can be characterized by this drawing。

 The reality I that a modern perimeter has all sorts of breaks in it。

 let's go through them one at a time。 So email you're going to have to have an email gateway。

 I mean you can。😊，operate in today's environment without allowing email into your users。

 So anybody anywhere， for the most part， can send an email to pretty much anybody in your company。

 That's the model that businesses and all of us use。

 So you're going to have to put a little break in the perimeter。 you're gonna have to say， well。

 you know， in a firewall or in a gateway of its email。 I got to let it in。

 So that's one place where the electrons are not bouncing off。 Second。

 you might have outsourced vendors。 you know， you might have decided that the help desk in your company is best served in some country。

 Maybe a country where you live。 you may actually work in an outsourced center。

 and you have the experience that for your client。 You are logging in their network， right。

 you're connecting in。 They're looking at the network you're sitting on。

 looking at the source Ip address。 and they've got a rule that's allowing your source I address to hit。

 They say identity system that's going to ask you for a password。 but that's。the enterprise。

 just the fact that you have the right source IP， gets your packets in。

 and then they're going to ask you who are you might maybe a password。

 might be too fact or whatever it is that you're used to doing if you work in that environment。

 but again it's a break in the peri， packets are coming in。Third possibility， remote access。

 I remember years ago。 We used to assume that maybe 10 to 12% of a typical company might be working from home at any given time。

 How crazy was that。 This must been 20 years ago。 Now。

 you have to assume that it could be 100% of the company trying to remotely access your resources on your network from home。

 weekends。 It seems like everybody works on weekends now anyway。

 or from Starbucks or an airports or at home or at night or whatever， sometimes even from the office。

 you might be sitting in your office。 And instead of connecting to the land。

 you might be using remote access into the network just because it's more convenient。

 but that also is a break in your perimeter。 It's not electrons bouncing off。 Another one is Web。

 Look， if you have a web server that's hosted in a data center and you want your customers to hit your Web server。

 Maybe you do commerce。 They're coming in their browsers are pointing in their get。I mean。

 let's face it， How about partners， you have any partners that you're dealing with。

 you might have a venture you're working on or maybe law firm that you work with where you're exchanging different types of things you might give them direct tag you get the idea and then there's a bunch of unknown gateways that you may not even know about look the reality is that if you accept that this is really the way a business operates than this picture is really how your perimeter is set up it's a much more accurate representation of a typical enterprise programs all cuts in it。

 little holes in it。follow so we started by saying I had this beautiful oval electron bouncing off of it。

 and I showed my auditor that， and I was hoping that everything would be just great。 The reality。

 however， is because I have to do so many different types of things in an enterprise。

 I need to support so many different types of services and capabilities in remote access and business conditions that I really end up with something that looks like this。

 And I think that may help you understand why typical enterprise business。😊。

Is being subjected to some pretty significant and successful cyber attacks。

 If you've got holes all over the place， you shouldn't be surprised when somebody's breaking into your business。

 Now to kind of test your understanding。 A little quiz here。

 You can make the case for a couple of them。 I mean。

 certainly anything is better with more management。

 but I think the best answer here is fewer services。 So a。

 the reason I think that's 1 I want you to focus on is that the idea is we'd like to simplify the kinds of things we're protecting with a perimeter。

's nothing wrong with a perimeter concept， it's when there's so much going on on the inside that I have to open all these doors that I actually expose everybody to these problems。

 It's like， I get a problem way up here in the top corner and down here in the bottom opposite corner。

 I feel the effect， because I've got lateral traversal。 I have trust between the things。

or inside a perimeter， you'd like to think it would make more sense if there' are different workloads to break them up。

 I've given you the image in other videos as we've talked together。Of elephants and mosquitoes。

 so if a perimeter is a big elephant and I have a gun and I want to shoot the elephant， boom。

 I shoot it and it falls down。But if I break the elephant up into a lot of little mosquitoes and I give you a gun and say kill the mosquitoes。

 you can't kill the mosquitoes with one gun。 right。

 So this idea of a big perimeter having all these problems should give a little bit of a hint that maybe the correct approach here is to think about distributing your systems and breaking systems up into smaller components。

 that's going to be a more powerful approach to doing cybersecurity。 We'll see in the next video。



![](img/a8f21c20cbe6d5b031fa8d867fa1980f_2.png)