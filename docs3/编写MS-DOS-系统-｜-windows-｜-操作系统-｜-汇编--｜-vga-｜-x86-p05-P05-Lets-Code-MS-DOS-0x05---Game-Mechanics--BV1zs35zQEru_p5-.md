# 编写MS-DOS-系统-｜-windows-｜-操作系统-｜-汇编--｜-vga-｜-x86-p05-P05-Lets-Code-MS-DOS-0x05---Game-Mechanics--BV1zs35zQEru_p5-

🎼Hello， welcome and good evening to。🎼Next part of our Let's go Dsstar series。🎼Last time we。

🎼Where at this point。Where we have two panels and。🎼그런 배 아요？🎼It's pretty nice。

🎼But no games so far and。🎼Today we're going to change that。

 We want to implement a lot of the game mechanics。 We will save a little bit like the scoring and game over stuff。

🎼For the next part， which might be the last part for this season， basically。🎼But。

🎼We will add some game mechanics today already。 And as you can imagine。

 we have two petddles there and there should be a ball right。

 So we will have in the end something that's similar to the classic pong game。🎼So， we need。

We need a ball。🎼We already have the structure for the player。

🎼Which has color position with the height， score and。🎼Something to back up our graphics memory。

🎼And will use that also for the ball here actually doing something like object oriented programming would be nice。

 but we don't have that now one copy。🎼The whole structure， because it will make the。

🎼Thing more concluded。 now will'll also not rename this this structure it will be。🎼Still player。

 But we will add something called the x and D Y D x and deta Y， which is the speed of。🎼The ball。

 we won't use the tro player。🎼At least not for now。🎼And only the ball will use that。So。

🎼This is just one additional thing。 And if you go to our main function。🎼Which is here。

🎼We will also add a ball。To our。🎼Players and yeah， here should probably say game object or something。

🎼a player and two players and a ball。🎼And we will copy of this stuff here for the player 1， player 2。

🎼We don't care much about。🎼嗯。The data thing。🎼But now for the ball， we just made it the same。😔，🎼Color。

 but it would obviously be much smaller。🎼This's might give five by five pixels。🎼And。🎼Yeah。

 we will place it in the middle of the screen。🎼Soスクイング。🎼唔系。🎼不是。🎼That's actually。🎼あ。

🎼Screen with the divide button。🎼And the Y position would be screen height。🎼But but two。

So it will start off dead center。🎼And then we have to give it an initial velocity。

🎼Let's say one pixel in either direction。🎼We don't care about the ball score。😔。

🎼But we do care about it。That got functionality。🎼And， of course， we will need to。

🎼The same way we did with the other stuff we need to。🎼真的是了。

🎼Store the graphics that we will over in the memory。🎼We will need to restore on every pro loop。

So this behaves exactly like every other player， which is very nice。と？

And we can use the same draw function。This is also very nice。 So doing this。

 we should have something being drawn。Yeah， okay， we did forget one thing。Didn't add the。

Last time we didn't at the。Color， right。Let's add that to the。Paette here。We are using color。嗯。

That's 2，5，5。And would add some sort of colour。Nice。We will make it great。2 for5 and then here。1。10。

Y， that's better。 So we can move it up and down。 and we have the ball in the middle。

 The ball doesn't do anything， right。Not yet， anyway。So what we will have to do here is。我。On that。so。

We need every roll loop， we need to update the position of the ball according to its。Speed。

 and we need to。Test， if it's like。Being caught by one of the parents。 So we say handle of ball。

Give it the ball pointer， but we will also pass both players in there。Because。

When we get to the border of the screen， we need to test if one of the players caught。The ball。

 right。So that's what we want to do。We need some kind of function that looks similar to this。

Let's put it， right。On top of this one here。It doesn't return anything it just wants。

Cllay a stretch ball。And a player structure， P1 and a player structure， P2。And what will it do。

Basically， we need to do two things。We need to move the ball。 That's pretty straightforward。

 We can just say。Come on， let's， let's call this just B。 Otherwise I will betyping most of the time。

So， the x coordinate will simply be。Incremented in in split plus， you can write。

