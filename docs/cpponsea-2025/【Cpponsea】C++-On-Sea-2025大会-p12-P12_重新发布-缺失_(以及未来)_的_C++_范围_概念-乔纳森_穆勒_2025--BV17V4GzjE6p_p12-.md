# 【Cpponsea】C++-On-Sea-2025大会-p12-P12_重新发布-缺失_(以及未来)_的_C++_范围_概念-乔纳森_穆勒_2025--BV17V4GzjE6p_p12-

![](img/3b6621316fabf78322edb660cfbf6abe_0.png)

OK。So I'm going to talk about missing and maybe future C++ range concerts。

So just my my colleague who spoke here before， I also bucket at think so we are the world's leading business presentation software。

 we founded in 2002， we have over 1 million users at 25000 companies we set a plugin that seamlessly integrate into PowerPoint that makes it just easier to create presentations and charts and stuff like that So if you like have to do so many presentations we sort of like the market stand for lot this is done by reverse engineering so we essentially hack into PowerPoints and then we have like fancy algorithms to like do automatically that sort of thing we do everything into and we also heavily really support the superQ+ standardization process。

And at the core of our product is the think sell standard driving。

 it started out as like some sort of like just some couple extensions to boost and standard library。

 and it is heavily built arounds。😊，So it predates still ranges and 233 sort of started evolving like out of boost range two boost ranges but now it's like entirely different。

 it is similar to Fls in that we use cursors I'm not sure if you are familiar with that。

 not important for this talk but like unlike Fls we like used that only as some implementation details so the main interface are still iterators especially in public and I already can to talk about it two years ago with sequence pass now to present some general principles。

In this talk， I will focus on missing range concepts that we have implemented in the Tel Library。

 which I think would make sense to have in the state。😊。

Our implementation is constrained by the C++ 23 subset that is already implemented by MVC， however。

 for convenience I will use all C++ 23 and C++ 26 features just to make the slide code a little bit nicer。

 but in principle all of this has been implemented using C++ 23。😊。

I will also pretend that everything is in the Stoo Rangs namespace。

 so we'll just use the equivalent functions from St Rangs instead of our own ones just so you don't have to be familiar with that。

😊，And even though I'm now officially chairing the study group and the CP+ Committee that standardizes to train of。

 I'm not promising that any of this actually makes it into a standard array。

 just because I'm giving a conference talk about it。

 there's a bit more work and work for that and also other people have to agree that that's useful and even though I'm sharing I can't。

😊，I got the paper rejected that I wrote last week in the group that I was chair。😀は。😊。

So I will I have two problems the first problem is optimizations for better performance the second problem is meta programming for compiler magic。

 this is the part Me with here for and then if you're still here after that we can talk about some unresolved standard issues in the wording of the range specification。

😊，So it's truly something for everybody。So for convention。

 I will use STD view Fo View and STDR Fo Rangers and then potentially future extensions are in STD2V and STD2 just for presentations。

So let's begin with the first problem the example problem I came up with is we want to meet a file and we want to normalize all tap characters to four spaces。

😊，And this can be somewhat trivial done using a range pipeline so we first meet all file and this returns a range of all the characters in file and then we transform each character if it's a tap。

 we turn it into four spaces otherwise we keep it unchanged and like we're returning a stood string here but it like all fits in the small mobile optimization so we don't do any location and thiss just the most convenient way to turn a single character into potentially range of characters So I'm just storing the ministry the result of transform is a range of ranges so a range of still strings and we want a range of characters so we join them all back together using join this flattens it out and then we have a lazy thing we want to eagerly turn that into stood string so we call stood ranges two it's a sequence23 thing that takes the entire pipeline and construct the appropriate container out of it。

The only thing that's non standard is the read file function。

 so the read file function takes a path and returns an input range。😊。

And the comp looks something like this， so it's based around iterators and the iterators。

 we maintain a buffer of characters， so we don't want to like call the file API function for every single character。

 so instead we have a buffer the D reference operator of the iterator just returns whatever character we have in the buffer and then we increment it in the increment operator if we reach the end。

 then we will read more， fill the entire buffer， reset the pointers back to the beginning and continue iterating。

😊，This is like a nice way to like turn a file into it。Now， the first problem， yeah。

 if this is not actually something。 this is actually something that's in the standard。

 I just wanted to mention it because I think it's pretty cool。 and this is approximately size ranges。

So what we do at the end is bere calling still range2 into a still string。😊。

And if our range is sized， this is very easy， so we create an empty string。

 we allocate enough space for it by just asking the range for the size。

 and then we just copy all the characters from the range into the string and the end result is a string that contains all the characters。

😊，If you in a format range then we don't have a size so instead we call distance and what distance does it iterates over all the characters of the range and like we just count them and this gives us the size and then we call reserve and this is still more efficient than having the eager like reallocation be solved。

😊，So this is presumably about the implementation task。But if you're having an input range。

 then we cannot do a reserve because an input range can only be iterated once。😊。

And when we iterate over to compute the size， then we can't iterate over again to get the actual characters so we can't actually resolve。

 This means we have to do the frequent pushbacks。😊，And。This is what we're having here。

 even though wheat file is an input range and we can make it a sized input range because we can just query the file system for the size of the file。

😊，After the transform and the join， we have something that is no longer sized because the transform turns it into a sized input range of size ranges。

 like like one string for each character and each string is sized。

 but when we join them back together we have to sum all the sizes of the individual strings so we don't have a size at all so we lose size information。

😊，And this makes sense because we like expando tap into spaces and we don't know a prior how many space attempts there are in the fire right？

😊，But let's say that most of the files we deal with， they do not contain any temp。😊，Right。

 because we are like nicely formatted files。 Nobody put in any tap in there。

 And so this function doesn't really need to do anything。 And it would be nice if we could like。😊。

Ppaate this approximate size information， right？If you could propagate and say that， hey。

 after the join， we have approximately the same size as the input。😊。

And this is where the approximately sized range concept。 So if you have an approximately sized range。

 you can call this function rein and this is C+ plus 26 so we can call rein and this returns a hint that we can have to reserve and then we can implement in just two by calling rein。

 It's a bit unfortunate that the concept is called approximately sized range。

 but the function is called rein。 It used to be called approximate size。

 but then somehow in the standardization process one of them got renamed but not the other。😊。

Let's see what we can do about that， I think it's confusing。And this rein function。

 this essentially just one of these things。 so if the vector is sized。

 then it is approximately sized and you just return the size。 otherwise。

 we call resorin as a member function or as ADL lookup。😊，And then the views。

 they propagate approximate site。 so like views like transform or reverse or take or drop。

 they they all have enough information to compute the approximateized。

 So if you input is approximately size， the result as also approximately sized。But crucially a join。

 join doesn't do that because in general a joint can't， right， there is no inherent relationship。

