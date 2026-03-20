# 【苏黎世联邦理工学院】信息检索-｜-Information-Retrieval-｜-Eth-Zurich-2025-p21-P21_8._优化_(2_2)--BV1ndsBzdEss_p21-

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_0.png)

Welcome back， everybody。 So I told you that， well， actually。

 this is my least favorite lecture of the semester because I， I have the fitting。

 I'm just throwing things at you， like throwing the all these tricks at you。😊。

But let it serve as inspiration to， to on how to big systems and how to make the systems even。

 even faster。嗯。Anyway， I would like to， because of the clustering。

 I'd like to come back to this secret extension， because， of course。

 the reason why we are doing all of that， all of these slides that I showed you with the tricks。😊。

Is because some people， engineers are working very hard in such a way that nobody has to go through this。

And the people that do not have to go through this。

 they can just write SQL and create their indices and create their tables and create their vectors and use their queries。

 and everything will just be magically fast。😊，So you've seen in the DMMDB normally that you can make your sQel queries fast within Ds。

 right？ You remember that that you have hash inds，3 indices， who remembers this。

From the database lecture， most of you are right。It turns out that we can also build indices for the for the vectors。

 We can also have indices。 And I'm going to briefly go over two of them to show you what it's like。

But first， in the s syntax， for the people who have the luxury of writing sequel that don't need to worry about the details。

 It's just two lines of code。

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_2.png)

They just say create index on on the the， you know， the， the table using。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_4.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_5.png)

One of several indices。 So there's two of them that I show you。 So HN S W。

 hierarchical or nevig small world is one of them。 So you you say which kind of index you want。

 And then the the the column that you want to index。

 And then the operations that you want to to index on。 So you remember， you can have the L2 distance。

 the L1 distance， the cosine humming jackard and so on。 And so you have plenty of them to pick from。

 depending on what you want to index on。 And then once you have an index like this。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_7.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_8.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_9.png)

That you have built。 then the queries that I showed you earlier。The set from where using the。

 the the distance is going to be super fast。Cause the that's exactly the good of the index。Alright。

 so two of them that I very briefly go over。 Lets me start。 They have very strange names。

 So let me start with IVF flat， which which basically means inverted file with flat compression。

The ID is still this clustering。 you remember the clustering。

 the idea that you basically group the document by clusters in this way。Sorry， I。 I went too far。

So what you're going to do。Is cluster the terms？And then all of those that are similar are in the same。

Are in the same region。And then you query whenever， whenever you have a query。

 you look at the cluster in which you are， and then you。

 you look at the documents that are in this cluster a bit simplified。

 And so the index provides you an efficient way to to directly access the clusters and the associated list。

 right， So that would be IVF flat。 So connected to cluster two clustering in this way。

 But that's all I'm going to tell you because otherwise， after it's it's to advanced。

So that's the IVF Pla that uses this idea of clustering。And the other one， in fact。

 I would connect it to the skip pointers。 You remember the skip pointers that we used in the to。

 to quickly go through a posting list when theres a lot of documents that do not match。When， in fact。

 the second index is， is a generalization of the skip points in a way where you have some kind of layers where you have。

All of your documents in here， for example， you have the thats let's go。

 let's call it a small small path， right， that where you have to go slowly over them。

 And then you have a highway， you have the train and you have the plane， right。

 So this is the fastest route。 and every time to go to an upper layer， you remove documents， right。

 That is the idea of the skip pointer， right， the skip pointer directly skips to to a document farther away。

 Well， the idea， the difference between the skip pointer is that now we have multiple layers of skip pointers。

 right we have the small skip pointers， medium skip pointers and very large skip pointers。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_11.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_12.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_13.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_14.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_15.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_16.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_17.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_18.png)

And so the idea is that you can go down or up in the layer that you wish。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_20.png)

If you are on the upper layer， you will have a lower recall。

Going to very quickly call come to the recall and precision。 But I've already explained that。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_22.png)

At the beginning of the semester。 So you are going to have fewer results。And if you go down。

 then you have more results。 But the idea of of this is that on the fast lane right here。

 on the highway， you can very quickly navigate close to where you want to be。

 and then you go down and then you see what you find locally。

 That's really just like taking the plane to to let's say Vancouver and then you take a train to a city。

 maybe a few hundred of kilometers away。 and then you take maybe a bike to go to your final destination。

 It's exactly the same I here of very fast and then you go down in the layers。

 That is exactly what this H NS W index is actually doing。 It has all of these all of these layers。

 these are all the vectors right that you want to to to compute these sensors on。

 but it organizes them in these layers in such a way that here you have these very fast lane that very quickly。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_24.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_25.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_26.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_27.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_28.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_29.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_30.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_31.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_32.png)

You get to everywhere in the vector space。 And once you have gotten close to where you want to be。

 you go down a layer， down a layer。 And then you look at the local， the。

 the local documents that you have around you， Right？ So this is。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_34.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_35.png)

H。And SW。几。😊，High level。 I'm not going through the detail of implementation。So， to summarize。

IVF flat has to do with clustering。HN SW。Has to do with skip pointers。 but over the vectors。

 instead of over posting this， right， That's basically the very high level way to think about that。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_37.png)

But， of course， the reason for that is that nobody needs to think about that because they can just write these two lines of SQL and get that for free。

 And then everything is going to be super fasted。Okay， that is the the trick。

And now to conclude this， this。嗯。Series of slides。I would like to now， zoom out。

