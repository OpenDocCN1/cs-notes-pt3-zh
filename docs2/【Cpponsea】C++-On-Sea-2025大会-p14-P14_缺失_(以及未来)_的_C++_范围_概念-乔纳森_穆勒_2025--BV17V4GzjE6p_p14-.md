# 【Cpponsea】C++-On-Sea-2025大会-p14-P14_缺失_(以及未来)_的_C++_范围_概念-乔纳森_穆勒_2025--BV17V4GzjE6p_p14-

![](img/a871a92de121a0dafcc04c73ca831928_0.png)

OK。So I'm going to talk about missing and maybe few Chelsea+ range concerts。

So just my like my colleague who spoke here before。

 I also bucket at thinkel we are the world's leading business presentation software。

 we founded in 2002， we have over 1 million users at 25000 companies we set plugin that seamlessly integrate into PowerPoint that makes it just easier to create presentations and charts and stuff like that so if you like have to do so many presentations we sort of like the market stand a lot this is done by reverse engineering so we essentially hack into PowerPoints and then we have like fancy algorithms to like do automatically layout that sort of thing we do everything in C+ and we also heavily support the CQ+ standardization process。

And at the core of our product is the think sell datadiv。

It started out as like some sort of like just some company extensions to booth and the standard library。

 and it is heavily built around ranges。😊，So it predates still ranges and 233 sort of started evolving like out of boost range two boost ranges but now it's like entirely different。

 it is similar to Fls in that we use cursors I'm if you are familiar with that。

 not important for this talk but unlike Fls we like used that only as some implementation details so the main interface are still iterators。

 especially in public and I already gave to talk about it two years ago with sequence pass now to present some general principles。

In this talk， I will focus on missing range concepts that we have implemented in the Tel Library。

 which I think would make sense to have in the stand。😊。

Our implementation is constrained by the C++ 23 subset that is already implemented by MVC， however。

 for convenience I will use all C++ 23 and C++ 26 features just to make the slide code a little bit nicer。

 but in principle all of this has been implemented using C++ 23。😊。

I will also pretend that everything is in the Stoot Rangles namespace。

 so we'll just use the equivalent functions from St Rangs instead of our own ones just so you don't have to be familiar with it。

😊，And even though I'm now officially chairing the study group and the CP press committee that standardizes to train。

 I'm not promising that any of this actually makes it into a standard array just because I'm giving conference talk about it there's a bit more work and work for that and also other people have to agree that that's useful and even though I'm sharing I can't。

😊，LikeI got the paper rejected that I wrote last week in the group that I was sharing。😀は。😊。

So I will I have two problems the first problem is optimizations for better performance the second problem is meta programming for compiler magic。

 this is the part Me with here for and then if you're still here after that we can talk about some unresolved standard issues in the wording of the window specification。

😊，So it's truly something for everybody。So for a convention。

 I will use SDD view Fo View and STDR Fo Rangers and then potentially future extensions are in SDN2 movie and SDN2 are just for presentations。

So let's begin with the first problem the example problem I came up with is we want to meet a file and we want to normalize all tap characters to four spaces。

😊，And this can be somewhat trivial done using a range pipeline。

 so we first meet off file and this returns a range of all the characters in file and then we transform each character if it's a tap。

 we turn it into four spaces， otherwise we keep it unchanged and like we're returning a still string here but it like all fits in the small buffer optimization so we don't do any location and there's just the most convenient way to turn a single character into potentially range of characters so I'm just storing the ministry string the result of transform is a range of ranges。

 so a range of still strings or we want a range of characters so we join them all back together using join this flattens it out and then we have a lazy thing we want to eagerly turn that into a stood string so we call stood ranges two it's a sequence plus 23 thing that takes the entire pipeline and construct the appropriate container out of it。

The only thing that's non standard is the read file function。

 so the read file function takes a path and returns an input range。😊。

And the quantum looks something like this， so it's based around iterators and the iterators。

 we maintain a buffer of characters， so we don't want to like call the file API function for every single character。

 so instead weF buffer the demo reference operator of the iterator just returns whatever character we have in the buffer and then we increment it in the increment operator if we reach the end。

 then we will read more， fill the entire buffer， reset the pointers back to the beginning and continue iterating。

😊，This is like a nice way to like turn a file into it。Now， the first problem， yeah。

 this is not actually something， this is actually something that's in the standard。

 I just wanted to mention it because I think it's pretty cool， and this is approximately size ranges。

So what we do at the end is bere calling still range2 into a still string。😊。

And if our range is sized， this is very easy， so we create an empty string。

 we allocate enough space for it by just asking the range for the size。

 and then we just copy all the characters from the range into the string and the end result is a string that contains all the characters。

😊，If you a format range then we don't have a size， so instead we call distance and what distance does it iterates over all the characters of the range and like we just count them and this gives us the size and then we call yourself and this is still more efficient than having the eager like reallocation that we solve。

😊，So this is presumably about the implementation task。But if you're having an input range。

 then we cannot do a reserve because an input range can only be iterated once。😊。

And when we iterate over to compute the size， then we can't iterate over again to get the actual characters so we can't actually resolve。

 This means we have to do the frequent pushbacks。😊，And。This is what we're having here。

 even though wheat file is an input range and we can make it a sized input range because we can just query the file system for the size of the file。

😊，After the transform and the join， we have something that is no longer sized because the transform turns that into a sized input range of size ranges。

 like like one string for each character and each string is sized。

 but when we join them back together， we have to sum all the sizes of the individual strings。

 so we don't have a size all so we lose size information。😊。

And this makes sense because we like expandound tap into spaces and we don't know a prior how many space attempts there are in the fire。

😊，But let's say that most of the fires we deal with， they do not contain any temps。😊，Right。

 because we are like nicely formatted files。 Nobody put in any tap in there。

 And so this function doesn't really need to do anything。 and it would be nice if we could like。😊。

Proppaate this approximate size information， right？If you could propagate and say that， hey。

 after the join， we have approximately the same size as the input。😊。

And this is where the approximately sized range concept。 So if you have an approximately sized range。

 you can call this function rent and this is is C+ plus 26 so we can call rein and this returns a hint that we can pass to reserve and then we can implement in two by calling rein。

 It's a bit unfortunate that the concept is called approximately sized range。

 but the function is called rein。 It used to be called approximate size。

 but then somehow in the standardization process one of them got renamed but not the other。😊。

Let's see what we can do about that， I think it's confusing。And this reorin function。

 this essentially just one of these things。 So if the winter is sized。

 then it is approximately sized and to just return the size。 Otherwise。

 we call reorin as a member function or as ADL looker。😊，And then the views。

 they propagate approximate site。 So like views like transform or reverse or take or drop。

 they they all have enough information to compute the approximateized。

 So if you input is approximately size， they result as also approximately sized。But crucially a join。

 join doesn't do that because in general the joint can't， right， there is no inherent relationship。