But in our specific case， we know that we could propagate their approximate size。

 so we just need a facility to do that。😊，So we could imagine a very simple like weaponon that just webs an input range and also stores an approximate size。

 and then we just use that as soon as of it。😊，And then we can construct our approximately sized range。

 so we create the pipeline before the transform， and then we pass that size to the approximate size and then we join that together and then we turn that into a string。

😊，And this works， it's just a bit ugly because we have to like put the range into like a single variable because we're using it twice in there and we really break this nice pipeline。

😊，We can give it a slightly better interface by introducing the approximately unchangeded size range adapter。

 and this just says， okay， so we take the input range， we join it and this doesn't change the size。😊。

And then it's like more nice and elegant coat。And the implementation for that。

 it's a bit technical curve to you have like a ranger that the closure object。

 the whole pipeline thing is a bit messy and produces bad error messages。 And like。

 this really should be a language feature。 But the idea is。

 we've got this thing which takes the join as a constructor argument。 And then we remember that。

 And then we have to call operatorer， which takes the input range and we pass its reserve hint to the approximately sized thing and also forward it to the closure。

 And this does what we want。 It's just a nice weird functional stuff that that。😊。

Takes a while to forgot。They're just kept a job off it。quite of stuff apparently。

Actually let me disable even notifications。😊，Because I， this is like it's going in so much nice。

 I I don't have to be flooded。Anyways， I really like my job just for the record。😊，Yeah， yes nothing。

 lots of hiring， so。😊，O。something that is actually missing from the standard library generators。

 so this is the copyF I'm going to ignore the approximate size stuff for the rest of the talk just for on space issues。

😊，So this is the code that we have。 And it essentially does this imperative curve。

 Soll be having an infinite loop where we like。😊，Like if you brush write this imperatively。

 this is what you do。 So if there read more function that like read stuff into buffer。

 you get then get this buffer， if you're done， then you break out of the loop。

 Otherwise you iterate over each character in the buffer。

 you translate that by turning it into like a string， translate over each character。

 and then you do something with it。😊，In this case， we want to turn that all into。

And this is the equivalent imperative code that will do the same thing。

 right So the first couple lines， this is the read file， and then the loop of the function。

 this is a transform join。😊，Now， what does the actual ranges called do Well。

 we have itators So the iterators have state for the joint inerator we are having。

 so essentially be having like the current auto iterator and then an iterator into the current element of the auto range。

😊，So we have two iterators， one that advances over the autoer range。

 and then the inner one that advances over each element of the autoer range。

That transform just doesn't introduce any additional state besides the function object。

 which I'm ignoring here so just perhapss the base iterator。

 and then the read file iterator has little pointed。

The dereence operator for join is simply de the inner like de references the inaruator。

The one from transform， it falls to the base， but through the transformation function。😊。

And the one from the wheat also just meets from the bar。

And the interesting logic here is in the increment， so for join， we increment the inerator。

 if this reaches the end of the current element， then we skip over until we find the next non-empty range in the outer one and start producing elements out of this one so well reset in to the beginning of the next element in the out。

😊，Transform just transform like increments， the underlying it。

And a read valuewriter does something very similar to the join one。

 like it increments the element in the buffer， and if it returnss the end。

 we reset the buffers to the next element by calling the Me function。😊，So in the imperative code。

 we just have nest loops， but with the Xs we've got the state machine。😊。

Where we split the nested loops into like a weed step into an advanced step and then we have arbitrarily deeply nested safe machines in there right like the joint this is just two loops。

 but they're not represented as two loops instead we've got extra logic in the increment right。😊。

And this means that iterators inherently have some of it right they are not directly the nested loops。

 they are the state machine and for performance the optimizer has to recognize that their nested loops does all a bunch of inlining and to unrolld the state machine。

 so we will inherently have some of。😊，And stuff like join are like particularly problematic because join is just two nest loops but instead we've got the state machine con this con in these multiple ranges and is logically just n ranges in sequence。

 but instead the actual implementation involves like a variant of iterators and then we advanced the active one and if this reaches the end then we grab change the variant to point to the next iterator and like this is famously very involved。

😊，And then transform and filter， this is logically one loop with an if。

 but instead we've got the state machine which potentially like has to semantically do something that invokes the transformation function twice once in the decre and once in the de reference and once in the equipmentement。

 and so this is not efficient。😊，So why do we have state machines？

Where we have state machines because rangers have a pool model in a pool model。

 the range consumer is entirely in control right so you can have a range。

 you can get an iterator and then you can do whatever you want to fit like read one element。

 skip one， use one element twice， skip two elements。

 use it again and then we stop at this point and no longer want to continue between right the consumer is in full control。

😊，However， often this is completely unnecessary because you're just calling something like Foage。😊。

And in this case， you don't want any control。 You just want to give me all the elements right So we don't need control。

 yet we have it。😊，And every time we have a range based followup， we just use a regular rate followup。

 we represent the range by a potentially very complex state machine。

 and then this state machine is repeatedly advanced until completion。😊。

So the entire thing is a bit unnecessary because we don't need the state machine and reconstruct one and then just。

😊，Exhaustively enumourerate all the states。So better for this particular case is a push model because this one directly expresses the loop right then the range producer is the one in control because the range eager pushes value onto the consumer using a function object as a sync and the consumer just gets the values and has to do something with it。

 This is what you do invoage or in range based follow loop。

 you just get values and you do something with it， but you're not really in control over when you get them or skipping elements and stuff。

😊，And but what we really nice is a direct customization of the entire loop。

 so we don't need to express a loop as a stick machine。😊。

I a paper for that together with Barry a couple years ago to just say， okay。

 maybe we can like customize the Hb follow loop by having a customization function that takes the body of the for loop as a landda and then we pass that on and then we just invoked the lambda of all the values。

 this was unfortunately rejected。 And since then Barry who worked on the reflection papers has written a blog post and how he can do that with his like reflection macros so。

😊，The nice thing about a C pass is you don't really need language features。

 you can just build them with other language features but。😊，This is like still in the future。

 This is beli on talking injection， which isn't even part of C plus+ 26 yet。So I think so for this。

 we have a pure library solution。😊，Essentially， it's something like a for each vile customization mode。

😊，This takes the range at the sink， and it iterates around the range and costs the sink for each element as long as the sync returnss to。

😊，And the default implementation just uses to wait west flow right this is the default implementations。

 so we itte over all the characters or elements of our range and call the sync and if the sync returns false。

 then we propagate that through and continue stop iteration。

 otherwise we continue and we turn through at the end。😊，However。

 it's a customization point so we can provide better behavior for some ranges。😊，For example。

 for our transform view， we just implement， okay， so forage while and transform is just for each while on the base range。

 but then we don't invoke the sync directly instead we pass each element through through the transformation function because this is what the transform does。

 It just changes the elements of it。😊，Or for a join well the join is two loops。

 then we write two loops right like one loop over the outer range and then one loop over the inner each element of the outer range and we pass that one to the sink right so the end result is that we get each element join together。

 but we just build two loops instead of the state machine。😊，And for each file view。

 we can just bite the imperative code directly， right。

 you just beat the next buffer if the buffer is empty be done。

 otherwise we propagate each element of our buffer to the sink until the sink returns what。😊。