On everything we've been doing， because we have looked at so many things in the beginning of the。

 of the semester。 And， in fact， we have looked at， looked at enough things that we now have enough components that we can assemble into a full fledged information retrieval system。

 So I just want to show you that like everything you can do now。嗯。

So the architecture would start with reading the documents。And passing the documents， right？

 So for that， we've seen linguistic post processing。 You know， the product stamer and all districts。

 the tokenization in order to， to， to read the documents。

 turn them into tokens and then build the indices。

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_39.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_40.png)

Which index， withinve seen plenty of them， We have seen the standard inverted index and plenty of modifications of these indices。

 even the the by by world index K word index， Kgramm index。

 Permeter term index are not even all here。 zone indices， inexact top K retrieval。

 the Tered positional index that I've shown you the as as a trick So typically。

 you can build several of them doesn't have to be just one。 You build all the indices that you need。

 depending on your use case， depending on the queries that the people that you think the people are going to run on your on your system。

 right So you build all your indices。

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_42.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_43.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_44.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_45.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_46.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_47.png)

Now we've seen that in terms of query， we have plenty of solutions。

 You have the Boolean query language that we've seen at the very beginning。

 We've seen that we can introduce wild cardss。 We've also seen how to use indices to process these wild card queries。

 We've seen phrase queries。 and we've also seen the indices that efficiently process phrase queries。

 You remember the byword index， the positional index。 We've seen the queries。

 that are basically the libraries of the 80s right， where you have the title。

 the author and you type a term in each one that's actually close to relational database systems。

 When you do it in this way。

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_49.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_50.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_51.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_52.png)

And then we have the vector space model， super powerful。

 super hype at the moment with vector databases where we have the。All of these。

 all of these scop products to， to compute。 So these are all the queries that you can have in your system。

Typically， a system that indexes the Internet or or a huge collection of books is going to cache the documents somewhere。

 Why is that useful， Because when you display the query results。

 you like to show some snippets of the book like you show the term。

 and you show around the world that are around the term。 That's what you see in a Google search。

 right， So you still want a bit of a cache of the document somewhere。 The indices。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_54.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_55.png)

Then the query arrives， so you have to pass the query， depending on the query language you use。

 maybe spell correction， you also know how to do that， the peruter index， the kgrams， and so on。

 the also the based on the sound soundex algorithm， you can do some spell correction。

 and then you can query one or more indices doesn't have to be just one。

 you can use all the indices you want。

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_57.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_58.png)

In order to return results。 And so you are going to score and rank。

 So you have the intersection algorithm union algorithm for Boolean queries。

 We have the evidence accumulation pattern that you have for the scalaf products， right。

 where you see you accumulate the sum of the products of the TF IDfs over the terms for every document。

 And then you have the results to display。 You use the document cache to display the fancy results。

 including excerpts from the document， right。

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_60.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_61.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_62.png)

And， of course， all of that might be parameterized， right。

 You might have some weights that that that decide how your system behaves。

 and these weights might have to be trained separately in advance based on machine learning， right？

 So this is outside of the scope of this lecture。 But this is where machine learning can be plugged in。

 right， You， you can learn some of the parameters to do that。 And that gives us a full architecture。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_64.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_65.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_66.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_67.png)

For a full fledged information retrieval system。 right， So， of course。

 building something like that is a lot of work。 We obviously cannot make you build an entire system like this。

 But with the weekly practical exercises， the programming exercises。

 we make you touch a little bit of these things one by one to to。

 So you get a feeling of how of how it's done。😊，Right。😊，呃。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_69.png)

Okay， oh I would like to say one more thing because I proceed to the evaluation when I come to that when we have all of these vectors here。

In this lecture， and that's the way it was done in the vector space model。The vectors here。

Represents documents and queries， right， Every point here is a document， or is a query。In LL Ms。

 like Cha GPT， it's no longer the case。 We still have the vectors。 We still have these computations。

 We still have the vector database。 We still have these indices。

 We still have the scalar product and so on。 But the interpretation of these vectors is different。

And that's what he's called an embedding who has ever heard of that， an embedding。

Right so maybe you'll see it in the some of you， right。

 So you'll see it in the LLM lecture is basically the idea that whenever you have a world that basically means something。

 you can represent kind of the the meaning in a vector space。

 and a world is going to be close to other world that means similar dark things in the same vector space。

 But it's actually even more powerful than that， because you can even have the directions in which you go that means something to associate things。

Like， I don't know as a， as an example，A king win。Men， woman， father， mother and so。

 like it it basically associates。 you can， you can compute associations in this way that correspond to directions in the in the vector space。

 And that's that's very， very powerful。 So it means that even though you have learned these things in the context in which vectors are documents and terms that are basically our TF Ifs for every term coordinate。

This still applies to LL Ms just with a different interpretation。 So if you are interested。

 you can just register to the LLM quas and and take it from there。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_71.png)

It's very interesting topic， of which I'm not a specialist。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_73.png)

All right。Any questions so far。

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_75.png)

Okay， so let's move on to the next part。 You will see it's going to be easier。 So let's take it as a。

 as， as a small break before we go to the to the probabilistic information retrieval and language language models。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_77.png)

![](img/ae8b0355eb741a6eb1077e1e9c928c1c_78.png)

Not the large ones， the normal ones。嗯。Let me。Stopped the recording。



![](img/ae8b0355eb741a6eb1077e1e9c928c1c_80.png)