Cant C red P X plus something。Or rather here。B deta X。But you can also take a shot。And。

 and just like this。B x plus equals B theelta x。And the same goes for。The y component， obviously。

We can also increment that。But now we have to check because we would were to run this。

The weird things would start happen。Thing would just move out and enter at the top or somewhere else。

 Very， very weird。So that's not what I want And it might even overwr everything in our memory。

Bad things will happen。So that's not what we're going to do。

 We will catch the ball whenever it touches one of the sides of the screen。そう。Yes。May exposition。

Its smaller than。We had an initial。I think we had。嗯。Mi she bought a 5。pl whatever。P are fives。

With this at this time。So if we are left of player， one basically。We need to check something。

We need to check something， and we don't have。Fally clue what this is actually called right now。

 So I just call it if does ball。Hit， player up。And we are asking， does the ball be。

Its the playapp want。And pivot us。 Then everything is fine， then we can。

🎼Direct the ball into the other direction， like very simple to do that。 we just say， well。

 the deelta x is now a negative of the deelta x， so it will move in the opposite direction。In future。

However， if that is not the case。🎼Then we know that the player did not catch them all。🎼Then we say。

 okay， player2 gets a point。🎼Explay one just lost。🎼And we start over over again。🎼你细。Again。

 start at the middle。🎼あ哈。🎼And。🎼Spre knowledge as well。🎼We also needs to reset the speed， I guess。

🎼Playear one loss， so we sent the stuff。I don't know。🎼I think it doesn't matter。

 let's say in this case， we send it off to the right again to player2。🎼I'm sure if that makes sense。

 but you can change that if you don't like it。And this one here as well。🎼This。

 this way could be randomized later on， but。We won't do that right now。🎼Okay， we have a case。

🎼Would be。🎼If we actually。🎼Probably hit。🎼Player 2。 So that's when the X coordinate red。🎼Its actually。

B than。🎼Speen with。🎼Minus our five pixel sets border。🎼マイナ。🎼系啊。🎼To what， I think。

🎼It should be roughly correct。🎼Well， let's see what it would look like。

 but I think this should be fine and it will be。🎼The same， except with a few changes。🎼S four k one。

🎼So we ask， does the ballhead player too， if so， we can。🎼Convert the movement of the ball。Otherwise。

 player one gets a point。🎼We reached the ball， and we swapped the。🎼There ball。🎼So， that's。

Really straightforward。🎼The only thing that's still needed。🎼Is。Very different thing。

🎼What is the white coordinate as well？🎼Neade something。

🎼So let's say the white code much is smaller than some arbitrary border。

 we could use the five pixels， but I use 10 so we can print something at the top。🎼Or this is。

🎼This is logical or in C。🎼The Y coordinate。🎼His bigger than screen。🎼H。

 and here we are hard to take the1 maybe we want to print something at the bottom as well。

🎼Learn very simply。🎼We。🎼Invert the Y direction as well。🎼That should be fine。

🎼It won't compile because。🎼We still have to implement。🎼We have to， we have to implement something。

 Just play a ball。🎼And weve at a parent this year。🎼So for now。

 I'm going to say some integer function。Does。🎼は。我食飞啊。🎼boy。The。🎼没有。Pstructure。

Ball and player structure。He。And for now， we just return true always， just for testing。

See what it will do。Now， you see。And it seems we are not using the v sink， or we are a bit slow。

Not sure about that， because I see Fler yet。Let's reduce the layout， maybe。Check that。

Cause we are definitely not。Coding very efficiently here。嗯。Will this be better。Seems better。 Now。

 this makes me a bit worrisome that we will have to。Do some more optd。Stuff here。

But maybe that's something for on the very last episode that we start optimizing our game。

Primature optimization is always added again。But we do have the wait for retrace。 Yes， that is fine。

We should be good here。But we are probably getting into problems here We are not fast enough。

But we can check。 Do we。We can switch to 286 and do some optimization for speed。

I'm sure if this will help at all。啊。It won't compile in all would。But it will， if I do this。