But in our specific case， we know that we could propagate their approximate size。

 so we just need a facility to do that。😊，So we could imagine a very simple like repar that just webs an input range and also stores an approximate size。

 and then we just use that as soon as of it。😊，And then we can construct our approximately sized range。

 so we create the pipeline for the transform， and then we pass that size to the approximate size and then we join that together and then we turn that into a string。

😊，And this works， it's just a bit ugly because we have to like put the range into like a single variable because we're using it twice in there and we really break this nice pipeline。

😊，We can give it a slightly better interface by introducing the approximately unchangeded size range adapter。

 and this just says， okay， so we take the input range， we join it and this doesn't change the size。😊。

And then it's like more nice and elegant code。And the implementation for that。

 it's a bit technical to you have like a ranger that the closure object。

 the whole pipeline thing is a bit messy and produces bad error messages。 And like。

 this really should be a language feature。 But the idea is we've got this thing。

 which takes the join as a constructor argument。 And then we remember that。

 And then we have to call operator， which takes the input range and we pass its reserve hint to the approximately sized thing and also forward it through the closure。

 And this does what we want。 It's just a nice weird functional stuff that that that。😊。

Takes a while to forgot。I're just got a job off it。Thanks some incredible of stuff apparently。

Actually let me disable even notifications because I this is like it's going and so much nice I know don't have to be flatter。

😊，Anyways， I really like my job just for the record。😊，Yeah， not lots are hiring。😊。



![](img/a871a92de121a0dafcc04c73ca831928_2.png)

O。something that is actually missing from the standard library generators， so this is the copyF。

 I'm going to ignore the approximate size stuff for the rest of the talk just for space issues。😊。

So this is the code that we have。 And it essentially does this imperative cut。

 So we having an infinite loop where we like。😊，Like if you retro write this imperatively。

 this is what you do。 So if the read more function that like read stuff into buffer。

 you get then get this buffer， if you're done， then you break out of the loop。

 otherwise you iterate over each character in the buffer。

 you translate that by turning it into like a string。

 translate over each character and then you do something with it。😊，In this case。

 we want to turn that all into。And this is the equivalent imperative code that will do the same thing。

 right， So the first couple lines， this is the read file。 and then the loop of the function。

 this is a transform join。😊，Now， what does the actual ranges called do， Well。

 we have itators So the iterators have state for the joint iterator we are having。

 so essentially be having like the current auto iterator and then an iterator into the current element of the auto range。

😊，So we have two iterators， one that advances over the auto range。

 and then the inner one that advances over each element of the autoer range。

That transform just doesn't introduce any additional state besides the function object。

 which I'm ignoring here so just perhapss the base iterator。

 and then the read file iterator has little point。The dereference operator for join is simply de comments dereences the inaruator。

😊，The one from transform， it forwards to the base， but through the transformation function。😊。

And the one from the wheatfall also just meets from the B。

And the interesting logic here is in the increment， so for join， we increment the inerator。

 if this reaches the end of the current element， then we skip over until we find the next non-empty range in the outer one and start producing elements out of this one so we reset in to the beginning of the next element in the。

😊，Transform just transform like increments， the underlying it。

And our read value writer does something very similar to the join one。

 like it increments the element in the buffer， and if it returnss the end。

 we reset the buffers to the next element by calling the Me function。😊，So in imperative code。

 we just have nest loop， but with the its， we've got the state machine。😊。

Where we split the nested loops into like a weed step into an advanced step。

 and then we have arbitrarily deeply nested shape machines in there right like the joint。

 this is just two loops， but they're not represented as two loops Instead we've got extra logic in the increment right。

😊，And this means that iterators inherently have some of it right they are not directly the nested loops。

 they are the state machine and for performance， the optimizer has to recognize that their nested loops does all a bunch of inlining and to unrollld the state machine。

 so we we will inherently have some of it。😊，And stuff like join are like particularly problematic because join is just two nest loops but instead we've got the state machine this con in these multiple ranges and is logically just n ranges in sequence。

 but instead the actual implementation involves like a variant of iterators and then we advanced the currently active one and if this reaches the end then we grab change the variant to point to the next iterator and like this is famously very involved。

😊，And then transform and filter， this is logically one loop with an if。

 but instead we've got the state machine which potentially has to semantically do something that invokes the transformation function twice once in the decre and once in the de reference and once in the equipmentement。

 and so this is not efficient。😊，So why do we have state machines？

Where we have state machines because ranges have a pool model in a pool model。

 the range consumer is entirely in control right so you can have a range。

 you can get an iterator and then you can do whatever you want to like read one element， skip one。

 use one element twice， skip two elements， use it again and then we stop at this point and no longer want to continue between right the consumer is in full control。

😊，However， often this is completely unnecessary because you're just calling something like Fud。😊。

And in this case， you don't want any control。 You just want to give me all the elements。

 right So we don't need control， yet we have it。😊，And every time we have a range based follow up。

 we just use a regular followup， we represent the range by a potentially very complex state machine。

 and then this state machine is repeatedly advanced until completion。😊。

So the entire thing is a bit unnecessary because we don't need the state machine and to reconstruct on and then just。

😊，Exhaustively enumerate all the states。So better for this particular case is a push model because this one directly expresses the loop right then the range producer is the one in control because the range really pushes value onto the consumer using a function object as a sync and the consumer just gets the values and has to do something with it。

 This is what you do in foage or an range based follow， you just get values and you do something。

 but you're not really in control over when you get the or skipping elements and stuff。😊。

And but what we really nice is a direct customization of the entire loop。

 so we don't need to express a loop as a stick machine。😊。

I a paper for that together with Barry a couple years ago to just say， okay。

 maybe we can like customize the Hb follow loop by having a customization function that takes the body of the for loopbe as a lander and then we pass that on and then we just invoked the land of all the values this was unfortunately rejected and since then Barry who worked on the reflection papers has written a blog post and how he can do that with his like reflection macros so。

😊，The nice thing on a super pass is you don't really need language features。

 you can just build them with other language features。😊，This is like still in the future。

 This is belies on talking direction， which isn't even part of C++ 26 yet。So I think so for this。

 we have a pure library solution。Essentially， it's something like a four each vile customization mode。

😊，This takes a range and a sink， and it its over the range and costs the sink for each element as long as the sync returnss to。

😊，And the default implementation just uses us the wait west flow right this is the default implementations。

 so we itte over all the characters or elements of a range and call the sync and if the sync returns false。

 then we propagate that through and continue stop iteration。

 otherwise we continue and we turn through at the end。😊，However。

 it's a customization point so we can provide better behavior for some ranges。😊，For example。

 for our transform view， we just implement， okay， so for each while on transform is just for each while on the base range。

 but then we don't invoke the thing directly instead we pass each element through to the transformation function because this is what the transform does。

 It just changes the elements of it。😊，Or for a drawing while a joins two loops so write two loops right like one loop over the outer range and then one loop over the inner each element of the outer range and we pass that one to the sink right so the end result is that we get each element drawing together but we just build two loops instead of the state machine。

