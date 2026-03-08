# 威斯康星大学【中英⚡编程语言与编译器导论｜CS536 2018 Introduction to Programming Languages and Compil p04 P4 -alt -BV1iwMpzfEDc_p4-

Okay， good afternoon。One thing I want to point out is we put out last week's lecture。

 but there was a glitch in the technology so that。

![](img/0b881dd4840d4158a6e8e11a46c4be9a_1.png)

All three segments have the audio part， but only the third segment about last hour is included in the video。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_3.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_4.png)

It was unintentional， just something got disconnected or something ran out of space or whatever。

 So if you see what's there。

![](img/0b881dd4840d4158a6e8e11a46c4be9a_6.png)

The missing video can be made up in part by the audio， but that's the best we can do on that one。

 But our intention is to have video for the entire lecture。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_8.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_9.png)

Would you remind to remember that there'll be dead spots in between because I don't believe the person editing the video is aware of the fact we have breaks and that they essentially have dead space after an hour and after the second hour。

 so in that case just do a fast forward you'll probably just have a fixed screen with no audio and that's just us taking a break。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_11.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_12.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_13.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_14.png)

It's my intention today to cover all the material you'll need for the first homework assignment。

 which is on this slash star star slash comment and also on the second project which is building the scanner so some of you started on that some of you are still working on Project one which is due today so I guess first thing to ask is any outstanding questions on Project one。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_16.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_17.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_18.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_19.png)

Or even maybe some ordinary questions。

![](img/0b881dd4840d4158a6e8e11a46c4be9a_21.png)

So everybody's good to go on that or you don't want to admitm it in public。

 You can also ask between sessions if you have any remaining questions on that。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_23.png)

So let's continue on then to Project 2。 And again， Project 2 is basically learning just how to speak J Le's as it were。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_25.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_26.png)

The thing is that I've talked about regular expressions as being a convenient way to define various kinds of tokens at its sets of strings。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_28.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_29.png)

JLX is a particular tool that takes the regular expression notation。

 makes it into an actual programming language， it's not all Java， partly Java。

 but it's partially just here's a token and here's what I want you to do when you match the token without any responsibility on your power to say。

 well how do you differentiate this token from that other than the fact that the patterns may match or not match the same sequence？



![](img/0b881dd4840d4158a6e8e11a46c4be9a_31.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_32.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_33.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_34.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_35.png)

A little later today， I'll talk about what happens if you have overlaps， which you in fact。

 you will have。

![](img/0b881dd4840d4158a6e8e11a46c4be9a_37.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_38.png)

But even there， the rules are extremely simple， it's that it always matches the longest possible sequence。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_40.png)

So apropo to that， let me just。Go back to my。Document camera。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_42.png)

And I had a question just a moment or two ago that it's not your responsibility in doing the scanner to make the scanner aware of what is valid or invalid at the pser level。

So for example， the question was if you wrote 101 bull。

Looking at that 101 looks like an integer literal and bo looks like the reserve were bull。

 but I didn't put a space between that。 if I put space between it。

 which is a very common thing to do。 then it would in fact be scanned that way。

 But the rule is the scanner keeps scanning until it can't read anymore。

 So 101 is certainly valid but 101 B is this representation of a bit valued or Boolean valued integer literal。

 So B means I'm only allowed to have bits 0 and1， which I have and it would then see the O and say hey。

 they can't go any further。 101 B is valid string literal and not string lit but bit string literal。

And since it's longer than 101， it wins out。If you think about it， you actually have to have that。

 Otherwise simple things like just bo。Could be mis scanned as give me a B as an identifier。

 give me an O as an identifier， another O and an L。

 and you'd hardly ever be able to get anything beyond single character tokens， which you don't want。

 So the rule is keep scanning as long as you can， but do not try to say， okay。

 this would be then scanned as a bit string literal and O OL would be scanned as an identifier。

And it's not the scan responsibility to know that it's probably the case that these two tokens may not appear next to each other。

 The parsel will check that in， in fact， in our language， they are not legal。

 so you get a parsing error saying at this particular stage this token may not follow that token but the scanner doesn't know that the parser has its own set of rules and maybe in some variation of our language that would be allowed。

 so the scanner does its job， it doesn't try to do everybody's job and in most cases when you're doing a program that's really important big programs are done by teams and each individual has responsibility to do this piece or that and you're certainly welcome to talk to other people and say does this make sense or not。

