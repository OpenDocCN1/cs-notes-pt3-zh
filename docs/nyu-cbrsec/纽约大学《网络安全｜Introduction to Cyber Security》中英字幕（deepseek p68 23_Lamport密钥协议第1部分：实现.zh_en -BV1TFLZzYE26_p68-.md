# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p68 23_Lamport密钥协议第1部分：实现.zh_en -BV1TFLZzYE26_p68-

![](img/6d7c33f00a9dc74a11adf46753906075_0.png)

Hi， folks at Amarosso here。 And today in this video I want to take you through a really interesting protocol called S key is was written by a very famous computer scientist named Leslie Lamport。

 I want to tell you a story。 back in the 1980s。 I was a graduate student。 And one of my friends said。

 hey， listen， you really like security， which I did。 And you really like this。 this guy。

 Leslie Lamport， which I did。 and he said he wrote a paper， real simple three page paper。

 Why don't you read it。 So I remember， I went， I got the paper。 I SAT down， I was all excited。

 short paper。 my favorite author， favorite topic。 I S to read it。

 And guess what I couldn't understand it at all。 And I thought maybe I'm having a bad day。

 I don't know。 So I put it aside， took it back out， tried to read it again， went through it。

 got lost halfway through page1。 I think I iterated four or five times on that。

 And the dirty trick here is that it's one of the required reading for you。

 but it's the topic of today's video。 So I'm going to explain it to you。 And on a subsequent。😊。

We'll do some crypt analysis on it。 Now， here's the idea。 Alice is trying to authenticate the bo。

 So Bob， you know， it is essentially， you know， saying to Alice， hey， prove who you are。

 here's how works。 It's this crazy but really interesting scheme。

 The idea is that Alice and Bob both have the ability to encrypt a seed， a number number。

 And what happens is Bob， the server saves not the seed， but rather saves the encryption function。

 And then the result of having encrypted the seed。N times。

 So imagine when we're doing the setup and I'm setting the server up。 I take some number。 Remember。

 a lot of times we refer to a random number as a nonce。 I take a nonce。

 and the server will encrypt it。 Let's say n is 10000。 So I go， I keep encrypting 10000 times。

 And what I'm done， I store that value alongside the actual encryption function。 Go that。

 So think of that as storing F。😊，And F to the N of lambmbda。 You got that Now at the client。

 What client does is the client has the seed value。

 knows the number n and has the encryption function。 So I've got stored here。 F to the n of lambmbda。

 Here's what happens。 The server interrogates the client says prove who you are。

 and the client encrypts the lambda seed value， n-1 times that crazy， but here's the idea。

 I encrypt it n-1 times， and I send it to the server。 Now。

 when it receives that F to the n-1 of lambmbda。 What can it do， It's got the encryption function。

 So it can encrypt it one more time。 And then it's got F of F to the n-1 of lambda。

 which is f to the n of lambda， which is what it has stored。 Isn't that amazing。

 So it's got F to the N。 I send you F to the n-1， you cry one more time， you compare if the right。

 I say， hello， Alice。 And then。😊，I throw away f to the n of lambda as my stored value。

 and I now store f to the n minus1。Now， the next time I come along as Alice。

 and I want to authenticate to the server says hey， proof， now I have f to the n minus1 stored。

 so Alice keeps track of the fact。That N now has been decremented。 Now。

 Alice sends f to the n-2 in a separate session second time around。

 And Bob then can encrypt one more time to get f to the n-1， compares， says hello。

 Alice throws out F to the n -1 and now stores F to the n-2 as the seed value or as the the encrypted multiplely times encrypted of the seed。

 In't that kind of a cool concept。 You can see how reading a paper on this would be a little bit confusing。

 And I remember thinking of myself。 What happens， if you run out， Like let's say it's 10000。

 And you keep decrementing each time somebody wants to authenticate What do you do， Well。

 I thought about it， I thought， what if it is 10000， there are 365 days in a year。

 So if you did it every day for 10 years， that's still less than 4000 if you did it twice a day for 10 years。

 And I thought， you。You to do it twice a day for 10 years and even if you did， you could replenish。

 you just have to go back to the drawing board and reset things up。

 It's an extremely interesting protocol， but the irony is，Hardly anybody used it。

 The place I first learned about it was in some free firewall toolki code that I downloaded in the 90s。

 And there was a guy named Phil Kn， who was working for a company called Belcourt at the time。

 who had actually read the paper。 I guess he understood it where I didn't。

 And in the liner notes to the code。 He explained what I just described to you。

 And I remember reading it going， Oh， I see。 I understand how it works。 I couldn't read the paper。

 but I read the liner notes to some source code。 Go figure。 right。 Now。

 listen in a subsequent video what we will do。😊，Is we will cryptana this。

 but just sort of as additional consideration， something to think about。

 I do want you to think about protocols that have finite numbers of login and or use or rounds And whether that makes sense。

 Do you think it's reasonable to have sort of an end and limit the number of times that you can do it just for your your further consideration as you ponder the Lampert Eci protocol and think more and more about how authentication can be used in practical settings。

 So we'll see you in the next video where we'll do some cryptanalytic sort of investigation of this protocol and see which type of crypt analysis would need to be done to break it。

 I'll see in the next one。

![](img/6d7c33f00a9dc74a11adf46753906075_2.png)

![](img/6d7c33f00a9dc74a11adf46753906075_3.png)