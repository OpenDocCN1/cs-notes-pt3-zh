# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p83 38_加密消息交换.zh_en -BV1TFLZzYE26_p83-

![](img/db7ae54b65a470959951006c73def207_0.png)

Hi guys， On this video， I want to tell you a little bit about a protocol called Diffy Helman Exchange。

 but I want to preface it with just a few comments about the cryptographic community and cryptography in general。

 And I'll bet a lot of you probably have some interest in this。 This is fun。

 Like if you like doing computer science。 if you like protocols you like the distributed systems。

 then you probably like cryptographic application protocols。 They're fun。

 like little puzzles on how you make certain properties be respected as different entities are interacting。

 the guys that we've been talking about here with Diffy Marty Heman， wonderful people。

 if you met with Diffy， you would like him immediately， he sort of looks the part of cryptgrapher。

 he's just in my mind， one of the few heroes that we have in cybersecurity。

 Did O Marty Heman and did other the guys from Mit who did RSI。 you know。

 we live in a time right now。 when sometimes it's not so easy to find heroes， like sports。

years maybe there's some it always seems like when they get into contract negotiations。

 they don't seem like such great heroes anymore。 Is asking for more money or our political figures a lot of times let us all down I don't have to go into too much detail on that but in technology people like with diiffy and others they really are heroes these are people who are true to their discipline。

 they're smart， they've made contributions to change the world， they're very modest。

 if you ran into any of them at the mall or something or at the store or at up conferenceference。

 they're not wearing blinking lights， you know calling attracting attention to themselves they're not that kind of person so as you some of the younger people here as you get interested in cryptography。

 there are a lot of really wonderful role models that you can study their history， read about them。

 look them up on the internet， see what kinds of careers they've had that led them to making contribution。

Such as the sort of thing that we're looking at from Whit Diffy and Martyhelmman。

 Now let's get into it with them。 We said earlier that we wanted it to be the case that we have both secrecy and authentication in a given protocol。

 We knew that if I took a message am and I encrypt it with your public key。

 then I can get it to you secretly。 If I take a message and I encrypt it with my secret key。

 I can authenticate。But I couldn't do both。 Well， diiffy and Heman went。Just do both。

I know it sounds so obvious。But if only it were so obvious。

 these amazing contributions seem so obvious afterwards， but before not so much。

 So here's what they said。 They said the first thing we want you to do， take the message and sign it。

😊，Crypt it with your secret key。 Then whatever you come up with and cr that with the public key。

 the recipient， and then slep it over to the recipient。 The recipient then gets it。

 uses its secret key to encryptpt what it will then get as payload as something that requires your public key to decrypt。

And then the result is the message。So doing it twice。Gives you secrecy， gives you authentication。

But guess what？It still doesn't solve something like this alone was not enough。

To kind of create the mystery and the legend that's Dffy and Heman。

The problem we have is it still doesn't preserve the efficiency of conventional cryptography。

 Do you follow， like even with all this work， if I can get a message I across and I can get both secrecy and authentication。

 the kind of cryptography we were fooling around with at the time required， you know。

 multiplying prime numbers together， the RSA implementation in doing all these complex numbers like the RSA algorithm involves two gigantic primes like 100 decimal digits long that you multiply together。

And that's your substantially your public key。 Comps in the 70s couldn't do that for a big giant file。

 If the message M is a big long document， then what。

 you see how block cipher worked very nicely blocked by block。

 this thing just uses a unquote message。 How are we going to fix all of this？ So stick with us。

 because in our next video， I'm going to explain that。

 But just sort of as an additional consideration as you're thinking this through。

 I want you to ponder the following question。 If this is so obvious， why didn't it pop up earlier。

 Like this is the mid70s， Why wasn't it the case in the 20s，30s，40s or even earlier in the 1800s。

 Why didn't people come up with this idea。 It's an interesting thought to ponder Because until diffy and Helman had made this public for thousands of years。

 People figured that the only way you could really effectively exchange a secret and do it in an authenticated way is with a key distribution center was one of the basic presumptions of human。

😊，communicationication for thousands of years。1970s they figure it out is it possible could have come up sooner and we'll get to that as well。

 So we'll see in the next video and we'll look at how diiffy and Helman solved this problem resulting in their winning of a touring award。

 which is the greatest prize in computer science， so I'll see in the next one。



![](img/db7ae54b65a470959951006c73def207_2.png)