# 美国贝鲁特大学《GPU计算｜CMPS 297S396AA - GPU Computing - Spring 2021》（豆包翻译 - P16：-16-Lecture 16 - Sparse Matrix Computation (COO and CSR).zh_en - GPT中英字幕课程资源 - BV1bw4m1k7a1

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_0.png)

Hello everyone and welcome to lecture 16 of GPU computing today we're going to talk about sparse matrix computation and in fact we're going to have two parts of of this topic today we're going to look at two particular storage formats one computing sparse matrices。

 COO and CSR and next time we're going to look at other formats that allow us to do other things。

So what we will look at today， like I said， the parallel pattern we're looking at is sparse matrix computation now there are a lot of different things that we do with sparse matrices。

 what we will be focusing on to showcase some of the challenges that we face when we do sparse matrix computations we'll be focusing on one case study which is sparse matrix vector multiplication or SPMV there's all kinds of other things we do with sparse matrixrices but we don't have you know we can spend a whole course on that but we don't have enough time for that so we'll only be doing two lectures on sparse matrix sparse matrix computations and during these two lectures we'll be focusing on sparse matrix vector multiplication as our case study。

We'll also be looking at multiple storage formats and I'll explain what those are later on。

 but today we're going to focus on two storage formats。

 the coordinate format or CO0 and the compressed sparse row format or CSR and and next time we will look at two other formats in which we will we will we will kind of see how we can you know what other how the。

The choice of storage format impacts how we process sparse matrices。 Okay。

 so let's get started before I you know talk about formats and SMV。

 let's first talk about what is a sparse matrix。Now。

 a dense matrix is a matrix where the majority of the elements in the matrix are non0。

 And here I'm using blue to indicate that some some element has a value， a non zero value there。

 So we say that a matrix is dense， when the majority of the elements in that matrix are nonze。

 In contrast， we say that a matrix is sparse when any of the elements in the matrix are 0。Okay。

 so if a matrix has many different zeros， many zeros inside of it， then we say this matrix is sparse。

 And it turns out that a lot of real world systems are actually sparse。

 A lot of the matrices that we use。😊，Whenever we're doing all kinds of computations turn out to actually be sparse and they turned out to actually be various sparse so the vast majority of elements and a lot of matrices that we use out there are actually zeroes and the fact that these matrices are zeros means that when we do things with these matrices like multiply them with vectors or multiply them with other matrices we can take advantage of the fact that we have all these zeroes to save on multiple things So what are the things we can save on when we take advantage of the fact that the matrix has many zeroes。

😊，Well there's several opportunities， first we can save memory， okay。

 because if a matrix has a lot of zeroes， okay we don't need to we can we can save memory by compressing the matrix such that we only store the nonzero values and we don't store the zero value so we don't need to allocate space for the zeros and this allows us to save memory。

Okay， or even storage， if we're storing the matrix in a file， we can save storage。Okay。

 now when we when we don't store these zeros。Ewhere， and we save delivery。

There's also a kind of an effect of that。And the effect of that is that when we compute with this matrix。

 the fact that we don't store these zeros means we don't need to load these zeros when we are computing。

 and this helps us save memory bandwidth。 and it also means we don't need to compute with these zeros。

 which also save it's computation time。 So when I take a matrix and multiply it with a vector。

 another vector or another matrix。 Okay I have to go through all these nonzes and process them when I'm doing the matrix vector or the matrix matrix multiplication。

😊，But when when my matrix has a whole bunch of zeros inside of it。

 not only do I not need to store these zeros， which help to save memory。

 I also don't need to load and compute with these zeroes。

 which saves the memory bandwidth and the computation time。Okay so when we look at sparse matrices。

 we spend a lot of time thinking about how can we represent sparse matrices in a way that allows me to save memory and also allows me to avoid loading and computing with zero values so a lot of the work on sparse matrices has to deal with how to design different storage formats for these sparse so there's actually many storage formats for sparse matrices out there what we will do is we will focus on four different storage formats in the next in this lecture in the next lecture and again you can you can go into all kinds of other formats that allow you to optimize for all kinds of different things but we will focus on these four because they're sufficient to kind of demonstrate all the concepts that we would like to demonstrate in an introduction to this kind of topic so one format is the coordinate format another format is the compressed。

😊，Sse row format and these are the two formats we'll focus on today another format is the LAP format you know and thebb abbreviation trend is ELL support format abbreviation is COO and the compressed Sprs row format is CSR。

😊，And then there's also the jagged diagonal format。

 which is also JDS and there is there are there are many many other formats again out there。

 there's still research on you know people still do research on different formats representing sparse matrices depending on depending on you know what their their specific application is somebodys asking how recent are these are you know these have been around for quite a while。

 The reason we look at them is their kind of the classics and and particularly for GPU they allow us to emphasize different things A lot of the other formats are kind of squeezing more and more benefit out of out of these formats。

 but they rely on kind of similar principles。😊，So yes。

 these formats are commonly used and there are other formats that are also used。

 but hopefully by covering these formats and allow you can easily go and read up on another format and understand why they made the decisions that they made so thank you for that question。

