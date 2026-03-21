# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p76 31_三重DES.zh_en -BV1TFLZzYE26_p76-

![](img/11853ef05511731d6efa878eea781b88_0.png)

Hi， folks， I want to talk to you about a really interesting contribution to communication and to computer science made by computer security folks。

 particularly the group at IBM in the 70s led by H Fistal and a number of others who are just absolutely wonderful pioneers and cryptography。

 And the result of their work is something we call triple Des。

 Now here's the idea when I encrypt something using Des， which we went through in a previous video。

 I'm effectively doing the work of two to the 56 bit sized domains。

 So if I wanted to do brute force on single Ds， I could technically search a two to the 56 B or two to 56 number of choices for keys。

 It turns out that's actually a pretty small number for computers。 know in the old days。

 we used to say astronomical was a big number。 Now。

 I think we should say sort of computationals big number because2 to 56。😊。

actually very small cryptography So the question was how can we make it bigger and this IBM team took some time。

 looked into this and actually came up with an answer that now we would say is sort of du like yeah。

 it seems so obvious， they said let's just encrypt it multiple times。

Cause if you do the thought process in your mind， you realize that if I encrypt something with， say。

 a 56 B key and then have to do it again， I'm doing twice the work Like I'm actually increasing the computational complexity or the rather the size of domain。

 so。Here's what the IBM team said。 They said， all right， Instead of doing one De。

 single des with key like key K， let's invent key K1 and K2 different。And I'll encrypt it with K1。

 and then encrypt it again with K2， and I'll have 56 plus 56 or 112 bit cryptography。Everybody went。

Yeah， and if you don't get why it's additive， go off and do a few little examples on paper with small numbers and you'll convince yourself that it is additive to work。

 so。Here's the problem。 If you do that， then a bank off in some place that wants to communicate with you using single De equipment now looks at you with your double Des or two De equipment with the two keys and it'll go。

How do I communicate with you， How do I arrange the keys in such a manner that we can communicate。

 And you can see that it doesn't really work。 It's hard to do that。

 You can come up with weird sort of arrangements， but you'll never be able to duplicate single des with keys on double doess。

 So they came up with the idea of something called triple Des。 And you can see on the screen there。

 The progression from single does， double does， triple Ds。 the way triple De works。 is first。

 it takes advantage of an artifact in Des That is essentially that you can either encrypt and then decrypt。

 or you can decrypt and then encrypt and it's the same thing。 Remember。

 I said encryptption might be like walking that way。 So Ill go boom， boom。 And then the key is too。

 So I know I' there。 Now decryption is walking this way。 Bo， boom and I'm back。 Well。

 I could decrypt first。 walk that way， too。 And then encryptpt walk this way。 Sam thing。

 That's how Des works。 You could do either one。😊，So they said， let's set this up with three keys。

 K1 K2 K3， and I'm going to do it in an arrangement I call EDE mode or En dec cryrypt En mode。

 here's how that works。I start with a message am， and I encrypt it with key K1。

Or if you want to put in the middle， you can call it K3， whatever you like， go call K1。

Then I'm going to decrypt that with keyK2。And then I'm going to encrypt that with keyK3， three keys。

 and dec crypt encryptpt？Now， the fun part of that is take the first two operations。

 I encrypted something with K K1。 I decrypted something with K K2。 Think about it。 If I set K1 to K2。

😊，Then they cancel out， don't they？I'm encrypting with the key。 andry with the key。

 I get the message back。 And then I encrypt with K K 3。 I've got single Des。

 How freaking cool is that， Like by just setting K1 and K2 to be the same thing。

 I can have triple Des become single Des。 and I can encrypt with a bank。 But if you don't like that。

 And you go， no， no， no， I really want to do it more。 want， I wanted to be stronger。

 Let's say you want 1 hundred and 12 bit cryptography。😊，No problem。

 Set K1 and K2 and K31 and 3 to be the same。 K2 to be different。

 So now what happens is I encrypt with K K1。 I decry with a different key。

 which is like encrypting again。 And then I encrypt again with key K 3。

 The whole thing is 112 B cryptography with two keys because we said K1 and K3 with the same。

 So that's a choice。 Let's say you want even stronger cryptography。

 You want three times 56 or whatever that comes to 168。Then K1， K2 and K3 are all different。

So do you see， this how modern ciphers provide you choices in how strong you want the cryptography to be。

Based on how you set up the keys， it is。It'sLike the guys who came up with this。

Our our geniuses is beautiful mathematics。 A team at IBM get a lot of credit in their ability to do this liket Walttuval and Hrs Feel and these wonderful mathematicians that deserve so much credit for having created these beautiful ciphers。

 particularly triple Des， which I think to this day， is is a marvelous achievement。

 So I hope you enjoy that。 I mean， that's that fixes the one problem we said in Deez the 56 part。

 But there's another problem。 And that's sort of the scaling and other kinds of issues that you have in triple Des。

 And we'll start looking at some additional problems and limitations in a subsequent video。

 So I hope you enjoyed it。 We'll see in the next one。😊。



![](img/11853ef05511731d6efa878eea781b88_2.png)

![](img/11853ef05511731d6efa878eea781b88_3.png)