And that way we can directly express the loops without having to involve any iterators。😊。

And so we can then use this customization point in algorithm implementations like algorithm like for each copy transform。

 they are all essential loops， so they can all be metped directly to for each file instead of the range based follow up so they can completely avoid any iterator avoid。

😊，And then we also have the short circuiting loops， luckily the sync can like also stop it。

 so we can also implement stuff like all of or equal or contains which iterate until something changes and then we just return on falses from the sink。

 stop iteration and we have that。😊，And so if we were to use for each vi to iterate over the range pipeline instead of the iterator line。

😊，This happens after one level of inlining， so the join is the two nested loop。

 so after one level of inlining we get the custom implementation for join with the two nested loops。

 one over the auto range and then over each element of the inner one。😊。

If we do another level of inlining we inline the for each file。

 so the for each file of a string this just uses iterators because that's the most efficient way you can do。

 so we just get the default implementation。😊，If we inline again， be in line the transform stuff。

 so we know it it about the base of the bins and still have to do the transform so invoke the function on each element。

😊，And then if we align again， the base of the base is the meet so we get the for by code of the mutual code。

 and what we end up with after a couple of inlining is just the imperative code。😊。

So the transformation from the iterator state machine to the imperative code is not trivial。

 optimize us to see a lot of things， but before each while it's just inlining and compilers are really good at inlining that's like the most important optimization and just by repeatedly inlining small functions we end up directly with the imperative code and so don't have any iterator world。

😊，Now ask yourself， well， if you want to express loop using like ranges。

 like why not use the generator and code， right， you can just write the function that returns turns the generator。

 and then you can just write the imperative code and use each element that you want。😊，However。

 this doesn't solve the problem because proteinss are still eight machine instead of just you having to write them。

 the compiler writes them for you， right It's still the pull model。

 This is the entire point of having the proteins that you can stop at any point and still the pull model not the push model。

 And in addition， we also have like over like allocation that wouldn't be present with the its。

 So maybe proteins are better because the compiler generates the eight machine。

 and then it can nicer see through that， but then we also have over like allocation that needs to be lighted So if you want to do this proteins。

 we need better optimizations for the generator to have something like the push model a mode for the push model to generator。

And this is sort of the unfortunate thing where we've got stuff with natural syntax。

 but bad performance right so for each bioal is the equivalent of co yield。

 co yield has a natural syntax， but bad performance。

 and this is similar to havings receivers on co weight， like CO weight has nicer syntax。

 but it has worse performance， so we ended up with a library solution for that。😊，Now of course。

 if you want to optimize the rangers using generators like it's not all that simple like like don't just add the 4H5 customization button and use it and you're done。

 they are like complications for example when I want to reverse reverse is also just a loop but it goes backwards so maybe we need like a second customization point to go backwards we have to think so so we have for each5 reversed right and then most algorithms implement both of them and they just forward to the reverse version in the reverse case but this is like a lot of complexity。

😊，Then we have zip， so zip is a view that takes a bunch of inches and its over them in log zip。

 So if you zip like an index sequence into a container。

 you get each index of the container together with its element。😊。

But we can't implement that purely in terms of forage vi because before forage vi。

 you can only go over one at the time right so you can only use forage vi on one of them and the other ones have to use iterators because this is not implementable otherwise so there is some houristic which one should use the forage vi because if you have like a concad and the span it doesn make sense to have the foage vi implementation for the span because the cond ones to more expensive so you want to use the forage vi for the concad and then just use iterators to iterate over the span and so we have some houristics to pick for which foage vi implementation you use which add some more complexity。

😊，We cannot use it for find， right because find returns iterators and we don't have iterators。😊。

But maybe we can write a customization point that like。

Pa invokes the sync with an iterator and not the element。

 but then this might have like under the optimization because you have to reconstruct the itator in each iteration and so on。

😊，And then。It's a lot easier to make something arranged by just providing for each while。

 So maybe we could allow ranges that only have for each while and don't have its because it's just one function as opposed to bucking the intors and you can still do a lot of useful algorithms。

 So we have done that extensively at things so like we have many ranges that just provide for each while because you can still do iteration over them。

 which is what you want。 And only when you need more advanced stuff like finds or like actually need the pull model than we add ittor support because this is just so much annoying Td work to manually build out the technology。

😊，And then of course the entire thing doesn't work for with the range based follow up。

 so stood for each is optimized， but the range based followup isn't， which is really unfortunate。

 so eventually we will want a language solution for that so we can use the natural range based follow loop syntax without having to result to algorithms。

😊，Now， one convenient thing I want to talk about is that the common case。

 you just have think that always returnss to。And it would be annoying to always have to write retention so we can make that implicit right so if the sync returnss void。

 this means implicit to。😊，And we can also go one step further and say， oh。

 this means return turn two statically， so we turn two type。

 so we can compile and detect better the sync of does short circle。😊。

And so the default implementation actually checks the return type of the sink if the return type is void or tool type。

😊，Then we just invoke the sink unconditionally and don't meet the branch to check for early exit because we don't have early exit。

😊，Yeah， and then we just also statically return the tool type and there's a thing where we have to like like we want to keep it at the two types so we can change it properly but there's well there's some meta programming involved there。

😊，And this would be really nice with the control operator， this is another proposal by Bery。😊。

But you can just do something like West Tri operator which that handles all of this for you。

 but it's still stuck in the pattern。The second optimization builds on this。

Because let's go back just to string this to to string， right this is the logic。

 so we do the appropriate reserve and then we cop it up。But if you have a continuous range。

 then we can just call the special append member function， which takes a point to emphasize。😊。

And this can then do some min copy of the result。 So this is more efficient。

 this is more efficient optimization。😊，And this is nice for contiguous ranges like a vector array string must span。

 but many ranges aren't contiguous， but they only have contiguous chunks right so a deck of t is logically a linked list of arrays right so we have these contiguous blocks in a linked list so they're not contiguous range but huge parts of them are contiguous or if you con two vectors right the end result。

😊，It's not contiguous because you have two different memory blocks。

 but like each memory block is contiguous， Similarlyly。

 when you have a range of spans and you join them and also read file function。

 it's not a contiguous range， but like it reads into buffer and the buffer is contiguous right So we have contiguous chunks in there。

😊，And so some ranges have this natural segmentation into chunks。

 and it would be really nice if you could just express this and like optimize it accordingly。😊。

Because then we can do mem copy on the conuous chunks。

 even though we can't do mem copy the entire image。😊。

And the good news is we already expressed this chunk。

We already did that when we customized for each while， right this is for each while underjoangle。

 right。😊，Be called for each vi on each chunk of the joint view。

 right So if this we are joiningin of H of spans， each of those chunks is contiguous and weing for each vi on each contiguous chunk。

