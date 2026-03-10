# 2025LLVM欧洲开发者大会-p31-P31-How-to-bring-your-Neural-Network-into-Upstream-MLIR-Dialects--BV1EoE9zUEbG_p31-

![](img/4721fb76f4294da820a699f88670ffb1_0.png)

So today I'm going to talk about how to bring your neural networks into upstream MLIR elects。

Just a brief overview of what I'm going to talk about。 So first。

 I will define the problem that I'm going to present and what you will learn。

 Then the two dialects that we're going to target from the frameworks。

 And then I will go framework by framework on how to lower that to abstract dialect。 And at the end。

 you have a small conclusion。So why do I give this talk。When you look at discourse。

 beginners very often struggle to get their neural network into upstream ML art dials。

And I get it MR is not a compiler， but the tens of compiler stuff still is a very big part of upstream ML IR。

 And we should not forget that。And the newcomers， they want to play around with MLAR， try tiling。

 try different passes。 But the importers to get the neural networks into upstream dialects。

 They are not part of MR。 They live in different repositories and different projects。

And that's quite hard for a newcomer to get this fragmentation right。Also。

 when you look at typical compilers using MLR， you very often see this image here where you have like Pytorch。

 on X Xx， whatever。 And then an arrow to your compiler。 And it's kind of hidden magic the end。

 But from my experience， this part is very complicated and messes up your dependes very often。😊。

So I'm going to talk about how to bring a model to Linuxux or Tosa。

 I'm going to show you which projects you need to use for which framework。

 We have to find the code and examples and also some tips and tricks on how to use them。

I've used almost every single one of those。 So I'll also give you like a bit of my own experience。

 Take with a grain of salt might be different for you。 Also， very important， we have April 2025。

 and this might change in the future。 So keep that in mind when you look for a talk in a distant future。

😊，Let me give you a quick example of the two dialects we're going to target。

 So the first measure one is Leg。 And then that comes some two flavors。

 We have something called named ops and generic ops。

 and named ops are just syntactic sugar for specific generic ops like a ma， things like that。😊。

I would say it's the main culture and dialect Ma art。 It's probably right。

 Maybe one of the most used ones and。The input frameworks I'm going to show most often try to lower to the named of variants just to preserve a bit more information。

And then below， you have a small example of Lg。On the other hand， you have Tulsa， which is the。

 which stands for Ten operator set architecture。 There was a talk yesterday in the workshop about it。

 It's tied to a spec。And their the goal is to have a minimal and stable set of ten operators。

It is the only M L graph dialg upstream。And it's。As much as input dialect as an output dialect。

 because there are also some backends using the Toa byte code for the downstream compilers。

Let's talk about the first framework， light R T。Probably most of you know it as Tensorflow light。

 they renamed it last year。 So it's a bit more decoupled from Tensorflow。

Light R T is a very lightweight Mron time， optimized for mobile image devices。

 and it has a stable flat buffer file format， normally with T of light at the end。😊。

It supports quantization and model optimization。 It's quite nice if you want to have fully intelligentte networks。

😊，And the original design was for CNN and RNs， but it can also normally compile transformers with it。

 even though some things like K V caching， all of that need to be handled by the surrounding program using a TF light file。

And it's widely used in Android， Ios and embedded Linux devices。

 So this one is one of the O G frameworks。All does the lowering work here。

 So you have to tear a flight flight off a file。 And inside of Tensorflow， you have a deization step。

Which is almost a one to one conversion to the T of light dialect。And then also in Tensorflow。

 there's the lowering from T of light to tosa。At the moment， you need， I think you need two binaries。

 I'm， I'm not super sure maybe someone can correct me if I'm wrong。

 but you need a flat flat buffer translate binary to translate the flat buffer file to the MLI R dialect。

 And then you can use T F optt to convert Tensorflow light to Tosa。There was a Pth API I to do that。

They removed it now。 I think it was because the arm wanted to contribute more。

 And that was in the way。 But maybe some armed people can comment on that later。And then below。

 you see actually in a sample of the I R， we get in Tulsa。 And as I said。

 it's full integer I I 32 here。 You have support for some dynamic shapes。嗯。