😊，And for a each5 view， we can just bite the imperative code directly， right。

 you just beat the next buffer if the buffer is empty be done。

 otherwise we propagate each element of our buffer to the sink until the sink returns what。😊。

And that way we can directly express the loops without having to involve any iterators。😊。

And so we can then use this customization point in algorithm implementations。

 like algorithm like for each copy transform they all essential loops。

 so they can all be met directly to for each file instead of the range based follow up so they can completely avoid any iterator avoid。

😊，And then we also have the short circuiting loops， luckily the sync can like also stop iteration。

 so we can also implement stuff like all over or equal or contains which iterate until something changes and then we just return on falses from the sink。

 stop iteration and we have that。😊，And so if we were to use for each vi to iterate over the range pipeline instead of the itator one。

 this happens after one level of inlining so the drawing is the two nest loops。

 so after one level of inlining we get the custom implementation for drawing with the two nest loops one over the out range and then over each element of the inner one。

😊，If we do another level of inlining inline the for each file。

 so the for each file of a string this just uses iterators because that's the most efficient way you can do。

 so we just get the default implementation。😊，If we inline again， be in line the transform stuff。

 so we know it it over the base of the bin and still have to do the transforms so invoke the function on each element。

😊，And then if we line again， the base of the base is the so we get the for each by code of the me code。

 and what we end up with after a couple of inlining is just the imperative code。😊。

So the transformation from the iterator state machine to the imperativeative code is not trivial。

 optimize us to see a lot of things， but before each while it's just inlining and compilers are really good at inlining that's like the most important optimization and just by repeatedly inlining small functions we end up directly with the imperativeative code and so don't have any iterator world。

😊，Now ask yourself， well， if you want to express loops using like ranges。

 like why not use the generator and proteins right you can just write the function that you turns the generator and then you can just write the imperative code and use each element that you want。

😊，However， this doesn't solve the problem because proteinss are still state machine instead of just having to write them。

 The compiler writes them for you， right It's still the pull model。

 This is the entire point of having the proteins that you can stop at any point Its still the push pull model。

 not the push model。 And in addition， we also have like over like allocation that wouldn't be present with the its。

 So maybe proteinsotes are better because the compiler generates the state machine and then can nicer see through that。

 but then we also have over like allocation that needs to be lighted So if you want to do the proteins。

 we need better generators faster the generator to have something like the push model a mode for the push model first to generator。

😊，And this is sort of the unfortunate thing where we've got stuff with natural syntax。

 but bad performance right so for each bioal is the equivalent of co yield。

 co yield has a natural syntax， but bad performance。

 and this is similar to having incentives receivers on co weight， like CO weight has nicer syntax。

 but it has worse performance， so we ended up with a library solution for that。😊，Now， of course。

 if you want to optimize the rangers using generators like it's not all that simple like like don't just add the 4H5 customization button and use it you're done。

 they are like complications for example， when I want reverse reverse is also just a loop。

 but it goes backwards so maybe we need like a second customization point to go backwards we have things so so we have4 each5 reversed and then most algorithms implement both of them and they just forward to the reverse version in the reverse case but this is like a lot of complexity。

😊，Then we have zip， so zip is a view that takes a bunch of inches and its over them in lockstep。

 so if you zip like an index sequence and a container。

 you get each index of the container together with its element。😊。

But we can't implement that purely in terms of forage vi because before forage vi。

 you can only go over one at the time right so you can only use forage vi on one of them and the other ones have to use iterators because this is not implementable otherwise so there is some houristic which one should use the forage vi because if you have like a concad and the span it doesn' make sense to have the forage vi implementation for the span because the cond ones more expensive so you want to use the forage vi for the concad and then just use iterators to iterate over the span and so we have some houristics to pick for which forage vi implementation we use which add some more complexity。

😊，We cannot use it for find， right because find returns iterators and we don't have iterators。😊。

But maybe we can write a customization point that， like。

Pa invokes the sync with an iterator and not the element。

 but then this might have like under the optimization because you have to reconstruct the itator in each iteration and so on。

😊，And then。It's a lot easier to make something arranged by just providing for each while。

 So maybe we could allow ranges that only have for each while and don't have its because it's just one function as opposed to button the innovas and you can still do a lot of useful algorithms So we have done that extensively at things so like we have many ranges that just provide for each while because you can still do iteration over them。

 which is what you want And only when you need more advanced stuff like Fis or like actually need the pull model than we add iterator support because this is just so much annoying Td work to manually build out the state machine。

😊，And then of course， the entire thing doesn't work for with the range based follow up。

 so stood for each is optimized， but the range based followup isn't， which is really unfortunate。

 so eventually we will want a language solution for that so we can use the natural range based follow loop syntax without having to result to algorithms。

😊，Now， one convenient thing I want to talk about is that the common case。

 you just have a sink that always pretends to。And it would be annoying to always have to write with so we can make that implicit。

 right so if the sync's void， this means implicit to。😊，And we can also go one step further and say。

 oh， this means return turn two statically， so we turn two type。

 so we can compile and detect better the sync about does short circuit。😊。

And so the default implementation actually checks the return type of the sink if the return type is void or tool type。

😊，Then we just invoke the sink unconditionally and don't need the branch to check for early exit because we don't have early exit。

😊，Yeah， and then we just also statically return the tool type and there's a thing where we have to like。

 like we want to keep it at the two types so we can change it properly。

 but there's well there's some meta programming involved。

And this would be really nice with the control operator， this is another proposal by Barry。😊。

But you can just do something like Westtry Opera which that handles all of this for you。

 but it's still stuck in the pattern。The second optimization builds on this。

Because let's go back just to train this to stitch string， right this is the logic。

 so we do the appropriate reserve and then we cop it up。😊，But if we have a continuous range。

 then we can just call the special append member function， which takes a point to emphasize。😊。

And this can then do some min copy of the result， so this is more efficient。

 this is more efficient optimization。😊，And this is nice for contiguous ranges like a vector array string must span but many ranges aren't contiguous。

 but they only have contiguous strengths right so a deck of t is logically a linked list of arrays right so we have these contiguous blocks in a linked list so they're not contiguous range but huge parts of them are contiguous or if you con two vectors right the end result。

😊，It's not contiguous because they have two different memory blocks。

 but like each memory block is contiguous， similarly when you have a range of spans and you join them and also a read file function。

 it's not a contiguous range， but like it reads into buffer and the buffer is contiguous right so we have contiguous chunks in there。

😊，And so some rangers have this natural segmentation into chunks。

 and it would be really nice if you could just express this and like optimize it accordingly。😊。

Because then we can do the me copy on the coniguous chunks。

 even though we can't do the name copy the entire。😊，And the good news is we already expressed this。😊。

We already did that when we customized F each while， right this is for each while underjuangle。

 right？😊，Be called for each while on each chunk of the join view right so if this be adjoining of h spans。

 each of those chunks is contiguous and we'reing for each while on each contiguous chunk。😊。

