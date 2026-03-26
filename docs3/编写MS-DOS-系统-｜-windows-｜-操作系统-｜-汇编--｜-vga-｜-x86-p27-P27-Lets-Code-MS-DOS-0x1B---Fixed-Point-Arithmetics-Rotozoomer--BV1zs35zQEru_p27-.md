# 编写MS-DOS-系统-｜-windows-｜-操作系统-｜-汇编--｜-vga-｜-x86-p27-P27-Lets-Code-MS-DOS-0x1B---Fixed-Point-Arithmetics-Rotozoomer--BV1zs35zQEru_p27-

🎼Hello， welcome and a very good evening indeed， to our second part of the Roto Zuma， let's code MSOs。

🎼Well， the rotzuma is a nice effect that we saw last episode and it looks like this。

 you take a source image and map it to the screen while rotating and scaling it and last week we went a bit through the maths behind that how to program it how to program it sort of efficiently but still we need to tune up the dos box cycles up to like 50。

000 to show something which is a。I think a pensium level or something。

🎼So it's still quite slow because it heavily relies on floating point arithmetic。

 which is slow on everything 46 or below， even slower on machines without an FBU， but of course。

 so it's expensive。 however we already optimize the formulas quite heavily。

 so we try to pull out all of the arithmetic。🎼To the outside of the for loop so it doesn't get evaluated all the time。

 but there are some things like this which get evaluated for every scanline at least and we need to do a few additions。

🎼Every pixel even。🎼And while this is sort of fast， we can do better。🎼And most。🎼Certainly。

 the floating point arithmetics are what's making this very slow on older machines like 386s or 486s。

 Even the 46 has still a pretty weak FU。 so we want to get rid of that part。

And that means we need to do integer arithmetics。🎼Floating point is called floating point because the numbers have a decimal point。

 something like one point。 Oh， sorry。Something like one point。🎼0。

 and then times 10 to the power of something， let's say minus6。 that would be equivalent to 0。000001。

🎼And basically， you let the point float to wherever is necessary to。🎼Represent the number。

🎼So that it has a manissa of something between 0 and 1。 and then an exponent。

Which leads to pretty good accuracy。嗯。🎼It's very useful。

🎼But it also requires a lot of computations on the FPU side。

🎼The integer operations on those older CPUs like the 486 or 36 are much faster than the floating point。

 even when there's a co processor installed， the 486 comes with the co processor， the 386 and 36。

🎼Even the 8086 can have one installed。🎼But every floating point operationration is expensive。

🎼So an interteger operation will be cheaper。 So what we could do is we could say， well， we have。

🎼160 Bs， let's say we are coding 160 B dos mode here， which runs on 286es and even 8086es。

🎼So we have on let's。🎼Like this one， two， three， four， five， six， seven， eight bits。🎼Here and one，2。

3，4，5，6，7，8 bits there and we could just say， okay。

 let's say this here is the point and it's not a floating point it's a fixed point and it's always like this。

🎼We have 8 B here for the decimal part and 8 bit here for the integer part。 Maybe we have 7 B。

 and we have a。Sign bit in front。Which gives us a range of roughly -127。Point something。嗯。

Probably not0， but something like 0。9， I don't know what。2 plus。Whoops plus1 at 27 point something。

With8 bit accuracy here behind the dec point。And this will be faster because this will use only the integer arithmetics of the CPU。

 and that will be。Very， very much faster， much less cycles on the。

 on the CPU and than the floating point operations。Even more so。

 if your machine doesn't even have a floating point unit installed， for example。

 if you have an old 386， they would have an extra chip installed and most didn't。That's just a fact。

 the 46 was always within an FP U。 if it wasn't the S X variant。

 but the D X variant of the 46 always had an FPU， but still even there。

 it would be faster to do it like this。The problem is， of course， we can only。

Use numbers between -127 and 127， whereas with the。Floating point， we have a huge range。

 We can display millions， or even billions。With relatively good accuracy。But also。

 one floating point number will take up 80 Bs instead of 16 bit。 So it's much larger。

 we can store it as 32 or 64 Bs in memory， but still running this on a real mode 3。

86 or 286 requires quite a couple of cycles because it will have to use at least for。

cycles to shift the bits around。If you use a 64 bit double precision variable。

But enough of that talk。 So we w to do the fixed point。 What are the rules here， Well， basically。

 you can just add them and multiply them as normal integers。However， when you multiply them。

The you will have overflows basically left and right。 So you will have to be careful。 Plus。

 you have to renmalize them by shifting right by the amount of bits that you're using on the right side。

 for example， if you。If you used8 bits as the decimal part。

 or we are probably going to use 7 bits to make space for the sign bit， etca。

 and for overflow reasons。So we probably will normalize the number after multiplications by shifting right by seven bits which。

Will push the decal point from way over here back to its normal position， basically。

That sounds probably a bit abstract， but once you'll see the formulas， it will hopefully make sense。

