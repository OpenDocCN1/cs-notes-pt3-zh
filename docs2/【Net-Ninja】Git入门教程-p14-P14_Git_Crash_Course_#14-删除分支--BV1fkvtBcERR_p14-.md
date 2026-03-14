# 【Net-Ninja】Git入门教程-p14-P14_Git_Crash_Course_#14-删除分支--BV1fkvtBcERR_p14-

Okay， then so we've just done our first merge and now we've got our newsletter feature integrated into the main branch。

 but if we look at our branches， we've still got that feature newsletter branch hanging around。

 We've also got the old minute branch that I created earlier as a test and generally speak him。😊。



![](img/40b22f4adcc5a2ae628e10b97d85e4d9_1.png)

It's a good practice to clean up branches once you're done with them。

 So they're not sitting around causing in any kind of clutter。

 And I speak from experience when I say that how intense branches lying around makes things a little confusing。

 you start to lose track of what's active work， what's not。

 and just having loads of stale branches makes it harder to stay organized。

 And this becomes even more true when you start to work in a team of developers all working on their own branches。

 So in this lesson， by're going to see how to delete old branches when we don't need them anymore。

 And it's pretty simple to do。 So let's start with this newsletter feature branches then。

 since we already merged it into the main one and we don't need it anymore。😊，Now importantly。

 in order to do this， we first of all need to make sure we're not currently on the branch we want to delete I'm on main so that's okay。

 but if you're on the feature branch， use the switch command to switch back to main before you try and delete the feature branch。

So then now let's try deleting it by running the command git branch and then the hyphen D flag。

 which stands for deletete， then the name of the branch we want to delete。

 which is feature hyphen newsletter。And once we run that。

 it's going to go ahead and delete that branch for us。 Now。

 you can verify that by running the git branch command again to see all the current branches that you have。

 And you're going to see now that the feature one， I it there Asome。

 So then now let's try deleting the other branch that we don't need anymore。 Now before we do that。

 I'm going to switch over to it by running the command Git switch。 and then the name of the branch。

 which is my new branch， Not so new anymore。😊，Okay。

 and this branch is now actually behind the main one because we made it back before we merged the newsletter feature into Maine。

So before we delete this branch， I want to show you another pattern you might follow which is to make a branch。

 start working on it， make a commit or two and then maybe decide that you don't want that work anymore or you don't want that branch anymore and we don't merge it back into main or anything we just want to delete it。

😊，So then I'm literally just going to open the homepage file and then add a character into the title or something just so we've got something to commit。

😊，I'm going to save the file and then we want to add the change to the staging area by running the Git add command。

 then adoptt and then press enter。 Now I'll commit that change by running Git commit along with the Mflag to add a commit message。

 which can be something I don't know like update homep page title。Okay， and then we can run it。😊。

So now we have a commit in this branch。 And now let's say we don't like anymore。

 The feature is complete trash。 We want to get rid of it。 Well， let's do that。 The first step， again。

 is to jump off the branch because we can't delete a branch if we're standing on it。

 So let's switch to the main branch by running the git switch command。

 Fo by main to jump to the main branch。 And now let's try deleting that other branch that we just jumped off by running that same command as before。

 which was git branch。And then we use the hyphen D flag to delete one， followed by the branch name。

 which is my new branch。Now， when we try to run this， Git wont letters。

 And it says instead that the branch is not merged。

 So this is Git's way of protecting us from accidentally deleteing a branch that we might not want to do and losing work essentially。

 because that branch does have a commit on it now， which hasn't been merged yet。

 So when we want to delete a branch with commits on it， which haven't been merged。

 we need to change the delete command just a little bit to force the delete。

And all we need to do is change the small case lower D flag to an uppercase one。😊。

And as you're basically telling it， look， I know there's work on this branch that hasn't been merged。

 but I still want to delete it。 So let's run this commander。 It's Git branch。 And then this time。

 hyphen D， but uppercase D。 And then at the branch name， which is my new branch。

 And when we try to delete it this time， it works， Git will delete that branch。

And we can confirm that by running Git branch and hitting enter to show us only the main branch is left。

 Okay so that is how to delete branches。 And again。

 it's always a good practice to get you into when you finished work on a branch so that your repo doesn't turn into a graveyard of old work and old branches。

 I' read them my friend。 So that is the end of the Gitcra course in the end of the preview of the whole Git and Github masterclass course that I released on the netinginja do dev site。

 So if you want to carry this on And there is about another five hours of content all about Git advanced features。

 Gitthub using AI with Github as well， the Gitthub Ci。😊。

Then feel free to go and grab this course on the netinja。

 dev website and we leave a link to the course page down below。 It's $10 to buy。

 or you can use the promo code， which is gett 40 to get it for $6 and you can also sign up for a nett Ninja Pro subscription by clicking on this link right here。

 and that's gonna be $9 a month to get access to all of my masterclass courses including this one And also you get your first month half price。

 So I really hope you've enjoyed this series so far。

 if you have please do not forget to share subscribe and like that really means a lot。

 And hopefully I'm gonna see you on the full one soon。😊。



![](img/40b22f4adcc5a2ae628e10b97d85e4d9_3.png)