😊，Okay， so different design the reason we have different formats is because as you can expect different formats are good at different things so there's various considerations that go into designing a storage format for bars matrices。

 one of them is space efficiency。😊，Okay， how you know how efficient you know how much memory do I save when I use this format okay another one is flexibility and particularly here I read the flexibility in terms of modifying the matrix okay so some formats make it easier to add reorder or remove values than other formats。

Okay。So if I plan to kind of modify my matrix a lot。

 I might to the different formats from if I'm planning to just keep my matrix fixed the whole time。

 my matrix is constant throughout my computation。Another one is accessibility to the ease of finding the desired data so when you when you access a matrix。

😡，You want to access it in a particular way， maybe you want to go through all the rows of the matrix or maybe you want to go through all the columns of the matrix okay depending on how you would like to access your matrix。

 different formats might make certain types of aes easier than other。😡。

Yet another one is the memory access pattern that the storage format enables right and in the context of GPUs it's whether this storage format enables memory coalescing。

Okay， so it does so the choice of storage format may impact you know how you how you how you lay out your data impacts how you access your data。

 the memory access pattern， so you can design formats that are designed that you know give you better coal L。

And then finally， load balance， and the load balance means how much work each parallel worker has and in the context of GPUs。

 this translates into control dirgence。Okay， so how much does your format allow you to minimize control divergence？

Okay。😊，So these are the different considerations that go into designing sparse matrix storage formats and by the way。

 some of these are kind of general so space efficiency is you know a general concept。

 but some of these are specific to a certain application right so so the memory access pattern。

 the load balance when we talk about these we talk about them in the context of a specific application。

 how these formats allow a specific application to have coalesced access how these formats allow a specific application to minimize its control divergence and for this reason。

😊，When we talk about these four beds， we're going to talk about them in the context。

Specific application。 and that's SPMV or sparse matrix vector multiplication。

 So the choice of the best format depends on the computation， okay。

We will use sparse matrix vector multiplication or SNV as an example to study the different formats。

 so in this lecture and the next lecture we will be looking at sparse matrix vector multiplication。

 which is where you take a sparse matrix。😊，And a dense vector。 Okay， and you produce a dense vector。

 This is what we will be looking at now and next time。Okay， however。

 there's all kinds of other sparse matrix computations that you might want to do maybe you're doing sparse matrix with a sparse vector or maybe you're doing a sparse matrix of the dense matrix or maybe you're doing a sparse matrix with another sparse sparse matrix and there's a whole bunch of computations you can do with sparse matrices and of course the storage different storage formats may be good for different computation。

😊，Okay， but we will use this particular computation as a case study just to showcase some of the challenges that go into dealing with sparse matrix computations。

 okay？Okay， so let's start with the。C， O，04。The CO format is as follows let's say I had this matrix over here the sparse matrix I have these white squares represent zero values and the non whiteh squares represent nonzero values Okay I'm using integers for simplicity but obviously this matrix could have floating points it could have doubles it could have all kinds of data types。

😊，Now， the way that the coordinate format works is that we're going to store every non zero along with its row index and its column index。

ok。😊，So what we do is we take these values， these non zero values in our matrix。

 we're going to put those in an array， you know one after the other， so we have one， we have seven。

 we have five， we have three。Right， we have di。Okay， and we put all the elements。

 one after the other。And then for each element， we're going to have a row array and a column array that tell us for each element to what the corresponding row and column index are。

诶。😊，So what this does is it says that row the value one is that row0 and column zero。

 so here the value one here is at row zero and column zero。The value 2， for example。

 is at row2 at column 1。 So here when we go to the value 2。

 we find that the value2 is at the row2 and column。Okay， clear。Questions about this format？

Some what's asking is this similar to how we represent graphs。 And yes， it is。

 It is similar to how we represent graphs。 And in fact， after our two lectures on sparse matrices。

 we're actually going have another two lectures on graphs。

 That's what I told you that you guys will be will' be quite accustomed to these formats by the time we finish the sparse matrix and graph lectures in this course。

😊，Doctor， okay， yes。When you say the matrix or whatever is in this format。

 do we have to as a programmer， change our data that is stored in memory， change it to this format。

 or do we assume that our data is already this way， like in practice， how is it done？I mean。

 you could have libraries that will you know you give them a dense matrix and then they sparsify them for you or they read some sparse matrix from a file and they provide them for you。

 but otherwise you can also implement such a library yourself Okay so who converted the matrix to this format。

 whether it was you or whether it's some library that you call is you know it's a detail know we don't care about that But what we care about is what this format you know how this format works and how we can use it to perform different kinds of sparse matrix computations。

Professor， depending on how spa your matrix is， you could end up having more data in your CO than the original matrix。

