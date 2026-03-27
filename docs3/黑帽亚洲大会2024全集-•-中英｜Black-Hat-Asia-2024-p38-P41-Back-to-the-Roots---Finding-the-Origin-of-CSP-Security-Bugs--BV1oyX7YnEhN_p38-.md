# 黑帽亚洲大会2024全集-•-中英｜Black-Hat-Asia-2024-p38-P41-Back-to-the-Roots---Finding-the-Origin-of-CSP-Security-Bugs--BV1oyX7YnEhN_p38-

Hi everyone， welcome to this session， we're happy to be here， so today we'll go back to the roots。

 we'll find the origin of content security policy bug。Yeah， so I'm Tom， this is Keian。

 were both researchers at the University in Lu in Belgium。

 where we do all sorts of research related to web security and privacy。

And now Captain will give a brief introduction on the research that we did。

Thanks Tom so why exactly do we want to find the origin of CSP bugs。

 well as you can see from these article headlines， it's still a prevalent issue。

 these report on bugs against security policies so it seems that browser developers still don't seem to be able to prevent all these bugs right so to find the origin we hope to actually find the reason as to why they can be prevented that easily。

So first a bit of context， what is the content security policy or CSP for short。

 so it was introduced about 10 years ago as a defense in depth against content injection attacks like。

 for example， crossside scripting。

![](img/4f2be2978c0f095e1f4f4c474b357cfb_1.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_2.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_3.png)

And essentially when you visit a website， that website has the opportunity to include ACSP and then client site in the browser。

 that policy will be enforced。

![](img/4f2be2978c0f095e1f4f4c474b357cfb_5.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_6.png)

So CSP is what they call a living standards throughout the years， a lot of new features。

 new use cases have been added， and nowadays we are at level three。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_8.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_9.png)

Just to be on the same page， a small example， let's say this is a social media website and this in particular is a webpage that presents the profile page of a hacker and despite the content sanitization countermeasures of the social media website the hacker was able to still inject a script Now if any visitor of this web page will have their cookie leaked。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_11.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_12.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_13.png)

Now， the website can prevent this by putting up an extra layer of defense being CSP。

 and this policy will effectively block the injected script。Now， as we saw before。

The implementations of these policies can have errors。

 and this also makes it more easy for the developer to circumvent this policy。

 and in this case maybe the hacker could circumvent this measure to still execute this script。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_15.png)

Like I said before， CSP was introduced about 10 years ago and throughout this time a lot of bugs have been discovered。

 as we will see later on， so the central question of the stock is what is actually the origin of these bugs？



![](img/4f2be2978c0f095e1f4f4c474b357cfb_17.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_18.png)

Because if we know the answer to this， we can use it as an attacker。

 we can find out where to find the next bug， but also as a defender。

 we could find out how to prevent the next bug。

![](img/4f2be2978c0f095e1f4f4c474b357cfb_20.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_21.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_22.png)

But maybe the most important question for now is how are we going to find these answers。

 and for this， we looked at the smallest recorded code changes that introduce or fix ACSP bug。

So for this we used code revisions， so these huge browser code bases。

 they use version control systems like Git for example。

 to track every change that is applied to the code change here。

 every green dot stands for a snapshot of the code base or a Git commitit or a code revision。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_24.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_25.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_26.png)

If we combine that with concepts of known bugs， we can then use dynamic analysis to find out what snapshots of the code base are vulnerable。

 in this case the red squares。And this as a result gives us the code changes that actually introduced or fixed a bug and the associated Me data Now this is very nice but these browser code bases。

 these are huge， they consist of more than a million go revisions and still each day。

 more than 100 are applied， so doing this manually is not very feasible。And for this reason。

 we developed Bhawk， which will automate a lifecycle analysis of these browser bugs。

So essentially you give Bcook a proof concept of the book you want to analyze and then it will find the introducing and fixing revisions Now this looks a lot like a bisection tool that's because it is。

 but it also sets itself apart from all other bisection tools。

This is because these binaries are executed in their own container。

 so we take care of all dependencies， this makes us able to evaluate even very old browsers。

 we can go back in time to Chromium and Firefox version 20。Also。

 we can run these evaluations concurrently to speed up the full evaluation process。