Similarly on the each file thing， we're calling for each file on each span we're getting from the buffer。

 so you naturally expressed these contiguous chunks based on the way we customized for each while。😊。

So a very simple tweak， we can actually have access to that。😊，So if we change our4age value to first。

 call the special chunk member function on the sink if it exists。😊，And if that one exists。

 then this means the sync knows how to handle the entire range at once and do a specialized algorithm。

 and otherwise we used the customization point and otherwise we use the default documentation。😊。

And it's crucially that the sync gets to customize first。😊，And then the range。

 because maybe the sync knows， oh， this particular kind of entry I can actually handle for my particular use case。

 so the sync knows better than the because the sync is the one that actually deals with it and only then does the range get to pick customization。

😊，So we can implement a special sync fostering ending。If it only gets a single character。

 it just quite push back， but if it takes an entire continuousuous range as a chunk。

 we can call a pen on this contuous chunk。😊，And then if we change our ranges to implementation to use foage while with this string appendda。

 we get this optimization essentially for free。😊，Because now if you call foage file on the joint range of spans with a string appendda。

 after a single level of inlinning join gives you the two nest loops and the inner foage file is conig is a span that the signals how to handle。

 so this ends up just calling the chunk member function which does the append of the entire chip。

 so just for free we get the ability to handle contiguous chunks of memory or whatever we want more efficiently。

😊，And this is really， really powerful。And so the standard currently uses ultra its and they're somewhat clunky。

 you have to like overload aer++ and you operator star even though you don't really care about that。

 and you don't have the ability to receive chunks， whereas things are just function objects that receive single elements and can optionally update chunks。

😊，So the standard really should embrace that， should support the output intor only like for backward compatibility and focus on chunks。

 appends using chunks and6s， because that way we can make so many optimizations just by getting the foage file just by having the ability to receive con。

😊，Now in our original example， unfortunately we don't have the ability to use trunks yet。

 so we've got the meat file which these is big contigious chunks， this is nice。

 but when we transform it we end up with not contigious range that contains tiny contigious chunks and so when we join that we have just a bunch of tiny contigious chunks。

 there's like one kg data data。😊，So yes， we have contiguous chunks， but they're not very big。

 so this is very useful。😊，Now we could rewrite this instead of using a transform a join。

 we could do a split inter joinin with。😊，So we take our input range and we split it into ranges at the tap character and then we've got each segment between the two taps。

 and then we join them together with another separator right and this will produce the big contigious chunks after other splitting and then the separator in between the tabs and if we don't have any tabs。

 we will just have an entire thing that is just the entire range because we haven't split it anywhere。

😊，And we can make joint view propagate this contigious trend properly。

 So this is the 4H viol implementation of join bi。 it calls for each on each element of the other one。

 but then there's the regular joint just test the 4 h vi on the inner one here we also put in the separator in between developments。

 so we can propagate the contiguousness no problem。😊，However， unfortunately。

 this example just doesn't work。😊，Because split requires a forward range。

 we be having an input range， so it just wouldn't compile and there's lazy split which handles input ranges。

 but because it's lazy， it cannot keep the contiguous chunks property。😊。

And said if we can't directly write the code like this。😊，Because we have having an input range。

 and then we can't just split it anybody。😊，However。

We are totally fine to handle link each continuoustiguous chunk off the file separately。

 we if we do that， then we just have the entire contiguous chunk and can just use contiguous chunks algorithms and then join them back together on the upper level。

😊，So instead of just having read file， we also need to function read file buffers and this returns a range of stpans。

 and then read file is just this joined together。😊。

And then when we implemented this in terms of read file buffers。

 we can call a transform that gets each contiguous chunk as a span。

 we then can propose as this one using split and join breath and the end result we have to join all the buffers back together and past data string and this implementation actually propagates the contiguous chunk properly because we are dealing with contiguous chunks inside the transform。

 this is then a range of contigious chunks of contigious chunks。

 which we join back together into a single range。😊，And this is really efficient。

And we actually don't implement read file instead of in terms of read file buffers。

 because you can implement read file buffers in terms of read file。😊，Like this。

 you just need a special forage by implementation that only takes the chunks in the sink and forward each chunk as a single element to the other language。

 and this is connected。😊，嗯。So with generators and chunking。

 we convert write to barely very efficient range of code that deals with entire chunks at the time and doesn't have the itoid output。

😊，Any questions at this one？O。So let's move to the second problem。

So a colleague was working on some SQL light database and he wanted some way to describe the schema in a compile term DSL and then generate the SQL statements to create the database entirely at compiler。

😊，So something like this， so you describe a table with some columns and then you just want to call people create and this gives you a string that you can pass to SQL to create this table entirely it compared。

😊，Now， there are two fundamental。 there's a fundamental plus classification。

 you have to deal with it。 And this involves the underscore T system there。

This is because when you're biting。A comp function， even though it is constable， for example。

 the arguments unconstable and this is what met when right so we can call a constant first string on a string that and pass it to a straight away。

 This works fine If a literal we pass it to a constants function， we use it as a conpiilor。

 but if you put the entire thing inside a constable function。

 then the string is no longer a constant expression so you cannot just use that in an intermediate constable function。

😊，So the arguments still aren't context but even though we are in a constable function。

 and this is just a fundamental by the model books right so even though we are doing anything at Compium。

 we can't instantiate stuff based on arguments within a constable function。😊。

So the solution is to embed the relevant information that you need in the type of the argument because the type of the argument that is a constant expression。

 even if in a constant function， and so I call this early compile time versus late compile time if you put it in the type you have access to it doing early compile times within the body。

 whereas if it's just the value， then you only have it at compile time after you return from the function but not within the body of the function。

😊，And so we need to express all our strings， we need to encode them into the type system so we can use them within a constable function。

😊，The second problem is pretty straightforward forward for strings， what's this code。

 but what's the size of ABC？It's four because ABC is an array of Cha。

 including an low terminator and it's just an array and just produces four。

 So like we need a special type of string lit anyway so we can use them with Ra this code。😊。

So we combine both of those problems into a lital range。

 So lital range just encodes the values in the type so it's a template。

 takes all the values and now the encodes in the type and then we can provide iters over them they just populate global areas somewhere put the values in there and let me use them and then we've got like user a different literal that takes a string like a bunch of like technical stuff but the end result is we've got something where we can call size on a T string liter and this actually gives the correct result and it is encode it in a type system so it is this size is a compile expression even within a contable function。

😊，So with that， we can tackle the real problems。So this is essentially what creates like this is the political problem want we do。

 We have our type， which is a string， we have a name， which is a string。

 and then we want to create create type name， right， put them together。

 have the end result via a string view and just use it。😊，Unfortunately， like like this doesn't comp。

 right， like you can't just add string interval and have a compile string。😊。

