# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p161 24_区块链第1部分.zh_en -BV1TFLZzYE26_p161-

![](img/fd6a27fc36aa0023bdc6321cc29fa9ec_0.png)

Hi folks Ed Amarosso here， and in this video I want to introduce in sort of a part one video。

 the concept of blockchain in the context of cybersecurity。

 blockchainlock has a lot of different applications。

 but for us as we learn cybersecurity willll see that one of its usages involves detection if something's been changed。

And detection a very clever way that makes it almost impossible to sort of erase the footprint of whether something really has been changed。

 So let's start with the idea that when we're hashing we generally hash on something abstractly。

 we call a message but in practice it's not going to be a message it's going to be something and and say we work at a bank or when're a financial services organization。

 then the kinds of things we want to be producing authenticity on by hashing would be like a financial record or data that describe some financial transaction。

 It could be one person giving a dollar to another and we sort of have a record of that and we'd like to hash that we could hash it directly。

 meaning we take that message and we could sort of run a function on it and produce whatever comes out。

 we generally refer abstractly to that as lambmbda， it would be whatever it is。

 it would be a string of ones whatever ones of zeros， but if we did it in heck。

Then it'd be a long hexadeadecimal number with ones and twos and nines and Abelbaker。

 Charlie's and foxes and sixes and so on。 big long number Now if we decided that we wanted the output to be something that was fixed was a fixed pattern and in kind of the context of the Bitcoinco community So's been some agreement that a typical sort of pattern that we would use for blockchain output as we hash would be a hash value that starts with four zeros。

 and you say why that what's just a convention could it have been four1s yes。

 could have been 46 is yes could be whatever， but the convention is four zeros So now what we do is we introduce along with that record。

 something that we refer to in cryptography as a nos So put the nos and we put the data together。

 I'm going to encrypt the two of them using a hash function。

 produce a lambda and it would be some number and I look at。

And it doesn't have four zeros and I go boy， I wish it had four zeros so I tried again and I tried again and I tried again and eventually I get a number with a non selection that gives me four zeros and we refer to that as kind of being mined now if everything stays the way it does we're in good shape you know we've got a record that has ance a non value that combined with the data record produces a hash value that has four zeros now if somebody comes along and wants to change a record like maybe change $1 to $4 million for whatever reason the whole thing goes all out of whack right you've changed the record you've changed the data and now the no that you'd selected with the data record。

 produce a hash value doesn doesn't have four zeros anymore。So that's not going to stand。

 that's a clear indicator that you haven't in some sense mined or validated the record。

 so what would you have to do now？Well。You start spinning the nos again。

 try a bunch of different Nos values， try， try， try and you're getting all these outputs。

 and then finally you get a hash value that has four zeros， but probably in fact。

 not probably definitely a different set of numbers as the hash value than you had before。

 Now it's valid in sense。That there's four zeros followed by some pattern。

 but it's different than it was before。So while we can acknowledge that we've gone back and we've changed the nos to make things in some sense。

 valid， we have a very clear record。 if we kept track of what was there before。

 And the way you might keep track is through multiple distributed copies of this blockchain。

 So if I have 10 of them。 and I'm watching all these things together。

 And somebody changes one of them， then the other guys are going to know something's funny。

 even if I go in and clean things up by remindmining the likelihood of you getting exactly the same。

Hash value unchanged record is a property of the hash function。

 The hash function is designed specifically for that not to be the case or for the likelihood of that to be so unlikely that you just don't have to worry about it as you in your study cryptography。

 you know how how that sort of thing is achieved through proper modern cryptographic algorithmic design。

 So so it's kind of a cool concept for those of us in cyber， we look at this。

 we say this is incredible really gives us an opportunity to really provide a footprint of whether somebody's tampered with data which is one of the primary threats we see in things like financial services somebody coming in wanting to change account balances。

 wanting to change transaction records kind of whatever you wouldn't want that to be the case and this idea of producing a hash with an o through a fixed。

Value where the value has a pattern that we predetermine and make sure that we're preserving through the validity check is really。

 really kind of cool。 It's one of the reasons why people get so excited about blockchain is base。

 Now I said at the beginning of this video。 This is a part one。

 What we'll do in a subsequent video is we'll look a little bit at how the second part of that word blockchain kind of comes into it and how you put things together in a way that's going to provide an even greater set of of evidence。

 greater confidence that when records are changed， it's very unlikely that the perpetrator is going to get away with it。

 So we'll see in a subsequent video。😊。

![](img/fd6a27fc36aa0023bdc6321cc29fa9ec_2.png)

![](img/fd6a27fc36aa0023bdc6321cc29fa9ec_3.png)