Right， so if your matrix， you know， this matrix here is quite dense。 Okay， just because I have。

 you know， I， I can only fit such you know， I cannot fit a huge matrix on this slide。

 So you're right that， you know， in with the matrix， this dense。

 you probably end up need more space to store the the sparse matrix representation。

 than you need to store the matrix， the matrix is a dense matrix of stuff。😊，However。

 you know when this matrix is thousands by thousands。

 then you can easily see how you quickly up you quickly end up saving a lot of memory when you use the sparse matrix format。

 yeah， good observation， you know if your matrix is this dense right you probably don't want to make make it sparse if your matrix is 50% dense or even 20% dense or even 10% dense in some cases。

 you probably don't want to sparsify it， but sparse matrices in practice can be very sparse。

 you're looking at less than 1% of the elements are zeros are nonzes。😊。

Okay so so have you seen the CO format now the question is。

 or let's take a look at how we can use the COO format to perform SPMV or sparse matrix vector multiplication so let's say I have this sparse matrix and what I would like to do is I would like to multiply this sparse matrix by this dense vector to produce this dense vector。

😊，Okay， and the question is。😊，How can I， you know， if I want to do this in theory， it's easy， right。

 I just go through the， You know， I can go through each element and multiply by the corresponding input value to get and。

 you know， update the corresponding output value。 But if I want to do this in parallel。

 how can I do it。The way we did it before， though。What we haven't done is sparse matrix exact modification before。

We didn't even do dense matrix vector。 We did dance matrix matrix。 How can we go far。

sorryrry we have to put the threads on the value matrix。

You need to assign a threat to each one of these values。

And the value and the value value array below。I want I assign a threat to everyone。The value the hat。

We take which row and which column。And we add the sums in the output， in the output vector。

Because we can do it the way we did it before and matrix matrix multiplication where we assigned a thread for each output element of the matrix because。

All right。Okay， so why so why can't we do it， Why can't we assign a thread to each output value。

 for example。I would argue we should because some non zero elements can now be。

Like non some0 elements could not could now mean non0。ok。So these are actually two。

 two very possible approaches to paralyzing this。 We can assign a thread to every output value， Okay。

 and have that thread to compute and multiply the row with the input vector to get the output value。

Or we can assign a thread to every non zero value in the matrix and have that thread， okay。

Find the input that corresponds to that non0 value。 So this case would be this。

 And then do the multiplication and update the corresponding output value。

So both of these are possible ways of paralyzing it。What way seems most suitable for the COO format。

let's say， for example， that I assigned a thread to every output element in this format and that thread wanted to go through the corresponding input row and a do a you know and calculate the value of the output would what would that thread need to do。

It would need to search for the raw vector。But's corresponding。呃 sub sub vector。Right， exactly。

 So if I assign a thread here to row 0， for example。So if I to output element0。

 this thread needs to go through the non zeros in rows0 and multiply them with a corresponding the elements in the input vectoror。

So the threat has to go and find all the non zeros and row zero。

Which means it'll have to do a search through this array， right？

And here I'd like to be lucky at the array is sorted。

But the CO format doesn't really tell me this array has to be sorted。

 These non zeros could be in any order。So I might actually have to do a linear search through the entire array to find the element that corresponds to the row that I'm interested in。

So this is why the COO format not really does not really make it easy for me to assign a thread to every output element and loop through the corresponding row。

 and this is one of the things I meant by accessibility。

 different formats make it easier to access different things。Okay。

 what does the CO format make easy for me to do？Assign a threat to each nonze vector。Right， exactly。

 I can assign a threat to each non zero element in the matrix。Okay。

 I assign a threat to each non zero element in the matrix。

 so the kind of the most sensible parallellyization approach is to assign a thread for every non zero element in the matrix。

Okay， and what that looks like down here is that I assign a thread to every。Value and the value。Okay。

 so that's I think somebody had mentioned that at the beginning。

 but I was I just wanted to emphasize logically what was going on logically what we're doing is we're assigning a thread to every nonzero in the matrix right physically what happens is we assign a thread to every element of the nonzero array and the values array。

Okay， so we assign a thread to every element and the we can assign a threat to every element to the matrix。

 and that thread， you know， can easily find its corresponding grow and column index。And what。

 once the thread nose its row and call index， what can it do。

It goes back to the row and takes the corresponding vector element。Right， so thread one。

 for this thread， for example， knows that it's responsible for the element。At row 0 and column 0。

 So it finds the input value at the corresponding row and then goes and updates the output value at the corresponding column。

 So to make it more clear， for example， this thread here is responsible for you know。

 this thread here is responsible for this down 0。 So it comes， it says oh， well。

 I'm responsible for the element at row 2 and column1。So I will load。

The the input value corresponding to my column index。

 I load the input value corresponding to to that has the index one。

 which in this case is one over here， and then I will multiply that with my non zero and then I will store the result at the index of the corresponding row。

几。😊，Now， the problem with its approach is that。I can have multiple threads updating the threads that are possibly to get nus of the same row will end up updating the same output value。

Okay， so what I will need is I will need to， since I have multiple threads that are writing to the same output value。

 I will need something like atomic operation。Okay， so this is， if I use the COO format。

 this is how I would have to implement SPMV。 I'm going assign a thread to every non zero。

 Every thread will be responsible for one element。 Okay， it'll it'll get the corresponding。