This we used in a study to evaluate 75 CSP bugs， and we found some very interesting things here。

First of all， we looked at the code changess that introduced these bugs。

 and more specifically we looked at the intentions of the developers that applied the bugs。

It turned out that half of the bugs in our data set were already introduced at the very first revision that CSP support was introduced。

 these are called foundational bugs。A lot of these lived under the radar。

 even one book with a bounty of $5，000， lived under the radar for eight years。

Also modifications to CSP logic are very prone to introduce new bugs， for example。

 even fixing a CSP bug is prone to introduce another CSB bug。

Then also adding features that are not really related to CSP。

 but should be scrutinized also caused bypasses because of oversights of developers。

We also identified a lot of room for improvement for crossB bug sharing。

 so if a security bug is reported for a browser， it will be shared with the other browser vendors because they share the same functionality。

 same specs。

![](img/4f2be2978c0f095e1f4f4c474b357cfb_28.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_29.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_30.png)

The current practice uses the web platform tests， so essentially it's a public get repository and regression tests of security bug are pushed there and other offenders can then pull these into to check if they're affected as well。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_32.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_33.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_34.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_35.png)

We evaluated this process by performing Chrobrowser evaluation between Chroium and FireFs。

 so essentially all bugs reported for Chroium in our data set we tested for FireFox and vice versa。

So we started with the 75 unique bugs of these 14 could be reproduced in B browsers。

 these were shared， and eight of those were only reported for one browser。Now more interestingly。

 seven， so half of the 14 could have been reduced in lifetime or even completely avoided at all if communication was more effective。

Now we also extended the evaluation to the release of Safari this was 16。

2 and here we could reproduce four of the publicly disclosed bugs。

 of course we reported the issues and this resulted in threefix and one not considered a bug very important here is that safari was exposed to these publicly disclosed bugs for more than one year and this is something you really want to avoid as a browser vendor but it even gets a little bit worse。

 we also identified inconsistent bug handling which led to premature disclosure。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_37.png)

So in three cases， the book was publicly disclosed by the browser vendors themselves before they landed an effective fix。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_39.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_40.png)

This was the case for two chromroium bug and one Firefox bug。

 and in each of cases it exposed to the browser for more than one year。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_42.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_43.png)

Even in the case of the Firef book， this one was still present in the latest release at the time of our evaluation。

 but again we reported this and this was fixed。Yeah， so as Captainf mentioned。

 there were like three main issues that we found related to the lifecycle of a bug。

 namely like when there's an introduction， it's more likely that there's other bugs there as well。

 like there might be also bugs that live across different browsers and the way that they're handled so in the next few slides we'll explore how we could use this either as an attacker。

 so I'll play the role as a attacker which could be like a bounty hunter。

 rat teamer or a security researcher looking for bugs in the browser。

And then we'll also look at how we can defend against these。

 and Kptan will be playing the role of the defender。

So whenever there's a change made to the core logic of CSP。

 it's quite likely that more than a single book will be introduced。

That's because well we did this analysis of these 75 books， and that's kind of what we find。So as。

Another thing is when there's things like iframes or other sorts of inheritance of the content security policy the enforcement of that is pretty difficult Now third thing that we found is。

When we have the script source directive， which is pretty complicated compared to the other directives。

 those are also quite likely to introduce。All sorts of different bugs。And also， the way that。

The content security policy is enforced in a browser it's been because first we had all these different features and then afterwards we retroactively applied content security policy to that and enforcement is quite fragmented。

 which means that sometimes browser vendors might miss something and there might be a very simple bypass。

So how can we use this as an attacker so we can look at the different public book reports because security reports become public after time they've been fixed？

And we then might use a tool like B Hawk to find which revision introduced the book and which one fixed it。

So we can look more deeply into the introducing book because as we found it's quite likely that there will be other bug introduced in the same revision as well。

呃。And we can also look at the fix and see whether theres， well the fix is complete。

 covers everything， and we can even compare it with an introduction to see if everything was fixed correctly。