And then you can lower that to Lena， if you want。So my own experience with that。 And I started， oh。

 that was the first importer I used。 It's quite stable。 I， it's okay。

 You have to be a bit careful that the Tensorflow package that you use and the MLAR version that you compiled that they're in sync because the dialects change。

 Now， we probably will get better with thetoser versioning scheme。😊。

The removal of the Python API is a bit annoying and convenient。

 And I don't think there is a solution to that yet。

 because now you need to compile Tensorflow foam source to use this flow。

 It's not shipped with the Python packages。Also， the depend on Tensorflow is even more annoying because you're just using very specific parts of it。

 Use the decentsization of the flat buffer file and the lowering totosa and the whole M F framework that Tensorflow is。

 you don't use that。 So it's even more annoying。😊，But I think this is the easiest way when you want to try fully inteiggerent networks。

 because also， function arguments， function return values are all handled by the T F light quantizer。

 And I think it's easier to export an integer network with that。Let's talk about Onyx。

 the other file format。 So Onyx stands for open neural network exchange format。And this time。

 you have a protocol buffer file， which normally ends with an onyx。This是。

Represents static computation graphs。Onex was build so you can share your your model across frameworks。

 but also you can send it as a file and makes handling your networks a lot easier。

 It's designed for interoperability。 If you want to execute that。

 you probably need to use other projects such as onex runtime， things like that。

And you can also export training graphs with onyx。 So you have to be careful when exporting that you don't have training notes if you want to do inference。

On access two ways of importing to upstream M IR。 The original one was via Onex M I R。是。

Onex M L R is quite an old ML L R project now， and I'm started at IBM。

 and it has an L VM backend to target CPUus， but also a fully coach and backend for the IBM teleelem accelerator。

😊，There's a lowering from Onyx to Tosa， but it's incomplete， which is kind of my fault。

 I did that at my previous day job， but left the company。 And since then， no one picked it up。

There's also a way from onyx M A R to stable H O to Lac。 I've never tried that path。

 And you also have to have another depend on stable H O。 But looking for the code。

 it seems like that one is a bit more complete。To use that。

 you have to first deseialize the file again and then convert onx toossa。 And at the bottom。

 you just have few like a small snippet of D IR that Onx IR uses。

 which is almost the one to one mapping to onx nodes。

And then you have the new way of doing it by a torch I。This is like the new kid on the blog。嗯。

Two main reasons for that。 Onyx and  A10， they're quite similar。 For example， for convolutions。

 you have the same data layout。 also， it's very easy normally to map onyx nodes to  A1 nodes or the other way around。

 which is actually more common to export the torch model as onyx。

The second reason was that people didn't want to have free dependencies on big MLLR projects。

 They had tos of flouryx MLR and Toch MLLR Keep on all in sewing on the same ML LD Mcom。

 plus your own downstrstream stuff was quite of a hassle。So。There's now decentizer in To M IR。

So you can remove the depends on XM L error。How that works is that you import your onyx model to an onyx to dialect。

Which is shown on the bottom。 It's modeled with torch customs。 So it's not really a dialect。

But it's the one to one mappingping tonics notes。And then you convert that one to the torch 8 or torch dialect。

And this dialect can be then converted to cantosa。So you kind of go sideways first and then down。So。

 my own experiences with。Both of them said they are not both not perfect。

 So on Xr is incomplete and taught M I R at least for the most。

 we try that we see failures sometimes， but it gets a lot better。For all X I art。

 try to use the stabilize your all path if the teleessopath is not enough。

But the nice thing about using torch MR is that you get two for one， right。

 You have onyx and torch support just by depending on Torch MLR。😊，Also。

 the onyx representation is a bit weird and torture M I are with the customs。

 You kind of would expect to have a dialect for that。But I also get why you don't want to do it。

 because then you would need to auto generate a tablegen file that then is in the built process for the C plus plus dialect。

 Maybe I RD L could solve something like that， but it's also not ready yet。

 So this was the pragmatic choice。 just use to onx customerss。Also the lowering， if you look for it。

 it's quite interesting because it's just alphabetically ordered。

 So you have one file going from a to， I don't know。 K。 Next file goes from K to Q and whatever。

 It's just a huge switch statement on the operator string。😊，Let's come to the most complicated one。

 torch。So everyone knows toj， right。 It gets like all whole other lamb word the snow p by toch。

It's a pyon first approach， and there's a lot of hiddenency plus plus code in chargerch。