Similarly on the read file thing， we are calling for each file on each span we're getting from the buffer。

 so you naturally expressed these contiguous chunks based on the way we customized for each while。😊。

So with a very simple tweak， we can actually have access to that。😊。

So if we change our foage file to first， call the special chunk member function on the sink if it exists。

😊，And if that one exists， then this means the sync knows how to handle the entire range at once and do a specialized algorithm。

 and otherwise we used the customization point and otherwise we used the default documentation。😊。

And it's crucially that the sync gets to customize first。😊，And then the range。

 because maybe the sink knows， oh， this particular kind of entry I can actually handle for my particular use case。

 So the sync knows better than the because the sink is the one that actually deals with it。

 And only then does the range get to pick customization。😊。

So we can implement a special sync fostering a ending if it only gets a single character。

 it just cut push back， but it takes an entire continuoustiguous range as a chunk。

 we can call a pen on this contuous chunk。😊，And then if we change our ranges to implementation to use foage while with the string appendda。

 we get this optimization essentially for free。😊，Because now if you call foage file on the joint range of spans with a string appendda。

 after a single level of inlining join gives you the two nest loops and the inner foage file is conig is a span that the signal how to handle。

 so this ends up just calling the chunk member function which does the append of the entire hook。

 so just for free， we get the ability to handle contiguous chunks of memory or whatever we want more efficiently。

😊，And this is really， really powerful。And so the standard currently uses auto its and they're somewhat clanunky。

 you have to like overload a pointer++ and your point star even though you don't really care about that。

 and you don't have the ability to receive chunks， whereas things are just functional objects that receive single elements and can optionally update to chunks。

😊，So the standard really should embrace that， should support the output intor only like for backwards compatibility and focus on chunks。

 appends using chunks and sixs， because that way we can make so many optimizations just by getting thevoage file just by having the ability to receive con。

😊，Now in our original example， unfortunately we don't have the ability to use trunks yet。

 so we've got the meat file which these is big contigious chunks， this is nice。

 but when we transform it we end up with not contigious range that contains tiny contigious chunks and so when we join that we have just a bunch of tiny contigious chunks。

 there's like one kg data data。😊，So yes， we have continuoustiguous chunks， but they're not very big。

 so this is very useful。😊，Now we could rewrite this instead of using a transform a join we could to a split inter join with。

😊，So we take our input range and we split it into ranges at the tap character and then we've got each segment between the two taps and then we join them together with another separator right and this will produce the big contiguous chunks after other splitting and then the separator in between the tabs and if we don't have any tabs。

 we will just have an entire thing that is just the entire range because we haven't split it anyway。

😊，And we can make joint view propagate this contigious trend probability。

 So this is the 4H viol proliferation of join bi it calls for each on each element of the other one。

 but then there's the regular joint just test the 4H viol on the inner one here we also put in the separator in between vis。

 so we can propagate the contiguousness in no problem。😊，However， unfortunately。

 this example just doesn't book。😊，Because split requires a forward range where I' be having an input range。

 so it just wouldn't compile and there's lazy split which handles input ranges。

 but because it's lazy， it cannot keep the contiguous chunks property。😊。

I said we can't directly write the code like this。😊，Because we have an input range。

 and then we can't just split it individual。However。

We are totally fine to handle link each continuoustiguous chunk off the file separately。

 we if we do that， then we just have the entire contiguous chunk and can just use contiguous chunks algorithms and then join them back together on the upper level。

😊，So instead of just having read file， we also need to function read file buffers and this returns a range of stpans。

 and then read file is just this joined together。😊。

And then when we implemented this in terms of read file buffers。

 we can have a transform that gets each contiguous chunk as span。

 we then can follow as this one using split and join with and the end result we have to join all the buffers back together and pass data string and this implementation actually propagates the contiguous chunk properly because we are dealing with contigious chunks inside the transform。

 this is then a range of contigious chunks of contigious chunks。

 which we join back together into a single range。😊，And this is really efficient。

And we actually don't implement read file instead of in terms of read file buffers because you can implement read file buffers in terms of read file like this。

 you just need a special voage file implementation that only takes the chunks in the sink and forward each chunk as a single element to the other language and this is connected。

😊，嗯。So with generators and chunking， we can write to barely very efficient range of code that deals with entire chunks at the time and doesn't have the itoid output。

😊，Any questions at this one？O。So let's move to the second problem。



![](img/a871a92de121a0dafcc04c73ca831928_4.png)

So a colleague was working on some SQL light database and he wanted some way to describe the schema in a compiler from DSL and then generate the SQL statements to create the database entirely at compiler。

😊，So something like this， so you describe a table with some columns and then you just want to call people create and this gives you a string that you can pass to SQL to create the table entirely it compared。

😊，Now， there are two fundamental， there's a fundamentally best classification。

 you have to deal with it。 And this involves the underscore T system there。

This is because when you're writing。A comp function， even though it is constable， for example。

 the arguments unconstable and this is what met when so we can call a constant string on the string that and pass it to stood away。

 This works fine If a literal， we pass it to a constants function， we use it as a conspiilor。

 but if you put the entire thing inside a constable function。

 then the string is no longer a constant expression so you cannot just use that in an intermediate constable function。

😊，So the arguments still aren'tcon but even though we are in a constable function。

 and this is just a fundamental by the model books right so even though we are doing anything at compileium。

 we can't instantiate stuff based on arguments within a constable function。😊。

So the solution is to embed the relevant information that you need in the type of the argument because the type of the argument that is a constant expression。

 even if in a constant function， and so I call this early compile time versus late compile time。

 if you put it in the type you have access to it doing early compile times within the body。

 whereas if it's just the value， then you only have it at compile time after you return from the function but not within the body of the function。

😊，And so we need to express all our strings， we need to encode them into the type system so we can use them within a constable function。

😊，The second problem is pretty straightforward forward for strings， what's this code。

 but what's the size of ABC？It's four because ABC is an array of Cha。

 including a low termulator and it's just an array and just produces four。

 So like we need a special type of string lit anyway so we can use them with Ra this code。😊。

So we combine both of those problems into a lital range。

 so lital range just encodes the values in the type right so it's a template takes all the values and now the encodes in the type and then we can provide its over them。

 they just populate a global area somewhere put the values in there and then me use them and then we've got like a user a different lit that takes a string like a bunch of technical stuff but the end result is we've got something where we can call size on a TC string lit and this actually gives the correct result and it is encode it in the type system so it is this size is compile expression even within a contable function。

😊。

![](img/a871a92de121a0dafcc04c73ca831928_6.png)

So with that， we can tackle the weird problems。So this is essentially what creates like this is the political problem want we do。

 we have our type， which is a string， we have a name， which is a string。

 and then we want to create create type name， right， put them together。

 have the end result via a string view and just use it。😊，Unfortunately， like like this doesn't comp。

 right， like you can't just add string interval and have a compile string。😊。

