# LLVM开发者大会-US-｜-2025-Llvm-Developers-Meeting-p18-P17_用于C++的未定义行为附录--BV1ejr5BAEja_p18-

![](img/5cca3b14a0edef84ea07a21412d67f4b_0.png)

Hi everybody welcome。 My name is Shafi Yamore。 I'm a Kang frontron end developer at Intel supporting C++ I'm also on the C+ plus Dans Committee mostly working in the core working group you may also know me from my weekly C+ quizzes on social media you may know me from my blog which I post about four times a year mostly on C+ plus edge cases know sometimes LOVM and general software development。

 you may also know me from my C+ plus dad jokes。 I have one here for you today and you know if you like the more you can try to follow me on social media So8 bytes walking into a bar barchaner asks。

 what can I make you They say make us a double。😊，Okay。Thank you， thank you for the generous applause。

 So we are here today to talk about a UB and IFNDR annex for C plus plus So UB stands for undefined behavioror undefined behavior is its bad code。

 right， It's basically the standard。😊，Says the behavior of this code you have no expectations right an optimizer is going to assume you don't do code like this and it's got to optimize accordingly and this is when bad things happen。

 you know security issues happen， unlike debugging sessions trying to figure out why your server is crashing all around just a bad thing for everybody IFNDR stands for illform。

 no diagnostic required。So the illform part in a standard where we have illform code。

 this means that it requires a diagnostic。 So the NDR part here。

 this is code in which we'd like it to be illform， but for technical reasons right。

 the implementations may not be able to reliably diagnose it and so you can end up with lots of the scenarios here。

 the code compiles， it doesn't compile。 it may compile on some of the limitations。

 it may not compile on others， it may have。Different behavior on different implementations， right。

 So it doesn't have this kind of unbounded runtime， bad behavior that UB has。 But in general， it is。

 you know， undesired behavior。 It's not something that a lot of C plus plus developers understood very understand very well。

 And so it's just a trap。So I'm going to often kind of just say UB when I mean both。

 and so I'm just kind of using as a shortcut。Well okay。Yeah。

 so let's talk about the problem at a high level。 right。

 So the C plus plus standard has a lot of undefined behavior in IFNDR。

 The next problem is that they're often very hard to identify。 So if we look at this list here right。

 just for undefined behavior。 The standards document is a 2600 page document。

 right And so we we can talk about undefined behavior as the behavior the program is undefined。

 undefined behavior。 The behavior is undefined the behavior。

 A bunch of other words is undefined and we can kind of go on right， And you can sit there and say。

 well， why don't we just look for the word undefined。 And unfortunately， we use undefined。

 in lots of other contexts， have nothing to do with undefined behavior。So。

So if you want to find all the UB and IFNDR， you have to go through the whole document and kind of find the one by one。

 it's a tedious， long process， I've done it， it takes a long time。

The next problem is they're often hard to understand。 The standards document is not a tutorial。

 It is a specification。 The language is often very dense。 Okay， there are usually no examples， right。

 sometimes are sometimes they're not it's not consistent。 And so if you don't get it。

 you don't understand undefined behavioral IFNDR， you're on your own。 Lastly。

 the problem is that sometimes UB is left implicit， right So the standards specification。

 It sets guidelines and rules for what conforming code is and sometimes when you break those rules。

 it's UB， often the standard will explicitly point out， but sometimes it doesn't。So you say， okay。

 well， okay， at least we could just kind of go through the standard， let's unify the wording。

 let's get everything kind of clean and simple and will that might be a great thing。

 but it doesn't solve the problem right because we still the standard is not a tutorial and so you still don't have a way of understanding that UB It's not put in laypersons terms and we don't have a good place to put examples of it right and honestly we would like to just have one place where all the UB in all the ifFNDR is listed and you could just see it all at once instead of having to search through this 2600 plus page document。

So what is an Nnex you might ask， so the ISL IEC directors part 2 actually gives us a really nice description。

 right？The C++ Standard Committee。Its an ISO committee often called W G21。 It has lots of documents。

 how you run a standards body and how you write standards， right。

It tells us right that annexes are used to provide additional information to the main body of the document and are developed for several reasons。

 right， Often when the information is just too verbo。

 it would kind of be out of place in the main body of document。

