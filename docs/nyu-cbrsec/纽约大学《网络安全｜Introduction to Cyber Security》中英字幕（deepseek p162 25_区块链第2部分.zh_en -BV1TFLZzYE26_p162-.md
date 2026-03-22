# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p162 25_区块链第2部分.zh_en -BV1TFLZzYE26_p162-

![](img/a5d46e29f157154e0df2dbe5969e89e3_0.png)

Hi everyone at Emmarosso here and in this video， we're gonna to call this kind of part two of our discussion in and round blockchain。

 Now let's go back in the 1970s。 we had this problem with block ciphers block encryption were a block of bits say 64 bits in the data encryption standard or similar algorithms。

 you had 64 bits you'd encrypt it and you get got 64 bit output， then 64 bits you'd encrypt it。

 64 bit output and it wasn't such a great idea because you could potentially signal Alice doing that The Bob could signal Eve by fixing the 64 B patterns like 64 zeros encrypts to something then 64 zeros encrypts to something then 641s encrypts to something different and so on and it creates a covert channel So the designers at the time had come up with this idea that maybe by linking the cryptography and subsequent blocks you could close the covert。

Channel and that was the main reason you did it sort of be at the outset。

 if we turn the clock back 40 years or so， we'd be talking about blockchain。

 cipher blocking we called it then CBC really is a way of tightening that channel and most of the cryppttographers at the time would have told you that's kind of an obscure aspect of cryptographic design wouldn't have been this thing that you'd be talking about on television and reading about in articles they would be astounded if they knew that some number of decades later。

 we all came to this amazing conclusion， the chaining was useful to our society it would be astounded。

 but here's how kind of out works。 So let's start with the concept that we introduced introduced in part one of our blockchain discussion where we have a data record again will assume that it's financial and somebodys giving money to someone else and we're going to have a and in the previous video。

Remember we said the Nos and the data record we didn't encrypt to produce the hash value and we decided we wanted that to start with four zeros Well now to cover the chaining case which we'll get to in a second what we're going to do is add yet another component to the hash and keep in mind I'm just composing a bunch of zeros and ones so when I take a nos it it's a number when I take the data record that's a number and I'm going to add another number which I'm going to call in some sense the previous hash。

And I'm going to take those three components composed。

 hash the thing and produce the value that as I flip the Nos again has to start with four zeros。

 Okay now the problem that you have when you ever design an algorithm that reaches back to the previous one is that once you're rolling in your rolling。

 there's no problem。 if I'm looking at a train rolling by and I point to a train car。

 and I say what was the previous one。 you go to that one the one that came before。

 But the problem is the first one never has a previous one So what we have in blocking is the idea of the concept of a Genis block。

 which we just sort of make up， it's another nos， it's something we make up as if it were the hash of a previous value。

 but if we have hashed a previous value we don't have it hence Genesis。

 So in this first example we've gots， we have data and we have this Genesis previous block。

 I'm going to go ahead and。😊，In the knots， do it over and over and over again。

 keep passion until w I get a value and output that has the four zeros and then some arbitrary pattern afterwards and I'm happy。

 I go okay good， I call this in some sense a mind block I'm good now another record comes along somebody's doing some financial thing you know it's somebody else transferring money to somebody else but what I'm going to do now。

I instead of sort of doing the hash of that in a contextfr manner。

 I'm going to do it in a context sensitive manner by taking the output。

 that hash that I produced with the previous block。

 and I'm going to use that now as the previous value in the new hash。So now I've got a new nos。

 I've got the new data record and I've got the previous value from the previous one I did put those things together。

 composeose them， take a hash of that， spin the nos。

 keep going and eventually I get four zeros and I stop it and I go we're good so now I've got two records and they both have been mined in a sense we're really good shape they both have the right output and they're chain together meaning if I make changes it could have unusual consequences。

 which we'll get two let's do another a third record comes along so you know doing some financial thing I do the same thing。

 I take the output the hash of the previous block that gets used in the computation for the present block。

 I mind using them spinning the nos I finally get some sort of output I'm totally psych。

 this looks great， I've got three records here I've got three outputs we're in good shape。

 I can do a fourth one fourth one you see you can chain。In this manner，That makes sense。

 So four blocks。A chain sort of a set of records here。

 and it's indicative of that early conceptualization， the CBC that we had from IBM in the 1970s。

 and yes， it certainly closes covert channels if that was something you were worried about。

 but the reason this is cool is because watch。If I go back， let's I'm a hacker。

 and I go back to the second block， the second transaction that we talked about in our progression。

 and I change some value of financial valueating a bigger number。 Well。

 what happens is it messes everything up in a subsequent manner， meaning。

By changing the value of the record， I've now messed up the hash that corresponds to that record。

 The nos is the same。 The previous block is the same。 The data record has changed。 So now。

 as that gets recomputd， to continual recompute on change。

Now what now I've got Ive got a problem and it cascades out because now that I've changed the hash value that feeds the next record。

 the hash value is different Now it's been changed it'll get recomputed Now that is no longer valid and on and on and on。

 have something colossally lucky case where something does happen to be zero is very unlikely。

 you pretty much have a mess。 So what do I have to do now， I have to go back to blocklock2 again。

 if I'm the bad guy， I have to go back。And I have to say， all right。 I want to leave the record。

 I want the more money there。 So what do I do， I go through， and I constantly change the nos。

 changing， changing， eventually get to a bunch of zeros，4 zeros， but a new pattern， okay。

 and that new pattern now feeds the next record， which will again， not be valid。

 it's you have to go in the next record and fix that one。

 I've got to go through and do the the non spinning the nos until I get through。 now， keep mind。

 this is taking some time， right， And while you're doing this。

The whole chain might be continually growing。 Let's say the chain has a bazillion entries and you' going way back to half a bazillion。

 You made a change。 You now have to go half a bazillion out to catch up。

 and it might still be growing at the point big problem there。 And then finally。

 you know might eventually catch up to those four blocks。

 But do you see how the amount of work here to do this。

 could be set up such that the likelihood of you being able to catch up is low。

 And also I am changing that hash chain。 There's no question that the output values here from a hashing perspective are going to be different。

 And you know， we don't have a lot of time here in these videos。

 but as you go often And if you investigate and learn more about blockchain。 I hope you do。

 I hope to sort of jog your interest and sort of like introduction to a topic that's very rich。

 you'll see that architecturally the way multiple blockchains can be set up is that they。

 in some sense can be providing validation on each other。😊，When something changes very， very cool。

 very deep concept and something that I think has been an interesting contribution to computer security and to computer science now as sort of an individual or as a little individual additional consideration for you to keep in mind as you think about this。

 I want you to think about that concept of an amount of work being， in some sense a safeguard right。

 if you do something bad that the way to recover from your attack so that you don't get caught is you have to do a bunch of work。

And an interesting thing about blockchain is it uses that amount of work as a type of safeguard。

 Think about that。 It's a pretty good idea。 You know that if you're going to do something bad。

 it's not going to be easy for you to recover。 I'm not going to make it easy for you。

 I think that's a good design goal or design concept as we build cybersecurity systems for enterprise for infrastructure and even for your individual PC。

 So I hope this has been a fun introduction to blockchain。

 And I hope it inspires you to go in and dig and learn a little bit more。

 I'll see you in the next video。😊。

![](img/a5d46e29f157154e0df2dbe5969e89e3_2.png)

![](img/a5d46e29f157154e0df2dbe5969e89e3_3.png)