And what we really want to do is we just want to use the regulate algorithms because this is what we used to。

 this is the copyright。 So what we want to do is something like coquet so we concatet the TC string rituals。

 convert that into a straight array and return the result。😊。

And like because we saw it in a static constant expert。

 we can return a string view to it right because it's just embedded into the man。

So we just don to buy code like this。Now， the first problem is。

Two for like two doesn't exist for database。Because like it takes a range and then it has to put the size of the range in the return type。

 and like range is a parameter which is not context。 this is the early versus compact problem。

 So this just doesn't work。 right we cannot write a function like this to just。In。

 it's a template based on some property of the argument， like this fundamentally doesn't work。😡。

Or does it？Because starting in CP press6， it just works。This code compiles。

We create a cont of some ranges。😮，As in a one time variable。

 and we can use its size in a constant expression。😊，And essentially。

 this is because of relaxation of the woods。😊，As long as you don't access any one time values。

 you can use local objects， you can use parameters in compile time code。😊。

And the size of a little range and the size of the concreted view。 So the size of the lit range。

 it just returns something like it doesn't exist any memorable and the size of the concreted view it has like a tuple of ranges and then we want to sum them all together。

 And if neither one of the sizes actually excesses the element of the tuple。

 then we don't at no point do we actually access the onetime value of range。

 So the entire thing is just a constant expression and the entire thing just works And this is really weird。

 but also really cool。😊，Because we can just use compile and properties of our 110 values。And so。

And so this code just works。At。We just need to encode that properly in the concept machinery。

 so we can introduce a concept called constant the size range or something like that。

 which is a size range， but we can also just use its size in a comp expression。

 like we just have a run-time reference to range and we can constant size and the resulting thing is a constant expression and I just check that by instantiating the constant paper。

 which is like a generalized integral constant coming in sequence to 26。😊。

And then we can also provide a thing that just given the type of the range gives you its size because we don't actually need to create a range of objects。

 We can just you know get a fake reference to it and use it a compile them So just giving this type of the range if it context precise。

 we can just get its size except we can't do it with decal while because you cannot call decal while I' planning to bring a paper to that because with the changes this could just work instead we have to do something a bit more technical where we have to cheat a bit and call decal inside the decoal type and then we press that into a lambda and code the return type into the type system and then get it out of the decal type。

😊，Right。嗯。😊，I'm going to bring a paper to make this just work because this is just stupid。

 But anyways， like like we now have dependent types or something， right。for this talk。

 I'm going to use this helper function which generalizes this pattern。

 It just invokes the function with some arguments and then does the same thing but but general。

 and then we can just say context per size is context spec of stood size of the range。

 So it just invoke stood size with a pink reference on range， and then we get the type。😊。

Out of there。Anyways， this is C++ 26 I had to do that before C++ 26 which is also possible just not annoying So what we have is a constant precise customization point that you can specialize based on various types so we say the constant precise of stood array type and the constant per size of any range that gives you an integral constant as the return type for size is the value of that integral constant and then some machinery need to propagate that tool right so it is possible before actually this is a C++ 23 feature I think even the dec bar stuff。

 not even 26 but MSVC didn't support that that so I actually like do some stuff it's not too interesting it's just possible written block post if you can。

😊，But this means that we can implement st train just to phone away right， so we take a range。

 we instantiate this straight away by just using the size of the range at compile time because it's context precise and then we can do that and then we just copy the without in there。

😊，This implementation just tested downside that stood away this requires a default constructor because we construct in a way。

 which inevitably requires a default constructor， but you can throw a bit more meta programming at the problem and generate and initialize all list of all the values and then you have stood away。

 The point is we can make it work。😊，And so we can write cut like this right to createat our object。

 we just conquer the string that dwells， turn that into st array， store that somewhere red lift。

 and then we turn that as a string wheel。😊，This is really nice and this actually supporter like this part was supported of box。

 I didn't need to change anything for this use case。

 It just works because we had this constant precise content。However。

The colleague didn't quite talk like this but that we have to like do the spaces right this is kind of annoying so we have cont with as an extension where we just give a separator and then it puts the separator in between That is not too much of a problem either it's just appropriately sliced cont where we put the separator in between the windowss。

 just works out of the box， I didn't have to change anything。😊，However。

 my colleague didn't use was coned with either。Because we also have qualifiers that we want to put in there in the when we create the Db and the qualifiers might be empty。

😊，So my colleague used concrete non empty with。Which first filled us out all the empty stuff and then concatetates the wrist。

 and con non empty work costed me months of my life。

Because this was the implementation of Concurd non empty I stopped。😊。

We take the range separator and all the ranges and then we call make range。

 so make range just takes packck of ranges and turns that into a range so we can use range algorithms on short the implementation data。

 we then filter out all the ones that are empty。😊，And then we join them together with a separator。

 so Concad non empty with isn't implemented in terms of concat。

 it's implemented in terms of join just after filtering them mode。😊，And this book atron time。

But the entire thing doesn't have a constant exercise。😊。

Because we just lose the context per size information。

 even if all the input ranges have context exercises。

 we just lose the context per information and then we can't call two away because we don't have the size anymore。

😊，So what you could do is you change the implementation to do some meta programming。

 so we have a pack， we filter out the empty ranges from the pack and then forward to Cond 5。😊。

And this is the implementation that they just gave my colleague so he could start working。

 but another colleague was like， yeah， but this is kind of ugly， can you make this work？😊，So。

I spend a lot of time making this work。So let's begin with make range This was the implementation with make range when I understand it。

 so we make and we just take all the ranges and turn them into straight away。😊。

So this just starts a pick inter， and then we can integrateerate on it。😊，However。

 each element of the resulting range has the same type because he put the all then it stood away。

 right， which means that if we have or fancy comp themselves size lit。

 the result of make range is the span of con。😊，So I've lost the size information。😊。

Because they were previously encoded in the type system， but now I just have span。

 so I've completely lost the precise information。😊。

So I need to have a range where we can just keep the individual type right and this leaves an implementation of make range does just make twople。

😊，However， a tool isn't arranged。Because。来。😡，But what the type of the like you have an iterator。

 you index into it， like what would their type P， right， It's a onetime value。

 So like it would be some kind of variant， right， you can imagine a two iterator that returns a variant of all the types right but like this adds a away like this is this is a nontta。

😊，However， what we could do with TL is we could implement for each vial for T。😊。

Because this one doesn't require quite iterators， and we just call the sink on each element of the tuple。

😊，This doesn't introduce any of it。Because we don't need to construct a variant at any point。

And this is a concept that we supported in the library。

 and I call it homogeneous ranges versus heterogeneous generators。😊。

So okay for for homogeneous range， we have iters， so can use begin in that end and optionally forage wire。