To set apart special types of information or to prevent or to present information regarding a particular application and document。

 So this kind of sounds like what we want， we want a place to list all the UB。

 all the AFNDR with late personson explanations and examples right And just to clarify。

 we often hear in the standards terminology， normative and informative So normative or rules。

 you have to follow those rules whenever you see these words in the standard right。

 that means that you have to follow them informative Often we have notes in the standard。

 They're not rules。 They're just there to guide further understanding。

So what are the high level goals here， right， so the first goal is to create an informative annex for UB。

De crcheate an informative annex for IFNDR。With plain explanations for each example and a code sample for each one。

And we want two separate documents basically because they're different things， right， IFNDR and UB。

 even though they kind of have the same property， they're unintuitive and they're kind of traps that developers fall into。

 but they're different things that we don't want to lump them all together。

Another goal is that we have a lot of different target audiences， right。

 we have regular C++ developers， it could be college students。

 it could be professionals who've been doing this for a long time。Who want to understand what UB is。

 They want to avoid these traps。 They want to learn， right， And then we have the trainers， right。

 trainers could be in house trainers， people， companies pay for it to come in and train people。

 professors in college。Psenters at C++ conferences or other conferences right they want the material to be able to explain UB ifFNDR have good examples and be able to teach people what to avoid right tools developers that's us so we write tools we write sanitizers。

 we write static analysis tools， we write diagnostics And so we can look at this as a list of targets right so are we catching things everything that we can catch。

 are we diagnosing them better， are we catching them as sanitizers and so for tools developers we want this nice list in which you can just go to and sit there and say。

 hey， listen。What could we be doing a better job with and obviously then also for security analysts right So UB often ends up with security vulnerabilities。

 This is you know news stories about this and the tech news all the time。

 and so we want security analysts to be able to have a list to look at and to be able to understand undefined behavior。

 to be able to explain it to their users to be able to teacher users just to be able to write。

Better tools for catching and diagnosing undefined behavior。

 Another goal is we want to diagnose all explicit U B， right。

 It doesn't help if we leave everything out anything out。 So it has to be a complete。

Listing of all of them， we are purposely not documenting implicit UB because it could be error prone because it's implicit。

 we may not understand the intents of how those words were written right and so maybe we might make that UB narrow too narrow or we may make it too wide right and so we want a separate process in which we now have to go and sit there and say。

 okay， we have implicit UB， we need to make it explicit so that then we can document it in annex。

And finally， we want to make sure that the WG21 process for writing proposals。Includes。

Adding and removing UB。And IFNDR from the annex is right。

 So whenever you write a proposal to change things in the standard， right。

 you have wording right that that you put into the standard to sit there and specify what you're doing。

 right， And so we want to make sure that that's explicitly part of of the process of writing a proposal。

So we may ask why is this important for C++ I think not surprisingly our users want a safer language right and I'm going as I go on and explain it we can kind of see how this will help us eventually get to a safer language right UB is a trap for unaware developers right？

If you don't know what to avoid， you don't know what the UBs are in IF NDRs。 you can't avoid them。

 And in general， we found that。Most developers don't understand UB very well。

 They may have heard of it。 They may have known some examples。

 but they don't really know the full space of it。I'm going to be honest experts。

Often can't easily identify UB。 I can't tell you how many times I've been in a chat or in a group or in a meeting and when you sit down and looking at this course say is that UB I don't know。

 maybe you know right and so even experts， we also need this documentation to help us better identify and learn about UB。

It's also important because a common set of examples to make UB more concrete helps us to understand this。

 you can describe the various undefined behaviors， but sometimes seeing the code really makes it brings it home and so。

When you see the code， somebody said they say， oh， wait a second， I've seen that code before。

 maybe I've done that code， right， And so it's important to be able to see examples。 And lastly。

 if we don't document it， we don't know if it's getting better， right？ So ideally。

 over the long term， we would like to see the undefined behavior in the standard decrease， right。

 But if we're not tracking it， We're not documenting it， we can't really tell。😊。

Another good question to ask is why is it important for client？So unsurprisingly。