And what we really want to do is we just want to use the regular age algorithms because this is what we used to。

 this is the copyright， So what we want to do is something like coquet， so we concatet。

 the TC string which else， convert that into a straight array and return the result。😊。

And and like because we saw in a static constant expert。

 we can return a string view to it right because it's just embedded into the man。

So we just want to buy code like this。Now， the first problem is。😊。

Two for like two doesn't exist for database。Because like it takes the range。

 and then it has to put the size of the range in the return type。

 And like range is a parameter which does not constant。 this is the early re compact problem。

 So this just doesn't work。 right we cannot write a function like this to just。Inally。

 it's a template based on some property of the argument， right like this fundamentally doesn't work。

😡，Or does it？Because starting C press 26， it just works。This code compiles。

We create a cont of some ranges。😮，As innerner one time variable。

 and we can use its size in a constant expression。😊，And essentially。

 this is because of relaxation of the woods。😊，As long as you don't access any one time values。

 you can use local objects， you can use parameters in compile time code。😊。

And the size of a little range and the size of the concreted view。 So the size of the lit range。

 it just returns something like it doesn't exist any memorable and the size of the concreted view。

 it has like a tuple of ranges。 And then we want to sum them all together。

 And if neither one of the sizes actually excesses the element of the tuple。

 then we don't at no point to we actually access the onetime value of range。

 So the entire thing is just a constant expression。 and the entire thing just works。

 right And this is really weird。 but also really cool。😊。

Because we can just use compile and properties of our 110 values。And so。And so this code just works。

Right。We just need to encode that properly in the concept machinery。

 so we can introduce a concept called constant the size range or something like that。

 which is a size range， but we can also just use its size in a comp expression like we just have a run-time reference to range and we can constant size and the resulting thing is a constant expression and I just check that by instantiating the constant paper。

 which is like a generalized integral constant coming in sequence to 26。😊。

And then we can also provide a thing that just given the type of the range gives you its size right because we don't actually need to create a range of objects。

 We can just you know get a fake reference to it and use it a compile them。

 So just giving this type of the range if it context precise， we can just get its size。

 except we can't do it with decal while because you cannot call decal while I'm failing to bring a paper to that because with the changes。

 this could just work instead we have to do something a bit more technical where we have to cheat a bit and call decal well inside the decoal type and then we press that into a lambda and code the return type into the type system and then get it out of the decal type right。

😊，嗯。😊，I'm going to bring a paper to make this just work because this is just stupid。 But anyways。

 like like we now have dependent types or something， right。

For this talk I'm going to use this helper function which generalizes this pattern。

 it just invokes a function with some arguments and then does the same three but general。

 and then we can just say context per size is context spec of stood size of the range。

 so it just invoke stood size with a fake reference on range and then we get the type out of there。😊。

Anyways， this is C+ 26 I had to do that before C++ 26 which is also possible just not annoying so what we have is a constant precise customization point that you can specialize based on various types so we say the constant precise of stood array type and the constant precise size of any range that gives you an integral constant as the return type for size is the value of that integral constant and then some machine you need to propagate that tool right so it is possible before actually this is a C+ 23 feature I think even the dec bar stuff not even 26 but MSVC didn't support that that so I actually like do some stuff it's not too interesting it's just possible written in a block post if you can。

😊，But this means that we can implement two train just to far away， right， So we take a range。

 we instantiate the stood away by just using the size of the range at compilean because it's context precise。

 and then we can do that。 and then we just copy the without in there。😊。

This implementation just tested downside that stood away this requires a default constructor。

 right because we construct in a way which inherent requires a default constructor。

 but you can throw a bit more meta programming at the problem and generate and initialize all list of all the values and then you have stood away。

 The point is we can make it work。😊，And so we can write cut like this right to a createater object。

 we just conquer the string that dwells， turn that into st array， store that somewhere red lift。

 and then return turn that as a string wheel。😊，This is really nice。

 And this actually supporter like this part was supported of the box。

 I didn't need to change anything for this use case。

 It just works because we had this constant precise content。However。

The colleague didn't write talk like this。 So that us， we have to like do the spaces right。

 This is kind of annoying。 So we have cont with as an extension where where we just give a separator and then it puts the separator in between。

 That is not too much of a problem either it's just appropriately sliced cont。

 maybe put the separator in between the windows。 just works out of the box。

 I didn't have to change anything。😊，However， my colleague didn't he was conquered with either。

m because we also have qualifiers that we want to put in there in the when we create the Db and the qualifiers might be empty。

😊，So my colleague used con non empty with。Which first filled us out all the empty stuff and then concatenateates the wrist。

 and con non empty work costed me months of my life。

Because this was the implementation of Con non empty when I stopped。

We take the range the separator and all the ranges and then we call make range。

 so make range just takes a packck of ranges and turns that into a range so we can use range algorithms on it short the implementation data。

 we then filter out all the ones that are empty。😊，And then we join them together with a separator。

 So Concad non empty with isn't implemented in terms of Conca。

 it's implemented in terms of join just after filtering them。😊，And this book at time。

But the entire thing doesn't have a constant beside。😊。

Because we just lose the context per size information。

 even if all the input ranges have context exercises。

 we just lose the context precise size information and then we can't call two away because we don't have the size anymore。

So what you could do is you change the implementation to do some meta programming， so we have a pack。

 we filter out the empty ranges from the pack and then forward to Concad 5。😊。

And this is the implementation that I just gave my colleague so he could start working。

 but another colleague was like， yeah， but this is kind of ugly， can you make this work。😊，So。

I spend a lot of time making this work。So let's begin with make range。

 this was the implementation with make range when I started。

 so we make we just take all the ranges and turn them into straight away。😊。

So this just starts the pick inter， and then we can integrateerate on it。😊，However。

 each element of the resulting range has the same type because he put the all then it stood away。

 right， which means that if we have a fancy comp size lit， the result of make range is a span of con。

😊，So I've lost the size information。😊，Because they were previously encoded in the type system。

 but now I just have spare， so I've completely lost the precise information。😊。

So I need to have a range where we can just keep the individual type right。

 and this leaves to an implementation of make range does just make tuple。😊，However。

 a tool isn't range。Because。来。😡，But what the type of the like you have an iterator you index into it。

 like， what would their type P， right， It's a one time value。

 So like it would be some kind of variant， right， You can imagine a two iterator that returns a variant of all the types。

 right， But like this add a。 like this is， this is a nonstar。😊，However。

 what we could do with TO is we could implement for each vial for T。😊。

Because this one doesn't require iterators， and we just call the sink on each element of the tuole。😊。

This doesn't introduce any of it。Because we don't need to construct a variant at any point。

And this is a concept that we supported in the library。

 and I call it homogeneous ranges versus heterogeneous generators。😊。

So if you have for homogeneous range， R we have iterators。

 so can use begin in and end and optionally forage wire。😊。