😊，But if you have hit a genius generatornova， you only have for each one。😊，Hmogeneous range。

 you have a common range value type for all Ls， but for hit withgeneius generator。

 you have potentially a type list of generator output types。

 right because a has multiple output types。😊，This means that you're seemingly restricted in the algorithm of use you can use and because you have to essentially use a generic La when you iterate our heterogeneous generator because the lambda is instantiated with different types on each iteration。

😊，And so every homogeneous range is a homogeneous generator， but not vice versa。😊。

And Tple is a heterogeneous generator， we can just call for it while on a twople。

 give it a templated learner， and then we do something with each element of the tool and we can use like if cons expert to select between different types and like handle each type separately。

😊，We can also use index sequence。 So index sequence is a compile time sequence of0 to n。

 We can pass that to4 each vial， and then we get to each index as a compile time value。

 And this is like an early compile time thing。 So we've got the value of the index sequence as an early compile time value and can do a fancy meta program here。

😊，OrAlso if you want to do meta programming on checklists， we give typelist for each wire。

 and then we just have a range of type entitiesent and then we can just use general range views and algorithms to do fancy type based meta programming。

 and this is how we do master our meta program。😊，And this's also where met comes in so in his talk yesterday he wanted to do something like this so he like wrote an emulator what does that80 and he said okay。

 so I've got all the up codes and I want to decode each up code into like a function pointer and collect them all in a way and this isn't valid purpose because we have the up code even though as like only late compile time so we can't decode it and then we can't compile it like we can't do it。

😊，But with just a couple tweak， we can instead iterate over make integer sequence and this gives us the integer from 0 to 256 as a byte as a constant thing。

 we can then have the thing in the type system decocodeed early and compile that in the function pointer and we already implement a two this2 array so this part just blocks。

😊，And his second implementation we went ahead and both the specialization for the instructions with the PE expansion。

 and we can also just use range algorithms， so make in sequence。

 you transform each bit into the appropriate function pointer by instantiating the thing at compileton。

 getting the execute function， turning that into the La， connectinging them all in and away。

 So this test box， if you were using things and stuff。😊，😀はははは。😊，Other cool stuff you can do。

 so a filter view， this is the forage vi implementation of filter view called forage while on the base thing。

 but then skips some elements by not passing them onto the sink。😊。

But because we now have different types， we can do stuff like hey， so its the predicate。

 one of those compile term expressions that doesn't actually require the one time value of the thing and then we can skip on it in context by code and so filter based on like type information。

😊，And because we don't instantiate the sink on the type that burn't take。

 we can red like this so we can take it to， we can filter out all the keep only the integers and turn that interested vector。

😊，And this just works because the filter just appropriately skips over the types at Compton and it's really cool。

😊，Not really relevant for this example yet， it's just really cool。😊，Anyways。

 with heterogeneous ranges， it means that were done with the first step。

 we have a compile size range with compile sized elements in concatetment emptypath。😊。



![](img/a871a92de121a0dafcc04c73ca831928_8.png)

The next step is filters。And the filter we use compile size information because filter isn't a size range。

😊，Because like this would be the size of filter， like we just count the elements that have a predicate。

 unfortunately， this is like a loop and size has to be01。😊，Now problem。

 we can do the favorite technically true thing by saying， hey， it has to be context precise size。

 now it's a1 because it's a compile term size2。😊，It's just potentially a big one right it's just saying like all algorithms under the way are one because the size of the array is a compile size is constant right technically works。

 but not nice。😊，We can add another constraint and say， okay。

 so we're constantlyd and the predicate only depends on the type， not on the value。😊。

And then this count if is an one that's hopefully optimized because we just add a bunch of true faults。

😊，Atheically at compile。That's still not quite。😊，And it would help me because I' have to do it before C++ 23 and so I have this variable template and like。

 okay， so especially my field of view， but then like I don't have access to the values like like I can't do it I can't do the count in there because I don't have the base over and I don't have the predicate。

😊，So I can do it and the reason I can do it is because it is not actually these constraints aren't actually enough to properly constrain the compile size of filter。

😊，Because of something like conditional range， so quick detour， this is code I shown in an example。😊。

In another talk where we want to do some joint algorithms to take reverse all the words in a string。

 So we start with fellowello world。 The end result is all the words of backward words。

 but still in the same order。 This is done by like splitttting the wind into chunks。

 then transforming each chunk and then joining it back together。😊。

And the problem with this code is that the transformation either its the chunk or the reverse chunk。

 but these are different types， so it doesn't comply。😊。

And when easy fix is to eagerly turn the above ultrato string and then it works because it's the same return type。

 but this is an eager location nice thing is to return conditional range。

 this is something we have think so it's not understand and essentially it does a variant of two ranges but the variant with itta support so it can iterate over one or the other depending on a one time condition。

😊，And conditional range is a problem for fit。Because if we have a tuple of ins compile sized and a tuple of doubles。

 also compile sized， we can then create a conditional range based on some random value from the user。

 and this is a range that's either over this tuple or the other one but it's still compile sized。

 because most tuples have the same size， so whatever the one time values be still of the same size。

 it's just the values are different and the types。😊，And so if you filter on types。

 we no longer have compbri。😊，Because if you say， okay， give me only the ins。

 then the answer is either0 or three， depending on the ones value。

 even though we have a compile time size range of compile time size ranges like like we lost the size information after the filter。

 it was preserved until there and then we filter and then we no longer have it。😊。

So filter actually is only compile time size， if the range has a compile time size。

 the predicate only depends on types， and we know at compile time each type of the element so we can at compile time invoke the predicate。

😊，And this is where we need to use a new concept called T generators。

So a two per generator is a tape that is a generator， so we4 each while。

 it is compileum sized and we give it the two polys so we can get each element given a compile size index and can decootype that。

😊，And if you have a tripleplelect generator， most views are upside of tripleite generator。😊。

And the Tple generator is essentially the random axis equivalent of a generator range。

 right because we have random access。😊，Not at the mostmal。

And so this leads to this thing where you have generators。

 you can iterate over them before 4 each bio， if you have a two generator。

 you can iterate over with the upcoming template for because template 4 essentially invokes get a whole bunch and if you have a regular range use a regular photo。

😊，And with two generators， we can finally make a filter of view compile sized because what we essentially just doing。

 we get all the elements。 We take type the thing pass it to the predicate and then count that all up。

 And this is an entirely compile time sized expression now that just does some work at compile time to count all the types of there。

😊，And that took me while。But anyways， with the simple code。

 your filter of use now don't have themselves test。And while we are at it。

 we can now also implement gett for filter view， so we essentially can give filter view random access。

 provide that the random access happens at compile time， so the constant。

 because we just need to do some index translation from the auto index to the base range index where we just count a skipped elements which we can do because the predicate works at compile time and so we can statically skip over the elements。