It'll get the corresponding value， it'll get the input value corresponding to its column index。

 and then it'll store at the output value corresponding to its row index。ok。😊。

implementmple this and because we have multiple threads writing to the same output value will the at topicomic operation。

 let's go and implement this and see how it works。😊。

So I'm going to switch to my code here here I've set up the code to where I have a matrix in the COO format。

 I allocate copy to the GPU and then I call I call the GPU kernel and a number of threads I give it correspond to the number of nonzes in the matrix and then I copy back the output vector and I free the data。

 So let's go and work on the code itself。 So I have my CO matrix Okay and I have my input vector and I have my output vector So first thing is each thread is going to be assigned to a different nonzero element。

 So the thread first needs to figure out the index of the nonze element in these arrays that it's responsible。

😊。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_2.png)

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_3.png)

Okay， so I I will find the global index of the thread。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_5.png)

Alright， unsed and I is equal to。Llock index dot x times block div dot x plus。Read than next got X。

Okay， so I over here is going to be the index of the non zero element。Okay。

 so it's going to be the index that I will use to index the value array， the column array。

 and the row array。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_7.png)

Okay， now one thing I need to make sure of is I need to make sure that I am within bound。

So what what does what do I have how could I be out of bounds。

 What do I need to compare I to to make sure that it's within bounds。

 I need to make sure that my I don't have any threads out here。

 I need to make sure that I is less than the total number of non zeros in the matrix。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_9.png)

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_10.png)

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_11.png)

right。I is less than the total number of non zeros。 So the COO matrix has a field over here。

 which is none。呃。Not zeros。Okay。So now that I've done the check。

 Now I know that the thread processes a valid non zero。

 So now I can now now I can process the element of that thread。

 So what do I need to do for each element。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_13.png)

Well I have to find its row。 We' going have to load its row index。 I'm have to find its column。

 I'm going to have to load its column index。 We' going to have to find its values。

 So I load the value from here。And then I'm going to need to get the element that corresponds to the column index for the input vector。

Multiply and then add the result to the element at corresponding the apple vector at the corresponding grow events。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_15.png)

Okay。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_17.png)

So the row is going to be in the row array of the COO representation。

 so I'm going to get my COO matrix。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_19.png)

At in my to O matrix， I'm going to。 I'm gonna have a real indexes。Field， okay。

 and the throw indexes field is indexed by whats going to be indexed by I。 Okay。

 because I is the index of the non0。Okay， similarly。I'm going to get my column value。

 so my COO matrix is also going to have a field called。All indexes， Okay。

 and this field is going to be out is also going to be indexed with I to get the corresponding。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_21.png)

Colln index。 Okay， and I'm also going to load the values。 The value is the floating point number。

 that'm going to load。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_23.png)

The value。And the value is also going to be at CO matrixtrix dot。Values。

 and I will access it with the element by。 So now I have the row and the column and the value that the thread is responsible。

Now， what do I need to do？I need to multiply the value value。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_25.png)

With the input element at the column index and add it to the output element at the row index。ok。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_27.png)

Whatna do is I want to do。Out vector of。R。And I want to add to it。Ed vector。Of column。

Times the value。This is what I would like to do。Now what's the problem if I just do it this way？

Re condition。I have a race condition， so what can I do to avoid the race condition？Atomic。Right。

 I'll tell the cut。 So instead of doing this， I will do。At topicomic a。

 I'll give it the address of the value I'm adding to。

And I will give it the value that I would like to add。Okay， so this is a COO。

 this is how we would implement sparse matrix vector multiplication in COO。All right， clear。

 any questions？But then I apologize。 I should have showed you the the， how I。

The presentation before we implemented this。So here this shows you how the CO matrix is represented。

 I have number rows， nu columns none on zeros， row index column index and the values so these are the different fields that I need in the COO matrix。

ok。😊，All right， let's compile this and run it and verify that it works， so we're going to compile。

And then， we're going to run。And indeed it works， and as you can see we get around four times speed up in the kernel。

This is also a relatively small matrix that I'm using。

 So the smaller the matrix the less speed up we will get， but still four times is substantial。😊。

Of course， if you include all the copy time right， the GP is not doing very well。

 but that's because again it's a small matrix and then also because sparse matrix vector applicationplication has low data reuse。

 you can expect that the GP performance is not going to be as substantial as if you have something that has a lot of data reuse。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_29.png)

Okay， so。What we already talked about what's bad in doing sparse matrix executive multiplication this way。

 we have these atomic operations， but what's good about doing it this way？

We only do the number of necessary operations like we ignore all the known zeros since the format is。

Okay， so sure we're only going to load kind of kind of do an elder nest operations actually in most formats the we do the only necessary operations in some cases we might you know we might have to store some of the zeros and do some unnecessary operations。

 but in most cases we don't。How's our memory access patterned here？To the to the matrix。

It'sest right， every thread is when we access the value array， when we access the common array。

 when access to the row array， our accesses are all going to be coalized。Okay。

 so we actually have good coalescing behavior for the matrix okay。

 of course the vectors are not going to be as coalesced the vector is arent going to be as coalesced and the output vectors we're use atomic operations okay。

 but at least when we access the matrix， the aes are coalesced。So this is the code that we wrote。