Our users want a safer language， right？Often our users are going to communicate write bug reports。

 have discussions， ask us questions。You know， optimization is， is is doing something wrong， right。

 or they don't understand why it's optimizing this way。 And often they come down to UB。

 And so having a list one place that lists all the UB and describes them well will allow us to communicate better to our users more effectively。

 And just well be to sit there and say， hey， listen， here's UB。This is what it is。

 and this is what you need to avoid。 as tools writers。

 it gives us as list of targets to write better tools。

 to write better diagnostics and to write extensions。

 hopefully to make it easier to avoid undefined behavior。We can move faster to implement solutions。

 right， We already have a lot of safe extensions， right， some examples here， F D， enostr aliasing。

 Liy plus plus hardening。 I'm going to point out that we。But。🤢，Aaron， Eric Vd， K1 and I。

 we have an RFC for a hardening mode in Kang。 We would hope that this would kind of be like an umbrella area in which we can help develop more safer code options for。

 for cl。 So if you haven't seen this RFC if you haven't comment on。

 I would check it out and and just， you know， add comments or just we didn't understand it better。😊。

嗯。I'd like to talk a little bit about the process right。

 So maybe if if you haven't been involved with the Standard committee。

 you don't know what Stan committees about how do you make changes， right？ So in general。

 you want to make a change to the C plus plus standard。

 You' got to have to write a proposal right So my first。Temp that this was P1705， right。

 You going to write a proposal and then。In general， right。

 So you could have the standards committees made up of， of lots of subcommittees。

My targets are mostly evolution and core， evolution deals with evolutionary changes to the language。

 you want to add features， you want to take away features， you want to enhance things。

Evolution is where you get targeted and so the annex is considered evolutionary change to the standards document and the court working group deals with the wording in the standard right so when you implement things you have to change the standard。

 the wording and the core working group makes sure that the changes to the wording actually deliver the intent of the changes right and its works and the specification is correct often your proposals don't survive first contact with the committee often you may have to refine things and add。

Complete， you know。Specify things more， more clearly right。 And so that was my second。

 my second proposal in this area， which is P 3075。 eventually you get accepted。

 And then we we're at this step here， which is iterate over annex wording， right。

 So we have a PR against a C plus plus draft standard currently。In which we have。

 I believe is is a complete list of UB and IFNDR。 And so we're kind of at the point where we're just wordsmithing。

And so then you know， then after once that's done and we sit there and we say， listen。

 we got this in the right shape， then we get a final acceptance of the wording and then we can then merge that into the draft standard and then we're done at least with that point of the process。

So I'd like to finish up with a call to action the annex could use more editors right we're kind of。

 I believe in a really good state where we have a full list of UB and IFNDR。

 but we need a lot of just wordsmithing， maybe better examples， etctera， etc cetera。

 so we could use use more help in trying to get that there， we need people。

To help us identify implicit UB in the standard， right， we know it's there。

 I haven't really SAT down and tried to take a look at it and figure out what they are。

 but we need people to kind of either if you're not in a committee file defect reports。

 if you're already on in W 21， then you can just kind of start conversations in a core reflector。

 But we do need to start that process， right， so we can kind of turn those implicit UBs into explicit Us。

 and hopefully remove all the implicit Us。 And finally， I'd like to say that， you know。

 we need to be the change that we want to see， So we as implementers and a tool designers。

 we can implement new diagnostics help specify the behaviors of U right often。😊，You know。

 there's U B。 We sit there and say， yes， okay， that's expected。

 What you're doing is undefined behavior， but sometimes the behavior can be pretty。Bonnkers， right。

 And so we can maybe do a better job than trying to restrict how crazy the we get with the optimizations。

 right， and hopefully maybe with extensions or other ways eliminate UB in general。Thank you。

 And if you have any questions， Im open to them。Thank you very much for this great talk。

 I completely support this undefined behaviors a wild field and there's a mis who will say you shouldn't have undefined behavior。

 but they don't know how to test it and there's not even a specification。

 the clear one and that's why I think it's very good I have a question。

 how would you approach this as you mentioned you went through the standard and then found everything listed there？

Is this the way or do they have do you have other ideas to's So you have to you have to manually go through the standard。

 find all of them， right， I missed some， So tomorrow and other people have added ones that I missed you know。

 because you know， when I started And then by a time I got it together know。

 be were specified and stuff like that。 So's it's 2600 pages right。

 the wording is not uniform across the standard。 So you just have you some words can be separated likelash next line That's right。

 Yeah，'s that's exactly right。 So it's it's a painstaking process。 But once we have the annex。

 then we shouldn't have to do that anymore So were one and done and that should be it。Okay。

 thank you。 I thought there might be also some experts that have some tools Check out analysis tools that say。

 okay， we have already some list here we do right， So we have sanitizers。 We have static analysis。

 right， But I mean， I don't think we have anything that catches all forms。

 and maybe there are some you just can't easily catch， right， But I think we could do a better job。

 I think there are holes where we can improve。 Okay， Thank you。