You have over time， you had multiple export formats， Torch script， onx and the Fx graph。

 But a new one introduced after Torch 2 to 0 is storage export。

T was extremely popular in research and production deployments。But the export。

Path doesn't have a stable serialization format。 so you cannot save your model as a file。 This one。

 iss experimental。 It changes very often， so。I don't know。 Maybe if you see that in half a year。

 it's ready。 But right now， it's not。And torch is even more complicated because now it's split into two parts。

 You have one part， depending on the Py toch infrastructure。

 and then you have parts living in Torch M R。So now。

 Torch export is the default way of exporting a model， and it's a tracing exporting format。

 So you give your model plus some fake arguments。And you execute that model with fake notess。

 and you can track if you have mutable buffers and things like that。

You cannot have control flow on tensor elements。 This will create a， what we call a graph break。

 and the model is not exportable。But this also gives the user a lot of freedom。

And then in Torsshamal R， you have the ethics importer， which takes the exporter graph。

And outputs torch dialect。It also has some hooks for very advanced features。

 like mutable buffers that are not that easy to represent if you' own an upstream dialect ten world。

All of this is nontrivial because you have mo buffer dynamic shapes， mixed precision things。

 And now not the compiler decides that， but the person who wrote the model。So let's see example。

 like I said， you have to have the model somehow in your file or in your python packages。

 So this is a very easy basic and end module just with one operator。Then the interesting thing is。

 you see batch channel in dynamic shapes。 So you can now say， hey。

 batch and channel they are dynamic， but they're also constrained。 So you can say， like。

 this is a maximum of 10， Min of 2。 And it's actually linear。

 So you can even say it's a multiple of 16。😊，You give that then to a function that lives on torch M IR called ethics export and import。

 What does does under the hood it export， it uses torch export to export your neural network and then cause the ethicx importer to import your model into the dialect。

If you look at the lit test on top， you can see that in the I R。

 we actually have the symbolic shapes that represent that we put constraints on our dynamic dimensions。

So if you build a compiler， you actually have two choices。 You ignore that， or you can use that。

 for example， to limit allocation sizes。 Or if you have multiple of 16， for example。

 you can even say， hey， I know this will be tileable by 16， even though it's dynamic。

 So this is very powerful。Then when you have to torch dialect， which is on top。

 you can lower that to Tulsa or to Lag。Torch M I R and the torch direct they have their own type system。

 which means you also have a type converter， and you also have passs making sure that the function arguments and the return values are in tensor types when you want to go to upstream dialects。

 So it's not a single pass。 This is a pass pipeline。

 but it's very convenient here wrapped into one command。

And it's the torch back into tors up backend pipeline。 And then you have tors up for that bottom。

Same thing goes for Leag。It's linear containers back and then。

So I spend most of my time actually on this one here。 And in my opinion。

 Torj export is super powerful in what it can capture。😊，The graph breaks are a bit annoying。

 but this kind of offloads are burden on the model developer。 So you cannot fix that。 you。

 or if you want to fix things and torch export， you have to contribute to pitorrch。Also。

 because of all the things I talked about， symbolic shapes， constraint dynamic dimensions。

Bigs precision， All of that。Means that a touchrch front end by design is more complicated than a T F I front end。

I think the ethics import is quite nice and that the hooks can be used like a plugin for your own compiler or for your own implementation are very convenient。

 I think at the moment， if you use something like mutable buffers。

 it's not fully supported if you go to Liard vanilla。😊，Toorch to Lac， in my opinion。

 has a better coverage than Torch to Tosa。Also comes down to Tosa being tied to a spec and allowing less operations or variances of operations。

 where like you can do whatever you want。Decord quality in some partss is an issue。 actually。

 So when you find a bug， for example， in a convolution lowering to Lig， super hard to fix。

 super hard to add new features。Most of the time this works， though。 So we have， we'。

 we've seen like with a few fixes， it's， it's workable。

I think a large part of this comes from a large redesign that Toch M I had a few years ago。

Which pushed it from also having backends to a more pure frontend project。Also， keep in mind。

 if you want to use Tosa， convolutions and pooling operations have different data layouts。

 So you will see a lot of transpos in your IR， and you need to optimize them way somehow。

