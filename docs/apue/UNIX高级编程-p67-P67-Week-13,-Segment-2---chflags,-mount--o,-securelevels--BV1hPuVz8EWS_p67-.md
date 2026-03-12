# UNIX高级编程-p67-P67-Week-13,-Segment-2---chflags,-mount--o,-securelevels--BV1hPuVz8EWS_p67-

Hello and welcome back to CS631 advancedance programming in the UniX Environ。

This is our second video covering how we can restrict processes。

 and today we'll revisit the mechanism by which we can change our effective UI。

 what pitfalls might await us there and what additional security mechanisms we have。

These mechanisms include fire flags， certain land options。And something called secure levels。



![](img/e958fb31c58df4211b51efedd3baf726_1.png)

As we saw in our last video， PerX echos can allow us to better control which users connects as which files。

 or rather we can control which processes when running with a given user's effective UID connects as which files。

Recall also from week3 segment3， our discussion around the use of effective and real UI and how we can change or elevate privileges。

A common example of using this mechanism are demons that in superus privileged just initially。

Such as to bind the privileged port or use raw sockets for ICMP。

To actually handle logins and then to downgrade privileges。

Or to raise what change privileges for the duration of a whole login session or a single command。

But each of these approaches has some pitfalls， too。

A said UD program needs to be very carefully written to only raise or use the race privileges when needed and to avoid allowing the user to escape and run any other programs that is often more difficult than it sounds。

This also depends on the correct installation and configuration of the binary。

 which is something the author of the programme has no influence on。What's more。

 setting the set UI bits un unexecutable allows anybody who can execute the fire to run it with the owner's privileges。

 meaning there is no fine grained control here。We've also seen examples of changing our effective UID when using。

 for example， SU。But being able to run as you relies on the password of the user。

And it grants you full access to everything that user controls。That is。

 you can only allow another user to S and thus to do anything in everything as the target user。

 but not restricted to a subset of functionality or commands。To overcome some of these limitations。

 as well as to provide a bit more control， logging and additional protections around the changing of Euids or running programs with the privileges of another user。

 many Uni systems use the pseudo utility。Although not part of every Uni system。

 it is the most commonly used mechanism here， allowing for fine grid control and careful definitions of which user may execute which commands。

 assuming which other users EUuIs。However， Suda turns out to be a complex beast and configuring it correctly and securely isn't easy。

All too often， trying to restrict privileges to a set of commands result in the user being able to break out of one of them。

 gaining more elevated privileges than intended。Because requiring additional authentication for the execution of the command can be cumbersome。

 especially for automated jobs， people oftentimes simply disable them。And quite frequently。

 people are not aware of what additional privileges they are granting by accident。

Let's illustrate this problem， by example。

![](img/e958fb31c58df4211b51efedd3baf726_3.png)

Let's create two files over here。One fire that we intend to share with Fred。

And one file that we intend to keep private。The permissions on these files look like so。Now。

 we will grant suitable privileges to Fred to edit files as the user， J Shama。

If you' are notfamar with the syntax for the Suas file。

 it consists of statements that specify which user may invoke which command as which other user。

 and our edition here simply states that Fred may run user BviI as user J Shama without providing a password。

O。So let's see。 here's Fred trying to edit our file。That， of course， didn't work。

What are the permissions again。Oh， we can't even look at the directory。

 The read and execute permissions are not set for others。Now， let's use Sudo instead。There we go。

 We can now edit the file。But now we have a problem。

We granted Fred the permission to run V I as J Shaalman。 So， of course。

 Fred can simply run the same command and give it the front the private filing debt。

This is an example of overly broad pseudo privileges where we intended to only grant one type of access。

 but received。Implied broader access。Okay， let's prevent Fred from accessing the file by removing permissions from it。

We， as the owner， can sm it as needed when we want to access it。 but Fred can't。

 since Fred can only run V eye as Jsm。There we go。 We Fred's plan to access this file。

 while still allowing him access to the shared file。But friend is no dummy。

With powers to edit files as J Sharma， Fred can now edit or shell start file。Here。

 let's create a back door When user J Shaalma logs in the next time we copy a regular shell and make it set U I D J Shaalma。

Because we are sneaky， we ought then ensure that this command is removed from the start of fire。

 so we have left no trace of our evil intrusion。With that line at the top of the dot S HRRC file。

 all we have to do is sit back and wait。Nothing happens for the user， while they're logged in。

But if the user logs in a new simulated here by executing a new screen window。

 then our commands get executed。And yep， we didn't leave any evidence。

So now Fred can find the shell in s temp。And wanted it to become Jehoma。Oh， wait， what's that。

 Why I I Fred。Well， it turns out that most unique shells have a check to see if the effective UID matches the real user D。

 and if they don't match， the shell sets the U ID to the real U ID。But if we pass the dash P flag。

 then we get privileged mode where this check is not performed and yep。

 we are J Shaalma with a real U I of 10，0，1 and an effective U ID of 10，0，0。So， now。