But if you have hit a a genius generatornova， you only have for each one。😊，Hmogeneous range。

 you have a common range radio type for all elementss。

 but for hit withgene generator you have potentially a typed list of generator output types。

 because a triple has multiple output types。😊，This means that you're seemingly restricted in the algorithm of use you can use and because you have to essentially use a generic La when you iterate our heterogeneous generator because the lambda is instantiated with different types on each iteration。

😊，And so every homogeneous range is a homogeneous generator， but not vice vera。😊。

And Tple as a heterogeneous generator， we can just call for it while on aO， give it a templated laer。

 and then we do something with each element of the tool。

 and we can use like if cons expert to select between different types and like handle each type separately。

😊，We can also use index sequence， so index sequence is a compile time sequence of0 to n。

 we can pass that to4 each bio and then we get to each index as a compile time value。

 and this is like an early compile time thing， so we've got the value of the index sequence as an early compile time value and can do a fancy meta program。

😊，OrAlso if you want to do meta programming on checklists we give typelist for each wire。

 and then we just have a range of type identities and then we can just use general range views and algorithms to do fancy type based meta programming and this is how we do master our meta program。

😊，And thiss also where Me comes in。 So in his talk yesterday， he to do something like this。

 So he like built an emulator for those at 80 and he said， okay。

 so I've got all the upcodes and I want to decode each up code into like a function pointer and collect them all in a way and this isn't validy++ because we have the up code even though it' like early late compile time so we can't decode it and then we can't compile it like we can't do it。

😊，But just a couple tweak， we can instead iterate over make integer sequence and this gives us the intedu from 0 to 256 as a byte as a constant thing。

 we can then have the thing in the type system decocodeded early and compile that in the function pointer and we already implemented a two this2 array so this part just works。

😊，And his second implementation we went ahead and both the specialization for the instructions with the PE expansion。

 we can also just use major algorithms。 So make in sequence。

 we transform each bit into the appropriate function pointer by instantiating the thing at compile time。

 getting the execute function， turning that into Lada， collecting them all in and away。

 So this just works if you were using things cell stuff。😊，😀は哈。😊。

Other cool stuff you can do so filter view， this is the forage vi implementation of filter view called foage while on the base thing。

 but then skips some elements by not passing them onto the sink。😊。

But because we now have different types， we can do stuff like， hey。

 so it's the predicate one of those compile term expressions that doesn't actually require the one time value of the thing and then we can skip skip on it in concept by code and so filter based on like type information。

😊，And because we don't instantiate the sink on the type that burn't take。

 we can red like this so we can take it to， we can filter out all the。

 keep only the integers and turn that into a vector。😊。

And this just works because the filter just appropriately skips over the types at Compton and it's really cool。

😊，Not really relevant for this example yet， it's just really cool。😊，Anyways。

 with heterogeneous ranges， it means that were done with the first step。

 we have a compile size range with compile sized elements in concatetinon emptypath。😊。

The next step is filtered。And the filter we use compile and sized information because filter isn't a sized range。

😊，Because like this would be the size of filter， like we just count the elements that have a predicate。

 Unfortunately， this is like a loop and size has to be o1。😊。

Now problem we can do the favorite technically true thing by saying， hey。

 it has to be context precise size， now it's a1 because it's a compile term size range。😊。

It's just potentially a big one right it's just saying like all all algorithms the array are one because the size of the array is a compile size is constant right technically works but not nice。

😊，We can add another constraint and say， okay， so we're constantlyd and the predicate only depends on the type。

 not on the value。😊，And then this count if is an that's hopefully optimized because we just add a bunch of true faults。

😊，Atheically at compileder。But' still not quite。😊，And it would help me because I' have to do it before C++ 23 and so I have this variable template and like。

 okay， so especially my field of view， but then like I don't have access to the values like like I can't do it I can't do the count in there because I don't have the base over and I don't have the predicate。

😊，So I can do it and the reason I can do it is because it is not actually these constraints aren't actually enough to properly constrain the compile size of filter view。

😊，Because of something like conditional range， so quick deour， this is called I shown in an example。

😊，In another talk where we want to do some paint algorithms to take reverse all the words in a string so we start with Hello world。

 the end result is all the words are backwards， but still in the same model this is done by like splitting the wind into chunks。

 then transforming each chunk and then joining a pig together。😊。

And the problem with this code is that the transformation either returns the chunk or the reverse chunk。

 but these are different types， so it doesn't comply， right。😊。

And when easy fix is to eagerly turn the above string。

 And then it works because it's the same return type。 But this is an eager location。

 nice thing is to return conditional range。 This is something we have think So。

 It's not understand standard。 And essentially， it does a variant of two ranges。

 but a variant with iterator support。 So it can iterate over one or the other。

 depending on a one term condition。😊，And conditional range is a problem for fit。

Because if we have a tuple of ints compile sized and a tuple of doubles also compile sized。

 we can then create a conditional range based on some random value from the user and this is a range that's either over this tuple or the other one but it still compileum sized because most tus have the same size。

 so whatever the one time values be still of the same size it's just the values are different and the types。

😊，And so if you filter on types， we no longer have compbri。😊，Because if you say， okay。

 give me only the ins， then the answer is either0 or3， depending on the one variable。

 even though we have a compile time size range of compile time size ranges。 right， like。

 like we lost the size information after the filter。 It was preserved until there。

 and then we filter， and then we no longer have it。😊，So filter actually is only compile time size。

 if the range has a compile time size， the predicate only depends on types。

 and we know at compile time each type of the element so we can at compile time invoke the predicate。

😊，And this is where we students use a new concept called two generators。

So a twople generator is a tape that is a generator，34 each while， it is compileum sized。

 and we give it the two interfaces so we can get each element given the compile size index and can decootype that。

😊，And if you have a triplepleite generator， most views are upside of tripleite generator。😊。

And the tuple generator is essentially the random axis equivalent of a generator range。

 right because we have random access， not just the most model。😊。

And so this leads to this thing where you have generators。

 you can iterate over them before for each bio， if you have a triple generator。

 you can iterate over with the upcoming template for because template 4 essentially invokes get a whole bunch and if you have a regular range use a regular photo。

😊，And with two generators， we can finally make a filter of view compile type sized because what we're essentially just doing。

 we get all the elements， we take type the thing pass it to the predicate and then count that all up。

 And this is an entirely compile time sized expression now that just does some work at compile time to count all the types of there。

😊，And that took me away。But anyways， with this simple code， your filter of use is not compete test。

And while we are at it， we can now also implement gett for filter view。

 so we essentially can give filter view random access。

 provide that the random access happens at compile time， so the constant。

 because we just need to do some index translation from the auto index to the base range index where we just count of a skipped elements which we can do because the predicate works at compile time and so we can statically skip over the elements。

😊，And this means that。At this step， we are compile time sized range with compile time sized elements because the filter only depends on the type because it was compile time sized so we get all the information and so only the join we left。