Let's come to Jas。 So with Jack， I have the least experience with。But I tried it out for this。

 for this talk。 And it's actually quite nice。 I liked it。😊，Its feels like nuy accelerated by X L A。

 and also source auto differentiation。 So you don't have to like。

 implement a backwards version of your operator。It's used in research and large scale of transformers。

 but everything mastered by Google to target Tpus。And it's a very native integration with MLAR。

So the code you see here is directly from the website。 I just put two conis together。

 and I'm downloading renet ETM from Hi face， exporting that to stable HL O and work out of the box。

 No issues there。So that was nice， but I also didn't try very advanced features。

 like dynamic shapes or things like that。Then you need to depend on stable alone。

 I don't know if Stbilature has a python。Library that you can just pi install。 I don't think so。

 So you have to build it from source。And then you can lower from so to Tosa to Liac。

 And thelinac one is quite complete。Like I said， I don't have too much experience with it。

Not look good so far。 Don't have problems with it。So， on summarymar。If you want to import a model。

 you have to choose the correct importing project for it。 If you have light R T use Tensorflow。

 unfortunately。And onyx， you can choose To M， Onyx MR Torch， of course。

 Torch MR and Jx would be stable at yellow。The easy case is small， often work for all of those four。

 But the devil is in the detail， especially with torch when you give the M。

 L developer so much power。You can very often choose between Tulsa or Liig。

 And what I saw across the projects is that normally the linear coverage is a bit better。

Over Tosa also has to use cases because it's a very reduced operator， said。Also。

 it's a bit annoying that you need to build so many projects on top of M I R from source just to import your model。

 I don't think it's very beginner frankly。Tch Mla at least has put package that you can install。

 but with tens of flow and the removal of Python by my I was a bit annoying。Yeah。

 so if you have any questions， happy to connect。

![](img/4721fb76f4294da820a699f88670ffb1_2.png)

And， thanks for listening。Cammelia。Question， please。Hi， nice talk。 I just。

 I was wondering what happens in the torch flow。 If you have just in time components like torch compile or Triton Git。

 do the， does the exporter。Support those and the importer， as well。

So torch compile uses a lot of the same infrastructure under the hood。

 but it also handles graph breaks。 So what torch compile does。

 it then stitches together two graphs and executes the python line。 It was not traceable。

 So in a sense， torch compile has a bigger coverage， but it also has performance hit。

 And as far as I know， Triton has its own flow。 But I'm， I'm not super sure I'm not a Triton expert。

Okay， I was just wondering if they create some kind of custom operator thing in the graph。

 like a node。And anyway， no， unfortunately not， there's if you see graph breaks。

 there's something like a dictionary of what you can do to， to fix that from torch。 But I mean。

 what we did， we went to transformers and fixed a few models and transformers and things like that。

Okay， thanks。How do the different importers compare when it comes to weights。

 Are they exposed as constants that you can， for example， optimize the transpose at compile time。

 or are they just exposed as per meter to the function。嗯。In the。

OnxMR and lightr T imported their N D IR is constant ops and To M I R。

 they you can off them to the resource part of the IR。

 where you can even save them in a different file。So we can compile your model without the weights。

 but。They're not， not arguments to the function。 It's more like you have operations like a global load thing that achieves the。

 the constant。Okay， thanks。Yeah， I guess I just want to comment that for the Triton one。

 it'll like kind of like export as like a custom high order app and you're responsible for building a custom torch extension that like interfaces with that。

 So it's a little hacky as far as you got to plug it in。 But yes，s what it does。 But I was gonna ask。

 So I had this problem where for torch export。 It always unrolls every single N N module。

 And it looks like by design， it can't just like give you a four loop to loop over N N modules。

 And if you have like instruction cut in general unrolling models can get very large as far as IR goes。

Very， so is there kind of like an effort to allow for it to just be like， you know。

 nested for loops for just like at each N end module because。

Such a large binary could be a little like。You know， performance is efficient。

I'm not completely sure。 So I know that you can tell torch export， which decompositions to use。

 and the normal set is quite。Cried bra。 So it might be that your for loops are just decomposed and you just have to remove that decomposition could。

 but it could also be a more systematic issue and torch。 They're working really hard on it。

 Exe torch also depends on torch export。 So they try to fix that。Okay， thank you。

Let's thanks Maximilian， for a good talk。

![](img/4721fb76f4294da820a699f88670ffb1_4.png)