We can simply smart the permissions。Write data to the file。And then under the permissions。

 change again to cover up our tracks。Here we confirm that the file was changed。Blast。Okay。

 let's try to be a bit smarter and not let Fred edit just any old file。Instead。

 we restrict Fred to only edit the file we want him to have access。There。Now。

 Fred can't edit any other files。Not our shell RRC file， and not the target file he wants to access。

As before， Fred Ken edit the shared file。But unfortunately。

 V eye allows you to read and write files so we can simply slurp in the file we care about。

Trying to write， however。We run into a problem。 permission to night。

Because of the five's permissions。But here's another thing V I let you do。

It lets you shell out and run commands。Here， if we run who am I， we see that we are J Shaalma。

That is VI runs as J Shaalma， and so any comments invoked from within VI run as J Shaalma too。

So I can run the shell from within the editor。Then I can fix the permissions。And write my data。And。

 quickly。Let the user know that。 We pound them。All right。

 I hope this illustrates some of the pitfalls with using pseudodo。

Many are comments besides editors allow the user to find ways to run other commands。

So it's often best to assume that unless you're really careful。

 giving another user pseudo access to some commands may imply giving them full access。

So what other ways do we have to restrict the user。Besides permissions。



![](img/e958fb31c58df4211b51efedd3baf726_5.png)

There also are file flags， That is we have additional ways beyond simple permissions to restrict access to a file。

The flag is called shown here comes in the three versions were used to flags operating on a file。

 L flags operating on ase and F flags operating on a file descriptor。

If your file system supports them， then these fire flags or fine attributes provide way to。

 for example， indicate that a file may not be changed at all。

 even by the owner and not even by route。Such a file is called immutable。 If this flag are set。

 then on root can un the flag。The flags are you aent only。User immutable。Syste repent only。

And system immutable。

![](img/e958fb31c58df4211b51efedd3baf726_7.png)

Here。Let's take a look what this looks like in practice again。Consider this new file。Of course。

 I can overrite the file。But now let's set the U append flag， making the file append only。Now。

 if we try to open the file in regular right mode， this will fail。But a pending data。Will work。

That is， we can force over pen mode on the file level for all access to the file。

To see the fire flags， we pass the D O flag to L S。Let's see what options are available。

Some of these options apply to system backup operations。

 The other ones are those we've just seen a minute ago。Let's create a second file。

And market a system immutable。Meaning， the ownerna can modify the file and even root can't。



![](img/e958fb31c58df4211b51efedd3baf726_9.png)

![](img/e958fb31c58df4211b51efedd3baf726_10.png)

Note that a file being immutable extends to it being removed。

 even though we normally think of unlinking as affecting the directory only。

This is because unlinking still modifies the metada of the file by decrementing the link count。



![](img/e958fb31c58df4211b51efedd3baf726_12.png)

As we can see here， even Ro can't remove the file。Then， of course。

 road can undo the change and unet the fire flag。

![](img/e958fb31c58df4211b51efedd3baf726_14.png)

Fief flags can also be set on directories。

![](img/e958fb31c58df4211b51efedd3baf726_16.png)

Now， we can manipulate the file。

![](img/e958fb31c58df4211b51efedd3baf726_18.png)

But， we can remove it。Because now we'd be modifying the directory it is in。Likewise。

 for renaming the file。

![](img/e958fb31c58df4211b51efedd3baf726_20.png)

O。So with a fire marked， a system immutable， even a root can change it。

But this is a change that's applied only on a pur level。

I'd take a look at ways to apply restrictions on a file system level， instead。

Here we are operating on a second file system mounted under a slash mount。

We have a trivial program that simply illustrates how the set U I bit works by printing the effective and real user I。

So let's create a set U I D executable。Owned by nobody。When we run the programme， we see that。

 of course， that U I D behaved exactly as we had intended。



![](img/e958fb31c58df4211b51efedd3baf726_22.png)

Now， suppose we want to make it impossible for any set executables to be run from this file system。



![](img/e958fb31c58df4211b51efedd3baf726_24.png)

![](img/e958fb31c58df4211b51efedd3baf726_25.png)

We can apply the no Su I mount option。

![](img/e958fb31c58df4211b51efedd3baf726_27.png)

Now， running the program shows that set UI does not have any effect。

Real and effective U I D remained the same。But we can take it one step further。

Suppose you have a partition where your Web server has access to。 Now。

 if there's a vulnerability in your Web server， the attacker might write an executable to the disk to in vogue。

 So it'd be great if we could make it impossible for any program to be executed。So。

 let's change our amount options。To be no exactec。Now， if we try to run the program。

 We get permission to night。

![](img/e958fb31c58df4211b51efedd3baf726_29.png)

Even Ro can execute a program on this file system since it's mounted to no exactec。

What other amount options exist。

![](img/e958fb31c58df4211b51efedd3baf726_31.png)

There are a number of options， some of which can improve performance of the file system。

 while others can help you protect the system。