😊，And this means that。At this step， we are compile time sized range with compile time sized elements because the filter only depends on the type because it was compile time sized。

 so we get all the information and so only the join we left。😊，And for simplicity。

 I'm just going to consider join joinbi is essentially the same。

 it just we have to add them to separate。😊，So previously this was the implementation of join view size。

 so if you're having a sized auto range and each inner element of the range has the same constants per size。

 So if you're having a join of like a range of stood arrays of size3。

 then we can make join view compile size by just taking it or sized in general by just taking the size of the auto range and multiplying it with a constant。

😊，If they have different sizes， we have to add them all up， but if you know it compile them。

 they all have the same size， we can just add them multiply them together。😊。

But this isn't what we have right in our case we have different sizes of each of the ranges because the ranges that we pass into concrete non empty。

 they have different sizes and you just know they're all non empty so we can't do this implementation。

😊，But we can do something with two ranges。 So if we don't have the same constant for size。

 but we're having a tu generator。Then we can get a pe。

 get each element and sum all the sizes in a fault expression。And this doesn't involve a loop。

 so it's a1 because we're just adding all the sizes of each individual element essentially at coned。

😊，So nobody ring up compact themselves sized。But at this point， when I wrote this。

 I had a bit of a data view。Because I bought a very similar code just a couple days ago。

So in particular， the triple case for drawing。I want this called a couple days ago。And can't get it。

The size of conquet is just the size of each element in the cont tuple。

 so cond range of ranges stored as a tuple and we just sum all the sizes。

 and this is what we're doing here too。😊，And the join for tuple。

 is the loop over the outer range with the loop over the element range and the for each vi for conquet is the loop over the tuple and then the loop after each element because when is the tuple。

 we can just implement both with for each vi。😊，So a conquer is really just a joy of。

Because we' joined， we take a range of ranges， we join them together with a concord。

 we take a pack of ranges， stored as a tuple， join them together， but the tuple is now a range。

 So Conqued is just a join of a tuple and that's in fact how I changed the implementation of concretet So con just delegates to join and then we have various specializations of join view depending on the power of the underlying range because con view a slightly different properties So we need a special case some cases but the base case where we only having generators。

 not iters， it's the same for both join and con because con is just the join of a tuple。😊。

And with that。I was finally done。And I could replace this ugly meta programming code with this nice ranges code that just works at compile and produce so the compile size ranges with all the essential power。

😊，And。This the upper code and the lower code。 They are the same algorithm。

 right And I don't mean that， oh， they're asymorphic。 I mean。

 they're literally the same algorithm because what our compile sized filter and our compile size join do essentially is exactly this meta programming code just internally。

 It has to skip over elements at compile。 It has to do all the logic。

 And the end result is a join of a tuple， which is a concurd。 And so this is just the same code。😊。

And this means that my colleague who said you shouldn't write this code。

 you should buy this code was absolutely right， because after a bunch of library infrastructure updates。

 the actual code to make concreted non empty with work was just this。😊，And that's really cool。

Like can just fell out of the pipeline and then can just use it a compile and have it done really nice。

Anyway， let me sell a power pipe plugin。😊，き出せ。I'm going to defer questions to the end because now it's time for some standards lower。

😊，Entirely different So this is some code that finds the smallest Fibonacci number that's greater than some threshold so we start with a sequence of infinite integers。

 then we transform them with the Fibonacci function which is computes scan Fibonacci number and then we just have all the Fibonacci numbers and now they' sorted and we want to find the first one that's smaller than a given value and so we just use Phi of。

😊，And this is also some code I gave him some another talk。

Now there's just a side problem with this code。If we can't fully read the range requirements and the standards。

😊，The standard says arranged is an iterator of the Sinel that designate the beginning and it。😊。

And this is done by having this I。 where like if I is equal to S， then the range is empty。 Otherwise。

 we have all the steps you reach by incrementing until you reach the sentence。 right。

 This is what the range is。And to say a sentinel is reachable if and only if there's a finite sequence of applications of plus plus I that make i equal to S。

😊，Finance sequence。So if you use aota unbounded， it gives you an infinite sequence of h address。

 So we have never reached the sententinel。 It's not the sententinel is not reachable and this is encoded because the type of S is。

 in fact， unreachable Sentinel。 So it is not a reachable sentinel。😊，So far good。However。

 there's this other clause that says if S is reachable from I， IS denotes a valid range。嗯。

The result of the application of laa functions to invalid Ras is undefinifieded。😊，嗯。

This means that this code is undefined behavior。We're having an invalid range。

 we're calling a library function on it。 It's invalid because it's infinite， undedefined behavior。😊。

This code is undefined behavior， we are an infinite range， we're calling take on it。

 this makes a def range， but take is a standard layer function， undefined behavior。😊。

This called undefined behavior， we're calling a standard library function do beging on aota view。

 this is undeified behavior， it's an invalid range。😊，This code。

 UB recalling the de of Ayota view undedefined behavior。😊，啊。

So we took a poll when this bus discovered in Hgenberg in March at the Standard Z meeting。

 and essentially we said the Standard Library should not provide facilities that only cause undefined behavior。

😊，And this past， like the extra poll had like slightly different wording。So。😊，How to fix it， Like。

 like how to change this building to， to make this because up， we have ayota view。

 You're supposed to use ayota view。 Like， it's kind of bad that this is a behavior。

So let's explore the problem space。We're having two invalid ranges like code like this。

 So if you have a sub range of an array plus 10 to array， that is just true invalid range。

 don't do that。 If you have a subrange of V1 begin and V2 dot end， that is an invalid range。

 Don't do that。 So these one should stay illegal。😊，Then we having two infinite ranges， repeat 42。

 just repeats 42 forever， aiota of unssteinign0 just。😊，It keeps ining thetor， wraps around。

 go over forever through infinite range。And then we have variances where dot end lies like ayiota of int。

 because eventually you will have integer overflow。😡，So it is un behavior for int。

 so Aota isn't really an infinite range， it's just we pretended there's an infinite range by returning and reach the sententinel。

😊，Likewise， if you just have a pointer and you， you can construct the subch manually out of this pointer and the unmutable sentinel。

 And just as like， trust me， I will only iterate as much as is valid， right。

 And these aren't really infr ranges。 It's just like end candleize。😊。

And then we have ranges where we don't know。Ice stream reads characters from a string。

 Is this an infinite range。 Is it defining range depends on the stream。 It's the generator。

 It type raises the entire range。 So we don't know how the size the infinite is。

And so what even this infinity， right， like， this is an infinite point。 repeat 42， this were pen 425。

😊，Is this an infinite range？I mean， surely eventually the user will stop typing。What。But。

What about this one， So this is a range where the range is done when the dice wall is6。

 like if you're really unlucky， right， the range is never done。😊。

And then you have to consider between like infinite usage and finite usage。 So with infinite usage。

 you just， for example， a server， take some input， process it， writes it out。

 and you just keep going forever forever because the server once forever。

Whereas if you combine like ayota with like something that is finite or in a finite of example。

 we're only looking at a finite crs because eventually the other range is exhausted or we find a condition that we care about so here'll be having infinite ranges but we don't really use them to infinity。

 we just use them for finite like for all of those we could provide an upper bound but we are just too lazy to bite on so we have the unbal ayota。