One other thing here in the floating point system， weve just used the mass function。

 cosine and signine， etc cetera。 We need again， the sign tables for the fixed point。

 and I use three different sign tables， one with 256 entries。

One special one for the zooming part for zooming in and out。Which has an offset added to it。 I wont。

 I won't talk about this right now。 You can look it up later on the code。

 and I will link to the full code of both examples。

 floating point and fixed point in the video description。 Everything is on Github。

 so you can check it out and play with it。And it will probably figure out why I did that。

And we will also take one。Sine function with 512 as its range。

For the translation of the whole image to get more accuracy。

 So we have three look up tables instead of computing the sign functions on the fly。 Also。

 you already see here that I'm going use 7 bits of precision。 That's why I take 2 to the power of 7。

 which is 120。8， actually， -11927 as the scaling factor。 And here for the。

 I'm not sure what I'm using that for。Let me look that up。I'm actually， not sure。

Where I'm using that。For the translation， yes， that's what the translation。

 So I'm using 63 values here。Wherever I chose 5 and 12 here I don't know can you can play around with the design tables and see what occurs in what makes sense here。

If you're not sure what the sign tables actually are， I will link。

Now a card to the video where I talk about sign tables。

 basically it's to speed up computations and to have integer values instead of float values and just look them up in memory instead of having to compute them。

 which is very expensive。So similar code will now be written for the fixed point。

 So we have here the ifF use float。And怎m gonna。Actually。Undefins or renames to no float。And。Now。

 this else part will be active。 and the interesting thing here is we can basically write the same code as we have for the floats here。

 we will have a lookup variable for the cosine， the current cosine， the current signine。

 the current zoom vector and the current translation vector。But it won't be using this stuff。

 but rather using the lookup tables。 We will also have the pre computeutd J times signine and J times cosine。

 as well as the I times cosine J times signine and the other way around。

 which is basically our rotation metrics。But those will all be integer values instead。

 So let's go here。And write just that code。So those will be constant because they won't change during the loop。

We will use 16 bit sine integers because we can have positive and negative values。Which。

So I think fine。 We look the cosine up in the sign 256 table。By using the time as an index。

En the cosine is one quarter pi。1 quarter pi，1 half pi。Yeah， one half pi ahead。

 So we add one quarter of 256， which is 64， which gives us the correct phase shift to get the cosine of the sign table。

And that's that。And， of course， the same goes for the sign。 But here we can just take the。

Value at T itself。Modulular 256。 the modo is， again because we have to wrap around the sine function is periodic and we just saw one full cycle and every2 56 elements。

 at least for this table， it will repeat。嗯Furthermorethermore。

We will have to compute the translation vectors。AndFor that， we take the other signine function。

 the same zoom or sign zoom。And here we take just。The value at T modo 2，56。And。Oh， sorry。

Not the translation。 And that's actually the zoom factor， which makes much more sense。

Now we get to the translation parts。So。T X equals。Sign 512。Of T modular。

 And now we have 5 not 12 values。And a thing for the。W direction。

 we will take the cosine because then we will create like a circular movement。

In the translation of the image。Sine versus cosine always gives a circle ish feature。

 So1 quarter of 5，12 is 128。This gives us a cosine。And then we need to create， of course。

 the variables which will change J S and J C， which are the products of the。Run time variable， giant。

Signon cos。🎼And also， the variables for the rotation metrics， which are I C， J S and。IS S JC。

That should be correct， yes。Now we can initialize those variables。

 So JS and JC are the automost variables。And they are， basically。Just the same as up here。

 So let's just copy that and maybe correct it where necessary。Let's delete that。

 copy that over there。And actually， no， we can leave that。

 It's y times Y plus T Y times S and y plus T Y times C。

 It's the exact same because the math didn't change at this point。So next up， we run the for loop。

We again， initialize J with0。 We initialize the pixel。With the frame of a pointer。Plus。

 wherever the current pixels list， this is wide times the width of the image plus。The ex coordinate。

Furthermore， we will stop when J reaches our desired image height。🎼And every loop。

 we will increment J until we are finished， and we will move the pixel pointer。A little bit further了。

Namely screen with minus width of the image。Which I explained already last time。

 So that should be exactly the same as in the floating point case。 So there's nothing new。

 If you have questions about that， check out the last video， and it will。Hopefully become clear。

All right。Now it's time。 the inner loop， let's have a peak ur。 We initialized I C J S and。Highes J C。

And what you know， it should look more or less the same。It should be x plus Tx。

Times C minus Js and times S plus J。 C。 This is basically the rotation matrix evaluated at this point。

 We just need to incrementally update it。Nothing has changed yet。So now comes to the inner loop。

Now we loop over every pixel。I equals 0， and I is less than the width of the desired image。