So I'm going to talk about various advantages of of doing this。 But first。

 let me kind of show you how we can see the access or coales。

 So here I is the is corresponds to the thread index。

 So every consecutive thread has a consecutive I value。

 And you can see how when we're accessing a row index and or column index and our values。

 we have we have nice coalescing behavior。 Okay， any questions about the code。😊，Okay。

 so let's talk about the trade docs of the COO format so that first of all we you know we've mentioned some advantages and disadvantages let's kind of recap them。

 So first the advantages of the storage format remember we talked about you know。

 different metrics by which we talk about advantages and disadvantages one of them was space efficiency another one was the flexibility how easy it is to add and remove elements from the format another one。

What accessibility， what does the format make it easy for you to access。

 another one was coalescing and another one was control divergence。Okay， so for the COO format。

 okay what what does how does the CO format do in terms of flexibility easy of adding and removing elements。

 if we go back。So looking at the storage format itself。

Here I can easily kind of reorder the elements， I can easily if I want to add elements。

 it's quite easy because I can just add stuff at the end of this array Okay。

 so the CO format actually makes it easy for me to add elements removing elements is a little bit more difficult because if I'm to remove and I want to shift everything that's quite expensive。

 but sometimes if you remove you can just replace this with some kind of kind of seal value that tells you that okay。

 this value here is not valid。😊，But the still format makes it easy for me to add elements。

 okay so it gives me that flexibility。What about accessibility。

 what does the two format make easy for me to access？If we go back and look at this over here。

 what does the CO format make easy for me to access？

The rows and the columns of the non zero elements。 Right， So given a non0 element。

 it's easy for me to find the row and the column for that non0 element。

The zero format makes it easy for me to find the row column of a specific nonzero element。

 which makes it easy for me to parallelze across nonzero elements because if fact I assign a threat to every nonzero element。

 then I can easily go and find its own column。😊，So that that's accessibility what about memory coalescing。

 how is it do on memory coalescing？Like we said， the aes are nice and coalescce。

 what about control divergence？How doesCOO with SPMV do on control dirgence？

Does not have controlled divergence， right， There's no controlled divergence because every thread does the same amount of work。

 Every thread processes is one non0 value。Okay， so so if we go and talk about the advantages of COO。

 we saw that we have the flexibility， it has good flexibility because we can easily add new elements okay。

 and also the non zeros can be stored in any order。😊，In terms of accessibility， it given non zero。

 it makes it easier for us to find the row in the column。

 this allows us to easily paralyze across non zeros。

We also see that SPM VCOO has coal delivery accesses to the matrix。

And we also have that SPM VCO does not have controlled leverage。Okay， what about the disadvantage？

What were the disadvantages of the COO format？What did the Se format make hard for us to do？

Accessing and using the coordinates。Right， exactly the search。Right， exactly。

 So we said that if you want to go through the all the elements of a single row， right。

 when we came and we said， hey， you know， why don't we try to parallel。

Why don't we try to paralyze by assigning a thread to every output element and having that thread compute input row well we weren't able to do that because it's not easy for us to find all the non zeros for a particular row。

So if we look at accessibility， given a row or a column， it's hard for us to find all the non zeros。

 we need to perform a search。Okay， and the other disadvantage is that we have because we cannot do this。

 we have to use atomic operations。So these are some of the advantages and disadvantages of CO。

 So to address the disadvantages here， to avoid doing atomic operations。

 to be able to assign a threat to every output elements and go through the corresponding row values。

 there's another format， which is the compressed sparse row format。

 So if I have my matrix if my matrix look like this。 this is the same matrix we had before。

 this time what I've done is I've colored all the elements in the same row， the same color。😊。

The way the compress course row format works is that we're going to store the nonzes in the same row adjacent to each other。

 and we're going to store an index to the first element of each of each row。

 So here for our values we're going to have the non-zes the first row next to each other and the non zeros in the next row next to each other。

 the non zeros will turn right next to each other， etc ceter。 for each of these values。

 we're going to have a corresponding column index。 So here one as that column 0，7 is at column 1。

 So we have 0，1 over here 5，3 and9 are column of 0，2 and3。 So that's we have 0。

2 and 3 over here2 and 8 our columns one and2。 So we're going to have one and2 over here。😊。

And then what we're going to do is we're going to store for each row where the non zeros of that row begin。

 So we're we're going to call this the row pointers array。

 So we're not going have a row index array like we had before。 Where for every nonze。

 we had the row index。😊，We're gonna have a row pointers array that's that stores。

 I don't gonna store a pointer。 It stores an index。

 It's gonna to store the index at which the nonzes of each row begins。

 So here the non the non zeros of the first row begin at index 0。

 the non zeros of the second row begin at index 2。 So we store two over here。

 the nonzes of the third row begin at index 5。 So we're gonna to store a 5 over here， etc ceter。

So now let's say that we wanted to use this format to implement SPMV。

 how would we implement SPMV with this format？1 thread per row。But exactly。

 we can have one thread for every output element that looks through the row corresponding to the output element and does the computation。

