# 弗吉尼亚大学【中英⚡计算机架构｜CS3330 2020 Computer Architecture】 p27 P27 Final review -BV1cKeGzqEuJ_p27-

Good afternoon。So， last time。

![](img/7e3bc81091c2c0c455b09e659731d8eb_1.png)

We looked at the problem。 our first step along the problem of。

Dealing with our page tables being rather large。 And one part of that problem was that it wouldn't be reasonable to just store the page table in the processor because we found out that for。



![](img/7e3bc81091c2c0c455b09e659731d8eb_3.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_4.png)

Typical virtual address sizes and typical page sizes that these tables would be very， very large。



![](img/7e3bc81091c2c0c455b09e659731d8eb_6.png)

And in particular， at the least， larger than we would typically want to keep in cash。



![](img/7e3bc81091c2c0c455b09e659731d8eb_8.png)

So we have the solution of keeping them in memory and we can access memory through a cache or we can cache parts of them so maybe it won't be so bad。

 we'll find out later today that you know that's not going to be fast enough and we'll have a solution and also that this reverse scheme of keeping it in memory is not going to be space efficient to not so we're going to extend it to be a little more space efficient。

But our original scheme was that we'd have a flat table in memory where we take each page table entry and represent it as byte。

 So we just choose some way of laying out the information in each page table entry。

 which remember was like a valid bit。

![](img/7e3bc81091c2c0c455b09e659731d8eb_10.png)

And some permission bits。

![](img/7e3bc81091c2c0c455b09e659731d8eb_12.png)

And the physical page number and putting them as some bytes。

 And we have an array of page table entries represented as you know a sequence of bytes。

 basically you know。

![](img/7e3bc81091c2c0c455b09e659731d8eb_14.png)

You know，So I'm fixed sized integer。That we decode into a physical page number of valid datata in the permission bit。

And we'd had this array and wed just give the hardware， you know。



![](img/7e3bc81091c2c0c455b09e659731d8eb_16.png)

We'll get a pointer to the beginning of the red。And it would do an array lookup where it would know。

 okay， I have this virtual page number that's， you know， if it's virtual page 17。

 that's element 17 of the array， it would compute the address of that element of the array。

 read it from the cache and then decode it to get the valid bit permission bin and the physical page number。

 process those and then get take the physical page number and the physical sorry in the page offset to make a physical address and send that to the cache to you know。

Actually access the virtual our stick program was looking at。

So this had sort of two problems that we're going to talk in detail today about addressing so one。

Is this fundamental issue that we're kind of increasing the number of physical memory accesses。

 most hopefully just catch accesses， but that's still going to be pretty slow。

 so we're going to run away of making that faster。 we'll talk about that as our last topic today。



![](img/7e3bc81091c2c0c455b09e659731d8eb_18.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_19.png)

And another problem is that we found out when doing some calculations that though this scheme at least makes it possible to fit the sort of page tables we'd want for a 30 2bit system。

Somewhere， it has a lot of overhead and when we think about 604 bit systems。

 even when we're not using all the bits of a virtual address。😡。

It ends up being impractical that we need terabytes of memory to store our page tables for a typical system running a couple processes。

 and that's just not acceptable， so we're going to have a more complex scheme that extends this into something where we have a practical amount of space。

 but we're going to briefly make this problem of accessing the cache more times worse to do that。😡。

But before we get to that， we had a bunch。 We had sort of an interlude yesterday talking about something I called sort of。



![](img/7e3bc81091c2c0c455b09e659731d8eb_21.png)

I might call page table tricks。So these are things we can do with page tables， you know， things。

 the OS， I should say， the software that runs multiple programs together。Can do with page tables。

Besides， provide programs independent memory。

![](img/7e3bc81091c2c0c455b09e659731d8eb_23.png)

And we had some mechanisms from the hardware to help this out。 So one thing， for example。

 we found out we wanted to do was we wanted to。

![](img/7e3bc81091c2c0c455b09e659731d8eb_25.png)

Give read only access。

![](img/7e3bc81091c2c0c455b09e659731d8eb_27.png)

For share data， so we wanted to have two programs share。

 say some machine code and we wanted to know that when we were doing this。

 that we could still at least preserve the illusion that the programs are operating independently。

 meaning that if one program messes up and tries to overwrite its machine code that it's not going to affect the other program。

😡，Because that right shouldn't succeed。The hardware can help us with this by adding these permission bits where we can。

 for example， disable writing， given a particular page table entry and how this would work in the hardware is just like the hardware would check a valid bit to see if the page table entry mapped to any physical page。

 it would also check， say a writeriable bit to see whether。😡。