And we increment I。Which is just fine。No comes the more complicated part Last time we had this lookup。

 which already looks a bit weird。 We had to multiply the rotation metrics by the zoom factor cast to an integer and do the modular operation so we don't run out of the image。

 but stay insert the image to get this tiling effect that We see a lot of small images。

And this is more or less， the same。Looks slightly different。So， u equals。Well。

 we take the ICJS value and now we need to renormalize it at first because we did a multiplication up here。

 so we shifted right by 7。Better to put。Parent is this around it because this operator is a very low priority。

So we will get the wrong answer if we don't do that。

 And then we multiply it by the zoom factor just as we did above。 But again， we did a multiplication。

 So that means we， again， need we normalize。 So we put another shift operator around that。

And this will give us the normalized number， again。

And now the last one is basically the same as above， but for speed reasons， I actually。

 and I know my the size of my image， I actually figured out that we can also use just an end operator with 0 x7 F。

What you would have to adjust。With the correct image size， but here。Yeah。

 if you know that you have such a small image， you can， you can use that to speed it up。

And that should be that， actually。The V operation will be similar， except of course， we use I S J C。

And that should do it yeah。The next part should be exactly the same。

 so we can copy all the pixel setting。And we can even copy the update of the rotation metrics if I were to press the right buttons。

Everything is here the same because they are just additions and they work in floating point。

 same as in fixed point。So here we go。 something is indented differently。 Why did I change something。

嗯。Oh， yes， I should probably have put that。Here， and。那该是比。Closing price over there。

 So that should be right。 Yes， so in the inner loop， we get the color from the image。

Set the pixel and if mode wise is enabled we double the pixel， so that's why this is there。

 and then we update the rotation metrics by adding the cosine and the signine。

It's exactly it's really exactly the same as in the13 point。

 So it's really not that hard to understand and that it should work the same。

 And same goes for the outer loop。 we update our J S and J C values。

 which are the products of J with the sine and the cosine。We can just put that there。

 and that should work。And that's actually。All there is。This is very little code actually。

 to make it run hopefully faster。Let's try to run it。

 remember that it looked already pretty smooth with 50000 cycles。 I haven't tested it。

 so let's see if it works。And it does。 And I think it looks smoother。 You see in the rotation。

 you can see a little bit of consization because we use only 7 bits。

 It looks a bit jerky while rotating。 But at the same time， it looks， in my opinion。

 really fluid even more so than with a floating point。Values。

 we can even turn down the cycles now and make it run。

This is roughly 486 speed ish around 20 to 30 MHz。 It's still slow。

 The best way to accelerate this now would be to rewrite this in assembly language。

And to actually use 32 bit operations，32 bit operations will make this incredibly faster and also more accurate because you can use much higher accuracy floating point。

 a fixed point， arithmetics so that you again don't get this stutter。🎼Alternatively。

 you could leave it in 16 B and rewrite an assembly language to get it maybe to run on a 86。

 but maybe you would need to switch to Mo Y with the pixelix doubling then， but still， I think。

🎼This already looks pretty neat， so this is the speed that we will get when we run it on my 486。

33 megaHs maybe a bit faster。🎼But I think for coding intuus C 2。

0 in 16 Bs in real mode this is actually a pretty good result without resorting to any assembly language and yeah maybe as a homework you guys can rewrite this using assembly language and 32 bit operations and then we can have like a benchmark and see that how much faster we can get this actually。

🎼And of course my 46 has an ISA card， it's probably fast enough it's a pretty decent card。

 but having a local bus card like a visa local bus or a PCI local bus will even make it faster。

🎼Anyway， this should show you that a lot of the demo effects that rely on floating point can actually be rewritten in fixed point arithmetics。

 but you have to be careful about the sizes of the numbers and the normalization。

🎼So having fast FPs on modern machines is actually a godsend。

 It makes a lot of coding so much easier to work with。 And back in the day。

 I didn't understand that because my math skills weret。🎼Good enough。

 etc but by now I can actually appreciate what the demo coders did when they coded stuff like this and I bet that Seity also uses fixed integeriththmetics I haven't checked the code again you can find it on GitHub both my code and especially the probably much better future crew code for this effect。

Well think from both stuff sources， you can learn a lot。🎼And for now， that's it， I think。

 make sure that you hit the subscribe button if you haven't。

🎼Click the like button of course and definitely leave a comment what you thought about this。

 Did you ever use fixed points of floating points， Do you know what that stuff is。

🎼Do you need more explanations I can delve into more depth， of course。

🎼And you can also support me otherwise on Patreon， Kofi or Paypal if you want to。

 if you have troubles at the moment， no big deal。 it's enough that you watch this stuff if you maybe watch the ads before that helps me also a bit。

🎼And I hope to see you in the next let's code episode。

 or maybe even the next video because that will probably be something very different。🎼But until then。

 I wish you a very good evening and say goodbye。🎼，🎼The。🎼，🎼あ。🎼。🎼ああ。🎼，🎼。🎼。🎼う。🎼。