😊，So we're going to assign one thread。to loop over each input rows sequential and update the corresponding output element。

All right。Now。Well， this looks like this。Okay， we have a thread for each that starts at the first non zero of each row。

Now， if you look at what this looks like down here when were going through our values array。

 we're going to have the first thread starting here， the second thread starting here。

 the third thread starting here， and then the fourth thread starting here。Now， on the next iteration。

The this this fourth thread is done， so it's finished working it's going to wait for the rest。

 The second thread you know comes here， third thread comes here Four thread comes here right on the next。

 you know， they each go to the second non zero element of the matrix。

On the next iteration these the first and the third thread are done。

 there's only the second thread remaining so these guys all these guys are done。

 they're waiting for this thread to finish and this thread goes to the next element of the matrix。😊。

As that， we are done。ok。😊，So what are the advantages and disadvantages here？😡。

They have controlled divergence as a disadvantage。 Right。

 So one of the advantage is that we have control divergence。

 Every thread has a different amount of work that it needs to do。So we have control divergence。

 what's another disadvantage？Memory access are not coalesist。 right。

 When we were going through these this this array， the memory axes are not coalesced。

What's the advantage？ThereThere are no automatic。RightWe don't have a weekend not to memory， right？

3rry。I mean， we can load the for every thread。 We can load the shared memory， right？

What do we want to load the shared memory。I mean， the， the array of value。

How does loading the array of values the shared of very healthy？

So I don't access for for in every iteration， I access the global memory。Sos such。

Do I have data use here？嗯。Well， can if， if we can use for every thread。

 it can load like for every thread loads one value。I see what you're getting at。

 So what you're saying is you want to use shared memories so that you load in a co way and then access in an uncoed way from shared memory。

Is that what youre says somehow Yeah， so you can kind of do that for very large matrices。

 you don't have really have a guarantee to to fit and shared memory， so that might be a challenge。

Okay。Also， whether whether there's other ways to improve coalescing other than using shared memory。

 so we're going to use different way to improve coalescing， Okay， but also in general。

 shared memory is not very effective for SPMV because you don't have data reused。

Every element to the matrix is used exactly once， so yes。

 you can use shared memory to improve the coalescing behavior。

 but there's better ways to improve the coalescing behavior by rearranging the data。😊，Okay。

 professor。Is there also is as a disadvantage， can we consider that we're not maximizing the number of threads running？

Yes， you can say that。 we have less parallelilism here。 We have less perilism。 Now。

 depending on how big our matrix is， that may or may not be a problem。Okay。

 so if our matrix is not that big， we're creating fewer threads so we're not fully utilizing the GPU if our matrix is huge。

 then we may not have a problem there。😊，But still we have control divergence。

 so some threads will finish before others and we'll have to wait for the slow threads to finish。

 so we will have underutil of our GPU at。Okay， let's go and implement this and see how well it performs。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_31.png)

So I'm going to leave my COO implementation， I'm going to go into my CSR implementation。Over here。

 just to show you， I have a CSR matrix struck defined。 I have non rows， none columns。

 number of non zeros， and I have the row pointers， the column index and the value。 Okay。

 when I come down， I want to。And I when to implement my SPMV kernel， we said。

 what are we going to assign every thread to？

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_33.png)

你 out。Every thread is going to be assigned to an output element and the corresponding row for that output element。

So the thread index is also going to be the row index。

 So here I will write unsigned and row with equal to thread index。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_35.png)

They go to creditex。ex。Oops。T x the x。O是。Excuse me。Block index dot x times block div dot x plus。

F index indexside X。What does my boundary check compare to？



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_37.png)

If finding a thread to every output element， what does my boundary check compare to to make sure my threads are inbal？



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_39.png)

Size of row pointers。Right， so the the number of rows， basically。

 So I'm gonna row pointers is actually an extra element that gives me the total number of elements So that for the last row。

 I know where it end Okay， because every row pointer， the next row pointer tells me where， where。

 where the previous row pointer in。😊。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_41.png)

Hello。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_43.png)

So then for a boundary re check， we need to make sure that the thread is processing a row that is within bound。

 So we will do if row is less than。CSR matrix dot number rows。Okay。😊。

And then once we have the thread， once the thread has figured out what row is responsible for。

 what this thread needs to do is it needs to go。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_45.png)

And it needs to find the big the non zeros for that row。

 and then it needs to go through them and loop through them one at a time， stopping at at the last。

Value， so how does the thread figure out where， where to where it's non zero start。 Well。

 it's going to use the rule pointers array。Okay， so what I will do is each thread。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_47.png)

It's going to loop through the non zeros inside of its row。

 it's going to start at row pointers of row。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_49.png)

Right， so thread 0 will start at row point。 the value at row pointers of0。

 Third one will start at the value at row pointers of one， et cetera。

 So here the thread will start at。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_51.png)

DSR matrixx， dot。Row pointers。Of rope。Okay， where does it stop， so it starts here and then it loops。

 where does it stop？😡。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_53.png)