😊，So let's come up with some definitions。So let's say we have an infinitefinitycent。😊，There。

 no matter how many times you do plasma plus I， you will not encounter undefined behavior and I equals S is false。

 And these are the two infinite ranges。 repeatat， Iotta have unsigned， potentially ice cream。

 potentially is the generator， depending on what you're doing。However， this is not aiota int。

 this is not the pointer of the unreachable sententinel and the two work range。

 so this captures half of the thing。😊，But the second case。

 we need to talk about maybe like unbounded sententinel。

 So there's an infinite Sentinel is never reached。 and unboned Sentinel is a equals S is still false。

 but eventually you will encounter undefined behavior。 So the range is still finite。

 We just don't know。 So we have an infinite。 be represented as an infinite range。

 but there's only a finite graphicx that is actually usable。

 It just not determined a priority And this is theotta of an in right you can only implement it like in science before you encounter undefined behavior。

 So this is not infinite is just unbounded Similarlyly for the sub range and potentially for the still generator。

😊，The problem with this definition is that it is what。

Because it also allows the sub area plus 10+ area。😊。

This is an un sententinel where we can incremented zero types and this would make it a valid range right Similarlyly the back1 begin to V2 end。

 you can increment it until you reach the end of V 1 and then you'll have undefined behavior and then you should stop right and in general we've just made any in sententinel pair where we can compare the two。

😊，Eval range。Which is failed because we still want to reject those sticks。

 like we want to have asserts in the sub constructor that like， hey。

 youre being vectors of two different innovas。 but what are you doing， right？

 So this definition is too broad。😊，So。Maybe we make it strict I'd say， okay。

 so be having still the same semantics for un and Sentinel。

 but only the sentinel type unreachable Sentinel T makes it valid。

 So ayota works at the subrange but not subrange the true infinite ranges because we're not using the unreachable Sentinel T right This is good。

😊，But we've also like don't allow an our to generate that is the infinite of finite。

Because it doesn't have unreutable finity。 It just has some other。

But like do we really care about generators， like like is there a difference from the ranges machinery between the infinite range and the unknowned range that has undefined behavior after ten0 iterations。

 or is it merely just an implementation detail of the generator the range algorithms don't need to care right like I don't have answers in the space like this is just me talking at loud about trying to fix this problem。

😊，And even if you decide this one， what don't want the defense type？😊。

After we did plus plus I an infinite number of times， I minus begin doesn't affect an point of50。😊，嗯。

Do we care like for finite usage， it doesn't matter because we're constrained by something else。

 but if youre having an infinite usage， maybe you have an iterator from like way back then and then you just wait a couple hours and know your iterators all the way over there and the distance is no longer representable。

😊，But also this is really a new problem because pointer if0 on a 32 B system is like only 2 GB and you can reasonably have ranges that are bigger than 2 gig on a 32 B system。

 right so。😊，This problem was always there， it just hasn't been properly specified until now。Now。

 ata unci is interesting because it like wraps around。

 So if the beginning is0 and they current't iterate us 4， what is the difference，4 units x plus 4。

10 times un max plus 4， All of those could be like valid answers for the difference because it wraps around and we don't know how many times it wrap around like were probably gonna to say。

 oh， the difference is always like the smallest one and for  cyclingic credits。

 But this also has to be specified。 And right now， the standard just ignore it。😊。

And so once we did all that， then we want to have like a newsizing hierarchy。

 so we we have size ranges with noun finite size， infinite ranges。

 which are the true infinite ranges where we know they' infinite。

 and then just all the other ranges where they could be finite or infinite or unbounded and we just don' notheically。

😊，And then we can do stuff like this so。In C 26， we will have parallel range algorithms so you can say I want to do a parallel transform and this is the binary transform that takes two ranges and invokes the function with one element from each and right now this example doesn't op because transform the parallel1 request that both ranges are sized and Iota of unsigned is an infinite unsized range so this is rejected but it's kind of stupid that this is rejected because we just pick the size of the other range because the ioota one is clearly bigger and this actually motivated me to work on this problem。

😊，U。😊，Because we can just say， okay， the either above size or one size and the other one is infinite。

 and then it just also works。We can do optimization。

 so if we have an infinite range and we take 10 elements。 take does a about check。

 Every iteration does a check herey， if we exhausted the underlying range， but if it's infinite。

 we can omit that bo check。 and in fact， there's going to be an unchecked take in the pipeline anyway where you know that you be than1。

😊，And so I wrote a paper to propose this and while this paper was discussed。

 I thought oh there's just I'm just going introduce a new concept infinite range and then we can be like st wording in those cases。

 somebody pointed out that infinite ranges are actually amplified behavior and maybe we should tackle that first and this made everybody really sad especially me because now I'm stuck to solving this problem which is not what I anticipated when I wrote this paper So coming to a super standard library in the next decade。

 less amplified behavior I've than using。😊，The day。So， to conclude。

What should definitely be included in those ranges。Conditional range， it's a small helper。

 you're going to have any view conditional range fits right in there just useful should be included。

Thevoage while customization point is desperately needed。

 it's just a hidden optimization that makes range algorithms usable in so many cases。😊，Similarly。

 we can then build sync based pandas on top of those and have better output generators and better performance and can do express chunking when we copy stuff want。

😊，We also already have compile time size ranges thanks to the C23 semantic changes。

 we just need a concept for it and then we can also add range tools that array because that is useful in subs situationsitations。

😊，And we definitely want to fix for infinite ranges。

 but like that's not really important because like in practice。

 it's fine like this is just the standard library specification is created。😊，However。

 the few generators， and especially the heterogeneous generators are probably not a good fit。 right。

 They are like wild departure from the existing range concepts。 They don't have iters。

 You can't use the regular follow loop。 and the heterogeneous ones don't even have a single value type。

 Like like having two as ranges is nice， but it's like not really。

Like like it requires a lot of work， requires a lot of specification。

 it's probably not worth it and especially because with reflection。

 we can somewhat emulate them by instead of having a range of types。

 we can have a range of stood meter infos representing types So the nice thing about reflection is that the meta info can represent anything It's completely untypeped and so you can just put them in containers。

 you can use range of algorithms with them。 it's just a bit more of a crky interface than having the type directly。

😊，So， anyways。If you wan to work on any of that， proposals are welcome。 The study group parameters。

 I'd say we are like， really small， like really nice， really welcoming。

 really good at spotting mut edge cases。 You've completely missed in your paper。 But， you know。

 we do that in a very nice and friendly way。 So if you want to welcome any of that in the space。

 I welcome any。 if you also like working in PowerPoint plugins that don't involve crazy meta programming。

 we also hiring。 So if you just want to use our wage machinery。😊，We are hiring and thank you。



![](img/a871a92de121a0dafcc04c73ca831928_10.png)