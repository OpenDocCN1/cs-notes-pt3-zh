# 纽约大学《网络安全｜Introduction to Cyber Security》中英字幕（deepseek p61 16_密码与分析.zh_en -BV1TFLZzYE26_p61-

![](img/fefd98e8aad2d43591b4feedcb242635_0.png)

Hi folks， what I want to do now is I want to analyze the password protocol。

 something we're all comfortable with， familiar with， use every day in the context of our schema。

 Our six step protocol schema that we went through。 So let's start。 So in step1。

 Alice reports that she's Alice。 The identification step in step 2， Bob provides back a challenge。

 basically saying， okay， your Alice， what's your password or typing password colon or something that makes it clear that you're looking for a password in step 3。

 Alice then computes， remembers， looks up on a piece of paper， whatever she's going to do。

 finds her password and you know， confirms that it's the right thing。 You know。

 I'm logging into this application。 You look up in your little book。 you wrote it down。

 I don't know whether writing it down is a great idea。

 It might be nowadays it seems like you have to write it down。 there's my password。 and that step。😊。

Three， just computing or looking things up， you're not doing something mathematical。

 you're finding or remembering or looking up password in step four， I type it in or maybe say it。

I'm providing the password back to the requesting server。 It asking me to validate。

 Here's my password。 Step 5， I look up the password。

 There's probably a file somewhere that has your name listed or your user ID and password a lot of times you'll want that to be encrypted because if it's not encrypted。

 hackers can come in and read it。And you want to do something even more than just encrypting it because when you store it encrypted。

 if hackers know the encryption algorithm， they can do these crazy things。

 like run something called a dictionary attack， where in a stored list of passwords that are encrypted。

 I can encrypt every element of the dictionary， This is assuming I steal your password file。

 and compare every word in the dictionary against each password。

 And if some user on a shared system has a password that's just a word in the dictionary。

 then it'll match。😊，If I know the encryption algorithm， I have your password file。

 It is a shared system with a bunch of users， and I have a dictionary。 There's a lot of ifs in there。

 But you get the point。 And then after in step 5， I validate or nor validate， does not you。

I notify you。 That's the six steps and password。 Now， let's think about Eve。

 How does Eve attack this system in zone 1。Find your password， asks your password。

 guesses your password。lott of easy ways to guess somebody's password pins are the easiest of all because it tends to be a part of your mobile number or your zip code。

 if you're here in the United States。 like some number that's part of your address。

 phone or something that you are some number that's been issued to you is almost always your pin I'm sure out of the people who are watching I probably could guess half of your pins。

 if I just know a little bit about you。 maybe a business card would be sufficient for me to get a pretty good idea of what a pin would be that you'd be using for either a mobile device or your garage door opener。

 So so you can guess or steal or do whatever she needs to do in zone1 Zone2。

 she can do something called sniffing in a previous discussion we mentioned sniffing that's basically collecting information on a network。

 know collecting packets or messages or commands because the internet is natively not encrypted。

 So if informations being passed。accross the public internet。

 then Eve can read it and your password might be passing by in in unencrypted or plain text in zone 3 again。

 you' go and read the password file。 Now hopefully you know you won't be storing it unencrypted and hopefully in addition to just having words there。

 you might introduce something called salt。 It's an interesting concept。

 that's where you take randomized numbers and you just append or prepen or inend random numbers into the word just for storage。

 that way， if I do a dictionary attack on the stored passwords。

 it's not going to match because I put a little random nonsense in there。 In fact。

 that word nonsense in cryptography is reused and we shorten it and we call it。

 So a lot of times there's just some number that I need for some reason we call that a。

 and you'll see that when we get to crypto we'll be using nonsense frequently to do interesting things bitcoin that block。

chain component of bit， which blockchain is certainly separate from Bitcoin。 but in blockchain。

 we use nonsenses to do mining。 we'll get to that as well。So you think passwords are very secure。 No。

 Eve has good opportunities in each zone。 Why do we keep using passwords， Because people love them。

 They're interoperable。 They're comfortable。 They cut across all of our systems。 They're fun to pick。

 We're used to it。 It's easy for developers。 They are never going away。 Don't even think they are。

 You might work for a company or you might have heard of talk by or you might have a professor somewhere。

 tells you they're working on getting rid of passwords。 You're never going to get rid of passwords。

 You can augment them。 You can build much stronger forms of multifactor authentication。

 No question about that。 but there's always going to be a place for passwords because people like them。

 I think system designers need to keep that in mind。 So with that， we will see you in the next video。

😊。

![](img/fefd98e8aad2d43591b4feedcb242635_2.png)

Thanks。

![](img/fefd98e8aad2d43591b4feedcb242635_4.png)