But if it's erroneous， somebody has to take responsibility for it， but in our rules。

 it's not going to be the scanner， it's going to be the parsers's problem to say that this integer literal and this identifier may not be next to each other。

 Typically you have some kind of punctuation or an operator or something。

 but that's up to the parser to say what's legal or not。So in this particular case， that's the rule。

There's a second rule that we'll get to in that you have to have various definitions for reserve words like bull。

 and you have to have a pattern for a general identifier。

A bull could be misconstrued as an identifier and the way we fix that is we have a rule that says if something like this can be scanned two different ways。

 namely as a reserved word bull or as an identifier B WOL， the earlier rule takes precedent。

 So what happens is when you're giving definitions for these tokens at a reserve words。

 you typically put them very early in the listing of all the valid tokens。

Turns out we can also use this trick in doing some fairly simple error handling。

There are certain characters which except when they're maybe a quoted character or a quoted string or prior of a comment。

 are not by themselves valid。 An example of that might be pound sign。

I don't think pound sign by itself is valid， remember there's a double pound sign and all that。

 but just pound sign say surrounded by blanks is illegal。How do we figure that out， Well。

 the way we're going to do it is after we have all the v tokens at the very bottom。

 and I'll show you this in a bit， we'll have something that matches any one single character。

And the notion is if I had a valid single character like a comma。

 it would have its definition earlier on， and therefore would be grabbed up。

 So it's almost like when you get to the lunchroom on Taco Tuesday and you got there late so all the good stuff is gone。

 the guacamole's gone， the sour creams gone I guess maybe you know you still have a few fixings。

 but not what you want and the same thing here， if every one of these rules has a chance to match Mr。

 Po sign。And no one else grabs it， you have something that matches it at the end and typically generates an error message saying error lines。

 so and so columns， so and so， this character is illegal。 And the way you'll handle is， skip it。

 you can't make sense out of you skip it that may or may not be the right thing to do。

 but you certainly wouldnt want to halt an entire a compilation just because one invalid character got entered。

If you're a bad typist like me， sometimes your fingers hit two keys instead of one and you get two for the price of one。

 if you're all excellent typists， you don't have that problem， but these sort of things do exist。

So we'll get to that and the takeaway on this is。Don't try to outsmart the system。Match what's legal。

 identify what's illegal in the way we go。 We'll talk a little bit about how you can handle fancier errors。

 But the more complex the error it is it's hard to even recognize it's an error。 And if so， what。

 in fact， is wrong。 So I'm sure if you've done any other software project。

 is certainly the case in some of the products that E produces。 you have a similar problem in that。

 say a physician or a nurse or somebody else might enter a particular。

bitit of information on how the patient's treatment is to proceed。

 But sometimes if you type something， it's totally illegal。 So you type in， you know， you know。

 how many hours of rest somebody get and you type in pound sign。What does that mean。

 And you could say， well， pound sign is where on the keyboard。 I never have memorized it。

 It's just above a three。 So maybe the person meant a three and they got messed up on the shifting。

 Well， maybe or maybe not。 but it's not your responsibility necessarily to say， did you mean a three。

 Maybe you did。 Maybe you meant something totally different。 But in this particular case。

 if the rule is that's illegal， it's up to you to say it's illegal。 in trivial cases。

 you might be able to do a fix。 but trying to read somebody's mind and guess what they really meant。

 It's kind of difficult。 and particularly in healthcare where it might have a significant difference as to how the treatment proceeds。

 It's not your responsibility to figure out what the nurse or the physician wanted necessarily。

 just your job to say， I expected this。 I didn't find anything legal， please tell me what to do。

So let's go back to。The screen then。And talk a little bit more about what I would want you to do。

 So here's Project 2。 So I mean we're putting Project 1 in the past。



![](img/0b881dd4840d4158a6e8e11a46c4be9a_44.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_45.png)

So I've given you a working scanner， and the scanner only handles a few tokens。

 but it has the entire J like specification for it。

 It actually even has a little bit of error handling on the bottom。

 Apropo to what I spoke about a moment ago。

![](img/0b881dd4840d4158a6e8e11a46c4be9a_47.png)

![](img/0b881dd4840d4158a6e8e11a46c4be9a_48.png)