![](img/e958fb31c58df4211b51efedd3baf726_33.png)

![](img/e958fb31c58df4211b51efedd3baf726_34.png)

![](img/e958fb31c58df4211b51efedd3baf726_35.png)

Here， let's give the read only option a try。Now， our file system is mounted to know exactec and read only。



![](img/e958fb31c58df4211b51efedd3baf726_37.png)

Which can be quite helpful。 Consider that during the regular system operations。

 it is unlikely that anything under say s user needs to change。

It could prevent any possible compromise process， even when running with UI 0 from installing a back door into user bin by marking the entire file system hierarchy as read only。

So now。We can't remove any files。

![](img/e958fb31c58df4211b51efedd3baf726_39.png)

Not even Ruot Ken。

![](img/e958fb31c58df4211b51efedd3baf726_41.png)

Nor can we create new files。

![](img/e958fb31c58df4211b51efedd3baf726_43.png)

But， of course， like before， root can undo those changes。



![](img/e958fb31c58df4211b51efedd3baf726_45.png)

As we know with U at 0， a process can do anything on the system。



![](img/e958fb31c58df4211b51efedd3baf726_47.png)

This is by design， and as well as its necessity。

![](img/e958fb31c58df4211b51efedd3baf726_49.png)

However， we also have a need to run certain services with such elevated privileges。

 yet we want to be able to limit the damage Rogue E U I D 0 process can reak。



![](img/e958fb31c58df4211b51efedd3baf726_51.png)

One solution to this problem。

![](img/e958fb31c58df4211b51efedd3baf726_53.png)

Are so called secure levels， which have been around in the B SD family of Uni Systems for a while。

 and for which Linux， for example， has later gotten support。The super user can raise a secure level。

 but， and this is critical。 Even the super user cannot lower it。In effect。

 you are configuring the system such as certain things are not possible without lowering the secure level of the O S。

Lweing the secure level of the US requires a system reboot， however。

 so as a noisy and more likely to be detected and B terminate any current connections you may have。

 thereby requiring persistent access to the system for the attacker。Therefore are。

 secure levels defined。Permanently insecure mode。 so called insecure mode。A secure mode。

 and a highly secure mode。The restrictions enforced by the different secure levels are listed in the manual page。

 S model secure level。Some of the more interesting restrictions are those relating to app pen and mu file legss。

 as well as the ability to mount， unmountund or remount file systems。



![](img/e958fb31c58df4211b51efedd3baf726_55.png)

Here's what this looks like。As we said， we can mount a file system read only。

 and even route can't make changes。But， of course， root can re the file system in read write mode and then modify the files。

Be nice if we could keep even rude from making such changes。

Here we see the different secure levels described。

![](img/e958fb31c58df4211b51efedd3baf726_57.png)

For example， in secure mode， fire flakes may not be removed。



![](img/e958fb31c58df4211b51efedd3baf726_59.png)

And kernel modules may not be loaded。And in highly secure mode， you can't even mount new disks。



![](img/e958fb31c58df4211b51efedd3baf726_61.png)

So。Let's set the system imm mututable flag on new file。



![](img/e958fb31c58df4211b51efedd3baf726_63.png)

And mount the fire system， read only。

![](img/e958fb31c58df4211b51efedd3baf726_65.png)

Now， let's check what our current secure level is via the ciscotital command。Okay。

 we are in permanently insec mode， which is why we could make all the changes。



![](img/e958fb31c58df4211b51efedd3baf726_67.png)

But that also means that we can raise the secure level now。If we go straight to highly secure mode。

Then we can't change the flags on the file any longer。

And neither can we mount the file system in readr mode。We can unman the file system。

But then we Kent mounted back again。In secure level 2。

 there really is absolutely nothing we can do now， not even a route。

So let's lower the secure level back to negative  one。 All right， we can't do that either。

Once a secure level has been set， you can only raise it。 Never lower it。Not even at the route。

The only thing you can do to undo those changes is to reboot the system。



![](img/e958fb31c58df4211b51efedd3baf726_69.png)

Okay， let's summarize what we've learned in this video。



![](img/e958fb31c58df4211b51efedd3baf726_71.png)

SU and pseudodo can be used to grant others the ability to run commands as another user。

 but it can be difficult to restrict access。We can use file flags to restrict some access。

 We can mark a file as being append only or as immutable。On B SD derived systems。

 we use Chi flags for this。 on Linux systems， there is a chatdter command that acts similarly。

We can restrict entire file systems。 We can mark them as not allowing execution。

 as not allowing set U I D， or as being entirely read only。

And we can prevent Ro from undoing some of these changes through the use of secure levels。

Lweing secure levels requires a reboot of the system。

 which is rather intrusive and not often something an attacker can sustain easily。All right。

 this gets us to the end of this video。In our next video， we'll talk about restricted shells。

 sh environments and jails before we go back to looking at restrictions applied on the per process level。

Until next time， thanks for watching， G。

![](img/e958fb31c58df4211b51efedd3baf726_73.png)