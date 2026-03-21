# 约翰霍普金斯大学《Web开发者的HTML, CSS, and Javascript》中英字幕 - P63：20_第38讲 第3部分 单个菜单分类页面编码.zh_en - GPT中英字幕课程资源 - BV1WzY6z9EUd

Yeah。

![](img/576d75de473058e86219d245d174d1f9_1.png)

In part1 and part two of this lecture， we're able to create the HTML and the CSS styling to lay out our single category menu items page in this lecture we're going to address the variability of the data that we display through using the gridit that we created in the previous parts。

😊，Now before we declare a victory over this page here。

 let's go ahead and add a whole bunch of these items inside the page。

 so here's one all the way down here and let's copy that and let's just make a space。

And that's going to be number three， it's going to be number four， number five， and number six。

 I think that's pretty much enough。Okay， so let's number them properly here。

Let's go all the way to the top here and the first item is D01。

 then the second item is going to be D02。The third item is going to be D03 and the fourth item is going to be D04。

Then， D，0，5。And finally， D0，6。Right here。So if we save that。

 go back to our browser we could see they're very nicely aligned。

 So you know the menu items are very nicely sitting here。 So if we squeeze the browser。

 let's see if they all aligned very nicely they're all nicely aligning and finally collapsing nicely as well if we collapse it all the way to the smallest screen extra small so they're all nicely collapsing all the way through even we could see our footer that we did before。

 okay one thing to test and this is a very good thing to test whenever you have content that you really have no control over In other words。

 I really have no control as to how large this description is going to be it's very possible the description is going to be pretty short it may be that this description will be pretty long and I don't know what what happens when the description gets taller than what my kind of row or this imaginary right now looks like Well I'm not sure what's gonna to happen。

 let's take a look So let's make for example， the very first item description much bigger。😊。

So let's go back to our code editor。 Let's go back to number one item in our menu right here。

 And let's just copy and paste this a couple of times。

 copypy and paste the description a couple of times。And save that， let's go back to our browser。Oh。

 and take a look。 Numb three is now kind of been pushed all the way to this side。

 It really it should have been sitting right here。 Ner three should have been sitting right here。

 Numb four should have been still in the second row。 So things are kind of messed up。

 So how do we take care of this problem。 Well， there's a couple of ways of taking care of it。

 Numb one is you could restrict what this text field is going to be like。 In other words。

 you could say that only so many characters， this is allowed to be or we're gonna cut it off we're basically just going clip whatever it is that doesn't fit in here according to our specifications。

 Now this is a pretty rigid approach。 and it's kind of hard to come up to the business owner to the restaurant owner and say。

 well， your descriptions can be longer than this。 even though it's really actually a good idea to kind of make them tight and nice and tight。

 nobody wants to read very long descriptions。 But the same time if our layout is now dictating to us how large a particular description of a menu item is going to be that sounds a little strange。

 So instead what we could do is we could fix this whole layout problem。😊，Now。

 why is this layout problem even happening to begin with？ Well， as you remember。

 the grid layout in the bootstrap， at least in the current version， is based on floating elements。

 So all these elements are being floated to the left。

 Well what happens when element floated to the left and something in front of it kind of gets too long。

 Well， it kind of starts wrapping。 Now it can't really fit in this row because its you know this thing is protruding over here。

 So the very next spot that it could fit is right here。

 And then this number4 element tries to float to the left of this and it can't because there's no moreoon。

 So it goes to the next line。😊，If you go back and review the lecture on floats。

 this is something that we dealt with and remember the clear property and this is basically what we're going to need to do here except bootstrap prebaked in its grid system。

 a special clear fix that kind of takes care of these problems So if we go to the bootstrap website and right now we're in the grid system portion of it you could see here it says responsive column resets what this is referring to is this specific problem where one column becomes bigger and the rest of the columns kind of get messed up and it's telling you here that in order to fix that need to add another div to your grid and this div basically has a class clear fix and then a qualification as to when this whole divff should even show up in this case for example they want only to show up visible XS block which means if they only wanted to show up when the screen is extra small in our case。

 let's take a look it really is happening on a large screen and this is happening on a smaller screen。

😊，It seems's happening on the medium screen here but if we get to this part since we're already stacking it。

 this doesn't make any difference so basically on the small screen it's not a problem。

 but it is a problem on the medium screen and definitely on the large screen so we could fix that by putting this type of a div right inside of our grid let's go back to our code editor and basically this is number one but we need it right after number two so number two is the one we need to clear。

😊，So right after grid cell number two， we're gonna to put a clear fix。

 but in our case we want it to be medium and we also needed to repeat it and have the same thing show up when it is a large screen as well So Lg So if we save that and go back to our browser let's take a look at our website and we could see here this clear it very nicely and of course we need to repeat this and insert this div after every second cell so we inserted one after this one insert and we need to now insert one after number four and after number6 So let's go back to code editor and let's actually do just that let's copy this div right here and after number this is number3。

 so we needed to insert it after number four here's the number four。

Let's go back right here and insert that there， so now if any of the descriptions of number three and number four get out of hand a little bit。

 we're still going to be good in terms of the layout and also we need to put this after number6。

 here's number six， let's scroll down a little bit more。

And we want to make sure not to make a mistake here right here after number six。

 we'll insert that div right there and let's go back to our browser and as we could see。

 things are still laying out just nicely if we squeezes and make this a medium size they're still laying out nicely so the whole row kind of gets pushed down row number two kind of get pushed down and still nicely aligned so you can see three comes before for it's not floating in the wrong way and everything else looks pretty good Okay so that concludes our single category page and really concludes the layout of the entire site we're basically done the only thing that's left to do is now dynamically insert the content that we need to insert into every one of these spots here under menu categories right now we only have lunch here and it's just sticking some random picture here over and over again。

 obviously want to have all this work much more dynamically but as far as the layout is concerned we're basically done。

😊。