What stops at the row pointers of the。Next value， right。

 It's going to stop at the row pointers of the next value。

 So here we will stop at DSsR dot row pointers of row plus one。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_55.png)

Okay， and this is why we need to have the for the we need to have one additional element at the end so that the very last thread。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_57.png)

Knows that knows where that it needs to stop。 So this last element will tell me the total number of non zeros the matrix。

 it also tells me where the last thread stops。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_59.png)

So for I is equal to CSR matrix that row pointers of rh。

 I is less than CSR matrix that row pointers of row plus 1 plus plus I。

And now what we would like to do is for each one of these values。

 we're going to get the column index， get the value。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_61.png)

Okay， and multiply the value with the input element at the corresponding column index。 Okay。

 so how do we get the value at the column index， We're going well， let's first get the column index。

 We're going to get unsigned n call is equal to。

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_63.png)

We're going to use the column indexes array and we're going to index it with I。

 which is the the counter in this loop that's going from the beginning of the9 zeros in the loop until the the beginning of the9 zeros of the row until the end of the9 zeros of the row and then we're going to。

Wite float value， we're going to get the value， the value we're going to get from the values array。

 so we're going to write CSR matrix。That。Values of I。Okay。

 and now what we would like to do is were going we want to increment the value out at we want to implement increment the element that we're responsible for by the non zero times the input element of the corresponding column index we're going to do。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_65.png)

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_66.png)

Out vector of row。Plus equals。The value times， the inve。啊 call。ok。😊，Now。

 since output vector here is a global memory to avoid， well， first of all。

 since this thread is the only thread that's going to write to its output。

 just each thread owns its own element in the output vector， we don't need an atomic operation here。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_68.png)

![](img/4f8b4ef2de0a3186f5a4443ca0319f83_69.png)

Okay， because every thread owns its output element。 And because of that。

 we also don't need to read and write from global memory on every generation。 we can simply。

Inize a counter outside the loop or an accumulator outside the loop。Okay。

 and then we can instead of having out vector of row here。

 we can increment the accumulator and then after that。

We can store the accumulator at Out vector Opera。Okay。

 so this is the good for doing SPNV using the CSR， the CSR format， any questions about this？

Professor， I want to ask， why don't we assign each element thread。

Why don't we assign for each a threat for each element and the matrix？



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_71.png)

You mean why don't we assign a thread for each element to the CSR matrix。

So why do we perform this loop for this for loop？So great question。

 Let's assume that we wanted to implement the previous approach。Which was the approach point to CO。

 Let's just assume we want to implement that with CSR。 So let's say I wanted in with the CSR format。

 assign a thread for every non zero element。And make that thread responsible for。

 for that non zero element。 Would it work with CSR。

I just need to keep track of the row pointers for each element and the value。

So the the thread if I assign a thread to every value here。😡。

The thread can find out what its value is， what its column indexes。

 but how does it know what its row is？If a thread with index3， for example。

 knows that it's responsible for this value。Okay， the thread with the next three happens to also have the value of 3。

 It knows that it's responsible for this column to。But how can it find what its real indexes？

It's going to have to come and search inside of this row pointers array。😡，For which row。

Contains the non zero at index 3 in this case it would be here because three is in between two and five。

So it'd have to do some kind of binary search inside of this row pointer's array to go and figure out what its row indexes。

And that is why the CSR representation makes it easy to paralyze across rows or across output elements。

 but it doesn't make it easy to paralyze across nonzero because given a row。

 we can go and find the non zeros for that row， but given a non zeroro。

 it's hard for us to go and find the corresponding row， we have to do a search。😡。

So this is one of the trade offs of the CSR format and I'll talk more about trade offs。

 but let me first run the code and show you the performance， so let's close。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_73.png)

And we're now going to compile the CSR code。And we're going to run this CSR code， and as you can see。

 it actually has worse performance。😊，Because of the atomics。几。😊，And because of the poor coalescing。

Now。In this particular case， it has for performance， Okay， in other cases， depending on the matrix。

 depending on the dimensions， the CSR， the CSR might have better performance than the CEO。

OkayBut in this particular case， for this particular matrix。

 CSR actually performed poorer than COO with atomics because。

The performance penalty that I got from having poor coalescing and poor divergence was worse than the performance penalty that I got poor coalescing and high control divergence was worse than the performance than penalty that I got from the atomic operation。

Okay， clear， any questions about that？You will notice something though。

 you'll notice that the copy time to the GPU and back or sorry， the copy time to the GPU。😡。

Is lower than the copy time to the GPU for CO，0。 Why is that。We had row before。

 as opposed to row pointers now， which is smaller。Right， exactly。

 So it takes me less time to copy the CSR matrix of the GPU than it takes me to copy the C matrix to the GPU。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_75.png)

Okay， and the reason is that the CR matrix does not have a row index array。

 It just has a row pointers array。Which is much smaller。

So the CSR matrix is actually more space efficient than the COO matrix。ok。😊。