![](img/7e3bc81091c2c0c455b09e659731d8eb_29.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_30.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_31.png)

Writing was allowed before it would do a write using that page table entry as part of the translation。

😡。

![](img/7e3bc81091c2c0c455b09e659731d8eb_33.png)

And we can extend this to other sorts of controls。 We saw our original example of。

Is it allowed to be used in kernel mode， we can also have， is it allowed to be executed。

 We can imagine hardware work could add other features like this if they felt it would help operating systems do。



![](img/7e3bc81091c2c0c455b09e659731d8eb_35.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_36.png)

Interesting things。

![](img/7e3bc81091c2c0c455b09e659731d8eb_38.png)

This was an important form of metadata。

![](img/7e3bc81091c2c0c455b09e659731d8eb_40.png)

And after we looked at sort of。嗯。

![](img/7e3bc81091c2c0c455b09e659731d8eb_42.png)

This extra feature of the hardware provided to be more convenient for things the OS would want to do beyond just independent memory for different programs。

 we also examined the implications of exceptions being involved when page table lookups encounter and error。



![](img/7e3bc81091c2c0c455b09e659731d8eb_44.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_45.png)

And。😡。

![](img/7e3bc81091c2c0c455b09e659731d8eb_47.png)

We were originally just saying， okay， you know， the page isn't valid or it's read only。

 We're just going to have the OS run to crash the program and run something else。

 We have to run the OS for that because the OS is the only piece of software。

 which is going to know about those other programs， but。



![](img/7e3bc81091c2c0c455b09e659731d8eb_49.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_50.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_51.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_52.png)

You know， our assumption was basically that it would just， you know， run something else。

 but the US doesn't have to do that。

![](img/7e3bc81091c2c0c455b09e659731d8eb_54.png)

And one example of what it could do instead is it could load pages on demand， it could say， okay。

 this page wasn't accessible， but rather than just assuming the program messed up。

 let's look at what the program you thought should be there。

 so we had one example that the OS might track where the program stack should be and not allocate it right away。

😡。

![](img/7e3bc81091c2c0c455b09e659731d8eb_56.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_57.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_58.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_59.png)

And instead， it can wait until the program tries to use it and detect。

 okay it tried to access something that wasn't allocated。

 let's figure out whether it was really never allocated in which case it's an error or it's just something that I the OS didn't allocate it right away and if I didn't I can fix that I can update the page table to allocate it and rerun the instruction that triggered the fault and the hardware can make this more possible by giving the OS a little help in figuring out this out and then rewriting that instruction。

😡。

![](img/7e3bc81091c2c0c455b09e659731d8eb_61.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_62.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_63.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_64.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_65.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_66.png)

So it can tell the OS， here's the address that the program is trying to access and make sure that when the OS returns from its exception handler。

 normally that it does the same instruction over again。



![](img/7e3bc81091c2c0c455b09e659731d8eb_68.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_69.png)

And an extension of this， which was actually the original sort of motivation for virtual memory and page tables。

 is that we can treat all of memory as a cash for disk that rather than allocating program space in memory。

 we allocate program space on a hard drive or。

![](img/7e3bc81091c2c0c455b09e659731d8eb_71.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_72.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_73.png)

Say that this part of the program's memory comes from a file， for example。😡。



![](img/7e3bc81091c2c0c455b09e659731d8eb_75.png)

And we can load data from that hard drive as the program needs it。

 and if we run out of space for all the data programs are' using， we can evict something。😡。



![](img/7e3bc81091c2c0c455b09e659731d8eb_77.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_78.png)

From what one of those programs are using to that space on disk and know that well。

 if we's needed it again， we'll load it back and this is the same kind of thing we can kind of think of our normal processor cache is doing。



![](img/7e3bc81091c2c0c455b09e659731d8eb_80.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_81.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_82.png)

When we think of interfacing the catch and main memory that there。



![](img/7e3bc81091c2c0c455b09e659731d8eb_84.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_85.png)

好。YouSing stuff from memory that's as it gets used and when they run out of space to store stuff from memory。

 they evicted back。 The difference here is that this is something that the OS would do without the hardware actually needing to do anything special to support it beyond implementing this translation and making sure that the OS you know。

 gets enough information when。

![](img/7e3bc81091c2c0c455b09e659731d8eb_87.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_88.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_89.png)

![](img/7e3bc81091c2c0c455b09e659731d8eb_90.png)

That translation fails when we find an invalid page table entry。



![](img/7e3bc81091c2c0c455b09e659731d8eb_92.png)

食。

![](img/7e3bc81091c2c0c455b09e659731d8eb_94.png)