Then we can also use some sort of heuristics because we know like when there's code touching the core CSP logic or there's some sort of inheritance logic。

 it's more likely that there will be a bug。So we could use all sorts of different heuristics。

 And then as an antier， we can more easily focus on the the different。

Pieces of the code that are more likely to be vulnerable。 or we can figure out whether a book is or。

Go change will be more likely to introduce a new book。 and ideally we would also automate this。

 This is something we're not quite yet at with Bhog， but maybe in the near future， we'll get there。

How can you use this as a defender well based on our data we found that centralization of enforcement logic really helps。

 it really reduces oversights thats introduced bypasses an example of this is the inheritance related bugs we found in total 22 inheritance related bugs and 20 of those affected chromium and only two affected Firefox this is the case because Firefox much bigger efforts centralizing this enforcement and now later on chromium developers also did a huge effort by putting CSP enforcement in the policy container and this was landed in 2021 and this immediately resolved seven of these inheritance bugs。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_45.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_46.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_47.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_48.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_49.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_50.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_51.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_52.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_53.png)

So as is kind of similar with the attacker， the defender can also assign more resources based on heuristics or likely culprits。

In this case， for example， it should really pay more attention to changes to the source code that are likely to introduce bugs。

 and this means for example， assigning more of viewers creating more tests。

And going further on these tests in the ideal case these would be automated and actually we found that a lot of these bugs that were part of our data set could have been prevented by very simple generated tests。

 for example， if you add a new feature， you can test it against the most strict possible policy and in the case of CSP for example。

 when a request is still sent， this indicates a bypass。

 and you can also take the strategy when a new policy is introduced， for example。So as we've seen。

 we also identified a lot of room for improvement considering sharing of bugs among vendors。

 quick recap， so seven of the 14 bugs in our data that were shared could have been prevented of or reduced in lifetime。

And four public bugs still affected the release version of Safari。Also a little detail。

 so five of the 14 foundational bugs in Chroium later appeared in FireF as a regression bug。

 so this means that it really makes sense to still include regression tests of other browsers even if you're not affected from the start。

And you would think that these regression bug might have been features that Chroium added way ahead of Firefox。

 but this was not the case， these regression bugs were introduced due to CSP bug fixes and this was in four cases due to a bug fix。

 but in one case it was also due to a CSP and enforcement design revision。So yeah。

 what what can we then do with this as an attacker？ So we know that like these。

These books get publicly disclosed and some of them might already contain certain tests。

 so a very simple thing to do is just run the same test in all the different browsers and as suppose the case with well at least Safari and Firefox as well。

 we might already discover some new books。Unfortunately not all of the fixes and book reports contain were platform tests。

 so if there isn't one already then it's sometimes fairly straightforward to just write one and then just keep on testing until you find that a new browser version becomes vulnerable to it。

嗯。And then yeah， next to looking at the browser book reports。

 we can also just look at the web platform tests and use kind of that as a sort of inspiration to find new types of bug。

Can， like。Take a。A test for one particular book and make some small adjustments and then see if this would be applicable to other browsers possibly as well and to find also new books。

As a defender book sharing platforms you use should be obviously representative and this means consistent sharing of bugs with other browser vendors in the short term this means maybe changing the sharing practice we identified a lot of disadvantages with the current practice of using the web platform tests repository for example sharing is postponed it's only done after creation of a regression test。

 sharing is public so when it's pushed to the repository it's public to the world and then the other vendors have time to react essentially。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_55.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_56.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_57.png)

And there's also no security focus。We think it would be better to use a privately shared bug reporting platform this enables sharing bugs as soon as possible。

 even right after Trich， also sharing is private and vendors can even disclose the bug in agreement。

 and there would be ideally a distinction for security bugs。And in the long term。

 we also think that browser vendors can learn from each other as to how they actually solve the same bug。

And then the last thing that we。Wanted to highlight was the handling of bugs and for instance。

The way that they're being tested and being mitigated。

 so we found these three bugs that were prematurely disclosed。嗯。So for instance。

 two of them were regression tests because in one case。

 the tests contained a meta tag instead of a header。

 and that caused the test to succeed while the vulnerability was still there。

And then another book was in Firefox where the book would exist in the package built。

 but not in the non package built and the nonpack built was the one used to run the dust。