So let's go let's go compare CSR COO based on the different metrics that we talked about。

 so in terms of space efficiency， what's better CSR or COO。CSR， CSR， right， in terms of flexibility。

 So the ease of ease of adding elements to the matrix， which one is better。姐1二楼去。Do。Addic elements。

Right， O is better because was C， O，0， I don't have an order， right。

 I can simply just add elements at the end of the the erased， whereasas here。

 if I wanted to add an element to column 3 or call So sorry。

 if I want to add an element to row row this second row or the third row over here。

 What would I need to do。all the elements after so all the elements in the same row need to be next to each other so if I want to add an element to a particular row I'm going to have to shift all the elements in the later rows and I'm going to have to go and increment all the row pointers for for the later rows。

So in terms of flexibility， in terms of space efficiency， CSR is better。

 where in terms of flexibility， the ease of adding things。😊，COO is actually better。Okay。

 what about what about accessibility， What does COO make easy to access。

 What does CSR make easy to access。Your O makes easy to access any any output thread。

 whereas CS SR makes it easy to access any input thread。No， not output。 if by input input。

 you mean the matrix， then then sure。 So CS SR makes it easy for me to access。 given a row。

 it's easy to find the non zeros of that row。SoAnd that makes it easy to paralyze across rows。😡。

DO makes it easy to do the following， give it a non zero。

 find the row and the column for that non zero。So COO makes it easy to paralyze across non zero。Okay。

 that's accessibility， what about coalescing？C is more called a memory colour than。

What about control divergence？You're always better。

Right the O is better and what about synchronization of having twoomics of things？CSR is better。

 CSR is better， exactly If we go back to our trade offs， yes question。For， for CS SR， are in the the。

The memory writes。Coale。You build the right to the output vector， yes to the object。Oh yes。

 you're absolutely right。 So， So you're absolutely right。

 CSR Vs coalescing the out rights to the output。 CSR helps you call us the rights to the output。😊。

Whereas with CO， you have to use atomics there， but CO0 makes it easier to coalesce the input。

 And since the input matrix is larger than the output vector。

 usually that's what dominates your memory access。 And that is why when talking about coalescing。

 we be focusing on the matrix because it's larger。Okay so the advantage of CSR are that it has better space efficiency better for accessibility it allows us given a row to find all the nonzes and thenPMV CSR avoids atomics because every thread owns output。

 but the disadvantage is that it's hard to add new elements to the matrix and then for accessibility。

 given it non zero， it's hard to find a row given a column it's hard to find all the non zeros for that column。

😊，And then SPMVR aes are not coalesced and SPMV CSR has control divergence。ok。😊。

So one thing here to note is I kind of sneak this in here， so given a column。

It's hard to find all the non zeros for that column。 Okay， so CSR， given a row。

 it helps me find the non zeros in that row。 But if I want to， for example。

 do a column traversal down a column， I cannot do that with CSR。

 So there's actually a transpose of CSR， which is well not transpose of CSR。

 but kind of the the other version of CSR， which is compressed parse column and CSC。It's like CSR。

 but it groups non zeros by column as opposed to by a row so SPFV doesn't require this。

 but if I have some other computation that requires me to loop through the columns of a matrix。Okay。

 in this case， CSC would put the nonzes of the first column next to each other followed by the non0 and the second column next to each other。

 followed by the non zeros of the third column next to each other， etc ceter。

 So CSC would have similar advantage of disadvantages to CSR except for accessibility CSD makes it easy to access the nonzes of a column given a column index where CSR makes it easy to access the nonzes of a row given a row index okay。

Now， it would be nice if we go back to these trade offs。

 it would be nice if we can avoid the atomics。Which is what CSR gives us。

 but at the same time have a better then we access pattern so where our access patterns call us and also be able to reduce our control divergence so it would be nice if we could have the best of both worlds。

And for this reason what we this lecture will is to be continued okay next time what we will do is we will look at other storage formats that allow us to improve coalescing and also reduce control divergence in particular we're going to look at the LPAC format or ELL。

 which helps us improve coalescing compared to CSR and we will also look at the jagged diagonal storage format or JDS which will help us reduce control divergence。

😊，Okay。😊，Any final questions before we end？Professor in all those formats。

 if you have a row or a column of complete zeros， can you collapse it or no do they offer that or no Well well it depends it depends and CO if you have a row or column that doesn't have any zeros Okay。

 one question is why should that be in your matrix in the first place， but in some cases， yes。

 you could run in a situation where one of your columns or zeros all have zeros and CO if you have a situation like that then you won't pay anything for that Because CO will only throw the nonzero with those column a row index。

In CSR， if you have a row and a row with all zeros。

 you will still need to have an element for it inside of the row pointers array。

 but you won't have any values for it inside of the。The the values in the column index rates。

 but we will see in some of these other formats， even if a row was all zeros。

 we might still need to have some data allocated for it， so we'll take a look at that。ok， thank you。

Yeah， you're welcome。 Any other questions。Okay， if not。

 then you can read more about what we covered today in chapter 10 of the textbook。

 particularly these sections and that's all for today and I will see you next time。Bye everyone。



![](img/4f8b4ef2de0a3186f5a4443ca0319f83_77.png)