I don't want to see any difference anyway， right。Also， I think。We are too slow here。

I think we are to slow。 Let's see what the reflection is as。

I could feel that we are off there as well。Okay， never mind。

I would like to make the speed of this whole thing faster。😔，And I think we should do something like。

Paedddle speed。F treated it more easily。And wed just put it right at the top。Fine paddle speed we 4。

 Let's try 8。Like everything， but。Faster。That's more like it。Of course， a bit more， Jackggy now。你装逼。

But let's return to the， to the。Function， where we test for。Hitting the player。This will be。

Not overly complicated but。ALi bit involved。Let me check my notes before I write something stupid。

Actually， it's not that hard。We just have to check the y on it because we already made sure that the xon is fine。

So if the Y coordinate。スピカ。Then。The players。Like on it。

 we know that we might be somewhere inside the paal。And。As well， if we are inside the pal also。

 we need to check if the white coordinate。Minus the balls height。Must be smaller。呃。Plays。

 white coordinate plus the playerss。Right。If both are true。

 then we can be certain that we are pin of the pddle。And we can say， yes， we did hit， and otherwise。

We missed。Well， that should be easy enough。Ren。客奇。That did work， but we forgot， look at that。

We forgot to reset。Correctly， right。So。This worked。

 so the collision detection worked on the right side。

But then the reset happens in a very weird manner。Let's see what we did there must have been something wrong。

Yes。I mistyped。should备在这。ok。😊，Okay， just works。And promise we can't move the pedal， right。

The right pedal is that， oh， okay， so there might be some corner cases here。Where I'm。

I think I hit the pedal。Just now， but it registered in not hitting。

So we have to be pretty accurate here。啊，不给た。Okay。What we can do now is make the other pedal move。

We have our keyboard handling here in the main loop。And I don't quite like it。Because we have this。

 the switch block。Inside， nested。整 here。To be able to determine the special case。

I'm going to say it the following。If we have。🎼Key code 0。 I know that theres a special key。

 So I will simply shift the value by8 ps。🎼Which means the key code is no longer a bite， but。

🎼An integer。🎼So I will make K an integer。🎼And with a special key。

 it will look something like this Now。 it will look like 4，8，0，0 and 5，0，0，0。

🎼This way it can discern the special keys and still handle the normal key。🎼Also， I。

🎼To indent this correctly， although I really don't want to。🎼That makes it more readable And so。

🎼Review menu your program。🎼Thank we。🎼Will add some。🎼Normal， not special piece。To this handling。

For a plan2。🎼We're just。Cpy of the soil block。🎼And the nice thing is。

 if we take your nonspec key like。🎼W。🎼And。🎼S， so that you have like the gamema keys。Or there to。

 you can just bite the character there。🎼Very easy。 And then we just say， okay。

 this will update player2。🎼Make sure to replace all the player I want references of the player too。

And。我啦。2。🎼It didn't work。 It didn't work。 It didn't work。 We have a buck， I think。This time。

 it worked。It looks a bit weird， doesn't it。🎼I think the。The ball， sort of like。

🎼Goes inside of the paedal。 I think we forgot to。At the width of the ball。So。嗯。

🎼It's actually pretty hard to play against itself。い。🎼There's something wrong， but。

🎼It's in the handle all。🎼嗯。い。We need to add the。Bonn with here。AndThat should make it better。🎼Yeah。

 looks better。🎼Much better。🎼I we already have a nice game mechanic。So we also， in the background。

 we are already keeping track of the score。🎼But we're not printing anything。

 we don't have a gameover thing。🎼This will be something for next time。

 and we will also take a look if we can make any of this more efficient because we already saw and make stuff here bigger well run into problems with the vertical retrace。

🎼The permanent solution would be not to use something like this， but to use page flipping。

 but that will be for another season and a more complex game probably。Other than that。

 please share like and subscribe。🎼You learned， hopefully， something today。Again。🎼And yeah。

 leave a comment。🎼Subscribe and。🎼I'll definitely try to build on this stuff。🎼Goodod night。🎼う。🎼The。🎼。

🎼。🎼。🎼，🎼。