So there's undefined behavior that is sometimes used as an extension point for compilers Yes does this annex make a distinction between undefined behavior that is we simply can't define this versus this is intentionally undefined behavior because we want to No no it just basically explains it and lay person's term and gives you examples of them。

 it doesn't explain intent it doesn't explain you know uses right we potentially could have TS right in which we kind of go into more details we go into what tool it can to use to check in and stuff like that I haven't started that process I don't think anybody else has started that process。

 but I think that that is an important process this is just okay we need one place where we can find everything and we can educate people and yeah and then now when you write proposals。

We have to add them and remove them。 and then we have to make it I think making an explicit part of the process。

 right， I think you sit down and you're looking at a proposal sit there say you're adding UB。 Oh。

 okay， I didn't realize that。 Why do you have to add U B。

 And I think hopefully that'll help a little bit in maybe reducing the UB or maybe getting some more pushback。

 Right？ So yeah， great。 Thank you， yeah。I thank you for the talk。

 I first hurt when you mentioned when you were characterizing C++ developers who don't know what undefined behavior is and where it might show up Yeah so thank you And and this is a novel effort although it's a long way have you thought about how C+++ 26 contracts will maybe make this process more mechanical finding out what even his undefined behavior and any given API I have not been involved in contracts so one of my other team members at Intel Tom Hoorman has actually been really focused on contracts。

 I have not been focused on it And so I think there are people who definitely have very strong opinions on this right So the contracts folks have thought about this I have not really talked to them about this in detail。

 So I'm not sure I mean yes， I think there are strong ideas on this right， but I don't。

What the contract folks are saying in this area。Thank you。 Yeah， Nor worries。 Thank you。Hi。

 so I had a question that was basically so like at the end。

 we had to kind of call to action and you know the idea is we need more people to sort of pour over the documents to figure out what is U in order to improve the annex do you see sort of a chicken and egg problem there where in order to create the anex。

 you have to understand what UB is but in order to understand what U is you have to have an annex of what UB is like what would be the process to bring people up to So my call to action kind of is targeting different people。

 right So editors right like if we want editors to you don't have to be an expert you could just be let's say like really great just being editor in general。

 right， but yeah， the people who are asking to look and find implicit UB。

 those are more likely and not gonna be experts people who are already on the committee or people who are just really know a lot about C plus And so a regular C plus developed。

who's not really familiar with the standards document。

 Probably they're not gonna be the ones doing it right。

 but I I do want to make sure that know there are gonna be lots of C plus experts here a bunch of people on the committee right and maybe they have ideas。

 Maybe there's somebody sitting there and said oh yeah， actually I've thought about this。

 looked at them and I just haven't thought about them in a while and they just fire off an email to the core reflector and start the conversation they don't even have to do much They just write the email and then core will kind of just take it from there because they do care about this。

Yeah。I mean again。Sometimes its also intended。 So if you have， for example。

 the order in which arguments are evaluated， that can be from left to right or from right to left。

 And some that's unspecified behavior。 yeah， yeah and this is an implementation defined。

 So I think these are terms that also should unspecified or then implementation defined。 Yes。

 those are separate， those are separate things。 So we actually。We do have implementation defined。

 Im actually not sure in the C right， but they are separate ideas， right。

 So so implementation defined behavior is not UB， right。

 And so that is a separate idea and there unspecified behavior， right， But so the thing is right。

 is that implementation defined behavior can catch people off。

 But UB kind of has this unbounded effect， right， that implementation and unspecified behavior doesn't have right。

 And so for port， it's dangerous But part of it， yes， for sure， for sure， definitely。 Yeah， yeah。

Okay， so let's thanks Yeah last question。Hi， I have a question。

 Do you have an example of implicit U B， I do not。 I do not。 I have not。 I have not dug into it。

 I don't have a good， a good example for implicit U B， yeah。So let's thank Shafik for the great talk。