And then the last case was when there was a fix in chromium where the fix was eventually reverted。

 but this was not reflected in the book reports， so the developers thought that the book was fixed while it was actually reverted and the vulnerability was still there。

So what we can do then as an attacker is that again。

 to see if there's any regression tests or or fixes and to check whether。

These are complete and sufficiently。Covering all the different issues。

And even we can look at differences in the dust builds versus the actual release builds。

 because the release builds is the thing that we actually care about because that's the things that actually run on the user's devices。

And whenever there's a revert that could also be like looked at as a sort of red flag to kind of raise the awareness of the attacker。

Tried to look into why it was reverted and was it correctly applied。 And was it later on。

 was there actually the fix relened。 And if that's not the case， then。

That's a very easy book reportport to make。And then finally。

 the attacker could also monitor certain lines of code of a fix because if。

There's adjustments being made to the fix， and it might be that the fix becomes undone。

 and then the vulnerability will be reintroduced as a regression。

So that could also be valuable for Nter to look into that specifically。

As a defender its really important that regression tests are an inherent part of the fixing process。

 first of all as a anity check that the fix really work。

 in the intended way but also in the long term we could use regression tests to find out what go change actually introduce the bug in our data sets the bug reports in 87% of the cases actually identified the fixing revision。

 you would think that this is 100% but in a lot of cases developers didn't really know how the bug was fixed。

 these were primarily bugs that took a long time to actually fix。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_59.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_60.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_61.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_62.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_63.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_64.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_65.png)

Then the identified introductions here， Buck reports only in 6% of the cases really identified these。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_67.png)

So consistent and comprehensive testing is very important， as Tom already mentioned。

 it's really important that bin should represent the release bin as much as possible。

 and also the tests should be independent of policy delivery。

 whether it's delivered through Metch or through the header。



![](img/4f2be2978c0f095e1f4f4c474b357cfb_69.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_70.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_71.png)

![](img/4f2be2978c0f095e1f4f4c474b357cfb_72.png)

And then also mentioned for the attacker is the red flags。

 so diversions from the default fixing protocol should be indicated as a red flag and here I'm talking about vverts and wheellands。

 for example。Okay we've arrived at the last slide just some key takeaways of this talk， first of all。

 we think that book life cycles are a much needed tool to better understand books。

This is both from an attacker' and a defender's perspective。

 we also found five issues by just looking at publicly disclosed bug and these issues affected releases。

So browsers， they implement the same specs and as such can be vulnerable to the same attacks。

 some bugs were only reported for a single browser so it makes sense to really effectively share these and we think that for this back channel is needed instead of the web platform tests that are currently being used。

We also found several instances of book mishandling。

 some were publicly disclosed before the fix was effectively landed and this was caused by incomplete regression tests and also by an unreported revert and as a last point I want to mention that Bhog is open source it's free to use you can use the QR code to visit our GiHub page and with that I will conclude it Doug thank you。

🎼别滚。Thanks for your talk。🎼So as you went through the identifications of the。

The moment where bugs was introduced。🎼Did you also。🎼Check the author of the Change as any pattern。

🎼Come out of that， should should we start blaming the people who actually introduce if they do that repeatedly in particular。

 we didn't actively compare the authors。But I think you will always see the same names because the teams that work on CSP。

 for example。These are quite small， I'd say。But we didn't look at it。

 but that might be an interesting statistic as well。🎼If there is no other question。

 So you have done that for CSP。 how， how reusable is your framework。You look at， I du't know。

 I Z archive， for instance， something like that。 I us， you know， these kinds of things。

Essentially if you can make a proof concept in a website that just requires。

 yeah that just sends a request to a certain endpoint when the bug is reproduce and it can be integrated as such in our framework so I guess its we already tried it for evaluating HSDS for example。

 also cookie policies， so it's。I think it can be widely used for other policies as well。And yeah。

 maybe in the future， also things unrelated to the browser might be applicable where because we already have like the whole infrastructure to run things。

 run the different tests。 So as long as we have。Like a a repository with the different commits。

 we can already start identifying what caused the issue and what fixed it。For questions。

Thank you again。