😊，And for simplicity， I'm just going to consider join join B is essentially the same。

 which just we have to add them to separate。😊，So previously this was the implementation of join view size。

 So if you're having a sized auto range and each inner element of the range has the same constants per size。

 So if you're having a join of like a range of stood arrays of size3。

 then we can make join view compile size by just taking it or sized in general by just taking the size of the auto range and multiplying it with a constant。

😊，If they have different sizes， we have to add them all up， but if you know it compile them。

 they all have the same size， we can just add them multiply them together。😊。

But this isn't what we have right in our case， we have different sizes of each of the ranges because the ranges that they pass into concrete non empty。

 they have different sizes and you just know they're all non empty so we can't do this implementation。

😊，But we can do something with two ranges。 So if we don't have the same constant for size。

 but we're having a tu generator。😊，Then we can get a pe。

 get each element and sum all the sizes in a fault expression。And this doesn't involve a loop。

 so it's a1 because we're just adding all the sizes of each individual element essentially at comp。😊。

So nobody I ring up compile themselves sized。But at this point， when I was this。

 I had a bit of a dera view。Because I bought a very similar code just a couple days ago。

So in particular， the triple case for drawing。I want this called a couple days ago。In conquer。

The size of cont is just the size of each element in the concretet tuple。

 so cond range of ranges stored as a tuple and we just sum all the sizes and this is what we're doing here too。

😊，And the join for tuple， is the loop over the outer range with the loop over the element range。

 and the for each vi for conqued is the loop over the tuple and then the loop after each element because when is the tuple we can just implement both with 4 each vi。

😊，So a conquer is really just a joy of。😊，Because we join， we take a range of ranges。

 we join them together with a cond， we take a pack of ranges stored as a tuple， join them together。

 but the tuple is now a range。 So Concad is just a join of a tuple and that's。

 in fact how I change the implementation of cont So cond just delegates to join and then we have various specializations of join will depending on the power of the underlying range because cond view a slightly different properties So we need a special case some cases but the base case where we only having generators。

 not iters it's the same for both join and cond because cond is just a join of a tuple。😊。

And with that。I was finally done。And I could replace this ugly metaprochmy code with this nice ranges code that just works at compile time produce the compile time size ranges with all the essential power。

😊，And。This the upper code and the lower code。 they are the same algorithm right And I don't mean that。

 oh， they're isymorphic。 I mean， they're literally the same algorithm because what our compile sized filter and our compile size join do essentially is exactly this meta programming code just internally。

 It has to skip over elements at compile。 It has to do all the logic。

 And the end result is a join of a tuple， which is a concurd。 And so this is just the same code。😊。

And this means that my colleague who said， you shouldn't write this code。

 you should write this code was absolutely right， because after a bunch of library infrastructure updates。

 the extra code to make Cond non empty with work was just this。😊，And that's really cool。

I can just fell out of the pipeline and then can just use it a compile and have it done really nicely。

Anyways， when you sell a power pipe plugin。😊，I'm going to defer questions to the end because now it's time for some standards lower。

😊，Entirely different So this is some code that finds the smallest Fibonacci number that's greater than some threshold so we start with a sequence of infinite integers。

 then we transform them with the Fibonacci function which just computes the and Fibonacci number and then we just have all the Fibonacci numbers and now they' sorted and we want to find the first one that's smaller than a given value and so we just use P of。

😊，And this is also some code I gave him some another talk。

Now there's just a side problem of this code。If we carefully fully read the range requirements and the standards。

😊，The standard S arranged is an itertor at the Sentinel that designate the beginning and end。😊。

And this is done by having this I。 where like if I is equal to S， then the range is empty。 Otherwise。

 we have all the steps you reach by incrementing until you reach the sentence。 right。

 this is what the range is。😊，And to say a sentinel is reachable if and only if there's a finite sequence of applications of plus+ I that make i equal to s。

😊，Finite sequence。RightSo if you use aota unbounded， it gives you an infinite sequence of h address。

 So we have never reached the sententinel。 It's not the sententinel is not reachable and this is encoded because the type of S is。

 in fact， unreachable Sentinel。 So it is not a reachable sentinel。😊，So far are good。However。

 there's this other clause that says if S is reachable from I， I denotes a valid range。嗯。

The result of the application of laa functions to invalid Ras is undefined。😊，嗯。

This means that this code is unified behavior。We're having an invalid range。

 We're calling a allow function on it。 It's invalid because it's infinite undedefined behavior。😊。

This code is undefined behavior， we are an infinite range， we're calling take on it。

 this makes a defined finite range， but take is a standard layer function， undefined behavior。😊。

Discount undefined behavior， recalling a standard library function dot begin on ayota view。

 This is undefined behavior， It's an invalid range Disc you be recalling the de of ayota view undefined behavior。

😊，啊。So we took a poll when this was discovered in Hingberg in March at the Standard Sh meeting。

 and essentially we said the Standard Library should not provide facilities that only cause undefined behavior。

😊，And this past， like the extra poet had like slightly different wording。So。😊，How to fix it， Like。

 like how to change this building to， to make this because up， we have ayota view。

 You're supposed to use ayota view。 Like， it's kind of bad that this is afin behavior。

So let's explore the problem space。We're having two invalid ranges like code like this。

 So if you have a subrange of an array plus 10 to array， that is just true invalid range。

 don't do that。 If you have a subrange of back1 begin and vector2 that end。

 that is an invalid range Don't do that。 So these one should stay illegal。😊。

Then we having two infinite ranges， repeat 42， just repeats 42 forever， aiota of unssteinign 0 just。

😊，It keeps inementing the iterator， wraps around， go over forever through infinite range。

And then we have varianceers where dot and lies like ayota of int。

 because eventually you will have integer overflow。😡，So which is an uned behavior for int。

 so Aota isn't really an infinite range， it's just you pretended there's an infinite range by returning and reach percententinel。

😊，Likewise， if you just have a pointer and you you can construct the subb manually out of this pointer and the unmutable sententinel。

 and just to like trust me， I will only iterate as much as is valid right and these aren't really infr ranges。

 It's just like and candlealize。😊，And then we have range just where we don't know。

Ice stream meets characters from a string。 Is this an infinite range。

 Is a defined range depends on the stream。 It's the generator。 It type arrays the entire range。

 so we don't know how the size the infinite is。And so what even this infinitefinity， right， like。

 this is an infinite point。 repeatpe 42， this were pen，42，5。😊，Is this an infinite range？I mean。

 surely eventually the user will stop typing。W。But。But about this one。

 so this is a range that the range is done when the dice wall is six， like if you're really unlucky。

 right the range is never done。😊，And then you have to consider between like infinite usage and finite usage。

 So with infinite usage， you just， for example， a server， take some input， process it， write it out。

 and you just keep going forever forever because the server once forever。

Whereas if you combine like ayota with like something that is finite or in our finite of example。

 we're only looking at a finite crs because eventually the other range is exhausted or we find a condition that we care about So herell be having infinite ranges but we don't really use them to infinity。

 we just use them for finite like for all of those we could provide an upper bound but we are just too lazy to bite on so we have the embal aota。

😊，So let's come up with some definitions。So let's say we have an infinitefin。😊，There。

 no matter how many times you do plus plus I， you will not encounter undefined behavior and I equals S is false。

 and these are the two infinite ranges。 repeat， Iot have unsign， potentially ice cream。

 potentially is the generator， depending on what you're doing。😊，However， this is not aiota int。

 this is not the pointer of the unreachable sententinel and the two working range。

 so this captures half of the thing。😊，But the second case。

 we need to talk about maybe like unbounded Sentinel。

 So there's an infinite Sentinel is never reached。 and unbounded Sentinel is I equals S still false。

 but eventually you will encounter undefined behavior。 So the range is still finite。

 we just don't know。 So we have an infinite be represented as an infinite range。

 but there's only a finite graphicx that is actually usable， its just not determined a priority。

 And this is the aotta of an int right you can only in it like in maxax times before you encounter undefined behavior。

 So this is not infinite It's just unbound。 Similarlyly for the sub range and potentially for the steel generator。

The problem with this definition is that it is what。😊。

Because it also allows the subpoint area plus 10+ area。😊。

This is an unboned sententinel where we can increment at zero types and this would make it a valid range right Similarlyly the back one begin to vector2 end。

 you can increment it until you reach the end of V 1 and then you'll have undefin behavior and then you should stop right and in general we've just made any in sententinel pair where we can compare the two。

😊，E valid range。Which is that because we still want to reject thoses。

 like we want to have asserts in the separate constructor that like， hey。

 you are being vectors of two different innovas。 What what are you doing， right？

 So this definition is too broad。😊，So。Maybe we make it strict I'd say okay。

 so be having still the same semantics for un and Sentinel。

 but only the sententinel type unreachable Sentinel T makes it valid So ayota works at the subrange but not subrange the true infinite ranges because we're not using the unreachable Sentinel T right This is good。

😊，But we've also like， don't allow an our to generate that is the infinite of finite。

Because it doesn't have unmutable finity。 it just has some other type。

But like do we really care about generators， like like is there a difference from the ranges machinery between the infinite range and the unknowned range that has undefined behavior of ten0 iterations。

 or is it merely just an implementation detail of the generator the range algorithms don't need to care right like I don't have answers in the space like this is just me talking at loud about trying to fix this problem。

😊，And even if you decide this one， what I want a difference type？😊。

After we did plus plus I an infinite number of times， I minus begin doesn't affect an point of5T。😊，啊。

Do we care like for finite usage， it doesn't matter because we're constrained by something else。

 But if you're having an infinite usage， maybe you have an inertor from like way back then and then you just waited a couple hours and know your iters all the way over there and the distance is no longer representable。

But also this isn't really a new problem because pointer if0 on a 32 B system is like only 2 GB and you can reasonably have ranges that are bigger than 2 gig on a 32 bit system。

 right so。😊，This problem was always there， it just hasn't been properly specified until now。

Now a youta un is interesting because of light wraps around。

 So if the beginning is zero and they current't iterate us 4。

 what is the difference4 units max plus 4，10 times u max plus4。

 all of those could be like ballot add us for the difference because it wraps around and we don't know how many times it wrap around like we probably want to say oh。

 the difference is always like the smallest one and for cyclic credits but this all has to be specified and right now the standard just ignore it。

😊，And so once we did all that， then we want to have like a kneesizing hierarchy。

 so we we have size ranges with noun finite size， infinite ranges。

 which are the true infinite ranges where we know they're infinite and then just all the other ranges where they could be finite or infinite or unbounded and we just don't no staticically。

😊，And then we can do stuff like this。In C 26， we will have parallel range algorithms so you can say I want to do a parallel transform and this is the binary new transform that takes two ranges and invokes the function with one element from each and right now this example doesn't compile because transform the parallel1 request that both ranges are sized and ota of uns is an infinite unsized range so this is rejected but it's kind of stupid that this is rejected because we just pick the size of the other range because the otta one is clearly bigger and this actually motivated me to work on this problem。

😊，U。😊，Because we can just say， okay， the either above size or one size and the other one is infinite。

 and then it just also works。We can do optimization so if we have an infinite range and we take 10 elements。

 take does a about check， every iteration does a check herey， if we exhausted the underlying range。

 but if it's infinite we can omit that bo check and in fact there's going to be an unchecked take in the pipeline anyway where you know that to be than10。

😊，And so I wrote a paper to propose this and while this paper was discussed。

 I thought oh there's just I'm just going to introduce a new concept to infinite range and then we can be like wording in those cases。

 somebody pointed out that infinite ranges are actually amplifying behavior and maybe we should tackle that first and this made everybody really sad especially me because now I'm stuck to solving this problem which is not what I anticipated when wrote this paper so coming to a supers standard library in the next decade less amplified behavior than using。

😊，The day。So， to conclude。What should definitely be included in a search engine。Conditional range。

 it's a small helper， you're going to have any view condition range fits right in there just useful should be included。

😊，The voidage while customization point is desperately needed。

 it's just a hidden optimization that makes range algorithms usable in so many cases。😊，Similarly。

 we can then build sync based pandas on top of those and have better outputed generators and better performance and can do express chunking when we copy stuff forward。

😊，We also already have compile size range thanks to the C dash23 semantic changes。

 we just need a concept for it and then we can also add train tools that array because that is useful in subs situationsituations。

😊，And we definitely want to fix for infinite ranges。

 but like it's not really important because like in practice。

 it's fine like this is just the standard library specification is createdable。😊，However。

 the few generators， and especially the heterogeneous generators are probably not a good fit。 right。

 They are like wild departure from the existing range concept。 They don't have iters。

 You can't use the regular follow loop。 and the heterogeneous ones don't even have a single value type。

 Like like having two as ranges is nice， but it's like not really。

Like like it requires a lot of work， requires a lot of specification。 it's probably not worth it。

 and especially because with reflection， we can somewhat emulate them by instead of having a range of types。

 we can have a range of stood meter infos representing types。

 So the nice thing about reflection is that the meta info can represent anything It's completely untypeped and so you can just put them in containers。

 You can use range algorithms with them。 It's just a bit more of a cranky interface than having the type directly。

😊，So， anyways。If you wan to work on any of that proposals are welcome The study group providers。

 I'd say we are like， really small， like really nice， really welcoming。

 really good at spotting media edge cases。 You've completely missed in your paper。 But you know。

 we do that in a very nice and friendly way。 So if you want to work on any of that in the space。

 I welcome any of。 if you also like working in PowerPoint plugins that don't involve crazy meta programming。

 we also hiring。 So if you just want to use our range machinery。😊，We are hiring and thank you。



![](img/3b6621316fabf78322edb660cfbf6abe_2.png)